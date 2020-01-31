---
title: Motivações de Gerenciamento de Custos e riscos de negócios
description: Motivações de Gerenciamento de Custos e riscos de negócios
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 16408b01e06e29fc2697dbbdd053126d026920f0
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806502"
---
# <a name="cost-management-motivations-and-business-risks"></a>Motivações de Gerenciamento de Custos e riscos de negócios

Este artigo aborda os motivos que os clientes normalmente adotam uma disciplina de Gerenciamento de Custos dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios que conduzem as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="is-cost-management-relevant"></a>O Gerenciamento de Custos é relevante?

Em termos de governança de custo, a adoção da nuvem cria uma mudança de paradigma. O gerenciamento de custos em um mundo tradicional local, se baseia em ciclos de atualização, aquisições de datacenter, renovações de host e problemas de manutenção recorrentes. Você pode prever, planejar e refinar cada um desses custos para alinhar com orçamentos anual de despesas de capital.

Para soluções de nuvem, muitas empresas tendem a adotar uma abordagem mais reativa para Gerenciamento de Custos. Em muitos casos, as empresas fazem a compra prévia ou confirmam o uso, uma quantidade de conjunto de serviços de nuvem. Este modelo assume que a maximização de descontos à vista com base em planos de negócios quanto nos gastos com um fornecedor de nuvem específicos, cria a percepção de um ciclo de custo proativo, planejado. No entanto, essa percepção só se tornará uma realidade se a empresa também implementar disciplinas de Gerenciamento de Custos maduras.

A nuvem oferece recursos de auto-atendimento que eram anteriormente conhecidos como datacenters locais tradicionais. Esses novos recursos capacitam empresas a ser mais ágil, menos restritiva e mais aberta para adotar novas tecnologias. No entanto, a desvantagem de autoatendimento é que os usuários finais podem exceder inadvertidamente os orçamentos alocados. Por outro lado, os mesmos usuários podem enfrentar uma alteração nos planos e inesperadamente não usar a quantidade de serviços de nuvem prevista. O potencial de alternância em qualquer direção justifica o investimento em uma disciplina de Gerenciamento de Custos dentro da equipe de governança.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de Gerenciamento de Custos tenta abordar riscos comerciais principais relacionados a despesas incorridas ao hospedar cargas de trabalho baseadas em nuvem. Trabalhar com seus negócios para identificar esses riscos e monitorar cada um deles para relevância como planejar e implementar suas implantações de nuvem.

Os riscos serão diferentes entre a organização, mas os seguintes servem como riscos comuns relacionados a custo que você pode usar como um ponto de partida para discussões em sua equipe de governança de nuvem:

- **Controle de orçamento:** Não controlar o orçamento pode levar a gastos excessivos com um fornecedor de nuvem.
- **Perda de utilização:** As precompras ou os precompromissos que não são usados podem resultar em perda de investimentos.
- **Anomalias de gastos:** Picos inesperados em qualquer direção podem ser indicadores de uso impróprio.
- **Ativos com provisionamento excessivo:** Quando os ativos são implantados em uma configuração que excede as necessidades de um aplicativo ou VM (máquina virtual), eles podem criar resíduos.

## <a name="next-steps"></a>Próximos passos

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Depois de obter uma compreensão dos riscos de negócios realísticos, a próxima etapa é documentar a tolerância de risco da empresa e os indicadores e métricas-chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Entenda os indicadores, métricas e tolerância a risco](./metrics-tolerance.md)
