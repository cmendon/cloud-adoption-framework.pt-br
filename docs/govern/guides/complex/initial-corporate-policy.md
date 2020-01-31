---
title: 'Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança'
description: 'Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2949c89b5cafd472af98245a37cae43e69c634a4
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806298"
---
# <a name="governance-guide-for-complex-enterprises-initial-corporate-policy-behind-the-governance-strategy"></a>Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança

A política corporativa a seguir define a posição de governança inicial, que é o ponto de partida para este guia. Este artigo define o estágio inicial de riscos, instruções de política inicial e processos antecipados para impor as declarações de política.

> [!NOTE]
>A política corporativa não é um documento técnico, mas conduz muitas decisões técnicas. A governança MVP descrita na [visão geral](./index.md) deriva, por fim, essa política. Antes de implementar uma governança MVP, sua organização deve desenvolver uma política corporativa com base em seus próprios objetivos e riscos de negócios.

## <a name="cloud-governance-team"></a>Equipe de governança de nuvem

Recentemente, o CIO ocupou uma reunião com a equipe de governança de ti para entender o histórico dos dados pessoais e as políticas de missão crítica e examinar o efeito de alterar essas políticas. O CIO também abordou o potencial geral da nuvem para ti e para a empresa.

Após a reunião, os dois membros da equipe de governança de TI solicitaram permissão para pesquisar e dar suporte a iniciativas de planejamento de nuvem. Ao reconhecer a necessidade de governança e uma oportunidade para limitar a TI invisível, o Diretor de Governança de TI apoiou essa ideia. Com isso, a equipe de governança de nuvem nasceu. Nos próximos meses, ela herdará a limpeza dos muitos erros cometidos durante a exploração na nuvem de uma perspectiva de governança. Isso irá ganhar o moniker dos _responsáveis pela nuvem_. Em iterações posteriores, este guia mostrará como suas funções são alteradas ao longo do tempo.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicadores de tolerância

A tolerância a riscos atual é alta e o apetite de investir em governança de nuvem é baixo. Dessa forma, os indicadores de tolerância atuam como um sistema de avisos antecipados para disparar mais investimento de tempo e energia. Se os seguintes indicadores forem observados, seria prudente avançar a estratégia de governança.

- **Gerenciamento de custos:** A escala de implantação excede 1.000 ativos para a nuvem, ou gastos mensais excedem $10000 USD por mês.
- **Linha de base de identidade:** Inclusão de aplicativos com requisitos de autenticação multifator herdados ou de terceiros.
- **Linha de base de segurança:** Inclusão de dados protegidos em planos de adoção de nuvem definidos.
- **Consistência de recursos:** Inclusão de qualquer aplicativo de missão crítica em planos de adoção de nuvem definidos.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Próximos passos

Essa política corporativa prepara a equipe de governança de nuvem para implementar o MVP de governança, que será a base para a adoção. A próxima etapa é implementar esse MVP.

> [!div class="nextstepaction"]
> [Práticas recomendadas explicadas](./prescriptive-guidance.md)
