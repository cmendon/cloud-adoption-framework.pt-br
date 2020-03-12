---
title: Lista de pendências de iteração e de lançamento
description: Use a estrutura de adoção de nuvem para o Azure para aprender a criar um registro posterior e de liberação para organizar suas tarefas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7204511d8b3f83d18f8179e04c4fd400151a7f3a
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79094182"
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

## <a name="next-steps"></a>Próximas etapas

Depois que a lista de pendências de iteração for definida e aceita pela equipe de adoção da nuvem, as [aprovações do gerenciamento de alterações](./approve.md) poderão ser finalizadas.

> [!div class="nextstepaction"]
> [Aprovar alterações na arquitetura antes da migração](./approve.md)
