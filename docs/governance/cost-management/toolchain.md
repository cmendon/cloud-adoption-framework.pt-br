---
title: Ferramentas de Gerenciamento de Custos no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de Gerenciamento de Custos no Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 32c05e04c224f88008ded6e9fe2c69bb6095d346
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828091"
---
# <a name="cost-management-tools-in-azure"></a>Ferramentas de Gerenciamento de Custos no Azure

O [Gerenciamento de Custos](./index.md) é uma das [Cinco disciplinas de Governança de Nuvem](../governance-disciplines.md). Essa disciplina concentra-se em maneiras de estabelecer planos de gastos com a nuvem, alocação de orçamentos de nuvem, monitoramento e imposição de orçamentos de nuvem, detecção de anomalias de alto custo e ajuste do plano de governança de nuvem quando os gastos reais estiverem desalinhados.

A seguir, é apresentada uma lista de ferramentas nativas do Azure que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

| Ferramenta | [Portal do Azure](https://azure.microsoft.com/features/azure-portal)  | [Gerenciamento de Custos do Azure](/azure/cost-management/overview-cost-mgt)  | [Pacote de conteúdo do EA do Azure](/power-bi/service-connect-to-azure-enterprise)  | [Azure Policy](/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Enterprise Agreement necessário?     | Não         | Não         | Sim         | Não         |
|Controle de orçamento     | Não         | Sim         | Não         | Sim         |
|Monitorar gastos em um único recurso    | Sim         | Sim         | sim         | Não         |
|Monitorar gastos em vários recursos    | Não         | Sim        | sim         | Não         |
|Controlar gastos em um único recurso     | Sim - dimensionamento manual         | Sim         | Não         | Sim         |
|Impor gastos em vários recursos    | Não         | Sim         | Não         | Sim         |
|Impor metadados de contabilidade em recursos    | Não         | Não         | Não         | Sim         |
|Monitorar e detectar tendências     | Sim - limitado         | Sim        | sim         | Não         |
|Detectar anomalias de gastos     | Não         | Sim        | sim         | Não        |
|Socializar desvios     | Não        | Sim        | sim        | Não        |