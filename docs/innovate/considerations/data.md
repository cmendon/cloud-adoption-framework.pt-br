---
title: 'Inovação em nuvem: dados de democratize'
description: Introdução à inovação em nuvem – dados do democratize
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 158c3e25bac2124312a8ceaf3ac5500a58246f48
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808491"
---
# <a name="democratize-data"></a>Democratizar os dados

Carvão, petróleo e potencial humano foram os três ativos mais CONSEQÜENCIAIS durante a revolução industrial. Esses ativos criaram empresas, mercados deslocados e, em última análise, Nações alteradas. Na economia digital, há três ativos igualmente importantes: dados, dispositivos e potencial humano. Cada um desses ativos tem grande potencial de inovação. Para qualquer esforço de inovação na era moderna, os dados são o novo óleo.

Em toda a empresa hoje, há bolsos de dados que poderiam ser usados para encontrar e atender às necessidades do cliente com mais eficiência. Infelizmente, o processo de mineração de dados para impulsionar a inovação tem sido muito dispendioso e demorado. Muitas das soluções mais valiosas para os clientes vão desaparecer, pois as pessoas certas não podem acessar os dados de que precisam.

Democratization de dados é o processo de obter esses dados em mãos à direita para impulsionar a inovação. Esse processo pode usar várias formas, mas geralmente inclui soluções para dados brutos ingeridos ou integrados, centralização de dados, compartilhamento de dados e proteção de dados. Quando esses métodos são bem-sucedidos, os especialistas em toda a empresa podem usar os dados para testar as mesmas. Em muitos casos, as equipes de adoção de nuvem podem [criar com empatia de clientes](./build.md) usando apenas dados e endereçando rapidamente as necessidades existentes do cliente.

## <a name="process-of-democratizing-data"></a>Processo de dados do democratizando

As fases a seguir guiarão as decisões e as abordagens necessárias para adotar uma solução que democratiza dados. Nem toda fase será necessariamente necessária para criar uma solução específica. No entanto, você deve avaliar cada fase quando estiver criando uma solução para uma hipótese do cliente. Cada uma delas fornece uma abordagem exclusiva para a criação de soluções inovadoras.

![Processo para dados do democratizando](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Compartilhar dados

Quando você [cria com o cliente empatia](./build.md), todos os processos elevam a necessidade do cliente sobre uma solução técnica. Como os dados de democratizando não são exceção, começamos compartilhando dados. Para democratize dados, ele deve incluir uma solução que compartilha dados com um consumidor de dados. O consumidor de dados pode ser um cliente direto ou um proxy que toma decisões para os clientes. Os consumidores de dados aprovados podem analisar, interrogar e relatar dados centralizados, sem nenhum suporte da equipe de ti.

Muitas inovações bem-sucedidas foram iniciadas como um MVP (produto viável) mínimo que fornece processos manuais controlados por dados em nome do cliente. Neste modelo do concierge, um funcionário é o consumidor de dados. Esse funcionário usa dados para auxiliar o cliente. Cada vez que o cliente envolve o suporte manual, uma hipótese pode ser testada e validada. Essa abordagem geralmente é um meio econômico de testar uma hipótese com foco no cliente antes de investir pesadamente em soluções integradas.

As principais ferramentas para compartilhar dados diretamente com consumidores de dados incluem relatórios de autoatendimento ou dados inseridos em outras experiências, usando ferramentas como [Power bi](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Antes de compartilhar dados, verifique se você leu as seções a seguir. O compartilhamento de dados pode exigir governança para fornecer proteção para os dados compartilhados. Além disso, esses dados podem ser distribuídos em várias nuvens e podem exigir centralização. Grande parte dos dados pode até residir em aplicativos, o que exigirá a coleta de dados antes que você possa compartilhá-lo.

### <a name="govern-data"></a>Controlar os dados

O compartilhamento de dados pode produzir rapidamente um MVP que você pode usar em conversas de clientes. No entanto, para transformar esses dados compartilhados em conhecimento útil e acionável, geralmente é necessário um pouco mais. Depois que uma hipótese foi validada por meio do compartilhamento de dados, a próxima fase de desenvolvimento normalmente é a governança de dados.

A governança de dados é um tópico abrangente que pode exigir sua própria estrutura dedicada. Esse grau de granularidade está fora do escopo da estrutura de [adoção da nuvem](../../index.md). No entanto, há vários aspectos do controle de dados que você deve considerar assim que a hipótese do cliente é validada. Por exemplo:

- **Os dados compartilhados são confidenciais?** Os [dados devem ser classificados](../../govern/policy-compliance/data-classification.md) antes de serem compartilhados publicamente para proteger os interesses dos clientes e da empresa.
- **Se os dados forem confidenciais, eles foram protegidos?** A proteção de dados confidenciais deve ser um requisito para qualquer dado de democratizado. A carga de trabalho de exemplo focada na [proteção de soluções de dados](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions) fornece algumas referências para proteger os dados.
- **Os dados são catalogados?** Capturar detalhes sobre os dados que estão sendo compartilhados ajudará no gerenciamento de dados de longo prazo. As ferramentas para documentar dados, como o catálogo de dados do Azure, podem tornar esse processo muito mais fácil na nuvem. A orientação sobre a [anotação de dados](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) e a [documentação de fontes de dados](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) pode ajudar a acelerar o processo.

Quando democratization de dados é importante para uma hipótese voltada para o cliente, verifique se a governança de dados compartilhados está em algum lugar no plano de lançamento. Isso ajudará a proteger clientes, consumidores de dados e a empresa.

### <a name="centralize-data"></a>Centralizar dados

Quando os dados são interrompidos em um ambiente de ti, as oportunidades de inovação podem ser extremamente restritas, caras e demoradas. A nuvem fornece novas oportunidades para centralizar dados entre silos de dados. Quando a centralização de várias fontes de dados é necessária para [criar com o cliente empatia](./build.md), a nuvem pode acelerar o teste de hipóteses.

> [!CAUTION]
> A centralização de dados representa um ponto de risco em qualquer processo de inovação. Quando a centralização de dados é um [aumento técnico](./build.md#reduce-complexity-and-delay-technical-spikes) (em oposição a uma fonte de valor de cliente), sugerimos que você atrase a centralização até que as subformas do cliente tenham sido validadas.

Se a centralização dos dados for necessária, primeiro defina o armazenamento de dados apropriado para os dados centralizados. É uma boa prática estabelecer um data warehouse na nuvem. Essa opção escalonável fornece um local central para todos os seus dados. Esse tipo de solução está disponível em opções de processamento analítico online (OLAP) ou de Big Data.

As arquiteturas de referência para soluções [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) e de [Big data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) podem ajudá-lo a escolher a solução mais relevante no Azure. Se uma solução híbrida for necessária, a arquitetura de referência para [estender dados locais](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) também poderá ajudar a acelerar o desenvolvimento da solução.

> [!IMPORTANT]
> Dependendo da necessidade do cliente e da solução alinhada, uma abordagem mais simples pode ser suficiente. O arquiteto de nuvem deve desafiar a equipe para considerar soluções de menor custo que poderiam resultar em uma validação mais rápida da hipótese do cliente, especialmente durante o desenvolvimento antecipado. A seção a seguir sobre a coleta de dados abrange alguns cenários que podem sugerir uma solução diferente para sua situação.

### <a name="collect-data"></a>Coletar dados

Quando você precisa que os dados sejam centralizados para atender a uma necessidade do cliente, é muito provável que você também precise coletar os dados de várias fontes e movê-los para o armazenamento de dados centralizado. Há duas formas principais de coleta de dados: *integração* e *ingestão*.

**Integração:** Os dados que residem em um repositório de dados existente podem ser integrados ao armazenamento de dados centralizado usando técnicas tradicionais de movimentação de dados. Isso é especialmente comum para cenários que envolvem o armazenamento de dados de nuvem. Essas técnicas envolvem extrair os dados do armazenamento de dados existente e, em seguida, carregá-los no armazenamento de dados central. Em algum momento nesse processo, os dados normalmente são transformados para serem mais utilizáveis e relevantes no armazenamento central.

As ferramentas baseadas em nuvem transformaram essas técnicas em ferramentas de pagamento por uso, reduzindo a barreira de entrada para a coleta e a centralização de dados. Ferramentas como o serviço de migração de banco de dados do Azure e Azure Data Factory são dois exemplos. A arquitetura de referência para [Data Factory com um armazenamento de dados OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) é um exemplo de uma dessas soluções.

**Ingestão:** Alguns dados não residem em um repositório de dados existente. Quando esses dados transitórios são uma fonte primária de inovação, você desejará considerar abordagens alternativas. Dados transitórios podem ser encontrados em uma variedade de fontes existentes, como aplicativos, APIs, fluxos de dados, dispositivos IoT, um blockchain, um cache de aplicativos, no conteúdo de mídia ou até mesmo em arquivos simples.

Você pode integrar essas várias formas de dados em um armazenamento de dados central em uma solução OLAP ou de Big Data. No entanto, para iterações iniciais do ciclo de desenvolvimento – medida – aprendizado, uma solução de OLTP (processamento transacional online) pode ser mais do que suficiente para validar uma hipótese do cliente. As soluções OLTP não são a solução de qualidade mais alta para qualquer cenário de relatório. No entanto, quando você está [criando com o cliente empatia](./build.md), é mais importante concentrar-se nas necessidades do cliente do que nas decisões técnicas de ferramentas. Depois que a hipótese do cliente é validada em escala, uma plataforma mais adequada pode ser necessária. A arquitetura de referência em [armazenamentos de dados OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) pode ajudá-lo a determinar qual armazenamento de dados é mais apropriado para sua solução.

**Virtualização:** A integração e a ingestão de dados pode, às vezes, diminuir a inovação. Quando uma solução para virtualização de dados já está disponível, ela pode representar uma abordagem mais razoável. A ingestão e a integração podem duplicar os requisitos de armazenamento e desenvolvimento, adicionar latência de dados, aumentar a área da superfície de ataque, disparar problemas de qualidade e aumentar os esforços de governança. A virtualização de dados é uma alternativa mais contemporânea que deixa os dados originais em um único local e cria consultas de passagem ou em cache dos dados de origem.

SQL Server 2017 e o Azure SQL Data Warehouse dão suporte ao [polybase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) , que é a abordagem para a virtualização de dados mais comumente usada no Azure.

## <a name="next-steps"></a>Próximos passos

Com uma estratégia para dados de democratizando em vigor, você vai querer avaliar abordagens para [envolver clientes por meio de aplicativos](./apps.md).

> [!div class="nextstepaction"]
> [Envolver clientes por meio de aplicativos](./apps.md)
