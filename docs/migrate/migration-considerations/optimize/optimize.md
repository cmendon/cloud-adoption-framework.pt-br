---
title: Parâmetros de comparação e redimensionamento de ativos de nuvem
description: Parâmetros de comparação e redimensionamento de ativos de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7198bdc1332a9d55bca68a04fe1384727dc7284a
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801827"
---
# <a name="benchmark-and-resize-cloud-assets"></a>Parâmetros de comparação e redimensionamento de ativos de nuvem

O monitoramento do uso e dos gastos é extremamente importante para as infraestruturas de nuvem. As organizações pagam pelos recursos que consomem ao longo do tempo. Quando o uso excede os limites do contrato, excedentes de custos inesperados podem ocorrer rapidamente. Os relatórios do Gerenciamento de Custos monitoraram os gastos para analisar e acompanhar o uso da nuvem, seus custos e tendências. Usando os relatórios ao longo do tempo, é possível detectar anomalias que diferem das tendências normais. As ineficiências da implantação de nuvem ficam visíveis nos relatórios de otimização. Observe as ineficiências em relatórios de análise de custos.

Nos modelos locais tradicionais de TI, a requisição dos sistemas de TI é dispendiosa e consome tempo. Os processos geralmente exigem longos ciclos de análise de gastos de capital e podem até mesmo necessitar de um processo de planejamento anual. Dessa forma, é comum comprar mais do que o necessário. É igualmente comum que os administradores de TI então provisionem ativos em preparação para as demandas futuras antecipadas.

Na nuvem, os modelos de provisionamento e contabilidade eliminam os atrasos de tempo que levam à compra excessiva. Quando um ativo precisa de recursos adicionais, é possível aumentar ou diminuir seu pedido quase instantaneamente. Ou seja, é possível reduzir o tamanho de ativos com segurança para minimizar o consumo de recursos e custos. Durante a comparação e a otimização, a equipe de adoção da nuvem procura encontrar o equilíbrio entre desempenho e custos, provisionando ativos para que não sejam maiores nem menores do que o necessário para atender às demandas de produção.

<!-- markdownlint-disable MD026 -->

## <a name="should-assets-be-optimized-during-or-after-the-migration"></a>É necessário otimizar os ativos durante ou após a migração?

Quando é necessário otimizar um ativo&mdash;durante ou após a migração? A resposta simples é *nos dois momentos*. No entanto, isso não é totalmente exato. Para explicar, dê uma olhada em dois cenários básicos para otimizar o dimensionamento de recursos:

- **Redimensionamento planejado.** Geralmente, quando um ativo é claramente superdimensionado e subutilizado, deve ser redimensionado durante a implantação. Determinar se um ativo foi redimensionado com êxito nesse caso requer o teste de aceitação do usuário após a migração. Se um usuário avançado não tiver perdas de desempenho ou de funcionalidade durante o teste, você poderá concluir que o ativo foi dimensionado com êxito.
- **Otimização.** Nos casos em que a necessidade de otimização não fica clara, as equipes de TI devem usar uma abordagem controlada por dados no gerenciamento de tamanho de recursos. Usando benchmarks do desempenho do ativo, uma equipe de ti pode tomar decisões instruídas sobre o tamanho, os serviços, a escala e a arquitetura mais apropriados de uma solução. Em seguida, ela pode redimensionar e testar o teorias de desempenho após a migração.

Durante a migração, use suposições realistas ao experimentar o dimensionamento. No entanto, a verdadeira otimização dos recursos exige dados baseados no desempenho real de um ambiente de nuvem. Para que a verdadeira otimização ocorra, primeiro a equipe de TI deve implementar abordagens para monitorar o desempenho e a utilização de recursos.

## <a name="benchmark-and-optimize-with-azure-cost-management"></a>Avaliações e otimizações com o Gerenciamento de Custos do Azure

O [Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management/overview) licenciado pela Cloudyn, uma subsidiária da Microsoft, gerencia os gastos da nuvem com transparência e precisão. Esse serviço monitora, avalia, aloca e otimiza os custos da nuvem.

Os dados históricos podem ajudar a gerenciar custos analisando o uso e os custos ao longo do tempo para identificar tendências, que então são usadas para prever gastos futuros. O Gerenciamento de Custo também inclui relatórios de custos previstos úteis. A alocação de custos gerencia os custos analisando-os de acordo com a política de marcação. Use a alocação de custos para showback/estornar ao mostrar a utilização de recursos e os custos associados para influenciar os comportamentos de consumo ou cobrar os clientes de locatários. O controle de acesso ajuda a gerenciar os custos garantindo que os usuários e as equipes acessem somente os dados necessários do Gerenciamento de Custos. Os alertas ajudam a gerenciar os custos pela notificação automática quando ocorrem gastos incomuns ou excessivos. Os alertas podem notificar outros stakeholders automaticamente sobre anomalias de gastos e riscos de excesso de gastos. Vários relatórios dão suporte a alertas com base no orçamento e nos limites de custo.

## <a name="improve-efficiency"></a>Melhorar a eficiência

Determine o uso ideal das VMs, identifique ou remova as VMs ociosas e os discos desanexados com o Gerenciamento de Custos. Usando as informações contidas nos relatórios de ineficiência e otimização de dimensionamento, crie um plano para reduzir ou remover as VMs ociosas.

## <a name="next-steps"></a>Próximos passos

Depois que uma carga de trabalho for testada e otimizada, é a hora de [preparar a carga de trabalho para promoção](./ready.md).

> [!div class="nextstepaction"]
> [Preparando uma carga de trabalho migrada para a promoção da produção](./ready.md)
