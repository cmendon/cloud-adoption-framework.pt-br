---
title: Governança na Microsoft Cloud Adoption Framework para o Azure
description: Aprenda sobre governança na Microsoft Cloud Adoption Framework para o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 60f1672f314c37dda35c19668f3df17b2c54f7db
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223701"
---
# <a name="governance-in-the-microsoft-cloud-adoption-framework-for-azure"></a>Governança na Microsoft Cloud Adoption Framework para o Azure

A nuvem cria paradigmas para as tecnologias que dão suporte empresarial. Esses novos paradigmas também mudam a maneira como essas tecnologias são adotadas, gerenciadas e controladas. Quando datacenters inteiros podem ser praticamente destruídos e recriados com uma linha de código executada por um processo autônomo, temos que repensar as abordagens tradicionais. Isso é especialmente verdadeiro para governança.

## <a name="get-started-with-cloud-governance"></a>Introdução à governança de nuvem

A governança de nuvem é um processo iterativo. Para organizações com políticas existentes que regem ambientes de TI locais, a governança de nuvem deve complementar essas políticas. No entanto, o nível de integração de política corporativa entre os locais e a nuvem variam de acordo com o amadurecimento da governança de nuvem e de uma propriedade digital na nuvem. À medida que o estado da nuvem se altera ao longo do tempo, o mesmo ocorrerá com os processos e as políticas de governança da nuvem. Os exercícios a seguir ajudam você a começar a criar sua base de governança inicial.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./methodology.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Metodologia</h3>
Estabeleça uma compreensão básica da metodologia que impulsiona a governança de nuvem no Cloud Adoption Framework para começar a refletir sobre a solução de estado final.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./benchmark.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Parâmetro de comparação</h3>
Avaliar o estado atual e o estado futuro para estabelecer uma visão para a aplicação da estrutura.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./initial-foundation.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Base de governança inicial</h3>
Comece sua jornada de governança com um conjunto de ferramentas de governança pequeno e implementado com facilidade. Essa base de governança inicial é chamada de MVP (produto mínimo viável).
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./foundation-improvements.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Melhorar a base de governança inicial</h3>
Em toda a implementação do plano de adoção da nuvem, adicione controles de governança iterativamente para abordar os riscos tangíveis conforme você avança rumo ao estado final.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="objective-of-this-content"></a>Objetivo deste conteúdo

As diretrizes nesta seção do Cloud Adoption Framework atendem a duas finalidades:

- Fornecer exemplos de guias de governança acionáveis que representam as experiências comuns normalmente encontradas pelos clientes. Cada exemplo apresenta riscos comerciais, políticas corporativas para mitigação de risco e diretrizes de design para implementar soluções técnicas. Por necessidade, as diretrizes de design são específicas para o Azure. O restante do conteúdo nesses guias pode ser aplicado em uma abordagem de várias nuvens ou independente de nuvem.
- Ajudar você a criar soluções de governança personalizadas que atendam a uma variedade de necessidades comerciais. Essas necessidades incluem a governança de várias nuvens públicas por meio de orientações detalhadas sobre o desenvolvimento de políticas, processos e ferramentas corporativas.

Este conteúdo destina-se para uso pela equipe de governança de nuvem. Também é relevante para os arquitetos de nuvem que precisam desenvolver uma base sólida de governança de nuvem.

## <a name="intended-audience"></a>Público-alvo

O conteúdo na Cloud Adoption Framework afeta os negócios, a tecnologia e a cultura das empresas. Esta seção da Cloud Adoption Framework interage intensamente com as equipes de segurança de TI, governança de TI, finanças, líderes de linha de negócios, rede, identidade e adoção de nuvem. Várias dependências desse pessoal exigem uma abordagem facilitadora por parte dos arquitetos de nuvem que usam essa diretriz. A facilitação com essas equipes pode ser um esforço único. Em alguns casos, interações com essas outras pessoas serão contínuas.

O arquiteto de nuvem serve como o líder de ideias e facilitador para reunir esses públicos. O conteúdo nesta coleção de guias foi projetado para ajudar o arquiteto de nuvem a facilitar a conversa certa, com o público correto, para orientar decisões necessárias. A transformação empresarial capacitada pela nuvem depende do arquiteto de nuvem para ajudar a guiar as decisões em toda a empresa e na TI.

**Especialização de arquiteto de nuvem nesta seção:** Cada seção da Cloud Adoption Framework representa especialização ou variante diferente da função de arquiteto de nuvem. Esta seção da Cloud Adoption Framework foi projetada para arquitetos de nuvem aficionados por mitigar ou reduzir os riscos técnicos. Alguns provedores de nuvem referem-se a esses especialistas como *custodiantes da nuvem*, mas nós preferimos *guardiões de nuvem* ou, coletivamente, a *equipe de governança de nuvem*. Em cada guia de governança acionável, os artigos mostram como a composição e a função da equipe de governança de nuvem podem ser alteradas ao longo do tempo.

## <a name="use-this-guide"></a>Use este guia

Se você quiser seguir este guia do início ao fim, este conteúdo ajudará a desenvolver uma estratégia de governança de nuvem robusta em paralelo à implementação de nuvem. A diretriz orienta você na teoria e implementação de uma estratégia.

Para um curso intensivo sobre a teoria e um acesso rápido à implementação do Azure, comece com a [visão geral de guias de governança](./guides/index.md). Usando este guia, você pode começar pequeno e melhorar iterativamente suas necessidades de governança em paralelo aos seus esforços de adoção de nuvem.

## <a name="next-steps"></a>Próximas etapas

Estabeleça uma compreensão básica da metodologia que impulsiona a governança de nuvem no Cloud Adoption Framework.

> [!div class="nextstepaction"]
> [Entender a metodologia](./methodology.md)
