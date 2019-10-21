---
title: Instruções de política de exemplo de aceleração de implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instruções de política de exemplo de aceleração de implantação
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c713af7557760d0bafeabf9d0cd0ef37a3885fe4
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547758"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Instruções de política de exemplo de aceleração de implantação

As instruções de política de nuvem individuais são diretrizes para tratar de riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções devem fornecer um resumo conciso de riscos e planos para lidar com eles. Cada definição de instrução deve incluir essas informações:

- **Risco técnico.** Um resumo do risco que essa política abordará.
- **Declaração de política.** Uma explicação resumida clara dos requisitos de política.
- **Opções de design.** Recomendações, especificações ou outras diretrizes acionáveis que as equipes de ti e os desenvolvedores podem usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à configuração comum. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dependência de implantação manual ou configuração de sistemas

**Risco técnico:** Depender de intervenção humana durante a implantação ou configuração aumenta a probabilidade de erro humano e reduz a possibilidade de repetição e previsibilidade de implantações e configurações do sistema. Normalmente, ele também leva à implantação mais lenta dos recursos do sistema.

**Declaração de política:** Todos os ativos implantados na nuvem devem ser implantados usando modelos ou scripts de automação sempre que possível.

**Opções de design potenciais:** [modelos de Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/template-deployment-overview) fornece uma abordagem de infraestrutura como código para implantar seus recursos no Azure. Você também pode usar o [Terraform](https://docs.microsoft.com/azure/terraform/terraform-overview) como uma ferramenta de implantação consistente local e baseada em nuvem.

## <a name="lack-of-visibility-into-system-issues"></a>Falta de visibilidade em problemas do sistema

**Risco técnico:** O monitoramento e o diagnóstico insuficientes para sistemas de negócios impedem que a equipe de operações identifique e corrija problemas antes que ocorra uma interrupção do sistema e possa aumentar significativamente o tempo necessário para resolver corretamente uma interrupção.

**Declaração de política:** As seguintes políticas serão implementadas:

- As métricas-chave e as medidas de diagnóstico serão identificadas para todos os sistemas e componentes de produção, e as ferramentas de monitoramento e diagnóstico serão aplicadas a esses sistemas e monitoradas regularmente pelo pessoal de operações.
- As operações considerarão o uso de ferramentas de monitoramento e diagnóstico em ambientes de não produção, como preparo e QA, para identificar problemas do sistema antes que eles ocorram no ambiente de produção.

**Opções de design potenciais:** [Azure monitor](https://docs.microsoft.com/azure/azure-monitor), que também inclui log Analytics e Application insights, fornece ferramentas para coletar e analisar a telemetria para ajudá-lo a entender como seus aplicativos estão sendo executados e proativamente identificar problemas que os afetam e os recursos dos quais eles dependem. Além disso, o [log de atividades do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) relata todas as alterações que estão sendo feitas no nível da plataforma e deve ser monitorado/auditado quanto a alterações não compatíveis.

## <a name="configuration-security-reviews"></a>Revisões de segurança de configuração

**Risco técnico:** Ao longo do tempo, novas ameaças à segurança ou preocupações podem aumentar os riscos de acesso não autorizado a recursos seguros.

**Declaração de política:** Os processos de governança de nuvem devem incluir a análise mensal com as equipes de gerenciamento de configuração para identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativos de nuvem.

**Possíveis opções de design:** Estabeleça uma reunião de revisão de segurança mensal que inclua membros da equipe de governança e a equipe de ti responsáveis por aplicativos e recursos de nuvem de configuração. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política e nas ferramentas de aceleração de implantação atuais, e atualize a política para corrigir quaisquer riscos novos.

## <a name="next-steps"></a>Próximos passos

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que atendam a riscos de negócios específicos que se alinham com seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas ao gerenciamento de identidade, baixe o [modelo de linha de base de identidade](../identity-baseline/template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Aproveitando os riscos e a tolerância, estabeleça um processo para controlar e comunicar a adesão da política de aceleração de implantação.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
