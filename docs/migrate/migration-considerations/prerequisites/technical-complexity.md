---
title: 'Preparar-se para a complexidade técnica: gerenciamento de alterações Agile'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como se preparar para a complexidade técnica – gerenciamento de alterações Agile
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 842143afbb042ceddee5029a3fa86d0aa8cdd997
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564542"
---
# <a name="prepare-for-technical-complexity-agile-change-management"></a>Preparar-se para a complexidade técnica: gerenciamento de alterações Agile

Quando um datacenter inteiro pode ser desprovisionado e recriado com uma única linha de código, os processos tradicionais lutam para acompanhar o processo. As diretrizes em todo o Cloud Adoption Framework se baseiam em práticas como o ITSM (gerenciamento de serviços de TI), a TOGAF (Estrutura de Arquitetura de Grupo Aberto) e outros. No entanto, para garantir a agilidade e a capacidade de resposta às alterações empresariais, essa estrutura molda tais práticas para se ajustar às metodologias Agile e às abordagens DevOps.

Ao mudar para um modelo Agile em que a flexibilidade e a iteração são enfatizadas, a complexidade técnica e o gerenciamento de alterações são tratados de forma diferente do que estão em um modelo tradicional em cascata, concentrando-se em uma série linear de etapas de migração. Este artigo descreve uma abordagem de alto nível para o gerenciamento de alterações em um esforço de migração baseado no Agile. Ao final deste artigo, você deve ter uma compreensão geral dos níveis de gerenciamento de alterações e da documentação envolvida em uma abordagem de migração incremental. Treinamentos e decisões adicionais são necessários para selecionar e implementar práticas Agile com base nesse entendimento. A intenção deste artigo é preparar os arquitetos de nuvem para uma conversa facilitada com a gerência de projetos, a fim de explicar o conceito geral do gerenciamento de alterações nessa abordagem.

## <a name="address-technical-complexity"></a>Abordar a complexidade técnica

Ao alterar qualquer sistema técnico, complexidade e interdependência, injetamos risco nos planos de projeto. As migrações para a nuvem não são exceção. Ao mover milhares&mdash;ou dezenas de milhares&mdash;de ativos para a nuvem, esses riscos são amplificados. Detectar e mapear todas as dependências em uma grande propriedade digital pode levar anos. Poucas empresas podem tolerar um ciclo de análise tão longo. Para equilibrar a necessidade de análise de arquitetura e aceleração dos negócios, o Cloud Adoption Framework se concentra em um modelo INVEST para o gerenciamento da lista de pendências do produto. As seções a seguir resumem esse tipo de modelo.

## <a name="invest-in-workloads"></a>INVEST nas cargas de trabalho

O termo _carga de trabalho_ aparece em todo o Cloud Adoption Framework. Uma carga de trabalho é uma unidade de funcionalidade de aplicativo que pode ser migrada para a nuvem. Pode ser um único aplicativo, uma camada de um aplicativo ou uma coleção de um aplicativo. A definição é flexível e pode ser alterada em várias frases da migração. O Cloud Adoption Framework usa o termo _INVEST_ para definir uma carga de trabalho.

INVEST é um acrônimo comum em muitas metodologias Agile para escrever histórias dos usuários ou itens da lista de pendências do produto, ambos os quais são unidades de saída nas ferramentas de gerenciamento de projetos Agile. A unidade mensurável de saída em uma migração é uma carga de trabalho migrada. O Cloud Adoption Framework modifica um pouco o acrônimo INVEST para criar um constructo para definir cargas de trabalho:

- **Independente:** Uma carga de trabalho não deve ter nenhuma dependência inacessível. Para que uma carga de trabalho seja considerada migrada, todas as dependências devem estar acessíveis e incluídas nos esforços de migração.
- **Negociável:** Conforme a descoberta adicional é executada, a definição de uma carga de trabalho é alterada. Os arquitetos que planejam a migração podem negociar fatores relacionados a dependências. Exemplos de pontos de negociação podem incluir o pré-lançamento de recursos, tornar recursos acessíveis em uma rede híbrida ou empacotar todas as dependências em uma única liberação.
- **Valioso:** O valor em uma carga de trabalho é medido pela capacidade de fornecer aos usuários acesso a uma carga de trabalho de produção.
- **Estimable:** As dependências, os ativos, o tempo de migração, o desempenho e os custos de nuvem devem ser estimabledos e devem ser estimados antes da migração.
- **Pequeno:** O objetivo é empacotar cargas de trabalho em um único Sprint. No entanto, isso nem sempre é viável. Em vez disso, as equipes são incentivadas a planejar os sprints e as versões a fim de minimizar o tempo necessário para mover uma carga de trabalho para a produção.
- **Teste:** Sempre deve haver um meio definido de teste ou validação da conclusão da migração de uma carga de trabalho.

Este acrônimo não se destina a servir de base para uma adesão rígida, mas deve ajudar a orientar a definição do termo _carga de trabalho_.

## <a name="migration-backlog-aligning-business-priorities-and-timing"></a>Registro posterior de migração: alinhando as prioridades de negócios e o tempo

A lista de pendências da migração permite que você controle seu portfólio de nível superior de cargas de trabalho migráveis. Antes da migração, a equipe de estratégia da nuvem e a equipe de adoção da nuvem são incentivadas a executar uma análise da [propriedade digital](../../../digital-estate/index.md) atual e a concordar com uma lista priorizada de cargas de trabalho a serem migradas. Esta lista constitui a base da lista de pendências de migração inicial.

Inicialmente, é improvável que as cargas de trabalho da lista de pendências da migração atendam aos critérios INVEST descritos na seção anterior. Em vez disso, elas servem como um agrupamento lógico de ativos de um estoque inicial como um espaço reservado para trabalhos futuros. Esses espaços reservados podem não ser tecnicamente precisos, mas servem como base para a coordenação com os negócios.

![Relação entre as listas de pendências de migração, lançamento e iteração, usadas durante o processo de migração](../../../_images/migrate/backlog-relationships.png)

*As listas de pendências posteriores de migração, lançamento e iteração controlam diferentes níveis de atividade durante os processos de migração.*

Em qualquer lista de pendências de migração, a equipe de gerenciamento de alterações deve se esforçar para obter as informações a seguir para qualquer carga de trabalho do plano. No mínimo, esses dados devem estar disponíveis para todas as cargas de trabalho priorizadas para migração nas próximas duas ou três versões.

### <a name="migration-backlog-data-points"></a>Pontos de dados da lista de pendências da migração

- **Impacto empresarial.** Compreensão do impacto empresarial de ignorar a linha do tempo esperada ou reduzir a funcionalidade durante as janelas de congelamento.
- **Prioridade empresarial relativa.** Uma lista classificada de cargas de trabalho com base nas prioridades empresariais.
- **Proprietário dos negócios.** Documenta o indivíduo responsável por tomar as decisões de negócios relacionadas a essa carga de trabalho.
- **Proprietário técnico.** Documenta o indivíduo responsável por tomar as decisões de técnicas relacionadas a essa carga de trabalho.
- **Linhas do tempo previstas.** Quando a migração está agendada para conclusão.
- **Congelamento de cargas de trabalho.** Intervalos de tempo em que a carga de trabalho deve ser inelegível para alteração.
- **Nome da carga de trabalho.**
- **Estoque inicial.** Todos os ativos necessários para fornecer a funcionalidade da carga de trabalho, incluindo VMs, dispositivos de TI, dados, aplicativos, pipelines de implantação e outros. Essas informações provavelmente serão imprecisas.

## <a name="release-backlog-aligning-business-change-and-technical-coordination"></a>Registro posterior de versões: alinhamento da mudança de negócios e coordenação técnica

No contexto de uma migração, o _lançamento_ é uma atividade que implanta uma ou mais cargas de trabalho em produção. Um lançamento geralmente abrange várias iterações ou trabalhos técnicos. No entanto, representa uma única iteração de alteração empresarial. O lançamento ocorrerá depois que uma ou mais cargas de trabalho forem preparadas para promoção à produção. A decisão de empacotar um lançamento é feita quando as cargas de trabalho migradas representam um valor empresarial suficiente para justificar a injeção de alterações em um ambiente empresarial. As liberações são executadas em conjunto com um [plano de mudança empresarial](../optimize/business-change-plan.md), após a conclusão dos [testes empresariais](../optimize/business-test.md). A equipe de estratégia da nuvem é responsável por planejar e supervisionar a execução de uma versão para garantir que a alteração empresarial desejada seja liberada.

Uma *lista de pendências de lançamento* é o plano de estado futuro que define um lançamento futuro. A lista de pendências de lançamento é o ponto dinâmico entre o gerenciamento de alterações empresariais (*lista de pendências da migração*) e o gerenciamento de alterações técnicas (*lista de pendências do sprint*). Uma lista de pendências de lançamento consiste em uma lista de cargas de trabalho da lista de pendências da migração que se alinham a um subconjunto específico de realização de resultados empresariais. A definição e o envio de uma lista de pendências de versão para a equipe de adoção da nuvem servem como gatilho para uma análise mais profunda e um planejamento de migração. Depois que a equipe de adoção da nuvem tiver verificado os detalhes técnicos associados a uma versão, ela poderá optar por confirmar a versão, estabelecendo uma linha do tempo de versão com base nos conhecimentos atuais.

Considerando o grau de análise necessário para validar uma versão, a equipe de estratégia da nuvem deve manter uma lista em execução das próximas duas a quatro versões. A equipe também deve tentar validar o máximo possível das informações a seguir, antes de definir e enviar um lançamento. Uma equipe de estratégia de nuvem disciplinada, capaz de manter as próximas quatro versões, pode aumentar significativamente a consistência e a precisão das estimativas de linha do tempo da versão.

### <a name="release-backlog-data-points"></a>Pontos de dados da lista de pendências de lançamento

Uma parceria entre a equipe de estratégia da nuvem e a equipe de adoção da nuvem colabora para adicionar os seguintes pontos de dados para todas as cargas de trabalho da lista de pendências da versão:

- **Estoque refinado.** Validação dos ativos necessários a serem migrados. Geralmente validados por meio de dados de log ou monitoramento no nível do host, da rede ou do sistema operacional para garantir uma compreensão precisa das dependências de rede e de hardware de cada ativo sob a carga padrão.
- **Padrões de uso.** Uma compreensão dos padrões de uso dos usuários finais. Esses padrões geralmente incluem uma análise da distribuição geográfica do usuário final, das rotas de rede, dos picos de uso sazonal, do picos de uso diário/por hora e da composição do usuário final (intervalo vs. externo).
- **Expectativas de desempenho.** Análise de dados de log disponíveis capturando taxa de transferência, exibições de página, rotas de rede e outros dados de desempenho necessários para replicar a experiência do usuário final.
- **Dependências.** Análise do tráfego de rede e padrões de uso do aplicativo para identificar eventuais dependências de carga de trabalho adicionais, que devem ser fatoradas em sequenciamento e preparação do ambiente. Não inclua uma carga de trabalho em um lançamento até que um dos critérios a seguir possa ser atendido:
  - Todas as cargas de trabalho dependentes foram migradas.
  - As configurações de rede e segurança foram implementadas para permitir que a carga de trabalho acesse todas as dependências em alinhamento com as expectativas de desempenho existentes.
- **Abordagem de migração desejada.** No nível da lista de pendências da migração, o esforço de migração assumido é a única consideração usada na análise. Por exemplo, se o resultado empresarial for uma saída de um datacenter existente, todas as migrações serão consideradas um cenário de novo host na lista de pendências de migração. Na lista de pendências da versão, a equipe de estratégia da nuvem e a equipe de adoção da nuvem devem avaliar o valor de longo prazo de recursos adicionais, modernização e investimentos no desenvolvimento contínuo para avaliar se uma abordagem mais moderna deve ser adotada.
- **Critérios de testes empresariais.** Depois que uma carga de trabalho é adicionada à lista de pendências da migração, os critérios de teste devem ser acordados mutuamente. Em alguns casos, os critérios de teste podem ser limitados a um teste de desempenho com um grupo de usuários avançados definido. No entanto, para validação estatística, um teste de desempenho automatizado é desejável e deve ser incluído. A instância existente do aplicativo geralmente não tem recursos de testes automatizados. Se isso se mostrar preciso, não será incomum que os arquitetos de nuvem trabalhem com usuários avançados para criar um teste de carga de linha de base em relação à solução existente a fim de estabelecer um parâmetro de comparação a ser usado durante a migração.

### <a name="release-backlog-cadence"></a>Cadência da lista de pendências de lançamento

Nas migrações maduras, as liberações ocorrem em uma cadência regular. A velocidade da equipe de adoção da nuvem costuma ser normalizada, produzindo uma versão a cada duas a quatro iterações (aproximadamente a cada um ou dois meses). No entanto, isso deve ser um resultado orgânico. A criação de cadências de versão artificial pode afetar negativamente a capacidade da equipe de adoção da nuvem de obter uma taxa de transferência consistente.

Para estabilizar o impacto empresarial, a equipe de estratégia da nuvem deve estabelecer um processo de versão mensal com a empresa a fim de manter um diálogo regular, mas também deve estabelecer a expectativa de que isso ocorra vários meses antes que uma cadência de versão regular possa ser prevista.

## <a name="sprint-or-iteration-backlog-aligning-technical-change-and-effort"></a>Pendências de Sprint ou iteração: alinhando o esforço e a alteração técnica

Um *sprint* ou uma *iteração* é uma unidade de trabalho consistente e com limite de tempo. No processo de migração, isso geralmente é medido em incrementos de duas semanas. No entanto, não é desconhecido ter iterações de uma semana ou de quatro semanas. A criação de iterações com limite de tempo força intervalos consistentes de conclusão de esforços e permite ajustes mais frequentes aos planos, com base nos novos aprendizados. Durante qualquer sprint específico, geralmente há tarefas para a avaliação, a migração e a otimização de cargas de trabalho definidas na lista de pendências de migração. Essas unidades de trabalho devem ser controladas e gerenciadas na mesma ferramenta de gerenciamento de projeto que as lista de pendências de migração e de lançamento, para gerar consistência em cada nível de gerenciamento de alterações.

Uma *lista de pendências de sprint* ou uma *lista de pendências de iteração* consiste no trabalho técnico a ser concluído em um único sprint ou iteração, lidando com a migração de ativos individuais. Esse trabalho deve ser derivado da lista de cargas de trabalho que estão sendo migradas. Ao usar ferramentas como o Azure DevOps (antigo Visual Studio Online) para o gerenciamento de projetos, os itens de trabalho de um sprint eram filhos dos itens da lista de pendências do produto em uma lista de pendências de lançamento e blocos de trabalho agile em uma lista de pendências de migração. Essa relação pai-filho permite a clareza em todos os níveis de gerenciamento de alterações.

Dentro de um único sprint ou uma única iteração, a equipe de adoção da nuvem trabalharia para fornecer a quantidade acordada de trabalho técnico, conduzindo no sentido da migração de uma carga de trabalho definida. Esse é o resultado final da estratégia de gerenciamento de alterações. Quando concluídos, esses esforços podem ser testados validando a preparação para a produção de uma carga de trabalho pré-configurada na nuvem.

### <a name="large-or-complex-sprint-structures"></a>Estruturas de sprint grandes ou complexas

Para uma migração pequena, com uma equipe de migração independente, um único sprint pode incluir todas as quatro fases da migração de uma carga de trabalho única (*avaliar*, *migrar*, *otimizar* e *proteger e gerenciar*). Com mais frequência, cada um desses processos é compartilhado por várias equipes em diferentes itens de trabalho, distribuídos entre vários sprints. Dependendo do tipo de esforço, da escala de esforço e das funções, esses sprints podem assumir algumas formas diferentes.

- **Fábrica de migração.** As migrações em larga escala, às vezes, exigem uma abordagem que se assemelha a uma fábrica no modelo de execução. Nesse modelo, várias equipes são alocadas para a execução de um processo (ou subconjunto de processo) de migração específico. Após a conclusão, a saída do sprint de uma equipe popula a lista de pendências da próxima equipe. Essa é uma abordagem eficiente para migrações de novo host em grande escala de várias cargas de trabalho em potencial envolvendo milhares de máquinas virtuais que passam pelas fases de avaliação, arquitetura, remediação e migração. No entanto, para que essa abordagem funcione, é necessário um novo ambiente homogêneo com processos simplificados de aprovação e gerenciamento de alterações.
- **Ondas de migração.** Outra abordagem que funciona bem para migrações de grande porte é o modelo de onda. Nesse modelo, a divisão de trabalho não é tão clara. As equipes se dedicam à execução do processo de migração para cargas de trabalho individuais. No entanto, a natureza de cada sprint é alterada. Em um sprint, a equipe pode concluir a avaliação e o trabalho de arquitetura. Em outro sprint, ela pode concluir o trabalho de migração. Em outro sprint ainda, o foco pode ser a otimização e o lançamento em produção. Essa abordagem permite que uma equipe principal fique alinhada às cargas de trabalho, enxergando-as por meio do processo como um todo. Ao adotar essa abordagem, a diversidade de habilidades exigidas e a alternância de contextos pode reduzir o potencial de velocidade da equipe, desacelerando o esforço de migração. Além disso, os obstáculos durante os ciclos de aprovação podem causar atrasos significativos. É importante manter opções na lista de pendências de lançamento que mantenham a equipe em ação mesmo durante períodos de bloqueio, com esse modelo. Também é importante fazer um treinamento entre os membros da equipe e garantir que os conjuntos de habilidades se alinhem com o tema de cada Sprint.

### <a name="sprint-backlog-data-points"></a>Pontos de dados da lista de pendências do sprint

O resultado de um sprint captura e documenta as alterações feitas em uma carga de trabalho, fechando assim o loop de gerenciamento de alterações. Quando concluído, pelo menos o seguinte deve ser documentado. Durante a execução de um sprint, esta documentação deve ser concluída em conjunto com os itens de trabalho técnicos.

- **Ativos implantados.** Todos os ativos implantados na nuvem para hospedar a carga de trabalho.
- **Remediação.** Toda alteração feita nos ativos a fim de se prepará-los para a migração na nuvem.
- **Configuração.** Configuração escolhida de qualquer ativo implantado, incluindo referências a scripts de configuração.
- **Modelo de implantação.** Abordagem usada para implantar o ativo na nuvem, incluindo referências a qualquer script ou ferramenta de implantação.
- **Arquitetura.** Documentação da arquitetura implantada na nuvem.
- **Métricas de desempenho.** Saída de teste automatizado ou teste empresarial realizado para validar o desempenho no momento da implantação.
- **Requisitos ou configuração exclusivos.** Todos os aspectos exclusivos da implantação, da configuração ou dos requisitos técnicos necessários para operar a carga de trabalho.
- **Aprovação operacional.** Aprovação da validação da preparação operacional do proprietário do aplicativo e da equipe de operações de TI responsável pelo gerenciamento da carga de trabalho após a implantação.
- **Aprovação da arquitetura.** Aprovação do proprietário da carga de trabalho e da equipe de adoção da nuvem para validar toda alteração de arquitetura necessária para hospedar cada ativo.

## <a name="next-steps"></a>Próximas etapas

Depois que as abordagens de gerenciamento de alterações tiverem sido estabelecidas, é hora de abordar o pré-requisito final, a [análise da lista de pendências de migração](./migration-backlog-review.md)

> [!div class="nextstepaction"]
> [Análise da lista de pendências de migração](./migration-backlog-review.md)
