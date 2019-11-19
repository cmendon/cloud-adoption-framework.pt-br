---
title: 'Rede definida pelo software: nativa na nuvem'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Discussão sobre serviços de rede virtual nativas de nuvem.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: bf585f923a4c8abddeeb56bab4a3a4b8eb370f8d
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160196"
---
# <a name="software-defined-networking-cloud-native"></a>Rede definida pelo software: nativa na nuvem

Uma rede virtual nativa de nuvem é necessária ao implantar recursos de IaaS, como máquinas virtuais, em uma plataforma de nuvem. Acesso a redes virtuais de fontes externas, semelhantes à web, precisa ser provisionado explicitamente. Esses tipos de redes virtuais dão suporte a criação de sub-redes, regras de roteamento e firewall virtual e dispositivos de gerenciamento de tráfego.

Uma rede virtual nativa de nuvem não tem dependências no local ou outros recursos de não nuvem para dar suporte às cargas de trabalho hospedadas na nuvem. Todos os recursos necessários são provisionados na rede virtual em si ou por meio de ofertas de PaaS gerenciadas.

## <a name="cloud-native-assumptions"></a>Pressuposições nativas de nuvem

Implantar uma rede virtual nativa de nuvem pressupõe o seguinte:

- As cargas de trabalho que você implantar a rede virtual não têm dependências em aplicativos ou serviços que são acessíveis somente de dentro de sua rede local. A menos que eles forneçam pontos de extremidade acessíveis pela Internet pública, os aplicativos e serviços hospedados internamente localmente não podem ser usados por recursos hospedados em uma plataforma de nuvem.
- Seu gerenciamento de identidade de carga de trabalho e controle de acesso depende dos serviços de identidade da plataforma ou servidores IaaS hospedados no seu ambiente de nuvem. Você não precisará se conectar diretamente aos serviços de identidade hospedados no local ou em locais externos.
- Os serviços de identidade não precisam dar suporte a logon único (SSO) com diretórios locais.

As redes virtuais nativas de nuvem não têm dependências externas. Isso os torna simples para implantar e configurar, e como o resultado dessa arquitetura é geralmente a melhor escolha para experimentos ou outras implantações menores independentes ou iteradas rapidamente.

Outros problemas que suas equipes de adoção de nuvem devem considerar ao discutir uma arquitetura de rede virtual nativa de nuvem incluem:

- Cargas de trabalho existentes, projetadas para serem executadas em um datacenter local, talvez seja necessário uma extensa modificação para tirar proveito da funcionalidade baseada em nuvem, como os serviços de armazenamento ou autenticação.
- As redes nativas de nuvem são gerenciadas exclusivamente por meio das ferramentas de gerenciamento da plataforma de nuvem e, portanto, podem levar ao gerenciamento e à divergência de políticas de seus padrões de ti existentes à medida que o tempo continua.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre redes virtuais nativas de nuvem no Azure, consulte:

- [Rede virtual do Azure: guias de instruções](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm). Redes Virtuais do Azure recentemente criadas são nativas de nuvem por padrão. Use esses guias para ajudar a planejar a criação e implantação de suas redes virtuais.
- [Limites de assinatura: rede](https://docs.microsoft.com/azure/azure-subscription-service-limits?toc=/azure/virtual-network/toc.json#networking-limits). Qualquer rede virtual única e os recursos conectados só podem existir em uma única assinatura e são associados por limites de assinatura.
