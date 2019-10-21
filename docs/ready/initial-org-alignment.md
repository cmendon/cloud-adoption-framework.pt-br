---
title: Alinhamento inicial da organização
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fornece uma visão geral do alinhamento inicial da organização.
author: alexbuckgit
ms.author: abuck
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: governance
ms.openlocfilehash: b15cee23f81027e3b5597079e61fcc7ac0e534e2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548733"
---
# <a name="initial-organization-alignment"></a>Alinhamento inicial da organização

A **transformação digital** para computação em nuvem representa uma mudança do funcionamento local para operar na nuvem. Essa mudança inclui novas maneiras de fazer negócios – por exemplo, a transformação Digital muda de despesas de capital para hardware de software e datacenter para despesas operacionais para o uso de recursos de nuvem. Vejamos como começar a usar a estrutura de [adoção do Microsoft Cloud para o Azure](../index.md).

## <a name="the-digital-transformation-process"></a>O processo de transformação digital

Para ter êxito ao adotar a nuvem, uma empresa deve preparar sua organização, as pessoas e os processos para que estejam prontos para essa transformação digital. A estrutura organizacional de cada empresa é diferente, portanto, não há nenhuma abordagem de tamanho único para a preparação organizacional. Este documento descreve as etapas de alto nível que sua empresa pode tomar para se preparar. Sua organização terá que gastar tempo desenvolvendo um plano detalhado para realizar cada uma das etapas listadas.

O processo de alto nível para a transformação digital é:

1. Crie uma equipe de estratégia de nuvem. Essa equipe é responsável por liderar a transformação digital. Também é importante neste estágio formar uma equipe de governança e uma equipe de segurança para a transformação digital.
2. Os membros da equipe de estratégia de nuvem aprendem as novidades e as diferentes sobre as tecnologias de nuvem.
3. A equipe de estratégia de nuvem prepara a empresa criando o caso comercial para transformação digital – enumera todas as lacunas atuais na estratégia de negócios e determina as soluções de alto nível para eliminá-las.
4. Alinhar soluções de alto nível com grupos de negócios. Identifique os participantes de cada grupo de negócios para ter o design e a implementação para cada solução.
5. Adapte as funções, habilidades e processos existentes para incluir funções, habilidades e processos de nuvem.

<!--6. Develop processes for operating in the cloud to make solutions more robust in terms of availability, resiliency, and security.
1. Optimize solutions for performance, scalability, and cost efficiency.-->

## <a name="step-1-create-a-cloud-strategy-team"></a>Etapa 1: criar uma equipe de estratégia de nuvem

A primeira etapa da transformação digital da sua empresa é envolver líderes de negócios de toda a organização para criar uma equipe de estratégia de nuvem (CST). Essa equipe consiste em líderes de negócios de finanças, infraestrutura de ti e grupos de aplicativos. Essas equipes podem ajudar na fase de análise e experimentação da nuvem.

Por exemplo, uma equipe de estratégia de nuvem poderia ser orientada pelo CTO e consistir em membros da equipe de arquitetura empresarial, finanças de ti, tecnólogos sêniores de vários grupos de aplicativos de ti (RH, finanças etc.) e líderes da infraestrutura, segurança, e equipes de rede.

Também é importante formar duas outras equipes de alto nível: uma equipe de governança e uma equipe de segurança. Essas equipes são responsáveis por projetar, implementar e fazer a auditoria contínua das políticas de governança e segurança da empresa. A equipe de governança requer membros que trabalharam com proteção de ativos, gerenciamento de custos, política de grupo e tópicos relacionados. A equipe de segurança requer membros que são bem informados em padrões de segurança atuais do setor, bem como os requisitos de segurança da empresa.

![Equipe de estratégia de nuvem, com equipes de governança e segurança](../_images/ready/getting-started-overview-1.png)

A equipe de governança é responsável por projetar e implementar o modelo de governança da empresa na nuvem, bem como implantar e manter os ativos de infraestrutura compartilhada que fazem parte da transformação digital. Esses ativos incluem hardware, software e recursos de nuvem necessários para conectar a rede local à rede virtual na nuvem.

A equipe de segurança é responsável por projetar e implementar a política de segurança da empresa na nuvem, trabalhando junto com a equipe de governança. A equipe de segurança possui a extensão do limite de segurança da rede local para incluir a rede virtual na nuvem. Isso pode assumir a forma de propriedade e manutenção dos firewalls de entrada e saída na rede virtual na nuvem, bem como garantir que as ferramentas e a política impeçam a implantação de recursos não autorizados.

## <a name="step-2-learn-whats-new-in-the-cloud"></a>Etapa 2: saiba o que há de novo na nuvem

A próxima etapa da transformação digital da sua empresa é para os membros da equipe de estratégia de nuvem aprenderem como a tecnologia de nuvem mudará a maneira como a empresa faz negócios. Essa é a preparação e o planejamento das alterações em seus negócios, pessoas e tecnologia. É importante que os membros da equipe de estratégia de nuvem compreendam as novidades e as diferentes na nuvem em comparação com o local.

![As equipes de segurança, governança e estratégia de nuvem aprendem as práticas recomendadas para operar na nuvem.](../_images/ready/getting-started-overview-2.png)

O ponto de partida para entender a nuvem é aprender [como o Azure funciona](../getting-started/what-is-azure.md) em um alto nível. Em seguida, saiba mais sobre as noções básicas de [governança no Azure](../govern/resource-consistency/what-is-governance.md) em preparação para [entender o gerenciamento de acesso aos recursos](../govern/resource-consistency/resource-access-management.md).

Para aprendizado avançado, a equipe de governança deve examinar os conceitos e guias de design na seção governança do Sumário. As seções infraestrutura e cargas de trabalho são úteis para aprender sobre as arquiteturas e cargas de trabalho típicas na nuvem.

## <a name="step-3-identify-gaps-in-business-strategy"></a>Etapa 3: identificar lacunas na estratégia de negócios

A próxima etapa é que a equipe de estratégia de nuvem enumere os problemas de negócios que exigem uma solução de transformação digital. Por exemplo, uma empresa pode ter um datacenter local existente com hardware de fim de vida que exige substituição. Em outro exemplo, uma empresa pode estar enfrentando dificuldades com o tempo de colocação no mercado para novos recursos e serviços e pode estar atrás da competição. Essas lacunas representam as _metas_ da transformação digital da sua empresa.

As lacunas na estratégia de negócios podem ser classificadas nas seguintes categorias:

| Categoria | Descrição |
| --- | --- |
| Gerenciamento de custos | Representa uma lacuna em como a empresa paga pela tecnologia. |
| Governança | Representa uma lacuna nos processos usados pela empresa para proteger seus ativos contra uso impróprio que pode resultar em estouros de custos, problemas de segurança ou problemas de conformidade. |
| Conformidade | Representa uma lacuna em como a empresa segue seus próprios processos e políticas internos, bem como leis, regulamentos e padrões externos. |
| Segurança | Representa uma lacuna na maneira como a empresa protege seus ativos de tecnologia e de dados de ameaças externas. |
| Governança de dados | Representa uma lacuna em como uma empresa gerencia seus dados, especialmente dados do cliente. Por exemplo, o Regulamento Geral sobre a Proteção de Dados (GDPR) na União Europeia tem requisitos estritos para a proteção dos dados do cliente que podem exigir novo hardware e software. |

Depois que sua empresa tiver classificado todas as lacunas da estratégia de negócios nessas categorias, a próxima etapa será determinar uma solução de alto nível para cada problema.

A tabela a seguir ilustra vários exemplos:

|Lacuna da estratégia de negócios|Categoria &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;|Solução &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0 1 2 3|
|-----|-----|-----|
| Os serviços atualmente hospedados no local apresentam problemas de disponibilidade, resiliência e escalabilidade durante o tempo de pico de demanda, que é aproximadamente 10% do uso. Os servidores no datacenter local são o fim da vida útil. A ti empresarial recomenda a compra de novo hardware local para datacenter com especificações para lidar com a demanda de pico.| Gerenciamento de custos | Migre cargas de trabalho locais existentes afetadas para recursos escalonáveis na nuvem, pagando pelo uso apenas. |
| As leis e regulamentos de gerenciamento de dados externos exigem que a empresa cumpra o conjunto de controles padrão que exigem Criptografia de dados em repouso, exigindo novo hardware e software. | Governança de dados | Mover dados para a criptografia do serviço de armazenamento do Azure para dados em repouso. |
| Os serviços hospedados no datacenter local estão enfrentando ataques de DDoS (negação de serviço distribuído) em serviços voltados para o público. Os ataques são difíceis de reduzir e exigir que novos hardware, software e pessoal de segurança lidem com eficiência. | Segurança | Migre serviços para o Azure e aproveite a proteção contra DDoS do Azure.|

Quando todas as lacunas na estratégia de negócios tiverem sido enumeradas e soluções de alto nível forem determinadas, priorize a lista. A lista pode ser priorizada alinhando as lacunas da estratégia de negócios com os objetivos de curto e longo prazo da empresa em cada categoria. Por exemplo, se a empresa tiver uma meta de curto prazo para reduzir os gastos de ti nos próximos dois trimestres fiscais, as lacunas de negócios na categoria de *Gerenciamento de custos* poderão ser priorizadas pelo economia de custo projetado associado a cada um.

A saída desse processo é uma lista classificada por pilha de soluções de alto nível alinhadas com categorias de negócios.

## <a name="step-4-align-high-level-solutions-with-business-groups-to-design-solutions"></a>Etapa 4: alinhar soluções de alto nível com grupos de negócios para criar soluções

Agora que as metas da transformação digital foram enumeradas, priorizadas e soluções de alto nível propostas, a próxima etapa é que a equipe de estratégia de nuvem alinhe cada uma das soluções de alto nível com as equipes de design e implementação em cada uma das empresas agrupa.

As equipes tomam as listas priorizadas e trabalham em cada solução de alto nível para criar cada solução. O processo de design envolverá a especificação da nova infraestrutura e novas cargas de trabalho. Também pode haver alterações nas funções das pessoas e dos processos que eles seguem. Também é importante nesse estágio para que cada uma das equipes de design inclua as equipes de governança e segurança para a análise de cada design. Cada design deve estar dentro das políticas e dos procedimentos definidos pelas equipes de governança e segurança, e essas equipes devem ser incluídas na aprovação final de cada design.

![a equipe de estratégia de nuvem fornece soluções de alto nível para equipes de design e implementação.](../_images/ready/getting-started-overview-3.png)

O design de cada solução é uma tarefa não trivial. Conforme os designs são criados, eles devem ser considerados no contexto de outros designs de solução de outras equipes. Por exemplo, se vários dos designs resultam em uma migração de aplicativos e serviços locais existentes para a nuvem, pode ser mais eficiente agrupá-los e criar uma estratégia geral de migração. Em outro exemplo, talvez não seja possível migrar alguns aplicativos e serviços locais existentes, e a solução pode ser substituí-los por novos serviços de desenvolvimento ou de terceiros. Nesse caso, pode ser mais eficiente agrupá-los e determinar a sobreposição entre eles para determinar se um serviço de terceiros pode ser usado para mais de uma solução.

Depois que o design da solução for concluído, a equipe passará para a fase de implementação para cada design. A fase de implementação para cada design de solução pode ser executada usando processos de gerenciamento de projeto padrão.

## <a name="step-5-adapt-existing-roles-skills-and-process-for-the-cloud"></a>Etapa 5: adaptar as funções, habilidades e processos existentes para a nuvem

Em cada fase do histórico do setor de ti, as alterações mais importantes do setor geralmente são marcadas por alterações nas funções da equipe. Durante a transição de mainframes para o modelo de cliente/servidor, a função do operador de computador basicamente desapareceu, substituída pelo administrador do sistema. Quando chegou a idade da virtualização, o requisito para pessoas que trabalham com servidores físicos diminuiu, substituiu a necessidade de especialistas em virtualização. Da mesma forma, à medida que as instituições mudam para a computação em nuvem, as funções provavelmente serão alteradas novamente. Por exemplo, os especialistas do datacenter podem ser substituídos por analistas financeiros na nuvem. Mesmo nos casos em que os títulos de trabalho de ti não foram alterados, as funções de trabalho diárias foram alteradas significativamente.

Os membros da equipe de ti podem sentir ansioso sobre suas funções e cargos, pois eles percebem que um conjunto diferente de habilidades é necessário para o suporte a soluções de nuvem. Mas os funcionários ágeis que exploram e aprendem novas tecnologias de nuvem não precisam ter esse medo. Eles podem conduzir a adoção de serviços de nuvem e ajudar a organização a entender e adotar as alterações associadas.

### <a name="capturing-concerns"></a>Capturando preocupações

Durante a transformação digital, cada equipe deve capturar qualquer preocupação da equipe à medida que elas surgirem. Ao capturar preocupações, identifique o seguinte:

- **O tipo de preocupação.** Por exemplo, os trabalhadores podem ser resistentes às alterações nas tarefas de trabalho que acompanham a transformação digital.
- **O impacto da preocupação se não for resolvido.** Por exemplo, a resistência à transformação digital pode fazer com que os trabalhadores sejam lentos para executar as alterações necessárias.
- **A área equipada para abordar a preocupação.** Por exemplo, se os trabalhadores do departamento de ti forem relutantes para adquirir novas habilidades, a área do stakeholder de ti será mais bem equipada para resolver essa preocupação. Identificar a área pode estar claro para algumas preocupações e, nesses casos, talvez seja necessário escalonar para a liderança executiva.

### <a name="identify-gaps"></a>Identificar lacunas

Outro aspecto de trabalhar com os problemas com a transformação digital da sua empresa é identificar as **lacunas**. Um intervalo é uma função, uma habilidade ou um processo necessário para sua transformação digital que não existe atualmente em sua empresa.

Comece enumerando as novas responsabilidades que acompanham a transformação digital, com ênfase em novas responsabilidades e responsabilidades atuais a serem desativadas. Identifique a área alinhada a cada responsabilidade. Para novas responsabilidades, determine o quão alinhado com a área. Algumas responsabilidades podem abranger várias áreas, e isso representa uma oportunidade para um melhor alinhamento que deve ser capturado como uma preocupação. No caso em que nenhuma área é identificada como responsável, Capture-a como uma lacuna.

Em seguida, identifique as habilidades necessárias para dar suporte à responsabilidade. Determine se sua empresa tem recursos existentes com essas habilidades. Se nenhum recurso existente estiver disponível, determine quais programas de treinamento ou aquisição de talento é necessária. Determine o período de tempo pelo qual a responsabilidade deve ter suporte para manter sua transformação digital sob controle.

Por fim, identifique as funções que irão executar essas habilidades. Algumas de suas forças de força existentes assumirão partes da função e, em outros casos, uma função totalmente nova pode ser necessária.

### <a name="partner-across-teams"></a>Parceiro entre equipes

As habilidades necessárias para preencher as lacunas na transformação digital de sua organização normalmente não serão confinadas em uma única função ou até mesmo em um único departamento. As habilidades terão relações e dependências que podem abranger uma única função ou várias funções, e essas funções podem existir em vários departamentos. Por exemplo, um proprietário de carga de trabalho pode exigir que alguém em uma função de ti provisione recursos principais, como assinaturas e grupos de recursos.

Essas dependências representam novos processos que sua organização implementa para gerenciar o fluxo de trabalho entre as funções. No exemplo acima, vários tipos diferentes de processo podem dar suporte à relação entre o proprietário da carga de trabalho e a função de ti. Por exemplo, uma ferramenta de fluxo de trabalho pode ser criada para gerenciar o processo ou um modelo de email simples pode ser usado.

Acompanhe essas dependências e anote os processos que oferecerão suporte a eles e se o processo existe ou não no momento. Para processos que exigem ferramentas, verifique se a linha do tempo para implantar qualquer ferramenta está alinhada com a agenda geral de transformação digital.

## <a name="next-steps"></a>Próximos passos

A transformação digital é um processo iterativo e, com cada iteração, as equipes envolvidas se tornam mais eficientes.

> [!div class="nextstepaction"]
> [Entenda como o Azure funciona](../getting-started/what-is-azure.md)
