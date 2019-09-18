---
title: Ferramentas de Linha de Base de Segurança no Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação das ferramentas que podem facilitar a melhoria da linha de base de segurança no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5d64befe7973201bc9727e0bef2b4f7a2e99052b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030661"
---
# <a name="security-baseline-tools-in-azure"></a>Ferramentas de Linha de Base de Segurança no Azure

A [Linha de Base de Segurança](./index.md) é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md). Essa disciplina se concentra em maneiras de estabelecer políticas que protegem a rede, os ativos e, mais importante, os dados que residirão em uma solução de provedor de nuvem. Dentro das cinco disciplinas de governança de nuvem, a disciplina de linha de base de segurança envolve a classificação do espaço digital e dos dados. Ele também envolve documentação de riscos, tolerância de negócios e estratégias de mitigação associados à segurança de dados, ativos e redes. Do ponto de vista técnico, essa disciplina também inclui o envolvimento em decisões relacionadas à [criptografia](../../decision-guides/encryption/index.md), [aos requisitos de rede, às](../../decision-guides/software-defined-network/index.md)estratégias de [identidade híbrida](../../decision-guides/identity/index.md)e às ferramentas para [automatizar a imposição](../../decision-guides/policy-enforcement/index.md) de políticas de segurança entre [grupos de recursos](../../decision-guides/resource-consistency/index.md).

A lista a seguir das ferramentas do Azure pode ajudar a amadurecer as políticas e os processos que dão suporte à linha de base de segurança.

| Ferramenta | [Portal do Azure](https://azure.microsoft.com/features/azure-portal) / [Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Cofre da Chave do Azure](https://docs.microsoft.com/azure/key-vault)  | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) | [Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) | [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) |
|------------------------------------------------------------|---------------------------------|-----------------|----------|--------------|-----------------------|---------------|
| Aplicar controles de acesso a recursos e criação de recursos   | Sim                             | Não              | Sim      | Não           | Não                    | Não            |
| Redes virtuais seguras                                    | Sim                             | Não              | Não       | Sim          | Não                    | Não            |
| Criptografar unidades virtuais                                     | Não                              | Sim             | Não       | Não           | Não                    | Não            |
| Criptografar armazenamento e bancos de dados de PaaS                         | Não                              | Sim             | Não       | Não           | Não                    | Não            |
| Gerenciar serviços de identidade híbrida                            | Não                              | Não              | Sim      | Não           | Não                    | Não            |
| Restringir tipos de recursos permitidos                         | Não                              | Não              | Não       | Sim          | Não                    | Não            |
| Impor restrições geo-regionais                          | Não                              | Não              | Não       | Sim          | Não                    | Não            |
| Monitorar a integridade da segurança de redes e recursos          | Não                              | Não              | Não       | Não           | Sim                   | Sim           |
| Detectar atividade mal-intencionada                                  | Não                              | Não              | Não       | Não           | Sim                   | Sim           |
| Detectar vulnerabilidades antecipadamente                        | Não                              | Não              | Não       | Não           | Sim                   | Não            |
| Configurar backup e recuperação de desastre                     | Sim                             | Não              | Não       | Não           | Não                    | Não            |

Para obter uma lista completa de ferramentas e serviços de segurança do Azure, consulte [Serviços de segurança e tecnologias disponíveis no Azure](https://docs.microsoft.com/azure/security/azure-security-services-technologies).

Também é comum que os clientes usem ferramentas de terceiros para facilitar as atividades de linha de base de segurança. Para obter mais informações, consulte o artigo [Integrar soluções de segurança na Central de Segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-partner-integration).

Além das ferramentas de segurança, a [Central de Confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/guidance/risk-assessment) contém diretrizes abrangentes, relatórios e documentação relacionada que podem ajudá-lo a realizar avaliações de risco como parte do processo de planejamento de migração.