---
title: Visão geral dos exemplos de migração de aplicativos para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fornece uma visão geral dos exemplos de migração de aplicativos incluídos como parte da seção Migração do Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a6af51f1fa6526e2ea7cf13a824c7834d631aa59
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70820577"
---
# <a name="application-migration-patterns-and-examples"></a>Exemplos e padrões de migração de aplicativos

Esta seção do Cloud Adoption Framework fornece exemplos de vários cenários de migração comuns, demonstrando como você pode migrar a infraestrutura local para a nuvem do [Microsoft Azure](https://azure.microsoft.com/overview/what-is-azure).

## <a name="introduction"></a>Introdução

O Azure fornece acesso a um conjunto abrangente de serviços de nuvem. Como desenvolvedor e profissional de TI, você pode usar esses serviços para criar, implantar e gerenciar aplicativos em uma variedade de ferramentas e estruturas, por meio de uma rede global de datacenters. Conforme a sua empresa vai enfrentando desafios associados à mudança digital, a nuvem do Azure o ajuda a descobrir como otimizar recursos e operações, envolver-se com seus clientes e funcionários e transformar seus produtos.

No entanto, o Azure reconhece que mesmo com todas as vantagens que a nuvem oferece em termos de velocidade e flexibilidade, redução de custos, desempenho e confiabilidade, muitas organizações ainda precisarão executar datacenters locais por algum tempo. Em resposta aos obstáculos para a adoção da nuvem, o Azure oferece uma estratégia de nuvem híbrida que cria pontes entre seus datacenters locais e a nuvem pública do Azure. Por exemplo, usar recursos de nuvem do Azure, como o Backup do Azure, para proteger recursos locais ou usar a análise do Azure para obter insights sobre cargas de trabalho locais.

Como parte da estratégia de nuvem híbrida, o Azure fornece soluções de crescimento para migrar aplicativos locais e cargas de trabalho para a nuvem. Com etapas simples, você pode avaliar seus recursos locais de forma abrangente para descobrir como eles serão executados na nuvem do Azure. Com uma avaliação detalhada, você pode migrar seus recursos para o Azure com tranquilidade. Quando os recursos estão em execução no Azure, você pode otimizá-los para manter e melhorar o acesso, a flexibilidade, a segurança e a confiabilidade.

## <a name="migration-patterns"></a>Padrões de migração

As estratégias para a migração para a nuvem se enquadram em quatro padrões amplos: hospedar novamente, refatorar, refazer arquitetura ou recompilar. A estratégia adotada depende de suas motivações de negócios e das metas de migração. Você pode adotar vários padrões. Por exemplo, pode optar por hospedar novamente aplicativos simples ou aplicativos que não são essenciais para seu negócio, mas refazer a arquitetura daqueles que são mais complexos e comercialmente críticos. Vamos examinar esses padrões.

<!-- markdownlint-disable MD033 -->

**Padrão** | **Definição** | **Quando usar**
--- | --- | ---
**Hospedar novamente** | Conhecida como uma migração "lift and shift". Essa opção não exige alterações de código e permite migrar seus aplicativos existentes para o Azure rapidamente. Cada aplicativo é migrado como está, para aproveitar os benefícios da nuvem, sem o risco e o custo associado com as alterações de código. | Quando você precisar mover aplicativos rapidamente para a nuvem.<br/><br/> Quando você deseja mover um aplicativo sem modificá-lo.<br/><br/> Quando os aplicativos são projetados para que possam se beneficiar da escalabilidade do [IaaS do Azure](https://azure.microsoft.com/overview/what-is-iaas) após a migração.<br/><br/> Quando aplicativos são importantes para a sua empresa, mas você não precisa de alterações imediatas nos recursos de aplicativo.
**Refatorar** | Conhecida como "reempacotamento", a refatoração requer alterações mínimas nos aplicativos, para que eles possam se conectar ao [PaaS do Azure](https://azure.microsoft.com/overview/what-is-paas) e usar as ofertas de nuvem.<br/><br/> Por exemplo, você pode migrar seus aplicativos existentes para o Serviço de Aplicativo do Azure ou o AKS (Serviço Kubernetes do Azure).<br/><br/> Ou você pode refatorar seus bancos de dados relacionais e não relacionais em opções como a Instância Gerenciada do Banco de Dados SQL do Azure, o Banco de Dados do Azure para MySQL, o Banco de Dados do Azure para PostgreSQL e o Azure Cosmos DB. | Se seu aplicativo pode facilmente ser empacotado novamente para funcionar no Azure.<br/><br/> Se você deseja aplicar práticas DevOps inovadoras fornecidas pelo Azure, ou se estiver pensando em DevOps usando uma estratégia de contêiner para cargas de trabalho.<br/><br/> Para a refatoração, você precisa pensar sobre a portabilidade de sua base de código existente e as habilidades de desenvolvimento disponíveis.
**Recriação de arquitetura** | A nova arquitetura para migração se concentra em modificar e estender a funcionalidade do aplicativo e o código base para otimizar a arquitetura do aplicativo de escalabilidade de nuvem.<br/><br/> Por exemplo, você pode decompor um aplicativo monolítico em um grupo de microsserviços que trabalham em conjunto e que são dimensionados com facilidade.<br/><br/> Ou você pode recriar a arquitetura dos bancos de dados relacionais e não relacionais para uma solução de banco de dados totalmente gerenciada, como Instância Gerenciada do Banco de Dados SQL do Azure, Banco de Dados do Azure para MySQL, Banco de Dados do Azure para PostgreSQL e Azure Cosmos DB. | Quando seus aplicativos precisam de revisões principais para incorporar os novos recursos ou trabalhar com eficiência em uma plataforma de nuvem.<br/><br/> Quando você quiser usar investimentos em aplicativos existentes, atenda aos requisitos de escalabilidade, aplique práticas inovadoras de DevOps do Azure e minimize o uso de máquinas virtuais.
**Recompilar** | A recompilação leva tudo a um novo patamar por meio da recompilação de um aplicativo do zero usando tecnologias de nuvem do Azure.<br/><br/> Por exemplo, é possível compilar aplicativos completamente novos com tecnologias [nativas da nuvem](https://azure.com/cloudnative), como Azure Functions, IA do Azure, Instância Gerenciada do Banco de Dados SQL do Azure e Azure Cosmos DB. | Quando você quiser um desenvolvimento rápido e os aplicativos existentes têm funcionalidade e vida útil limitadas.<br/><br/> Quando estiver pronto para acelerar a inovação nos negócios (incluindo práticas de DevOps fornecidas pelo Azure), compile novos aplicativos usando tecnologias nativas da nuvem e aproveite os avanços em IA, Blockchain e IoT.

<!-- markdownlint-enable MD033 -->

## <a name="migration-example-articles"></a>Artigos de exemplo de migração

Os artigos desta seção fornecem exemplos de vários cenários de migração comuns. Cada um dos exemplos inclui informações contextuais e cenários de implantação detalhados que ilustram como configurar uma infraestrutura de migração e avaliar a adequação dos recursos locais para migração. Mais artigos serão adicionados a esta seção ao longo do tempo.

![Projetos comuns de migração/modernização](./media/migration-patterns.png)

*Categorias comuns de projeto de migração e modernização.*

Os artigos da série são resumidos abaixo.

- Cada cenário de migração é orientado por metas de negócios ligeiramente diferentes que determinam a estratégia de migração.
- Para cada cenário de implantação, fornecemos informações sobre fatores e metas comerciais, uma arquitetura proposta, etapas para executar a migração e a recomendação para limpeza e próximas etapas após a conclusão da migração.

### <a name="assessment"></a>Avaliação

**Artigo** | **Detalhes**
--- | ---
[Avaliar recursos locais para migração para o Azure](contoso-migration-assessment.md) | Este artigo mostra como executar uma avaliação de um aplicativo local em execução no VMware. Neste exemplo, uma organização avalia as VMs do aplicativo usando o serviço de Migrações para Azure e o banco de dados do SQL Server do aplicativo usando o Assistente de Migração de Dados.

### <a name="infrastructure"></a>Infraestrutura

**Artigo** | **Detalhes**
--- | ---
[Implantar a infraestrutura do Azure](contoso-migration-infrastructure.md) | Este artigo mostra como uma organização pode preparar sua infraestrutura local e do Azure para migração. O exemplo de infraestrutura estabelecido neste artigo é referenciado nos outros exemplos fornecidos nesta seção.

### <a name="windows-server-workloads"></a>Cargas de trabalho do Windows Server

**Artigo** | **Detalhes**
--- | ---
[Hospedar novamente um aplicativo em VMs do Azure](contoso-migration-rehost-vm.md) | Este artigo fornece um exemplo de migração de VMs de aplicativo local para VMs do Azure usando o serviço Site Recovery.
[Recriar a arquitetura de um aplicativo em contêineres do Azure e no Banco de Dados SQL do Azure](contoso-migration-rearchitect-container-sql.md) | Este artigo fornece um exemplo de migração de um aplicativo ao recriar a arquitetura da camada do aplicativo Web como um contêiner do Windows em execução no Azure Service Fabric e o banco de dados com o Banco de Dados SQL do Azure.

### <a name="linux-workloads"></a>Cargas de trabalho do Linux

**Artigo** | **Detalhes**
--- | ---
[Hospedar novamente um aplicativo do Linux em VMs do Azure e no Banco de Dados do Azure para MySQL](contoso-migration-rehost-linux-vm-mysql.md) | Este artigo fornece um exemplo de migração de um aplicativo hospedado em Linux para VMs do Azure usando o Site Recovery. Ele migra o banco de dados do aplicativo para Banco de Dados do Azure para MySQL, usando MySQL Workbench.
[Hospedar novamente um aplicativo do Linux em VMs do Azure](contoso-migration-rehost-linux-vm.md) | Este exemplo mostra como concluir uma migração "lift and shift" de um aplicativo baseado em Linux para VMs do Azure, usando o serviço do Site Recovery.

### <a name="sql-server-workloads"></a>Cargas de trabalho do SQL Server

**Artigo** | **Detalhes**
--- | ---
[Hospedar novamente um aplicativo em uma VM do Azure e uma Instância Gerenciada do Banco de Dados SQL](contoso-migration-rehost-vm-sql-managed-instance.md) | Este artigo fornece um exemplo de migração "lift and shift" de um aplicativo local para o Azure. Isso envolve migrar a VM front-end do aplicativo usando o [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) e o banco de dados do aplicativo para uma Instância Gerenciada do Banco de Dados SQL do Azure, usando o [Serviço de Migração de Banco de Dados do Azure](/azure/dms/dms-overview).
[Hospedar novamente um aplicativo em VMs do Azure e em um grupo de disponibilidade Always On do SQL Server](contoso-migration-rehost-vm-sql-ag.md) | Este exemplo mostra como migrar um aplicativo e dados usando as VMs do SQL Server hospedadas no Azure. Ele usa o Site Recovery para migrar as VMs do aplicativo e o Serviço de Migração de Banco de Dados do Azure para migrar o banco de dados do aplicativo para um cluster do SQL Server protegido por um grupo de disponibilidade Always On.

### <a name="aspnet--php--java-apps"></a>Aplicativos ASP.NET/PHP/Java

**Artigo** | **Detalhes**
--- | ---
[Refatorar um aplicativo em um aplicativo Web do Azure e no Banco de Dados SQL do Azure](contoso-migration-refactor-web-app-sql.md) | Este exemplo mostra como migrar um aplicativo baseado no Windows local para um aplicativo Web do Azure e migra o banco de dados do aplicativo para uma instância de SQL Server do Azure com o Assistente de Migração de Dados.
[Refatorar um aplicativo do Linux para várias regiões usando o Serviço de Aplicativo do Azure, o Gerenciador de Tráfego do Azure e o Banco de Dados do Azure para MySQL](contoso-migration-refactor-linux-app-service-mysql.md) | Este exemplo mostra como migrar um aplicativo baseado no Linux local para um aplicativo Web do Azure em várias regiões do Azure usando o Gerenciador de Tráfego do Azure integrado ao GitHub para entrega contínua. O banco de dados do aplicativo é migrado para uma instância do Banco de Dados do Azure para MySQL.
[Recompilar um aplicativo no Azure](contoso-migration-rebuild.md) | Este artigo fornece um exemplo de recompilação de um aplicativo local usando uma variedade de serviços gerenciados e recursos do Azure, incluindo o Serviço de Aplicativo do Azure, AKS (Serviço de Kubernetes do Azure), Azure Functions,Serviços Cognitivos do Azure e Azure Cosmos DB.
[Refatorar o Team Foundation Server no Azure DevOps Services](contoso-migration-tfs-vsts.md) | Este artigo mostra um exemplo de migração de uma implantação do Team Foundation Server local para o Azure DevOps Services no Azure.

### <a name="migration-scaling"></a>Dimensionamento de migração

**Artigo** | **Detalhes**
--- | ---
[Dimensionar uma migração para o Azure](contoso-migration-scale.md) | Este artigo exemplifica como uma organização se prepara para dimensionar uma migração completa para o Azure.

### <a name="demo-apps"></a>Aplicativos de demonstração

Os artigos de exemplo fornecidos nesta seção usam dois aplicativos de demonstração: SmartHotel360 e osTicket.

- **SmartHotel360:** Esse aplicativo foi desenvolvido pela Microsoft como um aplicativo de teste que você pode usar ao trabalhar com o Azure. Ele é fornecido como o código-fonte aberto e você pode baixá-lo do [GitHub](https://github.com/Microsoft/SmartHotel360). É um aplicativo ASP.NET conectado a um banco de dados do SQL Server. Nos cenários discutidos nestes artigos, a versão atual desse aplicativo é implantada em duas VMs VMware que executam o Windows Server 2008 R2 e o SQL Server 2008 R2. Essas VMs do aplicativo estão hospedadas no local e gerenciadas pelo vCenter Server.
- **osTicket:** Um aplicativo de software livre de geração de tíquetes da central de serviços executado no Linux. Você pode baixá-lo do [GitHub](https://github.com/osTicket/osTicket). Nos cenários discutidos nestes artigos, a versão atual desse aplicativo é implantada localmente em duas VMs VMware que executam o Ubuntu 16.04 LTS, usando Apache 2, PHP 7.0 e MySQL 5.7
