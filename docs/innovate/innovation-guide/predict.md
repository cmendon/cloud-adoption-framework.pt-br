---
title: 'Guia de inovação do Azure: Prever e influenciar'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba prever e influenciar usando o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: b2ed1b072d5226649e5248e350edfa3578978c4c
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769254"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guia de inovação do Azure: Prever e influenciar

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prever e influenciar

::: zone-end

Como inovadora, sua empresa receberá insights sobre os dados, o comportamento e as necessidades de sua base de clientes. Estudar esses insights pode ajudar a prever as necessidades do cliente antes que eles possam estar cientes dessas necessidades. Este artigo apresentará algumas abordagens para fornecer soluções preditivas. Na seção mais adiante, o artigo introduz abordagens para integrar essas previsões de volta à sua solução para influenciar os comportamentos do cliente.

A tabela a seguir foi criada para ajudar a encontrar a melhor solução com base em suas necessidades de implementação.

|Serviço  |Modelos pré-criados  |Criar e experimentar  |Treinar e criar com o Python|Habilidades Necessárias|
|---------|---------|---------|---------|---------|
|Serviços Cognitivos|Sim|Não|Não|Habilidades do Desenvolvedor e de API|
|Azure Machine Learning Studio|Sim|sim|Não|Compreensão geral de algoritmos preditivos|
|Serviço do Azure Machine Learning|Sim|sim|Sim|Cientista de dados|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Serviços Cognitivos do Azure](#tab/CognitiveServices)

O caminho mais rápido e mais fácil para previsões são os Serviços Cognitivas do Azure. Os Serviços Cognitivos permitem que as previsões sejam feitas com base em modelos existentes, que não requerem treinamento adicional. Esses serviços são ideais quando não há um cientista de dados existente na equipe para treinar o modelo preditivo. Para alguns serviços, não é necessário nenhum treinamento. Outros exigem apenas treinamento mínimo.

Para obter uma lista dos serviços disponíveis e a quantidade de treinamento necessário, confira [Serviços Cognitivos e aprendizado de máquina](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Ação

Para usar uma API de serviço cognitivo:

1. Acesse **Serviços Cognitivos**.
2. Clique em **Adicionar+** para encontrar um Serviço Cognitivo no marketplace.
3. Se você souber o nome do serviço que você gostaria de usar, poderá inseri-lo na caixa de texto **Pesquisar no Marketplace**.
4. Como alternativa, para obter uma lista de Serviços Cognitivos, clique no link **Ver mais** ao lado do cabeçalho dos Serviços Cognitivos.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente os Serviços Cognitivos no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Se os modelos existentes dentro dos serviços cognitivos não se alinharem à previsão desejada, o Azure Machine Learning Studio poderá fornecer uma maneira de criar as previsões desejadas sem exigir habilidades profundas de cientistas de dados.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Você pode usar um Azure Machine Learning Studio para criar um modelo e experimentá-lo:

1. Acesse **Azure Machine Learning Studio**.
2. Clique em **Criar o Workspace do Machine Learning Studio** e siga os prompts para criar um workspace.
3. O novo workspace oferece uma interface do tipo "arrastar e soltar" para criar um modelo e experimentá-lo, como uma alternativa ao treinamento profundo.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente o Azure Machine Learning Studio no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Serviço do Azure Machine Learning](#tab/MachineLearningService)

O serviço do Azure Machine Learning oferece a abordagem baseada em código mais profunda necessária para um treinamento mais profundo de conjuntos de dados do cliente. Usando linguagens como Python, os cientistas de dados podem treinar e criar um algoritmo para prever as necessidades do cliente.

### <a name="action"></a>Ação

Um cientista de dados pode usar um Serviço do Azure Machine Learning para treinar e criar um modelo usando linguagens avançadas como Python:

1. Acesse o **Serviço do Azure Machine Learning**.
2. Clique em **Criar workspaces do serviço do Machine Learning** e siga os prompts para criar um workspace.
3. O novo workspace oferece uma abordagem orientada por código para os cientistas de dados treinarem e criarem modelos que exigem análise mais avançada para prever com precisão as necessidades do cliente.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente o Azure Machine Learning Studio no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influência

Todas as abordagens mencionadas acima resultam em uma API que expõe o modelo de previsão a aplicativos. Em sua solução, use qualquer uma dessas abordagens para alimentar dados coletados do seu cliente em uma API preditiva. Os resultados podem ser integrados à experiência do cliente como uma próxima etapa sugerida.

Essas próximas etapas tentam modelar os padrões de comportamento do cliente e influenciar o modo como ele reage. Como as próximas etapas sugeridas são baseadas em algoritmos preditivos, eles usarão os clientes anteriores e os dados disponíveis para prever a necessidade do cliente e atender a essa necessidade, geralmente antes mesmo que o cliente saiba que a necessidade existe.
