---
title: Validar suposições de avaliação antes da migração
description: Validar suposições de avaliação antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: e370ef47b27449a3a46965dc309403a09fb3829d
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78222270"
---
# <a name="validate-assessment-assumptions-before-migration"></a>Validar suposições de avaliação antes da migração

Muitas de suas cargas de trabalho existentes são candidatas ideais para a migração na nuvem, mas nem todo ativo é compatível com plataformas de nuvem e nem todas as cargas de trabalho podem se beneficiar de hospedagem na nuvem. O [planejamento de acervo digital](../../../digital-estate/index.md) permite que você gere uma [lista de pendências de migração](../prerequisites/technical-complexity.md#migration-backlog-aligning-business-priorities-and-timing) geral de cargas de trabalho potenciais para migrar. No entanto, esse esforço de planejamento é de alto nível. Ele baseia-se em suposições feitas pela equipe de estratégia de nuvem e não se aprofunda em considerações técnicas.

Como resultado, antes de migrar uma carga de trabalho para a nuvem, é crítico avaliar se os ativos individuais associados a ela são adequados para migração. Durante essa avaliação, sua equipe de adoção da nuvem deve avaliar a compatibilidade técnica, a arquitetura necessária, as expectativas de desempenho/dimensionamento e as dependências para garantir que a carga de trabalho migrada possa ser implantada para a nuvem com eficiência.

O processo de *Avaliação* é a primeira de quatro atividades incrementais que ocorrem dentro de uma iteração. Conforme discutido no artigo de pré-requisito em relação ao [gerenciamento de alterações e à complexidade técnica](../prerequisites/technical-complexity.md), uma decisão deve ser tomada com antecedência para determinar como essa fase será executada. Em particular, a avaliação será concluída pela equipe de adoção de nuvem durante o mesmo sprint que o esforço de migração real? Como alternativa, um modelo de onda ou alocador será usado para concluir a avaliação em uma iteração separada? Se cada membro da equipe não puder responder a essa pergunta de processo básica, talvez seja aconselhável rever a seção [Pré-requisitos](../prerequisites/index.md).

## <a name="objective"></a>Objetivo

Avalie um candidato à migração analisando a carga de trabalho, os ativos associados e as dependências antes da migração.

## <a name="definition-of-done"></a>Definição de *concluído*

Esse processo está concluído quando sabemos o seguinte sobre um único candidato a migração:

- O caminho do local para a nuvem, incluindo a decisão de abordagem de promoção de produção, foi definido.
- Quaisquer aprovações, alterações, estimativas de custo ou processos de validação necessários foram concluídos para permitir que a equipe de adoção de nuvem execute a migração.

## <a name="accountability-during-assessment"></a>Responsabilidade durante a avaliação

A equipe de adoção de nuvem é responsável por todo o processo de avaliação. No entanto, os membros da equipe de estratégia de nuvem têm algumas responsabilidades, conforme listado na seção a seguir.

## <a name="responsibilities-during-assessment"></a>Responsabilidades durante a avaliação

Além da responsabilidade de alto nível, há ações pelas quais uma pessoa ou grupo precisa ser diretamente responsável. Estas são algumas atividades que exigem atribuições a partes responsáveis:

- **Prioridade empresarial.** A equipe compreende a finalidade para migrar essa carga de trabalho, incluindo qualquer impacto desejado aos negócios.
  - Um membro da equipe de estratégia de nuvem deve assumir a responsabilidade final por essa atividade sob a orientação da equipe de adoção da nuvem.
- **Alinhamento de stakeholder.** A equipe alinha expectativas e prioridades com os stakeholders internos, identificando os critérios de sucesso para a migração. Como é o sucesso após a migração?
- **Racionalização refinada.** Avalie as suposições iniciais sobre a racionalização. Uma [abordagem de racionalização](../../../digital-estate/rationalize.md) diferente deve ser usada para migrar esta carga de trabalho específica?
- **Decisões de modernização.** Independentemente da decisão de racionalização, os vários ativos na carga de trabalho devem ser modernizados para aproveitar as soluções baseadas em PaaS?
- **Custo.** O custo da arquitetura de destino foi estimado e o orçamento geral foi ajustado.
- **Suporte à migração.** A equipe decidiu como o trabalho técnico da migração será concluído, incluindo decisões sobre o Suporte da Microsoft ou do parceiro.
- **Avaliação.** A compatibilidade e as dependências da carga de trabalho são avaliadas.
  - Essa atividade deve ser atribuída a um especialista que esteja familiarizado com a arquitetura e as operações da carga de trabalho candidata.
- **Arquitetar.** A equipe chegou a um acordo quanto à arquitetura do estado final para a carga de trabalho migrada.
- **Ferramentas de migração.** Dependendo das abordagens de modernização e arquitetura, uma variedade de ferramentas de migração poderia ser usada para automatizar a migração. Com base na arquitetura proposta, essa migração usará as melhores [ferramentas de migração](../../../decision-guides/migrate-decision-guide/index.md)?
- **Alinhamento da lista de pendências.** A equipe de adoção de nuvem examina os requisitos e compromete-se com a migração da carga de trabalho candidata. Depois de comprometer-se, a lista de pendências de versão e a lista de pendências de iteração devem ser atualizadas adequadamente.
- **Estrutura de detalhamento de trabalho ou agenda de work-back.** A equipe estabelece uma agenda dos principais marcos identificando metas de prazo de conclusão dos processos de planejar, implementar e examinar.
- **Aprovação final.** Qualquer aprovador necessário examinou o plano e aprovou a abordagem para fazer a migração do ativo.
  - Para evitar surpresas mais adiante no processo, pelo menos um representante da empresa deve estar envolvido no processo de aprovação.

> [!CAUTION]
> Essa lista completa de responsabilidades e ações pode dar suporte a migrações grandes e complexas envolvendo várias funções com diferentes níveis de responsabilidade e exigindo um processo de aprovação detalhado. Esforços de migração menores e mais simples podem não exigir todas as funções e ações descritas aqui. Para determinar quais dessas atividades agregam valor e quais são desnecessárias, a equipe de adoção de nuvem e a equipe de estratégia de nuvem devem usar esse processo completo como parte da primeira migração de carga de trabalho. Depois que a carga de trabalho tiver sido verificada e testada, a equipe poderá avaliar esse processo e escolher quais ações usar mais adiante.

## <a name="next-steps"></a>Próximas etapas

Com uma compreensão geral do processo de avaliação, você está pronto para iniciar o processo [alinhando as prioridades empresariais](./business-priorities.md).

> [!div class="nextstepaction"]
> [Alinhar prioridades empresariais](./business-priorities.md)
