---
title: Melhores práticas de migração do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução às Melhores Práticas de Migração do Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 1519adff06d600b9829c9b7ff3ca82a0aa5a0160
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753384"
---
# <a name="azure-migration-best-practices"></a>Melhores práticas de migração do Azure

O Azure fornece várias ferramentas no Azure para ajudar a executar um esforço de migração. Esta seção da Cloud Adoption Framework é projetada para ajudar os leitores a implementar essas ferramentas em alinhamento com as melhores práticas para a migração. Essas melhores práticas estão alinhadas a um dos processos dentro do modelo de migração da Cloud Adoption Framework ilustrados abaixo.

Expanda quaisquer processos no sumário à esquerda para ver as melhores práticas que costumam ser necessárias durante esse processo.

![Modelo de migração da Cloud Adoption Framework](../../_images/operational-transformation-migrate.png)

> [!NOTE]
> A avaliação de ativos e o planejamento de acervo digital representam dois níveis diferentes de avaliação e planejamento de migração:
>
> - **Planejamento de acervo digital:** você planeja ou racionaliza o acervo digital durante o planejamento para estabelecer uma lista de pendências de migração geral. No entanto, esse plano se baseia em algumas suposições e detalhes que precisam ser validados antes da migração de uma carga de trabalho.
> - **Avaliação de ativo:** você avalia os ativos individuais de uma carga de trabalho antes da migração dela para analisar a compatibilidade com a nuvem e entender as restrições de arquitetura e de dimensionamento. Esse processo valida suposições iniciais e fornece os detalhes necessários para fazer a migração de um ativo individual.
