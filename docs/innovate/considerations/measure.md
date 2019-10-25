---
title: 'Inovação na nuvem: medida'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação em nuvem – conteúdo de medidas
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 00928171c3bfba1638a7e8e43ea08df4745754d2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557642"
---
# <a name="measure-for-customer-impact"></a>Medida para o impacto do cliente

Há várias maneiras de medir o impacto do cliente. Este artigo ajudará a definir medidas que podem ajudar a validar as precauções criadas durante a tentativa [de compilação com o cliente empatia](./build.md).

## <a name="strategic-metrics"></a>Métricas estratégicas

Durante a [fase de estratégia](../../strategy/index.md) do ciclo de vida de adoção da nuvem, os leitores são guiados pela criação e documentação de [motivações](../../strategy/motivations.md) e [resultados de negócios](../../strategy/business-outcomes/index.md). Esses exercícios fornecem um conjunto de métricas para usar como um teste de impacto do cliente. Quando a inovação for bem-sucedida, ela produzirá resultados alinhados com os objetivos da estratégia.

Antes de estabelecer as métricas de aprendizado, defina um pequeno número de métricas estratégicas que essa inovação deve afetar. Geralmente, essas métricas estratégicas se alinharão a uma ou mais das seguintes áreas de resultado: [agilidade dos negócios](../../strategy/business-outcomes/agility-outcomes.md), [envolvimento do cliente](../../strategy/business-outcomes/engagement-outcomes.md), alcance do [cliente](../../strategy/business-outcomes/reach-outcomes.md), [impacto financeiro](../../strategy/business-outcomes/fiscal-outcomes.md)ou, no caso de inovação operacional: [solução Desempenho](../../strategy/business-outcomes/fiscal-outcomes.md).

Documente as métricas acordadas e acompanhe o impacto com frequência. No entanto, não espere resultados em qualquer uma dessas métricas para surgir em várias iterações. Confira o [compromisso com a iteração](./index.md#commitment-to-iteration) para alinhar as expectativas.

Além das métricas de motivação e de resultados de negócios, o restante deste artigo se concentrará nas métricas de aprendizado projetadas para guiar a descoberta transparente e as iterações focadas no cliente. Confira o [compromisso com a transparência](./index.md#commitment-to-transparency) para alinhar as expectativas.

## <a name="learning-metrics"></a>Métricas de aprendizagem

Quando a primeira versão de qualquer produto viável mínimo (MVP) é compartilhada com clientes, de preferência ao final da primeira iteração de desenvolvimento, não haverá nenhum impacto nas métricas estratégicas. Várias iterações mais tarde, a equipe ainda pode estar lutando para alterar comportamentos o suficiente para afetar materialmente as métricas estratégicas. Durante os processos de aprendizado, como os ciclos de compilação-avaliação-aprendizado, é recomendável que a equipe adote métricas de aprendizado. Essas métricas podem ser mais facilmente rastreadas e aproveitadas em oportunidades para aprender.

### <a name="customer-flow-and-learning-metrics"></a>Métricas de aprendizado e de fluxo do cliente

Se uma solução MVP validar uma hipótese voltada para o cliente, a solução conduzirá algumas alterações nos comportamentos do cliente. Esses comportamentos em vários coortes clientes gerarão resultados de negócios. Felizmente, a alteração de comportamentos do cliente geralmente é um processo de várias etapas. Cada etapa fornece uma oportunidade para medir o impacto, para que a equipe de adoção possa aprender e criar uma solução melhor.

Aprender sobre alterações nos comportamentos do cliente começa mapeando o fluxo desejado criado por uma solução MVP.

![Fluxo do cliente usado para determinar as métricas de aprendizado](../../_images/innovate/customer-flow-learning-metrics.png)

Na maioria dos casos, um fluxo de cliente terá um ponto de partida definido com facilidade e não mais do que dois pontos de extremidade. Entre os pontos inicial e final estão uma variedade de métricas de aprendizado a serem usadas como medidas no loop de comentários:

1. **Ponto inicial-gatilho inicial:** O ponto de partida é o cenário que dispara a necessidade dessa solução. Quando a solução é criada com empatia de clientes, esse gatilho inicial deve inspirar um cliente para experimentar a solução MVP.
2. O **cliente precisa cumprir:** A hipótese é validada quando uma necessidade do cliente é atendida usando a solução.
3. **Etapas da solução:** Cada etapa necessária para mover o cliente do gatilho inicial para um resultado bem-sucedido é uma etapa da solução. Cada etapa produz uma métrica de aprendizado com base nas decisões do cliente para passar para a próxima etapa.
4. **Adoção individual alcançada:** Na próxima vez em que o gatilho for encontrado, se o cliente retornar à solução para que a necessidade seja atendida novamente, a adoção individual será alcançada.
5. **Indicador de resultado comercial:** Quando um cliente se comporta de uma forma que contribui positivamente para o resultado comercial definido, um indicador de resultado comercial é observado.
6. **Verdadeira inovação:** Quando os "indicadores de resultados de negócios" e "adoção individual" ocorrem na escala desejada, a verdadeira inovação foi experimentada.

Cada etapa do fluxo do cliente gera métricas de aprendizado. Após cada iteração (ou versão), uma nova versão da hipótese é testada. Ao mesmo tempo, os ajustes na solução são testados para refletir os ajustes na hipótese. Quando os clientes seguem o caminho prescrito em qualquer etapa específica, uma métrica positiva é registrada. Quando os clientes se desviam do caminho prescrito para atender às suas necessidades, uma métrica negativa é registrada.

Esses contadores de alinhamento e desvio criam métricas de aprendizado. Cada um deve ser registrado e acompanhado à medida que a equipe de adoção da nuvem progredi em direção à realização dos resultados de negócios e à verdadeira inovação. No próximo artigo, [aprendendo com parceiros de clientes](./learn.md) , discutiremos maneiras de aproveitar essas métricas para aprender e criar soluções melhores.

### <a name="grouping-and-observing-customer-partners"></a>Agrupando e observando parceiros de clientes

A primeira medida para definir as métricas de aprendizagem é a definição de parceiro do cliente. Qualquer cliente que participe de ciclos de inovação se qualifica como um parceiro de cliente. Para medir com precisão o comportamento, é importante definir os parceiros do cliente em um modelo coorte. Nesse modelo, os clientes são agrupados para entender melhor como eles respondem a quaisquer alterações no MVP. Os parceiros do cliente geralmente são agrupados com base em pontos de dados como o seguinte:

- **Grupo de experimentos ou de foco:** Agrupamento com base em uma participação de clientes em um experimento específico para testar alterações ao longo do tempo.
- **Segmento:** Agrupar clientes pelo tamanho da empresa.
- **Vertical:** Agrupar clientes pela vertical do setor que eles representam.
- Dados **demográficos individuais:** Agrupamento com base em dados demográficos pessoais, como idade ou local físico.

Esse tipo de agrupamento permite a validação de métricas de aprendizado em várias seções cruzadas desses clientes que optam por fazer uma parceria com você durante os esforços de inovação. Todas as métricas subsequentes devem ser observadas com base em um agrupamento de clientes definíveis.

## <a name="next-steps"></a>Próximas etapas

À medida que as métricas de aprendizado são acumuladas, a equipe pode começar a [aprender com os clientes](./learn.md).

> [!div class="nextstepaction"]
> [Aprenda com os clientes](./learn.md)

Alguns dos conceitos neste artigo se baseiam nos tópicos descritos pela primeira vez na [inicialização de Lean](http://theleanstartup.com/book), escrito por Eric Ries.
