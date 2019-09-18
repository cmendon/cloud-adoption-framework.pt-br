---
title: Visão geral da disciplina de Gerenciamento de Custos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação sobre o Gerenciamento de Custos em relação a governança de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d7f44027bdc7b2b17dc60dd070092b266609188c
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025773"
---
# <a name="cost-management-discipline-overview"></a>Visão geral da disciplina de Gerenciamento de Custos

O Gerenciamento de Custos é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md) dentro do [modelo de governança da Cloud Adoption Framework](../index.md). Para muitos clientes, o custo regente é uma preocupação importante ao adotar tecnologias de nuvem. Balancear as demandas de desempenho, o ritmo de adoção e os custos dos serviços de nuvem pode ser um desafio. Isso é especialmente relevante durante as transformações de negócios importantes que implementam as tecnologias de nuvem. Esta seção descreve a abordagem para o desenvolvimento de uma disciplina de Gerenciamento de Custos como parte da estratégia de governança de nuvem.

> [!NOTE]
> Governança de Gerenciamento de Custos não substitui as equipes de negócios, práticas de contabilidade e procedimentos que estão envolvidos no gerenciamento financeiro da sua organização dos custos relacionados a TI. A principal finalidade dessa disciplina é identificar possíveis riscos relacionados à nuvem relativos aos gastos de TI e fornecer orientações de mitigação de risco para as equipes empresariais e de TI responsáveis por implantar e gerenciar recursos de nuvem.

O principal público-alvo dessas diretrizes são os arquitetos de nuvem da organização e outros membros da equipe de governança de nuvem. No entanto, as decisões, políticas e os processos que surgem dessa disciplina devem envolver participação e discussões com membros relevantes das equipes de TI e segurança, especialmente os líderes responsáveis pela propriedade, gerenciamento e pagamento das cargas de trabalho baseadas em nuvem.

## <a name="policy-statements"></a>Declarações de políticas

As declarações de política acionáveis e os requisitos de arquitetura resultantes servem como base de uma disciplina de Gerenciamento de Custos. Para ver exemplos de declarações de políticas, consulte o artigo sobre as [Declarações de Gerenciamento de Custos](./policy-statements.md). Esses exemplos podem servir como ponto de partida para as políticas de governança da sua organização.

> [!CAUTION]
> As políticas de exemplo são provenientes de experiências comuns do cliente. Para alinhar melhor essas políticas às necessidades específicas de governança de nuvem, execute as etapas a seguir para criar instruções de políticas que atendam às suas necessidades exclusivas de negócios.

## <a name="developing-cost-management-governance-policy-statements"></a>Instruções da política de controle de Gerenciamento de Custos de desenvolvimento

As seis etapas a seguir ajudarão você a definir as políticas de governança para controlar os custos em seu ambiente.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsE">
<li style="display: flex; flex-direction: column;">
    <a href="./template.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-template.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Modelo de Gerenciamento de Custos</h3>
                        <p class="x-hidden-focus">Baixe o modelo para documentar uma disciplina de Gerenciamento de Custos</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li><li style="display: flex; flex-direction: column;">
    <a href="./business-risks.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-risks.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Riscos dos negócios</h3>
                        <p class="x-hidden-focus">Reconheça os motivos e riscos normalmente associados à disciplina de Gerenciamento de Custos.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./metrics-tolerance.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-metrics.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Indicadores e Métricas</h3>
                        <p class="x-hidden-focus">Indicadores para reconhecer se é o momento certo para investir na disciplina de Gerenciamento de Custos.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./compliance-processes.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-enforce.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Processos de conformidade de política</h3>
                        <p class="x-hidden-focus">Processos sugeridos para dar suporte à conformidade da política na disciplina de Gerenciamento de Custos.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./discipline-improvement.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-maturity.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Maturidade</h3>
                        <p class="x-hidden-focus">Alinhar a maturidade do Gerenciamento de Nuvem com as fases de adoção de nuvem.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./toolchain.md">
        <div class="cardSize">
            <div class="cardPadding" >
                <div class="card" >
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../../_images/govern/process-toolchain.png" class="x-hidden-focus"/>
                        </div>
                    </div>
                    <div class="cardText" style="padding-left:0px;">
                        <h3>Cadeia de ferramentas</h3>
                        <p class="x-hidden-focus">Os Serviços do Azure que podem ser implementados para dar suporte à disciplina de Gerenciamento de custos.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Próximas etapas

Comece avaliando os riscos dos negócios em um ambiente específico.

> [!div class="nextstepaction"]
> [Reconheça os riscos comerciais](./business-risks.md)

<!-- markdownlint-enable MD033 -->
