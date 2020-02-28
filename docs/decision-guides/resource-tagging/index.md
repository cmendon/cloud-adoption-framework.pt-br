---
title: Guia de decisão de marcação e nomenclatura de recurso
description: Saiba mais sobre as abordagens e opções de nomenclatura e marcação ao organizar recursos baseados em nuvem, como parte do Cloud Adoption Framework para o Azure.
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 90b69a21f1643d4545b2ea5bce46d0c3c499d9a3
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708675"
---
# <a name="resource-naming-and-tagging-decision-guide"></a>Guia de decisão de marcação e nomenclatura de recurso

Organizar recursos baseados em nuvem é uma das tarefas mais importantes para TI, a menos que você tenha apenas implantações simples. Organizar seus recursos atende a três objetivos principais:

- **Gerenciamento de Recursos:** Suas equipes de TI precisarão localizar rapidamente os recursos associados às cargas de trabalho específicas, ambientes, grupos de propriedade ou outras informações importantes. Os recursos de organização são essenciais para a atribuição de funções organizacionais e permissões de acesso para o gerenciamento de recursos.
- **Automação:** Além de tornar mais fácil para os recursos que a TI gerencia, um esquema organizacional apropriado lhe permite tirar proveito de automação como parte da criação de recursos, monitoramento operacional e criação de processos de DevOps.
- **Contabilidade:** Tornar os grupos de negócios cientes do consumo de recursos de nuvem requer que a TI entenda quais cargas de trabalho e equipes estão usando quais recursos. Para dar suporte a abordagens, como estatísticas de análise e estorno, os recursos de nuvem precisam ser organizados para refletir o uso e propriedade.

## <a name="tagging-decision-guide"></a>Guia de decisão de marcação

![Opções de marcação de plotagem da menos para a mais complexa, alinhadas aos links de salto abaixo](../../_images/decision-guides/decision-guide-resource-tagging.png)

Ir para: [Convenções de nomenclatura de linha de base](#baseline-naming-conventions) | [Padrões de marcação de recursos](#resource-tagging-patterns) | [Saiba mais](#learn-more)

Sua abordagem de marcação pode ser simples ou complexa, com a ênfase variando de dar suporte às equipes de TI que gerenciam as cargas de trabalho de nuvem até a integração de informações relacionadas a todos os aspectos da empresa.

Um foco de marcação alinhado com a TI, como marcação baseada em carga de trabalho, função ou ambiente, reduzirá a complexidade de monitorar ativos e facilitará muito a tomada de decisões de gerenciamento com base em requisitos operacionais.

Esquemas de marcação que incluem um foco alinhado aos negócios, como contabilidade, propriedade empresarial ou nível de importância de negócios, podem exigir um maior investimento de tempo para criar padrões de marcação que reflitam os interesses empresariais e manter esses padrões ao longo do tempo. No entanto, o resultado desse processo é um sistema de marcação que fornece uma maior habilidade de levar em conta os custos e o valor dos ativos de TI para a empresa como um todo. Essa associação do valor empresarial de um ativo a seus custos operacionais é uma das primeiras etapas para alterar a percepção de centro de custo de TI em sua organização como um todo.

## <a name="baseline-naming-conventions"></a>Convenções de nomenclatura da linha de base

Uma convenção de nomenclatura padronizada é o ponto de partida para organizar seus recursos hospedados na nuvem. Um sistema de nomenclatura adequadamente estruturado permite que você identifique rapidamente os recursos de gerenciamento e fins de contabilização. Se você tiver convenções de nomenclatura de TI existentes em outras partes da sua organização, considere se as suas convenções de nomenclatura de nuvem devem ser alinhadas a elas ou se você deve estabelecer padrões separados baseados em nuvem.

Observe também que os tipos de recursos do Azure diferentes têm diferentes [requisitos de nomenclatura](../../ready/azure-best-practices/naming-and-tagging.md). As convenções de nomenclatura devem ser compatíveis com esses requisitos de nomenclatura.

## <a name="resource-tagging-patterns"></a>Padrões de marcação de recursos

Para a organização mais sofisticada do que uma convenção de nomenclatura consistente apenas pode fornecer, as plataformas de nuvem compatíveis com a capacidade de marcar os recursos.

*Marcas* são elementos de metadados anexados aos recursos. As marcas consistem em pares de cadeias de caracteres de chave/valor. Os valores que incluem esses pares cabem a você, mas a aplicação de um conjunto consistente de marcas globais, como parte de uma nomenclatura abrangente e política de marcação, é uma parte essencial de uma política de governança geral.

Como parte do processo de planejamento, use as seguintes perguntas para ajudar a determinar o tipo de informação a que suas marcas de recurso precisam dar suporte:

- As suas políticas de nomenclatura e marcação precisam integrar-se às políticas organizacionais e de nomenclatura existentes em sua empresa?
- Você implementará um sistema de contabilidade de estorno ou análise? Você precisará associar recursos a informações de contabilidade para departamentos, grupos empresariais e equipes em mais detalhes do que um simples detalhamento de nível de assinatura permite?
- A marcação precisa representar detalhes desses requisitos de conformidade regulatória para um recurso? E os detalhes operacionais como requisitos de tempo de atividade, cronogramas de patch ou requisitos de segurança?
- Quais marcas serão necessárias para todos os recursos com base na política de TI central? Quais marcas serão opcionais? As equipes individuais têm permissão para implementar os próprios esquemas de marcação personalizados?

Os padrões comuns de marcação listados a seguir dão exemplos de como a marcação pode ser usada para organizar os ativos de nuvem. Esses padrões não devem ser exclusivos e podem ser usados em paralelo, fornecendo várias maneiras de organizar os ativos com base nas necessidades da sua empresa.

<!-- markdownlint-disable MD033 -->

| Tipo de marca | Exemplos | Descrição |
|-----|-----|-----|
| Funcional            | app = catalogsearch1 <br/>camada = web <br/>webserver = apache<br/>env = prod <br/>env = preparo <br/>env = dev                 | Categorize os recursos em relação à sua finalidade dentro de uma carga de trabalho, em qual ambiente foram implantados ou outra funcionalidade e detalhes operacionais.                                 |
| classificação        | confidentiality=private<br/>SLA = 24 horas                                 | Classifica um recurso, como são usados e quais políticas se aplicam a ele                               |
| Contabilidade            | departamento = financeiro <br/>projeto = catalogsearch <br/>região = northamerica | Permite o recurso a ser associado a grupos específicos dentro de uma organização para fins de cobrança |
| Parceria           | proprietário = jsmith <br/>contactalias = catsearchowners<br/>stakeholders = user1;user2;user3<br/>                       | Fornece informações sobre o que as pessoas (fora da IT) são relacionadas ou caso contrário, são afetadas pelo recurso                      |
| Finalidade               | businessprocess=support<br/>businessimpact=moderate<br/>revenueimpact=high   | Alinha os recursos para as funções de negócios para dar melhor suporte a decisões de investimento  |

<!-- markdownlint-enable MD033 -->

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre nomenclatura e marcação no Azure, consulte:

- [Convenções de nomenclatura para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming). Veja esta orientação quanto às convenções de nomenclatura recomendadas para recursos do Azure.
- [Use as marcas para organizar seus recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags). Você pode aplicar marcas no Azure no grupo de recursos e no nível do recurso individual, dando a você flexibilidade na granularidade de quaisquer relatórios de estatísticas com base em marcas aplicadas.

## <a name="next-steps"></a>Próximas etapas

A marcação de recursos é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
