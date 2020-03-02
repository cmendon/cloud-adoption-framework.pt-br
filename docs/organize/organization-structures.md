---
title: Estabelecer estruturas de equipe
description: Use esses exemplos de estruturas de equipe comuns para encontrar a estrutura organizacional que melhor se alinha às suas necessidades operacionais.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/27/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 0aeaa665370c612e89a0d4ce72a2b38b2bb05e2b
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222219"
---
<!-- cSpell:ignore ccoe -->

# <a name="establish-team-structures"></a>Estabelecer estruturas de equipe

Cada recurso de nuvem é fornecido por alguém durante cada esforço de adoção da nuvem. Essas atribuições e estruturas de equipe podem ser desenvolvidas de forma orgânica ou podem ser intencionalmente projetadas para corresponder a uma estrutura de equipe definida.

Conforme as necessidades de adoção crescem, a necessidade de balancear e estrutura. Este artigo fornece exemplos de estruturas de equipe comuns em vários estágios de maturidade organizacional. O gráfico e a lista a seguir descrevem essas estruturas com base em estágios de desenvolvimento típicos. Use estes exemplos para encontrar a estrutura organizacional que melhor se alinha às suas necessidades operacionais.

![Ciclo de maturidade organizacional](../_images/ready/org-ready-maturity.png)

As estruturas organizacionais tendem a passar pelo modelo de maturidade comum descrito aqui:

1. [Somente equipe de adoção de nuvem](#cloud-adoption-team-only)
2. [Prática recomendada do MVP](#best-practice-minimum-viable-product-mvp)
3. [TI central](#central-it)
4. [Alinhamento estratégico](#strategic-alignment)
5. [Alinhamento operacional](#operational-alignment)
6. [Cloud Center of Excellence (CCoE)](#cloud-center-of-excellence)

A maioria das empresas começa com pouco mais do que uma *equipe de adoção de nuvem*. No entanto, recomendamos que você estabeleça uma estrutura organizacional que seja mais parecida com a estrutura de práticas [recomendadas do MVP](#best-practice-minimum-viable-product-mvp) .

## <a name="cloud-adoption-team-only"></a>Somente equipe de adoção de nuvem

A núcleo de todos os esforços de adoção de nuvem é a equipe de adoção de nuvem. Essa equipe orienta as alterações técnicas que permitem a adoção. Dependendo dos objetivos do esforço de adoção, essa equipe pode incluir uma variedade diversificada de membros da equipe que lidam com um amplo conjunto de tarefas técnicas e de negócios.

![Equipe de adoção de nuvem, com equipes de governança e segurança](../_images/ready/org-ready-adoption-only.png)

Para iniciativas de pequena escala ou de adoção de estágio inicial, essa equipe pode ser tão pequena quanto uma pessoa. Em esforços de maior escala ou de estágio posterior, é comum ter várias equipes de adoção de nuvem, cada uma com cerca de seis engenheiros. Independentemente do tamanho ou das tarefas, o aspecto consistente de qualquer equipe de adoção de nuvem é que ele fornece os meios para a integração de soluções na nuvem. Para algumas organizações, essa pode ser uma estrutura organizacional suficiente. O artigo da [equipe de adoção de nuvem](./cloud-adoption.md) fornece mais informações sobre a estrutura, a composição e a função da equipe de adoção da nuvem.

> [!WARNING]
> Operar com *apenas* uma equipe de adoção de nuvem (ou várias equipes de adoção de nuvem) é considerado um *antipadrão* e deve ser evitado. No mínimo, considere a [prática recomendada do MVP](#best-practice-minimum-viable-product-mvp).

## <a name="best-practice-minimum-viable-product-mvp"></a>Prática recomendada: produto (MVP) mínimo viável

É recomendável que você tenha duas equipes para criar um equilíbrio entre os esforços de adoção da nuvem. Essas duas equipes são responsáveis por vários recursos em todo o esforço de adoção.

- **Equipe de adoção de nuvem:** Essa equipe é protinada a soluções técnicas, alinhamento de negócios, gerenciamento de projetos e operações para soluções que são adotadas.
- **Equipe de governança de nuvem:** Para balancear a equipe de adoção da nuvem, uma equipe de governança de nuvem é dedicada a garantir a excelência nas soluções que são adotadas. A equipe de governança de nuvem é proficada para maturidade de plataforma, operações de plataforma, governança e automação.

![Adoção de nuvem com counterbalance de governança de nuvem](../_images/ready/org-ready-best-practice.png)

Essa abordagem comprovada é considerada um MVP porque pode não ser sustentável. Cada equipe está gastando muitas funções, conforme descrito nos [gráficos *responsável, responsáveis, consultados e informados* (RACI)](./raci-alignment.md).

As seções a seguir descrevem uma estrutura organizacional comprovada e totalmente equipada, juntamente com abordagens para alinhar a estrutura apropriada à sua organização.

## <a name="central-it"></a>TI central

À medida que a adoção é dimensionada, a equipe de governança de nuvem pode se esforçar para acompanhar o fluxo de inovação de várias equipes de adoção de nuvem. Isso é especialmente verdadeiro em ambientes que têm requisitos pesados de conformidade, operações ou segurança. Nesse estágio, é comum que as empresas mudem as responsabilidades da nuvem para uma equipe de ti central existente. Se essa equipe puder reavaliar as ferramentas, os processos e as pessoas para dar melhor suporte à adoção na nuvem em grande escala, a inclusão da equipe central de ti poderá adicionar um valor significativo. Trazendo especialistas no assunto de operações, automação, segurança e administração para modernizar a ti central pode gerar inovações operacionais eficazes.

![Adoção de nuvem com um modelo de ti central](../_images/ready/org-ready-central-it.png)

Infelizmente, a fase de ti central pode ser uma das fases difusos da maturidade organizacional. A equipe central de ti deve chegar à tabela com uma grande mentalidade de crescimento. Se a equipe exibir a nuvem como uma oportunidade de aumentar e adaptar seus recursos, ela poderá fornecer um ótimo valor durante todo o processo. No entanto, se a equipe de ti central exibir a adoção de nuvem principalmente como uma ameaça ao modelo existente, a equipe de ti central se tornará um obstáculo para as equipes de adoção de nuvem e os objetivos de negócios aos quais eles dão suporte. Algumas equipes de ti centrais gastaram meses ou até anos tentando forçar a nuvem a se alinhar com abordagens locais, com apenas resultados negativos. A nuvem não exige que tudo seja alterado na ti central, mas requer alteração. Se a resistência à alteração for predominante na equipe central de ti, essa fase de maturidade poderá rapidamente se tornar um antipadrão cultural.

Os planos de adoção de nuvem altamente concentrados em PaaS (plataforma como serviço), DevOps ou outras soluções que exigem menos suporte a operações têm menos probabilidade de ver o valor durante essa fase de maturidade. Por contrário, esses tipos de soluções são os mais prováveis de serem prejudicados ou bloqueados por tentativas de centralizá-lo. Um nível mais alto de maturidade, como uma [CCOE (Cloud Center of Excellence)](#cloud-center-of-excellence), tem mais probabilidade de gerar resultados positivos para esses tipos de esforços de transformação. Para entender as diferenças entre a ti central na nuvem e um CCoE, consulte [Cloud Center of Excellence](./cloud-center-of-excellence.md).

## <a name="strategic-alignment"></a>Alinhamento estratégico

À medida que o investimento na adoção da nuvem cresce e os valores de negócios são percebidos, os participantes comerciais geralmente se tornam mais envolvidos. Uma equipe de estratégia de nuvem definida, como ilustra a imagem a seguir, alinha esses participantes comerciais para maximizar o valor realizado pelos investimentos de adoção da nuvem.

![Adicionar uma equipe de estratégia de nuvem definida](../_images/ready/org-ready-strategy-aligned.png)

Quando a maturidade acontece de forma orgânica, como resultado dos esforços de adoção de nuvem orientados por ti, o alinhamento estratégico é geralmente precedido por uma equipe de governança ou central de ti. Quando os esforços de adoção da nuvem são liderados pela empresa, o foco no modelo operacional e na organização tende a acontecer antes. Sempre que possível, os resultados de negócios e a equipe de estratégia de nuvem devem ser definidos no início do processo.

## <a name="operational-alignment"></a>Alinhamento operacional

A obtenção de valor comercial de esforços de adoção de nuvem exige operações estáveis. As operações na nuvem podem exigir novas ferramentas, processos ou habilidades. Quando são necessárias operações de ti estáveis para alcançar resultados comerciais, é importante adicionar uma equipe de operações de nuvem definida, como mostrado aqui.

![Adicionar uma equipe de operações de nuvem definida](../_images/ready/org-ready-operations-aligned.png)

As operações de nuvem podem ser entregues pelas funções de operações de ti existentes. Mas não é incomum que as operações de nuvem sejam delegadas a outras partes fora das operações de ti. Provedores de serviços gerenciados, equipes DevOps e unidade de negócios geralmente assumem as responsabilidades associadas às operações de nuvem, com suporte e guardrails fornecidos pelas operações de ti. Isso é cada vez mais comum para os esforços de adoção de nuvem que se concentram fortemente em implantações DevOps ou PaaS.

## <a name="cloud-center-of-excellence"></a>Centro de excelência de nuvem

No mais alto estado de maturidade, um centro de excelência em nuvem alinha as equipes em um modelo operacional moderno de nuvem primeiro. Essa abordagem fornece funções de ti central como governança, segurança, plataforma e automação.

![Centro de excelência de nuvem](../_images/ready/org-ready-ccoe.png)

A principal diferença entre essa estrutura e a estrutura central de ti acima é um foco no autoatendimento. As equipes nessa estrutura se organizam com a intenção de delegar o controle o máximo possível. Alinhar práticas de governança e conformidade a soluções nativas de nuvem cria guardrails e mecanismos de proteção. Ao contrário do modelo de ti central, a abordagem nativa de nuvem maximiza a inovação e minimiza a sobrecarga operacional. Para que esse modelo seja adotado, o contrato mútuo para modernizar os processos de ti será exigido da liderança de ti e de negócios. Esse modelo é improvável de ocorrer de orgânica e geralmente requer suporte executivo.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Depois de alinhar a um determinado estágio da maturidade da estrutura organizacional, você pode usar [gráficos do RACI](./raci-alignment.md) para alinhar a responsabilidade e a responsabilidade em cada equipe.

> [!div class="nextstepaction"]
> [Alinhar o gráfico RACI apropriado](./raci-alignment.md)
