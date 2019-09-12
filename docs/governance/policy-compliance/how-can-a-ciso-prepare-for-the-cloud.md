---
title: Guia de preparação da nuvem CISO
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como um diretor de segurança da informação pode se preparar para a nuvem?
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/03/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 84663f303e198c06c958aaa7afbe5f504e890d3d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70826999"
---
# <a name="ciso-cloud-readiness-guide"></a>Guia de preparação da nuvem CISO

As diretrizes da Microsoft, como a estrutura de adoção de nuvem, não estão posicionadas para determinar ou orientar as restrições de segurança exclusivas dos milhares de empresas com suporte nesta documentação. Ao migrar para a nuvem, a função do diretor de segurança de informações da empresa ou da CISO (diretor de segurança de informações) não é suplantado pelas tecnologias de nuvem. Muito pelo contrário, o CISO e o escritório de CISO, se tornam mais integrantes e integrados. Este guia pressupõe que o leitor esteja familiarizado com os processos de CISO e está buscando modernizar esses processos para habilitar a transformação em nuvem.

A adoção da nuvem permite que os serviços que não sejam considerados geralmente em ambientes de TI tradicionais. As implantações autoatendimento ou automatizadas geralmente são executadas pelo desenvolvimento de aplicativos ou outras equipes de ti que não estão tradicionalmente alinhadas à implantação de produção. Em algumas organizações, aspectos relacionados aos negócios da mesma forma têm recursos de autoatendimento. Isso pode disparar novos requisitos de segurança que não eram necessários no mundo local. Segurança centralizada é mais desafiador, a segurança muitas vezes se torna uma responsabilidade compartilhada entre os negócios e a cultura de TI. Este artigo pode ajudar um CISO a se preparar para essa abordagem e participar de governança incremental.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-a-ciso-prepare-for-the-cloud"></a>Como um diretor de segurança da informação pode se preparar para a nuvem?

Como a maioria das políticas, as políticas de segurança e governança em uma organização tendem a crescer de forma orgânica. Quando ocorrerem incidentes de segurança, eles formam a política para informar os usuários e reduzir a probabilidade de ocorrências repetidas. Enquanto natural, essa abordagem cria inchaço de política e dependências técnicas. As jornadas de transformação em nuvem criam uma oportunidade única para modernizar e redefinir políticas. Durante a preparação para qualquer jornada de transformação, o CISO pode criar valor imediato e mensurável, servindo como o principal interessado stakeholder em uma [revisão da política](./what-is-a-cloud-policy-review.md).

Em revisão, a função do CISO é criar um equilíbrio seguro entre as restrições de política existente/conformidade e a postura de segurança aprimorada de provedores de nuvem. Medir o progresso pode ter várias formas, geralmente é medido no número de políticas de segurança que podem ser descarregadas com segurança para o provedor de nuvem.

**Transferindo riscos de segurança:** À medida que os serviços são movidos para modelos de hospedagem de infraestrutura como um serviço (IaaS), o negócio assume menos riscos diretos em relação ao provisionamento de hardware. O risco não é removido, em vez disso, ele é transferido para o fornecedor de nuvem. Caso a abordagem de um fornecedor de nuvem para o provisionamento de hardware forneça o mesmo nível de mitigação de risco, em um processo de repetição seguro, o risco de execução de provisionamento de hardware é removido da área de responsabilidade de ti corporativa e transferido para a nuvem operador. Isso reduz o risco de segurança geral corporativo que é responsável pelo gerenciamento, embora o risco em si ainda deva ser acompanhado e revisado periodicamente.

À medida que as soluções se movem ainda mais "pilha para cima" para incorporar os modelos de PaaS (plataforma como serviço) ou SaaS (software como serviço), os riscos adicionais podem ser evitados ou transferidos. Quando o risco com segurança é movido para um provedor de nuvem, o custo de executar, monitorar e impor políticas de segurança ou outras políticas de conformidade podem ser reduzidas com segurança também.

**Mentalidade de crescimento:** A alteração pode ser assustadora tanto para os implementadores técnicos como para os negócios. Quando o CISO leva a uma mudança de mentalidade de crescimento em uma organização, descobrimos que os temores naturais são substituídos por um aumento de interesse em segurança e política de conformidade. Abordar uma [análise de política](./what-is-a-cloud-policy-review.md), uma jornada de transformação ou revisões de implementação simples com uma mentalidade de crescimento, permite que a equipe se movimente rapidamente, mas não com o custo de um perfil de risco razoável e gerenciável.

## <a name="resources-for-the-chief-information-security-officer"></a>Recursos para Chief Information Security Officer

Saber conhecimento sore a nuvem é fundamental para abordar uma [revisão da política](./what-is-a-cloud-policy-review.md) com uma mentalidade de crescimento. Os recursos a seguir podem ajudar o CISO a entender melhor a postura de segurança da plataforma do Azure da Microsoft.

Recursos de plataforma de segurança:

- [Ciclo de vida de desenvolvimento de segurança, auditorias internas](https://www.microsoft.com/sdl)
- [Treinamento de segurança obrigatório, verificações em segundo plano](https://downloads.cloudsecurityalliance.org/star/self-assessment/StandardResponsetoRequestforInformationWindowsAzureSecurityPrivacy.docx)
- [Testes de penetração, Detecção de intrusão, DDoS, Auditorias e registro em log](https://www.microsoft.com/trustcenter/Security/AuditingAndLogging)
- [Centro de dados de última geração](https://www.microsoft.com/cloud-platform/global-datacenters), a segurança física, [rede segura](/azure/security/security-network-overview)
- Saiba mais em [Resposta da segurança do Microsoft Azure na nuvem (PDF)](https://aka.ms/SecurityResponsePaper)

Privacidade e cookies:

- [Gerenciar sempre seus dados](https://www.microsoft.com/trustcenter/Privacy/You-own-your-data)
- [Controlar o local dos dados](https://www.microsoft.com/trustcenter/Privacy/Where-your-data-is-located)
- [Fornecer acesso a dados em seus próprios termos](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Respondendo às autoridades competentes](https://www.microsoft.com/trustcenter/Privacy/Responding-to-govt-agency-requests-for-customer-data)
- [Padrões de privacidade rigorosos](https://www.microsoft.com/TrustCenter/Privacy/We-set-and-adhere-to-stringent-standards)

Conformidade:

- [Central de Confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/default.aspx)
- [Hub de controles comuns](https://www.microsoft.com/trustcenter/Common-Controls-Hub)
- [Lista de verificação de auditoria detalhada dos serviços de nuvem](https://www.microsoft.com/trustcenter/Compliance/Due-Diligence-Checklist)
- [Conformidade por serviço, local e setor](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

Transparência:

- [Como a Microsoft protege os dados do cliente nos serviços do Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Como a Microsoft gerencia o local de dados nos serviços do Azure](https://azuredatacentermap.azurewebsites.net)
- [Quem na Microsoft pode acessar seus dados e em quais termos](https://www.microsoft.com/trustcenter/Privacy/Who-can-access-your-data-and-on-what-terms)
- [Como a Microsoft protege os dados do cliente nos serviços do Azure](https://www.microsoft.com/trustcenter/Transparency/default.aspx)
- [Revisar a certificação para serviços do Azure, hub de transparência](https://www.microsoft.com/trustcenter/Compliance/default.aspx)

## <a name="next-steps"></a>Próximas etapas

A primeira etapa para executar uma ação em qualquer estratégia de governança, é uma [revisão da política](./what-is-a-cloud-policy-review.md). A [política e a conformidade](./index.md) podem ser um guia útil durante a revisão da política.

> [!div class="nextstepaction"]
> [Preparar para uma revisão de política](./what-is-a-cloud-policy-review.md)
