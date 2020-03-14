---
title: Atividades de preparo durante uma migração
description: Use a estrutura de adoção de nuvem para o Azure para entender as atividades de preparo e os resultados associados necessários durante uma migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 491080353d6cf67009720359257d9f1b8bbfdd6d
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311737"
---
# <a name="understand-staging-activities-during-a-migration"></a>Entender as atividades de preparo durante uma migração

Conforme descrito no artigo sobre modelos de promoção, o *preparo* é o ponto em que os ativos foram migrados para a nuvem. No entanto, eles ainda não estão prontos para serem promovidos para produção. Geralmente, essa é a última etapa no processo de migração. Após o preparo, a carga de trabalho é gerenciada por uma equipe de operações de TI ou de nuvem a fim de prepará-la para uso em produção.

## <a name="deliverables"></a>Resultados finais

Os ativos preparados podem não estar prontos para uso na produção. Há várias verificações de preparação para produção que precisam ser finalizadas antes que esse estágio seja considerado concluído. Confira a seguir uma lista de resultados geralmente associados à conclusão do preparo de ativos.

- **Testes automatizados.** Quaisquer testes automatizados disponíveis para validar o desempenho da carga de trabalho precisam ser executados antes da conclusão do processo de preparo. Depois que o ativo sai do preparo, a sincronização com o sistema de origem é finalizada. Assim, é mais difícil reimplantar os ativos replicados após os recursos serem preparados para otimização.
- **Documentação de migração.** A maioria das ferramentas de migração pode produzir um relatório automatizado dos ativos em migração. Antes da conclusão da atividade de preparo, todos os ativos migrados precisam ser documentados para fins de clareza.
- **Documentação de configuração.** As alterações feitas em um ativo (durante a correção, replicação ou preparo) têm que ser documentadas para haver prontidão operacional.
- **Documentação de pendências.** A lista de pendências de migração precisa ser atualizada para refletir a carga de trabalho e os ativos preparados.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Depois que os ativos preparados são testados e documentados, você pode prosseguir para as [atividades de otimização](../optimize/index.md).

> [!div class="nextstepaction"]
> [Otimizar cargas de trabalho migradas](../optimize/index.md)
