---
title: 'Rede definida pelo software: Hub e spoke'
description: Discussão sobre serviços de rede virtual nativas de nuvem.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: a24ccb7f382e03b3eb0138e94e6b02954c36bd87
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806621"
---
# <a name="software-defined-networking-hub-and-spoke"></a>Rede definida pelo software: Hub e spoke

O modelo de rede hub e spoke organiza a sua infraestrutura de rede de nuvem baseada no Azure em várias redes virtuais conectadas. Esse modelo permite a você gerenciar requisitos comuns de comunicação ou segurança com mais eficiência e lidar com possíveis limitações de assinatura.

No modelo hub e spoke, o _hub_ é uma rede virtual que atua como um local central para gerenciar a conectividade externa e hospedagem de serviços usados por várias cargas de trabalho. Os _spokes_ são as redes virtuais que hospedam as cargas de trabalho e conectam-se ao hub central por meio do [emparelhamento de rede virtual](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).

Passando dentro ou fora de redes de spoke de carga de trabalho, todo o tráfego é roteado por meio da rede de hub em que ele pode ser roteado, inspecionado ou de alguma forma gerenciado por regras de IT centralmente gerenciadas ou processos.

Esse modelo tem como objetivo abordar cada uma das seguintes preocupações:

- **Economia de custos e eficiência de gerenciamento.** A centralização de serviços que podem ser compartilhados por diversas cargas de trabalho, tais como soluções de virtualização de rede (NVAs) e servidores DNS em um local permite que a TI minimize recursos redundantes e esforço de gerenciamento em várias cargas de trabalho.
- **Superando limites de assinaturas.** Grandes cargas de trabalho baseadas em nuvem podem exigir o uso de mais recursos que são permitidos em uma única assinatura do Azure (consulte [limites de assinatura](https://docs.microsoft.com/azure/azure-subscription-service-limits)). Redes virtuais de carga de trabalho de emparelhamento de assinaturas diferentes para um hub central podem superar esses limites.
- **Separação de preocupações.** A capacidade de implantar cargas de trabalho individuais entre as equipes de TI centrais e as equipes de cargas de trabalho.

O diagrama a seguir mostra um hub de exemplo e arquitetura de spoke incluindo conectividade híbrida gerenciada centralmente.

![Arquitetura de rede hub e spoke](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/images/hub-spoke.png)

A arquitetura hub e spoke é frequentemente usada junto com a arquitetura de rede híbrida, fornecendo uma conexão gerenciada centralmente a ao seu ambiente local compartilhado entre várias cargas de trabalho. Nesse cenário, todo tráfego viajando entre as cargas de trabalho e locais, passa pelo hub, onde pode ser gerenciado e protegido.

## <a name="hub-and-spoke-assumptions"></a>Suposições de hub e spoke

Implementar uma arquitetura de rede virtual hub e spoke pressupõe o seguinte:

- As implantações de nuvem envolverão as cargas de trabalho hospedadas em ambientes de trabalho separados, como desenvolvimento, teste e produção, todos se baseiam em um conjunto de serviços comuns, como DNS ou serviços de diretório.
- Suas cargas de trabalho não precisam se comunicar entre si, mas ter comunicações externas comuns e requisitos de serviços compartilhados.
- Suas cargas de trabalho exigem mais recursos que estão disponíveis em uma única assinatura do Azure.
- Você precisa fornecer para as equipes de carga de trabalho direitos de gerenciamento delegado sobre seus próprios recursos enquanto mantêm o controle da central de segurança sobre conectividade externa.

## <a name="global-hub-and-spoke"></a>Hub e spoke global

As arquiteturas hub e spoke são normalmente implementadas com redes virtuais implantadas à mesma região do Azure para minimizar a latência entre as redes. Porém, organizações grandes com um alcance global podem precisar implantar cargas de trabalho através de várias regiões para disponibilidade, recuperação de desastres ou requisitos regulatórios. O modelo Hub e spoke pode usar o [emparelhamento de rede virtual global](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) do Azure para estender o gerenciamento centralizado e os serviços compartilhados entre regiões e dar suporte a cargas de trabalho distribuídas em todo o mundo.

## <a name="learn-more"></a>Saiba mais

Para obter exemplos de como implementar as redes de hub e spoke no Azure, consulte os exemplos a seguir no site de Arquiteturas de Referência do Azure:

- [Implementar uma topologia de rede hub e spoke no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/hub-spoke)
- [Implementar uma topologia de rede de Hub e spoke com serviços compartilhados no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services)
