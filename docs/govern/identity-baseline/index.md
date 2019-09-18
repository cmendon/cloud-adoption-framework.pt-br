---
title: Visão geral da disciplina de Linha de Base de Identidade
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação sobre o conceito de Linha de base de identidade em relação a governança de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 888e9e7381f5dba0dd2b3797bb4cc06e79a2c9b8
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025627"
---
# <a name="identity-baseline-discipline-overview"></a>Visão geral da disciplina de Linha de Base de Identidade

A Linha de Base de Identidade é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md) dentro do [modelo de governança da Cloud Adoption Framework](../index.md). A identidade cada vez mais é considerada o perímetro de segurança principal na nuvem, o que é uma mudança no enfoque tradicional de segurança de rede. Os serviços de identidade fornecem os mecanismos de núcleo que dão suporte a controle de acesso e organização em ambientes de TI e a disciplina de Linha de base de identidade complementa a [disciplina de Linha de base de segurança](../security-baseline/index.md) aplicando consistentemente requisitos de autenticação e autorização em esforços de adoção da nuvem.

> [!NOTE]
> A governança de Linha de Base de Identidade não substitui as equipes de TI, os processos e os procedimentos de TI existentes que a organização utiliza para proteger os recursos implantados na nuvem. O objetivo principal desta disciplina é identificar possíveis riscos de negócios relacionados à identidade e fornecer orientações de atenuação de risco para a equipe de TI que é responsável por implementar, manter e operar sua infraestrutura de gerenciamento de identidade. Ao desenvolver políticas e processos de governança, certifique-se de envolver equipes de TI pertinentes nos processos de planejamento e avaliação.

Esta seção da Cloud Adoption Framework descreve a abordagem ao desenvolvimento de uma disciplina de Linha de Base de Identidade como parte da estratégia de governança de nuvem. O principal público-alvo dessas diretrizes são os arquitetos de nuvem da organização e outros membros da equipe de governança de nuvem. No entanto, as decisões, políticas e os processos que surgem dessa disciplina devem envolver participação e discussões com membros relevantes das equipes de TI responsáveis pela implementação e gerenciamento das soluções de gerenciamento de identidade da sua organização.

Se a organização não tiver experiência interna em Linha de base de identidade e segurança, considere contratar consultores externos como parte dessa disciplina. Além disso, considere contratar os [Serviços de Consultoria Microsoft](https://www.microsoft.com/enterprise/services), o serviço de adoção de nuvem [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou outros especialistas externos em adoção de nuvem para discutir questões relacionadas a essa disciplina.

## <a name="policy-statements"></a>Declarações de políticas

As declarações de política acionáveis e os requisitos de arquitetura resultantes servem como base de uma disciplina de Linha de Base de Identidade. Para ver exemplos de declarações de políticas, consulte o artigo sobre [Declarações de políticas de Linha de Base de Identidade](./policy-statements.md). Esses exemplos podem servir como ponto de partida para as políticas de governança da sua organização.

> [!CAUTION]
> As políticas de exemplo são provenientes de experiências comuns do cliente. Para alinhar melhor essas políticas às necessidades específicas de governança de nuvem, execute as etapas a seguir para criar instruções de políticas que atendam às suas necessidades exclusivas de negócios.

## <a name="developing-identity-baseline-governance-policy-statements"></a>Desenvolver declarações de política de governança de Linha de Base de Identidade

As seis etapas a seguir oferecem exemplos e opções em potencial a serem consideradas ao desenvolver a governança de Linha de Base de Identidade. Use cada etapa como um ponto de partida para discussões com a equipe de governança de nuvem e com as equipes empresariais e de TI afetadas em sua organização para estabelecer as políticas e os processos necessários para gerenciar os riscos relacionados à identidade.

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
                        <h3>Modelo de Linha de base de identidade</h3>
                        <p class="x-hidden-focus">Baixe o modelo para documentar uma disciplina de Linha de Base de Identidade</p>
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
                        <p class="x-hidden-focus">Reconheça os motivos e riscos normalmente associados à disciplina de Linha de Base de Identidade.</p>
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
                        <p class="x-hidden-focus">Indicadores para reconhecer se é o momento certo para investir na disciplina de Linha de Base de Identidade.</p>
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
                        <p class="x-hidden-focus">Processos sugeridos para dar suporte à conformidade com políticas na disciplina Linha de Base de Identidade.</p>
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
                        <p class="x-hidden-focus">Os Serviços do Azure que podem ser implementados para dar suporte à disciplina de Linha de Base de Identidade.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Próximas etapas

Comece avaliando os [riscos dos negócios](./business-risks.md) em um ambiente específico.

> [!div class="nextstepaction"]
> [Reconheça os riscos comerciais](./business-risks.md)
