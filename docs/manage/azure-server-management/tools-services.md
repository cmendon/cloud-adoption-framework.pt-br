---
title: Ferramentas e serviços de gerenciamento do servidor do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas e serviços de gerenciamento do servidor do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 51564add9bfe50ab494b39344eb24d3079fce000
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565275"
---
# <a name="azure-server-management-tools-and-services"></a>Ferramentas e serviços de gerenciamento do servidor do Azure

Como é discutido na [visão geral](./index.md) dessas diretrizes, o pacote de serviços de gerenciamento de servidor do Azure abrange essas áreas:

- Migrar
- Segurança
- Proteger
- Monitoramento
- Configurar
- Administrar

As seções a seguir descrevem brevemente essas áreas de gerenciamento e fornecem links para conteúdo detalhado sobre os principais serviços do Azure que dão suporte a eles.

## <a name="migrate"></a>Migrar

Os serviços de migração podem ajudá-lo a migrar suas cargas de trabalho para o Azure. Para fornecer as melhores diretrizes, o serviço migrações para Azure começa medindo o desempenho do servidor local e avaliando a adequação para a migração. Após a migração do Azure concluir a avaliação, você poderá usar [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) e o [serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/dms-overview) para migrar seus computadores locais para o Azure.

## <a name="secure"></a>Segurança

A [central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) é um aplicativo abrangente de gerenciamento de segurança. Ao integrar à central de segurança, você pode obter rapidamente uma avaliação do status de conformidade normativa e de segurança do seu ambiente. Para obter instruções sobre a integração dos servidores à central de segurança do Azure, consulte [configurar os serviços de gerenciamento do Azure para uma assinatura](./onboard-at-scale.md#azure-security-center).

## <a name="protect"></a>Proteger

Para proteger seus dados, você precisa planejar o backup, a alta disponibilidade, a criptografia, a autorização e os problemas operacionais relacionados. Esses tópicos são amplamente abordados online, portanto, vamos nos concentrar em criar um plano de recuperação de desastres de continuidade de negócios (BCDR). Incluiremos referências à documentação que descreve em detalhes como implementar e implantar esse tipo de plano.

Ao criar estratégias de proteção de dados, primeiro considere dividir seus aplicativos de carga de trabalho em suas diferentes camadas. Essa abordagem ajuda porque cada camada normalmente requer seu próprio plano de proteção exclusivo. Para saber mais sobre como criar aplicativos para serem resilientes, consulte [criando aplicativos resilientes para o Azure](https://docs.microsoft.com/azure/architecture/resiliency).

A proteção de dados mais básica é o backup. Para acelerar o processo de recuperação se os servidores forem perdidos, faça backup não apenas dados, mas também configurações de servidor. O backup é um mecanismo eficaz para lidar com a exclusão acidental de dados e ataques de ransomware. O [backup do Azure](https://docs.microsoft.com/azure/backup) pode ajudá-lo a proteger seus dados no Azure e em servidores locais que executam Windows ou Linux. Para obter detalhes sobre o que o backup pode fazer e para os guias de instruções, consulte a [documentação do backup do Azure](https://docs.microsoft.com/azure/backup/backup-overview).

A recuperação por meio do backup pode levar muito tempo. O padrão do setor é geralmente um dia. Se uma carga de trabalho exigir continuidade de negócios para falhas de hardware ou interrupção do datacenter, considere o uso da replicação de dados. [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) fornece replicação contínua de suas VMs, uma solução que fornece perda de dados mínima. O Site Recovery também dá suporte a vários cenários de replicação, como replicação:

- De VMs do Azure entre duas regiões do Azure.
- Entre servidores locais.
- Entre servidores locais e o Azure.

Para obter mais informações, consulte a [matriz de replicação completa do Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview#what-can-i-replicate).

Para os dados do servidor de arquivos, outro serviço a ser considerado é [sincronização de arquivos do Azure](https://docs.microsoft.com/azure/storage/files/storage-sync-files-planning). Esse serviço ajuda a centralizar os compartilhamentos de arquivos de sua organização nos arquivos do Azure, preservando a flexibilidade, o desempenho e a compatibilidade de um servidor de arquivos local. Para usar esse serviço, siga as instruções para implantar o Sincronização de Arquivos do Azure.

## <a name="monitor"></a>Monitoramento

O [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) fornece uma exibição de vários recursos, como aplicativos, contêineres e máquinas virtuais. Ele também coleta dados de várias fontes:

- O Azure Monitor para VMs ([insights](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview)) fornece uma visão detalhada da integridade da máquina virtual, tendências de desempenho e dependências. O serviço monitora a integridade dos sistemas operacionais de suas máquinas virtuais do Azure, conjuntos de dimensionamento de máquinas virtuais e computadores em seu ambiente local.
- Log Analytics ([logs](https://docs.microsoft.com/azure/azure-monitor/platform/data-collection#logs)) é um recurso do Azure monitor. Sua função é fundamental para a história geral de gerenciamento do Azure. Ele serve como o armazenamento de dados para análise de log e para muitos outros serviços do Azure. Ele oferece uma linguagem de consulta avançada e um mecanismo de análise que fornece informações sobre a operação de seus aplicativos e recursos.
- O [log de atividades do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) também é um recurso do Azure monitor. Ele fornece informações sobre eventos de nível de assinatura que ocorrem no Azure.

## <a name="configure"></a>Configurar

Vários serviços se encaixam nessa categoria. Eles podem ajudá-lo a:

- Automatizar tarefas operacionais.
- Gerenciar configurações de servidor.
- Medir a conformidade da atualização.
- Agendar atualizações.
- Detectar alterações em seus servidores.

Esses serviços são essenciais para dar suporte a operações contínuas:

- O [Gerenciamento de atualizações](https://docs.microsoft.com/azure/automation/automation-update-management#view-update-assessments) automatiza a implantação de patches em seu ambiente, incluindo a implantação em instâncias do sistema operacional em execução fora do Azure. Ele dá suporte a sistemas operacionais Windows e Linux e controla as principais vulnerabilidades do sistema operacional e a não conformidade causadas por patches ausentes.
- O [controle de alterações e o inventário](https://docs.microsoft.com/azure/automation/change-tracking) fornecem informações sobre o software que está sendo executado em seu ambiente e realça as alterações ocorridas.
- A [automação do Azure](https://docs.microsoft.com/azure/automation/automation-intro) permite executar scripts do Python e do PowerShell ou runbooks para automatizar tarefas em seu ambiente. Ao usar a automação com o [Hybrid runbook Worker](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker), você pode estender seus runbooks para seus recursos locais também.
- A [configuração de estado da automação do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) permite que você envie por push configurações de DSC (configuração de estado desejado) do PowerShell diretamente do Azure. A DSC também permite que você monitore e preserve as configurações para sistemas operacionais e cargas de trabalho convidadas.

## <a name="govern"></a>Administrar

A adoção e a mudança para a nuvem geram novos desafios de gerenciamento. Isso requer uma mentalidade diferente à medida que você passa de uma carga de gerenciamento operacional para o monitoramento e a governança. A estrutura de adoção de nuvem para o Azure começa com [governança](../../govern/index.md). A estrutura explica como migrar para a nuvem, como será a jornada e quem deve estar envolvido.

O design de governança para organizações padrão muitas vezes difere do design de governança para empresas complexas. Para saber mais sobre as práticas recomendadas de governança para uma organização padrão, consulte o [Guia de governança empresarial padrão](../../govern/guides/standard/index.md). Para saber mais sobre as práticas recomendadas de governança para uma empresa complexa, consulte o [Guia de governança para empresas complexas](../../govern/guides/complex/index.md).

## <a name="billing-information"></a>Informações de cobrança

Para saber mais sobre os preços dos serviços de gerenciamento do Azure, acesse estas páginas:

- [Azure Site Recovery](https://azure.microsoft.com/pricing/details/site-recovery)

- [Serviço de Backup do Azure](https://azure.microsoft.com/pricing/details/backup)

- [Azure Monitor](https://azure.microsoft.com/pricing/details/monitor)

- [Central de Segurança do Azure](https://azure.microsoft.com/pricing/details/security-center)

- [Automação do Azure](https://azure.microsoft.com/pricing/details/automation), incluindo:
  - Configuração de estado desejado
  - Serviço de Gerenciamento de Atualizações do Azure
  - Serviços de Controle de Alterações e inventário do Azure

- [Azure Policy](https://azure.microsoft.com/pricing/details/azure-policy)

- [Serviço de Sincronização de Arquivos do Azure](https://azure.microsoft.com/pricing/details/storage/blobs)

> [!NOTE]
> A solução de Gerenciamento de Atualizações do Azure é gratuita, mas há um pequeno custo relacionado à ingestão de dados. Como regra geral, os primeiros 5 gigabytes (GB) por mês de ingestão de dados são gratuitos. Em geral, observamos que cada computador usa cerca de 25 MB por mês. Portanto, cerca de 200 máquinas por mês são cobertas gratuitamente. Para mais servidores, multiplique o número de servidores adicionais por 25 MB por mês. Em seguida, multiplique o resultado pelo preço de armazenamento para o armazenamento adicional de que você precisa. Para obter informações sobre custos, consulte [visão geral do armazenamento do Azure preço](https://azure.microsoft.com/pricing/details/storage). Cada servidor adicional normalmente tem um impacto nominal no custo.
