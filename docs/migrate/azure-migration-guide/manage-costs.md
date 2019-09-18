---
title: Mecanismos de controle de custo focados na migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como configurar orçamentos e pagamentos e entender as faturas de seus recursos do Azure.
author: bandersmsft
ms.author: banders
ms.date: 08/08/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: c6b195a69622a4934f257090650a8ba6ce884025
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024799"
---
# <a name="migration-focused-cost-control-mechanisms"></a>Mecanismos de controle de custo focados na migração

A nuvem apresenta algumas mudanças na forma como trabalhamos, independentemente de nossa função na equipe de tecnologia. O custo é um ótimo exemplo dessa mudança. No passado, apenas o setor de Finanças e a liderança de TI se preocupavam com o custo dos ativos de TI (infraestrutura, aplicativos e dados). A nuvem capacita todos os membros da área de TI a tomar e a agir com base em decisões que dão melhor suporte ao usuário final. No entanto, com esse poder vem a responsabilidade ter consciência do custo ao tomar essas decisões.

Este artigo apresenta as ferramentas que podem ajudar a tomar decisões de custo inteligente antes, durante e após uma migração para o Azure.

As ferramentas neste artigo incluem:

> - Migrações para Azure
> - Calculadora de preços do Azure
> - Calculadora de TCO do Azure
> - Gerenciamento de Custos do Azure
> - Assistente do Azure

Os processos descritos neste artigo também podem exigir uma parceria com gerentes de TI, de finanças ou com proprietários de aplicativos de linha de negócios. Para obter orientações sobre parcerias com essas funções, confira no artigo sobre Cloud Adoption Framework como estabelecer uma organização com consciência de custo (ele estará disponível no terceiro trimestre de 2019).

<!-- markdownlint-disable MD024 MD025 -->

# <a name="estimate-vm-costs-prior-to-migrationtabestimatevmcosts"></a>[Estimar os custos da VM antes da migração](#tab/EstimateVMCosts)

Antes da migração de qualquer ativo (infraestrutura, aplicativo ou dados), há uma oportunidade de estimar os custos e refinar o dimensionamento com base nos critérios de desempenho observados para esses ativos. A estimativa de custos tem duas finalidades: permite o controle de custos e fornece um ponto de verificação para garantir que os orçamentos atuais atendam aos requisitos de desempenho necessários.

## <a name="cost-calculators"></a>Calculadoras de custo

Para cálculos de custo manual, há duas calculadoras úteis que podem fornecer uma estimativa de custo rápida com base na arquitetura da carga de trabalho a ser migrada.

- A [calculadora de preços](https://azure.microsoft.com/pricing/calculator) do Azure fornece estimativas de custo com base em produtos do Azure inseridos manualmente.
- Às vezes, as decisões exigem uma comparação dos custos futuros da nuvem e dos custos locais atuais. A [calculadora de TCO (custo total de propriedade)](https://azure.microsoft.com/pricing/tco/calculator) pode fornecer tal comparação.

Essas calculadoras de custo manuais podem ser usadas individualmente para prever possíveis gastos e economias. Também podem ser usadas em conjunto com as ferramentas de previsão de custos das Migrações para Azure para ajustar as expectativas de custo a arquiteturas alternativas ou a restrições de desempenho.

## <a name="azure-migrate-calculations"></a>Cálculos das Migrações para Azure

**Pré-requisitos:** O restante desta guia pressupõe que o leitor já preencheu as Migrações para Azure com uma série de ativos (infraestrutura, aplicativos e dados) a serem migrados. O artigo anterior sobre avaliações fornece instruções sobre como coletar os dados iniciais. Após os dados serem preenchidos, siga as próximas etapas para estimar os custos mensais com base nos dados coletados.

As Migrações para Azure calculam **estimativas de custo mensal** com base em dados capturados pelo coletor e pelo mapa do serviço. As etapas a seguir carregam as estimativas de custo:

1. Navegue até a folha Avaliação das Migrações para Azure no portal.
1. Na página **Visão geral** do projeto, selecione **+Criar avaliação**.
1. Clique em **Exibir tudo** para examinar as propriedades da avaliação.
1. Crie o grupo e especifique um nome de grupo.
1. Selecione as máquinas que deseja adicionar ao grupo.
1. Clique em **Criar avaliação**, para criar o grupo e a avaliação.
1. Depois que a avaliação é criada, é possível exibi-la em Visão geral > Painel.
1. Na seção Detalhes da Avaliação na navegação da folha, selecione **Detalhes de custo**.

A estimativa resultante, ilustrada abaixo, identifica os custos mensais de computação e armazenamento, que geralmente representam a maior parte dos custos de nuvem.

![compute-storage-monthly-cost-estimate.png](./media/manage-costs/compute-storage-monthly-cost-estimate.png)
*Figura 1 – Imagem da exibição Detalhes de Custo de uma avaliação nas Migrações para Azure.*

## <a name="additional-resources"></a>Recursos adicionais

- [Configurar e examinar uma avaliação com as Migrações para Azure](https://docs.microsoft.com/azure/migrate/tutorial-assess-vmware#set-up-an-assessment)
- Para avaliar um plano mais abrangente do gerenciamento de custos em um número maior de ativos (infraestrutura, aplicativos e dados), confira o [Modelo de governança da Estrutura de Adoção da Nuvem](../../govern/guides/index.md). Em particular, orientações sobre a [Disciplina de Gerenciamento de Custos](../../govern/cost-management/index.md) e a [Melhoria do Gerenciamento de Custos no guia para grandes empresas](../../govern/guides/complex/cost-management-improvement.md).

# <a name="estimate-and-optimize-vm-costs-during-and-after-migrationtabestimateoptimize"></a>[Estimar e otimizar custos de VM durante e após a migração](#tab/EstimateOptimize)

Estimar o custo antes da migração fornece um objetivo sólido para as expectativas de custo. Também fornece oportunidades para considerar as necessidades de desempenho e custo de cada ativo (infraestrutura, aplicativos e dados) a ser migrado. No entanto, ainda é uma estimativa. Depois que o ativo é migrado e está sob carga, cálculos de custo mais precisos podem ser feitos, com base na carga real ou sintetizada.

## <a name="azure-advisor-cost-recommendations"></a>Recomendações de custo do Assistente do Azure

Dentro de 24 horas da migração de ativos (infraestrutura, aplicativos e dados) para o Azure, o Assistente do Azure começa a monitorar o desempenho de cada ativo para fornecer comentários sobre ele. Um item de feedback coletado está relacionado ao equilíbrio entre custo e utilização.

As etapas a seguir fornecem recomendações de custo para ativos (infraestrutura, aplicativos e dados) em suas assinaturas atuais:

1. Navegue até a folha **Assistente do Azure** no portal. Para fazer isso, selecione **Assistente** no painel de navegação esquerdo do portal do Azure. Se não vir o Assistente no painel esquerdo, selecione **Todos os serviços**. No painel do menu de serviços, em **Monitoramento e Gerenciamento**, selecione **Assistente**.
1. O painel Assistente exibirá um resumo das suas recomendações para todas as assinaturas selecionadas. Você pode escolher as assinaturas para as quais você deseja que as recomendações sejam exibidas usando a lista suspensa de filtro de assinatura.
1. Para ver as recomendações de custo, selecione a guia Custo.

## <a name="azure-cost-management"></a>Gerenciamento de Custos do Azure

O Gerenciamento de Custos do Azure pode fornecer uma visão mais holística dos hábitos de gasto, incluindo a exibição detalhada dos custos e das tendências de gastos ao longo do tempo. Para migrações grandes ou complexas, essa exibição pode fornecer os insights necessários para tomar decisões de gerenciamento de custos mais amplas.

Pré-requisitos: O restante desta guia pressupõe que o leitor concluiu a configuração do Gerenciamento de Custos do Azure ao concluir o guia de Preparação para o Azure. Para obter mais detalhes sobre como configurar o Gerenciamento de Custos do Azure, confira este [artigo no guia de Preparação para o Azure](../../ready/azure-readiness-guide/manage-costs.md). Após os dados serem preenchidos, siga as próximas etapas para estimar os custos mensais com base nos dados coletados.

As etapas a seguir carregarão dados de análise de custo do Gerenciamento de Custos do Azure para suas assinaturas:

1. Navegue até a folha **Gerenciamento de Custos + Cobrança** no portal. Se não vir Gerenciamento de Custos + Cobrança no painel esquerdo, clique em **Todos os serviços**. No painel do menu de serviço, em **Monitoramento e Gerenciamento**, clique em **Gerenciamento de Custos + Cobrança**.
1. Na folha Gerenciamento de Custos + Cobrança, selecione **Gerenciamento de Custos** no painel de navegação esquerdo para que a folha aberta comece a analisar e otimizar os custos da nuvem.
1. Na folha Gerenciamento de Custos, selecione **Análise de custo**.
    1. Use o item **Escopo** para alterar para um escopo diferente na análise de custo.

Essa análise permitirá que você examine os custos totais, o orçamento (se disponível) e os custos acumulados. Cada cálculo pode ser exibido por serviço, por recurso e com o passar do tempo. O mais importante é que os custos podem ser analisados segundo marcas. Nomear e marcar adequadamente os ativos (infraestrutura, aplicativos e dados) é o ponto de partida fundamental de todos os processos sólidos de governança e gerenciamento de custos. Marcações adequadas permitem um melhor gerenciamento dos custos e impactos mais claros do desempenho e das otimizações de custo.

## <a name="additional-resources"></a>Recursos adicionais

- Para avaliar um plano mais abrangente do gerenciamento de custos em um número maior de ativos (infraestrutura, aplicativos e dados), confira o [Modelo de governança da Estrutura de Adoção da Nuvem](../../govern/guides/index.md). Em particular, orientações sobre a [Disciplina de Gerenciamento de Custos](../../govern/cost-management/index.md) e a [Melhoria incremental do Gerenciamento de Custos no guia para grandes empresas](../../govern/guides/complex/cost-management-improvement.md).
- Para obter mais informações sobre o Assistente do Azure, confira [Reduzindo custos de serviço usando o Assistente do Azure](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations).
- Para obter mais informações sobre o Gerenciamento de Custos do Azure, confira [Entender e trabalhar com escopos](https://docs.microsoft.com/azure/cost-management/understand-work-scopes) e [Explorar e analisar custos com a Análise de Custos](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis).

# <a name="tips-and-tricks-to-optimize-coststabtipstricks"></a>[Dicas e truques para otimizar custos](#tab/TipsTricks)

Além das ferramentas mencionadas neste artigo, há algumas dicas e truques que podem ajudar a reduzir rapidamente os custos gerais da nuvem. A seguir, temos algumas dicas de alto nível a serem consideradas:

## <a name="avoid-unnecessary-spending"></a>Evitar gastos desnecessários

A maioria dos ativos (infraestrutura, aplicativos e dados) em um datacenter existente pode, teoricamente, ser migrada para a nuvem. No entanto, isso não significa que devem ser. Durante a avaliação de cada carga de trabalho, valide se a carga de trabalho deve ser migrada. O artigo da Estrutura de Adoção da Nuvem sobre [racionalização incremental](../../digital-estate/rationalize.md) pode ajudar a determinar quais ativos devem ser migrados.

## <a name="reduce-waste"></a>Reduzir o desperdício

Depois de implantar sua infraestrutura no Azure, é importante garantir que ela esteja sendo usada. A maneira mais fácil de começar a economizar imediatamente é examinar seus recursos e remover os que não estão sendo usados.

## <a name="reduce-overprovisioning"></a>Reduzir o provisionamento excessivo

Mesmo com as melhores abordagens para estimativa, é provável que haja ativos (infraestrutura, aplicativos e dados) provisionados e subutilizados. Examinar esses ativos usando as ferramentas nas duas guias anteriores identificará possíveis meios de reduzir o tamanho do ativo para atender melhor aos requisitos de desempenho e reduzir os custos.

## <a name="take-advantage-of-available-discounts"></a>Aproveitar os descontos disponíveis

Fale com seu representante de conta Microsoft para entender como você pode aproveitar as opções de desconto atuais. Veja a seguir alguns exemplos de descontos que costumam ser usados para reduzir os custos.

## <a name="azure-reservations"></a>Reservas do Azure

As [Reservas do Azure](https://docs.microsoft.com/azure/billing/billing-save-compute-costs-reservations) permitem que você pague antecipadamente por um ou três anos de máquina virtual ou pela capacidade de computação de Banco de Dados SQL. Pagar previamente permitirá obter um desconto nos recursos que você usar. As Reservas do Azure podem reduzir significativamente os custos de sua máquina virtual ou os custos de computação do Banco de Dados SQL em até 72% com base em preços pagos conforme o uso, com um compromisso antecipado de um ou três anos. As reservas fornecem um desconto de faturamento e não afetam o estado de tempo de execução de suas máquinas virtuais ou bancos de dados SQL.

## <a name="use-azure-hybrid-benefit"></a>Usar o Benefício Híbrido do Azure

Se já tiver licenças do Windows Server ou do SQL Server em suas implantações locais, você poderá usar o programa [Benefício Híbrido do Azure](https://azure.microsoft.com/pricing/hybrid-benefit) para economizar no Azure. Com o benefício do Windows Server, cada licença abrange o custo do sistema operacional (até duas máquinas virtuais), e você paga apenas pelos custos de computação base. Você pode usar as licenças existentes do SQL Server para economizar até 55% em opções de Banco de Dados SQL baseadas em vCore. As opções incluem o SQL Server em máquinas virtuais do Azure e o SQL Server Integration Services.

## <a name="low-priority-vms-with-batch"></a>VMs de baixa prioridade com o Lote

Para processos em segundo plano de prioridade mais baixa, o Lote oferece um meio de gerenciar as VMs de serviço em segundo plano e reduzir os custos. No entanto, é importante entender o impacto sobre o desempenho de [VMs de baixa prioridade com o Lote](https://docs.microsoft.com/azure/batch/batch-low-pri-vms) antes de escolher essa opção com desconto.

## <a name="additional-resources"></a>Recursos adicionais

Para avaliar um plano mais abrangente do gerenciamento de custos em um número maior de ativos (infraestrutura, aplicativos e dados), confira o [Modelo de governança da Estrutura de Adoção da Nuvem](../../govern/guides/index.md). Em particular, orientações sobre a [Disciplina de Gerenciamento de Custos](../../govern/cost-management/index.md) e a [Melhoria incremental do Gerenciamento de Custos no guia de governança para grandes empresas](../../govern/guides/complex/cost-management-improvement.md).
