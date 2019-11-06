---
title: Habilitar serviços de gerenciamento de servidor em uma única VM para avaliação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Habilitar serviços de gerenciamento de servidor em uma única VM para avaliação
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 6dbc0dce4e129a785ddd3ae735115a211bf04dee
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656534"
---
# <a name="enable-server-management-services-on-a-single-vm-for-evaluation"></a>Habilitar serviços de gerenciamento de servidor em uma única VM para avaliação

Saiba como habilitar os serviços de gerenciamento de servidor em uma única VM para avaliação.

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de implementar os serviços de gerenciamento do Azure em uma VM.

É simples integrar os serviços de gerenciamento do servidor do Azure a máquinas virtuais individuais no portal do Azure. Você pode se familiarizar com esses serviços antes de integrá-los. Quando você seleciona uma instância de VM, todas as soluções na lista de [ferramentas e serviços de gerenciamento](./tools-services.md) são exibidas no menu **operações** ou **monitoramento** . Você seleciona uma solução e segue o assistente para integrá-la.

![Captura de tela das configurações da máquina virtual no portal do Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Recursos relacionados

Para obter mais informações sobre como carregar essas soluções para VMs individuais, consulte:

- [Integração de soluções de Gerenciamento de Atualizações, Controle de Alterações e inventário da máquina virtual do Azure](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-vm)
- [Integração do monitoramento do Azure para VMs](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Próximos passos

Saiba como usar a política do Azure para carregar VMs do Azure em escala.

> [!div class="nextstepaction"]
> [Configurar os serviços de gerenciamento do Azure para uma assinatura](./onboard-at-scale.md)
