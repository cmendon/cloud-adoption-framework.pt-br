---
title: Zona de aterrissagem com Terraform
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda a usar o Terraform para criar suas zonas de aterrissagem.
author: arnaudlh
ms.author: arnaul
ms.date: 10/16/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: b540e2f4ea2a9c7f091a5505a19ad61eac05c971
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049764"
---
# <a name="use-terraform-to-build-your-landing-zones"></a>Use o Terraform para criar suas zonas de aterrissagem

Além dos serviços nativos do Azure, os clientes e parceiros geralmente usam o Terraform da Hashicorp para implantar zonas de aterrissagem. Esta seção descreve como usar uma zona de aterrissagem de protótipo para implantar recursos fundamentais de log, contabilidade e segurança para uma assinatura do Azure.

## <a name="purpose-of-the-landing-zone"></a>Finalidade da zona de aterrissagem

A zona de aterrissagem da estrutura de adoção de nuvem para Terraform tem um conjunto limitado de responsabilidades e recursos para impor registro em log, contabilidade e segurança. Projetamos essa zona de aterrissagem usam componentes padrão conhecidos como módulos Terraform para impor a consistência entre os recursos implantados no ambiente.

## <a name="using-standard-modules"></a>Usando módulos padrão

A reutilização de componentes é um princípio fundamental de infraestrutura como código. Os módulos são fundamentais para definir padrões e consistência em toda a implantação de recursos em e entre ambientes. O conjunto de módulos usado para implantar essa primeira zona de aterrissagem está disponível no [registro](https://registry.terraform.io/search?q=aztfmod)oficial do Terraform.

## <a name="architecture-diagram"></a>Diagrama da arquitetura

A primeira zona de aterrissagem implanta os seguintes componentes em sua assinatura:

![Zona de aterrissagem de fundação usando Terraform](../../_images/ready/foundations-terraform-landingzone.png)

## <a name="capabilities"></a>Capacidades

Os componentes implantados e sua finalidade incluem o seguinte:

| Componente | responsabilidade |
|---------|---------|
| Grupos de recursos | Principais grupos de recursos necessários para a base |
| Log de atividades | Auditar todas as atividades de assinatura e arquivamento: </br> -Conta de armazenamento </br> -Hubs de eventos |  
| Log de diagnóstico | Todo o log de operações é mantido por um número específico de dias: </br> -Conta de armazenamento </br> -Hubs de eventos |
| Log Analytics | Armazena todos os logs de operações </br> Implante soluções comuns para análise profunda de práticas recomendadas de aplicativo: </br> - NetworkMonitoring </br> - ADAssessment </br> - ADReplication </br> - AgentHealthAssessment </br> - DnsAnalytics </br> - KeyVaultAnalytics
| Central de Segurança | Métricas e alertas de higiene de segurança enviados para email e número de telefone |

## <a name="use-this-blueprint"></a>Usar este blueprint

Antes de usar a zona de aterrissagem do Cloud Preparation Framework Foundation, examine as seguintes suposições, decisões e diretrizes de implementação.

## <a name="assumptions"></a>Suposições

As seguintes suposições ou restrições foram consideradas quando esta zona de aterrissagem inicial foi definida. Se essas pressuposições estiverem alinhadas às suas restrições, você poderá usar o blueprint para criar sua primeira zona de acesso. O blueprint também pode ser estendido para criar um blueprint de zona de acesso que atenda às suas restrições específicas.

- **Limites de assinatura:** Esse esforço de adoção é improvável de exceder [os limites de assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits). Dois indicadores comuns são um excesso de 25.000 VMs ou 10.000 vCPUs.
- **Conformidade:** Nenhum requisito de conformidade de terceiros é necessário para essa zona de aterrissagem.
- **Complexidade da arquitetura:** A complexidade da arquitetura não exige assinaturas de produção adicionais.
- **Serviços compartilhados:** Não há nenhum serviço compartilhado existente no Azure que exija que essa assinatura seja tratada como um spoke em uma arquitetura Hub e spoke.

Se essas suposições corresponderem ao seu ambiente atual, esse plano gráfico poderá ser uma boa maneira de começar a criar sua zona de aterrissagem.

## <a name="design-decisions"></a>Decisões de design

As decisões a seguir são representadas na zona de aterrissagem Terraform:

| Componente | Decisões | Abordagens alternativas |
| --- | --- | --- |
|Log e monitoramento | Azure Monitor Log Analytics espaço de trabalho será usado. Uma conta de armazenamento de diagnóstico, bem como o Hub de eventos, será provisionada. |         |
|Rede | N/A-rede será implementada em outra zona de aterrissagem. |[Decisões de rede](../considerations/network-decisions.md) |
|Identidade | Supõe-se que a assinatura já esteja associada a uma instância do Azure Active Directory. | [Melhores práticas de gerenciamento de identidades](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices) |
| Política | Essa zona de aterrissagem atualmente supõe que nenhuma política do Azure será aplicada. | |
|Design de assinatura | N/A – projetado para uma única assinatura de produção. | [Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md) |
| Grupos de gerenciamento | N/A – projetado para uma única assinatura de produção. |[Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md) |
| Grupos de recursos | N/A – projetado para uma única assinatura de produção. | [Dimensionamento de assinaturas](../considerations/scaling-subscriptions.md) |
| Dados | N/D | [Escolha a opção de SQL Server correta no Azure e nas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas) [diretrizes do Azure Data Store](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview) |
|Armazenamento|N/D|[Diretrizes do Armazenamento do Azure](../considerations/storage-guidance.md) |
| Padrões de nomenclatura | Quando o ambiente for criado, um prefixo exclusivo também será criado. Os recursos que exigem um nome global exclusivo (como contas de armazenamento) usam esse prefixo. O nome personalizado será anexado com um sufixo aleatório. O uso de marca é obrigatório conforme descrito na tabela a seguir. | [Melhores práticas de nomenclatura e marcação](../considerations/naming-and-tagging.md) |
| Gerenciamento de custos | N/D | [Acompanhando os custos](../azure-best-practices/track-costs.md) |
| Computação | N/D | [Opções de computação](../considerations/compute-decisions.md) |

### <a name="tagging-standards"></a>Padrões de marcação

O seguinte conjunto de marcas mínimas deve estar presente em todos os recursos e grupos de recursos:

| Nome da marca | Descrição | Chave | Exemplo de valor |
|--|--|--|--|
| Unidade de negócios | Divisão de nível superior da sua empresa que tem a assinatura ou a carga de trabalho à qual o recurso pertence. | BusinessUnit | Finanças, MARKETING, {nome do produto}, CORP, compartilhado |
| Centro de custo | O centro de custo de contabilidade associado a este recurso.| CostCenter | NUMBER |
| Recuperação de desastres | Nível de importância empresarial do aplicativo, da carga de trabalho ou do serviço. | Recovery | HABILITADO PARA DR, NÃO HABILITADO PARA DR |
| Ambiente | Ambiente de implantação do aplicativo, da carga de trabalho ou do serviço. |  Variável | Prod, dev, QA, estágio, teste, treinamento |
| Nome do proprietário | Proprietário do aplicativo, da carga de trabalho ou do serviço.| Proprietário | email |
| DeploymentType | Define como os recursos são mantidos. | deploymentType | Manual, Terraform |
| Versão | Versão do Blueprint implantada | version | v 0,1 |
| Nome do Aplicativo | Nome do aplicativo, serviço ou carga de trabalho associado ao recurso. | ApplicationName | "nome do aplicativo" |

## <a name="customize-and-deploy-your-first-landing-zone"></a>Personalizar e implantar sua primeira zona de aterrissagem

Você pode [clonar sua zona de aterrissagem do Terraform Foundation](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready). É fácil começar a usar a zona de aterrissagem modificando as variáveis Terraform. Em nosso exemplo, usamos **blueprint_foundations. sandbox. auto. tfvars**, portanto, Terraform definirá automaticamente os valores nesse arquivo para você.

Vamos examinar as diferentes seções variáveis.

Nesse primeiro objeto, criamos dois grupos de recursos na região `southeastasia`, denominado "-Hub-núcleo-s" e "-Hub-núcleo-seg", juntamente com um prefixo adicionado no tempo de execução.

```hcl
resource_groups_hub = {
    HUB-CORE-SEC    = {
        name = "-hub-core-sec"
        location = "southeastasia"
    }
    HUB-OPERATIONS  = {
        name = "-hub-operations"
        location = "southeastasia"
    }
}
```

Em seguida, especificamos as regiões nas quais podemos definir as bases. Aqui, `southeastasia` será usado para implantar todos os recursos.

```hcl
location_map = {
    region1   = "southeastasia"
    region2   = "eastasia"
}
```

Em seguida, especificamos o período de retenção para os logs de operações e os logs de assinatura do Azure. Esses dados serão armazenados em contas de armazenamento separadas e em um hub de eventos, cujos nomes são gerados aleatoriamente, pois eles devem ser exclusivos.

```hcl
azure_activity_logs_retention = 365
azure_diagnostics_logs_retention = 60
```

No tags_hub, especificamos o conjunto mínimo de marcas que serão aplicadas a todos os recursos criados.

```hcl
tags_hub = {
    environment     = "DEV"
    owner           = "Arnaud"
    deploymentType  = "Terraform"
    costCenter      = "65182"
    BusinessUnit    = "SHARED"
    DR              = "NON-DR-ENABLED"
}
```

Em seguida, especificamos o nome do log Analytics e um conjunto de soluções que analisarão a implantação. Aqui, reguardamos o monitoramento de rede, Avaliação do AD e replicação, Análise de DNS e Análise do Key Vault.

```hcl

analytics_workspace_name = "lalogs"

solution_plan_map = {
    NetworkMonitoring = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/NetworkMonitoring"
    },
    ADAssessment = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/ADAssessment"
    },
    ADReplication = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/ADReplication"
    },
    AgentHealthAssessment = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/AgentHealthAssessment"
    },
    DnsAnalytics = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/DnsAnalytics"
    },
    KeyVaultAnalytics = {
        "publisher" = "Microsoft"
        "product"   = "OMSGallery/KeyVaultAnalytics"
    }
}

```

Em seguida, configuramos os parâmetros de alerta para a central de segurança do Azure.

```hcl
# Azure Security Center Configuration
security_center = {
    contact_email   = "joe@contoso.com"
    contact_phone   = "+6500000000"
}
```

## <a name="getting-started"></a>Introdução

Depois de examinar a configuração, você pode implantar a configuração da mesma forma que implantaria um ambiente Terraform. No entanto, recomendamos que você use o Rover, que é um contêiner do Docker que permite a implantação do Windows, Linux ou MacOS. Você pode começar a usar o [repositório GitHub do Rover](https://github.com/aztfmod/rover).

## <a name="next-steps"></a>Próximos passos

A zona de aterrissagem base estabelece a base para um ambiente complexo de forma decomposta. Esta edição fornece um conjunto de recursos muito simples que podem ser estendidos por:

- Adicionar outros módulos ao plano gráfico.
- Dispor zonas de aterrissagem adicionais sobre ela.

As zonas de aterrissagem em camadas são uma boa prática para desacoplar os sistemas, o controle de versão de cada componente que você está usando e permitir a inovação e a estabilidade rápidas para sua implantação de infraestrutura como código.

Arquiteturas de referência futuras demonstrarão esse conceito para uma topologia de Hub e spoke.

> [!div class="nextstepaction"]
> [Examine o exemplo de zona de aterrissagem de base usando Terraform](https://github.com/microsoft/CloudAdoptionFramework/tree/master/ready)
