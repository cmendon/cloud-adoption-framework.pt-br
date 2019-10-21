---
title: 'Preparar-se para a complexidade técnica: gerenciamento de alterações ágil'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Preparando-se para complexidade técnica – gerenciamento de alterações ágil
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d669d720d1bf56a5adc0df42a505608ab76b02ec
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548270"
---
# <a name="prepare-for-technical-complexity-agile-change-management"></a>Preparar-se para a complexidade técnica: gerenciamento de alterações ágil

Quando um datacenter inteiro pode ser desprovisionado e recriado com uma única linha de código, os processos tradicionais lutam para acompanhar o processo. As diretrizes em toda a estrutura de adoção de nuvem se baseiam em práticas como o gerenciamento de serviços de TI (ITSM), a Open Group Architecture Framework (TOGAF) e outras. No entanto, para garantir a agilidade e a capacidade de resposta às mudanças comerciais, essa estrutura molda essas práticas para ajustar as metodologias Agile e as abordagens DevOpss.

Ao mudar para um modelo ágil em que a flexibilidade e a iteração são enfatizadas, a complexidade técnica e o gerenciamento de alterações são tratados de forma diferente do que estão em um modelo tradicional em cascata, concentrando-se em uma série linear de etapas de migração. Este artigo descreve uma abordagem de alto nível para o gerenciamento de alterações em um esforço de migração baseado em Agile. No final deste artigo, você deve ter uma compreensão geral dos níveis de gerenciamento de alterações e da documentação envolvida em uma abordagem de migração incremental. Treinamento e decisões adicionais são necessários para selecionar e implementar práticas Agile com base nessa compreensão. A intenção deste artigo é preparar os arquitetos de nuvem para uma conversa facilitada com o gerenciamento de projetos, a fim de explicar o conceito geral do gerenciamento de alterações nessa abordagem.

## <a name="addressing-technical-complexity"></a>Lidando com a complexidade técnica

Ao alterar qualquer sistema técnico, complexidade e interdependência de injeção de risco em planos de projeto. As migrações de nuvem não são exceção. Ao mover milhares &mdash;or dezenas de milhares de &mdash;of ativos para a nuvem, esses riscos são amplificados. Detectar e mapear todas as dependências em um grande espaço digital pode levar anos. Poucas empresas podem tolerar um ciclo de análise longo. Para equilibrar a necessidade de análise de arquitetura e aceleração dos negócios, a estrutura de adoção de nuvem se concentra em um modelo de investimento para o gerenciamento de pendências do produto. As seções a seguir resumem esse tipo de modelo.

## <a name="invest-in-workloads"></a>INVESTIR em cargas de trabalho

O termo _carga de trabalho_ aparece em toda a estrutura de adoção de nuvem. Uma carga de trabalho é uma unidade de funcionalidade de aplicativo que pode ser migrada para a nuvem. Pode ser um único aplicativo, uma camada de um aplicativo ou uma coleção de um aplicativo. A definição é flexível e pode ser alterada em várias frases de migração. A estrutura de adoção de nuvem usa o termo _investimento_ para definir uma carga de trabalho.

INVESTIR é um acrônimo comum em muitas metodologias Agile para escrever histórias de usuários ou itens de lista de pendências de produtos, que são unidades de saída nas ferramentas de gerenciamento de projetos Agile. A unidade mensurável de saída em uma migração é uma carga de trabalho migrada. A estrutura de adoção de nuvem modifica o acrônimo de investimento um pouco para criar um constructo para definir cargas de trabalho:

- **Independente:** Uma carga de trabalho não deve ter nenhuma dependência inacessível. Para que uma carga de trabalho seja considerada migrada, todas as dependências devem ser acessíveis e incluídas no esforço de migração.
- **Negociável:** Conforme a descoberta adicional é executada, a definição de uma carga de trabalho é alterada. Os arquitetos que planejam a migração podem negociar fatores relacionados a dependências. Exemplos de pontos de negociação podem incluir pré-lançamento de recursos, tornar os recursos acessíveis em uma rede híbrida ou empacotar todas as dependências em uma única versão.
- **Valioso:** O valor em uma carga de trabalho é medido pela capacidade de fornecer aos usuários acesso a uma carga de trabalho de produção.
- **Estimable:** As dependências, os ativos, o tempo de migração, o desempenho e os custos de nuvem devem ser estimabledos e devem ser estimados antes da migração.
- **Pequeno:** O objetivo é empacotar cargas de trabalho em um único Sprint. No entanto, isso nem sempre pode ser viável. Em vez disso, as equipes são incentivadas a planejar sprints e versões para minimizar o tempo necessário para mover uma carga de trabalho para produção.
- **Teste:** Sempre deve haver um meio definido de teste ou validação da conclusão da migração de uma carga de trabalho.

Este acrônimo não se destina a uma base para a adesão rígida, mas deve ajudar a orientar a definição do termo _carga de trabalho_.

## <a name="migration-backlog-aligning-business-priorities-and-timing"></a>Registro posterior de migração: alinhando as prioridades de negócios e o tempo

A lista de pendências de migração permite que você acompanhe seu portfólio de nível superior de cargas de trabalho migrada. Antes da migração, a equipe de estratégia de nuvem e a equipe de adoção de nuvem são incentivadas a realizar uma revisão do [espaço digital](../../../digital-estate/index.md)atual e concordar com uma lista priorizada de cargas de trabalho a serem migradas. Esta lista constitui a base da lista de pendências de migração inicial.

Inicialmente, as cargas de trabalho na lista de pendências de migração são improvável de atender aos critérios de investimento descritos na seção anterior. Em vez disso, eles servem como um agrupamento lógico de ativos de um inventário inicial como um espaço reservado para trabalho futuro. Esses espaços reservados podem não ser tecnicamente precisos, mas servem como base para coordenação com os negócios.

![Relação entre os registros posteriores de migração, liberação e iteração usados durante o processo de migração](../../../_images/migrate/backlog-relationships.png)

*Os registros posteriores de migração, versão e iteração controlam diferentes níveis de atividade durante os processos de migração.*

Em qualquer pendência de migração, a equipe de gerenciamento de alterações deve se esforçar para obter as informações a seguir para qualquer carga de trabalho no plano. No mínimo, esses dados devem estar disponíveis para todas as cargas de trabalho priorizadas para migração nas próximas duas ou três versões.

### <a name="migration-backlog-data-points"></a>Pontos de dados da pendência de migração

- **Impacto nos negócios.** Compreensão do impacto ao negócio de falta da linha do tempo esperada ou redução da funcionalidade durante as janelas de congelamento.
- **Prioridade de negócios relativa.** Uma lista classificada de cargas de trabalho com base em prioridades de negócios.
- **Proprietário da empresa.** Documente uma pessoa responsável por tomar decisões de negócios relacionadas a essa carga de trabalho.
- **Proprietário técnico.** Documente um indivíduo responsável por decisões técnicas relacionadas a essa carga de trabalho.
- **Linhas do tempo esperadas.** Quando a migração estiver agendada para conclusão.
- **Carga de trabalho congela.** Os intervalos de tempo nos quais a carga de trabalho deve ser inqualificada para alteração.
- **Nome da carga de trabalho.**
- **Inventário inicial.** Todos os ativos necessários para fornecer a funcionalidade da carga de trabalho, incluindo VMs, dispositivos de ti, dados, aplicativos, pipelines de implantação e outros. Essas informações provavelmente serão imprecisas.

## <a name="release-backlog-aligning-business-change-and-technical-coordination"></a>Registro posterior de versões: alinhamento da mudança de negócios e coordenação técnica

No contexto de uma migração, uma _versão_ é uma atividade que implanta uma ou mais cargas de trabalho em produção. Uma versão geralmente abrange várias iterações ou trabalho técnico. No entanto, representa uma única iteração de alteração comercial. Depois que uma ou mais cargas de trabalho tiverem sido preparadas para a promoção de produção, ocorrerá uma versão. A decisão de empacotar uma versão é feita quando as cargas de trabalho migradas representam um valor comercial suficiente para justificar a injeção de alterações em um ambiente de negócios. As versões são executadas em conjunto com um [plano de mudança de negócios](../optimize/business-change-plan.md), após a conclusão do teste de [negócios](../optimize/business-test.md) . A equipe de estratégia de nuvem é responsável por planejar e supervisionar a execução de uma versão para garantir que a alteração de negócios desejada seja lançada.

Uma *pendência de versão* é o plano de estado futuro que define uma versão futura. A pendência de versão é o ponto dinâmico entre o gerenciamento de alterações de negócios (*registro posterior de migração*) e o gerenciamento de alterações técnicas (*acumulação de Sprint*). Um registro posterior de versão consiste em uma lista de cargas de trabalho das pendências de migração que se alinham a um subconjunto específico de realização de resultados de negócios. A definição e o envio de uma pendência de versão para a equipe de adoção de nuvem servem como um gatilho para análise mais profunda e planejamento de migração. Depois que a equipe de adoção de nuvem tiver verificado os detalhes técnicos associados a uma versão, ele poderá optar por confirmar o lançamento, estabelecendo uma linha do tempo de liberação com base no conhecimento atual.

Considerando o grau de análise necessário para validar uma versão, a equipe de estratégia de nuvem deve manter uma lista em execução das próximas duas a quatro versões. A equipe também deve tentar validar o máximo possível das informações a seguir, antes de definir e enviar uma versão. Uma equipe de estratégia de nuvem disciplinada capaz de manter as próximas quatro versões pode aumentar significativamente a consistência e a precisão das estimativas de cronograma de liberação.

### <a name="release-backlog-data-points"></a>Liberar pontos de dados de pendências

Uma parceria entre a equipe de estratégia de nuvem e a equipe de adoção de nuvem colabora para adicionar os seguintes pontos de dados para qualquer carga de trabalho na pendência de versão:

- **Inventário refinado.** Validação dos ativos necessários a serem migrados. Geralmente validados por meio de log ou monitoramento de dados no nível do host, da rede ou do sistema operacional para garantir uma compreensão precisa das dependências de rede e de hardware de cada ativo sob carga padrão.
- **Padrões de uso.** Uma compreensão dos padrões de uso dos usuários finais. Esses padrões geralmente incluem uma análise da distribuição geográfica do usuário final, rotas de rede, picos de uso sazonal, picos de uso diário/por hora e a composição do usuário final (intervalo versus externo).
- **Expectativas de desempenho.** Análise de dados de log disponíveis capturando taxa de transferência, pageviews, rotas de rede e outros dados de desempenho necessários para replicar a experiência do usuário final.
- **Depend.** Análise do tráfego de rede e padrões de uso do aplicativo para identificar quaisquer dependências de carga de trabalho adicionais, que devem ser fatoradas em sequenciamento e preparação ambiental. Não inclua uma carga de trabalho em uma versão até que um dos critérios a seguir possa ser atendido:
  - Todas as cargas de trabalho dependentes foram migradas.
  - As configurações de rede e segurança foram implementadas para permitir que a carga de trabalho acesse todas as dependências em alinhamento com as expectativas de desempenho existentes.
- **Abordagem de migração desejada.** No nível da pendência de migração, o esforço de migração assumido é a única consideração usada na análise. Por exemplo, se o resultado comercial for uma saída de um datacenter existente, todas as migrações serão consideradas um cenário de novo host na lista de pendências de migração. Na pendência de lançamento, a equipe de estratégia de nuvem e a equipe de adoção de nuvem devem avaliar o valor de longo prazo de recursos adicionais, modernização e investimentos de desenvolvimento contínuo para avaliar se uma abordagem mais moderna deve ser envolvida.
- **Critérios de teste de negócios.** Depois que uma carga de trabalho é adicionada à pendência de migração, os critérios de teste devem ser acordados mutuamente. Em alguns casos, os critérios de teste podem ser limitados a um teste de desempenho com um grupo de usuários avançados definido. No entanto, para validação estatística, um teste de desempenho automatizado é desejado e deve ser incluído. A instância existente do aplicativo geralmente não tem recursos de teste automatizados. Se isso for preciso, não será incomum que os arquitetos de nuvem trabalhem com usuários avançados para criar um teste de carga de linha de base em relação à solução existente para estabelecer um parâmetro de comparação a ser usado durante a migração.

### <a name="release-backlog-cadence"></a>Cadência da pendência de liberação

Em migrações maduras, as versões vêm em uma cadência regular. A velocidade da equipe de adoção da nuvem costuma ser normalizada, produzindo uma versão a cada duas a quatro iterações (aproximadamente a cada um ou dois meses). No entanto, isso deve ser um resultado orgânica. A criação de cadências de versão artificial pode afetar negativamente a capacidade da equipe de adoção da nuvem de obter uma taxa de transferência consistente.

Para estabilizar o impacto nos negócios, a equipe de estratégia de nuvem deve estabelecer um processo de lançamento mensal com a empresa para manter a caixa de diálogo regular, mas também deve estabelecer a expectativa de que ela será de vários meses antes que uma cadência de versão regular possa ser prevê.

## <a name="sprint-or-iteration-backlog-aligning-technical-change-and-effort"></a>Pendências de Sprint ou iteração: alinhando o esforço e a alteração técnica

Um *Sprint*, ou *iterativo*, é uma unidade de trabalho consistente e com limite de tempo. No processo de migração, isso geralmente é medido em incrementos de duas semanas. No entanto, não é desconhecido ter iterações de uma semana ou de quatro semanas. A criação de iterações com limite de tempo força intervalos consistentes de conclusão de esforço e permite um ajuste mais frequente aos planos, com base nos novos aprendizados. Durante qualquer Sprint específico, geralmente há tarefas para a avaliação, a migração e a otimização de cargas de trabalho definidas na lista de pendências de migração. Essas unidades de trabalho devem ser controladas e gerenciadas na mesma ferramenta de gerenciamento de projeto que as pendências de migração e de versão, para gerar consistência em cada nível de gerenciamento de alterações.

Uma *pendência de Sprint*, ou *pendências de iteração*, consiste no trabalho técnico a ser concluído em um único Sprint ou iteração, lidando com a migração de ativos individuais. Essa tarefa deve ser derivada da lista de cargas de trabalho que estão sendo migradas. Ao usar ferramentas como o Azure DevOps (anteriormente Visual Studio online) para o gerenciamento de projetos, os itens de trabalho em um Sprint seriam filhos dos itens da pendência de produto em uma pendência de versão e Epics em uma pendência de migração. Essa relação pai-filho permite a clareza em todos os níveis de gerenciamento de alterações.

Dentro de um único Sprint ou iterativo, a equipe de adoção de nuvem trabalharia para fornecer a quantidade comprometida de trabalho técnico, levando em direção à migração de uma carga definida. Esse é o resultado final da estratégia de gerenciamento de alterações. Ao concluir, esses esforços podem ser testados validando a preparação de produção de uma carga de trabalho preparada na nuvem.

### <a name="large-or-complex-sprint-structures"></a>Estruturas de Sprint grandes ou complexas

Para uma pequena migração com uma equipe de migração independente, um único Sprint pode incluir todas as quatro fases de uma migração para uma única carga de trabalho (*avaliar*, *migrar*, *otimizar*e *proteger e gerenciar*). Mais comumente, cada um desses processos compartilhados por várias equipes em itens de trabalho distintos em vários sprints. Dependendo do tipo de esforço, da escala de esforço e das funções, esses sprints podem ter algumas formas diferentes.

- **Fábrica de migração.** As migrações em larga escala às vezes exigem uma abordagem que se assemelha a uma fábrica no modelo de execução. Nesse modelo, várias equipes são alocadas para a execução de um processo de migração específico (ou subconjunto do processo). Após a conclusão, a saída do sprint de uma equipe popula a pendência para a próxima equipe. Essa é uma abordagem eficiente para migrações de vários hosts de grande escala de várias cargas de trabalho potenciais envolvendo milhares de máquinas virtuais passando por fases de avaliação, arquitetura, correção e migração. No entanto, para que essa abordagem funcione, é necessário um novo ambiente homogêneo com processos de aprovação e gerenciamento de alterações simplificados.
- **Ondas de migração.** Outra abordagem que funciona bem para grandes migrações é um modelo de onda. Nesse modelo, a divisão de trabalho não é tão clara. As equipes se dedicam à execução do processo de migração de cargas de trabalho individuais. No entanto, a natureza de cada Sprint é alterada. Em um Sprint, a equipe pode concluir a avaliação e o trabalho de arquitetura. Em outro Sprint, ele pode concluir o trabalho de migração. No entanto, em outro Sprint, o foco estaria na versão de otimização e de produção. Essa abordagem permite que uma equipe principal fique alinhada às cargas de trabalho, vendo-as em todo o processo em sua totalidade. Ao usar essa abordagem, a diversidade de habilidades e a alternância de contexto pode reduzir a possível velocidade da equipe, reduzindo o esforço de migração. Além disso, os obstáculos durante os ciclos de aprovação podem causar atrasos significativos. É importante manter as opções na pendência de lançamento para manter a equipe se movendo durante períodos bloqueados, com esse modelo. Também é importante fazer um treinamento entre os membros da equipe e garantir que habilidades se alinhem com o tema de cada Sprint.

### <a name="sprint-backlog-data-points"></a>Pontos de dados de pendências do Sprint

O resultado de um Sprint captura e documenta as alterações feitas em uma carga de trabalho, fechando assim o loop de gerenciamento de alterações. Quando concluído, no mínimo, o seguinte deve ser documentado. Durante a execução de um Sprint, esta documentação deve ser concluída em conjunto com os itens de trabalho técnicos.

- **Ativos implantados.** Todos os ativos implantados na nuvem para hospedar a carga de trabalho.
- **Corre.** Quaisquer alterações nos ativos para se preparar para a migração na nuvem.
- **Configuração.** Configuração escolhida de quaisquer ativos implantados, incluindo quaisquer referências a scripts de configuração.
- **Modelo de implantação.** Abordagem usada para implantar o ativo na nuvem, incluindo referências a quaisquer scripts ou ferramentas de implantação.
- **Arquitectura.** Documentação da arquitetura implantada na nuvem.
- **Métricas de desempenho.** Saída de teste automatizado ou teste de negócios realizado para validar o desempenho no momento da implantação.
- **Requisitos ou configuração exclusivos.** Quaisquer aspectos exclusivos da implantação, da configuração ou dos requisitos técnicos necessários para operar a carga de trabalho.
- **Aprovação operacional.** A aprovação da validação da prontidão operacional do proprietário do aplicativo e da equipe de operações de ti responsável pelo gerenciamento da carga de trabalho após a implantação.
- **Aprovação da arquitetura.** Saia do proprietário da carga de trabalho e da equipe de adoção da nuvem para validar quaisquer alterações de arquitetura necessárias para hospedar cada ativo.

## <a name="next-steps"></a>Próximos passos

Depois que as abordagens de gerenciamento de alterações tiverem sido estabelecidas, seu tempo para resolver o pré-requisito final, [revisão da pendência de migração](./migration-backlog-review.md)

> [!div class="nextstepaction"]
> [Revisão da pendência de migração](./migration-backlog-review.md)
