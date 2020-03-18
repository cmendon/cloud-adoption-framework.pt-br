---
title: Guia de introdução à migração do Azure
description: Use o Cloud Adoption Framework para Azure para saber como migrar de maneira eficaz os serviços de sua organização para o Azure.
author: matticusau
ms.author: mlavery
ms.date: 02/25/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 5c9c4b5477537cd71947e8ddbeff5a64eeb378c4
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311873"
---
# <a name="azure-migration-guide-before-you-start"></a>Guia de migração do Azure: Antes de começar

A [metodologia de migração do Cloud Adoption Framework](../index.md) orienta os leitores por meio de um processo iterativo de migração de uma carga de trabalho ou de uma pequena coleção de cargas de trabalho por versão. Em cada iteração, o processo de avaliar, migrar, otimizar e promover é seguido para garantir que as cargas de trabalho estejam prontas para atender às demandas de produção. Esse processo independente da nuvem pode orientar a migração para um provedor de nuvem.

Este guia demonstra uma versão simplificada desse processo ao migrar do seu ambiente local para o **Azure**.

::: zone target="docs"

> [!TIP]
> Para uma experiência interativa, exiba esse guia no portal do Azure. Vá para o [Centro de Início Rápido do Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) no portal do Azure, selecione **Migrar o ambiente para o Azure** e depois siga as instruções passo a passo.

::: zone-end

## <a name="migration-tools"></a>[Ferramentas de migração](#tab/MigrationTools)

Este guia é o caminho sugerido para sua primeira migração para o Azure, pois ele mostrará a você a metodologia e as ferramentas nativas de nuvem usadas com mais frequência durante a migração para o Azure. Essas ferramentas são apresentadas nas seguintes páginas:

> [!div class="checklist"]
>
> - **Avalie a adequação técnica de cada carga de trabalho.** Valide a prontidão técnica e a adequação para a migração.
> - **Migrar seus serviços.** Execute a migração real replicando recursos locais para o Azure.
> - **Gerenciar os custos e a cobrança.** Entenda as ferramentas necessárias para controlar os custos no Azure.
> - **Otimize e promova.** Otimize para ter equilíbrio de custo e desempenho antes de promover sua carga de trabalho para a produção.
> - **Obter assistência.** Obtenha ajuda e suporte durante a migração ou atividades pós-migração.

Assume-se que uma zona de destino já foi implantada, em alinhamento com as melhores práticas na [metodologia de preparação do Cloud Adoption Framework](../../ready/index.md).

## <a name="when-to-use-this-guide"></a>[Quando usar este guia](#tab/WhenToUseThisGuide)

Embora as ferramentas abordadas neste guia deem suporte a uma ampla variedade de cenários de migração, este guia se concentrará nos esforços de escopo limitado com _complexidade mínima_. Para determinar se este guia de migração é adequado para o seu projeto, considere se as seguintes condições se aplicam a você:

- As cargas de trabalho para a migração inicial não são críticas e não contêm dados confidenciais.
- Você está migrando um ambiente homogêneo.
- Apenas algumas unidades de negócios precisam se alinhar para concluir a migração.
- Você não está planejando automatizar toda a migração.
- Você está migrando um pequeno número de servidores.
- O mapeamento de dependência dos componentes a serem migrados é simples de definir.
- Seu setor tem os requisitos normativos mínimos relevantes para esta migração.

Se uma destas condições não for aplicável à sua situação, você deverá considerar o [guia de escopo expandido](../expanded-scope/index.md). Também recomendamos que você solicite assistência de uma de nossas equipes ou parceiros da Microsoft para executar migrações que exigem o guia de escopo expandido. Os clientes que interagem com a Microsoft ou parceiros certificados obtêm mais êxito nesses cenários. Mais informações sobre como solicitar assistência estão disponíveis neste guia.

<!-- markdownlint-enable MD033 -->

::: zone target="docs"

Para obter mais informações, consulte:

- [Guia de escopo expandido](../expanded-scope/index.md)

::: zone-end
