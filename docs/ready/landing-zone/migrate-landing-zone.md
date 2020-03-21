---
title: Implantar uma zona de acesso de migração no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como implantar uma zona de acesso de migração no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 1727bb9c77298663f30e6205a9a3230ce65be3c1
ms.sourcegitcommit: 5d7e93540a679252f1c7207e62cb2ee7213a6ae9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80069750"
---
<!-- cSpell:ignore vCPUs jumpbox -->

# <a name="deploy-a-migration-landing-zone"></a>Implantar uma zona de aterrissagem de migração

*Zona de acesso de migração* é um termo usado para descrever um ambiente que foi provisionado e preparado para hospedar cargas de trabalho migradas de um ambiente local para o Azure.

## <a name="deploy-the-first-landing-zone"></a>Implantar a primeira zona de aterrissagem

Antes de usar o esquema de zona de aterrissagem de migração na estrutura de adoção de nuvem, revise as seguintes suposições, decisões e diretrizes de implementação. Se essa orientação se alinhar com o plano de adoção de nuvem desejado, a [especificação da zona de aterrissagem de migração](https://docs.microsoft.com/azure/governance/blueprints/samples/caf-migrate-landing-zone/index) poderá ser implantada usando as etapas de [implantação][deploy-sample].

> [!div class="nextstepaction"]
> [Implantar a amostra Blueprint][deploy-sample]

## <a name="assumptions"></a>Suposições

Essa zona de aterrissagem inicial inclui as seguintes suposições ou restrições. Se essas pressuposições estiverem alinhadas às suas restrições, você poderá usar o blueprint para criar sua primeira zona de acesso. O blueprint também pode ser estendido para criar um blueprint de zona de acesso que atenda às suas restrições específicas.

- **Limites de assinatura:** Não se espera que esse esforço de adoção exceda [os limites de assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits).
- **Conformidade:** Nenhum requisito de conformidade de terceiros é necessário nessa zona de aterrissagem.
- **Complexidade da arquitetura:** A complexidade da arquitetura não exige assinaturas de produção adicionais.
- **Serviços compartilhados:** Não há nenhum serviço compartilhado existente no Azure que exija que essa assinatura seja tratada como um spoke em uma arquitetura de Hub e spoke.
- **Escopo de produção limitado:** Essa zona de aterrissagem pode hospedar cargas de trabalho de produção. No entanto, ele não é um ambiente adequado para dados confidenciais ou cargas de trabalho de missão crítica.

Se essas pressuposições estiverem alinhadas às suas necessidades de adoção atuais, esse plano gráfico poderá ser um ponto de partida para a criação de sua zona de aterrissagem.

## <a name="decisions"></a>Decisões

As decisões a seguir são representadas no blueprint da zona de acesso.

| Componente                    | Decisões                                                                                         | Abordagens alternativas                                                                                                                                                                                                                                                               |
|------------------------------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ferramentas de migração              | O Azure Site Recovery será implantado e um projeto do Migrações para Azure será criado.                | [Guia de decisão de ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md)                                                                                                                                                                                              |
| Log e monitoramento       | O workspace do Insights Operacionais e a conta de armazenamento de diagnóstico serão provisionados.                |                                                                                                                                                                                                                                                                                      |
| Rede                      | Uma rede virtual será criada com sub-redes para gateway, firewall, jumpbox e zona de acesso.  | [Decisões de rede](../considerations/networking-options.md)                                                                                                                                                                                                                      |
| Identity                     | Supõe-se que a assinatura já esteja associada a uma instância do Azure Active Directory. | [Melhores práticas de gerenciamento de identidades](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json) |
| Política                       | Atualmente, este blueprint pressupõe que nenhuma política do Azure deve ser aplicada.                        |                                                                                                                                                                                                                                                                                      |
| Design de assinatura          | N/A – projetado para uma única assinatura de produção.                                              | [Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Grupos de gerenciamento            | N/A – projetado para uma única assinatura de produção.                                              | [Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Grupos de recursos              | N/A – projetado para uma única assinatura de produção.                                              | [Dimensionamento de assinaturas](../azure-best-practices/scaling-subscriptions.md)                                                                                                                                                                                                            |
| Dados                         | {1&gt;N/A&lt;1}                                                                                               | [Escolha a opção de SQL Server correta no Azure e nas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) [diretrizes do Azure Data Store](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview)                      |
| Armazenamento                      | {1&gt;N/A&lt;1}                                                                                               | [Diretrizes do Armazenamento do Azure](../considerations/storage-options.md)                                                                                                                                                                                                                       |
| Padrões de nomenclatura e marcação | {1&gt;N/A&lt;1}                                                                                               | [Melhores práticas de nomenclatura e marcação](../azure-best-practices/naming-and-tagging.md)                                                                                                                                                                                                   |
| Gerenciamento de custo              | {1&gt;N/A&lt;1}                                                                                               | [Acompanhando os custos](../azure-best-practices/track-costs.md)                                                                                                                                                                                                                             |
| Computação                      | {1&gt;N/A&lt;1}                                                                                               | [Opções de computação](../considerations/compute-options.md)                                                                                                                                                                                                                              |

## <a name="customize-or-deploy-a-landing-zone"></a>Personalizar ou implantar uma zona de aterrissagem

Saiba mais e baixe um exemplo de referência do projeto de zona de aterrissagem de migração para implantação ou personalização de [exemplos de Azure Blueprint][deploy-sample].

> [!div class="nextstepaction"]
> [Implantar a amostra Blueprint][deploy-sample]

Para obter orientação sobre as personalizações que devem ser feitas nesse plano gráfico ou na zona de aterrissagem resultante, consulte [Considerações sobre a zona de aterrissagem](../considerations/index.md).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Depois de implantar sua primeira zona de aterrissagem, você estará pronto para [expandir sua zona de aterrissagem](../considerations/index.md)

> [!div class="nextstepaction"]
> [Expanda sua zona de aterrissagem](../considerations/index.md)

<!-- links -->

[deploy-sample]: https://docs.microsoft.com/azure/governance/blueprints/samples/caf-migrate-landing-zone/deploy
