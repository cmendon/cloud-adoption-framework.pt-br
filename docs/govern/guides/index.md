---
title: Guias de governança de nuvem
description: Examine os guias de governança de nuvem que ilustram as melhores práticas para uma abordagem incremental a qualquer cenário de governança.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: 51f24653998ab3cd4cf7fd043b487e4d7c1ccc5b
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709219"
---
# <a name="cloud-governance-guides"></a>Guias de governança de nuvem

Os guias de governança acionáveis desta seção ilustram a abordagem incremental do modelo de governança do Cloud Adoption Framework, com base na [metodologia de governança](../methodology.md) descrita anteriormente. Você pode estabelecer uma abordagem para a governança de nuvem que seja ágil e capaz de crescer para atender às necessidades de qualquer cenário.

## <a name="review-and-adopt-cloud-governance-best-practices"></a>Examine e adote as melhores práticas de governança de nuvem

Para começar seu percurso de adoção, escolha um dos seguintes guias de governança. Cada guia descreve um conjunto de melhores práticas, com base em um conjunto de experiências fictícias de cliente. Para os leitores que são novos na abordagem incremental do modelo de governança do Cloud Adoption Framework, revise a introdução da teoria de governança de alto nível abaixo antes de adotar qualquer conjunto de melhores práticas.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./standard/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
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
    <a href="./complex/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
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

## <a name="an-incremental-approach-to-cloud-governance"></a>Uma abordagem incremental para a governança de nuvem

## <a name="choose-a-governance-guide"></a>Escolha um guia de governança

Os guias demonstram como implementar um MVP de governança. Depois disso, cada guia mostra como a equipe de governança de nuvem pode trabalhar à frente das equipes de adoção da nuvem como um parceiro para acelerar os esforços de adoção. O modelo de governança do Cloud Adoption Framework guia a aplicação da governança desde a base até as melhorias e as evoluções subsequentes.

Para iniciar um percurso de governança, escolha uma das duas opções abaixo. As opções são baseadas em experiências de cliente sintetizadas. Os títulos são baseados na complexidade da empresa para facilitar a navegação. No entanto, a decisão do leitor pode ser mais complexa. As tabelas a seguir descrevem as diferenças entre as duas opções.

> [!WARNING]
> Pode ser necessário um ponto de partida de governança mais robusto. Nesses casos, considere a abordagem [Datacenter Virtual do Azure](#azure-virtual-datacenter) descrita brevemente [abaixo](#azure-virtual-datacenter). Essa abordagem é sugerida normalmente durante os esforços de adoção de escala empresarial, especialmente naqueles que ultrapassam dez mil ativos. É também a escolha concreta para cenários complexos de governança quando qualquer um dos itens a seguir é necessário: requisitos abrangentes de conformidade de terceiros, conhecimento profundo de domínio ou paridade com políticas de controle de TI e requisitos de conformidade.

<!-- markdownlint-disable MD028 -->

> [!NOTE]
> É improvável que algum dos guias se alinhe completamente à sua situação. Escolha o que estiver mais próximo e use-o como um ponto de partida. Ao longo do guia, são fornecidas informações adicionais para ajudá-lo a personalizar as decisões e atender a critérios específicos.

### <a name="business-characteristics"></a>Características de negócios

| Característica | Organização padrão | Empresa complexa |
|---|---|---|
| Geografia (país ou região geopolítica) | Os clientes ou funcionários residem, em grande parte, em uma região | Os clientes ou os funcionários residem em várias regiões ou exigem nuvens soberanas. |
| Unidades de negócios afetadas | Unidades de negócios que compartilham uma infraestrutura de TI comum | Várias unidades de negócios que não compartilham uma infraestrutura de TI comum |
| Orçamento de TI | Orçamento de TI único | Orçamento alocado entre as unidades de negócios e as moedas |
| Investimentos em TI | Os investimentos orientados por despesa de capital são planejados anualmente e costumam cobrir apenas uma manutenção básica. | Os investimentos orientados por despesa de capital são planejados anualmente e costumam incluir manutenção e um ciclo de atualização de três a cinco anos. |

### <a name="current-state-before-adopting-cloud-governance"></a>O estado atual antes da adoção da governança de nuvem

| Estado | Empresa padrão | Empresa complexa |
|---|---|---|
| Datacenter ou provedores de hospedagem terceirizados | Menos de cinco datacenters | Mais de cinco datacenters |
| Rede | Sem WAN ou 1 &ndash; 2 provedores de WAN | Rede complexa ou WAN global |
| Identidade | Floresta única, domínio único. | Várias florestas e vários domínios complexos. |

### <a name="desired-future-state-after-incremental-improvement-of-cloud-governance"></a>Estado futuro desejado após a melhoria incremental da governança de nuvem

| Estado | Organização padrão | Empresa complexa |
|---|---|---|
| Gerenciamento de Custos – contabilização da nuvem | Modelo de análise. A cobrança é centralizada entre a TI. | Modelo de estorno. A cobrança pode ser distribuída entre as aquisições da TI. |
| Linha de base de segurança – dados protegidos | Dados financeiros e IP da empresa. Dados de cliente limitados. Sem requisitos de conformidade de terceiros. | Várias coleções de dados financeiros e pessoais de clientes. Talvez seja preciso considerar a conformidade a terceiros. |

## <a name="azure-virtual-datacenter"></a>Datacenter Virtual do Azure

O Datacenter Virtual do Azure é uma abordagem para aproveitar ao máximo os recursos da plataforma de nuvem do Azure, respeitando os requisitos de governança e segurança da empresa.

Em comparação com os ambientes tradicionais no local, o Azure permite que as equipes de desenvolvimento de carga de trabalho e seus patrocinadores comerciais aproveitem a maior agilidade de implantação oferecida pelas plataformas em nuvem. No entanto, conforme seus esforços de adoção da nuvem expandem para incluir as cargas de trabalho e dados essenciais, essa agilidade pode entrar em conflito com os requisitos de conformidade de segurança e política corporativos estabelecidos por suas equipes de TI. Isso vale especialmente para grandes empresas que têm requisitos normativos e de governança sofisticados.

A abordagem do Datacenter Virtual do Azure tem como objetivo lidar com essas preocupações no início do ciclo de vida de adoção, fornecendo modelos, arquiteturas de referência, artefatos de automação de exemplo e orientação para ajudar a alcançar um equilíbrio entre os requisitos dos desenvolvedores e da governança de TI durante os esforços de adoção da nuvem empresarial. O ponto central dessa abordagem é o conceito de um datacenter virtual em si: a implementação de limites de isolamento em torno de sua infraestrutura de nuvem por meio da aplicação de controles de acesso e segurança, políticas de rede e monitoramento de conformidade.

Um datacenter virtual pode ser considerado como sua própria nuvem isolada na plataforma do Azure, integrando processos de gerenciamento, requisitos normativos e processos de segurança exigidos por suas políticas de controle. Dentro desse limite de virtual, o Datacenter Virtual do Azure oferece modelos de exemplo para implantar cargas de trabalho, garantindo conformidade uniforme, e fornece orientação básica sobre a implementação da separação de funções e responsabilidades de uma organização na nuvem.

### <a name="azure-virtual-datacenter-assumptions"></a>Suposições do Datacenter Virtual do Azure

Embora as equipes menores possam se beneficiar dos modelos e das recomendações fornecidas pelo Datacenter Virtual do Azure, essa abordagem foi desenvolvida para orientar os grupos de TI empresarial que gerenciam grandes ambientes de nuvem. Para organizações que atendem aos critérios a seguir, é recomendável consultar as diretrizes do Datacenter Virtual do Azure ao projetar uma infraestrutura de nuvem baseada no Azure:

- Sua empresa está sujeita aos requisitos de conformidade regulatória que exigem recursos de monitoramento e auditoria centralizados.
- Você precisa manter a conformidade com políticas e governança comuns, bem como o controle central da TI sobre os serviços principais.
- Seu setor depende de uma plataforma complexa que exige controles complexos e conhecimento profundo do domínio para administrar a plataforma. Isso é mais comum em grandes empresas dos setores financeiro, manufatureiro ou de petróleo e gás.
- Suas políticas de governança de TI existentes exigem paridade mais rigorosa com os recursos existentes, mesmo durante a adoção em estágio inicial.

Para obter mais informações, visite a seção [Datacenter Virtual do Azure](../../reference/vdc.md) do Cloud Adoption Framework.

## <a name="next-steps"></a>Próximas etapas

Escolha um destes guias:

> [!div class="nextstepaction"]
> [Guia de governança corporativa padrão](./standard/index.md)
>
> [Guia de governança para empresas complexas](./complex/index.md)
