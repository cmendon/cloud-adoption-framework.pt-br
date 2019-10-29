---
title: Linha de base de gerenciamento aprimorada no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhorias comuns na linha de base de gerenciamento
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 85e289867ac69f3403d964078a7c3f3b2a6c96a7
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683695"
---
# <a name="enhanced-management-baseline-in-azure"></a>Linha de base de gerenciamento aprimorada no Azure

As três primeiras disciplinas de gerenciamento de nuvem descrevem uma linha de base de gerenciamento. Os artigos anteriores neste guia descreveram um MVP (produto mínimo viável) para serviços de gerenciamento de nuvem, denominados linha de base de gerenciamento. Este artigo descreve algumas melhorias na linha de base.

A finalidade de uma linha de base de gerenciamento é criar uma oferta consistente que forneça um nível mínimo de compromisso de negócios para **todas*** as cargas de trabalho com suporte. Essa linha de base de ofertas comuns de gerenciamento reproduzíveis permite que a equipe ofereça gerenciamento operacional altamente otimizado com o mínimo de desvio. No entanto, pode ser necessário um compromisso maior com a empresa além da oferta padrão. A imagem e os marcadores a seguir mostram três maneiras de ir além da linha de base de gerenciamento.

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:**
  - Maior investimento de operações por carga de trabalho.
  - Grau mais alto de resiliência.
  - Sugerido para aproximadamente 20% das cargas de trabalho que orientam o valor comercial.
  - Normalmente reservado geralmente para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:**
  - O investimento de operações é distribuído entre muitas cargas de trabalho.
  - As melhorias de resiliência afetam todas as cargas de trabalho que usam a plataforma definida.
  - Sugerido para +/- 20% das plataformas de maior criticalidade.
  - Normalmente reservado para cargas de trabalho de criticalidade média a alta.
- **Linha de base de gerenciamento aprimorada:**
  - Menor investimento de operações relativo.
  - Compromissos de negócios ligeiramente aprimorados usando ferramentas e processos de operações nativos de nuvem adicionais.

As operações de carga de trabalho e de plataforma exigirão que as alterações criem e arquitetem princípios. Essas alterações podem levar tempo e resultar em maiores despesas operacionais. Para reduzir o número de cargas de trabalho que exigem esses investimentos, uma linha de base de gerenciamento aprimorada poderia fornecer um aperfeiçoamento suficiente para o compromisso de negócios.

A tabela a seguir descreve alguns processos, ferramentas e possíveis impactos comuns em linhas de base de gerenciamento aprimoradas dos clientes.

|Disciplina  |Processo  |Ferramenta  |Possível impacto| Saiba mais |
|---------|---------|---------|---------|---------|
|Inventário e visibilidade|Controle de Alterações de Serviço|Gráfico de Recursos do Azure|Maior visibilidade sobre alterações nos serviços do Azure pode ajudar a detectar impactos negativos mais cedo ou a corrigir com mais rapidez|[Visão geral do Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview)|
|Inventário e visibilidade|Integração de ITSM (Gerenciamento de serviços de TI)|Conector de Gerenciamento do Serviço de TI|A conexão de ITSM automatizada cria reconhecimento mais cedo|[Conector ITSM do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/itsmc-overview)|
|Conformidade operacional|Automação de operações|Automação do Azure|Automatizar a conformidade operacional para uma resposta mais rápida e precisa a alterações|Veja abaixo|
|Conformidade operacional|Operações multinuvem|Hybrid Runbook Worker da Automação do Azure|Automatizar operações em várias nuvens|[Visão geral do runbook híbrido](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)|
|Conformidade operacional|Automação do convidado|DSC (Desire State Configuration)|Configuração baseada em código de SOs Convidados para reduzir erros e o descompasso de configuração|[Visão Geral da DSC](/powershell/scripting/dsc/overview/overview)|
|Proteger e recuperar|Notificação de violação|Central de Segurança do Azure|Estender a proteção para incluir gatilhos de recuperação de violação de segurança|Veja abaixo|

::: zone target="docs"

## <a name="azure-automation"></a>Automação do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-automationtabazureautomation"></a>[Automação do Azure](#tab/AzureAutomation)

::: zone-end

A Automação do Azure fornece um sistema centralizado para o gerenciamento de controles automatizados. Na Automação do Azure, os processos simples de correção, escala e otimização podem ser executados em resposta a métricas ambientais, reduzindo a sobrecarga associada ao processamento manual de incidentes. Mais importante, a correção automatizada pode ser fornecida quase em tempo real, reduzindo significativamente as interrupções dos processos de negócios. Um estudo das interrupções de negócios mais comuns identificará as atividades em seu ambiente que poderiam ser automatizadas.

### <a name="runbooks"></a>Runbooks

A unidade de código básica para fornecer correção automatizada é um runbook. Os runbooks contêm as instruções para correção ou recuperação de um incidente.

Para criar ou gerenciar runbooks:

1. Acesse [Automação do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
2. Escolha uma das **contas de automação** listadas.
3. Localize a seção **Automação de processos** da navegação do portal.
4. As opções nessa seção permitem que você crie ou gerencie runbooks, agendamentos e outras funcionalidades de correção automatizada.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts]" submitText="Assign Policy" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
::: zone target="docs"

## <a name="azure-security-center"></a>Central de Segurança do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-security-centertabazuresecuritycenter"></a>[Central de Segurança do Azure](#tab/AzureSecurityCenter)

::: zone-end

A Central de Segurança do Azure também desempenha uma parte importante em sua estratégia de proteger e recuperar. Ela pode ajudar você a monitorar a segurança de seus computadores, redes, armazenamento, serviços de dados e aplicativos. A Central de Segurança do Azure fornece detecção avançada de ameaças usando análise comportamental e aprendizado de máquina para ajudar a identificar ameaças ativas visando seus recursos do Azure. Também fornece proteção contra ameaças que bloqueia malware ou outros códigos indesejados e reduz a área de superfície exposta à força bruta e outros ataques à rede.

Quando a Central de Segurança do Azure identifica uma ameaça, ela dispara um alerta de segurança com etapas que precisam ser tomadas para responder a um ataque. Ele também fornece um relatório com informações sobre a ameaça que foi detectada.

A Central de Segurança do Azure é oferecida em duas camadas de serviço: gratuita e standard. Recursos como recomendações de segurança estão disponíveis na camada gratuita. A camada standard fornece proteção adicional, como detecção de ameaças avançada e proteção em suas cargas de trabalho de nuvem híbrida.

::: zone target="chromeless"

### <a name="action"></a>Ação

**Experimente o nível Standard gratuitamente pelos primeiros 30 dias.**

Depois de habilitar e configurar políticas de segurança para recursos da uma assinatura, você poderá exibir o estado de segurança de seus recursos e todos os problemas na seção **Prevenção**. Você também pode exibir uma lista desses problemas no bloco **Recomendações** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Para explorar a Central de Segurança do Azure, vá para o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação da Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center).

::: zone-end
