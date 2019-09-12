---
title: Primeiro projeto de adoção de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre como implementar seu primeiro projeto de adoção de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 5/19/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 6f3e1ad47b329e39addd9fff087568e4124f8859
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825075"
---
<!-- markdownlint-disable MD026 -->

# <a name="first-cloud-adoption-project"></a>Primeiro projeto de adoção de nuvem

Há uma curva de aprendizado e um compromisso de tempo associado ao planejamento de adoção de nuvem. Mesmo para equipes experientes, o planejamento adequado leva tempo: tempo para alinhar os participantes, tempo para coletar e analisar dados, tempo para validar decisões de longo prazo e o tempo de alinhar pessoas, processos e tecnologia. Nos esforços de adoção mais produtivos, o planejamento cresce em paralelo com a adoção, melhorando cada versão e com cada migração de carga de trabalho para a nuvem. É importante entender a diferença entre um plano de adoção de nuvem e uma estratégia de adoção de nuvem. Você precisa de uma estratégia bem definida para facilitar e orientar a implementação de um plano de adoção de nuvem.

A estrutura de adoção de nuvem para o Azure descreve os processos de adoção de nuvem e a operação de cargas de trabalho hospedadas na nuvem. Cada um dos processos nas fases definir estratégia, plano, pronto, adotar e operar requer pequenas expansões de habilidades técnicas, de negócios e operacionais. Algumas dessas habilidades podem vir do aprendizado direcionado. Mas muitos deles são adquiridos com mais eficiência por meio de experiência prática.

Iniciar um primeiro processo de adoção em paralelo com o desenvolvimento do plano fornece alguns benefícios:

- Estabeleça uma mentalidade de crescimento para incentivar o aprendizado e a exploração
- Fornecer uma oportunidade para a equipe desenvolver as habilidades necessárias
- Criar situações que incentivam novas abordagens à colaboração
- Identificar lacunas de habilidades e necessidades de parceria em potencial
- Fornecer entradas tangíveis ao plano

## <a name="first-project-criteria"></a>Primeiros critérios de projeto

Seu primeiro projeto de adoção deve se alinhar com suas [motivações](./motivations-why-are-we-moving-to-the-cloud.md) para a adoção da nuvem. Sempre que possível, seu primeiro projeto também deve demonstrar o progresso em direção a um [resultado comercial](./business-outcomes/how-to-use-the-business-outcome-template.md)definido.

## <a name="first-project-expectations"></a>Expectativas do primeiro projeto

O primeiro projeto de adoção da sua equipe provavelmente resultará em uma implantação de produção de algum tipo. Mas esse nem sempre é o caso. Estabeleça expectativas adequadas com antecedência. Aqui estão algumas expectativas inteligentes a serem definidas:

- Este projeto é uma fonte de aprendizado.
- Esse projeto pode resultar em implantações de produção, mas provavelmente exigirá um esforço adicional primeiro.
- A saída desse projeto é um conjunto de requisitos claros para fornecer uma solução de produção de longo prazo.

## <a name="first-project-examples"></a>Primeiros exemplos de projeto

Para dar suporte aos critérios anteriores, essa lista fornece um exemplo de um primeiro projeto para cada categoria de motivação:

- **Eventos comerciais críticos:** Quando um evento crítico de negócios é a principal motivação, a implementação de uma ferramenta como [Azure site Recovery](../migrate/azure-migration-guide/migrate.md?tabs=Tools#azure-site-recovery) pode ser um bom primeiro projeto. Durante a migração, você pode usar essa ferramenta para migrar rapidamente os ativos do datacenter. Mas, durante o primeiro projeto, você pode usá-lo puramente como uma ferramenta de recuperação de desastres, reduzindo as dependências dos ativos de recuperação de desastres no datacenter.

- **Motivações de migração:** Quando a migração é a principal motivação, é recomendável começar com a migração de uma carga de trabalho não crítica. O [Guia de preparação do Azure](../ready/azure-readiness-guide/index.md) e o [Guia de migração do Azure](../migrate/azure-migration-guide/index.md) podem fornecer diretrizes para a migração da sua primeira carga de trabalho.

- **Motivações de inovação:** Quando a inovação é a principal motivação, a criação de um ambiente de desenvolvimento/teste direcionado pode ser um ótimo primeiro projeto.

Exemplos adicionais de primeiros projetos de adoção incluem:

- **Recuperação de desastres e continuidade dos negócios (DRBC):** Além Azure Site Recovery, você pode implementar várias estratégias DRBC como um primeiro projeto.
- **Não produção** Implantar uma instância de não produção de uma carga de trabalho.
- **Operação** O armazenamento frio pode encarregar os recursos do datacenter. Mover esses dados para a nuvem é um rápido ganho sólido.
- **Fim do suporte (EOS):** A migração de ativos que atingiram o fim do suporte é outra vitória rápida que cria habilidades técnicas. Ele também pode fornecer alguma redução de custos de contratos de suporte caros ou custos de licenciamento.
- **VDI (Virtual Desktop interface):** A criação de áreas de trabalho virtuais para funcionários remotos pode fornecer um rápido ganho. Em alguns casos, esse primeiro projeto de adoção também pode reduzir a dependência em redes privadas caras em favor da conectividade de Internet pública de mercadoria.
- **Desenvolvimento/teste:** Remova o desenvolvimento/teste de ambientes locais para dar aos desenvolvedores controle, agilidade e capacidade de autoatendimento.
- **Aplicativos simples (menos de cinco):** Modernizar e migrar um aplicativo simples para obter rapidamente experiência de desenvolvedor e operações.
- **Laboratórios de desempenho:** Quando você precisar de desempenho em grande escala em uma configuração de laboratório, use a nuvem para provisionar de forma rápida e econômica esses laboratórios por um curto período de tempo.
- **Plataforma de dados:** Criação de um data Lake com computação escalonável para cargas de trabalho de análise, relatório ou aprendizado de máquina.

## <a name="next-steps"></a>Próximas etapas

Depois que o primeiro projeto de adoção de nuvem começou, a equipe de estratégia de nuvem pode transformar sua atenção no [plano de adoção de nuvem](../plan/index.md)de longo prazo.

> [!div class="nextstepaction"]
> [Crie seu plano de adoção de nuvem](../plan/index.md)
