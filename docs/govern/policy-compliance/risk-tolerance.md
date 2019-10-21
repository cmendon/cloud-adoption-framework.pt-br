---
title: Avaliar a tolerância de risco
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação dos riscos de negócios associados a uma transformação de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 61f661a167b9a38a54a51dc9612a0b17df0bd0c3
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547180"
---
# <a name="evaluate-risk-tolerance"></a>Avaliar a tolerância de risco

Cada decisão de negócios cria novos riscos. Fazer um investimento em qualquer coisa cria o risco de perdas. Novos produtos ou serviços criam riscos de falha no mercado. As alterações nos produtos ou serviços atuais podem reduzir a participação no mercado. A transformação de nuvem não fornece uma solução mágico para o risco comercial diário. Para o contrário, as soluções conectadas (nuvem ou local) apresentam novos riscos. A implantação de ativos em qualquer recurso conectado à rede também expande o perfil de ameaça potencial expondo os pontos fracos de segurança a uma comunidade global muito mais ampla. Felizmente, os provedores de nuvem estão cientes das alterações, dos aumentos e da adição de riscos. Eles investem muito para reduzir e gerenciar esses riscos em nome de seus clientes.

Este artigo não se concentra em riscos de nuvem. Em vez disso, ele aborda os riscos de negócios associados a várias formas de transformação em nuvem. Posteriormente neste artigo, a discussão mudará o foco para discutir maneiras de compreender a tolerância a riscos dos negócios.

<!-- markdownlint-disable MD026 -->

## <a name="what-business-risks-are-associated-with-a-cloud-transformation"></a>Quais riscos de negócios estão associados a uma transformação de nuvem?

Os riscos de negócios verdadeiros são baseados nos detalhes de transformações específicas. Vários riscos comuns fornecem um iniciador de conversa para entender os riscos específicos aos negócios.

> [!IMPORTANT]
> Antes de ler o seguinte, lembre-se de que cada um desses riscos pode ser gerenciado. O objetivo deste artigo é informar e preparar os leitores para discussões de gerenciamento de riscos mais produtivas.

- **Violação de dados:** O principal risco associado a qualquer transformação é uma violação de dados. Os vazamentos de dados podem causar danos significativos à sua empresa, levando à perda de clientes, diminuir os negócios ou até mesmo em responsabilidade jurídica. As alterações na maneira como os dados são armazenados, processados ou usados geram risco. As transformações na nuvem criam um alto grau de alteração em relação ao gerenciamento de dados, portanto, o risco não deve ser pouco levado. A [linha de base de segurança](../security-baseline/index.md), a classificação de [dados](./data-classification.md)e a [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization) podem ajudar a gerenciar esse risco.

- **Interrupção do serviço:** As operações de negócios e as experiências do cliente dependem muito das operações técnicas. As transformações de nuvem criarão alterações nas operações de ti. Em algumas organizações, essa alteração é pequena e facilmente ajustada. Em outras organizações, essas alterações podem exigir referramentas, novos treinamentos ou novas abordagens para dar suporte a operações de nuvem. Quanto maior a alteração, maior o impacto potencial sobre as operações de negócios e a experiência do cliente. O gerenciamento desse risco exigirá o envolvimento dos negócios no planejamento da transformação. O planejamento de versão e a primeira seleção de carga de trabalho no artigo de [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization) discutem maneiras de escolher cargas de trabalho para projetos de transformação. A função da empresa nessa atividade é comunicar o risco de operações de negócios de alterar cargas de trabalho priorizadas. Ajudar a ti a escolher cargas de trabalho que tenham um impacto menor nas operações reduzirá o risco geral.

- **Controle de orçamento:** Os modelos de custo mudam na nuvem. Essa alteração pode criar riscos associados a estouros de custo ou aumentos no custo dos produtos vendidos (COGS), especialmente nas despesas operacionais diretamente atribuídas. Quando a empresa trabalha junto com ela, é viável criar transparência em relação aos custos e serviços consumidos por várias unidades de negócios, programas ou projetos. O [Gerenciamento de custos](../cost-management/index.md) fornece exemplos de como os negócios e de ti podem ser parceiros neste tópico.

Os itens acima são alguns dos riscos mais comuns mencionados pelos clientes. A equipe de governança de nuvem e as equipes de adoção de nuvem podem começar a desenvolver um perfil de risco, pois as cargas de trabalho são migradas e pronto para a versão de produção. Esteja preparado para conversas a fim de definir, refinar e gerenciar riscos com base nos resultados de negócios desejados e no esforço de transformação.

## <a name="understanding-risk-tolerance"></a>Noções básicas sobre a tolerância a riscos

A identificação de risco é um processo bastante direto. Os riscos relacionados a ti geralmente são padrão entre os setores. No entanto, a tolerância para esses riscos é específica para cada organização. Esse é o ponto onde as conversas de negócios e de ti tendem a ficar desligadas. Cada lado da conversa está basicamente falando em um idioma diferente. As seguintes comparações e perguntas foram projetadas para iniciar conversas que ajudam cada parte a entender melhor e calcular a tolerância a riscos.

## <a name="simple-use-case-for-comparison"></a>Caso de uso simples para comparação

Para ajudar a entender a tolerância a riscos, vamos examinar os dados do cliente. Se uma empresa em qualquer setor postar dados do cliente em um servidor desprotegido, o risco técnico de que os dados que estão sendo comprometidos ou roubados é praticamente o mesmo. No entanto, a tolerância da empresa para esse risco variará de forma invariável com base na natureza e no valor potencial dos dados.

- As empresas no setor de saúde e Finanças na Estados Unidos, são governadas por requisitos de conformidade de terceiros rígidos. Supõe-se que os dados pessoais ou os dados relacionados à área de saúde são extremamente confidenciais. Há sérias conseqüências para esses tipos de empresas, se estiverem envolvidas no cenário de riscos acima. Sua tolerância será extremamente baixa. Qualquer dado de cliente publicado dentro ou fora da rede precisará ser regido por essas políticas de conformidade de terceiros.
- Uma empresa de jogos cujos dados do cliente são limitados a um nome de usuário, tempos de reprodução e pontuações altas não é tão provável que sofra conseqüências significativas além da perda de reputação, caso eles se envolvam no comportamento arriscado acima. Embora os dados não seguros estejam em risco, o impacto desse risco é pequeno. Portanto, a tolerância para o risco, nesse caso, é alta.
- Uma empresa de médio porte que fornece serviços de limpeza de carpetes a milhares de clientes se enquadraria entre essas duas tolerâncias extremas. Lá, os dados do cliente podem ser mais robustos, contendo detalhes como endereço ou número de telefone. Ambos poderiam ser considerados dados pessoais e devem ser protegidos. No entanto, pode não haver nenhum requisito de governança específico obrigando a segurança dos dados. Da perspectiva de ti, a resposta é simples, protege os dados. Da perspectiva de negócios, talvez não seja tão simples. A empresa precisaria de mais detalhes antes de poder determinar um nível de tolerância para esse risco.

A próxima seção compartilha algumas perguntas de exemplo que podem ajudar a empresa a determinar um nível de tolerância a riscos para o caso de uso acima ou outros.

## <a name="risk-tolerance-questions"></a>Perguntas sobre tolerância de risco

Esta seção lista as perguntas de provocativa de conversa em três categorias: impacto de perda, probabilidade de perda e custos de correção. Quando a empresa e o parceiro de ti atendem a cada uma dessas áreas, a decisão de se empenhar no gerenciamento de riscos e na tolerância geral a um risco específico pode ser facilmente determinada.

**Impacto de perda:** Perguntas para determinar o impacto de um risco. Essas perguntas podem ser difíceis de responder. A quantificação do impacto é melhor, mas às vezes a conversa sozinha é suficiente para entender a tolerância. Os intervalos também são aceitáveis, especialmente se eles incluírem suposições que determinaram esses intervalos.

- Esse risco poderia violar os requisitos de conformidade de terceiros?
- Esse risco poderia violar as políticas corporativas internas?
- Esse risco pode causar a perda de vida, a propriedade
- Esse risco pode custar aos clientes ou à participação no mercado? Nesse caso, esse custo pode ser quantificado?
- Esse risco poderia criar experiências de clientes negativas? Essas experiências podem afetar as vendas ou a receita?
- Esse risco poderia criar uma nova responsabilidade legal? Nesse caso, há uma precedência para os prêmios de danos nesses tipos de casos?
- Esse risco pode parar as operações de negócios? Nesse caso, quanto tempo as operações ficarão inativas?
- Esse risco pode tornar as operações de negócios lentas? Em caso afirmativo, qual é a velocidade e quanto tempo?
- Nesse estágio da transformação, isso é um risco único ou será repetido?
- O risco aumenta ou diminui em frequência à medida que a transformação progride?
- O risco aumenta ou diminui em probabilidade ao longo do tempo?
- O tempo de risco é sensível por natureza? O risco será bem-sucedido ou pior, se não for resolvido?

Essas perguntas básicas resultarão em muito mais. Depois de explorar uma caixa de diálogo íntegra, é recomendável que os riscos relevantes sejam registrados e quando possível quantificar.

**Custos de correção de risco:** Perguntas para determinar o custo da remoção ou minimização do risco. Essas perguntas podem ser bem diretas, especialmente quando representadas em um intervalo.

- Há uma solução clara e o que isso custa?
- Há opções para impedir ou minimizar esse risco? Qual é o intervalo de custos para essas soluções?
- O que é necessário para a empresa selecionar a melhor solução clara?
- O que é necessário da empresa para validar os custos?
- Que outros benefícios podem vir da solução que removeria esse risco?

Essas perguntas sobre simplificam as soluções técnicas necessárias para gerenciar ou remover riscos. No entanto, essas perguntas comunicam essas soluções de maneiras que a empresa pode se integrar rapidamente a um processo de decisão.

**Probabilidade de perda:** Perguntas para determinar a probabilidade de que o risco se torne uma realidade. Essa é a área mais difícil de quantificar. Em vez disso, é recomendável que a equipe de governança de nuvem crie categorias para comunicar a probabilidade, com base nos dados de suporte. As perguntas a seguir podem ajudar a criar categorias que são significativas para a equipe.

- Alguma pesquisa foi feita com relação à probabilidade desse risco ser realizado?
- O fornecedor pode fornecer referências ou estatísticas sobre a probabilidade de um impacto?
- Há outras empresas no setor relevante ou vertical que foram atingidas por esse risco?
- Olhe ainda mais, existem outras empresas em geral que foram atingidas por esse risco?
- Esse risco é exclusivo para algo que esta empresa fez de forma ruim?

Depois de responder a essas perguntas, juntamente com as perguntas determinadas pela equipe de governança de nuvem, os agrupamentos de probabilidade provavelmente surgirão. A seguir estão alguns exemplos de agrupamento para ajudar a começar:

- **Nenhuma indicação:** Não foi concluída uma pesquisa suficiente para determinar a probabilidade.
- **Baixo risco:** A pesquisa atual indica que é improvável que o risco seja concretizado.
- **Risco futuro:** A probabilidade atual é baixa. No entanto, a adoção contínua exigiria uma nova análise.
- **Risco médio:** É provável que o risco afete os negócios.
- **Alto risco:** Ao longo do tempo, é cada vez mais provável que os negócios percebam esse risco.
- **Risco de declínio:** O risco é de médio a alto. No entanto, as ações nela ou a empresa estão reduzindo a probabilidade de um impacto.

**Determinando a tolerância:**

Os três conjuntos de perguntas acima devem alimentar dados suficientes para determinar as tolerâncias iniciais. Quando o risco e a probabilidade são baixos e os custos de correção de risco são altos, é improvável que os negócios invistam na correção. Quando o risco e a probabilidade são altos, é provável que os negócios considerem um investimento, desde que os custos não excedam os riscos potenciais.

## <a name="next-steps"></a>Próximos passos

Esse tipo de conversa pode ajudar a empresa e a ti a avaliar a tolerância com mais eficiência. Essas conversas podem ser usadas durante a criação de políticas MVP e durante as revisões de política incremental.

> [!div class="nextstepaction"]
> [Definir política corporativa](./policy-definition.md)
