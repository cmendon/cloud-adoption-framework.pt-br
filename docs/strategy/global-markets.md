---
title: Entenda o impacto das decisões de mercado globais
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação do conceito de mercados globais
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 36f0d5ccf826746370054ed213b83968babdee6b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548629"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-will-global-market-decisions-affect-the-transformation-journey"></a>Como as decisões de mercado global afetarão a jornada de transformação?

A nuvem abre novas oportunidades para executar em uma escala global. As barreiras para as operações globais são significativamente reduzidas, permitindo que as empresas implantem ativos no mercado, sem a necessidade de investir pesadamente em novos data centers. Infelizmente, isso também acrescenta uma grande quantidade de complexidade de perspectivas técnicas e legais.

## <a name="data-sovereignty"></a>Soberania de dados

Muitas regiões geopolítica estabeleceram regulamentos da soberania de dados. Essas regulamentações restringem onde os dados podem ser armazenados, quais dados podem sair do país de origem e quais dados podem ser coletados sobre cidadãos dessa região. Antes de operar qualquer solução baseada em nuvem em uma geografia estrangeira, você deve entender como esse provedor de nuvem lida com a soberania de dados. Mais informações sobre a abordagem do Azure para cada geografia estão disponíveis [aqui](https://azure.microsoft.com/global-infrastructure/geographies). Para obter mais informações sobre conformidade no Azure, consulte [privacidade na Microsoft](https://www.microsoft.com/trustcenter/privacy) na central de confiabilidade da Microsoft.

O restante deste artigo pressupõe que o consultor jurídico tenha revisado e aprovado as operações em um país estrangeiro.

## <a name="business-units"></a>Unidades de negócios

É importante entender quais unidades de negócios operam em países estrangeiros e quais países são afetados. Essas informações serão usadas para criar soluções de hospedagem, cobrança e implantações para o provedor de nuvem.

## <a name="employee-usage-patterns"></a>Padrões de uso do funcionário

É importante entender como os usuários globais acessam aplicativos que não estão hospedados no mesmo país que o usuário. WANs (redes de longa distância) globais encaminham usuários com base em contratos de rede existentes. Em um mundo local tradicional, algumas restrições limitam o design de WAN. Essas restrições podem levar a uma experiência de usuário ruim se não forem compreendidas corretamente antes da adoção da nuvem.

Em um modelo de nuvem, a Internet de mercadoria abre muitas opções novas também. A comunicação da disseminação de funcionários em várias regiões geográficas pode ajudar a equipe de adoção da nuvem a criar soluções WAN que criam experiências de usuário positivas e reduzem os custos **de** rede.

## <a name="external-user-usage-patterns"></a>Padrões de uso de usuário externo

É igualmente importante entender os padrões de uso de usuários externos, como clientes ou parceiros. Assim como os padrões de uso de funcionários, os padrões de uso de usuários externos podem afetar negativamente o desempenho das implantações na nuvem. Quando uma base de usuários grande ou de missão crítica reside em um país estrangeiro, pode ser prudente incluir uma estratégia de implantação global no design da solução geral.

## <a name="next-steps"></a>Próximos passos

Depois que as decisões globais do mercado forem feitas e comunicadas, a equipe estará pronta para começar a [estabelecer padrões técnicos](../digital-estate/index.md) contra essas métricas.
O resultado será uma pendência de [transformação ou uma pendência de migração](..//migrate/migration-considerations/prerequisites/technical-complexity.md).

> [!div class="nextstepaction"]
> [Avaliar o espaço digital](../digital-estate/index.md)
