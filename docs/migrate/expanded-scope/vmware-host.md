---
title: Acelere a migração com hosts VMWare
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Acelere a migração com hosts VMWare
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: da05a1acea8029620e55ffbd11c108ab656bd491
ms.sourcegitcommit: 15898374495761bfb76cee719e0f9189856884e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888856"
---
# <a name="accelerate-migration-with-vmware-hosts"></a>Acelere a migração com hosts VMWare

A migração de hosts VMWare completos pode mover várias cargas de trabalho e vários ativos em um único esforço de migração. As diretrizes a seguir expandirão o escopo do [Guia de migração do Azure](../azure-migration-guide/index.md) por meio de uma migração de host VMware.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

A maior parte desse esforço necessário nessa expansão de escopo ocorrerá durante os pré-requisitos e os processos de migração de um esforço de migração.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Ao migrar seu primeiro host VMWare para o Azure, há vários pré-requisitos que devem ser atendidos para preparar requisitos de identidade, rede e gerenciamento. Depois que esses pré-requisitos forem atendidos, cada host adicional deverá exigir significativamente menos esforço para migrar. Esses pré-requisitos estão alinhados a alguns esforços-chave: Proteja seu ambiente do Azure, o gerenciamento de nuvem privada e a rede de nuvem privada.

### <a name="secure-your-azure-environment"></a>Proteja seu ambiente do Azure

Implemente a solução de nuvem apropriada para RBAC e conectividade de rede em seu ambiente do Azure. O [guia proteger seu ambiente](https://docs.microsoft.com/azure/vmware-cloudsimple/private-cloud-secure?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) pode ajudar com essa implementação.

### <a name="private-cloud-management"></a>Gerenciamento de nuvem privada

Há duas tarefas necessárias e uma tarefa opcional para estabelecer o gerenciamento de nuvem privada. [Escalonar privilégios de nuvem privada](https://docs.microsoft.com/azure/vmware-cloudsimple/escalate-privileges?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) e [a configuração de DNS e DHCP](https://docs.microsoft.com/azure/vmware-cloudsimple/dns-dhcp-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json) são cada uma das melhores práticas necessárias.

Se o objetivo for [migrar cargas de trabalho usando redes ampliadas de camada 2](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-layer-2-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json), essa terceira prática recomendada será necessária.

### <a name="private-cloud-networking"></a>Rede de nuvem privada

Depois que os requisitos de gerenciamento forem estabelecidos, a rede de nuvem privada poderá ser estabelecida usando as seguintes práticas recomendadas:

- [Conexão VPN para nuvem privada](https://docs.microsoft.com/azure/vmware-cloudsimple/set-up-vpn?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Conexão de rede local com o ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Conexão de rede virtual do Azure com ExpressRoute](https://docs.microsoft.com/azure/vmware-cloudsimple/azure-expressroute-connection?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a resolução de nomes DNS](https://docs.microsoft.com/azure/vmware-cloudsimple/on-premises-dns-setup?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

### <a name="integration-with-the-cloud-adoption-plan"></a>Integração com o plano de adoção de nuvem

Depois que os pré-requisitos forem atendidos, cada host VMWare será incluído no [plano de adoção da nuvem](../../plan/template.md). No plano de adoção de nuvem, adicione cada host a ser migrado, como uma [carga de trabalho distinta](../../plan/workloads.md). Em cada carga de trabalho, as VMs a serem migradas podem ser adicionadas como [ativos](../../plan/workloads.md). Para adicionar cargas de trabalho e ativos em massa ao plano de adoção, confira [adição/edição de itens com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Durante cada iteração, a equipe de adoção trabalha por meio da pendência para migrar as cargas de trabalho de prioridade mais alta. O processo não é realmente alterado para hosts VMWare. Quando a próxima carga de trabalho na pendência for um host VMWare, a única alteração será a ferramenta usada.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

Veja a seguir alguns exemplos das ferramentas que podem ser usadas no esforço de migração:

- [Ferramentas nativas do VMWare](https://docs.microsoft.com/azure/vmware-cloudsimple/migrate-workloads?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Azure Data Box](https://docs.microsoft.com/azure/vmware-cloudsimple/migration-using-azure-data-box?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

Como alternativa, as cargas de trabalho podem ser migradas por meio de um failover de recuperação de desastre usando as seguintes ferramentas:

- [Fazer backup de máquinas virtuais de carga de trabalho](https://docs.microsoft.com/azure/vmware-cloudsimple/backup-workloads-veeam?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a nuvem privada como um site de recuperação de desastre usando o zerto](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-zerto?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)
- [Configurar a nuvem privada como um site de recuperação de desastre usando o VMware SRM](https://docs.microsoft.com/azure/vmware-cloudsimple/disaster-recovery-site-recovery-manager?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json)

## <a name="next-steps"></a>Próximos passos

Retorne à [Lista de verificação de escopo expandido](./index.md) para garantir que o método de migração esteja totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
