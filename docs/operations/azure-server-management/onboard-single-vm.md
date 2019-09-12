---
title: Habilitar serviços de gerenciamento em uma única VM para avaliação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Habilitar serviços de gerenciamento em uma única VM para avaliação
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 4ebf0bf17fafcd495414d32fe04882c36634d4e2
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825231"
---
# <a name="enable-management-services-on-a-single-vm-for-evaluation"></a>Habilitar serviços de gerenciamento em uma única VM para avaliação

Saiba como habilitar os serviços de gerenciamento em uma única VM para avaliação.

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de integrar máquinas virtuais aos serviços de gerenciamento do Azure.

A integração de máquinas virtuais individuais (VMs) aos serviços de gerenciamento do servidor do Azure é simples no portal do Azure. O portal permite que você se familiarize com esses serviços antes de integrá-los às suas VMs. Quando você seleciona uma instância de VM, todas as soluções discutidas na lista de [ferramentas e serviços de gerenciamento](./tools-services.md) aparecem no menu **operações** ou no menu **monitoramento** . Você pode selecionar cada solução e seguir o assistente para fazer a integração.

![Captura de tela das configurações da máquina virtual no portal do Azure](./media/onboarding-single-vm.png)

## <a name="related-resources"></a>Recursos relacionados

Para obter mais informações sobre a integração de VMs individuais a cada solução, consulte:

- [Integração de soluções de Gerenciamento de Atualizações, Controle de Alterações e inventário da máquina virtual do Azure](/azure/automation/automation-onboard-solutions-from-vm)
- [Carregar o monitoramento do Azure para a VM](/azure/azure-monitor/insights/vminsights-enable-single-vm)

## <a name="next-steps"></a>Próximas etapas

Saiba como usar Azure Policy para carregar VMs do Azure em escala.

> [!div class="nextstepaction"]
> [Configurar os serviços de gerenciamento do Azure para uma assinatura](./onboard-at-scale.md)
