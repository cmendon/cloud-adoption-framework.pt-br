---
title: Acelere a migração com uma migração do SQL
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Acelere a migração com uma migração do SQL
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4af94af91874ac666f45a917eed003b3cf881c51
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558214"
---
# <a name="accelerate-migration-with-a-sql-migration"></a>Acelere a migração com uma migração do SQL

A migração de instâncias inteiras de SQL Server pode acelerar os esforços de migração de carga de trabalho. As diretrizes a seguir expandirão o escopo do [Guia de migração do Azure](../azure-migration-guide/index.md) migrando um SQL Server fora de um esforço de migração focado em carga de trabalho. Essa abordagem pode propagar a migração de várias cargas de trabalho com uma única migração de plataforma de dados.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

A maior parte do esforço necessário nessa expansão de escopo ocorrerá durante os processos de pré-requisitos, avaliação, migração e otimização de um esforço de migração.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Esse é o direito de escopo expandido para você?

A abordagem recomendada descrita no [Guia de migração do Azure](../azure-migration-guide/index.md) é migrar cada estrutura de dados junto com as cargas de trabalho associadas como parte de um único esforço de migração. A abordagem iterativa da migração reduz a descoberta, a avaliação e outras tarefas que podem criar bloqueadores e retornos de valor comercial lentos.

No entanto, algumas estruturas de dados podem ser migradas com mais eficiência por meio de uma migração de plataforma de dados separada. Veja a seguir alguns exemplos que podem levar ao uso desta diretriz de escopo expandido:

- **Fim do serviço:** Mover rapidamente uma instância de SQL Server para evitar desafios de fim de serviço pode justificar o uso deste guia fora dos esforços de migração padrão.
- **Serviços SQL Servers:** A estrutura de dados faz parte de uma solução mais ampla que requer SQL Server em execução em uma máquina virtual. Isso é comum para soluções que aproveitam serviços SQL Server, como SQL Server Reporting Services, SQL Server Integration Services ou SQL Server Analysis Services.
- **Bancos de dados de uso baixo e de alta densidade:** O SQL Server tem uma alta densidade de bancos de dados. Cada um desses bancos de dados tem volumes de transação baixos e exigem poucos recursos de computação. Outras soluções mais modernas devem ser consideradas, mas uma abordagem de IaaS pode resultar em um custo operacional significativamente reduzido.
- **Custo total de propriedade:** Quando aplicável, os [benefícios híbridos do Azure](https://azure.microsoft.com/pricing/hybrid-benefit) podem ser aplicados ao preço da lista, criando o menor custo de propriedade para servidores SQL. Isso é especialmente comum para clientes que hospedam SQL Server em cenários de nuvem.
- **Acelerador de migração:** A migração de comparação de precisão e de deslocamento de uma instância de SQL Server pode mover vários bancos de dados em uma iteração. Às vezes, essa abordagem permite que iterações futuras se concentrem mais especificamente em aplicativos e VMs, migrando mais cargas de trabalho em uma única iteração.
- **Migração do VMware:** Uma arquitetura local comum inclui aplicativos e VMs em um host virtual e bancos de dados em bare-metal. Ao migrar essa arquitetura comum, a migração do host VMWare para o serviço VMWare do Azure (AVS) pode ser complementada por este guia para migrar SQL Server instâncias inteiras para dar suporte a esses hosts virtuais. Para obter orientações complementares, consulte [migração de host do VMware](./vmware-host.md).

Se nenhum dos critérios acima se aplicar a essa migração, talvez seja melhor continuar com o processo de [migração padrão](../index.md). No processo padrão, as estruturas de dados são migradas iterativamente ao lado de cada carga de trabalho.

Se este guia se alinhar com seus critérios, continue com esse guia de escopo expandido como um esforço dentro do [processo de migração padrão](../index.md). Durante a fase de pré-requisitos, o esforço pode ser integrado ao plano de adoção geral.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Antes de executar uma migração de SQL Server, comece com uma expansão do **espaço digital** , incluindo um espaço de dados. O espaço de dados registra um inventário dos ativos de dados que estão sendo considerados para migração. As tabelas a seguir descrevem uma abordagem para registrar o espaço de dados.

### <a name="server-inventory"></a>Inventário de servidor

Veja a seguir um exemplo de um inventário de servidor para servidores SQL:

|SQL Server|Finalidade|Versão|[Importância](../../manage/considerations/criticality.md)|[Confidencialidade](../../govern/policy-compliance/data-classification.md)|Contagem de banco de dados|SSIS|SSRS|ADAPTADOR|HDInsight|Número de nós|
|---------|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|Aplicativos principais|2016|Missão crítica|Altamente confidencial|40|N/D|N/D|N/D|Sim|3|
|SQL-02|Aplicativos principais|2016|Missão crítica|Altamente confidencial|40|N/D|N/D|N/D|Sim|3|
|SQL-03|Aplicativos principais|2016|Missão crítica|Altamente confidencial|40|N/D|N/D|N/D|Sim|3|
|SQL-04|BI|2012|Alto|XX|6|N/D|Confidencial|Sim – cubo multidimensional|Não|1|
|SQL-05|Integração|2008 R2|Baixo|Geral|20|Sim|N/D|N/D|Não|1|

### <a name="database-inventory"></a>Inventário de banco de dados

Veja a seguir um exemplo de um inventário de banco de dados para um dos SQL Servers acima:

|Servidor|Banco de dados|[Importância](../../manage/considerations/criticality.md)|[Confidencialidade](../../govern/policy-compliance/data-classification.md)|Resultados de DMA|Correção de DMA|Plataforma de destino|
|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|DB-1|Missão crítica|Altamente confidencial|Compatíveis|N/D|Banco de Dados SQL do Azure|
|SQL-01|DB-2|Alto|Confidencial|Alteração de esquema necessária|Alterações implementadas|Banco de Dados SQL do Azure|
|SQL-01|DB-1|Alto|Geral|Compatíveis|N/D|Instância Gerenciada do Azure SQL|
|SQL-01|DB-1|Baixo|Altamente confidencial|Alteração de esquema necessária|Alterações agendadas|Instância Gerenciada do Azure SQL|
|SQL-01|DB-1|Missão crítica|Geral|Compatíveis|N/D|Instância Gerenciada do Azure SQL|
|SQL-01|DB-2|Alto|Confidencial|Compatíveis|N/D|Banco de Dados SQL do Azure|

### <a name="integration-with-the-cloud-adoption-plan"></a>Integração com o plano de adoção de nuvem

Após a conclusão da descoberta, o plano pode ser incluído no [plano de adoção da nuvem](../../plan/template.md). No plano de adoção de nuvem, adicione cada instância de SQL Server a ser migrada como uma [carga de trabalho distinta](../../plan/workloads.md). Dentro de cada carga de trabalho, os bancos de dados e serviços (SSIS, SSAS, SSRS) podem ser adicionados como [ativos](../../plan/workloads.md). Para adicionar cargas de trabalho e ativos em massa ao plano de adoção, consulte [adicionando e editando itens de trabalho com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Depois que as cargas de trabalho e os ativos forem incluídos no plano, a equipe poderá continuar com um processo de migração padrão usando o plano de adoção para orientar os esforços. Quando a equipe de adoção passa para processos de avaliação, migração e otimização, as seguintes alterações devem ser fatoradas nos esforços.

## <a name="assessment-process-changes"></a>Alterações no processo de avaliação

Se qualquer banco de dados no plano puder ser migrado para uma plataforma de dados de PaaS (plataforma como serviço), use Assistente de Migração de Dados para avaliar a compatibilidade do banco de dado selecionado. Quando o banco de dados requer conversões de esquema, é recomendável que essas conversões sejam concluídas como parte do processo de avaliação para evitar interrupções no pipeline de migração.

### <a name="suggested-action-during-the-assessment-process"></a>Ação sugerida durante o processo de avaliação

Para bancos de dados que podem ser migrados para uma solução PaaS, as ações a seguir seriam concluídas durante o processo de avaliação.

- **Avalie com assistente de migração de dados:** Use Assistente de Migração de Dados para detectar problemas de compatibilidade que podem afetar a funcionalidade do banco de dados em sua instância gerenciada do banco de dados SQL do Azure de destino, para recomendar melhorias de desempenho e confiabilidade e para mover o esquema, os dados e os objetos não contidos do servidor de origem para o servidor de destino. Para obter mais informações, consulte [Assistente de migração de dados](/sql/dma/dma-overview).
- **Corrigir e converter:** Com base na saída de Assistente de Migração de Dados, converta o esquema de dados de origem para corrigir os problemas de compatibilidade. Teste o esquema de dados convertido com os aplicativos dependentes.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Durante a migração, há várias opções de ferramentas e abordagens. Mas cada abordagem segue um processo simples: migrar esquema, dados e objetos. Sincronizar dados com a fonte de dados de destino.

O destino e a origem da estrutura de dados e serviços podem tornar essas duas etapas bastante complicadas. Veja cada uma das seções a seguir para entender a melhor opção de ferramentas com base nas decisões de migração.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

O caminho sugerido para migração e sincronização usa uma combinação das três ferramentas a seguir. As seções a seguir descrevem opções mais complexas de migração e sincronização que permitem uma variedade mais ampla de soluções de destino e origem.

|Opção de migração|Finalidade|
|---------|---------|
|[Serviço de Migração de Banco de Dados do Azure](/sql/dma/dma-overview)|O Azure DMS dá suporte a migrações online (tempo de inatividade mínima) e offline (uma vez) em escala para uma instância gerenciada do banco de dados SQL do Azure do SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|
|[Replicação transacional](/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|A replicação transacional para uma instância gerenciada do banco de dados SQL do Azure tem suporte para migrações de: SQL Server 2012 (SP2 CU8, SP3 ou posterior), SQL Server 2014 (RTM CU10 ou posterior ou SP1 CU3 ou posterior), SQL Server 2016 SQL Server 2017|
|[Carregamento em massa](/sql/t-sql/statements/bulk-insert-transact-sql)|Use o carregamento em massa para uma instância gerenciada do banco de dados SQL do Azure para os dados armazenados no SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Diretrizes e tutoriais para o processo de migração sugerido

Escolher a melhor orientação para migração usando o DMS é contingente na plataforma de origem e de destino de sua escolha. A tabela a seguir descreve os tutoriais para cada uma das abordagens padrão para migrar um banco de dados SQL usando DMS.

|Fonte  |Destino  |Ferramenta  |Tipo de migração  |Diretrizes  |
|---------|---------|---------|---------|---------|
|SQL Server|Banco de Dados SQL do Azure|DMS|Off-line|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Banco de Dados SQL do Azure|DMS|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Instância Gerenciada do Banco de Dados SQL do Azure|DMS|Off-line|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Instância Gerenciada do Banco de Dados SQL do Azure|DMS|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Banco de dados SQL do Azure (ou Instância Gerenciada)|DMS|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Diretrizes e tutoriais para vários serviços para soluções de PaaS equivalentes

Depois de mover os bancos de dados de um SQL Server para o DMS, o esquema e os dados podem ser rehospedados em várias soluções PaaS. No entanto, outros serviços necessários ainda podem estar em execução nesse servidor. Os três tutoriais a seguir ajudarão a mover o SSIS, o SSAS e o SSRS para os serviços de PaaS equivalentes no Azure.

|Fonte  |Destino  |Ferramenta  |Tipo de migração  |Diretrizes  |
|---------|---------|---------|---------|---------|
|Serviço de integração do SQL Server|Data Factory Integration Runtime|Fábrica de dados do Azure|Off-line|[Tutorial](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|SQL Server Analysis Service-modelo de tabela|Azure Analysis Services|SSDT|Off-line|[Tutorial](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|SQL Server Reporting Service|Power BI servidor de relatórios|Power BI|Off-line|[Tutorial](/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Diretrizes e tutoriais para migração de SQL Server para uma instância de IaaS do SQL Server

Depois de migrar bancos de dados e serviços para instâncias de PaaS, ainda pode haver estruturas e serviços que não são compatíveis com PaaS. Quando as restrições existentes impedem a migração de estruturas de dados ou serviços, o tutorial a seguir pode ajudar na migração de vários ativos no portfólio de dados para soluções de IaaS do Azure.

Essa abordagem pode ser usada para migrar bancos de dados no SQL Server ou outros serviços em execução no SQL Server de origem.

|Fonte  |Destino  |Ferramenta  |Tipo de migração  |Diretrizes  |
|---------|---------|---------|---------|---------|
|SQL Server de instância única|SQL Server na IaaS|Variado|Off-line|[Tutorial](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Alterações no processo de otimização

Durante a otimização, cada estrutura de dados, serviço ou instância de SQL Server pode ser testada, otimizada e promovida para a produção. Esse é o maior impacto do deviating de um modelo de migração por carga de trabalho.

Idealmente, as cargas de trabalho, os aplicativos e as VMs dependentes serão migrados na mesma iteração que a instância de SQL Server. Quando esse cenário ideal ocorre, a carga de trabalho pode ser testada junto com a fonte de dados. Depois de testado, a estrutura de dados pode ser promovida para a produção e o processo de sincronização pode ser encerrado.

Infelizmente, a maior alteração no processo de otimização durante uma migração não controlada por carga de trabalho é quando há um intervalo de tempo significativo entre a migração de banco de dados e a migração de carga de trabalho. Quando vários bancos de dados são migrados como parte de uma migração de SQL Server, esses bancos de dados podem coexistir na nuvem e no local para várias iterações. Durante esse período, há a necessidade de manter a sincronização de dados até que esses ativos dependentes sejam migrados, testados e promovidos.

Até que todas as cargas de trabalho dependentes sejam promovidas, a equipe será responsável por dar suporte à sincronização de dados do sistema de origem para o sistema de destino. Essa sincronização consome largura de banda de rede, custos de nuvem e, o mais importante, a hora das pessoas. O alinhamento adequado do plano de adoção entre a "carga de trabalho" da migração de SQL Server e todas as cargas de trabalho/aplicativos dependentes reduzirá essa sobrecarga dispendiosa.

### <a name="suggested-action-during-the-optimization-process"></a>Ação sugerida durante o processo de otimização

Durante os processos de otimização, as tarefas a seguir devem ser concluídas a cada iteração até que todas as estruturas de dados e serviços tenham sido promovidos para produção.

1. Validar a sincronização de dados.
2. Teste todos os aplicativos migrados.
3. Otimize o aplicativo e a estrutura de dados para ajustar os custos.
4. Promova os aplicativos para produção.
5. Teste para o tráfego contínuo no local no banco de dados local.
6. Encerrar a sincronização de todos os dados promovidos para a produção.
7. Encerrar o banco de dados de origem original.

Até que a etapa 5 passe, os bancos de dados e a sincronização não podem ser encerrados. Até que todos os bancos de dados em um SQL Server tenham passado pelas etapas de 1-7, o SQL Server local deve ser tratado como produção e toda a sincronização deve ser mantida.

## <a name="next-steps"></a>Próximas etapas

Retorne à [lista de verificação de escopo expandido](./index.md) para verificar se o método de migração está totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
