---
title: O que é classificação de dados?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: O que é classificação de dados?
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d293aa5b4427b8f714175b85c6bb5197b53f107a
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027055"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-data-classification"></a>O que é classificação de dados?

A classificação de dados permite que você determine e atribua valor aos dados da sua organização e é um ponto de partida comum para governança. O processo de classificação de dados categoriza os dados por sensibilidade e impacto nos negócios a fim de identificar os riscos. Depois que os dados são classificados, eles podem ser gerenciados de maneiras que protegem dados confidenciais ou importantes contra roubo ou perda.

## <a name="understand-data-risks-then-manage-them"></a>Entender os riscos de dados e gerenciá-los

Antes que qualquer risco possa ser gerenciado, ele deve ser compreendido. No caso de responsabilidade de violação de dados, esse entendimento começa com a classificação de dados. A classificação de dados é o processo de associar uma característica de dados de metadados para todos os ativos em um estado digital, que identifica o tipo de dados associados a esse ativo.

A Microsoft sugere que qualquer ativo que for identificado como um candidato potencial para a migração ou implantação para a nuvem deve ter documentado metadados para registrar a classificação de dados, nível de importância de negócios e responsabilidade de cobrança. Esses três pontos de classificação podem ir muito longe para compreensão e minimização de riscos.

## <a name="microsofts-data-classification"></a>Classificação de dados da Microsoft

A seguir, uma lista de classificações de usos da Microsoft. Dependendo do seu setor ou requisitos de segurança existentes, os padrões de classificações de dados já podem existir dentro da sua organização. Se não houver nenhum padrão, convidamos você a usar essa classificação de exemplo para entender melhor seu próprio perfil de bens e riscos digitais.

- **Não comercial:** Dados de sua vida pessoal que não pertencem à Microsoft.
- **Público:** Dados corporativos disponíveis gratuitamente e aprovados para consumo público.
- **Geral:** Dados de negócios que não são destinados a um público público.
- **Confidencial:** Dados de negócios que poderiam causar danos à Microsoft se estiverem sobrepartilhados.
- **Altamente confidencial:** Dados de negócios que poderiam causar grandes danos à Microsoft se estiverem sobrepartilhados.

## <a name="tagging-data-classification-in-azure"></a>Marcação de classificação de dados no Azure

Cada provedor de nuvem deve oferecer um mecanismo para gravar metadados sobre qualquer ativo. No caso do Azure, as marcas de recurso são a abordagem sugerida para armazenamento de metadados e essas marcas podem ser usadas para aplicar informações de classificação de dados a recursos implantados. Embora a marcação de ativos de nuvem por classificação não seja uma substituição para um processo de classificação de dados formal, ela fornece uma ferramenta valiosa para o gerenciamento de recursos e a aplicação de políticas.

Para saber mais sobre marcação de recursos no Azure, consulte o artigo em [Uso de marcas para organizar os recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="next-steps"></a>Próximas etapas

Aplique classificações de dados durante um dos guias de governança acionáveis.

> [!div class="nextstepaction"]
> [Escolha um guia de governança acionável](../guides/index.md)
