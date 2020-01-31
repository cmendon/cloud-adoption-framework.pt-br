---
title: Exemplos comuns de Azure Policy
description: Exemplos comuns de Azure Policy
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7020ffed2395d6c22f835d66cd1c539b525f37c3
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808117"
---
# <a name="common-azure-policy-examples"></a>Exemplos comuns de Azure Policy

[Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) pode ajudá-lo a aplicar governança aos seus recursos de nuvem. Esse serviço pode ajudá-lo a criar guardrails que garantem a conformidade de toda a empresa com os requisitos de política de governança. Para criar políticas, use os cmdlets portal do Azure ou PowerShell. Este artigo fornece exemplos de cmdlet do PowerShell.

> [!NOTE]
> Com Azure Policy, as políticas de imposição (**deployIfNotExists**) não são implantadas automaticamente em VMs existentes. A correção é necessária para manter as VMs em conformidade. Para obter mais informações, consulte [corrigir recursos não compatíveis com Azure Policy](https://docs.microsoft.com/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Exemplos de políticas comuns

As seções a seguir descrevem algumas políticas usadas com frequência.

### <a name="restrict-resource-regions"></a>Restringir regiões de recursos

A conformidade com a política e a regulamentação geralmente depende do controle do local físico em que os recursos são implantados. Você pode usar uma política interna para permitir que os usuários criem recursos somente em determinadas regiões do Azure permitidas.

Para localizar essa política no portal, procure "local" na página definição de política. Ou execute este cmdlet para localizar a política:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*location*") }
```

O script a seguir mostra como atribuir a política. Altere o valor `$SubscriptionID` para apontar para a assinatura à qual você deseja atribuir a política. Antes de executar o script, use o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) para entrar.

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

#Replace the -Name GUID with the policy GUID you want to assign.
$AllowedLocationPolicy = Get-AzPolicyDefinition -Name "e56962a6-4747-49cd-b67b-bf8b01975c4c"

#Replace the locations with the ones you want to specify.
$policyParam = '{"listOfAllowedLocations":{"value":["eastus","westus"]}}'
New-AzPolicyAssignment -Name "Allowed Location" -DisplayName "Allowed locations for resource creation" -Scope $scope -PolicyDefinition $AllowedLocationPolicy -Location eastus -PolicyParameter $policyparam
```

Você também pode usar esse script para aplicar as outras políticas que são discutidas neste artigo. Basta substituir o GUID na linha que define `$AllowedLocationPolicy` com o GUID da política que você deseja aplicar.

### <a name="block-certain-resource-types"></a>Bloquear determinados tipos de recursos

Outra política interna comum que é usada para controlar os custos também pode ser usada para bloquear determinados tipos de recursos.

Para localizar essa política no portal, pesquise "tipos de recursos permitidos" na página definição de política. Ou execute este cmdlet para localizar a política:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Depois de identificar a política que você deseja usar, você pode modificar o exemplo do PowerShell na seção [restringir regiões de recursos](#restrict-resource-regions) para atribuir a política.

### <a name="restrict-vm-size"></a>Restringir o tamanho da VM

O Azure oferece uma ampla variedade de tamanhos de VM para dar suporte a várias cargas de trabalho. Para controlar seu orçamento, você pode criar uma política que permita apenas um subconjunto de tamanhos de VM em suas assinaturas.

### <a name="deploy-antimalware"></a>Implantar Antimalware

Você pode usar essa política para implantar uma extensão do Microsoft *iaasantimalware da* com uma configuração padrão para VMs que não são protegidas por antimalware.

O GUID da política é `2835b622-407b-4114-9198-6f7064cbe0dc`.

O script a seguir mostra como atribuir a política. Para usar o script, altere o valor `$SubscriptionID` para apontar para a assinatura à qual você deseja atribuir a política. Antes de executar o script, use o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) para entrar.

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

$AntimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

#Replace location “eastus” with the value that you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $AntimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre outros serviços e ferramentas de gerenciamento de servidor que estão disponíveis.

> [!div class="nextstepaction"]
> [Ferramentas e serviços de gerenciamento do servidor do Azure](./tools-services.md)
