---
title: Aprimoramento da disciplina de linha de base de identidade
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprimoramento da disciplina de linha de base de identidade
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 265365d2064349f53d61b10af4af053c418c871a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547456"
---
# <a name="identity-baseline-discipline-improvement"></a>Aprimoramento da disciplina de linha de base de identidade

A disciplina de linha de base de identidade concentra-se em maneiras de estabelecer políticas que garantem a consistência e a continuidade de identidades de usuário, independentemente do provedor de nuvem que hospeda o aplicativo ou a carga de trabalho. Dentro das cinco disciplinas de governança de nuvem, a linha de base de identidade inclui decisões relacionadas à [estratégia de identidade híbrida](../../decision-guides/identity/index.md), avaliação e extensão de repositórios de identidades, implementação de logon único (mesmo logon), auditoria e monitoramento de uso não autorizado ou atores mal-intencionados. Em alguns casos, ele também pode envolver decisões para modernizar, consolidar ou integrar vários provedores de identidade.

Este artigo descreve algumas tarefas potenciais pelas quais sua empresa pode se envolver para desenvolver melhor e amadurecer a disciplina de linha de base de identidade. Essas tarefas podem ser divididas em fases de planejamento, criação, adoção e operação de implementação de uma solução de nuvem, que são então iteradas para permitir o desenvolvimento de uma [abordagem incremental para governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

É impossível para qualquer documento considerar os requisitos de todas as empresas. Como tal, este artigo descreve as atividades de exemplo mínimas e potenciais do sugerido para cada fase do processo de desenvolvimento de governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de linha de base de identidade.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Estas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento dos dois requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Essa fase de maturidade de governança preenche a divisão entre resultados de negócios e estratégias acionáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas para o espaço digital e começa a planejar o esforço geral de migração.

**Mínimo de atividades sugeridas:**

- Avalie suas opções de [ferramentas de identidade](./toolchain.md) e implemente uma estratégia híbrida apropriada para sua organização.
- Desenvolva um documento de diretrizes de arquitetura de rascunho e distribua para as principais partes interessadas.
- Instrua e envolva as pessoas e equipes afetadas pelo desenvolvimento de diretrizes de arquitetura.

**Atividades potenciais:**

- Defina funções e atribuições que governarão o gerenciamento de identidade e acesso na nuvem.
- Defina seus grupos locais e mapeie para funções baseadas em nuvem correspondentes.
- Provedores de identidade de inventário (incluindo identidades controladas por banco de dados usadas por aplicativos personalizados).
- Consolide e integre provedores de identidade em que existam duplicação, para simplificar a solução de identidade geral e reduzir o risco.
- Avaliar a compatibilidade híbrida de provedores de identidade existentes.
- Para provedores de identidade que não são compatíveis com híbrido, avalie as opções de consolidação ou de substituição.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo concentra-se nas decisões, prontidão e infraestrutura básica que prosseguem com uma migração.

**Mínimo de atividades sugeridas:**

- Considere um teste piloto antes de implementar seu [ferramentas de identidade](./toolchain.md), garantindo que ele Simplifique a experiência do usuário o máximo possível.
- Aplique comentários dos testes do piloto à pré-implantação. Repita até que os resultados sejam aceitáveis.
- Atualize o documento de diretrizes de arquitetura para incluir os planos de implantação e adoção de usuário, e distribua para as principais partes interessadas.
- Considere estabelecer um programa pioneiro e distribuir para um número limitado de usuários.
- Continue a treinar as pessoas e as equipes mais afetadas pelas diretrizes de arquitetura.

**Atividades potenciais:**

- Avalie sua arquitetura lógica e física e determine uma [estratégia de identidade híbrida](../../decision-guides/identity/index.md).
- Mapeie políticas de gerenciamento de acesso de identidade, como atribuições de ID de logon, e escolha o método de autenticação apropriado para o Azure AD.
  - Se federado, habilite restrições de locatário para contas administrativas.
- Integre seus diretórios locais e na nuvem.
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

## <a name="adopt-and-migrate"></a>Adote e migre

A migração é um processo incremental que se concentra na movimentação, no teste e na adoção de aplicativos ou cargas de trabalho em um espaço digital existente.

**Mínimo de atividades sugeridas:**

- Migre seu [ferramentas de identidade](./toolchain.md) do desenvolvimento para a produção.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar a adoção do usuário.

**Atividades potenciais:**

- Valide se as práticas recomendadas definidas durante as fases de pré-implantação de compilação foram executadas corretamente.
- Valide e refine sua [estratégia de identidade híbrida](../../decision-guides/identity/index.md).
- Certifique-se de que cada aplicativo ou carga de trabalho continue a alinhar com a estratégia de identidade antes do lançamento.
- Valide se o SSO (logon único) e o SSO contínuo estão funcionando conforme o esperado para seus aplicativos.
- Reduza ou elimine o número de repositórios de identidades alternativos.
- Analisar a necessidade de qualquer armazenamento de identidade no aplicativo ou no banco de dados. As identidades que estão fora de um provedor de identidade adequado (primário ou de terceiros) podem representar o risco para o aplicativo e os usuários.
- Habilite o acesso condicional para [aplicativos federados locais](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup).
- Distribua a identidade entre regiões globais em vários hubs com sincronização entre regiões.
- Estabelecer uma federação de RBAC (controle de acesso baseado em função) central.

## <a name="operate-and-post-implementation"></a>Operar e pós-implementação

Depois que a transformação for concluída, a governança e as operações deverão residir para o ciclo de vida natural de um aplicativo ou carga de trabalho. Essa fase de maturidade de governança se concentra nas atividades que normalmente vêm depois que a solução é implementada e o ciclo de transformação começa a estabilizar.

**Mínimo de atividades sugeridas:**

- Personalize seu [ferramentas de linha de base de identidade](./toolchain.md) com base nas alterações nas necessidades de identidade dinâmicas de sua organização.
- Automatize notificações e relatórios para alertar sobre possíveis ameaças mal-intencionadas.
- Monitore e relate o uso do sistema e o andamento da adoção do usuário.
- Relate as métricas pós-implantação e distribua para os participantes.
- Refine as diretrizes de arquitetura para orientar processos futuros de adoção.
- Comunique-se e instrua continuamente as equipes afetadas periodicamente para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Realize auditorias periódicas de políticas de identidade e práticas de adesão.
- Garanta que contas de usuário confidenciais (CEO, CFO, VP, etc.) estejam sempre habilitadas para a autenticação multifator e a detecção de logon anômala.
- Verifique se há atores mal-intencionados e violações de dados regularmente, principalmente aqueles relacionados a fraudes de identidade, como takeovers de conta de administrador em potencial.
- Configure uma ferramenta de monitoramento e relatório.
- Considere a integração mais próxima com sistemas de segurança e prevenção contra fraudes.
- Examine regularmente os direitos de acesso para usuários ou funções elevados.
  - Identifique cada usuário que está qualificado para ativar o privilégio de administrador.
- Examine a integração, a integração e os processos de atualização de credenciais.
- Investigue os níveis crescentes de automação e comunicação entre os módulos IAM (gerenciamento de acesso de identidade).
- Considere a implementação de uma abordagem de DevSecOps (operações de segurança de desenvolvimento).
- Execute uma análise de impacto para avaliar os resultados de custos, segurança e adoção do usuário.
- Periodicamente, produza um relatório de impacto que mostra as alterações nas métricas criadas pelo sistema e estima os impactos comerciais da [estratégia de identidade híbrida](../../decision-guides/identity/index.md).
- Estabeleça o monitoramento integrado recomendado pela [central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro).

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu o conceito de governança de identidade de nuvem, examine o [ferramentas de linha de base de identidade](./toolchain.md) para identificar as ferramentas e os recursos do Azure que você precisará ao desenvolver a disciplina de governança de linha de base de identidade na plataforma Azure.

> [!div class="nextstepaction"]
> [Ferramentas de linha de base de identidade para o Azure](./toolchain.md)
