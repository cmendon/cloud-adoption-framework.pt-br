---
title: Implantar uma carga de trabalho básica
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve como implantar uma carga de trabalho básica para o Azure
author: alexbuckgit
ms.author: abuck
ms.date: 12/31/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4f00fbb1c494d3eecd32597cf94fe17192ad66ed
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160444"
---
# <a name="deploy-a-basic-workload-in-azure"></a>Implantar uma carga de trabalho básica no Azure

O termo *carga de trabalho* normalmente é definido como uma unidade arbitrária de funcionalidade como um aplicativo ou serviço. Isso nos ajuda a pensar em uma carga de trabalho em termos dos artefatos de código que são implantados em um servidor e também outros serviços específicos de um aplicativo. Essa pode ser uma definição útil para um aplicativo ou serviço local mas, para aplicativos de nuvem, ela precisa ser ampliada.

Na nuvem, uma carga de trabalho não abrange apenas todos os artefatos, mas também inclui os recursos da nuvem. Incluem-se recursos da nuvem como parte da definição devido ao conceito conhecido como "infraestrutura como código". Como você aprendeu em [como o Azure funciona?](../../getting-started/what-is-azure.md), os recursos no Azure são implantados por um serviço orquestrador. Esse serviço Orchestrator expõe a funcionalidade por meio de uma API da Web e você pode chamar a API Web usando várias ferramentas, como o PowerShell, o CLI do Azure e o portal do Azure. Isso significa que é possível especificar recursos do Azure em um arquivo legível por máquina que pode ser armazenado em conjunto com os artefatos de código associados ao aplicativo.

Isso permite definir uma carga de trabalho em termos de artefatos de código e recursos de nuvem necessários, permitindo ainda isolar cargas de trabalho. É possível isolar cargas de trabalho pela maneira como os recursos são organizados, por topologia de rede ou por outros atributos. A meta do isolamento de carga de trabalho é associar os recursos específicos de uma carga de trabalho a uma equipe, para que a equipe possa gerenciar de forma independente todos os aspectos desses recursos. Isso permite que várias equipes compartilharem serviços de gerenciamento de recursos no Azure, evitando a exclusão não intencional ou modificação de uns dos outros recursos.

Esse isolamento também permite outro conceito conhecido como DevOps. O DevOps inclui as práticas de desenvolvimento de software que abrange o desenvolvimento de software e as operações de TI acima e adiciona o uso de automação o máximo possível. Um dos princípios de DevOps é conhecido como integração contínua e entrega contínua (CI/CD). Integração contínua refere-se aos processos de build automatizados que são executados sempre que um desenvolvedor confirma uma alteração de código. A entrega contínua refere-se aos processos automatizados que implantam esse código em vários ambientes, como um ambiente de desenvolvimento para teste ou um ambiente de produção para a implantação final.

## <a name="basic-workload"></a>Carga de trabalho básica

Uma *carga de trabalho básica* normalmente é definida como um aplicativo Web único ou uma VNet (rede virtual) com VM (máquina virtual).

> [!NOTE]
> Este guia não abrange o desenvolvimento de aplicativos. Para obter mais informações sobre como desenvolver aplicativos no Azure, consulte o [Guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide).

Independentemente se a carga de trabalho é um aplicativo Web ou uma VM, cada uma dessas implantações requer um *grupo de recursos*. Um usuário com permissão para criar um grupo de recursos deverá fazer isso antes de seguir as etapas abaixo.

## <a name="basic-web-application-paas"></a>Aplicativo Web básico (PaaS)

Para um aplicativo Web básico, selecione um dos guias de início rápido de 5 minutos da [documentação de aplicativos Web](https://docs.microsoft.com/azure/app-service) e siga as etapas.

> [!NOTE]
> Alguns dos guias de início rápido implantarão um grupo de recursos por padrão. Nesse caso, não é necessário criar um grupo de recursos explicitamente. Caso contrário, implante o aplicativo Web para o grupo de recursos criado acima.

Depois de implantar uma carga de trabalho simples, você pode aprender mais sobre as práticas recomendadas para implantar um [aplicativo Web básico](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app) no Azure.

## <a name="single-windows-or-linux-vm-iaas"></a>VM única Windows ou Linux (IaaS)

Para uma carga de trabalho simples executada em uma VM, a primeira etapa é implantar uma rede virtual. Todos os recursos de IaaS (infraestrutura como serviço) no Azure, como máquinas virtuais, balanceadores de carga e gateways, exigem uma rede virtual. Saiba mais sobre [redes virtuais do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) e, em seguida, siga as etapas para [implantar uma rede virtual no Azure usando o portal](https://docs.microsoft.com/azure/virtual-network/quick-create-portal). Ao definir as configurações da rede virtual no portal do Azure, especifique o nome do grupo de recursos criado acima.

A próxima etapa é decidir se deseja implantar uma VM única Windows ou Linux. Para a VM do Windows, siga as etapas para [implantar uma VM do Windows no Azure com o portal](https://docs.microsoft.com/azure/virtual-machines/windows/quick-create-portal). Novamente, quando você especifica as configurações para a máquina virtual no portal do Azure, especifique o nome do grupo de recursos criado acima.

Depois de seguir as etapas e implantar a VM, você pode aprender sobre [as práticas recomendadas para executar uma VM do Windows no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/single-vm). Para uma VM Linux, siga as etapas para [implantar uma VM Linux no Azure com o portal](https://docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal). Você também pode aprender mais sobre [as práticas recomendadas para executar uma VM do Linux no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-linux/single-vm).

## <a name="next-steps"></a>Próximos passos

Consulte [Guias de decisão de arquitetura](../../decision-guides/index.md) para saber como usar os principais componentes de infraestrutura na nuvem do Azure.
