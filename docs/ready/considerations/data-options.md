---
title: Examine as opções de dados
description: Examine as opções de dados para cargas de trabalho do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 434fb0982b0749a6fcb117b86d8cf3bb6335f13a
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806876"
---
# <a name="review-your-data-options"></a>Examine as opções de dados

Ao preparar o ambiente de zona de acesso para a adesão à nuvem, você precisa determinar os requisitos de dados para hospedar as cargas de trabalho. Os produtos e os serviços de banco de dados do Azure são compatíveis com uma ampla variedade de cenários e recursos de armazenamento de dados. A maneira como você configura o ambiente de zona de acesso para dar suporte aos requisitos de dados depende dos requisitos de governança, técnicos e empresariais referentes às cargas de trabalho.

## <a name="identify-data-services-requirements"></a>Identificar requisitos de serviços de dados

Como parte da avaliação e preparação da zona de acesso, você precisa identificar os armazenamentos de dados aos quais a zona de acesso precisa dar suporte. O processo envolve avaliar cada um dos aplicativos e serviços que compõem as cargas de trabalho para determinar o armazenamento de dados e os requisitos de acesso. Depois de identificar e documentar esses requisitos, você pode criar políticas para que a zona de acesso controle os tipos de recursos permitidos com base nas necessidades das cargas de trabalho.

Para cada aplicativo ou serviço que você implantará no ambiente de zona de acesso, use a seguinte árvore de decisão como um ponto de partida para ajudá-lo a determinar os serviços de armazenamento de dados adequados a serem usados:

![Árvore de decisão de serviços de banco de dados do Azure](../../_images/ready/data-decision-tree.png)

### <a name="key-questions"></a>Principais perguntas

Responda às seguintes perguntas sobre as cargas de trabalho para ajudá-lo a tomar decisões com base na árvore de decisão de serviços de banco de dados do Azure:

- **Você precisa de controle total ou da propriedade do software de banco de dados ou do sistema operacional do host?** Alguns cenários exigem que você tenha um alto grau de controle ou a propriedade da configuração do software e dos servidores de host das cargas de trabalho do banco de dados. Nesses cenários, você pode implantar máquinas virtuais de IaaS (infraestrutura como serviço) personalizadas para controlar totalmente a implantação e a configuração dos serviços de dados. Se você não tem esses requisitos, os serviços de banco de dados gerenciados PaaS (plataforma como serviço) podem reduzir os custos de gerenciamento e operação.
- **As cargas de trabalho usarão uma tecnologia de banco de dados relacional?** Em caso afirmativo, que tecnologia você planeja usar? O Azure fornece recursos de banco de dados PaaS gerenciados para o [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), o [MySQL](https://docs.microsoft.com/azure/mysql/overview), o [PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) e o [MariaDB](https://docs.microsoft.com/azure/mariadb/overview).
- **As cargas de trabalho usarão SQL Server?** No Azure, você pode colocar suas cargas de trabalho para executar no [SQL Server em Máquinas Virtuais do Azure](https://azure.microsoft.com/services/virtual-machines/sql-server) baseadas em IaaS ou no [serviço hospedado do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) baseado em PaaS. A escolha da opção a ser usada é, principalmente, baseada no seu desejo de gerenciar o banco de dados, aplicar patches e fazer backups ou se deseja delegar essas operações ao Azure. Em alguns cenários, problemas de compatibilidade podem exigir o uso de SQL Server hospedado em IaaS. Para obter mais informações de como escolher a opção correta para suas cargas de trabalho, confira [Escolher a melhor opção do SQL Server no Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).
- **As cargas de trabalho usarão o armazenamento de banco de dados chave/valor?** O [Cache Redis do Azure](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) oferece uma solução de armazenamento de dados em cache de chave/valor de alto desempenho que pode potencializar aplicativos rápidos e escalonáveis. O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) também fornece recursos de armazenamento de chave/valor de uso geral.
- **As cargas de trabalho usarão dados de documento ou grafos?** O [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) é um serviço de banco de dados multimodelo compatível com uma ampla variedade de tipos de dados e APIs. O Azure Cosmos DB também fornece recursos de banco de dados de grafo e de documento.
- **Suas cargas de trabalho usarão dados de família de colunas?** O [Apache HBase no Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/hbase/apache-hbase-overview) é criado com base no Apache Hadoop. Ele é compatível com grandes quantidades de dados não estruturados e semiestruturados em um banco de dados sem esquema organizado por famílias de colunas.
- **Suas cargas de trabalho precisarão de recursos de análise de dados de alta capacidade?** Você pode usar o [SQL Data Warehouse do Azure](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) para armazenar e consultar dados estruturados em escala de petabytes de forma eficaz. Para cargas de trabalho de Big Data não estruturadas, você pode usar o [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) para armazenar e analisar arquivos de tamanho de petabytes e trilhões de objetos.
- **Suas cargas de trabalho precisarão de recursos de mecanismo de pesquisa?** Você pode usar o [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search) para compilar índices de pesquisa baseados em nuvem avançados para IA que podem ser integrados em aplicativos.
- **Suas cargas de trabalho usarão dados de série temporal?** O [Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-overview) é compilado para armazenar, visualizar e consultar grandes quantidades de dados de série temporal, como aqueles gerados por dispositivos IoT.

> [!NOTE]
> Saiba mais sobre como avaliar as opções de banco de dados para cada um dos seus aplicativos ou serviços no [guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-comparison).

## <a name="common-database-scenarios"></a>Cenários comuns de banco de dados

A tabela a seguir ilustra alguns requisitos de cenários de uso comum e os serviços de banco de dados recomendados para lidar com eles:

| **Cenário** | **Serviço de dados** |
|-----|-----|
| Preciso de um banco de dados multimodelo distribuído globalmente com suporte para opções de NoSQL. | [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) |
| Preciso de um banco de dados relacional totalmente gerenciado que provisiona rapidamente, dimensiona durante o uso e inclui segurança e inteligência internas. | [Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) |
| Preciso de um banco de dados relacional MySQL escalonável e totalmente gerenciado, que tenha alta disponibilidade e segurança interna sem custo extra. | [Banco de Dados do Azure para MySQL](https://docs.microsoft.com/azure/mysql/overview) |
| Preciso de um banco de dados relacional PostgreSQL escalonável e totalmente gerenciado, que tenha alta disponibilidade e segurança interna sem custo extra. | [Banco de Dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) |
| Pretendo hospedar aplicativos de SQL Server corporativos na nuvem e ter controle total sobre o sistema operacional do servidor. | [SQL Server em Máquinas Virtuais](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) |
| Preciso de um data warehouse elástico totalmente gerenciado, que tenha segurança em todos os níveis de escala, sem custo extra. | [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| Preciso de recursos de Data Lake Storage que sejam compatíveis com clusters Hadoop ou dados HDFS. | [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake) |
| Preciso de acesso de baixa latência consistente de alta taxa de transferência para que meus dados ofereçam suporte a aplicativos rápidos e escalonáveis. | [Cache Redis do Azure](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) |
| Preciso de um banco de dados relacional MariaDB escalonável e totalmente gerenciado, que tenha alta disponibilidade e segurança interna sem custo extra. | [Banco de Dados do Azure para MariaDB](https://docs.microsoft.com/azure/mariadb/overview) |

## <a name="regional-availability"></a>Disponibilidade regional

O Azure permite que você ofereça serviços na escala necessária para chegar a seus clientes e parceiros,  _onde quer que eles estejam_. Um fator primordial no planejamento da implantação na nuvem é determinar qual região do Azure hospedará seus recursos de carga de trabalho.

A maioria dos serviços de banco de dados está em disponibilidade geral na maioria das regiões do Azure. No entanto, há algumas regiões, principalmente direcionadas a clientes governamentais, compatíveis apenas com um subconjunto desses produtos. Antes de decidir em quais regiões você implantará seus recursos de banco de dados, recomendamos que você consulte a [página de regiões](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=data-factory,sql-server-stretch-database,redis-cache,database-migration,sql-data-warehouse,postgresql,mariadb,cosmos-db,mysql,sql-database) para verificar o status mais recente da disponibilidade regional.

Para saber mais sobre a infraestrutura global do Azure, confira a [página das regiões do Azure](https://azure.microsoft.com/global-infrastructure/regions). Você também pode exibir os [produtos disponíveis por região](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) para obter detalhes específicos sobre os serviços gerais que estão disponíveis em cada região do Azure.

## <a name="data-residency-and-compliance-requirements"></a>Requisitos de conformidade e residência de dados

Os requisitos legais e contratuais que são relacionados ao armazenamento de dados geralmente serão aplicados às suas cargas de trabalho. Esses requisitos podem variar de acordo com a localização da sua organização, a jurisdição dos ativos físicos que hospedam os armazenamentos de dados e o setor empresarial pertinente. Os componentes das obrigações de dados a serem considerados incluem a classificação de dados, a localização dos dados e as respectivas responsabilidades de proteção de dados no modelo de responsabilidade compartilhada. Para obter ajuda no entendimento desses requisitos, confira o White Paper [Como conseguir residência e segurança de dados em conformidade com o Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Parte dos seus esforços de conformidade pode incluir o controle do local em que os recursos do banco de dados ficam fisicamente. As regiões do Azure são organizadas em grupos chamados geografias. Uma [geografia do Azure](https://azure.microsoft.com/global-infrastructure/geographies) garante que os requisitos de residência, de soberania, de conformidade e de resiliência de dados sejam respeitados dentro de limites geográficos e políticos. Se as cargas de trabalho estiverem sujeitas à soberania de dados ou outros requisitos de conformidade, você deverá implantar os recursos de armazenamento em regiões em uma geografia do Azure em conformidade.

## <a name="establish-controls-for-database-services"></a>Estabelecer controles para serviços de banco de dados

Ao preparar o ambiente de zona de acesso, você poderá estabelecer controles que limitarão quais armazenamentos de dados os usuários poderão implantar. Controles podem ajudá-lo a gerenciar custos e limitar riscos de segurança, permitindo que os desenvolvedores e as equipes de TI implantem e configurem recursos necessários para dar suporte às suas cargas de trabalho.

Depois de identificar e documentar os requisitos da zona de acesso, você pode usar o [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) para controlar os recursos do banco de dados permitidos para os usuários criarem. Os controles podem assumir a forma de [permissão ou negativa da criação de tipos de recursos de banco de dados](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). Por exemplo, você pode restringir os usuários a criarem somente recursos do Banco de Dados SQL do Azure. Você também pode usar a política para controlar as opções permitidas quando um recurso é criado, como [restringir quais SKUs do Banco de Dados SQL podem ser provisionadas](https://docs.microsoft.com/azure/governance/policy/samples/allowed-sql-db-skus) ou [permitir que apenas versões específicas do SQL Server](https://docs.microsoft.com/azure/governance/policy/samples/require-sql-12) sejam instaladas em uma VM IaaS.

As políticas podem ser delimitadas a recursos, grupos de recursos, assinaturas e grupos de gerenciamento. Você pode incluir suas políticas em definições do [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) e aplicá-las repetidamente em todo o estado de nuvem.
