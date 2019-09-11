---
title: Migrar ativos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migrar ativos
author: matticusau
ms.author: mlavery
ms.date: 08/08/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: ce8338fbcd0e21cf0875a207633ce7c9ddf2ff9e
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818754"
---
# <a name="migrate-assets-infrastructure-apps-and-data"></a>Migrar ativos (infraestrutura, aplicativos e dados)

Nesta fase da jornada, você usa a saída da fase de avaliação para iniciar a migração do ambiente. Este guia ajuda a identificar as ferramentas apropriadas para alcançar um "estado finalizado", incluindo ferramentas nativas, de terceiros e de gerenciamento de projetos.

# <a name="native-migration-toolstabtools"></a>[Ferramentas de migração nativas](#tab/Tools)

As seções a seguir descrevem as ferramentas nativas do Azure disponíveis para executar ou auxiliar na migração. Para obter informações sobre como escolher as ferramentas certas para apoiar seus esforços de migração, confira o [Guia de decisão das ferramentas de migração da Estrutura de Adoção de Nuvem](../../decision-guides/migrate-decision-guide/index.md).

## <a name="azure-migrate"></a>Migrações para Azure

As Migrações para Azure fornecem uma experiência de migração unificada e extensível. As Migrações para Azure fornecem uma experiência única e dedicada de acompanhamento da jornada de migração nas fases de avaliação e migração para o Azure. Elas oferecem a opção de usar as ferramentas de sua escolha e acompanhar o progresso da migração entre elas.

As Migrações para Azure oferecem a seguinte funcionalidade:

1. Recursos aprimorados de avaliação e migração:
    - Avaliações do Hyper-V.
    - Avaliação do VMware aprimorada.
    - Migração autônoma de máquinas virtuais VMware para o Azure.
1. Avaliação unificada, migração e acompanhamento de progresso.
1. Abordagem extensível com integração ISV (como o Cloudamize).

Para executar uma migração usando as Migrações para Azure, siga essas etapas:

1. Pesquise as Migrações para Azure em **Todos os serviços**. Selecione **Migrações para Azure** para continuar.
1. Selecione **Adicionar uma ferramenta** para iniciar o projeto de migração.
1. Selecione a assinatura, o grupo de recursos e a região onde a migração será hospedada.
1. Clique em **Selecionar ferramenta de avaliação** > **Migrações para Azure: Avaliação de Servidor** >  **Avançar**.
1. Selecione **Revisar + adicionar ferramenta(s)** e confirme a configuração. Clique em **Adicionar ferramenta(s)** para iniciar o trabalho de criação do projeto de migração e registrar as soluções selecionadas.

<!-- TODO: TBA -->

### <a name="read-more"></a>Leia mais

- [Tutorial das Migrações para Azure – Migrar servidores físicos ou virtualizados para o Azure](/azure/migrate/tutorial-migrate-physical-virtual-machines)

## <a name="azure-site-recovery"></a>Azure Site Recovery

O serviço do Azure Site Recovery pode gerenciar a migração de recursos locais para o Azure. Ele também pode gerenciar e orquestrar a recuperação de desastres de computadores locais e VMs do Azure para fins de continuidade dos negócios e recuperação de desastre (BCDR).

As etapas a seguir descrevem como usar o Site Recovery para a migração:

> [!TIP]
> Dependendo da sua situação, as etapas podem variar um pouco. Para obter mais informações, confira o artigo [Migrar máquinas locais para o Azure](/azure/site-recovery/migrate-tutorial-on-premises-azure).

### <a name="prepare-azure-site-recovery-service"></a>Preparar o serviço do Azure Site Recovery

1. No portal do Azure, selecione **+Criar um recurso > Ferramentas de Gerenciamento > Backup e Site Recovery**.
1. Se você ainda não criou um cofre de recuperação, conclua o assistente para criar um recurso de **cofre dos Serviços de Recuperação**.
1. No menu **Recurso**, selecione **Site Recovery > Preparar infraestrutura> Meta de proteção**.
1. Em **Objetivo de proteção**, selecione o que você deseja migrar.
    1. **VMware:** Selecione **Para o Azure > Sim, com o VMware vSphere Hypervisor** .
    1. **Computador físico:** Selecione **Para o Azure > Não virtualizado/outro** .
    1. **Hyper-V:** Selecione **Para o Azure > Sim, com o Hyper-V**. Se as VMs do Hyper-V são gerenciadas pelo VMM, selecione **Sim**.

### <a name="configure-migration-settings"></a>Definir as configurações de migração

1. Configure o ambiente de origem conforme apropriado.
1. Configure o ambiente de destino.
    1. Clique em **Preparar infraestrutura > Destino**  e selecione a assinatura do Azure que deseja usar.
    1. Especifique o modelo de implantação do Gerenciador de Recursos.
    1. A Recuperação de Site verifica se você tem uma ou mais contas de armazenamento e redes do Azure compatíveis.
1. Configurar uma política de replicação.
1. Habilite a replicação.
1. Execute uma migração de teste (failover de teste).

### <a name="migrate-to-azure-using-failover"></a>Migrações para Azure usando failover

1. Em **Configurações > Itens replicados**, clique no computador > **Failover**.
1. Em **Failover**, selecione um **Ponto de Recuperação** para executar o failover. Selecione o ponto de recuperação mais recente.
1. Defina as configurações de chave de criptografia, conforme necessário.
1. Selecione **Desligar o computador antes do início do failover**. O Site Recovery tentará desligar máquinas virtuais antes de disparar o failover. O failover continuará mesmo o desligamento falhar. Você pode acompanhar o progresso do failover na página Trabalhos.
1. Verifique se a VM do Azure aparece no Azure, conforme o esperado.
1. Em **Itens replicados**, clique com o botão direito do mouse na VM e escolha **Migração completa**.
1. Realize todas as etapas pós-migração conforme necessário (confira as informações relevantes neste guia).

::: zone target="chromeless"

::: form action="Create[#create/Microsoft.RecoveryServices]" submitText="Create a Recovery Services vault" :::

::: zone-end

::: zone target="docs"

Para obter mais informações, consulte:

- [Migrar máquinas locais para o Azure](/azure/site-recovery/migrate-tutorial-on-premises-azure)

::: zone-end

## <a name="azure-database-migration-service"></a>Serviço de Migração de Banco de Dados do Azure

O Serviço de Migração de Banco de Dados do Azure é totalmente gerenciado e permite fazer migrações contínuas de várias fontes de banco de dados para plataformas de dados do Azure com tempo de inatividade mínimo (migrações online). O Serviço de Migração de Banco de Dados do Azure executa todas as etapas necessárias. O Serviço de Migração de Banco de Dados do Azure é totalmente gerenciado e permite fazer migrações contínuas de várias fontes de banco de dados para plataformas de dados do Azure com o mínimo de tempo de inatividade (migrações online).

### <a name="create-an-azure-database-migration-service-instance"></a>Criar uma instância do Serviço de Migração de Banco de Dados do Azure

Se esta for a primeira vez usando o Serviço de Migração de Banco de Dados do Azure, você precisará registrar o provedor de recursos para sua assinatura do Azure:

1. Selecione **Todos os serviços**, clique em **Assinaturas** e escolha a assinatura desejada.
1. Selecione **Provedores de recursos**.
1. Procure por `migration` e, à direita de **Microsoft.DataMigration**, selecione **Registrar**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

::: zone-end

Depois de registrar o provedor de recursos, você pode criar uma instância do Serviço de Migração de Banco de Dados do Azure.

1. Selecione **+Criar um recurso**  e pesquise no marketplace pelo **Serviço de Migração de Banco de Dados do Azure**.
1. Conclua o assistente para **Criar Serviço de Migração** e selecione **Criar**.

O serviço agora está pronto para migrar os bancos de dados de fontes compatíveis (por exemplo, SQL Server, MySQL, PostgreSQL ou MongoDb).

::: zone target="chromeless"

::: form action="Create[#create/Microsoft.AzureDMS]" submitText="Create an Azure Database Migration Service instance" :::

::: zone-end

::: zone target="docs"

Para obter mais informações, consulte:

- [Visão geral do Serviço de Migração de Banco de Dados do Azure](/azure/dms/dms-overview)
- [Criar uma instância do Serviço de Migração de Banco de Dados do Azure](/azure/dms/quickstart-create-data-migration-service-portal)
- [Migrações para Azure no portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade)
- [Portal do Azure: Criar um projeto de migração](https://portal.azure.com/#create/Microsoft.AzureMigrate)

::: zone-end

## <a name="data-migration-assistant"></a>Assistente de Migração de Dados

O Assistente de Migração de Dados (AMD) ajuda você a atualizar para uma plataforma de dados moderna, detectando problemas de compatibilidade que podem afetar a funcionalidade do banco de dados em sua nova versão do SQL Server ou do Banco de Dados SQL do Azure. O Assistente de Migração de Dados recomenda melhorias de desempenho e confiabilidade para seu ambiente de destino e permite mover seu esquema, dados e objetos não contidos do seu servidor de origem para o servidor de destino.

> [!NOTE]
> Para grandes migrações (em termos de número e tamanho de bancos de dados), recomendamos que você use o Serviço de Migração de Banco de Dados do Azure, que pode migrar bancos de dados em grande escala.
>

Para começar a usar o Assistente de Migração de Dados, siga estas etapas.

1. Baixe e instale o Assistente de Migração de Dados do [Centro de Download da Microsoft](https://www.microsoft.com/download/details.aspx?id=53595).
1. Crie uma avaliação clicando no ícone **Novo (+)** e selecione o tipo de projeto **Avaliação**.
1. Defina o tipo de servidor de origem e de destino. Clique em **Criar**.
1. Configure as opções de avaliação conforme necessário (recomende todos os padrões).
1. Adicione os bancos de dados a serem avaliados.
1. Clique em **Avançar** para iniciar a avaliação.
1. Visualize os resultados no conjunto de ferramentas do Assistente de Migração de Dados.

Para uma empresa, recomendamos seguir a abordagem descrita em [Avaliar uma empresa e consolidar relatórios de avaliação com o Assistente de Migração de Dados](/sql/dma/dma-consolidatereports) para avaliar vários servidores, combinar os relatórios e usar os relatórios do Power BI para analisar os resultados.

Para obter mais informações, incluindo etapas detalhadas de uso, confira:

- [Visão geral do Assistente de Migração de Dados](/sql/dma/dma-overview)
- [Avaliar uma empresa e consolidar relatórios de avaliação com o Assistente de Migração de Dados](/sql/dma/dma-consolidatereports)
- [Analisar relatórios de avaliação consolidados criados pelo Assistente de Migração de Dados com o Power BI](/sql/dma/dma-powerbiassesreport)

## <a name="sql-server-migration-assistant"></a>Assistente de Migração do SQL Server

O Assistente de Migração do SQL Server (SSMA) é uma ferramenta projetada para automatizar a migração de banco de dados para o SQL Server do Microsoft Access, DB2, MySQL, Oracle e SAP ASE. Em geral, essas ferramentas vão coletar, avaliar para, só então, revisar, no entanto, devido às variações no processo de cada um dos sistemas de origem, recomendamos revisar a [documentação detalhada do Assistente de Migração do SQL Server](/sql/ssma/sql-server-migration-assistant).

Para obter mais informações, consulte:

- [Visão geral do Assistente de Migração do SQL Server](/sql/ssma/sql-server-migration-assistant)

## <a name="database-experimentation-assistant"></a>Assistente para Experimentos de Banco de Dados

O Assistente para Experimentos de Banco de Dados (DEA) é uma nova solução de teste A/B para atualizações do SQL Server. Ele ajudará na avaliação de uma versão direcionada do SQL para uma determinada carga de trabalho. Os clientes que estão atualizando de versões anteriores do SQL Server (SQL Server 2005 e superior) para qualquer nova versão do SQL Server podem usar essas métricas de análise.

O Assistente para Experimentos de Banco de Dados contém as seguintes atividades de fluxo de trabalho:

- **Captura:** A captura de um rastreamento no seu servidor de origem é a primeira etapa do teste A/B do SQL Server. O servidor de origem é geralmente o servidor de produção.
- **Reprodução**: A segunda etapa do teste A/B do SQL Server consiste em reproduzir o arquivo de rastreamento que foi capturado em seus servidores de destino. A seguir, ele coleta rastreamentos extensos das reproduções da análise.
- **Análise**: A etapa final consiste em gerar um relatório de análise usando os rastreamentos de reprodução. O relatório de análise pode ajudar você a obter informações sobre as implicações de desempenho da alteração proposta.

Para obter mais informações, consulte:

- [Visão geral do Assistente para Experimentos de Banco de Dados](/sql/dea/database-experimentation-assistant-overview)

# <a name="third-party-migration-toolstabthird-party-tools"></a>[Ferramentas de migração de terceiros](#tab/third-party-tools)

Várias ferramentas de migração de terceiros e serviços ISV podem ajudar você durante o processo de migração. Cada um oferece benefícios e vantagens diferentes. Essas ferramentas incluem:

## <a name="cloudamize"></a>Cloudamize

O Cloudamize é um serviço ISV que abrange todas as fases da estratégia de migração.

[Saiba mais](https://www.cloudamize.com)

## <a name="zerto"></a>Zerto

O Zerto fornece replicação virtual para os ambientes Microsoft Hyper-V e VMware vSphere.

[Saiba mais](https://www.zerto.com/solutions/use-cases/data-center-migration-software)

## <a name="carbonite"></a>Carbonite

O Carbonite fornece soluções de migração de servidores e dados para migrar cargas de trabalho para, de ou entre qualquer ambiente físico, virtual ou baseado em nuvem.

[Saiba mais](https://www.carbonite.com/data-protection/data-migration-software)

## <a name="movere"></a>Movere

O Movere é uma solução de descoberta que fornece os dados e as informações necessárias para planejar migrações de nuvem e otimizar, monitorar e analisar continuamente os ambientes de TI com confiança.

[Saiba mais](https://www.movere.io)

Visite o [Centro de Migração do Azure](https://azure.microsoft.com/migration/support) para descobrir organizações que oferecem soluções de tecnologia de parceiros prontas para uso que se ajustam aos seus cenários de migração e saber mais sobre ferramentas adicionais de migração de terceiros e serviços de suporte.

# <a name="project-management-toolstabproject-management-tools"></a>[Ferramentas de gerenciamento de projetos](#tab/project-management-tools)

Projetos que não são rastreados e gerenciados têm mais chances de ter problemas. Para garantir um resultado bem-sucedido, achamos importante usar uma ferramenta de gerenciamento de projetos. Existem muitas ferramentas diferentes disponíveis e os gerentes de projeto em sua organização já devem ter um favorito. A Microsoft oferece as seguintes ferramentas de gerenciamento de projetos, que podem funcionar juntas para fornecer recursos mais amplos:

- [Microsoft Planner](https://tasks.office.com): Uma maneira simples e visual de organizar o trabalho em equipe.
- [Microsoft Project](https://products.office.com/project/project-and-portfolio-management-software): Gerenciamento de projetos e portfólios, gerenciamento de capacidade de recursos, gerenciamento financeiro, gerenciamento de horários e cronogramas.
- [Microsoft Teams](https://products.office.com/microsoft-teams): Colaboração em equipe e ferramenta de comunicação. Além disso, o Teams é integrado ao Planner e outras ferramentas para aprimorar ainda mais a colaboração.
- [Azure DevOps](https://dev.azure.com): Com o Azure DevOps, você pode gerenciar sua infraestrutura como código ou usar os itens e quadros corporativos para executar o gerenciamento de projetos. Conforme seus projetos tomam forma, sua organização pode aproveitar as vantagens do CI/CD.

E essas não são as únicas ferramentas disponíveis. Muitas outras ferramentas de terceiros são amplamente usadas na comunidade de gerenciamento de projetos.

## <a name="set-up-for-devops"></a>Configuração do DevOps

À medida que você migra para as tecnologias de nuvem, isso representa uma grande oportunidade de configurar sua organização para DevOps e CI/CD. Mesmo que sua organização esteja apenas gerenciando a infraestrutura, ao começar a fazê-lo usando códigos e os padrões e práticas do setor para DevOps, você pode aumentar sua agilidade por meio de pipelines de CI/CD, permitindo que você se adapte mais rápido a cenários de mudanças, crescimentos, lançamentos e até mesmo de recuperação.

O [Azure DevOps](https://dev.azure.com) fornece toda a funcionalidade e integração necessárias com o Azure, no local ou até mesmo com outras nuvens. Saiba mais [aqui](https://azure.microsoft.com/services/devops). Para obter um treinamento guiado, confira [CI e CD com o DevOps do Azure - Início Rápido](https://microsoft.github.io/PartsUnlimited/pandp/200.1x-PandP-CICDQuickstartwithVSTS.html).

# <a name="cost-managementtabmanagecost"></a>[Gerenciamento de Custos](#tab/ManageCost)

À medida que você migra recursos para o ambiente de nuvem, é importante executar uma análise de custo periódica. Isso ajuda a evitar encargos de uso inesperado, pois o processo de migração pode impor custos sobre requisitos de uso adicionais em seus serviços. Você também pode redimensionar recursos conforme necessário para equilibrar custo e carga de trabalho (discutido em mais detalhes na seção **[Otimizar e Transformar](optimize-and-transform.md)** ).