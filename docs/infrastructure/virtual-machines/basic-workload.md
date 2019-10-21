---
title: Implantar uma carga de trabalho básica
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve como implantar uma carga de trabalho básica no Azure
author: alexbuckgit
ms.author: abuck
ms.date: 12/31/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5c3fcb72fc58f4b33735a95a7fcf1623fe081795
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548096"
---
# <a name="deploy-a-basic-workload-in-azure"></a>Implantar uma carga de trabalho básica no Azure

O termo *carga de trabalho* normalmente é definido como uma unidade arbitrária de funcionalidade, como um aplicativo ou serviço. Isso ajuda a pensar em uma carga de trabalho em termos dos artefatos de código implantados em um servidor e também outros serviços específicos de um aplicativo. Isso pode ser uma definição útil para um aplicativo ou serviço local, mas para aplicativos de nuvem, ele precisa ser expandido.

Na nuvem, uma carga de trabalho não apenas abrange todos os artefatos, mas também inclui os recursos de nuvem. Os recursos de nuvem são incluídos como parte da definição devido ao conceito conhecido como "infraestrutura como código". Como você aprendeu em [como o Azure funciona?](../../getting-started/what-is-azure.md), os recursos no Azure são implantados por um serviço Orchestrator. Esse serviço Orchestrator expõe a funcionalidade por meio de uma API da Web e você pode chamar a API Web usando várias ferramentas, como o PowerShell, o CLI do Azure e o portal do Azure. Isso significa que você pode especificar recursos do Azure em um arquivo legível por máquina que pode ser armazenado junto com os artefatos de código associados ao aplicativo.

Isso permite que você defina uma carga de trabalho em termos de artefatos de código e dos recursos de nuvem necessários, permitindo, assim, que você Isole as cargas de trabalho. Você pode isolar cargas de trabalho por meio da maneira como os recursos são organizados, por topologia de rede ou por outros atributos. O objetivo do isolamento da carga de trabalho é associar os recursos específicos de uma carga de trabalho a uma equipe, para que a equipe possa gerenciar de forma independente todos os aspectos desses recursos. Isso permite que várias equipes compartilhem serviços de gerenciamento de recursos no Azure, impedindo a exclusão ou modificação acidental dos recursos uns dos outros.

Esse isolamento também habilita outro conceito, conhecido como DevOps. O DevOps inclui as práticas de desenvolvimento de software que incluem o desenvolvimento de software e as operações de ti acima, além de adicionar o uso da automação o máximo possível. Um dos princípios do DevOps é conhecido como integração contínua e entrega contínua (CI/CD). A integração contínua refere-se aos processos de compilação automatizados que são executados toda vez que um desenvolvedor confirma uma alteração de código. Entrega contínua refere-se aos processos automatizados que implantam esse código em vários ambientes, como um ambiente de desenvolvimento para teste ou um ambiente de produção para implantação final.

## <a name="basic-workload"></a>Carga de trabalho básica

Uma *carga de trabalho básica* normalmente é definida como um único aplicativo Web ou uma VNet (rede virtual) com VM (máquina virtual).

> [!NOTE]
> Este guia não abrange o desenvolvimento de aplicativos. Para obter mais informações sobre como desenvolver aplicativos no Azure, consulte o [Guia de arquitetura do aplicativo Azure](https://docs.microsoft.com/azure/architecture/guide).

Independentemente de a carga de trabalho ser um aplicativo Web ou uma VM, cada uma dessas implantações requer um *grupo de recursos*. Um usuário com permissão para criar um grupo de recursos deve fazer isso antes de seguir as etapas abaixo.

## <a name="basic-web-application-paas"></a>Aplicativo Web básico (PaaS)

Para um aplicativo Web básico, selecione um dos guias de início rápido de 5 minutos na [documentação dos aplicativos Web](https://docs.microsoft.com/azure/app-service?toc=/azure/architecture/cloud-adoption-guide/toc.json) e siga as etapas.

> [!NOTE]
> Alguns dos guias de início rápido implantarão um grupo de recursos por padrão. Nesse caso, não é necessário criar um grupo de recursos explicitamente. Caso contrário, implante o aplicativo Web no grupo de recursos criado acima.

Depois de implantar uma carga de trabalho simples, você pode aprender mais sobre as práticas recomendadas para implantar um [aplicativo Web básico](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app?toc=/azure/architecture/cloud-adoption-guide/toc.json) no Azure.

## <a name="single-windows-or-linux-vm-iaas"></a>Uma única VM Windows ou Linux (IaaS)

Para uma carga de trabalho simples que é executada em uma VM, a primeira etapa é implantar uma rede virtual. Todos os recursos de IaaS (infraestrutura como serviço) no Azure, como máquinas virtuais, balanceadores de carga e gateways, exigem uma rede virtual. Saiba mais sobre as [redes virtuais do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview?toc=/azure/architecture/cloud-adoption-guide/toc.json)e siga as etapas para [implantar uma rede virtual no Azure usando o portal](https://docs.microsoft.com/azure/virtual-network/quick-create-portal?toc=/azure/architecture/cloud-adoption-guide/toc.json). Ao especificar as configurações para a rede virtual no portal do Azure, certifique-se de especificar o nome do grupo de recursos criado acima.

A próxima etapa é decidir se uma única VM Windows ou Linux deve ser implantada. Para a VM do Windows, siga as etapas para [implantar uma VM do Windows no Azure com o portal](https://docs.microsoft.com/azure/virtual-machines/windows/quick-create-portal?toc=/azure/architecture/cloud-adoption-guide/toc.json). Novamente, quando você especificar as configurações para a máquina virtual na portal do Azure, especifique o nome do grupo de recursos criado acima.

Depois de seguir as etapas e implantar a VM, você pode aprender sobre [as práticas recomendadas para executar uma VM do Windows no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/single-vm?toc=/azure/architecture/cloud-adoption-guide/toc.json). Para uma VM do Linux, siga as etapas para [implantar uma VM do Linux no Azure com o portal](https://docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal?toc=/azure/architecture/cloud-adoption-guide/toc.json). Você também pode aprender mais sobre [as práticas recomendadas para executar uma VM do Linux no Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-linux/single-vm?toc=/azure/architecture/cloud-adoption-guide/toc.json).

## <a name="next-steps"></a>Próximos passos

Consulte os [guias de decisão de arquitetura](../../decision-guides/index.md) para saber como usar os componentes principais da infraestrutura na nuvem do Azure.
