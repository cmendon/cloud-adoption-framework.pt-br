---
title: 'Guia de gerenciamento do Azure: Antes de começar'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como gerenciar suas operações do Azure com diretrizes passo a passo.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 58a01e02abad2de68fac9a94d2a2aa3ad22d32a1
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769156"
---
::: zone target="docs"

# <a name="azure-management-guide-before-you-start"></a>Guia de gerenciamento do Azure: Antes de começar

> [!NOTE]
> Este guia é um ponto de partida para as diretrizes de inovação na Cloud Adoption Framework. Ele também está disponível no Centro de Início Rápido do Azure. Consulte a dica mais adiante neste artigo para obter um link para o Centro de Início Rápido do Azure.

::: zone-end

::: zone target="chromeless"

# <a name="before-you-start"></a>Antes de começar

::: zone-end

O Guia de Gerenciamento do Azure foi projetado para auxiliar clientes do Azure ativos com a criação de uma linha de base de gerenciamento para estabelecer a consistência dos recursos no Azure. Este guia descreve as ferramentas básicas necessárias para qualquer ambiente de produção do Azure, especialmente ambientes que hospedam dados confidenciais. Para obter mais informações, melhores práticas e considerações relacionadas à preparação do ambiente de nuvem, confira a [seção sobre preparação do Cloud Adoption Framework](../index.md).

## <a name="scope-of-this-guide"></a>Escopo deste guia

Este guia ensinará como estabelecer ferramentas para uma linha de base de gerenciamento. Ele também descreve maneiras de estender a linha de base ou aumentar a resiliência para além da linha de base.

> [!div class="checklist"]
>
> - **Inventário e visibilidade:** Crie um inventário de ativos em várias nuvens. Desenvolva a visibilidade do estado de execução de cada ativo.
> - **Conformidade operacional:** Estabeleça controles e processos para garantir que cada estado seja configurado corretamente e execute em um ambiente bem controlado.
> - **Proteger e recuperar:** Verifique se todos os ativos gerenciados estão protegidos e podem ser recuperados usando as ferramentas de gerenciamento de linha de base.
> - **Opções de linha de base aprimoradas:** Avalie adições comuns à linha de base que podem atender às necessidades de negócios.
> - **Operações de plataforma:** Estenda a linha de base de gerenciamento com um catálogo de serviços bem definido e plataformas gerenciadas centralmente.
> - **Operações de carga de trabalho:** Estenda a linha de base de gerenciamento para incluir um foco em cargas de trabalho críticas.

## <a name="management-baseline"></a>Linha de base de gerenciamento

Uma linha de base de gerenciamento é o conjunto mínimo de ferramentas e processos que devem ser aplicados a todos os ativos no ambiente. Várias opções adicionais podem ser incluídas na linha de base de gerenciamento. Os próximos artigos acelerarão os recursos de gerenciamento de nuvem, concentrando-se nas opções mínimas necessárias, em vez de em todas as opções disponíveis.

::: zone target="docs"

> [!TIP]
> Para uma experiência interativa, exiba esse guia no portal do Azure. Acesse o [Centro de Início Rápido do Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) no portal do Azure e selecione **Guia de Gerenciamento do Azure**. Em seguida, siga as instruções passo a passo.

Próximas etapas: [Inventário e visibilidade](./inventory.md)

::: zone-end

::: zone target="chromeless"

Este guia apresenta as etapas interativas que permitem que você experimente os recursos conforme eles são introduzidos. Para voltar para o ponto em que você parou, use a trilha de navegação.

::: zone-end
