---
title: Processos de conformidade de política do Gerenciamento de Custos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processos de conformidade de política do Gerenciamento de Custos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6345a8cae51a6b26b7fad174113a40e9dc0dae3e
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71220982"
---
# <a name="cost-management-policy-compliance-processes"></a>Processos de conformidade de política do Gerenciamento de Custos

Este artigo descreve uma abordagem para a criação de processos que dão suporte a uma disciplina de governança do [Gerenciamento de Custos](./index.md). A governança efetiva de custos de nuvem começa com recorrentes processos manuais, projetados para dar suporte à política de conformidade. Isso exige o envolvimento regular da equipe de governança de nuvem e os interessados comerciais interessados em revisar e atualizar a política e garantir a conformidade da política. Além disso, muitos processos de imposição e monitoramento contínuo podem ser automatizados ou complementados com ferramentas para reduzir a sobrecarga de governança e permitir uma resposta mais rápida ao desvio de políticas.

## <a name="planning-review-and-reporting-processes"></a>Planejar, revisar e relatar processos

As melhores ferramentas de Gerenciamento de Custos na nuvem somente são tão boas quanto os processos e políticas que dão suporte a elas. A seguir, é apresentado um conjunto de exemplos de processos normalmente envolvidos na disciplina de Linha de Gerenciamento de Custos. Use esses exemplos como ponto de partida ao planejar os processos que permitirão que você continue a atualizar a política de custo baseado na mudança comercial e feedback das equipes de negócios sujeitas a orientação de governança de custos.

**Avaliação e planejamento inicial de riscos:** Como parte da adoção inicial da disciplina de Gerenciamento de Custos, identifique os principais riscos e tolerâncias de negócios relacionados aos custos de nuvem. Use essas informações para os riscos de orçamento e relacionados a custo das suas equipes de negócios e desenvolva um conjunto de linha de base de políticas para atenuar esses riscos para restabelecer sua estratégia de governança inicial.

**Planejamento de implantação**: Antes de implantar qualquer ativo, estabeleça um orçamento previsto com base na alocação de nuvem esperada. Certifique-se de que as informações de propriedade e estatísticas para a implantação estão documentadas.

**Planejamento anual**: Anualmente, execute uma análise de acumulação em todos os ativos implantados e a serem implantados. Alinhe os orçamentos por unidades de negócios, departamentos, equipes e outras divisões apropriadas para capacitar a adoção de autoatendimento. Certifique-se de que o líder de cada unidade de cobrança está ciente do orçamento e como controlar os gastos.

Esse é o momento para fazer um pré-compromisso ou compra antecipada para aumentar o desconto. É recomendável alinhar o orçamento anual ao o ano fiscal do fornecedor de nuvem para capitalizar ainda mais opções de desconto de fim de ano.

**Planejamento trimestral**: A cada trimestre, examine os orçamentos com cada líder da unidade de cobrança para alinhar a previsão e gastos reais. Se houver alterações ao plano ou padrões de gastos inesperados, alinhe e realoque o orçamento.

Esse processo trimestral de planejamento também é um bom momento para avaliar a associação atual de sua equipe de governança de nuvem para as lacunas de conhecimento relacionadas aos planos de negócios atuais ou futuros. Convide a equipe relevante e os proprietários de carga de trabalho a participar das análises e planejamentos como consultores temporários ou membros permanentes da sua equipe.

**Educação e treinamento:** Em uma base Bimonthly, ofereça sessões de treinamento para garantir que a equipe de negócios e ti esteja atualizada sobre os requisitos mais recentes da política de gerenciamento de custos. Como parte desse processo, revise e atualize todas as documentações, diretrizes ou outros recursos de treinamento para garantir que estejam em sincronia com as últimas declarações da política corporativa.

**Relatório mensal:** Mensalmente, relate os gastos reais em relação a previsão. Notifique os líderes de cobrança sobre quaisquer desvios inesperados.

Esses processos básicos ajudarão a alinhar os gastos e estabelecer uma base para a disciplina de Gerenciamento de Custos.

## <a name="ongoing-monitoring-processes"></a>Processos de monitoramento contínuo

Uma estratégia de governança de Gerenciamento de Custos bem-sucedida depende da visibilidade do gasto relacionado a nuvem passado, atual e planejado para o futuro. Sem a capacidade de analisar as métricas relevantes e dados da integridade e atividade do ambiente da nuvem, você não pode identificar os riscos ou detectar violações das suas tolerâncias a risco. Os processo de administração contínua discutidos acima exigem dados de qualidade para garantir que a política possa ser modificada para proteger melhor a sua infraestrutura contra requisitos de mudança da empresa e uso da nuvem.

Certifique-se de que as equipes de TI implementaram sistemas automatizados para monitorar sua nuvem de gastos e uso para desvios não planejados de custos esperados. Estabelecer relatórios e alertas de sistemas para garantir a detecção de prompt e a mitigação de possíveis violações de política.

## <a name="compliance-violation-triggers-and-enforcement-actions"></a>Gatilhos de violação de conformidade e ações de imposição

Quando as violações forem detectadas, será necessário realizar ações para realinhar a política o mais rápido possível. Você pode automatizar a maioria dos gatilhos de violação usando as ferramentas descritas na [cadeia de ferramentas de Gerenciamento de Custos do Azure](./toolchain.md).

Estes são exemplos de gatilhos:

- **Desvios mensais do orçamento.** Discuta quaisquer desvios de gastos mensal que excederem 20% da relação previsão versus real com o líder da unidade de cobrança. Resoluções de registros e alterações na previsão.
- **Ritmo da adoção.** Qualquer desvio em um nível de assinatura acima de 20% disparará uma revisão com o líder da unidade de cobrança. Resoluções de registros e alterações na previsão.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de Gerenciamento de Nuvem](./template.md), documente os processos e gatilhos que alinham-se ao plano de adoção da nuvem atual.

Para obter diretrizes sobre a execução de políticas de gerenciamento de nuvem em alinhamento com planos de adoção, consulte o artigo sobre melhoria de disciplina do Gerenciamento de Custos.

> [!div class="nextstepaction"]
> [Aperfeiçoamento da disciplina de Gerenciamento de Custos](./discipline-improvement.md)
