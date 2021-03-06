---
title: Desenvolver um plano de mudança de negócios
description: Use a estrutura de adoção de nuvem para o Azure para saber como um plano de mudança de negócios pode ajudá-lo a implementar um plano de adoção de usuário mais amplo.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d1c842c672cc091deaad4e0b7f4ffc89231895c7
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79312026"
---
# <a name="business-change-plan"></a>Plano de alteração do negócio

Tradicionalmente, a TI supervisiona o lançamento de novas cargas de trabalho. Durante uma grande transformação, como uma migração de datacenter ou para a nuvem, um padrão semelhante de adoção de líder de TI poderia ser aplicado. No entanto, a abordagem tradicional pode perder oportunidades para obter um valor comercial adicional. Por esse motivo, antes de promover uma carga de trabalho migrada para a produção, é recomendável implementar uma abordagem mais ampla para a adoção dos usuários. Este artigo descreve as maneiras pelas quais um plano de alteração do negócio é adicionado a um plano de adoção de usuários padrão.

## <a name="traditional-user-adoption-approach"></a>Abordagem de adoção de usuários tradicionais

Os planos de adoção dos usuários concentram-se em como os usuários adotarão uma nova tecnologia ou mudarão para uma determinada tecnologia. Essa abordagem é testada ao longo do tempo para introduzir os usuários a novas ferramentas. Em um típico plano de adoção de usuários, a TI se concentra na instalação, na configuração, na manutenção e no treinamento associados às mudanças técnicas introduzidas no ambiente de negócios.

Embora as abordagens possam variar, os temas gerais estão presentes na maioria dos planos de adoção de usuários. Esses temas normalmente são baseados em uma abordagem de controle de risco e de facilitação que se alinha à mudança incremental. A Matriz Eason, ilustrada na figura abaixo, representa os acionadores por trás desses temas em um espectro de tipos de adoção.

![Matriz Eason de preocupações de adoção dos usuários](../../../_images/migrate/eason-matrix.jpg)

*Matriz Eason de tipos de adoção dos usuários.*

Geralmente esses temas baseiam-se na suposição de que a introdução de novas soluções para os usuários deve se concentrar principalmente no controle de riscos e na facilitação da alteração. Além disso, a TI precisa se concentrar principalmente nos riscos dessa mudança de tecnologia e facilitação.

## <a name="create-business-change-plans"></a>Criar planos de mudança de negócios

Um plano de alteração do negócio vai além da alteração técnica e assume que cada lançamento em um esforço de migração aciona algum nível de mudança no processo de negócios. Ele abrange para o que no upstream e no downstream das alterações técnicas. As questões a seguir ajudam os participantes a pensar a adoção do usuário por uma perspectiva de alteração do negócio a fim de maximizar o impacto nos negócios:

**Questões de upstream.** As questões de upstream examinam os impactos ou as alterações que ocorrem antes da adoção do usuário:

- O [resultado comercial](../../../strategy/business-outcomes/index.md) esperado foi quantificado?
- O impacto nos negócios é mapeado de acordo com [métricas de aprendizagem](../../../strategy/learning-metrics.md) definidas?
- Quais equipes e processos de negócios aproveitam essa solução técnica?
- Na empresa, quem pode alinhar melhor os usuários avançados para os testes e comentários?
- Os líderes de negócios afetados estavam envolvidos na priorização e no planejamento da migração?
- Há algum evento ou data críticos para a empresa que possam ser afetados por essa alteração?
- O plano de alteração do negócio maximiza o impacto, mas minimiza a interrupção nos negócios?
- O tempo de inatividade é esperado? Uma janela de tempo de inatividade foi comunicada aos usuários finais?

**Questões de downstream.** Após a conclusão da adoção, a alteração do negócio pode começar. Infelizmente, é aí que muitos planos de adoção de usuários terminam. As perguntas de downstream ajudam a equipe de estratégia da nuvem a manter o foco na transformação após a conclusão da alteração técnica:

- Os usuários empresariais estão respondendo bem às alterações?
- Agora que a mudança técnica foi adotada, a previsão de desempenho foi mantida?
- Os processos de negócios ou as experiências do cliente estão mudando de acordo com o previsto?
- São necessárias alterações adicionais para alcançar as métricas de aprendizado?
- As alterações se alinham aos resultados comerciais desejados? Se não, por que não?
- São necessárias alterações adicionais para contribuir para os resultados de negócios?
- Algum efeito negativo foi observado como resultado dessa alteração?

O plano de alteração do negócio varia de acordo com a empresa. O objetivo dessas perguntas é ajudar a integrar melhor os negócios às alterações associadas a cada lançamento. Ao examinar cada lançamento não como uma alteração de tecnologia a ser adotada, mas como um plano de alteração do negócio, pode ser mais fácil alcançar os resultados empresariais.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Após documentar e planejar a alteração do negócio, é possível começar os [testes de negócios](./business-test.md).

> [!div class="nextstepaction"]
> [Diretrizes para teste de negócios (UAT) durante a migração](./business-test.md)

## <a name="references"></a>Referências

- Eason, K. (1988) _tecnologia da informação e alteração organizacional_, Nova York: Taylor e Francis.
