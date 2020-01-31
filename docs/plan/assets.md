---
title: Alinhando ativos a cargas de trabalho priorizadas
description: Alinhando ativos a cargas de trabalho priorizadas
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 0f005e6b770edb3c89cb033113fdd07e1cd5af0b
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76800518"
---
# <a name="align-assets-to-prioritized-workloads"></a>Alinhar ativos a cargas de trabalho priorizadas

A carga de trabalho é uma descrição conceitual de uma coleção de ativos: VMs, aplicativos e fontes de dados. O artigo anterior, [priorizar e definir cargas de trabalho](./workloads.md), forneceu diretrizes para coletar os dados que definirão a carga de trabalho. Antes da migração, algumas das entradas técnicas nessa lista exigem validação adicional. Este artigo ajuda com a validação das seguintes entradas:

- **Aplicativos:** Listar todos os aplicativos incluídos nessa carga de trabalho.
- **VMs e servidores:** Listar quaisquer VMs ou servidores incluídos na carga de trabalho.
- **Fontes de dados:** Listar todas as fontes de dados incluídas na carga de trabalho.
- **Dependências:** Listar quaisquer dependências de ativos não incluídas na carga de trabalho.

Há várias opções para montar esses dados. A seguir estão algumas das abordagens mais comuns.

## <a name="alternative-inputs-migrate-modernize-innovate"></a>Entradas alternativas: migrar, modernizar, inovar

O objetivo dos pontos de dados anteriores é capturar o esforço técnico relativo e as dependências como um auxílio à priorização. Dependendo da transição desejada, talvez seja necessário reunir pontos de dados alternativos para dar suporte à priorização adequada.

**Migrar:** Para esforços de migração pura, o inventário existente e as dependências de ativos servem como uma medida justa de complexidade relativa.

**Modernizar:** Quando a meta de uma carga de trabalho é modernizar aplicativos ou outros ativos, esses pontos de dados ainda são medidas sólidas de complexidade. No entanto, pode ser prudente adicionar uma entrada para oportunidades de modernização à documentação da carga de trabalho.

**Inovar:** Quando a lógica de negócios ou os dados está passando por alteração de material durante um esforço de adoção de nuvem, ele é considerado um tipo *inovador* de transformação. O mesmo é verdadeiro quando você está criando novos dados ou uma nova lógica de negócios. Para qualquer cenário de inovações, a migração de ativos provavelmente representará a menor quantidade de esforço necessária. Para esses cenários, a equipe deve planejar um conjunto de entradas de dados técnicos para medir a complexidade relativa.

## <a name="azure-migrate"></a>Migrações para Azure

As migrações para Azure fornecem um conjunto de funções de agrupamento que podem acelerar a agregação de aplicativos, VMs, fontes de dados e dependências. Depois que as cargas de trabalho são definidas conceitualmente, elas podem ser usadas como base para agrupar ativos com base no mapeamento de dependência.

A documentação de migrações para Azure fornece orientação sobre [como agrupar máquinas com base em dependências](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies).

## <a name="configuration-management-database"></a>Configuração-banco de dados de gerenciamento

Algumas organizações têm um CMDB (banco de dados de gerenciamento de configuração) bem mantido em suas ferramentas de gerenciamento de operações existentes. Eles poderiam usar o CMDB de forma alternativa para fornecer os pontos de dados de entrada discutidos anteriormente.

## <a name="next-steps"></a>Próximos passos

[Revise decisões de racionalização](./review-rationalization.md) com base em definições de carga de trabalho e alinhamento de ativos.

> [!div class="nextstepaction"]
> [Revisar decisões de racionalização](./review-rationalization.md)
