---
title: 'Rede definida pelo software: DMZ da nuvem'
description: Essa arquitetura de rede permite o acesso limitado entre suas redes locais e baseadas em nuvem.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: eee22d6a0322a94ef0968c901642700fdc6247ee
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806655"
---
# <a name="software-defined-networking-cloud-dmz"></a>Rede definida pelo software: DMZ da nuvem

A arquitetura de rede da DMZ de Nuvem permite acesso limitado entre redes locais e baseadas em nuvem, usando uma VPN (rede privada virtual) para conectar as redes. Embora um modelo DMZ seja comumente usado quando você deseja proteger o acesso externo a uma rede, a arquitetura de DMZ da nuvem discutida aqui destina-se especificamente a proteger o acesso à rede local por meio de recursos baseados em nuvem e vice-versa.

![Proteger arquitetura de rede híbrida](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/images/dmz-private.png)

Essa arquitetura foi projetada para dar suporte a cenários em que a organização deseja iniciar a integração de cargas de trabalho baseadas em nuvem com cargas de trabalho locais, mas pode não ter políticas de segurança em nuvem totalmente desenvolvidas ou adquirido uma conexão WAN dedicada segura entre os dois ambientes. Como resultado, as redes em nuvem devem ser tratadas como uma zona desmilitarizada para garantir que os serviços locais sejam seguros.

A DMZ implanta NVAs (dispositivos virtuais de rede) para implementar a funcionalidade de segurança como firewalls e inspeção de pacotes. O tráfego que passa entre aplicativos ou serviços locais e baseados em nuvem deve passar pela DMZ onde pode ser auditado. As conexões VPN e as regras que determinam qual tráfego é permitido pela rede DMZ são estritamente controladas pelas equipes de segurança de TI.

## <a name="cloud-dmz-assumptions"></a>Suposições sobre a DMZ de Nuvem

A implantação de uma DMZ de nuvem inclui as seguintes suposições:

- As equipes de segurança não alinharam totalmente as exigências e políticas de segurança locais e baseadas em nuvem.
- Suas cargas de trabalho baseadas em nuvem exigem acesso ao subconjunto limitado de serviços hospedados em suas redes locais ou de terceiros, ou usuários ou aplicativos em seu ambiente local precisam de acesso limitado a recursos hospedados na nuvem.
- A implementação de uma conexão VPN entre as redes locais e o provedor de nuvem não é impedida pela política corporativa, requisitos regulamentares ou problemas de compatibilidade técnica.
- As cargas de trabalho não exigem várias assinaturas para ignorar limites de recursos de assinatura, ou envolvem várias assinaturas mas não requerem gerenciamento central de conectividade ou serviços compartilhados usados por recursos distribuídos por várias assinaturas.

Suas equipes de adoção de nuvem devem considerar os seguintes problemas ao analisar a implementação de uma arquitetura de rede virtual DMZ da nuvem:

- Conectar redes locais com redes em nuvem aumenta a complexidade dos requisitos de segurança. Embora as conexões entre redes de nuvem e o ambiente local estejam protegidas, você ainda precisa garantir que os recursos de nuvem estejam protegidos. Todos os IPs públicos criados para acessar cargas de trabalho baseadas em nuvem precisam ser devidamente protegidos usando uma [DMZ voltada](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) para o público ou o [Firewall do Azure](https://docs.microsoft.com/azure/firewall).
- A arquitetura de DMZ de Nuvem normalmente é utilizada como um ponto de partida, enquanto a conectividade é mais protegida e a política de segurança é alinhada entre as redes locais e na nuvem, permitindo uma adoção mais ampla de uma arquitetura de rede híbrida em grande escala. No entanto, ele também pode se aplicar a implantações isoladas com segurança, identidade e necessidades de conectividade específicas que a abordagem de DMZ da nuvem atenda.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre como implementar uma DMZ de nuvem no Azure, consulte:

- [Implementar uma DMZ entre o Azure e o datacenter local](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid). Este artigo descreve como implementar uma arquitetura de rede híbrida segura no Azure.
