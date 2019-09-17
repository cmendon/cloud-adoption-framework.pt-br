---
title: 'Guia de governança para empresas complexas: Melhorar a disciplina de gerenciamento de custos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: Melhorar a disciplina de gerenciamento de custos'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: f8b78ab958f732920d7282ade80e9da421e5b0e5
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028486"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-cost-management-discipline"></a>Guia de governança para empresas complexas: Melhorar a disciplina de gerenciamento de custos

Este artigo avança na narração adicionando controles de custo à governança mínima do MVP (produto viável).

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A adoção ultrapassou o indicador de tolerância definido na governança MVP. Os aumentos de gastos agora justificam um investimento de tempo da equipe de governança de nuvem para monitorar e controlar os padrões de gastos.

Como um driver claro de inovação de, a IT não é mais vista principalmente como um centro de custo. À medida que a organização de ti oferece mais valor, o CIO e o CFO concordam que o tempo é o mais adequado para mudar a função que ele desempenha na empresa. Entre outras alterações, o diretor financeiro quer testar uma abordagem de pagamento direto para estatísticas para a filial canadense de uma das unidades de negócios na nuvem. Um dos dois datacenters obsoletos era exclusivamente ativos hospedados para essas operações canadenses da unidade comercial. Nesse modelo, a subsidiária canadense da unidade de negócios será cobrada diretamente pelas despesas operacionais relacionadas aos ativos hospedados. Esse modelo permite que ele se concentre menos no gerenciamento de gastos de outra pessoa e muito mais na criação de valor. No entanto, antes de começar essa transição, pode começar com as ferramentas do Gerenciamento de Custos necessárias no local.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior dessa narrativa, a equipe de TI foi ativamente movendo cargas de trabalho de produção com dados protegidos no Azure.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- 5\.000 ativos foram removidos de dois datacenters sinalizados para desativação. Aquisição e a segurança de TI estão agora desprovisionando os ativos físicos restantes.
- As equipes de desenvolvimento de aplicativos implementaram pipelines de CI/CD para implantar alguns aplicativos nativos de nuvem, afetando significativamente as experiências do cliente.
- A equipe de BI criou agregação, curadoria, insight e processos de previsão, levando benefícios tangíveis para operações de negócios. Essas previsões agora estão capacitando novos produtos e serviços criativos.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

O monitoramento de custos e os relatórios devem ser adicionados à solução de nuvem. Os relatórios devem ligar as despesas operacionais diretas às funções que estão consumindo os custos de nuvem. Outros tipos de relatório devem permitir que a TI monitore os gastos e forneça orientações técnicas sobre o gerenciamento de custos. Para a filial canadense, o departamento será cobrado diretamente.

## <a name="changes-in-risk"></a>Alterações em risco

**Controle de orçamento:** Há um risco inerente que recursos de autoatendimento resultarão em custos excessivos e inesperados na nova plataforma. Processos de governança para monitorar os custos e minimizar os riscos de custo contínuo devem estar em vigor para garantir o alinhamento contínuo com o orçamento planejado.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

- Há um risco dos custos reais que excedem o plano.
- As condições de negócios mudam. Quando isso acontece, haverá casos quando uma função de negócios precisa consumir mais serviços de nuvem que o esperado, gerando anomalias de gastos. Há um risco de que esses custos adicionais sejam considerados excedentes em oposição a um ajuste necessário para o plano. Se for bem-sucedido, o experimento canadense deverá ajudar a corrigir esse risco.
- Há um risco de sistemas que estão sendo sobre provisionados, resultando em excesso de gastos.

## <a name="changes-to-the-policy-statements"></a>Alterações nas instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- Todos os custos de nuvem devem ser monitorados em relação ao plano semanalmente pela equipe de governança de nuvem. Relatório sobre desvios entre os custos de nuvem e o plano devem compartilhados com a liderança de TI e finanças mensalmente. Todos os custos de nuvem e as atualizações de plano devem ser revisados com a liderança de TI e finanças mensalmente.
- Todos os custos devem ser alocados para uma função de negócios para fins de responsabilidade.
- Os ativos de nuvem devem ser monitorados continuamente para oportunidades de otimização.
- As ferramentas de governança de nuvem devem limitar as opções de dimensionamento de ativo para uma lista aprovada de configurações. A ferramenta deve garantir que todos os ativos sejam detectáveis e controlados pelo custo de solução de monitoramento.
- Durante o planejamento da implantação, os recursos de nuvem necessários associados à hospedagem de cargas de trabalho de produção devem ser documentados. Esta documentação ajudará a refinar os orçamentos e a preparar ferramentas de automação adicionais para evitar o uso de opções mais caras. Durante esse processo, a consideração deve ser dada a diferentes ferramentas de descontos oferecidos pelo provedor de nuvem, como Instâncias Reservadas ou reduções de custo de licença.
- Todos os aplicativos proprietários são necessários para participar de treinamentos sobre práticas para otimizar cargas de trabalho para melhor controlar os custos da nuvem.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhorará o design do MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

1. Faça alterações na Enterprise Portal do Azure para cobrar o administrador do departamento pela implantação canadense.
1. Implemente o Gerenciamento de Custos do Azure.
    1. Estabeleça o nível correto de acesso para se alinhar ao padrão de assinatura e ao padrão de agrupamento de recursos. Supondo que o alinhamento com o MVP de governança definido nos artigos anteriores, isso exigiria o acesso ao **escopo da conta de registro** para a equipe de governança de nuvem em execução em relatórios de alto nível. Equipes adicionais fora da governança, como a equipe de compras canadense, exigirá acesso ao **Escopo do Grupo de Recursos**.
    1. Estabelecer um orçamento no Gerenciamento de Custos do Azure.
    1. Examinar e agir em recomendações iniciais. É recomendável ter um processo recorrente para oferecer suporte ao processo de geração de relatórios.
    1. Configurar e executar Relatórios de Gerenciamento de Custos do Azure, tanto iniciais como recorrentes.
1. Atualize o Azure Policy.
    1. Audite a marcação, grupo de gerenciamento, assinatura e valores de grupo de recursos para identificar qualquer desvio.
    1. Estabeleça as opções de tamanho de SKU para limitar as implantações para SKUs listadas na documentação de planejamento de implantação.

## <a name="conclusion"></a>Conclusão

Adicionar os processos acima e as alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados ao controle de custos. Juntos, criam a visibilidade, a responsabilidade e a otimização necessárias para controlar os custos.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem cresce e fornece valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para essa empresa fictícia, a próxima etapa é usar esse investimento de governança para gerenciar várias nuvens.

> [!div class="nextstepaction"]
> [Melhoria em nuvem](./multicloud-improvement.md)
