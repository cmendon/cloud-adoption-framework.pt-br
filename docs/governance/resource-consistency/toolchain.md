---
title: Ferramentas de consistência de recursos no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de consistência de recursos no Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6a0a2303473cffd9bb5175c67e12a84d6baa2814
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70824087"
---
# <a name="resource-consistency-tools-in-azure"></a>Ferramentas de consistência de recursos no Azure

A [Consistência de recurso](index.md) é uma das [Cinco disciplinas de Governança de Nuvem](../governance-disciplines.md). Essa disciplina se concentra em formas de estabelecer políticas relacionadas à gestão operacional de um ambiente, aplicativo ou carga de trabalho. Dentro das cinco disciplinas de governança de nuvem, a disciplina de consistência de recursos envolve o monitoramento do desempenho do aplicativo, da carga de trabalho e do ativo. Ele também envolve as tarefas necessárias para atender às demandas de escala, corrigir violações de SLA de desempenho e evitar proativamente violações de SLA de desempenho por meio de correção automatizada.

A seguir, é apresentada uma lista de ferramentas nativas do Azure que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

| Ferramenta | [Portal do Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)  | [Azure Blueprints](/azure/governance/blueprints/overview) | [Automação do Azure](/azure/automation/automation-intro) | [Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) | [Serviço de Backup do Azure](/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| Implantação de recursos                             | Sim | Sim | Sim | sim | Não  | Não | Não |
| Gerenciar recursos                             | Sim | Sim | Sim | sim | Não  | Não | Não |
| Implantar recursos usando modelos             | Não  | Sim | Não  | Sim | Não  | Não | Não |
| Implantação do ambiente orquestrada          | Não  | Não  | Sim | Não  | Não  | Não | Não |
| Definir grupos de recurso                       | Sim | Sim | sim | Não  | Não  | Não | Não |
| Gerenciar os proprietários da carga de trabalho e conta           | Sim | Sim | sim | Não  | Não  | Não | Não |
| Gerenciar acesso condicional aos recursos       | Sim | Sim | sim | Não  | Não  | Não | Não |
| Configurar usuários do RBAC                         | Sim | Não  | Não  | Não  | Sim | Não | Não |
| Atribuir funções e permissões para recursos | Sim | Sim | sim | Não  | Sim | Não | Não |
| Definir dependência entre recursos        | Não  | Sim | sim | Não  | Não  | Não | Não |
| Aplicar controle de acesso                         | Sim | Sim | sim | Não  | Sim | Não | Não |
| Avaliar disponibilidade e escalabilidade          | Não  | Não  | Não  | Sim | Não  | Não | Não |
| Aplicar marcas aos recursos                      | Sim | Sim | sim | Não  | Não  | Não | Não |
| Atribuir regras do Azure Policy                    | Sim | Sim | sim | Não  | Não  | Não | Não |
| Aplicar a correção automatizada                  | Não  | Não  | Não  | Sim | Não  | Não | Não |
| Gerenciar a cobrança                               | Sim | Não  | Não  | Não  | Não  | Não | Não |
| Preparar recursos para recuperação de desastre         | Sim | Sim | sim | Não  | Não  | Sim | Sim |
|Recuperar dados durante uma interrupção ou violação de SLA     | Não | Não  | Não  | Não  | Não  | Sim | Sim |
|Recuperar aplicativos e dados durante uma interrupção ou violação de SLA     | Não | Não  | Não  | Não  | Não  | Sim | Sim |

Junto com essas ferramentas de consistência de recursos e recursos, você precisará monitorar seus recursos implantados para problemas de desempenho e integridade. O [Azure Monitor](/azure/azure-monitor/overview) é o monitoramento padrão e solução de relatórios no Azure. O Azure Monitor fornece recursos para monitorar seus recursos de nuvem. Esta lista mostra qual recurso aborda os requisitos de monitoramento comuns.

| Ferramenta | [Portal do Azure](https://azure.microsoft.com/features/azure-portal) | [Application Insights](/azure/application-insights/app-insights-overview) | [Log Analytics](/azure/azure-monitor/log-query/log-query-overview) | [API REST do Azure Monitor](/rest/api/monitor) |
|----------------------------------------------------|--------------|----------------------|---------------|------------------------|
| Dados telemétricos de máquina virtual do log                 | Não           | Não                   | Sim           | Não                     |
| Dados telemétricos de rede virtual do log              | Não           | Não                   | Sim           | Não                     |
| Dados telemétricos de serviços PaaS de Log                   | Não           | Não                   | Sim           | Não                     |
| Dados telemétricos de aplicativo de log                     | Não           | Sim                  | Não            | Não                     |
| Configurar alertas e relatórios                       | Sim          | Não                   | Não            | Sim                    |
| Agendar relatórios regulares ou análise personalizada        | Não           | Não                   | Não            | Não                     |
| Visualizar e analisar dados de desempenho e log     | Sim          | Não                   | Não            | Não                     |
| Integrar a solução de monitoramento de terceiros ou locais     | Não           | Não                   | Não            | Sim                    |

Ao planejar a implantação, será necessário considerar onde os dados de registro em log serão armazenados e como os [serviços de relatório e monitoramento baseados em nuvem serão integrados](../../decision-guides/log-and-report/index.md) com os processos e as ferramentas existentes.

> [!NOTE]
> As organizações também usam ferramentas de DevOps de terceiros para monitorar recursos e cargas de trabalho. Para obter mais informações, consulte [integração da ferramenta DevOps](https://azure.microsoft.com/products/devops-tool-integrations).

## <a name="next-steps"></a>Próximas etapas

Aprenda como criar, atribuir e gerenciar [definições de políticas](/azure/governance/policy) no Azure.
