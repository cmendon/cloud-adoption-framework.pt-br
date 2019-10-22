---
title: Crie um consenso sobre o valor comercial da inovação na nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda a criar um consenso sobre o valor comercial da inovação em nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 643da95396a4983c2642fabcf21340264d0cd1c9
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683336"
---
# <a name="building-consensus-on-the-business-value-of-innovation"></a>Criando consenso sobre o valor comercial da inovação

A primeira etapa para desenvolver qualquer inovação nova é identificar como essa inovação levará ao valor comercial. Este exercício faz uma série de perguntas que destacam a importância de investir mais tempo definindo valor comercial.

## <a name="qualifying-questions"></a>Perguntas de qualificação

Antes de desenvolver qualquer solução (na nuvem ou local), Valide seus critérios de valor de negócios:

1. Quais são as necessidades definidas pelo cliente que estamos buscando abordar com essa solução?
2. Quais oportunidades essa solução criaria para a empresa?
3. Quais resultados de negócios seriam obtidos com essa solução?
4. Quais das motivações da empresa seriam servidas com essa solução?

Se as respostas a todas as quatro perguntas estiverem bem documentadas, talvez você não precise do restante deste exercício. Felizmente, essa documentação pode ser facilmente testada. Para testar a documentação e o alinhamento geral, hospede uma pequena reunião com participantes comerciais confirmados e uma reunião curta separada com a equipe de desenvolvimento envolvida. Em ambas as reuniões, faça as quatro perguntas acima e compare os resultados.

> [!NOTE]
> A documentação existente **não deve** ser compartilhada com nenhuma das equipes antes da reunião. Se houver um alinhamento verdadeiro, as condições de orientação devem ser referenciadas (ou melhor ainda, recitadas) por membros de cada grupo.

> [!WARNING]
> Não facilite a reunião. Este é um teste de alinhamento, não um exercício de criação de alinhamento. Ao iniciar a reunião, verifique se os participantes estão cientes do objetivo de testar o alinhamento direcional com os contratos existentes dentro da equipe. Estabeleça apenas um limite de tempo. Confirme cinco minutos por pergunta e defina um temporizador para cada um. Feche essa pergunta em cinco minutos, mesmo que a resposta não seja acordada.

Se as respostas estiverem alinhadas de forma direcionada, mas representarem os diferentes idiomas e interesses de cada grupo, considere este exercício uma vitória. Você está pronto para prosseguir para o desenvolvimento da solução.

Se uma ou duas das respostas estiverem alinhadas de forma direcionada, reconheça que seu trabalho árduo está pagando. Você já está mais alinhado do que a maioria das organizações. O sucesso futuro é muito provável, com um pequeno investimento contínuo em alinhamento. Examine cada uma das seções a seguir para obter ideias que podem ajudá-lo a criar mais alinhamento.

Se a equipe não responder a todas as quatro perguntas em trinta minutos, o alinhamento e os esforços a seguir provavelmente terão um grande impacto sobre esse esforço e outros. Preste muita atenção a cada uma das seções a seguir.

## <a name="address-the-big-picture-first"></a>Abordar a visão geral primeiro

A estrutura de adoção de nuvem segue um caminho prescrito por meio de estratégia, plano, pronto e adoção. A inovação na nuvem se encaixa na fase de adoção desse processo. Quando as respostas às perguntas 3 e 4 acima (resultados e motivações) são desalinhadas, indica que algo foi perdido durante a fase de estratégia do ciclo de vida de adoção da nuvem. É provável que vários dos cenários a seguir estejam em jogo.

- **Oportunidade de alinhamento:** Quando os participantes da empresa não conseguirem concordar sobre motivações e resultados de negócios relacionados a um esforço de inovação na nuvem, isso é um sintoma de um desafio maior. Os exercícios na [fase de estratégia de nuvem](../strategy/index.md) podem ser úteis para o desenvolvimento de alinhamento entre os participantes comerciais. Além disso, é altamente recomendável que as mesmas partes interessadas formem uma [equipe de estratégia de nuvem](../organize/cloud-strategy.md) que atenda regularmente.

- **Oportunidade de comunicação:** Quando a equipe de desenvolvimento não consegue concordar sobre motivações e resultados de negócios, pode ser um sintoma de lacunas de comunicação estratégica. Examinar a estratégia de nuvem com a equipe de adoção de nuvem pode resolver rapidamente esse bloqueador. Várias semanas após a revisão, a equipe deve repetir o exercício de perguntas de qualificação.

- **Oportunidade de priorização:** Uma estratégia de nuvem é essencialmente uma hipótese de nível executivo. As melhores estratégias de nuvem estão abertas para a iteração e os comentários. Se ambas as equipes entenderem a estratégia, mas ainda não conseguirem alinhar as respostas a essas perguntas, as prioridades poderão estar desalinhadas. Uma sessão com a equipe de adoção de nuvem e a equipe de estratégia de nuvem pode ajudar nos esforços de ambos os grupos. Durante essa sessão, a equipe de adoção de nuvem compartilha suas respostas alinhadas para as perguntas de visão geral. A partir daí, uma conversa entre a equipe de adoção de nuvem e a equipe de estratégia de nuvem pode realçar as oportunidades para alinhar melhor as prioridades.

Essas grandes oportunidades de panorama geral revelam maneiras de alinhar melhor essa solução com a estratégia de nuvem. Este exercício tem dois resultados comuns:

- Essas conversas podem levar a melhorias na estratégia de nuvem e uma melhor representação dessa necessidade importante do cliente. Essa alteração pode resultar em maior suporte executivo para a equipe.
- Por outro lado, essa conversa pode mostrar que investir em outra solução é mais apropriado para a equipe de adoção de nuvem. Nesse caso, considere migrar essa solução antes de continuar a investir em inovação. Como alternativa, isso pode indicar que uma abordagem de desenvolvedor do cidadão é necessária para testar o valor comercial primeiro. Em ambos os casos, ele ajudará a equipe a evitar fazer um grande investimento com Devoluções de negócios limitados.

## <a name="address-solution-alignment"></a>Alinhamento da solução de endereço

É bastante comum que as respostas às perguntas 1 e 2 (necessidade do cliente e oportunidade de negócios) sejam desalinhadas. Isso é especialmente comum durante os estágios iniciais de idealização e desenvolvimento. Encontrar um equilíbrio entre uma definição muito grande e muito pequena é desafiador para muitas equipes de desenvolvimento. Na estrutura de adoção de nuvem, abordagens de Lean como os loops de comentários de compilação-avaliação são sugeridos como a melhor maneira de responder a essas perguntas. A lista a seguir mostra as oportunidades e abordagens para criar alinhamento.

- **Oportunidade de hipótese:** É comum que vários participantes e equipes de desenvolvimento tenham muitas expectativas para uma solução. Quando isso ocorre, é um sinal de que a hipótese é muito vaga. Seguindo as orientações sobre como [criar com o Customer empatia](./considerations/build.md) para construir uma hipótese mais clara.
- **Oportunidade de compilação:** Quando as equipes são desalinhadas porque discordam na maneira de resolver a necessidade do cliente, ela normalmente indica que a equipe está sendo [atrasada por um pico técnico prematuro](./considerations/build.md#reduce-complexity-and-delay-technical-spikes). Para manter a equipe focada no cliente, inicie a primeira iteração e crie um pequeno MVP para abordar parte da hipótese. Para obter mais diretrizes para ajudar a equipe a avançar, consulte [desenvolvendo invenções digitais](./considerations/invention.md).
- **Oportunidade de treinamento:** Quando uma das equipes está desalinhada porque elas precisam de requisitos técnicos profundos e amplos requisitos funcionais, ela revela uma oportunidade de treinamento em metodologias Agile. Quando a cultura de equipe não está pronta para processos Agile, pode ser desafiador inovar e acompanhar o mercado. Para obter recursos de treinamento sobre as práticas DevOps e Agile, consulte:
  - [Evolua suas práticas de DevOps](https://docs.microsoft.com/learn/paths/evolve-your-devops-practices)
  - [Crie aplicativos com o Azure DevOps](https://docs.microsoft.com/learn/paths/build-applications-with-azure-devops)
  - [Implantar aplicativos com o Azure DevOps](https://docs.microsoft.com/learn/paths/deploy-applications-with-azure-devops/)

Usar essa metodologia e as ferramentas de gerenciamento de lista de pendências em cada seção listada acima pode ajudar a criar o alinhamento da solução.

## <a name="next-steps"></a>Próximos passos

Depois que a proposta de valor de negócios é bem alinhada e comunicada, é hora de começar a criar sua solução. Retorne à [inovação de exercícios](./index.md) para obter diretrizes sobre as próximas etapas.

> [!div class="nextstepaction"]
> [Retorne à inovação de exercícios para as próximas etapas](./index.md)
