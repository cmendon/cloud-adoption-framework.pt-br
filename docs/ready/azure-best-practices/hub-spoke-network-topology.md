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
ms.openlocfilehash: 48f73d7c7f2e7f3bba8183464c786a3e0744807c
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905486"
---
# <a name="hub-and-spoke-network-topology"></a>Topologia de rede hub e spoke

*Hub e spoke* é um modelo de rede para o gerenciamento mais eficiente de requisitos comuns de comunicação ou segurança. Ele também ajuda a evitar limitações de assinatura do Azure. Esse modelo soluciona as seguintes preocupações:

- **Redução de custos e eficiência do gerenciamento**. A centralização de serviços que podem ser compartilhados por diversas cargas de trabalho, tais como NVAs (soluções de virtualização de rede) e servidores DNS em uma localização permite que a TI minimize recursos redundantes e esforços de gerenciamento.
- **Superar os limites das assinaturas**. Grandes cargas de trabalho baseadas em nuvem podem exigir o uso de mais recursos que são permitidos em uma única assinatura do Azure. (Confira [limites de assinatura][Limits].) Redes virtuais de carga de trabalho de emparelhamento de assinaturas diferentes para um hub central podem superar esses limites.
- **Separação de preocupações**. Você pode implantar cargas de trabalho individuais entre as equipes de TI centrais e as equipes de cargas de trabalho.

Ativos de nuvem menores podem não se beneficiar da estrutura e dos recursos adicionais oferecidos por esse modelo. Mas esforços de adoção de nuvem maiores deverão considerar a implementação de uma arquitetura de rede hub e spoke se tiverem qualquer uma das preocupações listadas anteriormente.

> [!NOTE]
> O site de Arquiteturas de Referência do Azure contém modelos de exemplo que você pode usar como base para implementar suas próprias redes hub e spoke:
>
> - [Implementar uma topologia de rede hub e spoke no Azure](/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
> - [Implementar uma topologia de rede hub e spoke com serviços compartilhados no Azure](/azure/architecture/reference-architectures/hybrid-networking/shared-services)

## <a name="overview"></a>Visão geral

![Exemplos de uma topologia de rede hub e spoke][1]

Conforme mostrado no diagrama, o Azure dá suporte a dois tipos de design hub e spoke. Ele dá suporte à comunicação, aos recursos compartilhados e à política de segurança centralizada ("Hub de VNet" no diagrama) ou a um tipo de WAN Virtual ("WAN Virtual" no diagrama) para comunicações de branch a branch de grande escala e de branch para o Azure.

Um hub é uma zona central da rede que controla e inspeciona o tráfego de entrada ou saída entre as zonas: Internet, local e spokes. A topologia hub e spoke proporciona ao departamento de TI uma maneira eficiente de impor políticas de segurança em uma localização central. Ela também reduz a possibilidade de erros de configuração e exposição.

Frequentemente, o hub contém os componentes de serviço comuns consumidos pelos spokes. Os exemplos a seguir são serviços centrais comuns:

- A infraestrutura do Active Directory do Windows Server, necessária para a autenticação de usuários de terceiros que acessam de redes não confiáveis antes de obterem acesso às cargas de trabalho no spoke. Ela inclui os Serviços de Federação do Active Directory (AD FS).
- Um serviço DNS para resolver nomes para a carga de trabalho nos spokes, para acessar recursos locais e na Internet se o [DNS do Azure][DNS] não for usado.
- Uma infraestrutura de chave pública (PKI) para implementar logon único em cargas de trabalho.
- Controle de fluxo de tráfego TCP e UDP entre as zonas da rede de spoke e a Internet.
- Controle de fluxo entre os spokes e o local.
- Se necessário, fluxo de controle entre um spoke e outro.

Você pode minimizar a redundância, simplificar o gerenciamento e reduzir o custo geral usando a infraestrutura de hub compartilhado para dar suporte a vários spokes.

A função de cada spoke pode ser hospedar diferentes tipos de cargas de trabalho. Os spokes também fornecem uma abordagem modular para implantações repetíveis das mesmas cargas de trabalho. Os exemplos são desenvolvimento e teste, teste de aceitação do usuário, preparo e produção.

Os spokes também podem separar e habilitar diferentes grupos na sua organização. Um exemplo são os grupos Azure DevOps. Dentro de um spoke, é possível implantar uma carga de trabalho básica ou cargas de trabalho complexas de várias camadas com controle de tráfego entre as camadas.

## <a name="subscription-limits-and-multiple-hubs"></a>Limites de assinatura e vários hubs

No Azure, cada componente, seja qual for o tipo, é implantado em uma assinatura do Azure. O isolamento dos componentes do Azure em diferentes assinaturas do Azure pode atender aos requisitos de diferentes linhas de negócios, como configurar níveis diferenciados de acesso e autorização.

Uma única implementação de hub e spoke pode ser expandida para um grande número de spokes. Mas, assim como acontece com todos os sistemas de TI, há limites de plataformas. A implantação de hub está limitada a uma assinatura específica do Azure, que tem restrições e limites. Um exemplo é um número máximo de emparelhamentos de rede virtual. Confira [Assinatura do Azure e limites de serviço, cotas e restrições][Limits] para conhecer os detalhes.

Em casos em que limites podem ser um problema, a arquitetura pode ser expandida ainda mais estendendo o modelo de um único hub e spoke para um cluster de hubs e spokes. É possível interconectar vários hubs em uma ou mais regiões do Azure usando emparelhamento de rede virtual, Azure ExpressRoute, WAN Virtual ou VPN site a site.

![Cluster de hubs e spokes][2]

A introdução de vários hubs aumenta a sobrecarga de gerenciamento e o custo do sistema. Isso só é justificado pela escalabilidade, pelos limites do sistema ou pela redundância e replicação regional para desempenho do usuário ou a recuperação de desastre. Em cenários que exigem vários hubs, todos os hubs devem buscar oferecer o mesmo conjunto de serviços para facilidade operacional.

## <a name="interconnection-between-spokes"></a>Interconexão entre spokes

É possível implementar cargas de trabalho complexas de várias camadas em um único spoke. Você pode implementar configurações de várias camadas usando sub-redes (uma para cada camada) na mesma rede virtual e usando grupos de segurança de rede para filtrar os fluxos.

Um arquiteto talvez queira implantar uma carga de trabalho de várias camadas em várias redes virtuais. Com um emparelhamento de redes virtuais, os spokes podem se conectar a outros spokes no mesmo hub ou em hubs diferentes.

Um exemplo típico desse cenário é o caso em que os servidores de processamento do aplicativo estão em um spoke ou rede virtual. O banco de dados é implantado em um spoke ou em uma rede virtual diferente. Nesse caso, é fácil interconectar os spokes ao emparelhamento de redes virtuais e evitar trânsito pelo hub. A solução é executar uma análise cuidadosa de arquitetura e segurança para garantir que ignorar o hub não ignorará pontos de auditoria ou segurança importantes que possam existir somente no hub.

![Spokes conectando-se uns aos outros e a um hub][3]

Os spokes também podem ser interconectados a um spoke que atue como um hub. Essa abordagem cria uma hierarquia de dois níveis: o spoke no nível mais alto (nível 0) torna-se o hub dos spokes inferiores (nível 1) da hierarquia. Os spokes de uma implementação de hub e spoke são necessários para encaminhar o tráfego ao hub central para que o tráfego possa seguir até seu destino na rede local ou na Internet pública. Uma arquitetura com dois níveis de hubs apresenta roteamento complexo que remove os benefícios de uma relação de hub e spoke simples.

<!-- images -->

[0]: ./images/network-redundant-equipment.png "Exemplos de sobreposição de componentes"
[1]: ./images/network-hub-spoke-high-level.png "Exemplo de alto nível de hub e spoke"
[2]: ./images/network-hub-spokes-cluster.png "Cluster de hubs e spokes"
[3]: ./images/network-spoke-to-spoke.png "Spoke a spoke"
[4]: ./images/network-hub-spoke-block-level-diagram.png "Diagrama de nível de blocos de hub e spoke"
[5]: ./images/network-users-groups-subsciptions.png "Usuários, grupos, assinaturas e projetos"
[6]: ./images/network-infrastructure-high-level.png "Diagrama de alto nível de infraestrutura"
[7]: ./images/network-highlevel-perimeter-networks.png "Diagrama de alto nível de infraestrutura"
[8]: ./images/network-vnet-peering-perimeter-neworks.png "Emparelhamento de rede virtual e redes de perímetro"
[9]: ./images/network-high-level-diagram-monitoring.png "Diagrama de alto nível para monitoramento"
[10]: ./images/network-high-level-workloads.png "Diagrama de alto nível para carga de trabalho"

<!-- links -->

[Limits]: /azure/azure-subscription-service-limits
[Roles]: /azure/role-based-access-control/built-in-roles
[VNet]: /azure/virtual-network/virtual-networks-overview
[network-security-groups]: /azure/virtual-network/virtual-networks-nsg
[DNS]: /azure/dns/dns-overview
[PrivateDNS]: /azure/dns/private-dns-overview
[VNetPeering]: /azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: /azure/virtual-network/virtual-networks-udr-overview
[RBAC]: /azure/role-based-access-control/overview
[azure-ad]: /azure/active-directory/active-directory-whatis
[VPN]: /azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: /azure/expressroute/expressroute-introduction
[ExRD]: /azure/expressroute/expressroute-erdirect-about
[vWAN]: /azure/virtual-wan/virtual-wan-about
[NVA]: /azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: /azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: /azure/azure-resource-manager/resource-group-overview
[DMZ]: /azure/best-practices-network-security
[ALB]: /azure/load-balancer/load-balancer-overview
[PIP]: /azure/virtual-network/resource-groups-networking#public-ip-address
[AFD]: /azure/frontdoor/front-door-overview
[AppGW]: /azure/application-gateway/application-gateway-introduction
[WAF]: /azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: /azure/monitoring-and-diagnostics/
[ActLog]: /azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: /azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: /azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: /azure/operations-management-suite/operations-management-suite-overview
[NPM]: /azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: /azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: /azure/app-service/
[HDI]: /azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: /azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: /azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: /azure/traffic-manager/traffic-manager-overview
