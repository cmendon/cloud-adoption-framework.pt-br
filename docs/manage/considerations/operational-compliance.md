---
title: Conformidade operacional no gerenciamento de nuvem
description: Use a estrutura de adoção de nuvem para o Azure para saber como manter a conformidade com os compromissos operacionais.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 894208ff08a0100e8d5d8d5d9df3eff592773426
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78340971"
---
# <a name="operational-compliance-in-cloud-management"></a>Conformidade operacional no gerenciamento de nuvem

A conformidade operacional baseia-se na disciplina de [inventário e visibilidade](./inventory.md). Como a primeira etapa acionável do gerenciamento de nuvem, essa disciplina se concentra em análises regulares de telemetria e esforços de correção (correções proativas e reativas). Essa disciplina é a base para manter o equilíbrio entre segurança, governança, desempenho e custo.

## <a name="components-of-operations-compliance"></a>Componentes de conformidade de operações

Manter a conformidade com compromissos operacionais requer análise, automação e correção humana. A conformidade operacional efetiva requer consistência em alguns processos críticos:

- Consistência de recursos
- Consistência do ambiente
- Consistência de configuração de recurso
- Consistência da atualização
- Automação de correção

### <a name="resource-consistency"></a>Consistência de recursos

A etapa mais eficaz que uma equipe de gerenciamento de nuvem pode levar em direção à conformidade operacional é estabelecer a consistência na organização de recursos e na marcação. Quando os recursos são organizados e marcados consistentemente, todas as outras tarefas operacionais tornam-se mais fáceis. Para obter uma orientação mais profunda sobre a consistência de recursos, consulte a [fase de governança](../../govern/index.md) do ciclo de vida de adoção da nuvem. Especificamente, os [artigos iniciais do Governance Foundation](../../govern/initial-foundation.md) demonstram como começar a desenvolver a consistência de recursos.

### <a name="environment-consistency"></a>Consistência do ambiente

Estabelecer ambientes consistentes, ou zonas de aterrissagem, é a próxima etapa mais importante para a conformidade operacional. Quando as zonas de aterrissagem são consistentes e impostas por meio de ferramentas automatizadas, elas são significativamente menos complexas para diagnosticar e resolver problemas operacionais. Para obter uma orientação mais profunda sobre a consistência do ambiente, consulte a [fase pronta](../../ready/index.md) do ciclo de vida de adoção da nuvem. Os exercícios dessa fase ajudam a criar um processo repetível para definir e desenvolver uma abordagem consistente e de primeiro código para o desenvolvimento de ambientes baseados em nuvem.

### <a name="resource-configuration-consistency"></a>Consistência de configuração de recurso

Conforme se baseia nas abordagens de governança e preparação, o gerenciamento de nuvem deve incluir processos para o monitoramento e a avaliação contínuos de sua adesão aos requisitos de consistência de recursos. À medida que as cargas de trabalho mudam ou novas versões são adotadas, é vital que os processos de gerenciamento de nuvem avaliem as alterações de configuração, que não são facilmente regulamentadas por meio da automação.

Quando inconsistências são descobertas, algumas são resolvidas pela consistência nas atualizações e outras podem ser corrigidas automaticamente.

### <a name="update-consistency"></a>Consistência da atualização

A estabilidade na abordagem pode levar a operações mais estáveis. Mas algumas alterações são necessárias nos processos de gerenciamento de nuvem. Em particular, as alterações de desempenho e aplicação de patch regulares são essenciais para reduzir as interrupções e controlar os custos.

Um dos muitos valores de uma metodologia de gerenciamento de nuvem maduro é o foco na estabilização e no controle da alteração necessária.

Qualquer linha de base de gerenciamento de nuvem deve incluir um meio de agendar, controlar e possivelmente automatizar as atualizações necessárias. Essas atualizações devem incluir patches no mínimo, mas também podem incluir desempenho, dimensionamento e outros aspectos da atualização de ativos.

### <a name="remediation-automation"></a>Automação de correção

Como uma linha de base aprimorada para gerenciamento de nuvem, algumas cargas de trabalho podem se beneficiar da correção automatizada. Quando uma carga de trabalho normalmente encontra problemas que não podem ser resolvidos por meio de alterações de código ou arquitetura, a automatização da correção pode ajudar a reduzir a carga do gerenciamento de nuvem e aumentar a satisfação do usuário.

Muitos argumentam que qualquer problema que seja comum o suficiente para automatizar deve ser resolvido por meio da resolução da dívida técnica. Quando uma resolução de longo prazo é prudente, ela deve ser a opção padrão. No entanto, vários cenários de negócios dificultam a justificação de grandes investimentos na resolução da dívida técnica. Quando essa resolução não pode ser justificada, mas a correção é uma carga comum e dispendiosa, a solução de correção automatizada é a próxima melhor.

## <a name="next-steps"></a>Próximas etapas

[Proteção e recuperação](./protect.md) são as próximas áreas a serem consideradas em uma linha de base de gerenciamento de nuvem.

> [!div class="nextstepaction"]
> [Proteger e recuperar](./protect.md)
