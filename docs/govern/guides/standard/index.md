---
title: Guia de governança corporativa padrão
description: Siga uma empresa fictícia padrão por meio de vários estágios de maturidade de governança enquanto define um MVP (produto viável mínimo) com base nas melhores práticas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 481a617d3a09ae1f81fe313dd557314aed8f4f29
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706826"
---
# <a name="standard-enterprise-governance-guide"></a>Guia de governança corporativa padrão

## <a name="overview-of-best-practices"></a>Visão geral de melhores práticas

Esse guia de governança segue as experiências de uma empresa fictícia por vários estágios de maturidade de governança. Ela se baseia em experiências de clientes reais. As melhores práticas baseiam-se nas restrições e necessidades da empresa fictícia.

Como um ponto de partida rápido, esta visão geral define um produto mínimo viável (MVP) para um controle com base em práticas recomendadas. Também fornece links para algumas melhorias de governança que adicionam ainda mais práticas recomendadas conforme novos negócios ou riscos técnicos surgem.

> [!WARNING]
> Este MVP é um ponto de partida de linha de base, com base em um conjunto de suposições. Até mesmo esse conjunto mínimo de práticas recomendadas tem como base as políticas corporativas orientadas por riscos comerciais exclusivos e as tolerâncias de risco. Para ver se essas suposições se aplicam a você, leia a [narrativa mais longa](./narrative.md) que acompanha este artigo.

### <a name="governance-best-practices"></a>Melhores práticas de governança

Estas melhores práticas servem como base para uma organização adicionar proteções de governança de forma rápida e consistente em todas as suas assinaturas.

### <a name="resource-organization"></a>Organização do recurso

O diagrama a seguir mostra a hierarquia de MVP de governança para organizar recursos.

![Diagrama de organização do recurso](../../../_images/govern/resource-organization.png)

Todos os aplicativos devem ser implantados na área apropriada do grupo de gerenciamento, assinatura e hierarquia de grupo de recursos. Durante o planejamento da implantação, a equipe de governança de nuvem criará os nós necessários na hierarquia para capacitar as equipes de adoção da nuvem.

1. Um grupo de gerenciamento para cada tipo de ambiente (por exemplo, produção, desenvolvimento e teste).
2. Duas assinaturas: uma para cargas de trabalho de produção e outra para cargas de trabalho de não produção.
3. A [nomenclatura consistente](../../../ready/azure-best-practices/naming-and-tagging.md) deve ser aplicada em cada nível dessa hierarquia de agrupamento.
4. Os grupos de recursos devem ser implantados de uma maneira que considere seu ciclo de vida de conteúdo: tudo o que é desenvolvido em conjunto é gerenciado em conjunto e o que é desativado junto fica junto. Para saber mais sobre melhores práticas de grupo de recursos, [confira aqui](../../../decision-guides/resource-consistency/index.md).
5. A [seleção de região](../../../decision-guides/regions/index.md) é incrivelmente importante e deve ser considerada para que a rede, o monitoramento e a auditoria possam estar em vigor para failover/failback, assim como a confirmação de que os [SKUs necessários estão disponíveis nas regiões preferenciais](https://azure.microsoft.com/global-infrastructure/services).

Veja um exemplo desse padrão em uso:

![Exemplo de organização do recurso para uma empresa de médio porte](../../../_images/govern/mid-market-resource-organization.png)

Esses padrões fornecem espaço para crescimento sem complicar a hierarquia desnecessariamente.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

## <a name="iterative-governance-improvements"></a>Melhorias de governança iterativa

Quando esse MVP tiver sido implantado, camadas adicionais de governança poderão ser incorporadas rapidamente ao ambiente. Aqui estão algumas maneiras de aprimorar o MVP para atender às necessidades específicas de negócios:

- [Linha de base para dados protegidos](./security-baseline-improvement.md)
- [Configurações de recurso para aplicativos de missão crítica](./resource-consistency-improvement.md)
- [Controles para Gerenciamento de Custos](./cost-management-improvement.md)
- [Controles para evolução de várias nuvens](./multicloud-improvement.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>O que essas diretrizes oferecem?

No MVP, nas práticas recomendadas e nas ferramentas da disciplina [Aceleração de implantação](../../deployment-acceleration/index.md), são estabelecidas para aplicar rapidamente a política corporativa. Em particular, o MVP usa o Azure Blueprints, Azure Policy e grupos de gerenciamento do Azure para aplicar algumas políticas corporativas básicas, conforme definido na narrativa para esta empresa fictícia. Essas políticas corporativas são aplicadas usando modelos do Resource Manager e as políticas do Azure para estabelecer uma pequena linha de base para identidade e segurança.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-mvp.png)

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

Ao longo do tempo, esse controle MVP será usado para aprimorar as práticas de governança. Conforme a adoção avança, aumenta o risco de negócios. Várias disciplinas dentro do modelo de governança da Cloud Adoption Framework sofrerão alterações para gerenciar esses riscos. Artigos mais adiante nesta série discutem a melhoria incremental da política corporativa que afeta a empresa fictícia. Três melhorias ocorrem em três disciplinas:

- Gerenciamento de Custos como escalas de adoção.
- Linha de base de segurança, como os dados protegidos são implantados.
- Consistência de recursos, como operações de TI começam a dar suporte a cargas de trabalho de missão crítica.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-improvement.png)

## <a name="next-steps"></a>Próximas etapas

Agora que você está familiarizado com o MVP de governança e tem uma ideia das melhorias de governança a seguir, leia a narrativa de suporte para obter contexto adicional.

> [!div class="nextstepaction"]
> [Leia a narrativa de suporte](./narrative.md)
