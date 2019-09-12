---
title: 'Guia de governança para empresas complexas: Política corporativa inicial por trás da estratégia de governança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: Política corporativa inicial por trás da estratégia de governança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ddf6ca5f482d93a75a5748773e746e44fc0b8218
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908924"
---
# <a name="governance-guide-for-complex-enterprises-initial-corporate-policy-behind-the-governance-strategy"></a>Guia de governança para empresas complexas: Política corporativa inicial por trás da estratégia de governança

A política corporativa a seguir define a posição de governança inicial, que é o ponto de partida para este guia. Este artigo define o estágio inicial de riscos, instruções de política inicial e processos antecipados para impor as declarações de política.

> [!NOTE]
>A política corporativa não é um documento técnico, mas conduz muitas decisões técnicas. A governança MVP descrita na [visão geral](./index.md) deriva, por fim, essa política. Antes de implementar uma governança MVP, sua organização deve desenvolver uma política corporativa com base em seus próprios objetivos e riscos de negócios.

## <a name="cloud-governance-team"></a>Equipe de governança de nuvem

Recentemente, o CIO ocupou uma reunião com a equipe de governança de ti para entender o histórico dos dados pessoais e as políticas de missão crítica e examinar o efeito de alterar essas políticas. O CIO também abordou o potencial geral da nuvem para ti e para a empresa.

Após a reunião, os dois membros da equipe de governança de TI solicitaram permissão para pesquisar e dar suporte a iniciativas de planejamento de nuvem. Ao reconhecer a necessidade de governança e uma oportunidade para limitar a TI invisível, o Diretor de Governança de TI apoiou essa ideia. Com isso, a equipe de governança de nuvem nasceu. Nos próximos meses, ela herdará a limpeza dos muitos erros cometidos durante a exploração na nuvem de uma perspectiva de governança. Isso irá ganhar o moniker dos _responsáveis pela nuvem_. Em iterações posteriores, este guia mostrará como suas funções são alteradas ao longo do tempo.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicadores de tolerância

A tolerância a riscos atual é alta e o apetite de investir em governança de nuvem é baixo. Dessa forma, os indicadores de tolerância atuam como um sistema de avisos antecipados para disparar mais investimento de tempo e energia. Se os seguintes indicadores forem observados, seria prudente avançar a estratégia de governança.

- **Gerenciamento de custos:** A escala de implantação excede 1.000 ativos para a nuvem ou os gastos mensal excedem 100 milhões de dólares por mês.
- **Linha de base de identidade:** Inclusão de aplicativos com requisitos de autenticação multifator herdados ou de terceiros.
- **Linha de base de segurança:** Inclusão dos dados protegidos em planos de adoção definida da nuvem.
- **Consistência de recursos:** Inclusão de todos os aplicativos críticos em planos de adoção definida da nuvem.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Próximas etapas

Essa política corporativa prepara a equipe de governança de nuvem para implementar o MVP de governança, que será a base para a adoção. A próxima etapa é implementar esse MVP.

> [!div class="nextstepaction"]
> [Diretrizes prescritivas explicadas](./best-practice-explained.md)
