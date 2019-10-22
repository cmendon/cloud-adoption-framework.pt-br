---
title: Nivelamento de gerenciamento entre disciplinas de gerenciamento de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Nivelamento de gerenciamento entre disciplinas de gerenciamento de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 294ea288af478e0e451c9fd38663a26acb10359d
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682584"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Nivelamento de gerenciamento entre disciplinas de gerenciamento de nuvem

A chave para o gerenciamento adequado em qualquer ambiente é a consistência e os processos repetíveis. Há infinitas opções para as coisas que podem ser feitas no Azure. Da mesma forma, há inúmeras abordagens para o gerenciamento de nuvem. Para fornecer consistência e capacidade de repetição, é importante restringir essas opções a um conjunto consistente de processos e ferramentas de gerenciamento que serão oferecidos para cargas de trabalho hospedadas na nuvem.

## <a name="suggested-management-levels"></a>Níveis de gerenciamento sugeridos

Como as cargas de trabalho no seu portfólio de ti não são as mesmas, é improvável que um único nível de gerenciamento seja suficiente para cada carga de trabalho. Para dar suporte a várias cargas de trabalho e a vários compromissos de negócios, é recomendável que a equipe de operações de nuvem ou a equipe de operações do Cloud estabeleça alguns níveis de gerenciamento de operações.

![Gerenciar níveis de gerenciamento e maturidade na estrutura de adoção de nuvem](../../_images/manage/cloud-management-maturity.png)

Os seguintes níveis de gerenciamento (também mostrados acima) são alguns níveis sugeridos para servir como ponto de partida:

- **Linha**de base de gerenciamento: uma linha de base de gerenciamento de nuvem (ou linha de base de gerenciamento) é o conjunto definido de ferramentas, processos e preços consistentes que servirão como base para todo o gerenciamento de nuvem no Azure. Para estabelecer uma linha de base de gerenciamento de nuvem, examine a tabela na seção a seguir e determine quais ferramentas serão incluídas na oferta de linha de base para seu negócio.
- **Linha de base aprimorada**: várias cargas de trabalho podem exigir melhorias na linha de base que não são necessariamente específicas para uma única plataforma ou carga de trabalho. Embora esses aprimoramentos não sejam econômicos para cada carga de trabalho, deve haver processos, ferramentas e soluções comuns para qualquer carga de trabalho que possa justificar a justificação do suporte extra ao gerenciamento.
- **Especialização de plataforma**: em qualquer ambiente específico, há plataformas comuns que são usadas por várias cargas de trabalho diferentes. Essa semelhança geral da arquitetura não é alterada quando as empresas adotam a nuvem. A especialização de plataforma é um nível elevado de gerenciamento que aproveita os dados e a experiência do assunto da arquitetura para fornecer um nível mais alto de gerenciamento operacional. Exemplos de especialização de plataforma incluem funções de gerenciamento específicas para SQL Server, contêineres, Active Directory ou outros serviços que podem ser gerenciados melhor por meio de processos, ferramentas e arquiteturas consistentes e reproduzíveis.
- **Especialização de carga de trabalho**: para as cargas de trabalho que são verdadeiramente essenciais, pode haver uma justificativa de custo para aprofundar-se no gerenciamento dessa carga de trabalho. A especialização de carga de trabalho aproveita a telemetria de carga de trabalho para determinar abordagens mais avançadas para gerenciamento diário. Esses mesmos dados geralmente identificam as melhorias de automação, implantação e design que poderiam levar a uma maior estabilidade, confiabilidade e resiliência além do que é possível apenas com o gerenciamento operacional.
- **Sem suporte**: é igualmente importante comunicar processos de gerenciamento comuns que não serão fornecidos por meio de disciplinas de gerenciamento de nuvem para qualquer carga de trabalho classificada como sem suporte ou não crítica.

Os artigos restantes desta série descreverão vários processos normalmente encontrados em cada uma dessas disciplinas.
Em paralelo, o [Guia de gerenciamento do Azure](../azure-management-guide/index.md) demonstra as ferramentas que podem dar suporte a cada um desses processos. Para obter ajuda para criar sua linha de base de gerenciamento, comece com o guia de gerenciamento do Azure. Depois que a linha de base é estabelecida, esta série de artigos e as práticas recomendadas a seguir podem ajudar a expandir essa linha de base para definir outros níveis de suporte de gerenciamento.

## <a name="cloud-management-disciplines"></a>Disciplinas de gerenciamento de nuvem

Cada um dos níveis de gerenciamento sugeridos pode chamar diferentes disciplinas de gerenciamento de nuvem. No entanto, o mapeamento foi projetado para facilitar a localização dos processos e ferramentas sugeridos para fornecer o nível apropriado de gerenciamento de nuvem.

Na maioria dos casos, o "nível de linha de base de gerenciamento" descrito acima consistirá em processos e ferramentas das disciplinas a seguir. Em cada caso, alguns processos e ferramentas são realçados para demonstrar "funções de linha de base aprimoradas".

- **Inventário e visibilidade**: no mínimo, uma linha de base de gerenciamento deve incluir um meio de inventariar ativos e criar visibilidade no estado de execução de cada ativo.
- **Conformidade operacional:** O gerenciamento regular da configuração, do dimensionamento, do custo e do desempenho dos ativos é fundamental para manter as expectativas de desempenho e uma linha de base de gerenciamento.
- **Proteger e recuperar:** Minimizando interrupções operacionais e acelerando a recuperação cada ajuda para evitar perdas de desempenho e impactos de receita. Detecção e recuperação são aspectos essenciais dessa disciplina em qualquer linha de base de gerenciamento.

O nível de especialização da plataforma de gerenciamento Obtém os processos e as ferramentas alinhados às disciplinas de operações da plataforma.
Da mesma forma, o nível de especialização da carga de trabalho de gerenciamento Obtém os processos e as ferramentas alinhados às disciplinas de operações de carga de trabalho.
  
## <a name="next-steps"></a>Próximos passos

A próxima etapa para definir cada nível de gerenciamento de nuvem é compreender o [inventário e a visibilidade](./inventory.md).

> [!div class="nextstepaction"]
> [Opções de inventário e visibilidade](./inventory.md)
