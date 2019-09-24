---
title: Avaliar a tolerância a riscos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação dos riscos de negócios associados a uma transformação de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 2b8bc595377b2748bd00f306659a46196115e91d
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223551"
---
# <a name="evaluate-risk-tolerance"></a>Avaliar a tolerância a riscos

Cada decisão empresarial gera novos riscos. Quaisquer tipos de investimentos criam riscos de perdas. Novos produtos ou serviços criam riscos de falha de mercado. Alterações nos produtos ou serviços atuais podem reduzir a participação de mercado. A transformação de nuvem não fornece uma solução mágico para o risco comercial diário. Pelo contrário, soluções conectadas (nuvem ou local) introduzem novos riscos. A implantação de ativos em qualquer instalação conectada à rede também amplia o perfil de ameaça potencial, expondo as vulnerabilidades de segurança a uma comunidade global muito mais ampla. Felizmente, os provedores de nuvem estão cientes das alterações, dos aumentos e da adição de riscos. Eles investem muito para reduzir e gerenciar esses riscos em nome de seus clientes.

Este artigo não objetiva discutir sobre os riscos de nuvem. Em vez disso, ele aborda os riscos de negócios associados a várias formas de transformação em nuvem. No decorrer do artigo, a discussão mudará o foco para analisar as maneiras de reconhecer a tolerância aos riscos empresariais.

<!-- markdownlint-disable MD026 -->

## <a name="what-business-risks-are-associated-with-a-cloud-transformation"></a>Quais riscos de negócios estão associados a uma transformação de nuvem?

Os riscos de negócios verdadeiros são baseados nos detalhes de transformações específicas. Vários riscos comuns fornecem um iniciador de conversa para entender os riscos específicos aos negócios.

> [!IMPORTANT]
> Antes de ler o seguinte, lembre-se de que cada um desses riscos pode ser gerenciado. O objetivo deste artigo é informar e preparar os leitores para discussões de gerenciamento de riscos mais produtivas.

- **Violação de dados:** O risco número um associado a qualquer transformação é a proteção de dados. Os vazamentos de dados podem causar danos significativos à sua empresa, levando à perda de clientes, diminuir os negócios ou até mesmo em responsabilidade jurídica. Quaisquer alterações na maneira como os dados são armazenados, processados ou usados geram riscos. As transformações na nuvem criam um alto grau de alteração em relação ao gerenciamento de dados, portanto, o risco não deve ser pouco levado. A [linha de base de segurança](../security-baseline/index.md), a classificação de [dados](./data-classification.md)e a [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization) podem ajudar a gerenciar esse risco.

- **Interrupção do serviço:** As operações de negócios e as experiências do cliente dependem muito das operações técnicas. As transformações de nuvem criarão alterações nas operações de ti. Em algumas organizações, essa alteração é pequena e facilmente ajustada. Em outras organizações, essas alterações podem exigir referramentas, novos treinamentos ou novas abordagens para dar suporte a operações de nuvem. Quanto maior a alteração, maior o impacto potencial sobre as operações de negócios e a experiência do cliente. O gerenciamento desse risco exigirá o envolvimento dos negócios no planejamento da transformação. O planejamento de versão e a primeira seleção de carga de trabalho no artigo de [racionalização incremental](../../digital-estate/rationalize.md#incremental-rationalization) discutem maneiras de escolher cargas de trabalho para projetos de transformação. A função da empresa nessa atividade é comunicar o risco de operações de negócios de alterar cargas de trabalho priorizadas. Ajudar a ti a escolher cargas de trabalho que tenham um impacto menor nas operações reduzirá o risco geral.

- **Controle de orçamento:** Os modelos de custo mudam na nuvem. Essa alteração pode criar riscos associados a estouros de custo ou aumentos no custo dos produtos vendidos (COGS), especialmente nas despesas operacionais diretamente atribuídas. Quando a empresa trabalha junto com ela, é viável criar transparência em relação aos custos e serviços consumidos por várias unidades de negócios, programas ou projetos. O [Gerenciamento de custos](../cost-management/index.md) fornece exemplos de como os negócios e de ti podem ser parceiros neste tópico.

Esses riscos apresentados são alguns dos mais comuns mencionados pelos clientes. A equipe de governança de nuvem e as equipes de adoção de nuvem podem começar a desenvolver um perfil de risco, pois as cargas de trabalho são migradas e pronto para a versão de produção. Esteja preparado para conversas a fim de definir, refinar e gerenciar riscos com base nos resultados de negócios desejados e no esforço de transformação.

## <a name="understanding-risk-tolerance"></a>Reconhecer a tolerância de risco

Identificar o risco é um processo bastante direto. Os riscos relacionados a ti geralmente são padrão entre os setores. No entanto, a tolerância para esses riscos é específica para cada organização. Esse é o ponto em que as conversas entre corporativo e TI tendem a ficar suspensas. Basicamente, cada lado da conversa tem conhecimentos e pontos de vistas distintos. As comparações e perguntas a seguir são desenvolvidas para iniciar conversas que ajudam cada parte a melhor reconhecer e calcular a tolerância de risco.

## <a name="simple-use-case-for-comparison"></a>Caso de uso simples para comparação

Para ajudar a reconhecer a tolerância de risco, examinaremos os dados do cliente. Se uma empresa em qualquer setor postar dados do cliente em um servidor desprotegido, o risco técnico de que os dados que estão sendo comprometidos ou roubados é praticamente o mesmo. No entanto, a tolerância da empresa para esse risco variará de forma invariável com base na natureza e no valor potencial dos dados.

- As empresas do setor de saúde e finanças nos Estados Unidos são regidas por rigorosos requisitos de conformidade de terceiros. Supõe-se que os dados pessoais ou os dados relacionados à área de saúde são extremamente confidenciais. Haverá graves consequências para esses tipos de empresas, caso estejam envolvidas no cenário de riscos acima mencionado. A tolerância será extremamente baixa. Todos os dados de clientes publicados dentro ou fora da rede precisarão ser regidos por essas políticas de conformidade de terceiros.
- Uma empresa de jogos cujos dados do cliente são limitados a um nome de usuário, tempos de reprodução e pontuações altas não é tão provável que sofra conseqüências significativas além da perda de reputação, caso eles se envolvam no comportamento arriscado acima. Embora os dados não seguros estejam em risco, o impacto desse risco é pequeno. Portanto, a tolerância para o risco, nesse caso, é alta.
- Uma empresa de médio porte que fornece serviços de limpeza de carpetes a milhares de clientes se enquadraria entre essas duas tolerâncias extremas. Lá, os dados do cliente podem ser mais robustos, contendo detalhes como endereço ou número de telefone. Ambos poderiam ser considerados dados pessoais e devem ser protegidos. No entanto, pode não haver requisitos de governança específicos exigindo a proteção dos dados. De uma perspectiva de TI, a resposta é simples, proteja os dados. De uma perspectiva corporativa, pode não ser tão simples. O corporativo precisaria de mais detalhes antes de determinar um nível de tolerância para esse risco.

A próxima seção compartilha algumas perguntas de exemplo que podem ajudar a empresa a determinar um nível de tolerância a riscos para o caso de uso acima ou outros.

## <a name="risk-tolerance-questions"></a>Perguntas sobre tolerância de risco

Esta seção lista as perguntas de provocativa de conversa em três categorias: impacto de perda, probabilidade de perda e custos de correção. Quando a empresa e o parceiro de ti atendem a cada uma dessas áreas, a decisão de se empenhar no gerenciamento de riscos e na tolerância geral a um risco específico pode ser facilmente determinada.

**Impacto de perda:** Perguntas para determinar o impacto de um risco. Essas perguntas podem ser difíceis de responder. Quantificar o impacto é o ideal, porém, algumas vezes a própria conversa é suficiente para reconhecer a tolerância. Os intervalos também são aceitáveis, especialmente se incluem suposições que determinam esses intervalos.

- Esse risco poderia violar os requisitos de conformidade de terceiros?
- Esse risco poderia violar as políticas corporativas internas?
- Esse risco pode causar a perda de vida, a propriedade
- Esse risco poderia prejudicar clientes ou participação de mercado? Nesse caso, esse custo pode ser quantificado?
- Esse risco poderia criar experiências negativas para o cliente? Essas experiências podem afetar as vendas ou a receita?
- Este risco poderia criar uma nova responsabilidade jurídica? Em caso afirmativo, há uma precedência para compensação por danos nesses tipos de casos?
- Esse risco poderia interromper as operações de negócios? Em caso afirmativo, por quanto tempo as operações ficariam inativas?
- Isso poderia resultar em operações de negócios lentas? Em caso afirmativo, qual é a velocidade e quanto tempo?
- Nesse estágio da transformação, esse é um risco único ou será repetido?
- O risco aumenta ou diminui em frequência, na medida em que a transformação avança?
- O risco aumenta ou diminui em probabilidade ao longo do tempo?
- O risco é por natureza sensível ao tempo? O risco vai passar ou agravar, se não for resolvido?

Essas perguntas básicas conduzirão a muitas outras. Após explorar um diálogo produtivo, é recomendável que os riscos relevantes sejam registrados e, quando possível, quantificados.

**Custos de correção de risco:** Perguntas para determinar o custo da remoção ou minimização do risco. Essas perguntas podem ser bastante diretas, especialmente quando representadas em faixa.

- Há uma solução clara e o que isso custa?
- Há opções para impedir ou minimizar esse risco? Qual é a faixa de custo para essas soluções?
- O que é necessário do corporativo para escolher a solução clara e ideal?
- O que é necessário do corporativo para validar os custos?
- Que outros benefícios podem vir da solução que removeria esse risco?

Essas perguntas sobre simplificam as soluções técnicas necessárias para gerenciar ou remover riscos. No entanto, essas questões comunicam essas soluções de maneira que a empresa possa integrar-se rapidamente a um processo de decisão.

**Probabilidade de perda:** Perguntas para determinar a probabilidade do risco tornar-se realidade. Essa é a área mais difícil de quantificar. Em vez disso, é recomendável que a equipe de governança de nuvem crie categorias para comunicar a probabilidade, com base nos dados de suporte. As perguntas a seguir podem ajudar a criar categorias que sejam significativas para a equipe.

- Alguma pesquisa foi realizada acerca da probabilidade desse risco ser realizado?
- O fornecedor pode fornecer referências ou estatísticas sobre a probabilidade de um impacto?
- Há outras empresas do setor relevante ou vertical que foram atingidas por esse risco?
- Pesquise mais, há outras empresas em geral que foram atingidas por esse risco?
- Esse risco é exclusivo relacionado a algo que a empresa tem feito inadequadamente?

Depois de responder a essas perguntas, juntamente com as perguntas determinadas pela equipe de governança de nuvem, os agrupamentos de probabilidade provavelmente surgirão. A seguir, estão alguns exemplos de agrupamento para ajudar a começar:

- **Nenhuma indicação:** Não foi concluída uma pesquisa suficiente para determinar a probabilidade.
- **Baixo risco:** A pesquisa atual indica que é improvável que o risco seja concretizado.
- **Risco futuro:** A probabilidade atual é baixa. No entanto, a adoção contínua exigiria uma nova análise.
- **Risco médio:** É provável que o risco afete os negócios.
- **Alto risco:** Ao longo do tempo, é cada vez mais provável que os negócios percebam esse risco.
- **Risco de declínio:** O risco é de médio a alto. No entanto, as ações nela ou a empresa estão reduzindo a probabilidade de um impacto.

**Determinando a tolerância:**

Os três conjuntos de perguntas acima devem fornecer dados suficientes para determinar as tolerâncias iniciais. Quando o risco e a probabilidade são baixos e os custos de correção de risco são altos, é improvável que os negócios invistam na correção. Quando o risco e a probabilidade são altos, é provável que os negócios considerem um investimento, desde que os custos não excedam os riscos potenciais.

## <a name="next-steps"></a>Próximas etapas

Esse tipo de conversa pode ajudar o corporativo e a TI a avaliarem a tolerância de maneira mais eficaz. Essas conversas podem ser usadas durante a criação de políticas de MVP e durante análises de políticas incrementais.

> [!div class="nextstepaction"]
> [Definir política corporativa](./policy-definition.md)
