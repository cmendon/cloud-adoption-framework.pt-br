---
title: Entender os riscos de negócios durante a migração na nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Entender os riscos de negócios durante a migração na nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 85ff0f9fa54542309a814fbca44c38de65805933
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752670"
---
<!-- markdownlint-disable MD026 -->

# <a name="understand-business-risk-during-cloud-migration"></a>Entender os riscos de negócios durante a migração na nuvem

Compreender os riscos empresariais é essencial para qualquer transformação de nuvem. O risco impulsiona a política e influencia os requisitos de monitoramento e imposição. O risco influencia profundamente a forma como gerenciamos a propriedade digital local ou na nuvem.

<!-- markdownlint-enable MD026 -->

## <a name="relativity-of-risk"></a>Relatividade do risco

O risco é relativo. Uma pequena empresa com poucos ativos de TI, em um prédio fechado, tem pouco risco. Adicionar usuários e uma conexão de internet com acesso a esses ativos, o risco é intensificado. Quando essa pequena empresa cresce para status de classificação Fortune 500, os riscos tornam-se exponencialmente maiores. Na medida em que as receitas, os processos de negócios, as contagens de funcionários e os ativos de TI se acumulam, os riscos aumentam e se aglutinam. Os ativos de TI que auxiliam na geração de receita correm riscos reais de interromper esse fluxo de receita em caso de uma interrupção. Cada momento de inatividade equivale a perdas. Da mesma forma, na medida em que os dados se acumulam, o risco de prejudicar os clientes aumenta.

No mundo local tradicional, as equipes de governança de ti se concentram na avaliação de riscos, na criação de processos para gerenciar esses riscos e na implantação de sistemas para garantir que as medidas de correção sejam implementadas com êxito. Esses esforços funcionam para balancear os riscos necessários para operar em um ambiente de negócios moderno e conectado.

## <a name="understand-business-risks-in-the-cloud"></a>Entenda os riscos de negócios na nuvem

Durante uma transformação, existem os mesmos riscos relativos.

- Durante a experimentação inicial, alguns ativos são implantados com pouco ou nenhum dado relevante. O risco é pequeno.
- Quando a primeira carga de trabalho é implementada, o risco aumenta um pouco. Esse risco é facilmente corrigido escolhendo um aplicativo inerentemente de baixo risco com uma pequena base de usuários.
- À medida que mais cargas de trabalho tornam-se online, os riscos alteram a cada liberação. Novos aplicativos são ativados e os riscos mudam.
- Quando uma empresa coloca os primeiros 10 a 20 aplicativos online, o perfil de risco é muito diferente quando o milésimo aplicativo entra em produção na nuvem.

Os ativos acumulados no imóvel local tradicional provavelmente se acumularam ao longo do tempo. A maturidade das equipes de negócios e de TI provavelmente estava crescendo de maneira semelhante. Esse crescimento paralelo pode tender a criar alguma bagagem política desnecessária.

Durante uma transformação de nuvem, ambas as equipes de negócios e TI terão a oportunidade de redefinir essas políticas e criar novas com um conhecimento avançado.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-a-business-risk-mvp"></a>O que é um MVP de risco empresarial?

Um **produto viável mínimo** é comumente usado para definir a menor unidade de algo que pode produzir um valor tangível. Em um MVP de risco de negócios, a equipe de governança de nuvem começa com a suposição de que alguns ativos serão implantados em um ambiente de nuvem em algum momento. É desconhecido o que esses ativos estão no momento, e a equipe pode não ter certeza de quais tipos de dados serão armazenados nesses ativos.

Ao planejar o risco para os negócios, a equipe de governança de nuvem poderia criar o pior cenário e mapear cada política possível para a nuvem. No entanto, identificar todos os riscos de negócios potenciais para todos os cenários de uso de nuvem pode levar muito tempo e esforço, atrasando potencialmente a implementação de governança para suas cargas de trabalho de nuvem. Isso não é recomendado, mas é uma opção.

Por outro lado, uma abordagem do MVP pode permitir que a equipe defina um ponto de partida inicial e um conjunto de suposições que seriam verdadeiras para a maioria/todos os ativos. Este MVP de risco de negócios oferecerá suporte a implantações de nuvem de teste ou de pequeno porte inicial e, em seguida, será usado como base para identificar gradualmente e corrigir novos riscos conforme as necessidades comerciais surgirem ou as cargas de trabalho adicionais serão adicionadas ao seu ambiente de nuvem. Esse processo permite que você aplique governança em todo o processo de adoção da nuvem.

A seguir estão alguns exemplos básicos de riscos de negócios que podem ser incluídos como parte de um MVP:

- Todos os ativos correm o risco de serem excluídos (por erro, engano ou manutenção).
- Todos os ativos correm o risco de gerar muito gastos.
- Todos os ativos podem ser comprometidos por senhas fracas ou configurações inseguras.
- Qualquer ativo com portas abertas expostas à Internet correm o risco de comprometimento.

Os exemplos acima servem para estabelecer os riscos empresariais de MVP como uma teoria. A lista atual será exclusiva para todos os ambientes.
Depois que o MVP de risco de negócios for estabelecido, ele poderá ser convertido em [políticas](./index.md) para corrigir cada risco.

<!-- markdownlint-enable MD026 -->

## <a name="incremental-risk-mitigation"></a>Mitigação de risco incremental

À medida que sua organização implanta mais cargas de trabalho na nuvem, as equipes de desenvolvimento farão uso de aumento de quantidades de recursos de nuvem. Em cada iteração, novos ativos são criados e preparados. Em cada liberação, as cargas de trabalho são preparadas para promoção de produção. Cada um desses ciclos tem o potencial de apresentar riscos de negócios não identificados anteriormente.

Supondo que um MVP de risco de negócios seja o ponto de partida para seus esforços iniciais de adoção de nuvem, a governança pode ser desenvolvida em paralelo com o uso crescente de recursos de nuvem. Quando a equipe de governança de nuvem opera em paralelo com as equipes de adoção de nuvem, o crescimento dos riscos de negócios pode ser resolvido conforme eles são identificados, fornecendo um modelo contínuo estável para o desenvolvimento de maturidade de governança.

Cada ativo preparado pode ser facilmente classificado de acordo com o risco. Os documentos de classificação de dados podem ser criados ou criados em paralelo com os ciclos de preparo. O perfil de risco e os pontos de exposição também podem ser documentados. Ao longo do tempo, uma visão extremamente clara do risco de negócios entrará em foco na organização.

Com cada iteração, a equipe de governança de nuvem pode trabalhar com a equipe de estratégia de nuvem para comunicar rapidamente novos riscos, estratégias de mitigação, compensações e custos potenciais. Isso possibilitará que os participantes de negócios e líderes de TI estabeleçam parcerias para tomadas de decisão consolidadas e atualizadas. Essas decisões transmitem a maturidade da política. Quando necessário, as alterações da política produzem novos itens de trabalho para a maturidade dos principais sistemas de infraestrutura. Quando alterações nos sistemas preparados forem necessárias, as equipes de adoção de nuvem terão tempo suficiente para fazer alterações, enquanto a empresa testa os sistemas preparados e desenvolve um plano de adoção do usuário.

Essa abordagem minimiza os riscos, enquanto capacita a equipe a agir rapidamente. Ele também garante que os riscos sejam endereçados e resolvidos imediatamente antes da implantação.

## <a name="next-steps"></a>Próximos passos

Saiba como avaliar a tolerância a riscos durante a adoção da nuvem.

> [!div class="nextstepaction"]
> [Avaliar tolerância de risco](./risk-tolerance.md)
