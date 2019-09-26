---
title: Considerações sobre zonas de aterrissagem do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como as zonas de aterrissagem fornecem os blocos de construção básicos de qualquer ambiente de adoção da nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: a3c824b3f36a3252de0c43ff420096c48eda5fc1
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224246"
---
# <a name="landing-zone-considerations"></a>Considerações sobre zonas de aterrissagem

Uma zona de aterrissagem é o bloco de construção básico de qualquer ambiente de adoção da nuvem. O termo *zona de aterrissagem* descreve um ambiente que foi provisionado e preparado para hospedar cargas de trabalho em um ambiente de nuvem, como o Azure. Uma zona de aterrissagem totalmente funcional é a entrega final de qualquer iteração da metodologia Preparar do Cloud Adoption Framework.

![Considerações sobre zonas de aterrissagem](../../_images/ready/landing-zone-considerations.png)

Esta imagem mostra as principais considerações a serem feitas ao implementar qualquer zona de aterrissagem. Essas considerações podem ser divididas em três categorias ou tipos: hospedagem, conceitos básicos do Azure e governança.

## <a name="hosting-considerations"></a>Considerações sobre hospedagem

Todas as zonas de aterrissagem fornecem uma estrutura para as opções de hospedagem. Essa estrutura é criada explicitamente por meio de controles de governança ou organicamente por meio da adoção de serviços na zona de aterrissagem. Os artigos a seguir podem ajudar você a tomar decisões que serão então refletidas no blueprint ou em outros scripts de automação que criam a zona de aterrissagem:

- **[Decisões de computação](./compute-decisions.md)** . Para minimizar a complexidade operacional, alinhe as opções de computação com a finalidade da zona de aterrissagem. Essa decisão pode ser imposta usando cadeias de ferramentas de automação, como iniciativas do Azure Policy e blueprints da zona de aterrissagem.
- **[Decisões de armazenamento](./storage-guidance.md)** . Selecione a solução ideal de Armazenamento do Azure para dar suporte aos seus requisitos de carga de trabalho.
- **[Decisões de rede](./network-decisions.md)** . Escolha os serviços, as ferramentas e as arquiteturas de rede que darão suporte aos requisitos de carga de trabalho, governança e conectividade da sua organização.
- **[Decisões de banco de dados](./data-decisions.md)** . Determine qual tecnologia de banco de dados é mais adequada para seus requisitos de carga de trabalho.

## <a name="azure-fundamentals"></a>Conceitos básicos do Azure

Cada zona de aterrissagem faz parte de uma solução mais abrangente para organizar recursos em um ambiente de nuvem. Os conceitos básicos do Azure são os blocos de construção fundamentais para a organização.

- **[Conceitos fundamentais do Azure](./fundamental-concepts.md)** . Aprenda conceitos e termos fundamentais usados para organizar recursos no Azure e como os conceitos se relacionam entre si.
- **Guia de decisão de organização de recursos**. Depois que você compreender cada um dos conceitos básicos, o guia de decisão de organização de recursos poderá ajudá-lo a tomar decisões que moldarão a zona de aterrissagem.

## <a name="governance-considerations"></a>Considerações de governança

A metodologias Administrar do Cloud Adoption Framework estabelecem um processo para administrar o ambiente como um todo. No entanto, há muitos casos de uso que exigem a tomada de decisões de governança para cada zona de aterrissagem. Em muitos cenários, as linhas de base de governança são impostas para cada zona de aterrissagem, mesmo que essas linhas de base sejam estabelecidas de forma holística. Isso ocorre nas primeiras zonas de aterrissagem implantadas pela organização.

Os artigos a seguir ajudarão a tomar decisões relacionadas à governança da zona de aterrissagem. Você pode considerar cada decisão em suas linhas de base de governança.

- **Requisitos de custos**. Com base na motivação para os esforços de adoção da nuvem e nos compromissos operacionais de uma organização feitos em relação a esse ambiente, várias configurações de gerenciamento de custos podem precisar ser alteradas para essa zona de aterrissagem.
- **Decisões de monitoramento**. Dependendo dos requisitos operacionais dessa zona de aterrissagem, várias ferramentas de monitoramento podem ser implantadas. O artigo sobre decisões de monitoramento pode ajudar você a determinar as ferramentas mais apropriadas a serem implantadas.
- **Como usar o controle de acesso baseado em função**. O [RBAC (controle de acesso baseado em função)](../azure-best-practices/roles.md) do Azure oferece gerenciamento de acesso refinado baseado em grupo para os recursos organizados em torno das funções de usuário.
- **Decisões de política**. As [amostras do Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/samples) fornecem blueprints de conformidade pré-criados, cada um com iniciativas de política predefinidas. As decisões de política ajudam a embasar a seleção do melhor blueprint ou da melhor iniciativa de política de acordo com seus requisitos e suas restrições.
- **[Criar uma consistência de nuvem híbrida](../../infrastructure/misc/hybrid-consistency.md)** . Crie soluções de nuvem híbrida que fornecem os benefícios da inovação na nuvem à sua organização, mantendo muitas das conveniências do gerenciamento local.
