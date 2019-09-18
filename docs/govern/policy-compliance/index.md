---
title: Preparar a política de TI corporativa para a nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação do conceito de política corporativa em relação à governança de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 99d207240e3783edf9b33ad208ae2c8ad13a7a7b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025772"
---
<!-- markdownlint-disable MD026 -->

# <a name="prepare-corporate-it-policy-for-the-cloud"></a>Preparar a política de TI corporativa para a nuvem

A governança de nuvem é o produto de um esforço de adoção contínua ao longo do tempo, como uma transformação verdadeira contínua que não acontece da noite para o dia. A tentativa de entregar a governança de nuvem completa antes de abordar as alterações de política corporativa de chave usando um método rápido agressivo raramente produz os resultados desejados. Em vez disso, é recomendável uma abordagem incremental.

O diferencial de nosso Cloud Adoption Framework é o ciclo de compra e como ele pode possibilitar uma transformação autêntica. Uma vez que não há uma necessidade de uma aquisição de despesas de capital grande, os engenheiros podem começar a experimentação e a adoção mais cedo. Em culturas mais corporativas, eliminar a barreira de despesa de capital para a adoção pode levar a loops de comentários mais rigorosos, crescimento orgânico e execução incremental.

A mudança para a adoção da nuvem exige uma mudança na governança. Em muitas organizações, a transformação de política corporativa permite governança aprimorada e taxas mais altas de conformidade por meio de alterações incrementais de política e a aplicação automática dessas alterações, alimentado por recursos definidos recentemente que você configurar com seu provedor de serviços de nuvem.

Este artigo descreve as principais atividades que podem ajudar você a moldar as políticas da empresa para habilitar um modelo de governança expandido.

## <a name="define-corporate-policy-to-mature-cloud-governance"></a>Defina a política corporativa para governança de nuvem madura

No controle tradicional e governança incremental, a política corporativa cria a definição de trabalho de governança. A maioria das ações de governança de TI busca implementar a tecnologia para monitorar, impor, operar e automatizar essas políticas corporativas. A governança de nuvem é criada em conceitos semelhantes.

![Governança corporativa e disciplinas de governança](../../_images/operational-transformation-govern-highres.png)

*Figura 1 – governança corporativa e disciplinas de governança.*

A imagem acima demonstra as interações entre o risco de negócios, política e conformidade e monitorar e impor para criar uma estratégia de governança. Seguido pelas Cinco Disciplinas de Governança de Nuvem para realizar sua estratégia.

## <a name="review-existing-policies"></a>Revisão das políticas existentes

Na imagem acima, a estratégia de governança (risco, política e conformidade, monitorar e impor) começa com o reconhecimento dos riscos de negócios. Noções básicas sobre como as alterações do [risco aos negócios](./business-risk.md) é a primeira etapa para criar uma estratégia de governança de nuvem duradoura. Trabalhar com as suas unidades de negócios para obter um medidor [preciso da tolerância empresarial quanto ao risco](./risk-tolerance.md) ajuda você a entender o nível dos riscos que precisam ser remediados. A compreensão dos novos riscos e a tolerância aceitável pode impulsionar uma [revisão de políticas existentes](./cloud-policy-review.md) para determinar o nível necessário de governança que apropriado para sua organização.

> [!TIP]
> Se sua organização é regida por conformidade de terceiros, um dos maiores riscos de negócios a considerar pode ser um risco da aderência a [conformidade regulatória](./regulatory-compliance.md). Esse risco geralmente não pode ser remediado e, em vez disso, pode exigir uma aderência estrita. Certifique-se de entender seus requisitos de conformidade de terceiros antes de iniciar uma revisão da política.

## <a name="an-incremental-approach-to-cloud-governance"></a>Uma abordagem incremental para a governança de nuvem

Uma abordagem incremental para a governança de nuvem pressupõe que é inaceitável para exceder a [tolerância de riscos da empresa](./risk-tolerance.md). Em vez disso, pressupõe que a função da governança é acelerar as mudanças empresariais, ajudar os engenheiros a entender as diretrizes de arquitetura e comunicar e remediar regularmente os [riscos empresariais](./business-risk.md). Como alternativa, a função tradicional de governança pode se tornar uma barreira para a adoção pelos engenheiros ou pela empresa como um todo.

Com uma abordagem incremental para governança de nuvem, às vezes, há um atrito natural entre as equipes de criação de novas soluções de negócios e proteger a empresa contra riscos. No entanto, neste modelo essas duas equipes podem se tornar pares trabalhando em incrementos ou sprints. Como colegas, a equipe de governança de nuvem e as equipes de adoção de nuvem começam a trabalhar juntar para expor, avaliar e remediar os riscos empresariais. Esse esforço pode criar uma maneira natural de reduzir o atrito e a criação de colaboração entre equipes.

## <a name="minimum-viable-product-mvp-for-policy"></a>Produto mínimo viável (MVP) para a política

A primeira etapa em uma parceria emergente entre suas equipes de governança e a adoção da nuvem é um acordo sobre a política de MVP. Seu MVP para governança de nuvem deve confirmar que os riscos de negócios são pequenos no início, mas provavelmente aumentarão conforme sua empresa adota mais serviço de nuvem ao longo do temp.

Por exemplo, o risco empresarial é pequeno para uma empresa que esteja implantando cinco VMs que não contenham nenhum dado de HBI (alto impacto empresarial). Mais adiante no processo de adoção de nuvem, quando o número atingir 1.000 VMs e a empresa estiver começando a mover dados de HBI, o risco empresarial aumentará.

O MVP de política tenta definir uma base necessária para as políticas exigidas para implantar as primeiras _x_ VMs ou os primeiros _x_ aplicativos, em que _x_ ainda é uma quantidade pequena, mas significativa, de unidades que estão sendo adotadas. Esse conjunto de políticas requer algumas restrições, mas poderá conter os aspectos fundamentais necessários para rapidamente passar de um esforço de adoção de nuvem incremental para o seguinte. Durante o desenvolvimento incremental de política, essa estratégia de governança tende a aumentar ao longo do tempo. Por meio de turnos sutis lentos, MVP de política tende a aumentar em paridade de recursos com as saídas do exercício de análise de política.

## <a name="incremental-policy-growth"></a>Crescimento incremental de política

O crescimento incremental da política é o mecanismo principal para aumentar cada vez mais a política e a governança de nuvem. Também é o principal requisito para a adoção de um modelo incremental para governança. Para este modelo funcionar bem, a equipe de governança deve ser confirmada para uma alocação em andamento de tempo em cada sprint, para avaliar e implementar a alteração das disciplinas de governança.

**Requisitos de tempo de Sprint:** No início de cada iteração, cada equipe de adoção da nuvem cria uma lista de ativos a serem migrados ou adotados no incremento atual. A equipe de governança de nuvem deve dar tempo suficiente para a revisão da lista, a validação das classificações de dados para ativos, a avaliação de quaisquer novos riscos associados a cada ativo, a atualização de diretrizes de arquitetura e o treinamento da equipe a respeito das alterações. Esses compromissos normalmente exigem 10 a 30 horas por sprint. Também é esperado para esse nível de envolvimento, exigir pelo menos um funcionário dedicado gerenciar o controle em um esforço de adoção de nuvem grande.

**Requisitos de tempo para o lançamento:** No início de cada lançamento, as equipes de adoção da nuvem e a equipe de estratégia de nuvem devem priorizar uma lista de aplicativos ou cargas de trabalho a serem migrados na iteração atual, juntamente com qualquer atividade de mudança comercial. Esses pontos de dados permitem que a equipe de governança de nuvem entenda os novos riscos de negócios antecipadamente. Isso permite o tempo para se alinhar aos negócios e medir a tolerância do negócio de riscos.

## <a name="next-steps"></a>Próximas etapas

Uma estratégia de governança de nuvem eficaz começa com o reconhecimento dos riscos comerciais.

> [!div class="nextstepaction"]
> [Compreender os riscos comerciais](./business-risk.md)
