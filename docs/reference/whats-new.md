---
title: Novidades
description: Saiba mais sobre as atualizações para a estrutura de adoção do Microsoft Cloud para o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/02/2020
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: 0e93f0279ba210be594b3b5af40cf16657f224e3
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79095303"
---
# <a name="whats-new-in-the-microsoft-cloud-adoption-framework"></a>O que há de novo na estrutura de adoção de Microsoft Cloud

## <a name="fulfilling-the-vision"></a>Concretizando a visão

A estrutura atingiu a GA (disponibilidade geral). No entanto, ainda estamos criando ativamente essa estrutura em colaboração com clientes, parceiros e equipes internas. Para incentivar a parceria, o conteúdo é liberado quando ele se torna disponível. Essas versões públicas permitem testar, validar e refinar de forma incremental as diretrizes.

Alterações significativas são capturadas nas notas de versão a seguir.

## <a name="migration-update-03022020"></a>Atualização de migração: 03/02/2020

Esta versão respondeu a comentários sobre a continuidade da abordagem de migração por meio de várias metodologias, incluindo estratégia, plano, pronto e migrar. O objetivo desta versão era tornar mais fácil para os leitores entenderem o refinamento contínuo do planejamento e da adoção, à medida que os clientes continuam em uma jornada de migração. As seguintes alterações foram feitas para atender ao espírito desta versão:

### <a name="new-articles"></a>Novos artigos

- [Equilibrando prioridades concorrentes](../strategy/balance-competing-priorities.md): descreve o saldo em prioridades que ocorrem em cada metodologia para informar estratégias de clientes
- [Classificação durante os processos de avaliação](../migrate/migration-considerations/assess/classify.md): descreve a importância de classificar cada ativo e carga de trabalho antes da migração.

### <a name="restructure-landing-zone-process"></a>Reestruturar processo da zona de aterrissagem

A primeira zona de aterrissagem foi retirada do guia de preparação para servir como sua própria seção. Essa abordagem nos permite expandir o conceito de zonas de aterrissagem e opções de zona de aterrissagem. Isso também levou à criação de alguns novos artigos:

- [O que é uma zona de aterrissagem?](../ready/landing-zone/index.md): define a zona de aterrissagem do termo
- [Primeira zona de aterrissagem](../ready/landing-zone/first-landing-zone.md): expande na comparação de várias zonas de aterrissagem
- [Migrar zona de aterrissagem](../ready/landing-zone/migrate-landing-zone.md): moveu o artigo plano gráfico de zona de aterrissagem anterior, para separar a definição do plano gráfico CAF da seleção da primeira zona de aterrissagem, para permitir mais opções de zona de aterrissagem.
- Artigo da [zona de aterrissagem do Terraform](../ready/landing-zone/terraform-landing-zone.md) : movido da seção "escopo expandido" da metodologia pronta para a nova seção "zona de aterrissagem" da metodologia pronta, para tratar Terraform um cidadão de primeira classe na conversa da zona de aterrissagem.
- Agrupe as considerações de zona de aterrissagem básica em conjunto no sumário em "considerações básicas de zona de aterrissagem".
- Práticas recomendadas de segurança movidas da metodologia de migração para uma nova seção da zona de aterrissagem "melhorar a segurança da zona de aterrissagem (dados confidenciais)" para expor os leitores a essas diretrizes no início do ciclo de vida.

### <a name="refinements-to-the-azure-migration-guide"></a>Refinamentos para o guia de migração do Azure

Os padrões de tráfego do usuário sugerem que essa seção de conteúdo tem mais probabilidade de ser usada por implementadores e arquitetos durante a primeira migração. PARA dar melhor suporte a esse público, o foco do guia de migração foi refinado para melhor se alinhar com a intenção original de expor leitores para as ferramentas usadas durante uma primeira migração.

- [Visão geral](../migrate/azure-migration-guide/index.md): descrição mais clara do guia, com número reduzido de etapas.
- [Avaliar](../migrate/azure-migration-guide/assess.md): melhor ilustrar que a avaliação nesta fase se concentra na avaliação de um ajuste técnico de uma carga de trabalho específica e de ativos relacionados. Adicionada a seção de suposições desafiador para demonstrar quem esse nível de avaliação funciona com a abordagem de avaliação incremental mencionada pela primeira vez na metodologia do plano.
- [Migrar](../migrate/azure-migration-guide/migrate.md): em resposta a comentários nas conferências da camada 1, uma referência a UnifyCloud foi adicionada às opções da ferramenta de terceiros.
- [Teste, otimize e promova](../migrate/azure-migration-guide/optimize-and-transform.md): alinhar o título deste artigo com outras sugestões de aprimoramento do processo.

### <a name="refinements-to-migration-process-improvements"></a>Refinamentos para melhorias do processo de migração

- [Avalie a visão geral](../migrate/migration-considerations/assess/index.md): melhor ilustrar que a avaliação nesta fase se concentra na avaliação de um ajuste técnico de uma carga de trabalho específica e de ativos relacionados.
- [Lista de verificação de planejamento](../migrate/migration-considerations/prerequisites/planning-checklist.md): esclareça a importância do alinhamento de operações durante o planejamento de esforços de migração para garantir uma carga de trabalho bem gerenciada, após a migração.

### <a name="placement-of-related-articles"></a>Posicionamento de artigos relacionados

Cada lista de artigos abaixo foi movida. O tráfego é redirecionado para o novo local.

- Artigo de práticas [recomendadas de avaliação](../plan/contoso-migration-assessment.md) : movido da seção "práticas recomendadas" da metodologia de migração para a nova seção "prática recomendada" da metodologia do plano. Essa mudança expõe os leitores à prática de avaliar os ambientes locais anteriormente no ciclo de vida.
- [Equilibre o artigo do portfólio](../strategy/balance-the-portfolio.md) : movido da seção "escopo expandido" da metodologia de migração para a metodologia de estratégia. Essa mudança expõe os leitores a esse processo de pensamento anteriormente no ciclo de vida.

### <a name="alignment-of-the-changes"></a>Alinhamento das alterações

- [Visão geral pronta](../ready/index.md): Atualize as quatro etapas na visão geral pronta para refletir o processo refinado
- [Visão geral da migração](../migrate/index.md): Atualize as etapas na visão geral de migração para refletir o processo refinado
- [Gráfico de metodologia de migração](../migrate/index.md): atualizar para a imagem de metodologia para refletir as alterações
- [Gráfico de visão geral](../index.md): atualizações para o gráfico de visão geral para refletir as alterações
