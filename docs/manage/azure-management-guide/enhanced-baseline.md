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
ms.openlocfilehash: cfe7fdfa47b04cbcff7e09b18c5ba6a0b4fec795
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565517"
---
# <a name="enhanced-management-baseline-in-azure"></a>Linha de base de gerenciamento aprimorada no Azure

As três primeiras disciplinas de gerenciamento de nuvem descrevem uma linha de base de gerenciamento. Os artigos anteriores neste guia descreveram um MVP (produto mínimo viável) para serviços de gerenciamento de nuvem que são conhecidos como uma linha de base de gerenciamento. Este artigo descreve algumas melhorias na linha de base.

A finalidade de uma linha de base de gerenciamento é criar uma oferta consistente que forneça um nível mínimo de compromisso de negócios para *todas* as cargas de trabalho com suporte. Com essa linha de base de ofertas de gerenciamento comuns e reproduzíveis, a equipe pode fornecer um gerenciamento operacional altamente otimizado com o mínimo de desvio.

No entanto, talvez seja necessário um compromisso maior com os negócios além da oferta padrão. A imagem e a lista a seguir mostram três maneiras de ir além da linha de base de gerenciamento.

![Além da linha de base de gerenciamento de nuvem](../../_images/manage/beyond-the-baseline.png)

- **Operações de carga de trabalho:**
  - Maior investimento de operações por carga de trabalho.
  - Grau mais alto de resiliência.
  - Sugerido para aproximadamente 20% das cargas de trabalho que orientam o valor comercial.
  - Normalmente reservado geralmente para cargas de trabalho críticas ou altamente críticas.
- **Operações de plataforma:**
  - O investimento de operações é distribuído entre muitas cargas de trabalho.
  - As melhorias de resiliência afetam todas as cargas de trabalho que usam uma plataforma definida.
  - Sugerido para aproximadamente 20% das plataformas que têm maior importância.
  - Normalmente reservado para cargas de trabalho de criticalidade média a alta.
- **Linha de base de gerenciamento aprimorada:**
  - Menor investimento de operações relativo.
  - Compromissos de negócios ligeiramente aprimorados usando ferramentas e processos de operações nativos de nuvem adicionais.

As operações de carga de trabalho e de plataforma exigirão alterações nos princípios de design e arquitetura. Essas alterações podem levar tempo e resultar em maiores despesas operacionais. Para reduzir o número de cargas de trabalho que exigem esses investimentos, uma linha de base de gerenciamento aprimorada pode fornecer um aperfeiçoamento suficiente para o compromisso de negócios.

Esta tabela descreve alguns processos, ferramentas e possíveis impactos comuns nas linhas de base de gerenciamento aprimoradas dos clientes:

| Disciplina  | Processo  | Ferramenta | Possível impacto | Saiba mais |
|---|---|---|---|---|
|Inventário e visibilidade|Controle de alterações de serviço|Gráfico de Recursos do Azure|Uma maior visibilidade das alterações nos serviços do Azure pode ajudar a detectar impactos negativos mais cedo ou corrigir com mais rapidez.|[Visão geral do Azure Resource Graph](https://docs.microsoft.com/azure/governance/resource-graph/overview)|
|Inventário e visibilidade|Integração de ITSM (Gerenciamento de serviços de TI)|Conector de Gerenciamento do Serviço de TI|A conexão de ITSM automatizada cria reconhecimento mais cedo.|[ITSMC (Conector de Gerenciamento de Serviços de TI)](https://docs.microsoft.com/azure/azure-monitor/platform/itsmc-overview)|
|Conformidade operacional|Automação de operações|Automação do Azure|Automatize a conformidade operacional para uma resposta mais rápida e precisa a alterações.|Consulte as seções a seguir|
|Conformidade operacional|Operações multinuvem|Hybrid Runbook Worker da Automação do Azure|Automatize as operações em várias nuvens.|[Visão geral do Hybrid Runbook Worker](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)|
|Conformidade operacional|Automação do convidado| DSC (Configuração de Estado Desejado)|Configuração baseada em código de sistemas operacionais convidados para reduzir erros e descompasso de configuração.|[Visão Geral da DSC](https://docs.microsoft.com/powershell/scripting/dsc/overview/overview)|
|Proteger e recuperar|Notificação de violação|Central de Segurança do Azure|Estenda a proteção para incluir gatilhos de recuperação de violação de segurança.|Consulte as seções a seguir|

::: zone target="docs"

## <a name="azure-automation"></a>Automação do Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-automationtabazureautomation"></a>[Automação do Azure](#tab/AzureAutomation)

::: zone-end

A Automação do Azure fornece um sistema centralizado para o gerenciamento de controles automatizados. Na Automação do Azure é possível executar processos simples de correção, escala e otimização em resposta às métricas ambientais. Esses processos reduzem a sobrecarga associada ao processamento manual de incidentes.

O mais importante é que a correção automatizada pode ser fornecida quase em tempo real, reduzindo significativamente as interrupções dos processos de negócios. Um estudo sobre as interrupções de negócios mais comuns identifica as atividades em seu ambiente que poderiam ser automatizadas.

### <a name="runbooks"></a>Runbooks

A unidade básica de código para fornecer a correção automatizada é um runbook. Os runbooks contêm as instruções para correção ou recuperação de um incidente.

Para criar ou gerenciar runbooks:

1. Acesse [Automação do Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Automation%2FAutomationAccounts).
1. Selecione **Contas de automação** e escolha uma das contas listadas.
1. Acesse **Automação de processos**.
1. Com as opções apresentadas é possível criar ou gerenciar runbooks, agendas e outras funcionalidades de correção automática.

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

A Central de Segurança do Azure também desempenha uma parte importante em sua estratégia de proteger e recuperar. Ela pode ajudar você a monitorar a segurança de seus computadores, redes, armazenamento, serviços de dados e aplicativos.

A Central de Segurança do Azure fornece detecção avançada de ameaças usando análise comportamental e aprendizado de máquina para ajudar a identificar ameaças ativas visando seus recursos do Azure. Ela também fornece proteção contra ameaças que bloqueia malwares ou outros códigos indesejados, além de reduzir a área de superfície exposta à força bruta e outros ataques à rede.

Quando a Central de Segurança do Azure identifica uma ameaça, ela dispara um alerta de segurança com as etapas necessárias para responder a um ataque. Ela também fornece um relatório com informações sobre a ameaça detectada.

A Central de Segurança do Azure é oferecida em duas camadas: Gratuita e Standard. Recursos como recomendações de segurança estão disponíveis na Camada gratuita. A camada Standard fornece proteção adicional, como detecção de ameaças avançada e proteção em suas cargas de trabalho de nuvem híbrida.

::: zone target="chromeless"

### <a name="action"></a>Ação

#### <a name="try-standard-tier-for-free-for-your-first-30-days"></a>Experimente a camada Standard gratuitamente pelos primeiros 30 dias

Depois de habilitar e configurar as políticas de segurança para os recursos de uma assinatura, será possível exibir o estado de segurança de seus recursos e todos os problemas no painel **Prevenção**. Você também pode exibir uma lista desses problemas no bloco **Recomendações** .

::: form action="OpenBlade[#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0]" submitText="Explore Azure Security Center" :::

::: zone-end

::: zone target="docs"

Para explorar a Central de Segurança do Azure, vá para o [portal do Azure](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/SecurityMenuBlade/0).

### <a name="learn-more"></a>Saiba mais

Para obter mais informações, veja a [documentação da Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center).

::: zone-end
