---
title: Controle de acesso baseado em função recomendado
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Controle de acesso baseado em função recomendado
author: rotycenh
ms.author: brblanch
ms.date: 11/28/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: BrianBlanchard
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: d9b51b7bb67a58d3a41818b1c51138c2e1c9c43a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548970"
---
# <a name="role-based-access-control"></a>Controle de acesso baseado em funções

Direitos de acesso baseado em grupo e privilégios são uma boa prática. Lidar com grupos em vez de usuários individuais simplifica a manutenção de políticas de acesso, fornece gerenciamento de acesso consistente entre equipes e reduz erros de configuração. A atribuição de usuários ao e à remoção de usuários dos grupos apropriados ajuda a manter os privilégios atuais de um usuário específico. O [RBAC (controle de acesso baseado em função)](https://docs.microsoft.com/azure/role-based-access-control/overview) do Azure oferece gerenciamento de acesso refinado para recursos organizados em relação às funções de usuário.

Para obter uma visão geral das práticas de RBAC recomendadas como parte de uma estratégia de identidade e segurança, consulte [práticas recomendadas de segurança de controle de acesso e gerenciamento de identidades do Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices#use-role-based-access-control).

## <a name="overview-of-role-based-access-control"></a>Visão geral do controle de acesso baseado em função

Usando o [controle de acesso baseado em função](https://docs.microsoft.com/azure/role-based-access-control/overview), você pode separar as tarefas dentro de sua equipe e conceder apenas acesso suficiente para usuários específicos do Azure Active Directory (Azure AD), grupos, entidades de serviço ou identidades gerenciadas para executar seus trabalhos. Em vez de fornecer a todos acesso irrestrito à sua assinatura ou aos recursos do Azure, você pode limitar as permissões para cada conjunto de recursos.

As [definições de função do RBAC](https://docs.microsoft.com/azure/role-based-access-control/role-definitions) listam operações que são permitidas ou não permitidas para usuários ou grupos atribuídos a essa função. O [escopo](https://docs.microsoft.com/azure/role-based-access-control/overview#scope) de uma função especifica a quais recursos essas permissões definidas se aplicam. Os escopos podem ser especificados em vários níveis: grupo de gerenciamento, assinatura, grupo de recursos ou recurso. Os escopos são estruturados em uma relação pai/filho.

![Hierarquia de escopo do RBAC](../../_images/azure-best-practices/rbac-scope.png)

Para obter instruções detalhadas sobre como atribuir usuários e grupos a funções específicas e atribuir funções a escopos, consulte [gerenciar o acesso aos recursos do Azure usando o RBAC](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal).

Ao planejar sua estratégia de controle de acesso, use um modelo de acesso com privilégios mínimos que concede aos usuários somente as permissões necessárias para executar seu trabalho. O diagrama a seguir mostra um padrão sugerido para usar o RBAC por meio dessa abordagem.

![Padrão sugerido para usar o RBAC](../../_images/azure-best-practices/rbac-least-privilege.png)

> [!NOTE]
> Quanto mais específicas ou as permissões detalhadas forem definidas, maior será a probabilidade de que seus controles de acesso se tornem complexos e difíceis de gerenciar. Isso é especialmente verdadeiro à medida que seu estado de nuvem aumenta em tamanho. Evite permissões específicas do recurso. Em vez disso, [Use grupos de gerenciamento](https://docs.microsoft.com/azure/governance/management-groups) para controle de acesso de toda a empresa e [grupos de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) para controle de acesso em assinaturas. Evite também permissões específicas do usuário. Em vez disso, atribua acesso a [grupos no Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups).

## <a name="using-built-in-rbac-roles"></a>Usando funções RBAC internas

O Azure fornece várias definições de função internas, com três funções principais para fornecer acesso:

- A função de [proprietário](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) pode gerenciar tudo, incluindo o acesso aos recursos.
- A função [colaborador](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) pode gerenciar tudo, exceto o acesso aos recursos.
- A função [leitor](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader) pode exibir tudo, mas não fazer nenhuma alteração.

A partir desses níveis de acesso principal, funções internas adicionais fornecem controles mais detalhados para acessar tipos de recursos específicos ou recursos do Azure. Por exemplo, você pode gerenciar o acesso a máquinas virtuais usando as seguintes funções internas:

- A função de [logon administrador de máquina virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-administrator-login) pode exibir máquinas virtuais no portal e entrar como _administrador_.
- A função [colaborador da máquina virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) pode gerenciar máquinas virtuais, mas não pode acessá-las ou a rede virtual ou a conta de armazenamento à qual estão conectadas.
- A função de [logon de usuário da máquina virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-user-login) pode exibir máquinas virtuais no portal e entrar como um usuário comum.

Para obter outro exemplo de como usar funções internas para gerenciar o acesso a recursos específicos, consulte a discussão sobre como controlar o acesso a recursos de controle de custos no [controle de custos em unidades de negócios, ambientes ou projetos](./track-costs.md#provide-the-right-level-of-cost-access).

Para obter uma lista completa de funções internas disponíveis, consulte [funções internas para recursos do Azure](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles).

## <a name="using-custom-roles"></a>Usando funções personalizadas

Embora as funções criadas no Azure ofereçam suporte a uma ampla variedade de cenários de controle de acesso, elas podem não atender a todas as necessidades de sua organização ou equipe. Por exemplo, se você tiver um único grupo de usuários responsável por gerenciar máquinas virtuais e recursos do banco de dados SQL do Azure, talvez queira criar uma função personalizada para otimizar o gerenciamento dos controles de acesso necessários.

A documentação do RBAC do Azure contém instruções sobre como [criar funções personalizadas](https://docs.microsoft.com/azure/role-based-access-control/custom-roles), juntamente com detalhes sobre [como as definições de função funcionam](https://docs.microsoft.com/azure/role-based-access-control/role-definitions).

## <a name="separation-of-responsibilities-and-roles-for-large-organizations"></a>Separação de responsabilidades e funções para grandes organizações

O RBAC permite que as organizações atribuam diferentes equipes a várias tarefas de gerenciamento dentro de grandes imóveis de nuvem. Ele pode permitir que as equipes de ti central controlem os principais recursos de acesso e segurança, além de fornecer aos desenvolvedores de software e outras equipes grandes quantidades de controle sobre cargas de trabalho ou grupos de recursos específicos.

A maioria dos ambientes de nuvem também pode se beneficiar de uma estratégia de controle de acesso que usa várias funções e enfatiza uma separação de responsabilidades entre essas funções. Essa abordagem requer que todas as alterações significativas nos recursos ou na infraestrutura envolvam várias funções para serem concluídas, garantindo que mais de uma pessoa deva revisar e aprovar uma alteração. Essa separação de responsabilidades limita a capacidade de uma única pessoa acessar dados confidenciais ou introduzir vulnerabilidades sem o conhecimento de outros membros da equipe.

A tabela a seguir ilustra um padrão comum para dividir as responsabilidades de ti em funções personalizadas separadas:

<!-- markdownlint-disable MD033 -->

| Group | Nome de função comum | Consiste |
| --- | --- | --- |
| Operações de segurança | SecOps | Fornece supervisão de segurança geral.<br/><br/> Estabelece e impõe políticas de segurança, como criptografia em repouso.<br/><br/> Gerencia chaves de criptografia.<br/><br/> Gerencia regras de firewall. |
| Operações de rede | NetOps | Gerencia a configuração de rede e as operações em redes virtuais, como rotas e emparelhamentos. |
| Operações de sistemas | SysOps | Especifica opções de infraestrutura de armazenamento e computação e mantém os recursos que foram implantados. |
| Desenvolvimento, teste e operações | Operações de Desenvolvimento | Compila e implanta recursos e aplicativos de carga de trabalho.<br/><br/> O Opera com recursos e aplicativos para atender aos SLAs (contratos de nível de serviço) e a outros padrões de qualidade. |

<!-- markdownlint-enable MD033 -->

A divisão de ações e permissões nessas funções padrão geralmente é a mesma em seus aplicativos, assinaturas ou imóveis de nuvem inteira, mesmo que essas funções sejam executadas por pessoas diferentes em diferentes níveis. Da mesma forma, você pode criar um conjunto comum de definições de função do RBAC para aplicar em escopos diferentes em seu ambiente. Os usuários e grupos podem, então, ser atribuídos a uma função comum, mas apenas para o escopo de recursos, grupos de recursos, assinaturas ou grupos de gerenciamento que são responsáveis por gerenciar.

Por exemplo, em uma [configuração de rede hub e spoke](./hub-spoke-network-topology.md) com várias assinaturas, você pode ter um conjunto comum de definições de função para o Hub e todos os spokes de carga de trabalho. A função NetOps de uma assinatura de Hub pode ser atribuída a membros da equipe de ti central da organização, que são responsáveis por manter a rede para serviços compartilhados usados por todas as cargas de trabalho. Uma função NetOps da assinatura do spoke de carga de trabalho pode ser atribuída a membros dessa equipe de carga de trabalho específica, permitindo que eles configurem a rede nessa assinatura para dar melhor suporte aos seus requisitos de carga de trabalho. A mesma definição de função é usada para ambas, mas atribuições baseadas em escopo garantem que os usuários tenham apenas o acesso de que precisam para executar seu trabalho.
