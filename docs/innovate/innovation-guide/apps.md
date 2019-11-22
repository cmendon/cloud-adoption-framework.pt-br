---
title: 'Guia de inovação do Azure: Envolver clientes por meio de aplicativos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda a inovar, envolvendo clientes por meio de aplicativos usando o Azure
author: billyclaymyersmsft
ms.author: wimyers
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 09d5828e7b90a7530158b7f031e4f6f25d4b1d96
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251915"
---
::: zone target="docs"

# <a name="azure-innovation-guide-engage-customers-through-apps"></a>Guia de inovação do Azure: Envolver clientes por meio de aplicativos

::: zone-end

::: zone target="chromeless"

# <a name="engage-customers-through-apps"></a>Envolver clientes por meio de aplicativos

::: zone-end

A inovação com aplicativos inclui tanto a modernização de seus aplicativos existentes, que são hospedados localmente, quanto a criação de aplicativos nativos de nuvem usando contêineres ou tecnologias sem servidor. O Azure fornece serviços PaaS como o Serviço de Aplicativo do Azure para ajudar você a modernizar facilmente seus aplicativos Web e de API existentes escritos em .NET, .NET Core, Java, Node.js, Ruby, Python ou PHP para implantação no Azure.

Com um modelo de contêiner de padrão aberto, a criação de microsserviços ou a colocação de seus aplicativos existentes em contêineres e a implantação desses aplicativos no Azure é simples usando serviços gerenciados, tais como o Serviço de Kubernetes do Azure, as Instâncias de Contêiner do Azure e o Aplicativo Web para Contêineres. Tecnologias sem servidor como o Azure Functions e os Aplicativos Lógicos do Azure usam um modelo de consumo (pagar pelo que usar) e ajudam você a se concentrar na criação de seu aplicativo em vez de implantar e gerenciar uma infraestrutura.

<!-- markdownlint-disable MD025 -->

# <a name="deliver-value-fastertabdelivervaluefaster"></a>[Entregar valor mais rapidamente](#tab/DeliverValueFaster)

Uma das vantagens das soluções baseadas em nuvem é a capacidade de reunir comentários mais rapidamente e começar a fornecer valor ao usuário. Quer o usuário seja um cliente externo ou um usuário em sua empresa, quanto mais rápido você puder obter comentários sobre seus aplicativos, melhor.

## <a name="azure-app-service"></a>Serviço de aplicativo do Azure

O Serviço de Aplicativo do Azure fornece um ambiente de hospedagem para os aplicativos que remove a carga de gerenciamento de infraestrutura e aplicação de patches do sistema operacional. Ele fornece a automação de escala para atender às demandas dos usuários, sendo limitado pelos limites que você define para manter os custos sob controle.

O Serviço de Aplicativo do Azure fornece suporte de primeira classe para linguagens de programação como ASP.NET, ASP.NET Core, Java, Ruby, Node.js, PHP e Python. Se você precisa hospedar outra pilha de runtime, o Aplicativo Web para Contêineres permite hospedar de forma rápida e fácil um contêiner do Docker dentro do Serviço de Aplicativo, de modo que você pode hospedar sua pilha de códigos personalizada em um ambiente que retira você do negócio de servidores.

### <a name="action"></a>Ação

Para configurar ou monitorar implantações do Serviço de Aplicativo do Azure:

1. Acesse **Serviços de Aplicativos**.
2. Configurar um novo serviço: Selecione **Adicionar** e siga os avisos.
3. Gerencie os serviços existentes: Selecione o aplicativo desejado na lista de aplicativos hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites]" submitText="Go to App Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-cognitive-services"></a>Serviços Cognitivos do Azure

Com os Serviços Cognitivos do Azure, é possível inserir inteligência avançada diretamente no aplicativo por meio de um conjunto de APIs que permitem aproveitar algoritmos de IA e aprendizado de máquina que contam com suporte da Microsoft.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para configurar ou monitorar implantações dos Serviços Cognitivos do Azure:

1. Acesse **Serviços Cognitivos**.
2. Configurar um novo serviço: Selecione **Adicionar** e siga os avisos.
3. Gerencie os serviços existentes: Selecione o serviço desejado na lista de serviços hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-bot-service"></a>Serviço de Bot do Azure

O Serviço de Bot do Azure estende seu aplicativo padrão pela adição de uma interface de bot natural que usa IA e aprendizado de máquina para criar uma nova maneira de interagir com seus clientes.

### <a name="action"></a>Ação

Para configurar ou monitorar implantações dos Serviços de Bot do Azure:

1. Acesse **Serviços de Bot**.
2. Configurar um novo serviço: Selecione **Adicionar** e siga os avisos.
3. Gerencie os serviços existentes: Selecione o bot desejado na lista de serviços hospedados.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.BotService%2FbotServices]" submitText="Go to Bot Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-devops"></a>Azure DevOps

Durante seu percurso de inovação, você eventualmente se encontrará no caminho para o DevOps. A Microsoft tem há muito tempo um produto local conhecido como TFS (Team Foundation Server). Durante nosso próprio percurso de inovação, a Microsoft desenvolveu o Azure DevOps, um serviço baseado em nuvem que fornece ferramentas de build e de lançamento que dão suporte a várias linguagens de programação e destinos para suas versões. Para obter mais informações, confira [Azure DevOps](https://docs.microsoft.com/azure/devops).

## <a name="visual-studio-app-center"></a>Visual Studio App Center

À medida que os aplicativos móveis continuam crescendo em popularidade, aumenta a necessidade de uma plataforma que possa fornecer testes automatizados em dispositivos reais de configurações diversas. O Visual Studio App Center não fornece apenas um local onde você pode testar seus aplicativos em iOS, Android, Windows e macOS. Ele também fornece uma plataforma de monitoramento que pode usar o Azure Application Insights para analisar a telemetria com rapidez e facilidade. Para obter mais informações, confira [Visão geral do Visual Studio App Center](https://docs.microsoft.com/appcenter).

O Visual Studio App Center também fornece um serviço de notificação que permite usar uma única chamada para enviar notificações para o aplicativo entre plataformas sem precisar contatar cada serviço de notificação individualmente. Para obter mais informações, confira [Visual Studio ACP (App Center Push)](https://docs.microsoft.com/appcenter/push).

### <a name="learn-more"></a>Saiba mais

- [Visão geral do Serviço de Aplicativo](https://docs.microsoft.com/azure/app-service/overview)
- [Aplicativo Web para Contêineres: Executar um contêiner personalizado](https://docs.microsoft.com/azure/app-service/containers/quickstart-docker)
- [Uma introdução ao Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)
- [Azure para desenvolvedores .NET e .NET Core](https://docs.microsoft.com/dotnet/azure/?view=azure-dotnet)
- [Documentação do SDK do Azure para Python](https://docs.microsoft.com/azure/python)
- [Azure para desenvolvedores de nuvem do Java](https://docs.microsoft.com/azure/java/?view=azure-java-stable)
- [Criar um aplicativo Web do PHP no Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-php)
- [Documentação do SDK do Azure para JavaScript](https://docs.microsoft.com/azure/javascript)
- [Documentação do SDK do Azure para linguagem Go](https://docs.microsoft.com/azure/go)
- [Soluções de DevOps](https://azure.microsoft.com/solutions/devops)

# <a name="create-cloud-native-appstabcloudnative"></a>[Criar aplicativos nativos de nuvem](#tab/CloudNative)

<!-- markdownlint-disable MD026 -->

## <a name="what-are-cloud-native-applications"></a>O que são aplicativos nativos de nuvem?

Os aplicativos nativos de nuvem são compilados do zero e otimizados visando a escala e o desempenho da nuvem. Eles são fracamente acoplados se baseiam em arquiteturas de microsserviços, utilizam serviços gerenciados, podem ser observáveis e tiram proveito da entrega contínua para obter confiabilidade e serem disponibilizados no mercado com mais rapidez. Geralmente, eles são portáteis e podem ser executados em ambientes dinâmicos, tais como nuvens públicas, privadas e híbridas. Os aplicativos nativos de nuvem normalmente são criados usando uma ou mais das seguintes abordagens:

- Microsserviços
- Sem servidor
- Contêineres

## <a name="microservices"></a>Microsserviços

Microsserviços são um estilo de arquitetura de software em que os aplicativos são compostos por módulos pequenos e independentes que se comunicam entre si usando contratos de API bem definidos. Esses módulos de serviço são blocos de construção altamente dissociados, pequenos o suficiente para implementar uma única funcionalidade. Os microsserviços ajudam você a:

- Criar serviços de modo independente.
- Dimensionar serviços de modo autônomo.
- Usar as abordagens mais adequadas para linguagens de programação e de implantação.
- Isolar pontos de falha.
- Entregar valor mais rapidamente.

### <a name="azure-kubernetes-service-aks"></a>AKS (Serviço de Kubernetes do Azure)

Use um Serviço de Kubernetes totalmente gerenciado para lidar com o provisionamento, a atualização e o dimensionamento de recursos de cluster sob demanda. O AKS facilita a implantação e o gerenciamento de aplicativos em contêineres. Ele oferece Kubernetes sem servidor, uma experiência integrada de CI/CD (integração contínua, entrega contínua) e segurança e governança de nível corporativo. Una suas equipes de desenvolvimento e operações em uma única plataforma para criar, entregar e dimensionar aplicativos rapidamente com confiança.

#### <a name="action"></a>Ação

Para configurar ou monitorar um Serviço de Kubernetes do Azure:

1. Vá para **Serviços de Kubernetes do Azure**.
2. Configurar um novo serviço: Selecione **Adicionar** e siga os avisos.
3. Gerencie os serviços existentes: Selecione o Serviço de Kubernetes desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.ContainerService%2FmanagedClusters]" submitText="Go to Azure Kubernetes services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="event-based-solutions"></a>Soluções baseadas em eventos

### <a name="azure-functions"></a>Funções do Azure

O Azure Functions fornece uma plataforma para execução de pequenas unidades de código, também chamadas de funções, na nuvem. As funções podem ser uma maneira de começar a refatorar seu código em uma arquitetura de microsserviços.

O Azure Functions Runtime dá suporte a várias linguagens de programação, incluindo C#, Java, JavaScript e Python. Para obter uma listagem completa, confira [Linguagens compatíveis com o Azure Functions](https://docs.microsoft.com/azure/azure-functions/supported-languages).

Outro benefício das funções é sua capacidade de serem disparadas por diferentes ações e eventos, tais como HTTPTriggers, TimerTriggers e gatilhos de outros serviços do Azure, assim como o Armazenamento de Blobs, a Grade de Eventos e o Barramento de Serviço. Para obter mais informações sobre gatilhos e associações, confira [Gatilhos e conceitos de associações do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

#### <a name="action"></a>Ação

Para configurar ou monitorar implantações do Azure Functions:

1. Acesse **Aplicativo de Funções**.
2. Configurar um novo aplicativo: Selecione **Adicionar** e siga os avisos.
3. Gerencie os aplicativos existentes: Selecione o aplicativo desejado na lista de aplicativos de funções.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Web%2Fsites/kind/functionapp]" submitText="Go to Azure Functions" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="serverless-solutions"></a>Soluções sem servidor

Crie aplicativos nativos de nuvem sem provisionar e gerenciar a infraestrutura, utilizando uma plataforma totalmente gerenciada que lida com o dimensionamento, a disponibilidade e o desempenho para você. Os benefícios das soluções sem servidor do Azure incluem:

- aumento da velocidade do desenvolvedor;
- aumento do desempenho da equipe;
- melhoria do impacto na organização.

### <a name="azure-logic-apps"></a>Aplicativos Lógicos do Azure

Integre dados e aplicativos, em vez de escrever código de integração complexo entre sistemas distintos. Crie visualmente fluxos de trabalho sem servidor com Aplicativos Lógicos do Azure e use suas próprias APIs, funções sem servidor ou conectores de SaaS (software como serviço) prontos para uso, incluindo Salesforce, Microsoft Office 365 e Dropbox.

#### <a name="action"></a>Ação

Para configurar ou monitorar Aplicativos Lógicos do Azure:

1. Acesse **Aplicativos Lógicos**.
2. Configurar um novo aplicativo: Selecione **Adicionar** e siga os avisos.
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
2. Configurar um novo serviço: Selecione **Adicionar** e siga os avisos.
3. Gerencie os serviços existentes: Selecione o serviço desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ApiManagement%2Fservice]" submitText="Go to API Management services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="containers"></a>Contêineres

Para modernizar seu portfólio de aplicativos, o Azure fornece vários serviços de contêiner para migrar os aplicativos existentes para contêineres, bem como criar aplicativos de microsserviços nativos na nuvem para que seja possível entregar valor aos seus usuários com mais rapidez. Use ferramentas de ponta a ponta de CI/CD e para desenvolvedores para desenvolver, atualizar e implantar aplicativos em contêiner. Gerencie contêineres em escala com um serviço de orquestração de contêiner Kubernetes totalmente gerenciado que se integra ao Azure Active Directory. Qualquer que seja o estágio em que você se encontre em seu percurso de modernização de aplicativo, acelere o desenvolvimento de aplicativos em contêineres atendendo simultaneamente aos seus requisitos de segurança.

### <a name="azure-container-instances"></a>Instâncias de Contêiner do Azure

Execute contêineres do Docker sob demanda em um ambiente gerenciado e sem servidor do Azure. As Instâncias de Contêiner do Azure são uma solução para qualquer cenário que possa operar em contêineres isolados, sem orquestração. Ao executar suas cargas de trabalho em Instâncias de Contêiner, você pode se concentrar em projetar e compilar aplicativos em vez de precisar gerenciar a infraestrutura que os executa.

### <a name="action"></a>Ação

Para configurar ou monitorar instâncias de contêiner:

1. Acesse **Instâncias de contêiner**.
2. Configure uma nova instância de contêiner: Selecione **Adicionar** e siga os avisos.
3. Gerenciar instâncias de contêiner existentes: Selecione a instância de contêiner desejada na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.ContainerInstance%2FcontainerGroups]" submitText="Go to Container instances" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="azure-red-hat-openshift"></a>Red Hat OpenShift no Azure

O Red Hat OpenShift no Azure oferece uma implantação de autoatendimento flexível de clusters OpenShift totalmente gerenciados. Mantenha a conformidade regulatória e o foco no desenvolvimento de aplicativos, enquanto o patch dos seus nós mestres, de infraestrutura e de aplicativo é aplicado e eles são atualizados e monitorados pela Microsoft e pela Red Hat. Escolha seu próprio Registro, rede, armazenamento ou soluções CI/CD. Ou comece rapidamente usando soluções internas com gerenciamento de código-fonte automatizado, builds de contêiner e de aplicativo, implantações, dimensionamento, gerenciamento de integridade e mais.

**Acessar [Red Hat OpenShift no Azure](https://docs.microsoft.com/azure/openshift/intro-openshift)**

# <a name="isolate-points-of-failuretabisolatepointsoffailure"></a>[Isolar pontos de falha](#tab/IsolatePointsOfFailure)

Ao começar a fazer a transição de sua fase de teste inicial, avalie maneiras de isolar e remover pontos de falha. Devido à natureza distribuída da plataforma de nuvem do Azure, você pode projetar seu aplicativo para minimizar as falhas e também melhorar o desempenho.

## <a name="azure-front-door-service"></a>Azure Front Door Service

O Azure Front Door Service fornece um ponto de entrada escalonável e seguro que você pode usar para entregar seu aplicativo em todo o mundo. O Azure Front Door Service combina otimização do tráfego para melhor desempenho e failover global instantâneo. Convém usar o Azure Front Door Service em vez do Gerenciador de Tráfego do Azure se você precisar de encerramento de protocolo TLS ("descarregamento de SSL") ou ainda de processamento de camada de aplicativo por solicitação HTTP/HTTPS.

### <a name="action"></a>Ação

Para configurar ou monitorar Front Doors:

1. Acesse **Front Doors**.
2. Configurar uma nova Front Door: Selecione **Adicionar** e siga os avisos.
3. Gerencie as Front Doors existentes: Selecione a Front Door desejada na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ffrontdoors]" submitText="Go to Front Doors" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="traffic-manager"></a>Gerenciador de Tráfego

O Gerenciador de Tráfego fornece balanceamento de carga baseado em DNS que pode ser roteado com base em regras diferentes. Essa funcionalidade ajuda a garantir a resiliência no caso de algum serviço implantado falhar. Você também pode empilhar o Gerenciador de Tráfego para usar o roteamento baseado em falha e o roteamento baseado em desempenho para fornecer a melhor experiência possível com base na geografia.

### <a name="action"></a>Ação

Para configurar ou monitorar perfis do Gerenciador de Tráfego:

1. Acesse **Perfis do Gerenciador de Tráfego**.
2. Configurar um novo perfil: Selecione **Adicionar** e siga os avisos.
3. Gerencie os perfis existentes: Selecione o perfil desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Network%2Ftrafficmanagerprofiles]" submitText="Go to Traffic Manager profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-content-delivery-network"></a>Rede de Distribuição de Conteúdo do Azure

O Azure oferece uma CDN (Rede de Distribuição de Conteúdo) que permite que você garanta a entrega oportuna de ativos, colocando-os em cache próximo aos usuários. Esse cache ajuda a melhorar as experiências dos clientes. Durante o download do conteúdo, ele também impede dificuldades causadas por problemas de rede que ocorrem entre o ponto de extremidade da CDN e o datacenter que hospeda o aplicativo. A Rede de Distribuição de Conteúdo também pode ser usada por aplicativos que não são hospedados no Azure.

### <a name="action"></a>Ação

Para configurar ou monitorar perfis de Rede de Distribuição de Conteúdo:

1. Acesse **Perfis de CDN**.
2. Configurar um novo perfil: Selecione **Adicionar** e siga os avisos.
3. Gerencie os perfis existentes: Selecione o perfil desejado na lista.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.cdn%2Fprofiles]" submitText="Go to CDN profiles" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="learn-more"></a>Saiba mais

- [Azure Front Door](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
- [Gerenciador de Tráfego](https://docs.microsoft.com/azure/traffic-manager)
- [Rede de Distribuição de Conteúdo](https://docs.microsoft.com/azure/cdn)
