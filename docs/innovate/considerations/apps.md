---
title: 'Inovação na nuvem: envolver aplicativos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação na nuvem-participe de aplicativos
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 3db2349e3c1da7c80f3089ea187a3de72d006d1f
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683310"
---
# <a name="engage-through-applications"></a>Envolver aplicativos

Conforme discutido no artigo sobre [dados do democratizando](./data.md), os dados são o novo óleo. Ele incentiva a maioria das inovações na economia digital. Com base nessa analogia, os aplicativos são a estação de combustível e a infraestrutura necessária para que o combustível seja colocado nas mãos certas.

Em alguns casos, os dados são suficientes para impulsionar as alterações e atender às necessidades dos clientes. Mais comumente, a solução para as necessidades do cliente exigirá que os aplicativos modelem os dados e criem uma experiência. Os aplicativos são a maneira como podemos envolver o usuário. Eles são a base dos processos necessários para responder aos disparadores do cliente. Eles são os clientes que fornecem orientações de dados e de recebimento. Este artigo descreverá alguns princípios que ajudarão a alinhar a solução de aplicativo correta, com base nas mesmas que serão validadas.

![Envolva-se por meio de aplicativos](../../_images/innovate/engage-via-apps.png)

## <a name="shared-code"></a>Código compartilhado

As equipes que podem responder de forma mais rápida e precisa aos comentários dos clientes, às mudanças no mercado e às oportunidades de inovar, levarão seus respectivos mercados na inovação. O primeiro princípio dos aplicativos inovadores é descrito na [visão geral da mentalidade de crescimento](./learn.md#growth-mindset), "compartilhar o código". A inovação ao longo do tempo só pode vir de um foco cultural. Para sustentar a inovação, diversas perspectivas e contribuições serão necessárias.

Para estar pronto para a inovação, todo o desenvolvimento de aplicativos deve começar com um repositório de código compartilhado. A ferramenta mais comum para gerenciar repositórios de código é o [GitHub](https://guides.github.com/), que permite a criação de um repositório de código compartilhado com alguns cliques. Como alternativa, o recurso [Azure Repos](/azure/devops/repos/get-started/what-is-repos?view=azure-devops) do Azure DevOps pode ser usado para criar um repositório do [git](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) ou do [Team Foundation](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="citizen-developers"></a>Desenvolvedores do cidadão

Os desenvolvedores profissionais são um componente vital da inovação. Quando uma hipótese comprova precisamente em escala, os desenvolvedores profissionais precisam estabilizar e preparar a solução para escala. A maioria dos princípios mencionados neste artigo exigirá suporte de desenvolvedores profissionais. Infelizmente, as tendências atuais sugerem que há mais aberturas para desenvolvedores profissionais e, em seguida, há desenvolvedores. Além disso, o custo e o ritmo da inovação podem ser menos favoráveis quando os rigores do desenvolvimento profissional são necessários. Os desenvolvedores do cidadão fornecem uma maneira de dimensionar os esforços de desenvolvimento e acelerar o teste de hipótese inicial.

Os desenvolvedores do cidadão podem ser uma abordagem inteligente quando as primeiras expressões podem ser validadas usando ferramentas como o [PowerApps](https://docs.microsoft.com/powerapps/powerapps-overview) para interfaces de aplicativo, o [Construtor de ia](/powerapps/use-ai-builder) para processos e previsões, [Microsoft Flow](https://docs.microsoft.com/flow) para fluxos de trabalho ou [Power bi](https://docs.microsoft.com/power-bi) para dados utilização.

> [!NOTE]
> Ao aproveitar os desenvolvedores do cidadão para testar as mesmas, é recomendável que os desenvolvedores profissionais forneçam suporte, revisão e orientação. Depois que uma hipótese é validada em escala, um processo de transição do aplicativo para um modelo de programação mais robusto acelerará os retornos na inovação. Envolver desenvolvedores profissionais nas definições do processo inicial pode resultar em transições mais claras posteriormente.

## <a name="intelligent-experiences"></a>Experiências inteligentes

As experiências inteligentes combinam a velocidade e a escala de aplicativos Web modernos, com a inteligência de serviços e bots cognitivas. Sozinho, cada um pode ser suficiente para atender às necessidades dos seus clientes. A combinação do espectro de necessidades que pode ser atendida por meio de uma experiência digital é expandida, mas os investimentos em desenvolvimento ainda podem estar contidos.

### <a name="modern-web-apps"></a>Aplicativos Web modernos

Quando um aplicativo ou uma experiência é necessária para atender a uma necessidade do cliente, os aplicativos Web modernos podem ser a maneira mais rápida de atender a essa necessidade. Experiências da Web modernas podem envolver clientes internos ou externos rapidamente e permitir a iteração rápida na solução.

### <a name="infusing-intelligence"></a>Infusíveis de inteligência

O aprendizado de máquina e a inteligência artificial estão se tornando cada vez mais disponíveis para os desenvolvedores. A disponibilidade de larga propagação de APIs comuns com recursos de previsão, permite que os desenvolvedores atendam melhor às necessidades do cliente por meio do acesso expandido a dados e previsões.

A adição de inteligência a uma solução pode permitir a fala de texto, tradução de texto, visão computacional e até mesmo pesquisa visual. Com esses recursos expandidos, é mais fácil para os desenvolvedores criar soluções que aproveitam a inteligência para criar uma experiência interativa e moderna.

### <a name="bots"></a>Bots

Os bots fornecem uma experiência que parece menos com o uso de um computador e mais como lidar com uma pessoa ou pelo menos um robô inteligente. Eles podem ser usados para deslocar tarefas simples e repetitivas, como fazer uma reserva de jantar ou coletar informações de perfil, em sistemas automatizados que podem não exigir mais intervenção humana direta. Os usuários conversom com um bot usando texto, cartões interativos e fala. Uma interação de bot pode ser uma pergunta e resposta rápidas, ou pode ser uma conversa sofisticada que fornece acesso inteligente aos serviços.

Os bots são muito parecidos com aplicativos Web modernos, vivendo na Internet e usam APIs para enviar e receber mensagens. O que está em um bot varia muito dependendo do tipo de bot. O software de bot moderno conta com uma pilha de tecnologias e ferramentas para fornecer experiências cada vez mais complexas em uma ampla variedade de plataformas. No entanto, um bot simples poderia simplesmente receber uma mensagem e recebê-la para o usuário com muito pouco código envolvido.

Os bots podem fazer as mesmas coisas que outros tipos de software podem ler e gravar arquivos, usar bancos de dados e APIs e fazer as tarefas computacionais regulares. O que torna os bots exclusivos o uso dos mecanismos geralmente reservados para comunicação humana a humana.

## <a name="cloud-native-solutions"></a>Soluções nativas de nuvem

Os aplicativos nativos de nuvem são criados desde o início. Os aplicativos nativos de nuvem são otimizados para escala e desempenho na nuvem. Normalmente, os aplicativos nativos de nuvem são criados com o uso de microserviços, sem servidor, baseados em eventos ou abordagens baseadas em contêineres. Normalmente, as soluções nativas de nuvem aproveitam uma combinação de arquiteturas de microserviços, serviços gerenciados e entrega contínua para atingir a confiabilidade e o tempo de colocação no mercado mais rápido.

Uma solução nativa de nuvem permite que as equipes de desenvolvimento centralizado mantenham o controle da lógica de negócios, sem a necessidade de Soluções centralizadas monolíticas. Esse tipo de solução também cria uma âncora para impulsionar a consistência entre os desenvolvedores do cidadão e as experiências modernas. Por fim, as soluções nativas de nuvem fornecem um acelerador de inovação ao liberar desenvolvedores de cidadãos e profissionais para inovar com segurança e com bloqueios mínimos.

## <a name="innovate-through-existing-solutions"></a>Inovar por meio de soluções existentes

Muitas hipóteses de clientes podem ser mais bem entregues por uma versão modernizada de uma solução existente. Quando a lógica de negócios atual atende às necessidades do cliente (ou vem realmente perto), você pode acelerar a inovação com a criação de uma solução modernizada.

A maioria das formas de modernização, incluindo uma pequena refatoração do aplicativo, está incluída na [metodologia de migração](../../migrate/index.md) dentro da estrutura de adoção de nuvem. Essa metodologia orienta as equipes de adoção de nuvem por meio dos processos para migrar um [espaço digital](../../digital-estate/index.md) para a nuvem. O [Guia de migração do Azure](../../migrate/azure-migration-guide/index.md) fornece uma abordagem simplificada para a mesma metodologia, que é adequada para um pequeno número de cargas de trabalho ou até mesmo um único aplicativo.

Depois de migrados e modernizados, há várias maneiras pelas quais a solução pode ser aproveitada na criação de novas soluções inovadoras às necessidades dos clientes. Por exemplo, [os desenvolvedores do cidadão](#citizen-developers) poderiam testar as mesmas ou os desenvolvedores profissionais poderiam criar [experiências inteligentes](#intelligent-experiences) ou [soluções nativas de nuvem](#cloud-native-solutions).

### <a name="extend-an-existing-solution"></a>Estender uma solução existente

Estender uma solução é uma forma comum de modernização. Essa abordagem pode ser o caminho mais rápido para a inovação quando as seguintes são verdadeiras da hipótese do cliente:

- A lógica de negócios existente deve atender (ou chegar perto de cumprir) a necessidade do cliente existente.
- Uma experiência aprimorada atende melhor às necessidades de um cliente específico coorte.
- A lógica de negócios exigida pela solução MVP foi centralizada, geralmente por meio de um design de [N camadas](/azure/architecture/guide/architecture-styles/n-tier), serviços Web, API ou [microservices](/azure/architecture/guide/architecture-styles/microservices) . Essa abordagem consiste em encapsular a solução existente com uma nova experiência hospedada na nuvem. No Azure, essa solução provavelmente residiria em serviços Azure Apps.

### <a name="rebuild-an-existing-solution"></a>Recompilar uma solução existente

Se um aplicativo não puder ser estendido facilmente, pode ser necessário refatorar a solução. Nessa abordagem, a carga de trabalho é migrada para a nuvem. Depois de migrados, partes do aplicativo são modificadas ou duplicadas, como serviços Web ou [microservices](/azure/architecture/guide/architecture-styles/microservices), que são implantados em paralelo à solução existente. A solução baseada em serviço paralela poderia ser tratada como uma solução estendida. Essa solução simplesmente encapsularia a solução existente com uma nova experiência hospedada na nuvem. No Azure, essa solução provavelmente residiria em serviços Azure Apps.

> [!CAUTION]
> Refatorar ou rearquitetar soluções ou centralizar a lógica de negócios pode rapidamente se tornar um [pico técnico](./build.md#reduce-complexity-and-delay-technical-spikes)demorado, em oposição a uma fonte de valor de cliente. Trata-se de um risco de inovação, especialmente na validação da hipótese. Com um pouco de criatividade no design de uma solução, deve haver um caminho para o MVP que não exige refatoração de soluções existentes. É prudente atrasar a refatoração, até que a hipótese inicial possa ser validada em escala.

## <a name="operating-model-innovations"></a>Inovações do modelo operacional

Além das abordagens de inovação modernas para a criação de aplicativos, houve inovações em relação às operações dos aplicativos. As abordagens geraram muitos movimentos organizacionais. Uma das mais importantes é um movimento para os modelos operacionais [Cloud Center of Excellence](../../organize/cloud-center-of-excellence.md) . Quando totalmente equipes e amadurecedas, as equipes de negócios têm a opção de fornecer seu próprio suporte operacional para uma solução.

O tipo de modelo de gerenciamento operacional de autoatendimento, encontrado em um Cloud Center de excelência, permite controles mais rígidos e iterações mais rápidas dentro do ambiente da solução. Isso é feito transferindo o controle operacional e a responsabilidade para a equipe de negócios.

Quando o objetivo é dimensionar ou atender à demanda global de uma solução existente, essa abordagem pode ser suficiente para validar uma hipótese do cliente. Uma vez migrado e ligeiramente modernizado, a equipe de negócios teria a capacidade de dimensionar soluções para testar uma variedade de pessoas em relação aos clientes coortes que estão preocupados com desempenho, distribuição global ou outras necessidades do cliente impedidas por ele das.

## <a name="reduce-overhead-and-management"></a>Reduzir a sobrecarga e o gerenciamento

Quanto mais houver a manutenção dentro de uma solução, mais lenta será a solução. Acelere a inovação reduzindo o impacto que as operações têm sobre a velocidade disponível.

Para se preparar para as muitas iterações necessárias para fornecer uma solução inovadora, é importante imaginar em frente. Minimize as cargas operacionais no início do processo, favorecendo as opções sem servidor.

No Azure, as opções de aplicativo sem servidor podem incluir [Azure app serviço](https://docs.microsoft.com/azure/app-service/overview) ou [contêineres](https://docs.microsoft.com/azure/architecture/cloud-adoption/migrate/azure-best-practices/contoso-migration-rearchitect-container-sql).

Em paralelo, o Azure fornece opções de dados de transação sem servidor que também reduzem a sobrecarga. A [lista de produtos de banco](https://docs.microsoft.com/azure/#pivot=products&panel=databases) de dados fornece opções de Hospedagem de dado, sem a necessidade de uma plataforma de dados completa.

## <a name="next-steps"></a>Próximos passos

Dependendo da hipótese e da solução, os princípios neste artigo podem ajudar a criar aplicativos que atendam às definições de MVP e contrate usuários. Em seguida, veja os princípios de [capacitação da adoção](./ci-cd.md), que discutirá maneiras de obter rapidamente o aplicativo e os dados em mãos de clientes com mais rapidez.

> [!div class="nextstepaction"]
> [Capacitar a adoção](./ci-cd.md)
