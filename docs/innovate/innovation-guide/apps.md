---
title: 'Guia de inovação do Azure: Envolver-se por meio de aplicativos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda a inovar, envolvendo por meio de aplicativos usando o Azure.
author: billyclaymyersmsft
ms.author: wimyers
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: df91d44d9b1efc2196b8b322c247dd39ef3d0d1e
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769353"
---
::: zone target="docs"

# <a name="azure-innovation-guide-engage-through-apps"></a>Guia de inovação do Azure: Envolver-se por meio de aplicativos

::: zone-end

::: zone target="chromeless"

# <a name="engage-through-apps"></a>Envolver-se por meio de aplicativos

::: zone-end

A inovação com aplicativos inclui tanto a modernização de seus aplicativos existentes, que são hospedados localmente, quanto a criação de aplicativos nativos de nuvem usando contêineres ou tecnologias sem servidor. Quando se trata de modernização de aplicativo, o Azure fornece serviços PaaS como o Serviço de Aplicativo do Azure para modernizar facilmente seus aplicativos Web e de API existentes escritos em .NET, .NET Core, Java, Node.js, Ruby, Python ou PHP para implantação no Azure. Com um modelo de contêiner de padrão aberto, a criação de microsserviços ou a colocação de seus aplicativos existentes em contêineres e a implantação desses aplicativos no Azure é simples usando serviços gerenciados, tais como Serviços de Kubernetes do Azure, Instâncias de Contêiner do Azure e Aplicativo Web para Contêineres. Tecnologias sem servidor como o Azure Functions e os Aplicativos Lógicos do Azure ajudam você a se concentrar na criação de seu aplicativo usando um modelo de consumo (pagar pelo que usar) em vez de implantar e gerenciar uma infraestrutura.

<!-- markdownlint-disable MD025 -->

# <a name="deliver-value-fastertabdelivervaluefaster"></a>[Entregar valor mais rapidamente](#tab/DeliverValueFaster)

Uma das vantagens das soluções baseadas em nuvem é a capacidade de reunir comentários mais rapidamente e começar a fornecer valor ao usuário final. Quer o usuário final seja um cliente externo ou um usuário em sua empresa, quanto mais rápido você puder obter comentários sobre seus aplicativos, melhor.

## <a name="azure-app-service"></a>Serviço de aplicativo do Azure

O Serviço de Aplicativo do Azure fornece um ambiente de hospedagem para os aplicativos que remove a carga de gerenciamento de infraestrutura e aplicação de patches do sistema operacional. Ele fornece a automação de escala para atender às demandas dos usuários, sendo limitado pelos limites que você define para manter os custos sob controle.

O Serviço de Aplicativo do Azure fornece suporte de primeira classe para linguagens de programação como ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP ou Python. Se você precisa hospedar outra pilha de runtime, o Aplicativo Web para Contêineres permite hospedar de forma rápida e fácil um contêiner do Docker dentro do ambiente do Serviço de Aplicativo do Azure, hospedando, assim, sua pilha de códigos personalizada em um ambiente que retira você do negócio de servidores.

### <a name="action"></a>Ação

Para configurar ou monitorar implantações do Serviço de Aplicativo do Azure:

1. Acesse **Serviços de Aplicativos**.
2. Configure um novo serviço: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os serviços existentes: Selecione o aplicativo desejado na lista de aplicativos hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-cognitive-services"></a>Serviços Cognitivos do Azure

Os Serviços Cognitivos do Azure permitem que você insira inteligência avançada diretamente no aplicativo por meio de um conjunto de APIs, que permitem aproveitar algoritmos de IA e aprendizado de máquina que contam com suporte da Microsoft.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para configurar ou monitorar implantações dos Serviços Cognitivos do Azure:

1. Acesse **Serviços Cognitivos**.
2. Configure um novo serviço: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os serviços existentes: Selecione o serviço desejado na lista de serviços hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-bot-services"></a>Serviços de Bot do Azure

Os Serviços de Bot do Azure estendem seu aplicativo padrão para incluir uma interface de bot natural que usa IA e aprendizado de máquina para criar uma interação para seus clientes.

### <a name="action"></a>Ação

Para configurar ou monitorar implantações dos Serviços de Bot do Azure:

1. Acesse **Serviços de Bot**.
2. Configure um novo serviço: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os serviços existentes: Selecione o bot desejado na lista de serviços hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.BotService%2FbotServices]" submitText="Go to Bot Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-devops"></a>Azure DevOps

Durante seu percurso de inovação, você eventualmente se encontrará no caminho para o DevOps. A Microsoft tem há muito tempo um produto local conhecido como TFS (Team Foundation Server). Durante nosso próprio percurso de inovação, a Microsoft desenvolveu o Azure DevOps para ser um serviço baseado em nuvem que fornece ferramentas de build e de lançamento que dão suporte a várias linguagens de programação e destinos diferentes para suas versões. [Azure DevOps](https://docs.microsoft.com/azure/devops)

## <a name="visual-studio-app-center"></a>Visual Studio App Center

À medida que os aplicativos móveis continuam crescendo em popularidade, aumenta a necessidade de uma plataforma que possa fornecer testes automatizados em dispositivos reais de configurações diversas. O Visual Studio App Center não só fornece um lugar em que você pode testar seus aplicativos em iOS, Android, Windows e macOS, mas fornece uma plataforma de monitoramento capaz de fazer uso do Azure Application Insights para raciocinar rapidamente sobre sua telemetria. Para obter mais informações, confira a [Visão geral do Visual Studio App Center](https://docs.microsoft.com/appcenter).

O Visual Studio App Center também fornece um serviço de notificação que permite que uma única chamada envie notificações para seu aplicativo entre plataformas sem precisar contatar cada serviço de notificação individualmente. Para obter mais informações, confira [Visual Studio ACP (App Center Push)](https://docs.microsoft.com/appcenter/push).

### <a name="read-more"></a>Leia mais

- [Visão geral do Serviço de Aplicativo](https://docs.microsoft.com/azure/app-service/overview)
- [Aplicativos Web para Contêineres: Executar um contêiner personalizado](https://docs.microsoft.com/azure/app-service/containers/quickstart-docker)
- [Uma introdução ao Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)
- [Azure para desenvolvedores .NET e .NET Core](https://docs.microsoft.com/dotnet/azure/?view=azure-dotnet)
- [Documentação do SDK do Azure para Python](https://docs.microsoft.com/azure/python)
- [Azure para desenvolvedores de nuvem do Java](https://docs.microsoft.com/azure/java/?view=azure-java-stable)
- [Criar um aplicativo Web do PHP no Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-php)
- [Documentação do SDK do Azure para JavaScript](https://docs.microsoft.com/azure/javascript)
- [Documentação do SDK do Azure para linguagem Go](https://docs.microsoft.com/azure/go)
- [Soluções de DevOps](https://azure.microsoft.com/solutions/devops)

# <a name="cloud-native-appstabcloudnative"></a>[Aplicativos nativos da nuvem](#tab/CloudNative)

<!-- markdownlint-disable MD026 -->

## <a name="what-are-cloud-native-applications"></a>O que são aplicativos nativos de nuvem?

Os aplicativos nativos de nuvem são compilados do zero e otimizados visando a escala e o desempenho da nuvem. Eles são fracamente acoplados se baseiam em arquiteturas de microsserviços, utilizam serviços gerenciados, podem ser observáveis e tiram proveito da entrega contínua para obter confiabilidade e serem disponibilizados no mercado com mais rapidez. Geralmente, eles são portáteis e podem ser executados em ambientes dinâmicos, tais como nuvens públicas, privadas e híbridas. Os aplicativos nativos de nuvem normalmente são criados usando uma ou mais das seguintes abordagens:

- Microsserviços
- Sem servidor
- Contêiner

## <a name="microservices"></a>Microsserviços

Microsserviços são um estilo de arquitetura de software em que os aplicativos são compostos por módulos pequenos e independentes que se comunicam entre si usando contratos de API bem definidos. Esses módulos de serviço são blocos de construção altamente dissociados, pequenos o suficiente para implementar uma única funcionalidade. Os microsserviços ajudam você a:

- Criar serviços de modo independente.
- Dimensionar serviços de modo autônomo.
- Usar as abordagens mais adequadas para a linguagem de programação e de implantação.
- Isolar pontos de falha.
- Entregar valor mais rapidamente.

### <a name="azure-kubernetes-service-aks"></a>AKS (Serviço de Kubernetes do Azure)

Use um Serviço de Kubernetes totalmente gerenciado para lidar com o provisionamento, a atualização e o dimensionamento de recursos de cluster sob demanda. O AKS facilita a implantação e o gerenciamento de aplicativos em contêineres. Ele oferece Kubernetes sem servidor, uma experiência integrada de CI/CD (integração contínua, entrega contínua) e segurança e governança de nível corporativo. Una suas equipes de desenvolvimento e operações em uma única plataforma para criar, entregar e dimensionar aplicativos rapidamente com confiança.

#### <a name="action"></a>Ação

Para configurar ou monitorar os Serviços de Kubernetes do Azure:

1. Acesse **Serviços de Kubernetes**.
2. Configure um novo serviço: clique no link **Adicionar +** e siga os prompts.
3. Gerencie um serviço existente: Selecione o Serviço de Kubernetes desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.ContainerService%2FmanagedClusters]" submitText="Go to Kubernetes Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="event-based-solutions"></a>Soluções baseadas em eventos

### <a name="azure-functions"></a>Funções do Azure

O Azure Functions fornece uma plataforma para execução de pequenos trechos de código – também chamados de funções – na nuvem. As funções podem ser uma maneira de começar a refatorar seu código em uma arquitetura de microsserviços.

O Azure Functions Runtime dá suporte a várias linguagens, incluindo C#, Java, JavaScript e Python. Para obter uma listagem completa, confira [Linguagens compatíveis no Azure Functions](https://docs.microsoft.com/azure/azure-functions/supported-languages).

Outro benefício das funções é a capacidade de serem disparadas por diferentes ações e eventos, tais como HTTPTriggers, TimerTriggers e gatilhos de outros serviços do Azure, assim como o Armazenamento de Blobs, a Grade Eventos e o Barramento de Serviço. Para obter mais informações sobre gatilhos e associações, confira [Gatilhos e conceitos de associações do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

#### <a name="action"></a>Ação

Para configurar ou monitorar implantações do Azure Functions:

1. Acesse **Aplicativo de Funções**.
2. Configure um novo aplicativo: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os aplicativos existentes: Selecione o aplicativo desejado na lista de Aplicativos de Funções.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites/kind/functionapp]" submitText="Go to Azure Functions" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="serverless-solutions"></a>Soluções sem servidor

Crie aplicativos nativos de nuvem sem provisionar e gerenciar a infraestrutura, utilizando uma plataforma totalmente gerenciada que gerencia o dimensionamento, a disponibilidade e o desempenho para você. Os benefícios das soluções sem servidor do Azure incluem:

- Aumento da velocidade do desenvolvedor
- Aumento do desempenho da equipe
- Melhoria do impacto na organização

### <a name="azure-logic-apps"></a>Aplicativos Lógicos do Azure

Integre dados e aplicativos, em vez de escrever código de integração complexo entre sistemas distintos. Crie visualmente fluxos de trabalho sem servidor com Aplicativos Lógicos do Azure e use suas próprias APIs, funções sem servidor ou conectores de SaaS (software como serviço) prontos para uso, incluindo Salesforce, Microsoft Office 365 e Dropbox.

#### <a name="action"></a>Ação

Para configurar ou monitorar Aplicativos Lógicos do Azure:

1. Acesse **Aplicativos Lógicos**.
2. Configure um novo aplicativo: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os aplicativos existentes: Na lista, selecione o aplicativo lógico desejado.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Logic%2Fworkflows]" submitText="Go to Azure Logic Apps" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="serverless-api-management"></a>Gerenciamento de API sem servidor

Publique, proteja, transforme, mantenha e monitore APIs com o Gerenciamento de API do Azure, um serviço totalmente gerenciado que oferece um modelo de uso projetado e implementado para ser um ajuste natural para aplicativos sem servidor.

#### <a name="action"></a>Ação

Para configurar ou monitorar os serviços de Gerenciamento de API:

1. Acesse **Serviços de Gerenciamento de API**.
2. Configure um novo serviço: clique no link **Adicionar +** e siga os prompts.
3. Gerencie um serviço existente: Selecione o serviço desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="containers"></a>Contêineres

Quando se trata de modernizar seu portfólio de aplicativos, o Azure fornece vários serviços de contêiner para fazer lift-and-shift dos aplicativos existentes para contêineres, bem como criar aplicativos de microsserviços nativos na nuvem para entregar valor aos seus usuários com mais rapidez. Use ferramentas de ponta a ponta de CI/CD e para desenvolvedores para desenvolver, atualizar e implantar aplicativos em contêiner. Gerencie contêineres em escala com um serviço de orquestração de contêiner Kubernetes totalmente gerenciado que se integra ao Azure Active Directory. Qualquer que seja o estágio em que você se encontre em seu percurso de modernização de aplicativo, acelere o desenvolvimento de aplicativos em contêineres atendendo simultaneamente aos seus requisitos de segurança.

### <a name="azure-container-instances"></a>Instâncias de Contêiner do Azure

Execute contêineres do Docker sob demanda em um ambiente gerenciado e sem servidor do Azure. As ACIs (Instâncias de Contêiner do Azure) são uma solução para qualquer cenário que possa operar em contêineres isolados, sem orquestração. Ao executar suas cargas de trabalho nas ACIs, você pode se concentrar em projetar e compilar aplicativos em vez de precisar gerenciar a infraestrutura que os executa.

### <a name="action"></a>Ação

Para configurar ou monitorar as instâncias de contêiner:

1. Acesse **Instâncias de contêiner**.
2. Configure uma nova instância de contêiner: clique no link **Adicionar +** e siga os prompts.
3. Gerenciar instâncias de contêiner existentes: Selecione a instância de contêiner desejada na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ContainerInstance%2FcontainerGroups]" submitText="Go to Container instances" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="azure-red-hat-openshift"></a>Red Hat OpenShift no Azure

O Red Hat OpenShift no Azure oferece uma implantação de autoatendimento flexível de clusters OpenShift totalmente gerenciados. Mantenha a conformidade regulatória e o foco no desenvolvimento de aplicativos, enquanto o patch dos seus nós mestres, de infraestrutura e de aplicativo é aplicado e eles são atualizados e monitorados pela Microsoft e pela Red Hat. Escolha suas próprias soluções de registro, rede, armazenamento ou CI/CD ou então comece rapidamente a usar soluções internas com gerenciamento automatizado de código-fonte, builds de contêiner e aplicativo, implantações, dimensionamento, gerenciamento de integridade e muito mais.

**Acessar [Red Hat OpenShift no Azure](https://docs.microsoft.com/azure/openshift/intro-openshift)**

# <a name="isolate-points-of-failuretabisolatepointsoffailure"></a>[Isolar pontos de falha](#tab/IsolatePointsOfFailure)

Ao começar a fazer a transição de sua fase de teste inicial, avalie maneiras de isolar e remover pontos de falha. Devido à natureza distribuída da nuvem do Azure, você pode projetar seu aplicativo para minimizar as falhas e também melhorar o desempenho.

## <a name="azure-front-door"></a>Porta da frente do Azure

O Azure Front Door fornece um ponto de entrada escalonável e seguro para entregar seu aplicativo em todo o mundo. O Azure Front Door combina otimização do tráfego para melhor desempenho e failover global instantâneo. O Azure Front Door deverá ter precedência sobre o Gerenciador de Tráfego se houver necessidade de encerramento de protocolo TLS ("descarregamento de SSL") ou ainda de processamento de camada de aplicativo por solicitação HTTP/HTTPS.

### <a name="action"></a>Ação

Para configurar ou monitorar as front doors:

1. Acesse **Front Doors**.
2. Configure uma nova front door: clique no link **Adicionar +** e siga os prompts.
3. Gerencie as front doors existentes: Selecione o front door desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ffrontdoors]" submitText="Go to Front Doors" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="traffic-manager"></a>Gerenciador de Tráfego

O Gerenciador de Tráfego fornece balanceamento de carga baseado em DNS que pode ser roteado com base em regras diferentes. Isso ajuda a garantir a resiliência no caso de algum serviço implantado falhar. Você também pode empilhar o Gerenciador de Tráfego para usar o roteamento baseado em falha e o roteamento baseado em desempenho, fornecendo a melhor experiência possível com base na geografia.

### <a name="action"></a>Ação

Para configurar ou monitorar perfis do Gerenciador de Tráfego:

1. Acesse **Perfis do Gerenciador de Tráfego**.
2. Configure um novo perfil: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os perfis existentes: Selecione o perfil desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ftrafficmanagerprofiles]" submitText="Go to Traffic Manager profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-content-delivery-network"></a>Rede de Distribuição de Conteúdo do Azure

O Azure oferece uma CDN (rede de distribuição de conteúdo) que permite que você garanta a entrega oportuna de ativos, colocando-os em cache próximo aos seus usuários finais. Esse cache ajuda a melhorar a experiência de seus clientes e impede problemas ao baixar conteúdo causados por problemas de rede entre o ponto de extremidade da CDN e o datacenter que hospeda o aplicativo. Essa CDN também pode ser usada por aplicativos não hospedados no Azure.

### <a name="action"></a>Ação

Para configurar ou monitorar os perfis de CDN:

1. Acesse **Perfis de CDN**.
2. Configure um novo perfil: clique no link **Adicionar +** e siga os prompts.
3. Gerencie os perfis existentes: Selecione o perfil desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.cdn%2Fprofiles]" submitText="Go to CDN profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="read-more"></a>Leia mais

- [Azure Front Door](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
- [Gerenciador de Tráfego](https://docs.microsoft.com/azure/traffic-manager)
- [Rede de Distribuição de Conteúdo](https://docs.microsoft.com/azure/cdn)
