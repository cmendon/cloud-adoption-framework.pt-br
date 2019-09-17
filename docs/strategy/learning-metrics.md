---
title: Como podemos alinhar esforços às métricas de aprendizagem significativas?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação do conceito de métricas de aprendizado
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: f761f85fa4b21b35e8428985707176624b92a5ec
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030466"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-can-we-align-efforts-to-meaningful-learning-metrics"></a>Como podemos alinhar esforços às métricas de aprendizagem significativas?

A [visão geral dos resultados de negócios](./business-outcomes/index.md) abordou maneiras de medir e comunicar o impacto que uma transformação terá sobre os negócios. Infelizmente, pode levar alguns anos para que alguns desses resultados sejam produzidos por um resultado mensurável. O quadro e o conjunto C são insatisfeitos com relatórios que mostram um Delta de 0% por longos períodos de tempo.

As métricas de aprendizado são métricas provisórias e de curto prazo que podem ser vinculadas de volta a resultados de negócios de longo prazo. Essas métricas se alinham bem com uma mentalidade de crescimento e ajudam a posicionar a cultura para se tornar mais resiliente. Em vez de realçar a falta prevista de progresso em direção a uma meta de negócios de longo prazo, as métricas de aprendizado realçam os indicadores iniciais de sucesso. As métricas também realçam indicadores antecipados de falha, o que provavelmente produzirá a maior oportunidade para você aprender e ajustar o plano.

Como com grande parte do material nessa estrutura, vamos supor que você esteja familiarizado com a [jornada de transformação](../govern/guides/index.md) que melhor se alinha aos resultados comerciais desejados. Este artigo descreverá algumas métricas de aprendizagem para cada jornada de transformação para ilustrar o conceito.

## <a name="cloud-migration"></a>Migração na nuvem

Essa transformação enfoca o custo, a complexidade e a eficiência, com ênfase nas operações de ti. Os dados mais facilmente medidos por trás dessa transformação são a movimentação de ativos para a nuvem. Nesse tipo de transformação, o espaço digital é medido por máquinas virtuais (VMs), racks ou clusters que hospedam essas VMs, custos operacionais de datacenter, despesas de capital necessárias para manter sistemas e a depreciação desses ativos ao longo do tempo.

À medida que as VMs são movidas para a nuvem, a dependência de ativos herdados locais é reduzida. O custo da manutenção de ativos também é reduzido. Infelizmente, as empresas não conseguem perceber a redução de custos até que os clusters sejam desprovisionados e as concessões de datacenter expirem. Em muitos casos, o valor total do esforço não é realizado até que os ciclos de depreciação sejam concluídos.

Sempre alinhe com o CFO ou escritório financeiro antes de fazer demonstrativos financeiros. No entanto, as equipes de ti geralmente podem estimar o custo monetário atual e os valores de custo monetário futuro para cada VM com base na CPU, na memória e no armazenamento consumidos. Você pode aplicar esse valor a cada VM migrada para estimar a economia de custo imediata e o valor monetário futuro do esforço.

## <a name="application-innovation"></a>Inovação de aplicativos

A inovação de aplicativos habilitada para a nuvem se concentra principalmente na experiência do cliente e na disposição do cliente em consumir produtos e serviços fornecidos pela empresa. Leva tempo para incrementos de alteração para afetar os comportamentos de compra do consumidor ou do cliente. Mas os ciclos de inovação de aplicativos tendem a ser muito menores do que em outras formas de transformação. O Conselho tradicional é que você deve começar com uma compreensão dos comportamentos específicos que deseja influenciar e usar esses comportamentos como as métricas de aprendizado. Por exemplo, em um aplicativo de comércio eletrônico, compras totais ou complementos podem ser o comportamento de destino. Para uma empresa de vídeo, o tempo que observa fluxos de vídeo pode ser o destino.

O desafio com as métricas de comportamento do cliente é que elas podem ser facilmente influenciadas por variáveis externas. Portanto, é importante incluir estatísticas relacionadas com as métricas de aprendizado. Essas estatísticas relacionadas podem incluir a cadência da versão, bugs resolvidos por versão, cobertura de código de testes de unidade, número de exibições de página, taxa de transferência de página, tempo de carregamento de página e outras métricas de desempenho de aplicativo. Cada uma pode mostrar diferentes atividades e alterações na base de código e na experiência do cliente para correlacionar com padrões de comportamento de clientes de nível superior.

## <a name="data-innovation"></a>Inovação de dados

A alteração de um setor, a interrupção de mercados ou a transformação de produtos/serviços pode levar anos. Em um esforço de inovação de dados habilitado para nuvem, a experimentação é fundamental para medir o sucesso. Seja transparente compartilhando métricas de previsão, como probabilidade percentual, número de experimentos com falha e quantidade de modelos treinados. As falhas serão acumuladas mais rápido do que os sucessos. Essas métricas podem ser discouraging e é importante que a equipe executiva entenda o tempo e o investimento necessários para aproveitar os dados adequadamente.

Por outro lado, alguns indicadores positivos geralmente são associados ao aprendizado controlado por dados: centralização de conjuntos de dados heterogêneos, entrada de dados e democratization de dados. Embora a equipe esteja aprendendo sobre o cliente do futuro, os resultados reais podem ser produzidos hoje. As métricas de aprendizado de suporte podem incluir:

- Número de modelos disponíveis
- Número de fontes de dados do parceiro consumidas
- Dispositivos que produzem dados de entrada
- Volume de dados de entrada
- Tipos de dados

Uma métrica ainda mais valiosa é o número de dashboards criados a partir de fontes de dados combinadas. Esse número reflete os processos de negócios de estado atual que são afetados por novas fontes de dados. Ao compartilhar novas fontes de dados de forma aberta, sua empresa pode aproveitar os dados usando ferramentas de relatório como Power BI para produzir informações incrementais e gerar mudanças comerciais.

## <a name="next-steps"></a>Próximas etapas

Depois que as métricas de aprendizagem estiverem alinhadas, você estará pronto para começar [a avaliar o espaço digital](../digital-estate/index.md) em relação a essas métricas. O resultado será uma pendência de [transformação ou uma pendência de migração](../migrate/migration-considerations/prerequisites/technical-complexity.md).

> [!div class="nextstepaction"]
> [Avaliar o espaço digital](../digital-estate/index.md)
