---
title: Medir o impacto do cliente
description: Defina o fluxo do cliente desejado e estabeleça métricas de aprendizado para medir o comportamento e a adoção do cliente.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 3ba4cc99b210784c7503085234c25c1d9a0ae634
ms.sourcegitcommit: d660484d534bc61fc60470373f3fcc885a358219
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507991"
---
# <a name="measure-for-customer-impact"></a>Avaliar o impacto sobre o cliente

Há várias maneiras de medir o impacto do cliente. Este artigo o ajudará a definir métricas para validar as mesmas que surgirem de um esforço para [criar com empatia de clientes](./build.md).

## <a name="strategic-metrics"></a>Métricas estratégicas

Durante a [fase de estratégia](../../strategy/index.md) do ciclo de vida de adoção da nuvem, examinamos as [motivações](../../strategy/motivations.md) e os [resultados de negócios](../../strategy/business-outcomes/index.md). Essas práticas fornecem um conjunto de métricas para testar o impacto do cliente. Quando a inovação é bem-sucedida, você tende a ver os resultados alinhados aos seus objetivos estratégicos.

Antes de estabelecer as métricas de aprendizado, defina um pequeno número de métricas estratégicas que você deseja que essa inovação afete. Geralmente, essas métricas estratégicas se alinham com uma ou mais das seguintes áreas de resultado: [agilidade dos negócios](../../strategy/business-outcomes/agility-outcomes.md), [envolvimento do cliente](../../strategy/business-outcomes/engagement-outcomes.md), [alcance do cliente](../../strategy/business-outcomes/reach-outcomes.md), [impacto financeiro](../../strategy/business-outcomes/fiscal-outcomes.md)ou, no caso de inovação operacional: [desempenho da solução](../../strategy/business-outcomes/fiscal-outcomes.md).

Documente as métricas acordadas e acompanhe seu impacto com frequência. Mas não espere os resultados em qualquer uma dessas métricas surgirem para várias iterações. Para obter mais informações sobre como definir e alinhar as expectativas entre as partes envolvidas, consulte [compromisso com a iteração](./index.md#commitment-to-iteration).

Além das métricas de motivação e de resultados de negócios, o restante deste artigo se concentra em métricas de aprendizado projetadas para guiar a descoberta transparente e iterações voltadas para o cliente. Para obter mais informações sobre esses aspectos, consulte [compromisso com transparência](./index.md#commitment-to-transparency).

## <a name="learning-metrics"></a>Métricas de aprendizagem

Quando a primeira versão de qualquer produto viável mínimo (MVP) é compartilhada com clientes, de preferência ao final da primeira iteração de desenvolvimento, não haverá nenhum impacto nas métricas estratégicas. Várias iterações mais tarde, a equipe ainda pode estar lutando para alterar comportamentos o suficiente para afetar materialmente as métricas estratégicas. Durante os processos de aprendizado, como os ciclos de compilação-avaliação-aprendizado, aconselhamos a equipe a adotar as métricas de aprendizado. Essas métricas estão acompanhando e aprendendo as oportunidades.

### <a name="customer-flow-and-learning-metrics"></a>Métricas de aprendizado e de fluxo do cliente

Se uma solução MVP validar uma hipótese voltada para o cliente, a solução conduzirá algumas alterações nos comportamentos do cliente. Essas alterações de comportamento em coortes de clientes devem melhorar os resultados de negócios. Tenha em mente que alterar o comportamento do cliente normalmente é um processo de várias etapas. Como cada etapa fornece uma oportunidade para medir o impacto, a equipe de adoção pode continuar aprendendo ao longo do caminho e criar uma solução melhor.

Aprender sobre alterações no comportamento do cliente começa mapeando o fluxo que você espera ver em uma solução MVP.

![Fluxo do cliente usado para determinar as métricas de aprendizado](../../_images/innovate/customer-flow-learning-metrics.png)

Na maioria dos casos, um fluxo de cliente terá um ponto de partida definido com facilidade e não mais do que dois pontos de extremidade. Entre os pontos inicial e final estão uma variedade de métricas de aprendizado a serem usadas como medidas no loop de comentários:

1. **Ponto inicial – gatilho inicial:** O ponto de partida é o cenário que dispara a necessidade dessa solução. Quando a solução é criada com empatia de clientes, esse gatilho inicial deve inspirar um cliente para experimentar a solução MVP.
2. O **cliente precisa cumprir:** A hipótese é validada quando uma necessidade do cliente é atendida usando a solução.
3. **Etapas da solução:** Este termo refere-se às etapas necessárias para mover o cliente do gatilho inicial para um resultado bem-sucedido. Cada etapa produz uma métrica de aprendizado com base em uma decisão do cliente para passar para a próxima etapa.
4. **Adoção individual alcançada:** Na próxima vez que o gatilho for encontrado, se o cliente retornar à solução para atender às suas necessidades, a adoção individual terá sido atingida.
5. **Indicador de resultado comercial:** Quando um cliente se comporta de forma que contribui para o resultado comercial definido, um indicador de resultado comercial é observado.
6. **Verdadeira inovação:** Quando os *indicadores de resultados de negócios* e a *adoção individual* ocorrem na escala desejada, você percebeu uma inovação verdadeira.

Cada etapa do fluxo do cliente gera métricas de aprendizado. Após cada iteração (ou versão), uma nova versão da hipótese é testada. Ao mesmo tempo, os ajustes na solução são testados para refletir os ajustes na hipótese. Quando os clientes seguem o caminho prescrito em qualquer etapa específica, uma métrica positiva é registrada. Quando os clientes se desviam do caminho prescrito, uma métrica negativa é registrada.

Esses contadores de alinhamento e desvio criam métricas de aprendizado. Cada um deve ser registrado e acompanhado à medida que a equipe de adoção de nuvem progredi para os resultados de negócios e a verdadeira inovação. Em [Aprenda com os clientes](./learn.md), discutiremos maneiras de aplicar essas métricas para aprender e criar soluções melhores.

### <a name="grouping-and-observing-customer-partners"></a>Agrupando e observando parceiros de clientes

A primeira medida para definir métricas de aprendizado é a definição de parceiro do cliente. Qualquer cliente que participe de ciclos de inovação se qualifica como um parceiro de cliente. Para medir com precisão o comportamento, você deve usar um modelo coorte para definir parceiros de clientes. Nesse modelo, os clientes são agrupados para ajustar sua compreensão de suas respostas às alterações no MVP. Esses grupos normalmente se assemelham ao seguinte:

- **Grupo de experimentos ou de foco:** Agrupar clientes com base em sua participação em um experimento específico projetado para testar alterações ao longo do tempo.
- **Segmento:** Agrupar clientes pelo tamanho da empresa.
- **Vertical:** Agrupar clientes pela *vertical do setor* que eles representam.
- Dados **demográficos individuais:** Agrupamento com base em dados demográficos pessoais, como idade e localização física.

Esses tipos de agrupamentos ajudam a validar as métricas de aprendizado em várias seções cruzadas desses clientes que optam por fazer uma parceria com você durante seus esforços de inovação. Todas as métricas subsequentes devem ser derivadas do agrupamento de clientes definíveis.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

À medida que as métricas de aprendizado se acumulam, a equipe pode começar a [aprender com os clientes](./learn.md).

> [!div class="nextstepaction"]
> [Aprenda com os clientes](./learn.md)

Alguns dos conceitos neste artigo se baseiam nos tópicos descritos pela primeira vez na [inicialização de Lean](http://theleanstartup.com/book), escrito por Eric Ries.
