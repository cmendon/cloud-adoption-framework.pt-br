---
title: Identificar ferramentas da linha de base no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Identificar ferramentas da linha de base no Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 72060f16add37d62a4747c5fe9d5aef49fe04c58
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222110"
---
# <a name="identity-baseline-tools-in-azure"></a>Identificar ferramentas da linha de base no Azure

[Identificar a linha de base](./index.md) é uma das [Cinco disciplinas de governança de nuvem](../governance-disciplines.md). Esta disciplina se concentra em maneiras de estabelecer políticas que garantem a consistência e continuidade das identidades do usuário independentemente do provedor de nuvem que hospeda o aplicativo ou a carga de trabalho.

As ferramentas a seguir estão incluídas na guia de descoberta da identidade híbrida.

**Active Directory (local):** O Active Directory é o provedor de identidade usado com mais frequência na empresa para armazenar e validar as credenciais do usuário.

**Azure Active Directory:** Um software como serviço (SaaS) equivalente ao Active Directory, capaz de estabelecer uma federação com um diretório do Active Directory local.

**Active Directory (IaaS):** Uma instância de aplicativo do Active Directory em execução em uma máquina virtual no Azure.

A identidade é o novo plano de controle da segurança de TI. Portanto, a autenticação é a proteção de acesso de uma organização para a nuvem. As organizações precisam de um plano de controle de identidade que reforce a segurança e mantenha os aplicativos de nuvem protegidos contra invasores.

## <a name="cloud-authentication"></a>Autenticação na nuvem

Escolher o método de autenticação correto é a principal preocupação para organizações que desejam migrar seus aplicativos para a nuvem.

Quando você escolhe esse método, o Azure Active Directory cuida do processo de entrada dos usuários. Juntamente com o SSO (logon único) contínuo, os usuários podem entrar em aplicativos de nuvem sem precisar inserir suas credenciais novamente. Com a autenticação na nuvem, é possível escolher entre duas opções:

**Sincronização de hash de senha do Azure AD:** A maneira mais simples de habilitar a autenticação para objetos de diretório locais no Azure AD. Isso também pode ser usado com qualquer método de autenticação de failover de backup no caso de o servidor local ficar inativo.

**Autenticação de passagem do Azure AD:** Fornece uma validação de senha persistente para serviços de autenticação do Azure AD usando um agente de software que é executado em um ou mais servidores locais.

> [!NOTE]
> Empresas com requisito de segurança que desejam impor imediatamente os estados de conta do usuário no local, políticas de senha e horários de entrada, devem considerar o método de autenticação de passagem.

**Autenticação federada**:

Quando você escolhe esse método, o Azure AD transfere o processo de autenticação para um sistema de autenticação confiável separado, como os Serviços de Federação do Active Directory (AD FS) locais ou um provedor de federação de terceiros confiável para validar a senha do usuário.

O artigo [escolhendo o método de autenticação certo para o Azure Active Directory](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) contém uma árvore de decisão para ajudá-lo a escolher a melhor solução para sua organização.

A tabela a seguir lista as ferramentas nativas que ajudam a amadurecer as políticas e os processos que dão suporte a disciplina de governança.

<!-- markdownlint-disable MD033 -->

|Consideração|Sincronização de hash de senha + SSO Contínuo|Autenticação de Passagem + SSO Contínuo|Federação com o AD FS|
|:-----|:-----|:-----|:-----|
|Onde a autenticação ocorre?|Na nuvem|Na nuvem, após uma troca de verificação de senha segura com o agente de autenticação local|Configuração local|
|Quais são os requisitos de servidor local além do sistema de provisionamento: Azure AD Connect?|Nenhuma|Um servidor para cada agente de autenticação adicional|Dois ou mais servidores do AD FS<br><br>Dois ou mais servidores WAP na rede de perímetro/DMZ|
|Quais são os requisitos para Internet e rede local além do sistema de provisionamento?|Nenhuma|[Acesso de Internet de saída](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-quick-start) dos servidores que executam agentes de autenticação|[Acesso de Internet de entrada](https://docs.microsoft.com/windows-server/identity/ad-fs/overview/ad-fs-requirements) a servidores WAP no perímetro<br><br>Acesso à rede de entrada aos servidores AD FS por meio dos servidores WAP no perímetro<br><br>Balanceamento de carga de rede|
|Há algum requisito de certificado SSL?|Não|Não|sim|
|Há alguma solução de monitoramento de integridade?|Não requerido|Status do agente fornecido pelo [Centro de administração do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-pass-through-authentication)|[Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-adfs)|
|Usuários podem obter o logon único para recursos de nuvem de dispositivos que ingressaram no domínio dentro da rede da empresa?|Sim, com [SSO Contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|Sim, com [SSO Contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|sim|
|Há suporte para quais tipos de entrada?|Nome Principal do Usuário + senha<br><br>Autenticação Integrada do Windows usando [SSO Contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID de logon alternativa](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-custom)|Nome Principal do Usuário + senha<br><br>Autenticação Integrada do Windows usando [SSO Contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID de logon alternativa](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-faq)|Nome Principal do Usuário + senha<br><br>sAMAccountName + senha<br><br>Autenticação Integrada do Windows<br><br>[Autenticação de certificado e cartão inteligente](/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication)<br><br>[ID de logon alternativa](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id)|
|Há suporte para o Windows Hello for Business?|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado com o Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado com o Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado](/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs)|
|Quais são as opções da autenticação multifator?|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controles personalizados com acesso condicional*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controles personalizados com acesso condicional*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Servidor de autenticação multifator do Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy)<br><br>[Autenticação multifator de terceiros](/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs)<br><br>[Controles personalizados com acesso condicional*](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|
|Há suporte para quais estados de conta de usuário?|Contas desabilitadas<br>(até 30 minutos de atraso)|Contas desabilitadas<br><br>Conta bloqueada<br><br>A conta expirou<br><br>Senha expirada<br><br>Horários de entrada|Contas desabilitadas<br><br>Conta bloqueada<br><br>A conta expirou<br><br>Senha expirada<br><br>Horários de entrada|
|Quais são as opções de acesso condicional?|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)<br><br>[Regras de declaração do AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator)|
|Há suporte para protocolos herdados de bloqueio?|[Sim](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sim](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sim](/windows-server/identity/ad-fs/operations/access-control-policies-w2k12)|
|Você pode personalizar o logotipo, a imagem e a descrição nas páginas de entrada?|[Sim, com o Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sim, com o Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sim](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo)|
|Há suporte para quais cenários avançados?|[Bloqueio de senha inteligente](https://docs.microsoft.com/azure/active-directory/active-directory-secure-passwords)<br><br>[Relatórios de credenciais vazadas](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events)|[Bloqueio de senha inteligente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout)|Sistema de autenticação de baixa latência para vários sites<br><br>[Bloqueio de extranet de AD FS](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)<br><br>[Integração com sistemas de identidade de terceiros](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)|

<!-- markdownlint-enable MD033 -->

> [!NOTE]
> Atualmente, os controles personalizados no acesso condicional do Azure AD não dão suporte para registro de dispositivos.

## <a name="next-steps"></a>Próximas etapas

O [White paper da estrutura de transformação digital de identidade híbrida](https://resources.office.com/ww-landing-M365E-EMS-IDAM-Hybrid-Identity-WhitePaper.html?LCID=EN-US) descreve combinações e soluções para escolher e integrar cada um desses componentes.

A [ferramenta Azure Active Directory Connect](https://aka.ms/aadconnectwiz) ajuda você a integrar seus diretórios locais ao Azure Active Directory.
