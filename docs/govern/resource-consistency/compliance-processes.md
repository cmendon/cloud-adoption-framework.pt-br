---
title: Processos de conformidade de política de Consistência de Recursos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processos de conformidade de política de Consistência de Recursos
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5daec332aa4fdbc75e15bfd9948fe6db52935d20
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030664"
---
# <a name="resource-consistency-policy-compliance-processes"></a>Processos de conformidade de política de Consistência de Recursos

Este artigo descreve uma abordagem para processos de adesão a políticas que regem a [Consistência de Recursos](./index.md). A governança de consistência de recursos de nuvem eficaz começa com recorrentes processos manuais, projetados para identificar a ineficiência operacional, melhorar o gerenciamento de recursos implantados e garantir que as cargas de trabalho de missão crítica tenham interrupções mínimas. Esses processos manuais são complementados com monitoramento, automação e ferramentas para ajudar a reduzir a sobrecarga de governança e permitir respostas mais rápidas para desvio da política.

## <a name="planning-review-and-reporting-processes"></a>Planejar, revisar e relatar processos

Plataformas de nuvem fornecem uma matriz de ferramentas de gerenciamento e recursos que você pode usar para organizar, provisionar, dimensionar e minimizar o tempo de inatividade. Usar essas ferramentas para estruturar e operar com eficiência suas implantações em nuvem de maneiras que corrijam riscos potenciais requer processos e políticas bem considerados, além de cooperação com as equipes de operações de ti e os interessados comerciais.

A seguir, é apresentado um conjunto de exemplos de processos normalmente envolvidos na disciplina de Consistência de Recurso. Use esses exemplos como ponto de partida ao planejar os processos que permitirão continuar a atualizar a política de Consistência de Recurso com base nas alterações dos negócios e no feedback das equipes de TI encarregadas de transformar as diretrizes de governança em ações.

**Avaliação e planejamento inicial de riscos:** Como parte da sua adoção inicial da disciplina de Consistência de Recursos, identifique seus riscos comerciais principais e as tolerâncias relacionadas às operações e ao gerenciamento de TI. Use essas informações para discutir riscos técnicos específicos com membros de suas equipes de ti e proprietários de carga de trabalho para desenvolver um conjunto de linha de base de políticas de consistência de recursos projetado para corrigir esses riscos, estabelecendo sua estratégia de governança inicial.

**Planejamento de implantação**: Antes de implantar qualquer ativo, execute uma revisão para identificar novos riscos operacionais. Estabeleça requisitos de recursos e padrões de demanda esperada e identifique as necessidades de escalabilidade e possíveis oportunidades de otimização do uso. Certifique-se também que os planos de backup e recuperação estão em vigor.

**Teste de implantação:** Como parte da implantação, a equipe de governança de nuvem, em cooperação com suas equipes de operações de nuvem, será responsável por revisar a implantação para validar a conformidade da política de consistência de recursos.

**Planejamento anual**: Anualmente, realize uma análise de alto nível da estratégia de Consistência de recurso. Explore os planos de expansão corporativa futura ou prioridades e atualizar as estratégias de adoção de nuvem para identificar potencial aumento de risco ou outras necessidades de Consistência de Recurso. Além disso, use esse tempo para revisar as melhores práticas mais recentes para a Consistência de Recurso e integre esses a suas políticas e reveja os processos.

**Análise e planejamento trimestral:** Trimestralmente, execute uma análise de dados operacionais e relatórios de incidentes para identificar quaisquer alterações necessárias na política de consistência de recurso. Como parte desse processo, revise as alterações no uso de recursos e desempenho para identificar os ativos que requerem aumentar ou diminuir em alocação de recursos e identificam quaisquer ativos que são candidatos à desativação ou cargas de trabalho.

Esse processo de planejamento também é um bom momento para avaliar a associação atual de sua equipe de governança de nuvem para as lacunas de conhecimento relacionadas à política nova ou alteração e aos riscos relacionados à consistência de recursos como uma disciplina. Convide a equipe de TI relevante a participar das análises e planejamentos como consultores temporários ou membros permanentes da sua equipe.

**Educação e treinamento:** Em uma base Bimonthly, ofereça sessões de treinamento para garantir que a equipe de ti e os desenvolvedores estejam atualizados sobre os requisitos e as diretrizes mais recentes da política de consistência de recursos. Como parte desse processo, revise e atualize todas as documentações ou outros recursos de treinamento para garantir que estejam em sincronia com as últimas declarações da política corporativa.

**Revisões mensais de auditoria e relatórios:** Mensalmente, realize uma auditoria em todas as implantações na nuvem para garantir o alinhamento contínuo com a política de Consistência de recurso. Revise as atividades relacionadas com a equipe de TI e identifique quaisquer problemas de conformidade que ainda não são tratados como parte do processo de monitoramento e imposição em andamento. O resultado dessa análise é um relatório para a equipe de estratégia de nuvem e cada equipe de adoção da nuvem para comunicar o desempenho geral e a adesão à política. O relatório também é armazenado para fins de auditoria e legais.

## <a name="ongoing-monitoring-processes"></a>Processos de monitoramento contínuo

Determinar se a estratégia de governança de Consistência de Recurso é bem-sucedida depende da visibilidade no estado atual e futuro da sua infraestrutura de nuvem. Sem a capacidade de analisar as métricas relevantes e dados da integridade e atividade do ambiente da nuvem, você não pode identificar as mudanças nos seus riscos ou detectar violações das suas tolerâncias a riscos. Os processos de administração contínua discutidos acima exigem dados de qualidade para garantir que a política possa ser modificada para otimizar o uso de recursos de nuvem e melhorar o desempenho geral de cargas de trabalho hospedadas na nuvem.

Certifique-se de que as equipes de TI implementaram sistemas de monitoramento automatizados para a infraestrutura de nuvem que captura os dados de log relevantes que você precisa para avaliar os riscos. Seja proativo no monitoramento desses sistemas para garantir a detecção e mitigação imediatas de possíveis violações da política e garanta que a sua estratégia de monitoramento esteja em linha com as suas necessidades operacionais.

## <a name="violation-triggers-and-enforcement-actions"></a>Gatilhos de violação e ações de imposição

Como a conformidade da política de consistência de recursos pode levar à interrupção do serviço crítico ou a riscos de sobreexecuções de custos significativos, a equipe de governança de nuvem deve ter visibilidade em incidentes de não conformidade. Verifique se a equipe de ti tem caminhos de escalonamento claros para relatar esses problemas aos membros da equipe de governança mais adequados para identificar e verificar se os problemas de política são mitigados depois de detectados.

Quando violações forem detectadas, será necessário realizar ações para realinhar a política o mais rápido possível. A equipe de TI pode automatizar a maioria dos gatilhos de violação, usando as ferramentas descritas na [cadeia de Consistência de recurso do Azure](./toolchain.md).

Os gatilhos e ações de imposição a seguir fornecem exemplos que você pode consultar ao planejar como usar os dados de monitoramento para resolver violações da política:

- **Recurso provisionado detectado.** Recursos detectados usando menos de 60% da capacidade de CPU ou memória devem ser dimensionados automaticamente para baixo ou desprovisionar os recursos para reduzir os custos.
- **Recurso subprovisionado detectado.** Recursos detectados usando menos de 80% da capacidade de CPU ou memória devem ser dimensionados automaticamente para baixo ou desprovisionar os recursos para reduzir os custos.
- **Criação de recursos não marcados.** Qualquer solicitação para criar um recurso sem marcas de metadados necessárias será rejeitada automaticamente.
- **Interrupção de recurso crítico detectada.** A equipe de TI é notificada sobre todas as interrupções detectadas de interrupções de missão crítica. Se a interrupção não for resolvida imediatamente, a equipe irá escalonar o problema e notificar os proprietários da carga de trabalho e a equipe de governança de nuvem. A equipe de governança de nuvem controlará o problema até a resolução e a orientação da atualização se a revisão da política for necessária para evitar futuros incidentes.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de Gerenciamento de Nuvem](./template.md), documente os processos e gatilhos que alinham-se ao plano de adoção da nuvem atual.

Para obter diretrizes sobre a execução de políticas de gerenciamento de nuvem em alinhamento com planos de adoção, consulte o artigo sobre melhoria de disciplina.

> [!div class="nextstepaction"]
> [Melhoria da disciplina de Consistência de recursos](./discipline-improvement.md)
