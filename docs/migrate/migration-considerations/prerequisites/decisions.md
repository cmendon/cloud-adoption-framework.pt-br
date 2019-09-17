---
title: Decisões que afetam migrações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisões importantes a serem feitas com relação ao processo de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d1b07e5bc0dd578527e4e4c8c7271fad5fa967c9
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825374"
---
# <a name="decisions-that-affect-migrations"></a>Decisões que afetam migrações

Durante a migração, diversos fatores afetam as decisões e as atividades de execução. Este artigo explica o tema central dessas decisões e explora algumas perguntas que auxiliam nas discussões sobre os princípios de migração nesta seção de orientações da Cloud Adoption Framework.

## <a name="business-outcomes"></a>Resultados dos negócios

O objetivo ou a meta de qualquer esforço de adoção pode ter um impacto significativo sobre a abordagem sugerida para a execução.

- **Migração.** Drivers empresariais urgentes, velocidade de adoção ou economia de custos são exemplos de resultados operacionais. Esses resultados são fundamentais para os esforços que agregam valor empresarial de alterações transitivas em modelos de operações ou de TI. A seção Migrar da Cloud Adoption Framework se concentra intensamente nos resultados dos negócios voltados para a Migração.
- **Inovação de aplicativo.** Melhorar a experiência do cliente e aumentar a participação no mercado são exemplos de resultados incrementais. Os resultados derivam de uma série de alterações incrementais focadas nas necessidades e nos desejos dos clientes atuais.
- **Inovação controlada por dados.** Novos produtos ou serviços, especialmente aqueles que vêm do poder dos dados, são exemplos de resultados com interrupção. Esses resultados são provenientes de experimentação e de previsões que usam dados para interromper o status quo no mercado.

Nenhuma empresa buscaria apenas um desses resultados. Sem operações, não há clientes e vice-versa. Com a adoção da nuvem, não é diferente. Normalmente, as empresas trabalham para atingir todos esses resultados, mas tentar se concentrar em todos eles ao mesmo tempo pode pulverizar seus esforços e causar lentidão no progresso de trabalhos que poderiam beneficiar ao máximo suas necessidades empresariais.

Esse pré-requisito não é uma exigência para que você escolha uma dessas três metas, mas sim para ajudar a equipe de estratégia da nuvem e a equipe de adoção da nuvem a estabelecer um conjunto de prioridades operacionais que orientarão a execução nos próximos três a seis meses. Essas prioridades são definidas classificando cada uma das três opções da *mais significativa* para a *menos significativa*, pois elas estão relacionadas aos esforços com que as equipes podem contribuir nos próximos trimestres.

### <a name="acting-on-migration-outcomes"></a>Atuação nos resultados da migração

Se os resultados operacionais forem classificados como mais altos na lista, esta seção da Cloud Adoption Framework funcionará bem para sua equipe. Nesta seção, supõe-se que você precisa priorizar a velocidade e a economia de custos como KPIs (indicadores chave de desempenho). Nesse caso, um modelo de migração para a adoção estaria bem alinhado com os resultados. Um modelo focado na migração é muito predicado na migração de "deslocamento e mudança" de ativos de IaaS (infraestrutura como serviço) para esvaziar um datacenter e gerar economias de custos. Nesse modelo, a modernização poderá ocorrer, mas será um foco secundário até que a missão de migração principal seja realizada.

### <a name="acting-on-application-innovations"></a>Atuação em inovações de aplicativos

Se a participação de mercado e a experiência do cliente forem seus principais motivadores, talvez esta não seja a melhor seção da Cloud Adoption Framework para orientar os esforços de suas equipes. A inovação de aplicativos requer um plano que se concentre na modernização e na transição de cargas de trabalho, independentemente da infraestrutura subjacente. Nesse caso, as orientações nesta seção podem ser informativas, mas talvez não sejam a melhor abordagem para orientar as decisões principais.

### <a name="acting-on-data-innovations"></a>Atuando em inovações de dados

Se dados, experimentação, P&D (pesquisa e desenvolvimento ) ou novos produtos forem sua prioridade para os próximos seis meses, talvez esta não seja a melhor seção da Cloud Adoption Framework para orientar os esforços de suas equipes. Qualquer esforço de inovação de dados pode se beneficiar das orientações relacionadas à migração de dados de origem existentes. No entanto, o foco mais amplo desse esforço seriam a entrada e a integração de fontes de dados adicionais. Estender essas orientações com previsões e novas experiências é muito mais importante do que a migração de ativos de IaaS.

## <a name="balancing-the-portfolio"></a>Equilibrar o portfólio

Esta seção da Cloud Adoption Framework estabelece a teoria para ajudar os leitores a entenderem as diferentes abordagens para lidar com alterações em um portfólio equilibrado. O artigo sobre como [equilibrar o portfólio](../../expanded-scope/balance-the-portfolio.md) é um exemplo de escopo expandido, criado para ajudar a agir com base nessa teoria.

## <a name="effort"></a>Esforço

O esforço de migração pode variar muito dependendo do tamanho e das complexidades das cargas de trabalho envolvidas. Uma migração de carga de trabalho menor envolvendo algumas centenas de VMs (máquinas virtuais) é um processo tático, potencialmente implementado com ferramentas automatizadas, como as [Migrações para Azure](/azure/migrate/migrate-overview). Por outro lado, uma grande migração empresarial de dezenas de milhares de cargas de trabalho requer um processo altamente estratégico e pode envolver refatoração, recompilação e substituição extensivas de aplicativos existentes que integram funcionalidades de PaaS (plataforma como serviço) e SaaS (software como serviço). [Identificar e equilibrar o escopo](../../expanded-scope/balance-the-portfolio.md) de suas migrações planejadas é essencial.

Antes de tomar decisões que possam ter um impacto de longo prazo sobre o programa de migração atual, é vital que você crie consenso quanto às decisões a seguir.

### <a name="effort-type"></a>Tipo do esforço

Em qualquer migração de escala significativa (mais de 250 VMs), os ativos são migrados usando uma variedade de opções de transição, discutidas nos cinco Rs da racionalização: *Re-hospedar*, *Refatorar*, *Rearquitetar*, *Recompilar* e *Substituir* (do inglês Replace).

Algumas cargas de trabalho são modernizadas por meio de um processo de *recompilação* ou *rearquitetura*, criando aplicativos mais modernos com novos recursos e funcionalidades técnicas. Outros ativos passam por um processo de *refatoração*, por exemplo, uma mudança para contêineres ou outras abordagens mais modernas de hospedagem e operacionais que não afetam necessariamente a base de código das soluções. Normalmente, máquinas virtuais e outros ativos mais bem estabelecidos passam por um processo de *re-hospedagem*, fazendo a transição desses ativos do datacenter para a nuvem. Algumas cargas de trabalho podem ser migradas para a nuvem, mas, em vez disso, devem ser *substituídas* usando serviços de nuvem baseados em serviços (baseados em SaaS) que atendam à mesma necessidade empresariais, por exemplo, usando o Office 365 como uma alternativa para migrar instâncias do Exchange Server.

Na maioria dos cenários, algum evento empresarial cria uma função de força que faz com que um alto percentual de ativos sejam migrados temporariamente usando o processo de *re-hospedagem*, seguida por uma transição secundária mais significativa usando uma das outras estratégias de migração depois que estiverem na nuvem. Esse processo normalmente é conhecido como uma *transição de nuvem*.

Durante o processo de [racionalizar os ativos digitais](../../../digital-estate/calculate.md), esses tipos de decisões são aplicados a cada ativo a ser migrado. No entanto, o pré-requisito necessário no momento é fazer uma suposição de linha de base. Das cinco estratégias de migração, qual se alinha melhor aos objetivos empresariais ou aos resultados dos negócios que impulsionam esse esforço de migração? Essa decisão serve como uma orientação durante o esforço de migração.

### <a name="effort-scale"></a>Escala do esforço

A escala da migração é a próxima decisão de pré-requisito importante. Os processos necessários para migrar 1.000 ativos são diferentes do processo necessário para mover 10.000 ativos. Antes de começar qualquer esforço de migração, é importante responder às seguintes perguntas:

- **Quantos ativos dão suporte às cargas de trabalho de migração hoje?** Os ativos incluem estruturas de dados, aplicativos, VMs e os dispositivos de TI necessários. É recomendável escolher uma carga de trabalho relativamente pequena para seu primeiro candidato à migração.
- **Desses ativos, quantos estão planejados para a migração?** É comum que um percentual dos ativos seja encerrado durante o processo de migração, devido à falta de dependência sustentada do usuário final.
- **Quais são as estimativas de cima para baixo da escala dos ativos migráveis?** Para as cargas de trabalho incluídas para migração, estime o número de ativos de suporte, como aplicativos, máquinas virtuais, fontes de dados e dispositivos de TI. Consulte a seção sobre [ativos digitais](../../../digital-estate/index.md) da Cloud Adoption Framework para obter orientações de como identificar ativos relevantes.

### <a name="effort-timing"></a>Tempo do esforço

Geralmente, as migrações são impulsionadas por um evento empresarial atraente que é sensível ao tempo. Por exemplo, um motivador comum é o encerramento ou a renovação de um contrato de hospedagem de terceiros. Embora haja muitos possíveis eventos empresariais que demandem uma migração, eles compartilham uma semelhança: uma data de término. É importante entender o cronograma de qualquer evento empresarial que se aproxima, de modo que atividades e a velocidade possam ser planejadas e validadas corretamente.

## <a name="recap"></a>Recapitulação

Antes de continuar, documente as seguintes pressuposições e compartilhe-as com a equipe de estratégia da nuvem e a equipe de adoção da nuvem:

- Resultados dos negócios.
- Funções. Isso será documentado e refinado para os processos de migração *Avaliar*, *Migrar*, *Otimizar* e *Proteger e gerenciar*.
- Definição de concluído. Isso será documentado e refinado separadamente para os processos de migração *Avaliar*, *Migrar*, *Otimizar* e *Proteger e gerenciar*.
- Tipo do esforço.
- Escala do esforço.
- Tempo do esforço.

## <a name="next-steps"></a>Próximas etapas

Após o processo ser compreendido entre a equipe, é hora de examinar os pré-requisitos técnicos. A [lista de verificação de planejamento do ambiente de migração](./planning-checklist.md) ajuda a garantir que a base técnica esteja pronta para a migração.

Após o processo ser compreendido entre a equipe, é hora de examinar os pré-requisitos técnicos da [Lista de verificação de planejamento de migração] para ajudar a garantir que a base técnica esteja pronta para a migração.

> [!div class="nextstepaction"]
> [Examinar a lista de verificação de planejamento de migração](./planning-checklist.md)