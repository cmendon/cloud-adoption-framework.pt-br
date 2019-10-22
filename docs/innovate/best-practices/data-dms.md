---
title: 'Inovação em nuvem: serviço de migração de dados'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Inovação em nuvem – serviço de migração de dados
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: c75efe3576bb61ecb116ab22e4946b8d87da3d4a
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683430"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Coletar dados por meio da migração e da modernização de fontes de dados existentes

As empresas geralmente têm uma variedade de dados existentes que podem ser [democratizadodos](../considerations/data.md). Quando a hipótese do cliente requer o uso de dados existentes para criar soluções modernas, uma primeira etapa pode ser a migração e a modernização dos dados para se preparar para invenções e inovações. Para se alinhar com os esforços de migração existentes em um plano de adoção de nuvem, a migração e a modernização podem ser executadas com mais facilidade na [metodologia de migração](../../migrate/index.md).

## <a name="use-of-this-article"></a>Uso deste artigo

Este artigo descreve uma série de abordagens que se alinham com o processo de migração, mas que podem ser melhor alinhadas com a ferramentas de migração padrão. Durante o processo de avaliação dentro da metodologia de migração, a equipe de adoção de nuvem avaliaria o estado atual e desejaria o estado futuro do ativo a ser migrado. Quando esse processo faz parte de um esforço de inovação, ambas as equipes de adoção de nuvem poderiam usar este artigo para tomar essas decisões.

## <a name="primary-toolset"></a>Conjunto de ferramentas primário

Ao migrar e modernizar dados que residem no momento local, a opção de ferramenta do Azure mais comum é o [serviço de migração de dados (DMS)](https://docs.microsoft.com/azure/dms) que faz parte do ferramentas de [migrações mais amplo do Azure](https://docs.microsoft.com/azure/migrate/migrate-services-overview) . Para as fontes de dados SQL Server existentes, o [Assistente de migração de dados (DMA)](/sql/dma/dma-overview) também pode fornecer assistência para avaliar e migrar um número menor de estruturas de dados.

Para dar suporte a migrações do Oracle e do NoSQL, o [serviço de migração de dados (DMS)](https://docs.microsoft.com/azure/dms) também pode ser usado para determinados tipos de origem para bancos de dados de destino, como Oracle para PostgreSQL ou MongoDB para Cosmos DB. É mais comum que as equipes de adoção aproveitem ferramentas de terceiros ou scripts de migração personalizados para migrar para as opções de VM baseadas em Cosmos DB, HDInsight ou IaaS.

## <a name="considerations-and-guidance"></a>Considerações e diretrizes

Ao aproveitar o DMS para migração e modernização de dados, é importante entender a plataforma atual para hospedar os dados (fonte), a versão e a plataforma e versão futuras que melhorriam a oferecer suporte à hipótese do cliente (destino). Veja a seguir uma lista de pares de origem e de destino a serem examinados com a equipe de migração. Cada uma inclui uma opção de ferramenta e um link para um guia com base nessas considerações.

**Tipo de migração:** Com uma migração offline, o tempo de inatividade do aplicativo começa quando a migração é iniciada. Com uma migração online, o tempo de inatividade é limitado ao período de redução no final da migração. Sugerimos que você entenda o que é o tempo de inatividade aceitável dos negócios e teste uma migração offline para determinar se o horário de restauração atende a isso; caso contrário, faça uma migração online.

|Origem  |Escolha o destino  |Ferramenta  |Tipo de migração  |Diretriz  |
|---------|---------|---------|---------|---------|
|SQL Server|Banco de dados SQL do Azure|DMS|Está|[Destina](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Banco de dados SQL do Azure|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Instância Gerenciada do Banco de Dados SQL do Azure|DMS|Está|[Destina](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Instância Gerenciada do Banco de Dados SQL do Azure|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Banco de dados SQL do Azure (ou Instância Gerenciada)|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Banco de Dados do Azure para MySQL|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Banco de Dados do Azure para PostgreSQL|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MondoDB|API do Mongo Azure Cosmos DB|DMS|Está|[Destina](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|API do Mongo Azure Cosmos DB|DMS|Online|[Destina](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Intervalo de opções de PaaS & IaaS|Migrações de terceiros ou do Azure|Vários|[Árvore de decisão](../../migrate/expanded-scope/data-oracle-migration.md)|
|Vários bancos de todos NoSQL|Opções de Cosmo DB ou IaaS|Migrações de procedimento ou migração do Azure|Vários|[Árvore de decisão](../../migrate/expanded-scope/data-no-sql-migration.md)|
