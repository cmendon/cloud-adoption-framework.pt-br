---
title: 'Guia empresarial Standard: Melhorar a disciplina de gerenciamento de custos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia empresarial Standard: Melhorar a disciplina de gerenciamento de custos'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 078d484becaf62cd07ec124d818891c8a52b8dbc
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908794"
---
# <a name="standard-enterprise-guide-improve-the-cost-management-discipline"></a>Guia empresarial Standard: Melhorar a disciplina de gerenciamento de custos

Este artigo avança na narração adicionando controles de custo ao MVP de governança.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A adoção ultrapassou o indicador de tolerância de custo definido na governança MVP. Isso é bom, pois corresponde às migrações do datacenter “DR”. O aumento dos gastos agora justifica um investimento de tempo da equipe de governança de nuvem.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior a essa narrativa, a TI havia desativado 100% do data center de recuperação de Desastre. As equipes de BI e o desenvolvimento de aplicativos estavam prontos para o tráfego de produção.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- A equipe de migração começou migrando as VMs fora do datacenter de produção.
- As equipes de desenvolvimento de aplicativo estão enviando ativamente por push a aplicativos de produção para a nuvem por meio de pipelines de CI/CD. Esses aplicativos de forma reativa podem dimensionar com demandas de usuário.
- A equipe de business intelligence dentro dela forneceu várias ferramentas de análise preditiva na nuvem. Os volumes de dados agregados na nuvem continuam a crescer.
- Todo esse crescimento oferece suporte aos resultados de negócios comprometidos. No entanto, os custos começaram a crescer. Orçamentos projetados estão crescendo mais rapidamente do que o esperado. O CFO precisa de abordagens aprimoradas para gerenciamento de custos.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

O custo de monitoramento e a emissão de relatórios deve ser adicionado à solução de nuvem. A TI ainda está atuando como uma casa de compensação de custo. Isso significa que o pagamento para serviços de nuvem continua a vir de pagamento da TI. No entanto, os relatórios devem ligar as despesas operacionais diretas às funções que estão consumindo os custos de nuvem. Esse modelo é conhecido como um modelo de contabilidade de nuvem "Mostrar" de volta.

As alterações ao estado atual e futuro expõem novos riscos que exigem novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Controle de orçamento:** Há um risco inerente que recursos de autoatendimento resultarão em custos excessivos e inesperados na nova plataforma. Processos de governança para monitorar os custos e minimizar os riscos de custo contínuo devem estar em vigor para garantir o alinhamento contínuo com o orçamento planejado.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

- Os custos reais podem exceder o plano.
- As condições de negócios mudam. Quando isso acontece, haverá casos quando uma função de negócios precisa consumir mais serviços de nuvem que o esperado, gerando anomalias de gastos. Há um risco de que esses gastos extras sejam considerados excedentes, em vez de um ajuste necessário para o plano.
- Sistemas poderiam ser sobreprovisionados, resultando em excesso de gastos.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- Todos os custos de nuvem devem ser monitorados em relação ao plano semanalmente pela equipe de governança. Relatório sobre desvios entre os custos de nuvem e o plano devem compartilhados com a liderança de TI e finanças mensalmente. Todos os custos de nuvem e as atualizações de plano devem ser revisados com a liderança de TI e finanças mensalmente.
- Todos os custos devem ser alocados para uma função de negócios para fins de responsabilidade.
- Os ativos de nuvem devem ser monitorados continuamente para oportunidades de otimização.
- As ferramentas de governança de nuvem devem limitar as opções de dimensionamento de ativos a uma lista de configurações aprovadas. A ferramenta deve garantir que todos os ativos sejam detectáveis e controlados pelo custo de solução de monitoramento.
- Durante o planejamento da implantação, os recursos de nuvem necessários associados à hospedagem de cargas de trabalho de produção devem ser documentados. Esta documentação ajudará a refinar os orçamentos e preparar automação adicional para evitar o uso das opções mais caras. Durante esse processo, a consideração deve ser dada a diferentes ferramentas de descontos oferecidos pelo provedor de nuvem, como instâncias reservadas ou reduções de custo de licença.
- Todos os aplicativos proprietários são necessários para participar de treinamentos sobre práticas para otimizar cargas de trabalho para melhor controlar os custos da nuvem.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

1. Implemente o Gerenciamento de Custos do Azure.
    1. Estabelecer o escopo correto de acesso para se alinhar ao padrão de assinatura e a disciplina de Consistência de recursos. Supondo que o alinhamento com o MVP de governança definido nos artigos anteriores, isso requer acesso ao **escopo da conta de registro** para a equipe de governança de nuvem em execução em relatórios de alto nível. Equipes adicionais fora de governança podem exigir acesso ao **Escopo do Grupo de Recursos**.
    1. Estabelecer um orçamento no Gerenciamento de Custos do Azure.
    1. Examinar e agir em recomendações iniciais. Ter um processo recorrente para oferecer suporte a relatórios.
    1. Configurar e executar Relatórios de Gerenciamento de Custos do Azure, tanto iniciais como recorrentes.
2. Atualizar o Azure Policy
    1. Auditar a marcação, grupo de gerenciamento, assinatura e valores de grupo de recursos para identificar qualquer desvio.
    1. Estabeleça as opções de tamanho de SKU para limitar as implantações para SKUs listadas na documentação de planejamento de implantação.

## <a name="conclusion"></a>Conclusão

Adicionar esses processos e alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados ao controle de custos. Juntos, criam a visibilidade, a responsabilidade e a otimização necessárias para controlar os custos.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para a empresa fictícia neste guia, a próxima etapa é usar esse investimento de governança para gerenciar várias nuvens.

> [!div class="nextstepaction"]
> [Evolução em nuvem](./multicloud-evolution.md)
