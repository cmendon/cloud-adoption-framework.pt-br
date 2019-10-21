---
title: Aperfeiçoamento da disciplina de consistência de recursos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aperfeiçoamento da disciplina de consistência de recursos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9d465716784d125edebaf44d8a1bae2f369b9d5a
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548090"
---
# <a name="resource-consistency-discipline-improvement"></a>Aperfeiçoamento da disciplina de consistência de recursos

A disciplina de consistência de recursos concentra-se em maneiras de estabelecer políticas relacionadas ao gerenciamento operacional de um ambiente, aplicativo ou carga de trabalho. Dentro das cinco disciplinas de governança de nuvem, a consistência de recursos inclui o monitoramento do desempenho do aplicativo, da carga de trabalho e do ativo. Ele também inclui as tarefas necessárias para atender às demandas de escala, corrigir violações de Contrato de Nível de Serviço de desempenho (SLA) e evitar proativamente violações de SLA por meio de correção automatizada.

Este artigo descreve algumas tarefas potenciais pelas quais sua empresa pode se envolver para desenvolver melhor e amadurecer a disciplina de consistência de recursos. Essas tarefas podem ser divididas em fases de planejamento, criação, adoção e operação de implementação de uma solução de nuvem, que são então iteradas para permitir o desenvolvimento de uma [abordagem incremental para governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

É impossível para qualquer documento considerar os requisitos de todas as empresas. Como tal, este artigo descreve as atividades de exemplo mínimas e potenciais do sugerido para cada fase do processo de desenvolvimento de governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de consistência de recursos.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Estas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento dos dois requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Essa fase de maturidade de governança preenche a divisão entre resultados de negócios e estratégias acionáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas para o espaço digital e começa a planejar o esforço geral de migração.

**Mínimo de atividades sugeridas:**

- Avalie as opções de [ferramentas de consistência do recurso](./toolchain.md) .
- Entenda os requisitos de licenciamento para sua estratégia de nuvem.
- Desenvolva um documento de diretrizes de arquitetura de rascunho e distribua para as principais partes interessadas.
- Familiarize-se com o Gerenciador de recursos que você usa para implantar, gerenciar e monitorar todos os recursos de sua solução como um grupo.
- Instrua e envolva as pessoas e equipes afetadas pelo desenvolvimento de diretrizes de arquitetura.
- Adicione tarefas de implantação de recursos priorizadas à sua pendência de migração.

**Atividades potenciais:**

- Trabalhe com os acionistas de negócios e sua equipe de estratégia de nuvem para entender a abordagem de contabilidade de nuvem desejada e as práticas de contabilização de custos em suas unidades de negócios e organização como um todo.
- Defina os requisitos de [monitoramento e de imposição de políticas](./compliance-processes.md) .
- Examine o valor comercial e o custo da interrupção para definir a política de correção e os requisitos de SLA.
- Determine se você implantará uma [carga de trabalho simples](./governance-simple-workload.md) ou várias estratégias de governança de [equipe](./governance-multiple-teams.md) para seus recursos.
- Determine os requisitos de escalabilidade para suas cargas de trabalho planejadas.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

Vários pré-requisitos técnicos e não técnicos são necessários para migrar um ambiente com êxito. Esse processo concentra-se nas decisões, prontidão e infraestrutura básica que prosseguem com uma migração.

**Mínimo de atividades sugeridas:**

- Implemente seu [ferramentas de consistência de recursos](./toolchain.md) ao distribuir em uma fase de pré-implantação.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Implemente tarefas de implantação de recursos em sua pendência de migração priorizada.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar a adoção do usuário.

**Atividades potenciais:**

- Decida sobre uma [estratégia de design de assinatura](../../decision-guides/subscriptions/index.md), escolhendo os padrões de assinatura que melhor se ajustam à sua organização e às suas necessidades de carga de trabalho.
- Use uma estratégia de [consistência de recursos](../../decision-guides/resource-consistency/index.md) para impor diretrizes de arquitetura ao longo do tempo.
- Implemente a [nomenclatura de recursos e os padrões de marcação](../../decision-guides/resource-tagging/index.md) para seus recursos de acordo com seus requisitos organizacionais e de contabilidade.
- Para criar uma governança proativa pontual, use modelos de implantação e automação para impor configurações comuns e uma estrutura de agrupamento consistente ao implantar recursos e grupos de recursos.
- Estabeleça um modelo de permissões de privilégios mínimos, em que os usuários não têm permissões por padrão.
- Determine quem em sua organização possui cada carga de trabalho e conta e quem precisará acessar para manter ou modificar esses recursos. Defina funções de nuvem e responsabilidades que correspondam a essas necessidades e use essas funções como base para o controle de acesso.
- Defina as dependências entre os recursos.
- Implemente o dimensionamento automático de recursos para atender aos requisitos definidos no estágio do plano.
- Conduza o desempenho de acesso para medir a qualidade dos serviços recebidos.
- Considere implantar a [política](https://docs.microsoft.com/azure/governance/policy/overview) para gerenciar a imposição de SLA usando definições de configuração e regras de criação de recursos.

## <a name="adopt-and-migrate"></a>Adote e migre

A migração é um processo incremental que se concentra na movimentação, no teste e na adoção de aplicativos ou cargas de trabalho em um espaço digital existente.

**Mínimo de atividades sugeridas:**

- Migre seu [ferramentas de consistência de recursos](./toolchain.md) da pré-implantação para a produção.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar a adoção do usuário.
- Migre quaisquer ferramentas ou scripts de correção automatizados existentes para dar suporte aos requisitos de SLA definidos.

**Atividades potenciais:**

- Conclua e teste os dados de monitoramento e relatório com o seu local, o gateway de nuvem ou a solução híbrida escolhida.
- Determine se as alterações precisam ser feitas no SLA ou política de gerenciamento para recursos.
- Aprimore as tarefas de operações implementando recursos de consulta para localizar com eficiência recursos em todo o seu estado de nuvem.
- Alinhe os recursos às necessidades de negócios e aos requisitos de governança em constante mudança.
- Certifique-se de que suas máquinas virtuais, redes virtuais e contas de armazenamento reflitam as necessidades de acesso a recursos reais durante cada versão e ajuste conforme necessário.
- Verifique se o dimensionamento automático de recursos atende aos requisitos de acesso.
- Examine o acesso do usuário a recursos, grupos de recursos e assinaturas do Azure e ajuste os controles de acesso conforme necessário.
- Monitore as alterações nos planos de acesso aos recursos e valide-as com as partes interessadas se forem necessárias aprovações adicionais.
- Atualize as alterações no documento de diretrizes de arquitetura para refletir os custos reais.
- Determine se sua organização requer um alinhamento financeiro mais claro para P & ls para unidades de negócios.
- Para organizações globais, implemente seus requisitos de conformidade do SLA ou da soberania.
- Para a agregação de nuvem, implante uma solução de gateway em um provedor de nuvem.
- Para ferramentas que não permitem opções híbridas ou de gateway, o monitoramento está rigidamente acoplado com uma ferramenta de monitoramento operacional que abrange todos os data centers e nuvens.

## <a name="operate-and-post-implementation"></a>Operar e pós-implementação

Depois que a transformação for concluída, a governança e as operações deverão residir para o ciclo de vida natural de um aplicativo ou carga de trabalho. Essa fase de maturidade de governança se concentra nas atividades que normalmente vêm depois que a solução é implementada e o ciclo de transformação começa a estabilizar.

**Mínimo de atividades sugeridas:**

- Personalize seu [ferramentas de consistência de recursos](./toolchain.md) com base nas atualizações de acordo com as necessidades de gerenciamento de custos de sua organização.
- Considere automatizar notificações e relatórios para refletir o uso real de recursos.
- Refine as diretrizes de arquitetura para orientar processos futuros de adoção.
- Instrua as equipes afetadas periodicamente para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Ajuste os planos trimestral para refletir as alterações nos recursos reais.
- Aplicar e impor automaticamente os requisitos de governança durante implantações futuras.
- Avalie os recursos subutilizados e determine se vale a pena continuar.
- Detectar inalinhamentos e anomalias entre o uso de recursos planejado e real.
- Auxilie as equipes de adoção da nuvem e a equipe de estratégia de nuvem em entender e resolver essas anomalias.
- Determine se as alterações precisam ser feitas à consistência de recursos para cobrança e SLAs.
- Avalie as ferramentas de log e monitoramento para determinar se sua solução local, de gateway de nuvem ou híbrida precisa ser ajustada.
- Para unidades de negócios e grupos distribuídos geograficamente, determine se a sua organização deve considerar o uso de recursos adicionais de gerenciamento de nuvem, como [grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups) , para aplicar melhor a política centralizada e atender aos requisitos de SLA.

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu o conceito de governança de recursos de nuvem, vá para saiba mais sobre [como o acesso aos recursos é gerenciado](./resource-access-management.md) no Azure em preparação para aprender a criar um modelo de governança para uma [carga de trabalho simples](./governance-simple-workload.md) ou para [várias equipes](./governance-multiple-teams.md) .

> [!div class="nextstepaction"]
> [Saiba mais sobre o gerenciamento de acesso a recursos no azure](./resource-access-management.md) 
> [saiba mais sobre os contratos de nível de serviço para o Azure](https://azure.microsoft.com/support/legal/sla) 
> [saiba mais sobre registro em log, relatórios e monitoramento](../../decision-guides/logging-and-reporting/index.md)
