---
title: Entender as opções de parceria e suporte
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve opções e abordagens para dar suporte a esforços de migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 5eabc654c174ac3eff895e6b2ff94700789f5de5
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549166"
---
# <a name="understand-partnership-options"></a>Entender as opções de parceria

Durante a migração, a equipe de adoção de nuvem executa a migração real das cargas de trabalho para a nuvem. Ao contrário das tarefas colaborativas e de solução de problemas ao definir o [espaço digital](../../../digital-estate/index.md) ou criar a infraestrutura de nuvem principal, a migração tende a ser uma série de tarefas de execução repetitiva. Além dos aspectos repetitivos, há prováveis esforços de teste e ajuste que exigem conhecimento profundo do provedor de nuvem escolhido. A natureza repetitiva desse processo às vezes pode ser melhor contemplada por um parceiro, reduzindo a sobrecarga na equipe em tempo integral. Além disso, os parceiros podem ser capazes de alinhar melhor o profundo conhecimento técnico quando os processos repetitivos encontram anomalias de execução.

Os parceiros tendem a estar fortemente alinhados a um único fornecedor de nuvem ou a um pequeno número de fornecedores de nuvem. Para ilustrar melhor as opções de parceria, o restante deste artigo pressupõe que Microsoft Azure é o provedor de nuvem escolhido.

Durante o planejamento, a compilação ou a migração, uma empresa geralmente tem quatro opções de parceria de execução:

- **Autoatendimento guiado.** A equipe técnica existente executa a migração, com a ajuda da Microsoft.
- **FastTrack for Azure.** Use o programa Microsoft FastTrack for Azure para acelerar a migração.
- **Parceiro de soluções.** Conecte-se com os parceiros de soluções do Azure ou com os provedores de soluções de nuvem (CSPs) para acelerar a migração.
- **Autoatendimento com suporte.** A execução é concluída pela equipe técnica existente com suporte da Microsoft.

## <a name="guided-self-service"></a>Autoatendimento guiado

Se uma organização estiver planejando uma migração do Azure por conta própria, a Microsoft sempre poderá ajudá-lo em toda a jornada. Para ajudar a fazer a migração rápida para o Azure, a Microsoft e seus parceiros desenvolveram um amplo conjunto de arquiteturas, guias, ferramentas e serviços para reduzir o risco e acelerar a migração de máquinas virtuais, aplicativos e bancos de dados. Essas ferramentas e serviços oferecem suporte a uma ampla seleção de sistemas operacionais, linguagens de programação, estruturas e bancos de dados.

- **Ferramentas de avaliação e migração.** O Azure fornece uma ampla gama de ferramentas a serem usadas em diferentes fases para sua transformação em nuvem, incluindo a avaliação de sua infraestrutura existente. Para obter mais informações, consulte a seção "avaliar" no capítulo "migração" a seguir.
- **[Microsoft Cloud a estrutura de adoção](../../index.md).** Essa estrutura apresenta uma abordagem estruturada para a adoção e a migração de nuvem. Ele se baseia em práticas recomendadas em vários contratos de clientes com suporte da Microsoft e é organizado como uma série de etapas, desde arquitetura e design até a implementação. Para cada etapa, a orientação de suporte ajuda você com o design da arquitetura do aplicativo.
- **[Padrões de design de nuvem](https://docs.microsoft.com/azure/architecture/patterns).** O Azure fornece alguns padrões de design de nuvem úteis para a criação de cargas de trabalho confiáveis, escalonáveis e seguras na nuvem. Cada padrão descreve o problema que o padrão aborda, considerações para aplicar o padrão e um exemplo baseado no Azure. A maioria dos padrões inclui exemplos de código ou trechos que mostram como implementar o padrão no Azure. No entanto, eles são relevantes para qualquer sistema distribuído, seja hospedado no Azure ou em outras plataformas de nuvem.
- **[Conceitos básicos de nuvem](https://docs.microsoft.com/azure/architecture/guide).** Os conceitos básicos ajudam a ensinar as abordagens básicas à implementação de conceitos básicos. Este guia ajuda os técnicos a pensar em soluções que vão além de um único serviço do Azure.
- **[Cenários de exemplo](https://docs.microsoft.com/azure/architecture/example-scenario).** O guia fornece referências de implementações reais de clientes, descrevendo as ferramentas, as abordagens e os processos que os clientes anteriores seguiram para realizar metas de negócios específicas.
- **[Arquiteturas de referência](https://docs.microsoft.com/azure/architecture/reference-architectures).** As arquiteturas de referência são organizadas por cenário, com arquiteturas relacionadas agrupadas. Cada arquitetura inclui práticas recomendadas, juntamente com considerações sobre escalabilidade, disponibilidade, capacidade de gerenciamento e segurança. A maioria também inclui uma solução implantável.

## <a name="fasttrack-for-azure"></a>FastTrack for Azure

[FastTrack for Azure](https://azure.microsoft.com/roadmap/fasttrack-for-azure) fornece assistência direta dos engenheiros do Azure, trabalhando em mãos com parceiros, para ajudar os clientes a criar soluções do Azure com rapidez e confiança. O FastTrack traz práticas recomendadas e ferramentas de experiências reais de clientes para orientar os clientes da instalação, configuração e desenvolvimento à produção de soluções do Azure, incluindo:

- Migração de datacenter
- Windows Server no Azure
- Linux no Azure
- SAP no Azure
- Continuidade dos negócios e recuperação de desastres (BCDR)
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
- IoT * * *

*Versão prévia limitada nos Estados Unidos, no Canadá, no Reino Unido e na Europa Ocidental

**Versão prévia limitada no Reino Unido e na Europa Ocidental

Disponível em H2 2019

Durante um envolvimento FastTrack for Azure típico, a Microsoft ajuda a definir a visão comercial para planejar e desenvolver soluções do Azure com êxito. A equipe avalia as necessidades de arquitetura e fornece diretrizes, princípios de design, ferramentas e recursos para ajudar a criar, implantar e gerenciar soluções do Azure. A equipe faz a correspondência de parceiros especializados para serviços de implantação na solicitação e faz verificações periódicas para garantir que a implantação esteja no controle e ajude a remover bloqueadores.

As principais fases de um compromisso típico do FastTrack for Azure são:

- **Descoberta.** Identifique as principais partes interessadas, entenda a meta ou a visão de problemas a serem resolvidos e, em seguida, avalie as necessidades de arquitetura.
- **Habilitação de solução.** Aprenda princípios de design para a criação de aplicativos, examine a arquitetura de aplicativos e soluções e receba orientações e ferramentas para impulsionar o trabalho de PoC (prova de conceito) para produção.
- **Parceria contínua.** Os engenheiros do Azure e os gerentes de programa verificam cada vez mais frequentemente para garantir que a implantação esteja no controle e ajude a remover bloqueadores.

## <a name="microsoft-services-offerings-aligned-to-cloud-adoption-framework-approaches"></a>Ofertas de serviços da Microsoft alinhadas a abordagens da estrutura de adoção de nuvem

![Abordagem da estrutura de adoção de nuvem de serviços da Microsoft](../../../_images/migrate/mcs-program-approach.jpg)

**Avaliar:** Os serviços da Microsoft usam uma [abordagem orientada, de dados e de ferramentas](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) , que consiste em workshops de arquitetura, informações em tempo real do Azure, modelos de ameaça de identidade e segurança e várias ferramentas para fornecer ideias sobre desafios, riscos, recomendações e problemas em um ambiente existente do Azure com um resultado importante, como um [roteiro de modernização de alto nível](https://download.microsoft.com/download/F/7/2/F72FAD7E-8BBD-4E04-8C7B-9AC4FE04A150/Cloud_Adoption_Discovery_and_Roadmap_Datasheet.pdf).

**Adote:** Por meio do Microsoft [Azure cloud Foundation](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf), estabeleça seus principais designs, padrões e arquitetura de governança do Azure, mapeando seus requisitos para a arquitetura de referência mais apropriada e planeje, projete e implante a infraestrutura, gerenciamento, segurança e identidade necessários para cargas de trabalho.

**Migrar/otimizar:** A solução de [modernização em nuvem](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) dos serviços da Microsoft oferece uma abordagem abrangente para mover aplicativos e infraestrutura para o Azure, bem como para otimizar e modernizar uma vez na nuvem apoiada pela migração simplificada.

**Inovar:** A [solução de CCOE (Cloud Center of Excellence)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) dos serviços da Microsoft oferece um envolvimento de treinamento DevOps e usa princípios de DevOps combinados com controles de segurança e gerenciamento de serviços nativos de nuvem prescritiva para ajudar a impulsionar a inovação dos negócios, Aumente a agilidade e reduza o tempo de implantação em uma capacidade de gerenciamento de operações e entrega de serviços segura, previsível e flexível.

## <a name="azure-support"></a>Suporte do Azure

Se você tiver dúvidas ou precisar de ajuda, [crie uma solicitação de suporte](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest). Se sua solicitação de suporte exigir diretrizes técnicas profundas, visite [planos de suporte do Azure](https://azure.microsoft.com/support/plans) para alinhar o melhor plano às suas necessidades.

## <a name="azure-solutions-partner"></a>Parceiro de soluções do Azure

Os provedores de soluções certificados pela Microsoft são especializados no fornecimento de soluções de clientes baseadas em tecnologia Microsoft atualizadas em todo o mundo. Otimize seus negócios na nuvem com a ajuda de um parceiro experiente.

Obtenha ajuda de parceiros com soluções prontas ou personalizadas do Azure e parceiros que podem ajudar a implantar e gerenciar essas soluções:

- **[Encontre um parceiro de soluções de nuvem](https://www.microsoft.com/solution-providers/home).** Um CSP certificado pode ajudar a aproveitar ao máximo a nuvem avaliando as metas de negócios para a adoção da nuvem, identificando a solução de nuvem certa que atende às necessidades dos negócios e ajuda a tornar a empresa mais ágil e eficiente.
- **[Encontre um parceiro de serviço gerenciado](https://www.microsoft.com/solution-providers/search?cacheId=16a3b49b-fef2-449d-bdf0-628008114cca).** Um parceiro de serviço gerenciado do Azure (MSP) ajuda uma transição de negócios para o Azure, orientando todos os aspectos da jornada de nuvem. Desde consultoria até migrações e gerenciamento de operações, o Cloud MSPs mostra aos clientes todos os benefícios que vêm com a adoção da nuvem. Eles também atuam como uma loja única para suporte comum, provisionamento e experiência de cobrança, tudo com um modelo de negócios PAYG (pago conforme o uso) flexível.

## <a name="next-steps"></a>Próximos passos

Após a seleção de uma estratégia de parceiro e suporte, os registros posteriores de [versão e iteração](./release-iteration-backlog.md) podem ser atualizados para refletir as atribuições e os esforços planejados.

> [!div class="nextstepaction"]
> [Gerenciar alterações usando registros posteriores de versão e iteração](./release-iteration-backlog.md)
