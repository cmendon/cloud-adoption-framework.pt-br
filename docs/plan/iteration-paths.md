---
title: Estabelecer iterações e planos de liberação
description: Estabelecer iterações e planos de liberação
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: bdd0150aef6c04b43121b5bef1224bea93191e2c
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76800331"
---
# <a name="establish-iterations-and-release-plans"></a>Estabelecer iterações e planos de liberação

Agile e outras metodologias iterativas se baseiam nos conceitos de iterações e versões. Este artigo descreve a atribuição de iterações e versões durante o planejamento. Essas atribuições orientam a visibilidade da linha do tempo para facilitar as conversas entre os membros da equipe de estratégia de nuvem. As atribuições também alinham tarefas técnicas de forma que a equipe de adoção da nuvem possa ser gerenciada durante a implementação.

## <a name="establish-iterations"></a>Estabelecer iterações

Em uma abordagem iterativa para a implementação técnica, você planeja esforços técnicos em relação a blocos de tempo recorrentes. As iterações tendem a ser de uma semana a blocos de tempo de seis semanas. O consenso sugere que duas semanas seja a duração da iteração média para a maioria das equipes de adoção de nuvem. Mas a escolha da duração da iteração depende do tipo de esforço técnico, da sobrecarga administrativa e da preferência da equipe.

Para começar a alinhar os esforços a uma linha do tempo, sugerimos que você defina um conjunto de iterações que duram 6 a 12 meses.

## <a name="understand-velocity"></a>Entender a velocidade

Alinhar esforços a iterações e versões requer uma compreensão da velocidade. Velocidade é a quantidade de trabalho que pode ser concluída em qualquer iteração específica. Durante o planejamento antecipado, a velocidade é uma estimativa. Após várias iterações, a velocidade se torna um indicador altamente valioso dos compromissos que a equipe pode fazer com confiança.

Você pode medir a velocidade em termos abstratos, como pontos de história. Você também pode medir isso em termos mais tangíveis, como horas. Para a maioria das estruturas iterativas, recomendamos o uso de medidas abstratas para evitar desafios de precisão e percepção. Os exemplos neste artigo representam a velocidade em horas por Sprint. Essa representação torna o tópico mais compreendido universalmente.

**Exemplo:** Uma equipe de adoção em nuvem de cinco pessoas se confirmou em sprints de duas semanas. Dadas as obrigações atuais, como reuniões e suporte a outros processos, cada membro da equipe pode contribuir consistentemente com 20 horas por semana para o esforço de adoção. Para essa equipe, a estimativa de velocidade inicial é de 100 horas por Sprint.

## <a name="iteration-planning"></a>Planejamento de iteração

Inicialmente, você planeja iterações avaliando as tarefas técnicas com base na pendência priorizada. As equipes de adoção de nuvem estimam o esforço necessário para concluir várias tarefas. Essas tarefas são atribuídas à primeira iteração disponível.

Durante o planejamento da iteração, as equipes de adoção de nuvem validam e refinam estimativas Eles fazem isso até que tenham alinhado toda a velocidade disponível a tarefas específicas. Esse processo continua para cada carga de trabalho priorizada até que todos os esforços se alinhem a uma iteração prevista.

Nesse processo, a equipe valida as tarefas atribuídas ao próximo Sprint. A equipe atualiza suas estimativas com base na conversa da equipe sobre cada tarefa. A equipe, em seguida, adiciona cada tarefa estimada ao próximo Sprint até que a velocidade disponível seja atendida. Por fim, a equipe estima tarefas adicionais e as adiciona à próxima iteração. A equipe executa essas etapas até que a velocidade dessa iteração também seja esgotada.

O processo anterior continua até que todas as tarefas sejam atribuídas a uma iteração.

**Exemplo:** Vamos criar o exemplo anterior. Suponha que cada migração de carga de trabalho exija 40 tarefas. Suponha também que você estima cada tarefa para levar uma média de uma hora. A estimativa combinada é de aproximadamente 40 horas por migração de carga de trabalho. Se essas estimativas permanecerem consistentes para todas as 10 das cargas de trabalho priorizadas, essas cargas de trabalho levarão 400 horas.

A velocidade definida no exemplo anterior sugere que a migração das primeiras 10 cargas de trabalho terá quatro iterações, que é de dois meses de tempo do calendário. A primeira iteração consistirá em 100 tarefas que resultam na migração de duas cargas de trabalho. Na próxima iteração, uma coleção semelhante de 100 tarefas resultará na migração de três cargas de trabalho.

> [!WARNING]
> Os números de tarefas e estimativas anteriores são estritamente usados como um exemplo. As tarefas técnicas raramente são consistentes. Você não deve ver esse exemplo como uma reflexão da quantidade de tempo necessária para migrar uma carga de trabalho.

## <a name="release-planning"></a>Planejamento de liberação

Na adoção da nuvem, uma versão é definida como uma coleção de resultados que produzem um valor comercial suficiente para justificar o risco de interrupção nos processos de negócios.

A liberação de qualquer alteração relacionada à carga de trabalho em um ambiente de produção cria algumas alterações nos processos de negócios. O ideal é que essas alterações sejam contínuas e os negócios vejam o valor das alterações sem interrupções significativas no serviço. Mas o risco de interrupções nos negócios está presente em qualquer mudança e não deve ser pouco levado.

Para garantir que uma alteração seja justificada por seu retorno potencial, a equipe de estratégia de nuvem deve participar do planejamento de versão. Depois que as tarefas são alinhadas a sprints, a equipe pode determinar uma linha do tempo aproximada de quando cada carga de trabalho estará pronta para a versão de produção. A equipe de estratégia de nuvem examinaria o tempo de cada versão. Em seguida, a equipe identificaria o ponto de inflexão entre o risco e o valor comercial.

**Exemplo:** Continuando o exemplo anterior, a equipe de estratégia de nuvem analisou o plano de iteração. A revisão identificou dois pontos de versão. Durante a segunda iteração, um total de cinco cargas de trabalho estará pronto para migração. Essas cinco cargas de trabalho fornecerão um valor comercial significativo e dispararão a primeira versão. A próxima versão chegará a duas iterações posteriormente, quando as próximas cinco cargas de trabalho estiverem prontas para o lançamento.

## <a name="assign-iteration-paths-and-tags"></a>Atribuir caminhos e marcas de iteração

Para clientes que gerenciam planos de adoção de nuvem no Azure DevOps, os processos anteriores são refletidos por meio da atribuição de um caminho de iteração para cada tarefa e história de usuário. Também é recomendável marcar cada carga de trabalho com uma versão específica. Essa marcação e a atribuição alimentam a população automática de relatórios de linha do tempo.

## <a name="next-steps"></a>Próximos passos

[Estimar as linhas](./timelines.md) do tempo para comunicar as expectativas corretamente.

> [!div class="nextstepaction"]
> [Estimar linhas do tempo](./timelines.md)
