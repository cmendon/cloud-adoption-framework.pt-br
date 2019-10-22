---
title: Proteger e recuperar-gerenciamento de nuvem e operações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Proteger e recuperar-gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2e055cb6105b9424259d2b8e86bdde7d64798479
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682464"
---
# <a name="protect-and-recover-in-cloud-management"></a>Proteger e recuperar no gerenciamento de nuvem

Depois que os requisitos de [inventário e visibilidade](./inventory.md) e [conformidade operacional](./operational-compliance.md) tiverem sido atendidos, as equipes de gerenciamento de nuvem poderão ficar em frente e se preparar para o potencial de uma interrupção de uma carga de trabalho. Ao planejar o gerenciamento de nuvem, a equipe deve começar com uma suposição de que algo irá falhar.

Nenhuma solução técnica pode oferecer consistentemente um SLA de tempo de atividade de 100%. Soluções com a declaração de arquiteturas mais redundantes a serem entregues em tempo de atividade de "seis noves" ou 99,9999%. Mas mesmo uma solução de "seis noves" fica inativa por 31,6 segundos em um determinado ano. Infelizmente, as soluções raramente garantem o investimento operacional grande e contínuo necessário para alcançar "seis noves" de tempo de atividade.

A preparação para uma interrupção permitirá que a equipe detecte falhas mais cedo e se recupere mais rapidamente. O foco dessa disciplina é nas próximas etapas que surgem após a falha de um sistema. Como você protege cargas de trabalho, para que elas possam ser recuperadas rapidamente quando ocorre uma interrupção.

## <a name="translating-protection-and-recovery-conversations"></a>Convertendo conversas de proteção e recuperação

As cargas de trabalho que capacitam as operações de negócios consistem em aplicativos, dados, máquinas virtuais e outros ativos. Cada um desses ativos pode exigir uma abordagem diferente para proteção e recuperação. O aspecto importante dessa disciplina é estabelecer um compromisso consistente na linha de base de gerenciamento, para fornecer um ponto de partida durante as discussões de negócios.

No mínimo, cada ativo que dá suporte a uma determinada carga de trabalho deve ter uma abordagem de linha de base com um compromisso claro para a velocidade de recuperação (objetivos de tempo de recuperação ou RTO) e o risco de perda de dados (RPO ou objetivos de ponto de recuperação).

### <a name="recovery-time-objectives-rto"></a>RTO (objetivos de tempo de recuperação)

Quando ocorre um desastre, o RTO é a quantidade de tempo que deve levar para recuperar qualquer sistema específico para seu estado de pré-desastre. Para cada carga de trabalho, isso inclui o tempo necessário para restaurar a funcionalidade mínima necessária para as VMs e os aplicativos. Ele também inclui a quantidade de tempo necessária para restaurar os dados exigidos pelos aplicativos.

Em termos comerciais, o RTO representa a quantidade de tempo que o processo de negócios estará fora de serviço. Para cargas de trabalho de missão crítica, essa variável deve ser relativamente baixa, permitindo que os processos de negócios retomem rapidamente. Para cargas de trabalho de prioridade mais baixa, um nível padrão de RTO pode não ter um impacto perceptível no desempenho da empresa.

A linha de base de gerenciamento deve estabelecer um objetivo de tempo de recuperação padrão para cargas de trabalho não críticas. A empresa pode usar essa linha de base como uma maneira de justificar investimentos adicionais em tempos de recuperação.

### <a name="recovery-point-objectives-rpo"></a>RPOs (objetivos de ponto de recuperação)

Na maioria dos sistemas de gerenciamento de nuvem, os dados são capturados periodicamente e armazenados por meio de alguma forma de proteção de dados. A última vez que os dados foram capturados são chamados de ponto de recuperação. Quando um sistema falha, ele só pode ser restaurado para o ponto de recuperação mais recente.

Se um sistema tiver um objetivo de ponto de recuperação medido em horas ou dias, uma falha do sistema resultaria na perda de dados para essas horas ou dias entre o último ponto de recuperação e a interrupção. Um RPO de 1 dia, teoricamente, resultaria na perda de todas as transações no dia, levando a uma falha.

Para sistemas de missão crítica, um RPO medido em minutos ou segundos pode ser mais apropriado para evitar uma perda de receita. Mas, um RPO mais curto geralmente resulta em um aumento nos custos gerais de gerenciamento.

Uma linha de base de gerenciamento deve se concentrar no RPO mais longo aceitável para minimizar os custos. A equipe de gerenciamento de nuvem pode aumentar o RPO de plataformas ou cargas de trabalho específicas, o que garantiria mais investimento.

## <a name="protect-and-recover-workloads"></a>Proteger e recuperar cargas de trabalho

A maioria das cargas de trabalho em um ambiente de ti dá suporte a um processo de negócios ou técnico muito pequeno. Os sistemas que não têm um impacto do sistema sobre as operações de negócios geralmente não garantem os maiores investimentos necessários para a recuperação rápida ou minimizar a perda de dados. Estabelecer uma linha de base permite que a empresa entenda claramente qual nível de suporte à recuperação pode ser oferecido em um ponto de preço consistente e gerenciável. Isso ajuda os participantes da empresa a avaliar o valor de um maior investimento em recuperação.

Para a maioria das equipes de gerenciamento de nuvem, uma linha de base aprimorada com compromissos de RPO/RTO específicos para vários ativos gera o caminho mais favorável para compromissos de negócios mútuos. As seções a seguir descrevem algumas linhas de base aprimoradas comuns que capacitam a empresa a adicionar facilmente a proteção e a funcionalidade de recuperação por meio de um processo repetível.

### <a name="protect-and-recover-data"></a>Proteger e recuperar dados

Os dados são, sem dúvida, o ativo mais valioso na economia digital. A capacidade de proteger e recuperar dados com mais eficiência é a linha de base aprimorada mais comum. Para os dados que alimentam uma carga de trabalho de produção, a perda de dados pode ser diretamente igual à perda de receita ou perda de lucratividade. Geralmente, incentivamos que as equipes de gerenciamento de nuvem ofereçam um nível de linha de base de gerenciamento aprimorado que dá suporte a plataformas de dados comuns.

Antes de implementar as operações de plataforma, é comum que as equipes de gerenciamento de nuvem ofereçam suporte a operações aprimoradas para plataformas como uma plataforma de dados de serviço. Por exemplo, é fácil para uma equipe de gerenciamento de nuvem impor uma frequência mais alta de backup ou replicação de várias regiões para soluções do Azure SQL ou Cosmo DB. Fazendo isso, permite que a equipe de desenvolvimento aprimore o RPO facilmente, simplesmente modernizando suas plataformas de dados.

Esse processo de pensamento será revisitado mais detalhadamente, na [disciplina de operações da plataforma](./platform.md).

### <a name="protect-and-recover-vms"></a>Proteger e recuperar VMs

A maioria das cargas de trabalho tem alguma dependência em máquinas virtuais. Essas máquinas virtuais hospedam vários aspectos da solução. Para que a carga de trabalho dê suporte a um processo de negócios após uma falha do sistema, algumas dessas máquinas virtuais devem ser recuperadas rapidamente.

Cada minuto de tempo de inatividade nessas máquinas virtuais poderia equiparar-se à perda de receita ou à lucratividade reduzida. Quando o tempo de inatividade nas VMs tem um impacto direto no desempenho fiscal dos negócios, o RTO é muito importante. As máquinas virtuais podem ser recuperadas mais rapidamente usando replicação em um site secundário e recuperação automatizada, esse modelo é conhecido como um modelo de recuperação quente. No mais alto estado de recuperação, as máquinas virtuais podem ser replicadas para um site secundário totalmente funcional. Essa abordagem mais cara é conhecida como um modelo de recuperação de alta disponibilidade ou Hot-Hot.

Cada um dos modelos acima reduz o objetivo do tempo de recuperação, resultando em uma restauração mais rápida dos recursos do processo de negócios. No entanto, cada modelo também resulta em um aumento significativo dos custos de gerenciamento de nuvem.

Esse processo de pensamento será revisitado mais detalhadamente, na [disciplina de operações de carga de trabalho](./workload.md).

## <a name="next-steps"></a>Próximos passos

Depois que esse componente de linha de base de gerenciamento é atendido, a equipe pode parecer mais adiante para evitar interrupções com operações de [plataforma](./platform.md) e operações de [carga de trabalho](./workload.md).

> [!div class="nextstepaction"]
> Operações de [plataforma](./platform.md) 
> [operações de carga de trabalho](./workload.md)
