---
title: Proteger e gerenciar
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de monitoramento e gerenciamento seguros
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 14bd697a3332466fb97043d3420d80b1dca50679
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818124"
---
# <a name="secure-monitoring-and-management-tools"></a>Ferramentas de monitoramento e gerenciamento seguros

Após a migração ser concluída, os ativos migrados devem ser gerenciados pelas operações de TI controladas. Este artigo não se destina a sugerir um desvio das melhores práticas operacionais. Em vez disso, o seguinte deve ser considerado como um produto viável mínimo para proteger e gerenciar ativos migrados, sejam de operações de TI ou independentemente conforme as operações de TI ficarem online.

## <a name="monitoring"></a>Monitoramento

*Monitoramento* é o ato de coletar e analisar dados para determinar o desempenho, a integridade e a disponibilidade da sua carga de trabalho empresarial e os recursos dos quais ela depende. O Azure inclui vários serviços que individualmente executam uma função ou tarefa específica no espaço de monitoramento. Juntos, esses serviços oferecem uma solução abrangente para coletar, analisar e agir na telemetria de seus aplicativos de carga de trabalho e dos recursos do Azure que lhes dão suporte. Ganhe visibilidade sobre a integridade e o desempenho dos aplicativos, a infraestrutura e os dados no Azure com as ferramentas de monitoramento na nuvem, como o Azure Monitor, o Log Analytics e o Application Insights. Use essas ferramentas de monitoramento na nuvem para agir e integrar com suas soluções de gerenciamento de serviços:

- **Monitoramento principal.** O monitoramento principal fornece monitoramento necessário e fundamental nos recursos do Azure. Esses serviços requerem configuração mínima e coletam a telemetria fundamental utilizada pelos serviços de monitoramento Premium.
- **Monitoramento profundo de infraestrutura e aplicativo.** Os serviços do Azure fornecem recursos avançados para coletar e analisar dados de monitoramento em um nível mais profundo. Esses serviços compilam monitoramento principal e aproveitam as vantagens da funcionalidade comum no Azure. Eles fornecem uma análise poderosa com os dados coletados para fornecer informações exclusivas sobre seus aplicativos e sua infraestrutura.

Saiba mais sobre o [Azure Monitor](/azure/azure-monitor/overview) para monitoramento de ativos migrados.

## <a name="security-monitoring"></a>Monitoramento de segurança

Conte com a Central de Segurança do Azure para um monitoramento de segurança unificado e notificação avançada contra ameaças nas cargas de trabalho de nuvem híbrida. A Central de Segurança oferece visibilidade e controle totais da segurança de seus aplicativos de nuvem no Azure. Detecte ameaças rapidamente e tome medidas para responder a elas e reduzir a exposição habilitando proteção adaptável contra ameaças. O painel interno fornece informações instantâneas sobre alertas de segurança e vulnerabilidades que exigem atenção. A Central de Segurança do Azure pode ajudar com muitas funções, incluindo:

- **Monitoramento centralizado de políticas.** Garanta a conformidade com requisitos de segurança da empresa ou de regulamentação gerenciando políticas de segurança de forma centralizada nas cargas de trabalho de nuvem híbrida.
- **Avaliação contínua de segurança.** Monitore a segurança de computadores, redes, armazenamento e serviços de dados e aplicativos para descobrir problemas potenciais de segurança.
- **Recomendações práticas.** Corrija vulnerabilidades de segurança antes que elas sejam exploradas por invasores. Inclua recomendações de segurança priorizadas e práticas.
- **Defesas avançadas de nuvem.** Reduza ameaças com acesso Just-In-Time a portas de gerenciamento e listas seguras para controlar aplicativos em execução em suas VMs.
- **Alertas e incidentes priorizados.** Concentre-se primeiro nas ameaças mais críticas, com incidentes e alertas de segurança priorizados.
- **Soluções de segurança integradas.** Colete, pesquise e analise dados de segurança de uma variedade de fontes, incluindo soluções de parceiros conectadas.

Saiba mais sobre a [Central de Segurança do Azure](/azure/security-center) para proteger ativos migrados.

## <a name="protect-assets-and-data"></a>Proteger dados e ativos

O Backup do Azure fornece uma maneira de proteger VMs, arquivos e dados. O Backup do Azure pode ajudar com muitas funções, incluindo:

- Fazer backup de VMs.
- Fazer backup de arquivos.
- Fazer backup de bancos de dados do SQL Server.
- Recuperar ativos protegidos.

Saiba mais sobre o [Backup do Azure](/azure/backup) para proteger ativos migrados.
