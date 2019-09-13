---
title: Guia de governança para empresas padrão
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guia de governança para empresas padrão
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 82467948ae3141ef1f961ab07a503be485a1bc6f
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908448"
---
# <a name="standard-enterprise-governance-guide"></a>Guia de governança para empresas padrão

## <a name="overview-of-best-practices"></a>Visão geral de melhores práticas

Esse guia de governança segue as experiências de uma empresa fictícia por vários estágios de maturidade de governança. Ela se baseia em experiências de clientes reais. As melhores práticas baseiam-se nas restrições e necessidades da empresa fictícia.

Como um ponto de partida rápido, esta visão geral define um produto mínimo viável (MVP) para um controle com base em uma diretriz prescritiva. Também fornece links para algumas melhorias de governança que adicionam ainda mais melhores práticas conforme novos negócios ou riscos técnicos surgem.

> [!WARNING]
> Este MVP é um ponto de partida de linha de base, com base em um conjunto de suposições. Até mesmo esse conjunto mínimo de práticas recomendadas tem como base as políticas corporativas orientadas por riscos comerciais exclusivos e as tolerâncias de risco. Para ver se essas suposições se aplicam a você, leia a [narrativa mais longa](./narrative.md) que acompanha este artigo.

### <a name="governance-best-practices"></a>Melhores práticas de governança

Estas melhores práticas servem como base para uma organização adicionar proteções de governança de forma rápida e consistente em todas as suas assinaturas.

### <a name="resource-organization"></a>Organização do recurso

O diagrama a seguir mostra a hierarquia de MVP de governança para organizar recursos.

![Diagrama de organização do recurso](../../../_images/governance/resource-organization.png)

Todos os aplicativos devem ser implantados na área apropriada do grupo de gerenciamento, assinatura e hierarquia de grupo de recursos. Durante o planejamento da implantação, a equipe de governança de nuvem criará os nós necessários na hierarquia para capacitar as equipes de adoção da nuvem.

1. Um grupo de gerenciamento para cada tipo de ambiente (por exemplo, produção, desenvolvimento e teste).
2. Duas assinaturas, uma para produção e outra para não produção.
3. Grupos de recursos apropriados com o RBAC aplicado nessas assinaturas.
4. A [nomenclatura consistente](../../../ready/considerations/name-and-tag.md) deve ser aplicada em cada nível dessa hierarquia de agrupamento.

Veja um exemplo desse padrão em uso:

![Exemplo de organização do recurso para uma empresa de médio porte](../../../_images/governance/mid-market-resource-organization.png)

Esses padrões fornecem espaço para crescimento sem complicar a hierarquia desnecessariamente.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

## <a name="iterative-governance-improvements"></a>Melhorias de governança iterativa

Quando esse MVP tiver sido implantado, camadas adicionais de governança poderão ser incorporadas rapidamente ao ambiente. Aqui estão algumas maneiras de aprimorar o MVP para atender às necessidades específicas de negócios:

- [Linha de base para dados protegidos](./security-baseline-evolution.md)
- [Configurações de recurso para aplicativos de missão crítica](./resource-consistency-evolution.md)
- [Controles para Gerenciamento de Custos](./cost-management-evolution.md)
- [Controles para evolução de várias nuvens](./multicloud-evolution.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>O que essas diretrizes oferecem?

No MVP, nas práticas recomendadas e nas ferramentas da disciplina [Aceleração de implantação](../../deployment-acceleration/index.md), são estabelecidas para aplicar rapidamente a política corporativa. Em particular, o MVP usa o Azure Blueprints, Azure Policy e grupos de gerenciamento do Azure para aplicar algumas políticas corporativas básicas, conforme definido na narrativa para esta empresa fictícia. Essas políticas corporativas são aplicadas usando modelos do Resource Manager e as políticas do Azure para estabelecer uma pequena linha de base para identidade e segurança.

![Exemplo de MVP de governança incremental](../../../_images/governance/governance-mvp.png)

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

Ao longo do tempo, esse controle MVP será usado para aprimorar as práticas de governança. Conforme a adoção avança, aumenta o risco de negócios. Várias disciplinas dentro do modelo de governança da Cloud Adoption Framework sofrerão alterações para gerenciar esses riscos. Artigos mais adiante nesta série discutem a melhoria incremental da política corporativa que afeta a empresa fictícia. Três melhorias ocorrem em três disciplinas:

- Gerenciamento de Custos como escalas de adoção.
- Linha de base de segurança, como os dados protegidos são implantados.
- Consistência de recursos, como operações de TI começam a dar suporte a cargas de trabalho de missão crítica.

![Exemplo de MVP de governança incremental](../../../_images/governance/governance-evolution.png)

## <a name="next-steps"></a>Próximas etapas

Agora que você está familiarizado com a governança MVP e tem uma ideia das melhorias de governança a seguir, leia a narrativa de suporte para obter contexto adicional.

> [!div class="nextstepaction"]
> [Leia a narrativa de suporte](./narrative.md)
