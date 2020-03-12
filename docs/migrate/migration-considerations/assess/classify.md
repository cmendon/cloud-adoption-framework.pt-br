---
title: Classificação de carga de trabalho antes da migração
description: Classifique suas cargas de trabalho durante uma avaliação de pré-migração.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/03/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 8f912891bf90d0ecef29727d7d7a067d442234fc
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79095329"
---
# <a name="workload-classification-before-migration"></a>Classificação de carga de trabalho antes da migração

Durante cada iteração de qualquer processo de migração, uma ou mais cargas de trabalho serão migradas e promovidas para a produção. Antes de qualquer uma dessas atividades de migração, é importante classificar cada carga de trabalho. A classificação ajuda a esclarecer os requisitos de governança, segurança, operações e gerenciamento de dados.

As diretrizes a seguir se baseiam nos requisitos de marcação sugeridos descritos no [artigo padrões de nomenclatura e marcação](../../../ready/azure-best-practices/naming-and-tagging.md#metadata-tags) adicionando elementos importantes de [operações](../../../manage/considerations/criticality.md#criticality-scale) e [governança](../../../govern/guides/complex/prescriptive-guidance.md#resource-tagging) .

Neste artigo, sugerimos especificamente a adição de criticalidade e sensibilidade de dados aos padrões de marcação existentes. Cada um desses pontos de dados ajudará outras equipes a entender quais cargas de trabalho podem exigir atenção ou suporte adicional.

## <a name="data-sensitivity"></a>Sensibilidade de dados

Conforme descrito no artigo sobre [classificação de dados](../../../govern/policy-compliance/data-classification.md), a classificação de dados mede o impacto que um vazamento de dados teria nos negócios ou nos clientes. As equipes de governança e segurança aproveitam a sensibilidade de dados ou a classificação de dados como um indicador de riscos de segurança. Durante a avaliação, a equipe de adoção de nuvem deve avaliar a classificação de dados para cada carga de trabalho direcionada para a migração e compartilhar essa classificação com as equipes de suporte. As cargas de trabalho que lidam estritamente em "dados públicos" podem não ter nenhum impacto sobre as equipes de suporte. No entanto, à medida que os dados se movem ainda mais para o final "altamente confidencial" do espectro, as equipes de governança e segurança provavelmente terão um interesse maior em participar da avaliação da carga de trabalho.

Trabalhe com suas equipes de segurança e governança o mais cedo possível para definir os seguintes itens:

- Um processo claro para compartilhar qualquer carga de trabalho na pendência com dados confidenciais.
- Uma compreensão dos requisitos de governança e da linha de base de segurança necessários para vários níveis diferentes de sensibilidade de dados.
- Qualquer sensibilidade de dados de impacto pode ter um design de assinatura, hierarquias de grupo de gerenciamento ou requisitos de zona de aterrissagem.
- Quaisquer requisitos para testar a classificação de dados, que podem incluir ferramentas específicas ou escopo definido de classificação.

## <a name="mission-criticality"></a>Criticalidade de missão

Conforme descrito no artigo sobre a [criticalidade da carga de trabalho](../../../manage/considerations/criticality.md), a criticalidade de uma carga de trabalho é uma medida de quão significativamente a empresa será afetada durante uma interrupção. Esse ponto de dados ajuda as equipes de gerenciamento de operações e segurança a avaliar os riscos relacionados a interrupções e violações. Durante a avaliação, a equipe de adoção de nuvem deve avaliar a importância da missão para cada carga de trabalho direcionada para a migração e compartilhar essa classificação com as equipes de suporte. Cargas de trabalho "baixa" ou "sem suporte" provavelmente terão pouco impacto nas equipes de suporte. No entanto, à medida que as cargas de trabalho abordam as classificações "de missão crítica" ou "unidade crítica", suas dependências operacionais se tornam mais aparentes.

Trabalhe com suas equipes de segurança e operações o mais cedo possível para definir os seguintes itens:

- Um processo claro para compartilhar qualquer carga de trabalho na pendência com requisitos de suporte.
- Uma compreensão dos requisitos de gerenciamento de operações e de consistência de recursos para vários níveis diferentes de importância.
- Qualquer criticalidade de impacto pode ter um design de assinatura, hierarquias de grupo de gerenciamento ou requisitos de zona de aterrissagem.
- Quaisquer requisitos para documentar a criticalidade, que podem incluir tráfego específico ou relatórios de uso, análises financeiras ou outras ferramentas.

## <a name="next-steps"></a>Próximas etapas

Depois que as cargas de trabalho são classificadas corretamente, é muito mais fácil [alinhar as prioridades dos negócios](./business-priorities.md).

> [!div class="nextstepaction"]
> [Alinhar prioridades empresariais](./business-priorities.md)
