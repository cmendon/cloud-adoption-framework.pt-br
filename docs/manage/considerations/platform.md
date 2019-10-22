---
title: Operações de plataforma – gerenciamento de nuvem e operações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Operações de plataforma – gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ca62f35c059e185850bb47045fa0edef7be1d223
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683589"
---
# <a name="platform-operations-in-cloud-management"></a>Operações de plataforma no gerenciamento de nuvem

Uma linha de base de gerenciamento de nuvem que abrange o [inventário e a visibilidade](./inventory.md), a [conformidade operacional](./operational-compliance.md)e a [proteção e recuperação](./protect.md) podem fornecer um nível suficiente de gerenciamento de nuvem para a maioria das cargas de trabalho no portfólio de ti. No entanto, isso raramente é suficiente para dar suporte ao portfólio completo. Este artigo se baseia na próxima etapa mais comum no gerenciamento de nuvem, operações de portfólio.

Um estudo rápido dos ativos no portfólio de ti destacará os padrões entre as cargas de trabalho com suporte. Nessas cargas de trabalho, haverá várias plataformas comuns. Dependendo das decisões técnicas passadas dentro da empresa, essas plataformas podem ser muito diferentes. Para algumas organizações, haverá uma grande dependência no SQL Server, no Oracle ou em outras plataformas de dados de código aberto. Em outras organizações, o semelhanças pode ter raiz nas plataformas de hospedagem para máquinas virtuais ou contêineres. Ainda outros podem ter uma dependência comum em aplicativos ou em sistemas ERP (planejamento de recursos empresariais), como SAP, Oracle ou outros.

Entender esses semelhanças permite que a equipe de gerenciamento de nuvem seja especializada em níveis mais altos de suporte para essas plataformas priorizadas.

## <a name="establish-a-service-catalog"></a>Estabelecer um catálogo de serviços

O objetivo das operações de plataforma é criar soluções confiáveis e reproduzíveis que possam ser aproveitadas por uma equipe de adoção de nuvem para fornecer uma plataforma, que fornece um nível mais alto de compromisso de negócios. Esse compromisso pode diminuir a probabilidade ou a frequência de tempo de inatividade, melhorando a confiabilidade. O compromisso também pode diminuir a quantidade de perda de dados ou o tempo de recuperação, em caso de falha do sistema. Esse compromisso geralmente inclui operações contínuas e centralizadas para dar suporte à plataforma.

Como a equipe de gerenciamento de nuvem estabelece níveis mais altos de gerenciamento operacional e especialização relacionados a plataformas específicas, essas plataformas são adicionadas a um catálogo de serviços em crescimento. Esse catálogo de serviços fornece implantação de autoatendimento de plataformas em uma configuração específica, que obedece a operações de plataforma contínuas. Durante a conversa de alinhamento de negócios, as equipes de gerenciamento de nuvem e de estratégia de nuvem podem propor soluções de catálogo de serviços como uma maneira para a empresa melhorar a confiabilidade, o tempo de atividade e os compromissos de recuperação em um processo controlado e reproduzível.

Para referência, algumas organizações irão se referir a um catálogo de serviços de estágio inicial como uma "lista aprovada". A principal diferença é que um catálogo de serviços vem com compromissos operacionais contínuos do Cloud Center of Excellence. Uma "lista aprovada" é semelhante, pois fornece uma lista de soluções previamente aprovadas que uma equipe pode usar na nuvem, mas normalmente não há um benefício operacional associado aos aplicativos de "lista aprovada". Da mesma forma que o debate entre ti central e CCoE, a diferença é uma das prioridades. Um catálogo de serviços assume uma boa intenção, mas fornece guardrails operacional, de governança e de segurança que aceleram a inovação. Uma "lista aprovada" impede a inovação até que as operações, a conformidade e as entradas de segurança possam ser passadas para uma solução. Ambas são soluções viáveis, mas exigem que uma empresa tome decisões sutis de priorização para investir mais em inovação ou conformidade.

### <a name="building-the-service-catalog"></a>Criando o catálogo de serviços

O gerenciamento de nuvem raramente é bem-sucedido no fornecimento de um catálogo de serviços em um silo. O desenvolvimento adequado do catálogo exige uma parceria entre a ti central ou o Cloud Center of Excellence (CCoE). Essa abordagem tende a ser mais bem-sucedida quando uma organização de ti atinge um nível de maturidade CCoE, mas pode ser implementada mais cedo.

Ao criar o catálogo de serviços em um modelo CCoE, a equipe da plataforma de nuvem cria a plataforma de estado desejado. As equipes de segurança de nuvem e governança de nuvem validam a governança e a conformidade na implantação. A equipe de gerenciamento de nuvem estabelece operações contínuas para essa plataforma. A equipe de automação de nuvem empacota a plataforma para implantação escalonável e reproduzível.

Depois de empacotado, a equipe de gerenciamento de nuvem pode adicionar o pacote ao crescente catálogo de serviços. A partir daí, a equipe de adoção de nuvem pode aproveitar esse pacote ou outros no catálogo durante a implantação. Depois que a solução passa para a produção, a empresa obtém os benefícios adicionais do gerenciamento operacional melhorado e o potencial de interrupções de negócios reduzidas.

> [!NOTE]
> A criação de um catálogo de serviços requer uma grande quantidade de esforço e tempo de várias equipes. Usar o catálogo de serviços ou a lista branca como um mecanismo de retenção diminuirá a inovação. Quando a inovação é uma prioridade, os catálogos de serviços devem ser desenvolvidos paralelamente a outros esforços de adoção.

## <a name="defining-your-own-platform-operations"></a>Definindo suas próprias operações de plataforma

As ferramentas e os processos de gerenciamento podem melhorar as operações de plataforma. Mas isso geralmente não é suficiente para atingir o estado desejado de estabilidade e confiabilidade. As operações de plataforma verdadeiras exigem um foco nos pilares de qualidade da arquitetura. Quando uma plataforma justifica um investimento mais profundo em operações, os cinco pilares a seguir devem ser considerados antes que a plataforma se torne uma parte de qualquer catálogo de serviços:

1. Escalabilidade: a capacidade de um sistema de lidar com a carga aumentada.
2. Disponibilidade: a proporção de tempo em que um sistema está funcionando e funcionando.
3. Resiliência: a capacidade de um sistema de se recuperar de falhas e continuar a funcionar.
4. Gerenciamento: processos de operações que mantêm um sistema em execução na produção.
5. Segurança: proteger aplicativos e dados contra ameaças.

A [estrutura de arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fornece uma abordagem para avaliar cargas de trabalho específicas para adesão a esses pilares, em um esforço para melhorar as operações gerais. Esses pilares podem ser aplicados a operações de plataforma e operações de carga de trabalho.

## <a name="getting-started-with-specific-platforms"></a>Introdução a plataformas específicas

Entre clientes típicos do Azure, as seguintes são plataformas comuns, que podem justificar facilmente um investimento em operações de plataforma. As equipes de gerenciamento de nuvem tendem a começar com isso ao criar requisitos de operações de plataforma ou um catálogo de serviços completo.

### <a name="paas-data-operations"></a>Operações de dados de PaaS

Geralmente, os dados são a primeira plataforma para garantir os investimentos em operações de plataforma. Quando os dados são hospedados em um ambiente PaaS (plataforma como serviço), os participantes da empresa tendem a solicitar um RPO reduzido para minimizar a perda de dados. Dependendo da natureza do aplicativo, eles também podem solicitar uma redução no RTO. Em ambos os casos, a arquitetura que dá suporte a soluções de dados baseadas em PaaS pode acomodar facilmente um nível maior de suporte de gerenciamento.

Na maioria dos cenários, o custo de melhorar os compromissos de gerenciamento é facilmente justificado, mesmo para aplicativos que não são de missão crítica. Essa melhoria de operações de plataforma é tão comum, que muitas equipes de gerenciamento de nuvem veem isso mais como uma linha de base aprimorada, em oposição a tratá-la como uma verdadeira melhoria de operações de plataforma.

### <a name="iaas-data-operations"></a>Operações de dados de IaaS

Quando os dados são hospedados em uma solução de IaaS (infraestrutura como serviço) tradicional, o esforço para melhorar o RTO e o RPO pode ser significativamente maior. Ainda assim, o desejo dos acionistas comerciais de alcançar melhores compromissos de gerenciamento raramente é afetado por uma decisão de PaaS versus IaaS. Se algo, uma compreensão das diferenças fundamentais na arquitetura, pode solicitar que a empresa solicite soluções de PaaS ou compromissos que correspondam ao que está disponível em soluções de PaaS. A modernização de qualquer plataforma de dados IaaS deve ser considerada como uma primeira etapa nas operações de plataforma.

Quando a modernização não é uma opção, as equipes de gerenciamento de nuvem geralmente priorizam as plataformas de dados baseadas em IaaS, como um primeiro serviço necessário no catálogo de serviços. Fornecer aos negócios uma opção entre os servidores de dados autônomos e as soluções de dados em cluster e de alta disponibilidade torna a conversa de compromisso de negócios muito mais fácil de facilitar. Uma compreensão básica dos aprimoramentos operacionais e dos maiores custos, desconectará a empresa para tomar a melhor decisão para os processos de negócios e as cargas de trabalho de suporte.

### <a name="other-common-platform-operations"></a>Outras operações de plataforma comuns

Além das plataformas de dados, os hosts de máquina virtual tendem a ser uma plataforma comum para aprimoramentos de operações. Geralmente, as equipes de gerenciamento de nuvem e de plataforma de nuvem investirão em melhorias em hosts ou soluções de contêineres do VMWare para melhorar a estabilidade e a confiabilidade dos hosts, que dão suporte às VMs, que são cargas de trabalho de energia. As operações adequadas em um host ou contêiner podem melhorar o RPO/RTO de várias cargas de trabalho. Essa abordagem cria compromissos de negócios aprimorados, mas distribui o investimento. Juntos, os compromissos aprimorados e os custos reduzidos facilitam muito a justificação das melhorias no gerenciamento de nuvem e nas operações de plataforma.

## <a name="next-steps"></a>Próximos passos

Em paralelo com melhorias nas operações de plataforma, as equipes de gerenciamento de nuvem também se concentrarão em melhorar [as operações de carga de trabalho](./workload.md) para os 20% maiores ou menos de cargas de trabalho de produção.

> [!div class="nextstepaction"]
> [Melhorar as operações de carga de trabalho](./workload.md)
