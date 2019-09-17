---
title: Declarações da política de amostra de Consistência de Recursos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Declarações da política de amostra de Consistência de Recursos
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 654ec56f2196af4d16b3e19a47ae117b9936b38f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029522"
---
# <a name="resource-consistency-sample-policy-statements"></a>Declarações da política de amostra de Consistência de Recursos

Declarações da política de nuvem individuais são diretrizes para tratar de riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que esta política abordará.
- **Instrução da política:** Uma clara explicação de resumo dos requisitos de política.
- **Opções de design:** Recomendações viáveis, especificações ou outras diretrizes que as equipes de TI e desenvolvedores possam usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos comerciais comuns relacionados à consistência de recursos. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="tagging"></a>Marcação

**Risco técnico:** Sem a marcação de metadados adequada associada aos recursos implantados, as operações de TI não podem priorizar o suporte ou a otimização de recursos com base no SLA exigido, a importância das operações de negócios ou o custo operacional. Isso pode resultar em alocação incorreta de recursos de TI e possíveis atrasos na resolução de incidentes.

**Instrução da política:** As políticas a seguir serão implementadas:

- Os ativos implantados devem ser marcados com os seguintes valores:
  - Custo
  - Importância
  - SLA
  - Ambiente
- O conjunto de ferramentas de governança deve validar a marcação relacionada ao custo, criticidade, SLA, aplicativo e ambiente. Todos os valores devem ser alinhados a valores predefinidos gerenciados pela equipe de governança.

**Possíveis opções de design:** No Azure, as [marcas de metadados de nome-valor padrão](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) são compatíveis com a maioria dos tipos de recursos. O [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) é usado para impor marcas específicas como parte da criação de recursos.

## <a name="ungoverned-subscriptions"></a>Assinaturas sem governança

**Risco técnico:** A criação arbitrária de assinaturas e grupos de gerenciamento poderá resultar em seções isoladas da propriedade de nuvem que não estejam devidamente sujeitas às políticas de governança.

**Instrução da política:** A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos exigirá uma análise da equipe de governança de nuvem. As alterações aprovadas serão integradas em uma atribuição de blueprint adequada.

**Possíveis opções de design:** Restrinja o acesso administrativo aos [Grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups) da sua organização apenas para os membros da equipe de governança aprovados que controlarão o processo de criação de assinatura e controle de acesso.

## <a name="manage-updates-to-virtual-machines"></a>Gerenciar atualizações para máquinas virtuais

**Risco técnico:** VMs (máquinas virtuais) que não estejam atualizadas com as atualizações e correções de software mais recentes ficarão vulneráveis a problemas de segurança ou desempenho, o que poderá resultar em interrupções de serviço.

**Instrução da política:** O conjunto de ferramentas de governança deve garantir que as atualizações automáticas estejam habilitadas em todas as VMs implantadas. As violações devem ser analisadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Ativos que não são atualizados automaticamente devem ser incluídos nos processos pertencentes às Operações de TI.

**Possíveis opções de design:** Para VMs hospedadas no Azure, é possível fornecer gerenciamento de atualização consistente usando a [solução de Gerenciamento de Atualizações na Automação do Azure](https://docs.microsoft.com/azure/automation/automation-update-management).

## <a name="deployment-compliance"></a>Conformidade de implantação

**Risco técnico:** Scripts de implantação e ferramentas de automação que não são totalmente verificadosdos pela equipe de governança de nuvem podem resultar em implantações de recursos que violam a política.

**Instrução da política:** As políticas a seguir serão implementadas:

- As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
- Os scripts de implantação devem ser mantidos no repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.

**Possíveis opções de design:** O uso consistente do [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints) para gerenciar implantações automatizadas permite implantações consistentes de recursos do Azure que aderem aos padrões e políticas de governança da sua organização.

## <a name="monitoring"></a>Monitorando

**Risco técnico:** O monitoramento instrumentado de forma incorreta ou inconsistente pode impedir a detecção de problemas de integridade da carga de trabalho ou outras violações de conformidade com a política.

**Instrução da política:** As políticas a seguir serão implementadas:

- As ferramentas de governança devem validar que todos os ativos relacionados a aplicativos críticos ou dados protegidos sejam incluídos no monitoramento para otimização e degradação de recursos.
- As ferramentas de governança devem validar se o nível apropriado de dados de registro em log está sendo coletado para todos os aplicativos críticos ou dados protegidos.

**Possíveis opções de design:** [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) é o serviço de monitoramento padrão no Azure, e o monitoramento consistente pode ser imposto por meio de [plantas do Azure](https://docs.microsoft.com/azure/governance/blueprints) ao implantar recursos.

## <a name="disaster-recovery"></a>Recuperação de desastres

**Risco técnico:** Falhas, exclusões ou corrupção de recursos podem resultar na interrupção de serviços ou aplicativos críticos e na perda de dados confidenciais.

**Instrução da política:** Todos os aplicativos críticos e dados protegidos devem ter soluções de backup e recuperação implementadas para minimizar o impacto nos negócios decorrente de interrupções ou falhas do sistema.

**Possíveis opções de design:** O serviço [Azure Site Recovery] fornece recursos de backup, recuperação e replicação destinados a minimizar a duração da interrupção em cenários de BCDR (Continuidade dos Negócios e Recuperação de Desastres).

## <a name="next-steps"></a>Próximas etapas

Use as amostras mencionadas neste artigo como ponto de partida para desenvolver políticas que abordem os riscos empresariais específicos que alinham-se aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias declarações da política personalizadas relacionadas à Consistência de Recursos, baixe o [modelo de Consistência de Recursos](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Compilar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a adesão à política de Consistência de Recursos.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
