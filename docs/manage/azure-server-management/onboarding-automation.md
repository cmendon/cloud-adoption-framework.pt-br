---
title: Automatizar a integração e a configuração de alertas
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Automatizar a integração e a configuração de alertas
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 242c8a1a054507c3b1134b1126ea95e3ead74d84
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221362"
---
# <a name="automate-onboarding"></a>Automatizar a integração

Para melhorar a eficiência da implantação dos serviços de gerenciamento do servidor do Azure, considere automatizar a implantação de serviços de gerenciamento usando as recomendações discutidas nas seções anteriores desta orientação. O script e os modelos de exemplo fornecidos nas seções a seguir são pontos iniciais para o desenvolvimento de sua própria automação de processos de integração.

## <a name="onboarding-by-using-automation"></a>Integração usando automação

Este guia tem um repositório GitHub de suporte de código de exemplo, [CloudAdoptionFramework](https://aka.ms/caf/manage/automation-samples), que fornece scripts de exemplo e modelos de Azure Resource Manager para ajudá-lo a automatizar a implantação dos serviços de gerenciamento do servidor do Azure.

Esses arquivos de exemplo ilustram como usar Azure PowerShell cmdlets para automatizar as seguintes tarefas:

1. Crie um [espaço de trabalho log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access) (ou use um espaço de trabalho existente se&mdash;ele atender aos requisitos consulte [planejamento de espaço de trabalho](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

2. Crie uma conta de automação (ou use uma conta existente se atender aos requisitos&mdash;consulte [planejamento de espaço de trabalho](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

3. Vincule a conta de automação e o espaço de trabalho Log Analytics (não é necessário se estiver integração através do Portal).

4. Habilite Gerenciamento de Atualizações e Controle de Alterações e inventário para o espaço de trabalho.

5. Integrar VMs do Azure usando Azure Policy (uma política instala o agente de Log Analytics e o agente de dependência nas VMs do Azure).

6. Integre servidores locais instalando o agente de Log Analytics neles.

Os arquivos descritos na tabela a seguir são usados neste exemplo e você pode personalizá-los para dar suporte aos seus próprios cenários de implantação.

| Nome do Arquivo | Descrição |
|-----------|-------------|
| New-AMSDeployment.ps1 | O principal, orquestrando o script que automatiza a integração. Este script do PowerShell requer uma assinatura existente, mas criará grupos de recursos, local, espaço de trabalho e contas de automação, se não existirem. |
| Workspace-AutomationAccount.json | Um modelo do Resource Manager que implanta os recursos de conta de automação e espaço de trabalho. |
| WorkspaceSolutions.json | Um modelo do Resource Manager que habilita as soluções desejadas no espaço de trabalho Log Analytics. |
| ScopeConfig.json | Um modelo do Resource Manager que usa o modelo de aceitação para servidores locais com a solução de controle de alterações. O uso do modelo de aceitação é opcional. |
| Enable-VMInsightsPerfCounters.ps1 | Um script do PowerShell que habilita o VMInsight para servidores e configura contadores de desempenho. |
| ChangeTracking-Filelist.json | Um modelo do Resource Manager que define a lista de arquivos que serão monitorados pelo Controle de Alterações. |

Você pode executar New-AMSDeployment. ps1 usando o seguinte comando:

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Próximas etapas

Saiba como configurar alertas básicos para notificar sua equipe sobre os principais eventos e problemas de gerenciamento.

> [!div class="nextstepaction"]
> [Configurando alertas básicos](./setup-alerts.md)
