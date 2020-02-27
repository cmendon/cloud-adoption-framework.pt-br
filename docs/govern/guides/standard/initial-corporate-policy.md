---
title: 'Governança empresarial padrão: política corporativa inicial'
description: Use a estrutura de adoção de nuvem para o Azure para definir uma posição de governança inicial, riscos de estágio inicial, instruções de política iniciais e processos de imposição antecipada.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: f3afbeb33904473fbfd0d1590437cee68b80a7e4
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709049"
---
# <a name="standard-enterprise-governance-guide-initial-corporate-policy-behind-the-governance-strategy"></a>Guia de governança empresarial padrão: política corporativa inicial por trás da estratégia de governança

A política corporativa a seguir define uma posição de governança inicial, que é o ponto de partida para este guia. Este artigo define o estágio inicial de riscos, instruções de política inicial e processos antecipados para impor as declarações de política.

> [!NOTE]
>A política corporativa não é um documento técnico, mas conduz muitas decisões técnicas. A governança MVP descrita na [visão geral](./index.md) deriva, por fim, essa política. Antes de implementar uma governança MVP, sua organização deve desenvolver uma política corporativa com base em seus próprios objetivos e riscos de negócios.

## <a name="cloud-governance-team"></a>Equipe de governança de nuvem

Nesta narra, a equipe de governança de nuvem é composta por dois administradores de sistemas que reconheceram a necessidade de governança. Nos próximos meses, eles herdarão o trabalho de limpar a governança da presença de nuvem da empresa, ganhando a eles o título dos responsáveis pela _nuvem_. Em iterações subsequentes, esse título provavelmente será alterado.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicadores de tolerância

A tolerância a riscos atual é alta e o apetite de investir em governança de nuvem é baixo. Dessa forma, os indicadores de tolerância a atuam como um sistema de avisos antecipados para disparar mais investimento de tempo e energia. Se e quando os seguintes indicadores forem observados, você deverá melhorar iterativamente a estratégia de governança.

- **Gerenciamento de custos:** A escala de implantação excede os limites predeterminados de número de recursos ou custo mensal.
- **Linha de base de segurança:** Inclusão de dados protegidos em planos de adoção de nuvem definidos.
- **Consistência de recursos:** Inclusão de qualquer aplicativo de missão crítica em planos de adoção de nuvem definidos.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Próximas etapas

Essa política corporativa prepara a equipe de governança de nuvem para implementar o MVP de governança, que será a base para a adoção. A próxima etapa é implementar esse MVP.

> [!div class="nextstepaction"]
> [Práticas recomendadas explicadas](./prescriptive-guidance.md)
