---
title: Instruções de política de exemplo de Aceleração de implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instruções de política de exemplo de Aceleração de implantação
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4a2b1666332ca884dfb95b2b2372f3b5518bd635
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028490"
---
# <a name="deployment-acceleration-sample-policy-statements"></a>Instruções de política de exemplo de Aceleração de implantação

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico.** Um resumo do risco que esta política abordará.
- **Instrução da política.** Uma clara explicação de resumo dos requisitos de política.
- **Opções de design.** Recomendações viáveis, especificações ou outras diretrizes que as equipes de TI e desenvolvedores possam usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à configuração comum. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de ti e de negócios para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="reliance-on-manual-deployment-or-configuration-of-systems"></a>Dependência de implantação manual ou configuração de sistemas

**Risco técnico:** Depender de intervenção humana durante a implantação ou configuração aumenta a probabilidade de erro humano e reduz a capacidade de repetição e a previsibilidade de implantações de sistema e de configuração. Isso normalmente também leva a implantação mais lenta de recursos do sistema.

**Instrução da política:** Todos os ativos implantados na nuvem devem ser implantados usando modelos ou scripts de automação sempre que possível.

**Possíveis opções de design:** [Modelos do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#template-deployment) fornecem uma abordagem de infraestrutura como código para implantar seus recursos no Azure. Os [Blocos de Construção do Azure](https://github.com/mspnp/template-building-blocks/wiki) fornecem uma ferramenta de linha de comando e o conjunto de modelos do Gerenciador de Recursos projetados para simplificar a implantação de recursos do Azure.

## <a name="lack-of-visibility-into-system-issues"></a>Falta de visibilidade em problemas de sistema

**Risco técnico:** Monitoramento e diagnóstico insuficientes para sistemas de negócios impedem a equipe de operações de identificação e correção de problemas antes de uma interrupção do sistema ocorrer e poder aumentar significativamente o tempo necessário para resolver corretamente uma interrupção.

**Instrução da política:** As políticas a seguir serão implementadas:

- Medidas métricas principais e diagnósticos serão identificadas para todos os sistemas de produção e os componentes e ferramentas de diagnóstico e monitoramento serão aplicados a esses sistemas e monitorados regularmente pela equipe de operações.
- As operações considerarão o uso de ferramentas de monitoramento e diagnóstico em ambientes de não produção, como preparo e QA, para identificar problemas do sistema antes que eles ocorram no ambiente de produção.

**Possíveis opções de design:** [O Azure Monitor](https://docs.microsoft.com/azure/azure-monitor), que inclui também o Log Analytics e o Application Insights fornece ferramentas para coletar e analisar a telemetria para ajudar você a entender como estão o desempenho de seus aplicativos e identificar proativamente os problemas afetando-os e os recursos que eles dependem.

## <a name="configuration-security-reviews"></a>Revisões de segurança de configuração

**Risco técnico:** Ao longo do tempo, novas ameaças à segurança ou preocupações podem aumentar os riscos de acesso não autorizado para proteger os recursos.

**Instrução da política:** Os processos de governança de nuvem devem incluir revisão trimestral com as equipes de gerenciamento de configuração para identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativo de nuvem.

**Possíveis opções de design:** Estabeleça uma reunião de revisão trimestral de segurança que inclui membros da equipe de governança e a equipe de TI responsáveis por recursos e aplicativos de nuvem de configuração. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política e nas ferramentas de aceleração de implantação atuais, e atualize a política para corrigir quaisquer riscos novos.

## <a name="next-steps"></a>Próximas etapas

Use os exemplos mencionados neste artigo como um ponto de partida para desenvolver políticas que abordam os riscos de negócios específicos que se alinham aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas ao gerenciamento de identidade, baixe o [modelo de Linha de base de identidade](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Compilar riscos e tolerância, estabelecer um processo para administrar e comunicar a aderência da política de aceleração de implantação.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
