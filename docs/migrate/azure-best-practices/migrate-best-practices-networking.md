---
title: Práticas recomendadas para configurar a rede para cargas de trabalho migradas para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Depois de migrar para o Azure, obtenha as práticas recomendadas para configurar a rede para suas cargas de trabalho migradas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 863f1270679a849d53bce04a8c2fded6019fc65f
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548531"
---
# <a name="best-practices-to-set-up-networking-for-workloads-migrated-to-azure"></a>Práticas recomendadas para configurar a rede para cargas de trabalho migradas para o Azure

Ao planejar e projetar a migração, além da migração em si, uma das etapas mais críticas é o design e a implementação da rede do Azure. Este artigo descreve as práticas recomendadas para a rede ao migrar para as implementações de IaaS e PaaS no Azure.

> [!IMPORTANT]
> As práticas recomendadas e as opiniões descritas neste artigo baseiam-se na plataforma e nos recursos de serviço do Azure disponíveis no momento da gravação. Recursos e funcionalidades mudam com o passar do tempo. Nem todas as recomendações podem ser aplicáveis para sua implantação, portanto, selecione aquelas que funcionam para você.

## <a name="design-virtual-networks"></a>Projetar redes virtuais

O Azure fornece redes virtuais (VNets):

- Os recursos do Azure comunicam-se de forma privada, direta e segura entre si em VNets.
- Você pode configurar conexões de ponto de extremidade no VNets para VMs e serviços que exigem comunicação com a Internet.
- Uma VNet é um isolamento lógico da nuvem do Azure que é dedicada à sua assinatura.
- Você pode implementar vários VNets em cada assinatura do Azure e região do Azure.
- Cada VNet é isolada de outros VNets.
- VNets pode conter endereços IP públicos e privados definidos no [RFC 1918](https://tools.ietf.org/html/rfc1918), expresso em notação CIDR. Os endereços IP públicos especificados no espaço de endereço de uma VNet não são diretamente acessíveis pela Internet.
- O VNets pode se conectar entre si usando o emparelhamento VNet. VNets conectados podem estar na mesma região ou em regiões diferentes. Assim, os recursos em uma VNet podem se conectar a recursos em outros VNets.
- Por padrão, o Azure roteia o tráfego entre sub-redes em uma VNet, VNets conectadas, redes locais e a Internet.

Ao planejar sua topologia de VNet, você deve considerar como organizar espaços de endereço IP, como implementar uma rede hub e spoke, como segmentar VNets em sub-redes, configurar o DNS e implementar zonas de disponibilidade do Azure.

## <a name="best-practice-plan-ip-addressing"></a>Prática recomendada: planejar o endereçamento IP

Quando você cria VNets como parte de sua migração, é importante planejar o espaço de endereço IP da VNet.

- Você deve atribuir um espaço de endereço que não seja maior do que um intervalo CIDR de/16 para cada VNet. O VNets permite o uso de endereços IP 65536 e a atribuição de um prefixo menor que/16 resultaria na perda de endereços IP. É importante não desperdiçar endereços IP, mesmo que eles estejam nos intervalos privados definidos pela RFC 1918.
- O espaço de endereço da VNet não deve se sobrepor a intervalos de rede locais.
- A conversão de endereços de rede (NAT) não deve ser usada.
- Endereços sobrepostos podem causar redes que não podem ser conectadas e roteadas que não funcionam corretamente. Se as redes se sobrepõem, você precisará recriar a rede ou usar a NAT (conversão de endereços de rede).

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) do Azure VNets.
- [Leia](https://docs.microsoft.com/azure/virtual-network/virtual-networks-faq) as perguntas frequentes sobre rede.
- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-subscription-service-limits?toc=%2fazure%2fvirtual-network%2ftoc.json#networking-limits) as limitações de rede.

## <a name="best-practice-implement-a-hub-and-spoke-network-topology"></a>Prática recomendada: implementar uma topologia de rede hub e spoke

Uma topologia de rede hub e spoke isola as cargas de trabalho enquanto compartilha serviços como identidade e segurança.

- O Hub é uma VNet do Azure que atua como um ponto central de conectividade.
- Os spokes são VNets que se conectam à VNet do Hub usando o emparelhamento VNet.
- Os serviços compartilhados são implantados no Hub, enquanto as cargas de trabalho individuais são implantadas como spokes.

Considere o seguinte:

- A implementação de uma topologia hub e spoke no Azure centraliza serviços comuns, como conexões a redes locais, firewalls e isolamento entre o VNets. A VNet do Hub fornece um ponto central de conectividade para redes locais e um local para os serviços de host usados por cargas de trabalho hospedadas no spoke VNets.
- Uma configuração de Hub e spoke normalmente é usada por empresas maiores. Redes menores podem considerar um design mais simples para economizar em custos e complexidade.
- O spoke VNets pode ser usado para isolar cargas de trabalho, com cada spoke gerenciado separadamente de outros spokes. Cada carga de trabalho pode incluir várias camadas e várias sub-redes conectadas com os balanceadores de carga do Azure.
- Os VNets Hub e spoke podem ser implementados em diferentes grupos de recursos e até mesmo em assinaturas diferentes. Quando você emparelha redes virtuais em assinaturas diferentes, as assinaturas podem ser associadas aos locatários iguais ou diferentes Azure Active Directory (Azure AD). Isso permite o gerenciamento descentralizado de cada carga de trabalho, enquanto compartilha serviços mantidos na rede do Hub.

*Hub de ](./media/migrate-best-practices-networking/hub-spoke.png)
 de gerenciamento de ![Change e topologia spoke*

**Saiba Mais:**

- [Leia sobre](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke) uma topologia de Hub e spoke.
- Obtenha recomendações de rede para executar VMs [Windows](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/windows-vm) e [Linux](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/linux-vm) do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) Emparelhamento VNet.

## <a name="best-practice-design-subnets"></a>Prática recomendada: criar sub-redes

Para fornecer isolamento em uma VNet, você o segmenta em uma ou mais sub-redes e aloca uma parte do espaço de endereço da VNet para cada sub-rede.

- Você pode criar várias sub-redes em cada VNet.
- Por padrão, o Azure roteia o tráfego de rede entre todas as sub-redes em uma VNet.
- Suas decisões de sub-rede são baseadas em seus requisitos técnicos e organizacionais.
- Você cria sub-redes usando a notação CIDR.
- Ao decidir sobre o intervalo de rede para sub-redes, é importante observar que o Azure retém cinco endereços IP de cada sub-rede que não pode ser usada. Por exemplo, se você criar a menor sub-rede disponível de/29 (com oito endereços IP), o Azure manterá cinco endereços, portanto, você terá apenas três endereços utilizáveis que podem ser atribuídos a hosts na sub-rede.
- Na maioria dos casos, é recomendável usar/28 como a menor sub-rede.

**Exemplo:**

A tabela mostra um exemplo de uma VNet com um espaço de endereço de 10.245.16.0/20 segmentado em sub-redes, para uma migração planejada.

**Sub-rede** | **CIDR** | **Atende** | **Uso**
--- | --- | --- | ---
DEV-FE-EUS2 | 10.245.16.0/22 | 1019 | VMs de camada front-end/web
DEV-APP-EUS2 | 10.245.20.0/22 | 1019 | VMs da camada de aplicativo
DEV-DB-EUS2 | 10.245.24.0/23 | 507 | VMs de banco de dados

**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm#segmentation) criar sub-redes.
- [Saiba como](https://docs.microsoft.com/azure/migrate/contoso-migration-infrastructure) uma empresa fictícia (contoso) preparou sua infraestrutura de rede para migração.

## <a name="best-practice-set-up-a-dns-server"></a>Prática recomendada: configurar um servidor DNS

O Azure adiciona um servidor DNS por padrão quando você implanta uma VNet. Isso permite que você crie rapidamente VNets e implante recursos. No entanto, esse servidor DNS fornece apenas serviços para os recursos nessa VNet. Se você quiser conectar vários VNets juntos ou se conectar a um servidor local do VNets, você precisará de recursos de resolução de nome adicionais. Por exemplo, talvez seja necessário Active Directory para resolver nomes DNS entre redes virtuais. Para fazer isso, você implanta seu próprio servidor DNS personalizado no Azure.

- Os servidores DNS em uma VNet podem encaminhar consultas DNS para os resolvedores recursivos no Azure. Isso permite que você resolva os nomes de host dentro dessa VNet. Por exemplo, um controlador de domínio em execução no Azure pode responder a consultas DNS para seus próprios domínios e encaminhar todas as outras consultas para o Azure.
- O encaminhamento de DNS permite que as VMs vejam os recursos locais (por meio do controlador de domínio) e os nomes de host fornecidos pelo Azure (usando o encaminhador). O acesso aos resolvedores recursivos no Azure é fornecido usando o endereço IP virtual 168.63.129.16.
- O encaminhamento de DNS também permite a resolução de DNS entre VNets e permite que computadores locais resolvam nomes de host fornecidos pelo Azure.
  - Para resolver um nome de host da VM, a VM do servidor DNS deve residir na mesma VNet e ser configurada para encaminhar consultas de nome de host para o Azure.
  - Como o sufixo DNS é diferente em cada VNet, você pode usar regras de encaminhamento condicional para enviar consultas DNS para a VNet correta para resolução.
- Ao usar seus próprios servidores DNS, você pode especificar vários servidores DNS para cada VNet. Você também pode especificar vários servidores DNS por interface de rede (por Azure Resource Manager) ou por serviço de nuvem (para o modelo de implantação clássico).
- Os servidores DNS especificados para uma interface de rede ou serviço de nuvem têm precedência sobre os servidores DNS especificados para a VNet.
- No modelo de implantação de Azure Resource Manager, você pode especificar servidores DNS para uma VNet e um adaptador de rede, mas a prática recomendada é usar a configuração somente em VNets.

    servidores de ![DNS ](./media/migrate-best-practices-networking/dns2.png) *servidores DNS para VNet*

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/migrate/contoso-migration-infrastructure) a resolução de nomes ao usar seu próprio servidor DNS.
- [Saiba mais](../../ready/considerations/naming-and-tagging.md) Restrições e regras de nomenclatura de DNS.

## <a name="best-practice-set-up-availability-zones"></a>Prática recomendada: configurar zonas de disponibilidade

As zonas de disponibilidade aumentam a alta disponibilidade para proteger seus aplicativos e dados de falhas do datacenter.

- Zonas de Disponibilidade são locais físicos exclusivos em uma região do Azure.
- Cada zona é composta por um ou mais data centers equipados com energia, resfriamento e rede independentes.
- Para garantir a resiliência, há um mínimo de três zonas separadas em todas as regiões habilitadas.
- A separação física de zonas de disponibilidade em uma região protege aplicativos e dados de falhas do datacenter.
- Os serviços com redundância de zona replicam seus aplicativos e dados entre zonas de disponibilidade para proteger contra pontos únicos de falha. --Com zonas de disponibilidade, o Azure oferece um SLA de 99,99% de tempo de atividade da VM.

    *zona de disponibilidade* de ](./media/migrate-best-practices-networking/availability-zone.png) de zona de ![Availability

- Você pode planejar e criar alta disponibilidade em sua arquitetura de migração colocando recursos de computação, armazenamento, rede e dados em uma zona e replicando-os em outras zonas. Os serviços do Azure que dão suporte a zonas de disponibilidade se enquadram em duas categorias:
  - Serviços zonais: você associa um recurso a uma zona específica. Por exemplo, VMs, Managed disks, endereços IP).
  - Serviços com redundância de zona: o recurso é replicado automaticamente entre zonas. Por exemplo, armazenamento com redundância de zona, banco de dados SQL do Azure.
- Você pode implantar um balanceamento de carga do Azure padrão com cargas de trabalho voltadas para a Internet ou camadas de aplicativo, para fornecer tolerância a falhas zonal.

    balanceador de ![Load ](./media/migrate-best-practices-networking/load-balancer.png) *balanceador de carga*

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/availability-zones/az-overview) das zonas de disponibilidade.

## <a name="design-hybrid-cloud-networking"></a>Criar rede de nuvem híbrida

Para uma migração bem-sucedida, é essencial conectar redes corporativas locais ao Azure. Isso cria uma conexão Always on conhecida como uma rede de nuvem híbrida, em que os serviços são fornecidos da nuvem do Azure para usuários corporativos. Há duas opções para criar esse tipo de rede:

- **VPN site a site:** Você estabelece uma conexão site a site entre o dispositivo VPN local compatível e um gateway de VPN do Azure que é implantado em uma VNet. Qualquer recurso local autorizado pode acessar o VNets. As comunicações site a site são enviadas por meio de um túnel criptografado pela Internet.
- **Azure ExpressRoute:** Você estabelece uma conexão do Azure ExpressRoute entre sua rede local e o Azure, por meio de um parceiro de ExpressRoute. Essa conexão é privada e o tráfego não passa pela Internet.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn) sobre a rede híbrida na nuvem.

## <a name="best-practice-implement-a-highly-available-site-to-site-vpn"></a>Prática recomendada: implementar uma VPN site a site altamente disponível

Para implementar uma VPN site a site, você configura um gateway de VPN no Azure.

- Um gateway de VPN é um tipo específico de gateway de VNet que é usado para enviar tráfego criptografado entre uma VNet do Azure e uma localização local pela Internet pública.
- Você também pode usar um gateway de VPN para enviar o tráfego criptografado entre o Azure VNets pela rede da Microsoft.
- Cada VNet pode ter apenas um gateway de VPN.
- Você pode criar várias conexões com o mesmo gateway de VPN. Quando você cria várias conexões, todos os túneis de VPN compartilham a largura de banda do gateway disponível.
- Cada gateway de VPN do Azure consiste em duas instâncias em uma configuração ativa e em espera.
  - Para manutenção planejada ou interrupção não planejada na instância ativa, o failover ocorre e a instância em espera assume o failover automaticamente e retoma a conexão site a site ou VNet a VNet.
  - A alternância causa uma breve interrupção.
  - Para a manutenção planejada, a conectividade deve ser restaurada em 10 a 15 segundos.
  - Para problemas não planejados, a recuperação de conexão leva mais tempo, cerca de um a 1,5 minutos no pior caso.
  - Conexões de cliente VPN ponto a site (P2S) para o gateway serão desconectadas e os usuários precisarão se reconectar de computadores cliente.

Ao configurar uma VPN site a site, faça o seguinte:

- Você precisa de uma VNet cujo intervalo de endereços não se sobreponha à rede local à qual a VPN será conectada.
- Você cria uma sub-rede de gateway na rede.
- Você cria um gateway de VPN, especifica o tipo de gateway (VPN) e se o gateway é baseado em políticas ou em rota. Uma VPN RouteBased é recomendada como mais capaz e à prova de obsolescência.
- Você cria um gateway de rede local no local e configura seu dispositivo VPN no local.
- Você cria uma conexão VPN site a site de failover entre o gateway de VNet e o dispositivo local. O uso de VPN baseada em rota permite conexões ativo-passivo ou ativo-ativo com o Azure. O baseado em rota também dá suporte a conexões site a site (de qualquer computador) e ponto a site (de um único computador) simultaneamente.
- Especifique o SKU de gateway que você deseja usar. Isso dependerá de seus requisitos de carga de trabalho, produtividade, recursos e SLAs.
- O BGP (Border Gateway Protocol) é um recurso opcional que você pode usar com o Azure ExpressRoute e gateways de VPN baseados em rota para propagar suas rotas BGP locais para seu VNets.

![VPN ](./media/migrate-best-practices-networking/vpn.png)
*VPN site a site*

**Saiba Mais:**

- [Examine](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices) os dispositivos VPN locais compatíveis.
- [Obtenha uma visão geral](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) dos gateways de VPN.
- [Saiba mais sobre](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable) conexões VPN altamente disponíveis.
- [Saiba mais sobre como](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-plan-design) planejar e criar um gateway de VPN.
- [Examinar](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings#gwsku) Configurações de gateway de VPN.
- [Examine](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#gwsku) as SKUs de gateway.
- [Leia sobre como](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-bgp-overview) configurar o BGP com gateways de VPN do Azure.

### <a name="best-practice-configure-a-gateway-for-vpn-gateways"></a>Prática recomendada: configurar um gateway para gateways de VPN

Ao criar um gateway de VPN no Azure, você deve usar uma sub-rede especial chamada GatewaySubnet. Ao criar essa sub-rede, observe estas práticas recomendadas:

- O comprimento do prefixo da sub-rede de gateway pode ter um comprimento de prefixo máximo de 29 (por exemplo, 10.119.255.248/29). A recomendação atual é que você use um comprimento de prefixo 27 (por exemplo, 10.119.255.224/27).
- Quando você define o espaço de endereço da sub-rede de gateway, use a última parte do espaço de endereço da VNet.
- Ao usar o GatewaySubnet do Azure, nunca implante VMs ou outros dispositivos, como o gateway de aplicativo, para a sub-rede de gateway.
- Não atribua um NSG (grupo de segurança de rede) a essa sub-rede. Isso fará com que o gateway pare de funcionar.

**Saiba Mais:**

- [Use essa ferramenta](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) para determinar o espaço de endereço IP.

## <a name="best-practice-implement-azure-virtual-wan-for-branch-offices"></a>Prática recomendada: implementar a WAN virtual do Azure para filiais

Para várias conexões VPN, a WAN virtual do Azure é um serviço de rede que fornece conectividade de Branch para Branch automatizada e otimizada por meio do Azure.

- A WAN virtual permite que você conecte e configure dispositivos de ramificação para se comunicar com o Azure. Isso pode ser feito manualmente ou usando dispositivos de provedor preferenciais por meio de um parceiro de WAN virtual.
- O uso de dispositivos de provedor preferenciais permite o uso simples, conectividade e gerenciamento de configuração.
- O painel interno de WAN do Azure fornece informações instantâneas de solução de problemas que economizam tempo e fornecem uma maneira fácil de controlar a conectividade de site a site em grande escala.

**Saiba mais:** 
[saiba mais sobre](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) a WAN virtual do Azure.

### <a name="best-practice-implement-expressroute-for-mission-critical-connections"></a>Prática recomendada: implementar o ExpressRoute para conexões de missão crítica

O serviço de ExpressRoute do Azure estende sua infraestrutura local para a nuvem da Microsoft criando conexões privadas entre o datacenter virtual do Azure e redes locais.

- As conexões do ExpressRoute podem ser por meio de uma rede de qualquer para qualquer (IP VPN), uma rede Ethernet ponto a ponto ou por meio de um provedor de conectividade. Eles não passam pela Internet pública.
- As conexões do ExpressRoute oferecem maior segurança, confiabilidade e velocidades mais altas (até 10 Gbps), juntamente com a latência consistente.
- O ExpressRoute é útil para data centers virtuais, pois os clientes podem obter os benefícios das regras de conformidade associadas a conexões privadas.
- Com o ExpressRoute Direct, você pode se conectar diretamente aos roteadores da Microsoft em 100Gbps, para maior necessidade de largura de banda.
- O ExpressRoute usa BGP para trocar rotas entre redes locais, instâncias do Azure e endereços públicos da Microsoft.

A implantação de conexões do ExpressRoute geralmente envolve a participação em um provedor de serviços do ExpressRoute. Para um início rápido, é comum usar inicialmente uma VPN site a site para estabelecer a conectividade entre o datacenter virtual e os recursos locais e, em seguida, migrar para uma conexão do ExpressRoute quando uma interconexão física com seu provedor de serviços for estabelecida.

**Saiba Mais:**

- [Leia uma visão geral](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) do ExpressRoute.
- [Saiba mais](https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about) ExpressRoute direto.

### <a name="best-practice-optimize-expressroute-routing-with-bgp-communities"></a>Prática recomendada: otimizar o roteamento do ExpressRoute com comunidades BGP

Quando você tem vários circuitos de ExpressRoute, tem mais de um caminho para se conectar à Microsoft. Como resultado, o roteamento de qualidade inferior pode acontecer e seu tráfego pode levar um caminho mais longo para alcançar a Microsoft e a Microsoft para sua rede. Quanto mais longo o caminho de rede, maior a latência. A latência tem impacto direto no desempenho do aplicativo e na experiência do usuário.

**Exemplo:**

Vamos examinar um exemplo:

- Você tem dois escritórios nos EUA, um em Los Angeles e outro em Nova York.
- Seus escritórios estão conectados em uma WAN, que pode ser sua própria rede de backbone ou VPN IP do seu provedor de serviços.
- Você tem dois circuitos de ExpressRoute, um no Oeste dos EUA e outro no Leste dos EUA, que também estão conectados à WAN. Obviamente, você tem dois caminhos para se conectar à rede da Microsoft.

**Persisti**

Agora imagine que você tenha uma implantação do Azure (por exemplo, Azure App Service) nos EUA oeste e leste dos EUA.

- Você deseja que os usuários em cada escritório acessem seus serviços do Azure mais próximos para obter uma experiência ideal.
- Portanto, você deseja conectar os usuários em Los Angeles ao Azure US West e aos usuários em Nova York para o leste dos EUA do Azure.
- Isso funciona para os usuários da costa leste, mas não para aqueles na costa oeste. O problema é:
  - Em cada circuito do ExpressRoute, anunciamos os dois prefixos no leste dos EUA do Azure (23.100.0.0/16) e no centro-oeste do Azure (13.100.0.0/16).
  - Sem saber qual prefixo é de qual região, os prefixos não são tratados de forma diferente.
  - Sua rede WAN pode assumir que os dois prefixos estão mais próximos do leste dos EUA do que os oeste dos EUA e, portanto, encaminhar os usuários de ambos os escritórios para o circuito do ExpressRoute no leste dos EUA, fornecendo uma experiência ideal para os usuários no escritório de Los Angeles.

![VPN ](./media/migrate-best-practices-networking/bgp1.png)
 a*conexão de comunidades BGP não otimizada*

**Solução:**

Para otimizar o roteamento de ambos os usuários do Office, você precisa saber qual prefixo é do Azure no oeste dos EUA e qual é o leste dos EUA do Azure. Você pode codificar essas informações usando valores de comunidade BGP.

- Atribua um valor de comunidade BGP exclusivo a cada região do Azure. Por exemplo, 12076:51004 para o leste dos EUA; 12076:51006 para o oeste dos EUA.
- Agora que está claro qual prefixo pertence a qual região do Azure, você pode configurar um circuito de ExpressRoute preferencial.
- Como você está usando o BGP para trocar informações de roteamento, você pode usar a preferência local do BGP para influenciar o roteamento.
- Em nosso exemplo, você atribui um valor de preferência local mais alto para 13.100.0.0/16 em oeste dos EUA do que no leste dos EUA e, da mesma forma, um valor de preferência local superior para 23.100.0.0/16 no leste dos EUA do que no oeste dos EUA.
- Essa configuração garante que, quando ambos os caminhos para a Microsoft estiverem disponíveis, os usuários em Los Angeles se conectarão ao Azure EUA oeste usando o circuito oeste, e os usuários de Nova York se conectarão ao leste dos EUA do Azure usando o circuito leste. O roteamento é otimizado em ambos os lados.

![VPN ](./media/migrate-best-practices-networking/bgp2.png)
*conexão otimizada de comunidades BGP*

**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/expressroute/expressroute-optimize-routing) otimizar o roteamento.

## <a name="securing-vnets"></a>Protegendo VNets

A responsabilidade por proteger o VNets é compartilhada entre a Microsoft e você. A Microsoft fornece muitos recursos de rede, bem como serviços que ajudam a manter os recursos seguros. Ao projetar a segurança para VNets, as práticas recomendadas que você deve seguir incluem a implementação de uma rede de perímetro, o uso de filtros e grupos de segurança, a proteção do acesso a recursos e endereços IP e a implementação da proteção contra ataques.

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices) das práticas recomendadas para segurança de rede.
- [Saiba como](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm#security) projetar redes seguras.

## <a name="best-practice-implement-an-azure-perimeter-network"></a>Prática recomendada: implementar uma rede de perímetro do Azure

Embora a Microsoft investe pesadamente na proteção da infraestrutura de nuvem, você também deve proteger seus serviços de nuvem e grupos de recursos. Uma abordagem multicamada para segurança fornece a melhor defesa. Colocar uma rede de perímetro em vigor é uma parte importante dessa estratégia de defesa.

- Uma rede de perímetro protege recursos de rede internos de uma rede não confiável.
- É a camada mais externa que é exposta à Internet. Em geral, ele fica entre a Internet e a infraestrutura corporativa, geralmente com alguma forma de proteção em ambos os lados.
- Em uma topologia de rede corporativa típica, a infra-estrutura principal é muito reforçadada nos perímetros, com várias camadas de dispositivos de segurança. O limite de cada camada consiste em dispositivos e pontos de imposição de políticas.
- Cada camada pode incluir uma combinação das soluções de segurança de rede que incluem firewalls, prevenção de negação de serviço (DoS), detecção de intrusão/sistemas de proteção contra intrusão (IDS/IPS) e dispositivos VPN.
- A imposição de política na rede de perímetro pode usar políticas de firewall, ACLs (listas de controle de acesso) ou roteamento específico.
- À medida que o tráfego de entrada chega da Internet, ele é interceptado e manipulado por uma combinação de solução de defesa para bloquear ataques e tráfego prejudicial, ao mesmo tempo que permite solicitações legítimas na rede.
- O tráfego de entrada pode ser roteado diretamente para os recursos na rede de perímetro. O recurso de rede de perímetro pode então se comunicar com outros recursos mais profundamente na rede, movendo o tráfego para a rede após a validação.

A figura a seguir mostra um exemplo de uma rede de perímetro de sub-rede individual em uma rede corporativa, com dois limites de segurança.

![VPN a*implantação de rede de perímetro* ](./media/migrate-best-practices-networking/perimeter.png)


**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) implantar uma rede de perímetro entre o Azure e seu datacenter local.

## <a name="best-practice-filter-vnet-traffic-with-nsgs"></a>Prática recomendada: filtrar o tráfego de VNet com NSGs

Os NSG (grupos de segurança de rede) contêm várias regras de segurança de entrada e saída que filtram o tráfego que vai para os recursos. A filtragem pode ser por endereço IP de origem e de destino, porta e protocolo.

- NSGs contêm regras de segurança que permitem ou negam o tráfego de rede de entrada para (ou tráfego de rede de saída de) vários tipos de recursos do Azure. Para cada regra, você pode especificar a origem e o destino, a porta e o protocolo.
- As regras NSG são avaliadas por prioridade usando informações de cinco tuplas (origem, porta de origem, destino, porta de destino e protocolo) para permitir ou negar o tráfego.
- Um registro de fluxo é criado para conexões existentes. A comunicação é permitida ou negada com base no estado de conexão do registro de fluxo.
- Um registro de fluxo permite que um NSG seja monitorado. Por exemplo, se você especificar uma regra de segurança de saída para qualquer endereço pela porta 80, não precisará de uma regra de segurança de entrada para responder ao tráfego de saída. Você só precisa especificar uma regra de segurança de entrada se a comunicação for iniciada externamente.
- O oposto também é verdadeiro. Se o tráfego de entrada for permitido em uma porta, você não precisará especificar uma regra de segurança de saída para responder ao tráfego pela porta.
- As conexões existentes não são interrompidas quando você remove uma regra de segurança que habilitou o fluxo. Os fluxos de tráfego são interrompidos quando as conexões são interrompidas e nenhum tráfego flui em qualquer direção, por pelo menos alguns minutos.
- Ao criar NSGs, crie o mínimo possível, mas quantos forem necessários.

### <a name="best-practice-secure-northsouth-and-eastwest-traffic"></a>Prática recomendada: proteger o tráfego Norte/Sul e leste/oeste

Ao proteger o VNets, é importante considerar os vetores de ataque.

- Usar apenas a sub-rede NSGs simplifica seu ambiente, mas só protege o tráfego em sua sub-rede. Isso é conhecido como tráfego norte/sul.
- O tráfego entre as VMs na mesma sub-rede é conhecido como tráfego leste/oeste.
- É importante usar ambas as formas de proteção, de modo que, se um hacker obtiver acesso de fora, eles serão interrompidos ao tentar anexar as máquinas localizadas na mesma sub-rede.

### <a name="use-service-tags-on-nsgs"></a>Usar marcas de serviço em NSGs

Uma marca de serviço representa um grupo de prefixos de endereço IP. O uso de uma marca de serviço ajuda a minimizar a complexidade ao criar regras de NSG.

- Você pode usar marcas de serviço em vez de endereços IP específicos ao criar regras.
- A Microsoft gerencia os prefixos de endereço associados a uma marca de serviço e atualiza automaticamente a marca de serviço à medida que os endereços são alterados.
- Você não pode criar sua própria marca de serviço ou especificar quais endereços IP estão incluídos em uma marca.

As marcas de serviço tomam o trabalho manual de atribuir uma regra a grupos de serviços do Azure. Por exemplo, se você quiser permitir que uma sub-rede VNet que contenha servidores Web acessem um banco de dados SQL do Azure, você poderá criar uma regra de saída para a porta 1433 e usar a marca de serviço do **SQL** .

- Esta marca **SQL** denota os prefixos de endereço do banco de dados SQL do Azure e os serviços de SQL data warehouse do Azure.
- Se você especificar **SQL** como o valor, o tráfego será permitido ou negado ao SQL.
- Se você quiser permitir o acesso ao **SQL** em uma região específica, poderá especificar essa região. Por exemplo, se você quiser permitir o acesso somente ao banco de dados SQL do Azure na região leste dos EUA, poderá especificar **SQL. eastus** como uma marca de serviço.
- A marca representa o serviço, mas não as instâncias específicas do serviço. Por exemplo, a marca representa o serviço do banco de dados SQL do Azure, mas não representa um servidor ou banco de dados SQL específico.
- Todos os prefixos de endereço representados por essa marca também são representados pela marca da **Internet** .

**Saiba Mais:**

- [Leia sobre](https://docs.microsoft.com/azure/virtual-network/security-overview) NSGs.
- [Examine](https://docs.microsoft.com/azure/virtual-network/security-overview#service-tags) as marcas de serviço disponíveis para NSGs.

## <a name="best-practice-use-application-security-groups"></a>Prática recomendada: usar grupos de segurança de aplicativo

Os grupos de segurança de aplicativo permitem configurar a segurança de rede como uma extensão natural de uma estrutura de aplicativo.

- Você pode agrupar VMs e definir políticas de segurança de rede com base em grupos de segurança de aplicativo.
- Os grupos de segurança de aplicativo permitem que você reutilize sua política de segurança em escala sem a manutenção manual de endereços IP explícitos.
- Os grupos de segurança de aplicativo lidam com a complexidade de endereços IP explícitos e vários conjuntos de regras, permitindo que você se concentre na lógica de negócios.

**Exemplo:**

![Application grupo de segurança ](./media/migrate-best-practices-networking/asg.png)
*exemplo de grupo de segurança de aplicativo*

**Interface de rede** | **Grupo de segurança de aplicativo**
--- | ---
NIC1 | AsgWeb
NIC2 | AsgWeb
NIC3 estão associadas | AsgLogic
NIC4 | AsgDb

- Em nosso exemplo, cada interface de rede pertence a apenas um grupo de segurança de aplicativo, mas, de fato, uma interface pode pertencer a vários grupos, de acordo com os limites do Azure.
- Nenhuma das interfaces de rede tem um NSG associado. NSG1 está associado a ambas as sub-redes e contém as regras a seguir.

<!--markdownlint-disable MD033 -->

**Nome da regra** | **Objetivo** | **Detalhes**
--- | --- | ---
Permitir-HTTP-entrada-Internet | Permitir o tráfego da Internet para os servidores Web. O tráfego de entrada da Internet é negado pela regra de segurança padrão DenyAllInbound, portanto, nenhuma regra adicional é necessária para os grupos de segurança do aplicativo AsgLogic ou AsgDb. | Prioridade: 100<br/><br/> Fonte: Internet<br/><br/> Porta de origem: *<br/><br/> Destino: AsgWeb<br/><br/> Porta de destino: 80<br/><br/> Protocolo: TCP<br/><br/> Acesso: permitir.
Negar-banco de dados-tudo | AllowVNetInBound regra de segurança padrão permite toda a comunicação entre os recursos na mesma VNet, essa regra é necessária para negar o tráfego de todos os recursos. | Prioridade: 120<br/><br/> Origem: *<br/><br/> Porta de origem: *<br/><br/> Destino: AsgDb<br/><br/> Porta de destino: 1433<br/><br/> Protocolo: todos<br/><br/> Acesso: negar.
Allow-Database-BusinessLogic | Permitir o tráfego do grupo de segurança de aplicativo AsgLogic para o grupo de segurança de aplicativo AsgDb. A prioridade dessa regra é maior que a regra Deny-Database-All e é processada antes dessa regra, portanto, o tráfego do grupo de segurança do aplicativo AsgLogic é permitido e todos os outros tráfegos são bloqueados. | Prioridade: 110<br/><br/> Origem: AsgLogic<br/><br/> Porta de origem: *<br/><br/> Destino: AsgDb<br/><br/> Porta de destino: 1433<br/><br/> Protocolo: TCP<br/><br/> Acesso: permitir.

<!--markdownlint-enable MD033 -->

- As regras que especificam um grupo de segurança de aplicativo como a origem ou o destino são aplicadas somente às interfaces de rede que são membros do grupo de segurança de aplicativo. Se a interface de rede não for membro de um grupo de segurança de aplicativo, a regra não será aplicada ao adaptador de rede, mesmo que o grupo de segurança de rede esteja associado à sub-rede.

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/virtual-network/security-overview#application-security-groups) grupos de segurança de aplicativos.

### <a name="best-practice-secure-access-to-paas-using-vnet-service-endpoints"></a>Prática recomendada: acesso seguro ao PaaS usando pontos de extremidade de serviço de VNet

Os pontos de extremidade do serviço VNet estendem seu espaço de endereço privado de VNet e a identidade para os serviços do Azure por meio de uma conexão direta.

- Os pontos de extremidade permitem que você proteja os recursos de serviço do Azure críticos somente para o VNets. O tráfego de sua VNet para o serviço do Azure sempre permanece na rede de backbone Microsoft Azure.
- O espaço de endereço privado da VNet pode ser sobreposto e, portanto, não pode ser usado para identificar exclusivamente o tráfego originado de uma VNet.
- Depois que os pontos de extremidade de serviço são habilitados em sua VNet, você pode proteger os recursos de serviço do Azure adicionando uma regra de VNet aos recursos de serviço. Isso proporciona segurança aprimorada removendo totalmente o acesso à Internet pública aos recursos e permitindo o tráfego somente de sua VNet.

![Service pontos de extremidade ](./media/migrate-best-practices-networking/endpoint.png)
*pontos de extremidade de serviço*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) Pontos de extremidade de serviço de VNet.

## <a name="best-practice-control-public-ip-addresses"></a>Prática recomendada: controlar endereços IP públicos

Os endereços IP públicos no Azure podem ser associados a VMs, balanceadores de carga, gateways de aplicativo e gateways de VPN.

- Os endereços IP públicos permitem que os recursos da Internet comuniquem a entrada para os recursos do Azure e os recursos do Azure para comunicar a saída à Internet.
- Os endereços IP públicos são criados com um SKU básico ou Standard, que têm várias diferenças. Os SKUs padrão podem ser atribuídos a qualquer serviço, mas geralmente são configurados em VMs, balanceadores de carga e gateways de aplicativo.
- É importante observar que um endereço IP público básico não tem um NSG configurado automaticamente. Você precisa configurar seu próprio e atribuir regras para controlar o acesso. Os endereços IP de SKU padrão têm um NSG e as regras atribuídas por padrão.
- Como prática recomendada, as VMs não devem ser configuradas com um endereço IP público.
  - Se você precisar de uma porta aberta, ela só deve ser para serviços Web, como a porta 80 ou 443.
  - As portas de gerenciamento remoto padrão, como SSH (22) e RDP (3389), devem ser definidas como Deny, juntamente com todas as outras portas, usando NSGs.
- Uma prática melhor é colocar as VMs por trás de um Azure Load Balancer ou um gateway de aplicativo. Em seguida, se o acesso às portas de gerenciamento remoto for necessário, você poderá usar o acesso à VM just-in-time na central de segurança do Azure.

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/virtual-network/virtual-network-ip-addresses-overview-arm#public-ip-addresses) endereços IP públicos no Azure.
- [Leia mais](https://docs.microsoft.com/azure/security-center/security-center-just-in-time) sobre o acesso à VM just-in-time na central de segurança do Azure.

## <a name="take-advantage-of-azure-security-features-for-networking"></a>Aproveite os recursos de segurança do Azure para rede

O Azure tem recursos de segurança de plataforma que são fáceis de usar e fornece contramedidas avançadas a ataques de rede comuns. Isso inclui o Firewall do Azure, o Firewall do aplicativo Web e o observador de rede.

## <a name="best-practice-deploy-azure-firewall"></a>Prática recomendada: implantar o Firewall do Azure

O Firewall do Azure é um serviço de segurança de rede gerenciado baseado em nuvem que protege seus recursos de VNet. É um firewall gerenciado com estado total com alta disponibilidade interna e escalabilidade de nuvem irrestrita.

![Service pontos de extremidade ](./media/migrate-best-practices-networking/firewall.png)
 o*Firewall do Azure*

- O Firewall do Azure pode criar, impor e registrar políticas de conectividade de rede e de aplicativo de forma centralizada em assinaturas e VNets.
- O Firewall do Azure usa um endereço IP público estático para seus recursos de VNet, permitindo que os firewalls externos identifiquem o tráfego originado de sua VNet.
- O Firewall do Azure é totalmente integrado ao Azure Monitor para registro em log e análise.
- Como prática recomendada ao criar regras de firewall do Azure, use as marcas de FQDN para criar regras.
  - Uma marca FQDN representa um grupo de FQDNs associados aos serviços da Microsoft conhecidos.
  - Você pode usar uma marca FQDN para permitir o tráfego de rede de saída necessário por meio do firewall.
- Por exemplo, para permitir manualmente Windows Update tráfego de rede por meio do firewall, você precisaria criar várias regras de aplicativo. Usando marcas de FQDN, você cria uma regra de aplicativo e inclui a marca Windows Updates. Com essa regra em vigor, o tráfego de rede para os pontos de extremidade do Microsoft Windows Update pode fluir pelo firewall.

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/firewall/overview) do firewall do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/firewall/fqdn-tags) Marcas de FQDN.

## <a name="best-practice-deploy-a-web-application-firewall-waf"></a>Prática recomendada: implantar um firewall do aplicativo Web (WAF)

Os aplicativos Web são cada vez mais alvos de ataques mal-intencionados que exploram vulnerabilidades comumente conhecidas. As explorações incluem ataques de injeção de SQL e ataques de script entre sites. Impedir esses ataques no código do aplicativo pode ser desafiador e pode exigir uma manutenção rigorosa, aplicação de patches e monitoramento em várias camadas da topologia do aplicativo. Um firewall de aplicativo Web centralizado ajuda a tornar o gerenciamento de segurança muito mais simples e ajuda os administradores de aplicativos a proteger contra ameaças ou invasões. Um firewall de aplicativo Web pode reagir mais rapidamente às ameaças de segurança, corrigindo vulnerabilidades conhecidas em um local central, em vez de proteger aplicativos Web individuais. Os gateways de aplicativo existentes podem ser convertidos em um gateway de aplicativo habilitado para firewall de aplicativo Web facilmente.

O Firewall do aplicativo Web (WAF) é um recurso do gateway de Aplicativo Azure.

- O WAF fornece proteção centralizada de seus aplicativos Web, de explorações e vulnerabilidades comuns.
- O WAF protege sem modificações no código de back-end.
- Ele pode proteger vários aplicativos Web ao mesmo tempo por trás de um gateway de aplicativo.
- O WAF é integrado à central de segurança do Azure.
- Você pode personalizar regras de WAF e grupos de regras para atender aos requisitos do seu aplicativo.
- Como prática recomendada, você deve usar um WAF na frente em qualquer aplicativo voltado para a Web, incluindo aplicativos em VMs do Azure ou como um serviço Azure App.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/application-gateway/waf-overview) WAF.
- [Examinar](https://docs.microsoft.com/azure/application-gateway/application-gateway-waf-configuration) Limitações e exclusões do WAF.

## <a name="best-practice-implement-azure-network-watcher"></a>Prática recomendada: implementar o observador de rede do Azure

O observador de rede do Azure fornece ferramentas para monitorar recursos e comunicações em uma VNet do Azure. Por exemplo, você pode monitorar as comunicações entre uma VM e um ponto de extremidade, como outra VM ou FQDN, exibir recursos e relações de recursos em uma VNet ou diagnosticar problemas de tráfego de rede.

observador de ![Network ](./media/migrate-best-practices-networking/network-watcher.png)
*Inspetor de rede*

- Com o observador de rede, você pode monitorar e diagnosticar problemas de rede sem fazer logon em VMs.
- Você pode disparar a captura de pacotes definindo alertas e obter acesso a informações de desempenho em tempo real no nível de pacote. Ao ver um problema, você pode investigar isso detalhadamente.
- Como prática recomendada, use o observador de rede para examinar os logs de fluxo do NSG.
  - Os logs de fluxo do NSG no observador de rede permitem que você exiba informações sobre o tráfego IP de entrada e saída por meio de um NSG.
  - Os logs de fluxo são gravados no formato JSON.
  - Os logs de fluxo mostram os fluxos de entrada e saída por regra, a NIC (interface de rede) à qual o fluxo se aplica, informações de 5 tuplas sobre o fluxo (IP de origem/destino, porta de origem/destino e protocolo) e se o tráfego foi permitido ou negado.

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/network-watcher) do observador de rede.
- [Saiba mais](https://docs.microsoft.com/azure/network-watcher/network-watcher-nsg-flow-logging-overview) sobre os logs de fluxo do NSG.

## <a name="use-partner-tools-in-the-azure-marketplace"></a>Usar as ferramentas de parceiro no Azure Marketplace

Para topologias de rede mais complexas, você pode usar produtos de segurança de parceiros da Microsoft, em NVAs (soluções de virtualização de rede) específicas.

- Um NVA é uma VM que executa uma função de rede, como um firewall, otimização de WAN ou outra função de rede.
- O NVAs reforça as funções de rede e segurança de VNet. Eles podem ser implantados para firewalls altamente disponíveis, prevenção de intrusão, detecção de intrusão, firewall de aplicativo Web (WAFs), otimização de WAN, roteamento, balanceamento de carga, VPN, gerenciamento de certificados, Active Directory e autenticação multifator.
- O NVA está disponível de vários fornecedores no [Azure Marketplace](https://azuremarketplace.microsoft.com).

## <a name="best-practice-implement-firewalls-and-nvas-in-hub-networks"></a>Prática recomendada: implementar firewalls e NVAs em redes de Hub

No Hub, a rede de perímetro (com acesso à Internet) normalmente é gerenciada por meio de um firewall do Azure, um farm de firewall ou um WAF (firewall do aplicativo Web). Considere as seguintes comparações.

<!--markdownlint-disable MD033 -->

**Tipo de firewall** | **Detalhes**
--- | ---
WAFs | Os aplicativos Web são comuns e tendem a sofrer vulnerabilidades e possíveis explorações.<br/><br/> O WAFs foi projetado para detectar ataques contra aplicativos Web (HTTP/HTTPS), mais especificamente do que um firewall genérico.<br/><br/> Em comparação com a tecnologia de firewall tradicional, o WAFs tem um conjunto de recursos específicos que protegem servidores Web internos contra ameaças.
Firewall do Azure | Assim como os farms de firewall do NVA, o Firewall do Azure usa um mecanismo de administração comum e um conjunto de regras de segurança para proteger as cargas de trabalho hospedadas em redes spoke e para controlar o acesso a redes locais.<br/><br/> O Firewall do Azure tem escalabilidade interna.
Firewalls do NVA | Assim como os farms de firewall NVA do firewall do Azure têm um mecanismo de administração comum e um conjunto de regras de segurança para proteger as cargas de trabalho hospedadas em redes spoke e para controlar o acesso a redes locais.<br/><br/> Os firewalls do NVA podem ser manualmente dimensionados por trás de um balanceador de carga.<br/><br/> Embora um firewall NVA tenha um software menos especializado do que um WAF, ele tem um escopo de aplicativo mais amplo para filtrar e inspecionar qualquer tipo de tráfego em egresso e entrada.<br/><br/> Se você quiser usar o NVA, poderá encontrá-los no Azure Marketplace.

<!--markdownlint-enable MD033 -->

É recomendável usar um conjunto de firewalls do Azure (ou NVAs) para tráfego originado na Internet e outro para o tráfego originado no local.

- Usar apenas um conjunto de firewalls para ambos é um risco de segurança, pois ele não fornece nenhum perímetro de segurança entre os dois conjuntos de tráfego de rede.
- O uso de camadas de firewall separadas reduz a complexidade da verificação das regras de segurança e fica claro quais regras correspondem a qual solicitação de rede de entrada.

**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) usar o NVAs em uma VNet do Azure.

## <a name="next-steps"></a>Próximos passos

Examine outras práticas recomendadas:

- [Práticas recomendadas](./migrate-best-practices-security-management.md) de segurança e gerenciamento após a migração.
- [Práticas recomendadas](./migrate-best-practices-costs.md) para o gerenciamento de custos após a migração.
