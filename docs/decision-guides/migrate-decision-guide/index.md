---
title: Guia de decisão de ferramentas de migração
description: Guia de decisão de ferramentas de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.openlocfilehash: 38c0e6b56a51155be10501328d68c08bd500847e
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76806740"
---
# <a name="migration-tools-decision-guide"></a>Guia de decisão de ferramentas de migração

A estratégia e as ferramentas que você usa durante a migração de um aplicativo para o Azure dependem muito de suas motivações empresariais, estratégias de tecnologia e linhas do tempo. Além disso, é necessário profundo conhecimento das cargas de trabalho e dos ativos reais (infraestrutura, aplicativos e dados) que estão sendo migrados. A árvore de decisão a seguir serve como uma orientação geral para você selecionar as melhores ferramentas com base em decisões de migração. Trate essa árvore de decisão como um ponto de partida.

A opção de migrar usando as tecnologias PaaS (plataforma como serviço) ou IaaS (infraestrutura como serviço) é orientada pelo equilíbrio entre custo, tempo, débito técnico existente e retornos no longo prazo. IaaS costuma ser o caminho mais rápido para a nuvem com a menor quantidade de alteração necessária para a carga de trabalho. A PaaS pode até exigir modificações nas estruturas de dados ou no código-fonte, mas gera retornos substanciais no longo prazo sob a forma de custos operacionais reduzidos e maior flexibilidade técnica. No diagrama a seguir, o termo _modernizar_ é usado para refletir uma decisão de modernizar um ativo durante a migração e migrar o ativo modernizado para uma plataforma PaaS.

![Árvore de decisão de ferramentas de migração de exemplo.](../../_images/migrate/migration-tools-decision-tree.png)

## <a name="key-questions"></a>Principais perguntas

Responder às perguntas a seguir permitirá que você tome decisões com base na árvore acima.

- **A modernização da plataforma de aplicativo durante a migração se mostraria um bom investimento de tempo, energia e orçamento?** Tecnologias de PaaS, como o Serviço de Aplicativo do Azure ou o Azure Functions, podem aumentar a flexibilidade da implantação e reduzir a complexidade do gerenciamento de máquinas virtuais para hospedar aplicativos. No entanto, os aplicativos podem precisar de refatoração antes de poderem aproveitar essas funcionalidades nativas da nuvem, potencialmente adicionando tempo e custos significativos para um esforço de migração. Se o aplicativo pode migrar para as tecnologias de PaaS com um mínimo de alterações, provavelmente é um bom candidato para modernização. Se ampla refatoração for necessária, uma migração usando máquinas virtuais baseadas em IaaS poderá ser uma opção melhor.
- **A modernização da plataforma de dados durante a migração se mostraria um bom investimento de tempo, energia e orçamento?** Assim como ocorre com a migração de aplicativo, as opções de armazenamento gerenciado de PaaS do Azure, como Banco de Dados SQL do Azure, Cosmos DB e Armazenamento do Azure, oferecem benefícios significativos de flexibilidade e gerenciamento, mas a migração para esses serviços pode exigir a refatoração dos dados existentes e dos aplicativos que usam esses dados. As plataformas de dados geralmente exigem significativamente menos refatoração do que a plataforma de aplicativo. Como tal, é muito comum a plataforma de dados ser modernizada, mesmo que a plataforma de aplicativo permaneça a mesma. Se os dados podem ser migrados para um serviço de dados gerenciados com um mínimo de alterações, eles são bons candidatos à modernização. Os dados que exigem muito tempo ou custo para serem refatorados a fim de usar esses serviços de PaaS podem ser migrados de uma maneira melhor usando máquinas virtuais baseadas em IaaS para corresponder melhor às funcionalidades de hospedagem existentes.
- **Seu aplicativo atualmente está em execução em máquinas virtuais dedicadas ou compartilha a hospedagem com outros aplicativos?** Um aplicativo em execução em máquinas virtuais dedicadas pode ser migrado com mais facilidade para as opções de hospedagem de PaaS que outros aplicativos em execução em servidores compartilhados.
- **Sua migração de dados excederá a largura de banda de rede?** A capacidade de rede entre as fontes de dados locais e o Azure pode ser um gargalo na migração de dados. Se os dados que você precisa transferir enfrentam limitações de largura de banda que impedem a migração em tempo hábil ou eficiente, você precisa examinar mecanismos de transferência alternativos ou offline. O [artigo sobre replicação de migração](../../migrate/migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication) da Cloud Adoption Framework discute como os limites de replicação podem afetar os esforços de migração. Como parte de sua avaliação de migração, consulte suas equipes de TI para verificar se a largura de banda da WAN e local é capaz de atender seus requisitos de migração. Veja também o [cenário de migração de escopo expandido para quando os requisitos de armazenamento excedem a capacidade de rede durante uma migração](../../migrate/expanded-scope/network-capacity-exceeded.md#suggested-prerequisites).
- **Seu aplicativo usa um pipeline de DevOps existente?** Em muitos casos, o Azure Pipelines pode ser facilmente refatorado para implantar aplicativos em ambientes de hospedagem baseados em nuvem.
- **Seus dados têm requisitos de armazenamento de dados complexos?** Aplicativos de produção geralmente exigem armazenamento de dados com alta disponibilidade, que ofereça funcionalidade sempre ativa e recursos de continuidade e tempo de atividade similares. Opções de banco de dados gerenciado baseado em PaaS do Azure, como o Banco de Dados SQL do Azure, o Banco de Dados do Azure para MySQL e o Azure Cosmos DB, oferecem contratos de nível de serviço com tempo de atividade de 99,99%. Por outro lado, o SQL Server baseado em IaaS nas VMs do Azure oferece contratos de nível de serviço de instância única de 99,95%. Se os dados não puderem ser modernizados para usar as opções de armazenamento de PaaS, garantir um tempo de atividade de IaaS maior envolverá cenários mais complexos de armazenamento de dados como clusters Always-On do SQL Server sincronização contínua de dados entre instâncias. Isso pode envolver custos significativos de hospedagem e manutenção, portanto, balancear requisitos de tempo de atividade, esforços de modernização e impacto geral orçamentários é importante ao considerar suas opções de migração de dados.

## <a name="innovation-and-migration"></a>Inovação e migração

Alinhada com a ênfase de Cloud Adoption Frameworks em esforços de [migração incremental](../../migrate/index.md#migration-implementation), uma decisão inicial sobre a estratégia de migração e as ferramentas não descarta esforços de inovação futuros para atualizar um aplicativo para aproveitar oportunidades apresentadas pela plataforma do Azure. Embora um esforço de migração inicial possa se concentrar principalmente em nova hospedagem usando uma abordagem de IaaS, você deve planejar rever seu portfólio de aplicativos hospedados na nuvem regularmente para investigar as oportunidades de otimização.

## <a name="learn-more"></a>Saiba mais

- **[Conceitos básicos de nuvem: Visão geral das opções de computação do Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview):** Fornece informações sobre as capacidades das opções de computação do Azure IaaS e PaaS.
- **[Conceitos básicos de nuvem: Escolha o armazenamento de dados certo](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview):** Discute as opções de armazenamento de PaaS disponíveis na plataforma do Azure.
- **[Migração de escopo expandido: Os requisitos de dados excedem a capacidade da rede durante um esforço de migração](../../migrate/expanded-scope/network-capacity-exceeded.md):** Discute os mecanismos de migração de dados alternativos para cenários em que a migração de dados é prejudicada pela largura de banda de rede disponível.
- **[Banco de Dados SQL: Escolha a opção certa do SQL Server no Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas#business-motivations-for-choosing-databases-managed-instances-or-sql-virtual-machines):** Discussão sobre as opções e as justificativas empresariais para escolher hospedar suas cargas de trabalho do SQL Server em uma infraestrutura hospedada (IaaS) ou em um ambiente de serviço hospedado (PaaS).
