---
title: Motivações de Consistência de Recursos e os riscos de negócios
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivações de Consistência de Recursos e os riscos de negócios
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 42510f62cb3f673698832403126901789b05e978
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70826908"
---
# <a name="resource-consistency-motivations-and-business-risks"></a>Motivações de Consistência de Recursos e os riscos de negócios

Este artigo aborda os motivos que os clientes normalmente adotam uma disciplina de Consistência de Recursos dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios potenciais que podem conduzir as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="is-resource-consistency-relevant"></a>A Consistência de Recursos é relevante?

Quando se trata de implantação de recursos e cargas de trabalho, a nuvem oferece maior agilidade e flexibilidade em datacenters mais tradicionais no local. No entanto, essas vantagens potenciais baseadas em nuvem também são fornecidas emparelhadas com possíveis desvantagens de gerenciamento que possam prejudicar seriamente o sucesso da sua adoção da nuvem. Quais ativos você implantou? Quais equipes possuem quais ativos? Você tem recursos suficientes que dão suporte a uma carga de trabalho? Como saber se as cargas de trabalho estão íntegras?

A consistência de recursos é crucial para garantir que os recursos sejam implantados, atualizados e configurados de forma consistente de maneira repetitiva, e que as interrupções de serviço sejam minimizadas e remediadas no máximo tempo possível.

A disciplina de Consistência de Recursos está preocupada com a identificação e mitigação de riscos de negócios relacionados aos aspectos operacionais da sua implantação de nuvem. A Consistência de Recursos inclui monitoramento de aplicativos, cargas de trabalho e desempenho de ativos. Ele também inclui as tarefas necessárias para atender às demandas de escala, fornecer recursos de recuperação de desastres, mitigar violações de Contrato de Nível de Serviço de desempenho (SLA) e evitar proativamente essas violações de SLA por meio de correção automatizada.

Implantações de teste inicial podem não exigir muito além de adotar alguns padrões de nomenclatura e marcação para dar suporte às necessidades de Consistência de Recursos. À medida que sua adoção da nuvem amadurece e você implanta mais ativos críticos e complicados, a necessidade de investir na disciplina de consistência de recurso aumenta rapidamente.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de Consistência de Recursos tenta riscos de negócios operacionais de núcleo do endereço. Trabalhar com seus negócios e equipes de TI para identificar esses riscos e monitorar cada um deles para relevância como planejar e implementar suas implantações de nuvem.

Os riscos serão diferentes entre a organização, mas os seguintes servem como riscos comuns que você pode usar como ponto de partida para discussões em sua equipe de governança de nuvem:

- **Custo operacional desnecessário.** Recursos obsoletos ou não utilizados ou recursos que são sobreprovisionados durante horários de baixa demanda, adicione custos operacionais desnecessários.
- **Recursos subprovisionados.** Recursos que experimentam uma demanda maior que a antecipada podem resultar em interrupção dos negócios como recursos de nuvem sobrecarregados por demanda.
- **Ineficiências de gerenciamento.** Falta de nomenclatura consistente e metadados associados aos recursos de marcação pode levar a equipe de TI a ter dificuldades para localizar recursos para tarefas de gerenciamento ou de identificação de propriedade e informações de estatísticas relacionadas a ativos. Isso resulta em ineficiências de gerenciamento que podem aumentar o custo e a capacidade de resposta lenta da TI a interrupção do serviço ou outros problemas operacionais.
- **Interrupção dos negócios.** Interrupções de serviço que resultam em violações dos Contratos e Nível de Serviço (SLAs) estabelecidos da sua organização podem resultar em perda de negócios ou outros impactos financeiros a sua empresa.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Entenda os indicadores, métricas e tolerância a risco](./metrics-tolerance.md)
