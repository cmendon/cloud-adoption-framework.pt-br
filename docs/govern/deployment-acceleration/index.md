---
title: Visão geral da disciplina de Aceleração de implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação de Implantação de aceleração em relação a governança de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: f96ada5b1c43694d0ea1af10524f3c344db62356
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222716"
---
# <a name="deployment-acceleration-discipline-overview"></a>Visão geral da disciplina de Aceleração de implantação

A Aceleração da Implantação é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md) dentro do [modelo de governança da Cloud Adoption Framework](../index.md). Esta disciplina se concentra em maneiras de estabelecer políticas para controlar a configuração de ativos ou implantação. Dentro das Cinco Disciplinas de Governança de Nuvem, a Aceleração da Implantação inclui implantação, alinhamento de configuração e capacidade de reutilização de script. Isso pode ocorrer por meio de atividades manuais ou atividades de DevOps totalmente automatizadas. Em ambos os casos, as políticas permanecerão basicamente as mesmas. À medida que esta disciplina amadurece, a equipe de governança de nuvem pode servir como uma parceira em estratégias de implantação e DevOps acelerando as implantações e removendo as barreiras à adoção de nuvem por meio da aplicação de ativos reutilizáveis.

Este artigo descreve o processo de Implantação de aceleração que passa por uma empresa durante o planejamento, criação, adoção e fases operacionais de implementação de uma solução de nuvem. É impossível para qualquer pessoa documentar os requisitos a serem levados em consideração de todas as empresas. Dessa forma, cada seção deste artigo descreve atividades mínimas sugeridas e potenciais. O objetivo inicial dessas atividades é ajudar a criar uma [política MVP](../policy-compliance/index.md#minimum-viable-product-mvp-for-policy) e estabelecer uma estrutura para a melhoria da [Política Incremental](../policy-compliance/index.md#incremental-policy-growth). A equipe de governança de nuvem deve decidir quanto investir nessas atividades para melhorar a posição de Aceleração de Implantação.

> [!NOTE]
> A disciplina de Aceleração de implantação não substitui as equipes de TI existentes, processos e procedimentos que permitem que sua organização implante com eficiência os recursos baseados em nuvem. O principal objetivo dessa disciplina é identificar riscos de negócios relacionados à segurança e fornecer diretrizes de mitigação de risco à equipe de TI responsável pela infraestrutura de segurança. Ao desenvolver políticas e processos de governança, certifique-se de envolver equipes de TI pertinentes nos processos de planejamento e avaliação.

O principal público-alvo dessas diretrizes são os arquitetos de nuvem da organização e outros membros da equipe de governança de nuvem. No entanto, as decisões, políticas e os processos que surgem dessa disciplina devem envolver participação e discussões com membros relevantes das equipes de TI e segurança, especialmente os líderes responsáveis por implantar e configurar as cargas de trabalho baseadas em nuvem.

## <a name="policy-statements"></a>Declarações de políticas

As declarações de política acionáveis e os requisitos de arquitetura resultantes servem como base de uma disciplina de Aceleração de implantação. Para ver exemplos de declarações de políticas, consulte o artigo sobre as [Declarações de Política de Aceleração de Implantação](./policy-statements.md). Esses exemplos podem servir como ponto de partida para as políticas de governança da sua organização.

> [!CAUTION]
> As políticas de exemplo são provenientes de experiências comuns do cliente. Para alinhar melhor essas políticas às necessidades específicas de governança de nuvem, execute as etapas a seguir para criar instruções de políticas que atendam às suas necessidades exclusivas de negócios.

## <a name="developing-deployment-acceleration-governance-policy-statements"></a>Desenvolvimento de instruções de políticas de governança de Aceleração de implantação

As seis etapas a seguir ajudarão você a definir políticas de governança para controlar a implantação e configuração de recursos em seu ambiente de nuvem.

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
                        <h3>Modelo de Aceleração de implantação</h3>
                        <p class="x-hidden-focus">Baixar o modelo para documentar uma disciplina de Aceleração de Implantação</p>
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
                        <p class="x-hidden-focus">Reconheça os motivos e riscos normalmente associados à disciplina de Aceleração de Implantação.</p>
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
                        <p class="x-hidden-focus">Indicadores para reconhecer se é o momento certo para investir na disciplina de Aceleração de Implantação.</p>
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
                        <p class="x-hidden-focus">Processos sugeridos para dar suporte à conformidade da política na disciplina de Aceleração de Implantação.</p>
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
                        <p class="x-hidden-focus">Os Serviços do Azure que podem ser implementados para dar suporte à disciplina de Aceleração de implantação.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

## <a name="next-steps"></a>Próximas etapas

Comece avaliando os [riscos dos negócios](./business-risks.md) em um ambiente específico.

> [!div class="nextstepaction"]
> [Reconheça os riscos comerciais](./business-risks.md)

<!-- markdownlint-enable MD033 -->
