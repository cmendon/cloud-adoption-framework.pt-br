---
title: Topologia de rede hub e spoke
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Topologia de rede hub e spoke
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: fcbcda63ff080de234075f0a8784731e591ca0f3
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549019"
---
# <a name="hub-and-spoke-network-topology"></a>Topologia de rede hub e spoke

*Hub e spoke* é um modelo de rede para um gerenciamento mais eficiente de requisitos comuns de comunicação ou segurança. Ele também ajuda a evitar limitações de assinatura do Azure. Esse modelo aborda as seguintes preocupações:

- **Economia de custos e eficiência de gerenciamento**. Centralizar serviços que podem ser compartilhados por várias cargas de trabalho, como NVAs (soluções de virtualização de rede) e servidores DNS, em um único local permite que a ti minimize recursos redundantes e esforço de gerenciamento.
- **Superando limites de assinaturas**. Grandes cargas de trabalho baseadas em nuvem podem exigir o uso de mais recursos do que o permitido em uma única assinatura do Azure. As redes virtuais de carga de trabalho de emparelhamento de assinaturas diferentes para um hub central podem superar esses limites. Para obter mais informações, consulte [limites de assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits).
- **Separação de preocupações**. Você pode implantar cargas de trabalho individuais entre as equipes de ti central e as equipes de carga de trabalho.

Os bens de nuvem menores podem não se beneficiar da estrutura e dos recursos adicionados oferecidos por esse modelo. Mas esforços de adoção de nuvem maiores devem considerar a implementação de uma arquitetura de rede hub e spoke se elas tiverem qualquer uma das preocupações listadas anteriormente.

> [!NOTE]
> O site arquiteturas de referência do Azure contém modelos de exemplo que você pode usar como base para implementar suas próprias redes de Hub e spoke:
>
> - [Implementar uma topologia de rede hub e spoke no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
> - [Implementar uma topologia de rede hub e spoke com serviços compartilhados no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services)

## <a name="overview"></a>Visão Geral

![Exemplos de uma topologia de rede hub e spoke][1]

Conforme mostrado no diagrama, o Azure dá suporte a dois tipos de design de Hub e spoke. Ele dá suporte à comunicação, recursos compartilhados e à política de segurança centralizada ("Hub de VNet" no diagrama) ou um tipo de WAN virtual ("WAN virtual" no diagrama) para comunicações de ramificação para ramificação de grande escala e de ramificação para o Azure.

Um hub é uma zona de rede central que controla e inspeciona o tráfego de entrada ou saída entre zonas: Internet, local e spokes. A topologia hub e spoke dá ao seu departamento de ti uma maneira eficaz de impor políticas de segurança em um local central. Ele também reduz o potencial de configuração e exposição incorretas.

O Hub geralmente contém os componentes de serviço comuns que os spokes consomem. Os exemplos a seguir são serviços centrais comuns:

- A infraestrutura de Active Directory do Windows Server, necessária para autenticação de usuário de terceiros que obtêm acesso de redes não confiáveis antes de obterem acesso às cargas de trabalho no spoke. Ele inclui o Serviços de Federação do Active Directory (AD FS) relacionado (AD FS).
- Um serviço DNS para resolver o nome da carga de trabalho nos spokes para acessar recursos locais e na Internet se o [DNS do Azure](https://docs.microsoft.com/azure/dns/dns-overview) não for usado.
- Uma PKI (infraestrutura de chave pública), para implementar o logon único em cargas de trabalho.
- Controle de fluxo do tráfego TCP e UDP entre as zonas de rede do spoke e a Internet.
- Controle de fluxo entre os spokes e o local.
- Se necessário, o controle de fluxo entre um spoke e outro.

Você pode minimizar a redundância, simplificar o gerenciamento e reduzir o custo geral usando a infraestrutura de Hub compartilhado para dar suporte a vários spokes.

A função de cada spoke pode ser hospedar diferentes tipos de cargas de trabalho. Os spokes também fornecem uma abordagem modular para implantações reproduzíveis das mesmas cargas de trabalho. Os exemplos são desenvolvimento e teste, teste de aceitação do usuário, preparo e produção.

Os spokes também podem separar e habilitar grupos diferentes em sua organização. Um exemplo é o Azure DevOps groups. Dentro de um spoke, é possível implantar uma carga de trabalho básica ou cargas de trabalho multicamadas complexas com controle de tráfego entre as camadas.

## <a name="subscription-limits-and-multiple-hubs"></a>Limites de assinatura e vários hubs

No Azure, todos os componentes, independentemente do tipo, são implantados em uma assinatura do Azure. O isolamento dos componentes do Azure em diferentes assinaturas do Azure pode atender aos requisitos de diferentes linhas de negócios, como a configuração de níveis diferenciados de acesso e autorização.

Uma única implementação de Hub e spoke pode escalar verticalmente para um grande número de spokes. Mas, como em todos os sistemas de ti, há limites de plataforma. A implantação do Hub está associada a uma assinatura específica do Azure, que tem restrições e limites. (Um exemplo é um número máximo de emparelhamentos de rede virtual. Consulte [assinatura do Azure e limites de serviço, cotas e restrições] [limites] para obter detalhes).

Nos casos em que os limites podem ser um problema, você pode escalar verticalmente a arquitetura ampliando o modelo de um único Hub e spoke para um cluster de hubs e spokes. Você pode interconectar vários hubs em uma ou mais regiões do Azure usando o emparelhamento de rede virtual, o Azure ExpressRoute, uma WAN virtual ou uma VPN site a site.

![Cluster de hubs e spokes][2]

A introdução de vários hubs aumenta a sobrecarga de custo e de gerenciamento do sistema. Isso só é justificado por escalabilidade, limites do sistema ou redundância e replicação regional para desempenho do usuário ou recuperação de desastre. Em cenários que exigem vários hubs, todos os hubs devem se esforçar para oferecer o mesmo conjunto de serviços para facilitar a operação.

## <a name="interconnection-between-spokes"></a>Interconexão entre spokes

É possível implementar cargas de trabalho de várias camadas complexas em um único spoke. Você pode implementar configurações de várias camadas usando sub-redes (uma para cada camada) na mesma rede virtual e usando grupos de segurança de rede para filtrar os fluxos.

Um arquiteto pode querer implantar uma carga de trabalho multicamada em várias redes virtuais. Com o emparelhamento de rede virtual, os spokes podem se conectar a outros spokes no mesmo Hub ou em hubs diferentes.

Um exemplo típico desse cenário é o caso em que os servidores de processamento de aplicativos estão em um spoke ou em uma rede virtual. O banco de dados é implantado em uma rede virtual ou spoke diferente. Nesse caso, é fácil interconectar os spokes com o emparelhamento de rede virtual e evitar o tráfego por meio do Hub. A solução é executar uma análise cuidadosa e uma revisão de segurança para garantir que ignorar o Hub não ignore pontos de segurança ou de auditoria importantes que possam existir apenas no Hub.

![Spokes conectando uns aos outros e a um hub][3]

Os spokes também podem ser interconectados a um spoke que atua como um Hub. Essa abordagem cria uma hierarquia de dois níveis: o spoke no nível superior (nível 0) torna-se o Hub de spokes inferiores (nível 1) da hierarquia. Os spokes de uma implementação de Hub e spoke são necessários para encaminhar o tráfego para o hub central para que o tráfego possa transitar para seu destino na rede local ou na Internet pública. Uma arquitetura com dois níveis de hubs introduz um roteamento complexo que remove os benefícios de uma relação hub-e-spoke simples.

<!-- images -->

[0]: ../../_images/azure-best-practices/network-redundant-equipment.png "Exemplos de sobreposição de componente"
[1]: ../../_images/azure-best-practices/network-hub-spoke-high-level.png "Exemplo de alto nível de Hub e spoke"
[2]: ../../_images/azure-best-practices/network-hub-spokes-cluster.png "Cluster de hubs e spokes"
[3]: ../../_images/azure-best-practices/network-spoke-to-spoke.png "Spoke a spoke"
[4]: ../../_images/azure-best-practices/network-hub-spoke-block-level-diagram.png "Diagrama de nível de bloco do Hub e do spoke"
[5]: ../../_images/azure-best-practices/network-users-groups-subscriptions.png "Usuários, grupos, assinaturas e projetos"
[6]: ../../_images/azure-best-practices/network-infrastructure-high-level.png "Diagrama de infraestrutura de alto nível"
[7]: ../../_images/azure-best-practices/network-high-level-perimeter-networks.png "Diagrama de infraestrutura de alto nível"
[8]: ../../_images/azure-best-practices/network-vnet-peering-perimeter-networks.png "Emparelhamento de rede virtual e redes de perímetro"
[9]: ../../_images/azure-best-practices/network-high-level-diagram-monitoring.png "Diagrama de alto nível para monitoramento"
[10]: ../../_images/azure-best-practices/network-high-level-workloads.png "Diagrama de alto nível para carga de trabalho"

<!-- links -->

[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[VNetPeering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[azure-ad]: https://docs.microsoft.com/azure/active-directory/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[vWAN]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[SubMgmt]: ../../reference/azure-scaffold.md
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview
[DMZ]: https://docs.microsoft.com/azure/best-practices-network-security
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/resource-groups-networking#public-ip-address
[AFD]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction
[WAF]: https://docs.microsoft.com/azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/
[ActLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: https://docs.microsoft.com/azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview
[NPM]: https://docs.microsoft.com/azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: https://docs.microsoft.com/azure/app-service/
[HDI]: https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview
