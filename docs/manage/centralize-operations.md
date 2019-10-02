---
title: Centralizar operações de gerenciamento
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Orientação sobre como centralizar operações de gerenciamento
author: JnHs
ms.author: jenhayes
ms.date: 09/27/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: b8e4e37ba9a771937b11f08f1abae45de2f818ab
ms.sourcegitcommit: 1dccf1aed8e98aa0f58c4f86d90c65f5fa5ac84d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71804724"
---
# <a name="centralize-management-operations"></a>Centralizar operações de gerenciamento

Para a maioria das organizações, o uso de um único locatário do Azure Active Directory (Azure AD) para todos os usuários simplifica as operações de gerenciamento e reduz os custos de manutenção, já que todas as tarefas de gerenciamento podem ser por usuários designados, grupos de usuários ou entidades de serviço dentro disso vários. É recomendável usar apenas um locatário do Azure AD para sua organização, se possível.

No entanto, há situações que podem exigir que uma organização mantenha vários locatários do Azure AD. Por exemplo, vários locatários podem ser necessários devido a:

- Subsidiárias totalmente independentes.
- Operando de forma independente em várias regiões geográficas.
- Requisitos legais ou de conformidade.
- Aquisições de outras organizações (às vezes, temporárias até que uma estratégia de consolidação de locatário de longo prazo seja definida).

Nos casos em que uma arquitetura de vários locatários é necessária, o [Azure Lighthouse](https://docs.microsoft.com/azure/lighthouse/overview) fornece uma maneira de centralizar e simplificar as operações de gerenciamento. As assinaturas de vários locatários podem ser integradas para o [Gerenciamento de recursos delegado do Azure](https://docs.microsoft.com/azure/lighthouse/concepts/azure-delegated-resource-management), permitindo que os usuários especificados no locatário de gerenciamento executem [funções de gerenciamento entre locatários](https://docs.microsoft.com/azure/lighthouse/concepts/cross-tenant-management-experience) de maneira centralizada e escalonável.

Por exemplo, digamos que sua organização tenha um locatário único, *locatário a*. Sua organização adquire dois locatários adicionais, *Locatário B* e *Locatário C*, e você tem motivos empresariais que exigem a manutenção deles como locatários separados.

Sua organização deseja usar as mesmas definições de política, práticas de backup e processos de segurança entre todos os locatários. Como você já tem usuários (incluindo grupos de usuários e entidades de serviço) responsáveis por realizar essas tarefas no Locatário A, é possível integrar todas as assinaturas dentro do Locatário B e do Locatário C para que esses mesmos usuários no Locatário A possam executar essas tarefas. O locatário A torna-se o locatário de gerenciamento para o locatário B e o locatário C.

![Usuários no Locatário A gerenciando recursos no Locatário B e no Locatário C](../_images/manage/enterprise-azure-lighthouse.jpg)

Para obter mais informações, consulte [Azure Lighthouse em cenários empresariais](https://docs.microsoft.com/azure/lighthouse/concepts/enterprise).
