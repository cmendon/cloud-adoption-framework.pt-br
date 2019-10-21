---
title: Guia de preparação para a nuvem do CISO
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como um CISO pode se preparar para a nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 5675d611979c992f41f03d362f0110aaeb3b9b24
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547372"
---
# <a name="ciso-cloud-readiness-guide"></a>Guia de preparação para a nuvem do CISO

As diretrizes da Microsoft, como a estrutura de adoção de nuvem, não estão posicionadas para determinar ou orientar as restrições de segurança exclusivas dos milhares de empresas com suporte nesta documentação. Ao migrar para a nuvem, a função do diretor de segurança de informações da empresa ou da CISO (diretor de segurança de informações) não é suplantado pelas tecnologias de nuvem. O contrário, o CISO e o escritório do CISO, tornam-se mais refinados e integrados. Este guia pressupõe que o leitor esteja familiarizado com os processos de CISO e está buscando modernizar esses processos para habilitar a transformação em nuvem.

A adoção de nuvem habilita serviços que não eram frequentemente considerados em ambientes de ti tradicionais. As implantações autoatendimento ou automatizadas geralmente são executadas pelo desenvolvimento de aplicativos ou outras equipes de ti que não estão tradicionalmente alinhadas à implantação de produção. Em algumas organizações, os constituintes de negócios têm, de certa forma, recursos de autoatendimento. Isso pode disparar novos requisitos de segurança que não eram necessários no mundo local. A segurança centralizada é mais desafiadora, a segurança geralmente se torna uma responsabilidade compartilhada na empresa e na cultura de ti. Este artigo pode ajudar um CISO a se preparar para essa abordagem e se envolver no controle incremental.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-a-ciso-prepare-for-the-cloud"></a>Como um CISO pode se preparar para a nuvem?

Como a maioria das políticas, as políticas de segurança e governança em uma organização tendem a crescer de forma orgânica. Quando ocorrem incidentes de segurança, eles modelam a diretiva para informar os usuários e reduzir a probabilidade de ocorrências repetidas. Embora natural, essa abordagem cria o inchar de política e dependências técnicas. As jornadas de transformação em nuvem criam uma oportunidade única para modernizar e redefinir políticas. Durante a preparação para qualquer jornada de transformação, o CISO pode criar valor imediato e mensurável, servindo como o principal participante de uma [revisão de política](./cloud-policy-review.md).

Nessa revisão, a função do CISO é criar um equilíbrio seguro entre as restrições de política/conformidade existente e a postura de segurança aprimorada dos provedores de nuvem. Medir esse progresso pode assumir muitas formas, muitas vezes é medido no número de políticas de segurança que podem ser descarregadas com segurança para o provedor de nuvem.

**Transferindo riscos de segurança:** Como os serviços são movidos para modelos de Hospedagem de IaaS (infraestrutura como serviço), a empresa assume menos risco direto em relação ao provisionamento de hardware. O risco não é removido, em vez disso, é transferido para o fornecedor da nuvem. Caso a abordagem de um fornecedor de nuvem para o provisionamento de hardware forneça o mesmo nível de mitigação de risco, em um processo de repetição seguro, o risco de execução de provisionamento de hardware é removido da área de responsabilidade de ti corporativa e transferido para a nuvem operador. Isso reduz o risco de segurança geral corporativo que é responsável pelo gerenciamento, embora o risco em si ainda deva ser acompanhado e revisado periodicamente.

À medida que as soluções se movem ainda mais "pilha para cima" para incorporar os modelos de PaaS (plataforma como serviço) ou SaaS (software como serviço), os riscos adicionais podem ser evitados ou transferidos. Quando o risco é movido com segurança para um provedor de nuvem, o custo da execução, do monitoramento e da imposição de políticas de segurança ou outras políticas de conformidade também pode ser reduzido com segurança.

**Mentalidade de crescimento:** A alteração pode ser assustadora tanto para os implementadores técnicos como para os negócios. Quando o CISO lidera uma mudança de mentalidade de crescimento em uma organização, descobrimos que esses temoress naturais são substituídos por um maior interesse em segurança e conformidade com a política. Abordar uma [análise de política](./cloud-policy-review.md), uma jornada de transformação ou revisões de implementação simples com uma mentalidade de crescimento, permite que a equipe se movimente rapidamente, mas não com o custo de um perfil de risco razoável e gerenciável.

## <a name="resources-for-the-chief-information-security-officer"></a>Recursos para o diretor de segurança de informações

O conhecimento sobre a nuvem é fundamental para abordar uma [análise de política](./cloud-policy-review.md) com uma mentalidade de crescimento. Os recursos a seguir podem ajudar a CISO a entender melhor a postura de segurança da plataforma Azure da Microsoft.

Recursos da plataforma de segurança:

- [Ciclo de vida de desenvolvimento de segurança, auditorias internas](https://www.microsoft.com/sdl)
- [Treinamento de segurança obrigatório, verificações em segundo plano](https://downloads.cloudsecurityalliance.org/star/self-assessment/StandardResponsetoRequestforInformationWindowsAzureSecurityPrivacy.docx)
- [Teste de penetração, detecção de intrusão, DDoS, auditorias e registro em log](https://www.microsoft.com/trustcenter/Security/AuditingAndLogging)
- [Datacenter](https://www.microsoft.com/cloud-platform/global-datacenters)de ponta, segurança física, [rede segura](https://docs.microsoft.com/azure/security/security-network-overview)
- [Microsoft Azure resposta de segurança na nuvem (PDF)](https://aka.ms/SecurityResponsePaper)

Privacidade e controles:

- [Gerencie seus dados o tempo todo](https://www.microsoft.com/trustcenter/Privacy/You-own-your-data)
- [Controle no local dos dados](https://www.microsoft.com/trustcenter/Privacy/Where-your-data-is-located)
- [Fornecer acesso a dados em seus termos](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Respondendo à imposição de leis](https://www.microsoft.com/trustcenter/Privacy/Responding-to-govt-agency-requests-for-customer-data)
- [Padrões de privacidade rígidos](https://www.microsoft.com/TrustCenter/Privacy/We-set-and-adhere-to-stringent-standards)

Regulamenta

- [Central de Confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/default.aspx)
- [Hub de controles comuns](https://www.microsoft.com/trustcenter/Common-Controls-Hub)
- [Lista de verificação de auditoria detalhada dos serviços de nuvem](https://www.microsoft.com/trustcenter/Compliance/Due-Diligence-Checklist)
- [Conformidade por serviço, local e setor](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

Transparência

- [Como a Microsoft protege os dados do cliente nos serviços do Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Como a Microsoft gerencia o local de dados nos serviços do Azure](https://azuredatacentermap.azurewebsites.net)
- [Quem na Microsoft pode acessar seus dados em quais termos](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Como a Microsoft protege os dados do cliente nos serviços do Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Examinar a certificação para os serviços do Azure, Hub de transparência](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

## <a name="next-steps"></a>Próximos passos

A primeira etapa para executar uma ação em qualquer estratégia de governança é uma [análise de política](./cloud-policy-review.md). A [política e a conformidade](./index.md) podem ser um guia útil durante a revisão da política.

> [!div class="nextstepaction"]
> [Preparar para uma revisão de política](./cloud-policy-review.md)
