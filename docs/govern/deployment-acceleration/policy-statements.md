---
title: Instruções de política de exemplo de Aceleração de implantação
description: Instruções de política de exemplo de Aceleração de implantação
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c582b0a6e836f5198724e5675840f3f8085f55dc
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76803935"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Instruções de política de exemplo de Aceleração de implantação

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que essa política abordará.
- **Declaração de política:** Uma explicação resumida clara dos requisitos de política.
- **Opções de design:** Recomendações, especificações ou outras diretrizes acionáveis que as equipes de ti e os desenvolvedores podem usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à configuração comum. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dependência de implantação manual ou configuração de sistemas

**Risco técnico:** Depender de intervenção humana durante a implantação ou configuração aumenta a probabilidade de erro humano e reduz a possibilidade de repetição e previsibilidade de implantações e configurações do sistema. Isso normalmente também leva a implantação mais lenta de recursos do sistema.

**Declaração de política:** Todos os ativos implantados na nuvem devem ser implantados usando modelos ou scripts de automação sempre que possível.

**Opções de design potenciais:** [modelos de Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) fornece uma infraestrutura como abordagem de código para implantar seus recursos no Azure. Você também pode usar o [Terraform](https://docs.microsoft.com/azure/terraform/terraform-overview) como uma ferramenta de implantação consistente local e baseada em nuvem.

## <a name="lack-of-visibility-into-system-issues"></a>Falta de visibilidade em problemas de sistema

**Risco técnico:** O monitoramento e o diagnóstico insuficientes para sistemas de negócios impedem que a equipe de operações identifique e corrija problemas antes que ocorra uma interrupção do sistema e possa aumentar significativamente o tempo necessário para resolver corretamente uma interrupção.

**Declaração de política:** As seguintes políticas serão implementadas:

- Medidas métricas principais e diagnósticos serão identificadas para todos os sistemas de produção e os componentes e ferramentas de diagnóstico e monitoramento serão aplicados a esses sistemas e monitorados regularmente pela equipe de operações.
- As operações considerarão o uso de ferramentas de monitoramento e diagnóstico em ambientes de não produção, como preparo e QA, para identificar problemas do sistema antes que eles ocorram no ambiente de produção.

**Opções de design em potencial:** [Azure monitor](https://docs.microsoft.com/azure/azure-monitor), que inclui log Analytics e Application insights, fornece ferramentas para coletar e analisar a telemetria para ajudá-lo a entender como seus aplicativos estão executando e identificar proativamente os problemas que os afetam e os recursos dos quais eles dependem. Além disso, o [log de atividades do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) relata todas as alterações que estão sendo feitas no nível da plataforma e deve ser monitorado e auditado quanto a alterações não compatíveis.

## <a name="configuration-security-reviews"></a>Revisões de segurança de configuração

**Risco técnico:** Ao longo do tempo, novas ameaças à segurança ou preocupações podem aumentar os riscos de acesso não autorizado a recursos seguros.

**Declaração de política:** Os processos de governança de nuvem devem incluir a análise mensal com as equipes de gerenciamento de configuração para identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativos de nuvem.

**Possíveis opções de design:** Estabeleça uma reunião de revisão de segurança mensal que inclua membros da equipe de governança e a equipe de ti responsáveis por aplicativos e recursos de nuvem de configuração. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política e nas ferramentas de aceleração de implantação atuais, e atualize a política para corrigir quaisquer riscos novos.

## <a name="next-steps"></a>Próximos passos

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que abordam os riscos de negócios específicos que se alinham aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas ao gerenciamento de identidade, baixe o [modelo de Linha de base de identidade](../identity-baseline/template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Compilar riscos e tolerância, estabelecer um processo para administrar e comunicar a aderência da política de aceleração de implantação.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
