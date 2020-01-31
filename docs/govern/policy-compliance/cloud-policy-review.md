---
title: Realizar uma revisão da política de nuvem
description: Saiba como conduzir uma revisão de política de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 48e4e759435178e346e08233afeca95ab065711e
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76805057"
---
<!-- markdownlint-disable MD026 -->

# <a name="conduct-a-cloud-policy-review"></a>Realizar uma revisão da política de nuvem

Uma análise de política de nuvem é a primeira etapa para a [maturidade de governança](../index.md) na nuvem. O objetivo desse processo é modernizar as políticas corporativas de TI existentes. Quando concluído, as políticas atualizadas fornecem um nível equivalente de gerenciamento de riscos para recursos baseados em nuvem. Este artigo explica o processo de revisão da política de nuvem e sua importância.

## <a name="why-perform-a-cloud-policy-review"></a>Por que realizar uma revisão de política de nuvem?

A maioria das empresas gerenciam a TI através da execução de processos em alinhamento às políticas em vigor. Em empresas de pequeno porta, essas políticas podem ser anedóticas e os processos vagamente definidos. À medida que as empresas crescem para grandes empresas, as políticas e processos tendem a ser documentados com mais clareza e executadas de forma consistente.

Conforme as empresas amadurecem as políticas corporativas de TI, as dependências nas últimas decisões técnicas têm uma tendência a se infiltrar nas políticas em vigor. Por exemplo, é comum ver que os processos de recuperação de desastres incluem a política que exige backups em fitas externas. Essa inclusão pressupõe uma dependência em um tipo de tecnologia (backups em fita), que pode não ser mais a solução mais relevante.

As transformações na nuvem criam um ponto de inflexão natural para reconsiderar as decisões herdadas da política do passado. Recursos técnicos e processos padrão consideravelmente alteram na nuvem, como fazem os riscos herdados. Usando o exemplo anterior, a política de backup em fita foi originada do risco de um único ponto de falha, mantendo os dados em um local e a necessidade comercial de minimizar o perfil de risco, reduzindo esse risco. Em uma implantação de nuvem, há várias opções que fornecem a mesma mitigação de riscos, com muito muitos objetivos de tempo de recuperação inferiores (RTO). Por exemplo:

- Uma solução nativa de nuvem pode habilitar a replicação geográfica do banco de dados SQL do Azure.
- Uma solução híbrida poderia usar Azure Site Recovery para replicar uma carga de trabalho de IaaS no Azure.

Ao executar uma transformação de nuvem, as políticas geralmente controlam muitas das ferramentas, serviços e processos disponíveis para as equipes de adoção da nuvem. Se essas políticas se baseiam em tecnologias herdadas, elas podem atrapalhar os esforços da equipe para conduzir mudanças. Na pior das hipóteses, políticas importantes são inteiramente ignoradas pela equipe de migração para habilitar soluções alternativas. Nenhum deles é um resultado aceitável.

## <a name="the-cloud-policy-review-process"></a>Processo de revisão da política de nuvem

As revisões de política de nuvem alinham as políticas de segurança de ti e de governança de ti existentes às [cinco disciplinas de governança de nuvem](../index.md): [Gerenciamento de custos](../cost-management/index.md), [linha de base de segurança](../security-baseline/index.md), linha de base de [identidade](../identity-baseline/index.md), [consistência de recursos](../resource-consistency/index.md)e [aceleração](../deployment-acceleration/index.md)

Para cada uma dessas disciplinas, o processo de revisão segue essas etapas:

1. Políticas de revisão local existentes relacionadas à disciplina específica, procurando dois pontos de dados principais: dependências de legado e riscos comerciais identificados.
2. Avalie cada risco de negócios fazendo uma pergunta simples: "o risco comercial ainda existe em um modelo de nuvem?"
3. Se o risco ainda existir, reescreva a política ao documentar a mitigação de negócios necessária, não a solução técnica.
4. Examine a política atualizada com as equipes de adoção de nuvem para entender as possíveis soluções técnicas para a mitigação necessária.

## <a name="example-of-a-policy-review-for-a-legacy-policy"></a>Exemplo de uma revisão de política para uma política de legado

Para fornecer um exemplo do processo, vamos usar novamente a política de backup em fita da seção anterior:

- Uma política corporativa que rege a maneira de fazer backups em fita para todos os sistemas de produção. Nessa política, você pode ver dois pontos de dados de interesse:
  - Dependência herdada em uma solução de backup em fita
  - Um risco de negócios assumido associado ao armazenamento de backups no mesmo local físico que o equipamento de produção.
- O risco ainda existe? Sim. Até mesmo na nuvem, uma dependência em um único recurso cria algum risco. Há uma probabilidade menor desse risco afetar o negócio que estava presente na solução no local, mas ainda existe o risco.
- Regravação da política. Em caso de desastre de todo o datacenter, deve existir uma maneira de restaurar os sistemas de produção dentro de 24 horas de interrupção em um datacenter diferente e um local geográfico diferente.
  - Também é importante considerar que a linha do tempo especificada no requisito acima pode ter sido definida por restrições técnicas que não estão mais presentes na nuvem. Certifique-se de entender as restrições técnicas e os recursos da nuvem antes de simplesmente aplicar um RTO/RPO herdado.
- Examine com as equipes de adoção da nuvem. Dependendo da solução que está sendo implementada, há vários meios de aderir a esta política de Consistência de Recursos.

## <a name="next-steps"></a>Próximos passos

Saiba mais sobre como incluir a classificação de dados em sua estratégia de governança de nuvem.

> [!div class="nextstepaction"]
> [Classificação de dados](./data-classification.md)
