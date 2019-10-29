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
ms.openlocfilehash: 8b7902910de3df729524b1625fe83b0681eeef5b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556778"
---
# <a name="inventory-and-visibility-in-azure"></a>Inventário e visibilidade no Azure

_Inventário e visibilidade_ é a primeira de três disciplinas em uma linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

Essa disciplina vem em primeiro lugar, porque é essencial coletar dados operacionais adequados ao tomar decisões sobre operações. As equipes de gerenciamento de nuvem precisam entender o que está sendo gerenciado e qual é o desempenho da operação desses ativos. Este artigo percorre as várias ferramentas que fornecem um inventário e visibilidade sobre o estado de execução do inventário.

Para qualquer ambiente de nível corporativo, a tabela a seguir descreve o mínimo sugerido para qualquer linha de base de gerenciamento.

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Monitorar a integridade de serviços do Azure|Integridade do Serviço do Azure|Integridade, desempenho e diagnóstico para serviços em execução no Azure|
|Centralização de log|Log Analytics|Log central para fins de visibilidade|
|Centralização do monitoramento|Azure Monitor|Monitoramento central de tendências e dados operacionais|
|Inventário de VM e Controle de Alterações|Controle de Alterações do Azure e Serviço de Inventário|Inventariar VMs e monitorar alterações no nível do SO convidado|
|Integridade do Serviço|Log de Atividades do Azure|Monitorar alterações no nível da assinatura|
|Monitoramento de SO convidado|Azure Monitor para VMs|Monitorar alterações e o desempenho de VMs|
|Monitoramento de rede|Observador de Rede do Azure|Monitorar alterações e o desempenho de rede|
|Monitoramento de DNS|Análise de DNS|Segurança, desempenho e operações de DNS|

::: zone target="docs"

## <a name="azure-service-health"></a>Integridade do Serviço do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-service-healthtabazureservicehealth"></a>[Integridade do Serviço do Azure](#tab/AzureServiceHealth)

::: zone-end

A Integridade do Serviço do Azure fornece uma exibição personalizada da integridade dos serviços do Azure e das regiões que você usa. As informações sobre os problemas ativos são postados na Integridade do Serviço para ajudá-lo a entender o impacto sobre seus recursos. As atualizações regulares mantêm você informado enquanto o problema é resolvido.

Também publicamos os eventos de manutenção planejada na Integridade do Serviço para que você saiba sobre as alterações que poderiam afetar a disponibilidade de seus recursos. Configure os alertas da Integridade do Serviço para ser notificado quando problemas de serviço, manutenção planejada ou outras alterações puderem afetar os serviços do Azure e as regiões que você usa.

A Integridade do Serviço do Azure inclui:

- **Status do Azure:** uma exibição global da integridade dos serviços do Azure.
- **Integridade de serviço:** uma visão personalizada da integridade de seus serviços do Azure.
- **Resource Health:** uma visão mais profunda da integridade de cada um de seus recursos.

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

O Azure Monitor fornece um único hub unificado para todos os dados de monitoramento e diagnóstico no Azure. Você pode usá-lo para obter visibilidade em seus recursos. Com o Azure Monitor, você pode encontrar e corrigir problemas e otimizar o desempenho. Você também pode entender o comportamento do cliente.

- **Monitorar e visualizar métricas.** As métricas são valores numéricos disponíveis em recursos do Azure que ajudam você a entender a integridade dos seus sistemas. Personalize gráficos para seus painéis e use pastas de trabalho nos relatórios.

- **Consultar e analisar logs.** os logs incluem logs de atividade e logs de diagnóstico do Azure. Colete logs adicionais de outras soluções de gerenciamento e monitoramento para os seus recursos em nuvem ou locais. O Log Analytics oferece um repositório central para agregar todos esses dados. Daí, você pode executar consultas para ajudar a solucionar problemas ou visualizar os dados.

- **Configurar alertas e ações.** Alertas notificam você proativamente sobre condições críticas. Ações corretivas podem ser executadas com base nos gatilhos de métricas, logs ou problemas de integridade do serviço. Você pode configurar diferentes notificações e ações e enviar dados às suas ferramentas de gerenciamento de serviços de TI.

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

Para habilitar soluções, você precisa configurar o workspace do Log Analytics. As VMs do Azure e os servidores locais integrados receberão as soluções dos workspaces do Log Analytics ao quais estão conectados.

Há duas abordagens para a integração:

- [VM individual](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
- [Assinatura inteira](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

Cada artigo orientará você em uma série de etapas para integrar as seguintes soluções:

- Gerenciamento de atualizações
- Controle de Alterações e Inventário
- Log de Atividades do Azure
- Integridade do Agente do Azure Log Analytics
- Avaliação antimalware
- Azure Monitor para VMs
- Central de Segurança do Azure

Cada uma das opções acima ajudará a estabelecer o inventário e a visibilidade.
