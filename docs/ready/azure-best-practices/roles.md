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
ms.openlocfilehash: 98f456bf9af0ab5a7533acf9a9d49f445b7fe37b
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224317"
---
# <a name="role-based-access-control"></a>Controle de acesso baseado em função

Direitos e privilégios de acesso baseados em grupo são uma boa prática. Lidar com grupos em vez de usuários individuais simplifica a manutenção de políticas de acesso, fornece gerenciamento de acesso consistente entre equipes e reduz erros de configuração. Atribuir e remover usuários de grupos, conforme apropriado, ajuda a manter os privilégios dos usuários sempre atualizados. O [RBAC (controle de acesso baseado em função)](https://docs.microsoft.com/azure/role-based-access-control/overview) do Azure oferece gerenciamento de acesso refinado para os recursos organizados em torno das funções de usuário.

Para obter uma visão geral das práticas de RBAC recomendadas como parte de uma estratégia de identidade e segurança, confira [Melhores práticas de segurança para controle de acesso e gerenciamento de identidades do Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices#use-role-based-access-control).

## <a name="overview-of-role-based-access-control"></a>Visão geral do controle de acesso baseado em função

Ao usar o [controle de acesso baseado em função](https://docs.microsoft.com/azure/role-based-access-control/overview), você pode separar as tarefas dentro da sua equipe e conceder apenas o acesso suficiente para que atores específicos do Azure AD (Azure Active Directory) – como usuários, grupos, entidades de serviço ou identidades gerenciadas – executem seus trabalhos. Em vez de conceder a todos acesso irrestrito à assinatura ou aos recursos do Azure, você pode limitar as permissões para cada conjunto de recursos.

As [definições de função do RBAC](https://docs.microsoft.com/azure/role-based-access-control/role-definitions) listam as operações que são permitidas ou não aos usuários ou grupos a quem cada função foi atribuída. O [escopo](/azure/role-based-access-control/index#scope) de uma função especifica a quais recursos as permissões definidas se aplicam. O escopo pode ser especificado em vários níveis: grupo de gerenciamento, assinatura, grupo de recursos ou recursos. Os escopos são estruturados em uma relação pai/filho.

![Hierarquia de escopo do RBAC](../../_images/azure-best-practices/rbac-scope.png)

Para obter instruções detalhadas sobre como atribuir funções específicas a usuários e grupos e como atribuir escopos às funções, confira [Gerenciar o acesso aos recursos do Azure usando o RBAC](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal).

Ao planejar sua estratégia de controle de acesso, use um modelo de acesso com privilégios mínimos que conceda aos usuários somente as permissões necessárias para executar seu trabalho. O diagrama a seguir mostra um padrão sugerido para o uso do RBAC por meio dessa abordagem.

![Padrão sugerido para usar o RBAC](../../_images/azure-best-practices/rbac-least-privilege.png)

> [!NOTE]
> Quanto mais específicas ou detalhadas forem as permissões definidas, maior será a probabilidade de que seus controles de acesso se tornem complexos e difíceis de gerenciar. A probabilidade de que isso seja verdadeiro aumenta à medida que a propriedade digital da sua nuvem cresce de tamanho. Evite permissões específicas para cada recurso. Em vez disso, [use grupos de gerenciamento](https://docs.microsoft.com/azure/governance/management-groups) para controle de acesso no âmbito de toda a empresa e [grupos de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) para controle de acesso no âmbito de assinaturas. Evite também permissões específicas para cada usuário. Em vez disso, atribua acesso a [grupos do Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups).

## <a name="using-built-in-rbac-roles"></a>Como usar funções internas do RBAC

O Azure fornece várias definições de funções internas, com três funções principais para fornecer acesso:

- A função de [Proprietário](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner) pode gerenciar tudo, inclusive o acesso aos recursos.
- A função de [Colaborador](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) pode gerenciar tudo, exceto o acesso aos recursos.
- A função de [Leitor](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader) pode exibir tudo, mas não fazer alterações.

Desses níveis de acesso principais em diante, funções internas adicionais fornecem controles mais detalhados para acessar tipos de recursos específicos ou recursos do Azure. Por exemplo, você pode gerenciar o acesso a máquinas virtuais usando as seguintes funções internas:

- A função de [logon de Administrador de Máquina Virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-administrator-login) permite exibir as máquinas virtuais do portal e entrar como _administrador_.
- A função de [Colaborador de Máquina Virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-contributor) pode gerenciar as máquinas virtuais, mas não pode acessar elas e nem a rede virtual ou a conta de armazenamento às quais elas estão conectadas.
- A função de [logon de Usuário de Máquina Virtual](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#virtual-machine-user-login) permite exibir as máquinas virtuais do portal e entrar como um usuário regular.

Para outro exemplo de como usar as funções internas para gerenciar o acesso a recursos específicos, confira a discussão sobre como controlar o acesso a recursos de acompanhamento de custos em [Como acompanhar os custos em unidades de negócios, ambientes ou projetos](./track-costs.md#provide-the-right-level-of-cost-access).

Para obter uma lista completa das funções internas disponíveis, confira [Funções internas para recursos do Azure](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles).

## <a name="using-custom-roles"></a>Como usar funções personalizadas

Embora as funções internas do Azure sejam compatíveis com uma ampla variedade de cenários de controle de acesso, elas podem não atender a todas as necessidades de sua organização ou equipe. Por exemplo, se você tiver um único grupo de usuários responsável por gerenciar máquinas virtuais e recursos do Banco de Dados SQL do Azure, talvez queira criar uma função personalizada para otimizar o gerenciamento dos controles de acesso necessários.

A documentação do RBAC do Azure contém instruções sobre [como criar funções personalizadas](https://docs.microsoft.com/azure/role-based-access-control/custom-roles), juntamente com detalhes sobre [como funcionam as definições de função](https://docs.microsoft.com/azure/role-based-access-control/role-definitions).

## <a name="separation-of-responsibilities-and-roles-for-large-organizations"></a>Separação de responsabilidades e funções para organizações de grande porte

O RBAC permite que as organizações atribuam várias tarefas de gerenciamento a diferentes equipes dentro de grandes propriedades digitais de nuvem. Ele pode permitir que as equipes centrais de TI controlem os principais recursos de acesso e segurança, além de fornecer aos desenvolvedores de software e a outras equipes grandes quantidades de controle sobre cargas de trabalho ou grupos de recursos específicos.

A maioria dos ambientes de nuvem também pode se beneficiar de uma estratégia de controle de acesso que use várias funções e enfatize uma separação de responsabilidades entre essas funções. Essa abordagem exige que todas as alterações significativas nos recursos ou na infraestrutura envolvam várias funções para serem concluídas, designando mais de uma pessoa para analisar e aprovar cada alteração. Essa separação de responsabilidades limita a capacidade de uma única pessoa acessar dados confidenciais ou introduzir vulnerabilidades sem o conhecimento de outros membros da equipe.

A tabela a seguir ilustra um padrão comum para dividir as responsabilidades de TI em funções personalizadas separadas:

<!-- markdownlint-disable MD033 -->

| Grupo | Nome da função comum | Responsabilidades |
| --- | --- | --- |
| Operações de segurança | SecOps | Fornece supervisão geral de segurança.<br/><br/> Estabelece e impõe a política de segurança, como a criptografia em repouso.<br/><br/> Gerencia as chaves de criptografia.<br/><br/> Gerencia as regras de firewall. |
| Operações de rede | NetOps | Gerencia a configuração e as operações de rede em redes virtuais, como rotas e emparelhamentos. |
| Operações de sistema | SysOps | Especifica as opções de infraestrutura de armazenamento e computação e mantém os recursos que foram implantados. |
| Desenvolvimento, teste e operações | DevOps | Compila e implanta recursos e aplicativos de carga de trabalho.<br/><br/> Opera recursos e aplicativos para atender aos SLAs (contratos de nível de serviço) e a outros padrões de qualidade. |

<!-- markdownlint-enable MD033 -->

O detalhamento de ações e permissões nessas funções padrão é geralmente o mesmo nos aplicativos, nas assinaturas ou em toda a propriedade digital de nuvem, mesmo que essas funções sejam executadas por pessoas diferentes em diferentes níveis. Da mesma forma, você pode criar um conjunto comum de definições de função do RBAC para aplicar em diferentes escopos do seu ambiente. Então uma função comum poderá ser atribuída aos usuários e grupos, mas apenas para o escopo de recursos, grupos de recursos, assinaturas ou grupos de gerenciamento que eles forem responsáveis por gerenciar.

Por exemplo, em uma [configuração de rede hub e spoke](./hub-spoke-network-topology.md) com várias assinaturas, você pode ter um conjunto comum de definições de função para o hub e todos os spokes de carga de trabalho. A função NetOps de uma assinatura de hub pode ser atribuída aos membros da equipe central de TI da organização, que são responsáveis por manter a rede de serviços compartilhados usada por todas as cargas de trabalho. Uma função NetOps da assinatura do spoke da carga de trabalho pode ser atribuída aos membros de equipe dessa carga de trabalho específica, permitindo que eles configurem a rede nessa assinatura para dar melhor suporte aos seus requisitos de carga de trabalho. A mesma definição de função é usada para ambas, mas as atribuições baseadas em escopo garantem que os usuários tenham apenas o acesso de que realmente precisam para executar seu trabalho.
