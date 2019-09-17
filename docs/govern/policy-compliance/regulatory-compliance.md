---
title: Introdução à conformidade regulatória
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à conformidade regulatória
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b0bc28f46671c4ccf62bba9f3fa68f14e2b79aee
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030012"
---
# <a name="introduction-to-regulatory-compliance"></a>Introdução à conformidade regulatória

Este é um artigo introdutório sobre conformidade regulatória, portanto, não destina-se a implementar uma estratégia de conformidade. É apenas para conhecimento geral. Informações mais detalhadas sobre as [ofertas de conformidade do Azure](https://aka.ms/allcompliance) estão disponíveis na [central de confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/default.aspx). Além disso, toda a documentação para download está disponível para determinados clientes do Azure no [portal de confiança do serviço da Microsoft](https://servicetrust.microsoft.com).

A conformidade regulatória refere-se à disciplina e ao processo de garantir que uma empresa siga as leis impostas controlando corpos em sua geografia ou regras exigidas por padrões do setor voluntariamente adotados. Para conformidade regulatória de ti, as pessoas e os processos monitoram sistemas corporativos em um esforço para detectar e evitar violações de políticas e procedimentos estabelecidos por essas leis, regulamentos e padrões de controle. Isso, por sua vez, se aplica a uma ampla gama de processos de monitoramento e imposição. Dependendo do setor e da geografia, esses processos podem se tornar longos e complexos.

A conformidade é desafiadora para organizações multinacionais, especialmente em setores altamente regulamentados, como serviços de saúde e finanças. Padrões e regulamentos abound e, em determinados casos, podem ser alterados com frequência, o que dificulta para as empresas acompanharem as leis internacionais de manipulação de dados eletrônicos.

Assim como nos controles de segurança, as organizações devem compreender a divisão de responsabilidades relacionadas à conformidade regulatória na nuvem. Os provedores de nuvem estão empenhados para garantir que as plataformas e serviços estejam em conformidade. Mas as organizações também precisam confirmar que seus aplicativos, a infraestrutura da qual esses aplicativos dependem, e os serviços fornecidos por terceiros também são certificados como compatíveis.

A seguir, estão as descrições de regulamentos de conformidade em vários setores e geografias:

## <a name="hipaa"></a>HIPAA

Um aplicativo para serviços de saúde que processa PHI (informações de saúde protegidas) está sujeito tanto à Regra de Privacidade e como à Regra de Segurança englobadas na Lei HIPAA (Lei de Portabilidade e Responsabilidade de Seguros de Saúde). No mínimo, a HIPAA pode exigir que um negócio de saúde receba garantias escritas do provedor de nuvem que protegerá todos os PHI recebidos ou criados.

## <a name="pci"></a>PCI

PCI DSS (Padrão de Segurança de Dados da Indústria de Pagamento com Cartão) é um padrão de segurança de informações patenteado para organizações que lidam com cartões de crédito de marca dos principais sistemas de cartões, incluindo Visa, MasterCard, American Express, Discover e JCB. O padrão PCI é exigido pelas marcas de cartões e administrado pelo Conselho de Normas de Segurança da Indústria de Meios de Pagamento. O padrão foi criado para aumentar os controles sobre os dados do titular do cartão para reduzir fraudes com cartões de crédito. A validação da conformidade é realizada anualmente, seja por um QSA (Assessor de Segurança Qualificado) externo ou por um ISA (Assessor de Segurança Interno) específico da empresa que cria um ROC (Relatório de Conformidade) para organizações que lidam com grandes volumes de transações ou por um SAQ (Questionário de Autoavaliação) para empresas.

## <a name="personal-data"></a>Dados pessoais

Dados pessoais são informações que podem ser usadas para identificar um consumidor, funcionário, parceiro ou qualquer outra entidade de vida ou legal. Muitas leis emergentes, especialmente aquelas que lidam com dados pessoais e de privacidade, exigem que as empresas estejam em conformidade e relatem a conformidade e quaisquer violações que possam ocorrer.

## <a name="gdpr"></a>RGPD

Um dos desenvolvimentos mais importantes nesta área é a recente promulgação pela Comissão Europeia do GDPR (Regulamento Geral sobre a Proteção de Dados), concebido para reforçar a proteção de dados para as pessoas dentro da União Europeia. O GDPR exige que os dados sobre indivíduos (como "um nome, um endereço residencial, uma foto, um endereço de email, detalhes do banco, postagens em sites de rede social, informações médicas ou o endereço IP de um computador") sejam mantidos em servidores na UE e não sejam transferidos de ti. Ele também exige que as empresas notifiquem indivíduos de quaisquer violações de dados e exija que as empresas tenham um DPO (responsável pela proteção de dados). Outros países têm ou estão desenvolvendo tipos similares de regulamentos.

## <a name="compliant-foundation-in-azure"></a>Base compatível no Azure

Para ajudar os clientes a atender suas próprias obrigações de conformidade entre indústrias regulamentadas e mercados em todo o mundo, o Azure&mdash;mantém o maior portfólio de conformidade do setor em amplitude (número total de ofertas), bem como profundidade (número de serviços voltados para o cliente no escopo da avaliação). As ofertas de conformidade do Azure são agrupadas em quatro segmentos: aplicável globalmente, US Government, específico do setor e específico do região/país.

As ofertas de conformidade do Azure são baseadas em vários tipos de garantias, incluindo certificações formais, atestados, validações, autorizações e avaliações produzidas por empresas de auditoria de terceiros independentes, bem como alterações contratuais, autoavaliações e documentos de diretrizes para o cliente produzidos pela Microsoft. Cada descrição de oferta neste documento fornece uma declaração de escopo atualizada indicando quais serviços voltados ao cliente do Azure estão no escopo da avaliação, assim como links para recursos baixáveis para auxiliar os clientes com suas próprias obrigações de conformidade.

Informações mais detalhadas sobre as ofertas de conformidade do Azure estão disponíveis na [Central de Confiabilidade da Microsoft](https://www.microsoft.com/trustcenter/compliance/complianceofferings). Além disso, toda a documentação para download está disponível para determinados clientes do Azure no [portal de confiança do serviço](https://servicetrust.microsoft.com) nas seguintes seções:

- **Relatórios de auditoria:** Inclui seções para relatórios FedRAMP, avaliação de GRC, ISO, PCI DSS e SOC.
- **Recursos de proteção de dados:** Inclui guias de conformidade, perguntas frequentes e White papers e seções de avaliação de segurança e teste de caneta.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre a preparação de segurança na nuvem.

> [!div class="nextstepaction"]
> [Preparação para segurança na nuvem](./cloud-security-readiness.md)
