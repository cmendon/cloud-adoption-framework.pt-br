---
title: Configurar alertas básicos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurar alertas básicos
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5b11a97e78d5fcd1b2a2cc866f5a7062bc6a2977
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027476"
---
# <a name="set-up-basic-alerts"></a>Configurar alertas básicos

Uma parte fundamental do gerenciamento de recursos é notificado quando ocorrem problemas. Alertas notificam você proativamente sobre condições críticas. Eles podem se basear em gatilhos de métricas, logs ou problemas de integridade do serviço. Como parte da integração dos serviços de gerenciamento do servidor do Azure, você pode configurar alertas e notificações que podem ajudar a manter suas equipes de ti cientes de quaisquer problemas.

## <a name="azure-monitor-alerts"></a>Alertas de Azure Monitor

O Azure Monitor oferece recursos de [alerta](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) para notificá-lo por email ou mensagens quando as coisas dão errado. Esses recursos são baseados em uma plataforma de monitoramento de dados comum que inclui logs e métricas gerados por seus servidores e outros recursos. Essa plataforma permite que você analise os dados combinados de vários recursos usando um conjunto comum de ferramentas no Azure Monitor, que pode ser usado para disparar alertas. Esses gatilhos podem incluir:

- Valores de métrica.
- Consultas de pesquisa de log.
- Eventos do log de atividades.
- Integridade da plataforma subjacente do Azure.
- Testes de disponibilidade do site.

Consulte a [lista de Azure monitor fontes de dados](https://docs.microsoft.com/azure/azure-monitor/platform/data-sources) para obter uma descrição mais detalhada das fontes de dados de monitoramento coletados por esse serviço.

Para obter detalhes sobre como criar e gerenciar manualmente alertas usando o portal, consulte a [documentação do Azure monitor](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric).

## <a name="automated-deployment-of-recommended-alerts"></a>Implantação automatizada de alertas recomendados

Neste guia, recomendamos que você habilite um conjunto de 15 alertas para o monitoramento de infraestrutura básica. Você pode encontrar os scripts de implantação no [repositório GitHub do Azure Alert Toolkit](https://github.com/Microsoft/manageability-toolkits).

Este pacote cria alertas para espaço em disco insuficiente, memória baixa disponível, alta utilização da CPU, desligamentos inesperados, sistemas de arquivos corrompidos e falhas comuns de hardware. O pacote usa o hardware de servidor HP como um exemplo. Você deve alterar as configurações no arquivo de configuração associado para refletir o hardware OEM. Você também pode adicionar mais contadores de desempenho ao arquivo de configuração. Para implantar o pacote, execute o arquivo New-CoreAlerts. ps1.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre as operações e os mecanismos de segurança que dão suporte a suas operações em andamento.

> [!div class="nextstepaction"]
> [Gerenciamento e segurança contínuos](./ongoing-management-overview.md)
