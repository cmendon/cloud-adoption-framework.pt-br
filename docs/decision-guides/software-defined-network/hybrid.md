---
title: 'Rede definida pelo software: rede híbrida'
description: Use a estrutura de adoção de nuvem para o Azure para saber como as redes híbridas podem conectar redes virtuais de nuvem a recursos locais.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: f84dcbd1a215a34e2b05b63db2a08f64dca34a4b
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708539"
---
# <a name="software-defined-networking-hybrid-network"></a>Rede definida pelo software: rede híbrida

A arquitetura de rede em nuvem híbrida permite que as redes virtuais acessem os recursos e serviços locais e vice-versa, usando uma Conexão WAN dedicada como o ExpressRoute ou outro método de conexão para conectar diretamente as redes.

![Rede híbrida](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/images/expressroute.png)

Criando a arquitetura de rede virtual nativa de nuvem, uma rede virtual híbrida é isolada quando inicialmente criada. Adicionar conectividade ao ambiente local concede acesso de e para a rede local, embora todos os outros recursos de direcionamento de tráfego de entrada na rede virtual precisem ser explicitamente permitidos. É possível proteger a conexão usando dispositivos de firewall virtuais e regras de roteamento para limitar o acesso, especificar exatamente quais serviços podem ser acessados entre as duas redes usando recurso de roteamento nativo de nuvem, ou implantando NVAs (dispositivos virtuais de rede) para gerenciar o tráfego.

Embora a arquitetura de rede híbrida dê suporte a conexões VPN, conexões WAN dedicadas como ExpressRoute são preferenciais devido a um melhor desempenho e maior segurança.

## <a name="hybrid-assumptions"></a>Suposições sobre a rede híbrida

A implantação de uma rede virtual híbrida inclui as seguintes suposições:

- As equipes de segurança de TI alinham a política de segurança de rede local e baseada em nuvem para garantir que as redes virtuais baseadas em nuvem sejam confiáveis para a comunicação direta com os sistemas locais.
- As cargas de trabalho baseadas em nuvem exigem acesso a armazenamento, aplicativos e serviços hospedados nas redes locais ou de terceiros, ou os usuários ou aplicativos locais precisam de acesso a recursos hospedados em nuvem.
- Você precisa migrar aplicativos e serviços existentes que dependem de recursos locais, mas não quer gastar os recursos em redesenvolvimento para remover essas dependências.
- Conectar suas redes locais a recursos de nuvem por VPN ou WAN dedicada não é impedido por política corporativa, requisitos de soberania de dados ou outros problemas de conformidade regulatória.
- Suas cargas de trabalho não exigem várias assinaturas para ignorar limites de recursos de assinatura ou suas cargas de trabalho envolvem várias assinaturas, mas não exigem gerenciamento central de conectividade ou serviços compartilhados usados por recursos distribuídos entre várias assinaturas.

Suas equipes de adoção de nuvem devem considerar os seguintes problemas ao analisar a implementação de uma arquitetura de rede virtual híbrida:

- Conectar redes locais com redes em nuvem aumenta a complexidade dos requisitos de segurança. Ambas as redes devem ser protegidas contra vulnerabilidades externas e acesso não autorizado de ambos os lados do ambiente híbrido.
- O dimensionamento do número e tamanho das cargas de trabalho em um ambiente de nuvem híbrida pode adicionar uma complexidade significativa ao gerenciamento de tráfego e roteamento.
- Será necessário desenvolver políticas de gerenciamento e controle de acesso compatíveis para manter uma governança consistente em toda a organização.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre redes híbridas no Azure, consulte:

- [Arquitetura de referência de rede híbrida](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/expressroute). As redes virtuais híbridas do Azure usam um circuito de ExpressRoute ou VPN do Azure para conectar sua rede virtual com os ativos de ti existentes da sua organização não hospedados no Azure. Este artigo aborda as opções para criar uma rede híbrida no Azure.
