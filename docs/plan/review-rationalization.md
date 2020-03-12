---
title: Examinar as decisões de racionalização
description: Use a estrutura de adoção de nuvem para o Azure para aprender a examinar as decisões de racionalização e se preparar para facilitar uma conversa com a empresa.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: e38616b97f5026bd66de510cac12932290e276ba
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093263"
---
# <a name="review-rationalization-decisions"></a>Examinar as decisões de racionalização

Durante as fases iniciais de estratégia e planejamento, sugerimos que você aplique uma abordagem de [racionalização incremental](../digital-estate/rationalize.md#incremental-rationalization) ao espaço digital. Mas essa abordagem incorpora algumas suposições às decisões resultantes. Aconselhamos a equipe de estratégia de nuvem e as equipes de adoção de nuvem a revisar essas decisões em uma documentação de carga de trabalho expandida. Essa análise também é um bom momento para envolver os participantes comerciais e o patrocinador executivo em decisões de estado futuras.

> [!IMPORTANT]
> A validação adicional das decisões de racionalização ocorrerá durante a fase de avaliação da migração. Essa validação concentra-se na análise de negócios da racionalização para alinhar os recursos adequadamente.

Para validar decisões de racionalização, use as perguntas a seguir para facilitar uma conversa com a empresa. As perguntas são agrupadas pelo alinhamento provável da racionalização.

## <a name="innovation-indicators"></a>Indicadores de inovação

Se a análise conjunta das perguntas a seguir resultar em uma resposta "Sim", uma carga de trabalho poderá ser um candidato melhor para a inovação. Essa carga de trabalho não seria migrada por meio de um modelo de comparação de precisão e deslocamento ou modernização. Em vez disso, a lógica de negócios ou as estruturas de dados seriam recriadas como um aplicativo novo ou rearquitetado. Essa abordagem pode ser mais trabalhoso e demorada. Mas, para uma carga de trabalho que representa retornos de negócios significativos, o investimento é justificado.

- Os aplicativos nesta carga de trabalho criam diferenciação de mercado?
- Há um investimento proposto ou aprovado com o objetivo de melhorar as experiências associadas aos aplicativos nessa carga de trabalho?
- Os dados nessa carga de trabalho tornam novas ofertas de produtos ou serviços disponíveis?
- Há um investimento proposto ou aprovado com o objetivo de aproveitar os dados associados a essa carga de trabalho?
- O efeito da diferenciação do mercado ou das novas ofertas pode ser quantificado? Nesse caso, isso retorna justificar o aumento do custo da inovação durante a adoção da nuvem?

As duas perguntas a seguir podem ajudá-lo a incluir cenários técnicos de alto nível na revisão de racionalização. Responder "Sim" para poder identificar formas de contabilidade ou redução do custo associado à inovação.

- As estruturas de dados ou a lógica de negócios serão alteradas durante o curso de adoção da nuvem?
- Um pipeline de implantação existente foi usado para implantar essa carga de trabalho na produção?

Se a resposta para qualquer uma das perguntas for "Sim", a equipe deverá considerar a inclusão dessa carga de trabalho como um candidato à inovação. No mínimo, a equipe deve sinalizar essa carga de trabalho para análise da arquitetura para identificar oportunidades de modernização.

## <a name="migration-indicators"></a>Indicadores de migração

A migração é uma maneira mais rápida e barata de adotar a nuvem. Mas não aproveita as oportunidades de inovar. Antes de investir em inovação, responda às perguntas a seguir. Eles podem ajudá-lo a determinar se um modelo de migração é mais aplicável para uma carga de trabalho.

- O código-fonte está dando suporte a este aplicativo estável? Você espera que ele permaneça estável e inalterado durante o período deste ciclo de lançamento?
- Essa carga de trabalho dá suporte aos processos de negócios de produção hoje? Isso será feito durante o curso deste ciclo de lançamento?
- É uma prioridade que esse esforço de adoção de nuvem melhora a estabilidade e o desempenho dessa carga de trabalho?
- A redução de custos associada a essa carga de trabalho é um objetivo durante esse esforço?
- A redução da complexidade operacional dessa carga de trabalho é uma meta durante esse esforço?
- A inovação é limitada pela arquitetura atual ou pelos processos de operação de ti?

Se a resposta a qualquer uma dessas perguntas for "Sim", você deve considerar um modelo de migração para essa carga de trabalho. Essa recomendação é verdadeira mesmo se a carga de trabalho for um candidato para inovação.

Os desafios de complexidade operacional, custos, desempenho ou estabilidade podem atrapalhar os retornos de negócios. Você pode usar a nuvem para produzir rapidamente melhorias relacionadas a esses desafios. Quando aplicável, sugerimos que você use a abordagem de migração para primeiro estabilizar a carga de trabalho. Em seguida, expanda as oportunidades de inovação no ambiente de nuvem estável e ágil. Essa abordagem fornece retornos de curto prazo e reduz o custo necessário para gerar alterações de longo prazo.

> [!IMPORTANT]
> Os modelos de migração incluem modernização incremental. O uso de arquiteturas de PaaS (plataforma como serviço) é um aspecto comum das atividades de migração. Também são pequenas alterações de configuração que usam esses serviços de plataforma. O limite para migração é definido como uma alteração de material na lógica de negócios ou nas estruturas de negócios de suporte. Essa alteração é considerada um esforço de inovação.

## <a name="update-the-project-plan"></a>Atualizar o plano do projeto

As habilidades necessárias para um esforço de migração são diferentes das habilidades necessárias para um esforço de inovação. Durante a implementação de um plano de adoção de nuvem, sugerimos que você atribua esforços de migração e inovação a diferentes equipes. Cada equipe tem suas próprias cadências de iteração, liberação e planejamento. A atribuição de equipes separadas fornece a flexibilidade do processo para manter um plano de adoção de nuvem, levando em conta os esforços de inovação e de migração.

Quando você gerencia o plano de adoção de nuvem no Azure DevOps, esse gerenciamento é refletido alterando o item de trabalho pai (ou Epic) da migração de nuvem para a inovação em nuvem. Essa alteração sutil ajuda a garantir que todos os participantes do plano de adoção da nuvem possam controlar rapidamente o esforço necessário e as alterações nos esforços de correção. Esse controle também ajuda a alinhar as atribuições adequadas à equipe de adoção de nuvem relevante.

Para planos de adoção grandes e complexos com vários projetos distintos, considere atualizar o caminho de iteração. A alteração do caminho de área torna a carga de trabalho visível somente para a equipe atribuída a esse caminho de área. Essa alteração pode facilitar o trabalho para a equipe de adoção de nuvem, reduzindo o número de tarefas visíveis. Mas adiciona complexidade para os processos de gerenciamento de projeto.

## <a name="next-steps"></a>Próximas etapas

[Defina iterações e versões](./iteration-paths.md) para começar a planejar o trabalho.

> [!div class="nextstepaction"]
> [Defina iterações e versões](./iteration-paths.md) para começar a planejar o trabalho.
