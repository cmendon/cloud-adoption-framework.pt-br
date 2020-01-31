---
title: Proteger e recuperar no Azure
description: Garanta a estabilidade dos negócios reduzindo o tempo de recuperação
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 3e9eadbd246ba38f496d8c74b7bcd3e6ade03685
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808151"
---
# <a name="protect-and-recover-in-azure"></a>Proteger e recuperar no Azure

_Proteger e recuperar_ é a terceira e última disciplina em qualquer linha de base de gerenciamento de nuvem.

![Linha de base de gerenciamento de nuvem](../../_images/manage/management-baseline.png)

Na [conformidade Operacional no Azure](./operational-compliance.md) o objetivo é reduzir a probabilidade de uma interrupção dos negócios. Este artigo visa reduzir a duração e o impacto de interrupções que não podem ser evitadas.

Para qualquer ambiente de nível empresarial, esta tabela descreve o mínimo sugerido para qualquer linha de base de gerenciamento:

|Processo  |Ferramenta  |Finalidade  |
|---------|---------|---------|
|Proteger dados|Serviço de Backup do Azure|Faça o backup de dados e de máquinas virtuais na nuvem.|
|Proteger o ambiente|Central de Segurança do Azure|Fortaleça a segurança e forneça proteção avançada contra ameaças em suas cargas de trabalho híbridas.|

::: zone target="docs"

## <a name="azure-backup"></a>Serviço de Backup do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-backuptabupdbackupatemanagement"></a>[Serviço de Backup do Azure](#tab/UpdbackupateManagement)

::: zone-end

Com o Backup do Azure é possível fazer backup, proteger e recuperar seus dados no Microsoft Cloud. O Backup do Azure substitui sua solução existente de backup local ou externo por uma solução baseada em nuvem. Essa nova solução é confiável, segura e de custo competitivo. O Backup do Azure também pode ajudar a proteger e recuperar ativos locais por meio de uma solução consistente.

### <a name="enable-backup-for-an-azure-vm"></a>Habilitar o backup para uma VM do Azure

1. No Portal do Azure, selecione **Máquinas virtuais** e selecione a VM que você deseja replicar.
1. No painel **Operações**, selecione **Backup**.
1. Crie ou selecione um cofre existente dos Serviços de Recuperação do Azure.
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

O Site Recovery replica VMs e cargas de trabalho que são hospedadas em uma região primária do Azure. Ele as replica para uma cópia hospedada em uma região secundária. Quando ocorrer uma interrupção em sua região primária, faça failover para a cópia em execução na região secundária. Em seguida, continue acessando seus aplicativos e serviços a partir daí. Essa abordagem proativa de recuperação pode reduzir significativamente os tempos de recuperação. Quando o ambiente de recuperação não for mais necessário, o tráfego de produção poderá fazer fallback para o ambiente original.

### <a name="replicate-an-azure-vm-to-another-region-with-site-recovery"></a>Replicar uma VM do Azure para outra região com o Site Recovery

As etapas a seguir descrevem o processo para usar o Site Recovery para replicação do Azure para o Azure, ou seja, a replicação de uma VM do Azure para outra região.
>
> [!TIP]
> Dependendo do seu cenário, as etapas exatas podem variar um pouco.
>

### <a name="enable-replication-for-the-azure-vm"></a>Habilitar a replicação para a VM do Azure

1. No Portal do Azure, selecione **Máquinas virtuais** e selecione a VM que você deseja replicar.
1. No painel **Operações**, selecione **Recuperação de desastre**.
1. Selecione **Configurar recuperação de desastre** > **Região de destino** e escolha a região de destino para a qual você replicará.
1. Para este guia de início rápido, aceite os valores padrão para todas as outras opções.
1. Selecione **Habilitar replicação**, que inicia um trabalho para habilitar a replicação da VM.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="verify-settings"></a>Verificar as configurações

Após o trabalho de replicação, você poderá verificar o status de replicação, a integridade da replicação e testar a implantação.

1. No menu da VM, selecione **Recuperação de desastre**.
1. Verifique a integridade da replicação, os pontos de recuperação que foram criados e as regiões de origem e destino no mapa.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

### <a name="learn-more"></a>Saiba mais

- [Visão geral sobre o Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)
- [Replicar uma VM do Azure para outra região](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)
