---
title: Arquitetar cargas de trabalho antes da migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Arquitetar cargas de trabalho antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 151698c836add7c46c389cc94c76b942e52b0341
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240235"
---
# <a name="architect-workloads-prior-to-migration"></a>Arquitetar cargas de trabalho antes da migração

Este artigo expande o processo de avaliação revisando as atividades associadas à definição da arquitetura de uma carga de trabalho em uma determinada iteração. Conforme discutido no artigo sobre a [racionalização incremental](../../../digital-estate/rationalize.md), algumas suposições arquitetônicas são feitas durante qualquer transformação empresarial que exija uma migração. Este artigo esclarece essas suposições, compartilha alguns obstáculos que podem ser evitados e identifica oportunidades para acelerar o valor empresarial, desafiando essas suposições. Esse modelo incremental de arquitetura permite que as equipes se movimentem mais rapidamente e obtenham resultados dos negócios mais cedo.

## <a name="architecture-assumptions-prior-to-migration"></a>Pressuposições de arquitetura antes da migração

As suposições a seguir são típicas para qualquer esforço de migração:

- **IaaS.** Normalmente, supõe-se que a migração de cargas de trabalho envolve principalmente a movimentação de máquinas virtuais de um datacenter físico para um datacenter na nuvem por meio de uma migração de IaaS, exigindo o mínimo de redesenvolvimento ou de reconfiguração. Isso é conhecido como migração de comparação de _precisão e deslocamento_ . (Seguem as exceções.)
- **Consistência da arquitetura.** As alterações na arquitetura fundamental durante uma migração aumentam consideravelmente a complexidade. Depurar um sistema alterado em uma nova plataforma introduz muitas variáveis que podem ser difíceis de isolar. Por esse motivo, as cargas de trabalho devem ser submetidas apenas a alterações secundárias durante a migração e as alterações devem ser testadas detalhadamente.
- **Teste de desativação.** As migrações e a hospedagem de ativos consomem despesas operacionais e de capital possíveis. Supõe-se que as cargas de trabalho que estão sendo migradas foram revisadas para validar o uso contínuo. A opção de desativar ativos não utilizados gera economias de custos imediatas.
- **Redimensionar ativos.** Supõe-se que alguns ativos locais estão usando totalmente os recursos alocados. Antes da migração, supõe-se que os ativos serão redimensionados para se adequar melhor aos requisitos de uso reais.
- **Requisitos de BCDR (continuidade dos negócios e recuperação de desastres).** Supõe-se que um SLA acordado para a carga de trabalho foi negociado com a empresa antes do planejamento do lançamento. Esses requisitos provavelmente produzirão alterações secundárias na arquitetura.
- **Tempo de inatividade da migração.** Da mesma forma, o tempo de inatividade para promover a carga de trabalho para produção pode ter um efeito adverso na empresa. Às vezes, as soluções que devem fazer a transição com tempo de inatividade mínimo precisam de alterações de arquitetura. Supõe-se que um entendimento geral dos requisitos de tempo de inatividade tenha sido estabelecido antes do planejamento do lançamento.

## <a name="roadblocks-that-can-be-avoided"></a>Obstáculos que podem ser evitados

As suposições discriminadas podem criar empecilhos que poderiam retardar o progresso ou causar pontos problemáticos posteriores. Veja a seguir alguns obstáculos a serem observados, antes do lançamento:

- **Pagamento de dívida técnica.** Algumas cargas de trabalho obsoletas contêm uma grande quantidade de dívidas técnicas. Isso pode levar a desafios de longo prazo aumentando os custos de hospedagem com qualquer provedor de nuvem. Quando a dívida técnica aumenta de forma anormal os custos de hospedagem, arquiteturas alternativas devem ser avaliadas.
- **Padrões de tráfego do usuário.** As soluções existentes podem depender de padrões de roteamento de rede existentes. Esses padrões podem desacelerar o desempenho consideravelmente. Além disso, a introdução de novas soluções de WAN (rede de longa distância) pode levar semanas ou até mesmo meses. Prepare-se, no início do processo de arquitetura, para esses obstáculos considerando padrões de tráfego e alterações nos principais serviços de infraestrutura.

## <a name="accelerating-business-value"></a>Acelerar o valor empresarial

Alguns cenário poderiam exigir uma arquitetura diferente da estratégia de nova hospedagem de IaaS presumida. Seguem alguns exemplos:

- Alternativas do PaaS. As implantações do PaaS podem reduzir os custos de hospedagem e o tempo necessário para migrar determinadas cargas de trabalho. Para obter uma lista de abordagens que podem se beneficiar de uma conversão de PaaS, confira o artigo sobre [como avaliar ativos](./evaluate.md).
- Implantações com script/DevOps. Se uma carga de trabalho tiver uma implantação DevOps existente ou outras formas de implantação com script, o custo de alterar esses scripts poderá ser menor do que o custo de migrar o ativo.
- Esforços de correção. Os esforços de correção necessários para preparar uma carga de trabalho para migração podem ser amplos. Em alguns casos, faz mais sentido modernizar a solução do que corrigir problemas de compatibilidade subjacentes.

Em cada um desses cenários discriminados, uma arquitetura alternativa poder ser a melhor solução possível.

## <a name="next-steps"></a>Próximos passos

Depois que a nova arquitetura é definida, [estimativas de custo precisas podem ser calculadas](./estimate.md).

> [!div class="nextstepaction"]
> [Estimar os custos de nuvem](./estimate.md)
