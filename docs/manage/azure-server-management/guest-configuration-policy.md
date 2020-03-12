---
title: Política de configuração de convidado
description: Use a estrutura de adoção de nuvem para o Azure para aprender a usar a extensão de configuração de convidado Azure Policy para auditar as definições de configuração em uma VM do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 73373e5cc56ef7e5804151171a22ad9f541f1cd3
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79094695"
---
# <a name="guest-configuration-policy"></a>Política de configuração de convidado

Você pode usar a extensão de [configuração de convidado](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration) Azure Policy para auditar as definições de configuração em uma máquina virtual. Atualmente, a configuração de convidado tem suporte apenas em VMs do Azure.

Para localizar a lista de políticas de configuração de convidado, procure "configuração de convidado" na página do portal de Azure Policy. Ou execute este cmdlet em uma janela do PowerShell para encontrar a lista:

```powershell
Get-AzPolicySetDefinition | where-object {$_.Properties.metadata.category -eq "Guest Configuration"}
```

> [!NOTE]
> A funcionalidade de configuração de convidado é atualizada regularmente para dar suporte a conjuntos de políticas adicionais. Verifique se há novas políticas com suporte periodicamente e avalie se elas serão úteis.

<!-- TODO: Update these links when available. 

By default, we recommend that you enable the following policies:

- [Preview]: Audit to verify that password-security settings are correct on Linux and Windows machines.
- Audit to verify that certificates are not nearing expiration on Windows VMs.

-->

## <a name="deployment"></a>Implantação

Use o exemplo de script do PowerShell a seguir para implantar essas políticas em:

- Verifique se as configurações de segurança de senha em computadores Windows e Linux estão definidas corretamente.
- Verifique se os certificados não estão perto de expirar em VMs do Windows.

 Antes de executar esse script, use o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) para entrar. Ao executar o script, você deve fornecer o nome da assinatura à qual deseja aplicar as políticas.

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
