---
title: Design de governança para uma carga de trabalho simples
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Diretrizes para configurar os controles de governança do Azure para permitir que um usuário implante uma carga de trabalho simples.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9a64a069dcebb12cf550f697561b76903e6d01bf
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967355"
---
# <a name="governance-design-for-a-simple-workload"></a>Design de governança para uma carga de trabalho simples

A meta deste guia é ajudar você a aprender o processo para criar um modelo de controle de recursos no Azure para dar suporte a uma única equipe e a uma carga de trabalho simples. Iremos examinar um conjunto de requisitos de governança hipotético e passar por várias implementações de exemplo que atendem a esses requisitos.

No estágio básico de adoção, nossa meta é implantar uma carga de trabalho simples no Azure. Isso resulta nos seguintes requisitos:

- Gerenciamento de identidade para um único **proprietário de carga de trabalho**, que é responsável por implantar e manter a carga de trabalho simples. O proprietário da carga de trabalho exige permissão para criar, ler, atualizar e excluir recursos, bem como permissão para delegar esses direitos a outros usuários no sistema de gerenciamento de identidade.
- Gerencie todos os recursos para a carga de trabalho simples como uma unidade única de gerenciamento.

## <a name="licensing-azure"></a>Licenciamento do Azure

Antes de começarmos a criação de nosso modelo de governança, é importante entender como o Azure é licenciado. Isso ocorre porque as contas administrativas associadas à sua licença do Azure têm o nível mais alto de acesso aos recursos do Azure. Essas contas administrativas formam a base do seu modelo de governança.

> [!NOTE]
> Se sua organização tiver um [Microsoft Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx) existente que não inclui o Azure, este pode ser adicionado mediante uma confirmação de pagamento adiantado. Consulte [licenciamento do Azure para a empresa](https://azure.microsoft.com/pricing/enterprise-agreement) para obter mais informações.

Quando o Azure foi adicionado ao Enterprise Agreement de sua organização, foi solicitada a criação de uma **conta do Azure**. Durante o processo de criação da conta, um **proprietário da conta do Azure** foi criado, bem como um locatário do Azure Active Directory (Azure AD) com uma conta de **administrador global**. Um locatário do Azure AD é um constructo lógico que representa uma instância segura e dedicada do Azure AD.

conta do ![Azure com o Gerenciador de contas do Azure e o administrador global do Azure AD @ no__t-1*Figura 1-uma conta do Azure com um gerente de conta e um administrador global do Azure AD.*

## <a name="identity-management"></a>Gerenciamento de identidades

Somente o Azure confia no [Azure AD](https://docs.microsoft.com/azure/active-directory) para autenticar usuários e autorizar o acesso de usuários a recursos, por isso, o Azure AD é o nosso sistema de gerenciamento de identidade. O administrador global do Azure AD tem o nível mais alto de permissões e pode executar todas as ações relacionadas à identidade, incluindo a criação de usuários e a atribuição de permissões.

Nosso requisito é o gerenciamento de identidade para um único **proprietário de carga de trabalho**, que é responsável por implantar e manter a carga de trabalho simples. O proprietário da carga de trabalho exige permissão para criar, ler, atualizar e excluir recursos, bem como permissão para delegar esses direitos a outros usuários no sistema de gerenciamento de identidade.

Nosso administrador global do Azure AD criará a conta do **proprietário da carga** de trabalho para o proprietário da carga de trabalho:

![The o administrador global do Azure AD cria a conta do proprietário da carga de trabalho @ no__t-1*Figura 2-o administrador global do Azure ad cria a conta de usuário do proprietário da carga de trabalho.*

Não conseguimos atribuir permissão de acesso ao recurso até que esse usuário seja adicionado a uma **assinatura**, portanto, faremos isso nas próximas duas seções.

## <a name="resource-management-scope"></a>Escopo do gerenciamento de recursos

À medida que o número de recursos implantados por sua organização cresce, a complexidade de governar esses recursos também aumenta. O Azure implementa uma hierarquia de contêiner lógico para permitir que sua organização gerencie seus recursos em grupos em vários níveis de granularidade, o que também é conhecido como **escopo**.

O nível superior do escopo de gerenciamento de recursos é o nível de **assinatura**. Uma assinatura é criada pelo **proprietário da conta** do Azure, que estabelece o compromisso financeiro e é responsável pelo pagamento de todos os recursos do Azure associado à assinatura:

![The proprietário da conta do Azure cria uma assinatura @ no__t-1*Figura 3-o proprietário da conta do Azure cria uma assinatura.*

Quando a assinatura é criada, o **proprietário da conta** do Azure associa um locatário do Azure Active Directory com a assinatura e este locatário do Azure AD é usado para autenticar e autorizar usuários:

![The proprietário da conta do Azure associa o locatário do Azure AD à assinatura @ no__t-1*Figura 4-o proprietário da conta do Azure associa o locatário do Azure ad à assinatura.*

Você talvez tenha observado que não há, no momento, nenhum usuário associado à assinatura, o que significa que ninguém tem permissão para gerenciar recursos. Na realidade, o **proprietário da conta** é o proprietário da assinatura e tem permissão para executar qualquer ação em um recurso na assinatura. No entanto, em termos práticos, o **proprietário da conta** é muito provavelmente uma pessoa do departamento financeiro de sua organização e não é responsável por criar, ler, atualizar e excluir recursos - essas tarefas serão executadas pelo **proprietário da carga de trabalho**. Portanto, precisamos adicionar o **proprietário da carga de trabalho** à assinatura e atribuir permissões.

Uma vez que o **proprietário da conta** atualmente é o único usuário com permissão para adicionar o **proprietário da carga de trabalho** à assinatura, eles adicionam o **proprietário da carga de trabalho** à assinatura:

![The proprietário da conta do Azure adiciona o * * proprietário da carga de trabalho * * à assinatura @ no__t-1*Figura 5-o proprietário da conta do Azure adiciona o proprietário da carga de trabalho à assinatura.*

O **proprietário da conta** do Azure concede permissões ao **proprietário da carga de trabalho** atribuindo uma função de [controle de acesso baseado em função (RBAC)](https://docs.microsoft.com/azure/role-based-access-control). A função RBAC especifica um conjunto de permissões que o **proprietário da carga de trabalho** tem para um tipo de recurso individual ou um conjunto de tipos de recursos.

Observe que neste exemplo, o **proprietário da conta** atribuiu a [função de **proprietário** interna](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner):

![The * * proprietário da carga de trabalho * * foi atribuída a função de proprietário interna @ no__t-1*Figura 6-o proprietário da carga de trabalho recebeu a função de proprietário interna.*

A função de **proprietário** interna concede todas as permissões ao **proprietário da carga de trabalho** no escopo da assinatura.

> [!IMPORTANT]
> O **proprietário da conta** do Azure é responsável pelo compromisso financeiro associado à assinatura, mas o **proprietário da carga de trabalho** tem as mesmas permissões. O **proprietário da conta** deve confiar no **proprietário da carga de trabalho** para implantar recursos que estão dentro do orçamento da assinatura.

O próximo nível do escopo de gerenciamento é o nível do **grupo de recursos**. Um grupo de recursos é um contêiner lógico para recursos. Operações aplicadas no nível do grupo de recursos se aplicam a todos os recursos em um grupo. Além disso, é importante observar que as permissões para cada usuário são herdadas do próximo nível para cima, a menos que elas sejam alteradas explicitamente nesse escopo.

Para ilustrar isso, vamos examinar o que acontece quando o **proprietário da carga de trabalho** cria um grupo de recursos:

![The * * proprietário da carga de trabalho * * cria um grupo de recursos @ no__t-1*Figura 7-o proprietário da carga de trabalho cria um grupo de recursos e herda a função de proprietário interna no escopo do grupo de recursos.*

Novamente, a função de **proprietário** interna concede todas as permissões ao **proprietário da carga de trabalho** no escopo do grupo de recursos. Conforme discutido anteriormente, essa função é herdada do nível da assinatura. Se uma função diferente for atribuída a esse usuário nesse escopo, ela se aplicará somente a esse escopo.

O menor nível do escopo de gerenciamento é o nível de **recurso**. Operações aplicadas ao nível de recurso se aplicam somente ao próprio recurso. E, mais uma vez, as permissões no nível de recurso são herdadas do escopo do grupo de recursos. Por exemplo, vejamos o que acontece se o **proprietário da carga de trabalho** implantar uma [rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) no grupo de recursos:

![The * * proprietário da carga de trabalho * * cria um recurso @ no__t-1*Figura 8-o proprietário da carga de trabalho cria um recurso e herda a função de proprietário interna no escopo do recurso.*

O **proprietário da carga de trabalho** herda a função de proprietário no escopo do recurso, o que significa que o proprietário da carga de trabalho tem todas as permissões para a rede virtual.

## <a name="implementing-the-basic-resource-access-management-model"></a>Implementação do modelo de gerenciamento de acesso a recursos básicos

Agora saiba como implementar o modelo de governança criado anteriormente.

Para começar, sua organização exige uma conta do Azure. Se sua organização tiver um [Microsoft Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx) existente que não inclui o Azure, este pode ser adicionado mediante uma confirmação de pagamento adiantado. Consulte [licenciamento do Azure para a empresa](https://azure.microsoft.com/pricing/enterprise-agreement) para obter mais informações.

Ao criar sua conta do Azure, especifique uma pessoa em sua organização para ser o **proprietário da conta** do Azure. Em seguida, um locatário do Azure Active Directory (Azure AD) é criado por padrão. O **proprietário da conta** do Azure deve [criar a conta de usuário](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory) para a pessoa em sua organização que é o **proprietário da carga de trabalho**.

Em seguida, o **proprietário da conta** do Azure deve [criar uma assinatura](https://docs.microsoft.com/partner-center/create-a-new-subscription) e [associar o locatário do Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) a ele.

Por fim, agora que a assinatura está criada e seu locatário do Azure Active Directory está associado a ela, você poderá [adicionar o **proprietário da carga de trabalho** à assinatura com a função de **proprietário** interna](https://docs.microsoft.com/azure/billing/billing-add-change-azure-subscription-administrator#to-assign-a-user-as-an-administrator).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Implantar uma carga de trabalho básica para o Azure](../../infrastructure/virtual-machines/basic-workload.md)
> [!div class="nextstepaction"]
> [Saiba mais sobre o acesso aos recursos para várias equipes](./governance-multiple-teams.md)
