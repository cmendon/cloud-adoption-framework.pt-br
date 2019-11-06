---
title: Migração na nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migração na nuvem na Cloud Adoption Framework
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: migrate
layout: LandingPage
ms.openlocfilehash: a6e7cb52fdac7607765b32c5355c0f2df066538a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566853"
---
# <a name="cloud-migration-in-the-cloud-adoption-framework"></a>Migração na nuvem na Cloud Adoption Framework

Qualquer [plano de adoção da nuvem](../plan/index.md) em escala empresarial incluirá cargas de trabalho que não garantem investimentos significativos na criação de uma lógica de negócios. Essas cargas de trabalho podem ser movidas para a nuvem por inúmeras abordagens: lift-and-shift, lift-and-optimize ou modernização. Cada uma dessas abordagens é considerada uma migração. Os exercícios a seguir ajudarão a estabelecer os processos iterativos para avaliar, migrar, otimizar, proteger e gerenciar essas cargas de trabalho.

## <a name="getting-started"></a>Introdução

Para se preparar para essa fase do ciclo de vida de adoção da nuvem, a estrutura sugere os cinco seguintes exercícios:

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsF">
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/prerequisites.md?tabs=Checklist">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/1.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Pré-requisito de migração</h3>
Confirme se uma zona de aterrissagem foi implantada e está pronta para hospedar as primeiras cargas de trabalho que serão migradas para o Azure. Se uma estratégia e um plano de adoção da nuvem não foram criados, confirme se ambos os esforços estão em andamento.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-migration-guide/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/2.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Migrar sua primeira carga de trabalho</h3>
Aproveite o Guia de Migração do Azure para orientar a migração da sua primeira carga de trabalho. Isso ajudará você a se familiarizar com as ferramentas e as abordagens necessárias para dimensionar os esforços de adoção.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./expanded-scope/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/3.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Cenários de migração expandidos</h3>
Aproveite a lista de verificação de escopo expandido para identificar os cenários que exigem modificações em sua arquitetura de estado futuro, processos de migração, configurações de zona de aterrissagem ou decisões de ferramentas de migração.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./azure-best-practices/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/4.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Práticas Recomendadas</h3>
Valide as modificações em relação à seção de melhores práticas para garantir uma implementação adequada do escopo expandido ou das abordagens de migração específicas de carga de trabalho/arquitetura.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
    <li style="display: flex; flex-direction: column;">
        <a href="./migration-considerations/index.md">
            <div class="cardSize">
                <div class="cardPadding" style="padding-bottom:10px;">
                    <div class="card" style="padding-bottom:10px;">
                        <div class="cardImageOuter">
                            <div class="cardImage">
                                <img alt="" src="../_images/icons/5.png" data-linktype="external">
                            </div>
                        </div>
                        <div class="cardText" style="padding-left:0px;">
                            <h3>Melhorias do processo</h3>
A migração é uma atividade intensa de processo. Conforme os esforços de migração crescem, use a seção de considerações sobre migração para avaliar e melhorar vários aspectos de seus processos.
                        </div>
                    </div>
                </div>
            </div>
        </a>
    </li>
</ul>
<!-- markdownlint-enable MD033 -->

## <a name="iterative-migration-process"></a>Processo iterativo de migração

Em seu núcleo, a migração para a nuvem consiste em quatro fases simples: Avaliar, Migrar, Otimizar e Proteger e Gerenciar. Esta seção do Cloud Adoption Framework ensina os leitores a maximizar o retorno de cada fase do processo e alinhar essas fases ao seu plano de adoção da nuvem. O seguinte gráfico ilustra essas fases em uma abordagem iterativa:

![Modelo de migração da Cloud Adoption Framework](../_images/operational-transformation-migrate.png)

## <a name="create-a-balanced-cloud-portfolio"></a>Crie um portfólio de nuvem equilibrado

Qualquer portfólio de tecnologia equilibrado tem uma combinação de ativos em vários estados. Alguns aplicativos estão programados para desativação e recebem suporte mínimo. Outros aplicativos ou ativos têm suporte em um estado de manutenção, mas os recursos dessas soluções são estáveis. Para processos empresariais mais recentes, a alteração nas condições de mercado provavelmente vai incentivar modernização ou aprimoramentos de recursos contínuos. Quando surgem oportunidades para gerar novos fluxos de receita, novos aplicativos ou os ativos são introduzidos no ambiente. Em cada estágio do ciclo de vida do ativo, o impacto que qualquer investimento tem sobre a receita e lucro mudará. Quanto mais tarde no estágio do ciclo de vida, menor é a probabilidade de um novo esforço de recurso ou modernização gerar um forte retorno sobre o investimento.

A nuvem fornece vários mecanismos de adoção, cada um com graus semelhantes de investimento e retorno. Criar aplicativos nativos de nuvem pode reduzir significativamente as despesas operacionais. Depois que um aplicativo nativo de nuvem é liberado, o desenvolvimento de novos recursos e soluções pode ser iterado com mais rapidez. Modernizar um aplicativo pode gerar benefícios semelhantes removendo restrições herdadas associadas a modelos de desenvolvimento local. Essas duas abordagens são trabalhosas e dependem do tamanho, das habilidades e da experiência das equipes de desenvolvimento de software. Com frequência, o trabalho está desalinhado&mdash;pessoas com as habilidades e o talento para modernizar aplicativos prefeririam criar novos aplicativos. Em um mercado com restrição de mão de obra, projetos de modernização em grande escala podem ter problemas de satisfação do funcionário e retenção de talentos. Em um portfólio equilibrado, essa abordagem deve ser reservada a aplicativos que receberiam aprimoramentos de recursos significativos se permanecessem locais.

## <a name="envision-an-end-state"></a>Vislumbrar um estado final

Um percurso eficaz precisa de um destino alvo. Estabeleça uma visão aproximada do estado final antes de dar o primeiro passo. Este infográfico descreve um ponto de partida que consiste em aplicativos, dados e infraestrutura existentes, o que define o acervo digital. Durante o processo de migração, cada ativo é transferido usando uma das opções à direita.

## <a name="migration-implementation"></a>Implementação da migração

Esses artigos descrevem dois percursos, cada um com uma meta semelhante&mdash;para migrar um grande percentual de ativos existentes para o Azure. No entanto, os resultados empresariais e o estado atual vão influenciar significativamente os processos necessários para chegar lá. Esses desvios sutis resultam em duas abordagens radicalmente diferentes para atingir um estado final semelhante.

![Modelo de migração da Cloud Adoption Framework](../_images/operational-transformation-migrate.png)

Para orientar a execução incremental durante a transição para o estado final, esse modelo separa a migração em duas áreas de foco.

**Preparação da migração:** estabelece uma lista de pendências de migração aproximada com base, em grande parte, no estado atual e nos resultados desejados.

- **Resultados empresariais:** os principais objetivos empresariais que conduzem essa migração.
- **Estimativa de acervo digital:** uma estimativa aproximada do número e da condição das cargas de trabalho a serem migradas.
- **Funções e responsabilidades:** uma definição clara da estrutura de equipe, da separação de responsabilidades e dos requisitos de acesso.
- **Requisitos de gerenciamento de alterações:** o ritmo, os processos e a documentação necessários para examinar e aprovar as alterações.

Essas entradas iniciais moldam a lista de pendências de migração. A saída da lista de pendências de migração é uma lista priorizada de aplicativos a serem migrados para a nuvem. Essa lista molda a execução do processo de migração na nuvem. Ao longo do tempo, também será expandida para incluir grande parte da documentação necessária para gerenciar alterações.

**Processo de migração:** cada atividade de migração na nuvem está contida em um dos processos a seguir no que se refere à lista de pendências de migração.

- **Avaliar:** avalie um ativo existente e estabeleça um plano para a migração do ativo.
- **Migração:** replique a funcionalidade de um ativo na nuvem.
- **Otimizar:** equilibre o desempenho, o custo, o acesso e a capacidade operacional de um ativo de nuvem.
- **Proteger e gerenciar:** verifique se um ativo de nuvem está pronto para operações contínuas.

As informações coletadas durante o desenvolvimento de uma lista de pendências de migração determinam a complexidade e o nível de esforço necessário dentro do processo de migração na nuvem durante cada iteração e para cada versão da funcionalidade.

## <a name="transition-to-the-end-state"></a>Transição para o estado final

A meta é uma migração tranquila e parcialmente automatizada para a nuvem. O processo de migração usa as ferramentas fornecidas por um fornecedor de nuvem para replicar e preparar rapidamente os ativos na nuvem. Após a verificação, uma alteração de rede simples redireciona os usuários para a solução de nuvem. Para muitos casos de uso, a tecnologia para atingir essa meta está amplamente disponível. Há casos de exemplo que demonstram a velocidade na qual 10 mil VMs podem ser replicadas no Azure.

No entanto, uma abordagem de migração incremental ainda é necessária. Na maioria dos ambientes, a longa lista de VMs a serem migradas deve ser dividida em unidades de trabalho menores para uma migração ser bem-sucedida. Há muitos fatores que limitam o número de VMs que podem ser migradas em um determinado período. A velocidade de saída da rede é um dos poucos limites técnicos; a maioria dos limites depende da capacidade da empresa de validar e adaptar-se à mudança.

A abordagem de migração incremental da estrutura de adoção de nuvem ajuda a criar um plano incremental que reflete e documenta as limitações técnicas e culturais. A meta deste modelo é maximizar a velocidade da migração, minimizando a sobrecarga tanto para a TI quanto para a empresa. A seguir estão dois exemplos de uma execução de migração incremental com base na lista de pendências de migração.

<!-- markdownlint-disable MD033 -->

<ul class="panelContent cardsZ">
<li style="display: flex; flex-direction: column;">
    <a href="./azure-migration-guide/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guia de migração do Azure</h3>
                        <p><b>Resumo da narrativa:</b> Esse cliente está migrando menos de 1.000 VMs. Menos de dez aplicativos compatíveis pertencem a um proprietário de aplicativo que não está na organização de TI. Os aplicativos, as VMs e os dados associados restantes são de propriedade e recebem o suporte de membros da equipe de adoção da nuvem. Os membros da equipe de adoção de nuvem têm acesso administrativo aos ambientes de produção no datacenter existente.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li style="display: flex; flex-direction: column;">
    <a href="./expanded-scope/index.md" style="display: flex; flex-direction: column; flex: 1 0 auto;">
        <div class="cardSize" style="flex: 1 0 auto; display: flex;">
            <div class="cardPadding" style="display: flex;">
                <div class="card">
                    <div class="cardText">
                        <h3>Guia de cenário complexo</h3>
                        <p><b>Resumo da narrativa:</b> Essa migração do cliente é complexa em termos de cultura, tecnologia e negócios. Este guia inclui vários desafios específicos de complexidade e formas de superá-los.</p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

<!-- markdownlint-enable MD033 -->

Esses dois percursos representam dois extremos de experiência para os clientes que investem em migração na nuvem. A maioria das empresas reflete uma combinação dos dois cenários acima. Depois de analisar o percurso, use o modelo de migração da Cloud Adoption Framework para iniciar a conversa sobre migração e modificar os percursos da linha de base para atender melhor às suas necessidades.

## <a name="next-steps"></a>Próximas etapas

Escolha um desses percursos:

> [!div class="nextstepaction"]
> [Guia de migração do Azure](./azure-migration-guide/index.md)
>
> [Guia de escopo expandido](./expanded-scope/index.md)
