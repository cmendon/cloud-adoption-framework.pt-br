---
title: Operações de carga de trabalho – gerenciamento de nuvem e operações
description: Operações de carga de trabalho – gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: b97cd4963dc19753f0d8216923a376f4d077930a
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807692"
---
# <a name="workload-operations-in-cloud-management"></a>Operações de carga de trabalho no gerenciamento de nuvem

Algumas cargas de trabalho são críticas para o sucesso dos negócios. Para essas cargas de trabalho, uma linha de base de gerenciamento é insuficiente para atender aos compromissos de negócios necessários para o gerenciamento de nuvem. As operações de plataforma podem nem mesmo ser suficientes para atender aos compromissos comerciais. Esse subconjunto altamente importante de cargas de trabalho requer um foco especializado na maneira como as funções de carga de trabalho e como há suporte.

Em retorno, o investimento em operações de carga de trabalho pode levar a um desempenho aprimorado, menor risco de interrupção dos negócios e recuperação mais rápida quando ocorrem falhas do sistema. Este artigo aborda uma abordagem de investindo nas operações contínuas dessas cargas de trabalho de alta prioridade para impulsionar os compromissos comerciais aprimorados.

## <a name="when-to-invest-in-workload-operations"></a>Quando investir em operações de carga de trabalho

O _princípio de Pareto_ (também conhecido como a _regra 80/20_) afirma que 80% dos efeitos vêm de 20% das causas. Quando os portfólios de ti têm permissão para aumentar a orgânicamente com o passar do tempo, essa regra geralmente é ilustrada em uma análise do portfólio de ti. Dependendo do efeito que exige investimento, a causa pode variar, mas o princípio geral é verdadeiro:

- 80 por cento das falhas do sistema tendem a ser o resultado de 20% dos erros ou bugs comuns.
- 80% do valor comercial tende a vir de 20% das cargas de trabalho em um portfólio.
- 80 por cento do esforço para migrar para a nuvem vem de 20% das cargas de trabalho que estão sendo movidas.
- 80 por cento dos esforços de gerenciamento de nuvem dará suporte a 20% dos incidentes de serviço ou tíquetes de problema.
- 80 por cento do impacto nos negócios de uma interrupção será proveniente de 20% dos sistemas afetados pela interrupção.

As operações de carga de trabalho devem ser aplicadas somente quando a estratégia de adoção de nuvem, os resultados comerciais e as métricas operacionais são bem compreendidas. Essa é uma mudança de paradigma da exibição clássica da ti. Tradicionalmente, supõe-se que todas as cargas de trabalho tiveram o mesmo grau de suporte e que exigiam níveis semelhantes de prioridade.

Antes que eles invistam em operações de carga de trabalho profundas, a ti e a empresa devem entender as justificativas de negócios e as expectativas do aumento do investimento no gerenciamento de nuvem.

## <a name="start-with-the-data"></a>Iniciar com os dados

As operações de carga de trabalho começam com uma compreensão profunda dos requisitos de desempenho e suporte da carga de trabalho. Antes que a equipe investe em operações de carga de trabalho, ela deve ter dados avançados sobre dependências de carga de trabalho, desempenho de aplicativos, diagnósticos de banco, telemetria de máquina virtual e histórico de incidentes.

Esses dados propagam as informações que orientam as decisões de operações de carga de trabalho.

## <a name="continued-observation"></a>Observação continuada

Os dados iniciais e a telemetria contínua podem ajudar a formular e testar teorias sobre o desempenho de uma carga de trabalho. Mas as operações de carga de trabalho contínuas têm raiz em uma observação contínua e expandida do desempenho da carga de trabalho, com um foco intenso no desempenho de aplicativos e dados.

### <a name="test-the-automation"></a>Testar a automação

No nível do aplicativo, os primeiros requisitos de operações de carga de trabalho são um investimento em testes detalhados. Para qualquer aplicativo com suporte por meio de operações de carga de trabalho, um plano de teste deve ser estabelecido e executado regularmente para fornecer testes funcionais e de escala nos aplicativos.

A telemetria de teste regular pode fornecer validação imediata de várias informações sobre a operação da carga de trabalho. Melhorar os padrões de arquitetura e operacionais pode ser executado e testado. Os deltas resultantes fornecem uma análise de impacto clara para orientar os investimentos contínuos.

### <a name="understand-releases"></a>Entender as versões

Uma compreensão clara dos ciclos de liberação e dos pipelines de lançamento é um elemento importante das operações de carga de trabalho.

Uma compreensão dos ciclos pode se preparar para possíveis interrupções e permitir que a equipe resolva proativamente todas as versões que possam produzir um efeito adverso nas operações. Essa compreensão também permite que a equipe de gerenciamento de nuvem entre em parceria com as equipes de adoção para melhorar continuamente a qualidade do produto e resolver quaisquer bugs que possam afetar a estabilidade.

Mais importante, uma compreensão dos pipelines de versão pode melhorar significativamente o RPO (objetivo de ponto de recuperação) de uma carga de trabalho. Em muitos cenários, o caminho mais rápido e mais preciso para a recuperação de um aplicativo é um pipeline de lançamento. Para camadas de aplicativo que são alteradas somente quando ocorre uma nova versão, pode ser recomendável investir mais fortemente na otimização de pipeline do que na recuperação do aplicativo de processos de backup tradicionais.

Embora um pipeline de implantação possa ser o caminho mais rápido para a recuperação, ele também pode ser o caminho mais rápido para a correção. Quando um aplicativo tem um pipeline de lançamento rápido, eficiente e confiável, a equipe de gerenciamento de nuvem tem uma opção para automatizar a implantação em um novo host como forma de correção automatizada.

Pode haver muitos outros mecanismos mais rápidos e eficientes para correção e recuperação. No entanto, quando o uso de um pipeline existente pode atender a compromissos comerciais e capitalizar investimentos DevOps existentes, o pipeline existente pode ser uma alternativa viável.

### <a name="clearly-communicate-changes-to-the-workload"></a>Comunique claramente as alterações na carga de trabalho

A mudança para qualquer carga de trabalho está entre os maiores riscos para as operações de carga de trabalho. Para qualquer carga de trabalho no nível de operações de carga de trabalho do gerenciamento de nuvem, a equipe de gerenciamento de nuvem deve alinhar-se fortemente às equipes de adoção de nuvem para entender as alterações provenientes de cada versão. Esse investimento em compreensão proativa terá um impacto direto e positivo sobre a estabilidade operacional.

## <a name="improve-outcomes"></a>Melhorar os resultados

Os investimentos de dados e comunicação em uma carga de trabalho produzirão sugestões para melhorias em operações contínuas em uma das três áreas:

- Resolução técnica de dívidas
- Correção automatizada
- Melhor design do sistema

### <a name="technical-debt-resolution"></a>Resolução técnica de dívidas

Os planos de operações de melhor carga de trabalho ainda exigem correção. À medida que sua equipe de gerenciamento de nuvem busca se manter conectado para entender os esforços de adoção e as versões, a equipe da mesma forma deve compartilhar regularmente os requisitos de correção para garantir que a dívida técnica e os bugs sejam uma prioridade contínua para suas equipes de desenvolvimento.

### <a name="automated-remediation"></a>Correção automatizada

Ao aplicar o princípio de Pareto, podemos dizer que 80% do impacto de negócios negativo provavelmente vem de 20% dos incidentes de serviço. Quando esses incidentes não podem ser resolvidos em ciclos normais de desenvolvimento, os investimentos na automação de correção podem reduzir significativamente as interrupções de negócios.

### <a name="improved-system-design"></a>Melhor design do sistema

Nos casos de resolução de dívidas técnicas e correção automatizada, as falhas do sistema são a causa comum da maioria das interrupções do sistema. Você pode ter o maior impacto sobre as operações gerais de carga de trabalho ao aderir a alguns princípios de design:

- **Escalabilidade:** A capacidade de um sistema de lidar com a carga aumentada.
- **Disponibilidade:** A porcentagem de tempo em que um sistema está funcionando e funcionando.
- **Resiliência:** A capacidade de um sistema de se recuperar de falhas e continuar a funcionar.
- **Gerenciamento:** Processos de operações que mantêm um sistema em execução na produção.
- **Segurança:** Proteção de aplicativos e dados contra ameaças.

Para ajudar a melhorar as operações gerais, a [estrutura de arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fornece uma abordagem para avaliar cargas de trabalho específicas para adesão a esses pilares. Você pode aplicar os pilares que podem ser aplicados a operações de plataforma e operações de carga de trabalho.

## <a name="next-steps"></a>Próximos passos

Com uma compreensão total da metodologia de gerenciamento dentro da estrutura de adoção de nuvem, agora você está armado para implementar princípios de gerenciamento de nuvem. Para obter orientação sobre como tornar essa metodologia acionável no ambiente de operações, consulte [Gerenciamento de nuvem na estrutura de adoção de nuvem](../index.md) do ciclo de vida de adoção.

> [!div class="nextstepaction"]
> [Aplicar esta metodologia](../index.md)
