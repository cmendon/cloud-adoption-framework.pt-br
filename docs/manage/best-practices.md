---
title: Introdução ao gerenciamento operacional
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Entenda o gerenciamento operacional dentro da estrutura de adoção de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 46af630c299f1fb66565cf1d55e5acf9f36d8251
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683656"
---
# <a name="establishing-operational-management-practices-in-the-cloud"></a>Estabelecendo práticas de gerenciamento operacional na nuvem

A adoção de nuvem é um Catalyst para habilitar o valor comercial. No entanto, o valor comercial real é realizado por meio de operações contínuas e estáveis dos ativos de tecnologia implantados na nuvem. Esta seção da estrutura de adoção de nuvem, orienta o leitor por meio de várias transições para o gerenciamento operacional na nuvem.

## <a name="actionable-best-practices"></a>Práticas recomendadas acionáveis

As soluções modernas de gerenciamento de operações criam uma exibição de operações de nuvem. Os ativos gerenciados por meio das seguintes práticas recomendadas podem residir na nuvem, em um datacenter existente ou até mesmo em um provedor de nuvem concorrente. Atualmente, a estrutura inclui duas práticas recomendadas de referência para orientar a maturidade do gerenciamento de operações na nuvem:

- [Gerenciamento de servidor do Azure](./azure-server-management/index.md): guia de integração para incorporar as ferramentas e os serviços nativos da nuvem necessários para gerenciar as operações.
- [Monitoramento híbrido](./monitor/index.md): muitos clientes já fizeram um investimento substancial em System Center Operations Manager. Para esses clientes, este guia para o monitoramento híbrido ajuda a comparar e contrastar as ferramentas de relatório nativas de nuvem com ferramentas de Operations Manager. Essa comparação fará com que seja mais fácil decidir quais ferramentas usar para o gerenciamento operacional.

## <a name="cloud-operations"></a>Operações de nuvem

Essas duas práticas recomendadas se desenvolvem para uma metodologia de estado futuro para o gerenciamento de operações.

![Gerenciar a metodologia da estrutura de adoção de nuvem](../_images/manage/caf-manage.png)

**Alinhamento de negócios:** Na metodologia gerenciar, todas as cargas de trabalho são classificadas por criticalidade e valor comercial. Essa classificação pode então ser medida por meio de uma análise de impacto, que calcula o valor perdido associado à degradação do desempenho ou interrupções de negócios. Usando esse impacto tangível sobre a receita, as equipes de operações de nuvem podem trabalhar com a empresa para estabelecer um compromisso que equilibre o custo e o desempenho.

**Disciplinas de operações de nuvem:** Quando a empresa está alinhada, é muito mais fácil acompanhar e relatar as disciplinas adequadas de operações de nuvem para cada carga de trabalho. Tomar decisões ao longo de cada disciplina pode então ser convertida em termos de compromisso que podem ser facilmente compreendidos pela empresa. Essa abordagem colaborativa torna a empresa Stakeholder um parceiro para encontrar o equilíbrio certo entre custo e desempenho.

- **Inventário e visibilidade:** No mínimo, o gerenciamento de operações requer um meio de inventariar ativos e criar visibilidade para o estado de execução de cada ativo.
- **Conformidade operacional:** O gerenciamento regular da configuração, do dimensionamento, do custo e do desempenho dos ativos é fundamental para manter as expectativas de desempenho.
- **Proteger e recuperar:** Minimizando interrupções operacionais e acelerando a recuperação cada ajuda para evitar perdas de desempenho e impactos de receita. Detecção e recuperação são aspectos essenciais dessa disciplina.
- **Operações de plataforma:** Todos os ambientes de ti contêm um conjunto de plataformas usadas com frequência. Essas plataformas podem incluir armazenamentos de dados como SQL Server ou HDInsight. Outras plataformas comuns podem incluir soluções de contêiner como kubernetes ou AKS. Independentemente das plataformas, a maturidade das operações da plataforma se concentra na personalização de operações com base em como essas plataformas comuns são implantadas, configuradas e usadas por cargas de trabalho.
- **Operações de carga de trabalho:** No nível mais alto de maturidade operacional, as equipes de operações de nuvem são capazes de ajustar as operações de cargas de trabalho que são cruciais para o sucesso dos negócios. Para essas cargas de trabalho de alta importância, os dados disponíveis podem ajudar a automatizar a correção, o dimensionamento ou a proteção de cargas de trabalho com base em sua utilização.

Diretrizes adicionais como a [estrutura de análise de design (codinome: princípios de design de nuvem)](https://docs.microsoft.com/azure/architecture/reliability) podem ajudar a fazer decisões de arquitetura detalhadas em relação a cada carga de trabalho, dentro das disciplinas acima.

Esta seção da estrutura de adoção de nuvem será criada em cada um desses tópicos para operações de nuvem maduras em sua organização.
