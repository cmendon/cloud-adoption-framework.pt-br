---
title: Guia de decisão da assinatura
description: Saiba mais sobre assinaturas de plataforma de nuvem como um serviço principal nas migrações do Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 327077f912e916975eef08ad6613f3806a759bca
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806570"
---
# <a name="subscription-decision-guide"></a>Guia de decisão da assinatura

Um design de assinatura eficaz ajuda as organizações a estabelecer uma estrutura para organizar os ativos no Azure durante uma adoção da nuvem.

Cada recurso do Azure, como uma máquina virtual ou um banco de dados, está associado a uma assinatura. A adoção do Azure começa com a criação de uma assinatura do Azure, a associação dessa assinatura a uma conta e a implantação de recursos na assinatura. Para obter uma visão geral desses conceitos, confira [Conceitos fundamentais do Azure](../../ready/considerations/fundamental-concepts.md).

À medida que sua propriedade digital cresce no Azure, provavelmente, você precisará criar assinaturas adicionais para atender às suas necessidades. O Azure permite que você defina uma hierarquia de grupos de gerenciamento para organizar suas assinaturas e aplicar com facilidade a política certa aos recursos certos. Para obter mais informações, confira [Dimensionamento com várias assinaturas do Azure](../../ready/azure-best-practices/scaling-subscriptions.md).

Alguns exemplos básicos do uso de grupos de gerenciamento para separar diferentes cargas de trabalho incluem:

- **Cargas de trabalho de produção versus cargas de trabalho de não produção:** algumas empresas criam grupos de gerenciamento para separar suas assinaturas de produção e não produção. Os grupos de gerenciamento permitem que esses clientes gerenciem mais facilmente funções e políticas. Por exemplo, uma assinatura não de produção pode permitir aos desenvolvedores ter acesso de **colaborador**, porém, em produção, eles têm apenas acesso de **leitor**.
- **Serviços internos vs. externos:** Assim como ocorre com cargas de trabalho produção versus não produção, as empresas costumam ter requisitos' políticas e funções diferentes para serviços internos e externos voltados ao cliente.

Este guia de decisão ajuda você a considerar diferentes abordagens para organizar sua hierarquia de grupos de gerenciamento.

## <a name="subscription-design-patterns"></a>Padrões de design de assinatura

Como cada organização é diferente, os grupos de gerenciamento do Azure foram projetados para serem flexíveis. A modelagem de sua propriedade de nuvem para refletir a hierarquia de sua organização ajuda você a definir e aplicar políticas em níveis mais altos da hierarquia e depender da herança para garantir que essas políticas sejam aplicadas automaticamente aos grupos de gerenciamento em níveis inferiores na hierarquia. Embora as assinaturas possam ser movidas entre diferentes grupos de gerenciamento, é útil projetar uma hierarquia inicial de grupos de gerenciamento que reflita suas necessidades organizacionais previstas.

Antes de finalizar o design da assinatura, considere também como as considerações sobre [consistência de recursos](../resource-consistency/index.md) podem influenciar suas escolhas de design.

> [!NOTE]
> Os EAs (Contratos Enterprise) do Azure permitem que você defina outra hierarquia organizacional para fins de cobrança. Essa hierarquia é distinta da hierarquia de grupos de gerenciamento, que se concentra em fornecer um modelo de herança para aplicar com facilidade políticas e controle de acesso adequados aos seus recursos.

Os seguintes padrões de assinatura refletem um aumento inicial na sofisticação do design da assinatura, seguido por várias hierarquias mais avançadas que podem se alinhar bem à sua organização:

### <a name="single-subscription"></a>Assinatura única

Uma assinatura única por conta pode ser suficiente para organizações que precisam implantar um pequeno número de ativos hospedados na nuvem. Esse é o primeiro padrão de assinatura que você implementará no início do processo de adoção da nuvem, permitindo que implantações de prova de conceito ou experimentais em pequena escala explorem as funcionalidades da nuvem.

### <a name="production-and-nonproduction-pattern"></a>Padrão de produção e não produção

Quando você estiver pronto para implantar uma carga de trabalho em um ambiente de produção, adicione uma outra assinatura. Isso ajuda você a manter seus dados de produção e outros ativos fora dos ambientes de desenvolvimento/teste. Você também pode aplicar com facilidade dois diferentes conjuntos de políticas aos recursos nas duas assinaturas.

![Padrão de assinatura de produção e não produção](../../_images/ready/basic-subscription-model.png)

### <a name="workload-separation-pattern"></a>Padrão de separação de carga de trabalho

Conforme uma organização adiciona novas cargas de trabalho à nuvem, a propriedade diferente de assinaturas ou a separação básica de responsabilidade pode resultar em várias assinaturas nos grupos de gerenciamento de produção e não produção. Embora essa abordagem forneça uma separação básica de cargas de trabalho, ela não aproveita de forma significativa o modelo de herança para aplicar as políticas automaticamente a um subconjunto das assinaturas.

![Padrão de separação de carga de trabalho](../../_images/ready/management-group-hierarchy.png)

### <a name="application-category-pattern"></a>Padrão de categoria do aplicativo

À medida que aumenta o volume de nuvem de uma organização, normalmente, assinaturas adicionais são criadas para dar suporte a aplicativos com diferenças fundamentais em importância comercial, requisitos de conformidade, controles de acesso ou necessidades de proteção de dados. Baseando-se no padrão de assinatura de produção e não produção, as assinaturas que dão suporte a essas categorias de aplicativos são organizadas no grupo de gerenciamento de produção ou não produção, conforme aplicável. Essas assinaturas são normalmente pertencentes e administradas pela equipe central de operações de TI.

![Padrão de categoria do aplicativo](../../_images/infra-subscriptions/application.png)

Cada organização categorizará seus aplicativos de forma diferente, em geral, separando as assinaturas com base em serviços ou aplicativos específicos ou de acordo com arquétipos de aplicativo. Essa categorização costuma ser desenvolvida para dar suporte a cargas de trabalho que provavelmente consomem a maior parte dos limites de recurso de uma assinatura ou separar cargas de trabalho críticas a fim de garantir que elas não estejam competindo com outras cargas de trabalho abaixo desses limites. Algumas cargas de trabalho que podem justificar uma assinatura separada de acordo com esse padrão incluem:

- Cargas de trabalho críticas.
- Aplicativos que fazem parte do COGS (“Custo dos produtos vendidos”) em sua empresa. Exemplo: cada instância do widget da Empresa X contém um módulo do Azure IoT que envia telemetria. Isso pode exigir uma assinatura dedicada para fins de contabilidade/governança como parte do COGS.
- Aplicativos sujeitos a requisitos regulatórios, como HIPAA ou FedRAMP.

### <a name="functional-pattern"></a>Padrão funcional

O padrão funcional organiza assinaturas e contas ao longo de linhas funcionais, como finanças, vendas ou suporte de TI, usando uma hierarquia de grupos de gerenciamento.

### <a name="business-unit-pattern"></a>Padrão da unidade de negócios

O padrão de unidade de negócios agrupa assinaturas e contas com base na categoria de lucros e perdas, na unidade de negócios, na divisão, no centro de lucro ou em uma estrutura de negócios semelhante usando uma hierarquia de grupos de gerenciamento.

### <a name="geographic-pattern"></a>Padrão geográfico

Para as organizações com operações globais, o padrão geográfico agrupa assinaturas e contas com base em regiões geográficas usando uma hierarquia de grupos de gerenciamento.

## <a name="mixed-patterns"></a>Padrões mistos

As hierarquias de grupos de gerenciamento podem ter até seis níveis de profundidade. Isso fornece a flexibilidade para criar uma hierarquia que combine vários desses padrões de acordo com suas necessidades organizacionais. Por exemplo, o diagrama abaixo mostra uma hierarquia organizacional que combina um padrão de unidade de negócios com um padrão geográfico.

![Padrão de assinatura mista](../../_images/infra-subscriptions/mixed.png)

## <a name="related-resources"></a>Recursos relacionados

- [Gerenciamento de acesso aos recursos no Azure](../../govern/resource-consistency/resource-access-management.md)
- [Várias camadas de governança em empresas de grande porte](../../govern/guides/complex/multiple-layers-of-governance.md)
- [Várias regiões geográficas](../regions/index.md)

## <a name="next-steps"></a>Próximas etapas

O design de assinatura é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
