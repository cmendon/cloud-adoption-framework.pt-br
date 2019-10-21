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
ms.openlocfilehash: fc06264bad61571aaa4735350a16e294492dd9c0
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547704"
---
# <a name="improve-your-initial-cloud-governance-foundation"></a>Aprimore sua base de governança de nuvem inicial

Este artigo pressupõe que você estabeleceu uma [base de governança de nuvem inicial](./initial-foundation.md). À medida que seu plano de adoção de nuvem é implementado, riscos tangíveis surgirão das abordagens propostas pelas quais as equipes desejam adotar a nuvem. À medida que esses riscos surgirem em conversas de planejamento de lançamentos, use a grade a seguir para identificar rapidamente algumas práticas recomendadas para ficar à frente do plano de adoção, a fim de evitar que os riscos se tornem ameaças reais.

## <a name="maturity-vectors"></a>Vetores de maturidade

A qualquer momento, as práticas recomendadas a seguir podem ser aplicadas à base de governança inicial para resolver o risco ou a necessidade mencionada na tabela a seguir.

> [!IMPORTANT]
> A organização de recursos pode afetar como essas práticas recomendadas são aplicadas. É importante começar com as recomendações que melhor se alinham com a base de governança de nuvem inicial que você implementou na etapa anterior.

|Risco/necessidade | Enterprise Standard | Empresarial complexa |
|---|---|---|
|Dados confidenciais na nuvem|[Aprimoramento da disciplina](./guides/standard/security-baseline-improvement.md)|[Aprimoramento da disciplina](./guides/complex/security-baseline-improvement.md)|
|Aplicativos de missão crítica na nuvem|[Aprimoramento da disciplina](./guides/standard/resource-consistency-improvement.md)|[Aprimoramento da disciplina](./guides/complex/resource-consistency-improvement.md)|
|Gerenciamento de custos de nuvem|[Aprimoramento da disciplina](./guides/standard/cost-management-improvement.md)|[Aprimoramento da disciplina](./guides/complex/cost-management-improvement.md)|
|Multinuvem|[Aprimoramento da disciplina](./guides/standard/multicloud-improvement.md)|[Aprimoramento da disciplina](./guides/complex/multicloud-improvement.md)|
|Gerenciamento de identidade complexo/herdado|N/D|[Aprimoramento da disciplina](./guides/complex/identity-baseline-improvement.md)|
|Várias camadas de governança|N/D|[Aprimoramento da disciplina](./guides/complex/multiple-layers-of-governance.md)|

## <a name="next-steps"></a>Próximos passos

Além da aplicação das práticas recomendadas, a metodologia de governança na estrutura de adoção de nuvem pode ser personalizada para se ajustar a restrições de negócios exclusivas. Depois de seguir as recomendações aplicáveis, [avalie a política corporativa para entender os requisitos de personalização adicionais](./corporate-policy.md).

> [!div class="nextstepaction"]
> [Avaliar política corporativa](./corporate-policy.md)
