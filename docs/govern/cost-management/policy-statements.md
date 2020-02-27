---
title: Instruções de política de amostra de Gerenciamento de Custos
description: Use a estrutura de adoção de nuvem do Azure para obter instruções de política de gerenciamento de custo de exemplo que ajudarão você a criar instruções de política de rascunho.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3f9b7076cb50d9526beccfe4faabaa043b010841
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708879"
---
# <a name="cost-management-sample-policy-statements"></a>Instruções de política de amostra de Gerenciamento de Custos

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco para os negócios:** Um resumo do risco que essa política abordará.
- **Declaração de política:** Uma explicação resumida clara dos requisitos de política.
- **Opções de design:** Recomendações, especificações ou outras diretrizes acionáveis que as equipes de ti e os desenvolvedores podem usar ao implementar a política.

As instruções de política de exemplo a seguir abordam riscos de negócios comuns relacionados a custos. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser prescritivas e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="future-proofing"></a>Durabilidade

**Risco para os negócios:** Critérios atuais que não garantem um investimento em uma disciplina de gerenciamento de custos da equipe de governança. No entanto, você antecipar o investimento no futuro.

**Declaração de política:** Você deve associar todos os ativos implantados à nuvem com uma unidade de cobrança e um aplicativo/carga de trabalho. Esta política garantirá que os esforços do Gerenciamento de Custos futuros entrarão em vigor.

**Opções de design:** Para obter informações sobre como estabelecer uma base de verificação futura, consulte as discussões relacionadas à criação de um MVP de governança nos [guias de design acionáveis](../guides/index.md) incluídos como parte das diretrizes da estrutura de adoção da nuvem.

## <a name="budget-overruns"></a>Excedentes de orçamento

**Risco para os negócios:** A implantação de autoatendimento cria um risco de excesso de gastos.

**Declaração de política:** Qualquer implantação na nuvem deve ser alocada a uma unidade de cobrança com orçamento aprovado e um mecanismo para limites orçamentários.

**Opções de design:** No Azure, o orçamento pode ser controlado com o [Gerenciamento de custos do Azure](https://docs.microsoft.com/azure/cost-management/manage-budgets)

## <a name="underutilization"></a>Subutilização

**Risco para os negócios:** A empresa tem pré-pago para serviços de nuvem ou fez um compromisso anual para gastar um valor específico. Há um risco de que o valor acordado não seja usado, resultando em um investimento perdido.

**Declaração de política:** Cada unidade de cobrança com um orçamento de nuvem alocado será atendida anualmente para definir orçamentos trimestrais para ajustar orçamentos e mensalmente para alocar tempo para revisar gastos planejados versus reais. Discuta desvios maiores que 20% com o líder da unidade de cobrança mensal. Para fins de acompanhamento, atribua todos os ativos para uma unidade de cobrança.

**Opções de design:**

- No Azure, gastos planejados versus reais podem ser gerenciado através do [Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis)
- Há várias opções para agrupar recursos por unidade de cobrança. No Azure, um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) deve ser escolhido em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="overprovisioned-assets"></a>Ativos superprovisionados

**Risco para os negócios:** Em data centers locais tradicionais, é prática comum implantar ativos com planejamento de capacidade extra para crescimento no futuro distante. A nuvem pode dimensionar mais rapidamente do que o equipamento tradicional. Ativos na nuvem também são cobrados com base na capacidade técnica. Há um risco da prática do local antigo artificialmente aumentando os gastos com a nuvem.

**Declaração de política:** Qualquer ativo implantado na nuvem deve ser registrado em um programa que possa monitorar a utilização e relatar qualquer capacidade acima de 50% da utilização. Qualquer ativo implantado na nuvem deve ser agrupado ou marcado de uma maneira lógica, portanto, os membros da equipe governança podem envolver o proprietário da carga de trabalho em relação a qualquer otimização de ativos sobre provisionados.

**Opções de design:**

- No Azure, o [Assistente do Azure](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations) pode fornecer recomendações de otimização.
- Há várias opções para agrupar recursos por unidade de cobrança. No Azure, um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) deve ser escolhido em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="overoptimization"></a>Otimização excessiva

**Risco para os negócios:** O gerenciamento de custos efetivo cria novos riscos. A otimização dos gastos é o inverso para o desempenho do sistema. Ao reduzir os custos, há um risco de sobrecarregar gastos e produzindo as experiências de usuário insatisfatória.

**Declaração de política:** Qualquer ativo que afeta diretamente as experiências do cliente deve ser identificado por meio de agrupamento ou marcação. Antes de otimizar qualquer ativo que afete a experiência do cliente, a equipe de governança de nuvem deve ajustar a otimização com base em pelo menos 90 dias de tendências de utilização. Documente quaisquer intermitências sazonais ou orientadas por eventos consideradas ao otimizar ativos.

**Opções de design:**

- No Azure, [os recursos de insights do Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-performance) podem ajudar com a análise de utilização do sistema.
- Há várias opções para agrupar e marcar recursos baseados nas funções. No Azure, escolha um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="next-steps"></a>Próximas etapas

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que abordam os riscos de negócios específicos que se alinham aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas ao Gerenciamento de Custos, realize o download do [Modelo de Gerenciamento de Custos](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Usar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a conformidade com a política do Gerenciamento de Custos.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
