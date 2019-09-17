---
title: Integração com os serviços de gerenciamento do servidor do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Integração com os serviços de gerenciamento do servidor do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 330e297b4fb63eaa376e8b6dac0ccf77c2a16ef4
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026855"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Fase 2: Integração dos serviços de gerenciamento do servidor do Azure

Quando estiver familiarizado com as [ferramentas](./tools-services.md) e o [planejamento](./prerequisites.md) envolvidos nos serviços de gerenciamento do Azure, você estará pronto para a segunda fase, que fornece orientações passo a passo para a integração desses serviços para uso com os recursos do Azure. Comece avaliando esse processo de integração antes de adotá-lo em larga escala no seu ambiente.

> [!NOTE]
> As abordagens de automação discutidas nas seções posteriores desta orientação são destinadas a implantações que ainda não têm servidores implantados na nuvem. Eles exigem que você tenha a função de proprietário em uma assinatura para criar todos os recursos e políticas necessários. Se você já tiver recursos de conta de automação e espaço de trabalho do Log Analytics criados, recomendamos que você passe esses recursos nos parâmetros apropriados ao iniciar os scripts de automação de exemplo.

## <a name="onboarding-processes"></a>Processos de integração

Esta seção da orientação aborda os seguintes processos de integração para máquinas virtuais do Azure e servidores locais:

- **Habilite os serviços de gerenciamento em uma única VM para avaliação usando o portal**. Use esse processo para se familiarizar com os serviços de gerenciamento do servidor do Azure.
- **Configure serviços de gerenciamento para uma assinatura usando o portal**. Esse processo ajuda a configurar o ambiente do Azure para que todas as novas VMs provisionadas usem automaticamente os serviços de gerenciamento. Use essa abordagem se você preferir a experiência de portal do Azure para scripts e linhas de comando.
- **Configurar serviços de gerenciamento para uma assinatura usando a automação do Azure**. Esse processo é totalmente automatizado. Você só precisa criar uma assinatura e os scripts configurarão o ambiente para usar os serviços de gerenciamento para qualquer VM provisionada recentemente. Use essa abordagem se você estiver familiarizado com os scripts do PowerShell e os modelos de Azure Resource Manager, ou se quiser aprender a usá-los.

Os procedimentos para cada uma dessas abordagens são diferentes.

> [!NOTE]
> A sequência de etapas de integração ao usar o portal do Azure difere das etapas de integração automatizada, pois o portal oferece uma experiência de integração mais simples.

O diagrama a seguir mostra o modelo de implantação recomendado para serviços de gerenciamento. 

![Diagrama do modelo de implantação recomendado](./media/recommended-deployment.png)

> [!NOTE]
> Conforme mostrado no diagrama anterior, o agente de Log Analytics tem uma configuração de *inscrição automática* e de *aceitação* para servidores locais. O *registro automático* significa que quando o agente do log Analytics é instalado em um servidor e configurado para se conectar a um espaço de trabalho, as soluções habilitadas nesse espaço de trabalho serão aplicadas automaticamente ao servidor. A *aceitação* significa que, mesmo que o agente esteja instalado e conectado ao espaço de trabalho, a solução não será aplicada, a menos que seja adicionada à configuração de escopo do servidor no espaço de trabalho.

## <a name="next-steps"></a>Próximas etapas

Saiba como carregar uma única VM usando o portal para avaliar o processo de integração.

> [!div class="nextstepaction"]
> [Carregar uma única VM do Azure para avaliação](./onboard-single-vm.md)
