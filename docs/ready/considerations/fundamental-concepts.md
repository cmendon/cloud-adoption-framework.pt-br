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
ms.openlocfilehash: 8f1d622401eff58710e016b690292e81d9b7f1d7
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905280"
---
# <a name="azure-fundamental-concepts"></a>Conceitos fundamentais do Azure

Aprenda conceitos e termos fundamentais que são usados no Azure e como os conceitos se relacionam entre si.

## <a name="azure-terminology"></a>Terminologia do Azure

É útil conhecer as seguintes definições ao começar seus esforços de adesão à nuvem do Azure:

- **Recurso**: Uma entidade que é gerenciada pelo Azure. Os exemplos incluem máquinas virtuais do Azure, redes virtuais e contas de armazenamento.
- **Assinatura**: Um contêiner lógico para seus recursos. Cada recurso do Azure é associado a apenas uma assinatura. A criação de uma assinatura é a primeira etapa na adoção do Azure.
- **Conta do Azure**: O endereço de email que você fornece ao criar uma assinatura do Azure é a conta do Azure para a assinatura. A parte que está associada à conta de email é responsável pelos custos mensais incorridos pelos recursos na assinatura. Ao criar uma conta do Azure, você fornece informações de contato e detalhes de cobrança, como um cartão de crédito. Você pode usar a mesma conta do Azure (endereço de email) para várias assinaturas. Cada assinatura é associada a apenas uma conta do Azure.
- **Administrador da conta**: A parte associada ao endereço de email usado para criar uma assinatura do Azure. O administrador da conta é responsável por pagar por todos os custos incorridos pelos recursos da assinatura.
- **Azure AD** (Azure Active Directory): O serviço de gerenciamento de acesso e identidade baseado em nuvem da Microsoft. O Azure AD permite que seus funcionários entrem e acessem recursos.
- **Locatário do Azure AD**: Uma instância dedicada e confiável do Azure AD. Um locatário do Azure AD é automaticamente criado quando sua organização se inscreve pela primeira vez em uma assinatura de serviço de nuvem da Microsoft, como o Microsoft Azure, o Microsoft Intune ou o Office 365. Um locatário do Azure representa uma única organização.
- **Diretório do Azure AD**: Cada locatário do Azure AD tem um diretório único, dedicado e confiável. O diretório inclui os usuários, grupos e aplicativos do locatário. O diretório é usado para realizar as funções de gerenciamento de acesso e identidade para recursos de locatário. Um diretório pode ser associado a várias assinaturas, mas cada assinatura é associada a apenas um diretório.
- **Grupos de recursos**: Contêineres lógicos que você usa para agrupar recursos relacionados em uma assinatura. Cada recurso pode existir apenas em um grupo de recursos.
- **Grupos de gerenciamento**: Contêineres lógicos que você usa para uma ou mais assinaturas. Você pode definir uma hierarquia de grupos de gerenciamento, assinaturas, grupos de recursos e recursos para gerenciar com eficiência o acesso, as políticas e a conformidade por meio de herança.
- **Região**: Um conjunto de datacenters do Azure que são implantados dentro de um perímetro definido por latência. Os datacenters são conectados por meio de uma rede dedicada, regional de baixa latência. A maioria dos recursos do Azure é executada em uma região específica do Azure.

## <a name="azure-subscription-purposes"></a>Finalidades da assinatura do Azure

Uma assinatura do Azure atende a várias finalidades. Uma assinatura do Azure é:

- **Um contrato legal**. Cada assinatura é associada a uma [oferta do Azure](https://azure.microsoft.com/support/legal/offer-details) (como uma avaliação gratuita ou Pagamento Conforme o Uso). Cada oferta tem plano de taxa, benefícios e termos e condições específicos associados. Você escolhe uma oferta do Azure ao criar uma assinatura.
- **Um contrato de pagamento**. Ao criar uma assinatura, você fornece informações de pagamento para a assinatura, como um número de cartão de crédito. Todos os meses, os custos incorridos pelos recursos implantados nessa assinatura são calculados e cobrados por meio dessa forma de pagamento.
- **Um limite de escala**. Limites de escala são definidos para uma assinatura. Os recursos da assinatura não podem exceder os limites de escala definidos. Por exemplo, há um limite no número de máquinas virtuais que você pode criar em uma assinatura única.
- **Um limite administrativo**. Uma assinatura serve como um limite para administração, segurança e política. O Azure também fornece outros mecanismos para atender a essas necessidades, como grupos de gerenciamento, grupos de recursos e controle de acesso baseado em função.

## <a name="azure-subscription-considerations"></a>Considerações sobre a assinatura do Azure

Ao criar uma assinatura do Azure, você faz várias opções importantes sobre a assinatura:

- **Quem é responsável por pagar pela assinatura?** A parte associada ao endereço de email que você fornece ao criar uma assinatura por padrão, é o administrador da conta da assinatura. A parte associada com esse endereço de email é responsável por pagar por todos os custos incorridos pelos recursos da assinatura.
- **Em qual oferta do Azure eu estou interessado?** Cada assinatura é associada a uma [oferta do Azure](https://azure.microsoft.com/support/legal/offer-details) específica. Você pode escolher a oferta do Azure que melhor atenda às suas necessidades. Por exemplo, se você pretende usar uma assinatura para executar cargas de trabalho de não produção, você pode escolher a oferta de Desenvolvimento/Teste Pago Conforme o Uso ou a oferta de Desenvolvimento/Teste Enterprise.

> [!NOTE]
> Ao se inscrever no Azure, você poderá ver a frase *criar uma conta do Azure*. Você cria uma conta do Azure ao criar uma assinatura do Azure e associar a assinatura a uma conta de email.

## <a name="azure-administrative-roles"></a>Funções administrativas do Azure

O Azure define três tipos de funções para administrar assinaturas, identidades e recursos:

- Funções de administrador da assinatura clássica
- Funções do Azure RBAC (Controle de Acesso Baseado em Função)
- Funções de administrador do Azure AD (Azure Active Directory)

A função de administrador da conta para uma assinatura do Azure é atribuída à conta de email usada para criar a assinatura do Azure. O administrador da conta é o proprietário da cobrança da assinatura. O administrador da conta pode gerenciar os detalhes da assinatura no [Centro de Contas do Azure](https://account.azure.com/Subscriptions).

Por padrão, a função de administrador de serviços de uma assinatura também é atribuída à conta de email usada para criar a assinatura do Azure. O administrador de serviços tem permissões para a assinatura equivalente à função de Proprietário baseada em RBAC. O administrador de serviços também tem acesso completo ao portal do Azure. O administrador da conta pode alterar o administrador de serviços para uma conta de email diferente.

Ao criar uma assinatura do Azure, você pode associá-la a um locatário existente do Azure AD. Caso contrário, um novo locatário do Azure AD com um diretório associado será criado. A função de Administrador Global no diretório do Azure AD é atribuída à conta de email usada para criar a assinatura do Azure AD.

Uma conta de email pode ser associada a várias assinaturas do Azure. O administrador da conta pode transferir uma assinatura para outra conta.

Para uma descrição detalhada das funções definidas no Azure, confira [Funções de administrador da assinatura clássica, funções RBAC do Azure e funções de administrador do Azure AD](/azure/role-based-access-control/rbac-and-directory-admin-roles).

## <a name="subscriptions-and-regions"></a>Assinaturas e regiões

Todo recurso do Azure é associado logicamente a apenas uma assinatura. Ao criar um recurso, você escolhe a assinatura do Azure para a qual o recurso será implantado. Você pode mover um recurso para outra assinatura mais tarde.

Uma assinatura não é vinculada a uma região específica do Azure. No entanto, cada recurso do Azure é implantado em apenas uma região. Você pode ter recursos em várias regiões associados à mesma assinatura.

> [!NOTE]
> A maioria dos recursos do Azure são implantados em uma região específica. No entanto, determinados tipos de recursos são considerados recursos globais, como as políticas que você define usando os serviços do Azure Policy.

## <a name="related-resources"></a>Recursos relacionados

Os recursos a seguir fornecem informações detalhadas sobre os conceitos discutidos neste artigo:

- [Como funciona o Azure?](/azure/architecture/cloud-adoption/getting-started/what-is-azure)
- [Gerenciamento de acesso aos recursos no Azure](../../governance/resource-consistency/azure-resource-access.md)
- [Visão geral do Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)
- [RBAC (Controle de acesso baseado em função) para recursos do Azure](/azure/role-based-access-control/overview)
- [O que é o Active Directory do Azure?](/azure/active-directory/fundamentals/active-directory-whatis)
- [Associar ou adicionar uma assinatura do Azure ao seu locatário do Azure Active Directory](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)
- [Topologias para o Azure AD Connect](/azure/active-directory/hybrid/plan-connect-topologies)
- [Assinaturas, licenças, contas e locatários para ofertas de nuvem da Microsoft](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings)

## <a name="next-steps"></a>Próximas etapas

Agora que você entendeu conceitos fundamentais do Azure, saiba como [dimensionar com várias assinaturas do Azure](./scaling-subscriptions.md).

> [!div class="nextstepaction"]
> [Dimensionar com várias assinaturas do Azure](./scaling-subscriptions.md)
