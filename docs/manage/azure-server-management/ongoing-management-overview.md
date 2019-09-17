---
title: Gerenciamento e segurança contínuos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Gerenciamento e segurança contínuos
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7b77181dd8ef6efe655b56489e5d4e6b210382b6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029330"
---
# <a name="phase-3-ongoing-management-and-security"></a>Fase 3: Gerenciamento e segurança contínuos

Depois de ter integrado os serviços de gerenciamento do Azure, você precisará se concentrar nas configurações de operações e de segurança que oferecerão suporte a suas operações em andamento. Começaremos a proteger seu ambiente examinando a central de segurança do Azure. Em seguida, configuraremos políticas para manter seus servidores em conformidade e automatizar tarefas comuns. Esta seção contém os seguintes tópicos:

- **[Abordar as recomendações de segurança.](#address-security-recommendations)** A central de segurança do Azure fornece sugestões para melhorar a segurança do seu ambiente. Ao implementar essas recomendações, você pode ver o impacto refletido em uma pontuação de segurança.
- **[Habilite a política de configuração de convidado.](./guest-configuration-policy.md)** Habilite o recurso de configuração de convidado Azure Policy para auditar as configurações em uma máquina virtual. Por exemplo, você pode verificar se algum certificado está prestes a expirar.
- **[Acompanhe e Alerte as alterações críticas.](./enable-tracking-alerting.md)** Quando estiver solucionando problemas, a primeira pergunta a ser considerada é "o que mudou?" Neste artigo, você aprenderá a controlar as alterações e criar alertas para monitorar proativamente os componentes críticos.
- **[Criar agendas de atualização.](./update-schedules.md)** Agende a instalação das atualizações para garantir que todos os servidores tenham os mais recentes.
- **[Exemplos comuns de Azure Policy.](./common-policies.md)** Fornece exemplos de políticas de gerenciamento comuns.

## <a name="address-security-recommendations"></a>Solucionar recomendações de segurança

A central de segurança do Azure é o local central para gerenciar a segurança de seu ambiente. Você verá uma avaliação geral e recomendações direcionadas.

Recomendamos que você revise e implemente as recomendações fornecidas por esse serviço. Para obter informações sobre os benefícios adicionais da central de segurança do Azure, consulte [seguir as recomendações da central de segurança do Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-security-management#best-practice-follow-azure-security-center-recommendations).

## <a name="next-steps"></a>Próximas etapas

Saiba como [habilitar o recurso de configuração de convidado Azure Policy](./guest-configuration-policy.md) .

> [!div class="nextstepaction"]
> [Política de configuração de convidado](./guest-configuration-policy.md)
