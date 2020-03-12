---
title: O que é contabilidade de nuvem?
description: Use a estrutura de adoção de nuvem para o Azure para entender os modelos de contabilidade de nuvem comuns para ti à medida que você começa a sua jornada de migração na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 0ccff095f78442f583bcd526ee624161276c0db3
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092868"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-cloud-accounting"></a>O que é contabilidade de nuvem?

A nuvem altera como ela conta os custos, como é descrito em [criando um modelo financeiro para a transformação em nuvem](./financial-models.md). Vários modelos de contabilidade de ti são muito mais fáceis de dar suporte devido à forma como a nuvem aloca custos. Portanto, é importante entender como considerar os custos de nuvem antes de começar uma jornada de transformação na nuvem. Este artigo descreve os modelos de contabilidade de nuvem mais comuns para ele.

## <a name="traditional-it-accounting-cost-center-model"></a>Contabilidade de ti tradicional (modelo de centro de custo)

Geralmente, é preciso considerar um centro de custo. No modelo de contabilidade de ti tradicional, ele consolida a potência de compra de todos os ativos de ti. Como apontamos no artigo sobre [modelos financeiros](./financial-models.md) , essa aquisição de consolidação de energia pode incluir licenças de software, encargos recorrentes do licenciamento do CRM, compra de áreas de trabalho de funcionários e outros custos grandes.

Quando ele atua como um centro de custo, o valor percebido dele é exibido em grande parte por meio de uma lente de gerenciamento de compras. Essa percepção torna difícil para o quadro ou outros executivos entenderem o valor real que ele fornece. Os custos de aquisição tendem a distorcer a exibição dele por meio da importância de qualquer outro valor adicionado pela organização. Este modo de exibição explica por que muitas vezes é responsabilidade das responsabilidades do diretor financeiro ou do diretor de operações. Essa percepção de ti é limitada e pode ser de curta aparência.

## <a name="central-it-accounting-profit-center-model"></a>Contabilidade de ti central (modelo de centro de lucro)

Para superar a exibição do centro de custo de ti, alguns CIOs optavam por um modelo de ti central de contabilidade. Nesse tipo de modelo, ele é tratado como uma unidade de negócios concorrente e um ponto para as unidades de negócios que produzem receita. Em alguns casos, esse modelo pode ser totalmente lógico. Por exemplo, algumas organizações têm uma divisão de serviços de ti profissional que gera um fluxo de receita. Frequentemente, os modelos de ti centrais não geram receita significativa, dificultando a justificação do modelo.

Independentemente do modelo de receita, os modelos de contabilidade de ti central são exclusivos por causa de como as contas da unidade de ti custam. Em um modelo de ti tradicional, a equipe de ti registra os custos e paga os custos de fundos compartilhados, como operações e manutenção (O & M) ou uma conta de lucros e perdas dedicada (P & L).

Em um modelo de contabilidade de ti central, a equipe de ti marca os serviços fornecidos para levar em conta a sobrecarga, o gerenciamento e outras despesas estimadas. Em seguida, ele cobra as unidades de negócios concorrentes para os serviços marcados. Nesse modelo, espera-se que o CIO gerencie o P & L associado à venda desses serviços. Isso pode criar custos e contenção de ti informados entre as unidades centrais de ti e de negócios, especialmente quando precisa reduzir os custos ou não atender a SLAs acordados. Durante os horários de alteração da tecnologia ou do mercado, qualquer nova tecnologia causaria uma interrupção na central de ti de P & L, dificultando a transformação.

## <a name="chargeback"></a>Cobrança Retroativa

Uma das primeiras etapas comuns para alterar sua reputação é que o centro de custo está implementando um modelo de estorno de contabilidade. Esse modelo é especialmente comum em empresas menores ou em organizações de ti altamente eficientes. No modelo de estorno, os custos de ti associados a uma unidade de negócios específica são tratados como uma despesa operacional no orçamento da unidade de negócios. Essa prática reduz os efeitos de custo cumulativo, permitindo que os valores de negócios sejam mostrados mais claramente.

Em um modelo local herdado, o estorno é difícil de ser percebido, pois alguém ainda precisa ter as grandes despesas de capital e depreciação. A conversão contínua de despesas de capital para despesas operacionais associadas ao uso é um exercício de contabilidade difícil. Essa dificuldade é um grande motivo para a criação do modelo de contabilidade de ti tradicional e o modelo de contabilidade de ti central. O modelo de despesas operacionais da contabilização de custos de nuvem é quase necessário se você quiser fornecer um modelo de estorno com eficiência.

Mas você não deve implementar esse modelo sem considerar as implicações. Aqui estão algumas consequências que são exclusivas de um modelo de estorno:

- O estorno resulta em uma enorme redução do orçamento geral de ti. Para organizações de ti ineficientes ou que exigem habilidades técnicas extensivas e complexas em operações ou manutenção, esse modelo pode expor essas despesas de forma não íntegra.
- A perda de controle é uma conseqüência comum. Em ambientes altamente políticos, o estorno pode resultar na perda de controle e na equipe sendo realocada para a empresa. Isso poderia criar ineficiências significativas e reduzir a capacidade de atender consistentemente aos SLAs ou aos requisitos do projeto.
- A dificuldade de contabilização de serviços compartilhados é outra consequência comum. Se a organização cresceu por meio da aquisição e estiver realizando dívidas técnicas como resultado, é provável que uma alta porcentagem dos serviços compartilhados deva ser mantida para manter todos os sistemas trabalhando em conjunto com eficiência.

As transformações na nuvem incluem soluções para essas e outras consequências associadas a um modelo de estorno. Mas cada uma dessas soluções inclui despesas operacionais e de implementação. O CIO e o CFO devem ponderar cuidadosamente os prós e contras de um modelo de estorno antes de considerar um.

## <a name="showback-or-awareness-back"></a>Retorne ou reconhecimento

Para empresas maiores, um modelo de reversão ou reconhecimento é uma primeira etapa mais segura na transição do centro de custo para o centro de valor. Esse modelo não afeta a contabilidade financeira. Na verdade, a P & ls de cada organização não é alterada. A maior mudança está em mentalidade e conscientização. Em um modelo de reversão ou de reconhecimento, ele gerencia a potência de compra centralizada e consolidada como um agente para a empresa. Nos relatórios de volta para os negócios, ele relata os custos diretos para a unidade de negócios relevante, o que reduz o orçamento percebido diretamente consumido por ele. Ele também planeja orçamentos com base nas necessidades das unidades de negócios associadas, o que permite que ela tenha uma conta mais precisa para os custos associados a puramente iniciativas de ti.

Esse modelo fornece um equilíbrio entre um modelo de chargeback verdadeiro e os modelos mais tradicionais de contabilidade de ti.

## <a name="impact-of-cloud-accounting-models"></a>Impacto de modelos de contabilidade de nuvem

A escolha de modelos de contabilidade é crucial no design do sistema. A escolha do modelo de contabilidade pode afetar estratégias de assinatura, padrões de nomenclatura, padrões de marcação e designs de políticas e planos gráficos.

Depois de trabalhar com a empresa para tomar decisões sobre um modelo de contabilidade de nuvem e [mercados globais](./global-markets.md), você tem informações suficientes para [desenvolver uma base do Azure](../ready/index.md).

> [!div class="nextstepaction"]
> [Desenvolver uma base do Azure](../ready/index.md)
