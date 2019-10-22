---
title: Gerenciar o acesso ao seu ambiente do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como configurar o controle de acesso para seu ambiente do Azure com o RBAC (controle de acesso baseado em função).
author: LijuKodicheraJayadevan
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC, setup
ms.localizationpriority: high
ms.openlocfilehash: 7ce8b1f8509ab0e51c94913ef010eb35b22b8978
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72379026"
---
# <a name="manage-access-to-your-azure-environment-with-role-based-access-controls"></a>Gerenciar o acesso ao seu ambiente do Azure com controles de acesso baseado em função

Gerenciar quem pode acessar seus recursos e assinaturas do Azure constitui uma parte importante de sua estratégia de governança do Azure e a atribuição de direitos e privilégios de acesso baseado em grupo é uma boa prática. Lidar com grupos em vez de usuários individuais simplifica a manutenção de políticas de acesso, fornece gerenciamento de acesso consistente entre equipes e reduz erros de configuração. O RBAC (controle de acesso baseado em função) do Azure é o principal método de gerenciamento de acesso no Azure.

O RBAC oferece o gerenciamento de acesso detalhado dos recursos no Azure. Ele ajuda você a gerenciar quem tem acesso aos recursos do Azure, o que eles podem fazer com esses recursos e que escopo eles podem acessar.

Ao planejar sua estratégia de controle de acesso, conceda a usuários o menor privilégio necessário para realizarem seus trabalhos. A imagem a seguir mostra um padrão sugerido para a atribuição de RBAC.

![Diagrama que mostra as funções de RBAC](./media/manage-access/role-examples.png)

Ao planejar sua metodologia de controle de acesso, recomendamos que você trabalhe com pessoas em suas organizações com as seguintes funções: segurança e conformidade, administração de TI e arquiteto corporativo.

A Cloud Adoption Framework oferece diretrizes adicionais sobre como [usar o controle de acesso baseado em função](../azure-best-practices/roles.md) como parte de seus esforços de adoção de nuvem.

::: zone target="chromeless"

## <a name="actions"></a>Ações

**Conceder acesso ao grupo de recursos:**

Para conceder acesso de um grupo de recursos a um usuário:

1. Vá para **Grupos de recursos**.
1. Selecione um grupo de recursos.
1. Selecione **IAM (Controle de acesso)** .
1. Selecione **+Adicionar** > **Adicionar atribuição de função**.
1. Selecione uma função e, em seguida, atribua o acesso a um usuário, grupo ou entidade de serviço.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups]" submitText="Go to resource groups" ::: form-end

**Conceder acesso à assinatura:**

Para conceder acesso de uma assinatura a um usuário:

1. Vá para **Assinaturas**.
1. Selecione uma assinatura.
1. Selecione **IAM (Controle de acesso)** .
1. Selecione **+Adicionar** > **Adicionar atribuição de função**.
1. Selecione uma função e, em seguida, atribua o acesso a um usuário, grupo ou entidade de serviço.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to subscriptions" ::: form-end

::: zone-end

::: zone target="docs"

## <a name="grant-resource-group-access"></a>Conceder acesso a grupo de recursos

Para conceder acesso de um grupo de recursos a um usuário:

1. Vá para [Grupos de recursos](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Selecione um grupo de recursos.
1. Selecione **IAM (Controle de acesso)** .
1. Selecione **+Adicionar** > **Adicionar atribuição de função**.
1. Selecione uma função e, em seguida, atribua o acesso a um usuário, grupo ou entidade de serviço.

## <a name="grant-subscription-access"></a>Conceder acesso à assinatura

Para conceder acesso de uma assinatura a um usuário:

1. Vá para [Assinaturas](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Selecione uma assinatura.
1. Selecione **IAM (Controle de acesso)** .
1. Selecione **+Adicionar** > **Adicionar atribuição de função**.
1. Selecione uma função e, em seguida, atribua o acesso a um usuário, grupo ou entidade de serviço.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [O que é o RBAC (controle de acesso baseado em função)?](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [Cloud Adoption Framework: use o controle de acesso baseado em função](../azure-best-practices/roles.md)

::: zone-end