---
title: Guia de decisão de identidade
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre identidade como um serviço principal nas migrações do Azure.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: b071fc546f615679bf712e9caa7725e767b73ad9
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753195"
---
# <a name="identity-decision-guide"></a>Guia de decisão de identidade

Em qualquer ambiente, local, híbrido ou somente na nuvem, o departamento de TI precisa controlar quais administradores, usuários e grupos têm acesso aos recursos. Os serviços de IAM (Gerenciamento de Identidades e Acesso) permitem que você gerencie o controle de acesso na nuvem.

![Gráfico com opções de identidade, da menos para a mais complexa, alinhada aos links de salto abaixo](../../_images/decision-guides/decision-guide-identity.png)

Ir para: [Determinar Requisitos de Integração de Identidade](#determine-identity-integration-requirements) | [Linha de Base de Nuvem](#cloud-baseline) | [Sincronização de Diretório](#directory-synchronization) | [Serviços de domínio hospedados na nuvem](#cloud-hosted-domain-services) | [AD FS (Serviços de Federação do Active Directory)](#active-directory-federation-services) | [Saiba mais](#learn-more)

Várias opções estão disponíveis para gerenciar a identidade em um ambiente de nuvem. Essas opções variam de acordo com o custo e com a complexidade. Um fator essencial na estruturação dos serviços de identidade baseados em nuvem é o nível de integração exigido pela infraestrutura de identidade local existente.

No Azure, o Azure AD (Azure Active Directory) fornece um nível básico de gerenciamento de identidades e controle de acesso para recursos de nuvem. No entanto, se a infraestrutura do Active Directory local da sua organização tiver uma estrutura de floresta complexa ou UOs (unidades organizacionais) personalizadas, as cargas de trabalho baseadas em nuvem poderão exigir a sincronização de diretório com o Azure AD para manter um conjunto consistente de identidades, grupos e funções entre os ambientes local e de nuvem. Além disso, o suporte para aplicativos dependentes de mecanismos de autenticação herdados pode exigir a implantação do AD DS (Active Directory Domain Services) na nuvem.

Gerenciamento de identidades baseado em nuvem é um processo iterativo. Você pode começar com uma solução nativa de nuvem, um pequeno conjunto de usuários e as funções correspondentes para uma implantação inicial. À medida que a migração amadurecer, você precisará integrar sua solução de identidade usando a sincronização de diretório ou adicionar serviços de domínio como parte das implantações de nuvem. Reavalie sua estratégia de identidade em cada iteração do processo de migração.

## <a name="determine-identity-integration-requirements"></a>Determinar os requisitos de integração de identidade

| Pergunta | Linha de base de nuvem | Sincronização de diretório | Serviços de domínio hospedados na nuvem | Serviços de Federação do Active Directory (AD FS) |
|------|------|------|------|------|
| Você não tem um serviço de diretório local atualmente? | Sim | Não | Não | Não |
| Suas cargas de trabalho precisam usar um conjunto comum de usuários e grupos entre o ambiente de nuvem e local? | Não | Sim | Não | Não |
| Suas cargas de trabalho dependem de mecanismos de autenticação herdados, como Kerberos ou NTLM? | Não | Não | sim | Sim |
| Você precisa de logon único entre vários provedores de identidade? | Não | Não | Não | Sim |

Como parte do planejamento da migração para o Azure, você precisará determinar a melhor maneira de integrar seus serviços existentes de gerenciamento de identidades e de identidade na nuvem. Abaixo temos cenários comuns de integração.

### <a name="cloud-baseline"></a>Linha de base de nuvem

O Azure AD é o sistema de IAM (Gerenciamento de Identidades e Acesso) nativo para conceder acesso de usuários e grupos aos recursos de gerenciamento na plataforma do Azure. Se a organização não tem uma solução de identidade local relevante e você planeja fazer a migração de cargas de trabalho por questões de compatibilidade com mecanismos de autenticação baseados em nuvem, comece a desenvolver sua infraestrutura de identidade usando o Azure AD como base.

**Pressuposições da linha de base de nuvem:** O uso de uma infraestrutura de identidade puramente nativa de nuvem pressupõe o seguinte:

- Os recursos baseados em nuvem não dependerão de servidores do Active Directory ou serviços de diretório locais; como alternativa, as cargas de trabalho poderão ser modificadas para remover tais dependências.
- As cargas de trabalho de aplicativo ou serviço que estão sendo migradas dão suporte a mecanismos de autenticação compatíveis com o Azure AD ou podem ser modificadas facilmente para dar suporte a eles. O Azure AD se baseia em mecanismos de autenticação prontos para a Internet, como SAML, OAuth e OpenID Connect. As cargas de trabalho existentes que dependem de métodos de autenticação herdados e usam protocolos, como o Kerberos ou o NTLM, talvez precisem ser refatoradas antes da migração para a nuvem usando o padrão de linha de base de nuvem.

> [!TIP]
> Fazer a migração completa dos serviços de identidade para o Azure AD elimina a necessidade de manter sua própria infraestrutura de identidade, o que simplifica bastante o gerenciamento de TI.
>
> No entanto, o Azure AD não é uma substituição completa para uma infraestrutura local tradicional do Active Directory. Os recursos de diretório, como os métodos de autenticação herdados, o gerenciamento do computador ou a política de grupo, podem não estar disponíveis sem a implantação de ferramentas ou serviços adicionais na nuvem.
>
> Para cenários em que você precisa integrar suas identidades ou serviços de domínio locais com suas implantações de nuvem, veja a sincronização de diretórios e os padrões de serviços de domínio hospedado na nuvem discutidos abaixo.

### <a name="directory-synchronization"></a>Sincronização de diretório

Para organizações com uma infraestrutura local existente do Active Directory, a sincronização de diretório costuma ser a melhor solução para preservar o gerenciamento de acesso e de usuário existente, fornecendo as funcionalidades de IAM necessárias para gerenciar recursos da nuvem. Esse processo replica continuamente as informações de diretório entre o Azure AD e os serviços de diretório locais, o que permite credenciais em comum para os usuários e um sistema de identidade, função e permissão consistente para toda a organização.

Observação: as organizações que adotaram o Office 365 talvez já tenham implementado a [sincronização de diretório](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization) entre a infraestrutura do Active Directory local e o Azure Active Directory.

**Pressuposições da sincronização de diretório:** O uso de uma solução de identidade sincronizada pressupõe o seguinte:

- Você precisa manter um conjunto comum de contas de usuário e grupos na nuvem e na infraestrutura de TI local.
- Seus serviços de identidade locais dão suporte à replicação com o Azure AD.

> [!TIP]
> As cargas de trabalho baseadas em nuvem que dependem de mecanismos de autenticação herdados fornecidos por servidores locais do Azure Active Directory e que não têm suporte no Azure AD exigirão também conectividade com os serviços de domínio locais ou servidores virtuais no ambiente de nuvem que fornece esses serviços. O uso de serviços de identidade locais também introduz dependências na conectividade entre as redes locais e de nuvem.

### <a name="cloud-hosted-domain-services"></a>Serviços de domínio hospedados na nuvem

Se você tiver cargas de trabalho que dependam da autenticação baseada em solicitações usando protocolos herdados, como o Kerberos ou o NTLM, e elas não puderem ser refatoradas para aceitar os protocolos de autenticação modernos, como o SAML, o OAuth ou o OpenID Connect, talvez seja necessário migrar alguns dos serviços de domínio para a nuvem como parte da implantação de nuvem.

Esse padrão envolve a implantação de máquinas virtuais que executam o Active Directory para suas redes virtuais baseadas em nuvem para fornecer AD DS (Active Directory Domain Services) para recursos na nuvem. Todos os aplicativos e serviços existentes que estão migrando para sua rede de nuvem devem poder usar os servidores de diretório hospedados na nuvem com algumas modificações.

É provável que os serviços de domínio e diretórios existentes continuem a ser usados em seu ambiente local. Nesse cenário, é recomendável que você também use a sincronização de diretório para fornecer um conjunto comum de usuários e funções em ambientes de nuvem e locais.

**Pressuposições dos serviços de domínio hospedados na nuvem:** A execução de uma migração de diretório pressupõe o seguinte:

- Suas cargas de trabalho dependem de autenticação baseada em declarações usando protocolos como Kerberos ou NTLM.
- As máquinas virtuais da carga de trabalho precisa ter ingressado no domínio para fins de gerenciamento ou aplicação da política de grupo do Active Directory.

> [!TIP]
> Embora uma migração de diretório combinada com serviços de domínio hospedados na nuvem ofereça boa flexibilidade na hora de migrar cargas de trabalho existentes, a hospedagem de máquinas virtuais na rede virtual de nuvem para fornecer esses serviços aumenta a complexidade das tarefas de gerenciamento de TI. À medida que a experiência de migração de nuvem for progredindo, examine os requisitos de manutenção de longo prazo para hospedar os servidores. Avalie se a refatoração das cargas de trabalho existentes para permitir a compatibilidade com provedores de identidade de nuvem como o Azure Active Directory pode reduzir a necessidade de servidores hospedados na nuvem.

### <a name="active-directory-federation-services"></a>Serviços de Federação do Active Directory (AD FS)

A federação de identidades estabelece relações de confiança entre vários sistemas de gerenciamento de identidades para permitir recursos de autorização e autenticação comuns. Assim, é possível dar suporte à funcionalidade de logon único em vários domínios na organização ou nos sistemas de identidade gerenciados por seus clientes ou parceiros de negócios.

O Azure AD dá suporte à federação de domínios do Active Directory locais usando os [Serviços de Federação do Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-fed-whatis) (AD FS). Confira a arquitetura de referência [Estender o AD FS ao Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs) para ver como isso pode ser implementado no Azure.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre os serviços de identidade no Azure, veja:

- [Azure AD](https://azure.microsoft.com/services/active-directory). O Azure AD fornece serviços de identidade baseados em nuvem. Ele permite que você gerencie o acesso a seus recursos do Azure e controle o gerenciamento de identidades, o registro de dispositivos, o provisionamento de usuário, o controle de acesso do aplicativo e a proteção de dados.
- [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-hybrid-identity). A ferramenta Azure AD Connect permite que você se conecte a instâncias do Azure AD com suas soluções de gerenciamento de identidades existente, permitindo a sincronização do diretório existente com a nuvem.
- [RBAC](https://docs.microsoft.com/azure/role-based-access-control/overview) (Controle de Acesso Baseado em Função). O Azure AD fornece RBAC para gerenciar o acesso aos recursos no plano de gerenciamento com eficiência e segurança. Os trabalhos e as responsabilidades são organizados em funções; os usuários são atribuídos a essas funções. O RBAC permite controlar quem tem acesso a um recurso e quais ações um usuário pode executar em tal recurso.
- [Azure AD PIM](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure) (Privileged Identity Management). O PIM reduz o tempo de exposição dos privilégios de acesso a recursos e aumenta a visibilidade em relação a seu uso por meio de relatórios e alertas. Ele limita os usuários para só poderem usar seus privilégios JIT (“Just-In-Time”) ou atribuindo privilégios por uma duração reduzida, após a qual eles são revogados automaticamente.
- [Integrar domínios do Active Directory local ao Azure Active Directory](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad). A presente arquitetura de referência fornece um exemplo de sincronização de diretório entre domínios do Active Directory locais e o Azure AD.
- [Estender o AD DS (Active Directory Domain Services) ao Azure.](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain) A presente arquitetura de referência fornece um exemplo de implantação de servidores do AD DS para estender os serviços de domínio a recursos baseados em nuvem.
- [Estender o AD FS (Serviços de Federação do Active Directory) ao Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adfs). A presente arquitetura de referência configura os Serviços de Federação do Active Directory (AD FS) para realizar a autenticação federada e a autorização com seu diretório do Azure AD.

## <a name="next-steps"></a>Próximas etapas

Identidade é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
