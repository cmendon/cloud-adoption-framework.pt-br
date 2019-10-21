---
title: 'Migração de mainframe: mitos e fatos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migre aplicativos de ambientes de mainframe para o Azure, uma infraestrutura comprovada, altamente disponível e escalonável para sistemas que atualmente são executados em mainframes.
author: njray
ms.author: v-nanra
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4adf229b1ffca1d1360d197ab09a04f0d9584ef8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547907"
---
# <a name="mainframe-myths-and-facts"></a>Mitos e fatos sobre mainframe

Os mainframes são destacados em destaque na história da computação e permanecem viáveis para cargas de trabalho altamente específicas. A maioria concorda que os mainframes são uma plataforma comprovada com procedimentos operacionais muito estabelecidos que os tornam ambientes robustos e confiáveis. O software é executado com base no uso, medido em milhão de instruções por segundo (MIPS) e relatórios de uso extensivos estão disponíveis para estornos.

A eficiência da confiabilidade, da disponibilidade e do processamento dos mainframes levou em proporções quase mítico. Para avaliar as cargas de trabalho de mainframe mais adequadas para o Azure, primeiro você deseja distinguir os mitos da realidade.

## <a name="myth-mainframes-never-go-down-and-have-a-minimum-of-five-9s-of-availability"></a>Mito: os mainframes nunca ficam inativos e têm um mínimo de cinco noves de disponibilidade

Hardware e sistemas operacionais de mainframe são exibidos como confiáveis e estáveis. Mas a realidade é que o tempo de inatividade deve ser agendado para manutenção e reinicializações (chamadas de carregamentos de programa iniciais ou IPLs). Quando essas tarefas são consideradas, uma solução de mainframe geralmente tem mais de dois ou três noves de disponibilidade, o que é equivalente ao dos servidores de alto nível baseados em Intel.

Os mainframes também permanecem tão vulneráveis a desastres quanto quaisquer outros servidores e exigem sistemas UPS (Power Supply) para lidar com esses tipos de falhas.

## <a name="myth-mainframes-have-limitless-scalability"></a>Mito: os mainframes têm escalabilidade ilimitada

A escalabilidade de um mainframe depende da capacidade de seu software de sistema, como o CICS (sistema de controle de informações do cliente) e a capacidade de novas instâncias de armazenamento e mecanismos de mainframe. Algumas grandes empresas que usam mainframes personalizaram seus CICS para desempenho e, de outra forma, aumentaram a capacidade dos maiores mainframes disponíveis.

## <a name="myth-intel-based-servers-are-not-as-powerful-as-mainframes"></a>Mito: os servidores baseados em Intel não são tão poderosos como mainframes

Os novos sistemas com base em processadores Intel têm tanto capacidade computacional quanto mainframes.

## <a name="myth-the-cloud-cant-accommodate-mission-critical-applications-for-large-companies-such-as-financial-institutions"></a>Mito: a nuvem não pode acomodar aplicativos de missão crítica para grandes empresas, como instituições financeiras

Embora possa haver algumas instâncias isoladas nas quais as soluções de nuvem se enquadram, isso geralmente ocorre porque os algoritmos de aplicativo não podem ser distribuídos. Esses poucos exemplos são as exceções, não a regra.

## <a name="summary"></a>Resumo

Por comparação, o Azure oferece uma plataforma alternativa capaz de fornecer recursos e funcionalidades de mainframe equivalentes e com um custo muito menor. Além disso, o TCO (custo total de propriedade) do modelo de custo controlado por uso baseado em assinatura da nuvem é muito menos caro do que os computadores mainframe.

## <a name="next-steps"></a>Próximos passos

> [!div class="nextstepaction"]
> [Faça a mudança de mainframes para o Azure](./migration-strategies.md)
