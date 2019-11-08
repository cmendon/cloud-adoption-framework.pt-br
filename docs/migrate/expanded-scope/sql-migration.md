---
title: Acelere a migração migrando uma instância do SQL Server
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: A migração de instâncias inteiras de SQL Server pode acelerar os esforços de migração de carga de trabalho.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 71632e8f3f995922f4021f216f2090b742141169
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753529"
---
# <a name="accelerate-migration-by-migrating-an-instance-of-sql-server"></a>Acelere a migração migrando uma instância do SQL Server

A migração de instâncias inteiras de SQL Server pode acelerar os esforços de migração de carga de trabalho. As diretrizes a seguir expandem o escopo do [Guia de migração do Azure](../azure-migration-guide/index.md) migrando uma instância do SQL Server fora de um esforço de migração voltado para carga de trabalho. Essa abordagem pode propagar a migração de várias cargas de trabalho com uma única migração de plataforma de dados. A maioria dos esforços necessários nessa expansão de escopo ocorre durante os processos de pré-requisitos, avaliação, migração e otimização de um esforço de migração.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Esse é o direito de escopo expandido para você?

A abordagem recomendada no [Guia de migração do Azure](../azure-migration-guide/index.md) é migrar cada estrutura de dados junto com as cargas de trabalho associadas como parte de um único esforço de migração. A abordagem iterativa da migração reduz a descoberta, a avaliação e outras tarefas que podem criar bloqueadores e retornos de valor comercial lentos.

No entanto, algumas estruturas de dados podem ser migradas com mais eficiência por meio de uma migração de plataforma de dados separada. Seguem alguns exemplos:

- **Fim do serviço:** Mover rapidamente uma instância de SQL Server para evitar desafios de fim de serviço pode justificar o uso deste guia fora dos esforços de migração padrão.
- **Serviços SQL Servers:** A estrutura de dados faz parte de uma solução mais ampla que requer SQL Server em execução em uma máquina virtual. Isso é comum para soluções que usam serviços SQL Server como SQL Server Reporting Services, SQL Server Integration Services ou SQL Server Analysis Services.
- **Bancos de dados de uso baixo e de alta densidade:** A instância do SQL Server tem uma alta densidade de bancos de dados. Cada um desses bancos de dados tem volumes de transação baixos e requer pouco na forma de recursos de computação. Você deve considerar outras soluções mais modernas, mas uma abordagem de infraestrutura como serviço (IaaS) pode resultar em um custo operacional significativamente reduzido.
- **Custo total de propriedade:** Quando aplicável, você pode aplicar os [benefícios híbridos do Azure](https://azure.microsoft.com/pricing/hybrid-benefit) ao preço da lista, criando o menor custo de propriedade para instâncias do SQL Server. Isso é especialmente comum para clientes que hospedam SQL Server em cenários de nuvem.
- **Acelerador de migração:** A migração "comparando e Shift" de uma instância de SQL Server pode mover vários bancos de dados em uma iteração. Às vezes, essa abordagem permite que iterações futuras se concentrem mais especificamente em aplicativos e VMs, o que significa que você pode migrar mais cargas de trabalho em uma única iteração.
- **Migração do VMware:** Uma arquitetura local comum inclui aplicativos e VMs em um host virtual e bancos de dados em bare-metal. Nesse cenário, você pode migrar todas as instâncias de SQL Server para dar suporte à migração do host VMware para o serviço VMware do Azure. Para obter mais informações, consulte [migração de host do VMware](./vmware-host.md).

Se nenhum dos critérios acima se aplicar a essa migração, talvez seja melhor continuar com o processo de [migração padrão](../index.md). No processo padrão, as estruturas de dados são migradas iterativamente, ao lado de cada carga de trabalho.

Se este guia se alinhar com seus critérios, continue com esse guia de escopo expandido como um esforço dentro do [processo de migração padrão](../index.md). Durante a fase de pré-requisitos, você pode integrar o esforço ao plano de adoção geral.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Antes de executar uma migração de SQL Server, comece com uma expansão do espaço digital, incluindo um espaço de dados. O espaço de dados registra um inventário dos ativos de dados que você está considerando para a migração. As tabelas a seguir descrevem uma abordagem para registrar o espaço de dados.

### <a name="server-inventory"></a>Inventário de servidor

Veja a seguir um exemplo de um inventário de servidor:

|SQL Server|Finalidade|Versão|[Importância](../../manage/considerations/criticality.md)|[Confidencialidade](../../govern/policy-compliance/data-classification.md)|Contagem de banco de dados|SSIS|SSRS|ADAPTADOR|Cluster|Número de nós|
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|Aplicativos principais|2016|Essenciais|Altamente confidencial|40|N/D|N/D|N/D|SIM|3|
|SQL-02|Aplicativos principais|2016|Essenciais|Altamente confidencial|40|N/D|N/D|N/D|SIM|3|
|SQL-03|Aplicativos principais|2016|Essenciais|Altamente confidencial|40|N/D|N/D|N/D|SIM|3|
|SQL-04|BI|2012|Alto|XX|6|N/D|Confidencial|Sim – cubo multidimensional|Não|1|
|SQL-05|Integração|2008 R2|Baixo|Geral|20|SIM|N/D|N/D|Não|1|

### <a name="database-inventory"></a>Inventário de banco de dados

Veja a seguir um exemplo de inventário de banco de dados para um dos servidores acima:

|Servidor|Banco de dados|[Importância](../../manage/considerations/criticality.md)|[Confidencialidade](../../govern/policy-compliance/data-classification.md)|Resultados de Assistente de Migração de Dados (DMA)|Correção de DMA|Plataforma de destino|
|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|DB-1|Essenciais|Altamente confidencial|Compatíveis|N/D|Banco de dados SQL do Azure|
|SQL-01|DB-2|Alto|Confidencial|Alteração de esquema necessária|Alterações implementadas|Banco de dados SQL do Azure|
|SQL-01|DB-1|Alto|Geral|Compatíveis|N/D|Instância gerenciada do SQL do Azure|
|SQL-01|DB-1|Baixo|Altamente confidencial|Alteração de esquema necessária|Alterações agendadas|Instância gerenciada do SQL do Azure|
|SQL-01|DB-1|Essenciais|Geral|Compatíveis|N/D|Instância gerenciada do SQL do Azure|
|SQL-01|DB-2|Alto|Confidencial|Compatíveis|N/D|Banco de dados SQL do Azure|

### <a name="integration-with-the-cloud-adoption-plan"></a>Integração com o plano de adoção de nuvem

Depois que esse processo de descoberta for concluído, você poderá incluí-lo no [plano de adoção de nuvem](../../plan/template.md). No plano de adoção de nuvem, adicione cada instância de SQL Server a ser migrada como uma [carga de trabalho distinta](../../plan/workloads.md). Dentro de cada carga de trabalho, os bancos de dados e serviços (SSIS, SSAS, SSRS) podem ser adicionados como [ativos](../../plan/workloads.md). Para adicionar cargas de trabalho e ativos em massa ao plano de adoção, consulte [adicionando e editando itens de trabalho com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Depois que as cargas de trabalho e os ativos forem incluídos no plano, você e sua equipe poderão continuar com um processo de migração padrão usando o plano de adoção. Quando a equipe de adoção passa para os processos de avaliação, migração e otimização, o fator nas alterações abordadas nas seções a seguir.

## <a name="assessment-process-changes"></a>Alterações no processo de avaliação

Se qualquer banco de dados no plano puder ser migrado para uma plataforma de dados de PaaS (plataforma como serviço), use o DMA para avaliar a compatibilidade do banco de dado selecionado. Quando o banco de dados requer conversões de esquema, você deve concluir essas conversões como parte do processo de avaliação, para evitar interrupções no pipeline de migração.

### <a name="suggested-action-during-the-assessment-process"></a>Ação sugerida durante o processo de avaliação

Para bancos de dados que podem ser migrados para uma solução PaaS, as ações a seguir são concluídas durante o processo de avaliação.

- **Avalie com o DMA:** Use Assistente de Migração de Dados para detectar problemas de compatibilidade que podem afetar a funcionalidade do banco de dados em sua instância gerenciada do banco de dados SQL do Azure de destino. Use o DMA para recomendar melhorias de desempenho e confiabilidade e para mover o esquema, os dados e os objetos não contidos do seu servidor de origem para o servidor de destino. Para obter mais informações, consulte [Assistente de migração de dados](https://docs.microsoft.com/sql/dma/dma-overview).
- **Corrigir e converter:** Com base na saída de DMA, converta o esquema de dados de origem para corrigir os problemas de compatibilidade. Teste o esquema de dados convertido com os aplicativos dependentes.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Durante a migração, você pode escolher entre várias ferramentas e abordagens diferentes. Mas cada abordagem segue um processo simples: migrar esquema, dados e objetos. Em seguida, sincronize os dados para a fonte de dados de destino.

O destino e a origem da estrutura de dados e serviços podem tornar essas duas etapas bastante complicadas. As seções a seguir ajudam a entender a melhor opção de ferramentas com base nas decisões de migração.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

O caminho sugerido para migração e sincronização usa uma combinação das três ferramentas a seguir. As seções a seguir descrevem opções mais complexas de migração e sincronização que permitem uma variedade mais ampla de soluções de destino e origem.

|Opção de migração|Finalidade|
|---------|---------|
|[Serviço de Migração de Banco de Dados do Azure](https://docs.microsoft.com/sql/dma/dma-overview)|Dá suporte a migrações online (mínimo de tempo de inatividade) e offline (uma vez) em escala para uma instância gerenciada do banco de dados SQL do Azure. O oferece suporte à migração de: SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|
|[Replicação transacional](https://docs.microsoft.com/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|A replicação transacional para uma instância gerenciada do banco de dados SQL do Azure tem suporte para migrações de: SQL Server 2012 (SP2 CU8, SP3 ou posterior), SQL Server 2014 (RTM CU10 ou posterior ou SP1 CU3 ou posterior), SQL Server 2016 SQL Server 2017.|
|[Carregamento em massa](https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql)|Use o carregamento em massa para uma instância gerenciada do banco de dados SQL do Azure para os dados armazenados em: SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Diretrizes e tutoriais para o processo de migração sugerido

A escolha da melhor orientação para a migração usando o serviço de migração de banco de dados do Azure é contingente na plataforma de origem e de destino de sua escolha. A tabela a seguir contém links para tutoriais para cada uma das abordagens padrão para migrar um banco de dados SQL usando o serviço de migração de banco de dados do Azure.

|Origem  |Escolha o destino  |Ferramenta  |Tipo de migração  |Diretriz  |
|---------|---------|---------|---------|---------|
|SQL Server|Banco de dados SQL do Azure|Serviço de Migração do Banco de Dados|Off-line|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Banco de dados SQL do Azure|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Instância gerenciada do Banco de Dados SQL do Azure|Serviço de Migração do Banco de Dados|Off-line|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Instância gerenciada do Banco de Dados SQL do Azure|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Banco de dados SQL do Azure (ou instância gerenciada)|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Diretrizes e tutoriais para vários serviços para soluções de PaaS equivalentes

Depois de mover os bancos de dados de uma instância do SQL Server para o serviço de migração de banco de dado do Azure, o esquema e os dados podem ser rehospedados em várias soluções PaaS. No entanto, outros serviços necessários ainda podem estar em execução nesse servidor. Os três tutoriais a seguir auxiliam na movimentação do SSIS, do SSAS e do SSRS para os serviços de PaaS equivalentes no Azure.

|Origem  |Escolha o destino  |Ferramenta  |Tipo de migração  |Diretriz  |
|---------|---------|---------|---------|---------|
|SQL Server Integration Services|Tempo de execução de integração do Azure Data Factory|Fábrica de dados do Azure|Off-line|[Tutorial](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|Modelo de SQL Server Analysis Services de tabela|Analysis Services do Azure|SQL Server Data Tools|Off-line|[Tutorial](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|SQL Server Reporting Services|Servidor de Relatórios do Power BI|Power BI|Off-line|[Tutorial](https://docs.microsoft.com/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Diretrizes e tutoriais para migração de SQL Server para uma instância de IaaS do SQL Server

Depois de migrar bancos de dados e serviços para instâncias de PaaS, você ainda pode ter estruturas e serviços que não são compatíveis com PaaS. Quando as restrições existentes impedem a migração de estruturas de dados ou serviços, o tutorial a seguir pode ajudar na migração de vários ativos no portfólio de dados para soluções de IaaS do Azure.

Use essa abordagem para migrar bancos de dados ou outros serviços na instância do SQL Server.

|Origem  |Escolha o destino  |Ferramenta  |Tipo de migração  |Diretriz  |
|---------|---------|---------|---------|---------|
|SQL Server de instância única|SQL Server na IaaS|Variado|Off-line|[Tutorial](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Alterações no processo de otimização

Durante a otimização, você pode testar, otimizar e promover para produção cada estrutura de dados, serviço ou instância de SQL Server. Esse é o maior impacto do deviating de um modelo de migração por carga de trabalho.

O ideal é migrar as cargas de trabalho, os aplicativos e as VMs dependentes na mesma iteração que a instância de SQL Server. Quando esse cenário ideal ocorre, você pode testar a carga de trabalho junto com a fonte de dados. Após o teste, você pode promover a estrutura de dados para produção e encerrar o processo de sincronização.

Agora, vamos considerar o cenário no qual há uma lacuna de tempo significativa entre migração de banco de dados e migração de carga de trabalho. Infelizmente, essa pode ser a maior alteração no processo de otimização durante uma migração não controlada por carga de trabalho. Ao migrar vários bancos de dados como parte de uma migração de SQL Server, esses bancos de dados podem coexistir na nuvem e no local, para várias iterações. Durante esse tempo, você precisa manter a sincronização de dados até que esses ativos dependentes sejam migrados, testados e promovidos.

Até que todas as cargas de trabalho dependentes sejam promovidas, você e sua equipe serão responsáveis por dar suporte à sincronização de dados do sistema de origem para o sistema de destino. Essa sincronização consome largura de banda de rede, custos de nuvem e, o mais importante, a hora das pessoas. O alinhamento adequado do plano de adoção entre a carga de trabalho de migração de SQL Server e todas as cargas de trabalho e aplicativos dependentes pode reduzir essa sobrecarga dispendiosa.

### <a name="suggested-action-during-the-optimization-process"></a>Ação sugerida durante o processo de otimização

Durante os processos de otimização, conclua as tarefas a seguir a cada iteração, até que todas as estruturas de dados e serviços tenham sido promovidos para produção.

1. Validar a sincronização de dados.
2. Teste todos os aplicativos migrados.
3. Otimize o aplicativo e a estrutura de dados para ajustar os custos.
4. Promova os aplicativos para produção.
5. Teste para o tráfego contínuo no local no banco de dados local.
6. Encerrar a sincronização de todos os dados promovidos para a produção.
7. Encerrar o banco de dados de origem original.

Até que a etapa 5 passe, você não pode encerrar bancos de dados e sincronização. Até que todos os bancos de dados em uma instância do SQL Server tenham passado por todas as sete etapas, você deve tratar a instância local do SQL Server como produção. Toda a sincronização deve ser mantida.

## <a name="next-steps"></a>Próximos passos

Retorne à [lista de verificação de escopo expandido](./index.md) para verificar se o método de migração está totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
