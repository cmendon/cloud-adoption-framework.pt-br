---
title: 'Governança empresarial complexa: várias camadas de governança'
description: Use a estrutura de adoção de nuvem para o Azure para saber mais sobre níveis mais altos de complexidade com várias camadas de governança em grandes empresas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 5d7dc2163777cb931d6c4c57eb7b1fb276e6a0fd
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77709185"
---
# <a name="governance-guide-for-complex-enterprises-multiple-layers-of-governance"></a>Guia de governança para empresas complexas: várias camadas de governança

Quando grandes empresas exigem várias camadas de governança, há mais níveis de complexidade que devem ser fatorados no MVP de governança e nos aprimoramentos de governança posteriores.

Alguns exemplos comuns de tais complexidades incluem:

- Funções de governança distribuída.
- IT Corporativa com suporte às organizações de TI da unidade comercial.
- Suporte de TI corporativa que dá suporte geograficamente distribuído em organizações de TI distribuídas.

Este artigo explora algumas maneiras de navegar por esse tipo de complexidade.

## <a name="large-enterprise-governance-is-a-team-sport"></a>A governança de empresas de grande porte é um esporte em equipe

Grandes empresas estabelecidas geralmente têm equipes ou funcionários que se concentram nas disciplinas mencionadas em todo este guia. Este guia demonstra uma abordagem para tornar a governança um esporte de equipe.

Em muitas grandes empresas, as cinco disciplinas de governança de nuvem podem ser bloqueadores para adoção. Desenvolver competências de nuvem na identidade, segurança, operações, implantações e configuração em toda a empresa leva tempo. Implementar holisticamente a política de governança de TI e segurança de TI pode diminuir a inovação por meses ou até mesmo anos. Equilibrar a necessidade de negócios para inovar e a necessidade de governança para proteger os recursos existentes é delicada.

Os recursos inerentes da nuvem podem remover bloqueadores de inovação, mas aumentar os riscos. Neste guia de governança, mostramos como a empresa de exemplo criou o guardrails para gerenciar os riscos. Em vez de lidar com cada uma das disciplinas necessárias para proteger o ambiente, a equipe de governança de nuvem lidera uma abordagem baseada em risco para controlar o que poderia ser implantado, enquanto as outras equipes criam os desenvolvimentos de nuvem necessários. Mais importante, à medida que cada equipe atinge a maturidade de nuvem, a governança aplica suas soluções de forma global. À medida que cada equipe amadurece e acrescenta à solução geral, a equipe de governança de nuvem pode abrir as Gates de etapas, permitindo inovações e adoção adicionais para prosperar.

Esse modelo ilustra o crescimento de uma parceria entre a equipe de governança de nuvem e as equipes corporativas existentes (segurança, governança de ti, rede, identidade e outros). O guia começa com o MVP de governança e cresce para um estado de extremidade holística por meio de iterações de governança.

## <a name="requirements-to-supporting-such-a-team-sport"></a>Requisitos para dar suporte a uma equipe de esporte

O primeiro requisito de um modelo de governança de várias camadas é entender a hierarquia de governança. Responder às seguintes perguntas ajudará você a entender a hierarquia de governança geral:

- Como a contabilização de nuvem (cobrança dos serviços de nuvem) é alocada entre as unidades de negócios?
- Como as responsabilidades de governança são alocadas na TI corporativa e em cada unidade de negócios?
- Que tipos de ambientes fazem cada uma dessas unidades de IT gerenciar?

## <a name="central-governance-of-a-distributed-governance-hierarchy"></a>A governança central de uma hierarquia de governança distribuída

Ferramentas, como grupos de gerenciamento, permitem que a TI corporativa crie uma estrutura de hierarquia que corresponda à hierarquia de governança. Ferramentas como o Azure Blueprints podem aplicar ativos a camadas diferentes dessa hierarquia. Especificações técnicas do Azure Blueprints podem ser atualizadas e várias versões podem ser aplicadas a grupos de gerenciamento, assinaturas ou grupos de recursos. Cada um desses conceitos é descrito mais detalhadamente nas seções a seguir.

O aspecto importante de cada uma dessas ferramentas é a capacidade de aplicar vários planos de gráficos para uma hierarquia. Isso permite que o controle seja um processo em camadas. A seguir, um exemplo dessa aplicação hierárquica de governança:

- **Ti corporativa:** TI corporativa cria um conjunto de padrões e políticas que se aplicam a toda a adoção da nuvem. Isso é materializado em um blueprint de "Linha de base". A TI corporativa possui, em seguida, a hierarquia de grupo de gerenciamento, garantindo que uma versão da linha de base é aplicada a todas as assinaturas na hierarquia.
- **Ti regional ou de unidade de negócios:** Várias equipes de ti podem aplicar uma camada adicional de governança criando seu próprio plano gráfico. Esses blueprints criaram políticas e padrões aditivos. Depois que desenvolvido, a TI corporativa pode aplicar esses planos gráficos para os nós aplicáveis na hierarquia de grupo de gerenciamento.
- **Equipes de adoção de nuvem:** Decisões e implementação detalhadas sobre aplicativos ou cargas de trabalho podem ser feitas por cada equipe de adoção de nuvem, dentro do contexto de requisitos de governança. Às vezes, a equipe também pode solicitar outros modelos de consistência de recursos do Azure para acelerar os esforços de adoção.

Obtenha detalhes sobre a implementação da governança em cada nível exigirá a coordenação entre cada equipe. O MVP de governança e os aprimoramentos de governança descritos neste guia podem ajudar a alinhar essa coordenação.
