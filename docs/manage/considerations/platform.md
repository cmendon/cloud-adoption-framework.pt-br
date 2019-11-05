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
ms.openlocfilehash: 6a2cf644a7c046dfb62f6049c2eae6b283e6552b
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565067"
---
# <a name="platform-operations-in-cloud-management"></a>Operações de plataforma no gerenciamento de nuvem

Uma linha de base de gerenciamento de nuvem que abrange o [inventário e a visibilidade](./inventory.md), a [conformidade operacional](./operational-compliance.md)e a [proteção e recuperação](./protect.md) podem fornecer um nível suficiente de gerenciamento de nuvem para a maioria das cargas de trabalho no portfólio de ti. No entanto, essa linha de base raramente é suficiente para dar suporte ao portfólio completo. Este artigo se baseia na próxima etapa mais comum no gerenciamento de nuvem, operações de portfólio.

Um estudo rápido dos ativos no portfólio de ti realça os padrões entre as cargas de trabalho que têm suporte. Nessas cargas de trabalho, haverá várias plataformas comuns. Dependendo das decisões técnicas passadas dentro da empresa, essas plataformas podem variar muito.

Para algumas organizações, haverá uma grande dependência em SQL Server, Oracle ou outras plataformas de dados de código aberto. Em outras organizações, o semelhanças pode ter raiz nas plataformas de hospedagem para VMs (máquinas virtuais) ou contêineres. Outros ainda podem ter uma dependência comum em aplicativos ou em sistemas ERP (planejamento de recursos empresariais), como SAP, Oracle ou outros.

Ao compreender esses semelhanças, a equipe de gerenciamento de nuvem pode ser especializada em níveis mais altos de suporte para essas plataformas priorizadas.

## <a name="establish-a-service-catalog"></a>Estabelecer um catálogo de serviços

O objetivo das operações de plataforma é criar soluções confiáveis e reproduzíveis, que a equipe de adoção de nuvem pode usar para fornecer uma plataforma que forneça um nível mais alto de compromisso de negócios. Esse compromisso pode diminuir a probabilidade ou a frequência de tempo de inatividade, o que melhora a confiabilidade. No caso de uma falha do sistema, o compromisso também pode ajudar a diminuir a quantidade de perda de dados ou o tempo de recuperação. Esse compromisso geralmente inclui operações contínuas e centralizadas para dar suporte à plataforma.

Como a equipe de gerenciamento de nuvem estabelece níveis mais altos de gerenciamento operacional e especialização relacionados a plataformas específicas, essas plataformas são adicionadas a um catálogo de serviços em crescimento. O catálogo de serviços fornece a implantação de autoatendimento de plataformas em uma configuração específica, que obedece às operações de plataforma em andamento. Durante a conversa de alinhamento de negócios, as equipes de gerenciamento de nuvem e de estratégia de nuvem podem propor soluções de catálogo de serviços como uma maneira para a empresa melhorar a confiabilidade, o tempo de atividade e os compromissos de recuperação em um processo controlado e reproduzível.

Para referência, algumas organizações se referem a um catálogo de serviços de estágio inicial como uma _lista aprovada_. A principal diferença é que um catálogo de serviços vem com compromissos operacionais contínuos do Cloud Center of Excellence (CCoE). Uma lista aprovada é semelhante, pois fornece uma lista de soluções preaprovadas que uma equipe pode usar na nuvem. No entanto, normalmente não há um benefício operacional associado aos aplicativos em uma lista aprovada.

Da mesma forma que o debate entre ti central e CCoE, a diferença é uma das prioridades. Um catálogo de serviços assume uma boa intenção, mas fornece guardrails operacional, de governança e de segurança que aceleram a inovação. Uma lista aprovada impede a inovação até que as operações, a conformidade e as Gates de segurança possam ser passadas para uma solução. Ambas as soluções são viáveis, mas exigem que a empresa tome decisões sutis de priorização para investir mais em inovação ou conformidade.

### <a name="build-the-service-catalog"></a>Compilar o catálogo de serviços

O gerenciamento de nuvem raramente é bem-sucedido no fornecimento de um catálogo de serviços em um silo. O desenvolvimento adequado do catálogo requer uma parceria em ti central ou CCoE. Essa abordagem tende a ser mais bem-sucedida quando uma organização de ti atinge um nível de maturidade CCoE, mas pode ser implementada mais cedo.

Ao criar o catálogo de serviços em um modelo CCoE, a equipe da plataforma de nuvem cria a plataforma de estado desejado. As equipes de segurança de nuvem e governança de nuvem validam a governança e a conformidade na implantação. A equipe de gerenciamento de nuvem estabelece operações contínuas para essa plataforma. E a equipe de automação de nuvem empacota a plataforma para implantação escalonável e reproduzível.

Depois que a plataforma é empacotada, a equipe de gerenciamento de nuvem pode adicioná-la ao crescente catálogo de serviços. A partir daí, a equipe de adoção de nuvem pode usar o pacote ou outras pessoas no catálogo durante a implantação. Depois que a solução passa para a produção, a empresa percebe os benefícios adicionais do gerenciamento operacional melhorado e, potencialmente, as interrupções dos negócios.

> [!NOTE]
> A criação de um catálogo de serviços requer uma grande quantidade de esforço e tempo de várias equipes. Usar o catálogo de serviços ou a lista aprovada como um mecanismo de retenção diminuirá a inovação. Quando a inovação é uma prioridade, os catálogos de serviços devem ser desenvolvidos paralelamente a outros esforços de adoção.

## <a name="define-your-own-platform-operations"></a>Definir suas próprias operações de plataforma

Embora as ferramentas de gerenciamento e os processos possam ajudar a melhorar as operações de plataforma, isso geralmente não é suficiente para atingir os Estados desejados de estabilidade e confiabilidade. As operações de plataforma verdadeiras exigem um foco em pilares de qualidade de arquitetura. Quando uma plataforma justifica um investimento mais profundo em operações, os cinco pilares a seguir devem ser considerados antes que a plataforma se torne uma parte de qualquer catálogo de serviços:

- **Escalabilidade:** A capacidade de um sistema de lidar com a carga aumentada.
- **Disponibilidade:** A porcentagem de tempo em que um sistema está funcionando e funcionando.
- **Resiliência:** A capacidade de um sistema de se recuperar de falhas e continuar a funcionar.
- **Gerenciamento:** Os processos de operações que mantêm um sistema em execução na produção.
- **Segurança:** Proteção de aplicativos e dados contra ameaças.

A [estrutura de arquitetura do Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) fornece uma abordagem para avaliar cargas de trabalho específicas para adesão a esses pilares, em um esforço para melhorar as operações gerais. Esses pilares podem ser aplicados a operações de plataforma e operações de carga de trabalho.

## <a name="get-started-with-specific-platforms"></a>Introdução a plataformas específicas

As plataformas discutidas nas próximas seções são comuns a clientes típicos do Azure, e podem facilmente justificar um investimento em operações de plataforma. As equipes de gerenciamento de nuvem tendem a começar a usá-las quando estão criando requisitos de operações de plataforma ou um catálogo de serviços completo.

### <a name="paas-data-operations"></a>Operações de dados de PaaS

Geralmente, os dados são a primeira plataforma para garantir os investimentos em operações de plataforma. Quando os dados são hospedados em um ambiente PaaS (plataforma como serviço), os participantes da empresa tendem a solicitar um RPO (objetivo de ponto de recuperação) reduzido para minimizar a perda de dados. Dependendo da natureza do aplicativo, eles também podem solicitar uma redução no RTO (objetivo de tempo de recuperação). Em ambos os casos, a arquitetura que dá suporte a soluções de dados baseadas em PaaS pode acomodar facilmente um nível maior de suporte de gerenciamento.

Na maioria dos cenários, o custo de melhorar os compromissos de gerenciamento é facilmente justificado, mesmo para aplicativos que não são de missão crítica. Essa melhoria de operações de plataforma é tão comum que muitas equipes de gerenciamento de nuvem veem isso mais como uma linha de base aprimorada, em vez de como uma verdadeira melhoria de operações de plataforma.

### <a name="iaas-data-operations"></a>Operações de dados de IaaS

Quando os dados são hospedados em uma solução de IaaS (infraestrutura como serviço) tradicional, o esforço para melhorar o RPO e o RTO pode ser significativamente maior. Ainda assim, o desejo dos acionistas comerciais de alcançar melhores compromissos de gerenciamento raramente é afetado por uma decisão de PaaS versus IaaS. Se algo, uma compreensão das diferenças fundamentais na arquitetura pode solicitar que a empresa solicite soluções PaaS ou compromissos que correspondam ao que está disponível em soluções PaaS. A modernização de qualquer plataforma de dados IaaS deve ser considerada como uma primeira etapa nas operações de plataforma.

Quando a modernização não é uma opção, as equipes de gerenciamento de nuvem normalmente priorizam as plataformas de dados baseadas em IaaS como um primeiro serviço necessário no catálogo de serviços. Fornecer aos negócios uma opção entre servidores de dados autônomos e soluções de dados em cluster e de alta disponibilidade torna a conversa de compromisso de negócios muito mais fácil de facilitar. Uma compreensão básica dos aprimoramentos operacionais e dos maiores custos fará com que a empresa faça a melhor decisão para os processos de negócios e as cargas de trabalho de suporte.

### <a name="other-common-platform-operations"></a>Outras operações de plataforma comuns

Além das plataformas de dados, os hosts de máquina virtual tendem a ser uma plataforma comum para aprimoramentos de operações. Geralmente, as equipes de gerenciamento de nuvem e de plataforma de nuvem investem em melhorias em hosts VMware ou soluções de contêiner. Esses investimentos podem melhorar a estabilidade e a confiabilidade dos hosts, que dão suporte às VMs, que, por sua vez, alimentam as cargas de trabalho. As operações adequadas em um host ou contêiner podem melhorar o RPO ou o RTO de várias cargas de trabalho. Essa abordagem cria compromissos de negócios aprimorados, mas distribui o investimento. Compromissos aprimorados e custos reduzidos são combinados para tornar muito mais fácil justificar melhorias nas operações de gerenciamento de nuvem e plataforma.

## <a name="next-steps"></a>Próximas etapas

Em paralelo com melhorias nas operações de plataforma, as equipes de gerenciamento de nuvem também se concentram em melhorar [as operações de carga de trabalho](./workload.md) para os 20% maiores ou menos de cargas de trabalho de produção.

> [!div class="nextstepaction"]
> [Melhorar as operações de carga de trabalho](./workload.md)
