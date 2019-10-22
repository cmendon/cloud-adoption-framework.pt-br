---
title: Criticalidade dos negócios – gerenciamento e operações de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticalidade dos negócios – gerenciamento e operações de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: be5cc97c7b42eb79f0ec9721376524dc2710e2c4
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683624"
---
# <a name="business-impact-in-cloud-management"></a>Impacto nos negócios no gerenciamento de nuvem

Suponha o melhor, prepare-se para o pior. No gerenciamento de ti, é seguro supor que as cargas de trabalho necessárias para dar suporte às operações de negócios estarão disponíveis e serão executadas dentro das restrições acordadas, com base na criticalidade selecionada. No entanto, para gerenciar investimentos de maneira inteligente, é importante entender o impacto causado pela empresa quando ocorre uma degradação de desempenho ou interrupção. Essa importância é ilustrada no grafo a seguir, que mapeia interrupções de negócios potenciais de cargas de trabalho específicas para o impacto nos negócios de interrupções em uma escala de valor relativa.

![Impacto das interrupções de negócios](../../_images/manage/time-value-impact.png)

Para criar uma base justa de comparação para o impacto de várias cargas de trabalho em um portfólio, uma métrica de tempo/valor é sugerida. A métrica de tempo/valor captura o impacto adverso de uma interrupção de carga de trabalho. Em geral, esse impacto é registrado como uma perda direta de receita ou receita operacional durante um período de interrupção típico. Mais especificamente, calculando a quantidade de receita perdida para uma unidade de tempo. A métrica de tempo/valor mais comum é "impacto por hora", que mede as perdas de receita operacional por hora de interrupção.

Há algumas abordagens que podem ser usadas para calcular o impacto. Qualquer uma das opções nas seções a seguir pode ser aproveitada com resultados semelhantes. É importante usar a mesma abordagem para cada carga de trabalho ao calcular perdas protegidas em um portfólio.

## <a name="start-with-estimates"></a>Iniciar com estimativas

Os modelos operacionais atuais podem dificultar a determinação de um impacto preciso. Felizmente, poucos sistemas precisam de um cálculo de perda altamente preciso. Na etapa anterior: classificar a criticalidade, foi recomendável que todas as cargas de trabalho comecem com um padrão de "importância média". As cargas de trabalho de criticalidade médias geralmente receberão um nível padrão de suporte de gerenciamento com um impacto de custo de operação relativamente baixo. Somente quando uma carga de trabalho exigir recursos adicionais de gerenciamento operacional, um impacto financeiro preciso será necessário.

Para todas as cargas de trabalho padronizadas, o impacto nos negócios serve como uma variável de priorização ao recuperar sistemas durante uma interrupção. Fora dessas situações limitadas, o impacto nos negócios gerará pouca ou nenhuma alteração na experiência de gerenciamento de operações. 

## <a name="calculating-time"></a>Calculando o tempo

Dependendo da natureza da carga de trabalho, as perdas poderiam ser calculadas de forma diferente. Para sistemas transacionais de alto ritmo como uma plataforma de comércio em tempo real, as perdas por milissegundos podem ser significativas. Sistemas usados com menos frequência, como a folha de pagamento, não podem ser usados a cada hora. Se a frequência de uso é alta ou baixa, é importante normalizar a variável de tempo ao calcular o impacto financeiro.

## <a name="calculating-total-impact"></a>Calculando o impacto total

Quando são desejados investimentos de gerenciamento adicionais, é mais importante que o impacto nos negócios seja mais preciso. Os marcadores a seguir descrevem as abordagens para calcular as perdas, na ordem mais precisa (do mais preciso para o menos preciso):

- **Perdas ajustadas:** Se a empresa tiver tido um grande evento de perda no passado, como um furacão ou outro desastre natural, um ajustador de declarações poderá ter calculado as perdas reais durante a interrupção. Esses cálculos são baseados em padrões do setor de seguros para cálculo de perda e gerenciamento de riscos. O uso de perdas ajustadas como a quantidade total de perdas em um período de tempo específico pode levar a projeções altamente precisas.

- **Perdas históricas:** Se o ambiente local tiver sofrido de interrupções historicamente devido à instabilidade da infraestrutura, pode ser um pouco mais difícil calcular as perdas. Mas, as fórmulas do ajustador ainda podem ser aproveitadas internamente. Para calcular o histórico de perda, compare os deltas em vendas, receita bruta e custos operacionais em três quadros de tempo: antes, durante e após a interrupção. Examinar esses deltas pode identificar perda precisa quando nenhum outro dado está disponível.

- **Cálculo de perda completa:** Se nenhum dado histórico estiver disponível, um valor de perda comparativa poderá ser derivado. Nesse modelo, determine a receita bruta média por hora para a unidade de negócios. Supondo que uma interrupção completa do sistema seja igual a 100% de perda de receita é uma má suposição ao projetar investimentos de prevenção de perda. Mas ele pode ser usado como uma base aproximada para comparar impactos de perda e priorizar investimentos.

Antes de fazer suposições sobre cálculos de perda, trabalhe com seu departamento financeiro para determinar a melhor abordagem para calcular possíveis perdas associadas a uma interrupção da carga de trabalho.

## <a name="calculating-workload-impact"></a>Calculando o impacto da carga de trabalho

Ao aproveitar os dados históricos para calcular as perdas, pode haver informações suficientes para determinar claramente o impacto de cada carga de trabalho nessas perdas. Essa avaliação é onde a parceria com a empresa é absolutamente crítica. Depois que um impacto total tiver sido calculado, esse impacto deverá ser atribuído em cada carga de trabalho. Essa distribuição de impacto deve vir dos participantes da empresa, que devem concordar com o impacto relativo e cumulativo de cada carga de trabalho. Além disso, a equipe deve solicitar comentários de executivos de negócios para validar o alinhamento. Infelizmente, o resultado final é a emoção das partes iguais e a experiência do assunto. A importância deste exercício é que ele representa a lógica e a crenças dos participantes da empresa que devem ter um digamos na alocação de orçamento.

## <a name="using-the-template"></a>Usando o modelo

As etapas a seguir se aplicam aos leitores que estão usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem.

1. Cada carga de trabalho no "exemplo" ou "modelo limpo" deve ser atualizada pelo negócio com o "impacto de tempo/valor" de cada carga de trabalho. Por padrão, "impacto de tempo/valor" representa as perdas projetadas por hora associadas a uma interrupção da carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Quando o impacto é definido, os [compromissos podem ser alinhados](./commitment.md).

> [!div class="nextstepaction"]
> [Alinhar os compromissos de gerenciamento com os negócios](./commitment.md)
