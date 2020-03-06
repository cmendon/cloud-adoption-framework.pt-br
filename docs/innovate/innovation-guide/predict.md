---
title: 'Inovação do Azure: Prever e influenciar'
description: Saiba mais sobre as soluções do Azure para prever as necessidades dos clientes e integrar previsões de volta à sua solução para influenciar o comportamento do cliente.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 42cf4ffb65456bf1519a0f2bb0f017bb078687d9
ms.sourcegitcommit: 10637acba8c857a6f5aa8c4a80c0649903f60402
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78170963"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guia de inovação do Azure: Prever e influenciar

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prever e influenciar

::: zone-end

Na condição de inovadora, sua empresa terá insights sobre os dados, o comportamento e as necessidades da própria base de clientes. Estudar esses insights pode ajudar a prever as necessidades do cliente, possivelmente antes que os clientes estejam cientes dessas necessidades. Este artigo apresenta algumas abordagens para fornecer soluções preditivas. Nas seções finais, o artigo introduz abordagens para integrar as previsões de volta à sua solução para influenciar os comportamentos do cliente.

A tabela a seguir pode ajudá-lo a encontrar a melhor solução com base em suas necessidades de implementação.

|Serviço  |Modelos predefinidos  |Criar e experimentar  |Treinar e criar com o Python|Habilidades necessárias|
|---------|---------|---------|---------|---------|
|Serviços Cognitivos do Azure|Sim|Não|Não|Habilidades de desenvolvedor e de API|
|Azure Machine Learning Studio|Sim|Sim|Não|Compreensão geral de algoritmos preditivos|
|Serviço do Azure Machine Learning|Sim|Sim|Sim|Cientista de dados|

## <a name="azure-cognitive-services"></a>[Serviços Cognitivos do Azure](#tab/CognitiveServices)

O caminho mais rápido e mais fácil para prever as necessidades do cliente são os Serviços Cognitivos do Azure. Os Serviços Cognitivos permitem que as previsões sejam feitas com base em modelos existentes, que não requerem treinamento adicional. Esses serviços são ideais e eficazes quando não há nenhum cientista de dados na equipe para treinar o modelo preditivo. Para alguns serviços, não é necessário nenhum treinamento. Outros serviços exigem apenas treinamento mínimo.

Para obter uma lista dos serviços disponíveis e a quantidade de treinamento que pode ser necessária, confira [Serviços Cognitivos e aprendizado de máquina](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Ação

Para usar uma API dos Serviços Cognitivos:

1. No [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts), acesse **Serviços Cognitivos**.
2. Selecione **Adicionar** para encontrar uma API de Serviços Cognitivos no Azure Marketplace.
3. Execute um destes procedimentos:
   - Se você souber o nome do serviço gostaria de usar, insira esse nome na caixa **Pesquisar no Marketplace**.
   - Para obter uma lista de APIs de Serviços Cognitivos, selecione o link **Veja Mais** ao lado do cabeçalho dos Serviços Cognitivos.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente os Serviços Cognitivos no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Se os modelos existentes dentro dos Serviços Cognitivos não se alinharem à previsão desejada, o Azure Machine Learning Studio poderá fornecer uma maneira de criar as previsões desejadas sem exigir habilidades profundas de cientistas de dados.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Você pode usar um Azure Machine Learning Studio para criar um modelo e experimentar com ele, da seguinte maneira:

1. No [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces), acesse **Azure Machine Learning Studio**.
2. Selecione **Criar o Workspace do Machine Learning Studio** e siga os prompts para criar um workspace.

   O novo workspace oferece uma interface do tipo "arrastar e soltar" para criar um modelo e experimentar com ele, como uma alternativa ao treinamento profundo.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente o Azure Machine Learning Studio no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-service"></a>[Serviço do Azure Machine Learning](#tab/MachineLearningService)

O Serviço do Azure Machine Learning oferece a abordagem baseada em código mais profunda necessária para um treinamento mais profundo de conjuntos de dados do cliente. Usando linguagens como o Python, os cientistas de dados podem treinar e criar um algoritmo para prever as necessidades do cliente.

### <a name="action"></a>Ação

Um cientista de dados pode usar um Serviço do Azure Machine Learning para treinar e criar um modelo usando linguagens avançadas como Python:

1. Acesse o **Serviço do Azure Machine Learning**.
2. Selecione **Criar workspaces do serviço do Machine Learning** e siga os prompts para criar um workspace.
3. O novo workspace oferece uma abordagem orientada por código para os cientistas de dados treinarem e criarem modelos que exigem análise mais avançada para prever com precisão as necessidades do cliente.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Acesse diretamente o Azure Machine Learning Studio no [portal do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influência

Todas as abordagens mencionadas acima resultam em uma API que expõe o modelo de previsão a aplicativos. Em sua solução, use qualquer uma dessas abordagens para alimentar dados coletados do seu cliente em uma API preditiva. Os resultados podem ser integrados à experiência do cliente como uma próxima etapa sugerida.

As próximas etapas sugeridas podem ajudar a delinear padrões de comportamento do cliente e a influenciar o modo como os clientes reagem. Já que as próximas etapas sugeridas são baseadas em algoritmos preditivos, elas usam as necessidades anteriores dos clientes e os dados disponíveis para prever as futuras necessidades do cliente e atender a essas necessidades, geralmente antes mesmo que o cliente saiba que tais necessidades existem.
