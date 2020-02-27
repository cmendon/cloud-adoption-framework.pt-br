---
title: Ferramentas de Gerenciamento de Custos no Azure
description: Veja como as ferramentas nativas do Azure podem ajudar as políticas e os processos maduros que dão suporte à disciplina de governança de gerenciamento de custos.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 70014352d4b7f64f5c73a0fda96ef453f1a77176
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708777"
---
# <a name="cost-management-tools-in-azure"></a>Ferramentas de Gerenciamento de Custos no Azure

O [Gerenciamento de Custos](./index.md) é uma das [Cinco disciplinas de Governança de Nuvem](../governance-disciplines.md). Essa disciplina concentra-se em maneiras de estabelecer planos de gastos com a nuvem, alocação de orçamentos de nuvem, monitoramento e imposição de orçamentos de nuvem, detecção de anomalias de alto custo e ajuste do plano de governança de nuvem quando os gastos reais estiverem desalinhados.

A seguir, é apresentada uma lista de ferramentas nativas do Azure que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

| Ferramenta | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management/overview-cost-mgt)  | [Pacote de conteúdo do EA do Azure](https://docs.microsoft.com/power-bi/service-connect-to-azure-enterprise)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Enterprise Agreement necessário?     | Não         | Não         | Sim         | Não         |
|Controle de orçamento     | Não         | Sim         | Não         | Sim         |
|Monitorar gastos em um único recurso    | Sim         | Sim         | Sim         | Não         |
|Monitorar gastos em vários recursos    | Não         | Sim        | Sim         | Não         |
|Controlar gastos em um único recurso     | Sim - dimensionamento manual         | Sim         | Não         | Sim         |
|Impor gastos em vários recursos    | Não         | Sim         | Não         | Sim         |
|Impor metadados de contabilidade em recursos    | Não         | Não         | Não         | Sim         |
|Monitorar e detectar tendências     | Sim          | Sim        | Sim         | Não         |
|Detectar anomalias de gastos     | Não         | Sim        | Sim         | Não        |
|Socializar desvios     | Não        | Sim        | Sim        | Não        |
