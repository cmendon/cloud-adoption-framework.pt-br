---
title: Estabelecer uma análise de adequação operacional
description: Estabeleça um processo de revisão de adequação operacional para entender totalmente os problemas resultantes da execução de cargas de trabalho em um ambiente de produção.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9bc4e2bb9b39a83ab8829ea4a12cd1bb019bf0c3
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78341803"
---
# <a name="establish-an-operational-fitness-review"></a>Estabelecer uma análise de adequação operacional

À medida que sua empresa começa a operar cargas de trabalho no Azure, a próxima etapa é estabelecer um processo para *revisão de ADEQÜAÇÃO operacional*. Esse processo enumera, implementa e analisa iterativamente os requisitos não- *funcional* para essas cargas de trabalho. Os requisitos não-funcionais estão relacionados ao comportamento operacional esperado do serviço.

Há cinco categorias essenciais de requisitos não-infuncionais, que são chamadas de [pilares de qualidade de software](https://docs.microsoft.com/azure/architecture/guide/pillars):

- Escalabilidade
- Disponibilidade
- Resiliência, incluindo continuidade dos negócios e recuperação de desastres
- Gerenciamento
- Segurança

Um processo de revisão de adequação operacional garante que suas cargas de trabalho de missão crítica atendam às expectativas de seus negócios em relação aos pilares de qualidade.

Crie um processo de revisão de ADEQÜAÇÃO operacional para entender totalmente os problemas resultantes da execução de cargas de trabalho em um ambiente de produção e como corrigir e resolver esses problemas. Este artigo descreve um processo de alto nível para revisão de ADEQÜAÇÃO operacional que sua empresa pode usar para atingir essa meta.

## <a name="operational-fitness-at-microsoft"></a>Adequação operacional na Microsoft

Desde o início, muitas equipes na Microsoft estão envolvidas no desenvolvimento da plataforma Azure. É difícil garantir a qualidade e a consistência de um projeto de tal tamanho e complexidade. Você precisa de um processo robusto para enumerar e implementar requisitos fundamentais não de funcionalidade regularmente.

Os processos que a Microsoft segue formam a base dos processos descritos neste artigo.

## <a name="understand-the-problem"></a>Entender o problema

Como você aprendeu na [introdução](../getting-started/migrate.md), a primeira etapa da transformação digital de uma empresa é identificar os problemas de negócios a serem resolvidos adotando o Azure. A próxima etapa é determinar uma solução de alto nível para o problema, como migrar uma carga de trabalho para a nuvem ou adaptar um serviço local existente para incluir a funcionalidade de nuvem. Por fim, você cria e implementa a solução.

Durante esse processo, o foco geralmente está nos recursos do serviço: o conjunto de requisitos _funcionais_ que você deseja que o serviço execute. Por exemplo, um serviço de entrega de produto requer recursos para determinar os locais de origem e de destino do produto, acompanhar o produto durante a entrega e enviar notificações para o cliente.

Os requisitos não- _infuncionais_ , por outro lado, estão relacionados a propriedades como [disponibilidade](https://docs.microsoft.com/azure/architecture/checklist/availability), [resiliência](https://docs.microsoft.com/azure/architecture/resiliency)e [escalabilidade](https://docs.microsoft.com/azure/architecture/checklist/scalability)do serviço. Essas propriedades diferem dos requisitos funcionais porque não afetam diretamente a função final de qualquer recurso específico no serviço. No entanto, os requisitos não-infuncionais se relacionam com o desempenho e a continuidade do serviço.

Você pode especificar alguns requisitos não-infuncionais em termos de um SLA (contrato de nível de serviço). Por exemplo, você pode expressar a continuidade de serviço como uma porcentagem de disponibilidade: "disponível 99,99% do tempo". Outros requisitos não-funcionais podem ser mais difíceis de definir e podem mudar conforme as necessidades de produção mudam. Por exemplo, um serviço orientado ao consumidor pode enfrentar requisitos de taxa de transferência inesperados após um surto de popularidade.

> [!NOTE]
> Para obter mais detalhes sobre os requisitos de resiliência, consulte [projetando aplicativos confiáveis do Azure](https://docs.microsoft.com/azure/architecture/reliability#define-requirements). Esse artigo inclui explicações de conceitos como RPO (objetivo de ponto de recuperação), RTO (objetivo de tempo de recuperação) e SLA.

## <a name="process-for-operational-fitness-review"></a>Processo de revisão de adequação operacional

A chave para manter o desempenho e a continuidade dos serviços de uma empresa é implementar um processo de revisão de ADEQÜAÇÃO operacional.

![Uma visão geral do processo de revisão de adequação operacional](../_images/manage/ofr-flow.png)

Em um nível elevado, o processo conta com duas fases. Na *fase pré-requisitos*, os requisitos são estabelecidos e mapeados para serviços de suporte. Essa fase ocorre com pouca frequência: Talvez anualmente ou quando novas operações forem introduzidas. A saída da fase de pré-requisitos é usada na fase de *fluxo*. A fase de fluxo ocorre com mais frequência, como mensal.

### <a name="prerequisites-phase"></a>Fase de pré-requisitos

As etapas nesta fase capturam os requisitos para realizar uma revisão regular dos serviços importantes.

1. **Identificar operações de negócios críticas**. Identificar as operações de negócio críticas para a missão da empresa. Operações de negócios são independentes de qualquer funcionalidade de serviço de suporte. Em outras palavras, as operações de negócios representam as atividades reais que a empresa precisa executar e que têm suporte de um conjunto de serviços de ti.

    O termo *crítico* (ou *comercialmente crítico*) reflete um impacto grave na empresa se a operação for impedida. Por exemplo, um varejista online pode ter uma operação de negócios, como "permitir que um cliente adicione um item a um carrinho de compras" ou "processar um pagamento de cartão de crédito". Se uma dessas operações falhar, um cliente não poderá concluir a transação e a empresa não perceberá as vendas.

1. **Mapear operações para serviços**. Mapeie as operações comerciais críticas para os serviços que dão suporte a elas. No exemplo de compra-carrinho, vários serviços podem estar envolvidos, incluindo um serviço de gerenciamento de estoque de estoque e um serviço de carrinho de compras. Para processar um pagamento de cartão de crédito, um serviço de pagamento local pode interagir com um serviço de processamento de pagamento de terceiros.

1. **Analisar dependências de serviços**. A maioria das operações de negócios requer orquestração entre vários serviços de suporte. É importante entender as dependências entre os serviços e o fluxo de transações de missão crítica por meio desses serviços.

    Considere também as dependências entre os serviços locais e os serviços do Azure. No exemplo de compra-carrinho, o serviço de gerenciamento de estoque de estoque pode ser hospedado localmente e ingerir dados inseridos por funcionários de um depósito físico. No entanto, ele pode armazenar dados fora do local em um serviço do Azure, como o [armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-introduction), ou um banco de dado, como [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction).

O resultado dessas atividades é um conjunto de *métricas de scorecard* para operações de serviço. O Scorecard mede critérios como disponibilidade, escalabilidade e recuperação de desastre. As métricas do scorecard expressam os critérios operacionais que você espera que o serviço atenda. Essas métricas podem ser expressas em qualquer nível de granularidade apropriado para a operação de serviço.

O scorecard deve ser expresso em termos simples para facilitar uma discussão relevante entre os proprietários dos negócios e a engenharia. Por exemplo, uma métrica de scorecard para escalabilidade pode ser codificada por cores de uma maneira simples. Verde significa cumprir os critérios definidos, amarelo significa falha ao atender aos critérios definidos, mas implementar ativamente uma correção planejada e vermelho significa falha ao atender aos critérios definidos sem plano ou ação.

É importante enfatizar que essas métricas devem refletir diretamente as necessidades dos negócios.

### <a name="service-review-phase"></a>Fase de revisão de serviço

A fase de análise de serviço é o núcleo da revisão de ADEQÜAÇÃO operacional. Ele envolve estas etapas:

1. **Medir métricas de serviço**. Use as métricas do scorecard para monitorar os serviços, para garantir que os serviços atendam às expectativas dos negócios. O monitoramento de serviço é essencial. Se você não puder monitorar um conjunto de serviços em relação aos requisitos não-funcionais, considere as métricas de Scorecard correspondentes como vermelho. Nesse caso, a primeira etapa de correção é implementar o monitoramento de serviço apropriado. Por exemplo, se a empresa espera que um serviço opere com 99,99% de disponibilidade, mas não há nenhuma telemetria de produção em vigor para medir a disponibilidade, presuma que você não está atendendo ao requisito.

2. **Planejar uma correção**. Para cada operação de serviço para a qual as métricas ficam abaixo de um limite aceitável, determine o custo da correção do serviço para trazer a operação a um nível aceitável. Se o custo de correção do serviço for maior do que a geração de receita esperada do serviço, passe para considerar os custos intangíveis, como a experiência do cliente. Por exemplo, se os clientes tiverem dificuldade em fazer um pedido bem-sucedido usando o serviço, eles poderão escolher um concorrente.

3. **Implementar a correção**. Depois que a equipe de engenharia e os proprietários de negócios concordarem em um plano, implemente-o. Relate o status da implementação sempre que você revisar as métricas do scorecard.

Esse processo é iterativo e, teoricamente, sua empresa tem uma equipe dedicada a ela. Essa equipe deve atender regularmente para examinar os projetos de atualização existentes, iniciar a revisão fundamental das novas cargas de trabalho e acompanhar o Scorecard geral da empresa. A equipe também deve ter autoridade para manter as equipes de correção responsáveis se elas estiverem atrasadas ou falharem em atender às métricas.

## <a name="structure-of-the-review-team"></a>Estrutura da equipe de revisão

A equipe responsável pela revisão da adequação operacional é composta pelas seguintes funções:

- **Proprietário da empresa:** Fornece conhecimento da empresa para identificar e priorizar cada operação de negócios de missão crítica. Essa função também compara o custo de mitigação ao impacto nos negócios e orienta a decisão final sobre a correção.

- **Defensora dos negócios:** Divide as operações de negócios em partes discretas e mapeia essas partes para serviços e infraestrutura, seja no local ou na nuvem. A função requer um conhecimento profundo da tecnologia associada a cada operação de negócios.

- **Proprietário da engenharia:** Implementa os serviços associados à operação de negócios. Esses indivíduos podem participar do design, da implementação e da implantação de qualquer solução para problemas de requisitos não-infuncionais que são descobertos pela equipe de análise.

- **Proprietário do serviço:** Opera os aplicativos e serviços da empresa. Esses indivíduos coletam dados de registro em log e de uso para esses aplicativos e serviços. Esses dados são usados para identificar problemas e verificar correções depois de serem implantados.

## <a name="review-meeting"></a>Revisar reunião

É recomendável que sua equipe de análise se reúna regularmente. Por exemplo, a equipe pode atender mensalmente e, em seguida, relatar o status e as métricas à liderança sênior trimestralmente.

Adapte os detalhes do processo e da reunião para atender às suas necessidades específicas. Como ponto de partida, recomendamos as seguintes tarefas:

1. O proprietário da empresa e o defensor dos negócios enumeram e determinam os requisitos não-funcionais para cada operação de negócios, com a entrada dos proprietários de engenharia e serviço. Para operações comerciais que foram identificadas anteriormente, examine e verifique a prioridade. Para novas operações de negócios, atribua uma prioridade na lista existente.

2. Os proprietários de engenharia e serviço mapeiam o estado atual das operações de negócios para os serviços locais e de nuvem correspondentes. O mapeamento é uma lista dos componentes em cada serviço, orientado como uma árvore de dependência. Os proprietários de engenharia e serviço determinam os caminhos críticos por meio da árvore.

3. O responsável pela engenharia e o proprietário de serviços analisam o estado atual do log operacional e o monitoramento dos serviços listados na etapa anterior. O registro em log e o monitoramento robustos são críticos: eles identificam os componentes de serviço que contribuem para uma falha de atender aos requisitos não-funcionais. Se o registro em log e o monitoramento suficientes não estiverem em vigor, a equipe deverá colocá-los em vigor criando e implementando um plano.

4. A equipe cria métricas de scorecard para novas operações de negócios. O Scorecard consiste na lista de componentes constituintes para cada serviço identificado na etapa 2. Ele está alinhado com os requisitos não-funcionais e inclui uma medida de quão bem cada componente atende aos requisitos.

5. Para componentes constituintes que não atendem aos requisitos não-funcionais, a equipe cria uma solução de alto nível e atribui um proprietário de engenharia. Neste ponto, o proprietário da empresa e o defensor dos negócios estabelecem um orçamento para o trabalho de correção, com base na receita esperada da operação de negócios.

6. Por fim, a equipe realiza uma análise do trabalho de correção em andamento. Cada uma das métricas de scorecard para o trabalho em andamento é examinada em relação aos critérios esperados. Para componentes constituintes que atendem aos critérios de métrica, o proprietário do serviço apresenta logs e dados de monitoramento para confirmar que os critérios são atendidos. Para os componentes constituintes que não atendem aos critérios de métrica, cada proprietário da engenharia explica os problemas que estão impedindo que os critérios sejam atendidos e apresenta novos designs para correção.

## <a name="recommended-resources"></a>Recursos recomendados

- [Pilares de qualidade do software](https://docs.microsoft.com/azure/architecture/guide/pillars).
    Esta seção do guia de arquitetura do Aplicativo Azure descreve os cinco pilares da qualidade do software: escalabilidade, disponibilidade, resiliência, gerenciamento e segurança.
- [Dez princípios de design para aplicativos do Azure](https://docs.microsoft.com/azure/architecture/guide/design-principles).
    Esta seção do guia de arquitetura do Aplicativo Azure discute um conjunto de princípios de design para tornar seu aplicativo mais escalonável, resiliente e gerenciável.
- [Projetar aplicativos resilientes para o Azure](https://docs.microsoft.com/azure/architecture/resiliency).
    Este guia começa com uma definição do termo _resiliência_ e conceitos relacionados. Em seguida, ele descreve um processo de obtenção de resiliência usando uma abordagem estruturada durante o tempo de vida de um aplicativo, desde o design e a implementação até a implantação e as operações.
- [Padrões de design de nuvem](https://docs.microsoft.com/azure/architecture/patterns).
    Esses padrões de design são úteis para equipes de engenharia ao criar aplicativos sobre os pilares de qualidade do software.
- [Azure Advisor](https://docs.microsoft.com/azure/advisor).
    O Advisor fornece recomendações personalizadas com base no uso e nas configurações para ajudá-lo a otimizar seus recursos para alta disponibilidade, segurança, desempenho e custo.
