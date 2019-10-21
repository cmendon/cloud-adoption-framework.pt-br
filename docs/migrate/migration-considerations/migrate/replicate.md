---
title: Que função a replicação e a sincronização desempenham no processo de migração?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Um processo na migração de nuvem que se concentra nas tarefas de migrar cargas de trabalho para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 62c12796abf8921c13cebe471fe555d012bab15c
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549135"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-role-does-replication-play-in-the-migration-process"></a>Que função a replicação desempenha no processo de migração?

Os data centers locais são preenchidos com ativos físicos, como servidores, dispositivos e dispositivos de rede. No entanto, cada servidor é apenas um shell físico. O valor real vem do binário em execução no servidor. Os aplicativos e os dados são a finalidade do datacenter. Esses são os binários primários a serem migrados. A capacitação desses aplicativos e armazenamentos de dados são outros ativos digitais e fontes binárias, como sistemas operacionais, rotas de rede, arquivos e protocolos de segurança.

A replicação é a força de trabalho dos esforços de migração. É o processo de copiar uma versão pontual de vários binários. Os instantâneos binários são então copiados para uma nova plataforma e implantados em um novo hardware, em um processo referido como *propagação*. Quando executado corretamente, a cópia propagada do binário deve se comportar de forma idêntica ao binário original no hardware antigo. No entanto, esse instantâneo do binário é imediatamente desatualizado e desalinhado com a origem original. Para manter o novo binário e o binário antigo alinhado, um processo referido como *sincronização* atualiza continuamente a cópia armazenada na nova plataforma. A sincronização continua até que o ativo seja promovido em alinhamento com o modelo de promoção escolhido. Nesse ponto, a sincronização é severa.

## <a name="required-prerequisites-to-replication"></a>Pré-requisitos necessários para replicação

Antes da replicação, a *nova plataforma* e o hardware devem estar preparados para receber as cópias binárias. O artigo sobre os [pré-requisitos](../prerequisites/index.md) descreve os requisitos mínimos do ambiente para ajudar a criar uma plataforma segura, robusta e de alto desempenho para receber as réplicas binárias.

Os *binários de origem* também devem estar preparados para replicação e sincronização. Os artigos sobre avaliação, arquitetura e correção de cada um resolvem as ações necessárias para garantir que o binário de origem esteja pronto para replicação e sincronização.

Um *ferramentas* que se alinha com a nova plataforma e os binários de origem devem ser implementados para executar e gerenciar os processos de replicação e sincronização. O artigo sobre [as opções de replicação](./replicate-options.md) descreve várias ferramentas que podem contribuir para uma migração para o Azure.

## <a name="replication-risks---physics-of-replication"></a>Riscos de replicação-física da replicação

Ao planejar a replicação de qualquer fonte binária para um novo destino, há algumas leis fundamentais a serem consideradas seriamente durante o planejamento e a execução.

- **Velocidade de luz.** Ao mover grandes volumes de dados, a fibra ainda é a opção mais rápida. Infelizmente, esses cabos só podem mover dados em dois terços da velocidade de luz. Isso significa que não há nenhum método para replicação instantânea ou ilimitada de dados.
- **Velocidade do pipeline de WAN.** Mais consequencial do que a velocidade de movimentação de dados é a largura de banda de uplink, que define o volume de dados por segundo que pode ser transportado pela WAN existente da empresa para o datacenter de destino.
- **Velocidade de expansão de WAN.** Se os orçamentos permitirem, largura de banda adicional poderá ser adicionada à solução WAN de uma empresa. No entanto, pode levar semanas ou meses para adquirir, provisionar e integrar conexões de fibra adicionais.
- **Velocidade dos discos.** Se os dados puderem ser movidos mais rapidamente e não houver limite para a largura de banda entre o binário de origem e o destino de destino, a física ainda seria um limitador. Os dados só podem ser replicados rapidamente, pois podem ser lidos de discos de origem. Ler a cada um ou zero de cada disco de rotação em um datacenter leva tempo.
- **Velocidade de cálculos humanos.** Discos e movimentações leves mais rápido que os processos de decisão humana. Quando um grupo de humanos é necessário para colaborar e tomar decisões juntas, os resultados ficarão ainda mais lentos. A replicação nunca pode superar atrasos relacionados à inteligência humana.

Cada uma dessas leis da física orienta os seguintes riscos que normalmente afetam os planos de migração:

- **Tempo de replicação.** As ferramentas de replicação avançadas não podem superar a &mdash;replication física básica requer tempo e largura de banda. Os planos devem incluir cronogramas realistas que refletem a quantidade de tempo que leva para replicar binários. A *largura de banda de migração total disponível* é a quantidade de largura de banda de limite, medida em megabits por segundo (Mbps) ou gigabits por segundo (Gbps), que não é consumida por outras necessidades de negócios de prioridade mais alta. *Armazenamento de migração total* é o espaço total em disco, medido em gigabytes ou terabytes, necessário para armazenar um instantâneo de todos os ativos a serem migrados. Uma estimativa inicial de tempo pode ser calculada dividindo o *armazenamento de migração total* pela *largura de banda de migração total disponível*. Observe a conversão de bits para bytes. Consulte a seguinte entrada, "efeito cumulativo de descompasso de disco", para um cálculo mais preciso do tempo.
- **Efeito cumulativo de descompasso de disco.** Do ponto de replicação à promoção de um ativo para produção, os binários de origem e de destino devem permanecer sincronizados. Os *descompassos* em binários consomem largura de banda adicional, pois todas as alterações no binário devem ser replicadas de forma recorrente. Durante a sincronização, todas as descompassos binárias devem ser incluídas no cálculo para o armazenamento de migração total. Quanto mais tempo leva para promover um ativo para produção, ocorrerá a descompasso mais cumulativa. Quanto mais ativos forem sincronizados, mais largura de banda consumida. Com cada ativo que está sendo mantido em um estado de sincronização, um pouco mais da largura de banda de migração total disponível é perdido.
- **Tempo para mudar para os negócios.** Conforme mencionado na entrada anterior, "efeito cumulativo de descompasso de disco", o tempo de sincronização tem um efeito negativo cumulativo na velocidade de migração. A priorização da lista de pendências de migração e a preparação avançada para o [plano de alteração comercial](../optimize/business-change-plan.md) são cruciais para a velocidade da migração. O teste mais significativo de alinhamento técnico e de negócios durante um esforço de migração é o ritmo da promoção. Quanto mais rápido um ativo puder ser promovido para produção, menos impacto o descompasso de disco terá na largura de banda e mais largura de banda/tempo que pode ser alocada para a replicação da próxima carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Após a conclusão da replicação, [as atividades de preparo](./stage.md) podem começar.

> [!div class="nextstepaction"]
> [Atividades de preparo durante uma migração](./stage.md)
