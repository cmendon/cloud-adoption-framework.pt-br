---
title: Instruções de política de amostra de Gerenciamento de Custos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instruções de política de amostra de Gerenciamento de Custos
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: fc8a691b446b5c40534e7189cb9d381aabd5f402
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828143"
---
# <a name="cost-management-sample-policy-statements"></a>Instruções de política de amostra de Gerenciamento de Custos

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco para os negócios.** Um resumo do risco que esta política abordará.
- **Instrução da política.** Uma clara explicação de resumo dos requisitos de política.
- **Opções de design.** Recomendações viáveis, especificações ou outras diretrizes que as equipes de TI e desenvolvedores possam usar ao implementar a política.

As instruções de política de exemplo a seguir abordam riscos de negócios comuns relacionados a custos. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="future-proofing"></a>Durabilidade

**Risco de negócios:** Critérios atuais que não garantem um investimento em uma disciplina de Gerenciamento de Custos da equipe de governança. No entanto, você antecipar o investimento no futuro.

**Instrução da política:** Você deve associar todos os ativos implantados à nuvem com uma unidade de cobrança e um aplicativo/carga de trabalho. Esta política garantirá que os esforços do Gerenciamento de Custos futuros entrarão em vigor.

**Opções de design:** Para obter informações sobre como estabelecer uma base de verificação futura, consulte as discussões relacionadas à criação de um MVP de governança nos [guias de design acionáveis](../journeys/index.md) incluídos como parte das diretrizes da estrutura de adoção da nuvem.

## <a name="budget-overruns"></a>Excedentes de orçamento

**Risco de negócios:** A implantação por autoatendimento cria um risco de excesso de gastos.

**Instrução da política:** Qualquer implantação de nuvem deve ser alocada para uma unidade de cobrança com orçamento aprovado e um mecanismo para limites orçamentários.

**Opções de design:** No Azure, o orçamento pode ser controlado com o [Gerenciamento de Custos do Azure](/azure/cost-management/manage-budgets)

## <a name="underutilization"></a>Subutilização

**Risco de negócios:** A empresa tem pré-pago por serviços de nuvem ou fez um compromisso anual gastar uma quantidade específica. Há um risco de que o valor acordado não seja usado, resultando em um investimento perdido.

**Instrução da política:** Cada unidade de cobrança com um orçamento de nuvem alocado atenderá anualmente para definir os orçamentos trimestralmente para ajustar os orçamentos e mensal de alocar tempo para revisar os gastos reais versus planejados. Discuta desvios maiores que 20% com o líder da unidade de cobrança mensal. Para fins de acompanhamento, atribua todos os ativos para uma unidade de cobrança.

**Opções de design:**

- No Azure, gastos planejados versus reais podem ser gerenciado através do [Gerenciamento de Custos do Azure](/azure/cost-management/quick-acm-cost-analysis)
- Há várias opções para agrupar recursos por unidade de cobrança. No Azure, um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) deve ser escolhido em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="overprovisioned-assets"></a>Ativos superprovisionados

**Risco de negócios:** Em data centers tradicionais locais, é uma prática comum de implantar ativos com capacidade extra, planejamento para crescimento distante no futuro. A nuvem pode dimensionar mais rapidamente do que o equipamento tradicional. Ativos na nuvem também são cobrados com base na capacidade técnica. Há um risco da prática do local antigo artificialmente aumentando os gastos com a nuvem.

**Instrução da política:** Qualquer ativo implantado na nuvem deve ser registrado em um programa que pode monitorar a utilização e relatar qualquer capacidade mais de 50% de utilização. Qualquer ativo implantado na nuvem deve ser agrupado ou marcado de uma maneira lógica, portanto, os membros da equipe governança podem envolver o proprietário da carga de trabalho em relação a qualquer otimização de ativos sobre provisionados.

**Opções de design:**

- No Azure, o [Assistente do Azure](/azure/advisor/advisor-cost-recommendations) pode fornecer recomendações de otimização.
- Há várias opções para agrupar recursos por unidade de cobrança. No Azure, um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) deve ser escolhido em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="overoptimization"></a>Otimização excessiva

**Risco de negócios:** O gerenciamento de custos efetivo cria novos riscos. A otimização dos gastos é o inverso para o desempenho do sistema. Ao reduzir os custos, há um risco de sobrecarregar gastos e produzindo as experiências de usuário insatisfatória.

**Instrução da política:** Qualquer ativo que afeta diretamente as experiências do cliente deve ser identificado por meio do agrupamento ou marcação. Antes de otimizar qualquer ativo que afete a experiência do cliente, a equipe de governança de nuvem deve ajustar a otimização com base em pelo menos 90 dias de tendências de utilização. Documente quaisquer intermitências sazonais ou orientadas por eventos consideradas ao otimizar ativos.

**Opções de design:**

- No Azure, [os recursos de insights do Azure Monitor](/azure/azure-monitor/insights/vminsights-performance) podem ajudar com a análise de utilização do sistema.
- Há várias opções para agrupar e marcar recursos baseados nas funções. No Azure, escolha um [modelo de consistência do recurso](../../decision-guides/resource-consistency/index.md) em conjunto com a equipe de governança e aplicado a todos os ativos.

## <a name="next-steps"></a>Próximas etapas

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que abordam os riscos de negócios específicos que se alinham aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas ao Gerenciamento de Custos, realize o download do [Modelo de Gerenciamento de Custos](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../journeys/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Usar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a conformidade com a política do Gerenciamento de Custos.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
