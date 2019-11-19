---
title: Estabelecer os processos de conformidade com políticas
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Estabeleça processos para garantir a conformidade com as políticas corporativas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6671efc087d718a44de97062dcf8c32498cfdb81
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74159847"
---
<!-- markdownlint-disable MD026 -->

# <a name="establish-policy-adherence-processes"></a>Estabelecer os processos de conformidade com políticas

Após estabelecer as declarações da política de nuvem e elaborar um guia de planejamento, será necessário criar uma estratégia para garantir que a implantação na nuvem permaneça em conformidade com os requisitos da política. Essa estratégia precisará abranger os processos de comunicação e de análise em andamento da sua equipe de governança de nuvem, estabelecer critérios para quando as violações de política exigirem ação e definir os requisitos para sistemas de monitoramento e conformidade automatizados que irão detectar violações e disparar ações de correção.

Consulte as seções de política corporativa dos [guias de governança acionáveis](../guides/index.md) para obter exemplos de como o processo de adesão à política se encaixa em um plano de governança de nuvem.

## <a name="prioritize-policy-adherence-processes"></a>Priorizar processos de adesão à política

Quanto investimento em desenvolvimento de processos é necessário para apoiar os objetivos da política? Dependendo do tamanho e da maturidade da implantação de nuvem, o esforço necessário para estabelecer processos que assegurem a conformidade e os custos associados a esse esforço podem variar amplamente.

Para pequenas implantações que consistem em recursos de desenvolvimento e teste, os requisitos da política podem ser simples e requerem direcionamento de poucos recursos dedicados. Por outro lado, uma implantação de nuvem crítica consolidada com necessidades de segurança e desempenho de alta prioridade pode exigir uma equipe de funcionários, processos internos abrangentes e ferramentas de monitoramento personalizadas para atender às metas da política.

Como primeiro etapa para definir a estratégia de adesão à política, avalie como os processos abordados abaixo podem reforçar os requisitos da política. Determine quanto esforço é viável para investir nesses processos e, em seguida, use essas informações para estabelecer planos orçamentários e de pessoal realistas para atender a essas necessidades.

## <a name="establish-cloud-governance-team-processes"></a>Estabelecer processos da equipe de governança de nuvem

Antes de definir gatilhos para a correção de conformidade de política, você precisa estabelecer os processos gerais que sua equipe usará e como as informações serão compartilhadas e escalonadas entre a equipe de ti e a equipe de governança de nuvem.

### <a name="assign-cloud-governance-team-members"></a>Atribuir membros da equipe de governança de nuvem

Sua equipe de governança de nuvem fornecerá orientação contínua sobre a conformidade da política e tratará os problemas relacionados à política que surgiram ao implantar e operar seus ativos de nuvem. Ao criar essa equipe, convide os membros da equipe que têm experiência em áreas cobertas por suas declarações de política definidas e riscos identificados.

Para implantações iniciais de teste, isso pode ser limitado a alguns administradores de sistema responsáveis por estabelecer os conceitos básicos de governança. À medida que seus processos de governança forem amadurecedos, revise a associação da equipe de diretrizes da nuvem regularmente para garantir que você possa resolver corretamente os novos riscos potenciais e os requisitos de política. Identifique membros de sua equipe de ti e de negócios com experiência relevante ou interesse em áreas específicas de governança e inclua-os em suas equipes em uma base permanente ou temporária, conforme necessário.

### <a name="reviews-and-policy-iteration"></a>Análises e política de iteração

Conforme os recursos adicionais e as cargas de trabalho são implantados, a equipe de governança de nuvem precisará garantir que novas cargas de trabalho ou ativos estejam em conformidade com os requisitos de política. Avalie novos requisitos de equipes de desenvolvimento de carga de trabalho para garantir que suas implantações planejadas se alinhem com seus guias de design e atualize suas políticas para dar suporte a esses requisitos quando apropriado.

Planeje avaliar os novos riscos potenciais e atualizar as instruções de política e guias de design, conforme necessário. Trabalhe com a equipe de ti e as equipes de carga de trabalho para avaliar os novos recursos e serviços do Azure em uma base contínua. Também agende ciclos de revisão regulares cada uma das cinco disciplinas de governança para garantir que a política seja atual e em conformidade.

### <a name="education"></a>Educação

A conformidade com a política exige que a equipe de TI e os desenvolvedores reconheçam os requisitos da política que afetam suas áreas de responsabilidade. Planeje dedicar recursos para documentar decisões e requisitos e instruir todas as equipes relevantes sobre os guias de planejamento que dão suporte aos requisitos da política.

Conforme a política for alterada, atualize regularmente a documentação e os materiais de treinamento e garanta que os esforços educacionais comuniquem os requisitos atualizados e as diretrizes para a equipe de TI relevante.

Em vários estágios de sua jornada de nuvem, talvez você ache melhor consultar os parceiros e os programas de treinamento profissional para aprimorar a educação de sua equipe, tanto tecnicamente quanto de forma conceitual. Além disso, muitos acham que as certificações formais são uma adição valiosa ao seu portfólio de educação e devem ser consideradas.

### <a name="establish-escalation-paths"></a>Estabelecer caminhos de escalonamento

Se um recurso tornar-se não conforme, quem será notificado? Se a equipe de TI detectar um problema de conformidade com a política, a quem contatará? Verifique se o processo de escalonamento para a equipe de governança de nuvem está claramente definido. Garanta que esses canais de comunicação sejam mantidos atualizados para refletir as alterações na equipe e na organização.

## <a name="violation-triggers-and-actions"></a>Gatilhos e ações de violação

Depois de definir sua equipe de governança de nuvem e seus processos, você precisa definir explicitamente o que se qualifica como violações de conformidade que dispararão ações e quais devem ser essas ações.

### <a name="define-triggers"></a>Definir gatilhos

Para cada uma das declarações da política, analise os requisitos para determinar o que constitui uma violação da política. Gere os gatilhos usando as informações que você já estabeleceu como parte do processo de definição da política.

- **Tolerância a riscos:** Crie gatilhos de violação com base nas métricas e nos indicadores de risco estabelecidos como parte de sua [análise de tolerância a riscos](./risk-tolerance.md).
- **Requisitos de política definidos:** As instruções de política podem fornecer SLA (contrato de nível de serviço), BCDR (continuidade de negócios e recuperação de desastre) ou requisitos de desempenho que devem ser usados como base para gatilhos de conformidade.

### <a name="define-actions"></a>Definir ações

Cada gatilho de violação deve ter uma ação correspondente. Ações disparadas sempre devem notificar uma equipe de ti apropriada ou membro da equipe de governança de nuvem quando ocorrer uma violação. Essa notificação pode levar a uma revisão manual do problema de conformidade ou à abertura de um processo de correção predefinido, dependendo do tipo e da severidade da violação detectada.

Alguns exemplos de gatilhos e ações de violação:

| Disciplina de Governança de Nuvem | Amostra do gatilho | Ação de exemplo |
|-----------------------------|----------------|---------------|
| Gerenciamento de Custos | Os gastos mensais com a nuvem são mais de 20% superior ao esperado. | Notifique o líder da unidade de cobrança que iniciará uma revisão do uso do recurso. |
| Linha de base de segurança | Detectar atividade suspeita do usuário. | Notifique a equipe de segurança de ti e desabilite a conta de usuário suspeita. |
| Consistência de recursos | A utilização da CPU para uma carga de trabalho é maior que 90%. | Notifique a equipe de operações de ti e expanda recursos adicionais para lidar com a carga. |

## <a name="automation-of-monitoring-and-compliance"></a>Automação de monitoramento e conformidade

Após definir os gatilhos de violação de conformidade e as ações, você poderá iniciar o planejamento de como melhor utilizar as ferramentas de relatório e registro em log e outros recursos da plataforma de nuvem para ajudar a automatizar a estratégia de monitoramento e conformidade da política.

Para obter ajuda para escolher o melhor padrão de monitoramento para sua implantação, consulte o [Guia de decisão de registro em log e relatório](../../decision-guides/logging-and-reporting/index.md).

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre a conformidade regulatória na nuvem.

> [!div class="nextstepaction"]
> [Conformidade regulatória](./regulatory-compliance.md)
