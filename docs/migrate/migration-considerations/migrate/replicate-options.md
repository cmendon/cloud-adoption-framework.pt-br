---
title: Opções de replicação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Um processo na migração na nuvem que se concentra nas tarefas de migrar cargas de trabalho para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 8d3722028761adb70797fc9f654bfbdc7e697fb2
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825517"
---
# <a name="replication-options"></a>Opções de replicação

Antes de qualquer migração, você deve garantir que os principais sistemas estão seguros e continuam a ser executados sem problemas. Todo tempo de inatividade prejudica usuários ou clientes e custa tempo e dinheiro. A migração não se resume em desativar as máquinas virtuais locais e copiá-las para o Azure. As ferramentas de migração devem levar em conta a replicação assíncrona ou síncrona para garantir que os sistemas ativos possam ser copiados para o Azure sem tempo de inatividade. Acima de tudo, os sistemas devem ser mantidos em sincronia com os sistemas equivalentes locais. Convém testar os recursos migrados em partições isoladas no Azure para garantir que as cargas de trabalho funcionem conforme o esperado.

O conteúdo do Cloud Adoption Framework pressupõe que o recurso Migrações para Azure (ou Azure Site Recovery) seja a ferramenta mais apropriada para replicar ativos na nuvem. No entanto, há outras opções disponíveis. Este artigo discute essas opções para ajudar na tomada de decisões.

## <a name="azure-site-recovery-also-known-as-azure-migrate"></a>Azure Site Recovery (também conhecido como Migrações para Azure)

O [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) coordena e gerencia a recuperação de desastre para VMs do Azure, VMs locais e servidores físicos. Você também pode usar o Site Recovery para gerenciar a migração de computadores locais e outros provedores de nuvem para o Azure. Replique as máquinas locais para o Azure ou as VMs do Azure para uma região secundária. Em seguida, faça o failover da VM do site primário para o secundário e conclua o processo de migração. Com o Azure Site Recovery, você pode ter vários cenários de migração:

- **Migre do local para o Azure.** Migre VMs do VMware local, VMs do Hyper-V e servidores físicos para o Azure. Para fazer isso, conclua quase as mesmas etapas que usaria para a recuperação de desastre completo. Você simplesmente não faz failover de máquinas do Azure para o site local.
- **Migre entre regiões do Azure.** Migre VMs do Azure de uma região do Azure para outra. Após a conclusão da migração, configure a recuperação de desastre para VMs do Azure agora na região secundária para a qual migrou.
- **Migre de outra nuvem para o Azure.** Você pode migrar suas instâncias de computação provisionadas em outros provedores de nuvem para VMs do Azure. O Site Recovery trata dessas instâncias como servidores físicos para fins de migração.

![Azure Site Recovery](../../../_images/asr-replication-image.png)
*Azure Site Recovery migrando ativos para o Azure ou outras nuvens*

Depois de avaliar a infraestrutura local e na nuvem para migração, o Azure Site Recovery contribui para sua estratégia de migração através da replicação de máquinas locais. Com as simples etapas a seguir, você pode configurar a migração de VMs locais, servidores físicos e instâncias de VM na nuvem para o Azure:

- Verifique se os pré-requisitos.
- Prepare os recursos do Azure.
- Prepare instâncias locais de VM ou nuvem para migração.
- Implante um servidor de configuração.
- Habilite a replicação para VMs.
- Teste o failover para verificar se tudo está funcionando.
- Execute um failover avulso para o Azure.

## <a name="azure-database-migration-service"></a>Serviço de Migração de Banco de Dados do Azure

Esse serviço reduz a complexidade da migração na nuvem usando um único serviço abrangente em vez de uma combinação de diversas ferramentas. O [Serviço de Migração de Banco de Dados do Azure](/azure/dms/dms-overview) é projetado como uma solução perfeita de ponta a ponta para migrar bancos de dados do SQL Server local para a nuvem. O Serviço de Migração de Banco de Dados do Azure é um serviço totalmente gerenciado projetado para permitir migrações perfeitas de várias fontes de banco de dados para plataformas de dados do Azure com um tempo de inatividade mínimo. Ele integra algumas das funcionalidades de ferramentas e serviços existentes oferecendo aos clientes uma solução abrangente e altamente disponível.

O serviço usa o Assistente de Migração de Dados para gerar relatórios de avaliação que fornecem recomendações para orientar você durante as alterações necessárias antes de executar uma migração. Cabe a você executar as correções necessárias. Quando você estiver pronto para iniciar o processo de migração, o Serviço de Migração de Banco de Dados do Azure executará todas as etapas associadas. Você pode acioná-lo e ficar tranquilo quanto aos seus projetos de migração, com a certeza de que o processo aproveita as melhores práticas determinadas pela Microsoft.

## <a name="next-steps"></a>Próximas etapas

Após a conclusão da replicação, as [atividades de preparo](./stage.md) podem começar.

> [!div class="nextstepaction"]
> [Atividades de preparo durante uma migração](./stage.md)
