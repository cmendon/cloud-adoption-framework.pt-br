---
title: Guia de decisão de consistência de recursos
description: Saiba mais sobre a consistência de recursos ao planejar a migração do Azure.
author: doodlemania2
ms.author: dermar
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 6f995a3f6ffb26f408a45610d7d0674e02bf6a31
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806689"
---
# <a name="resource-consistency-decision-guide"></a>Guia de decisão de consistência de recursos

O [design de assinatura](../subscriptions/index.md) do Azure define como organizar seus ativos de nuvem em relação à estrutura, às práticas de contabilidade e aos requisitos de carga de trabalho da sua organização. Além desse nível de estrutura, abordar seus requisitos de política de governança organizacional em todo o seu acervo requer a habilidade de consistentemente organizar, implantar e gerenciar os recursos dentro de uma assinatura.

![Opções de consistência de recurso de plotagem da menos para a maix complexa, alinhadas aos links de salto abaixo](../../_images/decision-guides/decision-guide-resource-consistency.png)

Ir para: [Agrupamento básico](#basic-grouping) | [Consistência da implantação](#deployment-consistency) | [Consistência de política](#policy-consistency) | [Consistência hierárquica](#hierarchical-consistency) | [Consistência automatizada](#automated-consistency)

Decisões sobre o nível dos requisitos de consistência de recurso do seu acervo de nuvem são conduzidas principalmente por estes fatores: tamanho do acervo digital após a migração, requisitos empresariais ou ambientais que não se ajustam bem às suas atuais abordagens de design de assinatura ou a necessidade de impor governança ao longo do tempo após os recursos terem sido implantados.

Conforme a importância desses fatores aumenta, os benefícios de garantir consistência na implantação, no agrupamento e no gerenciamento de recursos baseados em nuvem tornam-se mais importantes. Alcançar níveis de consistência de recursos mais avançados a fim de atender a requisitos cada vez maiores requer aumentar o esforço dedicado a automação, ferramentas e imposição de consistência, o que resulta em mais tempo gasto com acompanhamento e gerenciamento de alterações.

## <a name="basic-grouping"></a>Agrupamento básico

No Azure, [grupos de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups) são um mecanismo de organização de recursos de núcleo para agrupar logicamente os recursos dentro de uma assinatura.

Os grupos de recursos atuam como contêineres para os recursos com um ciclo de vida comum e também como restrições de gerenciamento compartilhado, como os requisitos de RBAC (controle de acesso baseado em função) ou de política. Os grupos de recursos não podem ser aninhados e os recursos podem pertencer apenas a um grupo de recursos. Todas as ações do painel de controle agem em todos os recursos em um grupo de recursos. Por exemplo, a exclusão de um grupo de recursos também exclui todos os recursos daquele grupo. O padrão preferencial do gerenciamento de grupo de recursos é considerar:

1. O conteúdo do grupo de recursos foi desenvolvido em conjunto?
1. O conteúdo do grupo de recursos é gerenciado, atualizado e monitorado em conjunto e feito de acordo com as mesmas pessoas ou equipes?
1. O conteúdo do grupo de recursos foi desativado em conjunto?

Se você respondeu _NÃO_ a nenhum dos pontos acima, o recurso em questão deve ser colocado em outro lugar, em outro grupo de recursos.

> [!IMPORTANT]
> Os grupos de recursos também são específicos da região. No entanto, é comum que os recursos estejam em regiões diferentes dentro do mesmo grupo de recursos, pois eles são gerenciados juntos, conforme a descrição acima. Para obter mais informações sobre a seleção de região, confira o [Guia de decisão de regiões](../regions/index.md).

## <a name="deployment-consistency"></a>Consistência de implantação

Ao desenvolver o mecanismo de agrupamento de recurso de base, a plataforma do Azure fornece um sistema para usar os modelos para implantar seus recursos no ambiente de nuvem. Você pode usar modelos para criar organização consistente e convenções de nomenclatura ao implantar cargas de trabalho, impor esses aspectos do seu design de implantação e gerenciamento de recursos.

Os [Modelos do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) permitem que você implante repetidamente seus recursos em um estado consistente usando uma estrutura de grupo de recursos e configuração predeterminada. Modelos do Gerenciador de Recursos ajudam a definir um conjunto de padrões como base para suas implantações.

Por exemplo, você pode ter um modelo padrão para a implantação de uma carga de trabalho de servidor Web que contém duas máquinas virtuais como servidores Web combinadas com um balanceador de carga para distribuir o tráfego entre os servidores. Então você pode reutilizar esse modelo para criar um conjunto estruturalmente idêntico de máquinas virtuais e balanceadores de carga sempre que esse tipo de carga de trabalho for necessário, alterando apenas o nome da implantação e os endereços IP envolvidos.

Você também pode implantar esses modelos e integrá-los aos seus sistemas de CI/CD também por meio de programação.

## <a name="policy-consistency"></a>Consistência de política

Para garantir que as políticas de controle sejam aplicadas quando os recursos são criados, a parte do design de agrupamento de recursos envolve o uso de uma configuração comum ao implantar recursos.

Ao combinar grupos de recursos e modelos padronizados do Gerenciador de Recursos, você pode impor padrões para quais configurações são necessárias em uma implantação e quais regras da [política do Azure](https://docs.microsoft.com/azure/governance/policy/overview) são aplicadas a cada grupo de recursos ou recurso.

Por exemplo, você pode ter um requisito de que todas as máquinas virtuais implantadas dentro de sua assinatura se conectam a uma sub-rede comum gerenciada por sua equipe de TI central. Você pode criar um modelo padrão para a implantação de VMs de carga de trabalho para criar um grupo de recursos separado para a carga de trabalho e implantar as VMs necessárias de lá. Esse grupo de recursos teria uma regra de política para permitir que somente as interfaces de rede dentro do grupo de recursos fossem associados à sub-rede compartilhada.

Para obter uma discussão mais detalhada sobre impor suas decisões de política dentro de uma implantação de nuvem, consulte [Imposição de política](../policy-enforcement/index.md).

## <a name="hierarchical-consistency"></a>Consistência hierárquica

Grupos de recursos permitem que você dê suporte a níveis adicionais de hierarquia em sua organização dentro da assinatura, aplicando regras do Azure Policy e controles de acesso no nível de um grupo de recursos. Porém, à medida que o tamanho do seu acervo de nuvem aumenta, você precisa dar suporte a requisitos mais complicados de governança entre assinaturas, que podem ter suporte usando a hierarquia de empresa/departamento/conta/assinatura do Contrato Enterprise do Azure.

Os [grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups) permitem que você organize as assinaturas em estruturas organizacionais mais sofisticadas agrupando as assinaturas em uma hierarquia distinta da hierarquia de seu Contrato Enterprise. Essa hierarquia alternativa permite que você aplique os mecanismos de imposição de política e controle de acesso em várias assinaturas e os recursos que elas contêm. As hierarquias de grupo de gerenciamento podem ser usadas para combinar as assinaturas do seu acervo de nuvem com os requisitos de governança de negócios ou operações. Para obter mais informações, confira o [guia de decisão da assinatura](../subscriptions/index.md).

## <a name="automated-consistency"></a>Consistência automatizada

Para implantações de nuvem grande, a governança global se torna mais importante e mais complexa. É crucial aplicar e impor requisitos de governança ao implantar recursos automaticamente, bem como atender aos requisitos atualizados para implantações existentes.

[Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) permitem que as organizações deem suporte à governança global de instalações de nuvem grande no Azure. Blueprints se movem além dos recursos fornecidos pelos modelos padrão do Azure Resource Manager para criar orquestrações de implantação completa capaz de recursos de implantação e aplicar regras de política. O Blueprints dá suporte ao controle de versão, à capacidade de atualizar todas as assinaturas em que o blueprint foi usado e à capacidade de bloquear assinaturas implantadas para evitar a criação e a modificação não autorizadas dos recursos.

Esses pacotes permitem que as equipes de TI e de desenvolvimento implantem rapidamente novas cargas de trabalho e ativos de rede que estejam em conformidade com a alteração dos requisitos de política organizacional. Os blueprints podem ser integrados em pipelines de CI/CD para aplicar os padrões de governança revisados para implantações conforme são atualizados.

## <a name="next-steps"></a>Próximas etapas

A consistência de recursos é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
