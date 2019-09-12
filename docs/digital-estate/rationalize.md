---
title: Racionalizar a propriedade digital
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Avalie os ativos digitais para determinar a melhor maneira de hospedá-los na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: 7bb9eb697beb44aa5bf4e9eec736a5be4b575eb7
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829248"
---
# <a name="rationalize-the-digital-estate"></a>Racionalizar a propriedade digital

A racionalização de nuvem é o processo de avaliação de ativos para determinar a melhor abordagem para hospedá-los na nuvem. Depois de determinar uma [abordagem](approach.md) e agregar um [inventário](inventory.md), a racionalização de nuvem pode começar. A racionalização de [nuvem](rationalize.md) aborda as opções de racionalização mais comuns.

## <a name="traditional-view-of-rationalization"></a>Visão tradicional de racionalização

É fácil entender a racionalização ao visualizar o processo tradicional de racionalização como uma árvore de decisão complexa. Cada ativo no estado digital é alimentado por meio de um processo que resulta em uma das cinco respostas (as cinco RS). Para propriedades pequenas, esse processo funciona bem. Para os bens maiores, ele é ineficiente e pode levar a atrasos significativos. Vamos examinar o processo para ver o motivo. Em seguida, apresentaremos um modelo mais eficiente.

**Levantamento** Um inventário completo de ativos, incluindo aplicativos, software, hardware, sistemas operacionais e métricas de desempenho do sistema, é necessário para concluir uma racionalização completa usando modelos tradicionais.

**Análise quantitativa:** Na árvore de decisão, perguntas quantitativas geram a primeira camada de decisões. As perguntas comuns incluem o seguinte: O ativo está sendo usado atualmente? Nesse caso, ele está otimizado e dimensionado corretamente? Quais dependências existem entre os ativos? Essas perguntas são essenciais para a classificação do inventário.

**Análise qualitativa:** O próximo conjunto de decisões requer inteligência humana na forma de análise qualitativa. Muitas vezes, as perguntas que aparecem aqui são exclusivas para a solução e só podem ser respondidas por participantes de negócios e usuários avançados. Essas decisões normalmente atrasam o processo, reduzindo as coisas consideravelmente. Essa análise geralmente consome 40 a 80 horas de FTE por aplicativo.

Para obter diretrizes sobre como criar uma lista de perguntas qualitativas de análise, consulte [abordagens para planejamento de imóveis digital](approach.md).

**Decisão de racionalização:** Nas mãos de uma equipe experiente de racionalização, os dados qualitativos e quantitativos criam decisões claras. Infelizmente, as equipes com alto grau de experiência em racionalização são caras de se contratar ou precisam de meses de treinamento.

## <a name="rationalization-at-enterprise-scale"></a>Racionalização em escala empresarial

Se esse esforço for demorado e desanimador para um imóvel digital de 50 VMS, imagine o esforço necessário para impulsionar a transformação de negócios em um ambiente com milhares de VMs e centenas de aplicativos. O esforço humano necessário pode exceder facilmente 1.500 de horas FTE e nove meses de planejamento.

Embora a racionalização completa seja o estado final e uma ótima direção para se mover, raramente produz um alto ROI (retorno sobre o investimento) em relação ao tempo e à energia necessários.

Quando a racionalização é essencial para decisões financeiras, vale a pena considerar uma organização de serviços profissionais especializada em lógica de nuvem para acelerar o processo. Mesmo assim, a racionalização completa pode ser um esforço dispendioso e demorado que atrasa a transformação ou os resultados de negócios.

O restante deste artigo descreve uma abordagem alternativa, conhecida como racionalização incremental.

## <a name="incremental-rationalization"></a>Racionalização incremental

A racionalização completa de um grande espaço digital está sujeita a riscos e pode sofrer atrasos devido à sua complexidade. A suposição por trás da abordagem incremental é que as decisões atrasadas escalonam a carga na empresa para reduzir o risco de obstáculos. Ao longo do tempo, essa abordagem cria um modelo orgânica para desenvolver os processos e a experiência necessária para tornar as decisões de racionalização qualificadas com mais eficiência.

### <a name="inventory-reduce-discovery-data-points"></a>Inventário: Reduzir pontos de dados de descoberta

Poucas organizações investem no tempo, na energia e nas despesas na manutenção de um inventário preciso em tempo real do espaço digital completo. Perda, roubo, ciclos de atualização e integração de funcionários geralmente justificam o acompanhamento detalhado de ativos de dispositivos do usuário final. No entanto, o ROI de manter um inventário de aplicativos e de servidor preciso em um datacenter local tradicional geralmente é baixo. A maioria das organizações de TI têm outros problemas mais urgentes do que acompanhar o uso de ativos fixos em um data center.

Em uma transformação de nuvem, o inventário se correlaciona diretamente com os custos operacionais. São necessários dados de inventário precisos para o planejamento adequado. Infelizmente, as opções atuais de verificação ambiental podem atrasar as decisões em semanas ou meses. Felizmente, alguns truques podem acelerar a coleta de dados.

A verificação baseada em agente é o atraso citado com mais frequência. Os dados robustos necessários para uma racionalização tradicional geralmente podem ser coletados apenas com um agente em execução em cada ativo. Essa dependência nos agentes geralmente reduz o progresso, pois pode exigir comentários de segurança, operações e funções de administração.

Em um processo de racionalização incremental, uma solução sem agente pode ser usada para uma descoberta inicial para acelerar as decisões iniciais. Dependendo do nível de complexidade no ambiente, uma solução baseada em agente ainda pode ser necessária. No entanto, ele pode ser removido do caminho crítico para a alteração comercial.

### <a name="quantitative-analysis-streamline-decisions"></a>Análise quantitativa: Decisões simplificadas

Independentemente da abordagem para a descoberta de inventário, a análise quantitativa pode impulsionar as decisões e suposições iniciais. Isso é verdade principalmente ao tentar identificar a primeira carga de trabalho ou quando o objetivo da racionalização é uma comparação geral de custos. Em um processo de racionalização incremental, a equipe de estratégia de nuvem e as equipes de adoção de nuvem limitam os [cinco RS de racionalização](5-rs-of-rationalization.md) a duas decisões concisas e aplicam apenas esses fatores quantitativos. Isso simplifica a análise e reduz a quantidade de dados iniciais necessários para a alteração da unidade.

Por exemplo, se uma organização estiver no meio de uma migração de IaaS para a nuvem, você poderá assumir que a maioria das cargas de trabalho será desativada ou rehospedada.

### <a name="qualitative-analysis-temporary-assumptions"></a>Análise qualitativa: Suposições temporárias

Ao reduzir o número de resultados possíveis, fica mais fácil chegar a uma decisão inicial sobre o estado futuro de um ativo. Ao reduzir as opções, você também reduz o número de perguntas feitas pela empresa neste estágio inicial.

Por exemplo, se as opções estiverem limitadas à rehospedagem ou desativação, a empresa precisa responder apenas a uma pergunta durante a lógica inicial, que é o fato de desativar o ativo.

"A análise sugere que nenhum usuário está usando ativamente esse ativo. Essa é a precisão, ou você tem ignorado algo? " Essa pergunta binária normalmente é muito mais fácil de executar por meio da análise qualitativa.

Essa abordagem simplificada produz linhas de base, planos financeiros, estratégia e orientações. Em atividades posteriores, cada ativo passa por mais racionalização e análise qualitativa para avaliar outras opções. Todas as suposições que você faz nessa racionalização inicial são testadas antes

## <a name="challenge-assumptions"></a>Suposições de desafio

O resultado da seção anterior é uma racionalização aproximada que está cheia de suposições. A seguir, vamos desafiar algumas dessas suposições.

### <a name="retire-assets"></a>Desativar ativos

Em um ambiente local tradicional, hospedar ativos pequenos e não usados raramente causa um impacto significativo nos custos anuais. Com algumas exceções, o esforço de FTE necessário para analisar e desativar o ativo real supera a economia de custos com a remoção e a desativação desses ativos.

No entanto, quando você passa para um modelo de contabilidade de nuvem, a desativação de ativos pode produzir uma economia significativa nos custos operacionais anuais e nos esforços de migração antecipada.

Não é incomum que as organizações desativem 20% ou mais de seu espaço digital depois de concluir uma análise quantitativa. É recomendável fazer análises mais qualitativas antes de decidir sobre tal ação. Após a confirmação, a desativação desses ativos pode produzir a primeira vitória de ROI na migração na nuvem. Em muitos casos, trata-se de um dos maiores fatores de economia de custos. Como tal, recomendamos que a equipe de estratégia de nuvem supervisionasse a validação e a desativação dos ativos, em paralelo com a fase de compilação do processo de migração, para permitir um ganho financeiro inicial.

### <a name="program-adjustments"></a>Ajustes do programa

Uma empresa raramente embarca em apenas uma jornada de transformação. A escolha entre redução de custos, crescimento no mercado e novos fluxos de receita raramente é binária. Como tal, recomendamos que a equipe de estratégia de nuvem trabalhe com ela para identificar ativos em esforços de transformação paralelos que estão fora do escopo da jornada de transformação principal.

No exemplo de migração de IaaS fornecido neste artigo:

- Peça à equipe do DevOps para identificar os ativos que já fazem parte de uma automação de implantação e remover esses ativos do plano de migração principal.

- Peça às equipes de dados e de pesquisa e desenvolvimento para identificar ativos que estão viabilizando novos fluxos de receita e remova-os do plano de migração principal.

Esta análise qualitativa com foco no programa pode ser executada rapidamente e cria o alinhamento entre várias pendências de migração.

Talvez você ainda precise considerar alguns ativos como hospedar novamente os ativos por um tempo. Você pode fase em lógica posterior após a migração inicial.

## <a name="select-the-first-workload"></a>Selecione a primeira carga de trabalho

A implementação da primeira carga de trabalho é a chave para testes e aprendizado. É a primeira oportunidade de demonstrar e criar uma mentalidade de crescimento.

### <a name="business-criteria"></a>Critérios comerciais

Para garantir a transparência dos negócios, identifique uma carga de trabalho que tenha suporte de um membro da unidade de negócios da equipe de estratégia de nuvem. Preferivelmente, escolha um em que a equipe tenha um jogo de benefício e uma motivação forte para mudar para a nuvem.

### <a name="technical-criteria"></a>Critérios técnicos

Selecione uma carga de trabalho que tenha dependências mínimas e que possa ser migrada como um pequeno grupo de ativos. Recomendamos que você selecione uma carga de trabalho com um caminho de teste definido para facilitar a validação.

A primeira carga de trabalho é normalmente implantada em um ambiente experimental sem capacidade de governança ou operacional. É importante selecionar uma carga de trabalho que não interaja com dados seguros.

### <a name="qualitative-analysis"></a>Análise qualitativa

As equipes de adoção de nuvem e a equipe de estratégia de nuvem podem trabalhar em conjunto para analisar essa carga de trabalho pequena. Essa colaboração cria uma oportunidade controlada para criar e testar critérios de análise qualitativas. A população menor cria uma oportunidade para pesquisar os usuários afetados e para concluir uma análise qualitativa detalhada em uma semana ou menos. Para fatores de análise qualitativas comuns, consulte o destino de lógica específica no [5 RS de racionalização](5-rs-of-rationalization.md).

### <a name="migration"></a>Migração

Em paralelo com a racionalização contínua, a equipe de adoção de nuvem pode começar a migrar a carga de trabalho pequena para expandir o aprendizado nas seguintes áreas principais:

- Melhorar habilidades com a plataforma do provedor de nuvem.
- Defina os serviços principais (e os padrões do Azure) necessários para ajustar a visão em longo prazo.
- Entenda melhor como as operações podem precisar ser alteradas posteriormente na transformação.
- Entender os riscos inerentes aos negócios e a tolerância dos negócios em relação a esses riscos.
- Estabeleça uma linha de base ou um MVP (produto viável mínimo) para governança baseada na tolerância de risco empresarial.

## <a name="release-planning"></a>Planejamento de liberação

Embora a equipe de adoção de nuvem esteja executando a migração ou implementação da primeira carga de trabalho, a equipe de estratégia de nuvem pode começar a priorizar os aplicativos e as cargas de trabalho restantes.

### <a name="power-of-10"></a>Potência de 10

A abordagem tradicional para a racionalização tenta atender a todas as necessidades previstas. Felizmente, nem sempre é necessário ter um plano para todos os aplicativos para iniciar uma jornada de transformação. Em um modelo incremental, a potência de 10 fornece um bom ponto de partida. Nesse modelo, a equipe de estratégia de nuvem seleciona os primeiros 10 aplicativos a serem migrados. Essas dez cargas de trabalho devem conter uma mistura de cargas de trabalho simples e complexas.

### <a name="build-the-first-backlogs"></a>Criar os primeiros registros posteriores

As equipes de adoção de nuvem e a equipe de estratégia de nuvem podem trabalhar em conjunto na análise qualitativa para as 10 primeiras cargas de trabalho. Esse esforço cria a primeira pendência de migração priorizada e a primeira pendência de liberação priorizada. Esse método permite que as equipes iterem na abordagem e forneçam tempo suficiente para criar um processo adequado para análise qualitativa.

### <a name="mature-the-process"></a>Amadureceu o processo

Depois que as duas equipes concordarem com os critérios de análise qualitativos, a avaliação poderá se tornar uma tarefa em cada iteração. Atingir o consenso sobre os critérios de avaliação geralmente requer de duas a três versões.

Depois que a avaliação foi movida para o processo de execução incremental da migração, a equipe de adoção de nuvem pode iterar mais rapidamente na avaliação e na arquitetura. Nesse estágio, a equipe de estratégia de nuvem também é abstrata, o que reduz o tempo de descarregamento. Isso também permite que a equipe de estratégia de nuvem se concentre na priorização dos aplicativos que ainda não estão em uma versão específica, o que garante um grande alinhamento com as condições de mercado em constante mudança.

Nem todos os aplicativos priorizados estarão prontos para a migração. O sequenciamento provavelmente mudará, pois a equipe faz uma análise mais profunda qualitativa e descobre eventos de negócios e dependências que podem solicitar a repriorização da pendência. Algumas versões podem agrupar um pequeno número de cargas de trabalho. Outros podem conter apenas uma única carga de trabalho.

A equipe de adoção de nuvem provavelmente executará iterações que não produzem uma migração de carga de trabalho completa. Quanto menor for a carga de trabalho e as dependências, maior a probabilidade de uma carga de trabalho se encaixar em um único sprint ou iteração. Por esse motivo, recomendamos que os primeiros aplicativos na pendência de versão sejam pequenos e contenham poucas dependências externas.

## <a name="end-state"></a>Estado final

Ao longo do tempo, a combinação da equipe de adoção da nuvem e da equipe de estratégia de nuvem concluirá uma racionalização completa do inventário. No entanto, essa abordagem incremental permite que as equipes sejam continuamente mais rápidas no processo de racionalização. Ele também ajuda a jornada de transformação a gerar resultados de negócios tangíveis mais cedo, sem o esforço de análise antecipado.

Em alguns casos, o modelo financeiro pode ser muito rígido para tomar uma decisão sem racionalização adicional. Nesses casos, talvez você precise de uma abordagem mais tradicional para a racionalização.

## <a name="next-steps"></a>Próximas etapas

A saída de um esforço de racionalização é uma lista de pendências priorizada de todos os ativos afetados pela transformação escolhida. Essa lista de pendências agora está pronta para servir como base para modelos de custo dos serviços de nuvem.

> [!div class="nextstepaction"]
> [Alinhar modelos de custo com a propriedade digital](calculate.md)
