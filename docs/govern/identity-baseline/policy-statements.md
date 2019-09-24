---
title: Instruções de política de exemplo de Linha de base de identidade
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instruções de política de exemplo de Linha de base de identidade
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 39742436ab6c4a176e40ce8188c13cca55f23521
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222140"
---
# <a name="identity-baseline-sample-policy-statements"></a>Instruções de política de exemplo de Linha de base de identidade

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que esta política abordará.
- **Instrução da política:** Uma clara explicação de resumo dos requisitos de política.
- **Opções de design:** Recomendações viáveis, especificações ou outras diretrizes que as equipes de TI e desenvolvedores possam usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à identidade comuns. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="lack-of-access-controls"></a>Falta de controles de acesso

**Risco técnico:** Configurações de controle de acesso insuficiente ou ad hoc podem apresentar riscos de acesso não autorizado a recursos confidenciais ou críticos.

**Instrução da política:** Todos os ativos implantados na nuvem devem ser controlados usando identidades e funções aprovadas pelas políticas de governança atual.

**Possíveis opções de design:** [Acesso condicional ao Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) é o mecanismo de controle de acesso padrão no Azure.

## <a name="overprovisioned-access"></a>Acesso superprovisionados

**Risco técnico:** Usuários e grupos com controle sobre os recursos, além de suas áreas de responsabilidade podem resultar em modificações não autorizadas, levando a vulnerabilidades de segurança ou interrupções.

**Instrução da política:** As políticas a seguir serão implementadas:

- Um modelo de acesso com privilégios mínimos será aplicado a todos os recursos envolvidos em aplicativos de missão crítica ou em dados protegidos.
- Permissões elevadas devem ser uma exceção e essas exceções devem ser registradas com a equipe de governança de nuvem. As exceções serão auditadas regularmente.

**Possíveis opções de design:** Consulte as [práticas recomendadas de gerenciamento de identidade do Azure](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices) para implementar uma estratégia de RBAC (controle de acesso baseado em função) que restringe o acesso com base na [necessidade de conhecer](https://wikipedia.org/wiki/Need_to_know) os princípios de [segurança de privilégios mínimos](https://wikipedia.org/wiki/Principle_of_least_privilege) .

## <a name="lack-of-shared-management-accounts-between-on-premises-and-the-cloud"></a>Falta de contas de gerenciamento compartilhado entre local e nuvem

**Risco técnico:** A equipe administrativa ou de gerenciamento de TI com contas em seu Active Directory Domain Services local pode não ter acesso suficiente aos recursos da nuvem, pode não ser capaz de resolver problemas operacionais ou de segurança com eficiência.

**Instrução da política:** Todos os grupos que têm privilégios elevados na infraestrutura do Active Directory Domain Services local devem ser mapeados para uma função RBAC aprovada.

**Possíveis opções de design:** Implemente uma solução de identidade híbrida entre sua Azure Active Directory baseada em nuvem e sua Active Directory local e adicione os grupos locais necessários às funções de RBAC necessárias para realizar seu trabalho.

## <a name="weak-authentication-mechanisms"></a>Mecanismos de autenticação fraca

**Risco técnico:** Sistemas de gerenciamento de identidade com métodos de autenticação de usuário insuficientemente seguro, como combinações de usuário/senha básica, podem levar a senhas comprometidas ou violadas, fornecendo um grande risco de acesso não autorizado para proteger os sistemas de nuvem.

**Instrução da política:** Todas as contas são necessárias para entrar em recursos protegidos usando um método de autenticação multifator.

**Possíveis opções de design:** Para o Azure Active Directory, implemente a [Autenticação Multifator do Azure](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) como parte do processo de autorização de usuário.

## <a name="isolated-identity-providers"></a>Provedores de identidade isolados

**Risco técnico:** Provedores de identidade incompatíveis podem resultar na incapacidade de compartilhar recursos ou serviços com outros parceiros de negócios ou clientes.

**Instrução da política:** A implantação de qualquer aplicativo que exija a autenticação do cliente deve usar um provedor de identidade aprovado que seja compatível com o provedor de identidade principal para usuários internos.

**Possíveis opções de design:** Implementar a [Federação com Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-fed) entre os provedores de identidade interna e do cliente ou aproveitar [Azure Active Directory B2B](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

## <a name="identity-reviews"></a>Revisões de identidade

**Risco técnico:** Conforme a empresa muda ao longo do tempo, a adição de novas implantações em nuvem ou outras questões de segurança pode aumentar os riscos de acesso não autorizado a recursos seguros.

**Instrução da política:** Os processos de governança de nuvem devem incluir revisão trimestral com as equipes de gerenciamento de identidade para identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativo de nuvem.

**Possíveis opções de design:** Estabeleça uma reunião de revisão trimestral de segurança que inclui membros da equipe de governança e a equipe de TI responsáveis pelos serviços de identidade de gerenciamento. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política e nas ferramentas de gerenciamento de identidade atuais e na política de atualização para corrigir quaisquer riscos novos.

## <a name="next-steps"></a>Próximas etapas

Use os exemplos mencionados neste artigo como um ponto de partida para o desenvolvimento de políticas para lidar com riscos comerciais específicos que se alinham com seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas à Linha de base de identidade, baixe o [Modelo de Linha de base de identidade](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Usar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a conformidade com a política de linha de base de identidade.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
