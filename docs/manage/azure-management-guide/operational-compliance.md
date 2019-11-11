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
ms.openlocfilehash: b5a94ab41bff26371621acc5e62ae19d9fd02e5c
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565480"
---
# <a name="operational-compliance-in-azure"></a>Conformidade operacional no Azure

A _conformidade operacional_ é a segunda disciplina em qualquer linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

Melhorar a conformidade operacional reduz a probabilidade de uma interrupção relacionada a um descompasso de configuração ou a vulnerabilidades relacionadas aos sistemas que estão sendo corrigidos incorretamente.

Para qualquer ambiente de nível empresarial, esta tabela descreve o mínimo sugerido para uma linha de base de gerenciamento.

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Gerenciamento de patch|Gerenciamento de atualizações|Gerenciamento e agendamento de atualizações|
|Aplicação de políticas|Azure Policy|Imposição de política para garantir a conformidade do ambiente e do convidado|
|Configuração do ambiente|Azure Blueprints|Conformidade automatizada para os serviços principais|

::: zone target="docs"

## <a name="update-management"></a>Gerenciamento de atualizações

::: zone-end
::: zone target="chromeless"

## <a name="update-managementtabupdatemanagement"></a>[Gerenciamento de atualizações](#tab/UpdateManagement)

::: zone-end

Os computadores gerenciados pelo Gerenciamento de Atualizações usam as seguintes configurações para fazer implantações de avaliação e atualização:

- Microsoft Monitoring Agent (MMA) para Windows ou Linux
- DSC (PowerShell Desired State Configuration) para Linux
- Hybrid Runbook Worker da Automação do Azure
- Microsoft Update ou Windows Server Update Services (WSUS) para computadores Windows

Para obter mais informações, consulte a [Solução de Gerenciamento de Atualizações](https://docs.microsoft.com/azure/automation/automation-update-management).

> [!WARNING]
> Antes de usar o Gerenciamento de Atualizações é necessário integrar as máquinas virtuais ou uma assinatura inteira no Log Analytics e na Automação do Azure.
>
> Há duas abordagens para a integração:
>
> - [VM individual](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
> - [Assinatura inteira](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)
>
> Você deve seguir uma delas antes de prosseguir com o Gerenciamento de Atualizações.

### <a name="manage-updates"></a>Gerenciar atualizações

Para aplicar uma política a um grupo de recursos:

1. Acesse [Automação do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Selecione **Contas de automação** e escolha uma das contas listadas.
1. Acesse **Gerenciamento de Configuração**.
1. O **Inventário**, o **Gerenciamento de Alterações** e o **State Configuration** podem ser usados para controlar o estado e a conformidade operacional das VMs gerenciadas.

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

O Azure Policy é usado em todos os processos de governança. Ele também é altamente valioso nos processos de gerenciamento de nuvem. O Azure Policy pode auditar e corrigir recursos do Azure e também pode auditar configurações dentro de um computador. A validação é executada pela extensão e pelo cliente de Configuração de Convidado. A extensão, por meio do cliente, valida as configurações como:

- Configuração do sistema operacional.
- Configuração ou presença do aplicativo.
- Configurações do ambiente.

A Configuração de Convidado do Azure Policy atualmente audita somente as configurações dentro do computador. Ela não aplica configurações.

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

Com o Azure Blueprints, os arquitetos de nuvem e os grupos de tecnologia de informações centrais podem definir um conjunto repetitivo de recursos do Azure. Esses recursos implementam e aderem aos padrões e aos requisitos de uma organização.

Com o Azure Blueprints, as equipes de desenvolvimento podem criar e acumular novos ambientes rapidamente. As equipes também podem ter certeza de que estão criando dentro da conformidade organizacional. Elas fazem isso usando um conjunto de componentes internos, como uma rede, para acelerar o desenvolvimento e a entrega.

O Blueprints é uma maneira declarativa de orquestrar a implantação de diferentes modelos de recursos e outros artefatos, como:

- Atribuições de funções.
- Atribuições de políticas.
- Modelos do Azure Resource Manager.
- Grupos de recursos.

Aplicar um blueprint pode impor a conformidade operacional em um ambiente caso essa imposição não seja feita pela equipe de governança de nuvem.

### <a name="create-a-blueprint"></a>Criar um plano gráfico

Para criar um blueprint:

::: zone target="chromeless"

1. Vá para **Blueprints – Introdução**.
1. No painel **Criar um Blueprint**, selecione **Criar**.
1. Filtre a lista de blueprints para selecionar o mais apropriado.
1. Na caixa **Nome do blueprint**, insira o nome do blueprint.
1. Selecione **Local de definição** e escolha o local apropriado.
1. Selecione **Avançar: Artefatos >>** e revise os artefatos incluídos no blueprint.
1. Selecione **Salvar rascunho**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted]" submitText="Create a blueprint" :::

::: zone-end

::: zone target="docs"

1. Vá para [Blueprints – Introdução](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/GetStarted).
1. No painel **Criar um Blueprint**, selecione **Criar**.
1. Filtre a lista de blueprints para selecionar o mais apropriado.
1. Na caixa **Nome do blueprint**, insira o nome do blueprint.
1. Selecione **Local de definição** e escolha o local apropriado.
1. Selecione **Avançar: Artefatos >>** e revise os artefatos incluídos no blueprint.
1. Selecione **Salvar Rascunho**.

::: zone-end

### <a name="publish-a-blueprint"></a>Publicar um modelo

Para publicar artefatos de blueprint em sua assinatura:

::: zone target="chromeless"

1. Vá para **Blueprints – definições de blueprint**.
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Na caixa **Versão**, insira uma versão como "1.0".
1. Na caixa **Notas de alteração**, insira suas anotações.
1. Selecione **Publicar**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Vá para [Blueprints – definições de blueprint](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Na caixa **Versão**, insira uma versão como "1.0".
1. Na caixa **Notas de alteração**, insira suas anotações.
1. Selecione **Publicar**.

<!-- markdownlint-disable MD024 -->

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guia de decisão sobre a consistência do recurso](../../decision-guides/resource-consistency/index.md)
- [Exemplos de blueprints baseados em padrões](https://docs.microsoft.com/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end
