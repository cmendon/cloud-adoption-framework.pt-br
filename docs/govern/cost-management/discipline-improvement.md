---
title: Aperfeiçoamento da disciplina de Gerenciamento de Custos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aperfeiçoamento da disciplina de Gerenciamento de Custos
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2b94dad1ee2c4ddd95ecf513123a6f70969dcbfa
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027674"
---
# <a name="cost-management-discipline-improvement"></a>Aperfeiçoamento da disciplina de Gerenciamento de Custos

A disciplina de Gerenciamento de Custos tenta abordar riscos comerciais principais relacionados a despesas incorridas ao hospedar cargas de trabalho baseadas em nuvem. Dentro das cinco disciplinas de governança de nuvem, o gerenciamento de custos está envolvido no controle do custo e do uso de recursos de nuvem com o objetivo de criar e manter um ciclo de custo planejado.

Este artigo descreve as tarefas potenciais da sua empresa para realizar para desenvolver e maturar sua disciplina de Gerenciamento de Custos. Essas tarefas podem ser divididas entre as fases de planejamento, criação, adoção e operacional para a implementação de uma solução de nuvem, que depois são iteradas para permitir o desenvolvimento de uma [abordagem incremental para a governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

Nenhum documento individual pode contabilizar os requisitos de todas as empresas. Portanto, este artigo descreve as atividades de exemplo potenciais e mínimas sugeridas para cada fase do processo de amadurecimento da governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de gerenciamento de custos.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Essas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento de ambos os requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Esta fase de maturidade de governança une os resultados de negócios e as estratégias realizáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas ao estado digital e começa a planejar o esforço global de migração.

**Atividades mínimas sugeridas:**

- Avaliar suas opções de [cadeia de ferramentas de Gerenciamento de Custos](./toolchain.md).
- Desenvolver um documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Treinar e envolver as pessoas e equipes afetadas pelo desenvolvimento das diretrizes de arquitetura.

**Atividades potenciais:**

- Garantir em decisões orçamentárias que apoiam a justificativa e negócios para a sua estratégia de nuvem.
- Validar as métricas de aprendizado que podem ser usadas para relatar a alocação bem-sucedida de financiamento.
- Entender o modelo de contabilidade de nuvem desejado que afeta como os custos de nuvem devem ser considerados.
- Familiarizar-se com o plano de imóveis digital e validar as expectativas de custos precisas.
- Avaliar as opções de compras para determinar se é melhor "pagar conforme o uso" ou fazer um pré-compromisso com a compra de um Contrato Enterprise.
- Alinhar os objetivos de negócios aos orçamentos planejados e ajuste os planos orçamentários conforme necessário.
- Desenvolver metas e orçamento de mecanismo de relatórios para notificar técnicos e stakeholders do negócio no final de cada ciclo de custo.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo se concentra nas decisões, na preparação e na infraestrutura central que ocorrem após uma migração.

**Atividades mínimas sugeridas:**

- Implemente seu [ferramentas de gerenciamento de custos](./toolchain.md) ao distribuir em uma fase de pré-implantação.
- Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.
- Determine se seus requisitos de compra se alinham às suas metas e orçamentos.

**Atividades potenciais:**

- Alinhar seus planos de orçamento à [Estratégia de assinatura](../../decision-guides/subscriptions/index.md) que define o modelo de propriedade de núcleo.
- Use a [estratégia de consistência de recursos](../../decision-guides/resource-consistency/index.md) para reforçar a arquitetura e as diretrizes de custo ao longo do tempo.
- Determine se qualquer anomalia de custo afeta seus planos de adoção e migração.

## <a name="adopt-and-migrate"></a>Adotar e migrar

A migração é um processo incremental que se concentra no movimento, teste e adoção de aplicativos ou cargas de trabalho em um estado digital existente.

**Atividades mínimas sugeridas:**

- Migre seus [ferramentas de gerenciamento de custos](./toolchain.md) de pré-implantação para produção.
- Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.

**Atividades potenciais:**

- Implemente seu modelo de contabilidade de nuvem.
- Certifique-se de que seus orçamentos refletem seus gastos reais durante cada versão e ajuste conforme necessário.
- Monitore as alterações nos planos de acesso a recursos e valide com os stakeholders se forem necessárias aprovações adicionais.
- Atualizar as alterações no documento de Diretrizes de arquitetura para refletir os custos reais.

## <a name="operate-and-post-implementation"></a>Operação e pós-implementação

Depois que a transformação for concluída, a governança e as operações devem ser mantidas para o ciclo de vida natural de um aplicativo ou uma carga de trabalho. Essa fase de maturidade de governança se concentra em atividades que normalmente ocorrem depois que a solução é implementada e que o ciclo de transformação começa a se estabilizar.

**Atividades mínimas sugeridas:**

- Personalizar sua [cadeia de ferramentas de Gerenciamento de Custos](./toolchain.md) baseada em alterações nas necessidades de gerenciamento de custo da sua organização.
- Cogitar automatizar quaisquer notificações e relatórios para refletir o gasto real.
- Refinar as Diretrizes de arquitetura para orientar processos futuros de adoção.
- Treinar as equipes afetadas periodicamente para garantir a conformidade contínua às Diretrizes de Arquitetura.

**Atividades potenciais:**

- Executar uma análise de negócios trimestral de nuvem para comunicar o valor fornecido para os negócios e os custos associados.
- Ajustar planos trimestrais para refletir as alterações aos gastos reais.
- Determinar o alinhamento financeiro para perdas e ganhos para assinaturas de unidade de negócios.
- Analisar o valor do stakeholder e os métodos de relatórios de custo em uma base mensal.
- Avaliar os recursos subutilizados e determine se vale a pena mantê-los.
- Detectar desalinhamentos e anomalias entre os gastos reais e planejados.
- Auxilie as equipes de adoção da nuvem e a equipe de estratégia de nuvem com a compreensão e a resolução dessas anomalias.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende o conceito de governança de identidade de nuvem, examine a [cadeia de ferramentas de Gerenciamento de Custos](./toolchain.md) para identificar as ferramentas do Azure e recursos que você precisará ao desenvolver a disciplina de governança da de Gerenciamento de Custos na plataforma do Azure.

> [!div class="nextstepaction"]
> [Cadeia de ferramentas de Gerenciamento de Custos do Azure](./toolchain.md)
