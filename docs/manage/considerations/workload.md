---
title: Operações de carga de trabalho – gerenciamento de nuvem e operações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Operações de carga de trabalho – gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5f250362e93a81c6bb38ef11e8659484ef023182
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683727"
---
# <a name="workload-operations-in-cloud-management"></a>Operações de carga de trabalho no gerenciamento de nuvem

Algumas cargas de trabalho são críticas para o sucesso dos negócios. Para essas cargas de trabalho, uma linha de base de gerenciamento não é suficiente para atender aos compromissos de negócios necessários para o gerenciamento de nuvem. As operações de plataforma podem nem mesmo ser suficientes para atender aos compromissos de negócios. Esse subconjunto altamente importante de cargas de trabalho requer um foco especializado na maneira como as funções de carga de trabalho e como há suporte.

Em retorno, o investimento em operações de carga de trabalho pode levar a um desempenho aprimorado, menor risco de interrupção dos negócios e recuperação mais rápida quando ocorrem falhas do sistema. Este artigo orientará uma abordagem para investir nas operações contínuas dessas cargas de trabalho de alta prioridade para impulsionar os compromissos comerciais aprimorados.

## <a name="when-to-invest-in-workload-operations"></a>Quando investir em operações de carga de trabalho

O princípio de Pareto (também conhecido como a regra 80/20) afirma que 80% dos efeitos vêm de 20% das causas. Quando os portfólios de ti têm permissão para aumentar a orgânicamente ao longo do tempo, essa regra normalmente pode ser vista em uma análise do portfólio de ti. Dependendo do efeito que exige investimento, a causa pode variar, mas o princípio geral se aplica a verdadeiro:

- 80% das falhas do sistema tendem a ser o resultado de 20% dos erros ou bugs comuns
- 80% do valor comercial tende a vir de 20% das cargas de trabalho em um portfólio
- 80% do esforço para migrar para a nuvem vem de 20% das cargas de trabalho que estão sendo movidas
- 80% dos esforços de gerenciamento de nuvem dará suporte a 20% dos incidentes de serviço ou tíquetes de problema
- 80% do impacto nos negócios da interrupção será proveniente de 20% dos sistemas afetados por uma interrupção

As operações de carga de trabalho devem ser aplicadas somente quando a estratégia de adoção de nuvem, os resultados comerciais e as métricas operacionais forem bem compreendidas. Essa é uma mudança de paradigma da exibição clássica da ti. Tradicionalmente, supõe-se que todas as cargas de trabalho tiveram o mesmo grau de suporte e que exigiam níveis semelhantes de prioridade.

Antes de investir em operações de carga de trabalho profundas, a ti e a empresa devem entender as justificativas de negócios e as expectativas de maior investimento no gerenciamento de nuvem.

## <a name="start-with-the-data"></a>Comece com os dados

As operações de carga de trabalho começam com uma compreensão profunda dos requisitos de desempenho e suporte da carga de trabalho. Antes de investir em operações de carga de trabalho, a equipe deve ter dados avançados em relação a: dependências de carga de trabalho, desempenho de aplicativos, diagnóstico de banco, telemetria de máquina virtual e histórico de incidentes.

Esses dados propagam as informações que orientam as decisões de operações de carga de trabalho.

## <a name="continued-observation"></a>Observação continuada

Os dados iniciais e a telemetria contínua podem ajudar a formular e testar o teorias em relação ao desempenho de uma carga de trabalho. No entanto, as operações de carga de trabalho contínuas têm raiz em uma observação contínua e expandida do desempenho da carga de trabalho, com um foco intenso no desempenho de aplicativos e dados.

### <a name="testing-automation"></a>Testando a automação

No nível do aplicativo, os primeiros requisitos de operações de carga de trabalho são um investimento em testes detalhados. Para qualquer aplicativo com suporte por meio de operações de carga de trabalho, um plano de teste deve ser estabelecido e executado regularmente para fornecer testes funcionais e de escala nos aplicativos.

A telemetria de teste regular fornecerá a validação imediata de várias outras subformas sobre a operação da carga de trabalho. Aprimorar os padrões de arquitetura e operacionais pode ser executado e testado, o Delta nesses resultados fornece uma análise de impacto clara para orientar os investimentos contínuos.

### <a name="understand-releases"></a>Entender as versões

A compreensão clara dos ciclos de liberação e dos pipelines de lançamento é um elemento importante das operações de carga de trabalho.

Uma compreensão dos ciclos pode se preparar para possíveis interrupções e permitir que a equipe resolva proativamente todas as versões que possam produzir um efeito adverso nas operações. Essa compreensão também permite que a equipe de gerenciamento de nuvem entre em parceria com as equipes de adoção para melhorar continuamente a qualidade dos bugs de produtos e endereços que poderiam afetar a estabilidade.

Mais importante, uma compreensão dos pipelines de versão pode melhorar significativamente o RTO de uma carga de trabalho. Em muitos cenários, o caminho mais rápido e mais preciso para a recuperação de um aplicativo é um pipeline de lançamento. Para camadas de aplicativo que só mudam quando ocorre uma nova versão, pode ser recomendável investir mais pesado na otimização do pipeline, do que a recuperação do aplicativo de processos de backup tradicionais.

Embora um pipeline de implantação possa ser o caminho mais rápido para a recuperação, ele também pode ser o caminho mais rápido para a correção. Quando um aplicativo tem um pipeline de lançamento rápido, eficiente e confiável, a equipe de gerenciamento de nuvem tem uma opção para automatizar a implantação em um novo host como forma de correção automatizada.

Pode haver muitos outros mecanismos mais rápidos e eficientes para correção e recuperação. No entanto, quando o uso de um pipeline existente pode atender a compromissos comerciais e capitalizar investimentos DevOps existentes, pode ser uma alternativa viável.

### <a name="clearly-communicate-changes-to-the-workload"></a>Comunique claramente as alterações na carga de trabalho

A mudança para qualquer carga de trabalho está entre os maiores riscos para as operações de carga de trabalho. Para qualquer carga de trabalho no nível de operações de carga de trabalho do gerenciamento de nuvem, a equipe de gerenciamento de nuvem deve estar fortemente alinhada com as equipes de adoção de nuvem para entender as alterações provenientes de cada versão. Esse investimento em compreensão proativa terá um impacto direto na estabilidade operacional.

## <a name="improve-outcomes"></a>Melhorar os resultados

As operações em andamento geralmente são aprimoradas de uma de duas maneiras. Os investimentos de dados e comunicação em uma carga de trabalho produzirão sugestões para melhorias em um dos dois caminhos: correção automatizada ou design de sistema aprimorado

### <a name="technical-debt-resolution"></a>Resolução técnica de dívidas

Os melhores planos de operações de carga de trabalho ainda exigirão correção. À medida que a equipe de gerenciamento de nuvem busca se manter conectado para entender os esforços de adoção e as versões, a equipe deve estar compartilhando regularmente os requisitos de correção para garantir que a dívida técnica e os bugs sejam uma prioridade contínua para as equipes de desenvolvimento.

### <a name="automate-remediation"></a>Automatizar a correção

Aplicando o princípio do Pareto, 80% do impacto de negócios negativo provavelmente vem de 20% dos incidentes de serviço. Quando esses incidentes não podem ser resolvidos em ciclos normais de desenvolvimento, os investimentos na automação de correção podem reduzir significativamente as interrupções de negócios.

### <a name="improved-system-design"></a>Melhor design do sistema

Em ambos os casos (resolução de débito técnico ou correção automatizada), as falhas do sistema são a causa comum da maioria das interrupções do sistema. Aderir a alguns princípios de design pode ter o maior impacto sobre as operações gerais de carga de trabalho.

1. Escalabilidade: a capacidade de um sistema de lidar com a carga aumentada.
2. Disponibilidade: a proporção de tempo em que um sistema está funcionando e funcionando.
3. Resiliência: a capacidade de um sistema de se recuperar de falhas e continuar a funcionar.
4. Gerenciamento: processos de operações que mantêm um sistema em execução na produção.
5. Segurança: proteger aplicativos e dados contra ameaças.

A [estrutura de arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fornece uma abordagem para avaliar cargas de trabalho específicas para adesão a esses pilares, em um esforço para melhorar as operações gerais. Esses pilares podem ser aplicados a operações de plataforma e operações de carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Com uma compreensão total da metodologia de gerenciamento dentro da estrutura de adoção de nuvem, agora você está armado para implementar princípios de gerenciamento de nuvem. Consulte a [página de aterrissagem da fase gerenciar](../index.md) do ciclo de vida de adoção para obter orientação sobre como tornar essa metodologia acionável no ambiente de operações.

> [!div class="nextstepaction"]
> [Aplicar esta metodologia](../index.md)
