---
title: Exemplos de resultados fiscais
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Exemplos de resultados fiscais
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 350b13e993d2130dc72482cbe7cafb3823b6a4d8
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048361"
---
# <a name="examples-of-fiscal-outcomes"></a>Exemplos de resultados fiscais

No nível mais alto, as conversas fiscais são compostas por três conceitos básicos:

- **Receita:** Mais dinheiro entrará em negócios como resultado das vendas de bens ou serviços.
- **Custo:** Menos dinheiro será gasto na criação, no marketing, nas vendas ou na entrega de bens ou serviços.
- **Lucro:** Embora eles sejam raros, algumas transformações podem aumentar a receita e diminuir os custos. Esse é um resultado de lucro.

O restante deste artigo explica esses resultados fiscais no contexto de uma transformação de nuvem.

> [!NOTE]
> Os exemplos a seguir são hipotéticos e não devem ser considerados uma garantia de Devoluções ao adotar qualquer estratégia de nuvem.

## <a name="revenue-outcomes"></a>Resultados da receita

### <a name="new-revenue-streams"></a>Novos fluxos de receita

A nuvem pode ajudar a criar oportunidades para entregar novos produtos aos clientes ou fornecer produtos existentes de uma maneira nova. Novos fluxos de receita são inovadores, empresariais e empolgantes para muitas pessoas no mundo da empresa. Novos fluxos de receita também estão sujeitos a falhas e são considerados por muitas empresas para serem de alto risco. Quando os resultados relacionados à receita são propostos por ele, provavelmente haverá resistência. Para adicionar credibilidade a esses resultados, entre em parceria com um líder de negócios que é uma inovadora comprovada. A validação do fluxo de receita no início do processo ajuda a evitar obstáculos da empresa.

- **Exemplo:** Uma empresa vem vendendo livros por mais de uma centena de anos. Um funcionário da empresa percebe que o conteúdo pode ser entregue eletronicamente. O funcionário cria um dispositivo que pode ser vendido na livraria, o que permite que os mesmos livros sejam baixados diretamente, levando $X em novas vendas de livros.

### <a name="revenue-increases"></a>A receita aumenta

Com escala global e alcance digital, a nuvem pode ajudar as empresas a aumentarem as receitas de fluxos de receita existentes. Geralmente, esse tipo de resultado vem de um alinhamento com a liderança de vendas ou de marketing.

- **Exemplo:** Uma empresa que vende widgets pode vender mais widgets, se os vendedores pudessem acessar com segurança o catálogo digital e os níveis de estoque da empresa. Infelizmente, esses dados só estão no sistema ERP da empresa, que pode ser acessado somente por meio de um dispositivo conectado à rede. A criação de uma fachada de serviço para a interface com o ERP e a exposição da lista de catálogos e dos níveis de estoque não confidenciais a um aplicativo na nuvem permitiria que os vendedores acessassem os dados necessários enquanto estiverem no local com um cliente. Estender Active Directory locais usando Azure Active Directory (AD do Azure) e integrar o acesso baseado em função ao aplicativo permitiria que a empresa ajudasse a garantir que os dados permaneçam seguros. Este projeto simples pode afetar a receita de uma linha de produtos existente em _x%_ .

### <a name="profit-increases"></a>Aumento do lucro

Raramente, um único esforço aumenta a receita e reduz os custos simultaneamente. No entanto, quando isso acontecer, alinhe as instruções de resultado de um ou mais resultados de receita com um ou mais dos resultados de custo para comunicar o resultado desejado.

## <a name="cost-outcomes"></a>Resultados de custo

### <a name="cost-reduction"></a>Redução de custo

A computação em nuvem pode reduzir as despesas de capital para hardware e software, configurar data centers, executar data centers locais e assim por diante. Os custos de racks de servidores, eletricidade ininterrupta para energia e resfriamento e especialistas em ti para gerenciar a infra-estrutura se somam rapidamente. Desligar um datacenter pode reduzir os compromissos de despesas de capital. Isso é comumente conhecido como "saindo do datacenter Business". A redução de custos normalmente é medida em dólares no orçamento atual, o que pode abranger um a cinco anos, dependendo de como o CFO gerencia as finanças.

- **Exemplo #1:** O datacenter de uma empresa consome um grande percentual do orçamento de ti anual. Ele opta por conduzir uma migração na nuvem e faz a transição dos ativos desse datacenter para soluções IaaS (infraestrutura como serviço), criando uma redução de custos de três anos.
- **Exemplo #2:** Uma empresa controladora adquiriu recentemente uma nova empresa. Na aquisição, os termos ditam que a nova entidade deve ser removida dos data centers atuais dentro de seis meses. Não fazer isso resultará em uma multa de 1 milhão USD por mês para a empresa controladora. Mover os ativos digitais para a nuvem em uma migração de nuvem pode permitir uma desativação rápida dos ativos antigos.
- **Exemplo #3:** Uma empresa de imposto sobre renda que atende aos consumidores enfrenta 70% de sua receita anual durante os três primeiros meses do ano. No restante do ano, seu grande investimento em ti fica relativamente inativo. Uma migração de nuvem pode permitir que a ti implante a capacidade de computação/hospedagem necessária para esses três meses. Durante os nove meses restantes, os custos de IaaS poderiam ser reduzidos significativamente por meio da redução do volume de computação.

### <a name="example-coverdell"></a>Exemplo: Coverdell

A Coverdell moderniza sua infraestrutura para gerar recordes de economias com o Azure. A decisão do Coverdell de investir no Azure, e para unir sua rede de sites, aplicativos, dados e infraestrutura nesse ambiente, levou a uma economia mais econômica do que a empresa já era esperada. A migração para um ambiente somente com Azure eliminou 54.000 USD em custos mensais dos serviços de colocação. Com a nova infraestrutura corporativa da empresa sozinha, a Coverdell espera economizar US $1 milhão dólares nos próximos dois a três anos.

> "Ter acesso à pilha de tecnologia do Azure abre a porta de algumas soluções escalonáveis, fáceis de implementar e altamente disponíveis que são econômicas. Isso permite que nossos arquitetos sejam muito mais criativos com as soluções que eles fornecem. "  
> Ryan Sorensen  
> Diretor de desenvolvimento de aplicativos e arquitetura empresarial  
> Coverdell

### <a name="cost-avoidance"></a>Prevenção de custos

O encerramento de um datacenter também pode fornecer uma redução de custos, impedindo ciclos de atualização futura. Um ciclo de atualização é o processo de aquisição de novos hardwares e softwares, a fim de substituir sistemas locais antigos. No Azure, o hardware e o sistema operacional são rotineiramente mantidos, corrigidos e atualizados sem custo adicional aos clientes. Isso permite que um CFO remova os gastos futuros planejados de previsões financeiras de longo prazo. A redução de custos é medida em dólares. Ele difere da redução de custos, geralmente concentrando-se em um orçamento futuro que ainda não foi totalmente aprovado.

- **Exemplo:** O datacenter de uma empresa está ativo para uma renovação de concessão em seis meses. O datacenter está em serviço por oito anos. Quatro anos atrás, todos os servidores foram atualizados e virtualizados, custando a empresa milhões de dólares. No próximo ano, a empresa planeja atualizar o hardware e o software novamente. Migrar os ativos nesse datacenter como parte de uma migração de nuvem permitiria evitar custos removendo a atualização planejada do orçamento previsto do próximo ano. Ela também poderia produzir uma redução de custos ao diminuir ou eliminar os custos de concessão de imóveis.

### <a name="capital-expenses-vs-operating-expenses"></a>Despesas de capital versus despesas operacionais

Antes de discutir os resultados do custo, é importante entender as duas opções de custo principal: despesas de capital e despesas operacionais.

Os termos a seguir ajudarão você a entender as diferenças entre as despesas de capital e as despesas operacionais durante as discussões de negócios sobre uma jornada de transformação.

- **Capital** é o dinheiro e os ativos de propriedade de uma empresa para contribuir para uma finalidade específica, como aumentar a capacidade do servidor ou criar um aplicativo.
- As **despesas de capital** geram benefícios em um longo período. Essas despesas geralmente são recorrentes e resultam na aquisição de ativos permanentes. A criação de um aplicativo pode ser qualificada como uma despesa de capital.
- As **despesas operacionais** são custos contínuos de fazer negócios. O consumo de serviços de nuvem em um modelo pago conforme o uso pode ser qualificado como uma despesa operacional.
- **Ativos** são recursos econômicos que podem ser de propriedade ou controlados para produzir valor. Servidores, data lagos e aplicativos podem ser considerados ativos.
- A **depreciação** é uma redução no valor de um ativo ao longo do tempo. Mais relevante para a despesa de capital versus a conversa de despesas operacionais, a depreciação é como os custos de um ativo são alocados entre os períodos em que são usados. Por exemplo, se você criar um aplicativo neste ano, mas for esperado ter uma vida útil média de cinco anos (como a maioria dos aplicativos comerciais), o custo da equipe de desenvolvimento e das ferramentas necessárias necessárias para criar e implantar a base de código seria depreciado uniformemente em cinco últimos.
- **Avaliação** é o processo de estimativa de valor de uma empresa. Na maioria dos setores, a avaliação é baseada na capacidade da empresa de gerar receita e lucro, respeitando os custos operacionais necessários para criar os bens que fornecem essa receita. Em alguns setores, como varejo ou em alguns tipos de transação, como patrimônio privado, ativos e depreciação podem desempenhar uma grande parte da avaliação da empresa.

Geralmente, é uma aposta segura de que vários executivos, incluindo o CIO (diretor de investimentos), debater o melhor uso de capital para aumentar a empresa na direção desejada. Dar ao CIO um meio de converter conversas de despesas de capital contenciosos em responsabilidade clara por despesas operacionais pode ser um resultado atraente por si só. Em muitos setores, os diretores financeiros buscam maneiras de associar melhor a responsabilidade fiscal ao custo das mercadorias vendidas.

No entanto, antes de associar qualquer jornada de transformação a esse tipo de capital versus conversão de despesas operacionais, é recomendável atender aos membros das equipes do CFO ou do CIO para ver qual estrutura de custo a empresa prefere. Em algumas organizações, reduzir as despesas de capital em favor das despesas operacionais é um resultado altamente *indesejável* . Como mencionado anteriormente, essa abordagem às vezes é vista em empresas de capital de varejo, de retenção e privadas que colocam um valor maior em modelos tradicionais de contabilidade de ativos, que colocam pouco valor em IP. Ele também é visto em organizações que tiveram experiências negativas ao terceirizar a equipe de ti ou outras funções no passado.

Se um modelo de despesa operacional for desejável, o exemplo a seguir poderá ser um resultado comercial viável:

- **Exemplo:** O Data Center da empresa está sendo depreciado no momento em _US $ x_ por ano para os próximos três anos. Espera-se que seja necessário um _US x_ adicional para atualizar o hardware no próximo ano. Podemos converter as despesas de capital em um modelo de despesa operacional em uma taxa par de _z USD_ por mês, permitindo melhor gerenciamento e responsabilidade pelos custos operacionais da tecnologia.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre os [resultados da agilidade](./agility-outcomes.md).

> [!div class="nextstepaction"]
> [Resultados da agilidade](./agility-outcomes.md)
