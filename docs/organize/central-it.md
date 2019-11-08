---
title: Recursos centrais de ti
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre a formação de recursos centrais de ti.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 25e9ecd4d911766864d81a5ff34f00caf82e86bf
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753635"
---
# <a name="central-it-capabilities"></a>Recursos centrais de ti

À medida que a adoção de nuvem é dimensionada, os recursos de governança de nuvem sozinhos podem não ser suficientes para controlar os esforços de adoção. Quando a adoção é gradual, as equipes tendem a desenvolver proorgânicamente as habilidades e os processos necessários para estar prontos para a nuvem ao longo do tempo.

No entanto, quando uma equipe de adoção de nuvem usa a nuvem para atingir um resultado comercial de alto perfil, a adoção gradual raramente é o caso. O sucesso segue o sucesso. Isso também é verdadeiro para a adoção da nuvem, mas acontece em escala de nuvem. Quando a adoção de nuvem se expande de uma equipe para várias equipes relativamente rapidamente, é necessário ter suporte adicional da equipe de ti existente. No entanto, esses membros da equipe podem não ter o treinamento e a experiência necessários para dar suporte à nuvem usando ferramentas de ti nativas de nuvem. Isso geralmente orienta a formação de uma equipe de ti central que governa a nuvem.

> [!CAUTION]
> Embora essa seja uma etapa de maturidade comum, ela pode apresentar um alto risco de adoção, potencialmente bloqueando os esforços de inovação e de migração, se não forem gerenciados com eficiência. Consulte a seção de risco abaixo para saber como reduzir o risco de centralizar se tornar um antipadrão cultural.

## <a name="possible-sources-for-central-it-expertise"></a>Fontes possíveis para a experiência central de ti

As habilidades necessárias para fornecer recursos de ti centralizados podem ser fornecidas por:

- Uma equipe de ti central existente
- Arquitetos empresariais
- Operações de ti
- Governança de ti
- Infraestrutura de ti
- Rede
- Identidade
- Virtualização
- Continuidade dos negócios e recuperação de desastres
- Proprietários do aplicativo dentro dele

> [!WARNING]
> A ti central só deve ser aplicada na nuvem quando a entrega existente no local é baseada em um modelo de ti central. Se o modelo local atual for baseado no controle delegado, considere uma abordagem de CCoE (Cloud Center of Excellence) para uma alternativa mais compatível.

## <a name="key-responsibilities"></a>Principais responsabilidades

Adapte as práticas de ti existentes para garantir que os esforços de adoção resultem em ambientes bem controlados e bem gerenciados na nuvem.

As seguintes tarefas são normalmente executadas regularmente:

### <a name="strategic-tasks"></a>Tarefas estratégicas

- Revê
  - [resultados de negócios](../strategy/business-outcomes/index.md)
  - [modelos financeiros](../strategy/financial-models.md)
  - [motivações para adoção de nuvem](../strategy/motivations.md)
  - [riscos de negócios](../govern/policy-compliance/risk-tolerance.md)
  - [racionalização do espaço digital](../digital-estate/index.md)
- Monitore planos de adoção e o progresso em relação à [pendência de migração priorizada](../migrate/migration-considerations/assess/release-iteration-backlog.md).
- Identifique e Priorize as alterações de plataforma necessárias para dar suporte à lista de pendências de migração.
- Atue como uma camada intermediária ou de tradução entre as necessidades de adoção de nuvem e as equipes de ti existentes.
- Aproveite as equipes de ti existentes para acelerar os recursos de plataforma e habilitar a adoção.

### <a name="technical-tasks"></a>Tarefas técnicas

- Crie e mantenha a plataforma de nuvem para dar suporte a soluções.
- Defina e implemente a arquitetura da plataforma.
- Opere e gerencie a plataforma de nuvem.
- Aprimore a plataforma continuamente.
- Acompanhe as novas inovações na plataforma de nuvem.
- Forneça novos recursos de nuvem para dar suporte à criação de valor comercial.
- Sugira soluções de autoatendimento.
- Verifique se as soluções atendem aos requisitos de governança e conformidade existentes.
- Crie e valide a implantação da arquitetura da plataforma.
- Examine os planos de lançamento para obter fontes de novos requisitos de plataforma.

## <a name="meeting-cadence"></a>Cadência da reunião

A experiência central de ti normalmente vem de uma equipe de trabalho. Espere que os participantes confirmem grande parte de suas agendas diárias para esforços de alinhamento. As contribuições não são limitadas a ciclos de reuniões e comentários.

## <a name="central-it-risks"></a>Riscos de ti central

Cada um dos recursos de nuvem e as fases de maturidade organizacional são prefixados com a palavra "Cloud". Central é a única exceção. A ti central tornou-se predominante quando todos os ativos de ti pudessem ser alojados em alguns locais, gerenciados por um pequeno número de equipes e controlados por meio de uma única plataforma de gerenciamento de operações. As práticas de negócios globais e a economia digital reduziram amplamente as instâncias desses ambientes gerenciados centralmente.

No modo de exibição moderno de ti, os ativos são distribuídos globalmente. As responsabilidades são delegadas. O gerenciamento de operações é fornecido por uma combinação de equipe interna, provedores de serviços gerenciados e provedores de nuvem. Na economia digital, as práticas de gerenciamento de ti estão fazendo a transição para um modelo de autoatendimento e controle delegado com Clear guardrails para impor a governança. Central de ti pode ser um colaborador valioso para a adoção de nuvem, tornando-se um agente de nuvem e um parceiro de inovação e agilidade de negócios.

A ti central como uma função está bem posicionada para tomar conhecimento e práticas valiosas de modelos locais existentes e aplicar essas práticas à entrega na nuvem. No entanto, esse processo exigirá alteração. Novos processos, novas habilidades e novas ferramentas são necessários para dar suporte à adoção de nuvem em escala. Quando a ti central se adapta, ela se torna um parceiro importante nos esforços de adoção da nuvem. No entanto, se a ti central não se adaptar à nuvem ou tentar usar a nuvem como um catalisador para controles rígidos, central IT rapidamente se tornará um bloqueador de adoção, inovação e migração.

As medidas desse risco são a velocidade e a flexibilidade. A nuvem simplifica a adoção de novas tecnologias rapidamente. Quando novos recursos de nuvem podem ser implantados em minutos, mas as revisões de ti central adicionam semanas ou meses ao processo de implantação, esses processos centralizados se tornam um grande obstáculo ao sucesso dos negócios. Quando esse indicador for encontrado, considere estratégias alternativas para a entrega de ti.

### <a name="exceptions"></a>Exceções

Muitos setores exigem adesão rígida à conformidade de terceiros. Alguns requisitos de conformidade ainda exigem controle de ti centralizado. A oferta dessas medidas de conformidade pode adicionar tempo a processos de implantação, especialmente para novas tecnologias que não foram usadas em larga escala. Nesses cenários, espere atrasos na implantação durante os primeiros estágios de adoção. As situações semelhantes minhas existem para empresas que lidam com dados confidenciais do cliente, mas podem não ser regidas por um requisito de conformidade de terceiros.

### <a name="operate-within-the-exceptions"></a>Operar dentro das exceções

Quando processos de ti centralizados são necessários e esses processos criam pontos de verificação apropriados na adoção de novas tecnologias, esses pontos de verificação de inovação ainda podem ser tratados rapidamente. Os requisitos de governança e conformidade foram projetados para proteger as coisas que são confidenciais, não proteger tudo. A nuvem fornece mecanismos simples para adquirir e implantar recursos isolados, mantendo os guardrails adequados.

Uma equipe de ti central desenvolvida mantém as proteções necessárias, mas negocia as práticas que ainda habilitam a inovação. Demonstrar esse nível de maturidade depende da classificação apropriada e do isolamento dos recursos.

### <a name="example-narrative-of-operating-within-exceptions-to-empower-adoption"></a>Narração de exemplo de operação em exceções para capacitar a adoção

Esta narração de exemplo ilustra a abordagem adotada por uma equipe de ti central madura para capacitar a adoção.

A contoso, a LLC adotou um modelo de ti central para o suporte dos recursos de nuvem da empresa. Para fornecer esse modelo, eles implementaram controles rígidos para vários serviços compartilhados, como conexões de rede de entrada. Essa mudança inteligente reduziu a exposição de seu ambiente de nuvem e forneceu um único dispositivo de "interrupção" para bloquear todo o tráfego em caso de violação. Suas políticas de linha de base de segurança preparam que todo o tráfego de entrada deve vir por um dispositivo compartilhado gerenciado pela equipe de ti central.

No entanto, uma de suas equipes de adoção de nuvem agora requer um ambiente com uma conexão de rede de entrada dedicada e especialmente configurada para usar uma tecnologia de nuvem específica. Uma equipe de ti central inmaturo simplesmente recusaria a solicitação e priorizaria seus processos existentes em relação às necessidades de adoção. A equipe de ti central da Contoso é diferente. Eles identificaram rapidamente uma solução simples de quatro partes para esse dilema: classificação, negociação, isolamento e automação.

**Classificação:** Como a equipe de adoção de nuvem estava nos primeiros estágios da criação de uma nova solução e não tinha dados confidenciais ou necessidades de suporte de missão crítica, os ativos no ambiente foram classificados como baixo risco e não crítico. A classificação efetiva é um sinal de maturidade na ti central. Classificar todos os ativos e ambientes permite políticas mais claras.

**Negociação:** A classificação sozinha não é suficiente. Os serviços compartilhados foram implementados para operar ativos confidenciais e críticos de forma consistente. A alteração das regras deve comprometer as políticas de governança e de conformidade projetadas para os ativos que precisam de mais proteção. A capacitação da adoção não pode acontecer com o custo de estabilidade, segurança ou governança. Isso levou a uma negociação com a equipe de adoção para responder a perguntas específicas. Uma equipe de DevOps voltada para a empresa pode fornecer gerenciamento de operações para esse ambiente? Essa solução exigiria acesso direto a outros recursos internos? Se a equipe de adoção de nuvem estiver confortável com essas compensações, o tráfego de entrada poderá ser possível.

**Isolamento:** Como a empresa pode fornecer seu próprio gerenciamento contínuo de operações e, como a solução não depende do tráfego direto para outros ativos internos, ela pode ser isoladosda em uma nova assinatura. Essa assinatura também é adicionada a um nó separado da nova hierarquia do grupo de gerenciamento.

**Automação:** Outro sinal de maturidade nesta equipe são seus princípios de automação. A equipe usa Azure Policy para automatizar a imposição de políticas. Eles também usam plantas do Azure para automatizar a implantação de componentes comuns da plataforma e impor a adesão à linha de base de identidade definida. Para essa assinatura e quaisquer outras no novo grupo de gerenciamento, as políticas e os modelos são ligeiramente diferentes. As políticas que bloqueiam a largura de banda de entrada foram levantadas. Eles foram substituídos por requisitos para rotear o tráfego por meio da assinatura de serviços compartilhados, como qualquer tráfego de entrada, para impor o isolamento de tráfego. Como as ferramentas locais de gerenciamento de operações não podem acessar essa assinatura, os agentes para essa ferramenta não são mais necessários. Todas as outras guardrails de governança exigidas por outras assinaturas na hierarquia do grupo de gerenciamento ainda são impostas, garantindo guardrails suficientes.

A abordagem criativa desenvolvida da equipe de ti central da Contoso fornecia uma solução que não comprometeva a governança ou a conformidade, mas ainda foi incentivada a adoção. Essa abordagem de agente, em vez de alcançar abordagens nativas de nuvem para ser centralizada, é a primeira etapa para a criação de uma verdadeira CCoE (Cloud Center of Excellence). A adoção dessa abordagem para desenvolver rapidamente as políticas existentes permitirá o controle centralizado quando necessário e o guardrails de governança quando mais flexibilidade for aceitável. O balanceamento dessas duas considerações reduz os riscos associados à ti central na nuvem.

## <a name="next-steps"></a>Próximos passos

À medida que a ti central amadurece na nuvem, a próxima etapa de maturidade é normalmente um acoplamento mais flexível das [operações de nuvem](./cloud-operations.md). A disponibilidade de ferramentas de gerenciamento de operações nativas de nuvem e custos operacionais menores para soluções de PaaS-First geralmente leva a equipes de negócios (ou mais especificamente, DevOps equipes dentro da empresa) assumindo a responsabilidade pelas operações de nuvem.

> [!div class="nextstepaction"]
> [Funcionalidade de operações de nuvem](./cloud-operations.md)
