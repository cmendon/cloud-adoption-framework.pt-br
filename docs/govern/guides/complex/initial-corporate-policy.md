---
title: 'Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 56629e6f313614965ee1baddaa08e4264b4bef53
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547675"
---
# <a name="governance-guide-for-complex-enterprises-initial-corporate-policy-behind-the-governance-strategy"></a>Guia de governança para empresas complexas: política corporativa inicial por trás da estratégia de governança

A política corporativa a seguir define a posição de governança inicial, que é o ponto de partida para este guia. Este artigo define os riscos iniciais, as instruções de política inicial e os processos antecipados para impor instruções de política.

> [!NOTE]
>A política corporativa não é um documento técnico, mas impulsiona muitas decisões técnicas. O MVP de governança descrito na [visão geral](./index.md) deriva dessa política. Antes de implementar um MVP de governança, sua organização deve desenvolver uma política corporativa com base em seus próprios objetivos e riscos de negócios.

## <a name="cloud-governance-team"></a>Equipe de governança de nuvem

Recentemente, o CIO ocupou uma reunião com a equipe de governança de ti para entender o histórico dos dados pessoais e as políticas de missão crítica e examinar o efeito de alterar essas políticas. O CIO também abordou o potencial geral da nuvem para ti e para a empresa.

Após a reunião, dois membros da equipe de controle de ti solicitaram permissão para pesquisar e dar suporte aos esforços de planejamento de nuvem. Reconhecendo a necessidade de governança e uma oportunidade de limitar a ti sombra, o diretor de governança de ti com suporte nessa ideia. Com isso, a equipe de governança de nuvem nasceu. Nos próximos meses, eles herdarão a limpeza de muitos erros feitos durante a exploração na nuvem a partir de uma perspectiva de governança. Isso irá ganhar o moniker dos _responsáveis pela nuvem_. Em iterações posteriores, este guia mostrará como suas funções são alteradas ao longo do tempo.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicadores de tolerância

A tolerância a riscos atual é alta e o apetite para investir na governança de nuvem é baixo. Assim, os indicadores de tolerância atuam como um sistema de aviso antecipado para disparar o investimento de tempo e energia. Se os seguintes indicadores forem observados, seria prudente avançar a estratégia de governança.

- **Gerenciamento de custos:** A escala de implantação excede 1.000 ativos para a nuvem, ou gastos mensais excedem $10000 USD por mês.
- **Linha de base de identidade:** Inclusão de aplicativos com requisitos de autenticação multifator herdados ou de terceiros.
- **Linha de base de segurança:** Inclusão de dados protegidos em planos de adoção de nuvem definidos.
- **Consistência de recursos:** Inclusão de qualquer aplicativo de missão crítica em planos de adoção de nuvem definidos.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Próximos passos

Essa política corporativa prepara a equipe de governança de nuvem para implementar o MVP de governança, que será a base para a adoção. A próxima etapa é implementar esse MVP.

> [!div class="nextstepaction"]
> [Práticas recomendadas explicadas](./prescriptive-guidance.md)
