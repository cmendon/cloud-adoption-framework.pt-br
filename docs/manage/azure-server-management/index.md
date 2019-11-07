---
title: Visão geral dos serviços de gerenciamento do servidor do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução aos serviços de gerenciamento do servidor do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: c4939464c80668ca175a4d7ac53fe2198610afc1
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565362"
---
# <a name="overview-of-azure-server-management-services"></a>Visão geral dos serviços de gerenciamento do servidor do Azure

Os serviços de gerenciamento do servidor do Azure fornecem aos clientes uma experiência consistente para gerenciar seus servidores em escala. Esses serviços abrangem os sistemas operacionais Linux e Windows e podem ser usados em ambientes de produção, desenvolvimento e teste. Além disso, eles podem ser compatíveis com máquinas virtuais de IaaS do Azure, máquinas virtuais e servidores físicos hospedados localmente ou em outros ambientes de hospedagem.

O pacote de serviços de gerenciamento do servidor do Azure inclui os serviços mostrados no diagrama a seguir.

![Diagrama do modelo de operações do Azure](./media/operations-diagram.png)

As diretrizes desta seção do Cloud Adoption Framework da Microsoft fornecem um plano prescritivo acionável para a implantação de serviços de gerenciamento do servidor em seu ambiente. Esse plano tem como objetivo orientar você rapidamente sobre esses serviços, guiando você por um conjunto incremental de estágios de gerenciamento para todos os tamanhos de ambiente.

Para simplificar, categorizamos essas diretrizes em três estágios:

![Os três estágios de integração do pacote de gerenciamento do servidor do Azure](./media/operations-stages.png)

<!-- markdownlint-disable MD026 -->

## <a name="why-use-azure-management-services"></a>Por que usar os serviços de gerenciamento do Azure?

Os serviços de gerenciamento do Azure oferecem os seguintes benefícios:

- **Nativo no Azure:** Os serviços de gerenciamento são inseridos e integrados nativamente com o Azure Resource Manager. Eles são continuamente aprimorados para fornecer novos recursos e novas funcionalidades.
- **Windows e Linux:** Os computadores Windows e Linux têm a mesma experiência consistente de gerenciamento.
- **Híbrido:** Os serviços de gerenciamento abrangem máquinas virtuais de IaaS do Azure, bem como servidores físicos e virtuais hospedados localmente ou em outros ambientes de hospedagem.
- **Segurança:** A Microsoft dedica recursos substanciais a todas as formas de segurança. Esse investimento não só protege a infraestrutura de nuvem do Azure, mas também estende as tecnologias e as competências resultantes para proteger os recursos dos clientes onde quer que estejam.

## <a name="next-steps"></a>Próximas etapas

Familiarize-se com as [ferramentas, os serviços e o planejamento](./prerequisites.md) envolvidos com a adoção do pacote de gerenciamento do servidor do Azure.

> [!div class="nextstepaction"]
> [Ferramentas e planejamento de pré-requisito](./prerequisites.md)
