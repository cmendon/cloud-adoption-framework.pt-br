---
title: Melhoria da disciplina de Linha de base de identidade
description: Melhoria da disciplina de Linha de base de identidade
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6adb2e0d6edaacd45e41b8ac3eadb57969cad160
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807182"
---
# <a name="identity-baseline-discipline-improvement"></a>Melhoria da disciplina de Linha de base de identidade

Esta disciplina de Linha de base de identidade se concentra em maneiras de estabelecer políticas que garantem a consistência e continuidade das identidades do usuário independentemente do provedor de nuvem que hospeda o aplicativo ou a carga de trabalho. Dentro das Cinco disciplinas de governança de nuvem, a Identidade de linha de base inclui decisões a respeito da [Estratégia de Identidade Híbrida](../../decision-guides/identity/index.md), avaliação e extensão de repositórios de identidade, implementação de logon único (mesmo logon), auditoria e monitoramento de uso não autorizado ou atores mal-intencionados. Em alguns casos, também pode envolver decisões para modernizar, consolidar ou integrar vários provedores de identidade.

Este artigo descreve algumas tarefas potenciais em que sua empresa pode se envolver para desenvolver e consolidar melhor a disciplina de Linha de Base de Identidade. Essas tarefas podem ser divididas entre as fases de planejamento, criação, adoção e operacional para a implementação de uma solução de nuvem, que depois são iteradas para permitir o desenvolvimento de uma [abordagem incremental para a governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

É impossível para qualquer pessoa documentar os requisitos a serem levados em consideração de todas as empresas. Portanto, este artigo descreve as atividades de exemplo potenciais e mínimas sugeridas para cada fase do processo de amadurecimento da governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de linha de base de identidade.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Essas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento de ambos os requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Esta fase de maturidade de governança une os resultados de negócios e as estratégias realizáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas ao estado digital e começa a planejar o esforço global de migração.

**Atividades mínimas sugeridas:**

- Avaliar suas opções de [cadeia de ferramentas de Identidade](./toolchain.md) e implementar uma estratégia híbrida que é apropriada para sua organização.
- Desenvolver um documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Treinar e envolver as pessoas e equipes afetadas pelo desenvolvimento das diretrizes de arquitetura.

**Atividades potenciais:**

- Definir funções e atribuições que regem a identidade e acesso de gerenciamento na nuvem.
- Definir seus grupos locais e mapear para as funções correspondentes com base em nuvem.
- Provedores de identidade de inventário (incluindo identidades controladas por banco de dados usados por aplicativos personalizados).
- Consolide e integre provedores de identidade em que existam duplicação, para simplificar a solução de identidade geral e reduzir o risco.
- Avaliar a compatibilidade híbrida de provedores de identidade existentes.
- Para provedores de identidade que não são compatíveis híbridos, avalie as opções de consolidação ou a substituição.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo se concentra nas decisões, na preparação e na infraestrutura central que ocorrem após uma migração.

**Atividades mínimas sugeridas:**

- Considerar um teste do piloto antes de implementar sua [cadeia de ferramentas de Identidade](./toolchain.md), garantindo simplifique a experiência do usuário tanto quanto possível.
- Aplique comentários dos testes do piloto à pré-implantação. Repetir até que os resultados sejam aceitáveis.
- Atualizar o documento das Diretrizes de Arquitetura para incluir a implantação e planos de adoção de usuário e distribuir para os stakeholders.
- Considerar a possibilidade de estabelecer um programa de adoção antecipada e distribuir para um número limitado de usuários.
- Continuar a instruir as pessoas e equipes mais afetadas pelas diretrizes de arquitetura.

**Atividades potenciais:**

- Avaliar sua arquitetura lógica e física e determinar uma [Estratégia de Identidade Híbrida](../../decision-guides/identity/index.md).
- Mapear as políticas de gerenciamento de acesso de identidade, como atribuições de ID de logon e escolher o método de autenticação apropriado para o Microsoft Azure Active Directory.
  - Se federado, habilite as restrições de locatário para contas administrativas.
- Integrar seus diretórios locais ao e de nuvem.
- Considere usar os seguintes modelos de acesso:
  - Modelo [de acesso de privilégios mínimos](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) .
  - Modelo de acesso de [linha de base de identidade privilegiada](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure) .
- Finalize todos os detalhes de preintegração e veja as [práticas recomendadas de identidade](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices).
  - Habilite a identidade única, SSO (logon único) ou SSO contínuo.
  - Configurar a autenticação multifator para administradores.
  - Consolide ou integre provedores de identidade, quando necessário.
  - Implemente ferramentas necessárias para centralizar o gerenciamento de identidades.
  - Habilite o acesso JIT (just-in-time) e o alerta de alteração de função.
  - Conduza uma análise de risco das principais atividades de administração para atribuir funções internas.
  - Considere uma distribuição atualizada de autenticação mais forte para todos os usuários.
  - Habilite o PIM (linha de base de identidade privilegiada) para JIT (usando a ativação de tempo limitado) para funções administrativas adicionais.
  - Separe as contas de usuário de contas de administrador global (para garantir que os administradores não abram emails inadvertidamente ou executem programas associados às suas contas de administrador global).

## <a name="adopt-and-migrate"></a>Adotar e migrar

A migração é um processo incremental que se concentra no movimento, teste e adoção de aplicativos ou cargas de trabalho em um estado digital existente.

**Atividades mínimas sugeridas:**

- Migrar sua [cadeia de ferramentas de Identidade](./toolchain.md) do desenvolvimento à produção.
- Atualizar o documento com o esboço das Diretrizes de Arquitetura e distribuí-lo aos principais stakeholders.
- Desenvolver materiais e documentações educativas, comunicações de conscientização, incentivos e outros programas para ajudar a conduzir a adoção de usuários.

**Atividades potenciais:**

- Valide se as práticas recomendadas definidas durante as fases de pré-implantação de compilação foram executadas corretamente.
- Valide e refine sua [estratégia de identidade híbrida](../../decision-guides/identity/index.md).
- Certificar-se de que cada aplicativo ou carga de trabalho se alinha com a estratégia de identidade antes do lançamento.
- Validar esse logon único (SSO) e o SSO contínuo está funcionando conforme o esperado para seus aplicativos.
- Reduza ou elimine o número de repositórios de identidades alternativos.
- Analisar a necessidade de quaisquer armazenamentos de identidade no aplicativo ou no banco de dados. Identifica que fora de um provedor de identidade adequado (primários ou terceiros) podem representar risco para o aplicativo e os usuários.
- Habilitar acesso condicional para [aplicativos federados no local](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup).
- Distribuir a identidade entre regiões globais em vários hubs com a sincronização entre regiões.
- Estabelecer federação de RBAC (controle) de acesso baseado em função central.

## <a name="operate-and-post-implementation"></a>Operação e pós-implementação

Depois que a transformação for concluída, a governança e as operações devem ser mantidas para o ciclo de vida natural de um aplicativo ou uma carga de trabalho. Essa fase de maturidade de governança se concentra em atividades que normalmente ocorrem depois que a solução é implementada e que o ciclo de transformação começa a se estabilizar.

**Atividades mínimas sugeridas:**

- Personalize seu [ferramentas de linha de base de identidade](./toolchain.md) com base nas alterações nas necessidades de identidade dinâmicas de sua organização.
- Automatizar as notificações e relatórios para alertar a respeito de possíveis ameaças mal-intencionadas.
- Monitorar e informar sobre o andamento da adoção de uso e de usuário do sistema.
- Relatar a respeito das métricas de pós-implantação e distribuir aos stakeholders.
- Refine as Diretrizes de Arquitetura para orientar futuros processos de adoção.
- Periodicamente, treine as equipes afetadas para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Realizar auditorias periódicas de políticas de identidade e práticas de conformidade.
- Garanta que contas de usuário confidenciais (CEO, CFO, VP, etc.) estejam sempre habilitadas para a autenticação multifator e a detecção de logon anômala.
- Verificar atores mal-intencionados e violações de dados regularmente, especialmente as relacionadas a fraude de identidade, como aquisições potenciais de conta de administrador.
- Configurar uma ferramenta de monitoramento e emissão de relatório.
- Considerar a integração mais de perto com sistemas de segurança e prevenção de fraudes.
- Examinar regularmente os direitos de acesso para usuários com privilégios elevados ou funções.
  - Identificar cada usuário que é elegível para ativar o privilégio de administrador.
- Examine os processos de integração, remoção e atualização de credenciais.
- Investigar os níveis crescentes de automação e a comunicação entre os módulos de gerenciamento de acesso de identidade (IAM).
- Considerar implementar uma abordagem de operações (DevSecOps) de segurança de desenvolvimento.
- Realizar uma análise de impacto para medir os resultados em custos, segurança e adoção do usuário.
- Periodicamente, produzir um relatório de impacto que mostra as alterações nas métricas criadas pelo sistema e estimar o impacto de negócios da [estratégia de identidade híbrida](../../decision-guides/identity/index.md).
- Estabelecer monitoramento integrado recomendado pela [Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro).

## <a name="next-steps"></a>Próximos passos

Agora que você entende o conceito de governança de identidade de nuvem, examine a [cadeia de ferramentas da Linha de base de identidade](./toolchain.md) para identificar as ferramentas do Azure e recursos que você precisará ao desenvolver a disciplina de governança da Linha de base de identidade na plataforma do Azure.

> [!div class="nextstepaction"]
> [Cadeia de ferramentas de linha de base de identidade para o Azure](./toolchain.md)
