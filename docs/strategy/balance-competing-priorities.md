---
title: Balancear as prioridades concorrentes
description: Descubra estratégias para balancear as prioridades concorrentes
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/04/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: ba70687627e81b58eb76cd69838abf1ebcdb6489
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092987"
---
# <a name="balance-competing-priorities"></a>Balancear as prioridades concorrentes

A embarcação em qualquer jornada de transformação digital funciona como uma função de força para os participantes, entre as equipes de negócios e tecnologia. O caminho para o sucesso é firmemente roteado na capacidade das organizações de balancear as prioridades concorrentes.

Semelhante a outras transformações digitais, a adoção de nuvem vai expor as prioridades concorrentes em todo o ciclo de vida de adoção. Assim como outras formas de transformação, a capacidade de encontrar o equilíbrio nessas prioridades terá um impacto significativo na realização do valor comercial. O balanceamento dessas prioridades concorrentes exigirá conversas abertas (e às vezes difíceis) entre as partes interessadas (e às vezes com colaboradores individuais).

Este artigo descreve algumas das prioridades concorrentes normalmente discutidas durante a execução de cada metodologia. Esperamos que essa conscientização avançada ajude a se preparar melhor para essas discussões ao desenvolver sua estratégia de adoção de nuvem.

![Visão geral do ciclo de vida de adoção](../_images/caf-overview.png)

As seções a seguir se alinham ao fluxo do Visual do ciclo de vida de adoção da nuvem acima. Mas é importante observar que a adoção da nuvem é iterativa (não um processo sequencial), essas prioridades concorrentes surgirão (e, às vezes, resurgirão) em vários pontos ao longo da jornada de adoção da nuvem.

## <a name="general-theme-of-the-cloud-adoption-framework-approach"></a>Tema geral da abordagem da estrutura de adoção de nuvem

As soluções monolíticos e o planejamento avançado são ambos criados em uma série de suposições que podem (ou não) provar a precisão ao longo do tempo. A adoção da nuvem é, em geral, uma nova experiência para os negócios e as equipes técnicas. Assim como na maioria das novas experiências ou oportunidades de aprendizado, há uma grande probabilidade de que essas suposições sejam comprovadas como falsas.

Seguir os princípios ágeis comprovados das decisões técnicas atrasadas é a abordagem preferida para a maioria das diretrizes nessa estrutura. Essa abordagem segue um padrão consistente: estabelecer um estado geral final, mover rapidamente para implementação inicial, testar e validar suposições, refatorar antecipadamente para tratar suposições. Esse tipo de mentalidade de crescimento maximiza o aprendizado e minimiza o risco para o valor comercial. Mas essa mentalidade requer um grau de conforto com ambigüidade.

Às vezes, a ambiguidade pode ser scarier (ou mais perigosa) do que falsas suposições. Embora essa estrutura se Desaprenda e resolva a ambiguidade durante a execução, há muitas situações que exigem que a equipe se Desaprenda com as abordagens baseadas em análise ou em pressuposição. As seções a seguir tentarão ilustrar pelo menos um "exemplo de escopo expandido" em cada seção para ilustrar os horários em que uma segunda iteração mais profunda seria valiosa.

## <a name="balance-during-strategy"></a>Saldo durante a estratégia

O objetivo principal da metodologia de estratégia é desenvolver o alinhamento entre os participantes. Uma vez definido, essa posição estratégica alinhará comportamentos em cada uma das metodologias para garantir que as decisões técnicas alinhem os resultados de negócios desejados. Promover o alinhamento entre os participantes cria um conjunto comum de prioridades concorrentes: **profundidade de justificativa** versus **tempo para impacto nos negócios**.

**Prioridades concorrentes:**

- **Profundidade de justificativa**: os participantes geralmente querem uma análise financeira profunda e uma justificativa de negócios completa para se sentir confortável em alinhar a uma direção estratégica. Infelizmente, esse nível de análise pode exigir um período de tempo estendido para permitir a coleta e a análise de dados.
- **Impacto do tempo para os negócios**: por outro lado, os participantes costumam ser responsabilizados por fornecer resultados de negócios dentro de quadros de tempo definidos. A análise e a avaliação demoradas podem colocar esses resultados em risco antes que o trabalho técnico seja iniciado.

**Escopo mínimo:** Encontrar esse equilíbrio exige discussões entre os participantes no início do processo. A metodologia de estratégia sugere limitar o escopo do alinhamento durante esse esforço inicial. Na abordagem sugerida, os participantes concentram-se no alinhamento em um conjunto de motivações principais, resultados mensuráveis e uma justificativa de negócios de alto nível. É recomendável que os participantes, em seguida, confirmam rapidamente um pequeno número de projetos iniciais ou pilotos para impulsionar as oportunidades de aprendizado necessárias.

**Exemplo de escopo expandido:** Se a análise de negócios inicial indicar um alto risco de afetar negativamente os negócios, os participantes poderão precisar reduzir e avaliar com mais cautela uma análise mais profunda durante a justificativa de negócios.

## <a name="balance-during-plan"></a>Saldo durante o plano

Semelhante às prioridades da estratégia, durante o planejamento, há a necessidade de balancear: profundidade do planejamento inicial vs. decisões técnicas atrasadas.

**Prioridades concorrentes:**

- A **profundidade do planejamento inicial** sobre a implementação técnica na nuvem geralmente contém um grande número de suposições. Especialmente quando a equipe tem lacunas de habilidades, o ambiente sofre de falhas de descoberta ou as cargas de trabalho não têm Estados de extremidade de arquitetura claramente definidos. Todas essas suposições são comuns em planos de adoção de nuvem detalhados. Experimentação, pilotos e análise qualitativa são necessários para remover essas suposições.
- **Decisões técnicas atrasadas** pressupõem que, mais tarde, uma decisão técnica possa ser tomada, quanto mais precisa for a decisão. Os princípios a seguir do planejamento de produtos Agile ajudarão a atrasar decisões técnicas, permitindo que elas ocorram no momento certo com informações suficientes. No entanto, essa abordagem resulta em um grau muito maior de ambiguidade no plano inicial.

**Escopo mínimo:** Abordagens de desenvolvimento de produto Agile são sugeridas para orientar a ação de solicitação em planos gerenciáveis. A metodologia de plano recomenda as etapas a seguir para atingir esse equilíbrio. Inventariar todo o estado digital usando ferramentas de descoberta automatizada, mas usar a racionalização incremental para planejar até os próximos 1-3 meses de trabalho. Certifique-se de que o alinhamento adequado da organização seja movido rapidamente. Crie um plano de preparação de habilidades para a equipe atribuída. Aproveite o modelo de plano de adoção de nuvem para implantar rapidamente uma pendência inicial.

**Exemplo de escopo expandido:** Às vezes, a entrega de um plano de adoção de nuvem pode estar respondendo a um evento de negócios de alto impacto ou sensível ao tempo. Quando o sucesso exige a movimentação de um número elevado de ativos em um período fixo, as etapas acima geralmente são seguidas com um esforço de planejamento mais profundo. A chave para o sucesso nesses cenários é planejar o suficiente para entrar e planejar o envolvimento completo. Essa abordagem reduz a probabilidade de planejamento de resultados de negócios de bloqueio.

## <a name="balance-during-ready"></a>Saldo durante a preparação

Quando as equipes de adoção estão se preparando para suas primeiras etapas na nuvem, muitas vezes há prioridades concorrentes entre o tempo de adoção e as operações de longo prazo. A equipe pode se esforçar muito bem para oferecer a tarefa em vez de ser bem gerenciada. Esse esforço é necessário em ambientes de ti tradicionais, em que o ato de desenvolver uma plataforma requer ativos físicos e ciclos de aquisição. No entanto, quando toda a plataforma de ti é definida no código, as táticas de desenvolvimento tradicionais (como refatoração) reduzem a necessidade de serem bem gerenciadas desde o início.

**Prioridades concorrentes:**

- **Operações de longo prazo:** Os clientes geralmente são bloqueados pelo desejo de ter um ambiente de nuvem que atenda à paridade de recursos com sistemas de segurança, governança e gerenciamento de operações atuais. Em um estudo atual de clientes, mais de 90% dos clientes precisavam ter passado dessa mentalidade. Esse bloqueador injeta meses de atraso, diminuindo ou impedindo o impacto nos negócios.
- **Tempo para adoção:** Ferramentas baseadas em nuvem, como Azure Policy, plantas do Azure e grupos de gerenciamento, permitem facilitar a refatoração na plataforma de ti. Além disso, as zonas de aterrissagem predefinidas fornecem posições conceituada para acelerar a implantação em relação a um ambiente que já atenda a muitos dos requisitos de paridade de recursos. Juntos, há oportunidades de acelerar o tempo de colocação no mercado, com impacto mínimo sobre operações de longo prazo.

**Escopo mínimo:** A metodologia pronta descreve um caminho direto de adoção rápida para operações de longo prazo. Essa abordagem começa com uma introdução básica às ferramentas que habilitam a refatoração do ambiente. Com base nessas ferramentas e requisitos ambientais, os clientes são orientados a uma seleção de zonas de aterrissagem predefinidas (cada uma fornecida usando a infraestrutura como modelos de código). Esse código pode então ser refatorado durante a adoção da nuvem para melhorar as condições de operações, segurança e gerenciamento.

**Exemplo de escopo expandido:** Para equipes cujo plano de adoção chama um objetivo de médio prazo (dentro de 24 meses) para hospedar **mais de 1.000 ativos (aplicativos, infraestrutura ou ativos de dados) na nuvem**, uma exibição mais robusta das zonas de aterrissagem é sugerida. Nessas situações, administre e gerencie as metodologias que devem ser consideradas durante as conversas iniciais da zona de aterrissagem. No entanto, essa consideração mais profunda muitas vezes adiciona semanas ou meses a um plano de adoção de nuvem. Para minimizar o impacto nos resultados de negócios, a equipe de adoção deve fazer o piloto de cargas de trabalho reais na nuvem em paralelo à criação de uma zona de aterrissagem mais madura e uma solução de arquitetura central.

## <a name="balance-during-migrate"></a>Saldo durante a migração

Durante os esforços de migração, é comum que as equipes de adoção preparam que as cargas de trabalho serão rehospedadas na nuvem em sua configuração atual "no estado em que se encontra". Isso compete diretamente com uma exibição de aparência posterior para rearquitetar cada carga de trabalho para aproveitar melhor os recursos de nuvem. Infelizmente, os dois não são mutuamente exclusivos e podem ser gratuitos quando gerenciados por meio de um processo comum.

**Prioridades concorrentes:**

- **Hospedar novamente:** Os clientes geralmente correspondem à migração para um movimento de movimentação _e de deslocamento_ de replicação de todos os ativos para a nuvem em sua configuração de estado atual. Isso resulta em pouco descompasso no portfólio de ti. Essa abordagem também é a maneira mais rápida de desativar ativos em um data center existente.
- **Rearquitetar:** Modernizar a arquitetura de cada carga de trabalho maximiza o valor da nuvem em custo, desempenho e operações. No entanto, essa abordagem é muito mais lenta e geralmente requer acesso ao código-fonte de cada aplicativo.

**Escopo mínimo:** Durante o planejamento de estágio inicial, use a opção de novo host para planejamento, com uma clara compreensão de que essa opção é uma suposição de negócios inicial e não uma decisão técnica. Na metodologia de migração, a equipe de adoção desafiaria essa suposição para cada carga de trabalho migrada. Essa metodologia segue as etapas de avaliar, migrar, promover para cada carga de trabalho ou grupo ou cargas de trabalho criando uma fábrica de migração. Durante a fase de avaliação, a equipe de adoção avalia a adequação técnica e a arquitetura de cada carga de trabalho. Esse esforço de avaliação raramente resulta em uma abordagem pura de comparação e deslocamento, pois muitos dos componentes da arquitetura tendem a ser selecionados para refatoração e modernização.

**Exemplo de escopo expandido:** Para cargas de trabalho críticas ou de alta sensibilidade, como um aplicativo de microserviços de mainframe ou multicamadas, uma avaliação mais profunda da carga de trabalho pode ser necessária durante a fase de avaliação. Nessas situações de rearquitetura, sugerimos que os clientes aproveitem a análise de arquitetura do Azure e a estrutura de arquitetura do Azure para refinar os requisitos de carga de trabalho durante a avaliação.

## <a name="balance-during-innovate"></a>Saldo durante inovações

A verdadeira inovação voltada para o cliente cria prioridades comuns conflitantes entre a necessidade de fornecer um conjunto de recursos planejados e um processo de desenvolvimento de empatia de clientes.

**Prioridades concorrentes:**

- Foco de recurso: planos iniciais de inovação de desenvolvimento nos recursos de nuvem e espaço digital existentes para fornecer um conjunto de recursos que atendem a uma necessidade do cliente. É fácil permitir que o plano conduza a implementação técnica, levando a um esforço de desenvolvimento focado em recursos. Essa abordagem geralmente leva a uma satisfação de Stakeholder temporária, mas reduz a probabilidade de conduzir inovação que afete os comportamentos dos clientes.
- Empatia do cliente: os planos iniciais são uma parte importante do lado comercial do desenvolvimento e devem ser incluídos em relatórios regulares. No entanto, aprender, medir e criar com o empatia do cliente é uma medida mais precisa do sucesso em um esforço de inovação. O foco no cliente sobre os recursos tem mais probabilidade de resultar em uma satisfação do cliente de curto prazo e de longo prazo e no impacto nos negócios.

**Escopo mínimo:** A metodologia inovar ilustra como integrar estratégia e planos por meio de consenso de valor comercial. Em seguida, o guia apresenta ferramentas nativas de nuvem que podem acelerar cada disciplina de inovação, acompanhando as práticas recomendadas para a implementação. Por fim, a seção de aprimoramentos de processos demonstra abordagens para a criação de empatia de clientes ao respeitar planos e estratégias em toda a jornada de adoção da nuvem. Essa abordagem se concentra em fornecer inovação com o uso de uma pequena tecnologia como é possível.

**Exemplo de escopo expandido:** Às vezes, uma inovação pode ser dependente de uma missão crítica de cargas de trabalho de alta sensibilidade. Quando o "cliente" é um usuário interno, o esforço de desenvolvimento pode ser de missão crítica e de alta sensibilidade durante as iterações mais antigas. Para esses cenários, é recomendável que as equipes de adoção aproveitem a análise de arquitetura do Azure e a estrutura de arquitetura do Azure para avaliar o design de arquitetura avançada no início do processo.

## <a name="balance-during-govern"></a>Saldo durante o controle

A prática da governança de nuvem é um equilíbrio constante entre duas prioridades concorrentes: velocidade/agilidade e um ambiente bem controlado. A equipe de governança de nuvem se concentra na avaliação e na minimização de riscos para a empresa por meio de controles uniformes e a minimização de alterações. A equipe de adoção se concentra na condução de resultados de negócios, que exigem novos riscos e criam alterações inerentemente.

**Prioridades concorrentes:**

- Bem governada: todos os controles projetados para minimizar riscos bloqueiam alguns aspectos das opções de design de alteração ou limites. O controle é essencial para um ambiente bem controlado. No entanto, quando os controles são projetados e implantados isoladamente, eles podem ser tão prejudiciais quanto os riscos que se destinam a evitar.
- Velocidade/agilidade: a velocidade e a agilidade são requisitos fundamentais para os negócios na economia digital. Ambos exigem a capacidade de conduzir alterações com bloqueios mínimos para inovação ou adoção. Quando a alteração é controlada em isolamento de governança, ela gera novos riscos que podem prejudicar os negócios de maneiras involuntárias.

**Escopo mínimo:** A metodologia de controle sugere que nem a governança nem a adoção já devem acontecer isoladamente. Essa metodologia começa com uma compreensão das disciplinas de governança e uma conversa sobre o risco, a política e o processo dos negócios. Como um membro ativo em toda a jornada de adoção da nuvem, a equipe de governança pode implementar um conjunto mínimo de guardrails para abordar os riscos tangíveis no plano de adoção da nuvem. Ao longo do tempo, a equipe de governança pode refatorar e expandir essas guardrails para atender a novos riscos. Essa abordagem maximiza o aprendizado e a inovação, minimizando, ao mesmo tempo, o risco.

**Exemplo de escopo expandido:** Quando o risco de negócios é alto, especialmente na adoção, a equipe de governança de nuvem pode ser necessária para acelerar a expansão de implementações de governança. As mesmas diretrizes e exercícios podem ser usados para adicionar esse nível mais alto de governança, mas o tempo pode ter que ser acelerado. Em alguns cenários, um estado avançado de governança pode até ser necessário durante a implantação das primeiras zonas de aterrissagem.

## <a name="balance-during-manage"></a>Saldo durante o gerenciamento

O modelo comercial de ti sobre o gerenciamento de operações evoluiu continuamente na última década. À medida que a manutenção de hardware é movida além da principal proposta de valor, a exibição do Operations Management também foi deslocada. À medida que aumenta o foco no fornecimento de valor comercial, as equipes de gerenciamento de operações entram em conflito com o balanceamento de não operações/poucos Ops versus grandes investimentos.

**Prioridades concorrentes:**

- Grandes investimentos: investir igualmente em prevenção de interrupção, recuperação rápida e monitoramento em todo o ambiente é a visão tradicional do gerenciamento de operações. Essa abordagem pode ser dispendiosa e, às vezes, duplicação dos produtos de suporte disponibilizados pelo fornecedor de nuvem.
- Não há operações/operações baixas: Aproveite as ferramentas nativas de nuvem para minimizar tarefas repetitivas e recorrentes fornecidas anteriormente por funcionários em tempo integral. Reduzir essas dependências operacionais no modelo de gerenciamento de operações libera esses funcionários para impulsionar mais valor. Sozinho, essa abordagem pode levar a suporte a operações média.

**Escopo mínimo:** A metodologia de gerenciamento sugere estabelecer uma linha de base de gerenciamento de não Ops de nuvem nativa. A confirmação de que nenhuma linha de base de operações não atenderá a todas as necessidades de negócios, trabalhará com a empresa para definir compromissos e alinhar investimentos melhor. Expanda a linha de base para atender às necessidades comuns de todas as cargas de trabalho. Em seguida, habilite as equipes de plataforma ou as equipes de carga de trabalho específicas para manter soluções bem gerenciadas em um ambiente bem gerenciado.

**Exemplo de escopo expandido:** Na maioria dos ambientes, uma pequena porcentagem de cargas de trabalho cujo valor comercial justifica investimentos profundos nas operações. Nesses cenários, a equipe de ti pode querer aproveitar a revisão de arquitetura do Azure e a estrutura de arquitetura do Azure para orientar as operações mais profundas.

## <a name="balance-during-organize"></a>Saldo durante a organização

As prioridades concorrentes ao longo deste artigo são refletidas na unidade de ti para atender às demandas comerciais por velocidade e agilidade. Esse mesmo turno está aparecendo em alterações em organogramas (ou estruturas de equipe do V) para capacitar o maior suporte aos resultados de negócios. À medida que os líderes de ti refletem nas estruturas de equipe, duas prioridades concorrentes são normalmente tratadas: controle centralizado vs de controle delegado

**Prioridades concorrentes:**

- Controle centralizado: os modelos de operação de controle centralizado se concentram na centralização de todos os controles necessários para impor políticas rígidas. Nesse modelo, ele serve como um bloqueador para inovação, velocidade e agilidade. No entanto, ele é capaz de garantir um grau mais alto de estabilidade, conformidade e segurança.
- Controle delegado: nesse modelo operacional distribuído, supõe-se que cada equipe de DevOps ou equipe de aplicativos de negócios fornecerá seu próprio conjunto de controles, com base nas soluções necessárias para atender aos objetivos de negócios. Nesse modelo, ele fornece guardrails para ajudar a manter as equipes viajando, mas minimiza o número de restrições técnicas forçadas sempre que possível.

**Escopo mínimo:** A maioria das organizações passará por um conjunto natural de evoluções ao longo do tempo. A metodologia organizar descreve a série mais comum de evoluções. A orientação sugerida é que as equipes se esforçam para migrar para uma estrutura de excelência na nuvem para fornecer abordagens de controle delegadas.

**Exemplo de escopo expandido:** Há muitas situações que disparam uma necessidade de controle centralizado. Os requisitos de conformidade de terceiros e a exposição de segurança temporária são dois exemplos de gatilhos para controle centralizado. Nessas situações, normalmente é necessário estabelecer políticas de limitação e controles fixos rígidos. No entanto, para permitir que a inovação e a adoção continuem, recomendamos que as equipes de ti centrais forneçam esses controles com base na criticalidade e na sensibilidade de cada carga de trabalho. Fornecer ambientes com menos controle, mas um escopo reduzido ou um perfil de risco, permite flexibilidade mesmo quando o controle é necessário.
