---
title: 'Guia de inovação do Azure: Democratizar os dados'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como democratizar os dados usando o Azure
author: absheik
ms.author: absheik
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 5203ae99a7cf3c5e78f72edf020234f3ea703d36
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251877"
---
::: zone target="docs"

# <a name="azure-innovation-guide-democratize-data"></a>Guia de inovação do Azure: Democratizar os dados

::: zone-end

::: zone target="chromeless"

# <a name="democratize-data"></a>Democratizar os dados

::: zone-end

Uma das primeiras etapas para democratizar os dados é aprimorar a detectabilidade deles. Catalogar e gerenciar o compartilhamento de dados pode ajudar as empresas a obterem o maior valor possível dos seus ativos de informações existentes. Um catálogo de dados torna as fontes de dados facilmente identificáveis e compreensíveis para os usuários que gerenciam os dados. O Catálogo de Dados do Azure permite o gerenciamento dentro de uma empresa, enquanto o Azure Data Share permite o gerenciamento e o compartilhamento fora da empresa.

Os serviços do Azure que fornecem processamento de dados como o Azure Time Series Insights e o Stream Analytics são outras funcionalidades que os clientes e parceiros aproveitam com êxito para suas respectivas necessidades de inovação.

# <a name="catalogtabcatalog"></a>[Catálogo](#tab/Catalog)

## <a name="azure-data-catalog"></a>Catálogo de Dados do Azure

O Catálogo de Dados do Azure aborda os desafios de descoberta de consumidores de dados, além de permitir que os produtores de dados mantenham ativos de informações. Ele faz a ponte na lacuna que existe entre a TI e os negócios, permitindo que todos possam contribuir com suas próprias ideias. Você pode armazenar seus dados onde desejar e conectar-se com as ferramentas que deseja usar. Com o Catálogo de Dados do Azure, é possível controlar quem pode descobrir ativos de dados registrados. É possível integrar-se com as ferramentas e os processos existentes pelo uso das APIs REST abertas.

> [!div class="checklist"]
>
> - Registrar
> - Pesquisar e anotar
> - Conectar e gerenciar

::: zone target="docs"

**Acessar a [Documentação do Catálogo de Dados do Azure](https://docs.microsoft.com/azure/data-catalog)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

É possível usar apenas um Catálogo de Dados do Azure por organização. Se um catálogo de dados já tiver sido criado para sua organização, você não poderá adicionar catálogos adicionais.

Para criar um Catálogo de Dados do Azure para sua organização:

1. Acesse o **Catálogo de Dados do Azure**.
2. Selecione **Criar**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataCatalog%2Fcatalogs]" submitText="Go to Azure Data Catalog" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="sharetabshare"></a>[Compartilhar](#tab/Share)

## <a name="azure-data-share"></a>Azure Data Share

Alcançar um equilíbrio entre o compartilhamento de dados e o controle de quais dados são compartilhados e com quem é o principal fator de inovação. Ao tentar democratizar os dados, as organizações podem facilmente ser sobrecarregadas pela enormidade do volume, do ritmo e do ciclo de vida dos dados. O Azure Data Share garante que os provedores, ao especificar termos de uso para os próprios compartilhamento de dados, possam controlar como seus próprios dados são tratados. O consumidor de dados deve aceitar esses termos antes de poder receber os dados. Os provedores de dados podem especificar a frequência com que seus consumidores de dados recebem atualizações. O acesso a novas atualizações pode ser revogado a qualquer momento pelo provedor de dados.

> [!div class="checklist"]
>
> - Criar um Data Share.
> - Adicionar conjuntos de dados a seu Data Share.
> - Habilitar uma agenda de sincronização para seu Data Share.
> - Adicionar destinatários a seu Data Share.

::: zone target="docs"
**Acessar a [Documentação do Azure Data Share](https://docs.microsoft.com/azure/data-share)**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para criar um compartilhamento de dados:

1. Acesse **Azure Data Shares**.
2. Selecione **Criar um compartilhamento de dados**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataShare%2Faccounts]" submitText="Go to Azure Data Shares" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="insightstabinsights"></a>[Insights](#tab/Insights)

## <a name="azure-time-series-insights"></a>Azure Time Series Insights

Os recursos de inovação de dados de Azure Time Series Insights são intermináveis. Ele fornece exploração de dados quase em tempo real de fluxos de dados e armazenamento em várias camadas para dados de série temporal em escala de IoT. Ele também oferece modelos para contextualizar dados telemétricos brutos e derivar insights baseados em ativos. Você pode fornecer integração perfeita e contínua com outras soluções de dados, fornecer análise de causa raiz e detecção de anomalias, incluindo opções de aplicativo personalizadas na plataforma Time Series Insights.

> [!div class="checklist"]
>
> - Planeje o ambiente do Time Series Insights.
> - Visualize dados no explorador.
> - Entenda a retenção de dados.
> - Desenvolva e compartilhe modos de exibição personalizados.

::: zone target="docs"

**Acessar a [Visão geral do Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-update-overview)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para criar um ambiente do Azure Time Series Insights:

1. Acesse **ambientes do Azure Time Series Insights**.
2. Selecione **Criar um ambiente do Time Series Insights**.
3. Aponte esse ambiente para uma origem de evento, seja ela o Hub IoT do Azure ou os Hubs de Eventos.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.TimeSeriesInsights%2Fenvironments]" submitText="Go to Azure Time Series Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
