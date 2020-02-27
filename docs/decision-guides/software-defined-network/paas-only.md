---
title: 'Rede definida pelo software: somente PaaS'
description: Saiba mais sobre as vantagens e limitações de um modelo de arquitetura somente PaaS em rede definida por software na nuvem.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 14b1a068f4f1011fe10a61dd8f9a7738f7b35f07
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77707961"
---
# <a name="software-defined-networking-paas-only"></a>Rede definida pelo software: somente PaaS

Quando você implementa uma plataforma como um recurso de serviço (PaaS), o processo de implantação cria automaticamente uma rede subjacente assumida com um número limitado de controles na rede, incluindo balanceamento de carga, bloqueio de porta e conexões com outros serviços PaaS.

No Azure, vários tipos de recursos de PaaS podem ser [implantados](https://docs.microsoft.com/azure/virtual-network/virtual-network-for-azure-services) ou [conectados a](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) uma rede virtual, permitindo que esses recursos integrem sua infraestrutura de rede virtual existente. Outros serviços, como [ambientes de serviço de aplicativo](https://docs.microsoft.com/azure/app-service/environment/intro), [AKs (serviço de kubernetes do Azure)](https://docs.microsoft.com/azure/aks/intro-kubernetes)e [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) devem ser implantados na rede virtual. No entanto, em muitos casos, uma única arquitetura de rede de PaaS, contando apenas com os recursos de rede nativa padrão fornecidos pelos recursos de PaaS, é suficiente para atender aos requisitos de conectividade e gerenciamento de tráfego de uma carga de trabalho.

Se você estiver considerando uma arquitetura de rede somente de PaaS, certifique-se de que validar as suposições necessárias se alinha suas necessidades.

## <a name="paas-only-assumptions"></a>Suposições somente PaaS

Implantação de uma arquitetura de rede somente PaaS pressupõe o seguinte:

- O aplicativo que está sendo implantado é um aplicativo autônomo ou depende apenas de outros recursos de PaaS que não exigem uma rede virtual.
- As equipes de operações de TI podem atualizar suas ferramentas, treinamento e processos para dar suporte ao gerenciamento, configuração e implantação de aplicativos de PaaS autônomo.
- O aplicativo de PaaS não faz parte de um esforço de migração de nuvem mais abrangente que inclui recursos de IaaS.

Essas suposições são qualificadores mínimos alinhados ao implantar uma rede somente PaaS. Embora essa abordagem possa se alinhar com os requisitos de uma única implantação de aplicativo, cada equipe de adoção de nuvem deve considerar estas perguntas a longo prazo:

- Essa implantação será expandida no escopo ou escala para exigir acesso a outros recursos sem PaaS?
- Outras implantações de PaaS estão planejadas além da solução atual?
- A organização tem planos para outras migrações de nuvem futuras?

As respostas a essas perguntas não impediriam que uma equipe escolhesse uma única opção PaaS, mas deveriam ser considerada antes de tomar uma decisão final.
