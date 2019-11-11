---
title: 'Guia de inovação do Azure: Preparar para comentários dos clientes'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Preparar para comentários dos clientes
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 98db83bf842fe4c293eba482572bffbdb50caed6
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565574"
---
::: zone target="docs"

# <a name="azure-innovation-guide-prepare-for-customer-feedback"></a>Guia de inovação do Azure: Preparar para comentários dos clientes

::: zone-end

::: zone target="chromeless"

# <a name="prepare-for-customer-feedback"></a>Preparar para comentários dos clientes

::: zone-end

A adoção pelos usuários e o envolvimento e a retenção desses usuários são fundamentais para a inovação bem-sucedida. Por quê?

Criar uma solução inovadora não é fornecer aos usuários o que eles desejam ou pensam que desejam. É a formulação de uma hipótese que pode ser testada e aprimorada. Esse teste ocorre de duas formas:

- **Quantitativo (comentários dos testes):** Esses comentários medem as ações que esperamos ver.
- **Quantitativo (comentários dos clientes):** Esses comentários nos dizem o que essas métricas significam na opinião do cliente.

Antes de integrar os loops de comentários, você precisa ter um repositório compartilhado para a solução. Um repositório centralizado fornecerá uma maneira de registrar todos os comentários recebidos sobre seu projeto e agir com base neles. O [GitHub](https://github.com) é a página inicial para software livre. Ele também é uma das plataformas usadas com mais frequência para hospedar repositórios de código-fonte para aplicativos desenvolvidos comercialmente. O artigo sobre [criação de repositórios do GitHub](https://docs.microsoft.com/azure/devops/pipelines/repos/github?view=azure-devops&tabs=yaml) pode ajudá-lo a começar com seu repositório.

Cada uma das seguintes ferramentas no Azure se integra (ou é compatível) com projetos hospedados no GitHub:

## <a name="quantitative-feedback-for-web-appstabquantitative-apps"></a>[Comentários quantitativos para aplicativos Web](#tab/Quantitative-Apps)

O Application Insights é uma ferramenta de monitoramento que fornece comentários quantitativos quase em tempo real sobre o uso do aplicativo. Esses comentários podem ajudar a testar e validar a hipótese atual para moldar o próximo recurso ou História de Usuário na lista de pendências.

### <a name="action"></a>Ação

Para exibir dados quantitativos nos aplicativos:

1. Acesse **Application Insights**.
   - Se o aplicativo não aparecer na lista, selecione **Adicionar** e siga os prompts para iniciar a configuração do Application Insights.
   - Se o aplicativo desejado estiver na lista, selecione-o.
1. O painel **Visão geral** inclui algumas estatísticas sobre o aplicativo. Selecione **Painel do Aplicativo** para criar um painel personalizado para ver os dados mais relevantes para sua hipótese.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Go to Application Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Para exibir os dados sobre os aplicativos, acesse o [portal do Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents).

::: zone-end

### <a name="learn-more"></a>Saiba mais

- [Configurar o Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/learn/quick-monitor-portal)
- [Introdução ao Application Insights do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-users)
- [Criar um painel de telemetria](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards)

## <a name="quantitative-feedback-for-apistabquantitative-apis"></a>[Comentários quantitativos para APIs](#tab/Quantitative-APIs)

A economia conectada está mudando a maneira como as empresas inovam. Os mercados e os setores estão sendo interrompidos mais rápido do que nunca. A interrupção assume muitas formas e as empresas devem enfrentar o _dilema dos inovadores_: como definir o ritmo das mudanças sem tropeçar em atividades comerciais em andamento.

As empresas estão usando APIs externamente para alterar a forma como interagem com os respectivos clientes e parceiros. Internamente, elas estão usando APIs para conectar diretamente partes distintas da empresa. A economia de API opera em quatro blocos de construção: social, móvel, de análise e de nuvem. Os aplicativos e serviços podem ser vinculados de maneira rápida e econômica para criar uma proposta de valor estendido.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para registrar dados quantitativos em suas APIs:

1. Acesse **Serviços de Gerenciamento de API**.
2. Selecione a API desejada na lista.
3. Selecione **Configurações de Diagnóstico** na seção **Monitoramento**.

Para exibir dados quantitativos sobre as APIs:

1. Acesse **Serviços de Gerenciamento de API**.
2. Selecione a API desejada na lista.
3. Selecione **Aplicativo** na seção **Monitoramento**.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Para abrir os serviços de Gerenciamento de API, acesse o [portal do Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice).

::: zone-end

### <a name="learn-more"></a>Saiba mais

- [Usar o Azure Monitor para obter comentários sobre as APIs](https://docs.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor)

## <a name="qualitative-feedbacktabqualitative"></a>[Comentários qualitativos](#tab/Qualitative)

É na lista de pendências (ou quadro) que os comentários são registrados como Histórias de Usuário. É nela também que o trabalho relacionado é acompanhado como tarefas acionáveis. Os Azure Boards podem ser diretamente integrados ao GitHub, permitindo uma experiência simples entre o gerenciamento de comentários e de trabalho e qualquer eventual código-fonte.

::: zone target="docs"

### <a name="action"></a>Ação

O Azure Boards e o Azure Pipelines exigem um portal separado do GitHub e do Azure.
Para começar a usar qualquer dessas ferramentas, acesse [Azure DevOps](https://dev.azure.com).

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Ação

Para criar um projeto de DevOps:

1. Acesse **Azure DevOps Projects**.
2. Selecione **Criar projeto de DevOps**.
3. Selecione **Runtime, Estrutura e Serviço**.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/microsoft.visualstudio%2Faccount%2Fproject]" submitText="Go to Azure DevOps Projects" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>Saiba mais

Esses artigos ajudarão você a centralizar e gerenciar comentários usando Azure Boards junto com o GitHub:

- [Introdução ao Azure Boards](https://docs.microsoft.com/azure/devops/boards/github?view=azure-devops)
- [Azure Boards e GitHub](https://docs.microsoft.com/azure/devops/boards/get-started/?view=azure-devops)

## <a name="close-the-loop-with-pipelinestabpipelines"></a>[Fechar o loop com pipelines](#tab/pipelines)

Agir com base nos comentários nem sempre significa adicionar o recurso solicitado pelo cliente. Mas cada ponto de dados deve resultar em alguma alteração. Essa alteração pode ser no modo como você imagina as coisas. Também pode ser uma alteração técnica totalmente diferente da que foi solicitada. De qualquer forma, pipelines de implantação e ferramentas como o Azure Pipelines permitem que você publique rapidamente essas alterações, para que elas possam ser compartilhadas com o cliente com frequência.

### <a name="action"></a>Ação

Para exibir as implantações atuais no pipeline:

1. Acesse **Serviços de Aplicativos**.
2. Selecione o aplicativo desejado na lista.
3. Selecione **Central de Implantação** na seção **Implantação** no painel de Serviços de Aplicativos.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Para exibir os aplicativos no Serviço de Aplicativo, acesse o [portal do Azure](https://ms.portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites).

::: zone-end

### <a name="learn-more"></a>Saiba mais

Comece a criar seus pipelines de implantação:

- [Criar seu primeiro pipeline](https://docs.microsoft.com/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)
- [Tarefas de versão do GitHub](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/github-release?view=azure-devops)
