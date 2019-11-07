---
title: Guia de decisão de Rede Definida por Software
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda sobre redes definidas pelo software como um serviço principal em migrações do Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 46d01d6685b4cac55db7ed313b70891b4f9c029f
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564782"
---
# <a name="software-defined-networking-decision-guide"></a>Guia de decisão de Rede Definida por Software

A SDN (Rede Definida pelo Software) é uma arquitetura de rede projetada para permitir a funcionalidade de rede virtualizada que pode ser gerenciada, configurada e modificada centralmente por meio de software. SDN permite a criação de redes baseadas em nuvem usando os equivalentes virtualizados de roteadores físicos, firewalls e outros dispositivos de rede usados em redes locais. SDN é fundamental para criar redes virtuais seguras em plataformas de nuvem pública, como o Azure.

## <a name="networking-decision-guide"></a>Guia de decisão de rede

![Plotagem das opções de rede da menos para a mais complexa, alinhada com links de salto abaixo](../../_images/decision-guides/decision-guide-software-defined-network.png)

Ir para: [Somente PaaS](./paas-only.md) | [Nativo de Nuvem](./cloud-native.md) | [DMZ de Nuvem](./cloud-dmz.md) [Híbrido](./hybrid.md) | [Modelo de Hub e spoke](./hub-spoke.md) | [Saiba mais](#learn-more)

A SDN oferece várias opções com diferentes graus de complexidade e preço. O guia de descoberta acima fornece uma referência para personalizar rapidamente essas opções e alcançar melhor alinhamento com as estratégias tecnológicas e específicas do negócio.

O ponto de inflexão nesse guia depende de várias decisões importantes que a equipe de estratégia de nuvem tenha realizado antes de tomar decisões sobre a arquitetura de rede. Entre elas, as mais importantes são as decisões que envolvem a [definição de acervo digital](../../digital-estate/index.md) e [design de assinatura](../subscriptions/index.md) (que também pode exigir inserções das decisões tomadas relacionadas às estratégias de mercados globais e contabilidade de nuvem).

Implantações de região única e pequena de menos de 1.000 VMs têm menor probabilidade de serem significativamente afetadas por esse ponto de inflexão. Por outro lado, grandes esforços de adoção com mais de 1.000 VMs, várias unidades de negócios ou vários mercados geopolíticos podem ser substancialmente afetados pela decisão de SDN e esse ponto-chave de inflexão.

## <a name="choose-the-right-virtual-networking-architectures"></a>Escolha as arquiteturas de rede virtual certas

Essa seção expande o guia de decisão para ajudá-lo a escolher as arquiteturas de rede virtual corretas.

Há muitas maneiras de implementar tecnologias de SDN para criar redes virtuais baseadas em nuvem. O modo como você estrutura as redes virtuais usadas na migração e como essas redes interagem com a infraestrutura de TI existente dependerá de uma combinação dos requisitos de carga de trabalho e os requisitos de controle.

Ao planejar qual arquitetura de rede virtual ou combinação de arquiteturas deverá ser considerada ao planejar a migração na nuvem, considere as seguintes perguntas para ajudar a determinar a correta para a organização:

| Pergunta | PaaS-only | Nativo da nuvem | DMZ de nuvem | Híbrido | Hub e spoke |
|-----|-----|-----|-----|-----|-----|
| A carga de trabalho utilizará apenas serviços de PaaS e não exigirá recursos de rede além daqueles fornecidos pelos próprios serviços? | Sim | Não | Não | Não | Não |
| A carga de trabalho requer integração com aplicativos locais? | Não | Não | sim | sim | Sim |
| Você estabeleceu políticas de segurança sólidas e conectividade segura entre o local e as redes na nuvem? | Não | Não | Não | sim | Sim |
| A carga de trabalho exige serviços de autenticação que não têm suporte por meio dos serviços de identidade na nuvem ou você precisa de acesso direto aos controladores de domínio locais? | Não | Não | Não | sim | Sim |
| Você precisará implantar e gerenciar um grande número de VMs e cargas de trabalho? | Não | Não | Não | Não | Sim |
| Você precisará fornecer gerenciamento centralizado e conectividade local ao delegar controle sobre recursos a equipes de carga de trabalho individuais? | Não | Não | Não | Não | Sim |

## <a name="virtual-networking-architectures"></a>Arquiteturas de redes virtuais

Saiba mais sobre as principais arquiteturas de rede definidas pelo software:

- **[Somente PaaS](./paas-only.md):** a maioria dos produtos de PaaS (plataforma como serviço) dá suporte a um conjunto limitado de recursos de rede internos e pode não exigir uma rede definida pelo software definida explicitamente para dar suporte aos requisitos de carga de trabalho.
- **[Nativo da nuvem](./cloud-native.md):** uma arquitetura nativa de nuvem dá suporte a cargas de trabalho baseadas em nuvem usando redes virtuais criadas nas funcionalidades de rede definidas por software padrão da plataforma de nuvem sem depender de recursos locais ou outros recursos externos.
- **[DMZ de nuvem](./cloud-dmz.md):** dá suporte limitado para conectividade entre suas redes locais e na nuvem, protegidas por meio da implementação de uma zona desmilitarizada que controla rigidamente o tráfego entre os dois ambientes.
- **[Híbrida](./hybrid.md):** a arquitetura de rede de nuvem híbrida permite que as redes virtuais em ambientes de nuvem confiáveis acessem recursos locais e vice-versa.
- **[Hub e Spoke](./hub-spoke.md):** A arquitetura hub e spoke permite gerenciar centralmente a conectividade externa e os serviços compartilhados, isolar as cargas de trabalho individuais e superar possíveis limites de assinatura.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre Rede Definida por Software no Azure, veja:

- [Rede Virtual do Microsoft Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview). No Azure, o recurso de SDN principal é fornecido pela Rede Virtual do Azure, que atua como um análogo de nuvem para redes locais físicas. As redes virtuais também atuam como um limite de isolamento padrão entre recursos na plataforma.
- [Melhores práticas do Azure de segurança de rede](https://docs.microsoft.com/azure/security/azure-security-network-security-best-practices). Recomendações da equipe de Segurança do Azure sobre como configurar as redes virtuais para minimizar as vulnerabilidades de segurança.

## <a name="next-steps"></a>Próximas etapas

rede definida por software é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
