---
title: Implantar uma zona de acesso de migração no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como implantar uma zona de acesso de migração no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit
ms.openlocfilehash: 9b6c526f407a50327aad8dd2fb2639cb7172cb8d
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025213"
---
# <a name="deploy-a-migration-landing-zone"></a>Implantar uma zona de aterrissagem de migração

*Zona de acesso de migração* é um termo usado para descrever um ambiente que foi provisionado e preparado para hospedar cargas de trabalho migradas de um ambiente local para o Azure. Uma zona de acesso de migração é o resultado final do guia de Preparação para o Azure. Este artigo reúne todos os assuntos de preparação discutidos neste guia e aplica as decisões feitas à implantação da sua primeira zona de acesso de migração.

As seções a seguir descrevem uma zona de acesso normalmente usada para estabelecer um ambiente adequado para uso durante uma migração. O ambiente ou a zona de acesso descrita neste artigo também é capturada em um Azure Blueprint. Você pode usar o blueprint da zona de acesso de migração da Cloud Adoption Framework para implantar o ambiente definido com um único clique.

## <a name="purpose-of-the-blueprint"></a>Finalidade do blueprint

O blueprint da zona de acesso de migração da Cloud Adoption Framework cria uma zona de acesso. Essa zona de acesso é intencionalmente limitada. Ela foi projetada para criar um ponto de partida consistente que fornece espaço para aprender a infraestrutura como código. Para alguns esforços de migração, essa zona de acesso pode ser suficiente para atender às suas necessidades. Também é provável que você precise alterar algo no blueprint para atender às suas restrições específicas.

## <a name="blueprint-alignment"></a>Alinhamento do blueprint

A imagem a seguir mostra o blueprint da zona de acesso de migração da Cloud Adoption Framework em relação à complexidade da arquitetura e aos requisitos de conformidade.

![Alinhamento do blueprint](../../_images/ready/blueprint-overview.png)

- A letra A fica dentro de uma linha curva que marca o escopo deste blueprint. Esse escopo passa a ideia de que esse blueprint abrange uma complexidade de arquitetura limitada, mas que se baseia em requisitos de conformidade relativamente intermediários.
- Os clientes que têm um alto grau de complexidade e requisitos de conformidade rigorosos podem ser melhor atendidos usando um blueprint estendido de um parceiro ou um dos [exemplos de blueprint baseados em padrões](https://docs.microsoft.com/azure/governance/blueprints/samples/).
- A maioria das necessidades dos clientes se enquadrará em algum lugar entre esses dois extremos. A letra B representa o processo descrito nos artigos de [considerações sobre a zona de acesso](../considerations/index.md). Para clientes neste espaço, você pode usar os guias de decisão encontrados nesses artigos para identificar os nós a serem adicionados ao blueprint da zona de acesso de migração da Cloud Adoption Framework. Essa abordagem permite que você personalize o blueprint para atender às suas necessidades.

## <a name="use-this-blueprint"></a>Usar este blueprint

Antes de usar o blueprint da zona de acesso de migração da Cloud Adoption Framework, analise as seguintes suposições, decisões e diretrizes de implementação.

## <a name="assumptions"></a>Suposições

As seguintes suposições ou restrições foram usadas quando esta zona de acesso inicial foi definida. Se essas pressuposições estiverem alinhadas às suas restrições, você poderá usar o blueprint para criar sua primeira zona de acesso. O blueprint também pode ser estendido para criar um blueprint de zona de acesso que atenda às suas restrições específicas.

- **Limites da assinatura:** Não se espera que esse esforço de adoção exceda os [limites da assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits). Dois indicadores comuns são um excesso de 25.000 VMs ou 10.000 vCPUs.
- **Conformidade:** Nenhum requisito de conformidade de terceiros é necessário nessa zona de acesso.
- **Complexidade da arquitetura:** A complexidade da arquitetura não exige assinaturas de produção adicionais.
- **Serviços compartilhados:** Não há nenhum serviço compartilhado existente no Azure que exija que essa assinatura seja tratada como um spoke em uma arquitetura hub e spoke.

Se essas suposições parecem alinhadas com seu ambiente atual, esse blueprint pode ser um bom lugar para começar a criar a zona de acesso.

## <a name="decisions"></a>Decisões

As decisões a seguir são representadas no blueprint da zona de acesso.

| Componente | Decisões | Abordagens alternativas |
|---------|---------|---------|
|Ferramentas de migração|O Azure Site Recovery será implantado e um projeto do Migrações para Azure será criado.|[Guia de decisão de ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md)|
|Log e monitoramento|O workspace do Insights Operacionais e a conta de armazenamento de diagnóstico serão provisionados.|         |
|Rede|Uma rede virtual será criada com sub-redes para gateway, firewall, jumpbox e zona de acesso.|[Decisões de rede](../considerations/network-decisions.md)|
|Identidade|Supõe-se que a assinatura já esteja associada a uma instância do Azure Active Directory.|[Melhores práticas de gerenciamento de identidades](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json)         |
|Política|Atualmente, este blueprint pressupõe que nenhuma política do Azure deve ser aplicada.|         |
|Design de assinatura|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md)|
|Grupos de gerenciamento|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md)         |
|Grupos de recursos|N/A – projetado para uma única assinatura de produção.|[Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md)         |
|Dados|N/D|[Escolher a opção correta do SQL Server no Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json)         |
|Armazenamento|N/D|[Diretrizes do Armazenamento do Azure](../considerations/storage-guidance.md)         |
|Padrões de nomenclatura e marcação|N/D|[Melhores práticas de nomenclatura e marcação](../considerations/naming-and-tagging.md)         |
|Gerenciamento de custos|N/D|[Acompanhando os custos](../azure-best-practices/track-costs.md)|
|Computação|N/D|[Opções de computação](../considerations/compute-decisions.md)|

## <a name="customize-or-deploy-a-landing-zone-from-this-blueprint"></a>Personalizar ou implantar uma zona de acesso com base neste blueprint

Saiba mais e baixe um exemplo de referência do blueprint da zona de acesso de migração da Cloud Adoption Framework para implantação ou personalização de [exemplos do Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/samples/index).

Os exemplos de blueprint também estão disponíveis no portal. Para obter detalhes sobre como implantar um blueprint, confira [Azure Blueprints](./govern-org-compliance.md?tabs=azureblueprints#create-a-blueprint).

Para diretrizes sobre a personalização que deve ser feita nesse blueprint ou na zona de acesso resultante, confira os artigos sobre [considerações de zona de acesso](../considerations/index.md).

## <a name="next-steps"></a>Próximas etapas

Depois que uma zona de acesso de migração for implantada, você estará pronto para migrar cargas de trabalho para o Azure.
Para obter diretrizes sobre as ferramentas e os processos necessários para migrar sua primeira carga de trabalho, confira o [guia de migração do Azure](../../migrate/azure-migration-guide/index.md).

> [!div class="nextstepaction"]
> [Migrar sua primeira carga de trabalho com o guia de migração do Azure](../../migrate/azure-migration-guide/index.md)
