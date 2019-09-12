---
title: Gerenciamento de acesso aos recursos no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Explicação dos constructos de gerenciamento de acesso de recursos no Azure: Azure Resource Manager, assinaturas, grupos de recursos e recursos'
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 369cba95e0c5232bf22a7ec5ab146073b0f29649
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70824321"
---
# <a name="resource-access-management-in-azure"></a>Gerenciamento de acesso aos recursos no Azure

A [governança de nuvem](../index.md) descreve as cinco disciplinas de governança de nuvem, que inclui o gerenciamento de recursos. [O que é governança de acesso de recurso](index.md) explica como o gerenciamento de acesso de recurso se enquadra na disciplina de gerenciamento de recursos. Antes de prosseguir para aprender a criar um modelo de governança, é importante entender os controles de gerenciamento de acesso a recursos no Azure. A configuração desses controles de gerenciamento de acesso a recursos constitui a base do seu modelo de governança.

Comece examinando mais detalhadamente como os recursos são implantados no Azure.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-an-azure-resource"></a>O que é um recurso do Azure?

No Azure, o termo _recurso_ refere-se a uma entidade gerenciada pelo Azure. Por exemplo, máquinas virtuais, redes virtuais e contas de armazenamento são todas consideradas recursos do Azure.

![Diagrama de um recurso](../../_images/governance-1-9.png)
*Figura 1-um recurso.*

## <a name="what-is-an-azure-resource-group"></a>O que é um grupo de recursos do Azure?

Cada recurso no Azure deve pertencer a um [grupo de recurso](/azure/azure-resource-manager/resource-group-overview#resource-groups). Um grupo de recursos é simplesmente um constructo lógico que agrupa vários recursos para que eles possam ser gerenciados como uma única entidade. Por exemplo, os recursos que compartilham um ciclo de vida semelhante, como os recursos para um [aplicativo de n camadas](/azure/architecture/guide/architecture-styles/n-tier) podem ser criados ou excluídos como um grupo.

![Diagrama de um grupo de recursos que contém](../../_images/governance-1-10.png)
um recurso*Figura 2-um grupo de recursos contém um recurso.*

Os grupos de recursos e os recursos que eles contêm são associados a uma **assinatura** do Azure.

## <a name="what-is-an-azure-subscription"></a>O que é uma assinatura do Azure?

Uma assinatura do Azure é semelhante a um grupo de recursos em que ele é um constructo lógico que agrupa os grupos de recursos e seus recursos. No entanto, uma assinatura do Azure também é associada aos controles usados pelo Azure Resource Manager. O que isso significa? Examine detalhadamente o Azure Resource Manager para saber mais sobre o relacionamento entre ele e uma assinatura do Azure.

![Diagrama de uma assinatura](../../_images/governance-1-11.png)
do Azure*Figura 3-uma assinatura do Azure.*

## <a name="what-is-azure-resource-manager"></a>O que é o Azure Resource Manager?

Em [Como funciona o Azure?](../../getting-started/what-is-azure.md) você aprendeu que o Azure inclui um "front-end" com muitos serviços que orquestram todas as funções do Azure. Um desses serviços é o [Azure Resource Manager](/azure/azure-resource-manager), que hospeda a API RESTful usada pelos clientes para gerenciar recursos.

![Diagrama de Azure Resource Manager](../../_images/governance-1-12.png)
*Figura 4-Azure Resource Manager.*

A figura a seguir mostra três clientes: [PowerShell](/powershell/azure/overview), o [portal do Azure](https://portal.azure.com)e o [CLI do Azure](/cli/azure):

![Diagrama de clientes do Azure conectando-se](../../_images/governance-1-13.png)
à API Azure Resource Manager*Figura 5-os clientes do Azure se conectam à API RESTful Azure Resource Manager.*

Embora esses clientes conectem o Azure Resource Manager usando a API RESTful, o Azure Resource Manager não inclui a funcionalidade para gerenciar recursos diretamente. Em vez disso, a maioria dos tipos de recursos no Azure têm seus próprios [ **provedores de recursos**](/azure/azure-resource-manager/resource-group-overview#terminology).

![Provedores](../../_images/governance-1-14.png)
de recursos do Azure*Figura 6-provedores de recursos do Azure.*

Quando um cliente faz uma solicitação para gerenciar um recurso específico, o Azure Resource Manager conecta o provedor de recursos daquele tipo de recurso para concluir a solicitação. Por exemplo, se um cliente fizer uma solicitação para gerenciar um recurso de máquina virtual, o Azure Resource Manager conectará o provedor de recursos **Microsoft.Compute**.

![Azure Resource Manager se conectando ao provedor](../../_images/governance-1-15.png)
de recursos Microsoft. Compute *, Figura 7-Azure Resource Manager conecta-se ao provedor de recursos **Microsoft. Compute** para gerenciar o recurso especificado na solicitação do cliente.*

O Azure Resource Manager requer que o cliente especifique um identificador para a assinatura e o grupo de recursos para gerenciar o recurso da máquina virtual.

Agora que você tem uma compreensão de como o Azure Resource Manager funciona, retorne à discussão sobre como uma assinatura do Azure está associada aos controles usados pelo Azure Resource Manager. Antes que qualquer solicitação de gerenciamento de recursos possa ser executada pelo Azure Resource Manager, um conjunto de controles será verificado.

O primeiro controle é que uma solicitação deve ser feita por um usuário validado e o Azure Resource Manager tem uma relação de confiança com o [AD (Azure Active Directory)](/azure/active-directory) para fornecer funcionalidade de identidade do usuário.

![Azure Active Directory](../../_images/governance-1-16.png)
*Figura 8-Azure Active Directory.*

No Azure AD, os usuários são segmentados em **locatários**. Um locatário é um constructo lógico que representa uma instância segura e dedicada do Azure AD geralmente associada a uma organização. Cada assinatura está associada a um locatário do Azure Active Directory.

![Um locatário do Azure ad associado a uma](../../_images/governance-1-17.png)
assinatura*Figura 9-um locatário do Azure ad associado a uma assinatura.*

Cada solicitação de cliente para gerenciar um recurso em uma assinatura específica exige que o usuário tenha uma conta associada ao locatário do Azure AD.

O próximo controle é uma verificação de que o usuário tem permissão suficiente para fazer a solicitação. As permissões são atribuídas aos usuários que usam o [controle de acesso baseado em função (RBAC)](/azure/role-based-access-control).

![Usuários atribuídos a funções RBAC](../../_images/governance-1-18.png)
*Figura 10. Cada usuário no locatário é atribuído a uma ou mais funções RBAC.*

Uma função RBAC especifica um conjunto de permissões que um usuário pode executar em um recurso específico. Quando a função é atribuída ao usuário, essas permissões são aplicadas. Por exemplo, a [função de **proprietário** interna](/azure/role-based-access-control/built-in-roles#owner) permite que um usuário realize qualquer ação em um recurso.

O próximo controle é uma verificação de que a solicitação será permitida sob as configurações especificadas da [política de recursos do Azure](/azure/governance/policy). As políticas de recursos do Azure especificam as operações permitidas para um recurso específico. Por exemplo, uma política de recursos do Azure pode especificar que os usuários só têm permissão para implantar um tipo específico de máquina virtual.

![Política de recursos do Azure](../../_images/governance-1-19.png)
*Figura 11. Políticas de recursos do Azure.*

O próximo controle é uma verificação de que a solicitação não excede um [limite de assinatura do Azure](/azure/azure-subscription-service-limits). Por exemplo, cada assinatura tem um limite de 980 grupos de recursos por assinatura. Se uma solicitação é recebida para implantar um grupo de recursos adicionais depois que o limite for atingido, ela será negada.

![Limites de recursos do Azure](../../_images/governance-1-20.png)
*Figura 12. Limites de recursos do Azure.*

O controle final é uma verificação de que a solicitação está dentro do compromisso financeiro associado à assinatura. Por exemplo, se a solicitação for implantar uma máquina virtual, o Azure Resource Manager verificará se a assinatura tem informações de pagamento suficientes.

![Um compromisso financeiro associado a uma assinatura](../../_images/governance-1-21.png)
*Figura 13. Um compromisso financeiro é associado a uma assinatura.*

## <a name="summary"></a>Resumo

Neste artigo, você aprendeu sobre como o acesso a recursos é gerenciado no Azure usando o Azure Resource Manager.

## <a name="next-steps"></a>Próximas etapas

Agora que você sabe como gerenciar acesso de recurso no Azure, prossiga para aprender como criar um modelo de controle [para uma carga de trabalho simples](governance-simple-workload.md) ou para [várias equipe](governance-multiple-teams.md) usando esses serviços.

> [!div class="nextstepaction"]
> [Uma visão geral de governança](../index.md)
