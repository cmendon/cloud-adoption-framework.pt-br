---
title: Especialização de carga de trabalho para gerenciamento de nuvem no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhorar as operações de gerenciamento de nuvem específicas da carga de trabalho
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 51bdf23ccb2262202dfa095c5e9b57f727d11d3b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556982"
---
# <a name="workload-specialization-for-cloud-management"></a>Especialização de carga de trabalho para gerenciamento de nuvem

A especialização de carga de trabalho baseia-se nos conceitos descritos na [Especialização de Plataforma](./platform-specialization.md).

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:** Maior investimento de operações por carga de trabalho. Grau mais alto de resiliência. Sugerido para +/- 20% das cargas de trabalho que orientam o valor comercial. Reservado geralmente para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:** O investimento de operações é distribuído entre muitas cargas de trabalho. As melhorias de resiliência afetam todas as cargas de trabalho que usam a plataforma definida. Sugerido para +/- 20% das plataformas de maior criticalidade. Reservado geralmente para cargas de trabalho de criticalidade média a alta.
- **Linha de base de gerenciamento aprimorada:** Menor investimento de operações relativo. Compromissos de negócios ligeiramente aprimorados usando ferramentas e processos de operações nativos de nuvem adicionais.

## <a name="high-level-process"></a>Processo de alto nível

A especialização de carga de trabalho consiste em uma execução disciplinada dos quatro processos a seguir em uma abordagem iterativa. Cada processo é explicado mais detalhadamente no artigo [Especialização de Plataforma](./platform-specialization.md).

- **Melhorar o design do sistema:** melhore o design de uma carga de trabalho específica para minimizar interrupções efetivamente.
- **Automatizar a correção:** algumas melhorias não são econômicas. Nesses casos, talvez faça mais sentido automatizar a correção e reduzir o impacto de interrupções.
- **Dimensionar a solução:** à medida que o design dos sistemas e a correção automatizada são aprimorados, essas alterações podem ser dimensionadas em todo o ambiente por meio do catálogo de serviços.
- **Melhoria contínua:** várias ferramentas de monitoramento podem ser usadas para descobrir melhorias incrementais que podem ser abordadas na próxima etapa do design, da automação e da escala do sistema.

## <a name="cultural-change"></a>Mudança cultural

A especialização de carga de trabalho geralmente aciona uma mudança cultural. A TI tradicional cria processos que se concentram em oferecer uma linha de base de gerenciamento, linhas de bases aprimoradas e operações de plataforma. Esses tipos de oferta podem ser dimensionados em todo o ambiente. A especialização de carga de trabalho é muito semelhante, na execução, à especialização de plataforma. Mas, ao contrário das plataformas comuns, a especialização exigida por cargas de trabalho individuais geralmente não é dimensionada.

Quando a especialização de carga de trabalho é necessária, é comum que o gerenciamento operacional evolua para além de uma perspectiva de TI Central. A abordagem sugerida no Cloud Adoption Framework é uma distribuição de funcionalidades de gerenciamento de nuvem.

Nesse modelo, as tarefas operacionais como monitoramento, implantação, DevOps e outras funções focadas em inovação são deslocadas para um desenvolvimento de aplicativo ou uma organização de unidade de negócios. A equipe de Plataforma de Nuvem e a equipe principal de Monitoramento de Nuvem ainda oferecem linha de base de gerenciamento no ambiente. Essas equipes centralizadas também orientam e instruem equipes especializadas de carga de trabalho sobre operações de suas cargas de trabalho. Mas a responsabilidade operacional do dia a dia recai sobre uma equipe de gerenciamento de nuvem gerenciada fora da TI. Esse tipo de controle distribuído é um dos principais indicadores da maturidade do Centro de Excelência de Nuvem.

## <a name="beyond-platform-specialization---application-insights"></a>Além da especialização de plataforma – Application Insights

São necessários maiores detalhes sobre a carga de trabalho específica para fornecer operações de carga de trabalho claras. Durante a fase de melhoria contínua, o Application Insights será um acréscimo necessário à cadeia de ferramentas de gerenciamento de nuvem.

|Monitoramento de Aplicativos|Application Insights|Monitoramento e diagnóstico para aplicativos| |Desempenho, Disponibilidade, Uso|Application Insights|Monitoramento avançado de aplicativos com o Painel do Aplicativo, mapas compostos, uso e rastreamento|

### <a name="deploy-application-insights"></a>Implantar Application Insights

1. No portal do Azure, pesquise **Application Insights**.
2. Clique em **+ Adicionar** para criar um recurso do Application Insights para monitorar seu aplicativo Web em tempo real.
3. Siga os prompts na tela

Confira o [Hub do Application Insights do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub) para obter diretrizes sobre como configurar seu aplicativo para monitoramento.

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Monitorar o desempenho, a disponibilidade e o uso

1. No portal do Azure, pesquise **Application Insights**.
2. Escolha um dos recursos do Application Insights na lista

A navegação do Application Insights contém uma variedade de opções para monitorar o desempenho, a disponibilidade, o uso e as dependências. Cada uma dessas exibições dos dados do aplicativo fornecerá clareza sobre o loop de comentários de melhoria contínua.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
