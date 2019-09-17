---
title: Redes de perímetro
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Redes de perímetro
author: tracsman
ms.author: jonor
ms.date: 05/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: cf5b641bb894c9784f01e4e9eaae545b6b38a30d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828533"
---
# <a name="perimeter-networks"></a>Redes de perímetro

As [Redes de perímetro][perimeter-network] permitem a conectividade segura entre suas redes de nuvem e as redes locais ou do datacenter físico, bem como qualquer conectividade com a Internet. Também são conhecidas como DMZs (zonas desmilitarizadas).

Para que as redes de perímetro sejam eficazes, os pacotes de entrada devem fluir pelos dispositivos de segurança hospedados em sub-redes seguras antes de os alcançar servidores back-end. São exemplos o firewall, os IDSs (sistemas de detecção de intrusão) e os IPSs (sistemas de prevenção de intrusão). Antes de saírem da rede, pacotes direcionados à Internet das cargas de trabalho também devem passar pelos dispositivos de segurança na rede de perímetro. As finalidades deste fluxo são a imposição de políticas, a inspeção e a auditoria.

As redes de perímetro usam os seguintes recursos e serviços do Azure:

- [Redes virtuais][virtual-networks], [rotas definidas pelo usuário][user-defined-routes] e [grupos de segurança de rede][network-security-groups]
- NVAs [(soluções de virtualização de rede)][NVA]
- [Balanceador de carga do Azure][ALB]
- [Gateway de Aplicativo do Azure][AppGW] e WAF [(firewall do aplicativo Web)][AppGWWAF]
- [IPs públicos][PIP]
- [Azure Front Door][AFD] com [firewall do aplicativo Web][AFDWAF]
- [Firewall do Azure][AzFW]

> [!NOTE]
> As arquiteturas de referência do Azure fornecem modelos de exemplo que você pode usar para implementar suas próprias redes de perímetro:
>
> - [Implementar uma DMZ entre o Azure e o datacenter local](/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid)
> - [Implementar uma DMZ entre o Azure e a Internet](/azure/architecture/reference-architectures/dmz/secure-vnet-dmz)

Normalmente, suas equipes de TI e de segurança central são responsáveis por definir os requisitos de operação das redes de perímetro.

![Exemplo de rede hub e spoke][7]

O diagrama anterior mostra um exemplo de [rede hub e spoke](./hub-spoke-network-topology.md) que implementa a imposição de dois perímetros com acesso à Internet e uma rede local. Ambos os perímetros residem no hub DMZ. No hub DMZ, a rede de perímetro para a Internet pode ser expandida para dar suporte a muitas LOBs (linhas de negócios), usando vários farms de WAFs e instâncias do Firewall do Azure que ajudam a proteger as redes virtuais spoke. O hub também permite a conectividade via VPN ou Azure ExpressRoute, conforme necessário.

## <a name="virtual-networks"></a>Redes Virtuais

Redes de perímetro geralmente são criadas em uma [rede virtual][virtual-networks] com várias sub-redes para hospedar os diferentes tipos de serviços que filtram e inspecionam o tráfego de ou para a Internet por meio de NVAs, WAFs e instâncias do Gateway de Aplicativo do Azure.

## <a name="user-defined-routes"></a>Rotas definidas pelo usuário

Usando [rotas definidas pelo usuário][user-defined-routes], os clientes podem implantar firewalls, IDSs /IPSs e outras soluções de virtualização. Os clientes podem, então, encaminhar o tráfego de rede por meio dessas soluções de segurança para a imposição, auditoria e inspeção das políticas de limites de segurança. As rotas definidas pelo usuário podem ser criadas para garantir que o tráfego passe pelas VMs, NVAs e balanceadores de carga personalizados especificados.

Em um exemplo de rede hub e spoke, garantir que o tráfego gerado por máquinas virtuais que residem no spoke passe pelos dispositivos virtuais corretos no hub requer uma rota definida pelo usuário, definida nas sub-redes do spoke. Essa rota define o endereço IP de front-end do balanceador de carga interno como o próximo salto. O balanceador de carga interno distribui o tráfego interno para as soluções de virtualização (pool de back-end do balanceador de carga).

## <a name="azure-firewall"></a>Firewall do Azure

O [Firewall do Azure][AzFW] é um serviço baseado em nuvem gerenciado que ajuda a proteger seus recursos de rede virtual do Azure. Trata-se de um firewall gerenciado totalmente com estado com alta disponibilidade interna e escalabilidade de nuvem irrestrita. É possível criar, impor e registrar centralmente políticas de conectividade de rede e de aplicativo em assinaturas e redes virtuais.

O Firewall do Azure usa um endereço IP público estático para seus recursos de rede virtual. Ele permite firewalls externos para identificar o tráfego proveniente da sua rede virtual. O serviço interopera com o Azure Monitor para registro em log e análise.

## <a name="network-virtual-appliances"></a>Soluções de virtualização de rede

Redes de perímetro com acesso à Internet normalmente são gerenciadas por meio de uma instância do Firewall do Azure ou de um farm de firewalls ou [firewalls do aplicativo Web][AFDWAF].

Linhas de negócios diferentes normalmente usam muitos aplicativos Web. Esses aplicativos tendem a sofrer de diversas vulnerabilidades e explorações em potencial. Um firewall do aplicativo Web detecta ataques contra aplicativos Web (HTTP/HTTPS) com mais profundidade que um firewall genérico. Em comparação à tecnologia de firewall tradicional, firewalls do aplicativo Web têm um conjunto de recursos específicos para ajudar a proteger os servidores Web internos contra ameaças.

Uma instância do Firewall do Azure e um firewall de [solução de virtualização de rede][NVA] usam um plano de administração comum, com um conjunto de regras de segurança, para ajudar a proteger as cargas de trabalho hospedadas nos spokes e controlar o acesso a redes locais. O Firewall do Azure tem escalabilidade integrada, enquanto os firewalls do NVA podem ser dimensionados manualmente por um balanceador de carga.

Normalmente, um farm de firewalls tem software menos especializado comparado a um WAF, mas tem um escopo de aplicação mais amplo para filtrar e inspecionar qualquer tipo de tráfego de entrada e saída. Se usar uma abordagem de NVA, você poderá encontrar e implantar softwares do Azure Marketplace.

Use um conjunto de instâncias do Firewall do Azure (ou NVAs) para o tráfego originado na Internet e outro conjunto para o tráfego originado localmente. Usar apenas um conjunto de firewalls para ambos é um risco à segurança, uma vez que ele não oferece nenhuma segurança de perímetro entre os dois conjuntos de tráfego de rede. Usar camadas de firewall separadas reduz a complexidade da verificação das regras de segurança e deixa claro quais regras correspondem a quais solicitações de rede de entrada.

## <a name="azure-load-balancer"></a>Azure Load Balancer

O [Azure Load Balancer][ALB] oferece um serviço de Camada 4 (TCP, UDP) de alta disponibilidade que pode distribuir o tráfego de entrada entre instâncias de serviço definidas em um conjunto com balanceamento de carga. O tráfego enviado ao balanceador de carga dos pontos de extremidade de front-end (pontos de extremidade IP públicos ou pontos de extremidade IP privados) pode ser redistribuído com ou sem conversão de endereços para um pool de endereços IP de back-end (como NVAs ou VMs).

O Azure Load Balancer também pode investigar a integridade das diferentes instâncias do servidor. Quando uma instância não responde a uma investigação, o balanceador de carga interrompe o envio de tráfego para a instância não íntegra.

Como exemplo de uso de uma rede hub e spoke, você pode implantar um balanceador de carga externo no hub e nos spokes. No hub, o balanceador de carga encaminha com eficiência o tráfego para os serviços nos spokes. Nos spokes, os balanceadores de carga gerenciam o tráfego do aplicativo.

## <a name="azure-front-door-service"></a>Azure Front Door Service

O [Azure Front Door Service][AFD] é a plataforma de aceleração de aplicativos Web altamente disponível e escalonável da Microsoft, bem como um balanceador de carga HTTP global. Você pode usar o Azure Front Door Service para compilar, operar e expandir seus aplicativos Web dinâmicos e o conteúdo estático. Ele é executado em mais de 100 locais na borda da rede global da Microsoft.

O Azure Front Door Service oferece a seu aplicativo automação de manutenção de selo/regional unificada, automação de BCDR, informações unificadas de cliente/usuário, insights de serviço e cache. A plataforma oferece desempenho, confiabilidade e SLAs de suporte. Ela também oferece certificações de conformidade e práticas de segurança auditáveis desenvolvidas, operadas e com suporte nativo do Azure.

## <a name="application-gateway"></a>Application Gateway

O [Gateway de Aplicativo do Azure][AppGW] é uma solução de virtualização dedicada que fornece um ADC (controlador de entrega de aplicativos) gerenciado. Ele oferece vários recursos de balanceamento de carga de camada 7 ao seu aplicativo.

O Gateway de Aplicativo permite otimizar a produtividade do Web farm descarregando a terminação SSL com uso intensivo de CPU para o Gateway de Aplicativo. Ele também fornece outros recursos de roteamento de Camada 7, incluindo distribuição round robin do tráfego de entrada, afinidade de sessão, roteamento com base no caminho de URL e a capacidade de hospedar vários sites por trás de um único gateway de aplicativo baseado em cookie.

O SKU do WAF do gateway de aplicativo inclui um firewall do aplicativo Web. Essa SKU oferece proteção para aplicativos Web contra explorações e vulnerabilidades comuns da Web. Você pode configurar o Gateway de Aplicativo como um gateway voltado para a Internet, um gateway apenas interno ou uma combinação de ambos.

## <a name="public-ips"></a>IPs Públicos

Com alguns recursos do Azure, você pode associar pontos de extremidade de serviço a um endereço [IP público][PIP] para que seu recurso possa ser acessado pela Internet. Esse ponto de extremidade usa a conversão de endereços de rede (NAT) para rotear o tráfego para a porta e o endereço internos na rede virtual do Azure. Esse caminho é a principal rota para que o tráfego externo passe para dentro da rede virtual. Você pode configurar endereços IP públicos para determinar qual tráfego é passado para dentro e como e onde ele é convertido para a rede virtual.

## <a name="azure-ddos-protection-standard"></a>Proteção contra DDoS do Azure Standard

A [Proteção contra DDoS do Azure Standard][DDoS] fornece funcionalidades de mitigação adicionais à camada de [serviço Básico][DDoS] ajustadas especificamente para os recursos de rede virtual do Azure. A Proteção contra DDoS Standard é simples de habilitar e não exige nenhuma alteração no aplicativo.

Você pode ajustar as políticas de proteção por meio do monitoramento de tráfego dedicado e algoritmos de aprendizado de máquina. As políticas são aplicadas a endereços IP públicos associados aos recursos implantados em redes virtuais. Os exemplos são instâncias do Azure Load Balancer, Gateway de Aplicativo do Azure e Azure Service Fabric.

A telemetria em tempo real está disponível por meio de exibições do Azure Monitor durante um ataque e para fins de histórico. Você pode adicionar a proteção de camada de aplicativo usando o firewall do aplicativo Web no Gateway de Aplicativo do Azure. A proteção é fornecida para endereços IP públicos IPv4 do Azure.

<!-- images -->

[0]: ./images/network-redundant-equipment.png "Exemplos de sobreposição de componentes"
[1]: ./images/network-hub-spoke-high-level.png "Exemplo de alto nível de hub e spoke"
[2]: ./images/network-hub-spokes-cluster.png "Cluster de hubs e spokes"
[3]: ./images/network-spoke-to-spoke.png "Spoke a spoke"
[4]: ./images/network-hub-spoke-block-level-diagram.png "Diagrama em nível de bloco do hub e spoke"
[5]: ./images/network-users-groups-subsciptions.png "Usuários, grupos, assinaturas e projetos"
[6]: ./images/network-infrastructure-high-level.png "Diagrama de alto nível de infraestrutura"
[7]: ./images/network-highlevel-perimeter-networks.png "Diagrama de alto nível de infraestrutura"
[8]: ./images/network-vnet-peering-perimeter-neworks.png "Redes de perímetro e de emparelhamento VNet"
[9]: ./images/network-high-level-diagram-monitoring.png "Diagrama de alto nível para Monitoramento"
[10]: ./images/network-high-level-workloads.png "Diagrama de alto nível para Carga de Trabalho"

<!-- links -->

[Limits]: /azure/azure-subscription-service-limits
[Roles]: /azure/role-based-access-control/built-in-roles
[virtual-networks]: /azure/virtual-network/virtual-networks-overview
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
[perimeter-network]: /azure/best-practices-network-security
[ALB]: /azure/load-balancer/load-balancer-overview
[DDoS]: /azure/virtual-network/ddos-protection-overview
[PIP]: /azure/virtual-network/virtual-network-public-ip-address
[AFD]: /azure/frontdoor/front-door-overview
[AFDWAF]: /azure/frontdoor/waf-overview
[AppGW]: /azure/application-gateway/application-gateway-introduction
[AppGWWAF]: /azure/application-gateway/application-gateway-web-application-firewall-overview
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