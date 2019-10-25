---
title: Criticalidade dos negócios – gerenciamento e operações de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticalidade dos negócios – gerenciamento e operações de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7e7618163b15d17eab51571779e573dd9acb726e
ms.sourcegitcommit: 73dbedf580951f25bf4b5544b83451cb075b1fa1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72805809"
---
# <a name="business-commitment-in-cloud-management"></a>Compromisso de negócios no gerenciamento de nuvem

Definir um compromisso de negócios é um exercício em prioridades de balanceamento. O objetivo é alinhar o nível adequado de gerenciamento operacional a um custo operacional aceitável. Encontrar esse equilíbrio exige alguns pontos de dados e cálculos, descritos nas seções a seguir.

![Equilibrar custo e resiliência](../../_images/manage/business-commitment-scale.png)

Os compromissos com a estabilidade comercial (por meio de resiliência técnica ou outros impactos de SLA) são uma decisão de justificativa de negócios. Para a maioria das cargas de trabalho em um ambiente, um nível de linha de base de gerenciamento de nuvem é suficiente. Para outros, um aumento de custo de 2 &ndash;4x é facilmente justificado devido ao impacto potencial de quaisquer interrupções de negócios. Os artigos anteriores desta série ajudam a compreender a classificação e o impacto das interrupções em várias cargas de trabalho. Este artigo ajudará a calcular os retornos. Conforme descrito na imagem a seguir, em cada nível de gerenciamento de nuvem há pontos de inflexão em que o custo pode aumentar mais rapidamente do que o aumento na resiliência. Esses pontos de inflexão solicitar decisões de negócios e compromissos de negócios detalhados.

## <a name="determining-a-proper-commitment-with-the-business"></a>Determinando um compromisso adequado com os negócios

Para cada carga de trabalho no portfólio, a equipe de operações de nuvem e a equipe de estratégia de nuvem devem se alinhar ao nível de gerenciamento fornecido diretamente pela equipe de operações de nuvem.

A seguir estão os principais aspectos a serem alinhados ao estabelecer um compromisso com os negócios:

- Pré-requisitos de operações de ti
- Responsabilidade do gerenciamento
- Locação de nuvem
- Fatores de custo flexível
- ROI de evitar perda
- Validar nível de gerenciamento

O restante deste artigo descreverá cada um desses critérios para ajudar a tomar uma decisão.

## <a name="it-operations-prerequisites"></a>Pré-requisitos de operações de ti

O [Guia de gerenciamento do Azure](../azure-management-guide/index.md) descreve as ferramentas de gerenciamento disponíveis no Azure. Antes de alcançar um compromisso com os negócios, ele deve determinar uma linha de base aceitável de gerenciamento de nível padrão a ser aplicada a todas as cargas de trabalho gerenciadas. Em seguida, ele calcularia um custo de gerenciamento padrão para cada uma das cargas de trabalho gerenciadas no portfólio de ti, com base nas contagens de núcleos de CPU, espaço em disco e outras variáveis relacionadas ao ativo. Ele também estimaria um SLA composto para cada carga de trabalho com base na arquitetura.

> [!TIP]
> As equipes de operações de ti geralmente usarão um mínimo padrão de tempo de atividade de 99,9% para o SLA composto inicial. Eles também podem optar por normalizar os custos de gerenciamento com base na carga de trabalho média, especialmente para soluções com necessidades mínimas de registro em log e armazenamento. A média dos custos de algumas cargas de trabalho de criticalidade médias pode fornecer um ponto de partida para conversas iniciais.

> [!TIP]
> Para os leitores que estão usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem, os campos de gerenciamento de operações devem ser atualizados para refletir esses pré-requisitos. Esses campos incluem nível de compromisso, SLA composto e custo mensal. O custo mensal deve representar o custo das ferramentas de gerenciamento operacional adicionadas mensalmente.

A linha de base de gerenciamento de operações servirá como um ponto inicial para ser validado em cada uma das seções a seguir.

## <a name="management-responsibility"></a>Responsabilidade do gerenciamento

Em um ambiente local tradicional, o custo do gerenciamento do ambiente é geralmente considerado um custo perdido de propriedade de ti. Na nuvem, o gerenciamento é uma decisão proposital com impacto direto no orçamento. Os custos de cada função de gerenciamento podem ser atribuídos mais diretamente a cada carga de trabalho implantada na nuvem. Essa abordagem permite maior controle, mas cria um requisito para equipes de operações de nuvem e equipes de estratégia de nuvem para primeiro confirmar um contrato referente a responsabilidades.

As organizações também podem optar por [terceirizar algumas das funções de gerenciamento contínuas para um provedor de serviços](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Esses provedores de serviços podem usar o [Azure Lighthouse](https://azure.com/lighthouse) para dar às organizações mais precisão e controle para conceder acesso a seus recursos, juntamente com maior transparência nas ações executadas pelos provedores de serviços.

**Responsabilidade delegada:** Como não há necessidade de centralizar e assumir a sobrecarga de gerenciamento operacional, as operações de ti para muitas organizações estão considerando novas abordagens. Uma abordagem comum é conhecida como responsabilidade delegada. Em um Cloud Center de modelo de excelência, as operações de plataforma e a automação de plataforma fornecem ferramentas de gerenciamento de autoatendimento que podem ser aproveitadas por equipes de operações orientadas por negócios, independentemente de uma equipe de operações de ti central. Essa abordagem fornece aos participantes da empresa o controle total sobre os orçamentos relacionados ao gerenciamento. Ele também permite ao CCoE garantir que um conjunto mínimo de guardrails seja implementado corretamente. Nesse modelo, ele atua como um agente e um guia para ajudar a empresa a tomar decisões inteligentes. As operações de negócios supervisionam as operações diárias de cargas de trabalho dependentes.

**Responsabilidade centralizada:** Os requisitos de conformidade, a complexidade técnica e alguns modelos de serviço compartilhado podem exigir um modelo de ti central. Nesse modelo, ele continua a manter as responsabilidades do gerenciamento de operações. Assim, o design ambiental, os controles de gerenciamento e as ferramentas de governança podem ser gerenciados e controlados centralmente, o que restringe a função dos participantes comerciais ao fazer os compromissos de gerenciamento. Mas, a visibilidade de custo e arquitetura das abordagens de nuvem torna muito mais fácil para a ti centralizada comunicar o custo e o nível de gerenciamento de cada carga de trabalho.

**Modelo misto:** A classificação é a essência de um modelo misto para responsabilidades de gerenciamento. As empresas que estão no meio de uma transformação do local para a nuvem podem exigir um modelo operacional de primeiro local por um tempo. Outras empresas que têm requisitos de conformidade estritos ou que dependem de contratos de longo prazo com fornecedores de terceirização de ti podem exigir um modelo operacional centralizado. Apesar desses tipos de restrições, as empresas precisam inovar. Quando a inovação rápida deve prosperarr, no meio de um modelo central de ti centralizado, a classificação e um modelo misto podem fornecer um equilíbrio. Nessa abordagem, a ti central fornece um modelo de operação centralizado para todas as cargas de trabalho que são de missão crítica ou que contêm informações confidenciais. No entanto, todas as outras classificações de carga de trabalho podem ser colocadas em um ambiente de nuvem projetado para responsabilidades delegadas. A abordagem de responsabilidade centralizada serve como o modelo operacional geral. Em seguida, a empresa tem flexibilidade para aproveitar um modelo operacional especializado, com base no nível necessário de suporte e sensibilidade.

A primeira etapa é confirmar uma abordagem de responsabilidade, que irá moldar os compromissos a seguir.

**Qual organização será responsável pelo gerenciamento de operações do dia a dia para essa carga de trabalho?**

## <a name="cloud-tenancy"></a>Locação de nuvem

Para a maioria das empresas, o gerenciamento é mais fácil quando todos os ativos residem em um único locatário. No entanto, algumas organizações podem precisar manter vários locatários. O artigo sobre como [centralizar as operações de gerenciamento com o Azure Lighthouse](../centralize-operations.md) fornece alguns exemplos em que as empresas podem exigir ambientes multilocatários do Azure.

**Essa carga de trabalho residirá em um único locatário do Azure, juntamente com todas as outras cargas de trabalho?**

## <a name="soft-cost-factors"></a>Fatores de custo flexível

A próxima seção deste artigo descreve uma abordagem para retornos comparativos associados a níveis de processos e ferramentas de gerenciamento. No final dessa seção, cada carga de trabalho analisada medirá o custo de gerenciamento em relação ao impacto previsto das interrupções nos negócios. Essa abordagem fornecerá uma maneira relativamente fácil de entender se o investimento em abordagens de gerenciamento mais avançadas é garantido.

Antes de executar os números, é importante observar os fatores de custo flexível. Fatores de custo flexível produzem um retorno, mas esse retorno é difícil de medir por meio de economia de custo rígido direto que estaria visível em uma instrução de lucros e perdas. Fatores de custo flexível são importantes porque podem indicar a necessidade de investir em um nível mais alto de gerenciamento do que o livre prudente.

Alguns exemplos desses fatores incluem:

- Diariamente, use uma carga de trabalho pelo Conselho ou CEO.
- Uso de uma carga de trabalho por _x%_ principal de clientes que leva a um impacto maior na receita em outro lugar.
- Impacto na satisfação do funcionário.

O próximo ponto de dados necessário para fazer um compromisso é uma lista de fatores de custo flexível. Eles não precisam ser documentados neste estágio, mas os interessados comerciais devem estar cientes da importância desses fatores e de sua exclusão dos cálculos a seguir.

## <a name="calculate-loss-avoidance-roi"></a>Calcular ROI de prevenção de perda

Ao calcular o retorno relativo sobre os custos de gerenciamento de operações, a equipe de ti responsável pelas operações de nuvem deve concluir os pré-requisitos acima e assumir um nível mínimo de gerenciamento para todas as cargas de trabalho.

O próximo compromisso a ser feito é uma aceitação pelos negócios dos custos associados à oferta de linha de base gerenciada.

**A empresa concorda em investir na oferta de linha de base para atender aos padrões mínimos de operações de nuvem?**

Se a empresa não concordar com esse nível de gerenciamento, uma solução deverá ser planejada, o que permitirá que a empresa continue, sem afetar materialmente as operações de nuvem de outras cargas de trabalho.

Se a empresa quiser mais do que o nível padrão, o restante desta seção ajudará a validar esse investimento e os retornos associados (na forma de evitar a perda).

### <a name="increased-levels-of-management-design-principles-and-service-catalog"></a>Maiores níveis de gerenciamento: princípios de design e catálogo de serviços

Para soluções gerenciadas, há vários princípios de design e soluções de modelo que podem ser aplicados além da linha de base de gerenciamento. Cada um dos princípios de design para confiabilidade e resiliência adiciona o custo operacional à carga de trabalho. Para que a ti e a empresa concordem com esses compromissos adicionais, é importante entender possíveis perdas que podem ser evitadas com o aumento do investimento.

Os seguintes cálculos percorrerão fórmulas para entender melhor a comparação entre perdas e maiores investimentos em gerenciamento. Para obter orientação sobre como calcular o custo do aumento do gerenciamento, consulte os artigos sobre automação de [carga de trabalho](./workload.md) e [automação de plataforma](./platform.md).

> [!TIP]
> Para os leitores que estão usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem, os campos de gerenciamento de operações devem ser atualizados para refletir para refletir cada conversa. Esses campos incluem nível de compromisso, SLA composto e custo mensal. O custo mensal deve representar o custo das ferramentas de gerenciamento operacional adicionadas mensalmente. Depois de atualizado, esses campos atualizarão as fórmulas de ROI e cada um dos campos a seguir.

### <a name="estimate-outage-hours-per-year"></a>Estimativa de interrupção (horas por ano)

O "SLA composto" é o contrato de nível de serviço baseado na implantação de cada ativo na carga de trabalho. Esse campo irá impulsionar "interrupção estimada" (rotulada est. Interrupção * * * na pasta de trabalho). Para calcular a interrupção estimada em horas por ano sem usar a pasta de trabalho, aplique a seguinte fórmula:

**Interrupção estimada = (percentual de SLA composto 1)/* número de horas em um ano* *

Na pasta de trabalho, é usado o valor padrão de 8.760 horas por ano.

### <a name="standard-loss-impact"></a>Impacto de perda padrão

O impacto de perda padrão (intitulado "impacto padrão" na pasta de trabalho) prevê o impacto financeiro de qualquer interrupção, supondo que a previsão de "interrupção estimada" tenha uma prova precisa. Para calcular essa previsão sem usar a pasta de trabalho, aplique a seguinte fórmula:

**Impacto padrão = interrupção estimada @ três noves de impacto de tempo de atividade/* hora/valor* *

Isso serve como uma linha de base para custos, caso os participantes da empresa optem por investir em um nível mais alto de gerenciamento.

### <a name="composite-sla-impact"></a>Impacto de SLA de composição

O impacto de SLA composto (intitulado "impacto no nível de compromisso" na pasta de trabalho) fornece impacto fiscal atualizado, com base nas alterações no SLA de tempo de atividade. Isso permite que você compare o impacto financeiro projetado de ambas as opções. Para calcular esse impacto previsto sem a planilha, aplique a fórmula a seguir.

**Impacto de SLA composto = impacto estimado* /tempo/valor de interrupção* *

O valor representa as possíveis perdas a serem evitadas pelo nível de compromisso alterado e pelo novo SLA composto.

### <a name="comparison-basis"></a>Base de comparação

A base de comparação avalia o impacto padrão e o impacto do SLA composto para determinar qual é o mais apropriado na coluna de retorno.

### <a name="return-on-loss-avoidance"></a>Retorno de prevenção de perda

Se o custo do gerenciamento de uma carga de trabalho exceder as possíveis perdas, o investimento proposto no gerenciamento de nuvem poderá não ser proveitosa. Para comparar a "devolução de perda de retorno", consulte a coluna rotulada "ROI anual * * * *". Para calcular essa coluna por conta própria, use esta fórmula:

**Retorno da prevenção de perda = (base de comparação-(custo mensal/* 12))//(custo mensal/* 12)) **

A menos que haja outros fatores de custo flexível a considerar, essa comparação pode sugerir rapidamente se deve haver um investimento mais profundo em operações de nuvem, resiliência, confiabilidade ou outras áreas.

## <a name="validate-the-commitment"></a>Validar o compromisso

Nesse ponto do processo, os compromissos foram feitos: responsabilidade centralizada ou delegada, aluguel do Azure e nível de compromisso.
Cada compromisso deve ser validado e documentado para garantir que a equipe de operações de nuvem, a equipe de estratégia de nuvem e os participantes comerciais estejam alinhados a esse compromisso para gerenciar a carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Depois que os compromissos são feitos, as equipes de operações responsáveis podem iniciar a configuração da carga de trabalho em questão. Para começar, avalie várias abordagens para [inventário e visibilidade](./inventory.md).

> [!div class="nextstepaction"]
> [Opções de inventário e visibilidade](./inventory.md)
