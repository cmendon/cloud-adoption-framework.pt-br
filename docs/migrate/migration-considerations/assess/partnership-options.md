---
title: Noções básicas sobre opções de parceria e de suporte
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve as opções e abordagens para dar suporte aos esforços de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 70ae0b048b0cf5e3bd364f8c0cc1051c515c39ea
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74159900"
---
# <a name="understand-partnership-options"></a>Entender as opções de parceria

Durante a migração, a equipe de adoção da nuvem executa a migração real das cargas de trabalho para a nuvem. Ao contrário das tarefas colaborativas e de solução de problemas, ao definir a [propriedade digital](../../../digital-estate/index.md) ou criar a infraestrutura de nuvem principal, a migração tende a ser uma série de tarefas de execução repetitiva. Além dos aspectos repetitivos, provavelmente há esforços de teste e de ajuste que exigem um conhecimento aprofundado do provedor de nuvem escolhido. A natureza repetitiva desse processo às vezes pode ser mais bem contemplada por um parceiro, reduzindo a sobrecarga na equipe em tempo integral. Além disso, os parceiros talvez possam alinhar melhor o conhecimento técnico quando os processos repetitivos encontram anomalias de execução.

Os parceiros tendem a estar fortemente alinhados a um único fornecedor de nuvem ou a um pequeno número de fornecedores de nuvem. Para ilustrar melhor as opções de parceria, o restante deste artigo pressupõe que o Microsoft Azure é o provedor de nuvem escolhido.

Durante o plano, build ou migração, uma empresa geralmente tem quatro opções de parceria de execução:

- **Autoatendimento guiado.** A equipe técnica existente executa a migração, com a ajuda da Microsoft.
- **FastTrack for Azure.** Use o programa Microsoft FastTrack for Azure para acelerar a migração.
- **Parceiros de Solução.** Conecte-se aos Parceiros de Solução do Azure ou CSPs (Parceiros de Soluções de Nuvem) para acelerar a migração.
- **Autoatendimento com suporte.** A execução é concluída pela equipe técnica existente com suporte da Microsoft.

## <a name="guided-self-service"></a>Autoatendimento guiado

Se uma organização estiver planejando uma migração do Azure sozinha, a Microsoft sempre poderá ajudá-lo ao longo do percurso. Para ajudar a fazer a migração rápida para o Azure, a Microsoft e seus parceiros desenvolveram um amplo conjunto de arquiteturas, guias, ferramentas e serviços para reduzir o risco e acelerar a migração de máquinas virtuais, aplicativos e bancos de dados. Essas ferramentas e serviços dão suporte a uma ampla seleção de sistemas operacionais, linguagens de programação, estruturas e bancos de dados.

- **Ferramentas de avaliação e de migração.** O Azure oferece uma ampla variedade de ferramentas para serem usadas em diferentes estágios de sua transformação de nuvem, incluindo a avaliação da infraestrutura existente. Para saber mais, confira a seção "Avaliar" no capítulo "Migração" a seguir.
- **[Microsoft Cloud Adoption Framework](../../index.md).** Esta estrutura apresenta uma abordagem estruturada para a adoção e a migração de nuvem. Ele se baseia em práticas recomendadas em vários contratos de clientes com suporte da Microsoft e é organizado como uma série de etapas, desde arquitetura e design até a implementação. Para cada etapa, as diretrizes de suporte ajudam você com o design da arquitetura do seu aplicativo.
- **[Padrões de design na nuvem](https://docs.microsoft.com/azure/architecture/patterns).** O Azure oferece alguns padrões de design na nuvem úteis para criar cargas de trabalho confiáveis, escalonáveis e seguras na nuvem. Cada padrão descreve o problema que o padrão aborda, as considerações para a aplicação do padrão e um exemplo com base no Azure. A maioria dos padrões inclui exemplos de código ou snippets de código que mostram como implementar o padrão no Azure. No entanto, eles são relevantes para qualquer sistema distribuído, se hospedados no Azure ou em outras plataformas de nuvem.
- **[Conceitos básicos de nuvem](https://docs.microsoft.com/azure/architecture/guide).** Os conceitos básicos ajudam a ensinar as abordagens básicas à implementação dos conceitos principais. Este guia ajuda os técnicos a pensarem em soluções que vão além de um único serviço do Azure.
- **[Cenários de exemplo](https://docs.microsoft.com/azure/architecture/example-scenario).** O guia oferece referências de implementações de clientes reais, descrevendo as ferramentas, abordagens e processos que clientes anteriores seguiram para alcançar metas empresariais específicas.
- **[Arquiteturas de referência](https://docs.microsoft.com/azure/architecture/reference-architectures).** As arquiteturas de referência são organizadas por cenário, com arquiteturas relacionadas agrupadas juntos. Cada arquitetura inclui práticas recomendadas, juntamente com considerações sobre escalabilidade, disponibilidade, capacidade de gerenciamento e segurança. Mais também incluem uma solução implantável.

## <a name="fasttrack-for-azure"></a>FastTrack for Azure

O [FastTrack for Azure](https://azure.microsoft.com/roadmap/fasttrack-for-azure) oferece a assistência direta dos engenheiros do Azure, trabalhando em conjunto com parceiros, para ajudar os clientes a criar soluções do Azure com rapidez e confiança. O FastTrack traz melhores práticas e ferramentas de experiências de clientes reais para orientá-los desde a instalação, configuração e desenvolvimento até a produção de soluções do Azure, incluindo:

- Migração de datacenter
- Windows Server no Azure
- Linux no Azure
- SAP no Azure
- BCDR (continuidade de negócios e recuperação de desastre)
- Computação de alto desempenho*
- Aplicativos nativos de nuvem
- Operações de Desenvolvimento
- Modernização do aplicativo
- Análises de escala de nuvem**
- Aplicativos inteligentes
- Agentes inteligentes**
- Modernização de dados no Azure
- Segurança e gerenciamento
- Dados distribuídos globalmente
- IoT***

*Versão prévia limitada nos Estados Unidos, no Canadá, no Reino Unido e na Europa Ocidental

**Versão prévia limitada no Reino Unido e na Europa Ocidental

***Disponível no segundo semestre de 2019

Durante um envolvimento típico do FastTrack for Azure, a Microsoft ajuda a definir a visão empresarial para planejar e desenvolver soluções do Azure com êxito. A equipe avalia as necessidades arquitetônicas e oferece diretrizes, princípios de design, ferramentas e recursos para ajudar a criar, implantar e gerenciar soluções do Azure. A equipe faz a correspondência de parceiros especializados para serviços de implantação na solicitação e faz verificações periódicas para a implantação estar em conformidade e para ajudar a remover bloqueadores.

As principais fases de um compromisso típico do FastTrack for Azure são:

- **Descoberta.** Identificar os principais stakeholders, entender a meta ou a visão dos problemas a serem resolvidos e avaliar as necessidades de arquitetura.
- **Habilitação de solução.** Aprenda os princípios de design para criar aplicativos, examine a arquitetura de aplicativos e soluções e receba diretrizes e ferramentas para promover o trabalho de PoC (prova de conceito) por meio da produção.
- **Parceria contínua.** Os engenheiros e gerentes de programa do Azure fazem check-in com grande frequência para verificar se a implantação está no rumo certo e para ajudar a remover bloqueadores.

## <a name="microsoft-services-offerings-aligned-to-cloud-adoption-framework-approaches"></a>Ofertas do Serviços Microsoft alinhadas a abordagens do Cloud Adoption Framework

![Abordagem do Cloud Adoption Framework dos Serviços Microsoft](../../../_images/migrate/mcs-program-approach.jpg)

**Avaliar:** Os serviços da Microsoft usam uma [abordagem orientada, de dados e de ferramentas](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) , que consiste em workshops de arquitetura, informações em tempo real do Azure, modelos de ameaça de identidade e segurança e várias ferramentas para fornecer ideias sobre desafios, riscos, recomendações e problemas em um ambiente existente do Azure com um resultado importante, como um [roteiro de modernização de alto nível](https://download.microsoft.com/download/F/7/2/F72FAD7E-8BBD-4E04-8C7B-9AC4FE04A150/Cloud_Adoption_Discovery_and_Roadmap_Datasheet.pdf).

**Adote:** Por meio do Microsoft [Azure cloud Foundation](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf), estabeleça seus principais designs, padrões e arquitetura de governança do Azure, mapeando seus requisitos para a arquitetura de referência mais apropriada e planeje, projete e implante a infraestrutura, gerenciamento, segurança e identidade necessários para cargas de trabalho.

**Migrar/otimizar:** A solução de [modernização em nuvem](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) dos serviços da Microsoft oferece uma abordagem abrangente para mover aplicativos e infraestrutura para o Azure, bem como para otimizar e modernizar após a implantação na nuvem, apoiada pela migração simplificada.

**Inovar:** A [solução de CCOE (Cloud Center of Excellence)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) dos serviços da Microsoft oferece um envolvimento de treinamento de DevOps e usa princípios de DevOps combinados com controles de segurança e gerenciamento de serviços nativos de nuvem para ajudar a impulsionar a inovação dos negócios, aumentar a agilidade e reduzir o tempo de implantação em uma capacidade de gerenciamento de operações e de entrega de serviços segura, previsível e flexível.

## <a name="azure-support"></a>Suporte do Azure

Se você tiver dúvidas ou precisar de ajuda, [crie uma solicitação de suporte](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest). Se a solicitação de suporte exigir diretrizes técnicas detalhadas, acesse [Planos de Suporte do Azure](https://azure.microsoft.com/support/plans) para alinhar o melhor plano para suas necessidades.

## <a name="azure-solutions-partner"></a>Parceiro de Soluções do Azure

Os Provedores de soluções certificados pela Microsoft se especializam em fornecer soluções atualizadas com base em tecnologia Microsoft aos clientes do mundo todo. Otimize seus negócios na nuvem com a ajuda de um parceiro experiente.

Obtenha ajuda de parceiros com soluções do Azure prontas para uso ou personalizadas e os parceiros podem ajudar na implantação e no gerenciamento dessas soluções para seu negócio:

- **[Encontre um Parceiro de Soluções de Nuvem](https://www.microsoft.com/solution-providers/home).** Um CSP certificado pode ajudar a aproveitar ao máximo a nuvem, avaliando as metas empresariais para a adoção da nuvem, identificando a solução de nuvem certa que atenda às necessidades empresariais e que ajude a tornar a empresa mais ágil e eficiente.
- **[Encontrar um Parceiro de serviço gerenciado](https://www.microsoft.com/solution-providers/search?cacheId=16a3b49b-fef2-449d-bdf0-628008114cca).** Um MSP (parceiro de serviço gerenciado) do Azure ajuda na transição empresarial para o Azure, orientando todos os aspectos do percurso para a nuvem. Da consultoria ao gerenciamento de operações e migrações, os MSPs de nuvem mostram aos clientes todos os benefícios que a adoção da nuvem proporciona. Eles também atuam como uma loja conveniente que fornece suporte comum, provisionamento e experiência de cobrança, tudo com um modelo empresarial PAYG (pago conforme o uso) flexível.

## <a name="next-steps"></a>Próximos passos

Após a seleção de uma estratégia de parceiro e de suporte, a [lista de pendências de lançamento e de iteração](./release-iteration-backlog.md) pode ser atualizada para refletir as atribuições e os esforços planejados.

> [!div class="nextstepaction"]
> [Gerenciar a alteração usando listas de pendências de lançamento e de iteração](./release-iteration-backlog.md)
