---
title: Integração com os serviços de gerenciamento do servidor do Azure
description: Integração com os serviços de gerenciamento do servidor do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 48c0728c39457a2fa060679460a97c0ddca49c45
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807998"
---
# <a name="phase-2-onboarding-azure-server-management-services"></a>Fase 2: integração dos serviços de gerenciamento do servidor do Azure

Depois que estiver familiarizado com as [ferramentas](./tools-services.md) e o [planejamento](./prerequisites.md) envolvidos nos serviços de gerenciamento do Azure, você estará pronto para a segunda fase. A fase 2 fornece orientações passo a passo para a integração desses serviços para uso com os recursos do Azure. Comece avaliando esse processo de integração antes de adotá-lo em larga escala no seu ambiente.

> [!NOTE]
> As abordagens de automação discutidas nas seções posteriores desta diretriz são destinadas a implantações que ainda não têm servidores implantados na nuvem. Eles exigem que você tenha a função de proprietário em uma assinatura para criar todos os recursos e políticas necessários. Se você já criou Log Analytics espaços de trabalho e contas de automação, recomendamos que você passe esses recursos nos parâmetros apropriados ao iniciar os scripts de automação de exemplo.

## <a name="onboarding-processes"></a>Processos de integração

Esta seção da orientação aborda os seguintes processos de integração para máquinas virtuais do Azure e servidores locais:

- **Habilite os serviços de gerenciamento em uma única VM para avaliação usando o portal**. Use esse processo para se familiarizar com os serviços de gerenciamento do servidor do Azure.
- **Configure serviços de gerenciamento para uma assinatura usando o portal**. Esse processo ajuda a configurar o ambiente do Azure para que todas as novas VMs provisionadas usem automaticamente os serviços de gerenciamento. Use essa abordagem se você preferir a experiência de portal do Azure para scripts e linhas de comando.
- **Configurar serviços de gerenciamento para uma assinatura usando a automação do Azure**. Esse processo é totalmente automatizado. Basta criar uma assinatura e os scripts configurarão o ambiente para usar os serviços de gerenciamento para qualquer VM provisionada recentemente. Use essa abordagem se você estiver familiarizado com os scripts do PowerShell e os modelos de Azure Resource Manager, ou se quiser aprender a usá-los.

Os procedimentos para cada uma dessas abordagens são diferentes.

> [!NOTE]
> Quando você usa o portal do Azure, a sequência de etapas de integração é diferente das etapas de integração automatizada. O portal oferece uma experiência de integração mais simples.

O diagrama a seguir mostra o modelo de implantação recomendado para serviços de gerenciamento:

![Diagrama do modelo de implantação recomendado](./media/recommended-deployment.png)

Conforme mostrado no diagrama anterior, o agente de Log Analytics tem uma configuração de *inscrição automática* e de *aceitação* para servidores locais:

- **Registro automático:** Quando o agente de Log Analytics é instalado em um servidor e configurado para se conectar a um espaço de trabalho, as soluções habilitadas nesse espaço de trabalho são aplicadas automaticamente ao servidor.
- **Aceitação:** Mesmo que o agente esteja instalado e conectado ao espaço de trabalho, a solução não será aplicada, a menos que seja adicionada à configuração de escopo do servidor no espaço de trabalho.

## <a name="next-steps"></a>Próximos passos

Saiba como carregar uma única VM usando o portal para avaliar o processo de integração.

> [!div class="nextstepaction"]
> [Carregar uma única VM do Azure para avaliação](./onboard-single-vm.md)
