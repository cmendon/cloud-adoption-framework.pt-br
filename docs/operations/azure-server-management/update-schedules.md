---
title: Criar agendas de atualização
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criar agendas de atualização
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: eb48ba0b591df72e933c85a466bf096198f369e9
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70834539"
---
# <a name="create-update-schedules"></a>Criar agendas de atualização

Você pode gerenciar agendas de atualização usando o portal do Azure ou os novos módulos de cmdlet do PowerShell.

Para criar um agendamento de atualização por meio do portal do Azure, consulte [agendar uma implantação de atualização](/azure/automation/automation-tutorial-update-management#schedule-an-update-deployment).

O módulo AZ. Automation agora dá suporte à configuração do gerenciamento de atualizações usando Azure PowerShell. A [versão 1.7.0](https://www.powershellgallery.com/packages/Az/1.7.0) do módulo adiciona suporte para o cmdlet [New-AzAutomationUpdateManagementAzureQuery](/powershell/module/az.automation/new-azautomationupdatemanagementazurequery?view=azps-1.7.0) , que permite que você use marcas, local e pesquisas salvas para configurar agendamentos de atualização para um grupo de computadores flexível.

## <a name="example-script"></a>Script de exemplo

O script de exemplo a seguir ilustra o uso de marcação e consulta para criar grupos dinâmicos de computadores aos quais você pode aplicar agendas de atualização. Ele executa as seguintes ações. Você pode consultar as implementações das ações específicas ao criar seus próprios scripts.

- Cria uma agenda de atualização da automação do Azure que é executada a cada sábado às 8:00
- Cria uma consulta para computadores que correspondem a estes critérios:
  - Implantado `westus`no `eastus`, ou `eastus2` no local do Azure
  - Ter uma `Owner` marca aplicada a eles com um valor definido como`JaneSmith`
  - Ter uma `Production` marca aplicada a eles com um valor definido como`true`
- Aplica o agendamento de atualização às máquinas consultadas e define uma janela de atualização de duas horas

Antes de executar o script de exemplo, você precisará entrar usando o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) . Ao iniciar o script, você precisará fornecer as seguintes informações:

- A ID da assinatura de destino
- O grupo de recursos de destino
- O nome do espaço de trabalho Log Analytics
- O nome da sua conta de automação do Azure

```powershell
<#
    .SYNOPSIS
        This script orchestrates the deployment of the solutions and the agents.
    .Parameter SubscriptionName
    .Parameter WorkspaceName
    .Parameter AutomationAccountName
    .Parameter ResourceGroupName

#>

param (
    [Parameter(Mandatory=$true)]
    [string]$SubscriptionId,

    [Parameter(Mandatory=$true)]
    [string]$ResourceGroupName,

    [Parameter(Mandatory=$true)]
    [string]$WorkspaceName,

    [Parameter(Mandatory=$true)]
    [string]$AutomationAccountName,

    [Parameter(Mandatory=$false)]
    [string]$scheduleName = "SaturdayCritialSecurity"
)

Import-Module Az.Automation

$startTime = ([DateTime]::Now).AddMinutes(10)
$schedule = New-AzAutomationSchedule -ResourceGroupName $ResourceGroupName `
                                     -AutomationAccountName $AutomationAccountName `
                                     -StartTime $startTime `
                                     -Name $scheduleName `
                                     -Description "Saturday patches" `
                                     -DaysOfWeek Saturday `
                                     -WeekInterval 1 `
                                     -ForUpdateConfiguration

# Using AzAutomationUpdateManagementAzureQuery to create dynamic groups.

$queryScope = @("/subscriptions/$SubscriptionID/resourceGroups/")

$query1Location =@("westus", "eastus", "eastus2")
$query1FilterOperator = "Any"
$ownerTag = @{"Owner"= @("JaneSmith")}
$ownerTag.add("Production", "true")

$DGQuery = New-AzAutomationUpdateManagementAzureQuery -ResourceGroupName $ResourceGroupName `
                                       -AutomationAccountName $AutomationAccountName `
                                       -Scope $queryScope `
                                       -Tag $ownerTag

$AzureQueries = @($DGQuery)

$UpdateConfig = New-AzAutomationSoftwareUpdateConfiguration -ResourceGroupName $ResourceGroupName `
                                                             -AutomationAccountName $AutomationAccountName `
                                                             -Schedule $schedule `
                                                             -Windows `
                                                             -Duration (New-TimeSpan -Hours 2) `
                                                             -AzureQuery $AzureQueries `
                                                             -IncludedUpdateClassification Security,Critical
```

## <a name="next-steps"></a>Próximas etapas

Veja exemplos de como implementar [políticas comuns no Azure](./common-policies.md) que podem ajudar a gerenciar seus servidores.

> [!div class="nextstepaction"]
> [Políticas comuns no Azure](./common-policies.md)