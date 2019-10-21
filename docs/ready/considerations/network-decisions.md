---
title: Decisões de design de rede de preparação do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisões de design de rede de preparação do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 39eaf02d2701cc6f9ba2c12751b5e53ff1386776
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548814"
---
# <a name="networking-design-decisions"></a>Decisões de design de rede

Projetar e implementar recursos de rede do Azure é uma parte essencial dos seus esforços de adoção de nuvem. Você precisará tomar decisões de design de rede para dar suporte adequado às cargas de trabalho e aos serviços que serão hospedados na nuvem. Os produtos e serviços de rede do Azure dão suporte a uma ampla variedade de recursos de rede. A forma como você estrutura esses serviços e as arquiteturas de rede que você escolhe depende dos requisitos de carga de trabalho, governança e conectividade de sua organização.

## <a name="identify-workload-networking-requirements"></a>Identificar requisitos de rede de carga de trabalho

Como parte de sua avaliação e preparação da zona de aterrissagem, você precisa identificar os recursos de rede que sua zona de aterrissagem precisa dar suporte. Esse processo envolve avaliar cada um dos aplicativos e serviços que compõem suas cargas de trabalho para determinar seus requisitos de controle de rede de conectividade. Depois de identificar e documentar os requisitos, você pode criar políticas para sua zona de aterrissagem para controlar os recursos de rede permitidos e a configuração com base em suas necessidades de carga de trabalho.

Para cada aplicativo ou serviço que você implantará em seu ambiente de zona de aterrissagem, use a seguinte árvore de decisão como um ponto de partida para ajudá-lo a determinar as ferramentas de rede ou os serviços a serem usados:

![Árvore de decisão dos serviços de rede do Azure](../../_images/ready/network-decision-tree.png)

### <a name="key-questions"></a>Principais perguntas

Responda às seguintes perguntas sobre suas cargas de trabalho para ajudá-lo a tomar decisões com base na árvore de decisão dos serviços de rede do Azure:

- **Suas cargas de trabalho precisarão de uma rede virtual?** Os tipos de recursos de PaaS (plataforma como serviço) gerenciados usam recursos de rede da plataforma subjacente que nem sempre exigem uma rede virtual. Se suas cargas de trabalho não exigirem recursos de rede avançados e você não precisar implantar recursos de IaaS (infraestrutura como serviço), os recursos de [rede nativa padrão fornecidos pelos recursos de PaaS](../../decision-guides/software-defined-network/paas-only.md) podem atender à conectividade de sua carga de trabalho e requisitos de gerenciamento de tráfego.
- **Suas cargas de trabalho precisarão de conectividade entre redes virtuais e seu datacenter local?** O Azure fornece duas soluções para estabelecer recursos de rede híbrida: gateway de VPN do Azure e Azure ExpressRoute. O [Gateway de VPN do Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways) conecta suas redes locais ao Azure por meio de VPNs site a site semelhantes a como você pode configurar e se conectar a uma filial remota. O gateway de VPN tem uma largura de banda máxima de 1,25 GBps. O [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) oferece maior confiabilidade e latência mais baixa usando uma conexão privada entre o Azure e sua infraestrutura local. As opções de largura de banda para o ExpressRoute variam de 50 MBps a 100 GBps.
- **Será necessário inspecionar e auditar o tráfego de saída usando dispositivos de rede locais?** Para cargas de trabalho nativas de nuvem, você pode usar o [Firewall do Azure](https://docs.microsoft.com/azure/firewall/overview) ou as soluções de [virtualização de rede de terceiros (NVAs)](https://azure.microsoft.com/solutions/network-appliances) hospedadas na nuvem para inspecionar e auditar o tráfego que será proveniente da Internet pública. No entanto, muitas políticas de segurança de ti corporativas exigem o tráfego de saída associado à Internet para passar por dispositivos gerenciados centralmente no ambiente local da organização. O [túnel forçado](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview) dá suporte a esses cenários. Nem todos os serviços gerenciados dão suporte a túnel forçado. Serviços e recursos como [ambiente do serviço de aplicativo no serviço Azure app](https://docs.microsoft.com/azure/app-service/environment/intro), [Gerenciamento de API do Azure](https://docs.microsoft.com/azure/api-management/api-management-key-concepts), [AKs (serviço kubernetes do Azure)](https://docs.microsoft.com/azure/aks/intro-kubernetes), [instâncias gerenciadas no banco de dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index), [Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/what-is-azure-databricks)e [Azure O HDInsight](https://docs.microsoft.com/azure/hdinsight) dá suporte a essa configuração quando o serviço ou recurso é implantado dentro de uma rede virtual.
- **Será necessário conectar várias redes virtuais?** Você pode usar o [emparelhamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) para conectar várias instâncias da [rede virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). O emparelhamento pode dar suporte a conexões entre assinaturas e regiões. Para cenários em que você fornece serviços que são compartilhados entre várias assinaturas ou precisam gerenciar um grande número de emparelhamentos de rede, considere a adoção de uma [arquitetura de rede de Hub e spoke](../../decision-guides/software-defined-network/hub-spoke.md) ou usando a [Wan virtual do Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about). O emparelhamento de rede virtual fornece conectividade somente entre duas redes emparelhadas. Por padrão, ele não fornece conectividade transitiva entre vários emparelhamentos.
- **Suas cargas de trabalho poderão ser acessadas pela Internet?** O Azure fornece serviços projetados para ajudá-lo a gerenciar e proteger o acesso externo aos seus aplicativos e serviços:
  - [Firewall do Azure](https://docs.microsoft.com/azure/firewall/overview)
  - [Dispositivos de rede](https://azure.microsoft.com/solutions/network-appliances)
  - [Serviço de porta frontal do Azure](https://docs.microsoft.com/azure/frontdoor/front-door-overview)
  - [Application Gateway do Azure](https://docs.microsoft.com/azure/application-gateway)
  - [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)
- **Será necessário dar suporte ao gerenciamento de DNS personalizado?** O [DNS do Azure](https://docs.microsoft.com/azure/dns/dns-overview) é um serviço de hospedagem para domínios DNS. O DNS do Azure fornece a resolução de nomes usando a infraestrutura do Azure. Se suas cargas de trabalho exigirem resolução de nomes que ultrapasse os recursos fornecidos pelo DNS do Azure, talvez seja necessário implantar soluções adicionais. Se suas cargas de trabalho também exigirem serviços Active Directory, considere o uso de [Azure Active Directory Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/overview) para aumentar os recursos do DNS do Azure. Para obter mais recursos, você também pode [implantar máquinas virtuais IaaS personalizadas](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances) para dar suporte às suas necessidades.

## <a name="common-networking-scenarios"></a>Cenários comuns de rede

A rede do Azure é composta por vários produtos e serviços que fornecem diferentes recursos de rede. Como parte do seu processo de design de rede, você pode comparar seus requisitos de carga de trabalho com os cenários de rede na tabela a seguir para identificar as ferramentas do Azure ou os serviços que você pode usar para fornecer esses recursos de rede:

<!-- markdownlint-disable MD033 -->

| **Cenário** | **Produto ou serviço de rede** |
| --- | --- |
| Preciso da infraestrutura de rede para conectar tudo, de máquinas virtuais a conexões VPN de entrada. | [Rede Virtual do Azure](https://docs.microsoft.com/azure/virtual-network) |
| Preciso balancear conexões de entrada e saída e solicitações para meus aplicativos ou serviços. | [Balanceador de carga do Azure](https://docs.microsoft.com/azure/load-balancer) |
| Quero otimizar a entrega de farms de servidores de aplicativos enquanto aumenta a segurança de aplicativos com um firewall do aplicativo Web. | [Application Gateway do Azure](https://docs.microsoft.com/azure/application-gateway) <br/>[Serviço de porta frontal do Azure](https://docs.microsoft.com/azure/frontdoor) |
| Preciso usar a Internet com segurança para acessar a rede virtual do Azure por meio de gateways de VPN de alto desempenho. | [Gateway de VPN do Azure](https://docs.microsoft.com/azure/vpn-gateway) |
| Quero garantir respostas de DNS extremamente rápidas e alta disponibilidade para todas as minhas necessidades de domínio. | [DNS do Azure](https://docs.microsoft.com/azure/dns) |
| Preciso acelerar a entrega de conteúdo de alta largura de banda aos clientes em todo o mundo, de aplicativos e conteúdo armazenado para streaming de vídeo. | [Rede de distribuição de conteúdo do Azure](https://docs.microsoft.com/azure/cdn) |
| Preciso proteger meus aplicativos do Azure contra ataques de DDoS. | [Proteção contra DDoS do Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) |
| Preciso distribuir o tráfego de forma ideal para serviços em regiões globais do Azure, fornecendo, ao mesmo tempo, alta disponibilidade e capacidade de resposta. | [Gerenciador de Tráfego do Azure](https://docs.microsoft.com/azure/traffic-manager)<br/>[Serviço de porta frontal do Azure](https://docs.microsoft.com/azure/frontdoor) |
| Preciso adicionar conectividade de rede privada para acessar os serviços de nuvem da Microsoft de minhas redes corporativas, como se elas estivessem locais e residindo em meu próprio datacenter. | [Azure ExpressRoute](https://docs.microsoft.com/azure/expressroute) |
| Quero monitorar e diagnosticar condições em um nível de cenário de rede. | [Observador de rede do Azure](https://docs.microsoft.com/azure/network-watcher) |
| Preciso de recursos de firewall nativo, com alta disponibilidade interna, escalabilidade de nuvem irrestrita e manutenção zero. | [Firewall do Azure](https://docs.microsoft.com/azure/firewall) |
| Preciso conectar escritórios de negócios, locais de varejo e sites com segurança. | [WAN virtual do Azure](https://docs.microsoft.com/azure/virtual-wan) |
| Preciso de um ponto de entrega escalonável e com segurança aprimorado para aplicativos Web baseados em microserviços globais. | [Serviço de porta frontal do Azure](https://docs.microsoft.com/azure/frontdoor) |

<!-- markdownlint-enable MD033 -->

## <a name="choose-a-networking-architecture"></a>Escolher uma arquitetura de rede

Depois de identificar os serviços de rede do Azure que você precisa para dar suporte às suas cargas de trabalho, você também precisará projetar a arquitetura que combinará esses serviços para fornecer a infraestrutura de rede de nuvem da sua zona de aterrissagem. O [Guia de decisão de rede definida pelo software](../../decision-guides/software-defined-network/index.md) da estrutura de adoção de nuvem fornece detalhes sobre alguns dos padrões de arquitetura de rede mais comuns usados no Azure.

A tabela a seguir resume os principais cenários aos quais esses padrões dão suporte:

| **Cenário** | **Arquitetura de rede sugerida**
| --- | --- |
| Todas as cargas de trabalho hospedadas no Azure implantadas em sua zona de aterrissagem serão totalmente baseadas em PaaS, não exigirão uma rede virtual e não fazem parte de um esforço de adoção de nuvem maior que incluirá recursos de IaaS. | [Somente PaaS](../../decision-guides/software-defined-network/paas-only.md) |
| Suas cargas de trabalho hospedadas no Azure implantarão recursos baseados em IaaS como máquinas virtuais ou, de outra forma, exigirão uma rede virtual, mas não exigem conectividade com seu ambiente local. | [Nativo de nuvem](../../decision-guides/software-defined-network/cloud-native.md) |
| Suas cargas de trabalho hospedadas no Azure exigem acesso limitado a recursos locais, mas você precisa tratar as conexões de nuvem como não confiáveis. | [DMZ da nuvem](../../decision-guides/software-defined-network/cloud-dmz.md) |
| Suas cargas de trabalho hospedadas no Azure exigem acesso limitado a recursos locais e você planeja implementar políticas de segurança maduras e proteger a conectividade entre a nuvem e o ambiente local. | [Ti](../../decision-guides/software-defined-network/hybrid.md) |
| Você precisa implantar e gerenciar um grande número de VMs e cargas de trabalho, potencialmente excedendo [os limites de assinatura do Azure](https://docs.microsoft.com/azure/azure-subscription-service-limits), você precisa compartilhar serviços entre assinaturas ou precisar de uma estrutura mais segmentada para segregação de função, aplicativo ou permissão. | [Hub e spoke](../../decision-guides/software-defined-network/hub-spoke.md) |
| Você tem muitas filiais que precisam se conectar entre si e com o Azure. | [WAN virtual do Azure](https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about) |

### <a name="azure-virtual-datacenter"></a>Datacenter virtual do Azure

Além de usar um desses padrões de arquitetura, se seu grupo de ti empresarial gerencia grandes ambientes de nuvem, considere consultar as [diretrizes de datacenter virtual do Azure](../../reference/vdc.md) ao projetar sua infraestrutura de nuvem baseada no Azure. O datacenter virtual do Azure fornece uma abordagem combinada de rede, segurança, gerenciamento e infraestrutura se sua organização atender aos seguintes critérios:

- Sua empresa está sujeita à conformidade regulatória que exige recursos de monitoramento e auditoria centralizados.
- Seu estado de nuvem consistirá em mais de 10.000 VMs de IaaS ou em uma escala equivalente de serviços de PaaS.
- Você precisa habilitar os recursos de implantação Agile para cargas de trabalho para dar suporte a equipes de desenvolvedor e operações, mantendo a conformidade de políticas e de governança comuns e o controle central de ti sobre os serviços principais.
- Seu setor depende de uma plataforma complexa que exige um profundo conhecimento do domínio (por exemplo, finanças, petróleo e gás ou manufatura).
- Suas políticas de governança de ti existentes exigem uma paridade mais rígida com recursos existentes, mesmo durante a adoção de estágio inicial.

## <a name="follow-azure-networking-best-practices"></a>Siga as práticas recomendadas de rede do Azure

Como parte do seu processo de design de rede, consulte estes artigos:

- [Planejamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba como planejar as redes virtuais com base em seus requisitos de isolamento, conectividade e local.
- [Práticas recomendadas do Azure para segurança de rede](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Saiba mais sobre as práticas recomendadas do Azure que podem ajudá-lo a aprimorar sua segurança de rede.
- [Práticas recomendadas para rede ao migrar cargas de trabalho para o Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-networking?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Obtenha orientações adicionais sobre como implementar a rede do Azure para dar suporte a cargas de trabalho baseadas em IaaS e em PaaS.
