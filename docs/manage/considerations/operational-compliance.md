---
title: Conformidade operacional-gerenciamento e operações de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Conformidade operacional-gerenciamento e operações de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: bb6e4584da87d992f85b6ce90e21081c9c19d7c3
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682536"
---
# <a name="operational-compliance-in-cloud-management"></a>Conformidade operacional no gerenciamento de nuvem

A conformidade operacional baseia-se na disciplina de [inventário e visibilidade](./inventory.md), como a primeira etapa acionável do gerenciamento de nuvem. Essa disciplina concentra-se em análises regulares de telemetria e esforços de correção (correções proativas e reativas). Essa disciplina é a base para manter o equilíbrio entre segurança, governança, desempenho e custo.

## <a name="components-of-operations-compliance"></a>Componentes de conformidade de operações

Manter a conformidade com compromissos operacionais requer análise, automação e correção humana. A conformidade operacional efetiva requer consistência em alguns processos críticos:

1. Consistência de recursos
2. Consistência do ambiente
3. Consistência de configuração de recurso
4. Consistência da atualização
5. Automação de correção

### <a name="resource-consistency"></a>Consistência de recursos

A etapa mais eficaz que uma equipe de gerenciamento de nuvem pode levar em direção à conformidade operacional é estabelecer a consistência na organização de recursos e na marcação. Quando os recursos são organizados e marcados consistentemente, todas as outras tarefas operacionais tornam-se mais fáceis. Para obter uma orientação mais profunda sobre a consistência de recursos, consulte a [fase de governança](../../govern/index.md) do ciclo de vida de adoção da nuvem. Especificamente, os [artigos iniciais do Governance Foundation](../../govern/initial-foundation.md) demonstram exemplos de maneiras de começar a desenvolver a consistência de recursos.

### <a name="environment-consistency"></a>Consistência do ambiente

Ambientes consistentes, ou zonas de pouso, é a próxima etapa mais importante para a conformidade operacional. Quando as zonas de aterrissagem são consistentes e impostas por meio de ferramentas automatizadas, elas são significativamente menos complexas para diagnosticar e resolver problemas operacionais. Para obter uma orientação mais profunda sobre a consistência do ambiente, consulte a [fase pronta](../../ready/index.md) do ciclo de vida de adoção da nuvem. Os exercícios dessa fase estabelecem um processo repetível para definir e desenvolver uma abordagem consistente e de primeiro código para o desenvolvimento de ambientes baseados em nuvem.

### <a name="resource-configuration-consistency"></a>Consistência de configuração de recurso

Com base nas abordagens de governança e preparação, o gerenciamento de nuvem deve incluir processos para o monitoramento e a avaliação contínuas de adesão aos requisitos de consistência de recursos. À medida que as cargas de trabalho mudam ou novas versões são adotadas, é vital que os processos de gerenciamento de nuvem avaliem as alterações de configuração, que não são facilmente regulamentadas por meio de meios automatizados.

Quando inconsistências são descobertas, algumas são resolvidas pela consistência nas atualizações e outras podem ser corrigidas automaticamente.

### <a name="update-consistency"></a>Consistência da atualização

A estabilidade pode levar a operações estáveis. Mas, algumas alterações são necessárias nos processos de gerenciamento de nuvem. Em particular, as alterações de desempenho e aplicação de patch regulares são essenciais para reduzir as interrupções e controlar os custos.

Um dos muitos valores de uma metodologia de gerenciamento de nuvem maduro é estabilizar e controlar a alteração necessária.

Qualquer linha de base de gerenciamento de nuvem deve incluir um meio de agendar, controlar e possivelmente automatizar as atualizações necessárias. Essas atualizações devem incluir patches no mínimo, mas também podem incluir desempenho, dimensionamento e outros aspectos da atualização de ativos.

### <a name="remediation-automation"></a>Automação de correção

Como uma linha de base aprimorada para gerenciamento de nuvem, algumas cargas de trabalho podem se beneficiar da correção automatizada. Quando uma carga de trabalho normalmente encontra problemas que não podem ser resolvidos por meio de alterações de código ou arquitetura, a automação de correção pode reduzir a carga do gerenciamento de nuvem e aumentar a satisfação do usuário.

Muitos argumentam que qualquer problema, que é comum o suficiente para automatizar, deve ser resolvido por meio da resolução da dívida técnica. Quando a resolução a longo prazo é prudente, ela deve ser a opção padrão. No entanto, há vários cenários de negócios que dificultam a justificação de grandes investimentos na resolução da dívida técnica. Quando a resolução técnica de dívidas não pode ser justificada, mas a correção é uma carga comum e dispendiosa, a solução de correção automatizada é a próxima melhor.

## <a name="next-steps"></a>Próximos passos

[Proteção e recuperação](./protect.md) são as próximas áreas a serem consideradas em uma linha de base de gerenciamento de nuvem.

> [!div class="nextstepaction"]
> [Proteger e recuperar](./protect.md)
