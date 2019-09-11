---
title: Melhores práticas da Preparação para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução às melhores práticas de Preparação para o Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: f1d4423e230d2eeff524a864f163e0cb13dc065b
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818260"
---
# <a name="best-practices-for-azure-readiness"></a>Melhores práticas de Preparação para o Azure

Uma grande parte da preparação para a nuvem é equipar os funcionários com as habilidades técnicas necessárias para iniciar um esforço de adoção da nuvem e preparar o ambiente de destino de migração para os ativos e as cargas de trabalho que você moverá para a nuvem. Os tópicos a seguir fornecem as melhores práticas e diretrizes adicionais para ajudar sua equipe a estabelecer e preparar o ambiente do Azure.

## <a name="azure-fundamentals"></a>Conceitos básicos do Azure

Use as diretrizes a seguir ao organizar e implantar seus ativos no ambiente do Azure:

- [Conceitos fundamentais do Azure](../considerations/fundamental-concepts.md). Conheça os conceitos fundamentais e os termos usados no Azure. Saiba também como esses conceitos se relacionam entre si.
- [Convenções de nomenclatura e marcação recomendadas](../considerations/name-and-tag.md). Examine as recomendações detalhadas para nomear e marcar seus recursos. Essas recomendações dão suporte aos esforços de adoção de nuvem corporativa.
- [Dimensionamento com várias assinaturas do Azure](../considerations/scaling-subscriptions.md). Compreenda as estratégias de dimensionamento com várias assinaturas do Azure.
- [Organizar seus recursos com grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups/?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como os grupos de gerenciamento do Azure podem gerenciar recursos, funções, políticas e a implantação em várias assinaturas.
- [Criar uma consistência de nuvem híbrida](../../infrastructure/misc/hybrid-consistency.md). Crie soluções de nuvem híbrida que fornecem os benefícios da inovação na nuvem, mantendo muitas das conveniências do gerenciamento local.

## <a name="networking"></a>Rede

Use as diretrizes a seguir para preparar sua infraestrutura de rede de nuvem para dar suporte às suas cargas de trabalho:

- [Decisões de rede](../considerations/network-decisions.md). Escolha os serviços, as ferramentas e as arquiteturas de rede que darão suporte aos requisitos de carga de trabalho, governança e conectividade de sua organização.
- [Planejamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como planejar redes virtuais com base em seus requisitos de isolamento, conectividade e localização.
- [Melhores práticas de segurança de rede](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Conheça as melhores práticas para resolver problemas comuns de segurança de rede usando funcionalidades internas do Azure.
- [Redes de perímetro](./perimeter-networks.md). Também conhecidas como DMZs (zonas desmilitarizadas), as redes de perímetro permitem a conectividade segura entre as redes de nuvem e as redes locais ou do datacenter físico, juntamente com qualquer conectividade com a Internet.
- [Topologia de rede hub e spoke](./hub-spoke-network-topology.md). Hub e spoke é um modelo de rede para o gerenciamento eficiente dos requisitos comuns de comunicação ou segurança para cargas de trabalho complicadas. Também aborda as possíveis limitações da assinatura do Azure.

## <a name="identity-and-access-control"></a>Identidade e controle de acesso

Use as diretrizes a seguir ao projetar sua infraestrutura de identidade e controle de acesso para melhorar a segurança e a eficiência do gerenciamento de suas cargas de trabalho:

- [Melhores práticas de segurança do controle de acesso e gerenciamento de identidades do Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Conheça as melhores práticas de gerenciamento de identidades e controle de acesso usando funcionalidades internas do Azure.
- [Melhores práticas de controle de acesso baseado em função](./roles.md). O RBAC (controle de acesso baseado em função) do Azure oferece gerenciamento de acesso refinado baseado em grupo para os recursos organizados em torno das funções de usuário.
- [Como proteger o acesso privilegiado em implantações híbridas e de nuvem no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Use o Azure Active Directory para garantir que as contas do administrador e o acesso administrativo de sua organização sejam seguros em seu ambiente de nuvem e local.

## <a name="storage"></a>Armazenamento

- [Diretrizes do Armazenamento do Azure](../considerations/storage-guidance.md). Selecione a solução ideal do Armazenamento do Azure para dar suporte aos seus cenários de uso.
- [Guia de segurança do Armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-security-guide?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba mais sobre os recursos de segurança do Armazenamento do Azure.

## <a name="databases"></a>Bancos de dados

- [Escolher a opção correta do SQL Server no Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Escolha a solução de PaaS ou IaaS que dê melhor suporte às suas cargas de trabalho do SQL Server.
- [Melhores práticas de segurança do banco de dados](https://docs.microsoft.com/azure/security/azure-database-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Conheça as melhores práticas de segurança de banco de dados na plataforma Azure.
- [Escolher o armazenamento de dados correto](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview). Selecionar o armazenamento de dados certo para seus requisitos é uma decisão de design chave. Literalmente, há centenas de implementações para escolher entre Banco de dados NoSQL e SQL. Os armazenamentos de dados geralmente são categorizados por como eles estruturam dados e os tipos de operações às quais fornecem suporte. Este artigo descreve vários dos modelos de armazenamentos mais comuns.

## <a name="cost-management"></a>Gerenciamento de custo

- [Como controlar os custos em unidades de negócios, ambientes e projetos](./track-costs.md). Conheça as melhores práticas de criação de mecanismos apropriados de controle de custos.
- [Como otimizar seu investimento na nuvem com o Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Implemente uma estratégia de gerenciamento de custos e saiba mais sobre as ferramentas disponíveis para resolver os desafios de custos.
- [Criar e gerenciar orçamentos](https://docs.microsoft.com/azure/cost-management/tutorial-acm-create-budgets?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como criar e gerenciar orçamentos com o Gerenciamento de Custos do Azure.
- [Exportar dados de custo](https://docs.microsoft.com/azure/cost-management/tutorial-export-acm-data?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como criar e gerenciar os dados exportados no Gerenciamento de Custos do Azure.
- [Otimizar os custos com base nas recomendações](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como identificar os recursos subutilizados e tomar medidas para reduzir os custos usando o Gerenciamento de Custos do Azure e o Assistente do Azure.
- [Usar alertas de custo para monitorar o uso e os gastos](https://docs.microsoft.com/azure/cost-management/cost-mgt-alerts-monitor-usage-spending?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json). Saiba como usar alertas do Gerenciamento de Custos para monitorar seu uso e seus gastos do Azure.
