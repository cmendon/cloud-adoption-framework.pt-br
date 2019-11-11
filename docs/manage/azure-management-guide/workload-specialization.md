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
ms.openlocfilehash: 92b9988d47dcc8ba4b7a7e3dd02a4ec9ff3ed2e9
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565387"
---
# <a name="workload-specialization-for-cloud-management"></a>Especialização de carga de trabalho para gerenciamento de nuvem

A especialização de carga de trabalho baseia-se nos conceitos descritos na [Especialização de Plataforma](./platform-specialization.md).

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:** O maior investimento de operações por carga de trabalho e o maior grau de resiliência. Sugerimos operações de carga de trabalho para aproximadamente 20% das cargas de trabalho que impulsionam o valor comercial. Essa especialização geralmente é reservada para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:** O investimento de operações é distribuído entre muitas cargas de trabalho. As melhorias de resiliência afetam todas as cargas de trabalho que usam uma plataforma definida. Sugerimos operações de plataforma para aproximadamente 20% das plataformas que têm a maior importância. Essa especialização geralmente é reservada para cargas de trabalho de média a alta importância.
- **Linha de base de gerenciamento aprimorada:** O investimento relativamente menor em operações. Essa especialização melhora um pouco os compromissos de negócios usando processos e ferramentas de operações nativas de nuvem adicionais.

## <a name="high-level-process"></a>Processo de alto nível

A especialização de carga de trabalho consiste em uma execução disciplinada dos quatro processos a seguir em uma abordagem iterativa. Cada processo é explicado com mais detalhes no artigo [Especialização de Plataforma](./platform-specialization.md).

- **Melhorar o design do sistema:** melhore o design de uma carga de trabalho específica para minimizar interrupções efetivamente.
- **Automatizar a correção:** Algumas melhorias não são econômicas. Nesses casos, talvez faça mais sentido automatizar a correção e reduzir o impacto das interrupções.
- **Dimensionar a solução:** Ao melhorar o design de sistemas e a correção automatizada é possível dimensionar essas alterações em todo o ambiente por meio do catálogo de serviços.
- **Melhoria contínua:** É possível usar diferentes ferramentas de monitoramento para descobrir melhorias incrementais. Essas melhorias podem ser abordadas na próxima etapa do design, da automação e da escala do sistema.

## <a name="cultural-change"></a>Mudança cultural

A especialização de carga de trabalho geralmente dispara uma alteração cultural nos processos tradicionais de criação de TI que se concentram em oferecer uma linha de base de gerenciamento, linhas de base aprimoradas e operações de plataforma. Esses tipos de ofertas podem ser dimensionados em todo o ambiente. A especialização de carga de trabalho é semelhante, na execução, à especialização de plataforma. Porém, ao contrário das plataformas comuns, a especialização exigida por cargas de trabalho individuais geralmente não é dimensionada.

Quando a especialização de carga de trabalho é necessária, o gerenciamento operacional normalmente evolui além de uma perspectiva de TI central. A abordagem sugerida na Estrutura de Adoção de Nuvem é uma distribuição da funcionalidade de gerenciamento de nuvem.

Nesse modelo, tarefas operacionais como monitoramento, implantação, DevOps e outras funções focadas em inovação são deslocadas para um desenvolvimento de aplicativo ou uma organização de unidade de negócios. A equipe de Plataforma de Nuvem e a equipe principal de Monitoramento de Nuvem ainda oferecem linha de base de gerenciamento no ambiente.

Essas equipes centralizadas também orientam e instruem equipes especializadas em cargas de trabalho sobre as operações de cargas de trabalho delas. Porém, a responsabilidade operacional diária recai sobre uma equipe de gerenciamento de nuvem que é gerenciada fora da TI. Esse tipo de controle distribuído é um dos principais indicadores da maturidade do Centro de Excelência de Nuvem.

## <a name="beyond-platform-specialization---application-insights"></a>Além da especialização de plataforma – Application Insights

São necessários maiores detalhes sobre a carga de trabalho específica para fornecer operações de carga de trabalho claras. Durante a fase de melhoria contínua, o Application Insights será um acréscimo necessário à cadeia de ferramentas de gerenciamento de nuvem.

|Requisito|Ferramenta|Finalidade|
|---|---|---|
|Monitoramento de aplicativo|Application Insights|Monitoramento e diagnóstico para aplicativos|
|Desempenho, disponibilidade e uso|Application Insights|Monitoramento avançado de aplicativos com painel do aplicativo, mapas compostos, uso e rastreamento|

### <a name="deploy-application-insights"></a>Implantar Application Insights

1. No portal do Azure, acesse **Application Insights**.
1. Selecione **Adicionar +** para criar um recurso do Application Insights com o objetivo de monitorar seu aplicativo Web em tempo real.
1. Siga os prompts na tela.

Confira o [Hub do Application Insights do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub) para obter diretrizes sobre como configurar seu aplicativo para monitoramento.

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Monitorar o desempenho, a disponibilidade e o uso

1. No portal do Azure, pesquise **Application Insights**.
1. Escolha um dos recursos do Application Insights da lista.

O Application Insights contém diferentes tipos de opções para monitorar o desempenho, a disponibilidade, o uso e as dependências. Cada uma dessas exibições dos dados do aplicativo fornece clareza no loop de comentários de melhoria contínua.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
