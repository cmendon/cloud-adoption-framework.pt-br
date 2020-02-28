---
title: Indicadores e métricas de tolerância a riscos de aceleração de implantação
description: Use a estrutura de adoção de nuvem para o Azure para quantificar a tolerância a riscos de negócios relacionada à aceleração da implantação.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 83772d82d6f439bcd25382e21738ed01ef411596
ms.sourcegitcommit: 10637acba8c857a6f5aa8c4a80c0649903f60402
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78170946"
---
# <a name="deployment-acceleration-metrics-indicators-and-risk-tolerance"></a>Métricas de Aceleração de Implantação, indicadores e tolerância a riscos

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com a aceleração da implantação. Definir métricas e indicadores ajuda a criar um caso de negócios para fazer um investimento no amadurecimento da disciplina de Aceleração de Implantação.

## <a name="metrics"></a>Métricas

A disciplina de aceleração da implantação se concentra em riscos relacionados à forma como os recursos de nuvem são configurados, implantados, atualizados e mantidos. As informações a seguir são úteis ao adotar essa disciplina de governança de nuvem:

- **Falhas de implantação:** Percentual de implantações que falham ou resultam em recursos mal configurados.
- **Tempo para implantação:** A quantidade de tempo necessária para implantar atualizações em um sistema existente.
- **Ativos fora de conformidade:** O número ou o percentual de recursos que estão fora de conformidade com políticas definidas.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

Os riscos relacionados à aceleração de implantação em grande parte são relacionados ao número e a complexidade dos sistemas baseados em nuvem implantados para sua empresa. À medida em que a sua propriedade de nuvem cresce, o número de sistemas implantados e a frequência de atualização dos seus recursos aumentarão. As dependências entre recursos ampliarão a importância de garantir a configuração adequada de recursos e a criação de sistemas para resiliência se um ou mais recurso apresentar tempo de inatividade inesperado.

<!-- "en-us" location is required for the URL below. -->

As organizações tradicionais de ti corporativas geralmente têm equipes de operações, segurança e desenvolvimento em silos que, em geral, não colaboram bem ou são ainda antagônicos ou hostis em direção umas às outras. Reconhecer esses desafios no início e integrar os principais stakeholders de cada uma das equipes pode ajudar a garantir a agilidade na sua adoção da nuvem permanecendo seguro e bem governado. Portanto, deve-se considerar a adoção de uma cultura organizacional DevOps ou [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) no início da sua jornada de adoção de nuvem.

Trabalhe com a sua equipe DevSecOps e com os stakeholders da empresa para identificar os [riscos de negócios](./business-risks.md) relacionados à configuração, em seguida, determine uma linha de base aceitável para tolerância a riscos de configuração. Esta seção das diretrizes da estrutura de adoção de nuvem fornece exemplos, mas os riscos e as linhas de base detalhados para sua empresa ou implantações provavelmente serão diferentes.

Assim que você tiver uma linha de base, estabeleça parâmetros de comparação mínimos que representem um aumento inaceitável em seus riscos identificados. Esses benchmarks atuam como gatilhos para quando você precisa tomar medidas para corrigir esses riscos. A seguir, há alguns exemplos de como métricas relacionadas à configuração, como as discutidas anteriormente, podem justificar o aumento de investimento na disciplina de Aceleração de implantação.

- **Gatilhos de descompasso de configuração:** Uma empresa que está apresentando alterações inesperadas na configuração dos principais componentes do sistema, ou falhas na implantação ou atualizações em seus sistemas, deve investir na disciplina de aceleração da implantação para identificar as causas e as etapas de correção.
- **Disparadores de conformidade insuficientes:** Se o número de recursos fora de conformidade exceder um limite definido (como um número total de recursos ou uma porcentagem do total de recursos), uma empresa deverá investir em melhorias na disciplina de aceleração de implantação para garantir que a configuração de cada recurso permaneça em conformidade durante todo o ciclo de vida do recurso.
- **Gatilhos de agenda do projeto:** Se o tempo para implantar os recursos e aplicativos da empresa geralmente exceder um limite definido, uma empresa deverá investir em seus processos de aceleração de implantação para introduzir ou aprimorar implantações automatizadas para consistência e previsibilidade. Tempos de implantação, medidos em dias ou até mesmo semanas geralmente indicam uma estratégia de implantação de aceleração abaixo do ideal.

## <a name="next-steps"></a>Próximas etapas

Usar o [modelo de Gerenciamento de Nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.

Examine as políticas de aceleração de implantação de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos comerciais específicos que se alinham com seus planos de adoção de nuvem.

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
