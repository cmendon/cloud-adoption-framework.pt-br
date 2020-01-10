---
title: Proteger, monitorar e gerenciar ativos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de monitoramento e gerenciamento seguros
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: c311e4e789c7e5cc6c3b409fb2a4dbdcbfafe8ea
ms.sourcegitcommit: 7df593a67a2e77b5f61c815814af9f0c36ea5ebd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75781837"
---
# <a name="secure-monitoring-and-management-tools"></a>Ferramentas de monitoramento e gerenciamento seguros

Após a migração ser concluída, os ativos migrados devem ser gerenciados pelas operações de TI controladas. Este artigo não representa um desvio das práticas operacionais recomendadas. Em vez disso, o seguinte deve ser considerado como um produto viável mínimo para proteger e gerenciar ativos migrados, sejam de operações de TI ou independentemente conforme as operações de TI ficarem online.

## <a name="monitoring"></a>Monitoramento

*Monitoramento* é o ato de coletar e analisar dados para determinar o desempenho, a integridade e a disponibilidade da sua carga de trabalho empresarial e os recursos dos quais ela depende. O Azure inclui vários serviços que individualmente executam uma função ou tarefa específica no espaço de monitoramento. Juntos, esses serviços oferecem uma solução abrangente para coletar, analisar e agir na telemetria de seus aplicativos de carga de trabalho e dos recursos do Azure que lhes dão suporte. Ganhe visibilidade sobre a integridade e o desempenho dos aplicativos, a infraestrutura e os dados no Azure com as ferramentas de monitoramento na nuvem, como o Azure Monitor, o Log Analytics e o Application Insights. Use essas ferramentas de monitoramento na nuvem para agir e integrar com suas soluções de gerenciamento de serviços:

- **Monitoramento principal.** O monitoramento principal fornece monitoramento necessário e fundamental nos recursos do Azure. Esses serviços requerem configuração mínima e coletam a telemetria fundamental utilizada pelos serviços de monitoramento Premium.
- **Monitoramento profundo de infraestrutura e aplicativo.** Os serviços do Azure fornecem recursos avançados para coletar e analisar dados de monitoramento em um nível mais profundo. Esses serviços compilam monitoramento principal e aproveitam as vantagens da funcionalidade comum no Azure. Eles fornecem uma análise poderosa com os dados coletados para fornecer informações exclusivas sobre seus aplicativos e sua infraestrutura.

Saiba mais sobre o [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) para monitoramento de ativos migrados.

## <a name="security-monitoring"></a>Monitoramento de segurança

Conte com a Central de Segurança do Azure para um monitoramento de segurança unificado e notificação avançada contra ameaças nas cargas de trabalho de nuvem híbrida. A Central de Segurança oferece visibilidade e controle totais da segurança de seus aplicativos de nuvem no Azure. Detecte ameaças rapidamente e tome medidas para responder a elas e reduzir a exposição habilitando proteção adaptável contra ameaças. O painel interno fornece informações instantâneas sobre alertas de segurança e vulnerabilidades que exigem atenção. A Central de Segurança do Azure pode ajudar com muitas funções, incluindo:

- **Monitoramento centralizado de políticas.** Garanta a conformidade com requisitos de segurança da empresa ou de regulamentação gerenciando políticas de segurança de forma centralizada nas cargas de trabalho de nuvem híbrida.
- **Avaliação contínua de segurança.** Monitore a segurança de computadores, redes, armazenamento e serviços de dados e aplicativos para descobrir problemas potenciais de segurança.
- **Recomendações práticas.** Corrija vulnerabilidades de segurança antes que elas sejam exploradas por invasores. Inclua recomendações de segurança priorizadas e práticas.
- **Defesas avançadas de nuvem.** Reduza ameaças com acesso Just-In-Time a portas de gerenciamento e listas seguras para controlar aplicativos em execução em suas VMs.
- **Alertas e incidentes priorizados.** Concentre-se primeiro nas ameaças mais críticas, com incidentes e alertas de segurança priorizados.
- **Soluções de segurança integradas.** Colete, pesquise e analise dados de segurança de uma variedade de fontes, incluindo soluções de parceiros conectadas.

Saiba mais sobre a [Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center) para proteger ativos migrados.

## <a name="service-health-monitoring"></a>Monitoramento da integridade do serviço

A Integridade do Serviço do Azure fornece alertas e diretrizes personalizados quando problemas de serviço do Azure afetam você. Ela pode notificar e ajudar a entender o impacto dos problemas, mantendo você atualizado sobre a resolução do problema. Ela também ajuda você a preparar manutenções planejadas e alterações que poderão afetar a disponibilidade de seus recursos.

- **Painel de integridade do serviço.** Verifique a integridade geral de seus serviços e regiões do Azure, com atualizações detalhadas sobre qualquer problema de serviço atual, manutenção planejada futura e transições de serviço.
- **Alertas de integridade do serviço.** Configure alertas que notificarão você e suas equipes no caso de um problema de serviço, como uma interrupção ou uma manutenção planejada futura.
- **Histórico de integridade do serviço.** Examine os problemas de serviço anteriores e baixe resumos oficiais e relatórios da Microsoft.

Saiba mais sobre a [Integridade do Serviço do Azure ](https://docs.microsoft.com/azure/service-health) para ficar informado sobre a integridade dos recursos migrados.

## <a name="protect-assets-and-data"></a>Proteger dados e ativos

O Backup do Azure fornece uma maneira de proteger VMs, arquivos e dados. O Backup do Azure pode ajudar com muitas funções, incluindo:

- Fazer backup de VMs.
- Fazer backup de arquivos.
- Fazer backup de bancos de dados do SQL Server.
- Recuperar ativos protegidos.

Saiba mais sobre o [Backup do Azure](https://docs.microsoft.com/azure/backup) para proteger ativos migrados.

## <a name="optimize-resources"></a>Otimizar os recursos

O Assistente do Azure é seu guia personalizado de melhores práticas do Azure. Ele analisa suas configurações e a telemetria de uso e oferece recomendações para ajudar a otimizar seus recursos do Azure para alta disponibilidade, segurança, desempenho e custo. As ações embutidas do Assistente ajudam você a corrigir suas recomendações de maneira rápida e fácil e a otimizar suas implantações.

- **Melhores práticas do Azure.** Otimize a alta disponibilidade, a segurança, o desempenho e o custo dos recursos migrados do Azure.
- **Diretrizes passo a passo.** Corrija recomendações com eficiência com links rápidos guiados.
- **Novos alertas de recomendações.** Mantenha-se informado sobre novas recomendações, como oportunidades adicionais para dimensionar VMs e economizar dinheiro.

Saiba mais sobre o [Assistente do Azure ](https://docs.microsoft.com/azure/advisor/advisor-overview) para otimizar seus recursos migrados.

## <a name="suggested-skills"></a>Habilidades sugeridas

O Microsoft Learn é uma nova abordagem para o aprendizado. A preparação para as novas habilidades e responsabilidades que acompanham a adoção de nuvem não é fácil. O Microsoft Learn oferece uma abordagem mais recompensadora para o aprendizado prático que ajuda você a atingir suas metas mais rapidamente. Ganhe pontos e níveis e conquiste mais!

Aqui está um exemplo de um roteiro de aprendizagem personalizado no Microsoft Learn, alinhado com a parte Proteger e Gerenciar da Cloud Adoption Framework: 

[Proteja seus dados de nuvem](https://docs.microsoft.com/learn/paths/secure-your-cloud-data/): O Azure foi projetado para segurança e conformidade. Saiba como aproveitar os serviços internos para armazenar seus dados de aplicativo com segurança para garantir que somente serviços e clientes autorizados tenham acesso a eles.
