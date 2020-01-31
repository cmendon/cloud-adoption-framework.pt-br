---
title: Modelo de migração da Cloud Adoption Framework
description: Modelo de migração da Cloud Adoption Framework
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 46689512ec799ff8b5aa47ea095d34d8c25dd83a
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802422"
---
# <a name="cloud-adoption-framework-migration-model"></a>Modelo de migração da Cloud Adoption Framework

Esta seção da Cloud Adoption Framework explica os princípios por trás de seu modelo de migração. Sempre que possível, este conteúdo tenta manter uma posição neutra em termos de fornecedor ao orientá-lo pelos processos e pelas atividades que podem ser aplicados a qualquer migração na nuvem, independentemente de seu fornecedor de nuvem escolhido.

## <a name="understand-migration-motivations"></a>Compreender as motivações de migração

A migração na nuvem é um esforço de gerenciamento de portfólio, inteligentemente disfarçado de implementação técnica. Durante o processo de migração, você decidirá mover alguns ativos, investir em outros e desativar ativos obsoletos ou não usados. Alguns ativos serão otimizados, refatorados ou substituídos inteiramente como parte desse processo. Cada uma dessas decisões deve estar alinhada com as motivações por trás da migração na nuvem. As migrações de maior sucesso também vão um pouco além e alinham essas decisões aos resultados empresariais desejados.

O modelo de migração da Cloud Adoption Framework depende de sua organização ter concluído um processo de preparação empresarial para a adoção da nuvem. Examine a orientação de [Planejar](../../strategy/index.md) e [Pronto](../../ready/index.md) na Cloud Adoption Framework para determinar os condutores empresariais ou outra justificativa para uma migração na nuvem, bem como qualquer planejamento ou treinamento organizacional necessário antes de executar um processo de migração em escala.

> [!NOTE]
> Embora seja importante o planejamento empresarial, uma mentalidade de crescimento é igualmente importante. Em paralelo com esforços mais amplos de planejamento de negócios pela equipe de estratégia de nuvem, é aconselhável que a equipe de adoção da nuvem comece a migrar uma carga de trabalho primeiro como um precursor para os esforços de migração de escala maior. Essa migração inicial permitirá que a equipe obtenha experiência prática com os problemas técnicos e empresariais envolvidos na migração.

## <a name="envision-an-end-state"></a>Vislumbrar um estado final

É importante estabelecer uma visão aproximada do seu estado final antes de iniciar seus esforços de migração. O diagrama a seguir mostra um ponto de partida local da infraestrutura, de aplicativos e de dados, o que define seu *acervo digital*. Durante o processo de migração, esses ativos são transferidos usando uma das cinco estratégias de migração descritas em [Os cinco Rs da racionalização](../../digital-estate/5-rs-of-rationalization.md).

![Infográfico das opções de migração](../../_images/migrate/migration-options.png)

A migração e a modernização de cargas de trabalho variam de migrações simples de _nova hospedagem_ (também chamadas de _lift-and-shift_) usando as funcionalidades de IaaS (infraestrutura como serviço) que não exigem alterações de código e aplicativo até _refatoração_ com alterações mínimas e _rearquitetura_ para modificar e estender a funcionalidade de código e aplicativo para aproveitar as tecnologias de nuvem.

Estratégias nativas da nuvem e estratégias de PaaS (plataforma como serviço) *recompile* cargas de trabalho locais usando ofertas da plataforma do Azure e serviços gerenciados. Cargas de trabalho que têm as ofertas baseadas em nuvem de SaaS (software como serviço) totalmente gerenciadas muitas vezes podem ser totalmente *substituídas* por esses serviços como parte do processo de migração.

> [!NOTE]
> Durante a versão prévia pública da Cloud Adoption Framework, esta seção da estrutura enfatiza uma estratégia de migração de nova hospedagem. Embora as soluções de SaaS e PaaS sejam abordadas como alternativas quando apropriado, a migração de cargas de trabalho baseadas em máquina virtual usando as funcionalidades de IaaS é o principal foco.
>
> Outras seções e futuras iterações deste conteúdo serão expandidas em outras abordagens. Para uma discussão de alto nível sobre a expansão do escopo de sua migração para incluir estratégias de migração mais complicadas, veja o artigo sobre como balancear o portfólio.

## <a name="incremental-migration"></a>Migração incremental

O modelo de migração da Cloud Adoption Framework baseia-se em um processo de transformação incremental de nuvem. Pressupõe que sua organização começará com um esforço de migração na nuvem inicial de escopo limitado, que comumente chamamos de primeira carga de trabalho. Esse esforço será expandido iterativamente para incluir mais cargas de trabalho conforme suas equipes de Operações refinam e aprimoram seus processos de migração.

Ferramentas de migrações de nuvem, como o [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview), podem fazer a migração de datacenters inteiros consistindo em dezenas de milhares de VMs. No entanto, as operações de TI e empresariais existentes raramente podem lidar com uma mudança a um ritmo tão acelerado. Assim, muitas organizações dividem um esforço de migração em várias iterações, movendo uma carga de trabalho (ou uma coleção de cargas de trabalho) por iteração.

Os princípios por trás desse modelo incremental baseiam-se na execução de processos e pré-requisitos apresentados no seguinte infográfico.

![Modelo de migração da Cloud Adoption Framework](../../_images/operational-transformation-migrate.png)

A aplicação consistente desses princípios representa uma meta final para seus processos de migração na nuvem e não deve ser exibida como um ponto de partida necessário. Conforme seus esforços de migração amadurecem, veja a orientação nesta seção para ajudar a definir o melhor processo para dar suporte às suas necessidades organizacionais.

## <a name="next-steps"></a>Próximas etapas

Comece a aprender sobre esse modelo [investigando os pré-requisitos para migração](./prerequisites/index.md).

> [!div class="nextstepaction"]
> [Pré-requisitos para a migração](./prerequisites/index.md)
