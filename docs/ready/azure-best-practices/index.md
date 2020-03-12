---
title: Melhores práticas de Preparação para o Azure
description: Saiba como fornecer melhores práticas e diretrizes adicionais para ajudar sua equipe a estabelecer e preparar o ambiente do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 8d44d3981824c9599151391cd3b7e3550ac31cd6
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093562"
---
# <a name="best-practices-for-azure-readiness"></a>Melhores práticas de Preparação para o Azure

Uma grande parte da preparação para a nuvem é equipar os funcionários com as habilidades técnicas necessárias para iniciar um esforço de adoção da nuvem e preparar o ambiente de destino de migração para os ativos e as cargas de trabalho que você moverá para a nuvem. Leia essas melhores práticas e diretrizes adicionais para ajudar sua equipe a preparar o ambiente do Azure.

## <a name="azure-fundamentals"></a>Conceitos básicos do Azure

Organize e implante seus ativos no ambiente do Azure.

- [Conceitos fundamentais do Azure](../considerations/fundamental-concepts.md). Aprenda os principais conceitos e termos do Azure e como esses conceitos se relacionam uns com os outros.
- [Convenções de nomenclatura e marcação recomendadas](../azure-best-practices/naming-and-tagging.md). Examine as recomendações detalhadas para nomear e marcar seus recursos. Essas recomendações dão suporte aos esforços de adoção de nuvem corporativa.
- [Dimensionamento com várias assinaturas do Azure](../azure-best-practices/scaling-subscriptions.md). Compreenda as estratégias de dimensionamento com várias assinaturas do Azure.
- [Organizar seus recursos com grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups/?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como os grupos de gerenciamento do Azure podem gerenciar recursos, funções, políticas e a implantação em várias assinaturas.
- [Criar uma consistência de nuvem híbrida](../considerations/hybrid-consistency.md). Crie soluções de nuvem híbrida que fornecem os benefícios da inovação na nuvem, mantendo muitas das conveniências do gerenciamento local.

## <a name="networking"></a>Rede

Prepare sua infraestrutura de rede de nuvem para dar suporte às suas cargas de trabalho.

- [Decisões de rede](../considerations/networking-options.md). Escolha os serviços, as ferramentas e as arquiteturas de rede que darão suporte aos requisitos de carga de trabalho, governança e conectividade de sua organização.
- [Planejamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Planeje redes virtuais com base em seus requisitos de isolamento, conectividade e localização.
- [Melhores práticas de segurança de rede](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Conheça as melhores práticas para resolver problemas comuns de segurança de rede usando funcionalidades internas do Azure.
- [Redes de perímetro](./perimeter-networks.md). Habilite a conectividade segura entre suas redes de nuvem e as redes locais ou do datacenter físico, juntamente com qualquer conectividade com a Internet.
- [Topologia de rede de hub e spoke](./hub-spoke-network-topology.md). Gerencie a comunicação comum ou os requisitos de segurança com eficiência para cargas de trabalho complicadas e lide com possíveis limitações de assinatura do Azure.

## <a name="identity-and-access-control"></a>Identidade e controle de acesso

Crie sua infraestrutura de identidade e controle de acesso para aprimorar a segurança e a eficiência do gerenciamento de suas cargas de trabalho.

- [Melhores práticas de segurança do controle de acesso e gerenciamento de identidades do Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Conheça as melhores práticas de gerenciamento de identidades e controle de acesso usando funcionalidades internas do Azure.
- [Melhores práticas de controle de acesso baseado em função](../considerations/roles.md). Habilite o gerenciamento de acesso refinado baseado em grupo para os recursos organizados em torno das funções de usuário.
- [Como proteger o acesso privilegiado em implantações híbridas e de nuvem no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-admin-roles-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Verifique se as contas privilegiadas e de acesso administrativo de sua organização são seguras em seu ambiente local e de nuvem.

## <a name="storage"></a>Armazenamento

- [Diretrizes do Armazenamento do Azure](../considerations/storage-options.md). Selecione a solução ideal do Armazenamento do Azure para dar suporte aos seus cenários de uso.
- [Guia de segurança do Armazenamento do Azure](https://docs.microsoft.com/azure/storage/blobs/security-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba mais sobre os recursos de segurança do Armazenamento do Azure.

## <a name="databases"></a>Bancos de dados

- [Escolher a opção correta do SQL Server no Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Escolha a solução de PaaS ou IaaS que dê melhor suporte às suas cargas de trabalho do SQL Server.
- [Melhores práticas de segurança do banco de dados](https://docs.microsoft.com/azure/security/azure-database-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Conheça as melhores práticas de segurança de banco de dados na plataforma Azure.
- [Escolher o armazenamento de dados correto](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview). Selecione o armazenamento de dados certo para atender aos seus requisitos. Centenas de opções de implementação estão disponíveis entre bancos de dados SQL e NoSQL. Os armazenamentos de dados geralmente são categorizados por como eles estruturam dados e os tipos de operações às quais fornecem suporte. Este artigo descreve vários modelos de armazenamentos comuns.

## <a name="cost-management"></a>Gerenciamento de custo

- [Como controlar os custos em unidades de negócios, ambientes e projetos](./track-costs.md). Conheça as melhores práticas de criação de mecanismos apropriados de controle de custos.
- [Como otimizar seu investimento na nuvem com o Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Implemente uma estratégia de gerenciamento de custos e saiba mais sobre as ferramentas disponíveis para resolver os desafios de custos.
- [Criar e gerenciar orçamentos](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-create-budgets?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como criar e gerenciar orçamentos com o Gerenciamento de Custos do Azure.
- [Exportar dados de custo](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-export-acm-data?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como exportar dados de custo usando o Gerenciamento de Custos do Azure.
- [Otimizar os custos com base nas recomendações](https://docs.microsoft.com/azure/cost-management-billing/costs/tutorial-acm-opt-recommendations?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como identificar os recursos subutilizados e reduzir os custos usando o Gerenciamento de Custos do Azure e o Assistente do Azure.
- [Usar alertas de custo para monitorar o uso e os gastos](https://docs.microsoft.com/azure/cost-management-billing/costs/cost-mgt-alerts-monitor-usage-spending?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como usar alertas do Gerenciamento de Custos para monitorar seu uso e seus gastos do Azure.
