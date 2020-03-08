---
title: Lista de verificação de escopo expandido da migração na nuvem
description: Lista de verificação de escopo expandido da migração na nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 730da49f910c34bf2bd94b8766cb292520201e50
ms.sourcegitcommit: 58ea417a7df3318e3d1a76d3807cc4e7e3976f52
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78892626"
---
# <a name="expanded-scope-for-cloud-migration"></a>Escopo expandido para migração na nuvem

O [guia de migração do Azure](../azure-migration-guide/index.md) na Cloud Adoption Framework é o ponto de partida sugerido para leitores interessados em uma migração de novo host para o Azure, também conhecida como migração "lift-and-shift". Esse guia o orienta por uma série de pré-requisitos, ferramentas e abordagens para a migração de máquinas virtuais para a nuvem.

Embora este guia seja uma linha de base eficaz para familiarizar-se com este tipo de migração, ele faz várias suposições. Essas suposições, ao fornecerem uma abordagem simplificada a migrações, alinham o guia com muitos dos leitores da Cloud Adoption Framework. Esta seção da Cloud Adoption Framework aborda alguns cenários de migração de escopo expandido que ajudam a conduzir os esforços quando essas suposições não se aplicam.

## <a name="cloud-migration-expanded-scope-checklist"></a>Lista de verificação de escopo expandido da migração na nuvem

A lista de verificação a seguir descreve as áreas comuns de complexidade que podem exigir a expansão do escopo da migração para além do [guia de migração do Azure](../azure-migration-guide/index.md).

### <a name="business-driven-scope-expansion"></a>Expansão de escopo controlada por negócios

- **[Dar suporte a mercados globais](../azure-best-practices/multiple-regions.md):** a empresa opera em várias regiões geográficas com requisitos de soberania de dados díspares. Para atender a esses requisitos, é preciso levar em conta fatores adicionais na análise de pré-requisitos e na distribuição de ativos durante a migração.

### <a name="technology-driven-scope-expansion"></a>Expansão de escopo controlada por tecnologia

- **[Migração do VMware](../azure-best-practices/vmware-host.md):** A migração de hosts VMware pode acelerar o processo geral de migração. Cada host VMware migrado pode mover várias cargas de trabalho para a nuvem usando uma abordagem de lift-and-shift. Após a migração, essas VMs e cargas de trabalho podem permanecer no VMware ou serem migradas para funcionalidades de nuvem modernas.
- **[Migração do SQL Server](../azure-best-practices/sql-migration.md):** A migração de SQL Servers pode acelerar o processo geral de migração. Cada SQL Server migrado pode mover vários bancos de dados e serviços, potencialmente acelerando várias cargas de trabalho.
- **[Vários datacenters](../azure-best-practices/multiple-datacenters.md):** A migração de vários data centers cria muita complexidade. Durante os processos de avaliação, migração, otimização e gerenciamento, são discutidas considerações adicionais como preparação para ambientes mais complexos.
- **[Os requisitos de dados ultrapassam a capacidade da rede](../azure-best-practices/network-capacity-exceeded.md):** as empresas frequentemente optam por migrar para a nuvem porque a capacidade, a velocidade ou a estabilidade de um datacenter existente não são mais satisfatórias. Essas mesmas restrições adicionam complexidade ao processo de migração, exigindo um planejamento adicional durante os processos de avaliação e migração.
- **[Estratégia de governança ou conformidade](../azure-best-practices/governance-or-compliance.md):** Quando governança e conformidade são vitais para o sucesso de uma migração, é necessário alinhamento adicional entre as equipes de governança de TI e a equipe de adoção de nuvem.

Se qualquer uma dessas complexidades estiver presente em seu cenário, esta seção da Cloud Adoption Framework provavelmente fornecerá o tipo de orientação necessária para alinhar adequadamente o escopo nos processos de migração.

Cada um desses cenários é abordado pelos vários artigos nesta seção da estrutura de adoção de nuvem.

## <a name="next-steps"></a>Próximas etapas

Navegue no sumário à esquerda para abordar necessidades específicas ou alterações de escopo. Como alternativa, a primeira melhoria de escopo na lista, [Suporte a mercados globais](../azure-best-practices/multiple-regions.md), é um bom ponto de partida ao examinar esses cenários.

> [!div class="nextstepaction"]
> [Dar suporte a mercados globais](../azure-best-practices/multiple-regions.md)
