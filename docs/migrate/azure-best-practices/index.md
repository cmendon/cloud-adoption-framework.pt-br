---
title: Melhores práticas de migração do Azure
description: Use o Cloud Adoption Framework para o Azure para saber como implementar as ferramentas necessárias para se alinhar às melhores práticas de migração na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 90ec573d59c88187081fd640d9eb769977b787cf
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79091421"
---
# <a name="best-practices-for-cloud-migration"></a>Melhores práticas para migração na nuvem

O [guia de migração do Azure](../azure-migration-guide/index.md) no Cloud Adoption Framework é o ponto de partida sugerido se você está interessado em migrar para o Azure. Esse guia percorre um conjunto de ferramentas e abordagens básicas para migrar máquinas virtuais para a nuvem. Esta seção do Cloud Adoption Framework aborda muitas melhores práticas que vão além das ferramentas básicas nativas de nuvem.

## <a name="cloud-migration-best-practice-checklist"></a>Lista de verificação de melhores práticas de migração na nuvem

A lista de verificação a seguir descreve as áreas comuns de complexidade que podem exigir a expansão do escopo da migração para além do [guia de migração do Azure](../azure-migration-guide/index.md).

### <a name="business-driven-scope-expansion"></a>Expansão de escopo controlada por negócios

- **[Dar suporte a mercados globais](./multiple-regions.md):** a empresa opera em várias regiões geográficas com requisitos de soberania de dados díspares. Para atender a esses requisitos, é preciso levar em conta fatores adicionais na análise de pré-requisitos e na distribuição de ativos durante a migração.

### <a name="technology-driven-scope-expansion"></a>Expansão de escopo controlada por tecnologia

- **[Migração do VMware](./vmware-host.md):** A migração de hosts VMware pode acelerar o processo geral de migração. Cada host VMware migrado pode mover várias cargas de trabalho para a nuvem usando uma abordagem de lift-and-shift. Após a migração, essas VMs e cargas de trabalho podem permanecer no VMware ou serem migradas para funcionalidades de nuvem modernas.
- **[Migração do SQL Server](./sql-migration.md):** A migração de SQL Servers pode acelerar o processo geral de migração. Cada SQL Server migrado pode mover vários bancos de dados e serviços, potencialmente acelerando várias cargas de trabalho.
- **[Vários datacenters](./multiple-datacenters.md):** A migração de vários data centers cria muita complexidade. Durante os processos de avaliação, migração, otimização e gerenciamento, são discutidas considerações adicionais como preparação para ambientes mais complexos.
- **[Os requisitos de dados ultrapassam a capacidade da rede](./network-capacity-exceeded.md):** as empresas frequentemente optam por migrar para a nuvem porque a capacidade, a velocidade ou a estabilidade de um datacenter existente não são mais satisfatórias. Essas mesmas restrições adicionam complexidade ao processo de migração, exigindo um planejamento adicional durante os processos de avaliação e migração.
- **[Estratégia de governança ou conformidade](./governance-or-compliance.md):** Quando governança e conformidade são vitais para o sucesso de uma migração, é necessário alinhamento adicional entre as equipes de governança de TI e a equipe de adoção de nuvem.

Se qualquer uma dessas complexidades estiver presente em seu cenário, esta seção da Cloud Adoption Framework provavelmente fornecerá o tipo de orientação necessária para alinhar adequadamente o escopo nos processos de migração.

Cada um desses cenários é abordado pelos vários artigos nesta seção da estrutura de adoção de nuvem.

## <a name="next-steps"></a>Próximas etapas

Navegue no sumário à esquerda para abordar necessidades específicas ou alterações de escopo. Como alternativa, a primeira melhoria de escopo na lista, [Suporte a mercados globais](./multiple-regions.md), é um bom ponto de partida ao examinar esses cenários.

> [!div class="nextstepaction"]
> [Dar suporte a mercados globais](./multiple-regions.md)
