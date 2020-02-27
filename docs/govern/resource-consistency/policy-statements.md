---
title: Declarações da política de amostra de Consistência de Recursos
description: Use a estrutura de adoção de nuvem do Azure para obter instruções de exemplo de política de consistência de recursos que ajudarão você a rascunhar as instruções de política da sua organização.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4222639ddb82da88cc95600ad2c6731b541f9f35
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708131"
---
# <a name="resource-consistency-sample-policy-statements"></a>Declarações da política de amostra de Consistência de Recursos

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que essa política abordará.
- **Declaração de política:** Uma explicação resumida clara dos requisitos de política.
- **Opções de design:** Recomendações, especificações ou outras diretrizes acionáveis que as equipes de ti e os desenvolvedores podem usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos comerciais comuns relacionados à consistência de recursos. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="tagging"></a>Marcação

**Risco técnico:** Sem a marcação de metadados adequada associada a recursos implantados, as operações de ti não podem priorizar o suporte ou a otimização de recursos com base no SLA necessário, na importância das operações de negócios ou no custo operacional. Isso pode resultar em alocação incorreta de recursos de TI e possíveis atrasos na resolução de incidentes.

**Declaração de política:** As seguintes políticas serão implementadas:

- Os ativos implantados devem ser marcados com os seguintes valores:
  - Custo
  - Importância
  - Contrato de Nível de Serviço
  - Ambiente
- O conjunto de ferramentas de governança deve validar a marcação relacionada ao custo, criticidade, SLA, aplicativo e ambiente. Todos os valores devem ser alinhados a valores predefinidos gerenciados pela equipe de governança.

**Possíveis opções de design:** No Azure, as [marcas de metadados de valor de nome padrão](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) têm suporte na maioria dos tipos de recursos. O [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) é usado para impor marcas específicas como parte da criação de recursos.

## <a name="ungoverned-subscriptions"></a>Assinaturas sem governança

**Risco técnico:** A criação arbitrária de assinaturas e grupos de gerenciamento pode levar a seções isoladas do seu estado de nuvem que não estão sujeitos corretamente às suas políticas de governança.

**Declaração de política:** A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos exigirá uma análise da equipe de governança de nuvem. As alterações aprovadas serão integradas em uma atribuição de blueprint adequada.

**Possíveis opções de design:** Bloqueie o acesso administrativo aos grupos de [Gerenciamento do Azure](https://docs.microsoft.com/azure/governance/management-groups) de suas organizações para apenas os membros da equipe de governança aprovados que controlarão a criação da assinatura e o processo de controle de acesso.

## <a name="manage-updates-to-virtual-machines"></a>Gerenciar atualizações para máquinas virtuais

**Risco técnico:** As máquinas virtuais (VMs) que não estão atualizadas com as atualizações e os patches de software mais recentes estão vulneráveis a problemas de segurança ou desempenho, o que pode resultar em interrupções de serviço.

**Declaração de política:** As ferramentas de governança devem impor que as atualizações automáticas estejam habilitadas em todas as VMs implantadas. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Ativos que não são atualizados automaticamente devem ser incluídos nos processos pertencentes às Operações de TI.

**Possíveis opções de design:** Para VMs hospedadas no Azure, você pode fornecer gerenciamento de atualizações consistente usando a [solução gerenciamento de atualizações na automação do Azure](https://docs.microsoft.com/azure/automation/automation-update-management).

## <a name="deployment-compliance"></a>Conformidade de implantação

**Risco técnico:** Scripts de implantação e ferramentas de automação que não são totalmente verificadosdos pela equipe de governança de nuvem podem resultar em implantações de recursos que violam a política.

**Declaração de política:** As seguintes políticas serão implementadas:

- As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
- Os scripts de implantação devem ser mantidos no repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.

**Possíveis opções de design:** O uso consistente de [plantas do Azure](https://docs.microsoft.com/azure/governance/blueprints) para gerenciar implantações automatizadas permite implantações consistentes de recursos do Azure que aderem aos padrões e às políticas de governança de sua organização.

## <a name="monitoring"></a>Monitoramento

**Risco técnico:** O monitoramento instrumentado incorretamente ou inconsistente pode impedir a detecção de problemas de integridade da carga de trabalho ou outras violações de conformidade de política.

**Declaração de política:** As seguintes políticas serão implementadas:

- As ferramentas de governança devem validar que todos os ativos estão incluídos no monitoramento de esgotamento de recursos, segurança, conformidade e otimização.
- As ferramentas de governança devem validar se o nível apropriado de dados de log está sendo coletado para todos os aplicativos e dados.

**Opções de design em potencial:** [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) é o serviço de monitoramento padrão no Azure, e o monitoramento consistente pode ser imposto por meio de [plantas do Azure](https://docs.microsoft.com/azure/governance/blueprints) ao implantar recursos.

## <a name="disaster-recovery"></a>Recuperação de desastre

**Risco técnico:** Falhas de recursos, exclusões ou danos podem resultar em interrupção de aplicativos ou serviços de missão crítica e perda de dados confidenciais.

**Declaração de política:** Todos os aplicativos de missão crítica e dados protegidos devem ter soluções de backup e recuperação implementadas para minimizar o impacto nos negócios de interrupções ou falhas do sistema.

**Possíveis opções de design:** O serviço de [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) fornece recursos de backup, recuperação e replicação que minimizam a duração da interrupção nos cenários de continuidade dos negócios e recuperação de desastres (BCDR).

## <a name="next-steps"></a>Próximas etapas

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que abordam os riscos de negócios específicos que se alinham aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias declarações da política personalizadas relacionadas à Consistência de Recursos, baixe o [modelo de Consistência de Recursos](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Compilar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a adesão à política de Consistência de Recursos.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
