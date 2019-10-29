---
title: Monitoramento e relatórios no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como configurar monitoramento, relatórios e alertas para o seu ambiente de gerenciamento do Azure.
author: timleyden
ms.author: tileyden
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 5cb88bba1b82bf4255fb13f9ac9d415018316dec
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548890"
---
# <a name="monitoring-and-reporting-in-azure"></a>Monitoramento e relatórios no Azure

O Azure oferece vários serviços que, juntos, proporcionam uma solução abrangente para coletar, analisar e agir na telemetria de seus aplicativos e os recursos do Azure compatíveis com eles. Além disso, esses serviços podem estender para monitorar recursos críticos locais para fornecer um ambiente de monitoramento híbrido.

# <a name="azure-monitortabazuremonitor"></a>[Azure Monitor](#tab/AzureMonitor)

O Azure Monitor fornece um único hub unificado para todos os dados de monitoramento e diagnóstico no Azure. Você pode usá-lo para obter visibilidade em seus recursos. Com o Azure Monitor, você pode encontrar e corrigir problemas e otimizar o desempenho. Você também pode entender o comportamento do cliente.

- **Monitorar e visualizar métricas.** As métricas são valores numéricos disponíveis em recursos do Azure que ajudam você a entender a integridade dos seus sistemas. Personalize gráficos para seus painéis e use pastas de trabalho nos relatórios.

- **Consultar e analisar logs.** os logs incluem logs de atividade e logs de diagnóstico do Azure. Colete logs adicionais de outras soluções de gerenciamento e monitoramento para os seus recursos em nuvem ou locais. O Log Analytics oferece um repositório central para agregar todos esses dados. Daí, você pode executar consultas para ajudar a solucionar problemas ou visualizar os dados.

- **Configurar alertas e ações.** Alertas notificam você proativamente sobre condições críticas. Ações corretivas podem ser executadas com base nos gatilhos de métricas, logs ou problemas de integridade do serviço. Você pode configurar diferentes notificações e ações e enviar dados às suas ferramentas de gerenciamento de serviços de TI.

::: zone target="docs"

 Comece a monitorar seu:

- [Aplicativos](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Contêineres](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Máquinas virtuais](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Redes](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Para monitorar outros recursos, encontre soluções adicionais no Azure Marketplace.

Para explorar o Azure Monitor, acesse o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação do Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Ação

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

::: zone-end

# <a name="azure-service-healthtabazureservicehealth"></a>[Integridade do Serviço do Azure](#tab/AzureServiceHealth)

A Integridade do Serviço do Azure fornece uma exibição personalizada da integridade dos serviços do Azure e das regiões que você usa. As informações sobre os problemas ativos são postados na Integridade do Serviço para ajudá-lo a entender o impacto sobre seus recursos. As atualizações regulares mantêm você informado enquanto o problema é resolvido.

Também publicamos os eventos de manutenção planejada na Integridade do Serviço para que você saiba sobre as alterações que poderiam afetar a disponibilidade de seus recursos. Configure os alertas da Integridade do Serviço para ser notificado quando problemas de serviço, manutenção planejada ou outras alterações puderem afetar os serviços do Azure e as regiões que você usa.

A Integridade do Serviço do Azure inclui:

- **Status do Azure:** uma exibição global da integridade dos serviços do Azure.
- **Integridade de serviço:** uma visão personalizada da integridade de seus serviços do Azure.
- **Resource Health:** uma visão mais profunda da integridade de cada um de seus recursos.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

## <a name="action"></a>Ação

Para configurar um alerta da Integridade do Serviço:

1. Acesse **Integridade do Serviço**.
2. Selecione **Alertas de Integridade**.
3. Crie um alerta de integridade do serviço.

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

Para configurar um alerta da Integridade do Serviço, acesse o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, confira a [documentação da Integridade do Serviço do Azure](https://docs.microsoft.com/azure/service-health).

::: zone-end

# <a name="azure-advisortabazureadvisor"></a>[Assistente do Azure](#tab/AzureAdvisor)

O Assistente do Azure é um consultor de nuvem personalizado e gratuito que ajuda a seguir e implementar as melhores práticas de implantação do Azure. Ele analisa sua configuração de recurso e a telemetria de uso e recomenda soluções que podem ajudar a otimizar seu ambiente. As recomendações são divididas em quatro categorias:

- **Alta disponibilidade:** Para melhorar a continuidade dos aplicativos comercialmente críticos. Recomendações podem incluir adição de máquinas virtuais a um conjunto de disponibilidade ou adicionar pontos de extremidade com redundância geográfica.
- **Segurança:** Para detectar ameaças e vulnerabilidades que podem levar a violações de segurança. As recomendações podem incluir aplicar criptografia de disco ou habilitar os grupos de segurança de rede.
- **Desempenho:** Para melhorar a velocidade dos aplicativos. As recomendações podem incluir aumentar o desempenho de consultas SQL criando índices ou redefinindo as configurações do gerenciador de tráfego.
- **Custo:** Para otimizar e reduzir os gastos gerais do Azure. As recomendações podem incluir o redimensionamento ou o desligamento de máquinas virtuais subutilizadas ou alternar para as reservas do Azure para reduzir o custo total de propriedade.

As recomendações no Assistente se baseiam em recursos que você implanta e nas ações que você pode executar no Azure. Você pode verificar regularmente o Assistente para obter as recomendações mais recentes.

::: zone target="chromeless"

## <a name="action"></a>Ação

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Explore Azure Advisor" :::

::: zone-end

::: zone target="docs"

Para explorar o Assistente do Azure, acesse o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Expert/AdvisorBlade).

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação do Assistente do Azure](https://docs.microsoft.com/azure/advisor).

::: zone-end

# <a name="azure-security-centertabazuresecuritycenter"></a>[Central de Segurança do Azure](#tab/AzureSecurityCenter)

A Central de Segurança do Azure também desempenha um papel importante na sua estratégia de monitoramento. Ela pode ajudar você a monitorar a segurança de seus computadores, redes, armazenamento, serviços de dados e aplicativos. A Central de Segurança fornece detecção avançada de ameaças usando análise comportamental e aprendizado de máquina para ajudar a identificar ameaças ativas visando seus recursos do Azure. Também fornece proteção contra ameaças que bloqueia malware ou outros códigos indesejados e reduz a área de superfície exposta à força bruta e outros ataques à rede.

Quando a Central de Segurança identifica uma ameaça, ela dispara um alerta de segurança com etapas que precisam ser tomadas para responder a um ataque. Ele também fornece um relatório com informações sobre a ameaça que foi detectada.

A Central de Segurança do Azure é oferecida em duas camadas de serviço: gratuita e standard. Recursos como as recomendações de segurança estão disponíveis gratuitamente. A camada standard fornece proteção adicional, como detecção de ameaças avançada e proteção em suas cargas de trabalho de nuvem híbrida.

::: zone target="chromeless"

## <a name="action"></a>Ação

**Experimente o nível Standard gratuitamente pelos primeiros 30 dias.**

Depois de ativar e configurar as políticas de segurança para os recursos de uma assinatura, você poderá exibir o estado de segurança de seus recursos e todos os problemas na seção **Prevenção**. Você também pode exibir uma lista desses problemas no bloco **Recomendações** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Para explorar a Central de Segurança do Azure, vá para o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação da Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center).

::: zone-end
