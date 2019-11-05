---
title: Acelere a migração com hosts VMware
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Acelere a migração com hosts VMware
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 724a227407f431e08b5344dfd1280397bfca9b65
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566878"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Acelere a migração com hosts VMware

A migração de hosts VMware completos pode mover várias cargas de trabalho e vários ativos em um único esforço de migração. As diretrizes a seguir expandem o escopo do [Guia de migração do Azure](../azure-migration-guide/index.md) por meio de uma migração de host do VMware. A maior parte do esforço necessário nessa expansão de escopo ocorre durante os pré-requisitos e os processos de migração de um esforço de migração.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Ao migrar seu primeiro host VMware para o Azure, você deve atender a vários pré-requisitos para preparar requisitos de identidade, rede e gerenciamento. Depois que esses pré-requisitos forem atendidos, cada host adicional deverá exigir significativamente menos esforço para migrar. As seções a seguir fornecem mais detalhes sobre os pré-requisitos.

### <a name="secure-your-azure-environment"></a>Proteja seu ambiente do Azure

Implemente a solução de nuvem apropriada para controle de acesso baseado em função e conectividade de rede em seu ambiente do Azure. O [guia proteger seu ambiente](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) pode ajudar com essa implementação.

### <a name="private-cloud-management"></a>Gerenciamento de nuvem privada

Há duas tarefas necessárias e uma tarefa opcional para estabelecer o gerenciamento de nuvem privada. [Escalonar privilégios de nuvem privada](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) e [a configuração de DNS e DHCP](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) são cada uma das melhores práticas necessárias.

Se o objetivo é [migrar cargas de trabalho usando redes ampliadas de camada 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json), essa terceira prática recomendada também é necessária.

### <a name="private-cloud-networking"></a>Rede de nuvem privada

Depois que os requisitos de gerenciamento forem estabelecidos, você poderá estabelecer a rede de nuvem privada usando as seguintes práticas recomendadas:

- [Conexão VPN para nuvem privada](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Conexão de rede local com o ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Conexão de rede virtual do Azure com ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a resolução de nomes DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Integração com o plano de adoção de nuvem

Depois de atender aos outros pré-requisitos, você deve incluir cada host VMware no [plano de adoção de nuvem](../../plan/template.md). No plano de adoção de nuvem, adicione cada host a ser migrado, como uma [carga de trabalho distinta](../../plan/workloads.md). Em cada carga de trabalho, adicione as VMs a serem migradas como [ativos](../../plan/workloads.md). Para adicionar cargas de trabalho e ativos ao plano de adoção em massa, consulte [adicionando/editando itens de trabalhos com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Durante cada iteração, a equipe de adoção trabalha por meio da pendência para migrar as cargas de trabalho de prioridade mais alta. O processo não é realmente alterado para hosts VMware. Quando a próxima carga de trabalho na pendência for um host VMware, a única alteração será a ferramenta usada.

Você pode usar as seguintes ferramentas no esforço de migração:

- [Ferramentas nativas do VMware](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

Como alternativa, você pode migrar cargas de trabalho por meio de um failover de recuperação de desastre usando as seguintes ferramentas:

- [Fazer backup de máquinas virtuais de carga de trabalho](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a nuvem privada como um site de recuperação de desastre usando o zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a nuvem privada como um site de recuperação de desastre usando o VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Próximos passos

Retorne à lista de verificação de escopo expandido para garantir que o método de migração esteja totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
