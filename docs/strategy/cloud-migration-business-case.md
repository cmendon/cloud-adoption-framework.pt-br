---
title: Criar uma justificativa de negócios para a migração de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Considerações ao criar uma justificativa comercial para a migração para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 055c50ca2a934000b7e8d11927bc5ba1d4f95494
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026462"
---
# <a name="build-a-business-justification-for-cloud-migration"></a>Criar uma justificativa de negócios para a migração de nuvem

As migrações para a nuvem podem gerar retorno sobre o investimento (ROI) antecipado de iniciativas de transformação de nuvem. Mas desenvolver uma justificativa de negócios clara com custos tangíveis e relevantes e Devoluções pode ser um processo complexo. Este artigo o ajudará a pensar em quais dados você precisa para criar um modelo financeiro que se alinhe aos resultados da migração na nuvem. Primeiro, vamos eliminar alguns mitos sobre a migração para a nuvem, para que sua organização possa evitar alguns erros comuns.

## <a name="dispelling-cloud-migration-myths"></a>Dissipando mitos sobre a migração para a nuvem

**Mito: a nuvem sempre é mais barata.** Normalmente, acredita-se que operar um datacenter na nuvem é sempre mais barato do que operar um no local. Embora essa suposição geralmente seja verdadeira, nem sempre é o caso. Às vezes, os custos operacionais de nuvem são maiores. Esses custos mais altos geralmente são causados por controle de baixo custo, arquiteturas de sistema desalinhadas, duplicação de processo, configurações do sistema atípicos ou maior custo de equipe. Felizmente, você pode mitigar muitos desses problemas para criar um ROI inicial. Seguir as diretrizes de [criação da justificativa de negócios](#building-the-business-justification) pode ajudá-lo a detectar e evitar esses inalinhamentos. A grafia dos outros mitos descritos aqui também pode ajudar.

**Mito: tudo deve ir para a nuvem.** Na verdade, alguns drivers de negócios podem levá-lo a escolher uma solução híbrida. Antes de finalizar um modelo de negócios, é inteligente concluir uma análise quantitativa de primeira rodada, conforme descrito nos artigos de [imóveis digitais](../digital-estate/5-rs-of-rationalization.md). Para obter mais informações sobre os drivers quantitativos individuais envolvidos na racionalização, consulte [o 5 RS de racionalização](../digital-estate/5-rs-of-rationalization.md). As duas abordagens usarão dados de inventário obtidos facilmente e uma breve análise quantitativa para identificar as cargas de trabalho ou aplicativos que poderiam resultar em custos mais altos na nuvem. Essas abordagens também podem identificar dependências ou padrões de tráfego que exigiriam uma solução híbrida.

**Mito: o espelhamento do meu ambiente local me ajudará a economizar dinheiro na nuvem.** Durante o planejamento de imóveis digitais, não é despercebido que as empresas detectem capacidade não utilizada de mais de 50% do ambiente provisionado. Se os ativos forem provisionados na nuvem para corresponder ao provisionamento atual, será difícil perceber as economias de custos. Considere reduzir o tamanho dos ativos implantados para alinhar com padrões de uso em vez de padrões de provisionamento.

**Mito: Os custos do servidor impulsionam casos comerciais para migração na nuvem.** Às vezes, essa suposição é verdadeira. Para algumas empresas, é importante reduzir as despesas de capital contínuas relacionadas aos servidores. Mas depende de vários fatores. Empresas com um ciclo de atualização de hardware de cinco anos a oito anos são improvável de ver retornos rápidos em sua migração de nuvem. As empresas com ciclos de atualização padronizados ou impostos podem zerar o custo rapidamente. Em ambos os casos, outras despesas podem ser os gatilhos financeiros que justificam a migração. Aqui estão alguns exemplos de custos que geralmente são ignorados quando as empresas usam uma exibição somente de servidor ou somente VM de custos:

- Os custos de software para virtualização, servidores e middleware podem ser extensivos. Os provedores de nuvem eliminam alguns desses custos. Dois exemplos de um provedor de nuvem que reduz os custos de virtualização são os [benefício híbrido do Azure](https://azure.microsoft.com/pricing/hybrid-benefit/#services) e os programas de [reservas do Azure](https://azure.microsoft.com/reservations) .
- As perdas de negócios causadas por interrupções podem exceder rapidamente os custos de hardware ou software. Se seu datacenter atual estiver instável, trabalhe com a empresa para quantificar o impacto de interrupções em termos de custos de oportunidades ou custos reais de negócios.
- Os custos ambientais também podem ser significativos. Para a família americana média, uma casa é o maior investimento e o custo mais alto no orçamento. O mesmo costuma ser verdadeiro para datacenters. Imóveis, instalações e custos com serviços essenciais representam uma parte importante dos custos locais. Quando os data centers são desativados, essas instalações podem ser realocadas ou sua empresa pode ser liberada por completo desses custos.

**Mito: Um modelo de despesa operacional é melhor do que um modelo de despesas de capital.** Conforme explicado no artigo [resultados fiscais](./business-outcomes/fiscal-outcomes.md) , um modelo de despesa operacional pode ser algo bom. Mas alguns setores exibem as despesas operacionais de forma negativa. Aqui estão alguns exemplos que disparariam uma integração mais rígida com as unidades de contabilidade e de negócios em relação à conversa de despesas operacionais:

- Quando uma empresa vê ativos de capital como um driver para a avaliação dos negócios, as reduções de despesas de capital podem ser um resultado negativo. Embora não seja um padrão universal, esse sentimentos é mais comumente visto nos setores de varejo, manufatura e construção.
- Uma firma de patrimônio particular ou uma empresa que está buscando um influxo de capital pode considerar as despesas operacionais aumentadas como um resultado negativo.
- Se um negócio se concentra muito em melhorar as margens de vendas ou reduzir o custo dos produtos vendidos (COGS), as despesas operacionais podem ser um resultado negativo.

É mais provável que as empresas vejam as despesas operacionais como mais favoráveis do que as despesas de capital. Por exemplo, essa abordagem pode ser bem recebida por empresas que estão tentando melhorar o fluxo de caixa, reduzir investimentos de capital ou diminuir as contenções de ativo.

Antes de fornecer uma justificativa de negócios que se concentre em uma conversão de despesas de capital para despesas operacionais, entenda o que é melhor para sua empresa. A contabilidade e a aquisição muitas vezes podem ajudar a alinhar a mensagem a objetivos financeiros.

**Mito: migrar para a nuvem é como apertar um botão.** As migrações são uma transformação técnica manualmente intensa. Ao desenvolver uma justificativa comercial, especialmente justificativas com prazos apertados, considere os seguintes aspectos que podem aumentar o tempo necessário para migrar ativos:

- **Limitações de largura de banda:** A quantidade de largura de banda entre o datacenter atual e o provedor de nuvem orientará as linhas do tempo durante a migração.
- **Testando linhas do tempo:** Testar aplicativos com a empresa para garantir a prontidão e o desempenho podem ser demorados. O alinhamento dos usuários avançados com os processos de teste é essencial.
- **Cronogramas de migração:** A quantidade de tempo e esforço necessários para implementar a migração pode aumentar os custos e causar atrasos. Alocar funcionários ou parceiros contratados também pode atrasar o processo. O plano deve considerar essas alocações.

Impedimentos técnicos e culturais podem reduzir a adoção da nuvem. Quando o tempo é um aspecto importante da justificativa comercial, a melhor mitigação é o planejamento adequado. Durante o planejamento, duas abordagens podem ajudar a reduzir os riscos da linha do tempo:

- Invista o tempo e a energia em Noções básicas sobre restrições de adoção técnica. Embora a pressão para se mover rapidamente possa ser alta, é importante considerar os cronogramas realistas.
- Se surgirem impedimentos culturais ou de pessoas, eles terão efeitos mais graves do que as restrições técnicas. A adoção da nuvem cria alterações, o que produz a transformação desejada. Infelizmente, às vezes as pessoas têm medo de alterar e podem precisar de suporte adicional para se alinharem com o plano. Identifique as principais pessoas da equipe que estão em oposição a mudar e contrate-las antecipadamente.

Para maximizar a prontidão e a mitigação de riscos no cronograma, prepare os stakeholders executivos alinhando claramente o valor comercial e os resultados comerciais. Ajude esses participantes a entender as alterações que serão fornecidas com a transformação. Seja claro e defina expectativas realistas desde o início. Quando as pessoas ou tecnologias diminuem o processo, será mais fácil inscrever o suporte executivo.

## <a name="building-the-business-justification"></a>Criar a justificativa comercial

O processo a seguir define uma abordagem para desenvolver a justificativa comercial para migrações para a nuvem. Para obter mais informações sobre os cálculos e os termos financeiros, consulte o artigo sobre [modelos financeiros](./financial-models.md).

De forma geral, a fórmula para a justificativa comercial é simples. Mas os pontos de dados sutis necessários para popular a fórmula podem ser difíceis de alinhar. Em um nível básico, a justificativa de negócios concentra-se no retorno do investimento (ROI) associado à mudança técnica proposta. A fórmula genérica para o ROI é:

![ROI Equals (obter do investimento menos o custo de investimento) dividido por custo de investimento](../_images/strategy/formula-roi.png)

Podemos desempacotar esta equação para obter uma exibição específica da migração das fórmulas para as variáveis de entrada no lado direito da equação. As seções restantes deste artigo oferecem algumas considerações para levar em conta.

## <a name="migration-specific-initial-investment"></a>Investimento inicial específico da migração

- Provedores de nuvem como o Azure oferecem calculadoras para estimar os investimentos em nuvem. A [calculadora de preços do Azure](https://azure.microsoft.com/pricing) é um exemplo.
- Alguns provedores de nuvem também fornecem calculadoras de custo-Delta. A [calculadora do custo total de propriedade (TCO) do Azure](https://azure.com/tco) é um exemplo.
- Para estruturas de custo mais refinadas, considere um exercício de [planejamento de imobiliária digital](../digital-estate/index.md) .
- Estime o custo da migração.
- Estime o custo das oportunidades de treinamento esperadas, se houver. [Microsoft Learn](/learn) talvez possa ajudar a mitigar esses custos.
- Em algumas empresas, o tempo investido por membros da equipe existentes pode precisar ser incluído nos custos iniciais. Consulte o departamento financeiro para obter diretrizes.
- Discuta custos adicionais ou indiretos com o departamento financeiro para validação.

## <a name="migration-specific-revenue-deltas"></a>Deltas de receita específicos da migração

Esse aspecto geralmente é ignorado por estrategistas criando uma justificativa de negócios para a migração. Em algumas áreas, a nuvem pode cortar custos. Mas o objetivo final de qualquer transformação é gerar resultados melhores ao longo do tempo. Considere os efeitos de downstream para entender os aprimoramentos de receita de longo prazo. Quais novas tecnologias estarão disponíveis para o seu negócio após a migração que não pode ser usada hoje? Quais projetos ou objetivos de negócios estão vetados pela dependência de tecnologias herdadas? Quais programas estão em espera, as despesas com alta capital pendentes para a tecnologia?

Depois de considerar as oportunidades desbloqueadas pela nuvem, trabalhe com a empresa para calcular os aumentos de receita que poderiam vir dessas oportunidades.

## <a name="migration-specific-cost-deltas"></a>Deltas de custo específicos da migração

Calcule todas as alterações nos custos que resultarão da migração proposta. Consulte o artigo [modelos financeiros](./financial-models.md) para obter detalhes sobre os tipos de deltas de custo. Os provedores de nuvem geralmente oferecem ferramentas para cálculos de custo-Delta. A [calculadora do custo total de propriedade (TCO) do Azure](https://azure.com/tco) é um exemplo.

Outros exemplos de custos que podem ser reduzidos por uma migração de nuvem:

- Rescisão ou redução do datacenter (custos ambientais)
- Redução no consumo de energia (custos ambientais)
- Encerramento de rack (recuperação de ativo físico)
- Eliminação de atualização de hardware (redução de custos)
- Prevenção de renovação de software (redução de custos operacionais ou eliminação de custos)
- Consolidação de fornecedor (redução de custos operacionais e redução de custos de software potencial)

## <a name="when-roi-results-are-surprising"></a>Quando os resultados do ROI são surpreendentes

Se o ROI de uma migração de nuvem não corresponder às suas expectativas, talvez você queira revisitar os mitos comuns listados no início deste artigo.

Mas é importante entender que uma economia de custos nem sempre é possível. Alguns aplicativos custam mais para operar na nuvem do que localmente. Esses aplicativos podem afetar significativamente os resultados em uma análise.

Quando o ROI está abaixo de 20%, considere um exercício de [planejamento de imóveis digitais](../digital-estate/index.md) , pagando atenção específica à [racionalização](../digital-estate/rationalize.md). Durante a análise quantitativa, examine cada aplicativo para localizar cargas de trabalho que distorcem os resultados. Pode fazer sentido remover essas cargas de trabalho do plano. Se houver dados de uso disponíveis, considere reduzir o tamanho das VMs para corresponder ao uso.

Se o ROI ainda estiver desalinhado, procure a ajuda de seu representante de vendas da Microsoft ou [entre em contato com um parceiro experiente](https://azure.microsoft.com/migration/support).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Criar um modelo financeiro para a transformação de nuvem](./financial-models.md)
