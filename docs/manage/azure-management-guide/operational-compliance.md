---
title: Conformidade operacional no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Habilite a estabilidade de negócios aumentando a conformidade operacional
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 7073df6b697da49429d4086d9f8f3f113583e52d
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557084"
---
# <a name="operational-compliance-in-azure"></a>Conformidade operacional no Azure

A conformidade operacional é a segunda disciplina em qualquer linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

Melhorar a conformidade operacional reduz a probabilidade de uma interrupção relacionada a um descompasso de configuração ou a vulnerabilidades relacionadas ao fato de os sistemas não serem devidamente corrigidos.

Para qualquer ambiente de nível corporativo, a tabela a seguir descreve o mínimo sugerido para qualquer linha de base de gerenciamento.

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Gerenciamento de patch|Gerenciamento de atualizações|Gerenciamento e agendamento de atualizações|
|Aplicação de políticas|Azure Policy|Aplicação de política para garantir a conformidade do ambiente e do convidado|
|Env. Configuração|Especificações Técnicas do Azure|Conformidade automatizada para os serviços principais|

::: zone target="docs"

## <a name="update-management"></a>Gerenciamento de atualizações

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gerenciamento de atualizações](#tab/UpdateManagement)

::: zone-end

Os computadores que são gerenciados pelo Gerenciamento de Atualizações usam as configurações a seguir para realizar implantações de atualização e avaliação:

- Microsoft Monitoring Agent (MMA) para Windows ou Linux
- DSC (PowerShell Desired State Configuration) para Linux
- Hybrid Runbook Worker de Automação
- Microsoft Update ou Windows Server Update Services (WSUS) para computadores Windows

Para obter mais informações, confira [Solução de Gerenciamento de Atualizações](https://docs.microsoft.com/azure/automation/automation-update-management)

> [!WARNING]
> Antes de usar o gerenciamento de atualizações, você deve integrar VMs ou uma assinatura inteira no Log Analytics e na Automação do Azure.
> Há duas abordagens de integração, uma deve ser seguida antes de prosseguir com o gerenciamento de atualizações.
>
> - [VM individual](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Assinatura inteira](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

### <a name="manage-updates"></a>Gerenciar atualizações

Para aplicar uma política a um grupo de recursos:

1. Acesse [Automação do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
2. Escolha uma das **contas de automação** listadas.
3. Localize a seção **Gerenciamento de Configuração** da navegação do portal.
4. O Inventário, o Gerenciamento de Alterações e o State Configuration podem ser usados para controlar o estado e a conformidade operacional das VMs gerenciadas.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

## <a name="azure-policy"></a>Azure Policy

::: zone-end
::: zone target="chromeless"

## <a name="azure-policytabazurepolicy"></a>[Azure Policy](#tab/AzurePolicy)

::: zone-end

O Azure Policy é usado em todos os processos de governança. Porém, ele também é altamente valioso nos processos de gerenciamento de nuvem. Além de auditar e corrigir os recursos do Azure, o Azure Policy pode auditar configurações dentro de um computador. A validação é executada pela extensão e pelo cliente de Configuração de Convidado. A extensão, por meio do cliente, valida as configurações como:

- Configuração do sistema operacional
- Configuração ou presença do aplicativo
- Configurações do ambiente

Neste momento, a Configuração de Convidado do Azure Policy audita somente as configurações dentro do computador. Ela não aplica configurações.

::: zone target="chromeless"

### <a name="action"></a>Ação

Atribua uma política interna a um grupo de gerenciamento, assinatura ou grupo de recursos.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

### <a name="apply-a-policy"></a>Aplique uma política

Para aplicar uma política a um grupo de recursos:

1. Acesse [Azure Policy](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Selecione **Atribuir uma política**.

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Azure Policy](https://docs.microsoft.com/azure/azure-policy)
- [Azure Policy – Configuração de convidado](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration)
- [Cloud Adoption Framework: guia de decisão para imposição de política](../../decision-guides/policy-enforcement/index.md)

## <a name="azure-blueprints"></a>Azure Blueprints

::: zone-end
::: zone target="chromeless"

## <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprints](#tab/AzureBlueprints)

::: zone-end

O Azure Blueprints permite que arquitetos de nuvem e grupos centrais de tecnologia da informação definam um conjunto repetível de recursos do Azure que implementa e adere aos padrões e requisitos de uma organização. O Azure Blueprints permite que as equipes de desenvolvimento criem rapidamente e mantenham novos ambientes e a confiança que eles estão conquistando dentro da conformidade organizacional por meio de um conjunto de componentes internos – como rede – para acelerar o desenvolvimento e a entrega.

O Blueprints é uma maneira declarativa de orquestrar a implantação de vários modelos de recursos e outros artefatos, como:

- Atribuições de funções.
- Atribuições de políticas.
- Modelos do Azure Resource Manager.
- Grupos de recursos.

A aplicação de um blueprint poderá impor a conformidade operacional em um ambiente se isso ainda não tiver sido feito pela equipe de governança de nuvem.

### <a name="create-a-blueprint"></a>Criar um plano gráfico

Para criar um blueprint:

::: zone target="chromeless"

1. Vá para **Blueprints – Introdução**.
1. Na seção **Criar um Blueprint**, selecione **Criar**.
1. Filtre a lista de blueprints para selecionar o mais apropriado.
1. Insira o **Nome do blueprint** e selecione o **Local da definição** apropriado.
1. Clique em **Avançar: Artefatos >>** e examine os artefatos incluídos no blueprint.
1. Clique em **Salvar rascunho**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Vá para [Blueprints – Introdução](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. Na seção **Criar um Blueprint**, selecione **Criar**.
1. Filtre a lista de blueprints para selecionar o mais apropriado.
1. Insira o **Nome do blueprint** e selecione o **Local da definição** apropriado.
1. Clique em **Avançar: Artefatos >>** e examine os artefatos incluídos no blueprint.
1. Clique em **Salvar rascunho**.

::: zone-end

### <a name="publish-a-blueprint"></a>Publicar um modelo

Para publicar artefatos de blueprint em sua assinatura:

::: zone target="chromeless"

1. Vá para **Blueprints – Definições de blueprint**.
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Forneça uma **Versão** (como "1.0") e **Notas de alterações**. Em seguida, selecione **Publicar**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Vá para [Blueprints – Definições de blueprint](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Forneça uma **Versão** (como "1.0") e **Notas de alterações**. Em seguida, selecione **Publicar**.

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guia de decisão sobre a consistência do recurso](../../decision-guides/resource-consistency/index.md)
- [Exemplos de blueprints baseados em padrões](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
