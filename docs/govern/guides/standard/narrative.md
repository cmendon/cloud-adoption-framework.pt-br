---
title: 'Governança empresarial padrão: narração por trás da estratégia de governança'
description: Use a estrutura de adoção de nuvem para o Azure para saber como estabelecer um caso de uso para governança durante uma jornada de adoção de nuvem empresarial padrão.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d963053806a6a43476c7597be5dd628b6e187e06
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709270"
---
# <a name="standard-enterprise-governance-guide-the-narrative-behind-the-governance-strategy"></a>Guia de governança empresarial padrão: a narração por trás da estratégia de governança

A seguinte narração descreve o caso de uso para governança durante uma [jornada de adoção de nuvem padrão da empresa](./index.md). Antes de implementar a jornada, é importante entender as suposições e a lógica que se refletem nesta narração. Em seguida, você pode melhorar o alinhamento da estratégia de governança para a jornada da sua própria organização.

## <a name="back-story"></a>Histórico

O conselho de diretores começou o ano com planos para acionar os negócios de várias maneiras. Eles estão enviando por push liderança para melhorar as experiências de cliente para obter a participação no mercado. Eles também estão enviando por push para novos produtos e serviços que irão posicionar a empresa como um líder de ideias no setor. Também iniciaram um esforço paralelo para reduzir o desperdício e cortar custos desnecessários. Embora intimidantes, as ações da placa e liderança mostram que esse esforço está concentrando o maior número de capital possível em crescimento futuro.

No passado, o CIO da empresa foi excluído dessas conversas estratégicas. No entanto, como a visão futura intrinsecamente está vinculada ao crescimento técnico, a TI tem uma vaga para ajudar a orientar essas grandes planos. A IT agora é esperada para entregar de novas maneiras. A equipe não está preparada para essas alterações e provavelmente está lutando com a curva de aprendizado.

## <a name="business-characteristics"></a>Características de negócios

A empresa tem o seguinte perfil de negócios:

- Todas as operações e vendas residem em um único país, com uma porcentagem baixa de clientes globais.
- A empresa opera como uma única unidade de negócios, com um orçamento alinhado a funções, incluindo vendas, marketing, operações e TI.
- A empresa vê a maior parte da TI como um dreno de capital ou centro de custo.

## <a name="current-state"></a>Estado atual

Veja o estado atual da TI da empresa e das operações de nuvem:

- A TI opera com dois ambientes de infraestrutura hospedada. Um ambiente contém ativos de produção. O segundo ambiente contém alguns ativos de desenvolvimento/teste e recuperação de desastres. Esses ambientes são hospedados por dois provedores diferentes. A TI se refere a esses dois datacenters como produção e recuperação de Desastre, respectivamente.
- A TI inseriu a nuvem migrando todas as contas de email de usuário final para o Office 365. Essa migração foi concluída há seis meses. Apenas alguns outros ativos de TI foram implantados na nuvem.
- As equipes de desenvolvimento de aplicativos estão trabalhando em uma capacidade de desenvolvimento/teste para saber mais sobre os recursos nativos de nuvem.
- A equipe do business intelligence (BI) está experimentando big data na nuvem e curadoria dos dados em novas plataformas.
- A empresa tem uma política definida de forma flexível, indicando que dados de clientes pessoais e dados financeiros não podem ser hospedados na nuvem, o que limita aplicativos de missão crítica nas implantações atuais.
- Os investimentos de ti são controlados amplamente por despesas de capital. Esses investimentos são planejados anualmente. Nos últimos anos, investimentos incluíram pouco requisitos de manutenção mais básicos.

## <a name="future-state"></a>Estado futuro

As seguintes alterações estão previstas nos próximos vários anos:

- O CIO está examinando a política em dados pessoais e dados financeiros para permitir os objetivos de estado futuro.
- As equipes de BI e o desenvolvimento de aplicativos desejam liberar soluções com base em nuvem para produção nos próximos 24 meses com base na visão do compromisso com o cliente e novos produtos.
- Este ano, a equipe de TI concluirá a retirada das cargas de trabalho de recuperação de desastre do datacenter de recuperação de desastre, migrando 2.000 VMs para a nuvem. Isso é esperado para produzir uma economia de custo estimado de 25 milhões de dólares nos próximos cinco anos.
    ![custos locais versus os custos do Azure demonstrando um retorno de $25M USD nos próximos cinco anos](../../../_images/govern/calculator-small-to-medium-enterprise.png)
- A empresa planeja alterar a forma como ela faz investimentos reposicionando as despesas de capital confirmadas como uma despesa operacional dentro dela. Essa alteração fornecerá maior controle de custo e habilitará a TI para acelerar outros esforços planejados.

## <a name="next-steps"></a>Próximas etapas

A empresa desenvolveu uma política corporativa para formar a implementação de governança. A política corporativa conduz muitas das decisões técnicas.

> [!div class="nextstepaction"]
> [Examinar a política corporativa inicial](./initial-corporate-policy.md)
