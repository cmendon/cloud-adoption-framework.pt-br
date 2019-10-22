---
title: Criticalidade dos negócios – gerenciamento e operações de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticalidade dos negócios – gerenciamento e operações de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 290fcf7093f128c1415bbf960d65074d12490ae1
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683638"
---
# <a name="business-criticality-in-cloud-management"></a>Importância dos negócios no gerenciamento de nuvem

Em toda empresa, existe um pequeno número de cargas de trabalho que são muito importantes para falhar. Quando essas cargas de trabalho experimentam interrupções ou degradação de desempenho, um impacto adverso na receita e na lucratividade pode ser sentido em toda a empresa. Essas cargas de trabalho são consideradas de missão crítica.

Na outra extremidade do espectro, algumas cargas de trabalho podem ir meses por vez sem serem usadas. Baixo desempenho ou interrupções para essas cargas de trabalho não é desejável, mas o impacto é isolado e limitado.

Entender a criticalidade de cada carga de trabalho no portfólio de ti é a primeira etapa para cumprir os compromissos mútuos com o gerenciamento de nuvem.
A imagem abaixo descreve um alinhamento comum entre a escala de criticalidade a seguir e os compromissos padrão feitos pela empresa.

![Prioridade e alinhamento do nível de gerenciamento](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Escala de criticalidade

A primeira etapa em qualquer esforço de alinhamento de criticalidade de negócios é a criação de uma escala de criticalidade. Abaixo está um exemplo de escala que pode ser usado como uma referência ou um modelo para criar sua própria escala.

|Importância  |Exibição de negócios  |
|---------|---------|
|Missão crítica|Afeta a missão da empresa e pode afetar as declarações de lucros e perdas corporativas.|
|Unidade crítica|Afeta a missão de uma unidade de negócios específica e as instruções de lucros e perdas de unidades de negócios.|
|Alto|Pode não atrapalhar a missão, mas afeta os processos de alta importância. As perdas mensuráveis podem ser quantificadas no caso de interrupções.|
|Média|O impacto nos processos é provavelmente. As perdas são baixas ou inmensurável, mas danos à marca ou perdas de upstream são prováveis.|
|Baixo|O impacto nos processos de negócios é immensurável. Nenhum dano à marca ou perdas de upstream é provável. É provável que o impacto localizado em uma única equipe.|
|Sem suporte|Nenhum proprietário, equipe ou processo de negócios associado a essa carga de trabalho pode justificar qualquer investimento no gerenciamento contínuo da carga de trabalho|

É comum que as empresas incluam classificações de criticalidade adicionais específicas para um setor, uma vertical ou processos de negócios específicos. Exemplos de classificações adicionais incluem:

- **Conformidade-crítica:** Em setores altamente regulamentados, algumas cargas de trabalho podem ser críticas como parte de um esforço para manter os requisitos de conformidade.
- **Segurança-crítica:** Algumas cargas de trabalho podem não ser de missão crítica, mas as interrupções podem resultar em perda de dados ou acesso indesejado a informações protegidas.
- **Segurança-crítica:** Quando mora ou a segurança física de funcionários e clientes estão em risco durante uma interrupção, pode ser prudente classificar cargas de trabalho como de segurança crítica.

## <a name="importance-of-accurate-criticality"></a>Importância da criticalidade precisa

Posteriormente neste processo, a equipe de gerenciamento de nuvem usará essa classificação para determinar a quantidade de esforço necessária para atender aos níveis de criticalidade alinhados. Em ambientes locais, o gerenciamento de operações geralmente é adquirido central e tratado como uma carga comercial necessária, com pouco ou nenhum custo operacional adicional. Na nuvem, o gerenciamento de operações (como toda a nuvem) é adquirido em uma base por ativo como custos operacionais mensais.

Como há um custo claro e direto para o gerenciamento de operações na nuvem, é importante alinhar corretamente os custos e as escalas de criticalidade desejadas.

## <a name="select-a-default-criticality"></a>Selecione uma criticalidade padrão

Uma revisão inicial de cada carga de trabalho no portfólio pode ser demorada. Para garantir que esse esforço não bloqueie a estratégia de nuvem mais ampla, é recomendável que ela e a empresa concordem com uma criticalidade padrão a ser aplicada a todas as cargas de trabalho.

Com base na escala de criticalidade acima, é recomendável que a criticalidade "média" seja usada como padrão. Isso permitirá que a equipe de estratégia de nuvem identifique rapidamente as cargas de trabalho que exigem um nível mais alto de importância.

## <a name="using-the-template"></a>Usando o modelo

As etapas a seguir se aplicam aos leitores que estão usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem.

1. A escala de criticalidade pode ser registrada na guia escala da pasta de trabalho.
2. Cada carga de trabalho no "exemplo" ou "modelo limpo" deve ser atualizada para refletir a importância padrão na coluna "criticalidade".
3. Os valores corretos devem ser inseridos pela empresa para refletir qualquer desvio da criticalidade padrão.

## <a name="next-steps"></a>Próximos passos

Quando a criticalidade for definida, [calcule e registre o impacto nos negócios](./impact.md).

> [!div class="nextstepaction"]
> [Calcular e registrar o impacto nos negócios](./impact.md)
