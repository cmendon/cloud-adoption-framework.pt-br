---
title: Lista de pendências de iteração e de lançamento
description: Criar uma lista de pendências de iteração e de lançamento
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 604ce189a1518f87660d8f29d33413581e9b00f6
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802439"
---
# <a name="manage-change-in-an-incremental-migration-effort"></a>Gerenciar alteração em um esforço de migração incremental

Este artigo pressupõe que os processos de migração sejam incrementais por natureza, sendo executados paralelamente ao [processo de controle](../../../govern/index.md). No entanto, as mesmas diretrizes poderiam ser usadas para popular tarefas inicias em uma estrutura de detalhamento de trabalho para abordagens tradicionais de gerenciamento de alterações em cascata.

## <a name="release-backlog"></a>Lista de pendências de lançamento

Uma *lista de pendências de lançamento* é composta por de uma série de ativos (VMs, bancos de dados, arquivos e aplicativos, entre outros) que devem ser migrados antes que uma carga de trabalho possa ser lançada para uso de produção na nuvem. Durante cada iteração, a equipe de adoção da nuvem documenta e estima os esforços necessários para mover cada ativo para a nuvem. Confira a seção “Lista de pendências de iteração” a seguir.

## <a name="iteration-backlog"></a>Lista de pendências de iteração

Uma *lista de pendências de iteração* é uma lista do trabalho detalhado necessário para migrar um número específico de ativos da propriedade digital existente para a nuvem. As entradas nessa lista geralmente são armazenadas em uma ferramenta de gerenciamento ágil, como o Azure DevOps, como itens de trabalho.

Antes de iniciar a primeira iteração, a equipe de adoção da nuvem especifica uma duração da iteração, geralmente de duas a quatro semanas. Essa caixa de hora é importante para criar um período de tempo de início e de término para cada conjunto de atividades confirmadas. Manter janelas de execução consistentes facilita a medição da velocidade (ritmo de migração) e do alinhamento às necessidades empresariais em mudança constante.

Antes de cada iteração, a equipe examina a lista de pendências de lançamento, estimando o esforço e as prioridades dos ativos a serem migrados. Ela confirma para oferecer um número específico de migrações acordadas. Depois que for acordado pela equipe de adoção da nuvem, a lista de atividades se tornará a *lista de pendências de iteração atual*.

Durante cada iteração, os membros da equipe trabalham como uma equipe de auto-organização para atender aos compromissos na lista de pendências de iteração atual.

## <a name="next-steps"></a>Próximos passos

Depois que a lista de pendências de iteração for definida e aceita pela equipe de adoção da nuvem, as [aprovações do gerenciamento de alterações](./approve.md) poderão ser finalizadas.

> [!div class="nextstepaction"]
> [Aprovar alterações na arquitetura antes da migração](./approve.md)
