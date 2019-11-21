---
title: Implantar uma zona de acesso de migração no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como implantar uma zona de acesso de migração no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit
ms.openlocfilehash: 8c54ebc4c279493089c82a6d9f28c5e35dc3dd7e
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251442"
---
# <a name="deploy-a-migration-landing-zone"></a>Implantar uma zona de aterrissagem de migração

*Zona de acesso de migração* é um termo usado para descrever um ambiente que foi provisionado e preparado para hospedar cargas de trabalho migradas de um ambiente local para o Azure. A migration landing zone is the final deliverable of the Azure setup guide. Este artigo reúne todos os assuntos de preparação discutidos neste guia e aplica as decisões feitas à implantação da sua primeira zona de acesso de migração.

As seções a seguir descrevem uma zona de acesso normalmente usada para estabelecer um ambiente adequado para uso durante uma migração. O ambiente ou a zona de acesso descrita neste artigo também é capturada em um Azure Blueprint. Você pode usar o blueprint da zona de acesso de migração da Cloud Adoption Framework para implantar o ambiente definido com um único clique.

## <a name="purpose-of-the-blueprint"></a>Finalidade do blueprint

O blueprint da zona de acesso de migração da Cloud Adoption Framework cria uma zona de acesso. Essa zona de acesso é intencionalmente limitada. Ela foi projetada para criar um ponto de partida consistente que fornece espaço para aprender a infraestrutura como código. Para alguns esforços de migração, essa zona de acesso pode ser suficiente para atender às suas necessidades. Também é provável que você precise alterar algo no blueprint para atender às suas restrições específicas.

## <a name="blueprint-alignment"></a>Alinhamento do blueprint

A imagem a seguir mostra o blueprint da zona de acesso de migração da Cloud Adoption Framework em relação à complexidade da arquitetura e aos requisitos de conformidade.

![Alinhamento do blueprint](../../_images/ready/blueprint-overview.png)

- A letra A fica dentro de uma linha curva que marca o escopo deste blueprint. Esse escopo passa a ideia de que esse blueprint abrange uma complexidade de arquitetura limitada, mas que se baseia em requisitos de conformidade relativamente intermediários.
- Os clientes que têm um alto grau de complexidade e requisitos de conformidade rigorosos podem ser melhor atendidos usando um blueprint estendido de um parceiro ou um dos [exemplos de blueprint baseados em padrões](https://docs.microsoft.com/azure/governance/blueprints/samples).
- A maioria das necessidades dos clientes se enquadrará em algum lugar entre esses dois extremos. A letra B representa o processo descrito nos artigos de [considerações sobre a zona de acesso](../considerations/index.md). Para clientes neste espaço, você pode usar os guias de decisão encontrados nesses artigos para identificar os nós a serem adicionados ao blueprint da zona de acesso de migração da Cloud Adoption Framework. Essa abordagem permite que você personalize o blueprint para atender às suas necessidades.

## <a name="use-this-blueprint"></a>Usar este blueprint

Antes de usar o blueprint da zona de acesso de migração da Cloud Adoption Framework, analise as seguintes suposições, decisões e diretrizes de implementação.

## <a name="assumptions"></a>Suposições

As seguintes suposições ou restrições foram usadas quando esta zona de acesso inicial foi definida. Se essas pressuposições estiverem alinhadas às suas restrições, você poderá usar o blueprint para criar sua primeira zona de acesso. O blueprint também pode ser estendido para criar um blueprint de zona de acesso que atenda às suas restrições específicas.

- **Subscription limits:** This adoption effort isn't expected to exceed [subscription limits](https://docs.microsoft.com/azure/azure-subscription-service-limits). Dois indicadores comuns são um excesso de 25.000 VMs ou 10.000 vCPUs.
- **Compliance:** No third-party compliance requirements are needed in this landing zone.
- **Architectural complexity:** Architectural complexity doesn't require additional production subscriptions.
- **Shared services:** There are no existing shared services in Azure that require this subscription to be treated like a spoke in a hub and spoke architecture.

Se essas suposições parecem alinhadas com seu ambiente atual, esse blueprint pode ser um bom lugar para começar a criar a zona de acesso.

## <a name="decisions"></a>Decisões

As decisões a seguir são representadas no blueprint da zona de acesso.

| Componente | Decisões | Abordagens alternativas |
|---------|---------|---------|
|Ferramentas de migração|O Azure Site Recovery será implantado e um projeto do Migrações para Azure será criado.|[Guia de decisão de ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md)|
|Log e monitoramento|O workspace do Insights Operacionais e a conta de armazenamento de diagnóstico serão provisionados.|         |
|Rede|Uma rede virtual será criada com sub-redes para gateway, firewall, jumpbox e zona de acesso.|[Decisões de rede](../considerations/networking-options.md)|
|Identidade|Supõe-se que a assinatura já esteja associada a uma instância do Azure Active Directory.|[Melhores práticas de gerenciamento de identidades](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)         |
|Política|Atualmente, este blueprint pressupõe que nenhuma política do Azure deve ser aplicada.|         |
|Design de assinatura|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)|
|Grupos de gerenciamento|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)         |
|Grupos de recursos|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)         |
|Dados|N/D|[Choose the correct SQL Server option in Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) and [Azure Data Store guidance](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Armazenamento|N/D|[Diretrizes do Armazenamento do Azure](../considerations/storage-options.md)         |
|Padrões de nomenclatura e marcação|N/D|[Melhores práticas de nomenclatura e marcação](../azure-best-practices/naming-and-tagging.md)         |
|Gerenciamento de custos|N/D|[Acompanhando os custos](../azure-best-practices/track-costs.md)|
|Computação|N/D|[Opções de computação](../considerations/compute-options.md)|

## <a name="customize-or-deploy-a-landing-zone-from-this-blueprint"></a>Personalizar ou implantar uma zona de acesso com base neste blueprint

Learn more and download a reference sample of the Cloud Adoption Framework migrate landing zone blueprint for deployment or customization from [Azure Blueprints samples](https://docs.microsoft.com/azure/governance/blueprints/samples).

Os exemplos de blueprint também estão disponíveis no portal. For details of how to create a blueprint, see [Azure Blueprints](./govern-org-compliance.md?tabs=azureblueprints#create-a-blueprint).

Para diretrizes sobre a personalização que deve ser feita nesse blueprint ou na zona de acesso resultante, confira os artigos sobre [considerações de zona de acesso](../considerations/index.md).

## <a name="next-steps"></a>Próximos passos

Depois que uma zona de acesso de migração for implantada, você estará pronto para migrar cargas de trabalho para o Azure.
Para obter diretrizes sobre as ferramentas e os processos necessários para migrar sua primeira carga de trabalho, confira o [guia de migração do Azure](../../migrate/azure-migration-guide/index.md).

> [!div class="nextstepaction"]
> [Migrar sua primeira carga de trabalho com o guia de migração do Azure](../../migrate/azure-migration-guide/index.md)
