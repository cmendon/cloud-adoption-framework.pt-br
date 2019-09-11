---
title: Proteger e gerenciar
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Proteger e gerenciar
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 7d742242f2639708914927aedbf45d1c59020c7d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818720"
---
# <a name="secure-and-manage"></a>Proteger e gerenciar

Depois de migrar seu ambiente para o Azure, é importante considerar a segurança e os métodos usados para gerenciar o ambiente. O Azure fornece muitos recursos e funcionalidades para atender a essas necessidades em sua solução.

# <a name="azure-monitortabmonitor"></a>[Azure Monitor](#tab/monitor)

O Azure Monitor maximiza a disponibilidade e o desempenho de seus aplicativos fornecendo uma solução abrangente para coletar, analisar e agir em relação a dados telemétricos de seus ambientes locais e de nuvem. Ele ajuda a entender o desempenho de seus aplicativos, além de identificar de maneira proativa os problemas que os estão afetando e os recursos dos quais eles dependem.

## <a name="use-and-configure-azure-monitor"></a>Usar e configurar o Azure Monitor

1. Vá para **Monitor** no portal do Azure.
2. Selecione **Métricas**, **Logs** ou **Integridade do Serviço** para ter visões gerais.
3. Selecione qualquer uma das informações relevantes.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Go to Azure Monitor" :::

::: zone-end

::: zone target="docs"

## <a name="read-more"></a>Leia mais

- [Visão geral do Azure Monitor](/azure/azure-monitor/overview).

::: zone-end

# <a name="azure-service-healthtabservicehealth"></a>[Integridade do Serviço do Azure](#tab/servicehealth)

A Integridade do Serviço do Azure fornece diretrizes personalizadas e suporte quando problemas nos serviços do Azure afetam você. Ela pode notificar e ajudar a entender o impacto dos problemas, mantendo você atualizado sobre a resolução do problema. Ela também ajuda você a preparar manutenções planejadas e alterações que poderão afetar a disponibilidade de seus recursos.

A Integridade do Serviço do Azure inclui:

- **Status do Azure:** uma exibição global da integridade dos serviços do Azure.
- **Integridade do Serviço:** uma visão personalizada da integridade de seus Serviços do Azure.
- **Resource Health:** uma visão mais profunda da integridade dos recursos individuais fornecidos a você pelos serviços do Azure.

Combinadas, essas experiências oferecem uma visão abrangente da integridade do Azure, em um nível de detalhe relevante para você.

## <a name="access-service-health"></a>Acessar a Integridade do Serviço

1. Vá para **Monitor** no portal do Azure.
2. Selecione **Integridade do Serviço**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/serviceIssues]" submitText="Go to Service Health" :::

::: zone-end

::: zone target="docs"

## <a name="read-more"></a>Leia mais

Para obter mais informações, confira a [documentação de Integridade do Serviço do Azure](/azure/service-health).

::: zone-end

# <a name="azure-advisortabadvisor"></a>[Assistente do Azure](#tab/advisor)

O Azure Advisor é um consultor de nuvem personalizado que ajuda a seguir as práticas recomendadas para otimizar as implantações do Azure. Ele analisa a configuração dos recursos e a telemetria do uso. Então, recomenda soluções para ajudar a melhorar o desempenho, segurança e alta disponibilidade de seus recursos enquanto procura oportunidades para reduzir a despesa geral do Azure.

## <a name="access-azure-advisor"></a>Acessar o Assistente do Azure

1. Vá para o **Assistente** no portal do Azure ou pesquise o recurso.
2. Selecione **Alta Disponibilidade**, **Segurança**, **Desempenho**, **Custo**

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorMenuBlade/overview]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

## <a name="read-more"></a>Leia mais

[Visão geral](/azure/advisor/advisor-overview).

::: zone-end

# <a name="azure-security-centertabsecurity"></a>[Central de Segurança do Azure](#tab/security)

A Central de Segurança do Azure é um sistema de gerenciamento de segurança de infraestrutura unificado que fortalece a postura de segurança de seus data centers e fornece proteção avançada contra ameaças em suas cargas de trabalho híbridas locais e na nuvem, estejam elas no Azure ou não.

## <a name="access-azure-security-center"></a>Acessar a Central de Segurança do Azure

1. Vá para a **Central de Segurança** no portal do Azure ou pesquise o recurso.
2. Selecione **Recomendações**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/0]" submitText="Go to Security Center" :::

::: zone-end

::: zone target="docs"

## <a name="read-more"></a>Leia mais

[Visão geral](/azure/security-center/security-center-intro)

::: zone-end

# <a name="azure-backuptabbackup"></a>[Serviço de Backup do Azure](#tab/backup)

O Backup do Azure é o serviço baseado no Azure que você pode usar para fazer backup (ou proteger) e restaurar os dados na nuvem da Microsoft. Ele substitui a solução de backup local ou externa existente por uma solução confiável, segura e econômica baseada em nuvem.

## <a name="enable-backup-for-an-azure-vm"></a>Habilitar o backup para uma VM do Azure

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

[Visão geral](/azure/backup/backup-introduction-to-azure-backup)

::: zone-end

# <a name="azure-site-recoverytabsiterecovery"></a>[Azure Site Recovery](#tab/siterecovery)

Anteriormente neste guia, discutimos como o Azure Site Recovery pode ser usado como parte da execução da migração. Mas ele também é um componente crítico para sua estratégia de recuperação de desastre após a conclusão da migração.

O serviço Azure Site Recovery permite replicar máquinas virtuais e cargas de trabalho hospedadas em uma região primária do Azure para uma cópia hospedada em uma região secundária. Quando ocorre uma interrupção em sua região primária, você pode fazer failover para a cópia em execução na região secundária e continuar a acessar seus aplicativos e serviços a partir dela. Quando a cópia primária da sua máquina virtual estiver em execução novamente, você poderá fazer failback para ela.

## <a name="replicate-an-azure-vm-to-another-region-with-site-recovery-service"></a>Replicar uma VM do Azure para outra região com o serviço Site Recovery

As etapas a seguir descrevem o processo para usar o serviço Site Recovery para replicar uma VM do Azure para outra região (Azure para Azure):

>
> [!TIP]
> Dependendo da sua situação, as etapas exatas podem variar um pouco.
>

## <a name="enable-replication-for-the-azure-vm"></a>Habilitar a replicação para a VM do Azure

1. No Portal do Azure, selecione **Máquinas virtuais** e selecione a VM que você deseja replicar.
1. Em **Operações**, clique em **Recuperação de desastre**.
1. Em **Configurar a recuperação de desastre** > **Região de destino**, selecione a região de destino para a qual você replicará.
1. Para este guia de início rápido, aceite as outras configurações padrão.
1. Selecione **Habilitar replicação**. Isso inicia um trabalho para habilitar a replicação para a VM.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

## <a name="verify-settings"></a>Verificar as configurações

Após o trabalho de replicação, você poderá verificar o status de replicação, a integridade da replicação e testar a implantação.

1. No menu da VM, selecione **Recuperação de desastre**.
2. Verifique a integridade da replicação, os pontos de recuperação que foram criados e as regiões de origem e destino no mapa.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/Resources/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="learn-more"></a>Saiba mais

- [Visão geral sobre o Azure Site Recovery](/azure/site-recovery/site-recovery-overview)
- [Replicar uma VM do Azure para outra região](/azure/site-recovery/azure-to-azure-quickstart)

::: zone-end
