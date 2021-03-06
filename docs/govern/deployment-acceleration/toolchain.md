---
title: Ferramentas de Aceleração de implantação no Azure
description: Veja como as ferramentas nativas do Azure podem ajudar processos e políticas maduros que dão suporte à disciplina de governança de aceleração de implantação.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ee1c81fe5bada0fa435a598db2f79dc0b23b4392
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708998"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Ferramentas de Aceleração de implantação no Azure

[A Aceleração de implantação](./index.md) é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md). Esta disciplina se concentra em maneiras de estabelecer políticas para controlar a configuração de ativos ou implantação. Dentro das cinco disciplinas de governança de nuvem, a disciplina de aceleração da implantação envolve a implantação e o alinhamento da configuração. Isso pode ocorrer por meio de atividades manuais ou atividades de DevOps totalmente automatizadas. Em ambos os casos, as políticas envolvidas permanecerão basicamente as mesmas.

Responsáveis da nuvem, guardiões da nuvem e arquitetos da nuvem com interesse na governança, cada um provavelmente irá investir muito tempo na disciplina de Aceleração de implantação, o que codifica as políticas e os requisitos entre vários esforços de adoção de nuvem. As ferramentas neste ferramentas são importantes para a equipe de governança de nuvem e devem ter prioridade alta no roteiro de aprendizagem para a equipe.

A seguir, é apresentada uma lista de ferramentas nativas do Azure que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

|  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Grupos de Gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups) | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview) | [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Grafo de recursos do Azure](https://docs.microsoft.com/azure/governance/resource-graph/overview) | [Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management) |
|---------|---------|---------|---------|---------|---------|---------|
|Implementar políticas corporativas     |Sim |Não  |Não  |Não | Não |Não |
|Aplicar políticas entre assinaturas     |Obrigatório |Sim  |Não  |Não | Não |Não |
|Implantar recursos definidos     |Não |Não  |Sim  |Não | Não |Não |
|Criar ambientes em conformidade total      |Obrigatório |Obrigatório  |Obrigatório  |Sim | Não |Não |
|Políticas de auditoria      |Sim |Não  |Não  |Não | Não |Não |
|Recursos de Consulta do Azure      |Não |Não  |Não  |Não |Sim |Não |
|Relatório sobre o custo dos recursos      |Não |Não  |Não  |Não |Não |Sim |

A seguir estão as ferramentas adicionais que podem ser necessárias para atingir os objetivos de aceleração de implantação específicos. Geralmente, essas ferramentas são usadas fora da equipe de governança, mas ainda são consideradas um aspecto de aceleração de implantação como uma disciplina.

|  | [Azure portal](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Azure DevOps](https://docs.microsoft.com/azure/devops/index) | [Serviço de Backup do Azure](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|
|Implantação manual (único ativo)     | Sim | Sim  | Não  | Não é eficiente | Não | Sim |
|Implantação manual (todo o ambiente)     | Não é eficiente | Sim | Não  | Não é eficiente | Não | Sim |
|Implantação automatizada (todo o ambiente)     | Não  | Sim  | Não  | Sim  | Não | Sim |
|Atualize a configuração de um servidor único     | Sim | Sim | Não é eficiente | Não é eficiente | Não | Sim, durante a replicação |
|Atualizar a configuração de um ambiente completo     | Não é eficiente | Sim | Sim | Sim  | Não | Sim, durante a replicação |
|Gerenciar o descompasso da configuração     | Não é eficiente | Não é eficiente | Sim  | Sim  | Não | Sim, durante a replicação |
|Criar um pipeline automatizado para implantar o código e configurar ativos (DevOps)     | Não | Não | Não | Sim | Não | Não |

Além de ferramentas nativas do Azure mencionadas acima, é comum que os clientes usem ferramentas de terceiros para facilitar as implantações de Aceleração de implantação e DevOps.
