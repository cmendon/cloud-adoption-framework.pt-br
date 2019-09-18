---
title: Organizar seus recursos do Azure com eficácia
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhores práticas para organizar de forma eficaz os recursos do Azure para facilitar o gerenciamento.
author: laraaleite
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 19299c5855600524f3335b00272974790d83c8fa
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022765"
---
# <a name="organize-your-azure-resources"></a>Organizar seus recursos do Azure

Use as seguintes funcionalidades e as melhores práticas para proteger os recursos que são críticos para o seu sistema. Marca recursos para que possam ser rastreados por meio dos valores adequados à sua organização.

<!-- markdownlint-disable MD024 MD025 -->

# <a name="azure-management-groups-and-hierarchytabazuremanagmentgroupsandhierarchy"></a>[Hierarquia e grupos de gerenciamento do Azure](#tab/AzureManagmentGroupsAndHierarchy)

A estrutura de organização para os recursos no Azure tem quatro níveis: grupos de gerenciamento, assinaturas, grupos de recursos e recursos. A imagem a seguir mostra a relação de um desses níveis.

![Diagrama que mostra a relação da hierarquia de gerenciamento](./media/organize-resources/scope-levels.png)

- **Grupos de gerenciamento:** São contêineres que o ajudarão a gerenciar o acesso, a política e a conformidade para várias assinaturas. Todas as assinaturas em um grupo de gerenciamento herdam automaticamente as condições aplicadas ao grupo de gerenciamento.
- **Assinaturas:** Uma assinatura agrupa contas de usuários e os recursos que foram criados pelas contas de usuários. Para cada assinatura, há limites ou cotas na quantidade de recursos que você pode criar e usar. As organizações podem usar assinaturas para gerenciar os custos e os recursos criados por usuários, equipes ou projetos.
- **Grupos de recursos:** Um grupo de recursos é um contêiner lógico no qual os recursos do Azure, como aplicativos Web, bancos de dados e contas de armazenamento, são implantados e gerenciados.
- **Recursos:** Os recursos são instâncias dos serviços que você cria, como máquinas virtuais, armazenamento ou bancos de dados SQL.

## <a name="scope-of-management-settings"></a>Escopo das configurações de gerenciamento

Você pode aplicar configurações de gerenciamento, como políticas e controles de acesso baseados em função, em qualquer um dos níveis de gerenciamento. O nível que você seleciona determina o quão amplamente a configuração é aplicada. Os níveis inferiores herdam as configurações de níveis superiores. Por exemplo, quando você aplica uma política a uma assinatura, essa política também é aplicada a todos os grupos de recursos e recursos naquela assinatura.

Normalmente, é adequado aplicar configurações críticas em níveis superiores e requisitos específicos do projeto em níveis inferiores. Por exemplo, você pode querer garantir que todos os recursos para sua organização sejam implantados em determinadas regiões. Para fazer isso, aplique uma política à assinatura que especifique os locais permitidos. Na medida em que outros usuários em sua organização adicionarem novos recursos e grupos de recursos, as localizações permitidas serão aplicadas automaticamente. Saiba mais sobre as políticas na seção de governança, segurança e conformidade deste guia.

Ao planejar sua estratégia de conformidade, recomendamos que você trabalhe com pessoas em sua organização com as seguintes funções: segurança e conformidade, administração de TI, arquiteto corporativo, redes, finanças e compras.

::: zone target="docs"

## <a name="create-a-management-level"></a>Criar um grupo de gerenciamento

Você pode criar um grupo de gerenciamento, assinaturas adicionais ou grupos de recursos.

### <a name="create-management-group"></a>Criar grupo de gerenciamento

Crie um grupo de gerenciamento para ajudá-lo a gerenciar o acesso, a política e a conformidade para várias assinaturas.

1. Acesse [Grupos de Gerenciamento](https://portal.azure.com/#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade).
2. Selecione **Adicionar grupo de gerenciamento**.

### <a name="create-subscription"></a>Criar assinatura

Use as assinaturas para gerenciar os custos e os recursos criados por usuários, equipes ou projetos.

1. Vá para [Assinaturas](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
1. Selecione **Adicionar**.

### <a name="create-resource-group"></a>Criar grupo de recursos

Crie um grupo de recursos para armazenar recursos como aplicativos Web, bancos de dados e contas de armazenamento que compartilham o mesmo ciclo de vida, permissões e políticas.

1. Vá para [Grupos de Recursos](https://portal.azure.com/#create/Microsoft.ResourceGroup).
1. Selecione **Adicionar**.
1. Selecione a **Assinatura** sob a qual você deseja que seu grupo de recursos seja criado.
1. Insira um nome para o **Grupo de recursos**.
1. Selecione uma **Região** para a localização do grupo de recursos.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Noções básicas sobre o gerenciamento de acesso aos recursos no Azure](../../govern/resource-consistency/resource-access-management.md)
- [Organizar seus recursos com grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview)
- [Limites do serviço da assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits)

::: zone-end

::: zone target="chromeless"

## <a name="actions"></a>Ações

**Crie um grupo de gerenciamento:**

Crie um grupo de gerenciamento para ajudá-lo a gerenciar o acesso, a política e a conformidade para várias assinaturas.

1. Acesse **Grupos de gerenciamento**.
1. Selecione **Adicionar grupo de gerenciamento**.

::: form action="OpenBlade[#blade/Microsoft_Azure_ManagementGroups/HierarchyBlade]" submitText="Go to Management groups" :::

**Crie uma assinatura adicional:**

Use as assinaturas para gerenciar os custos e os recursos criados por usuários, equipes ou projetos.

1. Vá para **Assinaturas**.
1. Selecione **Adicionar**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/SubscriptionsBlade]" submitText="Go to Subscriptions" :::

**Crie um grupo de recursos:**

Crie um grupo de recursos para armazenar recursos como aplicativos Web, bancos de dados e contas de armazenamento que compartilham o mesmo ciclo de vida, permissões e políticas.

1. Vá para **Grupos de Recursos**.
1. Selecione **Adicionar**.
1. Selecione a **Assinatura** sob a qual você deseja que seu grupo de recursos seja criado.
1. Insira um nome para o **Grupo de recursos**.
1. Selecione uma **Região** para a localização do grupo de recursos.

::: form action="Create[#create/Microsoft.ResourceGroup]" submitText="Create a resource group" :::

::: zone-end

# <a name="naming-standardstabnamingstandards"></a>[Padrões de nomenclatura](#tab/NamingStandards)

Um bom padrão de nomenclatura ajuda a identificar recursos no portal, em uma fatura e nos scripts. Talvez você já tenha padrões de nomenclatura para sua infraestrutura local. Ao adicionar o Azure ao seu ambiente, você deve estender esses padrões de nomenclatura para os recursos do Azure. Os padrões de nomenclatura ajudam você a gerenciar seu ambiente com mais eficiência em todos os níveis. Você pode usar o Azure Policy como uma ferramenta para impor padrões de nomenclatura em todo o seu ambiente do Azure.

::: zone target="docs"

Recomendamos que você revise e adote as [Diretrizes de Padrões e Práticas](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions).

>[!TIP]
>Evite usar caracteres especiais (`-` ou `_`) como o primeiro ou último caractere em qualquer nome. Esses caracteres fazem com que a maioria das regras de validação falhe.

::: zone-end

| Entidade | Escopo | Comprimento | Capitalização | Caracteres válidos | Padrão sugerido | Exemplo |
| --- | --- | --- | --- | --- | --- | --- |
|Resource group |Subscription |1-90 |Não diferencia maiúsculas de minúsculas |Alfanumérico, sublinhado, parênteses, hífen, um período (exceto no final) e caracteres Unicode |`<service short name>-<environment>-rg` |`profx-prod-rg` |
|Conjunto de disponibilidade |Resource group |1-80 |Não diferencia maiúsculas de minúsculas |Alfanumérico, sublinhado e hífen |`<service-short-name>-<context>-as` |`profx-sql-as` |
|Marca |Entidade associada |512 (nome), 256 (valor) |Não diferencia maiúsculas de minúsculas |Alfanumérico |`"key" : "value"` |`"department" : "Central IT"` |

# <a name="resource-tagstabresourcetags"></a>[Marcações de recursos](#tab/ResourceTags)

As marcas são úteis para identificar rapidamente os seus recursos e grupos de recursos. Você pode aplicar marcas para os recursos do Azure para organizá-los logicamente por categorias. Cada marca consiste em um nome e em um valor. Por exemplo, você pode aplicar o nome "Ambiente" e o valor "Produção" a todos os recursos na produção.

Depois de aplicar marcas, você pode recuperar todos os recursos em sua assinatura com esse nome e valor de marca. As marcas permitem que você recupere recursos relacionados de diferentes grupos de recursos, o que é útil para organizar recursos para gerenciamento ou cobrança.

Você também pode usar marcas para muitos outros fins. Usos comuns incluem:

- **Metadados e documentação:** Os administradores podem facilmente ver os detalhes sobre os recursos com os quais estão trabalhando ao aplicar uma marca, como "ProjectOwner".
- **Automação:** talvez você tenha scripts que são executados regularmente que podem realizar uma ação com base em um valor de marca, como "ShutdownTime" ou "DeprovisionDate".
- **Cobrança:** as marcas podem aparecer na sua fatura. Você pode usá-las para ajudar a segmentar sua fatura, como "CostCenter" ou "BillTo".

Cada recurso ou grupo de recursos pode ter um máximo de 15 pares de nome/valor de marca. Porém, essa limitação se aplica somente a marcas aplicadas diretamente ao grupo de recursos ou recurso.

Para obter mais informações sobre marcação, confira [Convenções de nomenclatura para recursos do Azure no Centro de Arquitetura do Azure](../../ready/considerations/naming-and-tagging.md#metadata-tags)

::: zone target="docs"

## <a name="apply-a-resource-tag"></a>Aplicar uma marca de recurso

Para aplicar uma marca a um grupo de recursos:

1. Vá para [Grupos de recursos](https://portal.azure.com/#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups).
1. Selecione um grupo de recursos.
1. Selecionar **Marcas**.
1. Insira um novo nome e valor ou use a lista suspensa para selecionar um nome e valor existentes.

## <a name="learn-more"></a>Saiba mais

Para saber mais, veja [Usar marcas para organizar os recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

::: zone-end

::: zone target="chromeless"

## <a name="action"></a>Ação

**Aplicar uma tag de recurso:**

Para aplicar uma marca a um grupo de recursos:

1. Vá para **Grupos de recursos**.
1. Selecione um grupo de recursos.
1. Selecionar **Marcas**.
1. Insira um novo nome e valor ou selecione um nome e valor existente.

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Resources%2Fsubscriptions%2FresourceGroups]" submitText="Go to resource groups" :::

::: zone-end
