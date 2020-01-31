---
title: Como executar uma migração
description: Obtenha uma visão geral dos artigos que explicam as várias atividades que podem estar envolvidas na migração de uma carga de trabalho no Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 62100df7a32ca904454e0df2d7be8c1a860fd611
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802269"
---
# <a name="execute-a-migration"></a>Executar uma migração

Depois de avaliada, uma carga de trabalho pode ser migrada para a nuvem. Esta série de artigos explica as várias atividades que podem estar envolvidas na execução de uma migração.

## <a name="objective"></a>Objetivo

O objetivo de uma migração é migrar uma única carga de trabalho para a nuvem.

## <a name="definition-of-done"></a>Definição de *concluído*

A fase de migração é concluída quando uma carga de trabalho é preparada e está pronta para teste na nuvem, incluindo todos os ativos dependentes necessários para a carga de trabalho funcionar. Durante o processo de otimização, a carga de trabalho é preparada para uso em produção.

Essa definição de *concluído* pode variar conforme seus processos de teste e lançamento. O próximo artigo desta série aborda como [decidir sobre um modelo de promoção](./promotion-models.md) e pode ajudá-lo a entender quando seria melhor promover para a produção uma carga de trabalho migrada.

## <a name="accountability-during-migration"></a>Responsabilidade durante a migração

A equipe de adoção de nuvem é responsável por todo o processo de migração. No entanto, os membros da equipe de estratégia de nuvem têm algumas responsabilidades, conforme discutido na seção a seguir.

## <a name="responsibilities-during-migration"></a>Responsabilidades durante a migração

Além da responsabilidade de alto nível, há ações pelas quais uma pessoa ou grupo precisa ser diretamente responsável. Estas são algumas atividades que exigem atribuições a partes responsáveis:

- **Remediação.** Resolva quaisquer problemas de compatibilidade que impeçam a migração da carga de trabalho para a nuvem.
  - Conforme discutido no artigo de pré-requisito em relação ao [gerenciamento de alterações e à complexidade técnica](../prerequisites/technical-complexity.md), uma decisão deve ser tomada com antecedência para determinar como essa atividade será executada. Em particular, a remedição será concluída pela equipe de adoção da nuvem durante o mesmo sprint que o esforço de migração real? Como alternativa, um modelo de onda ou alocador será usado para concluir a correção em uma iteração separada? Se cada membro da equipe não puder responder a essa pergunta de processo básica, talvez seja aconselhável rever a seção sobre [pré-requisitos](../prerequisites/index.md).
- **Replicação.** Crie uma cópia de cada ativo na nuvem para sincronizar dados, VMs e aplicativos com recursos na nuvem.
  - Dependendo do modelo de promoção, diferentes ferramentas podem ser necessária para concluir essa atividade.
- **Preparo.** Depois que todos os ativos para uma carga de trabalho foram replicados e verificados, a carga de trabalho pode ser preparada para teste empresarial e execução de um plano de alteração empresarial.

## <a name="next-steps"></a>Próximas etapas

Com uma compreensão geral do processo de migração, você está pronto para [decidir-se quanto a um modelo de promoção](./promotion-models.md).

> [!div class="nextstepaction"]
> [Decidir-se quanto a um modelo de promoção](./promotion-models.md)
