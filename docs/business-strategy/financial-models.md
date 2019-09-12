---
title: Criar um modelo financeiro para a transformação de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como criar um modelo financeiro para a transformação de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 60d49cbb970b5fd20512e342961284115dbef984
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825101"
---
# <a name="create-a-financial-model-for-cloud-transformation"></a>Criar um modelo financeiro para a transformação de nuvem

A criação de um modelo financeiro que representa com precisão o valor comercial total de uma transformação de nuvem pode ser complicado. Os modelos financeiros e as justificativas de negócios tendem a variar para diferentes organizações. Este artigo estabelece algumas fórmulas e indica algumas coisas que normalmente são perdidas quando os estrategista cria modelos financeiros.

## <a name="return-on-investment"></a>Retorno do investimento

O ROI (retorno sobre o investimento) geralmente é um critério importante para o C-Suite ou para o quadro. ROI é usado para comparar as diferentes maneiras de se investir recursos de capital limitados. A fórmula do ROI é bastante simples. Os detalhes necessários para criar cada entrada para a fórmula podem não ser tão simples. Essencialmente, ROI é o valor de retorno produzido por um investimento inicial. Geralmente é representado como uma porcentagem:

![ROI Equals (obter do investimento menos o custo de investimento) dividido por custo de investimento](../_images/formula-roi.png)

Nas próximas seções, veremos os dados que você precisará para calcular o investimento inicial e o ganho de investimento (ganhos).

## <a name="calculating-initial-investment"></a>Calculando o investimento inicial

O investimento inicial é a despesa de capital e as despesas operacionais necessárias para concluir uma transformação. A classificação dos custos pode variar dependendo dos modelos de contabilidade e da preferência do diretor financeiro. Mas essa categoria inclui itens como serviços profissionais para transformar, licenças de software usadas somente durante a transformação, o custo dos serviços de nuvem durante a transformação e, potencialmente, o custo de funcionários com salários durante a transformação .

Adicione esses custos para criar uma estimativa do investimento inicial.

## <a name="calculating-the-gain-from-investment"></a>Calculando o ganho com o investimento

Calcular o lucro do investimento geralmente requer uma segunda fórmula específica para os resultados de negócios e as alterações técnicas associadas. Calcular os ganhos é mais difícil do que calcular as reduções de custos.

Para calcular os ganhos, você precisa de duas variáveis:

![Obter do investimento igual a deltas de receita, além de deltas de custo](../_images/formula-gain-from-investment.png)

Essas variáveis são descritas nas seções a seguir.

## <a name="revenue-deltas"></a>Deltas de receita

Os deltas de receita devem ser uma previsão em parceria com os participantes comerciais. Depois que os participantes da empresa concordarem em um impacto de receita, ele poderá ser usado para melhorar a posição de conquista.

## <a name="cost-deltas"></a>Deltas de custo

Os deltas de custo são a quantidade de aumento ou diminuição que serão causados pela transformação. Variáveis independentes podem afetar os deltas de custo. Os ganhos baseiam-se principalmente em custos tangíveis, como reduções de despesas de capital, provisões, reduções de custos operacionais e reduções de depreciação. As seções a seguir descrevem alguns deltas de custo a serem considerados.

### <a name="depreciation-reduction-or-acceleration"></a>Redução ou aceleração da depreciação

Para obter orientação sobre depreciação, fale com o diretor financeiro ou com a equipe financeira. As informações a seguir destinam-se a servir como uma referência geral sobre o tópico de depreciação.

Quando o capital é investida na aquisição de um ativo, esse investimento poderia ser usado para fins financeiros ou tributários a fim de produzir benefícios contínuos ao longo do tempo de vida esperado do ativo. Algumas empresas veem depreciação como uma vantagem tributária positiva. Outros veem isso como uma despesa confirmada e contínua semelhante a outras despesas recorrentes atribuídas ao orçamento de ti anual.

Fale com o escritório financeiro para descobrir se a eliminação de depreciação é possível e se ela fará uma contribuição positiva para os deltas de custo.

### <a name="physical-asset-recovery"></a>Recuperação de ativos físicos

Em alguns casos, os ativos desativados podem ser vendidos como uma fonte de receita. Essa receita costuma ser contratada em redução de custos para simplificação. Mas é realmente um aumento na receita e pode ser tributada como tal. Fale com o departamento financeiro para compreender a viabilidade dessa opção e como levar em conta a receita resultante.

### <a name="operational-cost-reductions"></a>Reduções de custo operacional

As despesas recorrentes necessárias para operar uma empresa geralmente são chamadas de despesas operacionais. Essa é uma categoria ampla. Na maioria dos modelos de contabilidade, ele inclui:

- Licenciamento de software.
- Despesas de hospedagem.
- Faturas elétricas.
- Locações de imóveis.
- Despesas de resfriamento.
- Equipe temporária necessária para operações.
- Locações de equipamentos.
- Peças de substituição.
- Contratos de manutenção.
- Reparar serviços.
- Continuidade dos negócios e serviços de recuperação de desastre (BCDR).
- Outras despesas que não exigem aprovações de despesas de capital.

Essa categoria fornece um dos deltas de maior conquista. Quando você está considerando uma migração na nuvem, o tempo investido para tornar essa lista exaustiva é raramente desperdiçado. Pergunte ao CIO e às perguntas da equipe de Finanças para garantir que todos os custos operacionais sejam contabilizados.

### <a name="cost-avoidance"></a>Prevenção de custos

Quando uma despesa operacional é esperada, mas ainda não está em um orçamento aprovado, ela pode não caber em uma categoria de redução de custo. Por exemplo, se as licenças do VMware e da Microsoft precisam ser renegociadas e pagas no próximo ano, elas ainda não são custos totalmente qualificados. As reduções nesses custos esperados são tratadas como os custos operacionais para fins de cálculos de Delta de custo. No entanto, informalmente eles devem ser chamados de "redução de custos" até que a negociação e a aprovação do orçamento sejam concluídas.

### <a name="soft-cost-reductions"></a>Reduções de custo flexível

Em algumas empresas, os custos flexíveis, como reduções na complexidade operacional ou reduções na equipe de tempo integral para operar um datacenter, também podem ser incluídos em deltas de custo. Mas incluir custos flexíveis pode não ser uma boa ideia. Quando você inclui reduções de custo flexível, insere uma suposição não documentada de que a redução criará uma economia de custo tangível. Os projetos de tecnologia raramente resultam em uma recuperação de custo flexível real.

### <a name="headcount-reductions"></a>Reduções do número de funcionários

A economia de tempo para a equipe costuma ser incluída na redução de custos flexíveis. Quando essas economias de tempo são mapeadas para a redução real do salário de ti ou da equipe, elas podem ser calculadas separadamente como reduções de funcionários.

Dito isso, as habilidades necessárias no local geralmente são mapeadas para um conjunto semelhante (ou de nível superior) de habilidades necessárias na nuvem. Portanto, as pessoas geralmente não são dispostas após uma migração na nuvem.

Uma exceção ocorre quando a capacidade operacional é fornecida por terceiros ou por um provedor de serviços gerenciados (MSP). Se os sistemas de ti forem gerenciados por terceiros, os custos operacionais poderão ser substituídos por uma solução nativa de nuvem ou MSP nativo de nuvem. Um MSP nativo de nuvem provavelmente operará com mais eficiência e, potencialmente, com um custo menor. Se esse for o caso, as reduções de custos operacionais pertencerão aos cálculos de custo rígido.

### <a name="capital-expense-reductions-or-avoidance"></a>Reduções de despesas de capital ou provisão

As despesas de capital são um pouco diferentes das despesas operacionais. Em geral, essa categoria é orientada pela expansão do datacenter ou pelos ciclos de atualização. Um exemplo de expansão de datacenter seria um novo cluster de alto desempenho para hospedar uma solução de Big Data ou data warehouse. Essa despesa geralmente se encaixa em uma categoria de despesas de capital. Os ciclos de atualização básicos são mais comuns. Algumas empresas têm ciclos de atualização de hardware rígidos, o que significa que os ativos são descontinuados e substituídos em um ciclo regular (geralmente a cada três, cinco ou oito anos). Esses ciclos geralmente coincidem com os ciclos de concessão de ativos ou com o período de vida previsto da previsão. Quando um ciclo de atualização atinge, ele consome despesas de capital para adquirir novos equipamentos.

Se um ciclo de atualização for aprovado e orçado, a transformação de nuvem poderá ajudar a eliminar esse custo. Se um ciclo de atualização estiver planejado, mas ainda não tiver sido aprovado, a transformação de nuvem poderá evitar uma despesa de capital. Ambas as reduções seriam adicionadas ao Delta de custo.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre os modelos de [contabilidade de nuvem](./cloud-accounting.md) .

> [!div class="nextstepaction"]
> [Contabilidade de nuvem](./cloud-accounting.md)
