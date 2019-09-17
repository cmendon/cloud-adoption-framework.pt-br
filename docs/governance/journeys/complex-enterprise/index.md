---
title: Guia de governança para empresas complexas
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guia de governança para empresas complexas
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c3962409f71f82319a6e5efc2313c03a44456298
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908414"
---
# <a name="governance-guide-for-complex-enterprises"></a>Guia de governança para empresas complexas

## <a name="overview-of-best-practices"></a>Visão geral de melhores práticas

Esse guia de governança segue as experiências de uma empresa fictícia por vários estágios de maturidade de governança. Ela se baseia em experiências de clientes reais. As práticas recomendadas sugeridas baseiam-se nas restrições e necessidades da empresa fictícia.

Como um ponto de partida rápido, esta visão geral define um produto mínimo viável (MVP) para um controle com base em práticas recomendadas. Também fornece links para algumas melhorias de governança que adicionam ainda mais práticas recomendadas conforme novos negócios ou riscos técnicos surgem.

> [!WARNING]
> Este MVP é um ponto de partida de linha de base, com base em um conjunto de suposições. Até mesmo esse conjunto mínimo de práticas recomendadas tem como base as políticas corporativas orientadas por riscos comerciais exclusivos e as tolerâncias de risco. Para ver se essas suposições se aplicam a você, leia a [narrativa mais longa](./narrative.md) que acompanha este artigo.

### <a name="governance-best-practices"></a>Melhores práticas de governança

Estas melhores práticas servem como uma base para uma organização adicionar proteções de governança de forma rápida e consistente entre várias assinaturas do Azure.

### <a name="resource-organization"></a>Organização do recurso

O diagrama a seguir mostra a hierarquia de MVP de governança para organizar recursos.

![Diagrama de organização do recurso](../../../_images/governance/resource-organization.png)

Todos os aplicativos devem ser implantados na área apropriada do grupo de gerenciamento, assinatura e hierarquia de grupo de recursos. Durante o planejamento da implantação, a equipe de governança de nuvem criará os nós necessários na hierarquia para capacitar as equipes de adoção da nuvem.

1. Defina um grupo de gerenciamento para cada unidade de negócios com uma hierarquia detalhada que reflete a geografia e, em seguida, o tipo de ambiente (por exemplo, produção ou não produção).
1. Crie uma assinatura para cada combinação exclusiva de unidade de negócios, geografia, ambiente e "Categorização de aplicativo".
1. Crie um grupo de recursos separado para cada aplicativo.
1. Aplique uma [nomenclatura consistente](../../../ready/considerations/name-and-tag.md) em cada nível dessa hierarquia de agrupamento.

![Diagrama de organização de recurso de empresa de grande porte](../../../_images/governance/large-enterprise-resource-organization.png)

Esses padrões fornecem espaço para crescimento sem complicar a hierarquia desnecessariamente.

[!INCLUDE [governance-of-resources](../../../../includes/caf-governance-of-resources.md)]

<!-- See comments for suggestion to possibly add here -->

## <a name="incremental-governance-improvements"></a>Melhorias incrementais de governança

Quando esse MVP tiver sido implantado, camadas adicionais de governança podem ser incorporadas rapidamente ao ambiente. Aqui estão algumas maneiras de aprimorar o MVP para atender às necessidades específicas de negócios:

- [Linha de base para dados protegidos](./security-baseline-evolution.md)
- [Configurações de recurso para aplicativos de missão crítica](./resource-consistency-evolution.md)
- [Controles para Gerenciamento de Custos](./cost-management-evolution.md)
- [Controles para melhoria incremental em várias nuvens](./multicloud-evolution.md)

<!-- markdownlint-disable MD026 -->

## <a name="what-does-this-guidance-provide"></a>O que essas diretrizes oferecem?

No MVP, nas práticas recomendadas e nas ferramentas da disciplina [Aceleração de implantação](../../deployment-acceleration/index.md), são estabelecidas para aplicar rapidamente a política corporativa. Em particular, o MVP usa o Azure Blueprints, Azure Policy e grupos de gerenciamento do Azure para aplicar algumas políticas corporativas básicas, conforme definido na narrativa para esta empresa fictícia. Essas políticas corporativas são aplicadas usando modelos do Azure Resource Manager e as políticas do Azure para estabelecer uma linha de base pequena para identidade e segurança.

![Exemplo de MVP de governança incremental](../../../_images/governance/governance-mvp.png)

## <a name="incremental-improvements-to-governance-practices"></a>Melhorias incrementais de práticas de governança

Ao longo do tempo, esse controle MVP será usado para aprimorar de modo incremental as práticas de governança. Conforme a adoção avança, aumenta o risco de negócios. Várias disciplinas dentro do modelo de governança da Cloud Adoption Framework vão se adaptar para gerenciar esses riscos. Outros artigos desta série discutem as alterações na política corporativa que afetam a empresa fictícia. Três alterações ocorrem em quatro disciplinas:

- Linha de base de identidade, conforme as dependências da migração se alteram a narrativa.
- Gerenciamento de Custos como escalas de adoção.
- Linha de base de segurança, como os dados protegidos são implantados.
- Consistência de recursos, como operações de TI começam a dar suporte a cargas de trabalho de missão crítica.

![Exemplo de MVP de governança incremental](../../../_images/governance/governance-evolution-large.png)

## <a name="next-steps"></a>Próximas etapas

Agora que você está familiarizado com a governança MVP e as alterações futuras na governança, leia a narrativa de suporte para obter contexto adicional.

> [!div class="nextstepaction"]
> [Leia a narrativa de suporte](./narrative.md)