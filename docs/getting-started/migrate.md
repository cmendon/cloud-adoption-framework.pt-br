---
title: Iniciar uma jornada de migração na nuvem no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comece uma jornada de migração na nuvem no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 8870f5ebeab855ec841ed00d109245a1efdeff20
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048311"
---
# <a name="begin-a-cloud-migration-journey-in-azure"></a>Iniciar uma jornada de migração na nuvem no Azure

Use o Microsoft Cloud a estrutura de adoção do Azure para iniciar uma jornada de migração na nuvem. Essa estrutura fornece diretrizes abrangentes para a transição de cargas de trabalho de aplicativo herdadas para a nuvem usando tecnologias inovadoras baseadas em nuvem.

## <a name="executive-summary"></a>Resumo executivo

A estrutura de adoção de nuvem ajuda os clientes a empreender uma jornada de adoção de nuvem simplificada. Essa estrutura contém informações detalhadas sobre uma jornada de adoção de nuvem de ponta a ponta, começando com resultados de negócios direcionados e, em seguida, alinhando a preparação e as avaliações da nuvem com os objetivos de negócios claramente definidos. Esses resultados são obtidos por meio de um caminho definido para a adoção da nuvem. Com a adoção baseada em migração, o caminho definido se concentra em grande parte da migração de cargas de trabalho locais para a nuvem. Às vezes, essa jornada inclui modernização de cargas de trabalho para aumentar o retorno do investimento do esforço de migração.

Essa estrutura foi projetada principalmente para arquitetos de nuvem e as equipes de estratégia de nuvem que lideram os esforços de adoção de nuvem. No entanto, muitos tópicos nessa estrutura são relevantes para outras funções em toda a empresa e ti. Os arquitetos de nuvem geralmente servem como facilitadores para envolver cada uma das funções relevantes. Este resumo executivo foi projetado para preparar as várias funções antes de facilitar as conversas.

> [!NOTE]
> Atualmente, essa diretriz é uma visualização pública. A terminologia, as abordagens e as diretrizes estão sendo totalmente testadas com clientes, parceiros e equipes da Microsoft durante essa visualização. Como tal, o Sumário e a orientação podem mudar um pouco ao longo do tempo.

## <a name="motivations"></a>Motivações

As migrações na nuvem podem ajudar as empresas a alcançar seus resultados comerciais desejados. Desmarque a comunicação de motivações, os drivers de negócios e as medidas de sucesso são conceitos importantes para tomar decisões inteligentes durante os esforços de migração na nuvem. A tabela a seguir classifica as motivações para facilitar essa conversa. Supõe-se que a maioria das empresas terá motivações em cada classificação. O objetivo desta tabela é não limitar os resultados, mas, em vez disso, facilitar a priorização dos objetivos e das motivações gerais:

<!-- markdownlint-disable MD033 -->

|Eventos comerciais críticos | Motivações de migração | Motivações de inovação |
|---------|---------|---------|
| Saída do datacenter<br/><br/>Fusões, aquisição ou divestiture<br/><br/>Reduções em despesas de capital<br/><br/>Fim do suporte para tecnologias de missão crítica<br/><br/>Resposta às alterações de conformidade regulatória<br/><br/>Atender aos novos requisitos de soberania de dados<br/><br/>Reduzir as interrupções e melhorar a estabilidade da ti|Redução de custos<br/><br/>Redução no fornecedor ou na complexidade técnica<br/><br/>Otimização de operações internas<br/><br/>Aumentar a agilidade dos negócios<br/><br/>Preparar-se para novos recursos técnicos<br/><br/>Dimensionar para atender às demandas de mercado<br/><br/>Dimensionar para atender às demandas geográficas|Preparar-se para novos recursos técnicos<br/><br/>Crie novos recursos técnicos<br/><br/>Dimensionar para atender às demandas de mercado<br/><br/>Dimensionar para atender às demandas geográficas<br/><br/>Melhorar experiências/compromissos do cliente<br/><br/>Transformar produtos ou serviços<br/><br/>Interromper o mercado com novos produtos ou serviços|

<!-- markdownlint-enable MD033 -->

Quando uma resposta a eventos de negócios críticos é a prioridade mais alta, é importante envolver a [implementação na nuvem](#cloud-implementation) desde o início, geralmente em paralelo com os esforços de estratégia e planejamento. Adotar essa abordagem requer uma mentalidade de crescimento e uma disposição para melhorar iterativamente os processos, com base nas lições aprendidas.

Quando as motivações de migração são uma prioridade, a [estratégia e o planejamento](#cloud-strategy-and-planning) vão desempenhar uma função vital no início do processo. No entanto, é altamente recomendável que a [implementação](#cloud-implementation) da primeira carga de trabalho seja conduzida em paralelo com o planejamento, para ajudar a equipe a entender e planejar as curvas de aprendizado associadas à nuvem.

Quando as motivações de inovação são a mais alta prioridade, a estratégia e o planejamento exigirão investimentos adicionais no início do processo para garantir o equilíbrio entre o portfólio e o alinhamento inteligente do investimento feito durante a nuvem. Para obter mais informações sobre como concretizar motivações de inovação, consulte [entender a jornada de inovação](./innovate.md).

Preparar todos os participantes no esforço de migração com um reconhecimento das motivações garantirá decisões mais inteligentes. A metodologia de migração a seguir descreve como a Microsoft sugere que os clientes orientem essas decisões em uma metodologia consistente.

## <a name="migration-approach"></a>Abordagem de migração

A estrutura de adoção de nuvem estabelece um constructo de alto nível de plano, pronto e adotado para agrupar os tipos de esforço necessários em qualquer adoção de nuvem. Esse resumo executivo se baseia nesse fluxo de alto nível para estabelecer processos iterativos que podem facilitar o aumento/deslocamento/otimização de esforços e esforços de modernização em uma única abordagem em todas as atividades **de** migração na nuvem.

Essa abordagem consiste em duas metodologias ou áreas de foco: estratégia de nuvem & planejamento e implementação de nuvem. A [motivação](#motivations) ou o resultado comercial desejado para uma migração na nuvem geralmente determina quanto uma equipe deve investir em [estratégia e planejamento](#cloud-strategy-and-planning) e [implementação](#cloud-implementation). Essas motivações também podem influenciar as decisões para executar cada uma sequencialmente ou em paralelo.

## <a name="cloud-implementation"></a>Implementação de nuvem

A implementação de nuvem é um processo iterativo para migrar e modernizar o espaço digital em alinhamento com resultados de negócios direcionados e controles de gerenciamento de alterações. Durante cada iteração, as cargas de trabalho são migradas ou modernizadas em alinhamento com a estratégia e o plano. As decisões sobre IaaS, PaaS ou híbrido são feitas durante a fase avaliar para controle e execução otimizados. Essas decisões orientarão as ferramentas usadas durante a fase de migração. Esse modelo pode ser usado com a estratégia e o planejamento mínimos. No entanto, para garantir o maior retorno de negócios, é altamente recomendável que a ti e a empresa se alinhem em uma estratégia clara e planejem o guia das atividades de implementação.

![Metodologia de implementação na nuvem da estrutura de adoção da nuvem](../_images/operational-transformation-migrate.png)

O foco desse esforço é a migração ou a modernização de cargas de trabalho. Uma carga de trabalho é uma coleção de infraestrutura, aplicativos e dados que, coletivamente, dá suporte a uma meta comercial comum ou à execução de um processo de negócios comum. Exemplos de cargas de trabalho podem incluir coisas como um aplicativo de linha de negócios, uma solução de folha de pagamento de RH, uma solução de CRM, um fluxo de trabalho de aprovação de documentos financeiros ou uma solução de business intelligence. As cargas de trabalho também podem incluir recursos técnicos compartilhados como um data warehouse que dá suporte a várias outras soluções. Em alguns casos, uma carga de trabalho pode ser representada por um único ativo, como um servidor independente, um aplicativo ou uma plataforma de dados.

As migrações de nuvem geralmente são consideradas um único projeto dentro de um programa mais amplo para simplificar as operações de ti, os custos ou a complexidade. A metodologia de implementação de nuvem ajuda a alinhar os esforços técnicos dentro de uma série de migrações de carga de trabalho a valores de negócios de nível mais alto descritos na estratégia e no plano de nuvem.

**Introdução:** Para começar a usar uma implementação de nuvem, o guia de [migração do Azure](../migrate/azure-migration-guide/index.md) e o [Guia de instalação do Azure](../ready/azure-setup-guide/index.md) descrevem as ferramentas e os processos de alto nível necessários para serem bem-sucedidos na execução de uma implementação de nuvem. Migrar sua primeira carga de trabalho usando esses guias ajudará a equipe a superar as curvas de aprendizado iniciais no início do processo de planejamento. Posteriormente, considerações adicionais devem ser dadas à [lista de verificação de escopo expandido](../migrate/expanded-scope/index.md), [práticas recomendadas de migração](../migrate/azure-best-practices/index.md) e consideração de [migração](../migrate/migration-considerations/index.md)para alinhar as diretrizes de linha de base com as restrições exclusivas, processos e equipe do seu esforço. estruturas e objetivos.

## <a name="cloud-strategy-and-planning"></a>Estratégia e planejamento de nuvem

Estratégia e planejamento de nuvem é uma metodologia que se concentra em alinhar resultados de negócios, prioridades e restrições para estabelecer uma estratégia de migração e um plano claros. O plano resultante (ou a pendência de migração) descreve a abordagem de migração e modernização em todo o portfólio de ti, que pode abranger data centers inteiros, várias cargas de trabalho ou diversas coleções de infraestrutura, aplicativos e dados. O gerenciamento adequado do portfólio de ti entre os esforços de implementação na nuvem ajudará a impulsionar os resultados de negócios desejados.

![Visão geral do Cloud Adoption Framework](../_images/caf-overview.png)

**Introdução:** O restante deste artigo prepara o leitor para a aplicação adequada da estratégia de nuvem e da metodologia de planejamento da estrutura de adoção de nuvem. Ele também descreve recursos adicionais e links que podem ajudar o leitor a adotar essa abordagem para orientar os esforços de implementação na nuvem.

### <a name="methodology-explained"></a>Metodologia explicada

A metodologia de planejamento e estratégia de nuvem da estrutura de adoção de nuvem baseia-se em uma abordagem incremental para a implementação em nuvem que se alinha às estratégias de tecnologia Agile, maturidade cultural com base nas abordagens de mentalidade de crescimento e estratégias orientadas por resultados de negócios. Essa metodologia consiste nos seguintes componentes de alto nível que orientam a implementação de cada estratégia.

Conforme ilustrado na imagem acima, essa estrutura alinha decisões estratégicas a um pequeno número de processos contidos, que operam dentro de um modelo iterativo. Enquanto descrito em um documento linear, espera-se que cada um dos processos a seguir seja maduro em paralelo com iterações da implementação da nuvem. Os links para cada processo ajudarão a definir o estado final e o meio de desenvolvimento para o estado final desejado:

- **[Plano](../strategy/index.md):** Quando a implementação técnica é alinhada com objetivos de negócios claros, é muito mais fácil medir e alinhar o sucesso entre vários esforços de implementação de nuvem, independentemente das decisões técnicas.
- **[Pronto](../ready/index.md):** Preparar os negócios, a cultura, as pessoas e o ambiente para alterações futuras leva a um sucesso em cada esforço e acelera a implementação e a alteração de projetos.
- **Adote:** Garanta a implementação adequada das alterações desejadas, em processos de negócios e de ti, para obter resultados de negócios.
  - **[Migrar](../migrate/index.md):** execução iterativa da [metodologia de implementação de nuvem](#cloud-implementation) aderir ao processo testado de avaliar, migrar, otimizar e proteger & gerenciar para criar um processo repetível para migrar cargas de trabalho.
  - **[Inovar](../innovate/index.md):** Conduza valor de negócios por meio de atividades de inovação que desbloqueiam novas habilidades técnicas e recursos de negócios expandidos.
- **[Controle](../govern/index.md):** Alinhe políticas corporativas a riscos tangíveis, atenuadas por meio de políticas, processos e ferramentas de governança baseadas em nuvem.
- **[Gerenciar](../manage/index.md):** Expanda as operações de ti para garantir que as soluções baseadas em nuvem possam ser operadas por meio de processos seguros e econômicos usando as ferramentas de operações modernas e de primeira nuvem.
- **[Organizar](../organize/index.md):** Alinhe pessoas e equipes para fornecer operações e adoção adequadas de nuvem.

Ao longo dessa experiência de migração, essa estrutura será usada para abordar a ambiguidade, gerenciar alterações e orientar equipes entre funções com a realização de resultados comerciais.

### <a name="common-cultural-changes-resulting-from-adherence-to-this-methodology"></a>Alterações culturais comuns resultantes da adesão a essa metodologia

O esforço para perceber os resultados de negócios desejados pode disparar ligeiras alterações na cultura da ti e em algum grau a cultura da empresa. A seguir estão algumas alterações culturais comuns vistas neste processo:

- A equipe de ti provavelmente adotará novas habilidades para dar suporte a cargas de trabalho na nuvem.
- A execução de uma migração de nuvem incentiva abordagens iterativas ou ágeis.
- A inclusão da governança de nuvem também tende a inspirar abordagens DevOpss.
- A criação de uma equipe de estratégia de nuvem pode levar a uma integração mais rígida entre os líderes de ti e de negócios.
- Coletivamente, essas mudanças tendem a levar a agilidade de ti e de negócios.

A mudança cultural não é uma meta da migração na nuvem nem da estrutura de adoção da nuvem, mas é um resultado mais experiente.
As alterações culturais não são guiadas diretamente, em vez disso, as alterações sutis na cultura são incorporadas às melhorias e abordagens do processo sugeridas em todas as diretrizes.

### <a name="common-technical-efforts-associated-with-this-methodology"></a>Esforços técnicos comuns associados a essa metodologia

Durante a implementação da estratégia de nuvem e planejar a equipe de ti, concentre-se em um grande percentual do tempo na migração de ativos digitais existentes para a nuvem. Durante esse esforço, as alterações mínimas de código são esperadas, mas geralmente podem ser limitadas a alterações de configuração. Em muitos casos, uma justificativa de negócios forte pode ser feita para modernização como parte da migração na nuvem.

### <a name="common-workload-examples"></a>Exemplos comuns de carga de trabalho

A estratégia de nuvem e o planejamento geralmente visam uma ampla coleção de cargas de trabalho e aplicativos. No portfólio, os tipos de aplicativos comuns ou de carga de trabalho normalmente são migrados. Seguem alguns exemplos:

- Aplicativos de linha de negócios
- Aplicativos voltados para o cliente
- Aplicativo de terceiros
- Plataformas de análise de dados
- Soluções distribuídas globalmente
- Soluções altamente escalonáveis

### <a name="common-technologies-migrated"></a>Tecnologias comuns migradas

As tecnologias migradas para a nuvem se expandem constantemente à medida que os provedores de nuvem adicionam novos recursos. Veja a seguir alguns exemplos das tecnologias normalmente vistas em um esforço de migração:

- Windows e SQL Server
- Bancos de dados Linux e OSS (software livre)
- Bancos de dados não estrutura/NoSQL
- SAP no Azure
- Análise (data warehouse, Data Lake)

## <a name="next-steps-lifecycle-solution"></a>Próximas etapas: solução de ciclo de vida

A estrutura de adoção de nuvem é uma solução de ciclo de vida. Ele foi projetado para ajudar os leitores que estão apenas começando sua jornada e também com leitores que estão profundamente em sua migração. Dessa forma, o conteúdo é bem específico ao contexto e ao público. As próximas etapas são mais bem alinhadas ao processo de alto nível que o leitor gostaria de melhorar em seguida.

> [!div class="nextstepaction"]
> [Estratégia](../strategy/index.md)
>
> [Plano](../plan/index.md)
>
> [Esteja](../ready/index.md)
>
> [Migrar](../migrate/index.md)
>
> [Inove](../innovate/index.md)
>
> [Indicadores](../govern/index.md)
>
> [Gerenciar](../manage/index.md)
>
> [Organizar](../organize/index.md)
