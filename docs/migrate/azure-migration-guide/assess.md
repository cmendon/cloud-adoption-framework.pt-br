---
title: Avaliar cada carga de trabalho e refinar planos
description: Esta seção do guia de migração do Azure ajuda você a avaliar o seu ambiente para determinar o que deve ser migrado e quais métodos de migração devem ser considerados.
author: matticusau
ms.author: mlavery
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 40e62a05101e14fcd7507011d521521e58920ffc
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78225541"
---
# <a name="assess-each-workload-and-refine-plans"></a>Avaliar cada carga de trabalho e refinar planos

Os recursos neste guia ajudam a avaliar cada carga de trabalho, a desafiar suposições sobre a adequação de cada carga de trabalho para migração e a finalizar as decisões arquitetônicas sobre as opções de migração.

<!-- markdownlint-disable MD025 -->

# <a name="tools"></a>[Ferramentas](#tab/Tools)

Se você não seguir as diretrizes nos links acima, provavelmente precisará de dados e de uma ferramenta de avaliação para tomar decisões informadas sobre migração. As Migrações para Azure são a ferramenta nativa para avaliar **e** migrar para o Azure. Se você ainda não fez isso, use essas etapas para criar um projeto de migração de servidor e coletar os dados necessários.

## <a name="azure-migrate"></a>Migrações para Azure

As Migrações para Azure avaliam as infraestruturas locais, os aplicativos e os dados para a migração para o Azure. Esse serviço:

- Avalia a adequação da migração de ativos locais.
- Realiza dimensionamento com base no desempenho.
- Fornece estimativas de custo para a execução de ativos locais no Azure.

Caso esteja considerando uma abordagem "lift-and-shift" ou esteja nos estágios iniciais de avaliação da migração, este serviço será perfeito para você. Depois de concluir a avaliação, use as Migrações para Azure a fim de executar a migração.

![Visão geral das Migrações para Azure](./media/assess/azure-migrate-overview-1.png)

### <a name="create-a-new-server-migration-project"></a>Crie um projeto de migração de servidor

Comece a avaliação de migração do servidor usando as Migrações para Azure por meio destas etapas:

1. Selecione **Migrações para Azure**.
1. Em **Visão Geral**, selecione **Avaliar e migrar servidores**.
1. Selecione **Adicionar ferramentas**.
1. Em **Descobrir, avaliar e migrar servidores**, selecione **Adicionar ferramentas**.
1. Em **Migrar projeto**, selecione sua assinatura do Azure e crie um grupo de recursos, caso não tenha um.
1. Em **Detalhes do Projeto**, especifique o nome do projeto e a geografia em que deseja criá-lo. Em seguida, clique em **Avançar**.
1. Em **Selecionar ferramenta de avaliação**, selecione **Ignorar a adição de uma ferramenta de avaliação por enquanto > Avançar**.
1. Em **Selecionar ferramenta de migração**, selecione **Migrações para Azure: Migração de servidor > Avançar**.
1. Em **Analisar + adicionar ferramentas**, examine as configurações e selecione **Adicionar ferramentas**.
1. Depois de adicionar a ferramenta, ela aparecerá em **Projeto de Migrações para Azure > Servidores > Ferramentas de migração**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview]" submitText="Assess and migrate servers" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Saiba mais

- [Visão geral das Migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-services-overview)
- [Migrar servidores físicos ou virtualizados para o Azure](https://docs.microsoft.com/azure/migrate/tutorial-migrate-physical-virtual-machines)
- [Migrações para Azure no portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)

::: zone-end

## <a name="service-map"></a>Mapa do Serviço

O Mapa do Serviço descobre automaticamente os componentes de aplicativo em sistemas Windows e Linux e mapeia a comunicação entre os serviços. Com o Mapa do Serviço é possível exibir seus servidores da maneira desejada: como sistemas interconectados que fornecem serviços críticos. O Mapa do Serviço mostra conexões entre servidores, processos, latência de conexão de entrada e saída e portas em qualquer arquitetura conectada a TCP, sem a necessidade de configuração diferente da instalação de um agente.

As Migrações para Azure usam o Mapa do Serviço para aprimorar os recursos de geração de relatórios e as dependências em todo o ambiente. Para ver os detalhes completos dessa integração, confira [Visualização de dependência](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization). Se você usar o serviço de Migração para Azure, não serão necessárias etapas adicionais para configurar e obter os benefícios do Mapa do Serviço. As instruções a seguir são fornecidas como referência, caso você deseje usar o Mapa do Serviço para outras finalidades ou projetos.

### <a name="enable-dependency-visualization-using-service-map"></a>Habilitar a visualização de dependência usando o Mapa do Serviço

Para usar a visualização de dependência, baixe e instale agentes em cada computador local que você deseja analisar.

- [O MMA (Microsoft Monitoring Agent)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) precisa ser instalado em cada máquina.
- O [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) precisa ser instalado em cada computador.
- Além disso, se você tem computadores sem conectividade com a Internet, baixe e instale o gateway do Log Analytics neles.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>Saiba mais

- [Usando a solução do Mapa do Serviço no Azure](https://docs.microsoft.com/azure/azure-monitor/insights/service-map)
- [Mapa do Serviço e Migrações para Azure: Visualização de dependências](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization)

# <a name="challenge-assumptions"></a>[Desafiar suposições](#tab/Challenge-Assumptions)

Em uma migração ideal, todos os ativos (infraestrutura, aplicativo ou dados) seriam compatíveis com uma plataforma de nuvem e estariam prontos para migração ou modernização. Porém, na realidade, nem toda carga de trabalho deve ser migrada para a nuvem. Nem todo recurso é compatível com plataformas de nuvem. Antes de migrar uma carga de trabalho para a nuvem, avalie cada carga de trabalho e todos os ativos dependentes (infraestrutura, aplicativos e dados).

A [metodologia de plano do Cloud Adoption Framework](../../plan/index.md) aconselha os leitores a usarem as abordagens de [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization) e [poder de 10](../../digital-estate/rationalize.md#release-planning) para avaliar e planejar a migração. Essa orientação também inclui uma melhor prática detalhada para [usar as Migrações para Azure para avaliar seu patrimônio digital](../../plan/contoso-migration-assessment.md).

Os links acima sugerem que as suposições são aceitáveis e geralmente incentivadas durante os estágios de planejamento da migração. Mas agora é hora de agir. Essas suposições devem ser desafiadas conforme a carga de trabalho antes da migração para a nuvem.

## <a name="two-steps-of-incremental-rationalization"></a>Duas etapas da racionalização incremental

Duas etapas igualmente ponderadas são necessárias para entregar com êxito a [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization). Ambas as etapas exigem dados e insights sobre o ambiente. No entanto, cada abordagem respeita a quantidade de tempo e a granularidade dos detalhes necessários para ser bem-sucedida em um esforço de migração.

- **[Planejamento de lançamento do Poder de 10](../../digital-estate/rationalize.md#release-planning):** Durante a racionalização inicial e o planejamento de lançamento, somente um dos [cinco Rs de racionalização](../../digital-estate/5-rs-of-rationalization.md) será usado na avaliação. Faça estimativas e planos com base na opção de racionalização que melhor se alinha às motivações gerais definidas no [documento de Estratégia de Adoção de Nuvem](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx).

- **Avaliação detalhada de cada carga de trabalho:** As suposições associadas ao planejamento de lançamento do Poder de 10 são aceitáveis o suficiente para criar um plano. Mas essas mesmas suposições poderão causar problemas significativos se não forem avaliadas antes da migração.

## <a name="challenge-assumptions-and-update-the-plan"></a>Desafiar as suposições e atualizar o plano

Examine de maneira minuciosa os dados de avaliação nas Migrações para Azure ou na ferramenta de avaliação escolhida. Esses dados fornecerão insights sobre problemas de compatibilidade, requisitos de correção, sugestões de dimensionamento e outras considerações.

Antes da migração, use esses dados, juntamente com conversas de descoberta com o proprietário do produto, as equipes de desenvolvimento, os administradores e outros para avaliar a viabilidade de migrar essa carga de trabalho específica. Use essa descoberta para desafiar suposições principais sobre essa carga de trabalho. Se as descobertas alterarem o plano de migração ou de adoção, atualize o plano adequadamente.

A primeira etapa para desafiar essas suposições é uma [revisão de todos os cinco Rs](../../digital-estate/rationalize.md).

    - A abordagem de racionalização assumida funciona para essa carga de trabalho? É a melhor abordagem?
    - Qualquer uma das [físicas de replicação](../migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication) afetará a migração dessa carga de trabalho?
    - Essa carga de trabalho requer alguma [atividade de correção](../migration-considerations/assess/evaluate.md) antes da migração?

Esses tipos de perguntas ajudam a desafiar as suposições e levam ao melhor caminho para cada carga de trabalho.

Para obter uma lista estendida de perguntas e um processo definido para validar suposições, confira a [visão geral das melhorias do processo de avaliação](../migration-considerations/assess/index.md).

# <a name="scenarios-and-stakeholders"></a>[Cenários e stakeholders](#tab/Scenarios)

## <a name="scenarios"></a>Cenários

Este guia abrange os seguintes cenários:

- **Hardware herdado:** migre para remover uma dependência de hardware herdado cujo prazo de suporte está próximo do fim ou está obsoleto.
- **Aumento da capacidade:** aumente a capacidade de ativos (infraestrutura, aplicativos e dados) que sua infraestrutura atual não pode fornecer.
- **Modernização do datacenter:** amplie ou modernize o datacenter com tecnologia de nuvem para aumentar a competitividade e atualizar sua empresa.
- **Modernização de aplicativo ou serviço:** atualize aplicativos para que estes possam aproveitar os recursos nativos de nuvem. Mesmo que seu objetivo inicial seja uma estratégia de migração com nova hospedagem, a capacidade de criar planos de revisão de aplicativos ou serviços e potencializar a modernização é um processo comum em qualquer migração.

### <a name="organizational-alignment-and-stakeholders"></a>Alinhamento organizacional e stakeholders

A lista completa de stakeholders varia para cada projeto de migração. É melhor assumir que você não conhecerá todos os stakeholders no início do planejamento da migração, uma vez que eles frequentemente são identificados apenas durante certas fases do projeto. No entanto, antes de iniciar qualquer projeto de migração, identifique os principais líderes de negócios em grupos financeiros, de infraestrutura de TI e de aplicativos que têm interesse nos esforços gerais de migração na nuvem da organização.

O estabelecimento de uma equipe central de estratégia em nuvem, criada pensando nesses principais stakeholders de alto nível, pode ajudar a preparar sua organização para a adoção da nuvem e orientar seus esforços gerais de migração para a nuvem. Essa equipe será responsável por entender as tecnologias de nuvem e os processos de migração, identificando a justificativa comercial das migrações e determinando as melhores soluções de alto nível para os esforços de migração. Ela também ajudará a identificar e trabalhar com aplicativos específicos e parceiros comerciais para garantir uma migração bem-sucedida.

Para obter mais informações sobre como preparar sua organização para os esforços de migração para a nuvem, confira as orientações do Cloud Adoption Framework sobre o [alinhamento inicial da organização](../../plan/initial-org-alignment.md).

# <a name="timelines"></a>[Linhas do tempo](#tab/Timelines)

Geralmente, os clientes acham que o cenário de migração abordado por este guia pode ser concluído de um a seis meses.

Ao avaliar a linha do tempo da sua migração, considere:

- **Migração de ativos (infraestrutura, aplicativos e dados):** O número e diversidade de ativos.
- **Preparação da equipe:** sua equipe está pronta para gerenciar o novo ambiente ou precisa de treinamento?
- **Financiamento:** Você tem a aprovação e o orçamento apropriados para concluir a migração?
- **Gerenciamento de alterações:** Sua empresa possui requisitos específicos relacionados à implementação e aprovação de alterações?
- **Regulamentos do setor:** Você precisa estar em conformidade com os regulamentos do setor ou da indústria?

# <a name="cost-management"></a>[Gerenciamento de Custos](#tab/ManageCost)

Avaliar seu ambiente proporciona uma grande oportunidade de incluir uma etapa de análise de custo. Usando os dados coletados pelas atividades de avaliação, você deve conseguir analisar e prever custos. Essa previsão de custos deve fatorar os custos do serviço de consumo, além de quaisquer custos únicos (como o aumento da entrada de dados).

Durante a migração, certos fatores podem afetar as decisões e atividades de execução:

- **Tamanho da propriedade digital:** Entender o tamanho do seu patrimônio digital afetará diretamente as decisões e os recursos necessários para realizar a migração.
- **Modelos contábeis:** Mudança de um modelo estruturado de despesas de capital para um modelo de despesas operacionais líquidas.

::: zone target="docs"

Os seguintes recursos fornecem informações relacionadas:

- [Estimar custos de nuvem](../migration-considerations/assess/estimate.md)

::: zone-end
