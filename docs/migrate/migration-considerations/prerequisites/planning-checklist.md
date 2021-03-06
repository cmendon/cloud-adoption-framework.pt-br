---
title: Lista de verificação de planejamento do ambiente de migração
description: Use a lista de verificação de planejamento do ambiente de migração para validar a prontidão do ambiente antes da migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: c428edaa37924b7e72bb0b9b86537d6cce5b241b
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311975"
---
# <a name="migration-environment-planning-checklist-validate-environmental-readiness-prior-to-migration"></a>Lista de verificação de planejamento do ambiente de migração: validar prontidão do ambiente antes da migração

Como uma etapa inicial no processo de migração, você precisa criar o ambiente certo na nuvem para receber, hospedar e dar suporte à migração de ativos. Este artigo fornece uma lista de coisas a serem validadas no ambiente atual antes da migração.

A lista de verificação a seguir está alinhada com as diretrizes encontradas na [seção Pronta](../../../ready/index.md) do Cloud Adoption Framework. Examine essa seção para obter orientação sobre a execução de qualquer um dos seguintes.

## <a name="effort-type-assumption"></a>Pressuposição do tipo de esforço

Este artigo e a lista de verificação assumem uma abordagem de _novo host_ ou de _transição da nuvem_ para a migração na nuvem.

## <a name="governance-alignment"></a>Alinhamento de governança

A primeira e mais importante decisão sobre qualquer ambiente pronto para a migração é a opção de alinhamento da governança. Chegou-se a um consenso sobre o alinhamento da governança com a fundação da migração? No mínimo, a equipe de adoção de nuvem deve entender se essa migração é inicial em um único ambiente com governança limitada, uma fábrica de ambiente totalmente controlada ou alguma variante entre elas. Para obter diretrizes adicionais sobre o alinhamento de governança, consulte a [metodologia](../../../govern/index.md)de controle.

## <a name="operations-management-alignment"></a>Alinhamento do gerenciamento de operações

Antes de migrar ativos para a nuvem, é importante entender quaisquer requisitos ou restrições relacionados ao gerenciamento de operações. No mínimo, o ambiente de migração deve incluir todas as implementações necessárias para atender à linha de base de operações. Para obter diretrizes adicionais sobre o alinhamento de operações, consulte a [metodologia gerenciar](../../../manage/index.md).

## <a name="cloud-readiness-implementation"></a>Implementação de preparação para a nuvem

Quer você escolha se alinhar com uma estratégia de governança de nuvem mais ampla ou não para sua migração inicial, será necessário garantir que seu ambiente de implantação de nuvem esteja configurado para dar suporte às suas cargas de trabalho.

Se você estiver planejando alinhar sua migração com uma estratégia de governança de nuvem desde o início, será necessário aplicar as [Cinco Disciplinas da Governança de Nuvem](../../../govern/governance-disciplines.md) para ajudar a informar decisões sobre políticas, cadeias de ferramentas e mecanismos de imposição que alinharão seu ambiente de nuvem com os requisitos corporativos gerais. Consulte os [guias de design de governança acionáveis](../../../govern/guides/index.md) do Cloud Adoption Framework para obter exemplos de como implementar esse modelo usando os serviços do Azure.

Se as migrações iniciais não estiverem fortemente alinhadas com uma estratégia de governança de nuvem mais ampla, os problemas gerais de organização, acesso e planejamento de infraestrutura ainda precisarão ser gerenciados. Consulte o [Guia de instalação do Azure](../../../ready/azure-setup-guide/index.md) para obter ajuda com essas decisões de preparação para a nuvem.

> [!CAUTION]
> É altamente recomendável que você desenvolva uma estratégia de governança para qualquer coisa além da sua migração de carga de trabalho inicial.

Independentemente do seu nível de alinhamento de governança, será necessário tomar decisões relacionadas aos tópicos a seguir.

### <a name="resource-organization"></a>Organização do recurso

Com base na decisão de alinhamento da governança, uma abordagem para a organização e a implantação de recursos deve ser estabelecida antes da migração.

### <a name="nomenclature"></a>Nomenclatura

Deve ser estabelecida antes da migração uma abordagem consistente para dar nome aos recursos, juntamente com esquemas de nomenclatura consistentes.

### <a name="resource-governance"></a>Governança de recursos

Uma decisão quanto às ferramentas para controlar os recursos deve ser tomada antes da migração. As ferramentas não precisam ser totalmente implementadas, mas uma direção deve ser selecionada e testada. A equipe de governança de nuvem deve definir e exigir a implementação de um MVP (produto viável) mínimo para ferramentas de governança antes da migração.

## <a name="network"></a>Rede

Suas cargas de trabalho baseadas em nuvem exigirão o provisionamento de redes virtuais para dar suporte ao usuário final e ao acesso administrativo. Com base nas decisões de organização de recursos e governança de recursos, você deve selecionar uma abordagem de rede para alinhá-la aos requisitos de segurança de TI. Além disso, suas decisões de rede devem estar alinhadas com todas as restrições de rede híbridas necessárias para operar as cargas de trabalho na lista de pendências da migração e dar suporte para acesso aos recursos hospedados localmente.

## <a name="identity"></a>Identity

Os serviços de identidade baseados em nuvem são um pré-requisito para oferecer IAM (gerenciamento de identidade e acesso) para seus recursos de nuvem. Alinhe sua estratégia de gerenciamento de identidades com seus planos de adoção da nuvem antes de continuar. Por exemplo, ao migrar ativos locais existentes, considere a possibilidade de oferecer suporte para uma abordagem de identidade híbrida usando a [sincronização de diretório](../../../decision-guides/identity/index.md) a fim de permitir um conjunto consistente de credenciais de usuário em seus ambientes local e na nuvem, durante e após a migração.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Se o ambiente atender aos requisitos mínimos, ele poderá ser considerado aprovado para preparação para a migração. [A complexidade cultural e o gerenciamento de alterações](./cultural-complexity.md) ajudam a alinhar funções e responsabilidades para garantir as expectativas adequadas durante a execução do plano.

> [!div class="nextstepaction"]
> [Complexidade cultural e gerenciamento de alterações](./cultural-complexity.md)
