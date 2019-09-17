---
title: Capacidade de rede excedida
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Os requisitos de armazenamento excedem a capacidade de rede durante um esforço de migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 9b1078cbb6b7ca40b7a38ea56ae803fd61e67449
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024758"
---
# <a name="storage-requirements-exceed-network-capacity-during-a-migration-effort"></a>Os requisitos de armazenamento excedem a capacidade de rede durante um esforço de migração

Em uma migração na nuvem, os ativos são replicados e sincronizados pela rede entre o datacenter existente e a nuvem. Não é incomum para os requisitos de tamanho de dados existentes de várias cargas de trabalho excedam a capacidade da rede. Nesse cenário, o processo de migração pode ser radicalmente desacelerado ou, em alguns casos, totalmente interrompido. As diretrizes a seguir expandirão o escopo do [guia de migração do Azure](../azure-migration-guide/index.md) para oferecer uma solução que contorne as limitações de rede.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

A maior parte do esforço necessário na expansão do escopo ocorrerá durante os processos de pré-requisitos, avaliação e migração da migração.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

**Validar riscos da capacidade de rede:** A [racionalização do acervo digital](../../digital-estate/rationalize.md) é um pré-requisito altamente recomendado, especialmente se houver preocupações em sobrecarregar a capacidade de rede disponível. Durante a racionalização do acervo digital, um [inventário de ativos digitais](../../digital-estate/inventory.md) é coletado. Esse inventário deve incluir os requisitos de armazenamento existentes no acervo digital. Conforme descrito em [riscos de replicação: Física da replicação](../migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication), esse inventário pode ser usado para estimar o **tamanho total dos dados de migração**, que pode ser comparado à **largura de banda total de migração disponível**. Se essa comparação não se alinhar com o **tempo necessário para a mudança de negócios**, este artigo pode ajudar a acelerar a velocidade de migração, reduzindo o tempo necessário para migrar o datacenter.

**Transferência offline de armazenamentos de dados independentes:** A figura no diagrama a seguir oferece exemplos de transferências de dados online e offline com o Azure Data Box. Essas abordagens podem ser usadas no envio de grandes volumes de dados para a nuvem antes da migração da carga de trabalho. Em uma transferência de dados offline, os dados de origem são copiados para o Azure Data Box e são enviados fisicamente à Microsoft para serem transferidos para uma conta de armazenamento do Azure como um arquivo ou um blob. Antes de outros esforços de migração, esse processo pode ser usado para enviar dados que não estão diretamente vinculados a uma carga de trabalho específica. Isso reduz a quantidade de dados que precisam ser enviados pela rede em uma tentativa para concluir uma migração dentro das restrições da rede.

Essa abordagem pode ser usada para transferir HDFS de dados, backups, arquivos mortos, servidores de arquivos, aplicativos, etc... As diretrizes técnicas existentes explicam como usar essa abordagem para transferir dados de [um repositório HDFS](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster) ou de discos usando [SMB](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data), [NFS](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-rest) ou o [serviço de cópia de dados](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-copy-service) para o Data Box.

Também há [soluções de parceiros terceiros](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) que usam o Azure Data Box em uma migração do tipo "Propagação e feed" em que um grande volume de dados é movido por meio de uma transferência offline, mas, em seguida, é sincronizado em menor escala na rede.

![Transferência de dados online e offline com o Azure Data Box](../../_images/migrate/databox.png)

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Se os requisitos de armazenamento de uma carga de trabalho (ou cargas de trabalho) exceder a capacidade da rede, o Azure Data Box ainda poderá ser usado em uma transferência de dados offline.

A opinião geral da Microsoft é que a transmissão da rede seja a abordagem recomendada, a menos que a rede não esteja disponível. Essa sugestão é resultado de velocidades de transferência. A transferência de dados pela rede (mesmo quando a largura de banda é restrita) é normalmente mais rápida do que o envio físico da mesma quantidade de dados usando um mecanismo de transferência offline, como o Data Box.

Se a conectividade com o Azure estiver disponível, realize uma análise antes de usar o Data Box, especialmente se a migração da carga de trabalho for sensível ao fator tempo. O Data Box só é aconselhável quando o tempo para transferir os dados necessários excede o tempo para preencher, enviar e restaurar dados usando o Data Box.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

**Análise da capacidade de rede:** Quando os requisitos de transferência de dados relacionados à carga de trabalho correm o risco de exceder a capacidade da rede, a equipe de adoção da nuvem adicionaria outra tarefa de análise ao processo de avaliação, chamado análise de capacidade de rede. Durante essa análise, um membro da equipe com conhecimento específico sobre a rede local e a conectividade de rede estimaria o total da capacidade de rede disponível e o tempo necessário da transferência de dados. Essa capacidade disponível seria comparada aos requisitos de armazenamento de todos os ativos que serão migrados durante a versão atual. Se os requisitos de armazenamento excederem a largura de banda disponível, os ativos dão suporte à carga de trabalho serão selecionados para transferência offline.

> [!IMPORTANT]
> Na conclusão da análise, o plano de lançamento pode precisar ser atualizado para refletir o tempo necessário para enviar, restaurar e sincronizar os ativos a serem transferidos offline.

**Análise do desvio:** Os ativos que serão transferidos offline deverão passar pela análise do desvio de configuração e armazenamento. O desvio de armazenamento é o número de alterações no armazenamento subjacente ao longo do tempo. A desvio de configuração é alterado na configuração do ativo ao longo do tempo. A partir do momento que o armazenamento é copiado até o momento que o ativo é promovido para produção, qualquer desvio pode ser perdido. Se esse desvio precisar ser refletido no ativo migrado, seria necessária alguma forma de sincronização entre o ativo local e o ativo migrado. Isso deve ser sinalizado para consideração durante a execução da migração.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Se usar mecanismos de transferência offline, os [processos de replicação](../migration-considerations/migrate/replicate.md) provavelmente não serão necessários. No entanto, os [processos de sincronização](../migration-considerations/migrate/replicate.md) ainda podem ser um requisito. A compreensão dos resultados da análise de desvio concluída durante o processo de avaliação indicará as tarefas necessárias durante a migração se um ativo estiver sendo transferido offline.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

**Armazenamento de cópia:** Essa abordagem pode ser usada para transferir HDFS de dados, backups, arquivos mortos, servidores de arquivos, aplicativos, etc... As diretrizes técnicas existentes explicam como usar essa abordagem para transferir dados de [um repositório HDFS](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster) ou de discos usando [SMB](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data), [NFS](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-rest) ou o [serviço de cópia de dados](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-copy-service) para o Data Box.

Há também [soluções de parceiros terceiros](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) que usam o Azure Data Box em uma migração do tipo "propagação e sincronização" em que um grande volume de dados é movido por meio de uma transferência offline, mas, em seguida, é sincronizado em menor escala na rede.

**Envie o dispositivo:** Após os dados serem copiados, o dispositivo poderá ser [enviado à Microsoft](https://docs.microsoft.com/azure/databox/data-box-deploy-picked-up). Depois de recebidos e importados, os dados ficam disponíveis em uma conta de armazenamento do Azure.

**Restaure o ativo:** [Verifique se os dados](https://docs.microsoft.com/azure/databox/data-box-deploy-picked-up#verify-data-upload-to-azure) estão disponíveis na conta de armazenamento. Após a verificação, os dados podem ser usados como um blob ou nos Arquivos do Azure. Se os dados forem um arquivo VHD/VHDX, o arquivo poderá ser convertido em discos gerenciados. Esses discos gerenciados podem ser usados para instanciar uma máquina virtual que criará uma réplica do ativo local original.

**Sincronização:** Se a sincronização de desvio for um requisito para um ativo migrado, uma das [soluções de parceiros terceiros](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) poderá ser usada para sincronizar os arquivos até que o ativo seja restaurado.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

As atividades de otimização provavelmente não serão afetadas por essa alteração no escopo.

## <a name="secure-and-manage-process-changes"></a>Alterações na proteção e no gerenciamento de processos

As atividades de segurança e gerenciamento provavelmente não serão afetadas por essa alteração no escopo.

## <a name="next-steps"></a>Próximas etapas

Retorne à [lista de verificação de escopo expandido](./index.md) para verificar se o método de migração está totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
