---
title: 'Preparar para complexidade cultural: alinhando funções e responsabilidades'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Prepare-se para a complexidade cultural alinhando funções e responsabilidades.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: bc880e3bb27492b18a8e577911527978c7a4e0d2
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548342"
---
# <a name="prepare-for-cultural-complexity-aligning-roles-and-responsibilities"></a>Preparar para complexidade cultural: alinhando funções e responsabilidades

Uma compreensão da cultura necessária para operar os data centers existentes é importante para o sucesso de qualquer migração. Em algumas organizações, o gerenciamento de datacenter está contido em equipes de operações de ti centralizadas. Nessas equipes, funções e responsabilidades centralizadas tendem a ser bem definidas e bem compreendidas em toda a equipe. Para empresas maiores, especialmente aquelas associadas a requisitos de conformidade de terceiros, a cultura tende a ser mais nuance e complexa. A complexidade cultural pode levar a obstáculos que são difíceis de entender e que demoram para superar.

Em qualquer cenário, é prudente investir na documentação de funções e responsabilidades necessárias para concluir uma migração. Este artigo descreve algumas das funções e responsabilidades vistas em uma migração de datacenter, para servir como um modelo de documentação que pode impulsionar a clareza durante a execução.

## <a name="business-functions"></a>Funções de negócios

Em qualquer migração, há algumas funções importantes que são mais bem executadas pela empresa, sempre que possível. Geralmente, ele é capaz de concluir as tarefas a seguir. No entanto, envolver os membros da empresa pode ajudar a reduzir as barreiras posteriormente no processo de adoção. Ele também garante o investimento mútuo das principais partes interessadas durante o processo de migração.

| Processo | Atividade | Descrição |
|---------|---------|---------|
| Avalie | Objetivos de negócios | Defina os resultados de negócios desejados do esforço de migração. |
| Avalie | Suas | Garanta o alinhamento com as prioridades de negócios e as condições de mercado em constante mudança. |
| Avalie | Elabora | Valide suposições que orientam a alteração de justificativas de negócios. |
| Avalie | Risco | Ajude a equipe de adoção da nuvem a entender o impacto de riscos de negócios tangíveis. |
| Avalie | Confirmar | Revise e aprove o impacto nos negócios das alterações de arquitetura propostas. |
| Otimize | Alterar plano | Defina um plano para o consumo de alterações dentro da empresa, incluindo períodos de baixa atividade e alterações de congelamento. |
| Otimize | Testando | Alinhe os usuários avançados capazes de validar o desempenho e a funcionalidade. |
| Proteja e gerencie | Impacto da interrupção | Auxilie a equipe de adoção da nuvem a quantificar o impacto de uma interrupção do processo de negócios. |
| Proteja e gerencie | Validação de SLA (contrato de nível de serviço) | Auxilie a equipe de adoção da nuvem na definição de contratos de nível de serviço e tolerâncias aceitáveis para interrupções de negócios. |

Por fim, a equipe de adoção de nuvem é responsável por cada uma dessas atividades. No entanto, estabelecer responsabilidades e uma cadência regular com a empresa para a conclusão dessas atividades em um ritmo estabelecido pode melhorar o alinhamento de Stakeholder e cohesiveness com a empresa.

## <a name="common-roles-and-responsibilities"></a>Funções e responsabilidades comuns

Cada processo na discussão sobre os princípios de migração da estrutura de adoção da nuvem inclui um artigo de processo que descreve atividades específicas para alinhar funções e responsabilidades. Para maior clareza durante a execução, uma única pessoa responsável pela conta deve ser atribuída a cada atividade, juntamente com as partes responsáveis necessárias para dar suporte a essas atividades. No entanto, a lista a seguir contém uma série de funções e responsabilidades comuns que têm um nível mais alto de impacto na execução da migração. Essas funções devem ser identificadas no início do esforço de migração.

> [!NOTE]
> Na tabela a seguir, uma parte que pode ser acessada deve iniciar o alinhamento das funções. Essa coluna deve ser personalizada para ajustar os processos existentes para execução eficiente. Idealmente, uma única pessoa deve ser nomeada como a parte responsável pela conta.

| Processo | Atividade | Descrição | Parte da conta |
|---------|---------|---------|---------|
| Pré-requisito | Espaço digital | Alinhe o inventário existente a pressuposições básicas, com base nos resultados de negócios. | Equipe de estratégia de nuvem |
| Pré-requisito | Pendências de migração | Priorize a sequência de cargas de trabalho a serem migradas. | Equipe de estratégia de nuvem |
| Avalie | Arquitetura | Suposições iniciais de desafio para definir a arquitetura de destino com base nas métricas de uso. | Equipe de adoção de nuvem |
| Avalie | Automática | Aprove a arquitetura proposta. | Equipe de estratégia de nuvem |
| Migre | Acesso à replicação | Acesso a hosts e ativos locais existentes para estabelecer processos de replicação. | Equipe de adoção de nuvem |
| Otimize | Preparado | Valide se o sistema atende aos requisitos de desempenho e custo antes da promoção. | Equipe de adoção de nuvem |
| Otimize | Promover | Permissões para promover uma carga de trabalho para produção e redirecionar o tráfego de produção. | Equipe de adoção de nuvem |
| Proteja e gerencie | Transição do Ops | Documente os sistemas de produção antes das operações de produção. | Equipe de adoção de nuvem |

> [!CAUTION]
> Para essas atividades, as permissões e a autorização influenciam muito a parte responsável, que deve ter acesso direto aos sistemas de produção no ambiente existente ou deve ter meios de proteger o acesso por meio de outros atores responsáveis. Determinar essa parte da conta afeta diretamente a estratégia de promoção durante os processos de migração e otimização.

## <a name="next-steps"></a>Próximos passos

Quando a equipe tem uma compreensão geral das funções e responsabilidades, é hora de começar a preparar os detalhes técnicos da migração. Compreender a [complexidade técnica e o gerenciamento de alterações](./technical-complexity.md) pode ajudar a preparar a equipe de adoção da nuvem para a complexidade técnica da migração alinhando-se a um processo de gerenciamento de alterações incremental.

> [!div class="nextstepaction"]
> [Complexidade técnica e gerenciamento de alterações](./technical-complexity.md)
