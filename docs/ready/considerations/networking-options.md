---
title: Examine as opções de rede
description: Examine as opções de rede para cargas de trabalho do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 199eedb6c9365f273588fae79b134298e8b60c6e
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78225380"
---
<!-- cSpell:ignore paas NVAs VPNs -->

# <a name="review-your-network-options"></a>Examine as opções de rede

Criar e implementar funcionalidades de rede do Azure é uma parte crítica dos seus esforços de adoção de nuvem. Você precisará tomar decisões de design de rede para dar suporte adequado às cargas de trabalho e aos serviços que serão hospedados na nuvem. Os produtos e serviços de rede do Azure dão suporte a uma ampla variedade de funcionalidades de rede. Como você estrutura esses serviços e as arquiteturas de rede escolhidas depende dos requisitos de carga de trabalho, de governança e de conectividade de sua organização.

## <a name="identify-workload-networking-requirements"></a>Identificar requisitos de rede da carga de trabalho

Como parte da avaliação e preparação da zona de acesso, você precisa identificar as funcionalidades de rede aos quais a zona de acesso precisa dar suporte. Este processo envolve avaliar cada um dos aplicativos e serviços que compõem as cargas de trabalho para determinar os requisitos de controle de rede de conectividade. Depois de identificar e documentar os requisitos, você pode criar políticas para que a zona de acesso controle os recursos e a configuração de rede permitidos com base nas necessidades das cargas de trabalho.

Para cada aplicativo ou serviço que você implantará no ambiente de zona de acesso, use a seguinte árvore de decisão como um ponto de partida para ajudá-lo a determinar as ferramentas de rede ou serviços a serem usados:

![Árvore de decisão de serviços de rede do Azure](../../_images/ready/network-decision-tree.png)

### <a name="key-questions"></a>Principais perguntas

Responda às seguintes perguntas sobre as cargas de trabalho para ajudá-lo a tomar decisões com base na árvore de decisão de serviços de rede do Azure:

- **Suas cargas de trabalho requererão uma rede virtual?** Os tipos de recurso de PaaS (plataforma como serviço) gerenciados usam funcionalidades de rede de plataforma subjacentes que nem sempre requerem uma rede virtual. Se as cargas de trabalho não exigirem recursos de rede avançados e você não precisar implantar recursos de IaaS (infraestrutura como serviço), as [funcionalidades de rede nativas fornecidas pelos recursos de PaaS](../../decision-guides/software-defined-network/paas-only.md) padrão poderão atender aos seus requisitos de conectividade de carga de trabalho e de gerenciamento de tráfego.
- **Suas cargas de trabalho exigirão conectividade entre redes virtuais e seu datacenter local?** O Azure fornece duas soluções para estabelecer recursos de rede híbrida: gateway de VPN do Azure e Azure ExpressRoute. O [Gateway de VPN do Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) conecta suas redes locais ao Azure por meio de VPNs site a site semelhantes à maneira como você pode configurar e se conectar a uma filial remota. O Gateway de VPN tem uma largura de banda máxima de 1,25 GBps. O [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) oferece maior confiabilidade e menor latência usando uma conexão privada entre o Azure e sua infraestrutura local. As opções de largura de banda do ExpressRoute variam de 50 MBps a 100 GBps.
- **Será necessário inspecionar e auditar o tráfego de saída usando dispositivos de rede locais?** Para cargas de trabalho nativas da nuvem, você pode usar o [Firewall do Azure](https://docs.microsoft.com/azure/firewall/overview) ou [NVAs (soluções de virtualização de rede)](https://azure.microsoft.com/solutions/network-appliances) de terceiros hospedadas na nuvem para inspecionar e auditar o tráfego para a Internet pública ou oriundo dela. No entanto, muitas políticas de segurança de TI corporativas exigem que o tráfego de saída associado à Internet passe por meio de dispositivos gerenciados centralmente no ambiente local da organização. O [túnel forçado](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview) é compatível com esses cenários. Nem todos os serviços gerenciados dão suporte ao túnel forçado. Serviços e recursos como [Ambiente do Serviço de Aplicativo no Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/environment/intro), [Gerenciamento de API do Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts), [AKS (Serviço de Kubernetes do Azure)](https://docs.microsoft.com/azure/aks/intro-kubernetes), [Instâncias Gerenciadas do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index), [Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/what-is-azure-databricks) e [Azure HDInsight](https://docs.microsoft.com/azure/hdinsight) dão suporte a essa configuração quando o serviço ou o recurso é implantado em uma rede virtual.
- **Você precisará conectar várias redes virtuais?** Você pode usar o [emparelhamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) para conectar várias instâncias da [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). O emparelhamento pode dar suporte a conexões entre assinaturas e regiões. Para cenários em que você fornece serviços compartilhados entre várias assinaturas ou que precisa gerenciar um grande número de emparelhamentos de rede, considere a adoção de [uma arquitetura de rede de hub e spoke](../../decision-guides/software-defined-network/hub-spoke.md) ou o uso do [WAN Virtual do Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about). O emparelhamento de rede virtual fornece conectividade somente entre duas redes emparelhadas. Por padrão, ele não fornece conectividade transitiva entre vários emparelhamentos.
- **Suas cargas de trabalho estarão acessíveis pela Internet?** O Azure fornece serviços projetados para ajudá-lo a gerenciar e a proteger o acesso externo aos seus aplicativos e serviços:
  - [Firewall do Azure](https://docs.microsoft.com/azure/firewall/overview)
  - [Dispositivos de rede](https://azure.microsoft.com/solutions/network-appliances)
  - [Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
  - [Gateway de Aplicativo do Azure](https://docs.microsoft.com/azure/application-gateway)
  - [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)
- **Você precisará dar suporte ao gerenciamento de DNS personalizado?** [O DNS do Azure](https://docs.microsoft.com/azure/dns/dns-overview) é um serviço de hospedagem para domínios DNS. O DNS do Azure fornece resolução de nomes usando a infraestrutura do Azure. Se as cargas de trabalho exigirem uma resolução de nomes que vá além dos recursos fornecidos pelo DNS do Azure, talvez você precise implantar outras soluções. Se as cargas de trabalho também exigirem serviços do Active Directory, considere usar o [Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/overview) para aumentar as funcionalidades do DNS do Azure. Para obter mais funcionalidades, você também pode [implantar máquinas virtuais IaaS personalizadas](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances) para atender aos seus requisitos.

## <a name="common-networking-scenarios"></a>Cenários comuns de rede

A rede do Azure é composta por vários produtos e serviços que fornecem diferentes funcionalidades de rede. Como parte do seu processo de criação de rede, é possível comparar seus requisitos de carga de trabalho com os cenários de rede na seguinte tabela para identificar as ferramentas ou serviços do Azure que você pode usar para fornecer estas funcionalidades de rede:

<!-- markdownlint-disable MD033 -->

| **Cenário** | **Produto ou serviço de rede** |
| --- | --- |
| Preciso da infraestrutura de rede para conectar tudo, de máquinas virtuais a conexões VPN de entrada. | [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network) |
| Preciso equilibrar conexões de entrada e de saída e solicitações em meus aplicativos ou serviços. | [Balanceador de carga do Azure](https://docs.microsoft.com/azure/load-balancer) |
| Desejo otimizar a entrega em farms de servidores de aplicativos, aumentando a segurança com um firewall do aplicativo Web. | [Gateway de Aplicativo do Azure](https://docs.microsoft.com/azure/application-gateway) <br/>[Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |
| Preciso usar a Internet de forma segura para acessar a Rede Virtual do Azure com gateways de VPN de alto desempenho. | [Gateway de VPN do Azure](https://docs.microsoft.com/azure/vpn-gateway) |
| Desejo ter respostas DNS ultrarrápidas e disponibilidade extremamente alta para todas as minhas necessidades de domínio. | [DNS do Azure](https://docs.microsoft.com/azure/dns) |
| Preciso acelerar a entrega de conteúdo de alta largura de banda a clientes em todo o mundo, desde aplicativos e conteúdo armazenado a vídeos por streaming. | [Rede de Distribuição de Conteúdo do Azure](https://docs.microsoft.com/azure/cdn) |
| Preciso proteger meus aplicativos do Azure contra ataques de DDoS. | [Proteção contra DDoS do Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) |
| Preciso distribuir o tráfego para serviços de forma ideal entre regiões globais do Azure oferecendo alta disponibilidade e dinamismo ao mesmo tempo. | [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager)<br/>[Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |
| Preciso adicionar conectividade de rede privada para acessar serviços em nuvem da Microsoft em minhas redes corporativas, como se elas estivessem residindo localmente em meu próprio datacenter. | [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute) |
| Desejo monitorar e diagnosticar condições em um nível de cenário de rede. | [Observador de Rede do Azure](https://docs.microsoft.com/azure/network-watcher) |
| Preciso de recursos de firewall nativo, com alta disponibilidade interna, escalabilidade de nuvem irrestrita e manutenção zero. | [Firewall do Azure](https://docs.microsoft.com/azure/firewall) |
| Preciso conectar escritórios empresariais, locais de varejo e sites com segurança. | [WAN Virtual do Azure](https://docs.microsoft.com/azure/virtual-wan) |
| Ponto de um ponto de entrega escalonável e com segurança avançada para aplicativos Web globais baseados em microsserviços. | [Azure Front Door Service](https://docs.microsoft.com/azure/frontdoor) |

<!-- markdownlint-enable MD033 -->

## <a name="choose-a-networking-architecture"></a>Escolha uma arquitetura de rede

Após identificar os serviços de rede do Azure de que você precisa para dar suporte às suas cargas de trabalho, você também precisará criar a arquitetura que combinará esses serviços para fornecer a infraestrutura de rede de nuvem da zona de acesso. O [guia de decisão de Rede Definida pelo Software](../../decision-guides/software-defined-network/index.md) do Cloud Adoption Framework fornece detalhes sobre alguns dos padrões de arquitetura de rede mais comuns usados no Azure.

A tabela a seguir resume os principais cenários aos quais esses padrões dão suporte:

| **Cenário**                                                                                                                                                                                                                                                                                                                        | **Arquitetura de rede sugerida**                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Todas as cargas de trabalho hospedadas no Azure implantadas em sua zona de aterrissagem serão totalmente baseadas em PaaS, não exigirão uma rede virtual e não fazem parte de um esforço de adoção de nuvem maior que inclui recursos de IaaS.                                                                                                                        | [PaaS-only](../../decision-guides/software-defined-network/paas-only.md)            |
| Suas cargas de trabalho hospedadas no Azure implantarão recursos baseados em IaaS como máquinas virtuais ou, de outra forma, exigirão uma rede virtual, mas não exigirão conectividade com seu ambiente local.                                                                                                                                          | [Nativo da nuvem](../../decision-guides/software-defined-network/cloud-native.md)      |
| Suas cargas de trabalho hospedadas no Azure exigem acesso limitado a recursos locais, mas você precisa tratar as conexões de nuvem como não confiáveis.                                                                                                                                                                                           | [DMZ de nuvem](../../decision-guides/software-defined-network/cloud-dmz.md)            |
| Suas cargas de trabalho hospedadas no Azure exigem acesso limitado a recursos locais e você planeja implementar políticas de segurança maduras e proteger a conectividade entre a nuvem e o ambiente local.                                                                                                                         | [Híbridos](../../decision-guides/software-defined-network/hybrid.md)                  |
| É necessário implantar e gerenciar um grande número de VMs e cargas de trabalho, excedendo potencialmente os [limites de assinatura do Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits), é necessário compartilhar serviços entre assinaturas ou é necessária uma estrutura mais segmentada para função, aplicativo ou segregação de permissão. | [Hub e spoke](../../decision-guides/software-defined-network/hub-spoke.md)        |
| Você tem muitas filiais que precisam se conectar entre si e com o Azure.                                                                                                                                                                                                                                                       | [WAN Virtual do Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) |

### <a name="azure-virtual-datacenter"></a>Datacenter Virtual do Azure

Além de usar um desses padrões de arquitetura, se o grupo de TI empresarial gerenciar grandes ambientes de nuvem, considere consultar as [diretrizes do Datacenter Virtual do Azure](../../reference/vdc.md) quando criar sua infraestrutura de nuvem baseada no Azure. O Datacenter Virtual do Azure fornece uma abordagem combinada de rede, segurança, gerenciamento e infraestrutura se a sua organização atende aos seguintes critérios:

- Sua empresa está sujeita à conformidade regulatória que exige recursos de monitoramento e auditoria centralizados.
- Sua propriedade de nuvem será composta por mais de 10 mil VMs de IaaS ou uma escala equivalente de serviços de PaaS.
- Você precisa habilitar as funcionalidades de implantação ágil para cargas de trabalho para dar suporte às equipes de desenvolvedores e de operações, mantendo a conformidade de governança e as políticas comuns e o controle central de TI sobre os serviços principais.
- Seu setor depende de uma plataforma complexa que exige conhecimento profundo do domínio (por exemplo, finanças, petróleo e gás ou produção).
- Suas políticas de governança de TI existentes exigem paridade mais rigorosa com os recursos existentes, mesmo durante a adoção em estágio inicial.

## <a name="follow-azure-networking-best-practices"></a>Siga as melhores práticas de rede do Azure

Como parte do seu processo de design de rede, confira estes artigos:

- [Planejamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Aprenda a planejar redes virtuais com base no seu isolamento, conectividade e requisitos de local.
- [Melhores práticas do Azure de segurança de rede](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Conheça as melhores práticas do Azure que podem ajudar você a aprimorar sua segurança de rede.
- [Melhores práticas de rede quando você migra cargas de trabalho para o Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-networking?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Obtenha outras diretrizes sobre como implementar a rede do Azure para dar suporte a cargas de trabalho baseadas em IaaS e PaaS.
