---
title: Implantar uma zona de aterrissagem de migração no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como implantar uma zona de aterrissagem de migração no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: fasttrack-edit, setup
ms.openlocfilehash: 0eee9746f4d2ee5fcf078774e070ffc25d430f38
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72379179"
---
# <a name="deploy-a-migration-landing-zone"></a>Implantar uma zona de aterrissagem de migração

A *zona de aterrissagem de migração* é um termo usado para descrever um ambiente que foi provisionado e preparado para hospedar cargas de trabalho migradas de um ambiente local para o Azure. Uma zona de aterrissagem de migração é o resultado final do guia de instalação do Azure. Este artigo reúne todos os assuntos de preparação discutidos neste guia e aplica as decisões feitas à implantação da sua primeira zona de aterrissagem de migração.

As seções a seguir descrevem uma zona de aterrissagem normalmente usada para estabelecer um ambiente adequado para uso durante uma migração. O ambiente ou a zona de aterrissagem descrita neste artigo também é capturada em uma especificação técnica do Azure. Você pode usar a estrutura de adoção da nuvem para migrar o Blueprint da zona de aterrissagem para implantar o ambiente definido com um único clique.

## <a name="purpose-of-the-blueprint"></a>Finalidade do plano gráfico

A estrutura de adoção da nuvem migrar plantas de zona de aterrissagem cria uma zona de aterrissagem. Essa zona de aterrissagem é intencionalmente limitada. Ele foi projetado para criar um ponto de partida consistente que fornece espaço para aprender a infraestrutura como código. Para alguns esforços de migração, essa zona de aterrissagem pode ser suficiente para atender às suas necessidades. Também é provável que você precise alterar algo no plano gráfico para atender às suas restrições exclusivas.

## <a name="blueprint-alignment"></a>Alinhamento do Blueprint

A imagem a seguir mostra a estrutura de adoção da nuvem do projeto de zona de aterrissagem em relação à complexidade e aos requisitos de conformidade da arquitetura.

![Alinhamento do Blueprint](../../_images/ready/blueprint-overview.png)

- A letra a fica dentro de uma linha curva que marca o escopo deste plano gráfico. Esse escopo é destinado a transmitir que essa especificação técnica abrange a complexidade da arquitetura limitada, mas que se baseia em requisitos de conformidade de linha relativamente mid.
- Os clientes que têm um alto grau de complexidade e requisitos de conformidade rigorosos podem ser melhor atendidos usando o plano gráfico estendido de um parceiro ou um dos [exemplos de especificações técnicas baseadas em padrões](https://docs.microsoft.com/azure/governance/blueprints/samples).
- A maioria das necessidades dos clientes se enquadrará em algum lugar entre esses dois extremos. A letra B representa o processo descrito nos artigos de [Considerações sobre a zona de aterrissagem](../considerations/index.md) . Para clientes neste espaço, você pode usar os guias de decisão encontrados nesses artigos para identificar os nós a serem adicionados à região de aterrissagem de migração da estrutura de adoção de nuvem. Essa abordagem permite que você personalize o plano gráfico para atender às suas necessidades.

## <a name="use-this-blueprint"></a>Use este projeto

Antes de usar a planta de migração da estrutura de adoção da nuvem, analise as seguintes suposições, decisões e diretrizes de implementação.

## <a name="assumptions"></a>Suposições

As seguintes suposições ou restrições foram usadas quando esta zona de aterrissagem inicial foi definida. Se essas pressuposições estiverem alinhadas às suas restrições, você poderá usar o plano gráfico para criar sua primeira zona de aterrissagem. O Blueprint também pode ser estendido para criar um plano gráfico de zona de aterrissagem que atenda às suas restrições exclusivas.

- **Limites de assinatura:** Não se espera que esse esforço de adoção exceda [os limites de assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits). Dois indicadores comuns são um excesso de 25.000 VMs ou 10.000 vCPUs.
- **Conformidade:** Nenhum requisito de conformidade de terceiros é necessário nessa zona de aterrissagem.
- **Complexidade da arquitetura:** A complexidade da arquitetura não exige assinaturas de produção adicionais.
- **Serviços compartilhados:** Não há nenhum serviço compartilhado existente no Azure que exija que essa assinatura seja tratada como um spoke em uma arquitetura Hub e spoke.

Se essas suposições parecem estar alinhadas com seu ambiente atual, esse plano gráfico pode ser um bom lugar para começar a criar sua zona de aterrissagem.

## <a name="decisions"></a>Decisões

As decisões a seguir são representadas no plano gráfico de zona de aterrissagem.

| Componente | Decisões | Abordagens alternativas |
|---------|---------|---------|
|Ferramentas de migração|Azure Site Recovery serão implantados e um projeto de migrações para Azure será criado.|[Guia de decisão das ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md)|
|Log e monitoramento|O espaço de trabalho de informações operacionais e a conta de armazenamento de diagnóstico serão provisionados.|         |
|Rede|Uma rede virtual será criada com sub-redes para gateway, firewall, Jumpbox e zona de aterrissagem.|[Decisões de rede](../considerations/network-decisions.md)|
|Identidade|Supõe-se que a assinatura já esteja associada a uma instância de Azure Active Directory.|[Práticas recomendadas de gerenciamento de identidade](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json)         |
|Política|Atualmente, este projeto pressupõe que nenhuma política do Azure seja aplicada.|         |
|Design de assinatura|N/A-projetado para uma única assinatura de produção.|[Dimensionando assinaturas](../considerations/scaling-subscriptions.md)|
|Grupos de gerenciamento|N/A-projetado para uma única assinatura de produção.|[Dimensionando assinaturas](../considerations/scaling-subscriptions.md)         |
|Grupos de recursos|N/A-projetado para uma única assinatura de produção.|[Dimensionando assinaturas](../considerations/scaling-subscriptions.md)         |
|Dados|N/D|[Escolha a opção de SQL Server correta no Azure e nas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas?toc=https://docs.microsoft.com/azure/architecture/toc.json&bc=https://docs.microsoft.com/azure/architecture/bread/toc.json) [diretrizes do Azure Data Store](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Armazenamento|N/D|[Diretrizes de armazenamento do Azure](../considerations/storage-guidance.md)         |
|Padrões de nomenclatura e marcação|N/D|[Práticas recomendadas de nomenclatura e marcação](../considerations/naming-and-tagging.md)         |
|Gerenciamento de custos|N/D|[Controlando os custos](../azure-best-practices/track-costs.md)|
|Computação|N/D|[Opções de computação](../considerations/compute-decisions.md)|

## <a name="customize-or-deploy-a-landing-zone-from-this-blueprint"></a>Personalizar ou implantar uma zona de aterrissagem deste plano gráfico

Saiba mais e baixe um exemplo de referência da estrutura de adoção da nuvem migrar gráfico de zona de aterrissagem para implantação ou personalização nos [exemplos de plantas do Azure](https://docs.microsoft.com/azure/governance/blueprints/samples).

Os exemplos de Blueprint também estão disponíveis no Portal. Para obter detalhes de como criar um plano gráfico, consulte [plantas do Azure](./govern-org-compliance.md?tabs=azureblueprints#create-a-blueprint).

Para obter orientação sobre a personalização que deve ser feita nesse plano gráfico ou na zona de aterrissagem resultante, consulte os artigos [sobre considerações de zona de aterrissagem](../considerations/index.md) .

## <a name="next-steps"></a>Próximos passos

Depois que uma zona de aterrissagem de migração for implantada, você estará pronto para migrar cargas de trabalho para o Azure.
Para obter orientação sobre as ferramentas e os processos necessários para migrar sua primeira carga de trabalho, consulte o [Guia de migração do Azure](../../migrate/azure-migration-guide/index.md).

> [!div class="nextstepaction"]
> [Migre sua primeira carga de trabalho com o guia de migração do Azure](../../migrate/azure-migration-guide/index.md)
