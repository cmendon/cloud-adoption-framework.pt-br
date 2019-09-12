---
title: Linhas do tempo em um plano de adoção de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Linhas do tempo em um plano de adoção de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 4e095dd90711f201935e88ea5f2712e881a8574b
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828728"
---
# <a name="timelines-in-a-cloud-adoption-plan"></a>Linhas do tempo em um plano de adoção de nuvem

No artigo anterior desta série, as cargas de trabalho e tarefas foram atribuídas a [versões e iterações](./iteration-paths.md). Essas atribuições alimentam as estimativas de linha do tempo neste artigo.

As estruturas de divisão de trabalho (EDT) são comumente usadas em ferramentas de gerenciamento de projeto sequenciais. Elas representam como as tarefas dependentes serão concluídas durante um período de tempo. Essas estruturas funcionam bem quando as tarefas são sequenciais por natureza. As interdependências nas tarefas encontradas na adoção da nuvem tornam difícil o gerenciamento dessas estruturas. Para preencher essa lacuna, você pode estimar as linhas do tempo com base em atribuições de caminho de iteração ocultando a complexidade.

## <a name="estimate-timelines"></a>Estimar linhas do tempo

Para desenvolver uma linha do tempo, comece com versões. Esses objetivos de lançamento criam uma data de destino para qualquer impacto comercial. As iterações ajudam a alinhar essas versões com durações de tempo específicas.

Se forem necessárias etapas mais granulares na linha do tempo, use a atribuição de iteração para indicar as etapas. Para fazer essa atribuição, suponha que a última instância de uma tarefa relacionada à carga de trabalho possa servir como a etapa final. Normalmente, as equipes também marcam a tarefa final como uma etapa.

Para qualquer nível de granularidade, use o último dia da iteração como a data de cada etapa. Isso vincula a conclusão da adoção de carga de trabalho a uma data específica. Você pode acompanhar a data em uma planilha ou uma ferramenta de gerenciamento de projeto sequencial, como o Microsoft Project.

## <a name="delivery-plans-in-azure-devops"></a>Planos de entrega no Azure DevOps

Se você estiver usando o Azure DevOps para gerenciar seu plano de adoção de nuvem, considere o uso da extensão [planos de entrega da Microsoft](https://marketplace.visualstudio.com/items?itemName=ms.vss-plans) . Essa extensão pode criar rapidamente uma representação visual da linha do tempo com base nas atribuições de iteração e versão.
