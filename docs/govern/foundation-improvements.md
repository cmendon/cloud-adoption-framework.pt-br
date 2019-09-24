---
title: Aprimore sua base de governança de nuvem inicial
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como melhorar incrementalmente sua base de governança de nuvem inicial.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/13/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d7e4c0516e1c52f1fc6ddd8b42485902cb24d58e
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223646"
---
# <a name="improve-your-initial-cloud-governance-foundation"></a>Aprimore sua base de governança de nuvem inicial

Este artigo pressupõe que você estabeleceu uma [base de governança de nuvem inicial](./initial-foundation.md). À medida que seu plano de adoção de nuvem é implementado, riscos tangíveis surgirão das abordagens propostas pelas quais as equipes desejam adotar a nuvem. À medida que esses riscos surgirem em conversas de planejamento de lançamento, use a grade a seguir para identificar rapidamente algumas práticas recomendadas para ficar à frente do plano de adoção, a fim de evitar que os riscos se tornem ameaças reais.

## <a name="maturity-vectors"></a>Vetores de maturidade

A qualquer momento, as orientações prescritivas a seguir podem ser aplicadas à base de governança inicial para resolver o risco ou a necessidade mencionada na tabela a seguir.

> [!IMPORTANT]
> A organização de recursos pode afetar como essas diretrizes prescritivas são aplicadas. É importante começar com as recomendações que melhor se alinham com a base de governança de nuvem inicial que você implementou na etapa anterior.

|Risco/necessidade | Empresa padrão | Empresa complexa |
|---|---|---|
|Dados confidenciais na nuvem|[Diretrizes prescritivas](./guides/standard/security-baseline-improvement.md)|[Diretrizes prescritivas](./guides/complex/security-baseline-improvement.md)|
|Aplicativos de missão crítica na nuvem|[Diretrizes prescritivas](./guides/standard/resource-consistency-improvement.md)|[Diretrizes prescritivas](./guides/complex/resource-consistency-improvement.md)|
|Gerenciamento de custos de nuvem|[Diretrizes prescritivas](./guides/standard/cost-management-improvement.md)|[Diretrizes prescritivas](./guides/complex/cost-management-improvement.md)|
|Multinuvem|[Diretrizes prescritivas](./guides/standard/multicloud-improvement.md)|[Diretrizes prescritivas](./guides/complex/multicloud-improvement.md)|
|Gerenciamento de identidade complexo/herdado|N/D|[Diretrizes prescritivas](./guides/complex/identity-baseline-improvement.md)|
|Múltiplas camadas de governança|N/D|[Diretrizes prescritivas](./guides/complex/multiple-layers-of-governance.md)|

## <a name="next-steps"></a>Próximas etapas

Além da aplicação de diretrizes prescritivas, a metodologia de governança na estrutura de adoção de nuvem pode ser personalizada para se ajustar a restrições de negócios exclusivas. Depois de seguir as recomendações aplicáveis, [avalie a política corporativa para entender os requisitos de personalização adicionais](./corporate-policy.md).

> [!div class="nextstepaction"]
> [Avaliar política corporativa](./corporate-policy.md)
