---
title: Avaliar bens digitais
description: Avaliar bens digitais
author: matticusau
ms.author: mlavery
ms.date: 08/08/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 298cfc866e770e2dcd33a22d6cd4713e4053de25
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807063"
---
# <a name="assess-the-digital-estate"></a>Avaliar bens digitais

Em uma migração ideal, todos os ativos (infraestrutura, aplicativo ou dados) seriam compatíveis com uma plataforma de nuvem e prontos para migração. Mas na realidade, nem tudo deve ser migrado para a nuvem. Além disso, nem todo recurso é compatível com plataformas de nuvem. Antes de migrar uma carga de trabalho para a nuvem, é importante avaliar a carga de trabalho e cada ativo relacionado (infraestrutura, aplicativos e dados).

Os recursos desta seção ajudarão você a avaliar seu ambiente para determinar sua adequação à migração e quais métodos devem ser considerados.

<!-- markdownlint-disable MD025 -->

# <a name="toolstabtools"></a>[Ferramentas](#tab/Tools)

As ferramentas a seguir ajudarão você a avaliar seu ambiente para determinar a adequação da migração e a melhor abordagem de uso. Para obter informações úteis sobre como escolher as ferramentas certas para apoiar aos seus esforços de migração, confira o [Guia de decisão das ferramentas de migração da Estrutura de Adoção de Nuvem](../../decision-guides/migrate-decision-guide/index.md).

## <a name="azure-migrate"></a>Migrações para Azure

O serviço de Migrações para Azure avalia as infraestruturas locais, os aplicativos e os dados para migração para o Azure. O serviço avalia a adequação da migração de ativos locais, realiza o dimensionamento com base no desempenho e fornece estimativas de custo para a execução de ativos locais no Azure. Caso esteja considerando usar as migrações "lift and shift" ou esteja nos estágios iniciais de avaliação da migração, este serviço será perfeito para você. Depois de concluir a avaliação, as Migrações para Azure podem ser usadas para executar a migração.

![Visão geral das Migrações para Azure](./media/assess/azuremigrate-overview-1.png)

### <a name="create-a-new-server-migration-project"></a>Crie um projeto de migração de servidor

Para começar a usar uma avaliação de migração do servidor usando as Migrações para Azure, siga essas etapas:

1. Selecione **Migrações para Azure**.
1. Em **Visão Geral**, clique em **Avaliar emigrar servidores**.
1. Selecione **Adicionar ferramentas**.
1. Em **Descobrir, avaliar e migrar servidores**, clique em **Adicionar ferramentas**.
1. Em **Migrar projeto**, selecione sua assinatura do Azure e crie um grupo de recursos, caso não tenha um.
1. Em **Detalhes do Projeto**, especifique o nome do projeto e a geografia em que deseja criar o projeto e clique em **Avançar**.
1. Em **Selecionar ferramenta de avaliação**, selecione **Ignorar a adição de uma ferramenta de avaliação por enquanto > Avançar**.
1. Em **Selecionar ferramenta de migração**, selecione **Migrações para Azure: Migração de servidor > Avançar**.
1. Em **Examinar + adicionar ferramentas**, examine as configurações e clique em **Adicionar ferramentas**
1. Depois de adicionar a ferramenta, ela aparecerá em **Projeto de Migrações para Azure > Servidores > Ferramentas de migração**.

::: zone target="chromeless"

::: form action="Blade[#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview]" submitText="Assess and migrate servers" :::

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Saiba mais

- [Visão geral das Migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-services-overview)
- [Migrar servidores físicos ou virtualizados para o Azure](https://docs.microsoft.com/azure/migrate/tutorial-migrate-physical-virtual-machines)
- [Migrações para Azure no portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)

::: zone-end

## <a name="service-map"></a>Mapa do Serviço

O Mapa do Serviço descobre automaticamente os componentes de aplicativo em sistemas Windows e Linux e mapeia a comunicação entre os serviços. Com o Mapa do Serviço é possível exibir seus servidores da maneira desejada: como sistemas interconectados que fornecem serviços críticos. O Mapa do Serviço mostra conexões entre servidores, processos, latência de conexão de entrada e saída e portas em qualquer arquitetura conectada a TCP, sem a necessidade de configuração diferente da instalação de um agente.

As Migrações para Azure usam o Mapa do Serviço para aprimorar os recursos de geração de relatórios e as dependências em todo o ambiente. Veja os detalhes completos dessa integração descritos em [Visualização de dependência](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization). Se você usar o serviço de Migração para Azure, não serão necessárias etapas adicionais para configurar e obter os benefícios do Mapa do Serviço. As instruções a seguir são fornecidas como referência, caso você deseje usar o Mapa do Serviço para outras finalidades ou projetos.

### <a name="enable-dependency-visualization-using-service-map"></a>Habilitar a visualização de dependência usando o Mapa do Serviço

Para usar a visualização de dependência, você precisa baixar e instalar agentes em cada computador local que você deseja analisar.

- [O Microsoft Monitoring Agent (MMA)](https://docs.microsoft.com/azure/log-analytics/log-analytics-agent-windows) precisa ser instalado em cada máquina.
- O [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud#install-the-dependency-agent-on-windows) precisa ser instalado em cada computador.
- Além disso, se você tiver máquinas sem conectividade com a Internet, será necessário fazer o download e instalar o gateway do Log Analytics nelas.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>Saiba mais

- [Usando a solução do Mapa do Serviço no Azure](https://docs.microsoft.com/azure/azure-monitor/insights/service-map)
- [Mapa do Serviço e Migrações para Azure: Visualização de dependências](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization)

# <a name="scenarios-and-stakeholderstabscenarios"></a>[Cenários e Stakeholders](#tab/Scenarios)

## <a name="scenarios"></a>Cenários

Este guia tem como foco os seguintes cenários:

- **Hardware herdado:** a migração está sendo feita para remover uma dependência de hardware herdado cujo prazo de suporte está próximo do fim ou está obsoleto.
- **Aumento da capacidade:** há a necessidade de se aumentar a capacidade de ativos (infraestrutura, aplicativos e dados), o que sua infraestrutura não pode fornecer.
- **Modernização do datacenter:** há a necessidade de ampliar ou modernizar o datacenter com tecnologia de nuvem para aumentar a competitividade e atualizar sua empresa.
- **Modernização de aplicativo ou serviço:** há uma necessidade de atualizar aplicativos para que estes possam aproveitar os recursos nativos da nuvem. Mesmo que uma estratégia de migração com nova hospedagem seja seu objetivo inicial, a capacidade de criar planos de revisão de aplicativos ou serviços e potencializar a modernização é um processo comum em qualquer migração.

### <a name="organizational-alignment-and-stakeholders"></a>Alinhamento organizacional e stakeholders

A lista completa de stakeholders varia para cada projeto de migração. É melhor assumir que você não conhecerá todos os stakeholders no início do planejamento de uma migração, uma vez que eles frequentemente são identificados apenas durante certas fases do projeto. No entanto, antes de iniciar qualquer projeto de migração, você pode identificar os principais líderes de negócios em grupos financeiros, de infraestrutura de TI e de aplicativos que terão interesse nos esforços gerais de migração na nuvem da organização.

O estabelecimento de uma equipe central de estratégia em nuvem, criada pensando nesses principais stakeholders de alto nível, pode ajudar a preparar sua organização para a adoção da nuvem e orientar seus esforços gerais de migração para a nuvem. Essa equipe será responsável por entender as tecnologias de nuvem e os processos de migração, identificando a justificativa comercial das migrações e determinando as melhores soluções de alto nível para os esforços de migração. Ela também ajudará a identificar e trabalhar com aplicativos específicos e parceiros comerciais para garantir uma migração bem-sucedida.

Para obter mais informações sobre como preparar sua organização para esforços de migração para a nuvem confira o artigo da Estrutura de Adoção de Nuvem no [alinhamento inicial da organização](../../plan/initial-org-alignment.md).

# <a name="timelinestabtimelines"></a>[Linhas do tempo](#tab/Timelines)

De maneira geral, os clientes acham que o cenário de migração abordado por este guia pode ser concluído em um a seis meses.

Alguns dos fatores a serem considerados ao avaliar a linha do tempo da sua migração são:

- **Migração de ativos (infraestrutura, aplicativos e dados):** O número e diversidade de ativos.
- **Preparação da equipe:** Sua equipe está pronta para gerenciar o novo ambiente ou precisa de treinamento?
- **Financiamento:** Você tem a aprovação e o orçamento apropriados para concluir a migração?
- **Gerenciamento de alterações:** Sua empresa possui requisitos específicos relacionados à implementação e aprovação de alterações?
- **Regulamentos do setor:** Você precisa estar em conformidade com os regulamentos do setor ou da indústria?

# <a name="cost-managementtabmanagecost"></a>[Gerenciamento de Custos](#tab/ManageCost)

Durante o processo de avaliação de seu ambiente, aproveite essa oportunidade para incluir uma etapa de análise de custos. Usando os dados coletados pelas atividades de avaliação, você deve conseguir analisar e prever custos. Essa previsão de custos deve fatorar os custos do serviço de consumo, além de quaisquer custos únicos (como o aumento da entrada de dados).

Durante a migração, certos fatores podem afetar as decisões e atividades de execução:

- **Tamanho da propriedade digital:** Entender o tamanho do seu patrimônio digital afetará diretamente as decisões e os recursos necessários para realizar a migração.
- **Modelos contábeis:** Mudança de um modelo estruturado de despesas de capital para um modelo de despesas operacionais líquidas.

::: zone target="docs"

Os seguintes recursos fornecem informações relacionadas:

- [Estimar custos de nuvem](../migration-considerations/assess/estimate.md)

::: zone-end
