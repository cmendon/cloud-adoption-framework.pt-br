---
title: Guia de monitoramento de nuvem
description: Saiba mais sobre Azure Monitor, o System Center Operations Manager e a estratégia recomendada para monitorar cada um dos modelos de implantação em nuvem.
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 4303a51a1a6df47e07e22f3de87639230f4a4c71
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79091443"
---
# <a name="cloud-monitoring-guide-introduction"></a>Guia de monitoramento de nuvem: Introdução

Fundamentalmente, a nuvem altera como as empresas adquirem e usam recursos de tecnologia. No passado, as empresas assumiam propriedade e responsabilidade por todos os níveis de tecnologia, da infraestrutura ao software. Agora, a nuvem oferece o potencial para que as empresas provisionem e consumam recursos conforme necessário.

Embora a nuvem ofereça flexibilidade praticamente ilimitada em termos de opções de design, as empresas buscam uma metodologia consistente e comprovada para a adoção de tecnologias de nuvem. Cada empresa tem metas e cronogramas diferentes para a adoção da nuvem, portanto, é praticamente impossível que haja uma única abordagem para todos os casos de adoção.

![Diagrama de estratégias de adoção da nuvem](./media/monitoring-management-guidance-cloud-and-on-premises/introduction-cloud-adoption.png)

Essa transformação digital também gera uma oportunidade de modernizar a infraestrutura, as cargas de trabalho e os aplicativos. De acordo com a estratégia e os objetivos de negócio, a adoção de um modelo de nuvem híbrida provavelmente fará parte do percurso de migração completa das operações locais para a nuvem. Durante essa jornada, as equipes de TI têm o desafio de adotar e realizar valor rapidamente com a nuvem. Essas equipes também precisam entender como monitorar a migração do aplicativo ou serviço para o Azure de maneira eficiente, bem como continuar a fornecer operações de TI/DevOps eficazes.

Os stakeholders querem usar monitoramento e ferramentas de gerenciamento de SaaS (software como serviço) baseados em nuvem. Eles precisam entender o que os serviços e as soluções oferecem para conquistar a visibilidade de ponta a ponta, reduzir os custos e concentrar-se menos na infraestrutura e na manutenção das ferramentas de operações de TI tradicionais baseadas em software.

No entanto, muitas vezes o departamento de TI prefere usar as ferramentas nas quais já foi feito um investimento significativo. Essa abordagem apoia processos de operações de serviço para monitorar ambos os modelos de nuvem, com a meta final de migrar para uma oferta baseada em SaaS. O departamento de TI prefere essa abordagem não apenas porque o planejamento, a obtenção de recursos e o financiamento para essa mudança são processos demorados. Isso também se deve à confusão em relação a quais produtos ou serviços do Azure são adequados ou aplicáveis para concluir a transição.

A meta deste guia é oferecer uma referência detalhada para ajudar os gerentes de TI, os tomadores de decisão de negócios, os arquitetos de aplicativos e os desenvolvedores de aplicativos da empresa a entender:

* As plataformas de monitoramento do Azure com uma visão geral e uma comparação das suas funcionalidades.
* A solução mais adequada para o monitoramento de cargas de trabalho híbridas, privadas e nativas do Azure.
* A abordagem de monitoramento de ponta a ponta recomendada para a infraestrutura e os aplicativos. Isso inclui soluções implantáveis para essas cargas de trabalho comuns que estão sendo migradas para o Azure.

Este guia não é um artigo de instruções para usar ou configurar soluções e serviços individuais do Azure, mas citará as fontes relacionadas a esses assuntos quando for aplicável ou quando elas estiverem disponíveis. Depois de ler este guia, você entenderá como operar uma carga de trabalho com sucesso seguindo as melhores práticas e padrões.

Se você não estiver familiarizado com o Azure Monitor e o System Center Operations Manager e quiser entender melhor o que os torna únicos e como eles se comparam entre si, leia a [Visão geral de nossas plataformas de monitoramento](./platform-overview.md).

## <a name="audience"></a>Público

O público-alvo deste guia são os administradores corporativos, as equipes de operações de TI, de segurança de TI e de conformidade, os arquitetos de aplicativos, os proprietários de desenvolvimento de carga de trabalho e os proprietários de operações de carga de trabalho.

## <a name="how-this-guide-is-structured"></a>Como este guia é estruturado

Este artigo faz parte de uma série. Os artigos a seguir devem ser lidos em conjunto, nesta ordem:

* Introdução (deste artigo)
* [Estratégia de monitoramento para modelos de implantação em nuvem](./cloud-models-monitor-overview.md)
* [Coletar os dados certos](./data-collection.md)
* [Alertas](./alerting.md)

## <a name="products-and-services"></a>Produtos e serviços

Alguns softwares e serviços estão disponíveis para ajudar a monitorar e gerenciar uma variedade de recursos hospedados no Azure, na sua rede corporativa ou em outros provedores de nuvem. Eles são:

* System Center Operations Manager
* O Azure Monitor, que agora inclui o Log Analytics e o Application Insights
* Azure Policy e Azure Blueprints
* Automação do Azure
* Aplicativos Lógicos do Azure
* Hubs de eventos do Azure

Esta primeira versão do guia fala sobre nossas plataformas de monitoramento atuais: Azure Monitor e System Center Operations Manager. Além disso, descreve nossa estratégia recomendada para monitorar cada um dos modelos de implantação de nuvem. Também está incluído o primeiro conjunto de recomendações de monitoramento, começando com a coleta de dados e os alertas.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Estratégia de monitoramento para modelos de implantação em nuvem](./cloud-models-monitor-overview.md)
