---
title: Processos de conformidade de política de aceleração de implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processos de conformidade de política de aceleração de implantação
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: de64b03c6c6113261426beed5de729eb6927a440
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566392"
---
# <a name="deployment-acceleration-policy-compliance-processes"></a>Processos de conformidade de política de aceleração de implantação

Este artigo descreve uma abordagem para processos de adesão a políticas que regem a [Aceleração de implantação](./index.md). O controle efetivo da configuração de nuvem começa com processos manuais recorrentes projetados para detectar problemas e impor políticas para corrigir esses riscos. No entanto, você pode automatizar esses processos e complementar com ferramentas para reduzir a sobrecarga de governança e permitir respostas mais rápidas para desvio.

## <a name="planning-review-and-reporting-processes"></a>Planejar, revisar e relatar processos

As melhores ferramentas de Aceleração de implantação na nuvem somente são tão boas quanto os processos e políticas que dão suporte a elas. Veja a seguir um conjunto de processos de exemplo normalmente usados como parte de uma disciplina de aceleração de implantação. Use estes exemplos como ponto de partida ao planejar os processos que permitirão que você continue a atualizar a implantação e a política de configuração com base nas alterações de negócios e nos comentários das equipes de desenvolvimento e ti responsáveis por transformar as diretrizes de governança Action.

**Avaliação e planejamento inicial de riscos:** Como parte da adoção inicial da disciplina de aceleração da implantação, identifique seus principais riscos e tolerâncias de negócios relacionados à implantação de seus aplicativos de negócios. Use essas informações para discutir riscos técnicos específicos com membros da equipe de operações de ti e desenvolver um conjunto de linhas de base de implantação e políticas de configuração para corrigir esses riscos para estabelecer sua estratégia inicial de governança.

**Planejamento da implantação:** Antes de implantar qualquer ativo, execute uma revisão de segurança e de operações para identificar novos riscos e garantir que todos os requisitos de política relacionados à implantação sejam atendidos.

**Teste de implantação:** Como parte do processo de implantação de qualquer ativo, a equipe de governança de nuvem, em cooperação com suas equipes de operações de ti, é responsável por revisar a conformidade da política de implantação.

**Planejamento anual:** Realize uma revisão anual de alto nível da estratégia de aceleração de implantação. Explore as prioridades corporativas futuras e estratégias de adoção de nuvem atualizadas para identificar o aumento de risco potencial e outras necessidades de configuração emergentes e oportunidades. Além disso, use esse tempo para examinar as práticas recomendadas mais recentes do DevOps e integrá-las em suas políticas e examinar processos.

**Análise e planejamento trimestral:** Realize uma revisão trimestral dos dados de auditoria operacionais e dos relatórios de incidentes para identificar as alterações necessárias na política de aceleração de implantação. Como parte desse processo, examine as práticas recomendadas atuais de DevOps e DevTechOps e atualize a política conforme apropriado. Depois que a análise for concluída, alinhe as diretrizes de design e aplicativo à política atualizada.

Esse processo de planejamento também é um bom momento para avaliar a associação atual de sua equipe de governança de nuvem para as lacunas de conhecimento relacionadas à política nova ou alteração e aos riscos relacionados à aceleração de DevOps e implantação. Convide a equipe de TI relevante a participar das análises e planejamentos como consultores temporários ou membros permanentes da sua equipe.

**Educação e treinamento:** Em uma base Bimonthly, ofereça sessões de treinamento para garantir que a equipe de ti e os desenvolvedores estejam atualizados sobre os requisitos e a estratégia de aceleração de implantação mais recentes. Como parte desse processo, revise e atualize todas as documentações, diretrizes ou outros recursos de treinamento para garantir que estejam em sincronia com as últimas declarações da política corporativa.

**Revisões mensais de auditoria e relatórios:** Execute uma auditoria mensal em todas as implantações de nuvem para garantir seu alinhamento contínuo com a política de configuração. Examine as atividades relacionadas à implantação com a equipe de ti e identifique quaisquer problemas de conformidade ainda não tratados como parte do processo de monitoramento e imposição contínuo. O resultado dessa revisão é um relatório para a equipe de estratégia de nuvem e para cada equipe de adoção da nuvem comunicar a conformidade geral com a política. O relatório também é armazenado para fins de auditoria e legais.

## <a name="ongoing-monitoring-processes"></a>Processos de monitoramento contínuo

Determinar se a estratégia de governança de Aceleração de implantação é bem-sucedida depende da visibilidade no estado atual e futuro da sua infraestrutura de nuvem. Sem a capacidade de analisar as métricas e os dados relevantes da atividade e da integridade operacional dos recursos de nuvem, você não pode identificar as alterações em seus riscos ou detectar violações de suas tolerâncias de risco. Os processo de administração contínua discutido acima exigem dados de qualidade para garantir que a política possa ser modificada para proteger a sua infraestrutura contra ameaças e riscos de recursos configurados incorretamente.

Verifique se suas equipes de operações de ti implementaram sistemas de monitoramento automatizados para sua infraestrutura de nuvem que capturam os dados de logs relevantes de que você precisa para avaliar o risco. Seja proativo no monitoramento desses sistemas para garantir a detecção e mitigação imediatas de possíveis violações da política e garanta que a sua estratégia de monitoramento esteja em linha com as necessidades de implantação e configuração.

## <a name="violation-triggers-and-enforcement-actions"></a>Gatilhos de violação e ações de imposição

Como a não conformidade com as políticas de configuração pode levar a riscos críticos de interrupção do serviço, a equipe de governança de nuvem deve ter visibilidade das sérias violações de política. Verifique se a equipe de ti tem caminhos de escalonamento claros para relatar problemas de conformidade de configuração aos membros da equipe de governança mais adequados para identificar e verificar se os problemas de política foram mitigados quando detectados.

Quando violações forem detectadas, será necessário realizar ações para realinhar a política o mais rápido possível. A equipe de TI pode automatizar a maioria dos gatilhos de violação usando as ferramentas descritas na [cadeia de ferramentas de Aceleração de implantação](./toolchain.md).

Os gatilhos e ações de imposição a seguir fornecem exemplos que você pode consultar ao discutir como usar os dados de monitoramento para resolver violações da política:

- **Alterações inesperadas na configuração detectadas.** Se a configuração de um recurso for alterada inesperadamente, trabalhe com os proprietários de carga de trabalho e da equipe IT para identificar a causa raiz e desenvolver um plano de correção.
- **A configuração de novos recursos não adere à política.** Trabalhe com as equipes do DevOps e proprietários da carga de trabalho para examinar as políticas de aceleração de implantação durante a inicialização do projeto para que todos os envolvidos compreendam os requisitos de política relevantes.
- **Falhas na implantação ou problemas de configuração causam atrasos em cronogramas do projeto.** Trabalhe com as equipes de desenvolvimento e os proprietários da carga de trabalho para garantir que a equipe compreenda como automatizar a implantação de recursos baseados em nuvem para consistência e capacidade de repetição. As implantações totalmente automatizadas devem ser necessárias no início do ciclo de desenvolvimento&mdash;tentar fazer isso mais tarde no ciclo de desenvolvimento geralmente leva a problemas e atrasos inesperados.

## <a name="next-steps"></a>Próximos passos

Usando o [modelo de Gerenciamento de Nuvem](./template.md), documente os processos e gatilhos que alinham-se ao plano de adoção da nuvem atual.

Para obter diretrizes sobre a execução de políticas de gerenciamento de nuvem em alinhamento com planos de adoção, consulte o artigo sobre melhoria de disciplina.

> [!div class="nextstepaction"]
> [Aperfeiçoamento da disciplina de Aceleração de implantação](./discipline-improvement.md)
