---
title: Nivelamento de gerenciamento entre disciplinas de gerenciamento de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Este artigo discute o nivelamento de gerenciamento entre as disciplinas de gerenciamento de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2e3aa2b27c503039d39bf3cc4a90b528f45d513e
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565176"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Nivelamento de gerenciamento entre disciplinas de gerenciamento de nuvem

As chaves para o gerenciamento adequado em qualquer ambiente são os processos de consistência e reproduzíveis. Há infinitas opções para as coisas que podem ser feitas no Azure. Da mesma forma, há inúmeras abordagens para o gerenciamento de nuvem. Para fornecer consistência e capacidade de repetição, é importante restringir essas opções a um conjunto consistente de processos e ferramentas de gerenciamento que serão oferecidos para cargas de trabalho hospedadas na nuvem.

## <a name="suggested-management-levels"></a>Níveis de gerenciamento sugeridos

Como as cargas de trabalho em seu portfólio de ti variam, é improvável que um único nível de gerenciamento seja suficiente para cada carga de trabalho. Para ajudá-lo a dar suporte a uma variedade de cargas de trabalho e compromissos de negócios, sugerimos que sua equipe de operações de nuvem ou a equipe de operações de plataforma estabeleça alguns níveis de gerenciamento de operações.

![Gerenciar níveis de gerenciamento e maturidade na estrutura de adoção de nuvem](../../_images/manage/cloud-management-maturity.png)

Como ponto de partida, considere estabelecer os níveis de gerenciamento mostrados no diagrama anterior e sugerido na lista a seguir:

- **Linha de base de gerenciamento:** Uma linha de base de gerenciamento de nuvem (ou linha de base de gerenciamento) é um conjunto definido de ferramentas, processos e preços consistentes que servem como base para todo o gerenciamento de nuvem no Azure. Para estabelecer uma linha de base de gerenciamento de nuvem e determinar quais ferramentas incluir na oferta de linha de base para sua empresa, examine a lista na seção "disciplinas de gerenciamento de nuvem".
- **Linha de base aprimorada:** Várias cargas de trabalho podem exigir aprimoramentos na linha de base que não são necessariamente específicas de uma única plataforma ou carga de trabalho. Embora esses aprimoramentos não sejam econômicos para cada carga de trabalho, deve haver processos, ferramentas e soluções comuns para qualquer carga de trabalho que possa justificar o custo do suporte de gerenciamento extra.
- **Especialização de plataforma:** Em qualquer ambiente específico, algumas plataformas comuns são usadas por uma variedade de cargas de trabalho. Essa semelhança geral da arquitetura não é alterada quando as empresas adotam a nuvem. A especialização de plataforma é um nível elevado de gerenciamento que aplica dados e experiência no assunto da arquitetura para fornecer um nível mais alto de gerenciamento operacional. Exemplos de especialização de plataforma incluem funções de gerenciamento específicas para SQL Server, contêineres, Active Directory ou outros serviços que podem ser gerenciados melhor por meio de processos, ferramentas e arquiteturas consistentes e reproduzíveis.
- **Especialização de carga de trabalho:** Para cargas de trabalho que são verdadeiramente essenciais, pode haver uma justificativa de custo para aprofundar-se no gerenciamento dessa carga de trabalho. A especialização de carga de trabalho aplica telemetria de carga de trabalho para determinar abordagens mais avançadas para gerenciamento diário. Esses mesmos dados geralmente identificam as melhorias de automação, implantação e design que poderiam levar a uma maior estabilidade, confiabilidade e resiliência além do que é possível apenas com o gerenciamento operacional.
- **Sem suporte:** É igualmente importante comunicar processos de gerenciamento comuns que não serão fornecidos por meio de disciplinas de gerenciamento de nuvem para cargas de trabalho que são classificadas como sem suporte ou não são críticas.

As organizações também podem optar por [terceirizar funções relacionadas a um ou mais desses níveis de gerenciamento para um provedor de serviços](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Esses provedores de serviços podem usar o [Lighthouse do Azure](https://azure.com/lighthouse) para fornecer maior precisão e transparência.

Os artigos restantes desta série descrevem vários processos que normalmente são encontrados em cada uma dessas disciplinas.
Em paralelo, o [Guia de gerenciamento do Azure](../azure-management-guide/index.md) demonstra as ferramentas que podem dar suporte a cada um desses processos. Para obter ajuda com a criação de sua linha de base de gerenciamento, comece com o guia de gerenciamento do Azure. Depois de estabelecer a linha de base, esta série de artigos e as práticas recomendadas a seguir podem ajudar a expandir essa linha de base para definir outros níveis de suporte de gerenciamento.

## <a name="cloud-management-disciplines"></a>Disciplinas de gerenciamento de nuvem

Cada nível de gerenciamento sugerido pode chamar uma variedade de disciplinas de gerenciamento de nuvem. No entanto, o mapeamento foi projetado para facilitar a localização dos processos e ferramentas sugeridos para fornecer o nível apropriado de gerenciamento de nuvem.

Na maioria dos casos, o *nível de linha de base de gerenciamento* discutido anteriormente consiste em processos e ferramentas das disciplinas a seguir. Em cada caso, alguns processos e ferramentas são realçados para demonstrar *funções de linha de base aprimoradas*.

- **Inventário e visibilidade:** No mínimo, uma linha de base de gerenciamento deve incluir um meio de inventariar ativos e criar visibilidade para o estado de execução de cada ativo.
- **Conformidade operacional:** O gerenciamento regular da configuração, do dimensionamento, do custo e do desempenho dos ativos é fundamental para manter as expectativas de desempenho e uma linha de base de gerenciamento.
- **Proteger e recuperar:** Minimizar as interrupções operacionais e acelerar a recuperação pode ajudá-lo a evitar perdas de desempenho e impactos de receita. Detecção e recuperação são aspectos essenciais dessa disciplina em qualquer linha de base de gerenciamento.

O nível de especialização da plataforma de gerenciamento Obtém os processos e as ferramentas que estão alinhados com as disciplinas de operações da plataforma. Da mesma forma, o nível de especialização da carga de trabalho de gerenciamento Obtém os processos e as ferramentas alinhados com as disciplinas de operações de carga de trabalho.

## <a name="next-steps"></a>Próximas etapas

A próxima etapa para definir cada nível de gerenciamento de nuvem é compreender o [inventário e a visibilidade](./inventory.md).

> [!div class="nextstepaction"]
> [Opções de inventário e visibilidade](./inventory.md)
