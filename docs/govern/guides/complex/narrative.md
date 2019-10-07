---
title: 'Guia de governança para empresas complexas: A narração de suporte'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Essa narração estabelece um caso de uso para governança durante uma jornada de adoção de nuvem complexa da empresa.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: acc82a629adf32cd9a7bfe638b0ad176f1de7933
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967667"
---
# <a name="governance-guide-for-complex-enterprises-the-supporting-narrative"></a>Guia de governança para empresas complexas: A narração de suporte

A seguinte narração estabelece um caso de uso para [governança durante a jornada de adoção de nuvem de uma empresa complexa](./index.md). Antes de agir sobre as recomendações no guia, é importante entender as suposições e os motivos que se refletem nesta narração. Em seguida, você pode alinhar melhor a estratégia de governança à jornada de adoção de nuvem da sua própria organização.

## <a name="back-story"></a>Histórico

Os clientes estão exigindo uma melhor experiência ao interagir com essa empresa. A experiência atual causou erosão no mercado e levou o conselho a contratar um Diretor Digital (CDO). O CDO está trabalhando com marketing e vendas para orientar uma transformação digital que irá potencializar as experiências aprimoradas. Além disso, várias unidades comerciais recentemente contrataram cientistas para criar dados e melhorar muitas das experiências manuais através do aprendizado e previsão. A TI está dando suporte a esses esforços onde é possível. No entanto, há atividades de "TI invisível" ocorrendo que estão fora do controle da segurança e governança necessárias.

A organização de TI também está voltada aos seus próprios desafios. O setor de finanças está planejando reduções contínuas no orçamento de TI nos próximos cinco anos, levando a alguns cortes de custos necessários, começando este ano. Por outro lado, o GDPR e outros requisitos de soberania de dados estão obrigando a TI ao investir em ativos em países adicionais para localizar dados. Dois dos data centers existentes estão atrasados para as atualizações de hardware, causando mais problemas com o funcionário e satisfação do cliente. Mais três data centers exigem atualizações de hardware durante a execução do plano de cinco anos. O CFO está enviando por push para a CIO considerar a nuvem como uma alternativa para os datacenters, para liberar as despesas de capital.

A CIO tem ideias inovadoras que podem ajudar a empresa, mas ela e suas equipes estão limitadas a apagar incêndios e controlar os custos. Em um almoço com o CDO e um dos líderes da unidade de negócios, a conversa de migração de nuvem gerou interesse de colegas da CIO. Os três líderes buscam apoiar uns aos outros usando a nuvem para alcançar seus objetivos de negócios e começaram a exploração e planejamento de fases de adoção da nuvem.

## <a name="business-characteristics"></a>Características de negócios

A empresa tem o seguinte perfil de negócios:

- Operações de vendas e operações abrangem várias áreas geográficas com clientes globais em vários mercados.
- A empresa cresceu por meio da aquisição e opera em três unidades de negócios com base na base de clientes de destino. O orçamento é uma matriz complexa entre funções e as unidades de negócios.
- A empresa vê a maior parte da TI como um dreno de capital ou centro de custo.

## <a name="current-state"></a>Estado atual

Veja o estado atual da TI da empresa e das operações de nuvem:

- A TI opera mais de 20 datacenters privados em todo o mundo.
- Devido ao crescimento orgânica e a várias geografias, há algumas equipes de ti que têm requisitos exclusivos de soberania e conformidade de dados que afetam uma única unidade de negócios operando em uma geografia específica.
- Cada datacenter está conectado por uma série de linhas dedicadas regionais, criando um WAN global menos rígido.
- A TI inseriu a nuvem migrando todas as contas de email de usuário final para o Office 365. Essa migração foi concluída há mais de seis meses. Desde então, apenas alguns ativos de TI foram implantados na nuvem.
- A equipe de desenvolvimento principal do CDO está trabalhando em uma capacidade de desenvolvimento/teste para saber mais sobre os recursos nativos de nuvem.
- Uma unidade de negócios está experimentando big data na nuvem. A equipe do BI dentro da IT está participando desse esforço.
- A política de governança de ti existente declara que os dados pessoais do cliente e os dados financeiros devem ser hospedados em ativos de propriedade direta pela empresa. Essa política bloqueia a adoção de nuvem para qualquer aplicativo crítico de missão ou dados protegidos.
- Os investimentos de ti são controlados amplamente por despesas de capital. Esses investimentos são planejados anualmente e muitas vezes incluem planos de manutenção em andamento, bem como os ciclos de atualização estabelecidos de três a cinco anos, dependendo do datacenter.
- A maioria dos investimentos em tecnologia que não se alinham ao plano anual são abordados pelos esforços da TI invisível. Esses esforços normalmente são gerenciados por unidades de negócios e financiados por meio de despesas operacionais da unidade de negócios.

## <a name="future-state"></a>Estado futuro

As seguintes alterações estão previstas nos próximos vários anos:

- O CIO está liderando um esforço para modernizar a política em dados pessoais e financeiros para dar suporte a futuras metas. Dois membros da equipe de governança de TI têm a visibilidade desse esforço.
- O CIO deseja usar a migração de nuvem como uma função de força para melhorar a consistência e a estabilidade entre unidades de negócios e geografias. No entanto, o estado futuro deve respeitar quaisquer requisitos de conformidade externos que exijam desvio de abordagens padrão por equipes de ti específicas.
- Se os experimentos iniciais no desenvolvimento de aplicativos e BI mostram os principais indicadores de sucesso, cada um gostaria de lançar soluções de produção em pequena escala para a nuvem de versão nos próximos 24 meses.
- A CIO e o CFO haviam atribuído um arquiteto e Vice-presidente de infraestrutura para criar um estudo de viabilidade e análise de custo. Esses esforços determinarão se a empresa pode e deve mover 5.000 ativos para a nuvem nos próximos 36 meses. Uma migração bem-sucedida permitiria que o CIO eliminasse dois data centers, reduzindo os custos em mais de 100 milhões de dólares durante o plano de cinco anos. Se três ou quatro datacenters podem enfrentar resultados semelhantes, o orçamento estará em branco novamente, fornecendo o orçamento da CIO para dar suporte a iniciativas mais inovadoras.
    custos ![On versus custos do Azure demonstrando um retorno de US $100 milhões nos próximos cinco anos, @ no__t-1
- Junto com essa economia de custos, a empresa planeja alterar o gerenciamento de alguns investimentos em ti Reposicionando a despesa de capital confirmada como uma despesa operacional dentro dela. Essa alteração fornecerá maior controle de custo que poderá usar para acelerar as outras iniciativas planejadas.

## <a name="next-steps"></a>Próximas etapas

A empresa desenvolveu uma política corporativa para formar a implementação de governança. A política corporativa conduz muitas das decisões técnicas.

> [!div class="nextstepaction"]
> [Examinar a política corporativa inicial](./initial-corporate-policy.md)
