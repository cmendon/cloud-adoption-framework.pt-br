---
title: Métricas de Gerenciamento de Custos, indicadores e tolerância a risco
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação sobre o Gerenciamento de Custos em relação a governança de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: dc026ec6fc1a82db3c5c025becd31cd5cf2e7d8d
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752698"
---
# <a name="cost-management-metrics-indicators-and-risk-tolerance"></a>Métricas de Gerenciamento de Custos, indicadores e tolerância a risco

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com o gerenciamento de custos. Definir métricas e indicadores ajuda a criar um caso de negócios para fazer um investimento no amadurecimento da disciplina de Gerenciamento de Custos.

## <a name="metrics"></a>Métricas

O Gerenciamento de Custos em geral se concentra em métricas relacionadas aos custos. Como parte da análise de risco, você irá querer reunir dados relacionados aos seus gastos atuais e planejados em cargas de trabalho baseadas em nuvem para determinar quanto risco você enfrenta e como o investimento em governança de custos é importante para sua estratégia de adoção da nuvem.

Veja a seguir exemplos de métricas úteis que você deve coletar para ajudar a avaliar a tolerância a riscos na disciplina de gerenciamento de custos:

- **Gasto anual:** O custo anual total dos serviços fornecidos por um provedor de nuvem.
- **Gastos mensais:** O custo mensal total dos serviços fornecidos por um provedor de nuvem.
- **Previsão versus taxa real:** A taxa que compara os gastos previstos e reais (mensal ou anual).
- **Proporção do ritmo de adoção (MOM):** A porcentagem do Delta nos custos de nuvem, do mês para o mês.
- **Custo acumulado:** Total de gastos diários acumulados, a partir do início do mês.
- **Tendências de gastos:** Gastar tendência em relação ao orçamento.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

Durante as implantações iniciais de pequeno escala, como desenvolvimento/teste ou primeiras cargas de trabalho experimentais, o gerenciamento de custos provavelmente será de um risco relativamente baixo. Conforme mais ativos são implantados, o risco aumenta a tolerância da empresa quanto a risco é provável de recuar. Além disso, conforme mais equipes de adoção da nuvem recebem a capacidade de configurar ou implantar ativos para a nuvem, aumenta o risco e diminui a tolerância. Por outro lado, aumentar uma disciplina de Gerenciamento de Custos levará as pessoas desde a fase de adoção da nuvem para implantar as mais novas tecnologias inovadoras.

Nos estágios iniciais de adoção da nuvem, você trabalhará com seu negócio para determinar uma linha de base de tolerância de risco. Depois de ter uma linha de base, você precisará determinar os critérios que disparam um investimento na disciplina de Gerenciamento de Custos. Esses critérios provavelmente serão diferentes para cada organização.

Depois de ter identificado [riscos de negócios](./business-risks.md), você trabalhará com seu negócio para identificar os parâmetros de comparação que você pode usar para identificar gatilhos que poderiam aumentar potencialmente esses riscos. A seguir estão alguns exemplos de como as métricas, como aquelas mencionadas acima, podem ser comparadas com sua tolerância de risco de linha de base para indicar a necessidade da sua empresa ainda mais a investir no Gerenciamento de Custos.

- **Controlado por compromisso (mais comum):** Uma empresa comprometida em gastar _$x, 000000_ neste ano em um fornecedor de nuvem. Eles precisam de uma disciplina de gerenciamento de custos para garantir que a empresa não exceda suas metas de gastos em mais de 20% e que elas usarão pelo menos 90% de seu compromisso.
- **Gatilho de percentual:** Uma empresa com gastos em nuvem estável para seus sistemas de produção. Se isso mudar em mais de _x%_ , uma disciplina de gerenciamento de custo será um investimento inteligente.
- **Gatilho com provisionamento excessivo:** Uma empresa que acredita que suas soluções implantadas é excessivamente provisionada. O gerenciamento de custos é um investimento prioritário até que ele demonstre o alinhamento adequado do provisionamento e da utilização de ativos.
- **Gatilho de gastos mensais:** Uma empresa que passa pelo _$x, 000_ por mês, é considerada um custo ajustável. Se os gastos excederem esse valor em um determinado mês, precisará investir no Gerenciamento de Custos.
- **Gatilho de gasto anual:** Uma empresa com um orçamento de R & D que permite gastar _$x, 000_ por ano em experimentação de nuvem. Eles podem executar cargas de trabalho de produção na nuvem, mas eles ainda serão considerados soluções experimentais se o orçamento não exceder essa quantidade. Se o orçamento for excedido, ele precisará tratar o orçamento como um investimento em produção e gerenciar os gastos de forma minuciosa.
- **Despesa operacional-adverso (incomum):** Como uma empresa, eles estão avessando as despesas operacionais e precisarão de controles de gerenciamento de custos em vigor antes de implantar uma carga de trabalho de desenvolvimento/teste.

## <a name="next-steps"></a>Próximos passos

Uso do [modelo de Gerenciamento de nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.

Examine as políticas de gerenciamento de custo de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos de negócios específicos que se alinham com seus planos de adoção de nuvem.

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
