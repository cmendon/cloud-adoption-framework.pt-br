---
title: Pré-requisitos para a migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Pré-requisitos para a migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ce4cf827f391c5fb15f6b9e78997dd0f02e1751b
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683790"
---
# <a name="prerequisites-for-migration"></a>Pré-requisitos para migração

Antes de começar as migrações, seu _ambiente_ de destino de migração deve estar preparado para alterações futuras. Nesse caso, ambiente refere-se à base técnica na nuvem. Ambiente também significa o ambiente empresarial e a atitude que impulsiona a migração. Da mesma forma, ambiente inclui a cultura das equipes que executam as alterações e aquelas que recebem o resultado. Falta de preparação para essas alterações é o motivo mais comum para falha de migrações. Esta série de artigos descreverá os pré-requisitos sugeridos para preparar o ambiente.

## <a name="objective"></a>Objetivo

Garanta preparação técnica, cultural e empresarial antes de iniciar um plano de migração iterativo.

## <a name="review-business-drivers"></a>Examine os condutores empresariais

Antes de iniciar qualquer migração na nuvem, examine a orientação para [Planejar](../../../strategy/index.md) e ficar [Pronto](../../../ready/index.md) na Cloud Adoption Framework para garantir que sua organização esteja preparada para os processos de migração e adoção da nuvem. Em particular, examine os requisitos empresariais e os resultados esperados que conduzem a migração:

- [Introdução: migração](../../../getting-started/migrate.md)
- [Por que estamos migrando para a nuvem?](../../../strategy/motivations.md)

## <a name="definition-of-done"></a>Definição de *concluído*

Os pré-requisitos estão concluídos quando o seguinte é verdadeiro:

- **Preparação empresarial.** A equipe de estratégia de nuvem definiu e priorizou uma lista de pendências de migração de alto nível que representa a parte do acervo digital a ser migrada nas próximas duas ou três versões. A equipe de estratégia de nuvem e a equipe de adoção de nuvem concordaram com uma estratégia inicial para o gerenciamento de alteração.
- **Preparação do Azure.** As funções, as responsabilidades e as expectativas da equipe de adoção de nuvem, da equipe de estratégia de nuvem e dos usuários afetados foram acordadas com relação às cargas de trabalho a serem migradas nas próximas duas ou três versões.
- **Preparação técnica.** A zona de aterrissagem (ou o espaço alocado de hospedagem na nuvem) que receberá os ativos migrados cumpre os requisitos mínimos para hospedar a primeira carga de trabalho migrada.

> [!CAUTION]
> Preparação é o segredo para o sucesso da migração. No entanto, preparação demais pode causar *paralisia de análise*, em que tempo demais dedicado ao planejamento pode atrasar seriamente um esforço de migração. Os processos e pré-requisitos definidos nesta seção destinam-se a ajudá-lo a tomar decisões, mas não deixe que o impeçam de fazer progresso significativo.
>
> Escolha uma carga de trabalho relativamente simples para a sua migração inicial. Use os processos abordados nesta seção ao planejar e implementar essa migração primeiro. Esse primeiro esforço de migração demonstrará rapidamente os princípios de nuvem para sua equipe e a forçará a aprender mais sobre como a nuvem funciona. Conforme sua equipe adquire experiência, integre esses aprendizados ao assumir migrações cada vez maiores e mais complexas.

## <a name="accountability-during-prerequisites"></a>Responsabilidade durante os pré-requisitos

Duas equipes são responsáveis pela preparação durante a fase de pré-requisitos:

- **Equipe de estratégia de nuvem:** Essa equipe é responsável por identificar e priorizar as primeiras duas ou três cargas de trabalho para servir como candidatas à migração.
- **Equipe de adoção de nuvem:** Essa equipe é responsável por validar a preparação do ambiente técnico e a viabilidade de migrar as cargas de trabalho propostas.

Um único membro de cada equipe deve ser identificado como responsável por cada uma das três definições de instruções concluídas na seção anterior.

## <a name="responsibilities-during-prerequisites"></a>Responsabilidades durante os pré-requisitos

Além da responsabilidade de alto nível, há ações pelas quais uma pessoa ou grupo precisa ser diretamente responsável. A seguir estão algumas dessas responsabilidades que afetam essas atividades:

- **Priorização empresarial.** Tome decisões empresariais sobre as cargas de trabalho a serem migradas e as restrições de tempo gerais. Para obter mais informações, veja [Motivações empresariais da migração na nuvem](../../../strategy/motivations.md).
- **Prontidão para gerenciamento de alterações.** Estabeleça e comunique o plano para acompanhar alterações técnicas durante a migração.
- **Alinhamento de usuário empresarial.** Estabeleça um plano para preparar a comunidade de usuários empresariais para a execução da migração.
- **Inventário e análise do acervo digital.** Execução das ferramentas necessárias para inventariar e analisar o acervo digital. Confira a discussão do Cloud Adoption Framework sobre a [propriedade digital](../../../digital-estate/index.md) para obter mais informações.
- **Preparação para a nuvem.** Avalie o ambiente de implantação de destino para garantir que ele esteja em conformidade com os requisitos dos primeiros candidatos da carga de trabalho. Confira o [guia de configuração do Azure](../../../ready/azure-setup-guide/index.md) para obter mais informações.

Os artigos restantes desta série ajudam na execução de cada um.

## <a name="next-steps"></a>Próximas etapas

Com uma compreensão geral dos pré-requisitos, você está pronto para tratar do primeiro pré-requisito, [decisões iniciais de migração](./decisions.md).

> [!div class="nextstepaction"]
> [Decisões iniciais de migração](./decisions.md)
