---
title: Abordagens para planejamento de propriedade digital
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre as várias abordagens para o planejamento digital de imóveis.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: d4f420274b27646e94c64c2e5347bff50124c9dd
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829339"
---
# <a name="approaches-to-digital-estate-planning"></a>Abordagens para planejamento de propriedade digital

O planejamento de imóveis pode usar várias formas dependendo dos resultados desejados e do tamanho do espaço existente. Há várias abordagens que você pode tomar. É importante definir as expectativas com relação à abordagem logo no início dos ciclos de planejamento. As expectativas inclaras muitas vezes levam a atrasos associados a exercícios adicionais de coleta de inventário. Este artigo descreve três abordagens para análise.

## <a name="workload-driven-approach"></a>Abordagem orientada por carga de trabalho

A abordagem de avaliação de cima para baixo avalia os aspectos de segurança. A segurança inclui a categorização de dados (alto, médio ou baixo impacto nos negócios), conformidade, soberania e requisitos de risco de segurança. Essa abordagem avalia a complexidade da arquitetura de alto nível. Ele avalia aspectos como autenticação, estrutura de dados, requisitos de latência, dependências e expectativa de vida do aplicativo.

A abordagem de cima para baixo também mede os requisitos operacionais do aplicativo, como níveis de serviço, integração, janelas de manutenção, monitoramento e insight. Quando todos esses aspectos foram analisados e levados em consideração, a pontuação resultante que reflete a dificuldade relativa de migrar esse aplicativo para cada uma das plataformas de nuvem: IaaS, PaaS e SaaS.

Além disso, a avaliação de cima para baixo avalia os benefícios financeiros do aplicativo, como eficiência operacional, TCO, retorno sobre o investimento e outras métricas financeiras apropriadas. A avaliação também examina o sazonalidade do aplicativo (por exemplo, há ocasiões do ano em que a demanda é pico?) e carga de computação geral.

Ele também examina os tipos de usuários que ele dá suporte (casual/especialista, sempre/ocasionalmente conectado) e a escalabilidade e a elasticidade necessárias. Por fim, a avaliação é concluída examinando os requisitos de continuidade e resiliência dos negócios, bem como as dependências para a execução do aplicativo caso ocorra uma interrupção do serviço.

> [!TIP]
> Essa abordagem exige entrevistas e comentários informais dos participantes técnicos e empresariais. A disponibilidade de indivíduos chave é o maior risco à pontualidade. A natureza informal das fontes de dados dificulta ainda mais a produção de estimativas de custo ou de tempo. Planeje agendamentos antecipadamente e valide todos os dados coletados.

## <a name="asset-driven-approach"></a>Abordagem orientada por ativos

A abordagem controlada por ativos fornece um plano baseado nos ativos que dão suporte a um aplicativo para migração. Nessa abordagem, você efetua pull de dados de uso estatístico de um CMDB (banco de dados de gerenciamento de configuração) ou outras ferramentas de avaliação de infraestrutura.

Geralmente, essa abordagem pressupõe um modelo de implantação IaaS como linha de base. Nesse processo, a análise avalia os atributos de cada ativo: memória, número de processadores (núcleos de CPU), espaço de armazenamento do sistema operacional, unidades de dados, NICs (placas de interface de rede), IPv6, balanceamento de carga de rede, clustering, versão do sistema operacional, versão do banco de dados (se necessário), domínios com suporte e componentes de terceiros ou pacotes de software, entre outros. Os ativos que você inventaria nessa abordagem são alinhados com cargas de trabalho ou aplicativos para fins de agrupamento e mapeamento de dependências.

> [!TIP]
> Essa abordagem exige uma fonte rica de dados de uso em estatística. O tempo necessário para verificar o inventário e coletar dados é o maior risco de cronometragem. As fontes de dados de baixo nível podem perder dependências entre os aplicativos ou ativos. Planeje durante pelo menos um mês a verificação do inventário. Valide as dependências antes da implantação.

## <a name="incremental-approach"></a>Abordagem incremental

É altamente recomendável uma abordagem incremental, como fazemos para muitos processos na estrutura de adoção de nuvem. No caso do planejamento de imóveis digitais, isso equivale a um processo de Multifase:

- **Análise de custo inicial:** Se a validação financeira for necessária, comece com uma abordagem controlada por ativo, descrita anteriormente, para obter um cálculo de custo inicial para todo o espaço digital, sem racionalização. Isso estabelece um parâmetro de comparação de pior cenário possível.

- **Planejamento da migração:** Depois de montar uma equipe de estratégia de nuvem, crie uma pendência de migração inicial usando uma abordagem controlada por carga de trabalho com base em seu conhecimento coletivo e em entrevistas de Stakeholder limitadas. Essa abordagem cria rapidamente uma avaliação de carga de trabalho leve para promover a colaboração.

- **Planejamento de versão:** Em cada versão, a pendência de migração é removida e priorizada para se concentrar no impacto comercial mais relevante. Durante esse processo, as próximas cinco a dez cargas de trabalho são selecionadas como versões priorizadas. Neste ponto, a equipe de estratégia de nuvem investe o tempo de conclusão de uma abordagem exaustiva controlada por carga de trabalho. Atrasar essa avaliação até que uma versão seja alinhada melhor respeita o tempo dos participantes. Também atrasa o investimento em análise completa até que a empresa comece a ver resultados dos esforços anteriores.

- **Análise de execução:** Antes de migrar, modernizar ou replicar qualquer ativo, avalie-o individualmente e como parte de uma versão coletiva. Neste ponto, os dados da abordagem inicial orientada por ativos podem ser examinados a fim de garantir o dimensionamento preciso e restrições operacionais.

> [!TIP]
> Essa abordagem incremental permite o planejamento simplificado e os resultados acelerados. É importante que todas as partes envolvidas entendam a abordagem da tomada de decisão atrasada. É igualmente importante que as suposições feitas em cada estágio sejam documentadas para evitar a perda de detalhes.

## <a name="next-steps"></a>Próximas etapas

Após a seleção de uma abordagem, o inventário pode ser coletado.

> [!div class="nextstepaction"]
> [Coletar dados de inventário](inventory.md)
