---
title: Proteger e recuperar no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Garantir a estabilidade dos negócios diminuindo o tempo de recuperação
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: a79164435772f571849d0a836f43b53ce3bca087
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556999"
---
# <a name="protect-and-recover-in-azure"></a>Proteger e recuperar no Azure

Proteger e recuperar é a terceira e última disciplina em qualquer linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

No último artigo “Conformidade operacional”, o objetivo é reduzir a probabilidade de uma interrupção dos negócios. Este artigo “Proteger e recuperar” visa reduzir a duração e o impacto das interrupções que não podem ser evitadas.

Para qualquer ambiente de nível corporativo, a tabela a seguir descreve o mínimo sugerido para qualquer linha de base de gerenciamento.

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Proteger dados|Serviço de Backup do Azure|Fazer backup de dados e VMs na nuvem|
|Proteger o ambiente|Central de Segurança do Azure|

::: zone target="docs"

## <a name="azure-backup"></a>Serviço de Backup do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-backuptabupdbackupatemanagement"></a>[Serviço de Backup do Azure](#tab/UpdbackupateManagement)

::: zone-end

O Backup do Azure é o serviço baseado no Azure que você pode usar para fazer backup (ou proteger) e recuperar os dados na nuvem da Microsoft. Ele substitui a solução de backup local ou externa existente por uma solução confiável, segura e econômica baseada em nuvem. Ele também pode ser usado para proteger e recuperar ativos locais por meio de uma solução consistente.

### <a name="enable-backup-for-an-azure-vm"></a>Habilitar o backup para uma VM do Azure

1. No Portal do Azure, selecione **Máquinas virtuais** e selecione a VM que você deseja replicar.
1. Em **Operações**, selecione **Backup**.
1. Crie ou selecione um cofre dos Serviços de Recuperação.
1. Selecione **Criar (ou editar) uma nova política**.
1. Configure a agenda e o período de retenção.
1. Selecione **OK**.
1. Selecione **Habilitar Backup**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

[Visão geral](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup)

## <a name="azure-site-recovery"></a>Azure Site Recovery

::: zone-end
::: zone target="chromeless"

## <a name="azure-site-recoverytabsiterecovery"></a>[Azure Site Recovery](#tab/siterecovery)

::: zone-end

O Azure Site Recovery é um componente crítico em sua estratégia de recuperação de desastre.

O serviço Azure Site Recovery permite replicar máquinas virtuais e cargas de trabalho hospedadas em uma região primária do Azure para uma cópia hospedada em uma região secundária. Quando ocorre uma interrupção em sua região primária, você pode fazer failover para a cópia em execução na região secundária e continuar a acessar seus aplicativos e serviços a partir dela. Essa abordagem proativa de recuperação pode reduzir significativamente os tempos de recuperação. Quando o ambiente de recuperação não for mais necessário, o tráfego de produção poderá fazer fallback para o ambiente original.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Replicar uma VM do Azure para outra região com o serviço Site Recovery

As etapas a seguir descrevem o processo para usar o serviço Site Recovery para replicar uma VM do Azure para outra região (Azure para Azure):

>
> [!TIP]
> Dependendo da sua situação, as etapas exatas podem variar um pouco.
>

### <a name="enable-replication-for-the-azure-vm"></a>Habilitar a replicação para a VM do Azure

1. No Portal do Azure, selecione **Máquinas virtuais** e selecione a VM que você deseja replicar.
1. Em **Operações**, clique em **Recuperação de desastre**.
1. Em **Configurar recuperação de desastre** > **Região de destino**, selecione a região de destino para a qual será replicada.
1. Para este guia de início rápido, aceite as outras configurações padrão.
1. Selecione **Habilitar replicação**, que inicia um trabalho para habilitar a replicação da VM.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Verificar as configurações

Após o trabalho de replicação, você poderá verificar o status de replicação, a integridade da replicação e testar a implantação.

1. No menu da VM, selecione **Recuperação de desastre**.
2. Verifique a integridade da replicação, os pontos de recuperação que foram criados e as regiões de origem e destino no mapa.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="learn-more"></a>Saiba mais

- [Visão geral sobre o Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Replicar uma VM do Azure para outra região](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
