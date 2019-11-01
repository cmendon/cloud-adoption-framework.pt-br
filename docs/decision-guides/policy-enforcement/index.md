---
title: Guia de decisão de imposição de política
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre as assinaturas de imposição de política como uma prioridade de design principal em migrações no Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 10af3ade249bcc115d5b273b2610c093e48bf9a2
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73238859"
---
# <a name="policy-enforcement-decision-guide"></a>Guia de decisão de imposição de política

A definição da política organizacional não é eficaz, a menos que ela possa ser imposta em sua organização. Um aspecto fundamental do planejamento de qualquer migração na nuvem é determinar a melhor maneira de combinar as ferramentas fornecidas pela plataforma de nuvem com seus processos de TI existentes para maximizar a conformidade com a política em toda a propriedade de nuvem.

![Gráfico com opções de aplicação de políticas, da menos para a mais complexa, alinhada aos links de salto abaixo](../../_images/decision-guides/decision-guide-policy-enforcement.png)

Ir para: [Melhores práticas de linha de base](#baseline-best-practices) | [Monitoramento de conformidade de política](#policy-compliance-monitoring) | [Aplicação de política](#policy-enforcement) | [Política entre organizações](#cross-organization-policy) | [Aplicação automatizada](#automated-enforcement)

À medida que o seu acervo de nuvem cresce, você se depara com uma necessidade correspondente de manter e impor políticas em uma matriz maior de recursos e assinaturas. Conforme seu acervo fica cada vez maior e os requisitos de política da sua organização aumentam, o escopo de seus processos de imposição de política precisa ser expandido para garantir uma adesão consistente à política e uma rápida detecção de violações.

Mecanismos de imposição de política fornecidos pela plataforma no nível do recurso ou da assinatura geralmente são suficientes para acervos de nuvem menores. Implantações menores justificam um escopo de imposição maior e podem precisar aproveitar mecanismos de imposição mais sofisticados que envolvem a implantação de padrões, o agrupamento e a organização de recursos e a integração da imposição da política com sistemas de relatórios e registro em log.

Os principais fatores para determinar o escopo de seus processos de imposição de política são os [requisitos de governança de nuvem](../../govern/index.md) da sua organização, o tamanho e a natureza de seu acervo de nuvem e como sua organização é refletida no seu [design de assinatura](../subscriptions/index.md). Um aumento no tamanho de seu acervo ou uma maior necessidade de gerenciar centralmente a imposição da política podem justificar um aumento no escopo da imposição.

## <a name="baseline-best-practices"></a>Melhores práticas de linha de base

Para implantações de nuvem simples e de assinatura única, muitas políticas corporativas podem ser impostas usando funcionalidades nativas de recursos e assinaturas no Azure. O uso consistente dos padrões discutidos em todos os [guias de decisão](../index.md) da Cloud Adoption Framework pode ajudar a estabelecer um nível de linha de base da política de conformidade sem investimento específico na imposição de política. Esses recursos incluem:

- [Modelos de implantação](../resource-consistency/index.md) podem provisionar recursos com a estrutura padronizada e a configuração.
- [Marcação e padrões de nomenclatura](../resource-tagging/index.md) podem ajudar a organizar as operações e oferecer suporte aos requisitos de negócios e de estatísticas.
- Restrições de rede e de gerenciamento de tráfego podem ser implementadas por meio da [Rede Definida por Software](../software-defined-network/index.md).
- [Controle de acesso baseado em função](../identity/index.md) pode proteger e isolar seus recursos de nuvem.

Inicie o seu planejamento de implantação da política de nuvem examinando como o aplicativo dos padrões discutidos ao longo desses guias pode ajudar a atender às suas necessidades organizacionais.

## <a name="policy-compliance-monitoring"></a>Monitorar a conformidade da política

Uma primeira etapa além de simplesmente contar com os mecanismos de imposição de política fornecidos pela plataforma do Azure é garantir a capacidade de verificar se os aplicativos e serviços baseados em nuvem estão em conformidade com a política organizacional. Isso inclui a implementação de funcionalidades de notificação para alertar as partes responsáveis se um recurso deixar de estar em conformidade. O [registro em log e os relatórios](../logging-and-reporting/index.md) efetivos do status de conformidade de suas cargas de trabalho de nuvem é uma parte crítica de uma estratégia de imposição de política corporativa.

Conforme sua propriedade de nuvem cresce, ferramentas adicionais como a [Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center) pode fornecer a segurança integrada e a detecção de ameaças e ajudar a aplicar gerenciamento centralizado de políticas e alertas para seu local e ativos de nuvem.

## <a name="policy-enforcement"></a>Aplicação de políticas

No Azure, você pode aplicar as definições de configuração e as regras de criação de recursos no nível de grupo de gerenciamento, de assinatura ou de grupo de recursos para ajudar a garantir o alinhamento com a política.

[O Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) é um serviço do Azure para criar, atribuir e gerenciar políticas. Essas políticas impõem diferentes regras e efeitos sobre os recursos para que esses recursos permaneçam em conformidade com seus padrões corporativos e contratos de nível de serviço. O Azure Policy avalia seus recursos quanto a não conformidade com políticas atribuídas. Por exemplo, você talvez queira limitar o tamanho da SKU de máquinas virtuais em seu ambiente. Depois que essa política é implementada, os recursos novos e existentes são avaliados quanto à conformidade. Com a política certa, os recursos existentes podem ser colocados em conformidade.

## <a name="cross-organization-policy"></a>Política entre organizações

À medida que seu acervo de nuvem aumenta para abranger várias assinaturas que exigem imposição, você precisa se concentrar em uma estratégia de imposição para todo o acervo de nuvem para garantir a consistência da política.

Sua [design de assinatura](../subscriptions/index.md) deve levar em conta para a que diz respeito à sua estrutura organizacional. Além de ajudar a dar suporte a organização complexa dentro de seu design de assinatura, [grupos de gerenciamento do Azure](../../ready/azure-best-practices/scaling-subscriptions.md#managing-multiple-subscriptions) podem ser usados para atribuir as regras do Azure Policy entre várias assinaturas.

## <a name="automated-enforcement"></a>Imposição automática

Embora modelos de implantação padronizado entrarão em vigor em uma escala menor, [o Azure BluePrints](https://docs.microsoft.com/azure/governance/blueprints/overview) permite a orquestração em larga escala padronizada de provisionamento e a implantação de soluções do Azure. As cargas de trabalho entre várias assinaturas podem ser implantadas com as configurações de política consistentes para todos os recursos criados.

Para ambientes de TI, ao integrar recursos de nuvem e locais, talvez seja necessário usar o registro em log e relatório de sistemas para fornecer recursos de monitoramento híbrido. Seus sistemas de monitoramento operacionais personalizados ou de terceiros podem oferecer recursos de imposição de política adicionais. Para acervos de nuvem maiores ou mais maduros, considere a melhor maneira de integrar esses sistemas a seus ativos de nuvem.

## <a name="next-steps"></a>Próximas etapas

A imposição de política é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
