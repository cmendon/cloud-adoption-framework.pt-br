---
title: Recursos de governança de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve a formação de recursos de governança de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: bf68bc17d5e94ae4c35e0a88d3ca73bd42935a5b
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566800"
---
# <a name="cloud-governance-capabilities"></a>Recursos de governança de nuvem

Qualquer tipo de alteração gera novos riscos. Os recursos de governança de nuvem garantem que os riscos e a tolerância a riscos sejam avaliados e gerenciados corretamente. Esse recurso garante a identificação adequada dos riscos que não podem ser tolerados pela empresa. As pessoas que fornecem esse recurso podem então converter riscos no controle de políticas corporativas. As políticas de controle são então executadas por meio de disciplinas definidas executadas pelos membros da equipe que fornecem recursos de governança de nuvem.

## <a name="possible-sources-for-this-capability"></a>Fontes possíveis para esse recurso

Dependendo dos resultados de negócios desejados, as habilidades necessárias para fornecer recursos completos de governança de nuvem podem ser fornecidas por:

- Governança de ti
- Arquitetura empresarial
- Operações de ti
- Infraestrutura de ti
- Rede
- Identidade
- Virtualização
- Continuidade dos negócios e recuperação de desastres
- Proprietários do aplicativo dentro dele

O recurso de governança de nuvem identifica os riscos relacionados às versões atuais e futuras. Esse recurso é visto nos esforços para avaliar o risco, entender os possíveis impactos e tomar decisões relacionadas à tolerância a riscos. Ao fazer isso, os planos podem ser atualizados rapidamente para refletir as necessidades dinâmicas da [capacidade de adoção da nuvem](./cloud-adoption.md).

## <a name="key-responsibilities"></a>Principais responsabilidades

O principal imposto de qualquer recurso de governança de nuvem é equilibrar as forças concorrentes da transformação e da mitigação de riscos. Além disso, a governança de nuvem garante que a [adoção de nuvem](./cloud-adoption.md) esteja ciente da classificação de ativos e de dados e das diretrizes de arquitetura que regem todas as abordagens de adoção. A equipe também trabalhará com o [Cloud Center de excelência](./cloud-center-of-excellence.md) para aplicar abordagens automatizadas para o controle de ambientes de nuvem.

Essas tarefas geralmente são executadas pelo recurso de governança de nuvem mensalmente.

**Tarefas de planejamento antecipadas:**

- Entenda os [riscos de negócios](../govern/policy-compliance/risk-tolerance.md) introduzidos pelo plano
- Representar a [tolerância de risco dos negócios](../govern/policy-compliance/risk-tolerance.md)
- Auxiliar na criação de um [MVP de governança](../govern/guides/index.md)

**Tarefas mensais em andamento:**

- Entenda [os riscos de negócios](../govern/policy-compliance/risk-tolerance.md) introduzidos durante cada versão
- Representar a [tolerância de risco dos negócios](../govern/policy-compliance/risk-tolerance.md)
- Auxiliar na melhoria incremental dos [requisitos de política e conformidade](../govern/policy-compliance/index.md)

## <a name="meeting-cadence"></a>Cadência da reunião

A funcionalidade de governança de nuvem geralmente é fornecida por uma equipe de trabalho. O tempo de comprometimento de cada membro da equipe representará um grande percentual de suas agendas diárias. As contribuições não serão limitadas a ciclos de reuniões e comentários.

## <a name="additional-participants"></a>Participantes adicionais

Veja a seguir os participantes que irão participar frequentemente das atividades de governança de nuvem:

- Os líderes do gerenciamento central e dos colaboradores diretos nas principais funções que foram apontados para representar os negócios ajudarão a avaliar as tolerâncias de risco.
- Os recursos de governança de nuvem são fornecidos por uma extensão do [recurso de estratégia de nuvem](./cloud-strategy.md). Assim como se espera que o CIO e os líderes de negócios participem dos recursos de estratégia de nuvem, seus subordinados diretos devem participar das atividades de governança de nuvem.
- Os funcionários de negócios que são membros da unidade de negócios que trabalham junto com a liderança da linha de negócios devem ser capacitados a tomar decisões relacionadas a riscos corporativos e técnicos.
- Os funcionários de ti (tecnologia da informação) e de segurança da informação (IS) que entendem os aspectos técnicos da transformação na nuvem podem servir em uma capacidade rotativa em vez de serem um provedor consistente de recursos de governança de nuvem.

## <a name="maturation-of-cloud-governance-capability"></a>Desenvolvimento do recurso de governança de nuvem

Algumas organizações de grande porte têm equipes dedicadas existentes que se concentram na governança de ti. Essas equipes são especializadas em gerenciamento de riscos em todo o portfólio de ti por meio de metodologias como ITIL ou ITSM. Quando essas equipes existem, os modelos de maturidade a seguir podem ser acelerados rapidamente. No entanto, a equipe de governança de ti é incentivada a examinar o modelo de governança de nuvem para entender como a governança muda ligeiramente na nuvem. Os principais artigos incluem a [extensão de políticas corporativas para a nuvem](../govern/corporate-policy.md) e as [cinco disciplinas de governança de nuvem](../govern/governance-disciplines.md).

**Sem governança:** É comum que as organizações se movam para a nuvem sem planos claros para governança. Antes de longo, as preocupações com relação à segurança, ao custo, à escala e às operações começam a disparar conversas sobre a necessidade de um modelo de governança e de pessoas para a equipe dos processos associados a esse modelo. Iniciar essas conversas antes que elas se tornem preocupações é sempre uma boa primeira etapa para superar o antipadrão de "sem governança". A seção sobre como [definir políticas corporativas](../govern/corporate-policy.md) pode ajudar a facilitar essas conversas.

**Governança bloqueada:** Quando as preocupações com segurança, custo, escala e operações não são respondidas, os projetos e as metas de negócios tendem a ser bloqueados. A falta de governança adequada gera medo, incerteza e dúvida entre os participantes e os engenheiros. Pare isso em suas trilhas executando a ação antecipadamente. Os dois guias de governança definidos na estrutura de adoção de nuvem podem ajudá-lo a começar pequeno, definir inicialmente as políticas de limitação para minimizar a incerteza e a governança amadurece ao longo do tempo. Escolha entre o guia [corporativo complexo](../govern/guides/complex/index.md) ou o [guia Standard Enterprise](../govern/guides/standard/index.md).

**Governança voluntária:** Há a tendência de ser corajoso coitados em todas as empresas. Esses Gallants que estão dispostos a saltar e ajudar a equipe a aprender com seus erros. Geralmente, é assim que a governança é iniciada, especialmente em empresas menores. Essas corajoso coitadosm o tempo de voluntários para corrigir alguns problemas e enviar por push equipes de adoção de nuvem para um conjunto consistente e bem gerenciado de práticas recomendadas.

Os esforços desses indivíduos são muito melhores do que os cenários "sem governança" ou "governança bloqueada". Embora seus esforços devam ser recomendado, essa abordagem não deve ser confundida com governança. A governança adequada requer mais do que o suporte esporádico para impulsionar a consistência, que é o objetivo de qualquer boa abordagem de governança. As diretrizes nas [cinco disciplinas de governança de nuvem](../govern/governance-disciplines.md) podem ajudar a desenvolver essa disciplina.

**Responsáveis pela nuvem:** Esse moniker se tornou um crachá de honrar muitos arquitetos de nuvem especializados na governança de estágio inicial. Quando as práticas de governança começam a ser iniciadas pela primeira vez, os resultados são semelhantes aos voluntários de governança. No entanto, há uma diferença fundamental. Um dos responsáveis pela nuvem tem um plano em mente. Nesse estágio da maturidade, a equipe está gastando tempo limpando as bagunças feitas pelos arquitetos de nuvem que vieram antes delas. No entanto, os responsáveis pela nuvem alinham esse esforço à [política corporativa](../govern/corporate-policy.md)bem estruturada. Eles também usam ferramentas de automação de governança, como as descritas no [MVP de governança](../govern/guides/complex/index.md).

Outra diferença fundamental entre um responsável pela nuvem e uma governança voluntária é o suporte à liderança. Os voluntários colocam horas extras acima das expectativas regulares devido à sua busca de aprender e fazer. Os responsáveis pela nuvem recebem suporte da liderança para reduzir suas obrigações diárias para garantir que as alocações regulares de tempo possam ser investidos no aprimoramento da governança de nuvem.

**Guardião de nuvem:** À medida que as práticas de governança solidificam e se tornam aceitas pelas equipes de adoção de nuvem, a função dos arquitetos de nuvem que se especializa em governança muda um pouco, assim como a função da equipe de governança de nuvem. Em geral, as práticas mais maduras têm a atenção de outros especialistas no assunto que podem ajudar a fortalecer as proteções fornecidas pelas implementações de governança.

Embora seja sutil, a diferença entre essas duas classificações deve ser considerada durante o estabelecimento de uma cultura de TI focada em governança. O trabalho de um guardião da nuvem é "arrumar a bagunça" feita pelos arquitetos de nuvem inovadores, além do atrito natural existente entre essas duas funções que, na prática, têm objetivos opostos. Por outro lado, um guardião ajuda a proteger a nuvem para que outros arquitetos possam trabalhar com mais rapidez e menos complicações.

Os guardiões de nuvem começam a usar abordagens de governança mais avançadas para acelerar a implantação da plataforma e ajudar as equipes a fazer o autoatendimento de suas necessidades ambientais, para que elas possam se mover mais rapidamente. Exemplos dessas funções mais avançadas são vistos nos aprimoramentos incrementais para o MVP de governança, como [a melhoria da linha de base de segurança](../govern/guides/complex/security-baseline-improvement.md).

**Aceleradores de nuvem:** Os Guardiões e os responsáveis na nuvem de nuvem naturalmente coletam scripts e automaçãos que aceleram a implantação de ambientes, plataformas ou até mesmo componentes de vários aplicativos. A organização e o compartilhamento desses scripts, além das responsabilidades de governança centralizadas, desenvolve um alto grau de respeito para esses arquitetos em todo ele.

Esses profissionais de governança que compartilham seus scripts estruturados ajudam a fornecer projetos de tecnologia com mais rapidez e incorporar governança à arquitetura das cargas de trabalho. Essa influência de carga de trabalho e o suporte a bons padrões de design eleva os aceleradores de nuvem a uma classificação mais alta do especialista em governança.

**Governança global:** Quando as organizações dependem de necessidades de ti distribuídas globalmente, pode haver desvios significativos em operações e governança em várias regiões geográficas. Demandas de unidades de negócios e até mesmo requisitos de soberania de dados locais podem fazer com que as práticas recomendadas de governança interfiram nas operações necessárias Nesses cenários, um modelo de governança em camadas permite consistência minimamente viável e governança localizada. O artigo em [várias camadas de governança](../govern/guides/complex/multiple-layers-of-governance.md) fornece mais informações sobre como atingir esse nível de maturidade.

Todas as empresas são exclusivas e, portanto, suas necessidades de governança. Escolha o nível de maturidade que se adapta à sua organização e use a estrutura de adoção de nuvem para orientar as práticas, os processos e as ferramentas para ajudá-lo a chegar lá.

## <a name="next-steps"></a>Próximas etapas

À medida que a governança de nuvem amadurece, as equipes serão capacitadas a adotar a nuvem em ritmos mais rápidos. Os esforços contínuos de adoção na nuvem tendem a disparar a maturidade nas operações de ti. Esse amadurecimento também pode exigir o desenvolvimento de [recursos de operações de nuvem](./cloud-operations.md).

> [!div class="nextstepaction"]
> [Desenvolver recursos de operações de nuvem](./cloud-operations.md)
