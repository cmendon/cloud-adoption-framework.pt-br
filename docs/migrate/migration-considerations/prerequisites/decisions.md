---
title: Decisões que afetam a migração
description: Decisões importantes a serem feitas sobre o processo de migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3281f7a14c5af58e435be9e3a412fc5285da1b47
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78225474"
---
<!-- cSpell:ignore migrateable -->

# <a name="decisions-that-affect-migration"></a>Decisões que afetam a migração

Durante a migração, diversos fatores afetam as decisões e as atividades de execução. Este artigo explica o tema central dessas decisões e explora algumas perguntas que auxiliam nas discussões sobre os princípios de migração nesta seção de orientações da Cloud Adoption Framework.

## <a name="business-outcomes"></a>Resultados dos negócios

O objetivo ou a meta de qualquer esforço de adoção pode ter um impacto significativo sobre a abordagem sugerida para a execução.

- **Migração.** Drivers empresariais urgentes, velocidade de adoção ou economia de custos são exemplos de resultados operacionais. Esses resultados são fundamentais para os esforços que agregam valor empresarial de alterações transitivas em modelos de operações ou de TI. A seção Migrar da Cloud Adoption Framework se concentra intensamente nos resultados dos negócios voltados para a Migração.
- **Inovação de aplicativo.** Melhorar a experiência do cliente e aumentar a participação no mercado são exemplos de resultados incrementais. Os resultados derivam de uma série de alterações incrementais focadas nas necessidades e nos desejos dos clientes atuais.
- **Inovação conduzida por dados.** Novos produtos ou serviços, especialmente aqueles que vêm do poder dos dados, são exemplos de resultados de interrupção. Esses resultados são provenientes de experimentação e de previsões que usam dados para interromper o status quo no mercado.

Nenhuma empresa buscaria apenas um desses resultados. Sem operações, não há clientes e vice-versa. Com a adoção da nuvem, não é diferente. Normalmente, as empresas trabalham para atingir todos esses resultados, mas tentar se concentrar em todos eles ao mesmo tempo pode pulverizar seus esforços e causar lentidão no progresso de trabalhos que poderiam beneficiar ao máximo suas necessidades empresariais.

Esse pré-requisito não é uma exigência para que você escolha uma dessas três metas, mas sim para ajudar a equipe de estratégia da nuvem e a equipe de adoção da nuvem a estabelecer um conjunto de prioridades operacionais que orientarão a execução nos próximos três a seis meses. Essas prioridades são definidas classificando cada uma das três opções da *mais significativa* para a *menos significativa*, pois elas estão relacionadas aos esforços com que as equipes podem contribuir nos próximos trimestres.

### <a name="act-on-migration-outcomes"></a>Agir em resultados de migração

Se os resultados operacionais forem classificados como mais altos na lista, esta seção da estrutura de adoção de nuvem se adequará bem à sua equipe. Nesta seção, supõe-se que você precisa priorizar a velocidade e a economia de custos como KPIs (indicadores chave de desempenho). Nesse caso, um modelo de migração para a adoção estaria bem alinhado com os resultados. Um modelo com foco em migração é muito predicado na migração de deslocamento e mudança de ativos de IaaS (infraestrutura como serviço) para depauperam um datacenter e para produzir economias de custos. Nesse modelo, a modernização poderá ocorrer, mas será um foco secundário até que a missão de migração principal seja realizada.

### <a name="act-on-application-innovations"></a>Aja em inovações de aplicativos

Se a participação no mercado e a experiência do cliente forem seus principais drivers, esta seção poderá não ser a melhor seção da estrutura de adoção de nuvem para orientar os esforços de suas equipes. A inovação de aplicativos requer um plano que se concentre na modernização e na transição de cargas de trabalho, independentemente da infraestrutura subjacente. Nesse caso, as orientações nesta seção podem ser informativas, mas talvez não sejam a melhor abordagem para orientar as decisões principais.

### <a name="act-on-data-innovations"></a>Aja em inovações de dados

Se os dados, experimentação, pesquisa e desenvolvimento (R & D) ou novos produtos forem sua prioridade para os próximos seis meses ou mais, esta seção poderá não ser a melhor seção da estrutura de adoção de nuvem para orientar os esforços de suas equipes. Qualquer esforço de inovação de dados pode se beneficiar das orientações relacionadas à migração de dados de origem existentes. No entanto, o foco mais amplo desse esforço seriam a entrada e a integração de fontes de dados adicionais. Estender essas orientações com previsões e novas experiências é muito mais importante do que a migração de ativos de IaaS.

## <a name="effort"></a>Esforço

O esforço de migração pode variar muito dependendo do tamanho e das complexidades das cargas de trabalho envolvidas. Uma migração de carga de trabalho menor envolvendo algumas centenas de VMs (máquinas virtuais) é um processo tático, potencialmente implementado com ferramentas automatizadas, como as [Migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-overview). Por outro lado, uma grande migração empresarial de dezenas de milhares de cargas de trabalho requer um processo altamente estratégico e pode envolver refatoração, recompilação e substituição extensivas de aplicativos existentes que integram funcionalidades de PaaS (plataforma como serviço) e SaaS (software como serviço). [Identificar e equilibrar o escopo](../../../strategy/balance-the-portfolio.md) de suas migrações planejadas é essencial.

Antes de tomar decisões que possam ter um impacto de longo prazo sobre o programa de migração atual, é vital que você crie consenso quanto às decisões a seguir.

### <a name="effort-type"></a>Tipo do esforço

Em qualquer migração de escala significativa (mais de 250 VMs), os ativos são migrados usando uma variedade de opções de transição, discutidas em cinco RS de racionalização: *rehospedar*, *refatorar*, *rearquitetar*, *Recompilar*e *substituir*.

Algumas cargas de trabalho são modernizadas por meio de um processo de *recompilação* ou *rearquitetura*, criando aplicativos mais modernos com novos recursos e funcionalidades técnicas. Outros ativos passam por um processo de *refatoração*, por exemplo, uma mudança para contêineres ou outras abordagens mais modernas de hospedagem e operacionais que não afetam necessariamente a base de código das soluções. Normalmente, as máquinas virtuais e outros ativos mais bem estabelecidos passam por um processo de novo *host* , fazendo a transição desses ativos do datacenter para a nuvem. Algumas cargas de trabalho podem ser migradas para a nuvem, mas, em vez disso, devem ser *substituídas* usando serviços de nuvem baseados em serviços (baseados em SaaS) que atendem à mesma necessidade de negócios&mdash;por exemplo, usando o Office 365 como uma alternativa para migrar instâncias do Exchange Server.

Na maioria dos cenários, algum evento empresarial cria uma função de força que faz com que um alto percentual de ativos sejam migrados temporariamente usando o processo de *re-hospedagem*, seguida por uma transição secundária mais significativa usando uma das outras estratégias de migração depois que estiverem na nuvem. Esse processo normalmente é conhecido como uma *transição de nuvem*.

Durante o processo de [racionalizar os ativos digitais](../../../digital-estate/calculate.md), esses tipos de decisões são aplicados a cada ativo a ser migrado. No entanto, o pré-requisito necessário no momento é fazer uma suposição de linha de base. Das cinco estratégias de migração, qual se alinha melhor aos objetivos empresariais ou aos resultados dos negócios que impulsionam esse esforço de migração? Essa decisão serve como uma orientação durante o esforço de migração.

### <a name="effort-scale"></a>Escala do esforço

A escala da migração é a próxima decisão de pré-requisito importante. Os processos necessários para migrar os ativos 1.000 são diferentes dos processos necessários para mover os ativos de 10.000. Antes de começar qualquer esforço de migração, é importante responder às seguintes perguntas:

- **Quantos ativos dão suporte às cargas de trabalho de migração hoje?** Os ativos incluem estruturas de dados, aplicativos, VMs e os dispositivos de TI necessários. É recomendável escolher uma carga de trabalho relativamente pequena para seu primeiro candidato à migração.
- **Desses ativos, quantos estão planejados para a migração?** É comum que um percentual dos ativos seja encerrado durante o processo de migração, devido à falta de dependência sustentada do usuário final.
- **Quais são as estimativas de cima para baixo da escala de ativos que podem ser migrados?** Para as cargas de trabalho incluídas para migração, estime o número de ativos de suporte, como aplicativos, máquinas virtuais, fontes de dados e dispositivos de TI. Consulte a seção sobre [ativos digitais](../../../digital-estate/index.md) da Cloud Adoption Framework para obter orientações de como identificar ativos relevantes.

### <a name="effort-timing"></a>Tempo do esforço

Geralmente, as migrações são impulsionadas por um evento empresarial atraente que é sensível ao tempo. Por exemplo, um motivador comum é o encerramento ou a renovação de um contrato de hospedagem de terceiros. Embora existam muitos eventos de negócios em potencial que exigem uma migração, eles compartilham um fator comum: uma data de término. É importante entender o cronograma de qualquer evento empresarial que se aproxima, de modo que atividades e a velocidade possam ser planejadas e validadas corretamente.

## <a name="recap"></a>Recapitulação

Antes de continuar, documente as seguintes pressuposições e compartilhe-as com a equipe de estratégia da nuvem e a equipe de adoção da nuvem:

- Resultados dos negócios.
- Funções, documentadas e refinadas para *avaliar*, *migrar*, *otimizar*e *proteger* os processos de migração.
- Definição de concluído, documentado e refinado separadamente para os processos de *avaliação avaliar*, *migrar*, *otimizar*e *proteger e gerenciar* .
- Tipo do esforço.
- Escala do esforço.
- Tempo do esforço.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Depois que o processo é compreendido entre a equipe, é hora de revisar os pré-requisitos técnicos. A [lista de verificação de planejamento do ambiente de migração](./planning-checklist.md) ajuda a garantir que a base técnica esteja pronta para a migração.

Depois que o processo for compreendido entre a equipe, seu tempo para revisar os pré-requisitos técnicos da [lista de verificação de planejamento de migração] ajudará a garantir que a base técnica esteja pronta para a migração.

> [!div class="nextstepaction"]
> [Examinar a lista de verificação de planejamento de migração](./planning-checklist.md)
