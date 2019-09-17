---
title: Estabelecer uma base de governança de nuvem inicial
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comece a usar a governança de nuvem estabelecendo uma base de governança de nuvem inicial.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 3e1f2c1b54a55a740376ba1d1c45c13dc9e7e26d
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029116"
---
# <a name="establish-an-initial-cloud-governance-foundation"></a>Estabelecer uma base de governança de nuvem inicial

O estabelecimento da governança de nuvem é um esforço iterativo amplo. É desafiador ter um equilíbrio eficaz entre velocidade e controle, especialmente durante as primeiras fases da adoção da nuvem. As diretrizes de governança na estrutura de adoção de nuvem ajudam a fornecer esse equilíbrio por meio de uma abordagem ágil para a adoção.

Este artigo fornece duas opções para estabelecer uma base inicial para governança. Qualquer opção garante que as restrições de governança possam ser dimensionadas e expandidas conforme o plano de adoção é implementado e os requisitos se tornam mais claramente definidos. Por padrão, a base inicial pressupõe uma posição isolar e controlar. Ele também se concentra mais na organização de recursos do que na governança de recursos. Esse ponto de partida leve é chamado de _MVP (produto viável) mínimo_ para governança. O objetivo do MVP é reduzir as barreiras para estabelecer uma posição de governança inicial e, em seguida, habilitar o desenvolvimento rápido da solução para lidar com uma variedade de riscos tangíveis.

## <a name="already-using-the-cloud-adoption-framework"></a>Já está usando a estrutura de adoção de nuvem

Se você esteve acompanhando a estrutura de adoção de nuvem, talvez já tenha implantado um MVP de governança. A orientação é um aspecto principal de qualquer modelo operacional. Ele está presente durante cada fase do ciclo de vida de adoção da nuvem. Dessa forma, a [estrutura de adoção de nuvem](../index.md) fornece diretrizes que injetam governança em atividades relacionadas à implementação do seu [plano de adoção de nuvem](../plan/index.md). Um exemplo dessa integração de governança é usar plantas para implantar uma ou mais zonas de chegada presentes nas diretrizes [prontas](../ready/index.md) . Outro exemplo é a orientação para [expandir assinaturas](../ready/considerations/scaling-subscriptions.md). Se você seguiu uma dessas recomendações, as seguintes seções do MVP são simplesmente uma análise das decisões de implantação existentes. Após uma revisão rápida, vá à frente para [a solução de governança inicial e aplique os controles de práticas recomendadas](./foundation-improvements.md).

## <a name="establish-an-initial-governance-foundation"></a>Estabelecer uma base de governança inicial

A seguir estão dois exemplos diferentes de fundamentos de governança iniciais (também chamados de MVPs de governança) para aplicar uma base de som para governança a implantações novas ou existentes. Escolha o MVP que melhor se alinha às suas necessidades de negócios para começar:

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./guides/standard/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guia de governança padrão</h3>
                        <p>Um guia para a maioria das organizações com base no modelo recomendado de duas assinaturas, projetado para implantações em várias regiões, mas que não abrange nuvens públicas e soberanas/governamentais.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./guides/complex/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guia de governança para empresas complexas</h3>
                        <p>Um guia para empresas que são gerenciadas por várias unidades de negócios independentes de TI ou que abrangem nuvens públicas e soberanas/governamentais.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Próximas etapas

Quando uma base de governança estiver em vigor, aplique recomendações adequadas para melhorar a solução e proteger contra riscos tangíveis.

> [!div class="nextstepaction"]
> [Melhorar a base de governança inicial](./foundation-improvements.md)
