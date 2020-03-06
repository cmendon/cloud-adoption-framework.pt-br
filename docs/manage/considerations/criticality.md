---
title: Importância dos negócios no gerenciamento de nuvem
description: Use a estrutura de adoção de nuvem para o Azure para entender a importância da carga de trabalho e evitar o impacto adverso na receita e na lucratividade.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2c3d5a71025e821b9554e2a8d99223c7e6b0712b
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341446"
---
# <a name="business-criticality-in-cloud-management"></a>Importância dos negócios no gerenciamento de nuvem

Em toda empresa, existe um pequeno número de cargas de trabalho que são muito importantes para falhar. Essas cargas de trabalho são consideradas de missão crítica. Quando essas cargas de trabalho experimentam interrupções ou degradação de desempenho, o impacto adverso na receita e na lucratividade pode ser sentido em toda a empresa.

Na outra extremidade do espectro, algumas cargas de trabalho podem ir meses por vez sem serem usadas. Baixo desempenho ou interrupções para essas cargas de trabalho não é desejável, mas o impacto é isolado e limitado.

Entender a criticalidade de cada carga de trabalho no portfólio de ti é a primeira etapa para estabelecer compromissos mútuos com o gerenciamento de nuvem.
O diagrama a seguir ilustra um alinhamento comum entre a escala de criticalidade a seguir e os compromissos padrão feitos pela empresa.

![Prioridade e alinhamento do nível de gerenciamento](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Escala de criticalidade

A primeira etapa em qualquer esforço de alinhamento de criticalidade de negócios é criar uma escala de criticalidade. A tabela a seguir apresenta uma escala de exemplo a ser usada como uma referência, ou modelo, para criar sua própria escala.

| Importância | Exibição de negócios |
| --------- | --------- |
| Essenciais |  Afeta a missão da empresa e pode afetar visivelmente as instruções corporativas de lucros e perdas. |
| Unidade-crítica | Afeta a missão de uma unidade de negócios específica e suas instruções de lucros e perdas. |
| Alta | Pode não atrapalhar a missão, mas afeta os processos de alta importância. As perdas mensuráveis podem ser quantificadas no caso de interrupções. |
| Médio | O impacto nos processos é provavelmente. As perdas são baixas ou inmensurável, mas danos à marca ou perdas de upstream são prováveis. |
| Baixo | O impacto nos processos de negócios não é mensurável. Nem os danos à marca nem as perdas de upstream são prováveis. É provável que o impacto localizado em uma única equipe seja. |
| Sem suporte | Nenhum proprietário, equipe ou processo de negócios associado a essa carga de trabalho pode justificar qualquer investimento no gerenciamento contínuo da carga de trabalho. |

É comum que as empresas incluam classificações de criticalidade adicionais específicas para seus processos de negócios específicos do setor, vertical ou específico. Exemplos de classificações adicionais incluem:

- **Conformidade-crítica:** Em setores altamente regulamentados, algumas cargas de trabalho podem ser críticas como parte de um esforço para manter os requisitos de conformidade.
- **Segurança-crítica:** Algumas cargas de trabalho podem não ser de missão crítica, mas as interrupções podem resultar em perda de dados ou acesso indesejado a informações protegidas.
- **Segurança-crítica:** Quando mora ou a segurança física de funcionários e clientes está em risco durante uma interrupção, pode ser prudente classificar as cargas de trabalho como de segurança crítica.

## <a name="importance-of-accurate-criticality"></a>Importância da criticalidade precisa

Posteriormente no processo de adoção de nuvem, a equipe de gerenciamento de nuvem usará essa classificação para determinar a quantidade de esforço necessária para atender aos níveis de criticalidade alinhados. Em ambientes locais, o gerenciamento de operações é muitas vezes adquirido centralmente e tratado como uma carga comercial necessária, com pouco ou nenhum custo operacional adicional. Na nuvem, o gerenciamento de operações (como toda a nuvem) é adquirido em uma base por ativo como custos operacionais mensais.

Como há um custo claro e direto para o gerenciamento de operações na nuvem, é importante alinhar corretamente os custos e as escalas de criticalidade desejadas.

## <a name="select-a-default-criticality"></a>Selecione uma criticalidade padrão

Uma revisão inicial de cada carga de trabalho no portfólio pode ser demorada. Para garantir que esse esforço não bloqueie sua estratégia de nuvem mais ampla, recomendamos que suas equipes concordem com uma criticalidade padrão para aplicar a todas as cargas de trabalho.

Com base na tabela de escala de criticalidade anterior, recomendamos que você adote a criticalidade *média* como padrão. Isso permitirá que sua equipe de estratégia de nuvem identifique rapidamente as cargas de trabalho que exigem um nível mais alto de importância.

## <a name="use-the-template"></a>Usar o modelo

As etapas a seguir se aplicam se você estiver usando a [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) para planejar o gerenciamento de nuvem.

1. Registre a escala de criticalidade na guia **escala** da pasta de trabalho.
2. Atualize cada carga de trabalho no *exemplo* ou *Limpe o modelo* para refletir a criticalidade padrão na coluna de *criticalidade* .
3. A empresa deve inserir os valores corretos para refletir quaisquer desvios da criticalidade padrão.

## <a name="next-steps"></a>Próximas etapas

Depois que sua equipe tiver definido a criticalidade de negócios, você poderá [calcular e registrar o impacto nos negócios](./impact.md).

> [!div class="nextstepaction"]
> [Calcular e registrar o impacto nos negócios](./impact.md)
