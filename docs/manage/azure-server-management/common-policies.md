---
title: Exemplos comuns de Azure Policy
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Exemplos comuns de Azure Policy
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 0d998f06e73c03a74cdaf5fbd75cb605fa9a2fbb
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547306"
---
# <a name="common-azure-policy-examples"></a>Exemplos comuns de Azure Policy

[Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) pode ajudá-lo a aplicar governança aos seus recursos de nuvem. Esse serviço pode ajudá-lo a criar guardrails que garantem a conformidade de toda a empresa com os requisitos de política de governança. Para criar políticas, use os cmdlets portal do Azure ou PowerShell. Este artigo fornece exemplos de cmdlet do PowerShell.

> [!NOTE]
> Com Azure Policy, as políticas de imposição (**deployIfNotExists**) não são implantadas automaticamente em VMs existentes. A correção é necessária para manter essas VMs em conformidade. Para obter mais informações, consulte [corrigir recursos não compatíveis com Azure Policy](https://docs.microsoft.com/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Exemplos de políticas comuns

As seções a seguir descrevem algumas políticas usadas com frequência.

### <a name="restrict-resource-regions"></a>Restringir regiões de recursos

A conformidade com a política e a regulamentação geralmente dependerá do controle do local físico em que os recursos são implantados. Você pode usar uma política interna para permitir que os usuários criem recursos somente em regiões do Azure na lista de permissões. Você pode encontrar essa política no portal pesquisando por "local" na página definição de política.

Ou você pode executar este cmdlet para localizar a política:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*location*") }
```

O script a seguir mostra como atribuir a política. Para usar o script, altere o valor `$SubscriptionID` para que ele aponte para a assinatura à qual você deseja atribuir a política. Antes de executar o script, você precisará entrar usando o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

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

Você pode usar esse mesmo script para aplicar as outras políticas discutidas neste artigo. Basta substituir o GUID na linha que define `$AllowedLocationPolicy` com o GUID da política que você deseja aplicar.

### <a name="block-certain-resource-types"></a>Bloquear determinados tipos de recursos

Outra política interna comum que é usada para controlar os custos permite que você bloqueie determinados tipos de recursos. Você pode encontrar essa política no portal pesquisando "tipos de recurso permitidos" na página definição de política.

Ou você pode executar este cmdlet para localizar a política:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Depois de identificar a política que você deseja usar, você pode modificar o exemplo do PowerShell na seção [restringir regiões de recursos](#restrict-resource-regions) para atribuir a política.

### <a name="restrict-vm-size"></a>Restringir o tamanho da VM

O Azure oferece uma ampla variedade de tamanhos de VM para dar suporte a vários tipos de cargas de trabalho. Para controlar seu orçamento, você pode criar uma política que permita apenas um subconjunto de tamanhos de VM em suas assinaturas.

### <a name="deploy-antimalware"></a>Implantar Antimalware

Você pode usar essa política para implantar uma extensão do Microsoft Iaasantimalware da com uma configuração padrão para VMs que não são protegidas por antimalware.

O GUID da política é `2835b622-407b-4114-9198-6f7064cbe0dc`.

O script a seguir mostra como atribuir a política. Para usar o script, altere o valor `$SubscriptionID` para que ele aponte para a assinatura à qual você deseja atribuir a política. Antes de executar o script, você precisará entrar usando o cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

$AntimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

#Replace location “eastus” with the value you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $AntimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre outros serviços e ferramentas de gerenciamento de servidor que estão disponíveis.

> [!div class="nextstepaction"]
> [Ferramentas e serviços de gerenciamento do servidor do Azure](./tools-services.md)
