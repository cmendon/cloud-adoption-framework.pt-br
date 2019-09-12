---
title: Motivações de Gerenciamento de Custos e riscos de negócios
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivações de Gerenciamento de Custos e riscos de negócios
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 328352ac7ccd8cacbc92cc09ce0c07e2843afcf1
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829118"
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

- **Controle de orçamento:** Controlar o orçamento não pode levar a gastos excessivos com um fornecedor de nuvem.
- **Perda de utilização:** As precompras ou os precompromissos que não são usados podem resultar em investimentos desperdiçados.
- **Anomalias de gastos:** Picos inesperados em qualquer direção podem ser indicadores de uso inapropriado.
- **Ativos com provisionamento excessivo:** Quando os ativos são implantados em uma configuração que excede as necessidades de um aplicativo ou máquina virtual (VM), podem aumentar os custos e desperdício.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Entenda os indicadores, métricas e tolerância a risco](./metrics-tolerance.md)
