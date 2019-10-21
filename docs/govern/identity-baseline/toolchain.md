---
title: Ferramentas de linha de base de identidade no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de linha de base de identidade no Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 348bcc8a98585efb4b4b1dddef1499d4c4958424
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547420"
---
# <a name="identity-baseline-tools-in-azure"></a>Ferramentas de linha de base de identidade no Azure

A [linha de base de identidade](./index.md) é uma das [cinco disciplinas de governança de nuvem](../governance-disciplines.md). Essa disciplina se concentra em maneiras de estabelecer políticas que garantem a consistência e a continuidade de identidades de usuário, independentemente do provedor de nuvem que hospeda o aplicativo ou a carga de trabalho.

As seguintes ferramentas estão incluídas no guia de descoberta em identidade híbrida.

**Active Directory (local):** Active Directory é o provedor de identidade mais frequentemente usado na empresa para armazenar e validar as credenciais do usuário.

**Azure Active Directory:** Um SaaS (software como serviço) equivalente a Active Directory, capaz de federar com um Active Directory local.

**Active Directory (IaaS):** Uma instância do aplicativo Active Directory em execução em uma máquina virtual no Azure.

Identidade é o plano de controle para segurança de ti. Portanto, a autenticação é a proteção de acesso de uma organização para a nuvem. As organizações precisam de um plano de controle de identidade que fortaleça sua segurança e mantenha seus aplicativos de nuvem protegidos contra intrusos.

## <a name="cloud-authentication"></a>Autenticação na nuvem

Escolher o método de autenticação correto é a primeira preocupação para as organizações que desejam mover seus aplicativos para a nuvem.

Quando você escolhe esse método, o Azure AD lida com o processo de entrada dos usuários. Junto com o SSO (logon único) contínuo, os usuários podem entrar em aplicativos de nuvem sem precisar reinserir suas credenciais. Com a autenticação na nuvem, você pode escolher entre duas opções:

**Sincronização de hash de senha do Azure AD:** A maneira mais simples de habilitar a autenticação para objetos de diretório local no Azure AD. Esse método também pode ser usado com qualquer método como um método de autenticação de failover de backup, caso o servidor local fique inativo.

**Autenticação de passagem do Azure AD:** Fornece uma validação de senha persistente para os serviços de autenticação do Azure AD usando um agente de software que é executado em um ou mais servidores locais.

> [!NOTE]
> As empresas com um requisito de segurança para impor imediatamente Estados de conta de usuário local, políticas de senha e horas de entrada devem considerar o método de autenticação de passagem.

**Autenticação federada:**

Quando você escolhe esse método, o Azure AD passa o processo de autenticação para um sistema de autenticação confiável separado, como o Serviços de Federação do Active Directory (AD FS) local (AD FS) ou um provedor de Federação de terceiros confiável, para validar a senha do usuário.

O artigo [escolhendo o método de autenticação certo para Azure Active Directory](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) contém uma árvore de decisão para ajudá-lo a escolher a melhor solução para sua organização.

A tabela a seguir lista as ferramentas nativas que podem ajudar a amadurecer as políticas e os processos que dão suporte a essa disciplina de governança.

<!-- markdownlint-disable MD033 -->

|Reflexão|Sincronização de hash de senha + SSO contínuo|Autenticação de passagem + SSO contínuo|Federação com o AD FS|
|:-----|:-----|:-----|:-----|
|Onde ocorre a autenticação?|Na nuvem|Na nuvem após uma troca de verificação de senha segura com o agente de autenticação local|Local|
|Quais são os requisitos do servidor local além do sistema de provisionamento: Azure AD Connect?|Nenhum|Um servidor para cada agente de autenticação adicional|Dois ou mais servidores AD FS<br><br>Dois ou mais servidores WAP na rede de perímetro/DMZ|
|Quais são os requisitos para Internet e rede local além do sistema de provisionamento?|Nenhum|[Acesso de Internet de saída](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-quick-start) dos servidores que executam agentes de autenticação|[Acesso de Internet de entrada](https://docs.microsoft.com/windows-server/identity/ad-fs/overview/ad-fs-requirements) a servidores WAP no perímetro<br><br>Acesso à rede de entrada para AD FS servidores de servidores WAP no perímetro<br><br>Balanceamento de carga de rede|
|Há um requisito de certificado SSL?|Não|Não|Sim|
|Existe uma solução de monitoramento de integridade?|Não obrigatório|Status do agente fornecido pelo [centro de administração Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-pass-through-authentication)|[Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-adfs)|
|Os usuários obtêm logon único para recursos de nuvem de dispositivos ingressados no domínio na rede da empresa?|Sim com o [SSO contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|Sim com o [SSO contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)|Sim|
|Quais tipos de entrada têm suporte?|UserPrincipalName + senha<br><br>Autenticação integrada do Windows usando [SSO contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID de logon alternativa](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-custom)|UserPrincipalName + senha<br><br>Autenticação integrada do Windows usando [SSO contínuo](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)<br><br>[ID de logon alternativa](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-pta-faq)|UserPrincipalName + senha<br><br>sAMAccountName + senha<br><br>Autenticação integrada do Windows<br><br>[Certificado e autenticação de cartão inteligente](/windows-server/identity/ad-fs/operations/configure-user-certificate-authentication)<br><br>[ID de logon alternativa](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id)|
|Há suporte para o Windows Hello para empresas?|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado com o Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado com o Intune](https://microscott.azurewebsites.net/2017/12/16/setting-up-windows-hello-for-business-with-intune)|[Modelo de confiança de chave](/windows/security/identity-protection/hello-for-business/hello-identity-verification)<br><br>[Modelo de confiança de certificado](/windows/security/identity-protection/hello-for-business/hello-key-trust-adfs)|
|Quais são as opções de autenticação multifator?|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controles personalizados com acesso condicional *](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Controles personalizados com acesso condicional *](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|[Autenticação Multifator do Azure](https://docs.microsoft.com/azure/multi-factor-authentication)<br><br>[Servidor de autenticação multifator do Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-deploy)<br><br>[Autenticação multifator de terceiros](/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs)<br><br>[Controles personalizados com acesso condicional *](https://docs.microsoft.com/azure/active-directory/conditional-access/controls#custom-controls-preview)|
|Quais Estados de conta de usuário têm suporte?|Contas desabilitadas<br>(atraso de até 30 minutos)|Contas desabilitadas<br><br>Conta bloqueada<br><br>Conta expirada<br><br>Senha expirada<br><br>Horas de entrada|Contas desabilitadas<br><br>Conta bloqueada<br><br>Conta expirada<br><br>Senha expirada<br><br>Horas de entrada|
|Quais são as opções de acesso condicional?|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)|[Acesso condicional do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)<br><br>[Regras de declaração de AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator)|
|Está bloqueando protocolos herdados com suporte?|[Sim](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sim](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)|[Sim](/windows-server/identity/ad-fs/operations/access-control-policies-w2k12)|
|Você pode personalizar o logotipo, a imagem e a descrição nas páginas de entrada?|[Sim, com Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sim, com Azure AD Premium](https://docs.microsoft.com/azure/active-directory/customize-branding)|[Sim](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-management#customlogo)|
|Quais cenários avançados têm suporte?|[Bloqueio de senha inteligente](https://docs.microsoft.com/azure/active-directory/active-directory-secure-passwords)<br><br>[Relatórios de credenciais vazadas](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-risk-events)|[Bloqueio de senha inteligente](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-smart-lockout)|Sistema de autenticação de baixa latência multissite<br><br>[AD FS o bloqueio de extranet](/windows-server/identity/ad-fs/operations/configure-ad-fs-extranet-soft-lockout-protection)<br><br>[Integração com sistemas de identidade de terceiros](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility)|

<!-- markdownlint-enable MD033 -->

> [!NOTE]
> No momento, os controles personalizados no acesso condicional do Azure AD não dão suporte ao registro de dispositivo.

## <a name="next-steps"></a>Próximos passos

O [White paper da estrutura de transformação digital de identidade híbrida](https://resources.office.com/ww-landing-M365E-EMS-IDAM-Hybrid-Identity-WhitePaper.html?LCID=EN-US) descreve combinações e soluções para escolher e integrar cada um desses componentes.

A [ferramenta Azure ad Connect](https://aka.ms/aadconnectwiz) ajuda a integrar seus diretórios locais ao Azure AD.
