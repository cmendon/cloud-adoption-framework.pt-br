---
title: 'Guia de inovação do Azure: Democratizar os dados'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como democratizar os dados usando o Azure.
author: absheik
ms.author: absheik
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 65c1ecd1d722286fb495af3069862131629c35d1
ms.sourcegitcommit: 0d14d89b9004a65a322724342cb5086ad2c77467
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777084"
---
::: zone target="docs"

# <a name="azure-innovation-guide-democratize-data"></a>Guia de inovação do Azure: Democratizar os dados

::: zone-end

::: zone target="chromeless"

# <a name="democratize-data"></a>Democratizar os dados

::: zone-end

Uma das primeiras etapas para democratizar os dados é aprimorar a detectabilidade deles. Catalogar e gerenciar o compartilhamento de dados pode ajudar as empresas a obterem o maior valor possível dos seus ativos de informações existentes. Um catálogo de dados torna as fontes de dados facilmente detectáveis e reconhecíveis para os usuários que gerenciam os dados. O Catálogo de Dados do Azure permite o gerenciamento dentro de uma empresa, enquanto o Azure Data Share permite o gerenciamento e o compartilhamento fora da empresa.

Os serviços do Azure que fornecem processamento de dados como o Azure Time Series Insights e o Stream Analytics são outras funcionalidades que os clientes e parceiros aproveitam com êxito para as respectivas necessidades de inovação.

# <a name="catalogtabcatalog"></a>[Catálogo](#tab/Catalog)

## <a name="azure-data-catalog"></a>Catálogo de Dados do Azure

O Catálogo de Dados do Azure aborda os desafios de descoberta de consumidores de dados, além de permitir que os produtores de dados mantenham ativos de informações. Faça a ponte na lacuna que existe entre a TI e os negócios, permitindo que todos possam contribuir com suas ideias. Deixe os seus dados ativos no lugar que você quiser, conecte-se com as ferramentas que você escolher. Controle quem pode descobrir ativos de dados registrados. Integre-se com as ferramentas e os processos existentes com as APIs REST abertas.

> [!div class="checklist"]
>
> - Registrar
> - Pesquisar e anotar
> - Conectar e gerenciar

::: zone target="docs"

**Acesse o [Catálogo de Dados do Azure](https://docs.microsoft.com/azure/data-catalog).**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Apenas um Catálogo de Dados do Azure é compatível por organização. Se um catálogo já tiver sido criado para sua organização, você não poderá adicionar catálogos adicionais.

Para criar o Catálogo de Dados do Azure para sua organização:

1. Acesse o **Catálogo de Dados do Azure**.
2. Selecione o botão **Criar**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataCatalog%2Fcatalogs]" submitText="Go to Azure Data Catalog" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="sharetabshare"></a>[Compartilhar](#tab/Share)

## <a name="azure-data-share"></a>Azure Data Share

Alcançar o equilíbrio entre o compartilhamento de dados e o controle de quais dados são compartilhados e com quem é o principal fator de inovação. Ao buscar democratizar os dados, as organizações podem facilmente ser sobrecarregadas pela enormidade do volume, do ritmo e do ciclo de vida desses dados. O uso do Azure Data Share garante que o provedor mantenha o controle de como seus dados são tratados especificando termos de uso para o compartilhamento de dados dele. O consumidor de dados deve aceitar esses termos antes de poder receber os dados. Os provedores de dados podem especificar a frequência com que seus consumidores de dados recebem atualizações. O acesso a novas atualizações pode ser revogado a qualquer momento pelo provedor de dados.

> [!div class="checklist"]
>
> - Criar um Data Share.
> - Adicionar conjuntos de dados a seu Data Share.
> - Habilitar uma agenda de sincronização para seu Data Share.
> - Adicionar destinatários a seu Data Share.

::: zone target="docs"
**Acesse o [Azure Data Share](https://docs.microsoft.com/azure/data-share).**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para criar um Azure Data Share:

1. Acesse o **Azure Data Share**.
2. Clique em **Criar um Data Share**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataShare%2Faccounts]" submitText="Go to Azure Data Share" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

Use o [Azure Open Datasets](https://docs.microsoft.com/azure/open-datasets/overview-what-are-open-datasets) para aprimorar sua análise incorporando dados de [feriados](https://azure.microsoft.com/services/open-datasets/catalog/public-holidays), [clima](https://azure.microsoft.com/services/open-datasets/catalog/noaa-global-forecast-system) e [imagens espaciais](https://azure.microsoft.com/services/open-datasets/catalog/hls) em seus modelos.

As informações sobre [democratização de processos comerciais](https://docs.microsoft.com/business-applications-release-notes/october18/microsoft-flow/democratize-business-processes) e [capacitação dos cidadãos desenvolvedores](https://docs.microsoft.com/business-applications-release-notes/october18/microsoft-flow/empower-citizen-developers) encontradas aqui são as próximas etapas.

# <a name="insightstabinsights"></a>[Insights](#tab/Insights)

## <a name="azure-time-series-insights"></a>Azure Time Series Insights

Fazendo a exploração de dados quase em tempo real dos fluxos de dados e do armazenamento em várias camadas para os dados e modelos de série temporal em escala de IoT para contextualizar telemetria bruta e derivar informações baseadas em ativos, as funcionalidades de inovação de dados são intermináveis. Você pode fornecer integração perfeita e contínua com outras soluções de dados, fornecer análise de causa raiz e detecção de anomalias, incluindo opções de aplicativo personalizadas na plataforma Time Series Insights.

> [!div class="checklist"]
>
> - Planeje o ambiente do Time Series Insights.
> - Visualize dados no explorador.
> - Entenda a retenção de dados.
> - Desenvolva e compartilhe modos de exibição personalizados.

::: zone target="docs"

**Acesse o [Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-update-overview).**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Ação

Para criar um ambiente do Azure Time Series Insights:

1. Acesse o **Azure Time Series Insights**.
2. Clique em **Criar um ambiente do Time Series Insights**.
3. Aponte esse ambiente para uma origem de evento, seja ela o Hub IoT ou o Hub de Eventos.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.TimeSeriesInsights%2Fenvironments]" submitText="Go to Azure Time Series Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
