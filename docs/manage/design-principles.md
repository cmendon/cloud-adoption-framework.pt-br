---
title: Princípios de design e operações avançadas
description: Aprenda a aplicar princípios de design e opções avançadas para criar uma oferta que forneça um nível mínimo de compromisso de negócios para todas as cargas de trabalho com suporte.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a5861b23e5cc408957f922472dd6ee863c7c13fa
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341038"
---
# <a name="apply-design-principles-and-advanced-operations"></a>Aplicar princípios de design e operações avançadas

As três primeiras disciplinas de gerenciamento de nuvem descrevem uma linha de base de gerenciamento. No mínimo, uma linha de base de gerenciamento deve incluir um compromisso de negócios padrão para minimizar interrupções de negócios e acelerar a recuperação se o serviço for interrompido. A maioria das linhas de base de gerenciamento inclui um foco disciplinado na manutenção de "inventário e visibilidade", "conformidade operacional" e "proteção e recuperação".

A finalidade de uma linha de base de gerenciamento é criar uma oferta consistente que forneça um nível mínimo de compromisso de negócios para todas as cargas de trabalho com suporte. Essa linha de base de ofertas de gerenciamento comuns e reproduzíveis permite que a equipe forneça um grau de gerenciamento operacional altamente otimizado, com um desvio mínimo. Mas essa oferta padrão pode não fornecer um compromisso suficientemente avançado com os negócios.

O diagrama na próxima seção ilustra três maneiras de ir além da linha de base de gerenciamento.

A linha de base de gerenciamento deve atender ao compromisso mínimo exigido por 80% das cargas de trabalho de menor importância no portfólio. A linha de base não deve ser aplicada a cargas de trabalho de missão crítica. Nem deve ser aplicado a plataformas comuns que são compartilhadas entre cargas de trabalho. Essas cargas de trabalho exigem um foco nos princípios de design e nas operações avançadas.

## <a name="advanced-operations-options"></a>Opções de operações avançadas

Há três caminhos sugeridos para melhorar os compromissos comerciais além da linha de base de gerenciamento, conforme mostrado no diagrama a seguir:

![Operações avançadas](../_images/manage/beyond-the-baseline.png)

## <a name="enhanced-management-baseline"></a>Linha de base de gerenciamento aprimorado

Conforme descrito no guia de gerenciamento do Azure, uma linha de base de gerenciamento aprimorado usa ferramentas nativas de nuvem para melhorar o tempo de atividade e diminuir os tempos de recuperação. As melhorias são significativas, mas menos do que com a especialização de carga de trabalho ou plataforma. A vantagem de uma linha de base de gerenciamento aprimorada é a redução igualmente significativa em custo e tempo de implementação.

## <a name="management-specialization"></a>Especialização de gerenciamento

Os aspectos da carga de trabalho e das operações de plataforma podem exigir alterações nos princípios de design e arquitetura. Essas alterações podem levar tempo e podem resultar em maiores despesas operacionais. Para reduzir o número de cargas de trabalho que exigem esses investimentos, uma linha de base de gerenciamento aprimorada poderia fornecer um aperfeiçoamento suficiente para o compromisso de negócios.

Para cargas de trabalho que garantem um investimento maior para atender a um compromisso de negócios, a especialização das operações é fundamental.

## <a name="areas-of-management-specialization"></a>Áreas de especialização de gerenciamento

Há duas áreas de especialização:

- **Especialização de plataforma:** Investir em operações contínuas de uma plataforma compartilhada, distribuindo o investimento entre várias cargas de trabalho.
- **Especialização de carga de trabalho:** Invista em operações contínuas de uma carga de trabalho específica, geralmente reservada para cargas de trabalho de missão crítica.

### <a name="central-it-or-cloud-center-of-excellence-ccoe"></a>TI central ou centro de excelência em nuvem (CCoE)

As decisões entre a especialização de plataforma e a especialização de carga de trabalho são baseadas na criticalidade e no impacto de cada carga de trabalho. No entanto, essas decisões também são indícios de decisões culturais maiores entre os modelos organizacionais de ti central e CCoE.

A especialização de carga de trabalho geralmente aciona uma mudança cultural. Ti tradicional e central de ti os dois processos de compilação que podem fornecer suporte em escala. O suporte a escala é mais atingível para serviços repetíveis encontrados em uma linha de base de gerenciamento, linha de base aprimorada ou até mesmo operações de plataforma. A especialização de carga de trabalho não é geralmente dimensionada. Essa falta de escala dificulta para uma organização de ti centralizada fornecer o suporte necessário sem alcançar as limitações de escala organizacional.

Como alternativa, uma abordagem do Cloud Center of Excellence é dimensionada pela delegação proposital de responsabilidade e centralização seletiva. A especialização de carga de trabalho tende a se alinhar melhor à abordagem de responsabilidade delegada de um CCoE.

O alinhamento natural das funções em um CCoE é descrito da seguinte maneira:

- A equipe da plataforma de nuvem ajuda a criar plataformas comuns que dão suporte a várias equipes de adoção de nuvem.
- A equipe de automação de nuvem estende essas plataformas para ativos implantáveis em um catálogo de serviços.
- O gerenciamento de nuvem fornece a linha de base de gerenciamento centralmente e ajuda a dar suporte ao uso do catálogo de serviços.
- Mas a unidade de negócios (na forma de uma equipe de DevOps de negócios ou de adoção de nuvem) tem a responsabilidade de operações cotidianas da carga de trabalho, do pipeline ou do desempenho.

Para o alinhamento das áreas de gerenciamento, os modelos de ti central e CCoE geralmente podem ser fornecidos na especialização da plataforma, com uma alteração cultural mínima. A oferta da especialização de carga de trabalho pode ser um pouco mais complexa para as equipes de ti central.

## <a name="management-specialization-processes"></a>Processos de especialização de gerenciamento

Em cada especialização, o processo de quatro etapas a seguir é fornecido em uma abordagem iterativa disciplinada. Essa abordagem requer parceria entre a adoção da nuvem, a plataforma de nuvem, a automação de nuvem e os especialistas em gerenciamento de nuvem para criar um loop de comentários viável e informado.

- **Melhorar o design do sistema:** Aprimore o design de sistemas comuns (plataformas) ou cargas de trabalho específicas para minimizar efetivamente as interrupções.
- **Automatizar a correção:** Algumas melhorias não são econômicas. Nesses casos, pode fazer mais sentido automatizar a correção e reduzir o impacto das interrupções.
- **Dimensionar a solução:** À medida que o design de sistemas e a correção automatizada são aprimorados, você pode dimensionar essas alterações em todo o ambiente por meio do catálogo de serviços.
- **Aperfeiçoamento contínuo:** Você pode usar várias ferramentas de monitoramento para descobrir melhorias incrementais para abordar na próxima etapa do design, da automação e da escala do sistema.

### <a name="improve-system-design"></a>Melhorar o design do sistema

Melhorar o design do sistema é a abordagem mais eficaz para melhorar operações de qualquer plataforma comum. As melhorias de design do sistema podem ajudar a aumentar a estabilidade e diminuir as interrupções de negócios. O design de sistemas individuais está fora do escopo da exibição de ambiente obtido em todo o Cloud Adoption Framework. Como um complemento a essa estrutura, a Estrutura de Arquitetura do Azure oferece melhores práticas para melhorar a resiliência e o design de um sistema específico. Você pode aplicar essas melhorias de design ao design de sistemas de uma plataforma ou uma carga de trabalho específica.

A Estrutura da Arquitetura do Azure concentra-se na melhoria em cinco pilares do design do sistema:

- **Escalabilidade:** Dimensionamento dos ativos de plataforma comuns para lidar com o aumento da carga.
- **Disponibilidade:** Diminuindo as interrupções de negócios, melhorando o potencial de tempo de atividade.
- **Resiliência:** Melhorar os tempos de recuperação para reduzir a duração das interrupções.
- **Segurança:** Proteção de aplicativos e dados de ameaças externas.
- **Gerenciamento:** Processos de operações específicos para esses ativos de plataforma comuns.

A maioria das interrupções de negócios equivale a alguma forma de dívida técnica ou deficiência na arquitetura. Para implantações existentes, as melhorias no design dos sistemas podem ser exibidas como pagamentos com relação à dívida técnica existente. Para novas implantações, as melhorias no design dos sistemas podem ser exibidas como prevenção de dívida técnica. A próxima seção, "correção automatizada", analisa maneiras de abordar a dívida técnica que não pode ou não ser resolvida.

Para ajudar a melhorar o design do sistema, saiba mais sobre a [estrutura de arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars). Conforme o design do seu sistema aprimora, retorne a este artigo para encontrar novas oportunidades para melhorar e dimensionar as melhorias em seu ambiente.

### <a name="automated-remediation"></a>Correção automatizada

Uma dívida técnica não pode ou não ser resolvida. A resolução pode ser muito cara para corrigir. Pode ser planejado, mas pode ter uma duração longa do projeto. A interrupção dos negócios pode não ter um impacto significativo nos negócios, ou a prioridade dos negócios é recuperar-se rapidamente em vez de investir em resiliência.

Quando a resolução da dívida técnica não for o caminho desejado, a correção automatizada será comumente a próxima etapa desejada. Usar a Automação do Azure e o Azure Monitor para detectar tendências e fornecer correção automatizada é a abordagem mais comum para a correção automatizada.

Para obter orientação sobre correção automatizada, consulte [Alertas e Automação do Azure](https://docs.microsoft.com/azure/automation/automation-create-alert-triggered-runbook).

### <a name="scale-the-solution-with-a-service-catalog"></a>Dimensionar a solução com um catálogo de serviços

A base da especialização e das operações de plataforma é um catálogo de serviços bem gerenciado. É assim que as melhorias no design dos sistemas e na correção são dimensionadas em um ambiente. A equipe da plataforma de nuvem e a equipe de automação de nuvem se alinham para criar soluções reproduzíveis para as plataformas mais comuns em qualquer ambiente. Mas, se essas soluções não forem aplicadas consistentemente, o gerenciamento de nuvem poderá fornecer pouco mais do que uma oferta de linha de base.

Para maximizar a adoção e minimizar a sobrecarga de manutenção de qualquer plataforma otimizada, a plataforma deve ser adicionada a um catálogo de serviços. Cada aplicativo no catálogo pode ser implantado para consumo interno por meio do catálogo de serviços ou como uma oferta de marketplace para consumidores externos.

Para obter informações sobre como publicar em um catálogo de serviços, consulte a série sobre [publicação em um catálogo de serviços](https://docs.microsoft.com/azure/managed-applications/publish-service-catalog-app).

### <a name="continuous-improvement"></a>Melhoria contínua

A especialização de plataforma e as operações de plataforma dependem de loops de comentários fortes entre as equipes de adoção, de plataforma, de automação e de gerenciamento. A fundamentação desses loops de comentários em dados capacita cada equipe a tomar decisões sábias. Para que as operações de plataforma obtenham compromissos de negócios de longo prazo, é importante aproveitar as informações específicas para a plataforma centralizada. Como os contêineres e SQL Server são as duas plataformas mais comuns gerenciadas centralmente, considere a introdução à coleta de dados de melhoria contínua revisando os seguintes artigos:

- [Desempenho do contêiner](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview)
- [Desempenho do Banco de Dados PaaS](https://docs.microsoft.com/azure/azure-monitor/insights/azure-sql)
- [Desempenho do Banco de Dados IaaS](https://docs.microsoft.com/azure/azure-monitor/insights/sql-assessment)
