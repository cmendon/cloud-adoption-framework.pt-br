---
title: Especialização de plataforma para gerenciamento de nuvem no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhore as operações de gerenciamento de nuvem específicas da plataforma.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 0386a8c30758cce6c1c3d23bfa73d1f90e919692
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556965"
---
# <a name="platform-specialization-for-cloud-management"></a>Especialização de plataforma para gerenciamento de nuvem

Assim como a linha de base de gerenciamento aprimorado, a especialização de plataforma é a extensão além da linha de base de gerenciamento padrão. Veja abaixo uma lista com marcadores e visual das maneiras de expandir a linha de base de gerenciamento. Este artigo aborda a opção de especialização da plataforma.

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:** Maior investimento de operações por carga de trabalho. Grau mais alto de resiliência. Sugerido para +/- 20% das cargas de trabalho que orientam o valor comercial. Reservado geralmente para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:** O investimento de operações é distribuído entre muitas cargas de trabalho. As melhorias de resiliência afetam todas as cargas de trabalho que usam a plataforma definida. Sugerido para +/- 20% das plataformas de maior criticalidade. Reservado geralmente para cargas de trabalho de criticalidade média a alta.
- **Linha de base de gerenciamento aprimorada:** Menor investimento de operações relativo. Compromissos de negócios ligeiramente aprimorados usando ferramentas e processos de operações nativos de nuvem adicionais.

As operações de carga de trabalho e de plataforma exigirão que as alterações criem e arquitetem princípios. Essas alterações podem levar tempo e resultar em maiores despesas operacionais. Para reduzir o número de cargas de trabalho que exigem esses investimentos, uma linha de base de gerenciamento aprimorada poderia fornecer um aperfeiçoamento suficiente para o compromisso de negócios.

A tabela a seguir descreve alguns processos, ferramentas e possíveis impactos comuns em linhas de base de gerenciamento aprimoradas dos clientes.

|Processo  |Ferramenta  |Finalidade  |Nível de Gerenciamento Sugerido  |
|---------|---------|---------|---------|
|Melhorar o design do sistema|Estrutura de Arquitetura do Azure|Melhorar o design de arquitetura da plataforma para melhorar operações|
|Automatizar a correção|Automação do Azure|Responder a dados avançados de plataforma com automação específica da plataforma|Operações de Plataforma|
|Catálogo de Serviços|Centro de aplicativos gerenciados|Fornecer um catálogo de autoatendimento de soluções aprovadas que atendam aos padrões organizacionais|Operações de Plataforma|
|Desempenho do contêiner|Azure Monitor para Contêineres|Monitoramento e diagnóstico de contêineres|Operações de Plataforma|
|Desempenho de dados PaaS|Azure SQL Analytics|Monitoramento e diagnóstico para bancos de dados PaaS|Operações de Plataforma|
|Desempenho de dados IaaS|Verificação de Integridade do SQL Server|Monitoramento e diagnóstico para bancos de dados IaaS|Operações de Plataforma|

## <a name="high-level-process"></a>Processo de alto nível

A especialização de plataforma consiste em uma execução disciplinada dos quatro processos a seguir em uma abordagem iterativa. Cada processo é explicado mais detalhadamente nas seguintes seções deste artigo.

- **Melhorar o design do sistema:** melhore o design de sistemas comuns (ou plataformas) para minimizar efetivamente as interrupções.
- **Automatizar a correção:** algumas melhorias não são econômicas. Nesses casos, talvez faça mais sentido automatizar a correção e reduzir o impacto de interrupções.
- **Dimensionar a solução:** à medida que o design dos sistemas e a correção automatizada são aprimorados, essas alterações podem ser dimensionadas em todo o ambiente por meio do catálogo de serviços.
- **Melhoria contínua:** várias ferramentas de monitoramento podem ser usadas para descobrir melhorias incrementais que podem ser abordadas na próxima etapa do design, da automação e da escala do sistema.

::: zone target="docs"

## <a name="improve-system-design"></a>Melhorar o design do sistema

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Melhorar o design do sistema](#tab/SystemsDesign)

::: zone-end

Melhorar o design do sistema é a abordagem mais eficaz para melhorar operações de qualquer plataforma comum. Por meio de melhorias de design do sistema, a estabilidade pode aumentar e as interrupções de negócios podem diminuir. O design de sistemas individuais está fora do escopo da exibição de ambiente obtido em todo o Cloud Adoption Framework. Como um complemento a essa estrutura, a Estrutura de Arquitetura do Azure oferece melhores práticas para melhorar a resiliência e o design de um sistema específico. Essas melhorias de design podem ser aplicadas ao design de sistemas de uma plataforma ou uma carga de trabalho específica.

A Estrutura da Arquitetura do Azure concentra-se na melhoria em cinco pilares do design do sistema:

- **Escalabilidade:** dimensionar os ativos de plataforma comuns para lidar com o aumento da carga.
- **Disponibilidade:** diminuir as interrupções de negócios melhorando o potencial de tempo de atividade.
- **Resiliência:** melhorar os tempos de recuperação para reduzir a duração de interrupções.
- **Segurança:** proteger aplicativos e dados contra ameaças externas.
- **Gerenciamento:** processos operacionais específicos para esses ativos de plataforma comuns.

A maioria das interrupções de negócios equivale a alguma forma de dívida técnica ou deficiência na arquitetura. Para implantações existentes, as melhorias no design dos sistemas podem ser exibidas como pagamentos com relação à dívida técnica existente. Para novas implantações, as melhorias no design dos sistemas podem ser exibidas como prevenção de dívida técnica. A próxima guia, “Correção automatizada”, examina maneiras de tratar a dívida técnica que não podem ou não devem ser tratadas.

Saiba mais sobre a [Estrutura de Arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) para melhorar o design do sistema.

Conforme o design do sistema é aprimorado, retorne a este artigo para encontrar novas oportunidades de melhorar e dimensionar esses aprimoramentos em seu ambiente.

::: zone target="docs"

## <a name="automated-remediation"></a>Correção Automatizada

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correção Automatizada](#tab/AutomatedRemediation)

::: zone-end

Algumas dívidas técnicas não podem ser resolvidas. A resolução pode ser muito cara para corrigir. A resolução pode ser planejada, mas ter uma longa duração de projeto. Pode ser que a interrupção dos negócios não tenha um impacto significativo nos negócios ou que a prioridade dos negócios seja recuperar-se rapidamente em vez de investir em resiliência.

Quando a resolução da dívida técnica não for o caminho desejado, a correção automatizada será comumente a próxima etapa desejada. Usar a Automação do Azure e o Azure Monitor para detectar tendências e fornecer correção automatizada é a abordagem mais comum para a correção automatizada.

Para obter diretrizes sobre correção automatizada, confira este artigo sobre [Alertas e Automação do Azure](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Dimensionar a solução com um catálogo de serviços

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Dimensionar a solução com um catálogo de serviços](#tab/ServiceCatalog)

::: zone-end

A base da especialização e das operações de plataforma é um catálogo de serviços bem gerenciado. É assim que as melhorias no design dos sistemas e na correção são dimensionadas em um ambiente. A equipe da plataforma de nuvem e a equipe de automação de nuvem se alinham para criar soluções reproduzíveis para as plataformas mais comuns em qualquer ambiente. No entanto, se essas soluções não forem utilizadas consistentemente, o gerenciamento de nuvem poderá fornecer um pouco mais do que uma oferta de linha de base.

Para maximizar a adoção e minimizar a sobrecarga de manutenção de qualquer plataforma otimizada, a plataforma deve ser adicionada a um catálogo de serviços no Azure. Cada aplicativo no catálogo pode ser implantado para consumo interno por meio do catálogo de serviços ou como uma oferta de marketplace para consumidores externos.

Para obter instruções sobre como publicar em um catálogo de serviços, confira a série de artigos sobre como [publicar em um catálogo de serviços](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="deploy-applications-from-the-service-catalog"></a>Implantar aplicativos do catálogo de serviços

1. No portal do Azure, pesquise **Centro de aplicativos gerenciados (versão prévia)** .
2. Clique em **Aplicativos do catálogo de serviços** na seção **Procurar** da navegação do portal.
3. Clique em **+ Adicionar** para escolher uma definição de aplicativo no catálogo de serviços da sua empresa.

Os aplicativos gerenciados que você está atendendo são exibidos aqui.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gerenciar aplicativos do catálogo de serviços

1. No portal do Azure, pesquise **Centro de aplicativos gerenciados (versão prévia)** .
2. Clique em **Aplicativos do Catálogo de Serviços** na seção **Serviço** da navegação do portal.

Os aplicativos gerenciados que você está atendendo são exibidos aqui.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Melhoria contínua

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Melhoria Contínua](#tab/ContinuousImprovement)

::: zone-end

A especialização de plataforma e as operações de plataforma dependem de loops de comentários fortes entre as equipes de adoção, de plataforma, de automação e de gerenciamento. A fundamentação desses loops de comentários em dados capacita cada equipe a tomar decisões sábias. Para que as operações de plataforma alcancem compromissos de negócios de longo prazo, é importante usar insights específicos da plataforma centralizada. Como os contêineres e o SQL Server são as duas plataformas mais comuns gerenciadas centralmente, veja a seguir alguns artigos para ajudá-lo a começar a usar a coleta de dados de melhoria contínua.

[Desempenho do contêiner](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
[Desempenho do banco de dados PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
[Desempenho do banco de dados IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
