---
title: Automatizar a integração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Automatizar a integração
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 83e1cd80bcb821ba1b815291f7f25f875ba66284
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73751591"
---
# <a name="automate-onboarding"></a>Automatizar a integração

Para melhorar a eficiência da implantação dos serviços de gerenciamento do servidor do Azure, considere automatizar a implantação conforme discutido nas seções anteriores desta orientação. O script e os modelos de exemplo fornecidos nas seções a seguir são pontos iniciais para o desenvolvimento de sua própria automação de processos de integração.

Este guia tem um repositório GitHub de suporte de código de exemplo, [CloudAdoptionFramework](https://aka.ms/caf/manage/automation-samples). O repositório fornece scripts de exemplo e modelos de Azure Resource Manager para ajudá-lo a automatizar a implantação dos serviços de gerenciamento do servidor do Azure.

Os arquivos de exemplo ilustram como usar Azure PowerShell cmdlets para automatizar as seguintes tarefas:

- Crie um [espaço de trabalho log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access). (Ou use um espaço de trabalho existente se ele atender aos requisitos. Para obter detalhes, consulte [planejamento de espaço de trabalho](./prerequisites.md#log-analytics-workspace-and-automation-account-planning).

- Crie uma conta de automação. (Ou use uma conta existente se atender aos requisitos. Para obter detalhes, consulte [planejamento de espaço de trabalho](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

- Vincule a conta de automação e o espaço de trabalho Log Analytics. Essa etapa não será necessária se você estiver integrando usando o portal do Azure.

- Habilite Gerenciamento de Atualizações e Controle de Alterações e inventário para o espaço de trabalho.

- Integre VMs do Azure usando Azure Policy. Uma política instala o agente de Log Analytics e o Microsoft Dependency Agent nas VMs do Azure.

- Integre servidores locais instalando o agente de Log Analytics neles.

Os arquivos descritos na tabela a seguir são usados neste exemplo. Você pode personalizá-los para dar suporte aos seus próprios cenários de implantação.

| Nome do arquivo | Descrição |
|-----------|-------------|
| New-AMSDeployment. ps1 | O principal, orquestrando o script que automatiza a integração. Ele cria grupos de recursos e contas de local, espaço de trabalho e automação, se eles ainda não existirem. Este script do PowerShell requer uma assinatura existente. |
| Espaço de trabalho-AutomationAccount. JSON | Um modelo do Resource Manager que implanta os recursos de conta de automação e espaço de trabalho. |
| WorkspaceSolutions. JSON | Um modelo do Resource Manager que habilita as soluções que você deseja no espaço de trabalho Log Analytics. |
| ScopeConfig. JSON | Um modelo do Resource Manager que usa o modelo de aceitação para servidores locais com a solução Controle de Alterações. O uso do modelo de aceitação é opcional. |
| Enable-VMInsightsPerfCounters. ps1 | Um script do PowerShell que habilita as informações de VM para servidores e configura contadores de desempenho. |
| ChangeTracking-FileList. JSON | Um modelo do Resource Manager que define a lista de arquivos que serão monitorados pelo Controle de Alterações. |

Use o comando a seguir para executar New-AMSDeployment. ps1:

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Próximos passos

Saiba como configurar alertas básicos para notificar sua equipe sobre os principais eventos e problemas de gerenciamento.

> [!div class="nextstepaction"]
> [Configurar alertas básicos](./setup-alerts.md)
