---
title: Visão geral dos serviços de gerenciamento do servidor do Azure
description: Entenda o plano prescritivo fornecido nesta seção do Cloud Adoption Framework para o Azure para implantar serviços de gerenciamento de servidor em seu ambiente.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: c6afdfe05a9245d729b17d1d56f3c64ffa6107bd
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341667"
---
# <a name="overview-of-azure-server-management-services"></a>Visão geral dos serviços de gerenciamento do servidor do Azure

Os serviços de gerenciamento de servidor do Azure fornecem uma experiência consistente para gerenciar servidores em escala. Esses serviços abrangem os sistemas operacionais Linux e Windows. Eles podem ser usados em ambientes de produção, desenvolvimento e teste. Os serviços de gerenciamento de servidor podem dar suporte a máquinas virtuais de IaaS do Azure, servidores físicos e máquinas virtuais hospedadas localmente ou em outros ambientes de hospedagem.

O pacote de serviços de gerenciamento do servidor do Azure inclui os serviços presentes no diagrama a seguir: ![Diagrama do modelo de operações do Azure](./media/operations-diagram.png)

Esta seção do Microsoft Cloud Adoption Framework fornece um plano prescritivo e acionável para a implantação de serviços de gerenciamento do servidor em seu ambiente. Esse plano orienta você rapidamente sobre esses serviços, guiando você por um conjunto incremental de estágios de gerenciamento para todos os tamanhos de ambiente.

Para simplificar, categorizamos essas diretrizes em três estágios:

![Os três estágios de integração do pacote de gerenciamento do servidor do Azure](./media/operations-stages.png)

<!-- markdownlint-disable MD026 -->

## <a name="why-use-azure-server-management-services"></a>Por que usar os serviços de gerenciamento de servidor do Azure?

Os serviços de gerenciamento de servidor do Azure oferecem os seguintes benefícios:

- **Nativo no Azure:** os serviços de gerenciamento de servidor são inseridos e integrados nativamente ao Azure Resource Manager. Eles são continuamente aprimorados para fornecer novos recursos e novas funcionalidades.
- **Windows e Linux:** os computadores Windows e Linux obtêm a mesma experiência de gerenciamento consistente.
- **Híbrido:** os serviços de gerenciamento de servidor abrangem máquinas virtuais de IaaS do Azure, bem como servidores físicos e virtuais hospedados localmente ou em outros ambientes de hospedagem.
- **Segurança:** A Microsoft dedica recursos substanciais a todas as formas de segurança. Esse investimento não só protege a infraestrutura do Azure, mas também estende as tecnologias e as competências resultantes para proteger os recursos dos clientes onde quer que estejam.

## <a name="next-steps"></a>Próximas etapas

Familiarize-se com as [ferramentas, os serviços e o planejamento](./prerequisites.md) envolvidos com a adoção do pacote de gerenciamento do servidor do Azure.

> [!div class="nextstepaction"]
> [Ferramentas e planejamento de pré-requisito](./prerequisites.md)
