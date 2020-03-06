---
title: Otimizar e promover
description: Esta parte do Guia de Migração do Azure aborda áreas de otimização, incluindo a revisão do design da solução, o dimensionamento correto dos serviços e a análise de custos.
author: matticusau
ms.author: mlavery
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: bcd49a2168db862c3e1a0d948e4948abccbfe7c7
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222501"
---
<!-- cSpell:ignore Fservers Fdatabases -->

<!-- markdownlint-disable MD025 DOCSMD001 -->

# <a name="test-optimize-and-promote"></a>Testar, otimizar e promover

Agora que você migrou seus serviços para o Azure, a próxima fase inclui a revisão da solução para encontrar possíveis áreas de otimização. Esse esforço pode incluir examinar o design da solução, o dimensionamento correto dos serviços e a análise dos custos.

Essa fase também é uma oportunidade para otimizar seu ambiente e executar possíveis transformações nele. Por exemplo, você pode ter realizado uma migração "hospedar novamente" e, agora que seus serviços estão em execução no Azure, é possível revisitar a configuração das soluções ou os serviços consumidos e, possivelmente, executar algumas "refatorações" para modernizar e aumentar a funcionalidade da sua solução.

O restante deste artigo se concentra em ferramentas para otimizar a carga de trabalho migrada. Quando o equilíbrio entre desempenho e custo for atingido, uma carga de trabalho estará pronta para ser promovida para produção. Para obter orientação sobre as opções de promoção, confira os artigos de melhoria do processo em [Otimizar e promover](../migration-considerations/optimize/index.md).

# <a name="right-size-assets"></a>[Ativos do tamanho certo](#tab/optimize)

Todos os serviços do Azure que fornecem um modelo de custo baseado em consumo podem ser redimensionados por meio do portal do Azure, da CLI ou do PowerShell. A primeira etapa no dimensionamento correto de um serviço é revisar suas métricas de uso. O serviço do Azure Monitor fornece acesso a essas métricas. Talvez seja necessário configurar a coleta das métricas do serviço que você está analisando e proporcionar o tempo adequado para coletar dados significativos com base em seus padrões de carga de trabalho.

1. Acesse **Monitorar**.
1. Selecione **Métricas** e configure o gráfico para mostrar as métricas do serviço a ser analisado.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/metrics]" submitText="Go to Monitor" :::

::: zone-end

A seguir estão alguns serviços comuns que você pode redimensionar.

## <a name="resize-a-virtual-machine"></a>Redimensionar uma máquina virtual

As Migrações para Azure executam uma análise de dimensionamento correto como parte de sua fase de avaliação pré-migração, e as máquinas virtuais migradas usando essa ferramenta provavelmente já serão dimensionadas com base em seus requisitos pré-migração.

No entanto, para máquinas virtuais criadas ou migradas usando outros métodos ou nos casos em que os requisitos de máquina virtual após a migração precisem de ajuste, convém refinar ainda mais seu dimensionamento da máquina virtual.

1. Acesse **Máquinas virtuais**.
1. Selecione a máquina virtual desejada na lista.
1. Selecione o **Tamanho** e o novo tamanho desejado na lista. Talvez seja preciso ajustar os filtros para encontrar o tamanho necessário.
1. Selecione **Redimensionar**.

O redimensionamento de máquinas virtuais de produção pode causar interrupções de serviço. Tente aplicar o dimensionamento correto para suas VMs antes de promovê-las para produção.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Compute%2FVirtualMachines]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

- [Gerenciar reservas para recursos do Azure](https://docs.microsoft.com/azure/billing/billing-manage-reserved-vm-instance)
- [Redimensionar uma VM do Windows](https://docs.microsoft.com/azure/virtual-machines/windows/resize-vm)
- [Redimensionar uma máquina virtual do Linux usando a CLI do Azure](https://docs.microsoft.com/azure/virtual-machines/linux/change-vm-size)

Os parceiros podem usar o Partner Center para analisar o uso.

- [Dimensionamento de VM do Microsoft Azure para uso máximo de reserva](https://docs.microsoft.com/partner-center/azure-usage)

::: zone-end

## <a name="resize-a-storage-account"></a>Redimensionar uma conta de armazenamento

1. Acesse **Contas de armazenamento**.
1. Selecione a conta de armazenamento desejada.
1. Selecione **Configurar** e ajuste as propriedades da conta de armazenamento para atender às suas necessidades.
1. Clique em **Salvar**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Storage%2FStorageAccounts]" submitText="Go to Storage Accounts" :::

::: zone-end

## <a name="resize-a-sql-database"></a>Redimensionar um Banco de Dados SQL

1. Acesse **Bancos de dados SQL** ou **SQL Servers** e, em seguida, selecione o servidor.
1. Selecione o banco de dados desejado.
1. Selecione **Configurar** e o novo tamanho de camada de serviço desejado.
1. Escolha **Aplicar**.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Sql%2Fservers%2Fdatabases]" submitText="Go to SQL Databases" :::

::: zone-end

# <a name="cost-management"></a>[Gerenciamento de Custos](#tab/ManageCost)

É importante executar análises e revisões de custos contínuas. Esse esforço oferece uma oportunidade de redimensionar os recursos conforme a necessidade a fim de balancear os custos e a carga de trabalho.

O Gerenciamento de Custos do Azure funciona com o Assistente do Azure para fornecer recomendações de otimização de custo. O Assistente do Azure ajuda você a otimizar e melhorar a eficiência identificando recursos ociosos e subutilizados.

1. Selecione **Gerenciamento de Custos + Cobrança**.
1. Selecione **Recomendações do assistente** e a guia **Custos**.
1. Use o **Impacto** e a **Economia potencial por ano** para analisar os possíveis benefícios.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Billing/ModernBillingMenuBlade/Overview]" submitText="Go to Cost Management + Billing" :::

::: zone-end

Também é possível usar o **Assistente** e selecionar a guia **Custos** para identificar as recomendações de reduções de custo potenciais.

> [!TIP]
> Para serviços que não exigem disponibilidade contínua, a implementação de uma solução para iniciar, parar ou pausar o serviço, conforme necessário, pode ajudar a gerenciar o custo (por exemplo, Máquinas Virtuais do Azure ou SQL Data Warehouse do Azure).
>

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Expert/AdvisorBlade]" submitText="Go to Azure Advisor" :::

::: zone-end

::: zone target="docs"

- [Tutorial: Otimizar os custos usando recomendações](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations)
- [Evite cobranças inesperadas com o gerenciamento de custo e a cobrança do Azure](https://docs.microsoft.com/azure/billing/billing-getting-started)
- [Explorar e analisar os custos com a Análise de Custos](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis)

::: zone-end
