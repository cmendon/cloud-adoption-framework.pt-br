---
title: Decisões que afetam as migrações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisões importantes a serem feitas com relação ao processo de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 01380bdd795fac0fc2740e4e41c3638a8b8d93f3
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548299"
---
# <a name="decisions-that-affect-migrations"></a>Decisões que afetam as migrações

Durante a migração, vários fatores afetam as decisões e as atividades de execução. Este artigo explica o tema central dessas decisões e explora algumas perguntas que realizam as discussões dos princípios de migração nesta seção das diretrizes da estrutura de adoção de nuvem.

## <a name="business-outcomes"></a>Resultados de negócios

O objetivo ou objetivo de qualquer esforço de adoção pode ter um impacto significativo na abordagem sugerida para a execução.

- **As.** Drivers de negócios urgentes, velocidade de adoção ou economia de custos são exemplos de resultados operacionais. Esses resultados são fundamentais para os esforços que impulsionam o valor comercial de alterações transitivas nos modelos de operações ou de ti. A seção migrar da estrutura de adoção de nuvem se concentra intensamente nos resultados de negócios voltados para a migração.
- **Inovação de aplicativos.** Melhorar a experiência do cliente e aumentar a participação no mercado são exemplos de resultados incrementais. Os resultados resultam de uma coleção de alterações incrementais focadas nas necessidades e nos desejos dos clientes atuais.
- **Inovação controlada por dados.** Os novos produtos ou serviços, especialmente aqueles que vêm do poder dos dados, são exemplos de resultados de interrupção. Esses resultados são o resultado de experimentação e previsões que usam dados para interromper o status quo no mercado.

Nenhum negócio buscaria apenas um desses resultados. Sem operações, não há clientes e vice-versa. A adoção da nuvem não é diferente. Normalmente, as empresas trabalham para atingir cada um desses resultados, mas tentar se concentrar em todos eles simultaneamente pode espalhar seus esforços muito finos e causar um progresso lento no trabalho que pode aproveitar ao máximo suas necessidades de negócios.

Esse pré-requisito não é uma demanda para que você escolha uma dessas três metas, mas em vez disso, para ajudar sua equipe de estratégia de nuvem e sua equipe de adoção de nuvem a estabelecer um conjunto de prioridades operacionais que orientarão a execução dos próximos três a seis meses. Essas prioridades são definidas por meio da classificação de cada uma das três opções discriminadas da *mais significativa* para a *menos significativa*, pois elas se relacionam com os esforços para os quais essa equipe pode contribuir nos próximos um ou dois trimestres.

### <a name="acting-on-migration-outcomes"></a>Atuando nos resultados da migração

Se os resultados operacionais forem classificados como mais altos na lista, esta seção da estrutura de adoção de nuvem funcionará bem para sua equipe. Nesta seção, supõe-se que você precisa priorizar a velocidade e a economia de custos como KPIs (indicadores chave de desempenho). nesse caso, um modelo de migração para adoção seria bem alinhado com os resultados. Um modelo com foco em migração é muito predicado à migração de "deslocamento e mudança" de ativos de IaaS (infraestrutura como serviço) para depauperam um datacenter e para produzir economias de custos. Nesse modelo, a modernização pode ocorrer, mas é um foco secundário até que a missão de migração principal seja realizada.

### <a name="acting-on-application-innovations"></a>Agindo sobre inovações de aplicativos

Se a participação no mercado e a experiência do cliente forem seus principais drivers, essa pode não ser a melhor seção da estrutura de adoção de nuvem para orientar os esforços de suas equipes. A inovação de aplicativos requer um plano que se concentre na modernização e na transição de cargas de trabalho, independentemente da infraestrutura subjacente. Nesse caso, as diretrizes nesta seção podem ser informativas, mas talvez não sejam a melhor abordagem para orientar as decisões principais.

### <a name="acting-on-data-innovations"></a>Atuando em inovações de dados

Se os dados, experimentação, pesquisa e desenvolvimento (R & D) ou novos produtos forem sua prioridade para os próximos seis meses, isso pode não ser a melhor seção da estrutura de adoção de nuvem para orientar os esforços de suas equipes. Qualquer esforço de inovação de dados pode se beneficiar das diretrizes relacionadas à migração de dados de origem existentes. No entanto, o foco mais amplo desse esforço seria a entrada e a integração de fontes de dados adicionais. Estender essa orientação com previsões e novas experiências é muito mais importante do que a migração de ativos de IaaS.

## <a name="balancing-the-portfolio"></a>Equilibrando o portfólio

Esta seção da estrutura de adoção de nuvem estabelece a teoria para ajudar os leitores a entenderem abordagens diferentes para lidar com alterações em um portfólio equilibrado. O artigo sobre [balanceamento de portfólio](../../expanded-scope/balance-the-portfolio.md) é um exemplo de escopo expandido, projetado para ajudar a agir nessa teoria.

## <a name="effort"></a>Atividade

O esforço de migração pode variar muito dependendo do tamanho e das complexidades das cargas de trabalho envolvidas. Uma migração de carga de trabalho menor que envolve algumas centenas de VMs (máquinas virtuais) é um processo tático, potencialmente implementado com ferramentas automatizadas, como [migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-overview). Por outro lado, uma grande migração empresarial de dezenas de milhares de cargas de trabalho requer um processo altamente estratégico e pode envolver refatoração extensiva, recriação e substituição de aplicativos existentes que integram a plataforma como um serviço (PaaS) e software como um recursos de serviço (SaaS). [A identificação e o balanceamento do escopo](../../expanded-scope/balance-the-portfolio.md) de suas migrações planejadas são essenciais.

Antes de tomar decisões que possam ter um impacto de longo prazo sobre o programa de migração atual, é vital que você crie consenso sobre as decisões a seguir.

### <a name="effort-type"></a>Tipo de esforço

Em qualquer migração de escalas significativas (> 250 VMs), os ativos são migrados usando uma variedade de opções de transição, discutidas em cinco RS de racionalização: *rehospedar*, *refatorar*, *rearquitetar*, *Recompilar*e *substituir*.

Algumas cargas de trabalho são modernizadas por meio de um processo de *recriação* ou *rearquitetura* , criando aplicativos mais modernos com novos recursos e recursos técnicos. Outros ativos passam por um processo de *refatoração* , por exemplo, mover para contêineres ou outras abordagens mais modernas de hospedagem e operacional que não afetam necessariamente a base de código de soluções. Normalmente, as máquinas virtuais e outros ativos que são mais bem estabelecidos passam por um processo de novo *host* , fazendo a transição desses ativos do datacenter para a nuvem. Algumas cargas de trabalho podem ser migradas para a nuvem, mas, em vez disso, devem ser *substituídas* usando serviços de nuvem baseados em serviços (baseados em SaaS) que atendem à mesma necessidade de negócios, por exemplo, usando o Office 365 como uma alternativa à migração do Exchange Server ocasiões.

Na maioria dos cenários, algum evento de negócios cria uma função de força que causa um alto percentual de ativos para migrar temporariamente usando o processo de novo *host* , seguido por uma transição secundária mais significativa usando uma das outras migrações estratégias depois que estão na nuvem. Esse processo é normalmente conhecido como uma *transição de nuvem*.

Durante o processo de [racionalizar o espaço digital](../../../digital-estate/calculate.md), esses tipos de decisões são aplicados a cada ativo para migrar. No entanto, o pré-requisito necessário no momento é fazer uma suposição de linha de base. Das cinco estratégias de migração, que melhor se alinha com os objetivos de negócios ou os resultados de negócios que levam a esse esforço de migração? Essa decisão serve como uma suposição de orientação durante o esforço de migração.

### <a name="effort-scale"></a>Escala de esforço

A escala da migração é a próxima decisão de pré-requisito importante. Os processos necessários para migrar os ativos de 1.000 são diferentes do processo necessário para mover os ativos de 10.000. Antes de começar qualquer esforço de migração, é importante responder às seguintes perguntas:

- **Quantos ativos dão suporte às cargas de trabalho de migração hoje?** Os ativos incluem estruturas de dados, aplicativos, VMs e dispositivos de ti necessários. É recomendável que você escolha uma carga de trabalho relativamente pequena para seu primeiro candidato de migração.
- **Desses ativos, quantos estão planejados para a migração?** É comum que um percentual de ativos seja encerrado durante um processo de migração, devido à falta de dependência de usuário final sustentada.
- **Quais são as estimativas de cima para baixo da escala de ativos do migrada?** Para as cargas de trabalho incluídas para migração, estime o número de ativos de suporte, como aplicativos, máquinas virtuais, fontes de dados e dispositivos de ti. Consulte a seção [espaço digital](../../../digital-estate/index.md) da estrutura de adoção de nuvem para obter orientação sobre como identificar ativos relevantes.

### <a name="effort-timing"></a>Tempo de esforço

Geralmente, as migrações são orientadas por um evento de negócios atraente que é sensível ao tempo. Por exemplo, um driver comum é o encerramento ou a renovação de um contrato de Hospedagem de terceiros. Embora haja muitos eventos de negócios em potencial que exijam uma migração, eles estão compartilhando uma semelhança: uma data de término. É importante entender o tempo de qualquer abordagem de eventos de negócios, de modo que atividades e a velocidade podem ser planejadas e validadas corretamente.

## <a name="recap"></a>Capitula

Antes de continuar, documente as seguintes suposições e compartilhe-as com a equipe de estratégia de nuvem e com as equipes de adoção de nuvem:

- Resultados de negócios.
- Papéis. Isso será documentado e refinado para os processos *avaliar*, *migrar*, *otimizar*e *proteger e gerenciar* a migração.
- Definição de concluída. Isso será documentado e refinado separadamente para os processos de *avaliação avaliar*, *migrar*, *otimizar*e *proteger e gerenciar* .
- Tipo de esforço.
- Escala de esforço.
- Tempo de esforço.

## <a name="next-steps"></a>Próximos passos

Depois que o processo é compreendido entre a equipe, é hora de revisar os pré-requisitos técnicos. A [lista de verificação de planejamento do ambiente de migração](./planning-checklist.md) ajuda a garantir que a base técnica esteja pronta para a migração.

Depois que o processo for compreendido entre a equipe, seu tempo para revisar os pré-requisitos técnicos da [lista de verificação de planejamento de migração] ajudará a garantir que a base técnica esteja pronta para a migração.

> [!div class="nextstepaction"]
> [Examinar a lista de verificação de planejamento de migração](./planning-checklist.md)
