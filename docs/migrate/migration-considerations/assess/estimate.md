---
title: Estimar os custos de nuvem antes da migração
description: Explicação do processo de estimar custos de nuvem antes da migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 0618676a995971951a27a5bdba66b7e9b126d7d6
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802575"
---
# <a name="estimate-cloud-costs"></a>Estimar os custos de nuvem

Durante a migração, há vários fatores que podem afetar as decisões e as atividades de execução. Para ajudar a entender quais dessas opções são melhores para diferentes situações, este artigo aborda várias opções para estimar os custos de nuvem.

## <a name="digital-estate-size"></a>Tamanho da propriedade digital

O tamanho de sua propriedade digital afeta diretamente as decisões de migração. As migrações que envolvem menos de 250 VMs podem ser estimadas com muito mais facilidade do que uma migração que envolve mais de 10 mil VMs. É altamente recomendável que você selecione uma carga de trabalho menor como sua primeira migração. Isso dá à sua equipe a oportunidade de saber como estimar os custos de um esforço de migração simples antes de tentar estimar migrações de carga de trabalho maiores e mais complicadas.

No entanto, observe que migrações menores e de carga de trabalho única ainda podem envolver uma quantidade muito variada de ativos de suporte. Se a migração envolver menos de mil VMs, provavelmente uma ferramenta como as [Migrações para Azure](https://docs.microsoft.com/azure/migrate/migrate-overview) será suficiente para coletar dados no inventário e prever custos. Outras opções de ferramentas para estimativa de custos são descritas no artigo sobre [cálculos de custo da propriedade digital](../../../digital-estate/calculate.md).

Para os bens digitais de mais de 1000 unidades, ainda é possível dividir uma estimativa em quatro ou cinco iterações acionáveis, tornando o processo de estimativa gerenciável. Para propriedades maiores ou quando for necessário um grau mais alto de precisão de previsão, uma abordagem mais abrangente, como a descrita na seção "[Propriedade digital](../../../digital-estate/index.md)" da Cloud Adoption Framework, provavelmente será necessária.

## <a name="accounting-models"></a>Modelos contábeis

Modelos contábeis

Se você já conhece o processo tradicional de aquisição de TI, a estimativa na nuvem pode parecer estranha. Ao adotar tecnologias de nuvem, a aquisição passa de um modelo de despesas de capital estruturado e rígido para um modelo de despesas operacionais fluido. No modelo tradicional de despesas de capital, a equipe de TI tentaria consolidar o poder de compra para várias cargas de trabalho entre vários programas para centralizar um pool de ativos de TI compartilhados que poderiam dar suporte a cada uma dessas soluções. No modelo de nuvem despesas operacionais, os custos podem ser atribuídos diretamente às necessidades de suporte de cargas de trabalho individuais, equipes ou unidades de negócios. Essa abordagem possibilita uma atribuição mais direta de custos ao cliente interno com suporte. Ao estimar os custos, é importante entender primeiro quanto desse novo recurso de contabilidade será usado pela equipe de ti.

Para quem deseja replicar a abordagem de despesas de capital herdada de contabilidade, use as saídas de qualquer abordagem sugerida na seção "[Tamanho da propriedade digital](#digital-estate-size)" acima para obter uma base de custo anual. Em seguida, multiplique esse custo anual pelo ciclo de atualização de hardware típico da empresa. O ciclo de atualização de hardware é a taxa na qual uma empresa substitui o hardware obsoleto, normalmente medido em anos. A taxa de execução anual multiplicada pelo ciclo de atualização de hardware cria uma estrutura de custo semelhante a um padrão de investimento de despesas de capital.

## <a name="next-steps"></a>Próximos passos

Após estimar custos, a migração pode começar. No entanto, seria prudente examinar as [opções de parceria e de suporte](./partnership-options.md) antes de iniciar qualquer migração.

> [!div class="nextstepaction"]
> [Noções básicas sobre opções de parceria](./partnership-options.md)
