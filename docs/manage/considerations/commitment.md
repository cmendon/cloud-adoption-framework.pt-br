---
title: 'Compromisso de negócios: gerenciamento de nuvem e operações'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Compromisso de negócios: gerenciamento de nuvem e operações'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 29acef56de414d1a98e5fe11e5e396922b84392d
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752883"
---
# <a name="business-commitment-in-cloud-management"></a>Compromisso de negócios no gerenciamento de nuvem

Definir o _compromisso de negócios_ é um exercício em prioridades de balanceamento. O objetivo é alinhar o nível adequado de gerenciamento operacional a um custo operacional aceitável. Encontrar esse equilíbrio exige alguns pontos de dados e cálculos, que descrevemos neste artigo.

![Equilibrar custo e resiliência](../../_images/manage/business-commitment-scale.png)

Os compromissos de estabilidade de negócios, por meio de resiliência técnica ou outros impactos de SLA (contrato de nível de serviço), são uma decisão de justificativa de negócios. Para a maioria das cargas de trabalho em um ambiente, um nível de linha de base de gerenciamento de nuvem é suficiente. Para outros, um aumento de custo de 2x a 4x é facilmente justificado devido ao impacto potencial de quaisquer interrupções de negócios.

Os artigos anteriores desta série podem ajudá-lo a entender a classificação e o impacto das interrupções em várias cargas de trabalho. Este artigo ajuda você a calcular os retornos. Conforme ilustrado na imagem anterior, cada nível de gerenciamento de nuvem tem pontos de inflexão em que o custo pode aumentar mais rapidamente do que o aumento na resiliência. Esses pontos de inflexão solicitar decisões de negócios e compromissos de negócios detalhados.

## <a name="determine-a-proper-commitment-with-the-business"></a>Determine um compromisso adequado com os negócios

Para cada carga de trabalho no portfólio, a equipe de operações de nuvem e a estratégia de nuvem devem se alinhar ao nível de gerenciamento fornecido diretamente pela equipe de operações de nuvem.

Como você está estabelecendo um compromisso com os negócios, há alguns aspectos fundamentais a serem alinhados:

- Pré-requisitos de operações de ti
- Responsabilidade do gerenciamento
- Locação de nuvem
- Fatores de custo flexível
- ROI de evitar perda
- Validação do nível de gerenciamento

Para ajudar no processo de decisão, o restante deste artigo descreve cada um desses aspectos com mais detalhes.

## <a name="it-operations-prerequisites"></a>Pré-requisitos de operações de ti

O [Guia de gerenciamento do Azure](../azure-management-guide/index.md) descreve as ferramentas de gerenciamento disponíveis no Azure. Antes de alcançar um compromisso com os negócios, ele deve determinar uma linha de base de gerenciamento de nível padrão aceitável a ser aplicada a todas as cargas de trabalho gerenciadas. Em seguida, ele calcularia um custo de gerenciamento padrão para cada uma das cargas de trabalho gerenciadas no portfólio de ti, com base nas contagens de núcleos de CPU, espaço em disco e outras variáveis relacionadas ao ativo. Ele também estimaria um SLA composto para cada carga de trabalho, com base na arquitetura.

> [!TIP]
> As equipes de operações de ti geralmente usam um mínimo padrão de tempo de atividade de 99,9% para o SLA composto inicial. Eles também podem optar por normalizar os custos de gerenciamento com base na carga de trabalho média, especialmente para soluções com necessidades mínimas de registro em log e armazenamento. A média dos custos de algumas cargas de trabalho de criticalidade médias pode fornecer um ponto de partida para conversas iniciais.

<!-- -->

> [!TIP]
> Se você estiver usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem, os campos de gerenciamento de operações deverão ser atualizados para refletir esses pré-requisitos. Esses campos incluem _nível de compromisso_, _SLA composto_e _custo mensal_. O custo mensal deve representar o custo das ferramentas de gerenciamento operacional adicionadas mensalmente.

A linha de base de gerenciamento de operações serve como um ponto de partida inicial para ser validado em cada uma das seções a seguir.

## <a name="management-responsibility"></a>Responsabilidade do gerenciamento

Em um ambiente local tradicional, o custo do gerenciamento do ambiente é geralmente considerado um custo perdido que é de propriedade de operações de ti. Na nuvem, o gerenciamento é uma decisão proposital com impacto direto no orçamento. Os custos de cada função de gerenciamento podem ser atribuídos mais diretamente a cada carga de trabalho implantada na nuvem. Essa abordagem permite maior controle, mas cria um requisito para equipes de operações de nuvem e equipes de estratégia de nuvem para primeiro confirmar um contrato sobre responsabilidades.

As organizações também podem optar por [terceirizar algumas das funções de gerenciamento contínuas para um provedor de serviços](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Esses provedores de serviços podem usar o [Azure Lighthouse](https://azure.com/lighthouse) para dar ao organizações um controle mais preciso para conceder acesso a seus recursos, juntamente com maior visibilidade das ações executadas pelos provedores de serviços.

- **Responsabilidade delegada:** Como não há necessidade de centralizar e assumir a sobrecarga de gerenciamento operacional, as operações de ti para muitas organizações estão considerando novas abordagens. Uma abordagem comum é conhecida como _responsabilidade delegada_. Em um Cloud Center de modelo de excelência, as operações de plataforma e a automação de plataforma fornecem ferramentas de gerenciamento de autoatendimento que podem ser usadas por equipes de operações orientadas por negócios, independentemente de uma equipe de operações de ti central. Essa abordagem dá aos participantes da empresa controle total sobre os orçamentos relacionados ao gerenciamento. Ele também permite que a equipe do Cloud Center of Excellence (CCOE) garanta que um conjunto mínimo de guardrails tenha sido adequadamente implementado. Nesse modelo, ele atua como um agente e um guia para ajudar a empresa a tomar decisões inteligentes. As operações de negócios supervisionam as operações diárias de cargas de trabalho dependentes.

- **Responsabilidade centralizada:** Os requisitos de conformidade, a complexidade técnica e alguns modelos de serviço compartilhado podem exigir um modelo de _ti central_ . Nesse modelo, ele continua a exercitar suas responsabilidades de gerenciamento de operações. O design ambiental, os controles de gerenciamento e as ferramentas de governança podem ser gerenciados e controlados centralmente, o que restringe a função dos participantes de negócios ao fazer compromissos de gerenciamento. Mas a visibilidade do custo e da arquitetura das abordagens de nuvem torna muito mais fácil para a ti centralizada comunicar o custo e o nível de gerenciamento de cada carga de trabalho.

- **Modelo misto:** A classificação é a essência de um _modelo misto_ de responsabilidades de gerenciamento. As empresas que estão no meio de uma transformação do local para a nuvem podem exigir um modelo operacional de primeiro local por um tempo. As empresas com requisitos de conformidade estritos ou que dependem de contratos de longo prazo com fornecedores de terceirização de ti podem exigir um modelo operacional centralizado.

  Independentemente de suas restrições, as empresas de hoje devem inovar. Quando a inovação rápida deve prosperar, no meio de um modelo central de ti e centralizado, uma abordagem de modelo misto pode fornecer saldo. Nessa abordagem, a ti central fornece um modelo de operação centralizado para todas as cargas de trabalho que são de missão crítica ou que contêm informações confidenciais. Ao mesmo tempo, todas as outras classificações de carga de trabalho podem ser colocadas em um ambiente de nuvem projetado para responsabilidades delegadas. A abordagem de responsabilidade centralizada serve como o modelo operacional geral. Em seguida, a empresa tem flexibilidade para adotar um modelo operacional especializado, com base em seu nível necessário de suporte e sensibilidade.

A primeira etapa é confirmar uma abordagem de responsabilidade que, em seguida, forma os compromissos a seguir.

**Qual organização será responsável pelo gerenciamento de operações do dia a dia para essa carga de trabalho?**

## <a name="cloud-tenancy"></a>Locação de nuvem

Para a maioria das empresas, o gerenciamento é mais fácil quando todos os ativos residem em um único locatário. No entanto, algumas organizações podem precisar manter vários locatários. Para saber por que uma empresa pode exigir um ambiente multilocatário do Azure, consulte [centralizar operações de gerenciamento com o Azure Lighthouse](../centralize-operations.md).

**Essa carga de trabalho residirá em um único locatário do Azure, juntamente com todas as outras cargas de trabalho?**

## <a name="soft-cost-factors"></a>Fatores de custo flexível

A próxima seção descreve uma abordagem para os retornos comparativos que estão associados a níveis de processos de gerenciamento e ferramentas. No final dessa seção, cada carga de trabalho analisada mede o custo de gerenciamento em relação ao impacto da previsão das interrupções nos negócios. Essa abordagem fornece uma maneira relativamente fácil de entender se um investimento em abordagens de gerenciamento mais avançadas é garantido.

Antes de executar os números, é importante observar os fatores de custo flexível. Fatores de custo flexível produzem um retorno, mas esse retorno é difícil de medir por meio de economia de custo rígido direto que estaria visível em uma instrução de lucros e perdas. Fatores de custo flexível são importantes porque podem indicar a necessidade de investir em um nível mais alto de gerenciamento do que o livre prudente.

Alguns exemplos de fatores de custo flexível incluem:

- Uso diário da carga de trabalho pelo Conselho ou CEO.
- Uso de carga de trabalho por um _x percentual_ superior de clientes que leva a um impacto maior na receita em outro lugar.
- Impacto na satisfação do funcionário.

O próximo ponto de dados necessário para fazer um compromisso é uma lista de fatores de custo flexível. Esses fatores não precisam ser documentados neste estágio, mas os interessados comerciais devem estar cientes da importância desses fatores e de sua exclusão dos cálculos a seguir.

## <a name="calculate-loss-avoidance-roi"></a>Calcular ROI de prevenção de perda

Quando estiver calculando o retorno relativo sobre os custos do gerenciamento de operações, a equipe de ti responsável pelas operações de nuvem deverá concluir os pré-requisitos mencionados anteriormente e assumir um nível mínimo de gerenciamento para todas as cargas de trabalho.

O próximo compromisso a ser feito é uma aceitação pelos negócios dos custos associados à oferta de linha de base gerenciada.

**A empresa concorda em investir na oferta de linha de base para atender aos padrões mínimos de operações de nuvem?**

Se a empresa não concordar com esse nível de gerenciamento, será necessário desenvolver uma solução que permita que a empresa continue, sem afetar materialmente as operações de nuvem de outras cargas de trabalho.

Se a empresa quiser mais do que o nível de gerenciamento padrão, o restante desta seção ajudará a validar esse investimento e os retornos associados (na forma de evitar perda).

### <a name="increased-levels-of-management-design-principles-and-service-catalog"></a>Maiores níveis de gerenciamento: princípios de design e catálogo de serviços

Para soluções gerenciadas, vários princípios de design e soluções de modelo podem ser aplicados além da linha de base de gerenciamento. Cada um dos princípios de design para confiabilidade e resiliência adiciona o custo operacional à carga de trabalho. Para que a ti e a empresa concordem com esses compromissos adicionais, é importante entender possíveis perdas que podem ser evitadas com o aumento do investimento.

Os seguintes cálculos percorrerão fórmulas para ajudá-lo a entender melhor as diferenças entre perdas e maiores investimentos em gerenciamento. Para obter orientação sobre como calcular o custo do aumento do gerenciamento, consulte [automação de carga de trabalho](./workload.md) e automação de [plataforma](./platform.md).

> [!TIP]
> Se você estiver usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem, atualize os campos de gerenciamento do Ops para refletir para refletir cada conversa. Esses campos incluem _nível de compromisso_, _SLA composto_e _custo mensal_. O custo mensal deve representar o custo mensal das ferramentas de gerenciamento operacional adicionadas. Depois que eles forem atualizados, os campos atualizarão as fórmulas de ROI e cada um dos campos a seguir.

### <a name="estimate-outage-hours-per-year"></a>Estimativa de interrupção (horas por ano)

O SLA composto é o contrato de nível de serviço baseado na implantação de cada ativo na carga de trabalho. Esse campo impulsiona a _interrupção estimada_ (rotulada _est. interrupção_ na pasta de trabalho). Para calcular a interrupção estimada em horas por ano sem usar a pasta de trabalho, aplique a seguinte fórmula:

> _Interrupção estimada = (percentual de SLA de composição &#215; ) número de horas em um ano_

A pasta de trabalho usa o valor padrão de _8.760 horas por ano_.

### <a name="standard-loss-impact"></a>Impacto de perda padrão

O _impacto de perda padrão_ (rotulado como _impacto padrão_ na pasta de trabalho) prevê o impacto financeiro de qualquer interrupção, supondo que a previsão de _interrupção estimada_ tenha uma prova precisa. Para calcular essa previsão sem usar a pasta de trabalho, aplique a seguinte fórmula:

> _Impacto padrão = interrupção estimada @ três noves &#215; de tempo de atividade – impacto do valor_

Isso serve como uma linha de base para custos, caso os participantes da empresa optem por investir em um nível mais alto de gerenciamento.

### <a name="composite-sla-impact"></a>Impacto de SLA de composição

O _impacto de SLA composto_ (rotulado _impacto no nível de compromisso_ na pasta de trabalho) fornece impacto fiscal atualizado, com base nas alterações no SLA de tempo de atividade. Esse cálculo permite que você compare o impacto financeiro projetado de ambas as opções. Para calcular esse impacto de previsão sem a planilha, aplique a seguinte fórmula:

> _Impacto de SLA de composição = &#215; impacto estimado de tempo-valor de interrupção_

O valor representa as possíveis perdas a serem evitadas pelo nível de compromisso alterado e pelo novo SLA composto.

### <a name="comparison-basis"></a>Base de comparação

A _base de comparação_ avalia o impacto padrão e o impacto do SLA composto para determinar qual é o mais apropriado na coluna de retorno.

### <a name="return-on-loss-avoidance"></a>Retorno de prevenção de perda

Se o custo do gerenciamento de uma carga de trabalho exceder as possíveis perdas, o investimento proposto no gerenciamento de nuvem poderá não ser proveitosa. Para comparar o _retorno da prevenção de perda_, consulte a coluna rotulada _ROI anual * *_ * *. Para calcular essa coluna por conta própria, use a seguinte fórmula:

> _Retorno de prevenção de perda = (base de comparação-( &#215; custo mensal 12 &#247; )) ( &#215; custo mensal 12))_

A menos que haja outros fatores de custo flexível a considerar, essa comparação pode sugerir rapidamente se deve haver um investimento mais profundo em operações de nuvem, resiliência, confiabilidade ou outras áreas.

## <a name="validate-the-commitment"></a>Validar o compromisso

Nesse ponto do processo, os compromissos foram feitos: responsabilidade centralizada ou delegada, aluguel do Azure e nível de compromisso. Cada compromisso deve ser validado e documentado para garantir que a equipe de operações de nuvem, a equipe de estratégia de nuvem e os participantes comerciais estejam alinhados a esse compromisso para gerenciar a carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Depois que os compromissos são feitos, as equipes de operações responsáveis podem começar a configurar a carga de trabalho em questão. Para começar, avalie várias abordagens para [inventário e visibilidade](./inventory.md).

> [!div class="nextstepaction"]
> [Opções de inventário e visibilidade](./inventory.md)
