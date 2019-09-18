---
title: Visão geral da disciplina de Consistência de recursos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Visão geral da disciplina de Consistência de recursos
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 652405257f50b0ee5f1edb5d634c999feeecf72e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026308"
---
# <a name="resource-consistency-discipline-overview"></a>Visão geral da disciplina de Consistência de recursos

A Consistência de Recursos é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md) dentro do [modelo de governança da Cloud Adoption Framework](../index.md). Essa disciplina se concentra em formas de estabelecer políticas relacionadas à gestão operacional de um ambiente, aplicativo ou carga de trabalho. As equipes de operações de TI geralmente fornecem monitoramento de aplicativos, carga de trabalho e desempenho de ativos. Ela também normalmente executam as tarefas necessárias para atender às demandas de dimensionamento, corrigir violações do Contrato de Nível de Serviço (SLA) e evitam proativamente as violações de SLA através da correção automatizada. Dentro das Cinco Disciplinas de Governança de Nuvem, a Consistência de Recursos é uma disciplina que garante que os recursos sejam consistentemente configurados de modo que possam ser detectáveis por operações de TI, estejam incluídos em soluções de recuperação e possam ser integrados a processos de operações repetíveis.

> [!NOTE]
> A governança de consistência de recursos não substitui existente as equipes TI existentes, processos e procedimentos que permitem que sua organização gerencie com eficiência os recursos baseados em nuvem. O principal objetivo dessa disciplina é identificar riscos de negócios relacionados à segurança e fornecer diretrizes de mitigação de risco à equipe de TI responsável pela infraestrutura de segurança. Ao desenvolver políticas e processos de governança, certifique-se de envolver equipes de TI pertinentes nos processos de planejamento e avaliação.

Esta seção da Cloud Adoption Framework descreve como desenvolver uma disciplina de Consistência de Recursos como parte de sua estratégia de governança de nuvem. O principal público-alvo dessas diretrizes são os arquitetos de nuvem da organização e outros membros da equipe de governança de nuvem. No entanto, as decisões, políticas e os processos que surgem dessa disciplina devem envolver participação e discussões com membros relevantes das equipes de TI responsáveis pela implementação e gerenciamento das soluções de Consistência de Recursos da sua organização.

Se a organização não tiver experiência interna em estratégias de Consistência de recursos, considere contratar consultores externos de segurança como um componente dessa disciplina. Além disso, considere contratar os [Serviços de Consultoria Microsoft](https://www.microsoft.com/enterprise/services), o serviço de adoção de nuvem [Microsoft FastTrack](https://azure.microsoft.com/programs/azure-fasttrack) ou adoção de outros especialistas externos para discutir como melhor organizar, rastrear e otimizar seus ativos baseados em nuvem.

## <a name="policy-statements"></a>Declarações de políticas

As declarações de política acionáveis e os requisitos de arquitetura resultantes servem como base de uma disciplina de Linha de base de segurança. Para ver exemplos de declarações de políticas, consulte o artigo sobre [Declarações de políticas de consistência de recurso](./policy-statements.md). Esses exemplos podem servir como ponto de partida para as políticas de governança da sua organização.

> [!CAUTION]
> As políticas de exemplo são provenientes de experiências comuns do cliente. Para alinhar melhor essas políticas às necessidades específicas de governança de nuvem, execute as etapas a seguir para criar instruções de políticas que atendam às suas necessidades exclusivas de negócios.

## <a name="developing-resource-consistency-governance-policy-statements"></a>Instruções de políticas de governança de consistência de recursos de desenvolvimento

As seis etapas a seguir oferecem exemplos e opções em potencial a serem consideradas ao desenvolver a governança de consistência de recursos. Use cada etapa como um ponto de partida para discussões com a equipe de governança de nuvem e com as equipes empresariais e de TI afetadas em sua organização para estabelecer as políticas e os processos necessários para gerenciar os riscos relacionados à Consistência de Recursos.

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
                        <h3>Modelo de consistência de recursos</h3>
                        <p class="x-hidden-focus">Baixe o modelo para documentar uma disciplina de Consistência de recursos</p>
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
                        <p class="x-hidden-focus">Reconheça os motivos e riscos normalmente associados à disciplina de Consistência de recursos.</p>
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
                        <p class="x-hidden-focus">Indicadores para reconhecer se é o momento certo para investir na disciplina de Consistência de recursos.</p>
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
                        <p class="x-hidden-focus">Processos sugeridos para apoiar a conformidade com a política na disciplina de Consistência de recursos.</p>
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
                        <p class="x-hidden-focus">Os serviços do Azure que podem ser implementados para dar suporte à disciplina de Consistência de recursos.</p>
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
