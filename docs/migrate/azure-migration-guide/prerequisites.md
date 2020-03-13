---
title: Pré-requisitos da migração para o Azure
description: Use o Cloud Adoption Framework para o Azure para entender como se preparar para a migração do Azure e de quais pré-requisitos você precisa para ter um projeto de migração bem-sucedido.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 777b68bcd7faa613681f2d9ebbdf6cffe4accc3f
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79094797"
---
::: zone target="chromeless"

# <a name="prerequisites"></a>Pré-requisitos

::: zone-end

::: zone target="docs"

# <a name="prerequisites-for-migrating-to-azure"></a>Pré-requisitos da migração para o Azure

::: zone-end

Os recursos nesta seção ajudarão a preparar seu ambiente atual para a migração para o Azure.

# <a name="overview"></a>[Visão geral](#tab/Overview)

Os motivos para migrar para o Azure incluem a eliminação de riscos associados ao hardware herdado, a redução de gastos de capital, a liberação de espaço do datacenter e o rápido retorno sobre o investimento (ROI).

- **Elimine o hardware herdado.** É provável que você tenha aplicativos hospedados em uma infraestrutura que está se aproximando do fim da vida útil ou do suporte, seja no local ou em um provedor de hospedagem. A migração para a nuvem oferece uma solução interessante para o desafio já que a capacidade de migrar "no estado em que se encontra" permite que a equipe resolva rapidamente o atual desafio do ciclo de vida da infraestrutura e volte sua atenção para o planejamento de longo prazo do ciclo de vida e otimização de aplicativos na nuvem.
- **Trate do fim do suporte do software.** É provável que você tenha aplicativos que dependem de outro software ou sistemas operacionais que estão se aproximando do fim do suporte. A mudança para o Azure pode fornecer opções de suporte estendido para essas dependências ou outras opções de migração que minimizam os requisitos de refatoração para dar suporte aos seus aplicativos daqui para frente. Por exemplo, confira [opções de suporte estendido para o Windows Server 2008 e SQL Server 2008](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support).
- **Reduza gastos de capital.** Hospedar sua própria infraestrutura de servidor exige investimentos consideráveis em hardware, software, eletricidade e pessoal. A migração para uma solução na nuvem pode fornecer reduções significativas nos gastos de capital. Para obter as melhores reduções de gastos de capital, uma reformulação da solução poderá ser necessária. No entanto, uma migração "como está" é uma ótima primeira etapa.
- **Libere espaço no datacenter.** Você pode escolher o Azure para expandir a capacidade do datacenter. Uma maneira de fazer isso é usando a nuvem como uma extensão de seus recursos locais.
- **Entenda rapidamente o retorno sobre o investimento.** Realizar o retorno sobre o investimento (ROI) é muito mais fácil com as soluções na nuvem já que o modelo de pagamento em nuvem oferece um excelente insight da utilização e promove uma cultura para entender o ROI.

Cada um dos cenários acima pode ser um ponto de entrada para estender sua pegada na nuvem usando outra metodologia (hospedar novamente, refatorar, rearquitetar, recompilar ou substituir).

## <a name="migration-characteristics"></a>Características da migração

O guia pressupõe que, antes dessa migração, seu acervo digital consistia principalmente da infraestrutura hospedada no local e podia incluir aplicativos hospedados comercialmente críticos. Depois de uma migração bem-sucedida, seu acervo de dados pode ser muito semelhante ao ocorrido com o local, porém tem a infraestrutura hospedada em recursos de nuvem. Como alternativa, o acervo de dados ideal é uma variação de seu acervo de dados atual, pois possui aspectos de sua infraestrutura local com componentes que foram refatorados para otimizar e aproveitar a plataforma de nuvem.

O foco dessa jornada de migração é alcançar a:

- Correção do fim de vida do hardware herdado.
- Redução dos gastos de capital.
- Retorno sobre o investimento.

> [!NOTE]
> Um benefício adicional dessa jornada de migração é o modelo de suporte de software adicional para o Windows 2008, Windows 2008 R2, SQL Server 2008 e SQL Server 2008 R2. Para obter mais informações, consulte:
>
> - [Windows Server 2008 e Windows Server 2008 R2](https://www.microsoft.com/cloud-platform/windows-server-2008).
> - [SQL Server 2008 e SQL Server 2008 R2](https://www.microsoft.com/sql-server/sql-server-2008).

# <a name="understand-migration-approaches"></a>[Entender as abordagens de migração](#tab/Approach)

A estratégia e as ferramentas que você usa durante a migração de um aplicativo para o Azure dependem muito de suas motivações empresariais, requisitos tecnológicos e linhas do tempo. Além disso, é necessário profundo conhecimento das cargas de trabalho e dos ativos reais (infraestrutura, aplicativos e dados) que estão sendo migrados.

Antes de determinar sua estratégia de migração na nuvem, analise os aplicativos candidatos para identificar sua compatibilidade com as tecnologias de hospedagem na nuvem. Use o [guia de decisão de ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md) do Cloud Adoption Framework para ajudar você a iniciar este processo.

Geralmente, a abordagem mais direta para mover as cargas de trabalho para a nuvem é uma migração focada em IaaS, em que os servidores (juntamente com seus aplicativos e dados associados) são novamente hospedados na nuvem usando máquinas virtuais (VMs). No entanto, considere que configurar, proteger e manter corretamente as VMs requer muito mais tempo e conhecimento em TI em comparação com o uso dos serviços PaaS no Azure. Se você estiver considerando as Máquinas virtuais do Azure, certifique-se de levar em conta o esforço de manutenção contínuo necessário para corrigir, atualizar e gerenciar seu ambiente de VM.

Ao avaliar cargas de trabalho para migração, identifique aplicativos que não precisariam de modificações substanciais para serem executados com tecnologias PaaS, como o Serviço de Aplicativo do Azure, ou orquestradores, como o Serviço Kubernetes do Azure. Esses aplicativos devem ser os primeiros candidatos para a modernização e otimização da nuvem.

## <a name="learn-more"></a>Saiba mais

- [Guia de decisão de ferramentas de migração do Cloud Adoption Framework](../../decision-guides/migrate-decision-guide/index.md)
- [Os cinco Rs de racionalização](../../digital-estate/5-rs-of-rationalization.md)

# <a name="planning-checklist"></a>[Lista de verificação de planejamento](#tab/Checklist)

Antes de iniciar uma migração, será preciso concluir alguns pré-requisitos. Os detalhes exatos dessas atividades variam dependendo do ambiente que está sendo migrado. Em geral, a seguinte lista de verificação é aplicada:

> [!div class="checklist"]
>
> - **Identifique os stakeholders:** Identifique as principais pessoas que têm uma função a desempenhar ou uma participação no resultado da migração.
> - **Identifique as principais etapas:** Para planejar efetivamente as linha de tempo da migração, identifique os principais marcos que deverão ser atingidos.
> - **Identifique a estratégia de migração:** Determine qual dos cinco Rs de racionalização será usado.
> - **Avalie sua adequação técnica:** Valide a preparação técnica e a adequação para a migração e determine o nível de assistência que você pode exigir de parceiros externos ou do suporte do Azure.
> - **Planejamento da migração:** Realize a avaliação detalhada e o planejamento necessários para preparar seus ativos (infraestrutura, aplicativos e dados) além da infraestrutura do Azure para a migração.
> - **Teste sua migração:** Valide seu plano de migração executando a migração de teste de escopo limitado.
> - **Migre seus serviços:** Execute a migração real.
> - **Após a migração:** Entenda as exigências após migrar seu ambiente para o Azure.

Supondo que você escolha uma abordagem de nova hospedagem para a migração, as seguintes atividades também serão relevantes:

> [!div class="checklist"]
>
> - **Alinhamento de governança:** Chegou-se a um consenso sobre o alinhamento da governança com a fundação da migração?
> - **Rede:** Uma estratégia de rede deve ser escolhida e alinhada aos requisitos de segurança de TI.
> - **Identidade:** Uma estratégia de identidade híbrida deve ser alinhada para se ajustar ao gerenciamento de identidades e ao plano de adoção da nuvem.

::: zone target="docs"

<!-- markdownlint-disable MD024 -->

## <a name="learn-more"></a>Saiba mais

- [O cinco Rs de racionalização](../../digital-estate/5-rs-of-rationalization.md)
- [Guia de decisão de ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md)
- [Lista de verificação do planejamento da Cloud Adoption Framework](../migration-considerations/prerequisites/planning-checklist.md)

::: zone-end
