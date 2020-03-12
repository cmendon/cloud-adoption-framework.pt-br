---
title: Criar consistência de nuvem híbrida
description: Use a estrutura de adoção de nuvem para o Azure para saber como definir a abordagem para criar a consistência de nuvem híbrida.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7b2433b787683cf8ecaaf4a1f7a858aa18bf682c
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093036"
---
# <a name="create-hybrid-cloud-consistency"></a>Criar consistência de nuvem híbrida

Este artigo orienta você pelas abordagens de alto nível para a criação de consistência de nuvem híbrida.

Os modelos de implantação híbrida durante a migração podem reduzir o risco e contribuir para uma transição da infraestrutura sem problemas. Em relação aos processos de negócios, as plataformas de nuvem oferecem o maior nível de flexibilidade. Muitas organizações são hesitars para fazer a mudança para a nuvem. Em vez disso, eles preferem manter o controle total sobre seus dados mais confidenciais. Infelizmente, os servidores locais não permitem a mesma taxa de inovação que a nuvem. Uma solução de nuvem híbrida oferece a velocidade de inovação na nuvem e o controle do gerenciamento local.

## <a name="integrate-hybrid-cloud-consistency"></a>Integrar a consistência da nuvem híbrida

O uso de uma solução de nuvem híbrida permite que as organizações dimensionem os recursos de computação. Isso também elimina a necessidade de fazer grandes investimentos de capital para lidar com picos de demanda de curto prazo. As alterações na sua empresa podem impulsionar a necessidade de liberar recursos locais para dados ou aplicativos mais confidenciais. É mais fácil, rápido e mais barato desprovisionar recursos de nuvem. Você paga apenas pelos recursos que sua organização usa temporariamente em vez de precisar comprar e fazer a manutenção de recursos adicionais. Essa abordagem reduz a quantidade de equipamentos que podem permanecer ociosos por longos períodos de tempo. A computação em nuvem híbrida oferece todos os benefícios da flexibilidade de computação em nuvem, escalabilidade e eficiências de custo com o menor risco possível de exposição de dados.

![a criação de consistência de nuvem híbrida entre identidade, gerenciamento, segurança, dados, desenvolvimento e DevOps](../../_images/hybrid-consistency.png)
*Figura 1-criando consistência de nuvem híbrida entre identidade, gerenciamento, segurança, dados, desenvolvimento e DevOps.*

Uma verdadeira solução de nuvem híbrida deve fornecer quatro componentes, cada um dos quais traz benefícios significativos:

- **Identidade comum para aplicativos locais e na nuvem:** Esse componente melhora a produtividade do usuário, fornecendo aos usuários o SSO (logon único) para todos os seus aplicativos. Ele também garante a consistência, pois os aplicativos e os usuários cruzam os limites de rede ou de nuvem.
- **Gerenciamento e segurança integrados em sua nuvem híbrida:** Esse componente fornece uma maneira coesa de monitorar, gerenciar e proteger o ambiente, o que permite aumentar a visibilidade e o controle.
- **Uma plataforma de dados consistente para o datacenter e a nuvem:** Esse componente cria portabilidade de dados, combinada com acesso contínuo a serviços de dados locais e na nuvem para obter informações aprofundadas sobre todas as fontes de dados.
- **Desenvolvimento unificado e DevOps em data centers locais e na nuvem:** Esse componente permite que você mova aplicativos entre os dois ambientes, conforme necessário. A produtividade do desenvolvedor melhora porque os dois locais agora têm o mesmo ambiente de desenvolvimento.

Aqui estão alguns exemplos desses componentes de uma perspectiva do Azure:

- O Azure Active Directory (AD do Azure) funciona com o Active Directory local para fornecer identidade comum para todos os usuários. O SSO entre o local e por meio da nuvem facilita o acesso seguro dos usuários aos aplicativos e ativos de que precisam. Os administradores podem gerenciar a segurança e os controles de governança e também ter a flexibilidade de ajustar as permissões sem afetar a experiência do usuário.
- O Azure fornece serviços integrados de gerenciamento e segurança para a infraestrutura local e na nuvem. Esses serviços incluem um conjunto integrado de ferramentas que são usadas para monitorar, configurar e proteger nuvens híbridas. Essa abordagem de ponta a ponta do gerenciamento resolve especificamente desafios reais que enfrentam organizações que consideram uma solução de nuvem híbrida.
- Uma nuvem híbrida do Azure fornece ferramentas comuns que garantem acesso seguro a todos os dados, de modo perfeito e eficiente. Os serviços de dados do Azure se unem ao Microsoft SQL Server para criar uma plataforma de dados consistente. Um modelo de nuvem híbrida consistente permite que os usuários trabalhem com dados analíticos e operacionais. Os mesmos serviços são fornecidos localmente e na nuvem para data warehousing, análise de dados e visualização de dados.
- Os serviços de nuvem do Azure, combinados com Azure Stack local, fornecem desenvolvimento unificado e DevOps. A consistência na nuvem e no local significa que sua equipe do DevOps pode criar aplicativos que são executados em qualquer ambiente e podem facilmente implantar no local certo. Você também pode reutilizar modelos em toda a solução híbrida, o que pode simplificar ainda mais os processos DevOps.

## <a name="azure-stack-in-a-hybrid-cloud-environment"></a>Azure Stack em um ambiente de nuvem híbrida

Azure Stack é uma solução de nuvem híbrida que permite que as organizações executem serviços consistentes no Azure em seu datacenter. Ele fornece uma experiência simplificada de desenvolvimento, gerenciamento e segurança que é consistente com os serviços de nuvem pública do Azure. Azure Stack é uma extensão do Azure. Você pode usá-lo para executar os serviços do Azure de seus ambientes locais e, em seguida, mover para a nuvem do Azure se e quando necessário.

Com o Azure Stack, você pode implantar e operar o IaaS e o PaaS usando as mesmas ferramentas e oferecendo a mesma experiência que a nuvem pública do Azure. O gerenciamento do Azure Stack, seja por meio do portal de interface do usuário da Web ou por meio do PowerShell, tem uma aparência consistente para os administradores de TI e usuários finais do Azure.

O Azure e Azure Stack abrem novos casos de uso híbrido para aplicativos de linha de negócios internos e voltados para o cliente:

- **Soluções de borda e desconectadas.** Para atender aos requisitos de latência e conectividade, os clientes podem processar dados localmente em Azure Stack e, em seguida, agregar-os no Azure para análise adicional. Eles podem usar a lógica de aplicativo comum em ambos. Muitos clientes estão interessados nesse cenário de borda em diferentes contextos, como plantas de fábrica, lançamentos de cruzeiro e meus eixos.
- **Aplicativos de nuvem que atendem a várias regulamentações.** Os clientes podem desenvolver e implantar aplicativos no Azure, com total flexibilidade para implantar localmente em Azure Stack para atender aos requisitos regulatórios ou de política. Nenhuma alteração de código é necessária. Os exemplos de aplicativos incluem auditoria global, relatórios financeiros, comércio de trocas estrangeiras, Jogos Online e relatórios de despesas. Às vezes, os clientes procuram implantar diferentes instâncias do mesmo aplicativo no Azure ou Azure Stack, com base nos requisitos técnicos e de negócios. Embora o Azure cumpra a maioria dos requisitos, o Azure Stack complementa a abordagem de implantação quando necessário.
- **Modelo de aplicativo de nuvem local.** Os clientes podem usar os serviços Web, os contêineres e as arquiteturas sem servidor e de microsserviço do Azure para atualizar e estender aplicativos existentes ou criar novos. É possível usar processos consistentes de DevOps entre o Azure na nuvem e o Azure Stack local. Há um interesse crescente na modernização do aplicativo, mesmo para aplicativos essenciais fundamentais.

O Azure Stack é oferecido com duas opções de implantação:

- **Azure Stack sistemas integrados:** Azure Stack sistemas integrados são oferecidos pela Microsoft e por parceiros de hardware para criar uma solução que fornece inovação com o ritmo da nuvem balanceada com gerenciamento simples. Como o Azure Stack é oferecido como um sistema integrado de hardware e software, você obtém flexibilidade e controle ao mesmo tempo que ainda está adotando a inovação da nuvem. Azure Stack intervalo de sistemas integrados de tamanho de 4 a 12 nós. Eles têm suporte em conjunto pelo parceiro de hardware e pela Microsoft. Use sistemas integrados do Azure Stack para habilitar novos cenários para suas cargas de trabalho de produção.
- **Kit de desenvolvimento do Azure Stack:** O kit de desenvolvimento de Microsoft Azure Stack é uma implantação de nó único do Azure Stack. Você pode usá-lo para avaliar e saber mais sobre Azure Stack. Você também pode usar o kit como um ambiente de desenvolvedor, no qual você pode desenvolver usando APIs e ferramentas que são consistentes com o Azure. O Kit de Desenvolvimento do Azure Stack não se destina ao uso como um ambiente de produção.

## <a name="azure-stack-one-cloud-ecosystem"></a>Azure Stack ecossistema de uma nuvem

Você pode acelerar Azure Stack iniciativas usando o ecossistema completo do Azure:

- O Azure garante que a maioria dos aplicativos e serviços certificados para o Azure funcionará em Azure Stack. Vários ISVs estão estendendo suas soluções para Azure Stack. Esses ISVs incluem BitNami, Docker, Kemp Technologies, Pivotal Cloud Foundry, Red Hat Enterprise Linux e SUSE Linux.
- Você pode optar por ter o Azure Stack entregue e operado como um serviço totalmente gerenciado. Vários parceiros terão ofertas de serviço gerenciadas no Azure e Azure Stack em breve. Esses parceiros incluem Tieto, Yourhosting, revera, Pulsant e NTT. Esses parceiros fornecem serviços gerenciados para o Azure por meio do programa CSP (provedor de soluções na nuvem). Eles estão estendendo suas ofertas para incluir soluções híbridas.
- Como exemplo de uma solução de nuvem híbrida completa e totalmente gerenciada, a Avanade oferece uma oferta tudo em um. Ele inclui serviços de transformação de nuvem, software, infraestrutura, instalação e configuração e serviços gerenciados em andamento. Dessa forma, os clientes podem consumir Azure Stack da mesma forma que no Azure hoje.
- Os provedores podem ajudar a acelerar as iniciativas de modernização de aplicativos criando soluções de ponta a ponta do Azure para os clientes. Eles trazem conjuntos de habilidades do Azure aprofundados, conhecimento do setor e de domínio e experiência de processo, como DevOps. Cada Azure Stack nuvem é uma oportunidade para que um provedor projete a solução e conduza e influencie a implantação do sistema. Eles também podem personalizar os recursos incluídos e fornecer atividades operacionais. Exemplos de provedores incluem Avanade, DXC, Dell EMC Services, Infront Consulting Group, HPE Pointnext e PwC (anteriormente conhecido como PricewaterhouseCoopers).
