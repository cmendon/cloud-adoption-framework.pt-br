---
title: Governança, segurança e conformidade no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como configurar governança, segurança e conformidade para o seu ambiente do Azure.
author: tvuylsteke
ms.author: kfollis
ms.date: 04/09/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 99d8520b74f00372d5cbf22f81669a6c27d22431
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224278"
---
# <a name="governance-security-and-compliance-in-azure"></a>Governança, segurança e conformidade no Azure

Ao estabelecer a política corporativa e planejar suas estratégias de governança, você pode usar ferramentas e serviços como o Azure Policy, o Azure Blueprints e a Central de Segurança do Azure para impor e automatizar as decisões de governança da sua organização. Antes de iniciar seu planejamento de governança, use a [ferramenta de Parâmetro de Comparação de Governança](http://aka.ms/caf/gov/assess) para identificar possíveis lacunas na abordagem de governança de nuvem da sua organização. Para obter mais informações sobre como desenvolver processos de governança, confira [Cloud Adoption Framework para diretrizes de governança do Azure](../../govern/index.md).

# <a name="azure-blueprintstabazureblueprints"></a>[Azure Blueprints](#tab/AzureBlueprints)

O Azure Blueprints permite que arquitetos de nuvem e grupos centrais de tecnologia da informação definam um conjunto repetível de recursos do Azure que implementa e adere aos padrões e requisitos de uma organização. O Azure Blueprints permite que as equipes de desenvolvimento criem rapidamente e mantenham novos ambientes e a confiança que eles estão conquistando dentro da conformidade organizacional por meio de um conjunto de componentes internos – como rede – para acelerar o desenvolvimento e a entrega.

O Blueprints é uma maneira declarativa de orquestrar a implantação de vários modelos de recursos e outros artefatos, como:

- Atribuições de funções.
- Atribuições de políticas.
- Modelos do Azure Resource Manager.
- Grupos de recursos.

## <a name="create-a-blueprint"></a>Criar um plano gráfico

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

## <a name="publish-a-blueprint"></a>Publicar um modelo

Para publicar artefatos de blueprint em sua assinatura:

::: zone target="chromeless"

1. Vá para **Blueprints – Definições de blueprint**.
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Forneça uma **Versão** (como _1.0_) e as **Notas de alterações**. Em seguida, selecione **Publicar**.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints]" submitText="Blueprint definitions" :::

::: zone-end

::: zone target="docs"

1. Vá para [Blueprints – Definições de blueprint](https://portal.azure.com/#blade/Microsoft_Azure_Policy/BlueprintsMenuBlade/Blueprints).
1. Selecione o blueprint criado nas etapas anteriores.
1. Examine a definição do blueprint e selecione **Publicar blueprint**.
1. Forneça uma **Versão** (como _1.0_) e as **Notas de alterações**. Em seguida, selecione **Publicar**.

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints)
- [Cloud Adoption Framework: Guia de decisão sobre a consistência do recurso](../../decision-guides/resource-consistency/index.md)
- [Exemplos de blueprints baseados em padrões](/azure/governance/blueprints/samples/index#standards-based-blueprint-samples)

::: zone-end

# <a name="azure-policytabazurepolicy"></a>[Azure Policy](#tab/AzurePolicy)

O Azure Policy é um serviço usado para criar, atribuir e gerenciar políticas. Essas políticas impõem regras sobre seus recursos para que esses recursos permaneçam em conformidade com seus padrões corporativos e contratos de nível de serviço. O Azure Policy examina os recursos para identificar aqueles que não estão em conformidade com as políticas que você implementa. Por exemplo, você pode ter uma política para permitir que apenas um tamanho de VM (máquina virtual ) específico seja executado em seu ambiente. Quando você implementa essa política, ela avalia as VMs existentes em seu ambiente e quaisquer novas VMs que são implantadas. A avaliação da política gera eventos de conformidade para você usar para monitoramento e emissão de relatórios.

Considere políticas comuns para:

- Impor a marcação para recursos e grupos de recursos.
- Restringir as regiões para recursos implantados.
- Restringir SKUs caras para recursos específicos.
- Auditar o uso de recursos opcionais importantes, como os Managed Disks do Azure.

::: zone target="chromeless"

## <a name="action"></a>Ação

Atribua uma política interna a um grupo de gerenciamento, assinatura ou grupo de recursos.

::: form action="OpenBlade[#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted]" submitText="Assign Policy" :::

::: zone-end

::: zone target="docs"

## <a name="apply-a-policy"></a>Aplique uma política

Para aplicar uma política a um grupo de recursos:

1. Acesse [Azure Policy](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyMenuBlade/GettingStarted).
1. Selecione **Atribuir uma política**.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Azure Policy](https://docs.microsoft.com/azure/azure-policy)
- [Cloud Adoption Framework: guia de decisão para imposição de política](../../decision-guides/policy-enforcement/index.md)

::: zone-end

# <a name="azure-security-centertabazuresecuritycenter"></a>[Central de Segurança do Azure](#tab/AzureSecurityCenter)

A Central de Segurança do Azure desempenha um papel importante na sua estratégia de governança. Ela ajuda você a manter o controle da segurança, pois:

- Apresenta uma exibição unificada da segurança em todas as suas cargas de trabalho.
- Coleta, pesquisa e analisa dados de segurança de uma série de fontes, que incluem firewalls e outras soluções de parceiros.
- Fornece recomendações de segurança acionáveis para corrigir problemas antes de serem explorados.
- Pode ser usada para aplicar políticas de segurança em todas as suas cargas de trabalho de nuvem híbrida para garantir a conformidade com padrões de segurança.

Muitos dos recursos de segurança, como política e recomendações de segurança, estão disponíveis gratuitamente. Alguns dos recursos mais avançados, como o acesso à VM Just-In-Time e suporte à carga de trabalho híbrida, estão disponíveis na camada padrão da Central de Segurança. O acesso à VM just-in-time pode ajudar a reduzir a superfície de ataque da rede controlando o acesso às portas de gerenciamento nas VMs do Azure.

> [!TIP]
> A Central de Segurança do Azure é habilitada por padrão em cada assinatura. Recomendamos habilitar a coleta de dados em máquinas virtuais de modo a permitir que a Central de Segurança do Azure instale seu agente e comece a coletar dados.

::: zone target="docs"

Para explorar a Central de Segurança do Azure, vá para o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte:

- [Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center)
- [Acesso à VM Just-In-Time](https://docs.microsoft.com/azure/security-center/security-center-just-in-time#how-does-just-in-time-access-work)
- [Tipo de preço padrão versus gratuito](https://azure.microsoft.com/pricing/details/security-center)
- [Cloud Adoption Framework: disciplina de governança da Linha de Base de Segurança](../../govern/security-baseline/index.md)

::: zone-end

::: zone target="chromeless"
## <a name="action"></a>Ação

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end