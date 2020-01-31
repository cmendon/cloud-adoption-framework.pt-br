---
title: Otimizar cargas de trabalho migradas
description: Otimizar cargas de trabalho migradas
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 87235584bc9da0f1a9e5124408b587eec864af48
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801878"
---
# <a name="optimize-migrated-workloads"></a>Otimizar cargas de trabalho migradas

Depois que uma carga de trabalho e seus ativos de suporte forem migrados para a nuvem, eles deverão ser preparados antes que possam ser promovidos para produção. Neste processo, as atividades preparam a carga de trabalho, dimensionam os ativos dependentes e preparam a empresa para quando a carga de trabalho baseada em nuvem migrada entrar em uso em produção.

O objetivo da otimização é preparar uma carga de trabalho migrada para a promoção para uso em produção.

## <a name="definition-of-done"></a>Definição de *concluído*

O processo de otimização está concluído quando uma carga de trabalho foi corretamente configurada, dimensionada e está sendo usada na produção.

## <a name="accountability-during-optimization"></a>Responsabilidade durante a otimização

A equipe de adoção da nuvem é responsável por todo o processo de otimização. No entanto, os membros da equipe de estratégia de nuvem, da equipe de operações de nuvem e da equipe de governança de nuvem também devem ser responsáveis por atividades dentro desse processo.

## <a name="responsibilities-during-optimization"></a>Responsabilidades durante a otimização

Além da responsabilidade de alto nível, há ações pelas quais uma pessoa ou grupo precisa ser diretamente responsável. Estas são algumas atividades que exigem atribuições a partes responsáveis:

- **Teste empresarial.** Resolva quaisquer problemas de compatibilidade que impeçam a conclusão da migração da carga de trabalho para a nuvem.
  - Usuários avançados de dentro da empresa devem participar intensamente do teste da carga de trabalho migrada. Dependendo do grau de otimização que foi tentado, vários ciclos de teste podem ser necessários.
- **Plano de mudança empresarial.** Desenvolvimento de um plano para a adoção do usuário, alterações a processos empresariais e modificação para KPIs de negócios ou métricas de aprendizado como resultado do esforço de migração.
- **Submeter a benchmark e otimizar.** Estudo do teste empresarial e do teste automatizado para submeter o desempenho a benchmark. Com base no uso, a equipe de adoção de nuvem refina o dimensionamento dos ativos implantados para balancear custo e desempenho em relação aos requisitos de produção esperados.
- **Pronto para produção.** Prepare a carga de trabalho e o ambiente para o suporte do uso de produção contínuo da carga de trabalho.
- **Promover.** Redirecione o tráfego de produção para a carga de trabalho migrada e otimizada. Esta atividade representa a conclusão de um ciclo de lançamento.

Além das atividades principais, há algumas atividades paralelas que exigem atribuições e planos de execução específicos:

- **Desativação.** Em geral, é possível obter economias de custo de uma migração quando os ativos de produção anteriores são desativados e descartados adequadamente.
- **Retrospectiva.** Cada versão cria uma oportunidade para aprendizado mais profundo e a adoção de uma mentalidade de crescimento. Quando cada ciclo de versão é concluído, a equipe de adoção da nuvem deve avaliar os processos usados durante a migração para identificar aperfeiçoamentos.

## <a name="next-steps"></a>Próximas etapas

Com uma compreensão geral do processo de otimização, você está pronto para iniciar o processo [estabelecendo um plano de mudança empresarial para a carga de trabalho candidata](./business-change-plan.md).

> [!div class="nextstepaction"]
> [Plano de mudança empresarial](./business-change-plan.md)
