---
title: Conceitos fundamentais do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda conceitos e termos fundamentais usados no Azure e como os conceitos se relacionam entre si.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 02d4cf1218c6b00dd0d42dfb877af49a92498115
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548818"
---
# <a name="azure-fundamental-concepts"></a>Conceitos fundamentais do Azure

Aprenda conceitos e termos fundamentais que são usados no Azure e como os conceitos se relacionam uns com os outros.

## <a name="azure-terminology"></a>Terminologia do Azure

É útil conhecer as seguintes definições ao começar seus esforços de adoção de nuvem do Azure:

- **Recurso**: uma entidade que é gerenciada pelo Azure. Os exemplos incluem máquinas virtuais do Azure, redes virtuais e contas de armazenamento.
- **Assinatura**: um contêiner lógico para seus recursos. Cada recurso do Azure é associado a apenas uma assinatura. A criação de uma assinatura é a primeira etapa na adoção do Azure.
- **Conta do Azure**: o endereço de email que você fornece ao criar uma assinatura do Azure é a conta do Azure para a assinatura. A parte que está associada à conta de email é responsável pelos custos mensais incorridos pelos recursos na assinatura. Ao criar uma conta do Azure, você fornece informações de contato e detalhes de cobrança, como um cartão de crédito. Você pode usar a mesma conta do Azure (endereço de email) para várias assinaturas. Cada assinatura é associada a apenas uma conta do Azure.
- **Administrador da conta**: a parte associada ao endereço de email usado para criar uma assinatura do Azure. O administrador da conta é responsável por pagar por todos os custos incorridos pelos recursos da assinatura.
- **Azure Active Directory** (AD do Azure): o serviço de gerenciamento de identidade e acesso baseado em nuvem da Microsoft. O Azure AD permite que seus funcionários entrem e acessem recursos.
- **Locatário do Azure ad**: uma instância dedicada e confiável do Azure AD. Um locatário do Azure AD é criado automaticamente quando sua organização se inscreve pela primeira vez para uma assinatura do serviço de nuvem da Microsoft como Microsoft Azure, Microsoft Intune ou Office 365. Um locatário do Azure representa uma única organização.
- **Diretório do AD do Azure**: cada locatário do Azure ad tem um diretório único, dedicado e confiável. O diretório inclui os usuários, grupos e aplicativos do locatário. O diretório é usado para executar funções de gerenciamento de acesso e identidade para recursos de locatário. Um diretório pode ser associado a várias assinaturas, mas cada assinatura é associada a apenas um diretório.
- **Grupos de recursos**: contêineres lógicos que você usa para agrupar recursos relacionados em uma assinatura. Cada recurso pode existir em apenas um grupo de recursos.
- **Grupos de gerenciamento**: contêineres lógicos que você usa para uma ou mais assinaturas. Você pode definir uma hierarquia de grupos de gerenciamento, assinaturas, grupos de recursos e recursos para gerenciar com eficiência o acesso, as políticas e a conformidade por meio de herança.
- **Região**: um conjunto de data centers do Azure que são implantados dentro de um perímetro definido por latência. Os data centers são conectados por meio de uma rede dedicada, regional e de baixa latência. A maioria dos recursos do Azure é executada em uma região específica do Azure.

## <a name="azure-subscription-purposes"></a>Propósitos de assinatura do Azure

Uma assinatura do Azure atende a várias finalidades. Uma assinatura do Azure é:

- **Um contrato legal**. Cada assinatura é associada a uma [oferta do Azure](https://azure.microsoft.com/support/legal/offer-details) (como uma avaliação gratuita ou paga conforme o uso). Cada oferta tem um plano de taxa, benefícios e termos e condições associados específicos. Você escolhe uma oferta do Azure ao criar uma assinatura.
- **Um contrato de pagamento**. Ao criar uma assinatura, você fornece informações de pagamento para essa assinatura, como um número de cartão de crédito. Todos os meses, os custos incorridos pelos recursos implantados nessa assinatura são calculados e cobrados por meio desse método de pagamento.
- **Um limite de escala**. Os limites de escala são definidos para uma assinatura. Os recursos da assinatura não podem exceder os limites de escala definidos. Por exemplo, há um limite no número de máquinas virtuais que você pode criar em uma única assinatura.
- **Um limite administrativo**. Uma assinatura pode atuar como um limite para administração, segurança e política. O Azure também fornece outros mecanismos para atender a essas necessidades, como grupos de gerenciamento, grupos de recursos e controle de acesso baseado em função.

## <a name="azure-subscription-considerations"></a>Considerações sobre a assinatura do Azure

Ao criar uma assinatura do Azure, você faz várias opções importantes sobre a assinatura:

- **Quem é responsável por pagar pela assinatura?** A parte associada ao endereço de email que você fornece ao criar uma assinatura por padrão é o administrador da conta da assinatura. A parte associada a esse endereço de email é responsável por pagar por todos os custos incorridos pelos recursos da assinatura.
- **Em qual oferta do Azure eu estou interessado?** Cada assinatura é associada a uma [oferta específica do Azure](https://azure.microsoft.com/support/legal/offer-details). Você pode escolher a oferta do Azure que melhor atenda às suas necessidades. Por exemplo, se você pretende usar uma assinatura para executar cargas de trabalho de não produção, você pode escolher a oferta de Desenvolvimento/Teste Pago Conforme o Uso ou a oferta de Desenvolvimento/Teste Enterprise.

> [!NOTE]
> Ao se inscrever no Azure, você poderá ver a frase *criar uma conta do Azure*. Você cria uma conta do Azure ao criar uma assinatura do Azure e associar a assinatura a uma conta de email.

## <a name="azure-administrative-roles"></a>Funções administrativas do Azure

O Azure define três tipos de funções para administrar assinaturas, identidades e recursos:

- Funções de administrador de assinatura clássica
- Funções de RBAC (controle de acesso baseado em função) do Azure
- Funções de administrador do Azure Active Directory (AD do Azure)

A função de administrador de conta para uma assinatura do Azure é atribuída à conta de email usada para criar a assinatura do Azure. O administrador da conta é o proprietário da cobrança da assinatura. O administrador da conta pode gerenciar os detalhes da assinatura no [centro de contas do Azure](https://account.azure.com/Subscriptions).

Por padrão, a função de administrador de serviços para uma assinatura também é atribuída à conta de email usada para criar a assinatura do Azure. O administrador de serviços tem permissões para a assinatura equivalente à função de proprietário baseada em RBAC. O administrador de serviços também tem acesso completo ao portal do Azure. O administrador da conta pode alterar o administrador de serviços para uma conta de email diferente.

Ao criar uma assinatura do Azure, você pode associá-la a um locatário existente do Azure AD. Caso contrário, um novo locatário do Azure AD com um diretório associado será criado. A função de administrador global no diretório do Azure AD é atribuída à conta de email usada para criar a assinatura do Azure AD.

Uma conta de email pode ser associada a várias assinaturas do Azure. O administrador da conta pode transferir uma assinatura para outra conta.

Para obter uma descrição detalhada das funções definidas no Azure, consulte [funções de administrador da assinatura clássica, funções do RBAC do Azure e funções de administrador do Azure ad](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles).

## <a name="subscriptions-and-regions"></a>Assinaturas e regiões

Cada recurso do Azure é logicamente associado a apenas uma assinatura. Ao criar um recurso, você escolhe a assinatura do Azure para a qual o recurso será implantado. Você pode mover um recurso para outra assinatura mais tarde.

Uma assinatura não está vinculada a uma região específica do Azure. No entanto, cada recurso do Azure é implantado em apenas uma região. Você pode ter recursos em várias regiões associadas à mesma assinatura.

> [!NOTE]
> A maioria dos recursos do Azure são implantados em uma região específica. No entanto, determinados tipos de recursos são considerados recursos globais, como as políticas que você define usando os serviços de Azure Policy.

## <a name="related-resources"></a>Recursos relacionados

Os recursos a seguir fornecem informações detalhadas sobre os conceitos discutidos neste artigo:

- [Como funciona o Azure?](../../getting-started/what-is-azure.md)
- [Gerenciamento de acesso a recursos no Azure](../../govern/resource-consistency/resource-access-management.md)
- [Visão geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)
- [RBAC (controle de acesso baseado em função) para recursos do Azure](https://docs.microsoft.com/azure/role-based-access-control/overview)
- [O que é o Active Directory do Azure?](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis)
- [Associar ou adicionar uma assinatura do Azure ao seu locatário Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)
- [Topologias para o Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies)
- [Assinaturas, licenças, contas e locatários para ofertas de nuvem da Microsoft](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings)

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu conceitos fundamentais do Azure, saiba como [dimensionar com várias assinaturas do Azure](./scaling-subscriptions.md).

> [!div class="nextstepaction"]
> [Dimensionar com várias assinaturas do Azure](./scaling-subscriptions.md)
