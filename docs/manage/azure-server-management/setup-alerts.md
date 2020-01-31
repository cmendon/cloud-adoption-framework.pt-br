---
title: Configurar alertas básicos
description: Saiba como usar os serviços de gerenciamento de servidor do Azure para configurar alertas e notificações que ajudam a manter suas equipes de ti cientes de quaisquer problemas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: e24932b074f69f83aff583d560399d884c6c5b0e
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807947"
---
# <a name="set-up-basic-alerts"></a>Configurar alertas básicos

Uma parte fundamental do gerenciamento de recursos é notificado quando ocorrem problemas. Os alertas o notificam proativamente sobre condições críticas, com base em gatilhos de métricas, logs ou problemas de integridade do serviço. Como parte da integração dos serviços de gerenciamento do servidor do Azure, você pode configurar alertas e notificações que ajudam a manter suas equipes de ti cientes de quaisquer problemas.

## <a name="azure-monitor-alerts"></a>Alertas de Azure Monitor

O Azure Monitor oferece recursos de [alerta](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) para notificá-lo, por email ou mensagens, quando as coisas dão errado. Esses recursos são baseados em uma plataforma comum de monitoramento de dados que inclui logs e métricas gerados por seus servidores e outros recursos. Usando um conjunto comum de ferramentas no Azure Monitor, você pode analisar os dados que são combinados de vários recursos e usá-los para disparar alertas. Esses gatilhos podem incluir:

- Valores de métrica.
- Consultas de pesquisa de log.
- Eventos do log de atividades.
- A integridade da plataforma subjacente do Azure.
- Testes de disponibilidade do site.

Consulte a [lista de Azure monitor fontes de dados](https://docs.microsoft.com/azure/azure-monitor/platform/data-sources) para obter uma descrição mais detalhada das fontes de dados de monitoramento que esse serviço coleta.

Para obter detalhes sobre como criar e gerenciar manualmente alertas usando o portal do Azure, consulte a [documentação do Azure monitor](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric).

## <a name="automated-deployment-of-recommended-alerts"></a>Implantação automatizada de alertas recomendados

Neste guia, recomendamos que você crie um conjunto de 15 alertas para o monitoramento de infraestrutura básico. Localize os scripts de implantação no [repositório GitHub do Azure Alert Toolkit](https://github.com/Microsoft/manageability-toolkits).

Este pacote cria alertas para:

- Pouco espaço em disco
- Baixa memória disponível
- Alto uso da CPU
- Desligamentos inesperados
- Sistemas de arquivos corrompidos
- Falhas comuns de hardware

O pacote usa o hardware de servidor HP como um exemplo. Altere as configurações no arquivo de configuração associado para refletir o hardware OEM. Você também pode adicionar mais contadores de desempenho ao arquivo de configuração. Para implantar o pacote, execute o arquivo New-CoreAlerts. ps1.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre as operações e os mecanismos de segurança que dão suporte a suas operações em andamento.

> [!div class="nextstepaction"]
> [Gerenciamento e segurança contínuos](./ongoing-management-overview.md)
