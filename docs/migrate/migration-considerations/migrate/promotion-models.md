---
title: Modelos de promoção – promover, preparar ou comprovar
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Entender o impacto da promoção em atividades de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: b251e5159f6e6728e0b5a7ce807eaba0ea85696a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548439"
---
# <a name="promotion-models---single-step-staged-or-flight"></a>Modelos de promoção-etapa única, preparado ou vôo

A migração de carga de trabalho geralmente é discutida como uma única atividade. Na realidade, é uma coleção de atividades menores que facilitam a movimentação de um ativo digital para a nuvem. Uma das últimas atividades em uma migração é a promoção de um ativo para produção. Promoção é o ponto no qual o sistema de produção muda para os usuários finais. Geralmente, isso pode ser tão simples quanto alterar o roteamento de rede, redirecionando os usuários finais para o novo ativo de produção. A promoção também é o ponto em que operações de ti ou operações de nuvem alteram o foco dos processos de gerenciamento operacional do sistema de produção anterior para os novos sistemas de produção.

Há vários modelos de promoção. Este artigo descreve três das mais comuns usadas em migrações na nuvem. A escolha de um modelo de promoção altera as atividades vistas nos processos migrar e otimizar. Dessa forma, o modelo de promoção deve ser decidido no início de uma versão.

## <a name="impact-of-promotion-model-on-migrate-and-optimize-activities"></a>Impacto do modelo de promoção em migrar e otimizar atividades

Em cada um dos modelos de promoção a seguir, a ferramenta de migração escolhida Replica e prepara os ativos que compõem uma carga de trabalho. Após o preparo, cada modelo trata o ativo um pouco diferente.

- **Promoção de etapa única.** Em um modelo de promoção de *etapa única* , o processo de preparo dobra como o processo de promoção. Depois que todos os ativos são preparados, o tráfego do usuário final é redirecionado e o preparo torna-se produção. Nesse caso, a promoção faz parte do processo de migração. Esse é o modelo de migração mais rápido. No entanto, essa abordagem dificulta a integração de atividades robustas de teste ou otimização. Além disso, esse tipo de modelo pressupõe que a equipe de migração tem acesso ao ambiente de preparo e produção, que compromete a separação dos requisitos de imposto em alguns ambientes.
  > [!NOTE]
  >O Sumário para este site lista a atividade de promoção como parte do processo de otimização. Em um modelo de etapa única, a promoção ocorre durante o processo de migração. Ao usar esse modelo, as funções e responsabilidades devem ser atualizadas para refletir isso.
- **Em etapas.** Em um modelo de promoção em *etapas* , a carga de trabalho é considerada migrada após ser preparada, mas ainda não foi promovida. Antes da promoção, a carga de trabalho migrada passa por uma série de testes de desempenho, testes de negócios e alterações de otimização. Em seguida, ele é promovido em uma data futura em conjunto com um plano de teste de negócios. Essa abordagem melhora o equilíbrio entre custo e desempenho, ao mesmo tempo que facilita a obtenção de validação de negócios.
- **Estejam.** O modelo de promoção de *voo* combina modelos de etapa única e em etapas. Em um modelo de vôo, os ativos na carga de trabalho são tratados como produção após o pouso no preparo. Após um período condensado de testes automatizados, o tráfego de produção é roteado para a carga de trabalho. No entanto, é um subconjunto do tráfego. Esse tráfego serve como o primeiro vôo de produção e teste. Supondo que a carga de trabalho seja executada de uma perspectiva de recursos e desempenho, o tráfego adicional é migrado. Depois que todo o tráfego de produção for movido para os novos ativos, a carga de trabalho será considerada totalmente promovida.

O modelo de promoção escolhido afeta a sequência de atividades a serem executadas. Ele também afeta as funções e as responsabilidades da equipe de adoção da nuvem. Pode até mesmo afetar a composição de um Sprint ou de vários sprints.

## <a name="single-step-promotion"></a>Promoção de etapa única

Esse modelo usa ferramentas de automação de migração para replicar, preparar e promover ativos. Os ativos são replicados em um ambiente de preparo independente controlado pela ferramenta de migração. Depois que todos os ativos forem replicados, a ferramenta poderá executar um processo automatizado para promover os ativos na assinatura escolhida em uma única etapa. Durante o preparo, a ferramenta continua replicando o ativo, minimizando a perda de dados entre os dois ambientes. Depois que um ativo é promovido, a ligação entre o sistema de origem e o sistema replicado é severa. Nessa abordagem, se ocorrerem alterações adicionais nos sistemas de origem iniciais, as alterações serão perdidas.

**Prós.** Os benefícios positivos dessa abordagem incluem:

- Esse modelo apresenta menos alterações nos sistemas de destino.
- A replicação contínua minimiza a perda de dados.
- Se um processo de preparo falhar, ele poderá ser excluído e repetido rapidamente.
- A replicação e os testes de preparo repetidos permitem um processo incremental de script e de teste.

**Contras.** Aspectos negativos dessa abordagem incluem:

- Os ativos preparados nas ferramentas – área restrita isolada não permitem modelos de teste complexos.
- Durante a replicação, a ferramenta de migração consome largura de banda no datacenter local. O preparo de um grande volume de ativos durante uma duração estendida tem um impacto exponencial na largura de banda disponível, prejudicando o processo de migração e potencialmente afeta o desempenho das cargas de trabalho de produção no ambiente local.

## <a name="staged-promotion"></a>Promoção em etapas

Nesse modelo, a área restrita de preparo gerenciada pela ferramenta de migração é usada para fins de teste limitado. Os ativos replicados são então implantados no ambiente de nuvem, que serve como um ambiente de preparo estendido. Os ativos migrados são executados na nuvem, enquanto os ativos adicionais são replicados, preparados e migrados. Quando cargas de trabalho completas ficam disponíveis, um teste mais avançado é iniciado. Quando todos os ativos associados a uma assinatura foram migrados, a assinatura e todas as cargas de trabalho hospedadas são promovidas para a produção. Nesse cenário, não há nenhuma alteração nas cargas de trabalho durante o processo de promoção. Em vez disso, as alterações tendem a estar nas camadas de rede e identidade, roteando os usuários para o novo ambiente e revogando o acesso da equipe de adoção de nuvem.

**Prós.** Os benefícios positivos dessa abordagem incluem:

- Esse modelo fornece oportunidades de teste de negócios mais precisas.
- A carga de trabalho pode ser estudada mais de maneira mais próxima para otimizar o desempenho e os custos dos ativos.
- Um número maior de ativos pode ser replicado em restrições de tempo e largura de banda semelhantes.

**Contras.** Aspectos negativos dessa abordagem incluem:

- A ferramenta de migração escolhida não pode facilitar a replicação em andamento após a migração.
- Um meio secundário de replicação de dados é necessário para sincronizar plataformas de dados durante o período de tempo preparado.

## <a name="flight-promotion"></a>Promoção de voo

Esse modelo é semelhante ao modelo de promoção em etapas. No entanto, há uma diferença fundamental. Quando a assinatura está pronta para promoção, o roteamento do usuário final ocorre em estágios ou voos. Em cada vôo, usuários adicionais são redirecionados para os sistemas de produção.

**Prós.** Os benefícios positivos dessa abordagem incluem:

- Esse modelo atenua os riscos associados a uma grande atividade de migração ou promoção. Os erros na solução migrada podem ser identificados com menos impacto nos processos de negócios.
- Ele permite o monitoramento de demandas de desempenho de carga de trabalho no ambiente de nuvem por uma duração estendida, aumentando a precisão das decisões de dimensionamento de ativos.
- Números maiores de ativos podem ser replicados em restrições de tempo e largura de banda semelhantes.

**Contras.** Aspectos negativos dessa abordagem incluem:

- A ferramenta de migração escolhida não pode facilitar a replicação em andamento após a migração.
- Um meio secundário de replicação de dados é necessário para sincronizar plataformas de dados durante o período de tempo preparado.

## <a name="next-steps"></a>Próximos passos

Depois que um modelo de promoção é definido e aceito pela equipe de adoção de nuvem, a [correção de ativos](./remediate.md) pode começar.

> [!div class="nextstepaction"]
> [Corrigindo ativos antes da migração](./remediate.md)
