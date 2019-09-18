---
title: Introdução ao gerenciamento operacional
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Compreenda o gerenciamento operacional dentro do Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: manage
ms.openlocfilehash: 3abc103e09a11af4cb822dde985b96c56bca6242
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026387"
---
# <a name="establishing-operational-management-practices-in-the-cloud"></a>Estabelecimento de práticas de gerenciamento operacional na nuvem

A adoção da nuvem é um catalisador para habilitar o valor comercial. No entanto, o verdadeiro valor comercial é obtido por meio de operações em andamento e estáveis dos ativos de tecnologia implantados na nuvem. Esta seção do Cloud Adoption Framework orienta o leitor por várias transições em gerenciamento operacional na nuvem.

## <a name="actionable-best-practices"></a>Melhores práticas do StorSimple

Soluções de gerenciamento de operações modernas criam uma exibição de operações em várias nuvens. Ativos gerenciados por meio das melhores práticas a seguir podem residir na nuvem, em um data center existente ou até mesmo em um provedor de nuvem concorrente. Atualmente, a estrutura inclui duas melhores práticas de referência para orientar a maturidade do gerenciamento de operações na nuvem:

* [Gerenciamento do Servidor do Azure](./azure-server-management/index.md): Guia de integração para incorporar as ferramentas nativas da nuvem e serviços necessários para gerenciar operações.
* [Monitoramento híbrido](./monitor/index.md): Muitos clientes já fizeram um investimento substancial no System Center Operations Manager. Para esses clientes, este guia de monitoramento híbrido ajuda a comparar e contrastar as ferramentas de relatório nativas de nuvem com as ferramentas do Operations Manager. Essa comparação tornará mais fácil decidir quais ferramentas usar para fins de gerenciamento operacional.

## <a name="cloud-operations"></a>Operações de nuvem

Ambas essas melhores práticas levam a uma metodologia de estado futuro para o gerenciamento de operações.

![Metodologia de Gerenciamento da CAF](../_images/manage/caf-manage.png)

**Alinhamento de negócios:** Na metodologia de Gerenciamento, todas as cargas de trabalho são classificadas por importância e valor comercial. Essa classificação pode ser então medida por meio de uma análise de impacto, que calcula o valor perdido associado com a degradação do desempenho ou interrupções de negócios. Usando esse impacto tangível de receita, as equipes de operações de nuvem podem trabalhar com a empresa para estabelecer um compromisso que equilibra custo e desempenho.

**Disciplinas de operações de nuvem:** Depois que os negócios estão alinhados, é muito mais fácil acompanhar e relatar as disciplinas adequadas das operações em nuvem para cada carga de trabalho. A tomada de decisões ao longo de cada disciplina pode ser então convertida em termos de compromisso, os quais podem ser facilmente compreendidos pela empresa. Essa abordagem colaborativa transforma o stakeholder da empresa em um parceiro na busca do equilíbrio correto entre custo e desempenho.

* Inventário e visibilidade: No mínimo, o gerenciamento de operações requer um meio para inventário de ativos e criação de visibilidade sobre o estado da execução de cada ativo.
* Conformidade operacional: Regularmente, o gerenciamento de configuração, dimensionamento, custo e desempenho de ativos é a chave para manter as expectativas de desempenho.
* Proteger e recuperar: Minimizar interrupções operacionais e agilizar a recuperação são ações que, individualmente, ajudam a evitar perdas de desempenho e a impactos sobre a receita. Detecção e recuperação são aspectos essenciais desta disciplina.
* Operações de plataforma: Todos os ambientes de TI contêm um conjunto de plataformas comumente usadas. Essas plataformas podem incluir armazenamentos de dados como SQL Server ou HDInsights. Outras plataformas comuns podem incluir soluções de contêiner como Kubernetes ou AKS. Independentemente das plataformas, a maturidade de operações de plataforma enfatiza a personalização de operações com base em como essas plataformas comuns são implantadas, configuradas e usadas por cargas de trabalho.
* Operações de carga de trabalho: No nível mais alto de maturidade operacional, as equipes de operações de nuvem são capazes de ajustar as operações para cargas de trabalho que são cruciais para o sucesso dos negócios. Para essas cargas de trabalho de alto nível de importância, dados disponíveis podem ajudar a automatizar a correção, o dimensionamento ou a proteção de cargas de trabalho com base em sua utilização.

Diretrizes adicionais, tais como a [Estrutura de verificação do design (codinome: Princípios de design de nuvem)](https://docs.microsoft.com/azure/architecture/reliability) podem ajudar a tomar decisões arquiteturais detalhadas sobre cada carga de trabalho dentro das disciplinas acima.

Esta seção do Cloud Adoption Framework agregará a cada um desses tópicos, amadurecendo as operações na nuvem em sua organização.
