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
ms.openlocfilehash: 4d1ada9d47e54f4b0d3828ce93b2d55f3eda8a34
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025628"
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

- **Nativos ao Azure.** Os serviços de gerenciamento são inseridos e integrados nativamente com o Azure Resource Manager. Eles são continuamente aprimorados para fornecer novos recursos e novas funcionalidades.
- **Windows e Linux**. Os computadores Windows e Linux têm a mesma experiência consistente de gerenciamento.
- **Híbridos.** Os serviços de gerenciamento abrangem máquinas virtuais de IaaS do Azure, bem como servidores físicos e virtuais hospedados localmente ou em outros ambientes de hospedagem.
- **Segurança.** A Microsoft dedica recursos substanciais a todas as formas de segurança. Esse investimento não só protege a infraestrutura de nuvem do Azure, mas também estende as tecnologias e as competências resultantes para proteger os recursos dos clientes onde quer que estejam.

## <a name="next-steps"></a>Próximas etapas

Familiarize-se com as [ferramentas, os serviços e o planejamento](./prerequisites.md) envolvidos com a adoção do pacote de gerenciamento do servidor do Azure.

> [!div class="nextstepaction"]
> [Ferramentas e planejamento de pré-requisito](./prerequisites.md)
