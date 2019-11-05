---
title: 'Modelos de promoção: etapa única, preparado ou vôo'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Entender o impacto da promoção em atividades de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 690c871ab18bef96a5a1738de90a216ca5b8df90
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564611"
---
# <a name="promotion-models-single-step-staged-or-flight"></a>Modelos de promoção: etapa única, preparado ou vôo

A migração da carga de trabalho geralmente é discutida como uma única atividade. Na verdade, ela é uma coleção de atividades menores que facilitam a movimentação de um ativo digital para a nuvem. Uma das últimas atividades em uma migração é a promoção de um ativo para a produção. A promoção é o ponto no qual o sistema de produção muda para os usuários finais. Geralmente isso pode ser tão simples quanto alterar o roteamento de rede, redirecionando os usuários finais para o novo ativo de produção. A promoção também é o ponto em que operações de TI ou da nuvem alteram o foco dos processos de gerenciamento operacional do sistema de produção anterior para os novos sistemas de produção.

Existem vários modelos de promoção. Este artigo descreve três dos mais comuns usados em migrações para a nuvem. A escolha de um modelo de promoção altera as atividades vistas nos processos de migração e otimização. Dessa forma, é necessário decidir o modelo de promoção no início de um lançamento.

## <a name="impact-of-promotion-model-on-migrate-and-optimize-activities"></a>Impacto do modelo de promoção nas atividades de migração e otimização

Em cada um dos modelos de promoção a seguir, a ferramenta de migração escolhida replica e prepara os ativos que compõem uma carga de trabalho. Após o preparo, cada modelo trata o ativo de forma um pouco diferente.

- **Promoção de etapa única.** Em um modelo de promoção de *etapa única*, o processo de preparo também serve como o processo de promoção. Depois de preparar em fases todos os ativos, o tráfego do usuário final é redirecionado e o preparo se torna a produção. Nesse caso, a promoção faz parte do processo de migração. Esse é o modelo de migração mais rápido. No entanto, essa abordagem dificulta a integração de atividades robustas de testes ou otimização. Além disso, esse tipo de modelo pressupõe que a equipe de migração tem acesso ao ambiente de preparo e produção, o que compromete a separação dos requisitos das funções em alguns ambientes.
  > [!NOTE]
  >O sumário deste site apresenta a atividade de promoção como parte do processo de otimização. Em um modelo de etapa única, a promoção ocorre durante o processo de migração. Ao usar esse modelo, as funções e responsabilidades devem ser atualizadas para refletir isso.
- **Em fases.** Em um modelo de promoção *em fases*, a carga de trabalho é considerada como migrada após ser preparada em fases, mas ainda não foi promovida. Antes da promoção, a carga de trabalho migrada passa por uma série de testes de desempenho, testes de negócios e alterações de otimização. Depois ela é promovida em uma data futura em conjunto com um plano de testes de negócios. Essa abordagem melhora o equilíbrio entre custo e desempenho, ao mesmo tempo que facilita a obtenção de validação de negócios.
- **Versão piloto.** O modelo de promoção em *versão piloto* combina os modelos de etapa única e em fases. Em um modelo de versão piloto, os ativos na carga de trabalho são tratados como produção após chegarem ao preparo em fases. Após um período condensado de testes automatizados, o tráfego da produção é direcionado para a carga de trabalho. No entanto, é um subconjunto do tráfego. Esse tráfego serve como a primeira versão piloto da produção e de testes. Supondo que a carga de trabalho seja executada a partir de uma perspectiva de recursos e desempenho, o tráfego adicional é migrado. Depois que todo o tráfego da produção for movido para os novos ativos, a carga de trabalho será considerada totalmente promovida.

O modelo de promoção escolhido afeta a sequência de atividades a serem executadas. Também afeta as funções e as responsabilidades da equipe de adoção da nuvem. Pode até mesmo afetar a composição de um ou de vários sprints.

## <a name="single-step-promotion"></a>Promoção de etapa única

Esse modelo usa ferramentas de automação de migração para replicar, preparar em fases e promover ativos. Os ativos são replicados em um ambiente de preparo em fases contido controlado pela ferramenta de migração. Depois que todos os ativos forem replicados, a ferramenta pode executar um processo automatizado para promover os ativos na assinatura escolhida em uma única etapa. Durante o preparo em fases, a ferramenta continua a replicar o ativo, minimizando a perda de dados entre os dois ambientes. Depois que um ativo é promovido, a ligação entre o sistema de origem e o sistema replicado é rompida. Com essa abordagem, se ocorrerem alterações adicionais nos sistemas de origem iniciais, as alterações serão perdidas.

**Vantagens.** Os benefícios dessa abordagem incluem:

- Esse modelo apresenta menos alterações nos sistemas de destino.
- A replicação contínua minimiza a perda de dados.
- Se um processo de preparo em fases falhar, poderá ser excluído e repetido rapidamente.
- A replicação e os testes repetidos de preparo em fases permitem um processo incremental de script e de teste.

**Desvantagens.** Os aspectos negativos dessa abordagem incluem:

- Os ativos preparados nas áreas restritas isoladas das ferramentas não permitem modelos de teste complexos.
- Durante a replicação, a ferramenta de migração consome a largura de banda no datacenter local. O preparo em fases de um grande volume de ativos durante uma duração estendida tem um impacto exponencial na largura de banda disponível, prejudicando o processo de migração e potencialmente afetando o desempenho das cargas de trabalho de produção no ambiente local.

## <a name="staged-promotion"></a>Promoção em fases

Nesse modelo, a área restrita de preparo em fases gerenciada pela ferramenta de migração é usada para fins de testes limitados. Os ativos replicados são depois implantados no ambiente de nuvem, que serve como um ambiente de preparo em fases estendido. Os ativos migrados são executados na nuvem, enquanto os ativos adicionais são replicados, preparados em fases e migrados. Quando as cargas de trabalho completas ficam disponíveis, um teste mais avançado é iniciado. Quando todos os ativos associados a uma assinatura forem migrados, a assinatura e todas as cargas de trabalho hospedadas serão promovidas para a produção. Nesse cenário, não há nenhuma alteração nas cargas de trabalho durante o processo de promoção. Em vez disso, as alterações tendem a estar nas camadas de rede e identidade, direcionando os usuários para o novo ambiente e revogando o acesso da equipe de adoção da nuvem.

**Vantagens.** Os benefícios dessa abordagem incluem:

- Esse modelo fornece oportunidades de teste de negócios mais exatas.
- É possível estudar melhor a carga de trabalho para otimizar o desempenho e os custos dos ativos.
- Um número maior de ativos pode ser replicado com restrições de tempo e largura de banda semelhantes.

**Desvantagens.** Os aspectos negativos dessa abordagem incluem:

- A ferramenta de migração escolhida não pode facilitar a replicação em andamento após a migração.
- Há a necessidade de um meio secundário de replicação de dados para sincronizar plataformas de dados durante o período de tempo do preparo em fases.

## <a name="flight-promotion"></a>Promoção de versão piloto

Esse modelo é semelhante ao modelo de promoção em fases. No entanto, há uma diferença fundamental. Quando a assinatura está pronta para promoção, o roteamento do usuário final ocorre em estágios ou versões pilotos. Em cada versão piloto, usuários adicionais são redirecionados para os sistemas de produção.

**Vantagens.** Os benefícios dessa abordagem incluem:

- Esse modelo atenua os riscos associados a uma grande atividade de migração ou promoção. Os erros na solução migrada podem ser identificados causando menos impacto aos processos de negócios.
- Ele permite monitorar as demandas de desempenho de carga de trabalho no ambiente de nuvem por mais tempo, aumentando a precisão das decisões de dimensionamento de ativos.
- É possível replicar um número maior de ativos com restrições de tempo e largura de banda semelhantes.

**Desvantagens.** Os aspectos negativos dessa abordagem incluem:

- A ferramenta de migração escolhida não pode facilitar a replicação em andamento após a migração.
- Há a necessidade de um meio secundário de replicação de dados para sincronizar plataformas de dados durante o período de tempo do preparo em fases.

## <a name="next-steps"></a>Próximos passos

Depois que um modelo de promoção é definido e aceito pela equipe de adoção de nuvem, a [correção de ativos](./remediate.md) pode começar.

> [!div class="nextstepaction"]
> [Corrigir ativos antes da migração](./remediate.md)
