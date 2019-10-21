---
title: Ambiente de migração-lista de verificação de planejamento
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Validar prontidão ambiental antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5b4e192aac3cf73aca704ed2c04116cd0d2a972b
ms.sourcegitcommit: b30952f08155513480c6b2c47a40271c2b2357cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72378377"
---
# <a name="migration-environment-planning-checklist---validate-environmental-readiness-prior-to-migration"></a>Lista de verificação de planejamento do ambiente de migração – validar prontidão do ambiente antes da migração

Como uma etapa inicial no processo de migração, você precisa criar o ambiente certo na nuvem para receber, hospedar e dar suporte à migração de ativos. Este artigo fornece uma lista de itens a serem validados no ambiente atual antes da migração.

A lista de verificação a seguir se alinha com as diretrizes encontradas na [seção pronta](../../../ready/index.md) da estrutura de adoção de nuvem. Examine essa seção para obter orientação sobre a execução de qualquer um dos seguintes.

## <a name="effort-type-assumption"></a>Pressuposição de tipo de esforço

Este artigo e a lista de verificação assumem uma abordagem de _Rehost_ ou de _transição de nuvem_ para a migração na nuvem.

## <a name="governance-alignment"></a>Alinhamento de governança

A primeira e mais importante decisão sobre qualquer ambiente pronto para migração é a opção de alinhamento de governança. Um consenso foi obtido com relação ao alinhamento de governança com o Migration Foundation? No mínimo, a equipe de adoção de nuvem deve entender se essa migração é inicial em um único ambiente com governança limitada, uma fábrica de ambiente totalmente controlada ou alguma variante entre elas. Para obter mais opções e diretrizes sobre o alinhamento de governança, consulte o artigo sobre [alinhamento de governança e conformidade](../../expanded-scope/governance-or-compliance.md).

## <a name="cloud-readiness-implementation"></a>Implementação de preparação para a nuvem

Se você optar por se alinhar com uma estratégia de governança de nuvem mais ampla ou não para a migração inicial, será necessário garantir que seu ambiente de implantação de nuvem esteja configurado para dar suporte às suas cargas de trabalho.

Se estiver planejando alinhar sua migração com uma estratégia de governança de nuvem desde o início, você precisará aplicar as [cinco disciplinas de governança de nuvem](../../../govern/governance-disciplines.md) para ajudar a informar decisões sobre políticas, cadeias e mecanismos de imposição que alinharão seu ambiente de nuvem com requisitos corporativos gerais. Consulte os [guias de design de governança acionáveis](../../../govern/guides/index.md) da estrutura de adoção de nuvem para obter exemplos de como implementar esse modelo usando os serviços do Azure.

Se suas migrações iniciais não estiverem fortemente alinhadas com uma estratégia de governança de nuvem mais ampla, os problemas gerais de organização, acesso e planejamento de infraestrutura ainda precisam ser gerenciados. Consulte o [Guia de instalação do Azure](../../../ready/azure-setup-guide/index.md) para obter ajuda com essas decisões de preparação para a nuvem.

> [!CAUTION]
> É altamente recomendável que você desenvolva uma estratégia de governança para qualquer coisa além da migração de carga de trabalho inicial.

Independentemente do seu nível de alinhamento de governança, será necessário tomar decisões relacionadas aos tópicos a seguir.

### <a name="resource-organization"></a>Organização de recursos

Com base na decisão de alinhamento da governança, uma abordagem para a organização e a implantação de recursos devem ser estabelecidas antes da migração.

### <a name="nomenclature"></a>Nomenclatura

Uma abordagem consistente para nomear recursos, juntamente com esquemas de nomenclatura consistentes, deve ser estabelecida antes da migração.

### <a name="resource-governance"></a>Governança de recursos

Uma decisão sobre as ferramentas para controlar os recursos deve ser feita antes da migração. As ferramentas não precisam ser totalmente implementadas, mas uma direção deve ser selecionada e testada. É recomendável que a equipe de governança de nuvem defina e exija a implementação de um MVP (produto viável) mínimo para ferramentas de governança antes da migração.

## <a name="network"></a>Rede

Suas cargas de trabalho baseadas em nuvem exigirão o provisionamento de redes virtuais para dar suporte ao usuário final e ao acesso administrativo. Com base nas decisões de controle de recursos e da organização de recursos, você deve selecionar uma abordagem de rede para alinhá-la aos requisitos de segurança de ti. Além disso, suas decisões de rede devem ser alinhadas com quaisquer restrições de rede híbridas necessárias para operar as cargas de trabalho na pendência de migração e dar suporte a qualquer acesso aos recursos hospedados localmente.

## <a name="identity"></a>Identidade

Os serviços de identidade baseados em nuvem são um pré-requisito para oferecer IAM (gerenciamento de identidade e acesso) para seus recursos de nuvem. Alinhe sua estratégia de gerenciamento de identidade com seus planos de adoção de nuvem antes de continuar. Por exemplo, ao migrar ativos locais existentes, considere dar suporte a uma abordagem de identidade híbrida usando a [sincronização de diretório](../../../decision-guides/identity/index.md) para permitir um conjunto consistente de credenciais de usuário em ambientes de nuvem e locais durante e após o as.

## <a name="next-steps"></a>Próximos passos

Se o ambiente atender aos requisitos mínimos, ele poderá ser considerado aprovado para preparação da migração. A [complexidade cultural e o gerenciamento de alterações](./cultural-complexity.md) ajudam a alinhar funções e responsabilidades para garantir as expectativas adequadas durante a execução do plano.

> [!div class="nextstepaction"]
> [Complexidade cultural e gerenciamento de alterações](./cultural-complexity.md)
