---
title: Metodologia de governança de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Estabeleça uma compreensão básica da metodologia que orienta a governança de nuvem na estrutura de adoção de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/04/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 431895263473481fbd43fc9c63d832a538a499db
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547398"
---
# <a name="cloud-governance-methodology"></a>Metodologia de governança de nuvem

A adoção da nuvem é uma jornada, não um destino. Ao longo do caminho, há Marcos claros e benefícios de negócios tangíveis. No entanto, o estado final da adoção de nuvem é desconhecido quando uma empresa começa a jornada. A governança de nuvem cria guardrails que mantêm a empresa em um caminho seguro durante toda a jornada.

A estrutura de adoção de nuvem fornece guias de governança que descrevem as experiências de empresas fictícias, que se baseiam nas experiências de clientes reais. Cada guia segue o cliente por meio dos aspectos de governança de sua adoção de nuvem.

## <a name="envision-an-end-state"></a>Previsionar um estado final

Uma jornada sem um destino de destino está apenas se esvagando. É importante estabelecer uma visão aproximada do estado final antes de dar a primeira etapa. O infográfico a seguir fornece um quadro de referência para o estado final. Não é seu ponto de partida, mas mostra o destino potencial.

![Infográfico do modelo de governança da estrutura de adoção da nuvem](../_images/operational-transformation-govern-highres.png)

O modelo de governança da estrutura de adoção da nuvem identifica as principais áreas de importância durante a jornada. Cada área está relacionada a diferentes tipos de riscos que a empresa deve resolver à medida que ele adota mais serviços de nuvem. Nessa estrutura, o guia de governança identifica as ações necessárias para a equipe de governança de nuvem. Ao longo do caminho, cada princípio do modelo de governança da estrutura de adoção da nuvem é descrito mais detalhadamente. Em grande escala, eles incluem:

**Políticas corporativas:** As políticas corporativas impulsionam a governança de nuvem. O guia de governança concentra-se em aspectos específicos da política corporativa:

- **Riscos de negócios:** Identificação e compreensão de riscos corporativos.
- **Política e conformidade:** Conversão de riscos em instruções de política que dão suporte a quaisquer requisitos de conformidade.
- **Processos:** Garantindo a adesão às políticas declaradas.

**Cinco disciplinas de governança de nuvem:** Essas disciplinas dão suporte às políticas corporativas. Cada disciplina protege a empresa contra possíveis armadilhas:

- Gerenciamento de Custos
- Linha de base de segurança
- Consistência de recursos
- Linha de base de identidade
- Aceleração da implantação

Basicamente, as políticas corporativas servem como o sistema de aviso antecipado para detectar possíveis problemas. As disciplinas ajudam a empresa a gerenciar riscos e a criar guardrails.

## <a name="grow-to-the-end-state"></a>Aumentar até o estado final

Como os requisitos de governança serão alterados em toda a jornada de adoção da nuvem, uma abordagem diferente para governança será necessária. As empresas não podem mais esperar que uma pequena equipe crie guardrails e roteiros em cada rodovia *antes de dar a primeira etapa*. Os resultados de negócios são esperados mais rapidamente e sem problemas. A governança de ti também deve se mover rapidamente e acompanhar as demandas comerciais para permanecer relevante durante a adoção da nuvem e evitar "Shadow IT".

Uma abordagem de **governança incremental** capacita essas características. A governança incremental depende de um pequeno conjunto de políticas, processos e ferramentas corporativas para estabelecer uma base para adoção e governança. Essa base é chamada de **produto viável mínimo (MVP)** . Um MVP permite que a equipe de governança incorpore rapidamente a governança em implementações em todo o ciclo de vida de adoção. Um MVP pode ser estabelecido a qualquer momento durante o processo de adoção da nuvem. No entanto, é uma boa prática adotar um MVP o mais cedo possível.

A capacidade de responder rapidamente aos riscos em alteração permite que a equipe de governança de nuvem se envolva de novas maneiras. A equipe de governança de nuvem pode participar da equipe de estratégia de nuvem como Scouts, passando pelas equipes de adoção de nuvem, plotando rotas e estabelecendo rapidamente o guardrails para gerenciar os riscos associados aos planos de adoção. Essas camadas de governança just-in-time são conhecidas como **iterações de governança**. Com essa abordagem, a estratégia de governança cresce um passo à frente das equipes de adoção de nuvem.

O diagrama a seguir mostra um MVP de governança simples e três iterações de governança. Durante as iterações, políticas corporativas adicionais são definidas para corrigir novos riscos. Em seguida, a disciplina de aceleração de implantação aplica essas alterações em cada implantação.

![Exemplo de melhoria de governança incremental](../_images/govern/incremental-governance-example.png)

> [!NOTE]
> A governança não é uma substituição para funções essenciais, como segurança, rede, identidade, finanças, DevOps ou operações. Ao longo do caminho, haverá interações e dependências de membros de cada função. Esses membros devem ser incluídos na equipe de governança de nuvem para acelerar as decisões e ações.

## <a name="next-steps"></a>Próximos passos

Use a [ferramenta de benchmark de governança](https://cafbaseline.com) da estrutura de adoção da nuvem para avaliar sua jornada de transformação e ajudá-lo a identificar lacunas em sua organização em seis domínios-chave, conforme definido na estrutura.

> [!div class="nextstepaction"]
> [Avaliar sua jornada de transformação](./benchmark.md)
