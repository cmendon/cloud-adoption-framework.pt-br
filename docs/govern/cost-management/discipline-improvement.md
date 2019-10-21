---
title: Melhoria da disciplina de gerenciamento de custos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhoria da disciplina de gerenciamento de custos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 1c546512b2b9407d9edf54648e704209f8d460ea
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547802"
---
# <a name="cost-management-discipline-improvement"></a>Melhoria da disciplina de gerenciamento de custos

A disciplina de gerenciamento de custos tenta abordar os principais riscos de negócios relacionados a despesas incorridas ao hospedar cargas de trabalho baseadas em nuvem. Dentro das cinco disciplinas de governança de nuvem, o gerenciamento de custos está envolvido no controle do custo e do uso de recursos de nuvem com o objetivo de criar e manter um ciclo de custo planejado.

Este artigo descreve as tarefas em potencial que sua empresa executa para desenvolver e amadurecer sua disciplina de gerenciamento de custos. Essas tarefas podem ser divididas em fases de planejamento, criação, adoção e operação de implementação de uma solução de nuvem, que são então iteradas para permitir o desenvolvimento de uma [abordagem incremental para governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

Nenhum documento único pode considerar os requisitos de todas as empresas. Como tal, este artigo descreve as atividades de exemplo mínimas e potenciais do sugerido para cada fase do processo de desenvolvimento de governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de gerenciamento de custos.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Estas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento dos dois requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Essa fase de maturidade de governança preenche a divisão entre resultados de negócios e estratégias acionáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas para o espaço digital e começa a planejar o esforço geral de migração.

**Mínimo de atividades sugeridas:**

- Avalie suas opções de [ferramentas de gerenciamento de custos](./toolchain.md) .
- Desenvolva um documento de diretrizes de arquitetura de rascunho e distribua para as principais partes interessadas.
- Instrua e envolva as pessoas e equipes afetadas pelo desenvolvimento de diretrizes de arquitetura.

**Atividades potenciais:**

- Garanta decisões orçamentárias que dão suporte à justificativa de negócios para sua estratégia de nuvem.
- Valide as métricas de aprendizado que você usa para relatar a alocação de financiamento bem-sucedida.
- Entenda o modelo de contabilidade de nuvem desejado que afeta como os custos de nuvem devem ser contabilizados.
- Familiarize-se com o plano de imóveis digital e valide expectativas de custos precisas.
- Avalie as opções de compra para determinar se é melhor "pague pelo uso" ou para fazer um comprometimento com a compra de um Enterprise Agreement.
- Alinhe as metas de negócios com os orçamentos planejados e ajuste os planos orçamentários conforme necessário.
- Desenvolva um mecanismo de metas e relatórios de orçamento para notificar os participantes técnicos e comerciais no final de cada ciclo de custo.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo concentra-se nas decisões, prontidão e infraestrutura básica que prosseguem com uma migração.

**Mínimo de atividades sugeridas:**

- Implemente seu [ferramentas de gerenciamento de custos](./toolchain.md) ao distribuir em uma fase de pré-implantação.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar a adoção do usuário.
- Determine se os requisitos de compra estão alinhados com seus orçamentos e metas.

**Atividades potenciais:**

- Alinhe seus planos orçamentários com a [estratégia de assinatura](../../decision-guides/subscriptions/index.md) que define seu modelo de propriedade de núcleo.
- Use a [estratégia de consistência de recursos](../../decision-guides/resource-consistency/index.md) para reforçar a arquitetura e as diretrizes de custo ao longo do tempo.
- Determine se qualquer anomalia de custo afeta seus planos de adoção e migração.

## <a name="adopt-and-migrate"></a>Adote e migre

A migração é um processo incremental que se concentra na movimentação, no teste e na adoção de aplicativos ou cargas de trabalho em um espaço digital existente.

**Mínimo de atividades sugeridas:**

- Migre seus [ferramentas de gerenciamento de custos](./toolchain.md) de pré-implantação para produção.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar a adoção do usuário.

**Atividades potenciais:**

- Implemente seu modelo de contabilidade de nuvem.
- Certifique-se de que seus orçamentos reflitam seus gastos reais durante cada versão e ajuste conforme necessário.
- Monitore as alterações nos planos orçamentários e valide com os participantes se forem necessárias aprovações adicionais.
- Atualize as alterações no documento de diretrizes de arquitetura para refletir os custos reais.

## <a name="operate-and-post-implementation"></a>Operar e pós-implementação

Depois que a transformação for concluída, a governança e as operações deverão residir para o ciclo de vida natural de um aplicativo ou carga de trabalho. Essa fase de maturidade de governança se concentra nas atividades que normalmente vêm depois que a solução é implementada e o ciclo de transformação começa a estabilizar.

**Mínimo de atividades sugeridas:**

- Personalize seu [ferramentas de gerenciamento de custos](./toolchain.md) com base nas alterações nas necessidades de gerenciamento de custos de sua organização.
- Considere automatizar notificações e relatórios para refletir os gastos reais.
- Refine as diretrizes de arquitetura para orientar processos futuros de adoção.
- Instrua as equipes afetadas periodicamente para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Execute uma análise de negócios de nuvem trimestral para comunicar o valor entregue aos negócios e aos custos associados.
- Ajuste os planos trimestral para refletir as alterações feitas nos gastos reais.
- Determine o alinhamento financeiro ao P & ls para assinaturas de unidade de negócios.
- Analise os métodos de relatório de valor e custo do stakeholder mensalmente.
- Corrija ativos subutilizados e determine se vale a pena continuar.
- Detectar inalinhamentos e anomalias entre o plano e os gastos reais.
- Auxilie as equipes de adoção da nuvem e a equipe de estratégia de nuvem com a compreensão e a resolução dessas anomalias.

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu o conceito de governança de identidade de nuvem, examine o [ferramentas de gerenciamento de custos](./toolchain.md) para identificar as ferramentas e os recursos do Azure que você precisará ao desenvolver a disciplina de governança de gerenciamento de custos na plataforma Azure.

> [!div class="nextstepaction"]
> [Ferramentas de gerenciamento de custos para o Azure](./toolchain.md)
