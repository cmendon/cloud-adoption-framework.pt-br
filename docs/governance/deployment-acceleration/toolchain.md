---
title: Ferramentas de Aceleração de implantação no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de Aceleração de implantação no Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 62058d6a7d8d05b046e29a03650ca0f095a3789d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828962"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Ferramentas de Aceleração de implantação no Azure

[A Aceleração de implantação](index.md) é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md). Esta disciplina se concentra em maneiras de estabelecer políticas para controlar a configuração de ativos ou implantação. Dentro das cinco disciplinas de governança de nuvem, a disciplina de aceleração da implantação envolve a implantação e o alinhamento da configuração. Isso pode ocorrer por meio de atividades manuais ou atividades de DevOps totalmente automatizadas. Em ambos os casos, as políticas envolvidas permanecerão basicamente as mesmas.

Responsáveis da nuvem, guardiões da nuvem e arquitetos da nuvem com interesse na governança, cada um provavelmente irá investir muito tempo na disciplina de Aceleração de implantação, o que codifica as políticas e os requisitos entre vários esforços de adoção de nuvem. As ferramentas neste ferramentas são importantes para a equipe de governança de nuvem e devem ter prioridade alta no roteiro de aprendizagem para a equipe.

A seguir, é apresentada uma lista de ferramentas nativas do Azure que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

|  | [Azure Policy](/azure/governance/policy/overview) | [Grupos de Gerenciamento do Azure](/azure/governance/management-groups) | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) | [Azure Blueprints](/azure/governance/blueprints/overview) | [Grafo de recursos do Azure](/azure/governance/resource-graph/overview) | [Gerenciamento de Custos do Azure](/azure/cost-management) |
|---------|---------|---------|---------|---------|---------|---------|
|Implementar políticas corporativas     |Sim |Não  |Não  |Não | Não |Não |
|Aplicar políticas entre assinaturas     |Necessário |Sim  |Não  |Não | Não |Não |
|Implantar recursos definidos     |Não |Não  |Sim  |Não | Não |Não |
|Criar ambientes em conformidade total      |Necessário |Necessário  |Necessário  |Sim | Não |Não |
|Políticas de auditoria      |Sim |Não  |Não  |Não | Não |Não |
|Recursos de Consulta do Azure      |Não |Não  |Não  |Não |Sim |Não |
|Relatório sobre o custo dos recursos      |Não |Não  |Não  |Não |Não |Sim |

A seguir estão as ferramentas adicionais que podem ser necessárias para atingir os objetivos de aceleração de implantação específicos. Geralmente, essas ferramentas são usadas fora da equipe de governança, mas ainda são consideradas um aspecto de aceleração de implantação como uma disciplina.

|  | [Portal do Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)  | [Azure Policy](/azure/governance/policy/overview) | [Azure DevOps](/azure/devops/index) | [Serviço de Backup do Azure](/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|
|Implantação manual (único ativo)     | Sim | sim  | Não  | Não é eficiente | Não | Sim |
|Implantação manual (todo o ambiente)     | Não é eficiente | Sim | Não  | Não é eficiente | Não | Sim |
|Implantação automatizada (todo o ambiente)     | Não  | Sim  | Não  | Sim  | Não | Sim |
|Atualize a configuração de um servidor único     | Sim | Sim | Não é eficiente | Não é eficiente | Não | Sim, durante a replicação |
|Atualizar a configuração de um ambiente completo     | Não é eficiente | Sim | Sim | sim  | Não | Sim, durante a replicação |
|Gerenciar o descompasso da configuração     | Não é eficiente | Não é eficiente | Sim  | sim  | Não | Sim, durante a replicação |
|Criar um pipeline automatizado para implantar o código e configurar ativos (DevOps)     | Não | Não | Não | Sim | Não | Não |

Além de ferramentas nativas do Azure mencionadas acima, é comum que os clientes usem ferramentas de terceiros para facilitar as implantações de Aceleração de implantação e DevOps.
