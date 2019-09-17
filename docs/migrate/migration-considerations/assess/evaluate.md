---
title: Avaliar a preparação da carga de trabalho
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Um processo na migração na nuvem que se concentra nas tarefas de migrar cargas de trabalho para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 186aa4d4dc5218e2166e7dfb4c9834917e647a02
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024656"
---
# <a name="evaluate-workload-readiness"></a>Avaliar a preparação da carga de trabalho

Essa atividade se concentra em avaliar a prontidão de uma carga de trabalho a ser migrada para a nuvem. Durante essa atividade, a equipe de adoção da nuvem valida que todos os ativos e dependências associadas são compatíveis com o modelo de implantação e o provedor de nuvem escolhidos. Durante o processo, a equipe documenta os esforços necessários para [corrigir](../migrate/remediate.md) problemas de compatibilidade.

## <a name="evaluation-assumptions"></a>Suposições sobre avaliação

A maior parte do conteúdo que discute os princípios no Cloud Adoption Framework é destinada a ser independente de nuvem. No entanto, o processo de avaliação de prontidão deve ser amplamente específico para cada plataforma de nuvem específica. As diretrizes a seguir pressupõem uma intenção de migrar para o Azure. Elas também pressupõem o uso de Migrações para Azure (também conhecidas como Azure Site Recovery) para [atividades de replicação](../migrate/replicate.md). Para ferramentas alternativas, confira [opções de replicação](../migrate/replicate-options.md).

Este artigo não se destina a capturar todas as atividades de avaliação possíveis. Supõe-se que cada ambiente e o resultado dos negócios determinarão requisitos específicos. Para ajudar a acelerar a criação desses requisitos, o restante deste artigo compartilha algumas atividades de avaliação comuns relacionadas à avaliação de [infraestrutura](#common-infrastructure-evaluation-activities), de [banco de dados](#common-database-evaluation-activities) e de [rede](#common-network-evaluation-activities).

## <a name="common-infrastructure-evaluation-activities"></a>Atividades comuns de avaliação de infraestrutura

- Requisitos do VMware: [Examine os requisitos do Azure Site Recovery para o VMware](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix).
- Requisitos do Hyper-V: [Examine os requisitos do Azure Site Recovery para Hyper-V](https://docs.microsoft.com/azure/site-recovery/hyper-v-azure-support-matrix).

Documente discrepâncias na configuração de host, configuração de VM replicada, requisitos de armazenamento ou configuração de rede.

## <a name="common-database-evaluation-activities"></a>Atividades comuns de avaliação de banco de dados

- Documente os Objetivos de Ponto de Recuperação e de Tempo de Recuperação da implantação de banco de dados atual. Eles são usados em [atividades de arquitetura](./architect.md) para auxiliar na tomada de decisões.
- Documente os requisitos para configuração de alta disponibilidade. Para obter assistência para entender os requisitos do SQL Server, confira o [Guia de Soluções de Alta Disponibilidade do SQL Server](https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server).
- Avalie a compatibilidade de PaaS. O [Guia de Migração de Dados do Azure](https://datamigration.microsoft.com) mapeia bancos de dados locais para soluções de PaaS do Azure compatíveis, como o [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) ou o [Azure DB](https://docs.microsoft.com/azure/sql-database) para [MySQL](https://docs.microsoft.com/azure/mysql), [Postgres](https://docs.microsoft.com/azure/postgresql) ou [MariaDB](https://docs.microsoft.com/azure/mariadb).
- Quando a compatibilidade de PaaS é uma opção sem a necessidade de qualquer correção, confira a equipe responsável pelas [atividades de arquitetura](./architect.md). As migrações de PaaS podem produzir economias e reduções de tempo significativas no TCO (custo total de propriedade) da maioria das soluções de nuvem.
- Quando a compatibilidade de PaaS é uma opção, mas a correção é necessária, confira as equipes responsáveis pelas [atividades de arquitetura](./architect.md) e [de correção](../migrate/remediate.md). Em muitos cenários, as vantagens das migrações de PaaS para soluções de banco de dados podem superar o aumento no tempo de correção.
- Documente o tamanho e a taxa de alteração de cada banco de dados a ser migrado.
- Quando possível, documente todos os aplicativos ou outros ativos que fazem chamadas para cada banco de dados.

> [!NOTE]
> A sincronização de qualquer ativo consome largura de banda durante os processos de replicação. Uma armadilha muito comum é ignorar o consumo de largura de banda necessário para manter os ativos sincronizados entre o ponto de replicação e a versão. Os bancos de dados são consumidores comuns de largura de banda durante os ciclos de lançamento e os bancos de dados com grandes volumes de armazenamento ou uma alta taxa de alteração são especialmente preocupantes. Considere uma abordagem de replicação da estrutura de dados, com atualizações controladas antes do UAT (teste de aceitação do usuário) e do lançamento. Nesses cenários, alternativas ao Azure Site Recovery podem ser mais apropriadas. Para obter mais detalhes, confira as diretrizes do [Guia de Migração de Dados do Azure](https://datamigration.microsoft.com).

## <a name="common-network-evaluation-activities"></a>Atividades comuns de avaliação de rede

- Calcule o armazenamento total para todas as VMs a serem replicadas durante as iterações que levam a um lançamento.
- Calcule a taxa de descompasso ou de alteração de armazenamento para todas as VMs a serem replicadas durante as iterações que levam a um lançamento.
- Calcule os requisitos de largura de banda necessários para cada iteração resumindo o armazenamento e o descompasso total.
- Calcule a largura de banda não utilizada disponível na rede atual para validar o alinhamento por iteração.
- Largura de banda do documento necessária para alcançar a velocidade de migração antecipada. Se qualquer correção for exigida para fornecer a largura de banda necessária, notifique a equipe responsável pelas [atividades de correção](../migrate/remediate.md).

> [!NOTE]
> O armazenamento total afeta diretamente os requisitos de largura de banda durante a replicação inicial. No entanto, o descompasso de armazenamento continua do ponto de replicação até o lançamento. Isso significa que i descompasso tem um efeito cumulativo na largura de banda disponível.

## <a name="next-steps"></a>Próximas etapas

Após a conclusão da avaliação de um sistema, as saídas alimentam o desenvolvimento de uma nova [arquitetura de nuvem](./architect.md).

> [!div class="nextstepaction"]
> [Arquitetar cargas de trabalho antes da migração](./architect.md)
