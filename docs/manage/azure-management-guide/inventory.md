---
title: Inventário e visibilidade no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como configurar inventário, monitoramento, relatórios e alertas para seu ambiente de gerenciamento do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 4969681cbc6fbb71da70f3ced09b5e4616c773b5
ms.sourcegitcommit: 7df593a67a2e77b5f61c815814af9f0c36ea5ebd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75781769"
---
# <a name="inventory-and-visibility-in-azure"></a>Inventário e visibilidade no Azure

_Inventário e visibilidade_ é a primeira de três disciplinas em uma linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

Esta disciplina vem em primeiro lugar porque é essencial coletar dados operacionais adequados ao tomar decisões sobre as operações. As equipes de gerenciamento de nuvem devem entender o que é gerenciado e qual é o desempenho da operação desses ativos. Este artigo descreve as diferentes ferramentas que fornecem um inventário e uma visibilidade sobre o estado de execução do inventário.

Para qualquer ambiente de nível empresarial, a tabela a seguir descreve o mínimo sugerido para uma linha de base de gerenciamento.

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Monitorar a integridade de serviços do Azure|Integridade do Serviço do Azure|Integridade, desempenho e diagnóstico para serviços em execução no Azure|
|Centralização de log|Log Analytics|Log central para fins de visibilidade|
|Centralização do monitoramento|Azure Monitor|Monitoramento central de tendências e dados operacionais|
|Inventário de máquinas virtuais e controle de alterações|Controle de Alterações e Inventário do Azure|Inventariar VMs e monitorar alterações para o nível do SO convidado|
|Monitoramento de assinatura|Log de Atividades do Azure|Monitoramento de alterações no nível da assinatura|
|Monitoramento de SO convidado|Azure Monitor para VMs|Monitoramento de alterações e do desempenho de VMs|
|Monitoramento de rede|Observador de Rede do Azure|Monitoramento de alterações e desempenho de rede|
|Monitoramento de DNS|Análise de DNS|Segurança, desempenho e operações do DNS|

::: zone target="docs"

## <a name="azure-service-health"></a>Integridade do Serviço do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-service-healthtabazureservicehealth"></a>[Integridade do Serviço do Azure](#tab/AzureServiceHealth)

::: zone-end

A Integridade do Serviço do Azure fornece uma exibição personalizada da integridade de seus serviços e das regiões do Azure. Informações sobre os problemas ativos são postadas na Integridade do Serviço para ajudar você a entender o impacto em seus recursos. As atualizações regulares mantêm você informado enquanto o problema é resolvido.

Também publicamos eventos de manutenção planejada na Integridade do Serviço para que você saiba sobre as alterações que podem afetar a disponibilidade dos recursos. Configure alertas de Integridade do Serviço para ser notificado quando problemas de serviço, manutenção planejada ou outras alterações puderem afetar os serviços e as regiões do Azure.

A Integridade do Serviço do Azure inclui:

- **Status do Azure:** uma exibição global da integridade dos serviços do Azure.
- **Integridade de serviço:** uma visão personalizada da integridade de seus serviços do Azure.
- **Resource Health:** Uma visão mais profunda sobre a integridade de cada um de seus recursos.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para configurar um alerta da Integridade do Serviço:

1. Acesse **Integridade do Serviço**.
2. Selecione **Alertas de Integridade**.
3. Crie um alerta de integridade do serviço.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Para configurar um alerta da Integridade do Serviço, acesse o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, confira a [documentação da Integridade do Serviço do Azure](https://docs.microsoft.com/azure/service-health).

## <a name="log-analytics"></a>Log Analytics

::: zone-end
::: zone target="chromeless"

## <a name="log-analyticstablog-analytics"></a>[Log Analytics](#tab/Log-Analytics)

::: zone-end

Um [workspace do Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) é um ambiente exclusivo para dados de log do Azure Monitor. Cada workspace tem seu próprio repositório de dados e configuração. As fontes de dados e as soluções são configuradas para armazenar seus dados em determinados workspaces. As soluções de monitoramento do Azure exigem que todos os servidores estejam conectados a um workspace para que seus dados de log possam ser armazenados e acessados.

::: zone target="chromeless"

### <a name="action"></a>Ação

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.OperationalInsights%2Fworkspaces]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Saiba mais

Para saber mais confira, [Documentação de criação do workspace do Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace).

## <a name="azure-monitor"></a>Azure Monitor

::: zone-end
::: zone target="chromeless"

## <a name="azure-monitortabazure-monitor"></a>[Azure Monitor](#tab/Azure-Monitor)

::: zone-end

O Azure Monitor fornece um único Hub unificado para todos os dados de monitoramento e diagnóstico no Azure e oferece visibilidade em seus recursos. Com o Azure Monitor, você pode encontrar e corrigir problemas e otimizar o desempenho. Também é possível entender o comportamento do cliente.

- **Monitorar e visualizar métricas.** As métricas são valores numéricos disponíveis nos recursos do Azure. Elas ajudam você a entender a integridade de seus sistemas. Personalize gráficos para seus painéis e use pastas de trabalho nos relatórios.

- **Consultar e analisar logs.** os logs incluem logs de atividade e logs de diagnóstico do Azure. Colete logs adicionais de outras soluções de gerenciamento e monitoramento para os seus recursos em nuvem ou locais. O Log Analytics fornece um repositório central para agregar todos esses dados. Daí, você pode executar consultas para ajudar a solucionar problemas ou visualizar os dados.

- **Configurar alertas e ações.** Os alertas notificam você sobre condições críticas. Ações corretivas podem ser executadas com base em gatilhos de métricas, logs ou problemas de integridade do serviço. Você pode configurar diferentes notificações e ações, bem como também pode enviar dados para suas ferramentas de gerenciamento de serviços de TI.

::: zone target="chromeless"

### <a name="action"></a>Ação

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

 Comece a monitorar seu:

- [Aplicativos](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Contêineres](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Máquinas virtuais](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Redes](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Para monitorar outros recursos, encontre soluções adicionais no Azure Marketplace.

Para explorar o Azure Monitor, acesse o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação do Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

## <a name="onboard-solutions"></a>Integrar soluções

::: zone-end
::: zone target="chromeless"

## <a name="onboard-solutionstabconfigure-solutions"></a>[Integrar soluções](#tab/Configure-solutions)

::: zone-end

Para habilitar soluções, você precisa configurar o workspace do Log Analytics. As VMs do Azure e os servidores locais integrados obtêm as soluções dos workspaces do Log Analytics aos quais estão conectados.

Há duas abordagens para a integração:

- [VM individual](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
- [Assinatura inteira](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

Cada artigo orienta você por uma série de etapas para integrar essas soluções:

- Gerenciamento de atualizações
- Controle de Alterações e Inventário
- Log de Atividades do Azure
- Integridade do Agente do Azure Log Analytics
- Avaliação antimalware
- Azure Monitor para VMs
- Central de Segurança do Azure

Cada uma das etapas anteriores ajuda a estabelecer o inventário e a visibilidade.
