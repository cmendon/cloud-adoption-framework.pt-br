---
title: Estimar os custos de nuvem antes da migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação do processo de estimativa dos custos de nuvem antes da migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: be4fe4616b4f0599075ceac2b9c0838949b350c8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548491"
---
# <a name="estimate-cloud-costs"></a>Estimar os custos de nuvem

Durante a migração, há vários fatores que podem afetar as decisões e as atividades de execução. Para ajudar a entender quais dessas opções são melhores para situações diferentes, este artigo aborda várias opções para estimar os custos de nuvem.

## <a name="digital-estate-size"></a>Tamanho do estado digital

O tamanho do seu espaço digital afeta diretamente as decisões de migração. As migrações que envolvem menos de 250 VMs podem ser estimadas muito mais facilmente do que uma migração envolvendo mais de 10.000 VMs. É altamente recomendável que você selecione uma carga de trabalho menor que a sua primeira migração. Isso dá à sua equipe a oportunidade de saber como estimar os custos de um esforço de migração simples antes de tentar estimar migrações de carga de trabalho maiores e mais complicadas.

No entanto, observe que as migrações menores, de carga de trabalho única, ainda podem envolver uma quantidade muito variada de ativos de suporte. Se a sua migração envolver em 1.000 VMs, uma ferramenta como [migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-overview) provavelmente será suficiente para coletar dados sobre o inventário e os custos de previsão. As opções adicionais de ferramentas de estimativa de custo são descritas no artigo sobre [cálculos de custo de imóveis](../../../digital-estate/calculate.md).

Para os bens digitais de mais de 1000 unidades, ainda é possível dividir uma estimativa em quatro ou cinco iterações acionáveis, tornando o processo de estimativa gerenciável. Para os bens maiores ou quando um grau mais alto de precisão de previsão é necessário, uma abordagem mais abrangente, como a descrita na seção "[imóvel digital](../../../digital-estate/index.md)" da estrutura de adoção de nuvem, provavelmente será necessária.

## <a name="accounting-models"></a>Modelos de contabilidade

Modelos de contabilidade

Se você estiver familiarizado com os processos tradicionais de aquisição de ti, a estimativa na nuvem poderá parecer estrangeira. Ao adotar tecnologias de nuvem, a aquisição muda de um modelo de despesas de capital rígido e estruturado para um modelo de despesa de operação fluida. No modelo de despesas de capital tradicional, a equipe de ti tentaria consolidar a potência de compra de várias cargas de trabalho em vários programas para centralizar um pool de ativos de ti compartilhados que poderiam dar suporte a cada uma dessas soluções. No modelo de nuvem despesas operacionais, os custos podem ser atribuídos diretamente às necessidades de suporte de cargas de trabalho individuais, equipes ou unidades de negócios. Essa abordagem permite uma atribuição mais direta de custos para o cliente interno com suporte. Ao estimar os custos, é importante entender primeiro quanto desse novo recurso de contabilidade será usado pela equipe de ti.

Para aqueles que desejam replicar a abordagem de despesas de capital herdada para contabilidade, use as saídas de uma das abordagens sugeridas na seção "[tamanho de imóveis digitais](#digital-estate-size)" acima para obter uma base de custo anual. Em seguida, multiplique esse custo anual pelo ciclo de atualização de hardware típico da empresa. O ciclo de atualização de hardware é a taxa na qual uma empresa substitui o hardware de envelhecimento, normalmente medido em anos. A taxa de execução anual multiplicada pelo ciclo de atualização de hardware cria uma estrutura de custo semelhante a um padrão de investimento de despesas de capital.

## <a name="next-steps"></a>Próximos passos

Depois de estimar os custos, a migração pode começar. No entanto, seria prudente revisar [as opções de parceria e suporte](./partnership-options.md) antes de iniciar qualquer migração.

> [!div class="nextstepaction"]
> [Noções básicas sobre opções de parceria](./partnership-options.md)
