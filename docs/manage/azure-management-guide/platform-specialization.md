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
ms.openlocfilehash: 8c3954627ee991f43c2b8d3a94dbd77746d3d4b2
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752928"
---
# <a name="platform-specialization-for-cloud-management"></a>Especialização de plataforma para gerenciamento de nuvem

Assim como a linha de base de gerenciamento aprimorado, a especialização de plataforma é a extensão além da linha de base de gerenciamento padrão. Consulte a seguinte imagem e lista que mostram as maneiras de expandir a linha de base de gerenciamento. Este artigo aborda as opções de especialização de plataforma.

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:** O maior investimento de operações por carga de trabalho e o maior grau de resiliência. Sugerimos operações de carga de trabalho para aproximadamente 20% das cargas de trabalho que impulsionam o valor comercial. Essa especialização geralmente é reservada para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:** O investimento de operações é distribuído entre muitas cargas de trabalho. As melhorias de resiliência afetam todas as cargas de trabalho que usam uma plataforma definida. Sugerimos operações de plataforma para aproximadamente 20% das plataformas que têm a maior importância. Essa especialização geralmente é reservada para cargas de trabalho de média a alta importância.
- **Linha de base de gerenciamento aprimorada:** O investimento relativamente menor em operações. Essa especialização melhora um pouco os compromissos de negócios usando processos e ferramentas de operações nativas de nuvem adicionais.

As operações de carga de trabalho e plataforma exigem alterações nos princípios de design e arquitetura. Essas alterações podem levar tempo e resultar em maiores despesas operacionais. Para reduzir o número de cargas de trabalho que exigem esses investimentos, uma linha de base de gerenciamento aprimorada poderia fornecer um aperfeiçoamento suficiente para o compromisso de negócios.

Esta tabela descreve alguns processos, ferramentas e possíveis impactos comuns nas linhas de base de gerenciamento aprimoradas dos clientes:

|Processo  |Ferramenta  |Finalidade  |Nível de gerenciamento sugerido  |
|---------|---------|---------|---------|
|Melhorar o design do sistema|Estrutura de Arquitetura do Azure|Melhorar o design de arquitetura da plataforma para melhorar as operações|N/D|
|Automatizar a correção|Automação do Azure|Responder a dados avançados da plataforma com uma automação específica da plataforma|Operações de plataforma|
|Catálogo de serviços|Centro de aplicativos gerenciados|Fornecer um catálogo de autoatendimento de soluções aprovadas que atendam aos padrões organizacionais|Operações de plataforma|
|Desempenho do contêiner|Azure Monitor para contêineres|Monitoramento e diagnóstico de contêineres|Operações de plataforma|
|Desempenho de dados de PaaS (plataforma como serviço)|Azure SQL Analytics|Monitoramento e diagnóstico para bancos de dados PaaS|Operações de plataforma|
|Desempenho de dados de IaaS (infraestrutura como serviço)|Verificação de Integridade do SQL Server|Monitoramento e diagnóstico para bancos de dados IaaS|Operações de plataforma|

## <a name="high-level-process"></a>Processo de alto nível

A especialização de plataforma consiste em uma execução disciplinada dos quatro processos a seguir em uma abordagem iterativa. Cada processo é explicado com mais detalhes nas seções posteriores deste artigo.

- **Melhorar o design do sistema:** Melhore o design de sistemas ou plataformas comuns para minimizar efetivamente as interrupções.
- **Automatizar a correção:** Algumas melhorias não são econômicas. Nesses casos, talvez faça mais sentido automatizar a correção e reduzir o impacto das interrupções.
- **Dimensionar a solução:** à medida que o design dos sistemas e a correção automatizada são aprimorados, essas alterações podem ser dimensionadas em todo o ambiente por meio do catálogo de serviços.
- **Melhoria contínua:** Diferentes ferramentas de monitoramento podem ser usadas para descobrir melhorias incrementais. Essas melhorias podem ser abordadas na próxima etapa do design, da automação e da escala do sistema.

::: zone target="docs"

## <a name="improve-system-design"></a>Melhorar o design do sistema

::: zone-end
::: zone target="chromeless"

## <a name="improve-system-designtabsystemsdesign"></a>[Melhorar o design do sistema](#tab/SystemsDesign)

::: zone-end

Melhorar o design do sistema é a abordagem mais eficaz para melhorar operações de qualquer plataforma comum. Por meio de melhorias de design do sistema, a estabilidade pode aumentar e as interrupções de negócios podem diminuir. O design de sistemas individuais está fora do escopo da exibição de ambiente que é executada durante toda a Estrutura de Adoção de Nuvem para o Azure.

Como complemento à Estrutura de Adoção de Nuvem, a Estrutura de Arquitetura do Azure fornece práticas recomendadas para melhorar a resiliência e o design de um sistema específico. Essas melhorias de design podem ser aplicadas ao design de sistemas, de uma plataforma ou de uma carga de trabalho específica.

A Estrutura da Arquitetura do Azure concentra-se na melhoria em cinco pilares de design do sistema:

- **Escalabilidade:** Dimensionar ativos de plataforma comuns para lidar com o aumento da carga
- **Disponibilidade:** Reduzir as interrupções de negócios melhorando o potencial de tempo de atividade
- **Resiliência:** Melhorar os tempos de recuperação para reduzir a duração das interrupções
- **Segurança:** Proteger aplicativos e dados contra ameaças externas
- **Gerenciamento:** Processos operacionais específicos para esses ativos de plataforma comuns

A dívida técnica e as falhas arquitetônicas causam a maioria das interrupções nos negócios. Para implantações existentes é possível exibir as melhorias de design do sistema, como pagamentos em relação à dívida técnica existente. Para as novas implantações é possível exibir essas melhorias como forma de evitar a dívida técnica.

A seguinte guia **Correção automatizada** mostra maneiras de corrigir a dívida técnica que não pode ou não deve ser tratada.

Saiba mais sobre a [Estrutura de Arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) para melhorar o design do sistema.

Conforme o design do sistema é aprimorado, retorne a este artigo para encontrar novas oportunidades de melhorar e dimensionar esses aprimoramentos em seu ambiente.

::: zone target="docs"

## <a name="automated-remediation"></a>Correção automatizada

::: zone-end
::: zone target="chromeless"

## <a name="automated-remediationtabautomatedremediation"></a>[Correção automatizada](#tab/AutomatedRemediation)

::: zone-end

Algumas dívidas técnicas não podem ser resolvidas. A resolução pode ser muito cara para corrigir ou pode ser planejada, mas tem uma longa duração do projeto. A interrupção dos negócios pode não ter um impacto comercial significativo. Ou a prioridade empresarial pode ser recuperada rapidamente em vez de investir em resiliência.

Quando a resolução da dívida técnica não for a abordagem desejada, a correção automatizada será normalmente a próxima etapa desejada. Usar a Automação do Azure e o Azure Monitor para detectar tendências e fornecer correção automatizada é a abordagem mais comum para a correção automatizada.

Para obter orientação sobre correção automatizada, consulte [Alertas e Automação do Azure](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

::: zone target="docs"

## <a name="scale-the-solution-with-a-service-catalog"></a>Dimensionar a solução com um catálogo de serviços

::: zone-end
::: zone target="chromeless"

## <a name="scale-the-solution-with-a-service-catalogtabservicecatalog"></a>[Dimensionar a solução com um catálogo de serviços](#tab/ServiceCatalog)

::: zone-end

Um catálogo de serviços bem gerenciado é a base da especialização de plataforma e das operações de plataforma. O uso de um catálogo é como as melhorias no design e na correção dos sistemas são dimensionadas em um ambiente.

A equipe da plataforma de nuvem e a equipe de automação de nuvem se alinham para criar soluções reproduzíveis para as plataformas mais comuns em qualquer ambiente. No entanto, se essas soluções não forem usadas de forma consistente, o gerenciamento de nuvem poderá fornecer um pouco mais do que uma oferta de linha de base.

Para maximizar a adoção e minimizar a sobrecarga de manutenção de qualquer plataforma otimizada, você deve adicionar a plataforma a um catálogo de serviços do Azure. É possível implantar cada aplicativo no catálogo para consumo interno por meio do catálogo de serviços ou como uma oferta do Marketplace para consumidores externos.

Para obter instruções sobre como publicar em um catálogo de serviços, confira a série de artigos sobre como [publicar em um catálogo de serviços](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="deploy-applications-from-the-service-catalog"></a>Implantar aplicativos do catálogo de serviços

1. No portal do Azure, acesse **Centro de aplicativos gerenciados (versão prévia)** .
2. No painel **Procurar**, selecione **Aplicativos do Catálogo de Serviços**.
3. Clique em **Adicionar +** para escolher uma definição de aplicativo no catálogo de serviços de sua empresa.

Todos os aplicativos gerenciados que você estiver reparando serão exibidos.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/browseServiceCatalog]" submitText="Go to Virtual Machines" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

### <a name="manage-service-catalog-applications"></a>Gerenciar aplicativos do catálogo de serviços

1. No portal do Azure, acesse **Centro de aplicativos gerenciados (versão prévia)** .
1. No painel **Serviço**, selecione **Aplicativos do Catálogo de Serviços**.

Todos os aplicativos gerenciados que você estiver reparando serão exibidos.

::: zone target="chromeless"

::: form action="OpenBlade[#blade/Microsoft_Azure_Appliance/ManagedAppsHubBlade/serviceServiceCatalogApps]" submitText="Go to Virtual Machines" :::

::: zone-end

::: zone target="docs"

## <a name="continuous-improvement"></a>Melhoria contínua

::: zone-end
::: zone target="chromeless"

## <a name="continuous-improvementtabcontinuousimprovement"></a>[Melhoria contínua](#tab/ContinuousImprovement)

::: zone-end

A especialização e as operações de plataforma dependem de loops de comentários fortes entre a adoção, a plataforma, a automação e as equipes de gerenciamento. Fundamentar esses loops de comentários em dados ajuda cada equipe a tomar decisões inteligentes. Para que as operações de plataforma obtenham compromissos de negócios de longo prazo é importante usar informações específicas para a plataforma centralizada.

Contêineres e SQL Server são as duas plataformas mais comuns gerenciadas de forma centralizada. Estes artigos podem ajudar você a começar a usar a coleta de dados de melhoria contínua nestas plataformas:

- [Desempenho do contêiner](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Desempenho do Banco de Dados PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Desempenho do Banco de Dados IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
