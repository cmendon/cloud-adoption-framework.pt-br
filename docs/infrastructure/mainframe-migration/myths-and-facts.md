---
title: 'Migração de mainframe: Mitos e fatos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migre aplicativos de ambientes de mainframe no Azure, uma infraestrutura escalonável, altamente disponível e comprovada para sistemas que atualmente executam em mainframes.
author: njray
ms.author: v-nanra
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 42981c9d3e8a87579033fbd0bd01c912d79c937f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024392"
---
# <a name="mainframe-myths-and-facts"></a>Mitos e fatos a respeito de mainframe

Os mainframes aparecem proeminentemente na história da computação e permanecem viáveis para cargas de trabalho altamente específicas. A maioria das pessoas concorda que mainframes são uma plataforma comprovada com procedimentos operacionais de longo prazo que os tornam ambientes confiáveis e robustos. O software é executado com base no uso, medido em milhão de instruções por segundo (MIPS) e relatórios de uso extensivos estão disponíveis para estornos.

A confiabilidade, disponibilidade e capacidade de processamento de mainframes assumiram proporções quase míticas. Para avaliar as cargas de trabalho de mainframe que são mais adequadas para o Azure, primeiro você deseja distinguir os mitos da realidade.

## <a name="myth-mainframes-never-go-down-and-have-a-minimum-of-five-9s-of-availability"></a>Mito: Mainframes nunca ficam inativos e têm um mínimo de cinco 9s de disponibilidade

Hardware de mainframe e sistemas operacionais são vistos como confiáveis e estáveis. Mas, a realidade é que esse tempo de inatividade deve ser agendado para manutenção e reinicializações (conhecidas como cargas iniciais de programa ou IPLS). Quando essas tarefas são consideradas, uma solução de mainframe geralmente tem o mais próximo de dois ou três 9s de disponibilidade, que é equivalente aos servidor avançados com base em Intel.

Os mainframes também permanecem vulneráveis a desastres, assim como em outros servidores e exigem sistemas de alimentação ininterrupta (no-break) para lidar com esses tipos de falhas.

## <a name="myth-mainframes-have-limitless-scalability"></a>Mito: Mainframes têm escalabilidade ilimitada

A escalabilidade de um mainframe depende da capacidade do seu software de sistema, como o sistema de controle de informações do cliente (CICS) e a capacidade de novas instâncias dos mecanismos de mainframe e armazenamento. Algumas empresas de grandes porte que usam mainframes personalizaram sua CICS e de outra forma superaram a capacidade dos maiores mainframes disponíveis.

## <a name="myth-intel-based-servers-are-not-as-powerful-as-mainframes"></a>Mito: Servidores baseados na Intel não são tão poderosos quanto mainframes

Os novos sistemas baseados na Intel de núcleo denso têm tanta capacidade de computação quanto os mainframes.

## <a name="myth-the-cloud-cant-accommodate-mission-critical-applications-for-large-companies-such-as-financial-institutions"></a>Mito: A nuvem não pode acomodar aplicativos de missão crítica para grandes empresas, como instituições financeiras

Embora possa haver algumas instâncias isoladas nas quais as soluções de nuvem se enquadram, isso geralmente ocorre porque os algoritmos de aplicativo não podem ser distribuídos. Alguns desses exemplos são as exceções, não a regra.

## <a name="summary"></a>Resumo

Por comparação, o Azure oferece uma plataforma alternativa capaz de fornecer recursos e funcionalidades de mainframe equivalentes e com um custo muito menor. Além disso, o custo total de propriedade (TCO) do modelo de custo controlado por uso com base em assinatura da nuvem, é muito menos dispendioso que computadores mainframe.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Faça a mudança de mainframes para o Azure](./migration-strategies.md)
