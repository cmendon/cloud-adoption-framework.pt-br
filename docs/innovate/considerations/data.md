---
title: 'Inovação em nuvem: dados de democratize'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação em nuvem – dados do democratize
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 80cd8c74f283436d9f32ce647c27bb7c67d3c92c
ms.sourcegitcommit: 15898374495761bfb76cee719e0f9189856884e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888884"
---
# <a name="democratize-data"></a>Dados do democratize

Carvão, petróleo e potencial humano foram os três ativos mais CONSEQÜENCIAIS em toda a revolução industrial. Esses ativos criaram empresas, mercados deslocados e, em última análise, Nações alteradas. Na economia digital, há três ativos igualmente importantes: dados, dispositivos e potencial humano. Em cada um desses ativos, há um grande potencial de inovação. Em qualquer esforço de inovação, os dados são o novo óleo.

Em toda a empresa hoje, há bolsos de dados que podem ser utilizados para encontrar e atender às necessidades do cliente com mais rapidez. Infelizmente, o processo de mineração de dados para impulsionar a inovação tem sido muito dispendioso e demorado. Muitas das soluções mais valiosas para os clientes vão desaparecer, pois as pessoas certas não podem acessar os dados de que precisam.

Democratization de dados é o processo de obter esses dados em mãos à direita para impulsionar a inovação. Esse processo pode levar várias formas, mas geralmente inclui soluções para dados brutos ingeridos ou integrados, centralização dos dados, compartilhamento de dados e proteção dos dados. Quando bem-sucedido, os especialistas em toda a empresa podem aproveitar os dados para testar as mesmas. Em muitos casos, as equipes de adoção de nuvem podem [criar com empatia de clientes](./build.md) usando apenas dados, resultando em um impacto rápido nas necessidades existentes do cliente.

## <a name="process-of-democratizing-data"></a>Processo de dados do democratizando

As fases a seguir guiarão as decisões e as abordagens necessárias para adotar uma solução que democratiza dados. Cada uma das fases pode não ser necessária para criar uma solução específica. No entanto, cada um deve ser avaliado ao criar uma solução para uma hipótese do cliente. Cada uma delas fornece uma abordagem exclusiva para a criação de soluções inovadoras.

![Processo para dados do democratizando](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Compartilhar dados

Ao [criar com empatia de clientes](./build.md), todos os processos se concentram em uma necessidade do cliente em relação a uma solução técnica. Os dados de democratizando não são exceção, portanto, começamos com o compartilhamento de dados. Para democratize dados, ele deve incluir uma solução que compartilha dados com um consumidor de dados. O consumidor dos dados pode ser um cliente direto ou um proxy que toma decisões para os clientes. Os consumidores de dados aprovados têm a capacidade de analisar, interrogar e relatar dados centralizados, sem nenhum suporte da equipe de ti.

Muitas inovações bem-sucedidas foram iniciadas como MVPs, que fornecem processos manuais controlados por dados em nome do cliente. Neste modelo do concierge, um funcionário é o consumidor de dados. Esse funcionário usa dados para auxiliar o cliente. Cada vez que o cliente envolve o suporte manual, uma hipótese pode ser testada e validada. Essa abordagem geralmente é um meio econômico de testar uma hipótese com foco no cliente antes de investir pesadamente em soluções integradas.

As principais ferramentas para compartilhar dados diretamente com consumidores de dados incluem relatórios de autoatendimento ou dados inseridos em outras experiências, usando ferramentas como [Power bi](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Antes de compartilhar dados, é importante estar atento às seções a seguir. O compartilhamento de dados pode exigir governança para fornecer proteção para os dados compartilhados. Além disso, os dados podem ser distribuídos em várias nuvens e podem exigir a centralização. Grande parte dos dados pode até residir em aplicativos que exigirão a coleta dos dados antes de compartilhá-los.

### <a name="govern-data"></a>Controlar dados

O compartilhamento de dados pode produzir rapidamente um MVP que pode ser usado em conversas de clientes. No entanto, os dados sozinhos são apenas dados. Para transformar esses dados compartilhados em um conhecimento acionável, é necessário um pouco mais. Depois que uma hipótese foi validada por meio do compartilhamento de dados, a próxima fase de desenvolvimento geralmente é a governança de dados.

A governança de dados é um tópico abrangente que pode exigir sua própria estrutura dedicada. Isso está fora do escopo da estrutura de [adoção da nuvem](../../index.md). No entanto, há alguns aspectos da governança de dados que devem ser considerados, assim como a hipótese do cliente é validada. Veja a seguir alguns exemplos dessas perguntas:

- **Os dados compartilhados são confidenciais?** Os [dados devem ser classificados](../../govern/policy-compliance/data-classification.md) antes de qualquer compartilhamento público para proteger os interesses dos clientes e da empresa.
- **Se os dados forem confidenciais, eles foram protegidos?** A proteção de dados confidenciais deve ser um requisito para qualquer dado de democratizado. A carga de trabalho de exemplo focada na [proteção de soluções de dados](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions) fornece algumas referências para proteger os dados.
- **Os dados estão catalogados?** Capturar detalhes sobre os dados que estão sendo compartilhados ajudará no gerenciamento de dados de longo prazo. As ferramentas para documentar dados, como o catálogo de dados do Azure, podem tornar esse processo muito mais fácil na nuvem. A orientação sobre a [anotação de dados](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) e a [documentação de fontes de dados](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) pode ajudar a acelerar o processo.

Quando democratization de dados é importante para uma hipótese voltada para o cliente, a governança de dados compartilhados deve estar em algum lugar no plano de lançamento para proteger clientes, consumidores de dados e a empresa.

### <a name="centralize-data"></a>Centralizar dados

Quando os dados são interrompidos em um ambiente de ti, as oportunidades de inovação podem ser extremamente restritas, caras e demoradas. A nuvem fornece novas oportunidades para centralizar dados em vários silos de dados. Quando a centralização de várias fontes de dados é necessária para [criar com clientes empatia](./build.md) , a nuvem pode acelerar o teste de hipóteses.

> [!CAUTION]
> A centralização de dados é um ponto de risco comum em qualquer processo de inovação. Quando a centralização de dados é um [aumento técnico](./build.md#reduce-complexity-and-delay-technical-spikes), em oposição a uma fonte de valor de cliente, é recomendável atrasar a centralização até que a hipótese do cliente tenha sido validada.

Se a centralização dos dados for necessária, a primeira etapa será definir o armazenamento de dados apropriado para os dados centralizados. A abordagem aconselhada é estabelecer um data warehouse na nuvem. Essa opção escalonável fornecerá um local central para todos os dados. Esse tipo de solução está disponível em opções de processamento analítico online (OLAP) ou de Big Data.

As arquiteturas de referência para soluções [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) e de [Big data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) podem ajudar a escolher a solução mais relevante no Azure. Se uma solução híbrida for necessária, a arquitetura de referência para [estender dados locais](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) também poderá ajudar a acelerar o desenvolvimento da solução.

> [!IMPORTANT]
> Dependendo da necessidade do cliente e da solução alinhada, uma solução mais simples pode ser suficiente. O arquiteto de nuvem deve desafiar a equipe para considerar soluções de menor custo que poderiam resultar em uma validação mais rápida da hipótese do cliente, especialmente durante o desenvolvimento antecipado. A seção sobre a coleta de dados abaixo descreverá alguns cenários que podem solicitar uma solução diferente.

### <a name="collect-data"></a>Coletar dados

Quando os dados precisam ser centralizados para fornecer uma necessidade do cliente, é muito provável que os dados também precisem ser coletados de várias fontes e movidos para o armazenamento de dados centralizado. Há duas formas principais de coleta de dados: integração e ingestão. Cada uma delas fornece um meio diferente de coletar dados.

**Integrar:** Os dados existentes que residem em um repositório de dados existente podem ser integrados ao armazenamento de dados centralizado usando técnicas tradicionais de movimentação de dados. Isso é especialmente comum para cenários que envolvem o armazenamento de dados de nuvem. Essas técnicas consistem em extrair os dados do armazenamento de dados existente. Em seguida, carregando os dados no armazenamento de dados central. Em algum momento nesse processo, os dados geralmente são transformados para serem mais utilizáveis e relevantes no armazenamento central.

As ferramentas baseadas em nuvem transformam essas técnicas em ferramentas de pagamento por uso, reduzindo a barreira de entrada para a coleta e a centralização de dados. Ferramentas como serviço de migração de dados e Data Factory são dois exemplos comuns no Azure. A arquitetura de referência para [Data Factory com um armazenamento de dados OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) fornece um exemplo de tal solução.

**Ingestão:** Alguns dados não estão em nenhum repositório de dados existente. Quando esses dados transitórios são uma fonte primária de inovação, abordagens alternativas devem ser consideradas. Dados transitórios podem ser encontrados em uma variedade de fontes existentes, como aplicativos, APIs, fluxos de dados, dispositivos IoT, blockchain, cache de aplicativos, conteúdo de mídia ou até mesmo arquivos simples.

Essas várias formas de dados podem ser integradas em um armazenamento de dados central em uma solução OLAP ou de Big Data. No entanto, para iterações iniciais de ciclos de compilação-medida-aprendizado, uma solução OLTP (processamento transacional online) pode ser mais do que suficiente para validar uma hipótese do cliente. As soluções OLTP não são a solução de qualidade mais alta para qualquer cenário de relatório. No entanto, quando a [criação com o cliente empatia](./build.md) foco na necessidade do cliente tem prioridade sobre decisões técnicas de ferramentas. Depois que a hipótese do cliente é validada em escala, uma plataforma mais adequada pode ser necessária. A arquitetura de referência em [armazenamentos de dados OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) pode ajudar a determinar qual armazenamento de dados é mais apropriado para sua solução.

**Virtualização:** A integração e a ingestão de dados pode, às vezes, diminuir a inovação. Quando uma solução para virtualização de dados já está disponível, isso pode ser uma abordagem mais relevante. A ingestão e a integração podem duplicar os requisitos de armazenamento/desenvolvimento, adicionar latência de dados, aumentar a área da superfície de ataque, injetar problemas de qualidade e aumentar os esforços de governança. A virtualização de dados é uma alternativa mais moderna que deixa os dados originais em um único local e cria consultas de passagem ou em cache dos dados de origem.

SQL Server 2017 e o Azure SQL Data Warehouse dão suporte ao [polybase](/sql/relational-databases/polybase/polybase-guide) , que é a abordagem para a virtualização de dados mais comumente usada no Azure.

## <a name="next-steps"></a>Próximos passos

Com uma estratégia para dados democratizando em vigor, a próxima etapa é avaliar abordagens para [envolver clientes por meio de aplicativos](./apps.md).

> [!div class="nextstepaction"]
> [Envolver clientes por meio de aplicativos](./apps.md)
