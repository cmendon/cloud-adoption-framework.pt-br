---
title: Que função a replicação e a sincronização desempenham no processo de migração?
description: Um processo na migração na nuvem que se concentra nas tarefas de migrar cargas de trabalho para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5eaea53e65951cb5fee3d36b2eba472e1048feb2
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222243"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-role-does-replication-play-in-the-migration-process"></a>Que função a replicação desempenha no processo de migração?

Os datacenters locais são preenchidos com ativos físicos, como servidores, dispositivos e dispositivos de rede. No entanto, cada servidor é apenas um shell físico. O valor real vem do binário em execução no servidor. Os aplicativos e os dados são a finalidade do datacenter. Eles são os principais binários a serem migrados. Outros ativos digitais e fontes binárias, como sistemas operacionais, rotas de rede, arquivos e protocolos de segurança fornecem esses aplicativos e os armazenamentos de dados.

A replicação é o principal instrumento dos esforços de migração. É o processo de copiar a versão de um ponto no tempo de vários binários. Em seguida, os instantâneos binários são copiados para uma nova plataforma e implementados em um novo hardware, em um processo conhecido como *propagação*. Quando executada corretamente, a cópia propagada do binário deve se comportar de maneira idêntica ao binário original no hardware antigo. No entanto, esse instantâneo do binário é imediatamente desatualizado e desalinhado com a fonte original. Para manter o novo binário e o antigo binário alinhados, um processo chamado de *sincronização* atualiza continuamente a cópia armazenada na nova plataforma. A sincronização continua até que o ativo seja promovido de acordo com o modelo de promoção escolhido. Nesse ponto, a sincronização é interrompida.

## <a name="required-prerequisites-to-replication"></a>Pré-requisitos exigidos para a replicação

Antes da replicação, a *nova plataforma* e o hardware devem estar preparados para receber as cópias binárias. O artigo sobre os [pré-requisitos](../prerequisites/index.md) descreve os requisitos mínimos do ambiente para ajudar a criar uma plataforma segura, robusta e de alto desempenho para receber as réplicas binárias.

Os *binários de origem* também devem ser preparados para a replicação e sincronização. Os artigos sobre avaliação, arquitetura e remediação abordam as ações necessárias para garantir que o binário de origem esteja pronto para a replicação e sincronização.

Uma *cadeia de ferramentas* condizente com a nova plataforma e os binários de origem deve ser implementada para executar e gerenciar os processos de replicação e sincronização. O artigo sobre as [opções de replicação](./replicate-options.md) descreve várias ferramentas que podem contribuir para uma migração para o Azure.

## <a name="replication-risks---physics-of-replication"></a>Riscos da replicação - física da replicação

Durante o planejamento para a replicação de qualquer fonte binária para um novo destino, há algumas leis fundamentais que devem ser seriamente consideradas durante o planejamento e a execução.

- **Velocidade da luz.** Para mover grandes volumes de dados, a fibra ainda é a opção mais rápida. Infelizmente, esses cabos só conseguem migrar dados a dois terços da velocidade da luz. Isso significa que não há métodos para a replicação instantânea ou ilimitada de dados.
- **Velocidade do pipeline de WAN.** Mais consequencial do que a velocidade de movimentação de dados é a largura de banda de uplink, que define o volume de dados por segundo que pode ser transportado pela WAN existente da empresa para o datacenter de destino.
- **Velocidade da expansão de WAN.** Se os orçamentos permitirem, uma largura de banda adicional poderá ser adicionada à solução de WAN de uma empresa. No entanto, pode levar semanas ou meses para adquirir, provisionar e integrar conexões de fibra adicionais.
- **Velocidade de discos.** Se os dados pudessem se mover com mais rapidez e não houvesse limite para a largura de banda entre o binário de origem e o destino, a física ainda seria um limitador. Os dados podem ser replicados somente da maneira mais rápida possível para serem lidos dos discos de origem. A leitura de todos os uns ou zeros de cada disco giratório em um datacenter leva tempo.
- **Velocidade de cálculos humanos.** Discos e luz se movem mais rapidamente que processos de decisão humanos. Quando um grupo de humanos é obrigado a colaborar e tomar decisões em conjunto, os resultados surgirão ainda mais devagar. A replicação jamais superará atrasos relacionados à inteligência humana.

Cada uma dessas leis da física orienta os seguintes riscos que normalmente afetam os planos de migração:

- **Tempo de replicação.** As ferramentas avançadas de replicação não podem superar a física básica&mdash;a replicação requer tempo e largura de banda. Os planos devem incluir cronogramas realistas que reflitam o tempo necessário para replicar binários. A *largura de banda total de migração disponível* é a quantidade de largura de banda limite, medida em megabits por segundo (Mbps) ou gigabits por segundo (Gbps), que não é consumida por outras necessidades de negócios de prioridade mais alta. O *armazenamento total de migração* é o espaço total em disco, medido em gigabytes ou terabytes, necessário para armazenar um instantâneo de todos os ativos que serão migrados. Uma estimativa inicial de tempo pode ser calculada dividindo o *armazenamento total de migração* pela *largura de banda total de migração disponível*. Observe a conversão de bits para bytes. Confira a seguinte entrada: "Efeito cumulativo do desvio do disco", para ver um cálculo mais preciso do tempo.
- **Efeito cumulativo do desvio do disco.** Do ponto de replicação até a promoção de um ativo para produção, os binários de origem e destino devem permanecer sincronizados. O *desvio* nos binários consomem largura de banda adicional já que todas as alterações no binário devem ser replicadas de forma recorrente. Durante a sincronização, todo o desvio binário deve ser incluído no cálculo do armazenamento de migração total. Quanto mais tempo demorar para promover um ativo para a produção, mais desvio cumulativo haverá. Quanto mais ativos estiverem sendo sincronizados, mais largura de banda será consumida. Com os ativos sendo mantidos em um estado de sincronização, perde-se um pouco mais da largura de banda total de migração disponível.
- **Tempo para mudanças nos negócios.** Conforme mencionado na entrada anterior, "Efeito cumulativo do desvio do disco", o tempo de sincronização tem um efeito cumulativo negativo na velocidade de migração. A priorização da lista de pendências de migração e a preparação avançada para o [plano de mudança empresarial](../optimize/business-change-plan.md) são cruciais para a velocidade da migração. O ritmo da promoção é o teste mais importante de alinhamento comercial e técnico durante um esforço de migração. Quanto mais rápido um ativo puder ser promovido para produção, menos impacto haverá na largura de banda e maior será a largura de banda/tempo que poderá ser alocada/o para a replicação da próxima carga de trabalho.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Após a conclusão da replicação, as [atividades de preparo](./stage.md) podem começar.

> [!div class="nextstepaction"]
> [Atividades de preparo durante uma migração](./stage.md)
