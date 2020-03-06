---
title: Impacto nos negócios no gerenciamento de nuvem
description: Use a estrutura de adoção de nuvem para o Azure para saber como determinar e entender o impacto que as interrupções ou a degradação do desempenho podem ter em sua empresa.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: bdd45861141b8fe69f8c13a49bdb6d387acd12ba
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341174"
---
# <a name="business-impact-in-cloud-management"></a>Impacto nos negócios no gerenciamento de nuvem

Suponha o melhor, prepare-se para o pior. No gerenciamento de ti, é seguro pressupor que as cargas de trabalho necessárias para dar suporte às operações de negócios estarão disponíveis e serão executadas em restrições acordadas, com base na criticalidade selecionada. No entanto, para gerenciar os investimentos de maneira inteligente, é importante entender o impacto sobre os negócios quando ocorre uma interrupção ou degradação do desempenho. Essa importância é ilustrada no grafo a seguir, que mapeia interrupções de negócios potenciais de cargas de trabalho específicas para o impacto comercial de interrupções em uma escala de valor relativa.

![Impacto das interrupções de negócios](../../_images/manage/time-value-impact.png)

Para criar uma base justa de comparação para o impacto em várias cargas de trabalho em um portfólio, uma métrica de tempo/valor é sugerida. A métrica de tempo/valor captura o impacto adverso de uma interrupção de carga de trabalho. Em geral, esse impacto é registrado como uma perda direta de receita ou receita operacional durante um período de interrupção típico. Mais especificamente, ele calcula a quantidade de receita perdida para uma unidade de tempo. A métrica de tempo/valor mais comum é o *impacto por hora*, que mede as perdas de receita operacional por hora de interrupção.

Algumas abordagens podem ser usadas para calcular o impacto. Você pode aplicar qualquer uma das opções nas seções a seguir para obter resultados semelhantes. É importante usar a mesma abordagem para cada carga de trabalho ao calcular perdas protegidas em um portfólio.

## <a name="start-with-estimates"></a>Iniciar com estimativas

Os modelos operacionais atuais podem dificultar a determinação de um impacto preciso. Felizmente, poucos sistemas precisam de um cálculo de perda altamente preciso. Na etapa anterior, *Classifique a criticalidade*, sugerimos que você inicie todas as cargas de trabalho com um padrão de *criticalidade média*. As cargas de trabalho de criticalidade médias geralmente recebem um nível padrão de suporte de gerenciamento com um impacto relativamente baixo no custo operacional. Somente quando uma carga de trabalho requer recursos adicionais de gerenciamento operacional, talvez você precise de um impacto financeiro preciso.

Para todas as cargas de trabalho padronizadas, o impacto nos negócios serve como uma variável de priorização quando você está recuperando sistemas durante uma interrupção. Fora dessas situações limitadas, o impacto nos negócios gera pouca ou nenhuma alteração na experiência de gerenciamento de operações.

## <a name="calculate-time"></a>Calcular hora

Dependendo da natureza da carga de trabalho, você pode calcular as perdas de forma diferente. Para sistemas transacionais de alto ritmo, como uma plataforma de comércio em tempo real, as perdas por milissegundos podem ser significativas. Sistemas usados com menos frequência, como folha de pagamento, podem não ser usados a cada hora. Se a frequência de uso é alta ou baixa, é importante normalizar a variável de tempo ao calcular o impacto financeiro.

## <a name="calculate-total-impact"></a>Calcular impacto total

Quando você quiser considerar os investimentos de gerenciamento adicionais, é mais importante que o impacto nos negócios seja mais preciso. As três abordagens a seguir para calcular as perdas são ordenadas do mais preciso para o menos preciso:

- **Perdas ajustadas:** Se sua empresa tiver tido um grande evento de perda no passado, como um furacão ou outro desastre natural, um ajustador de declarações poderá ter calculado as perdas reais durante a interrupção. Esses cálculos são baseados em padrões do setor de seguros para cálculo de perda e gerenciamento de riscos. O uso de perdas ajustadas como a quantidade total de perdas em um período de tempo específico pode levar a projeções altamente precisas.

- **Perdas históricas:** Se o seu ambiente local tiver sofrido historicamente de interrupções resultantes da instabilidade da infraestrutura, pode ser um pouco mais difícil calcular as perdas. Mas você ainda pode aplicar as fórmulas do ajustador usadas internamente. Para calcular as perdas históricas, compare os deltas em vendas, receita bruta e custos operacionais em três quadros de tempo: antes, durante e após a interrupção. Ao examinar esses deltas, você pode identificar perdas precisas quando nenhum outro dado está disponível.

- **Cálculo de perda completa:** Se nenhum dado histórico estiver disponível, você poderá derivar um valor de perda comparativa. Nesse modelo, você determina a receita bruta média por hora para a unidade de negócios. Quando você está projetando a perda de investimentos, não é justo pressupor que uma interrupção completa do sistema corresponda a uma perda de 100% da receita. Mas você pode usar essa suposição como uma base aproximada para comparar impactos de perda e priorizar investimentos.

Antes de tomar algumas suposições sobre possíveis perdas associadas a interrupções de carga de trabalho, é uma boa ideia trabalhar com seu departamento financeiro para determinar a melhor abordagem para esses cálculos.

## <a name="calculate-workload-impact"></a>Calcular o impacto da carga de trabalho

Quando estiver calculando perdas aplicando dados históricos, você poderá ter informações suficientes para determinar claramente a contribuição de cada carga de trabalho para essas perdas. A realização dessa avaliação é onde as parcerias dentro da empresa são absolutamente críticas. Depois que o impacto total tiver sido calculado, esse impacto deverá ser atribuído em cada uma das cargas de trabalho. Essa distribuição de impacto deve vir dos participantes da empresa, que devem concordar com o impacto relativo e cumulativo de cada carga de trabalho. Para esse fim, sua equipe deve solicitar comentários de executivos de negócios para validar o alinhamento. Esses comentários costumam ser uma questão de emoções de partes iguais e experiência no assunto. É importante que este exercício represente a lógica e a crenças dos participantes da empresa que devem ter um digamos na alocação de orçamento.

## <a name="use-the-template"></a>Usar o modelo

Se você estiver usando a [pasta de trabalho do Operations Management](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem, considere o seguinte:

- Cada empresa deve atualizar cada carga de trabalho no *exemplo* ou *limpar modelo* com o *impacto de tempo/valor* de cada carga de trabalho. Por padrão, o *impacto de tempo/valor* representa as perdas projetadas por hora associadas a uma interrupção da carga de trabalho.

## <a name="next-steps"></a>Próximas etapas

Depois que a empresa tiver definido o impacto, você poderá [alinhar os compromissos](./commitment.md).

> [!div class="nextstepaction"]
> [Alinhar os compromissos de gerenciamento com os negócios](./commitment.md)
