---
title: 'Preparação para complexidade cultural: alinhamento de funções e responsabilidades'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Preparação para complexidade cultural – alinhamento de funções e responsabilidades.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 011d00038ea29c60601945441f21b14b8865f80d
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833343"
---
# <a name="prepare-for-cultural-complexity-aligning-roles-and-responsibilities"></a>Preparação para complexidade cultural: alinhamento de funções e responsabilidades

Uma compreensão da cultura necessária para operar os datacenters existentes é importante para o sucesso de qualquer migração. Em algumas organizações, o gerenciamento de datacenters fica contido em equipes de operações de TI centralizadas. Nessas equipes centralizadas, funções e responsabilidades tendem a ser bem definidas e bem compreendidas em toda a equipe. Para empresas maiores, especialmente aquelas que seguem requisitos de conformidade de terceiros, a cultura tende a ser mais sutil e complexa. A complexidade cultural pode levar a obstáculos difíceis de entender e que demoram para serem superados.

Qualquer que seja o cenário, é prudente investir na documentação das funções e responsabilidades necessárias para concluir uma migração. Este artigo descreve algumas das funções e responsabilidades vistas em uma migração de datacenter, para servir como um modelo de documentação que pode levar à clareza durante a execução.

## <a name="business-functions"></a>Funções empresariais

Em qualquer migração, há algumas funções importantes que são mais bem executadas pela empresa, sempre que possível. Frequentemente, o setor de TI é capaz de concluir as tarefas a seguir. No entanto, envolver membros da empresa pode ajudar a reduzir barreiras posteriormente no processo de adoção. Isso também garante o investimento mútuo dos principais stakeholders durante o processo de migração.

| Process | Atividade | Descrição |
|---------|---------|---------|
| Avaliar | Metas empresariais | Defina os resultados dos negócios desejados do esforço de migração. |
| Avaliar | Prioridades | Garanta o alinhamento com as diferentes prioridades empresariais e condições de mercado. |
| Avaliar | Justificação | Valide suposições que levam a justificativas comerciais em evolução. |
| Avaliar | Risco | Ajude a equipe de adoção da nuvem a entender o impacto dos riscos empresariais tangíveis. |
| Avaliar | Aprovar | Examine e aprove o impacto empresarial das alterações de arquitetura propostas. |
| Otimizar | Alterar plano | Defina um plano para o consumo de alterações dentro da empresa, incluindo períodos de baixa atividade e congelamento de alterações. |
| Otimizar | Testes | Alinhe os usuários avançados capazes de validar o desempenho e a funcionalidade. |
| Proteger e gerenciar | Impacto da interrupção | Auxilie a equipe de adoção da nuvem a quantificar o impacto da interrupção de um processo empresarial. |
| Proteger e gerenciar | Validação do SLA (contrato de nível de serviço) | Auxilie a equipe de adoção da nuvem na definição dos contratos de nível de serviço e das tolerâncias aceitáveis para interrupções empresariais. |

No fim, a equipe de adoção da nuvem é responsável por cada uma dessas atividades. No entanto, estabelecer responsabilidades e uma cadência regular com a empresa para a conclusão dessas atividades em um ritmo estabelecido pode melhorar o alinhamento dos stakeholders e a coesão com a empresa.

## <a name="common-roles-and-responsibilities"></a>Funções e responsabilidades comuns

Cada processo na discussão sobre os princípios de migração da Estrutura de Adoção da Nuvem inclui um artigo de processo que descreve atividades específicas para alinhar funções e responsabilidades. Para maior clareza durante a execução, uma única pessoa responsável pela conta deve ser atribuída a cada atividade, juntamente com as partes responsáveis necessárias para dar suporte a essas atividades. No entanto, a lista a seguir contém uma série de funções e responsabilidades comuns que têm um nível mais alto de impacto na execução da migração. Essas funções devem ser identificadas no início do esforço de migração.

> [!NOTE]
> Na tabela a seguir, uma parte que pode ser responsabilizada deve iniciar o alinhamento das funções. Essa coluna deve ser personalizada para se ajustar aos processos existentes para levar a uma execução eficiente. Idealmente, uma única pessoa deve ser nomeada como a parte responsável pela conta.

| Process | Atividade | Descrição | Parte responsável |
|---------|---------|---------|---------|
| Pré-requisito | Propriedade digital | Alinhar o inventário existente a pressuposições básicas, com base nos resultados dos negócios. | equipe de estratégia da nuvem |
| Pré-requisito | Lista de pendências da migração | Priorizar a sequência de cargas de trabalho a serem migradas. | equipe de estratégia da nuvem |
| Avaliar | Arquitetura | Desafiar suposições iniciais para definir a arquitetura de destino com base nas métricas de uso. | equipe de adoção da nuvem |
| Avaliar | Aprovação | Aprovar a arquitetura proposta. | equipe de estratégia da nuvem |
| Migrar | Acesso à replicação | Acesso a hosts e ativos locais existentes para estabelecer processos de replicação. | equipe de adoção da nuvem |
| Otimizar | Pronto | Validar se o sistema atende aos requisitos de desempenho e custo antes da promoção. | equipe de adoção da nuvem |
| Otimizar | Promover | Permissões para promover uma carga de trabalho para produção e redirecionar o tráfego de produção. | equipe de adoção da nuvem |
| Proteger e gerenciar | Transição de operações | Documentar os sistemas de produção antes das operações de produção. | equipe de adoção da nuvem |

> [!CAUTION]
> Para essas atividades, as permissões e a autorização influenciam muito a parte responsável, que deve ter acesso direto aos sistemas de produção no ambiente existente ou deve ter meios de garantir o acesso por meio de outros atores responsáveis. Determinar essa parte responsável afeta diretamente a estratégia de promoção durante os processos de migração e otimização.

## <a name="next-steps"></a>Próximas etapas

Quando a equipe tem uma compreensão geral das funções e responsabilidades, é hora de começar a preparar os detalhes técnicos da migração. Compreender a [complexidade técnica e o gerenciamento de alterações](./technical-complexity.md) pode ajudar a preparar a equipe de adoção da nuvem para a complexidade técnica da migração alinhando-se a um processo de gerenciamento de alterações incremental.

> [!div class="nextstepaction"]
> [Complexidade técnica e gerenciamento de alterações](./technical-complexity.md)
