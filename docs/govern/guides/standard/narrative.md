---
title: 'Guia de governança empresarial padrão: a narração por trás da estratégia de governança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Essa narração estabelece um caso de uso para governança durante uma jornada de adoção de nuvem padrão da empresa.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8bf9b65c71defd57c319f46a83b5d4540967b012
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547431"
---
# <a name="standard-enterprise-governance-guide-the-narrative-behind-the-governance-strategy"></a>Guia de governança empresarial padrão: a narração por trás da estratégia de governança

A seguinte narração descreve o caso de uso para governança durante uma [jornada de adoção de nuvem padrão da empresa](./index.md). Antes de implementar a jornada, é importante entender as suposições e a lógica que se refletem nesta narração. Em seguida, você pode alinhar melhor a estratégia de governança à jornada de sua própria organização.

## <a name="back-story"></a>Voltar à história

O Conselho de diretores começou o ano com planos para energizar os negócios de várias maneiras. Eles estão enviando liderança para melhorar as experiências do cliente para obter participação no mercado. Eles também estão enviando por push novos produtos e serviços que posicionarão a empresa como líder de idéias no setor. Eles também iniciaram um esforço paralelo para reduzir o desperdício e cortar custos desnecessários. Embora seja intimidador, as ações da diretoria e da liderança mostram que esse esforço está se concentrando em um maior número de capital possível em crescimento futuro.

No passado, o CIO da empresa foi excluído dessas conversas estratégicas. No entanto, como a visão futura está vinculada intrinsecamente ao crescimento técnico, ela tem um assento na tabela para ajudar a guiar esses grandes planos. Agora, espera-se entregar de novas maneiras. A equipe não está preparada para essas alterações e provavelmente está lutando com a curva de aprendizado.

## <a name="business-characteristics"></a>Características de negócios

A empresa tem o seguinte perfil de negócios:

- Todas as vendas e operações residem em um único país, com um percentual baixo de clientes globais.
- A empresa funciona como uma única unidade de negócios, com orçamento alinhado a funções, incluindo vendas, marketing, operações e ti.
- A empresa vê a maior parte dela como um dreno de capital ou um centro de custo.

## <a name="current-state"></a>Estado atual

Aqui está o estado atual das operações de ti e de nuvem da empresa:

- Ele opera dois ambientes de infraestrutura hospedados. Um ambiente contém ativos de produção. O segundo ambiente contém recuperação de desastres e alguns ativos de desenvolvimento/teste. Esses ambientes são hospedados por dois provedores diferentes. Ele se refere a esses dois data centers como produção e DR, respectivamente.
- Ele entrou na nuvem migrando todas as contas de email do usuário final para o Office 365. Esta migração foi concluída há seis meses. Alguns outros ativos de ti foram implantados na nuvem.
- As equipes de desenvolvimento de aplicativos estão trabalhando em uma capacidade de desenvolvimento/teste para saber mais sobre os recursos nativos de nuvem.
- A equipe de business intelligence (BI) está experimentando Big Data na nuvem e na organização de dados em novas plataformas.
- A empresa tem uma política definida de forma flexível, indicando que dados de clientes pessoais e dados financeiros não podem ser hospedados na nuvem, o que limita aplicativos de missão crítica nas implantações atuais.
- Os investimentos de ti são controlados amplamente por despesas de capital. Esses investimentos são planejados anualmente. Nos últimos anos, os investimentos incluíram pouco mais do que os requisitos básicos de manutenção.

## <a name="future-state"></a>Estado futuro

As seguintes alterações são antecipadas nos próximos vários anos:

- O CIO está examinando a política em dados pessoais e dados financeiros para permitir os objetivos de estado futuro.
- O desenvolvimento de aplicativos e as equipes de BI desejam lançar soluções baseadas em nuvem para produção nos próximos 24 meses com base na visão para o envolvimento do cliente e novos produtos.
- Neste ano, a equipe de ti acabará desativando as cargas de trabalho de recuperação de desastre do datacenter de DR migrando 2.000 VMs para a nuvem. Isso é esperado para produzir uma economia estimada de US $25M em dólares nos próximos cinco anos.
    os custos ![On locais versus os custos do Azure demonstrando um retorno de $25M USD nos próximos cinco anos ](../../../_images/govern/calculator-small-to-medium-enterprise.png)
- A empresa planeja alterar a forma como ela faz investimentos reposicionando as despesas de capital confirmadas como uma despesa operacional dentro dela. Essa alteração fornecerá maior controle de custo e permitirá que ele Acelere outros esforços planejados.

## <a name="next-steps"></a>Próximos passos

A empresa desenvolveu uma política corporativa para moldar a implementação de governança. A política corporativa impulsiona muitas das decisões técnicas.

> [!div class="nextstepaction"]
> [Examinar a política corporativa inicial](./initial-corporate-policy.md)
