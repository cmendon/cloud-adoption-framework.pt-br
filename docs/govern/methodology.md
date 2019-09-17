---
title: Metodologia de governança de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Estabeleça uma compreensão básica da metodologia que impulsiona a governança de nuvem no Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/04/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: cc4567495d60f76be760d532dc16a66274834396
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026849"
---
# <a name="cloud-governance-methodology"></a>Metodologia de governança de nuvem

Adotar a nuvem é um percurso, não um destino. Ao longo do caminho, há marcos claros e benefícios comerciais tangíveis. No entanto, o estado final de adoção da nuvem é desconhecido quando uma empresa começa o percurso. A governança de nuvem cria as grades de proteção que mantêm a empresa em um caminho seguro durante todo o percurso.

A estrutura de adoção de nuvem fornece guias de governança que descrevem as experiências de empresas fictícias, que se baseiam nas experiências de clientes reais. Cada guia segue o cliente por entre os aspectos de governança da sua adoção da nuvem.

## <a name="envision-an-end-state"></a>Vislumbrar um estado final

Um percurso sem um destino é apenas um passeio. É importante estabelecer uma visão aproximada do estado final antes de dar o primeiro passo. O infográfico a seguir fornece um quadro de referência do estado final. Mesmo não sendo o seu ponto de partida, ele mostra seu potencial destino.

![Infográfico do modelo de governança do Cloud Adoption Framework](../_images/operational-transformation-govern-highres.png)

O modelo de governança do Cloud Adoption Framework identifica as principais áreas de importância durante o percurso. Cada área se relaciona com diferentes tipos de riscos que devem ser resolvidos pela a empresa conforme ela adota mais serviços de nuvem. Dentro dessa estrutura, o guia de governança identifica as ações necessárias para a equipe de governança de nuvem. Ao longo do caminho, cada princípio do modelo de governança do Cloud Adoption Framework é descrito com mais detalhes. No geral, incluem-se:

**Políticas corporativas:** As políticas corporativas orientam a governança de nuvem. O guia de governança se concentra nos aspectos específicos da política corporativa:

- **Riscos empresariais:** identificar e compreender os riscos corporativos.
- **Política e conformidade:** converter os riscos em instruções de política que dão suporte a requisitos de conformidade.
- **Processos:** garantir a conformidade às políticas de estado.

**Cinco disciplinas da governança de nuvem:** Essas disciplinas dão suporte às políticas corporativas. Cada disciplina protege a empresa contra possíveis armadilhas:

- Gerenciamento de Custos
- Linha de base de segurança
- Consistência de recursos
- Linha de base de identidade
- Aceleração de implantação

Essencialmente, as políticas corporativas atuam como um sistema de avisos antecipados para detectar possíveis problemas. As disciplinas ajudam a empresa a gerenciar riscos e criar grades de proteção.

## <a name="grow-to-the-end-state"></a>Expanda até o estado final

Como os requisitos de governança se alterarão durante todo o processo de adoção da nuvem, é necessária uma abordagem diferente para a governança. As empresas não podem mais esperar até que uma equipe pequena crie as grades de proteção e os roteiros de cada rodovia *antes de dar o primeiro passo*. Os resultados de negócios são esperados mais rapidamente e sem problemas. A governança de TI também deve se mover rapidamente e acompanhar o ritmo das demandas de negócios para permanecer relevante durante a adoção da nuvem e evitar a “TI sombra”.

Uma abordagem de **governança incremental** possibilita essas características. A governança incremental se baseia em um pequeno conjunto de políticas, processos e ferramentas corporativas para estabelecer uma fundação para a adoção e a governança. Essa fundação é chamada de **MVP (produto mínimo viável)** . Um MVP permite que a equipe de governança incorpore a governança rapidamente em implementações durante todo o ciclo de vida de adoção. Um MVP pode ser estabelecido a qualquer momento durante o processo de adoção da nuvem. No entanto, trata-se de uma boa prática adotar um MVP o quanto antes.

A capacidade de responder rapidamente aos riscos em mudança possibilita que a equipe da governança de nuvem se engaje de novas formas. A equipe de governança de nuvem pode se unir à equipe de estratégia de nuvem para observação, antecipar-se às equipes de adoção da nuvem, planejar rotas e estabelecer rapidamente proteções para gerenciar os riscos associados aos planos de adoção. Essas camadas de governança just-in-time são conhecidas como **iterações da governança**. Com essa abordagem, a estratégia de governança evolui um passo à frente das equipes de adoção da nuvem.

O diagrama a seguir mostra um MVP de governança simples e três iterações da governança. Durante as iterações, políticas corporativas adicionais são definidas para corrigir novos riscos. Depois, a disciplina de Aceleração de Implantação aplica essas alterações em cada implantação.

![Exemplo de melhoria incremental de governança](../_images/govern/incremental-governance-example.png)

> [!NOTE]
> A governança não é uma substituição para funções-chave, como segurança, rede, identidade, finanças, DevOps ou operações. Ao longo do caminho, haverá interações e dependências com membros de cada função. Esses membros devem ser incluídos na equipe de governança de nuvem para acelerar a tomada de decisões e ações.

## <a name="next-steps"></a>Próximas etapas

Use a [ferramenta de benchmark de governança](https://cafbaseline.com) da estrutura de adoção da nuvem para avaliar sua jornada de transformação e ajudá-lo a identificar lacunas em sua organização em seis domínios-chave, conforme definido na estrutura.

> [!div class="nextstepaction"]
> [Avaliar sua jornada de transformação](./benchmark.md)
