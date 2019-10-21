---
title: 'Guia de governança para empresas complexas: melhorar a disciplina de gerenciamento de custos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: melhorar a disciplina de gerenciamento de custos'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3a6e2effbd47c3516e3663d3c0f1f75d9db924e8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547696"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-cost-management-discipline"></a>Guia de governança para empresas complexas: melhorar a disciplina de gerenciamento de custos

Este artigo avança na narração adicionando controles de custo à governança mínima do MVP (produto viável).

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A adoção cresceu além do indicador de tolerância definido no MVP de governança. Os aumentos de gastos agora justificam um investimento de tempo da equipe de governança de nuvem para monitorar e controlar os padrões de gastos.

Como um driver claro de inovação, ele não é mais visto principalmente como um centro de custo. À medida que a organização de ti oferece mais valor, o CIO e o CFO concordam que o tempo é o mais adequado para mudar a função que ele desempenha na empresa. Entre outras alterações, o CFO deseja testar uma abordagem de pagamento direto para a contabilidade de nuvem para a ramificação canadense de uma das unidades de negócios. Um dos dois data centers desativados foi exclusivamente hospedado em ativos para as operações canadenses da unidade de negócios. Nesse modelo, a subsidiária canadense da unidade de negócios será cobrada diretamente pelas despesas operacionais relacionadas aos ativos hospedados. Esse modelo permite que ele se concentre menos no gerenciamento de gastos de outra pessoa e muito mais na criação de valor. No entanto, antes que essa transição possa começar, as ferramentas de gerenciamento de custos precisam estar em vigor.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narração, a equipe de ti estava movendo ativamente as cargas de trabalho de produção com dados protegidos no Azure.

Desde então, algumas coisas mudaram que afetarão a governança:

- 5\.000 os ativos foram removidos dos dois data centers sinalizados para aposentadoria. A aquisição e a segurança de ti agora estão Desprovisionando os ativos físicos restantes.
- As equipes de desenvolvimento de aplicativos implementaram pipelines de CI/CD para implantar alguns aplicativos nativos de nuvem, afetando significativamente as experiências do cliente.
- A equipe de BI criou processos de agregação, de coleta, de Insight e de previsão que conduzem benefícios tangíveis para operações de negócios. Essas previsões agora estão capacitando novos produtos e serviços criativos.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

O monitoramento de custos e os relatórios devem ser adicionados à solução de nuvem. Os relatórios devem ligar as despesas operacionais diretas às funções que estão consumindo os custos de nuvem. Relatórios adicionais devem permitir que ele monitore gastos e forneça orientações técnicas sobre o gerenciamento de custos. Para a ramificação canadense, o departamento será cobrado diretamente.

## <a name="changes-in-risk"></a>Alterações em risco

**Controle de orçamento:** Há um risco inerente de que os recursos de autoatendimento resultarão em custos excessivos e inesperados na nova plataforma. Os processos de governança para monitorar custos e reduzir os riscos de custo contínuo devem estar em vigor para garantir o alinhamento contínuo com o orçamento planejado.

Esse risco comercial pode ser expandido em alguns riscos técnicos:

- Há um risco de os custos reais excederem o plano.
- As condições de negócios mudam. Quando isso ocorrer, haverá casos em que uma função comercial precisa consumir mais serviços de nuvem do que o esperado, levando a um gasto de anomalias. Há um risco de que esses custos adicionais sejam considerados excedentes em oposição a um ajuste necessário para o plano. Se for bem-sucedido, o experimento canadense deverá ajudar a corrigir esse risco.
- Há um risco de os sistemas serem excessivamente provisionados, resultando em excesso de gastos.

## <a name="changes-to-the-policy-statements"></a>Alterações nas instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- Todos os custos de nuvem devem ser monitorados em relação ao plano semanalmente pela equipe de governança de nuvem. O relatório sobre desvios entre os custos de nuvem e o plano é ser compartilhado com liderança de ti e Finanças mensais. Todos os custos de nuvem e atualizações de plano devem ser analisados com a liderança de ti e Finanças mensais.
- Todos os custos devem ser alocados a uma função comercial para fins de responsabilidade.
- Os ativos de nuvem devem ser continuamente monitorados para oportunidades de otimização.
- As ferramentas de governança de nuvem devem limitar as opções de dimensionamento de ativos a uma lista de configurações aprovadas. As ferramentas devem garantir que todos os ativos sejam detectáveis e acompanhados pela solução de monitoramento de custos.
- Durante o planejamento da implantação, todos os recursos de nuvem necessários associados à Hospedagem de cargas de trabalho de produção devem ser documentados. Esta documentação ajudará a refinar os orçamentos e a preparar ferramentas de automação adicionais para evitar o uso de opções mais caras. Durante essa consideração de processo deve ser dada a diferentes ferramentas de descontação oferecidas pelo provedor de nuvem, como instâncias reservadas ou reduções de custo de licença.
- Todos os proprietários de aplicativos são obrigados a participar de práticas para otimizar as cargas de trabalho para controlar melhor os custos de nuvem.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhorará o design do MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas duas alterações de design atenderão às novas instruções de política corporativa.

1. Faça alterações na Enterprise Portal do Azure para cobrar o administrador do departamento pela implantação canadense.
2. Implemente o gerenciamento de custos do Azure.
    1. Estabeleça o nível certo de escopo de acesso para alinhar com o padrão de assinatura e o padrão de agrupamento de recursos. Supondo que o alinhamento com o MVP de governança definido nos artigos anteriores, isso exigiria o acesso ao **escopo da conta de registro** para a equipe de governança de nuvem em execução em relatórios de alto nível. Equipes adicionais fora do controle, como a equipe de compras canadense, exigirão acesso ao **escopo do grupo de recursos** .
    2. Estabeleça um orçamento no gerenciamento de custos do Azure.
    3. Examine e aja sobre as recomendações iniciais. É recomendável ter um processo recorrente para dar suporte ao processo de relatório.
    4. Configure e execute relatórios de gerenciamento de custos do Azure, tanto iniciais quanto recorrentes.
3. Atualizar Azure Policy.
    1. Marcação de auditoria, grupo de gerenciamento, assinatura e valores de grupo de recursos para identificar qualquer desvio.
    2. Estabeleça opções de tamanho de SKU para limitar as implantações a SKUs listadas na documentação de planejamento de implantação.

## <a name="conclusion"></a>Conclusão

Adicionar os processos acima e as alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados ao controle de custos. Juntos, eles criam a visibilidade, a responsabilidade e a otimização necessárias para controlar os custos.

## <a name="next-steps"></a>Próximos passos

À medida que a adoção de nuvem cresce e fornece valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para essa empresa fictícia, a próxima etapa é usar esse investimento de governança para gerenciar várias nuvens.

> [!div class="nextstepaction"]
> [Melhoria em nuvem](./multicloud-improvement.md)
