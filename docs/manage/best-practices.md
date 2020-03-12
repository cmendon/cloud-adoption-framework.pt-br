---
title: Introdução ao gerenciamento operacional
description: Use a estrutura de adoção de nuvem para o Azure para entender as várias transições que devem ser feitas para habilitar o gerenciamento operacional na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: d2e6434dc43ae7de4873384901ac73804c3d586d
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092086"
---
# <a name="establish-operational-management-practices-in-the-cloud"></a>Estabelecer práticas de gerenciamento operacional na nuvem

A adoção da nuvem é um catalisador para habilitar o valor comercial. No entanto, o verdadeiro valor comercial é obtido por meio de operações em andamento e estáveis dos ativos de tecnologia implantados na nuvem. Esta seção da estrutura de adoção de nuvem orienta você por várias transições no gerenciamento operacional na nuvem.

## <a name="actionable-best-practices"></a>Melhores práticas acionáveis

As soluções modernas de gerenciamento de operações criam uma exibição de operações de nuvem. Os ativos gerenciados por meio das seguintes práticas recomendadas podem residir na nuvem, em um datacenter existente ou até mesmo em um provedor de nuvem concorrente. Atualmente, a estrutura inclui duas referências de práticas recomendadas para orientar a maturidade do gerenciamento de operações na nuvem:

- [Gerenciamento de servidor do Azure](./azure-server-management/index.md): um guia de integração para incorporar as ferramentas e os serviços nativos da nuvem necessários para gerenciar as operações.
- [Monitoramento híbrido](./monitor/index.md): muitos clientes já fizeram um investimento substancial em System Center Operations Manager. Para esses clientes, este guia para monitoramento híbrido pode ajudá-los a comparar e contrastar as ferramentas de relatório nativas de nuvem com Operations Manager ferramentas. Essa comparação torna mais fácil decidir quais ferramentas usar para o gerenciamento operacional.

## <a name="cloud-operations"></a>Operações de nuvem

Essas duas práticas recomendadas se desenvolvem em uma metodologia de estado futuro para o gerenciamento de operações, conforme ilustrado no diagrama a seguir:

![Gerenciar a metodologia da estrutura de adoção de nuvem](../_images/manage/caf-manage.png)

**Alinhamento de negócios:** Na metodologia gerenciar, todas as cargas de trabalho são classificadas por criticalidade e valor comercial. Essa classificação pode ser então medida por meio de uma análise de impacto, que calcula o valor perdido associado com a degradação do desempenho ou interrupções de negócios. Usando esse impacto tangível de receita, as equipes de operações de nuvem podem trabalhar com a empresa para estabelecer um compromisso que equilibra custo e desempenho.

**Disciplinas de operações de nuvem:** Depois que a empresa está alinhada, é muito mais fácil acompanhar e relatar as disciplinas adequadas de operações de nuvem para cada carga de trabalho. Tomar decisões ao longo de cada disciplina pode então ser convertida em termos de compromisso que podem ser facilmente compreendidos pela empresa. Essa abordagem colaborativa transforma o stakeholder da empresa em um parceiro na busca do equilíbrio correto entre custo e desempenho.

- **Inventário e visibilidade:** No mínimo, o gerenciamento de operações requer um meio de inventariar ativos e criar visibilidade para o estado de execução de cada ativo.
- **Conformidade operacional:** O gerenciamento regular da configuração, do dimensionamento, do custo e do desempenho dos ativos é fundamental para manter as expectativas de desempenho.
- **Proteger e recuperar:** Minimizar as interrupções operacionais e acelerar a recuperação ajuda a empresa a evitar perdas de desempenho e impactos de receita negativa. Detecção e recuperação são aspectos essenciais desta disciplina.
- **Operações de plataforma:** Todos os ambientes de ti contêm um conjunto de plataformas usadas com frequência. Essas plataformas podem incluir armazenamentos de dados como o SQL Server ou o Azure HDInsight. Outras plataformas comuns podem incluir soluções de contêiner, como o AKS (serviço kubernetes do Azure). Independentemente da plataforma, a maturidade das operações da plataforma se concentra na personalização de operações com base em como as plataformas comuns são implantadas, configuradas e usadas por cargas de trabalho.
- **Operações de carga de trabalho:** No nível mais alto de maturidade operacional, as equipes de operações de nuvem podem ajustar as operações para cargas de trabalho críticas. Para essas cargas de trabalho, os dados disponíveis podem ajudar a automatizar a correção, o dimensionamento ou a proteção de cargas de trabalho com base em sua utilização.

Diretrizes adicionais, como a [estrutura de análise de design (nome do código: princípios de design de nuvem)](https://docs.microsoft.com/azure/architecture/framework/resiliency/overview), podem ajudá-lo a tomar decisões de arquitetura detalhadas sobre cada carga de trabalho, nas disciplinas descritas anteriormente.

Esta seção da estrutura de adoção de nuvem será criada em cada um dos tópicos anteriores para ajudar a promover operações de nuvem maduras em sua organização.
