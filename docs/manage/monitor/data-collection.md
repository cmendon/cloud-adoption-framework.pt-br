---
title: Guia de monitoramento de nuvem – coletar os dados corretos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Escolha quando usar Azure Monitor ou System Center Operations Manager no Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 05596379872fbfa9099297a55d4b75dedc0b672a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564940"
---
# <a name="cloud-monitoring-guide-collect-the-right-data"></a>Guia de monitoramento de nuvem: coletar os dados corretos

Este artigo descreve algumas considerações para coletar dados de monitoramento em um aplicativo de nuvem.

Para observar a integridade e a disponibilidade da sua solução de nuvem, você deve configurar as ferramentas de monitoramento para coletar um nível de sinais que se baseiam em Estados de falha previsíveis. Esses sinais são os sintomas da falha, não a causa. As ferramentas de monitoramento usam métricas e, para diagnóstico avançado e análise de causa raiz, logs.

Planeje o monitoramento e a migração com cuidado. Comece incluindo o proprietário do serviço de monitoramento, o gerente de operações e outros funcionários relacionados durante a fase de planejamento e continue a envolver em todo o ciclo de desenvolvimento e de lançamento. Seu foco será desenvolver uma configuração de monitoramento com base nos seguintes critérios:

- Qual é a composição do serviço e essas dependências são monitoradas hoje? Nesse caso, há várias ferramentas envolvidas? Há uma oportunidade de consolidar, sem introduzir riscos?
- Qual é o SLA do serviço e como irei medi-lo e relatá-lo?
- Como deve ser a aparência do painel de serviço quando um incidente é gerado? Como deve ser a aparência do painel para o proprietário do serviço e para a equipe que dá suporte ao serviço?
- Que métricas o recurso produz que preciso monitorar?  
- Como o proprietário do serviço, as equipes de suporte e outros funcionários estão pesquisando os logs?

A forma como você responde a essas perguntas e os critérios de alerta, determina como você usará a plataforma de monitoramento. Se você estiver migrando de uma plataforma de monitoramento existente ou de um conjunto de ferramentas de monitoramento, use a migração como uma oportunidade para reavaliar os sinais coletados. Isso é especialmente verdadeiro agora que há vários fatores de custo a serem considerados ao migrar ou integrar com uma plataforma de monitoramento baseada em nuvem como Azure Monitor. Lembre-se de que os dados de monitoramento precisam ser acionáveis. Você precisa ter dados otimizados coletados para fornecer uma "exibição de 10.000 pés" da integridade geral do serviço. A instrumentação que é definida para identificar incidentes reais deve ser tão simples, previsível e confiável quanto possível.

## <a name="develop-a-monitoring-configuration"></a>Desenvolver uma configuração de monitoramento

O proprietário e a equipe do serviço de monitoramento normalmente seguem um conjunto comum de atividades para desenvolver uma configuração de monitoramento. Essas atividades começam nos estágios iniciais de planejamento, continuam a testar e validando em um ambiente de não produção e se estendem para a implantação na produção. As configurações de monitoramento são derivadas de modos de falha conhecidos, resultados de teste de falhas simuladas e a experiência de várias pessoas na organização (a central de serviços, operações, engenheiros e desenvolvedores). Essas configurações pressupõem que o serviço já existe, está sendo migrado para a nuvem e não foi rearquitetado.

Para obter os resultados de qualidade de nível de serviço, monitore a integridade e a disponibilidade desses serviços no início do processo de desenvolvimento. Se você monitorar o design desse serviço ou aplicativo como uma prioridade, seus resultados não serão tão bem-sucedidos.

Para gerar uma resolução mais rápida do incidente, considere as seguintes recomendações:

- Defina um painel para cada componente de serviço.
- Use as métricas para ajudar a orientar o diagnóstico adicional e identificar uma resolução ou solução alternativa do problema se uma causa raiz não puder ser descoberta.
- Use os recursos de busca detalhada do painel ou dê suporte à personalização da exibição para refiná-la.
- Se você precisar de logs detalhados, as métricas devem ter ajudado a direcionar os critérios de pesquisa. Se as métricas não ajudarem, melhore-as para o próximo incidente.

Adotar esse conjunto de princípios de orientação pode ajudar a fornecer percepções quase em tempo real, bem como um melhor gerenciamento do seu serviço.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Estratégia de alerta](./alerting.md)
