---
title: Centralizar operações de gerenciamento
description: Aprenda a centralizar as operações de gerenciamento usando um único locatário de Azure Active Directory para todos os usuários. O gerenciamento centralizado simplifica as operações de gerenciamento e reduz os custos de manutenção.
author: JnHs
ms.author: jenhayes
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 312be5ae3b716ad8d6aa609749bcbb615f6ef1c5
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140415"
---
<!-- cSpell:ignore jenhayes -->

# <a name="centralize-management-operations"></a>Centralizar operações de gerenciamento

Para a maioria das organizações, o uso de um único locatário do Azure Active Directory (Azure AD) para todos os usuários simplifica as operações de gerenciamento e reduz os custos de manutenção. Isso ocorre porque todas as tarefas de gerenciamento podem ser por usuários designados, grupos de usuários ou entidades de serviço dentro desse locatário.

É recomendável que você use apenas um locatário do Azure AD para sua organização, se possível. No entanto, algumas situações podem exigir que uma organização mantenha vários locatários do Azure AD pelos seguintes motivos:

- São subsidiárias totalmente independentes.
- Eles estão operando de forma independente em várias regiões geográficas.
- Determinados requisitos legais ou de conformidade se aplicam.
- Há aquisições de outras organizações (às vezes, temporárias até que uma estratégia de consolidação de locatário de longo prazo seja definida).

Quando uma arquitetura de vários locatários é necessária, o [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) fornece uma maneira de centralizar e simplificar as operações de gerenciamento. As assinaturas de vários locatários podem ser integradas para o [Gerenciamento de recursos delegado do Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management). Essa opção permite que os usuários especificados no locatário de gerenciamento executem [funções de gerenciamento entre locatários](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) de maneira centralizada e escalonável.

Por exemplo, digamos que sua organização tenha um locatário único, *locatário a*. Em seguida, a organização adquire dois locatários adicionais, o *locatário B* e o *locatário C*, e você tem motivos comerciais que exigem que você os mantenha como locatários separados.

Sua organização deseja usar as mesmas definições de política, práticas de backup e processos de segurança entre todos os locatários. Como você já tem usuários (incluindo grupos de usuários e entidades de serviço) responsáveis por executar essas tarefas no locatário A, é possível integrar todas as assinaturas no locatário B e no locatário C para que os mesmos usuários no locatário A possam executá-las tarefa. O locatário A torna-se o locatário de gerenciamento para o locatário B e o locatário C.

![Usuários no Locatário A gerenciando recursos no Locatário B e no Locatário C](../_images/manage/enterprise-azure-lighthouse.jpg)

Para obter mais informações, consulte [Azure Lighthouse em cenários empresariais](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
