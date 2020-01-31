---
title: Melhoria da disciplina de Linha de Base de Segurança
description: Melhoria da disciplina de Linha de Base de Segurança
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 316a848e0f9f3f90a2f7badde3166733dce4a4c0
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808899"
---
# <a name="security-baseline-discipline-improvement"></a>Melhoria da disciplina de Linha de Base de Segurança

A disciplina de linha de base de segurança concentra-se em maneiras de estabelecer políticas que protegem a rede, os ativos e, mais importante, os dados que residirão na solução de um provedor de nuvem. Dentro das cinco disciplinas de governança de nuvem, a linha de base de segurança inclui a classificação do espaço digital e dos dados. Adicionalmente, inclui documentação de riscos, tolerância comercial e estratégias de mitigação associadas à segurança dos dados, ativos e rede. De uma perspectiva técnica, também inclui o envolvimento nas decisões relativas à [criptografia](../../decision-guides/encryption/index.md), [requisitos de rede](../../decision-guides/software-defined-network/index.md), [estratégias de identidade híbrida](../../decision-guides/identity/index.md) e aos [processos](./compliance-processes.md) utilizados para desenvolver políticas de Linha de Base de Segurança de nuvem.

Este artigo descreve algumas tarefas potenciais em que sua empresa pode se envolver para desenvolver e consolidar melhor a disciplina de Linha de Base de Segurança. Essas tarefas podem ser divididas entre as fases de planejamento, criação, adoção e operacional para a implementação de uma solução de nuvem, que depois são iteradas para permitir o desenvolvimento de uma [abordagem incremental para a governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

É impossível para qualquer pessoa documentar os requisitos a serem levados em consideração de todas as empresas. Portanto, este artigo descreve as atividades de exemplo potenciais e mínimas sugeridas para cada fase do processo de amadurecimento da governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de linha de base de segurança.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Essas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento de ambos os requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Esta fase de maturidade de governança une os resultados de negócios e as estratégias realizáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas ao estado digital e começa a planejar o esforço global de migração.

**Atividades mínimas sugeridas:**

- Avalie as opções da [cadeia de ferramentas de Linha de Base de Segurança](./toolchain.md).
- Desenvolver um documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Treinar e envolver as pessoas e equipes afetadas pelo desenvolvimento das diretrizes de arquitetura.
- Adicione tarefas de segurança prioritárias à lista de pendências de migração.

**Atividades potenciais:**

- Defina um esquema de classificação de dados.
- Conduza um processo de planejamento de propriedade digital para inventariar os ativos de TI atuais, potencializando os processos empresariais e as operações de suporte.
- Realize uma [análise de política](../../govern/policy-compliance/cloud-policy-review.md) para iniciar o processo de modernização das políticas de segurança de TI corporativas existentes e defina políticas de MVP que abordem riscos conhecidos.
- Analise as diretrizes de segurança da sua plataforma de nuvem. Para o Azure, é possível localizá-las na [Plataforma de Confiança do Serviço da Microsoft](https://www.microsoft.com/trustcenter/stp/default.aspx).
- Determine se a política de Linha de Base de Segurança inclui um [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl).
- Avalie os riscos empresariais relacionados a ativos, dados e rede, tendo como base as próximas três liberações, e meça a tolerância da organização para esses riscos.
- Analise o relatório das [principais tendências em segurança cibernética](https://www.microsoft.com/security/operations/security-intelligence-report) da Microsoft para obter uma visão geral do atual cenário de segurança.
- Considere desenvolver uma função [DevOps de Segurança](https://www.microsoft.com/en-us/securityengineering/devsecops) na organização.

<!-- "en-us" location is required for the URL above. -->

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo se concentra nas decisões, na preparação e na infraestrutura central que ocorrem após uma migração.

**Atividades mínimas sugeridas:**

- Implemente sua [linha de base de segurança ferramentas](./toolchain.md) distribuindo em uma fase de pré-implantação.
- Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Implemente tarefas de segurança na lista de pendências de migração priorizada.
- Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.

**Atividades potenciais:**

- Determine a estratégia de [criptografia](../../decision-guides/encryption/index.md) da organização para dados hospedados na nuvem.
- Avalie a estratégia de [identidade](../../decision-guides/identity/index.md) da implantação em nuvem. Determine como a solução de identidade baseada em nuvem coexistirá ou se integrará aos provedores de identidade locais.
- Determine políticas de limite de rede para [SDN (Rede Definida pelo Software)](../../decision-guides/software-defined-network/index.md) para garantir recursos de rede virtualizados seguros.
- Avalie as políticas de [acesso de privilégios mínimos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/roles-delegate-by-task) de sua organização e use funções baseadas em tarefas para fornecer acesso a recursos específicos.
- Aplique mecanismos de segurança e monitoramento a todos os serviços de nuvem e máquinas virtuais.
- Automatize as [políticas de segurança](../../decision-guides/policy-enforcement/index.md) sempre que possível.
- Analise sua política de Linha de Base de Segurança e determine se é necessário modificar os planos de acordo com as diretrizes de melhores práticas, conforme descrito em [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl).

## <a name="adopt-and-migrate"></a>Adotar e migrar

A migração é um processo incremental que se concentra no movimento, teste e adoção de aplicativos ou cargas de trabalho em um estado digital existente.

**Atividades mínimas sugeridas:**

- Migre sua [linha de base de segurança ferramentas](./toolchain.md) de pré-implantação para produção.
- Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.

**Atividades potenciais:**

- Revise as informações mais recentes sobre a Linha de Base de Segurança e ameaças para identificar novos riscos empresariais.
- Meça a tolerância da organização para lidar com novos riscos de segurança que possam surgir.
- Identifique os desvios da política e imponha correções.
- Ajuste a automação de controle de acesso e segurança para garantir a máxima conformidade com as políticas.
- Valide se as práticas recomendadas definidas durante as fases de compilação e pré-implantação foram executadas corretamente.
- Revise suas políticas de acesso de privilégio mínimo e ajuste os controles de acesso para maximizar a segurança.
- Teste a cadeia de ferramentas da Linha de Base de Segurança das cargas de trabalho para identificar e resolver quaisquer vulnerabilidades.

## <a name="operate-and-post-implementation"></a>Operação e pós-implementação

Depois que a transformação for concluída, a governança e as operações devem ser mantidas para o ciclo de vida natural de um aplicativo ou uma carga de trabalho. Essa fase de maturidade de governança se concentra em atividades que normalmente ocorrem depois que a solução é implementada e que o ciclo de transformação começa a se estabilizar.

**Atividades mínimas sugeridas:**

- Valide e refine sua [linha de base de segurança ferramentas](./toolchain.md).
- Personalize notificações e relatórios para alertá-lo sobre potenciais problemas de segurança.
- Refine as Diretrizes de Arquitetura para orientar futuros processos de adoção.
- Periodicamente, comunique e treine as equipes afetadas para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Descubra padrões e comportamento para as cargas de trabalho e configure as ferramentas de monitoramento e relatório para identificar e notificá-lo sobre qualquer atividade, acesso ou uso de recursos anormal.
- Atualize continuamente as políticas de monitoramento e relatório para detectar as vulnerabilidades, explorações e ataques mais recentes.
- Tenha procedimentos implantados para parar rapidamente o acesso não autorizado e desabilitar recursos que possam ter sido comprometidos por um invasor.
- Revise regularmente as melhores práticas de segurança mais recentes e aplique recomendações às políticas de segurança, automação e monitoramento de recursos, sempre que possível.

## <a name="next-steps"></a>Próximos passos

Agora que você já entende o conceito de governança de segurança de nuvem, prossiga e saiba [quais as diretrizes de segurança e melhores práticas a Microsoft oferece](./azure-security-guidance.md) para o Azure.

> [!div class="nextstepaction"]
> [Saiba mais sobre as diretrizes de segurança do azure](./azure-security-guidance.md)
> [introdução à segurança do Azure](https://docs.microsoft.com/azure/security/azure-security)
> [saiba mais sobre registro em log, relatórios e monitoramento](../../decision-guides/logging-and-reporting/index.md)
