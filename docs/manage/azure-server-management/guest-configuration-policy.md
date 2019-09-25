---
title: Política de configuração de convidado
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Política de configuração de convidado
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: c43d07c6cfdea0152559d7a13fec7dde148b1530
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221575"
---
# <a name="guest-configuration-policy"></a>Política de configuração de convidado

A extensão de [configuração de convidado](/azure/governance/policy/concepts/guest-configuration) Azure Policy permite que você audite as definições de configuração em uma máquina virtual. Atualmente, a configuração de convidado tem suporte apenas em VMs do Azure.

Você pode encontrar a lista de políticas de configuração de convidado pesquisando a categoria "configuração de convidado" na página do portal de Azure Policy. Você também pode encontrar a lista executando este cmdlet em uma janela do PowerShell:

```powershell
Get-AzPolicySetDefinition | where-object {$_.Properties.metadata.category -eq "Guest Configuration"}
```

> [!NOTE]
> A funcionalidade de configuração de convidado é atualizada regularmente para dar suporte a conjuntos de políticas adicionais. Verifique se há novas políticas com suporte periodicamente e avalie se elas são úteis para suas necessidades.

<!-- TODO: Update these links when available. 

By default, we recommend enabling the following policies:

- [Preview]: Audit to verify password security settings are set correctly inside Linux and Windows machines.
- Audit to verify that certificates are not nearing expiration on Windows VMs.

-->

## <a name="deployment"></a>Implantação

Você pode usar o seguinte script do PowerShell de exemplo para implantar essas políticas:

- Verifique se as configurações de segurança de senha em computadores Windows e Linux estão definidas corretamente.
- Verifique se os certificados não estão perto de expirar em VMs do Windows.

 Antes de executar esse script, você precisará entrar usando o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) . Ao executar o script, você precisará fornecer o nome da assinatura à qual deseja aplicar as políticas.

```powershell

    #Assign Guest Configuration policy.
    param (
        [Parameter(Mandatory=$true)]
        [string]$SubscriptionName
    )

    $Subscription = Get-AzSubscription -SubscriptionName $SubscriptionName
    $scope = "/subscriptions/" + $Subscription.Id

    $PasswordPolicy = Get-AzPolicySetDefinition -Name "3fa7cbf5-c0a4-4a59-85a5-cca4d996d5a6"
    $CertExpirePolicy = Get-AzPolicySetDefinition -Name "b6f5e05c-0aaa-4337-8dd4-357c399d12ae"

    New-AzPolicyAssignment -Name "PasswordPolicy" -DisplayName "[Preview]: Audit that password security settings are set correctly inside Linux and Windows machines" -Scope $scope -PolicySetDefinition $PasswordPolicy -AssignIdentity -Location eastus

    New-AzPolicyAssignment -Name "CertExpirePolicy" -DisplayName "[Preview]: Audit that certificates are not expiring on Windows VMs" -Scope $scope -PolicySetDefinition $CertExpirePolicy -AssignIdentity -Location eastus

```

## <a name="next-steps"></a>Próximas etapas

Saiba como [habilitar o controle de alterações e os alertas](./enable-tracking-alerting.md) para alterações críticas de arquivo, serviço, software e registro.

> [!div class="nextstepaction"]
> [Habilitar acompanhamento e alertas para alterações críticas](./enable-tracking-alerting.md)
