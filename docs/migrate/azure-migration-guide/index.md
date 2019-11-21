---
title: Guia de introdução à migração do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como migrar efetivamente os serviços da sua organização para o Azure com orientação passo a passo.
author: matticusau
ms.author: mlavery
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 9f27c7fca9a9a5bd2f5c38f78b8db2092b24d014
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251498"
---
::: zone target="docs"

# <a name="azure-migration-guide-before-you-start"></a>Guia de migração do Azure: Antes de começar

::: zone-end

::: zone target="chromeless"

# <a name="before-you-start"></a>Antes de começar

::: zone-end

Antes fazer a migração dos recursos do Azure, é necessário escolher o método de migração e os recursos que você usará para controlar e proteger seu ambiente. Este guia o orienta por esse processo de decisão.

::: zone target="docs"

> [!TIP]
> Para uma experiência interativa, exiba esse guia no portal do Azure. Vá para o [Centro de Início Rápido do Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) no portal do Azure, selecione **Migrar o ambiente para o Azure** e depois siga as instruções passo a passo.

::: zone-end

# <a name="overviewtaboverview"></a>[Visão geral](#tab/Overview)

Este guia o conduz pelos fundamentos de migrar aplicativos e recursos do ambiente local para o Azure. Ele é projetado para escopos de migração com complexidade mínima. Para determinar a adequação desse guia para migração, veja a guia **Quando usar este guia**.

Quando você faz a migração para o Azure, é possível migrar seus aplicativos no estado em que se encontram usando soluções de máquina virtual baseadas em IaaS (conhecidas como migração do tipo _lift-and-shift_ ou _nova hospedagem_) ou ter a flexibilidade de usar serviços gerenciados e outros recursos nativos de nuvem para modernizar seus aplicativos. Veja a guia **Opções de migração** para obter mais informações sobre essas opções. À medida que você desenvolve sua estratégia de migração, pode considerar:

- Meus aplicativos migrados vão funcionar na nuvem?
- Qual é a melhor estratégia (em relação a tecnologia, ferramentas e migrações) para meu aplicativo? Veja o [Guia de decisão das ferramentas de migração](../../decision-guides/migrate-decision-guide/index.md) da Microsoft Cloud Adoption Framework para obter mais informações.
- Como fazer para minimizar o tempo de inatividade durante a migração?
- Como controlar os custos?
- Como fazer para acompanhar custos de recurso e faturá-los com precisão?
- Como fazer para garantir que eles permanecem em conformidade e cumpram os regulamentos?
- Como atender aos requisitos legais para a soberania de dados em determinados países?

Este guia ajuda a responder a essas perguntas. Ele sugere as tarefas e os recursos a serem considerados quando você se prepara para implantar recursos no Azure, incluindo:

> [!div class="checklist"]
>
> - **Configurar pré-requisitos.** Planeje e prepare-se para a migração.
> - **Avaliar sua adequação técnica.** Valide a prontidão técnica e a adequação para a migração.
> - **Gerenciar os custos e a cobrança.** Examine os custos de seus recursos.
> - **Migrar seus serviços.** Execute a migração real.
> - **Organizar seus recursos.** Bloqueie recursos críticos para seu sistema e marque recursos para acompanhá-los.
> - **Otimizar e transformar.** Use a oportunidade de pós-migração para examinar seus recursos.
> - **Proteger e gerenciar.** Verifique se o seu ambiente está seguro e monitorado corretamente.
> - **Obter assistência.** Obtenha ajuda e suporte durante a migração ou atividades pós-migração.

::: zone target="docs"

Para saber mais sobre como organizar e estruturar suas assinaturas, gerenciar seus recursos implantados e estar em conformidade com os requisitos de política corporativa, veja [Governança no Azure](https://docs.microsoft.com/azure/security/governance-in-azure).

::: zone-end

# <a name="when-to-use-this-guidetabwhentousethisguide"></a>[Quando usar este guia](#tab/WhenToUseThisGuide)

Embora as ferramentas abordadas neste guia deem suporte a uma ampla variedade de cenários de migração, este guia se concentrará nos esforços de escopo limitado com _complexidade mínima_. Para determinar se este guia de migração é adequado para seu projeto, considere se as seguintes condições se aplicam a você:

- Você está migrando um ambiente homogêneo.
- Apenas algumas unidades de negócios precisam se alinhar para concluir a migração.
- Você não está planejando automatizar toda a migração.
- Você está migrando um pequeno número de servidores.
- O mapeamento de dependência dos componentes a serem migrados é simples de definir.
- Seu setor tem os requisitos normativos mínimos relevantes para esta migração.

Se qualquer uma destas condições _não_ for aplicável à sua situação, você deverá considerar o [guia de escopo expandido](../expanded-scope/index.md). Também recomendamos que você solicite assistência de uma de nossas equipes ou parceiros da Microsoft para executar migrações que exigem o guia de escopo expandido. Os clientes que interagem com a Microsoft ou parceiros certificados obtêm mais êxito nesses cenários. Mais informações sobre como solicitar assistência estão disponíveis neste guia.

<!-- markdownlint-enable MD033 -->

::: zone target="docs"

Para obter mais informações, consulte:

- [Guia de escopo expandido](../expanded-scope/index.md)

::: zone-end

# <a name="migration-optionstabmigrationoptions"></a>[Opções de migração](#tab/MigrationOptions)

Você pode executar uma migração na nuvem de várias maneiras. Algumas são mais adequadas para cenários diferentes do que outras. Conforme você determina como fazer a migração de seu ambiente, considere as seguintes opções ao escolher uma estratégia de migração:

- **Hospedar novamente:** também conhecido como "lift-and-shift", um esforço de nova hospedagem move o estado atual para o Azure, com alterações mínimas à arquitetura geral.
- **Refatorar:** as opções de PaaS (plataforma como serviço) podem reduzir os custos operacionais associados a muitos aplicativos. Pode ser prudente refatorar ligeiramente um aplicativo para ajustá-lo a um modelo de PaaS. Isso também se refere ao processo de desenvolvimento de aplicativo de refatorar código para permitir que um aplicativo forneça novas oportunidades empresariais.
- **Recriação da arquitetura:** Alguns aplicativos mais velhos não são compatíveis com provedores de nuvem devido a decisões arquitetônicas tomadas durante a compilação do aplicativo. Nesses casos, o aplicativo pode precisar de uma nova arquitetura como parte da migração.
- **Recompilar:** em alguns cenários, as alterações necessárias para fazer a migração de um aplicativo podem ser muito grandes para justificar o investimento e a solução deve ser recompilada.
- **Substituir:** normalmente, as soluções são implementadas usando as melhores tecnologias e técnicas disponíveis no momento. Em alguns casos, aplicativos modernos de SaaS (software como serviço) podem atender a todas as funcionalidades fornecidas pelo aplicativo hospedado. Nesses cenários, uma carga de trabalho poderia ser agendada para substituição futura, deixando de ser considerada como parte da migração.

::: zone target="chromeless"

Esses métodos não são mutuamente excludentes&mdash;por exemplo, embora sua migração inicial possa usar um modelo de **nova hospedagem**, você pode optar por implementar **refatoração** ou **recriação de arquitetura** como parte da fase de otimização após a migração. Isso é revisto na seção **Otimizar e transformar** deste guia.

::: zone-end

::: zone target="docs"

Esses métodos não são mutuamente excludentes&mdash;por exemplo, embora sua migração inicial possa usar um modelo de **nova hospedagem**, você pode optar por implementar **refatoração** ou **recriação de arquitetura** como parte da fase de otimização após a migração. Isso é revisto na seção [Otimizar e transformar](./optimize-and-transform.md) deste guia.

::: zone-end

![Infográfico das opções de migração](../../_images/migrate/migration-options.png)
