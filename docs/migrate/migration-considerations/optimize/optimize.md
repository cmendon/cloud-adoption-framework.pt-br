---
title: Benchmark e redimensionamento de ativos de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Benchmark e redimensionamento de ativos de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 53ff6f0d32b80ef9c89d4ebd0234dd3442412907
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548432"
---
# <a name="benchmark-and-resize-cloud-assets"></a>Benchmark e redimensionamento de ativos de nuvem

O monitoramento do uso e do gasto é extremamente importante para as infraestruturas de nuvem. As organizações pagam pelos recursos que consomem ao longo do tempo. Quando o uso excede os limites do contrato, as excedentes de custos inesperados podem se acumular rapidamente. Os relatórios de gerenciamento de custos monitoram gastos para analisar e acompanhar o uso, os custos e as tendências da nuvem. Usando relatórios de horas extras, detecte anomalias que diferem das tendências normais. As ineficiências na implantação na nuvem são visíveis em relatórios de otimização. Anote as ineficiências em relatórios de análise de custo.

Nos modelos locais de ti tradicionais, a requisição dos sistemas de ti é dispendiosa e consome tempo. Os processos geralmente exigem ciclos de análise de gastos de capital longos e podem até mesmo exigir um processo de planejamento anual. Como tal, é uma prática comum comprar mais do que o necessário. É igualmente comum que os administradores de ti, em seguida, provisionem ativos em preparação para demandas futuras antecipadas.

Na nuvem, os modelos de contabilidade e provisionamento eliminam os atrasos de tempo que levam à supercompra. Quando um ativo precisa de recursos adicionais, ele pode ser expandido ou reduzido quase instantaneamente. Isso significa que os ativos podem ser reduzidos de tamanho com segurança para minimizar os recursos e os custos consumidos. Durante o benchmark e a otimização, a equipe de adoção de nuvem procura encontrar o equilíbrio entre desempenho e custos, Provisionando ativos para não serem maiores e não menores do que o necessário para atender às demandas de produção.

<!-- markdownlint-disable MD026 -->

## <a name="should-assets-be-optimized-during-or-after-the-migration"></a>Os ativos devem ser otimizados durante ou após a migração?

Quando um ativo deve ser otimizado &mdash;during ou após a migração? A resposta simples é a *ambas*. No entanto, isso não é totalmente preciso. Para explicar, dê uma olhada em dois cenários básicos para otimizar o dimensionamento de recursos:

- **Redimensionamento planejado.** Geralmente, um ativo é claramente superdimensionado e subutilizado e deve ser redimensionado durante a implantação. Determinar se um ativo foi redimensionado com êxito nesse caso requer o teste de aceitação do usuário após a migração. Se um usuário avançado não tiver perdas de desempenho ou de funcionalidade durante o teste, você poderá concluir que o ativo foi dimensionado com êxito.
- **Otimização.** Nos casos em que a necessidade de otimização não é clara, as equipes de ti devem usar uma abordagem controlada por dados para o gerenciamento de tamanho de recursos. Usando benchmarks do desempenho do ativo, uma equipe de ti pode tomar decisões instruídas sobre o tamanho, os serviços, a escala e a arquitetura mais apropriados de uma solução. Em seguida, eles podem redimensionar e testar o desempenho teorias após a migração.

Durante a migração, use palpites instruídos e experimente o dimensionamento. No entanto, a verdadeira otimização dos recursos exige dados com base no desempenho real em um ambiente de nuvem. Para que a verdadeira otimização ocorra, a equipe de ti deve primeiro implementar abordagens para monitorar o desempenho e a utilização de recursos.

## <a name="benchmark-and-optimize-with-azure-cost-management"></a>Benchmark e otimizar com o gerenciamento de custos do Azure

O [Gerenciamento de custos do Azure](https://docs.microsoft.com/azure/cost-management/overview) licenciado pela Cloudyn, uma subsidiária da Microsoft, gerencia os gastos com a nuvem com transparência e precisão. Esse serviço monitora, realiza a localização de parâmetros de comparação e otimiza os custos de nuvem.

Os dados históricos podem ajudar a gerenciar custos analisando o uso e os custos ao longo do tempo para identificar tendências, que são então usadas para prever gastos futuros. O gerenciamento de custos também inclui relatórios de custo projetados úteis. A alocação de custos gerencia os custos analisando os custos com base nas políticas de marcação. Use a alocação de custos para reversão/estorno para mostrar a utilização de recursos e os custos associados para influenciar os comportamentos de consumo ou cobrar os clientes de locatários. O controle de acesso ajuda a gerenciar os custos, garantindo que os usuários e as equipes acessem apenas os dados de gerenciamento de custos de que precisam. O alerta ajuda a gerenciar os custos por meio de notificação automática quando ocorrem gastos incomuns ou em caso de perda. Os alertas também podem notificar outros participantes automaticamente para gastar anomalias e engastando riscos. Vários relatórios dão suporte a alertas com base no orçamento e nos limites de custo.

## <a name="improve-efficiency"></a>Melhorar a eficiência

Determine o uso ideal da VM, identifique as VMs ociosas ou remova as VMs ociosas e os discos desconectados com o gerenciamento de custos. Usando informações em relatórios de otimização de dimensionamento e ineficiência, crie um plano para diminuir ou remova as VMs ociosas.

## <a name="next-steps"></a>Próximos passos

Depois que uma carga de trabalho é testada e otimizada, é hora de [preparar a carga de trabalho para promoção](./ready.md).

> [!div class="nextstepaction"]
> [Obtendo uma carga de trabalho migrada pronta para promoção de produção](./ready.md)
