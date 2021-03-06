---
title: Guia de decisão de registro em log e relatório
description: Desenvolva uma estratégia principal de registro em log, relatório e monitoramento para garantir que sua organização atenda às metas de tempo de atividade, segurança e conformidade de políticas.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: a6229013dcbc56ff39fd4d41a5b81f13b446e625
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222773"
---
# <a name="logging-and-reporting-decision-guide"></a>Guia de decisão de registro em log e relatório

Todas as organizações precisam de mecanismos para notificar as equipes de TI sobre problemas de desempenho, tempo de atividade e segurança antes que tornem-se problemas sérios. Uma estratégia de monitoramento com êxito permite reconhecer como está o desempenho dos componentes individuais que compõem as cargas de trabalho e a infraestrutura de rede. No contexto de uma migração de nuvem pública, integrar registro em log e relatório a qualquer um dos sistemas de monitoramento existentes, enquanto monitora eventos e métricas importantes para a equipe de TI apropriada, é essencial para garantir que a organização atenda às metas de tempo de atividade, segurança e conformidade com a política.

![Plotagem das opções de registro em log, relatório e monitoramento do menos ao mais complexo, alinhado com links de salto abaixo](../../_images/decision-guides/decision-guide-logging-and-reporting.png)

Ir para: [Planejar a infraestrutura de monitoramento](#plan-your-monitoring-infrastructure) | [Nativo de Nuvem](#cloud-native) | [Extensão local](#on-premises-extension) | [Agregação de gateway](#gateway-aggregation) | [Monitoramento híbrido (local)](#hybrid-monitoring-on-premises) | [Monitoramento híbrido (baseado em nuvem)](#hybrid-monitoring-cloud-based) | [Multinuvem](#multicloud) | [Saiba mais](#learn-more)

O ponto de inflexão ao determinar uma estratégia de identidade e registro em log de nuvem baseia-se principalmente nos investimentos existentes feitos pela organização nos processos operacionais e, até certo ponto, nos requisitos necessários para dar suporte a uma estratégia de multinuvem.

As atividades na nuvem podem ser registradas e relatadas de várias maneiras. Os registros em log centralizado e nativo de nuvem são duas opções comuns de serviço gerenciado, orientadas pelo design de assinatura e pelo número de assinaturas.

## <a name="plan-your-monitoring-infrastructure"></a>Planejar sua infraestrutura de monitoramento

Ao planejar a implantação, será necessário considerar onde os dados de registro em log serão armazenados e como os serviços de relatório e monitoramento baseados em nuvem serão integrados com os processos e as ferramentas existentes.

| Pergunta | Nativo da nuvem | Extensão local | Monitoramento híbrido | Agregação de gateway |
|-----|-----|-----|-----|-----|
| Há uma infraestrutura de monitoramento local existente? | Não | Sim | Sim |  Não |
| Há requisitos para impedir o armazenamento de dados do log em locais de armazenamento externos? | Não | Sim | Não | Não |
| Você precisa integrar o monitoramento de nuvem com sistemas locais? | Não | Não | Sim | Não |
Você precisará processar ou filtrar dados telemétricos, antes de enviá-los aos sistemas de monitoramento? | Não | Não | Não | Sim |

### <a name="cloud-native"></a>Nativo da nuvem

Se a organização atualmente não tiver sistemas de registros em log e relatórios estabelecidos ou se a implantação planejada não precisar ser integrada ao sistema local existente ou outros sistemas de monitoramento externos, uma solução de SaaS nativa de nuvem, como o [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview), será a opção mais simples.

Nesse cenário, todos os dados de log são gravados e armazenados na nuvem, enquanto as ferramentas de registro em log e relatórios que processam e descobrem informações para a equipe de TI são fornecidas pela plataforma do Azure e pelo Azure Monitor.

As soluções de registro em log personalizadas baseadas no Azure Monitor podem ser implementadas conforme necessário para cada assinatura ou carga de trabalho em implantações menores ou experimentais. Essas soluções são organizadas de modo centralizado para monitorar dados de log em todo o espaço de nuvem.

**Suposições sobre a solução nativa da nuvem:** O uso de um sistema de registro em log e relatório de nuvem nativa supõe o seguinte:

- Não é necessário integrar os dados do log das cargas de trabalho de nuvem em sistemas locais existentes.
- Você não usará os sistemas de relatórios baseados em nuvem para monitorar sistemas locais.

### <a name="on-premises-extension"></a>Extensão local

Uma nova etapa de desenvolvimento significativa pode ser necessária para que os aplicativos e os serviços que estejam migrando para a nuvem usem soluções baseadas em nuvem para registro em log e relatórios, como o Azure Monitor. Nesses casos, considere permitir que essas cargas de trabalho continuem enviando dados de telemetria para sistemas locais existentes.

Para dar suporte a essa abordagem, os recursos de nuvem precisarão se comunicar diretamente com os sistemas locais por meio de uma combinação de [rede híbrida](../software-defined-network/hybrid.md) e [serviços de domínio hospedados na nuvem](../identity/index.md#cloud-hosted-domain-services). Dessa forma, a rede virtual na nuvem funcionará como uma extensão da rede do ambiente local. Consequentemente, as cargas de trabalho hospedadas na nuvem poderão comunicar-se diretamente com o sistema de registro em log e relatórios local.

Essa abordagem converte o investimento existente em ferramentas de monitoramento com modificações limitadas para todos os aplicativos ou serviços implantados na nuvem. Geralmente, essa é a abordagem mais rápida para dar suporte ao monitoramento durante uma migração lift-and-shift. Porém, ele não capturará dados de log produzidos por recursos de PaaS e SaaS baseados em nuvem e omitirá todos os logs relacionados à VM gerados pela plataforma de nuvem propriamente dita, tais como o status da VM. Como resultado, esse padrão deverá ser uma solução temporária até que uma solução de monitoramento híbrido mais abrangente seja implementada.

Suposições somente&ndash;locais:

- É necessário manter os dados do log somente no ambiente local para dar suporte aos requisitos técnicos ou devido a requisitos da política ou regulatórios.
- Os sistemas locais não dão suporte a registros em log e relatórios híbridos ou soluções de agregação de gateway.
- Os aplicativos baseados em nuvem podem enviar telemetria diretamente aos sistemas de registro em log local ou os agentes de monitoramento que enviam para o local podem ser implantados em VMs de carga de trabalho.
- As cargas de trabalho não dependem de serviços de PaaS ou SaaS que exigem registros em log e relatórios baseados em nuvem.

### <a name="gateway-aggregation"></a>Agregação de gateway

Para cenários em que a quantidade de dados de telemetria baseados em nuvem é grande ou os sistemas de monitoramento locais existentes precisam que os dados de log sejam modificados antes do processamento, pode ser necessário usar um serviço de [agregação de gateway](https://docs.microsoft.com/azure/architecture/patterns/gateway-aggregation) de dados de log.

Um serviço de gateway é implantado no provedor de nuvem. Em seguida, aplicativos e serviços relevantes são configurados para enviar dados telemétricos para o gateway, em vez de um sistema de registro em log padrão. O gateway poderá, em seguida, processar os dados: agregando, combinando ou formatando-os antes de enviá-los ao serviço de monitoramento para ingestão e análise.

Além disso, um gateway poderá ser utilizado para agregar e pré-processar dados telemétricos vinculados a sistemas híbridos ou nativos de nuvem.

Suposições sobre a agregação de gateway:

- Você espera grandes volumes de dados de telemetria dos aplicativos ou serviços baseados em nuvem.
- Você precisará formatar ou otimizar os dados telemétricos, antes de enviá-los aos sistemas de monitoramento.
- Os sistemas de monitoramento têm APIs ou outros mecanismos disponíveis para ingerir dados do log após processamento pelo gateway.

### <a name="hybrid-monitoring-on-premises"></a>Monitoramento híbrido (local)

Uma solução de monitoramento híbrido combina dados do log dos recursos locais e da nuvem para fornecer uma exibição integrada do status operacional da propriedade de TI.

Se você já tem um investimento em sistemas de monitoramento locais cuja substituição seria difícil ou muito cara, pode ser necessário integrar a telemetria das cargas de trabalho de nuvem nas soluções de monitoramento locais já existentes. Em um sistema de monitoramento local híbrido, os dados telemétricos locais continuam usando o sistema de monitoramento local existente. Os dados telemétricos baseados em nuvem são enviados diretamente ao sistema de monitoramento local ou são enviados ao Azure Monitor e então compilados e ingeridos no sistema local a intervalos regulares.

**Suposições sobre o monitoramento híbrido local:** O uso de um sistema local de registro em log e relatório para monitoramento híbrido supõe o seguinte:

- Você precisa usar sistemas de relatórios locais existentes para monitorar as cargas de trabalho na nuvem.
- Você precisa manter a propriedade dos dados do log no local.
- Os sistemas de gerenciamento locais têm APIs ou outros mecanismos disponíveis para ingerir dados do log de sistemas baseados em nuvem.

> [!TIP]
> Como parte da natureza iterativa da migração na nuvem, fazer a transição de monitoramentos nativo na nuvem e local distintos para uma abordagem híbrida parcial é provável conforme a integração de serviços e recursos baseados em nuvem para seu acervo de TI geral amadurece.

### <a name="hybrid-monitoring-cloud-based"></a>Monitoramento híbrido (baseado em nuvem)

Se você não tiver uma forte necessidade de manter um sistema de monitoramento local ou se quiser substituir os sistemas de monitoramento locais por uma solução de baseada em nuvem centralizada, também poderá optar por integrar dados do log locais com um Azure Monitor para fornecer um sistema de monitoramento baseado em nuvem centralizado.

Espelhando a abordagem centrada em local, neste cenário, cargas de trabalho baseadas em nuvem enviariam telemetria diretamente para o Azure Monitor e serviços e aplicativos locais enviariam a telemetria diretamente para o Azure Monitor ou agregariam esses dados localmente para ingestão no Azure Monitor a intervalos regulares. O Azure Monitor então serviria como seu sistema de monitoramento baseado em nuvem e relatório principal para todo o acervo de TI.

Suposições sobre o monitoramento híbrido baseado em nuvem: O uso de sistemas de registro em log e relatório baseados em nuvem para monitoramento híbrido supõe o seguinte:

- Você não depende de sistemas de monitoramento locais existentes.
- As cargas de trabalho não possuem requisitos regulatórios ou de política para armazenar dados do log no local.
- Os sistemas de monitoramento baseados em nuvem têm APIs ou outros mecanismos disponíveis para ingerir dados do log de aplicativos e serviços locais.

### <a name="multicloud"></a>Multinuvem

Integrar os recursos de registro em log e relatório em uma plataforma com várias nuvens pode ser complexo. Os serviços oferecidos entre plataformas muitas vezes não são diretamente comparáveis, e os recursos de registro em log e telemetria fornecidos por esses serviços também são diferentes.
O suporte para registro em log em várias nuvens geralmente exigirá o uso de serviços de gateway para processar dados do log em um formato comum antes de enviar os dados para uma solução de registro em log híbrida.

## <a name="learn-more"></a>Saiba mais

O [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) é o serviço de monitoramento e relatório padrão do Azure. Ela oferece:

- Uma plataforma unificada para coletar telemetria de aplicativos, telemetria do host (como VMs), métricas de contêineres, métricas da plataforma do Azure e logs de eventos.
- Visualização, consultas, alertas e ferramentas de análise. Adicionalmente, pode fornecer informações sobre máquinas virtuais, sistemas operacionais convidados, redes virtuais e eventos de aplicativo de carga de trabalho.
- [APIs REST](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-rest-api-walkthrough) para integração com serviços externos e automação de serviços de monitoramento e alerta.
- [Integração](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-partners) com muitos fornecedores de terceiros populares.

## <a name="next-steps"></a>Próximas etapas

Registro em log e relatórios são apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
