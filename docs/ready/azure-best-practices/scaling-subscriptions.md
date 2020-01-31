---
title: Dimensionamento com várias assinaturas do Azure
description: Saiba como dimensionar com várias assinaturas do Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 6a893ce6f8620b31fcf23d8c3e8581e95035bdcf
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76799787"
---
# <a name="scale-with-multiple-azure-subscriptions"></a>Dimensionar com várias assinaturas do Azure

As organizações geralmente precisam de mais de uma assinatura do Azure como resultado de limites de recursos e outras considerações de governança. É importante ter uma estratégia para dimensionar suas assinaturas.

## <a name="production-and-nonproduction-workloads"></a>Cargas de trabalho de produção e não produções

Ao implantar sua primeira carga de trabalho de produção no Azure, você deve começar com duas assinaturas: uma para seu ambiente de produção e outra para seu ambiente de não produção (desenvolvimento/teste).

![Um modelo de assinatura básico mostrando chaves ao lado das caixas rotuladas como "produção" e "não produção"](../../_images/ready/basic-subscription-model.png)

Recomendamos esta abordagem por vários motivos:

- O Azure tem ofertas de assinatura específicas para cargas de trabalho de desenvolvimento/teste. Essas ofertas fornecem tarifas com desconto nos serviços e licenciamento do Azure.
- Seus ambientes de produção e não produtos de ti provavelmente terão conjuntos diferentes de políticas do Azure. O uso de assinaturas separadas torna simples a aplicação de cada política distinta definida no nível da assinatura.
- Você pode querer certos tipos de recursos do Azure em uma assinatura de desenvolvimento/teste para teste. Com uma assinatura separada, você pode usar esses tipos de recursos sem disponibilizá-los em seu ambiente de produção.
- Você pode usar assinaturas de desenvolvimento/teste como ambientes de área restrita isolados. Essas áreas restritas permitem que administradores e desenvolvedores criem e desmontem rapidamente conjuntos inteiros de recursos do Azure. Esse isolamento também pode ajudar com questões de segurança e de proteção de dados.
- Os limites de custo aceitáveis provavelmente variarão entre assinaturas de produção e de desenvolvimento/teste.

## <a name="other-reasons-for-multiple-subscriptions"></a>Outros motivos para várias assinaturas

Outras situações podem exigir outras assinaturas. Tenha em mente o seguinte conforme você expande sua propriedade de nuvem.

- Assinaturas têm limites diferentes para diferentes tipos de recurso. Por exemplo, o número de redes virtuais em uma assinatura é limitado. Quando uma assinatura se aproximar de qualquer um de seus limites, você precisará criar outra assinatura e colocar novos recursos lá.

  Para saber mais, confira [Assinatura e limites de serviço, cotas e restrições do Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits).

- Cada assinatura pode implementar suas próprias políticas para tipos de recursos implantáveis e regiões com suporte.

- As assinaturas em regiões de nuvem pública e regiões de nuvem soberanas ou governamental têm diferentes limitações. Geralmente, elas são orientadas por diferentes níveis de classificação de dados entre ambientes.

- Se você tiver separado completamente diferentes conjuntos de usuários por motivos de segurança ou de conformidade, poderá exigir assinaturas separadas. Por exemplo, as organizações governamentais nacionais talvez precisem limitar o acesso de uma assinatura apenas aos cidadãos.

- Assinaturas diferentes podem ter tipos diferentes de ofertas, cada uma com seus próprios termos e benefícios.

- Podem existir problemas de confiança entre os proprietários de uma assinatura e o proprietário dos recursos a serem implantados. No entanto, usar outra assinatura com Propriedade diferente pode atenuar esses problemas. no entanto, também é necessário considerar os problemas de rede e proteção de dados que surgirão nessa implantação.

- Controles geopolíticos ou financeiros rígidos podem exigir disposições financeiras separadas para assinaturas específicas. Essas preocupações podem incluir considerações sobre a soberania de dados, empresas com várias subsidiárias ou contabilidade separada e cobrança para unidades de negócios em diferentes países e moedas diferentes.

- Os recursos do Azure criados usando o modelo de implantação clássico devem ser isolados em sua própria assinatura. A segurança para recursos clássicos é diferente da segurança de recursos implantados por meio de Azure Resource Manager. As políticas do Azure não podem ser aplicadas a recursos clássicos.

- Os administradores de serviço que usam recursos clássicos têm as mesmas permissões que os proprietários de RBAC (controle de acesso baseado em função) de uma assinatura. É difícil restringir suficientemente o acesso desses administradores de serviços em uma assinatura que combina recursos clássicos e recursos do Resource Manager.

Você também pode optar por criar assinaturas adicionais por outros motivos técnicos ou empresariais específicos da sua organização. Pode haver alguns custos adicionais para entrada e saída de dados entre assinaturas.

Você pode mover muitos tipos de recursos de uma assinatura para outra ou usar implantações automatizadas para migrar recursos para outra assinatura. Para saber mais, confira [Mover recursos do Azure para outro grupo de recursos ou assinatura](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="manage-multiple-subscriptions"></a>Gerenciar várias assinaturas

Se você tiver apenas algumas assinaturas, gerenciá-las de forma independente é relativamente simples. Mas se você tiver muitas assinaturas, deverá considerar a criação de uma hierarquia de grupo de gerenciamento para simplificar o gerenciamento de suas assinaturas e recursos.

Os grupos de gerenciamento permitem o gerenciamento eficiente de acesso, políticas e conformidade para as assinaturas de uma organização. Cada grupo de gerenciamento é um contêiner para uma ou mais assinaturas.

Os grupos de gerenciamento são organizados em uma única hierarquia. Você define essa hierarquia em seu locatário do Azure Active Directory (AD do Azure) para alinhar com a estrutura e as necessidades da sua organização. O nível superior é denominado o *grupo de gerenciamento raiz*. Você pode definir até seis níveis de grupos de gerenciamento em sua hierarquia. Cada assinatura está contida apenas por um grupo de gerenciamento.

O Azure fornece quatro níveis de escopo de gerenciamento: grupos de gerenciamento, assinatura, grupos de recursos e recursos. Qualquer acesso ou política aplicada em um nível na hierarquia é herdado pelos níveis abaixo dela. Um proprietário de recurso ou proprietário de assinatura não pode alterar uma política herdada. Essa limitação ajuda a melhorar a governança.

> [!NOTE]
> Observe que a herança de marca não está disponível no momento, mas ficará disponível em breve.

Ao confiar nesse modelo de herança, você pode organizar as assinaturas em sua hierarquia para que cada uma delas siga as políticas apropriadas e os controles de segurança.

![Os quatro níveis de escopo para organizar seus recursos do Azure](../../ready/azure-setup-guide/media/organize-resources/scope-levels.png)

Qualquer acesso ou atribuição de política no grupo de gerenciamento raiz se aplica a todos os recursos no diretório. Considere cuidadosamente quais itens você define nesse escopo. Inclua apenas as atribuições que você deve ter.

Ao definir inicialmente sua hierarquia de grupo de gerenciamento, primeiro você cria o grupo de gerenciamento raiz. Mova todas as assinaturas existentes no diretório para o grupo de gerenciamento raiz. As novas assinaturas sempre são criadas no grupo de gerenciamento raiz. Você pode movê-las posteriormente para outro grupo de gerenciamento raiz.

Quando você move uma assinatura para um grupo de gerenciamento existente, ela herda as políticas e atribuições de função da hierarquia de grupo de gerenciamento acima dela. Depois de estabelecer várias assinaturas para suas cargas de trabalho do Azure, você deve criar assinaturas adicionais para conter os serviços do Azure que outras assinaturas compartilham.

![Exemplo de uma hierarquia do grupo de gerenciamento](../../_images/ready/management-group-hierarchy.png)

Para saber mais, confira [Organizar seus recursos com grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups).

## <a name="tips-for-creating-new-subscriptions"></a>Dicas para criar assinaturas

- Identifique quem será responsável pela criação de assinaturas.
- Decida quais recursos estarão em uma assinatura por padrão.
- Decida como deve ser a aparência de todas as assinaturas padrão. As considerações incluem acesso RBAC, políticas, marcas e recursos de infraestrutura.
- Se possível, [use uma entidade de serviço](https://docs.microsoft.com/azure/azure-resource-manager/grant-access-to-create-subscription) para criar assinaturas. Defina um grupo de segurança que possa solicitar novas assinaturas por meio de um fluxo de trabalho automatizado.
- Se você for um cliente EA (Contrato Enterprise), peça ao Suporte do Azure para bloquear a criação de assinaturas que não são EA para sua organização.

## <a name="related-resources"></a>Recursos relacionados

- [Conceitos fundamentais do Azure](../considerations/fundamental-concepts.md).
- [Organizar seus recursos com grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups).
- [Elevar o acesso para gerenciar todas as assinaturas e grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/role-based-access-control/elevate-access-global-admin).
- [Mover recursos do Azure para outro grupo de recursos ou assinatura](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-move-resources).

## <a name="next-steps"></a>Próximos passos

Examine as [convenções de nomenclatura e de marcação recomendadas](./naming-and-tagging.md) a serem seguidas ao implantar os recursos do Azure.

> [!div class="nextstepaction"]
> [Convenções de nomenclatura e de marcação recomendadas](./naming-and-tagging.md)
