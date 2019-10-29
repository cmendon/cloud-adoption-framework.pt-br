---
title: O que é classificação de dados?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: A classificação de dados permite que você determine e atribua valor aos dados da sua organização e é um ponto de partida comum para governança.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 513fa8c7ea57909657584815f12b37e07c02f5d0
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72980231"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-data-classification"></a>O que é classificação de dados?

A classificação de dados permite que você determine e atribua valor aos dados da sua organização e é um ponto de partida comum para governança. O processo de classificação de dados categoriza os dados por sensibilidade e impacto nos negócios a fim de identificar os riscos. Quando os dados são classificados, você pode gerenciá-los de maneiras que protejam dados confidenciais ou importantes contra roubo ou perda.

## <a name="understand-data-risks-then-manage-them"></a>Entender os riscos de dados e gerenciá-los

Antes que qualquer risco possa ser gerenciado, ele deve ser compreendido. No caso de responsabilidade de violação de dados, esse entendimento começa com a classificação de dados. A classificação de dados é o processo de associar uma característica de metadados a cada ativo em um imóvel digital, que identifica o tipo de dados associado a esse ativo.

Qualquer ativo identificado como um candidato potencial para migração ou implantação na nuvem deve ter metadados documentados para registrar a classificação de dados, a importância dos negócios e a responsabilidade da cobrança. Esses três pontos de classificação podem ir muito longe para compreensão e minimização de riscos.

## <a name="classifications-microsoft-uses"></a>Classificações que a Microsoft usa

A seguir, uma lista de classificações de usos da Microsoft. Dependendo do setor ou dos requisitos de segurança existentes, os padrões de classificação de dados podem já existir em sua organização. Se não houver padrão, talvez você queira usar essa classificação de exemplo para entender melhor seu próprio perfil de bens e riscos digitais.

- **Não comercial:** Dados de sua vida pessoal que não pertencem à Microsoft.
- **Público:** Dados corporativos disponíveis gratuitamente e aprovados para consumo público.
- **Geral:** Dados de negócios que não são destinados a um público público.
- **Confidencial:** Dados de negócios que podem causar danos à Microsoft se estiverem sobrepartilhados.
- **Altamente confidencial:** Dados de negócios que poderiam causar grandes danos à Microsoft se estiverem sobrepartilhados.

## <a name="tagging-data-classification-in-azure"></a>Marcação de classificação de dados no Azure

As marcas de recurso são uma boa abordagem para armazenamento de metadados, e você pode usar essas marcas para aplicar informações de classificação de dados a recursos implantados. Embora a marcação de ativos de nuvem por classificação não seja uma substituição para um processo de classificação de dados formal, ela fornece uma ferramenta valiosa para o gerenciamento de recursos e a aplicação de políticas. A [proteção de informações do Azure](https://docs.microsoft.com/azure/information-protection/what-is-information-protection) é uma solução excelente para ajudá-lo a classificar _os dados_ em si, independentemente de onde eles estiverem (no local, no Azure ou em algum outro lugar). Considere isso como parte de uma estratégia de classificação geral.

Para obter informações adicionais sobre a marcação de recursos no Azure, consulte [usando marcas para organizar os recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="next-steps"></a>Próximos passos

Aplique classificações de dados durante um dos guias de governança acionáveis.

> [!div class="nextstepaction"]
> [Escolha um guia de governança acionável](../guides/index.md)
