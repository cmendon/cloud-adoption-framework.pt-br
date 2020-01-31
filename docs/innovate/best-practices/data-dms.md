---
title: 'Inovação em nuvem: serviço de migração de banco de dados do Azure'
description: Inovação de nuvem-serviço de migração de banco de dados do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 44ebe7e28eea56d1b7e61b5926a9588f4c985ae1
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808661"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Coletar dados por meio da migração e da modernização de fontes de dados existentes

As empresas geralmente têm diferentes tipos de dados existentes que podem [democratize](../considerations/data.md). Quando uma hipótese de cliente requer o uso de dados existentes para criar soluções modernas, uma primeira etapa pode ser a migração e a modernização de dados para se preparar para invenções e inovações. Para se alinhar com os esforços de migração existentes em um plano de adoção de nuvem, você pode fazer mais facilmente a migração e a modernização dentro da [metodologia de migração](../../migrate/index.md).

## <a name="use-of-this-article"></a>Uso deste artigo

Este artigo descreve uma série de abordagens que se alinham com o processo de migração. Você pode alinhar melhor essas abordagens ao ferramentas de migração padrão.

Durante o processo de avaliação dentro da metodologia de migração, uma equipe de adoção de nuvem avalia o estado atual e o estado futuro desejado para o ativo migrado. Quando esse processo faz parte de um esforço de inovação, ambas as equipes de adoção de nuvem podem usar este artigo para ajudar a fazer essas avaliações.

## <a name="primary-toolset"></a>Conjunto de ferramentas primário

Quando você migra e moderniza dados locais, a opção de ferramenta do Azure mais comum é o [serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms). Esse serviço faz parte do ferramentas de [migrações mais amplo do Azure](https://docs.microsoft.com/azure/migrate/migrate-services-overview) . Para as fontes de dados SQL Server existentes, [Assistente de migração de dados](https://docs.microsoft.com/sql/dma/dma-overview) pode ajudá-lo a avaliar e migrar um pequeno número de estruturas de dados.

Para dar suporte a migrações do Oracle e do NoSQL, você também pode usar o [serviço de migração de banco de dados](https://docs.microsoft.com/azure/dms) para determinados tipos de bancos de dados de origem para destino. Os exemplos incluem Oracle para PostgreSQL e MongoDB para Cosmos DB. Mais comumente, as equipes de adoção usam ferramentas de parceiros ou scripts personalizados para migrar para Azure Cosmos DB, Azure HDInsight ou opções de máquina virtual com base em IaaS (infraestrutura como serviço).

## <a name="considerations-and-guidance"></a>Considerações e diretrizes

Quando você usa o serviço de migração de banco de dados do Azure para a migração e a modernização, é importante entender:

- A plataforma atual para hospedar a fonte de dados.
- A versão atual.
- A plataforma futura e a versão que melhor dá suporte à hipótese ou ao alvo do cliente.

A tabela a seguir mostra os pares de origem e de destino a serem examinados com a equipe de migração. Cada par inclui uma opção de ferramenta e um link para um guia relacionado.

### <a name="migration-type"></a>Tipo de migração

Com uma migração offline, o tempo de inatividade do aplicativo começa quando a migração é iniciada. Com uma migração online, o tempo de inatividade é limitado ao tempo de transferência no final da migração.

Sugerimos que você decida o tempo de inatividade aceitável dos negócios e teste uma migração offline. Você faz isso para verificar se o horário de restauração atende ao tempo de inatividade aceitável. Se o tempo de restauração for inaceitável, faça uma migração online.

|Origem  |Escolha o destino  |Ferramenta  |Tipo de migração  |Diretriz  |
|---------|---------|---------|---------|---------|
|SQL Server|Banco de dados SQL do Azure|Serviço de Migração do Banco de Dados|Offline|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|Banco de dados SQL do Azure|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Instância gerenciada do Banco de Dados SQL do Azure|Serviço de Migração do Banco de Dados|Offline|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Instância gerenciada do Banco de Dados SQL do Azure|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Banco de dados SQL do Azure ou instância gerenciada do banco de dados SQL|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Banco de Dados do Azure para MySQL|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Banco de Dados do Azure para PostgreSQL|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MongoDB|API do Mongo Azure Cosmos DB|Serviço de Migração do Banco de Dados|Offline|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|API do Mongo Azure Cosmos DB|Serviço de Migração do Banco de Dados|Online|[Tutorial](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Opções de PaaS (plataforma como serviço) e IaaS diferentes|A ferramenta de um parceiro ou migrações para Azure|Offline ou online|[Árvore de decisão](../../migrate/expanded-scope/data-oracle-migration.md)|
|Opções de banco de tinta NoSQL diferentes|Opções de Cosmo DB ou IaaS|Migrações de procedimento ou migração do Azure|Offline ou online|[Árvore de decisão](../../migrate/expanded-scope/data-no-sql-migration.md)|
