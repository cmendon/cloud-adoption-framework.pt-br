---
title: Criando uma organização sensível ao custo
description: Aprenda as práticas recomendadas para a criação de uma organização com consciência de custo.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.openlocfilehash: 42025e9e7459aae8731b6269d6bc5512acde64e4
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76800892"
---
# <a name="build-a-cost-conscious-organization"></a>Crie uma organização com consciência de custo

Conforme descrito em [motivações: por que estamos migrando para a nuvem?](../strategy/motivations.md), há muitos motivos de som para uma empresa adotar a nuvem. Quando a redução de custos é um driver primário, é importante criar uma organização sensível ao custo.

Garantir o custo cérebro não é uma atividade única. Como outros tópicos de adoção de nuvem, é iterativa. O diagrama a seguir descreve esse processo para se concentrar em três atividades interdependentes: *visibilidade*, *responsabilidade*e *otimização*. Esses processos são executados em macros e micro níveis, que descrevemos detalhadamente neste artigo.

![processo sensível ao custo](../_images/ready/cost-optimization-process.png)
*Figura 1-contorno da organização com consciência de custo.*

## <a name="general-cost-conscious-processes"></a>Processos de custos gerais

- **Visibilidade:** Para que uma organização esteja consciente dos custos, ela precisa de visibilidade nesses custos. A visibilidade em uma organização econômica exige relatórios consistentes para as equipes que adotam a nuvem, as equipes financeiras que gerenciam orçamentos e equipes de gerenciamento responsáveis pelos custos. Essa visibilidade é realizada estabelecendo:
  - O escopo de relatório certo.
  - Organização de recursos apropriada (grupos de gerenciamento, grupos de recursos, assinaturas).
  - Desmarque as estratégias de marcação.
  - Controles de acesso apropriados (RBAC).

- **Responsabilidade:** A responsabilidade é tão importante quanto a visibilidade. A responsabilidade começa com orçamentos claros para esforços de adoção. Os orçamentos devem ser bem estabelecidos, comunicados claramente e com base nas expectativas realistas. A responsabilidade exige um processo iterativo e uma mentalidade de crescimento para impulsionar o nível certo de responsabilidade.

- **Otimização:** A otimização é a ação que cria reduções de custos. Durante a otimização, as alocações de recursos são modificadas para reduzir o custo de suporte a várias cargas de trabalho. Esse processo requer iteração e experimentação. Cada redução no custo reduz o desempenho. Encontrar o equilíbrio certo entre o controle de custo e as expectativas de desempenho do usuário final exige a entrada de várias partes.

As seções a seguir descrevem as funções que a *equipe de estratégia de nuvem*, a equipe de adoção de *nuvem,* a *equipe de governança de nuvem*e o *Cloud Center of Excellence* (CCOE) desempenham no desenvolvimento de uma organização com consciência de custo.

## <a name="cloud-strategy-team"></a>Equipe de estratégia de nuvem

A criação de cérebro de custo em esforços de adoção de nuvem começa no nível de liderança. Para ser efetivo a longo prazo, a [equipe de estratégia de nuvem](./cloud-strategy.md) deve incluir um membro da equipe de finanças. Se sua estrutura financeira mantiver gerentes comerciais acessados por custos de soluções, eles deverão ser convidados a participar da equipe também. Além das atividades principais que normalmente são atribuídas à equipe de estratégia de nuvem, todos os membros da equipe de estratégia de nuvem também devem ser responsáveis por:

- **Visibilidade:** A equipe de estratégia de nuvem e a [equipe de governança de nuvem](./cloud-governance.md) precisam saber os custos reais dos esforços de adoção de nuvem. Dada a visão de nível executivo dessa equipe, eles devem ter acesso a vários escopos de custo para analisar decisões de gastos. Normalmente, um executivo precisa de visibilidade dos custos totais em todos os "gastos" da nuvem. Mas como membros ativos da equipe de estratégia de nuvem, eles também devem ser capazes de exibir os custos por unidade de negócios ou por unidade de cobrança para validar o regressivo, o estorno ou outros [modelos de contabilidade de nuvem](../strategy/cloud-accounting.md).

- **Responsabilidade:** Os orçamentos devem ser estabelecidos entre a estratégia de nuvem, [governança de nuvem](./cloud-governance.md)e equipes de [adoção de nuvem](./cloud-adoption.md) com base nas atividades de adoção esperadas. Quando ocorrem desvios do orçamento, a equipe de estratégia de nuvem e a equipe de governança de nuvem devem ser parceiras para determinar rapidamente o melhor curso de ação para corrigir os desvios.

- **Otimização:** Durante os esforços de otimização, a equipe de estratégia de nuvem pode representar o investimento e o valor de retorno de cargas de trabalho específicas. Se uma carga de trabalho tiver um valor estratégico ou impacto financeiro sobre os negócios, os esforços de otimização de custos devem ser monitorados de maneira minuciosa. Se não houver impacto estratégico na organização e nenhum custo inerente de desempenho ruim de uma carga de trabalho, a equipe de estratégia de nuvem poderá aprovar a superotimização. Para impulsionar essas decisões, a equipe deve ser capaz de exibir os custos em um escopo por projeto.

## <a name="cloud-adoption-team"></a>Equipe de adoção de nuvem

A [equipe de adoção de nuvem](./cloud-adoption.md) está no centro de todas as atividades de adoção. Portanto, eles são a primeira linha de defesa contra o excesso de gastos. Essa equipe tem uma função ativa em todas as três fases de custo-cérebro.

- **Visualizar**

  - **Conscientização:** É importante que a equipe de adoção de nuvem tenha visibilidade das metas de economia de custo do esforço. Simplesmente informando que o esforço de adoção da nuvem ajudará a reduzir os custos é uma receita de falha. Visibilidade *específica* é importante. Por exemplo, se o objetivo é reduzir o TCO do datacenter em 3% ou despesas operacionais anuais em 7%, divulgue os destinos antecipadamente e claramente.
  - **Telemetria:** Essa equipe precisa de visibilidade do impacto de suas decisões. Durante as atividades de migração ou inovação, suas decisões têm um efeito direto sobre os custos e o desempenho. A equipe precisa balancear esses dois fatores concorrentes. O monitoramento de desempenho e o monitoramento de custos que são incluídos no escopo dos projetos ativos da equipe são importantes para fornecer a visibilidade necessária.

- **Responsabilidade:** A equipe de adoção de nuvem precisa estar ciente de quaisquer orçamentos predefinidos associados aos seus esforços de adoção. Quando os custos reais não se alinham com o orçamento, há uma oportunidade de criar responsabilidade. A responsabilidade não equivale a penalizar a equipe de adoção de exceder o orçamento, pois o excesso de orçamentos pode resultar de decisões de desempenho necessárias. Em vez disso, a responsabilidade significa instruir a equipe sobre as metas e como suas decisões afetam essas metas. Além disso, a responsabilidade inclui fornecer uma caixa de diálogo na qual a equipe possa se comunicar sobre decisões que levaram a um excesso de gastos. Se essas decisões estiverem desalinhadas com as metas do projeto, esse esforço fornecerá uma boa oportunidade para fazer uma parceria com a equipe de estratégia de nuvem para tomar decisões melhores.

- **Otimização:** Esse esforço é um ato de balanceamento, pois a otimização dos recursos pode reduzir o desempenho das cargas de trabalho com suporte. Às vezes, as economias previstas ou orçadas não podem ser realizadas para uma carga de trabalho porque a carga de trabalho não é executada adequadamente com os recursos orçados. Nesses casos, a equipe de adoção de nuvem tem que tomar decisões inteligentes e relatar alterações na equipe de estratégia de nuvem e na equipe de governança de nuvem para que os orçamentos ou decisões de otimização possam ser corrigidos.

## <a name="cloud-governance-team"></a>Equipe de governança de nuvem

Em geral, a [equipe de governança de nuvem](./cloud-governance.md) é responsável pelo gerenciamento de custos em todo o esforço de adoção da nuvem. Conforme descrito no tópico disciplina de [Gerenciamento de custos](../govern/cost-management/index.md) da metodologia de governança da estrutura de adoção da nuvem, o gerenciamento de custos é a primeira das cinco disciplinas de governança de nuvem. Esses artigos descrevem uma série de responsabilidades mais profundas para a equipe de governança de nuvem.

Esse esforço se concentra nas seguintes atividades relacionadas ao desenvolvimento de uma organização com consciência de custo:

- **Visibilidade:** A equipe de governança de nuvem funciona como um par da equipe de estratégia de nuvem para planejar os orçamentos de adoção de nuvem. Essas duas equipes também trabalham em conjunto para analisar regularmente as despesas reais. A equipe de governança de nuvem é responsável por assegurar relatórios de custos consistentes e confiáveis e telemetria de desempenho.

- **Responsabilidade:** Quando ocorrem desvios de orçamento, a equipe de estratégia de nuvem e a equipe de governança de nuvem devem ser parceiras para determinar rapidamente o melhor curso de ação para corrigir os desvios. Em geral, a equipe de governança de nuvem agirá nessas decisões. Às vezes, a ação pode ser um novo treinamento simples para a [equipe de adoção de nuvem](./cloud-adoption.md)afetada. A equipe de governança de nuvem também pode ajudar a otimizar ativos implantados, alterar opções de desconto ou até mesmo implementar opções automatizadas de controle de custo, como o bloqueio da implantação de ativos não planejados.

- **Otimização:** Depois que os ativos são migrados para o ou criados na nuvem, você pode empregar ferramentas de monitoramento para avaliar o desempenho e a utilização desses ativos. O monitoramento e os dados de desempenho adequados podem identificar os ativos que devem ser otimizados. A equipe de governança de nuvem é responsável por garantir que as ferramentas de monitoramento e relatório de custos sejam implantadas de forma consistente. Eles também podem ajudar as equipes de adoção a identificar oportunidades para otimizar com base no desempenho e na telemetria de custos.

## <a name="cloud-center-of-excellence"></a>Centro de excelência de nuvem

Embora não seja normalmente responsável pelo gerenciamento de custos, o CCoE pode ter um impacto significativo em organizações com custos de custo. Muitas decisões fundamentais de ti afetam os custos em escala. Quando o CCoE faz sua parte, os custos podem ser reduzidos para vários esforços de adoção de nuvem.

- **Visibilidade:** Qualquer grupo de gerenciamento ou grupo de recursos que hospeda os principais ativos de ti deve estar visível para a equipe do CCoE. A equipe pode usar esses dados para as oportunidades de farm para otimizar.

- **Responsabilidade:** Embora não seja normalmente contabilizado por custo, o CCoE pode se manter em conta própria para criar soluções reproduzíveis que minimizem o custo e maximizem o desempenho.

- **Otimização:** Dada a visibilidade do CCoE a várias implantações, a equipe está em uma posição ideal para sugerir dicas de otimização e para ajudar as equipes de adoção a ajustar ativos melhor.

## <a name="next-steps"></a>Próximos passos

A prática dessas responsabilidades em cada nível da empresa ajuda a conduzir uma organização econômica. Para começar a agir nessas diretrizes, examine a [introdução à preparação organizacional](./index.md) para ajudar a identificar as estruturas de equipe corretas.

> [!div class="nextstepaction"]
> [Identificar as estruturas de equipe certas](./index.md)
