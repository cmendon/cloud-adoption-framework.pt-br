---
title: Proteger e recuperar no gerenciamento de nuvem
description: Aprenda a importância de se preparar para uma interrupção potencial da carga de trabalho. Essa preparação permite que sua equipe detecte falhas antes e se recupere mais rapidamente.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: f46fb65572d319e2dc9a4a779cd205bbe476908b
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78340988"
---
# <a name="protect-and-recover-in-cloud-management"></a>Proteger e recuperar no gerenciamento de nuvem

Depois de atenderem aos requisitos de [inventário e visibilidade](./inventory.md) e à [conformidade operacional](./operational-compliance.md), as equipes de gerenciamento de nuvem podem prever e se preparar para uma interrupção potencial da carga de trabalho. Conforme eles estão planejando o gerenciamento de nuvem, as equipes devem começar com uma suposição de que algo falhará.

Nenhuma solução técnica pode oferecer consistentemente um SLA de tempo de atividade de 100%. Soluções com a declaração de arquiteturas mais redundantes a serem entregues em tempo de atividade de "seis noves" ou 99,9999%. Mas mesmo uma solução de "seis noves" fica inativa por 31,6 segundos em um determinado ano. Infelizmente, é raro que uma solução garanta um investimento operacional grande e contínuo que seja necessário para atingir "seis noves" de tempo de atividade.

A preparação para uma interrupção permite que a equipe detecte falhas mais cedo e se recupere mais rapidamente. O foco dessa disciplina é nas etapas que surgem imediatamente após a falha de um sistema. Como proteger cargas de trabalho para que elas possam ser recuperadas rapidamente quando ocorre uma interrupção?

## <a name="translate-protection-and-recovery-conversations"></a>Converter conversas de proteção e recuperação

As cargas de trabalho que capacitam as operações de negócios consistem em aplicativos, dados, máquinas virtuais (VMs) e outros ativos. Cada um desses ativos pode exigir uma abordagem diferente para proteção e recuperação. O aspecto importante dessa disciplina é estabelecer um compromisso consistente dentro da linha de base de gerenciamento, que pode fornecer um ponto de partida durante as discussões de negócios.

No mínimo, cada ativo que dá suporte a uma determinada carga de trabalho deve ter uma abordagem de linha de base com um compromisso claro com a velocidade de recuperação (objetivos de tempo de recuperação ou RTO) e o risco de perda de dados (objetivos de ponto de recuperação ou RPO).

### <a name="recovery-time-objectives-rto"></a>RTO (objetivos de tempo de recuperação)

Quando ocorre um desastre, um objetivo de tempo de recuperação é a quantidade de tempo que deve levar para recuperar qualquer sistema para seu estado antes do desastre. Para cada carga de trabalho, isso inclui o tempo necessário para restaurar a funcionalidade mínima necessária para as VMs e os aplicativos. Ele também inclui a quantidade de tempo necessária para restaurar os dados exigidos pelos aplicativos.

Em termos comerciais, o RTO representa a quantidade de tempo que o processo de negócios estará fora de serviço. Para cargas de trabalho de missão crítica, essa variável deve ser relativamente baixa, permitindo que os processos de negócios retomem rapidamente. Para cargas de trabalho de baixa prioridade, um nível padrão de RTO pode não ter um impacto perceptível no desempenho da empresa.

A linha de base de gerenciamento deve estabelecer um RTO padrão para cargas de trabalho não críticas. A empresa pode usar essa linha de base como uma maneira de justificar investimentos adicionais em tempos de recuperação.

### <a name="recovery-point-objectives-rpo"></a>Objetivos do ponto de recuperação (RPO)

Na maioria dos sistemas de gerenciamento de nuvem, os dados são capturados periodicamente e armazenados por meio de alguma forma de proteção de dados. A última vez que os dados foram capturados são chamados de ponto de recuperação. Quando um sistema falha, ele pode ser restaurado somente para o ponto de recuperação mais recente.

Se um sistema tiver um objetivo de ponto de recuperação medido em horas ou dias, uma falha do sistema resultaria na perda de dados para essas horas ou dias entre o último ponto de recuperação e a interrupção. Um RPO de um dia teoricamente resultaria na perda de todas as transações no dia, levando a uma falha.

Para sistemas de missão crítica, um RPO medido em minutos ou segundos pode ser mais apropriado para evitar uma perda de receita. Mas um RPO mais curto geralmente resulta em um aumento nos custos gerais de gerenciamento.

Para ajudar a minimizar os custos, uma linha de base de gerenciamento deve se concentrar no RPO mais longo aceitável. A equipe de gerenciamento de nuvem pode aumentar o RPO de plataformas ou cargas de trabalho específicas, o que garantiria mais investimento.

## <a name="protect-and-recover-workloads"></a>Proteger e recuperar cargas de trabalho

A maioria das cargas de trabalho em um ambiente de ti dá suporte a um processo comercial ou técnico específico. Os sistemas que não têm um impacto do sistema sobre as operações de negócios geralmente não garantem os crescentes investimentos necessários para recuperar rapidamente ou minimizar a perda de dados. Ao estabelecer uma linha de base, a empresa pode entender claramente o nível de suporte à recuperação que pode ser oferecido em um ponto de preço consistente e gerenciável. Essa compreensão ajuda os participantes da empresa a avaliar o valor de um maior investimento em recuperação.

Para a maioria das equipes de gerenciamento de nuvem, uma linha de base aprimorada com compromissos de RPO/RTO específicos para vários ativos gera o caminho mais favorável para compromissos de negócios mútuos. As seções a seguir descrevem algumas linhas de base aprimoradas comuns que capacitam a empresa a adicionar facilmente a proteção e a funcionalidade de recuperação por meio de um processo repetível.

### <a name="protect-and-recover-data"></a>Proteger e recuperar dados

Os dados são, sem dúvida, o ativo mais valioso na economia digital. A capacidade de proteger e recuperar dados com mais eficiência é a linha de base aprimorada mais comum. Para os dados que alimentam uma carga de trabalho de produção, a perda de dados pode ser diretamente igual à perda de receita ou perda de lucratividade. Geralmente incentivamos as equipes de gerenciamento de nuvem a oferecer um nível de linha de base de gerenciamento aprimorado que dá suporte a plataformas de dados comuns.

Antes que as equipes de gerenciamento de nuvem implementem as operações de plataforma, é comum que elas ofereçam suporte a operações aprimoradas para uma plataforma de dados de PaaS (plataforma como serviço). Por exemplo, é fácil para uma equipe de gerenciamento de nuvem impor uma frequência mais alta de backup ou replicação de multiregião para soluções de banco de dados SQL do Azure ou Azure Cosmos DB. Isso permite que a equipe de desenvolvimento aprimore o RPO facilmente, modernizando suas plataformas de dados.

Para saber mais sobre esse processo de pensamento, consulte [disciplina de operações de plataforma](./platform.md).

### <a name="protect-and-recover-vms"></a>Proteger e recuperar VMs

A maioria das cargas de trabalho tem alguma dependência em máquinas virtuais, que hospedam vários aspectos da solução. Para que a carga de trabalho dê suporte a um processo de negócios após uma falha do sistema, várias máquinas virtuais devem ser recuperadas rapidamente.

Cada minuto de tempo de inatividade nessas máquinas virtuais pode causar perda de receita ou lucratividade reduzida. Quando o tempo de inatividade da VM tem um impacto direto no desempenho fiscal dos negócios, o RTO é muito importante. As máquinas virtuais podem ser recuperadas mais rapidamente usando a replicação para um site secundário e a recuperação automatizada, um modelo que é conhecido como um modelo de recuperação quente. No mais alto estado de recuperação, as máquinas virtuais podem ser replicadas para um site secundário totalmente funcional. Essa abordagem mais cara é conhecida como um modelo de recuperação de alta disponibilidade ou quente.

Cada um dos modelos anteriores reduz o RTO, resultando em uma restauração mais rápida dos recursos do processo de negócios. No entanto, cada modelo também resulta em um aumento significativo dos custos de gerenciamento de nuvem.

Para saber mais sobre esse processo de pensamento, consulte [disciplina de operações de carga de trabalho](./workload.md).

## <a name="next-steps"></a>Próximas etapas

Depois que esse componente de linha de base de gerenciamento for atendido, a equipe poderá ficar à frente para evitar interrupções nas operações de [plataforma](./platform.md) e operações de [carga de trabalho](./workload.md).

> [!div class="nextstepaction"]
> Operações de [plataforma](./platform.md)
> [operações de carga de trabalho](./workload.md)
