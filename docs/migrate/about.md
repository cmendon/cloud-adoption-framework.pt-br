---
title: Migração na nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução ao conteúdo de Migração na Nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 6bbd3ffe401a3e886ee1f91072a715002ab5e836
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547241"
---
# <a name="cloud-migration-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Migração na nuvem na estrutura de adoção Microsoft Cloud para o Azure

A migração na nuvem é o processo de mover ativos digitais existentes para uma plataforma de nuvem. Nessa abordagem, os ativos existentes são replicados para a nuvem com modificações mínimas. Quando um aplicativo ou uma carga de trabalho está operacional na nuvem, os usuários são transferidos da solução existente para a solução de nuvem. A migração na nuvem é um meio de balancear efetivamente um portfólio de nuvem. Geralmente, essa é a abordagem mais rápida e ágil em curto prazo. Por outro lado, alguns dos benefícios da nuvem podem não ser percebidos por meio dessa abordagem sem modificação futura adicional. Empresas e clientes de médio porte usam essa abordagem para acelerar o ritmo de alteração, evitar despesas de capital planejadas e reduzir custos operacionais contínuos.

## <a name="cloud-migration-guidance"></a>Diretrizes de migração na nuvem

As diretrizes nesta seção da estrutura de adoção de nuvem são projetadas para duas finalidades:

- Forneça guias de migração acionáveis que representem experiências comuns que os clientes geralmente encontram. Cada guia encapsula o processo e as ferramentas necessárias para serem bem-sucedidas em um esforço de migração na nuvem. Por necessidade, as diretrizes de design são específicas do Azure. Todas as outras recomendações contidas nesses guias podem ser aplicadas como parte de uma abordagem de nuvem ou que não é independente de Cloud.
- Ajude os leitores a criar planos de migração personalizados que possam atender a uma variedade de necessidades comerciais, incluindo a migração para várias nuvens públicas, por meio de orientações detalhadas sobre o desenvolvimento de processos, funções e responsabilidades e controles de gerenciamento de alterações.

Este conteúdo destina-se à equipe de adoção de nuvem. Também é relevante para os arquitetos de nuvem que precisam desenvolver uma base sólida na migração na nuvem.

## <a name="intended-audience"></a>Público-alvo

A orientação na estrutura de adoção de nuvem afeta a empresa, a tecnologia e a cultura das empresas. Esta seção afeta significativamente os proprietários dos aplicativos, a equipe de gerenciamento de mudanças (como o PMO e o departamento de gerenciamento Agile) e os líderes de linha de negócios e a equipe de adoção de nuvem. Há várias dependências nessas pessoas que exigirão a facilitação pelos arquitetos de nuvem usando essas diretrizes. A facilitação com essas equipes pode ser um esforço único, mas em alguns casos, isso resultará em interações recorrentes com essas outras pessoas.

O arquiteto de nuvem serve como líder de idéias e facilitador para trazer esses públicos juntos. O conteúdo desta coleção de guias foi projetado para ajudar o arquiteto de nuvem a facilitar a conversa certa, com o público certo, para impulsionar as decisões necessárias. A transformação de negócios que é habilitada pela nuvem depende da função do arquiteto de nuvem para ajudar a orientar as decisões em toda a empresa e na ti.

**Especialização de arquiteto de nuvem nesta seção:** Cada seção da estrutura de adoção de nuvem representa uma especialização ou variante diferente da função de arquiteto de nuvem. Esta seção foi projetada para arquitetos de nuvem com experiência no assunto sobre o ambiente local existente e como isso afeta as opções de migração.

**Separação de tarefas:** Em muitas empresas, a separação de tarefas existe para limitar o acesso a sistemas de produção ou segmentos do ambiente corporativo. Nesse caso, o processo de migração se torna mais complexo. Em alguns casos, essas funções e responsabilidades podem exigir vários arquitetos de nuvem para abranger todo o processo de migração.

**Opções de parceria** Em cada um desses processos, as equipes aprenderão novas habilidades e abordagens para a execução técnica. A expansão de habilidades técnicas entre os membros da equipe existentes é uma opção durante a execução. Contratando outra equipe adicional. A parceria com terceiros muitas vezes pode fornecer aceleração significativa e reduções de riscos. [As opções de parceria](./migration-considerations/assess/partnership-options.md) podem ajudar a orientar as decisões para escolher a melhor opção de parceria.

## <a name="next-steps"></a>Próximos passos

Para os leitores que desejam seguir este guia do início ao fim, esse conteúdo ajudará a desenvolver uma estratégia de migração de nuvem robusta. As diretrizes orientam o leitor por meio da teoria e da implementação dessa estratégia.

Como uma primeira etapa, é recomendável que os leitores trabalhem no [Guia de migração do Azure](./azure-migration-guide/index.md) para entender o conjunto padrão de ferramentas e as abordagens necessárias para a migração em um caso de uso comum. Posteriormente, as diretrizes de linha de base podem ser expandidas para atender às necessidades dos leitores por meio de [cenários complexos de migração](./expanded-scope/index.md), [práticas recomendadas de migração](./azure-best-practices/index.md)e [considerações de migração](./migration-considerations/index.md).

> [!div class="nextstepaction"]
> [Guia de migração do Azure](./azure-migration-guide/index.md)
