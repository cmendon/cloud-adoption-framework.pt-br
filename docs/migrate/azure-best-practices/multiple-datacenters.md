---
title: Vários datacenters
description: Vários datacenters
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 9156df0b76f6edf1d249d5d724e0a5d0f4fd8e15
ms.sourcegitcommit: 58ea417a7df3318e3d1a76d3807cc4e7e3976f52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78898064"
---
# <a name="multiple-datacenters"></a>Vários datacenters

Geralmente, o escopo de uma migração envolve a transição de vários datacenters. As diretrizes a seguir expandirão o escopo do [guia de migração do Azure](../azure-migration-guide/index.md) para abordar vários datacenters.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

A maior parte do esforço necessário na expansão do escopo ocorrerá durante os processos de pré-requisitos, avaliação e otimização da migração.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Antes de iniciar a migração, você precisa criar Epics na ferramenta de gerenciamento de projeto para representar cada datacenter a ser migrado. É importante entender as motivações e os resultados do negócio, que justificam essa migração. Essas motivações podem ser usadas para priorizar a lista de Epics (ou datacenters). Por exemplo, se a migração visasse sair dos datacenters antes que as concessões sejam renovadas, cada Epic seria priorizado com base na data de renovação da concessão.

Em cada Epic, as cargas de trabalho a serem avaliadas e migradas seriam gerenciadas como recursos. Cada ativo dentro dessa carga de trabalho seria gerenciado como uma história de usuário. O trabalho necessário para avaliar, migrar, otimizar, promover, proteger e gerenciar cada ativo seria representado como tarefas para cada ativo.

Então, os sprints ou iterações seriam formados por uma série de tarefas necessárias para migrar os ativos e as histórias de usuários confirmadas pela equipe de adoção da nuvem. Os lançamentos consistiriam em uma ou mais cargas de trabalho ou recursos a serem promovidos para a produção.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

A maior mudança no processo de avaliação, ao expandir o escopo para lidar com vários datacenters, está relacionada à gravação precisa e à priorização de cargas de trabalho e dependências entre os datacenters.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

**Avaliar dependências entre datacenters:** As [ferramentas de visualização de dependência nas migrações para Azure](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization) podem ajudar a identificar dependências. O uso desse conjunto de ferramentas antes da migração é uma melhor prática geral. No entanto, ao lidar com a complexidade global, ela se torna uma etapa necessária para o processo de avaliação. Por meio do [agrupamento de dependências](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies), a visualização pode ajudar a identificar os endereços IP e as portas de ativos necessários para dar suporte à carga de trabalho.

> [!IMPORTANT]
> Duas observações importantes: primeiro, um especialista no assunto com uma compreensão do posicionamento do ativo e dos esquemas de endereço IP é necessário para identificar os ativos que residem em um datacenter secundário. Depois, é importante avaliar as dependências de downstream e os clientes no visual para entender as dependências bidirecionais.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

A migração de vários datacenters é semelhante à consolidação de datacenters. Após a migração, a nuvem se torna a solução de datacenter singular para vários ativos. A expansão de escopo mais provável durante o processo de migração é a validação e o alinhamento de endereços IP.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

Confira a seguir as atividades que afetam muito o sucesso de uma migração na nuvem:

- **Avaliar conflitos de rede:** Ao consolidar data centers em um único provedor de nuvem, há uma probabilidade de criar conflitos de rede, DNS ou outros. Durante a migração, é importante testar se há conflitos, a fim de evitar interrupções em sistemas de produção hospedados na nuvem.
- **Atualizar tabelas de roteamento:** Muitas vezes, as modificações nas tabelas de roteamento são necessárias ao consolidar redes ou data centers.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Durante a otimização, podem ser necessários testes adicionais.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Ação sugerida durante o processo de otimização e promoção

Antes da promoção, é importante fornecer níveis adicionais de teste durante essa expansão de escopo. Durante o teste, é importante testar o roteamento ou outros conflitos de rede. Além disso, é importante isolar o aplicativo implantado e testá-lo novamente para validar se todas as dependências foram migradas para a nuvem. Nesse caso, o isolamento significa separar o ambiente implantado das redes de produção. Isso pode capturar ativos ignorados que ainda estão em execução no local.

## <a name="secure-and-manage-process-changes"></a>Alterações na proteção e no gerenciamento de processos

A proteção e o gerenciamento de processos precisam permanecer inalterados nessa expansão de escopo.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Retorne à [Lista de verificação de escopo expandido](./index.md) para garantir que o método de migração esteja totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
