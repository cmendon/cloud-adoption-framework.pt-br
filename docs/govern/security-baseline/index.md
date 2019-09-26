---
title: Visão geral da disciplina de Linha de Base de Segurança
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Visão geral da disciplina de Linha de Base de Segurança
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 1338fb14ed39915dc9e55c855dd5bbf00ba7a6eb
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221757"
---
# <a name="security-baseline-discipline-overview"></a>Visão geral da disciplina de Linha de Base de Segurança

A Linha de Base de Segurança é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md) dentro do [modelo de governança da Cloud Adoption Framework](../index.md). A segurança é um componente de qualquer implantação de TI, e a nuvem apresenta preocupações de segurança exclusivas. Muitas empresas estão sujeitas a requisitos regulamentares que tornam a proteção de dados confidenciais uma importante prioridade organizacional ao considerar uma transformação em nuvem. A identificação de possíveis ameaças à segurança no ambiente de nuvem e o estabelecimento de processos e procedimentos para lidar com essas ameaças devem ser uma prioridade para qualquer equipe de segurança de TI ou de segurança cibernética. A disciplina de Linha de Base de Segurança garante que os requisitos técnicos e as restrições de segurança sejam aplicados sistematicamente a ambientes de nuvem conforme esses requisitos amadurecem.

> [!NOTE]
> A governança de Linha de Base de Segurança não substitui as equipes, os processos e os procedimentos de TI existentes que a organização utiliza para proteger os recursos implantados na nuvem. O principal objetivo dessa disciplina é identificar riscos de negócios relacionados com a segurança e fornecer diretrizes de mitigação de risco à equipe de TI responsável pela infraestrutura de segurança. Ao desenvolver políticas e processos de governança, certifique-se de envolver equipes de TI pertinentes nos processos de planejamento e avaliação.

Este artigo descreve a abordagem para o desenvolvimento de uma disciplina de Linha de Base de Segurança como parte da estratégia de governança de nuvem. O principal público-alvo dessas diretrizes são os arquitetos de nuvem da organização e outros membros da equipe de governança de nuvem. No entanto, as decisões, políticas e os processos que surgem dessa disciplina devem envolver participação e discussões com membros relevantes das equipes de TI e segurança, especialmente os líderes técnicos responsáveis pela implementação de serviços de identidade, criptografia e rede.

Tomar as decisões corretas relacionadas à segurança é fundamental para o êxito das implantações de nuvem e maior sucesso dos negócios. Se a organização não tiver experiência interna em segurança cibernética, considere contratar consultores externos de segurança como um componente dessa disciplina. Além disso, considere contratar os [Serviços de Consultoria Microsoft](https://www.microsoft.com/enterprise/services), o serviço de adoção de nuvem [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou outros especialistas externos em adoção de nuvem para discutir questões relacionadas a essa disciplina.

## <a name="policy-statements"></a>Declarações de políticas

As declarações de política acionáveis e os requisitos de arquitetura resultantes servem como base de uma disciplina de Linha de Base de Segurança. Para ver exemplos de declarações de políticas, consulte o artigo sobre [Declarações de políticas de Linha de Base de Segurança](./policy-statements.md). Esses exemplos podem servir como ponto de partida para as políticas de governança da organização.

> [!CAUTION]
> As políticas de exemplo são provenientes de experiências comuns do cliente. Para alinhar melhor essas políticas às necessidades específicas de governança de nuvem, execute as etapas a seguir para criar instruções de políticas que atendam às suas necessidades exclusivas de negócios.

## <a name="developing-security-baseline-governance-policy-statements"></a>Desenvolver declarações de política de governança de Linha de Base de Segurança

As seis etapas a seguir oferecem exemplos e opções em potencial a serem consideradas ao desenvolver a governança de Linha de Base de Segurança. Use cada etapa como um ponto de partida para discussões com a equipe de governança de nuvem e com as equipes de negócios, TI e segurança afetadas em toda a organização para estabelecer as políticas e os processos necessários para gerenciar os riscos relacionados à segurança.

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
                        <h3>Modelo de Linha de Base de Segurança</h3>
                        <p class="x-hidden-focus">Baixar o modelo para documentar uma disciplina de Linha de Base de Segurança</p>
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
                        <p class="x-hidden-focus">Reconhecer os motivos e riscos normalmente associados à disciplina de Linha de Base de Segurança.</p>
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
                        <p class="x-hidden-focus">Indicadores para reconhecer se é o momento certo para investir na disciplina de Linha de Base de Segurança.</p>
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
                        <p class="x-hidden-focus">Processos sugeridos para dar suporte à conformidade com políticas na disciplina Linha de Base de Segurança.</p>
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
                        <p class="x-hidden-focus">Os serviços do Azure que podem ser implementados para dar suporte à disciplina de Linha de Base de Segurança.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Próximas etapas

Comece avaliando os riscos dos negócios em um ambiente específico.

> [!div class="nextstepaction"]
> [Reconheça os riscos comerciais](./business-risks.md)
