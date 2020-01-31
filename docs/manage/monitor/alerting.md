---
title: 'Guia de monitoramento de nuvem: alertas'
description: Escolha quando usar Azure Monitor ou System Center Operations Manager no Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 9c13333e6d0e834a4c66d4a1bd6a72ccc9a1bdbb
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807641"
---
# <a name="cloud-monitoring-guide-alerting"></a>Guia de monitoramento de nuvem: alertas

Há anos, as organizações de ti lutaram em combater o alerta fadiga criado pelas ferramentas de monitoramento implantadas na empresa. Muitos sistemas geram um alto volume de alertas frequentemente considerados sem sentido, enquanto outros alertas são relevantes, mas são ignorados ou ignorados. Como resultado, as operações de ti e de desenvolvedores lutaram para atender à qualidade de nível de serviço prometida para clientes internos ou externos. Para garantir a confiabilidade, é essencial entender o estado da infraestrutura e dos aplicativos. Para minimizar a degradação e a interrupção do serviço, ou para diminuir o efeito ou reduzir o número de incidentes, você precisa identificar as causas rapidamente.

## <a name="successful-alerting-strategy"></a>Estratégia de alerta bem-sucedida

*Não é possível corrigir o que você não sabe que está desfeito.*

Alertas sobre o que importa é essencial. Ele é subfixado coletando e medindo as métricas e os logs certos. Você também precisa de uma ferramenta de monitoramento capaz de armazenar, agregar, Visualizar, analisar e iniciar uma resposta automatizada quando as condições forem atendidas. Você pode melhorar a observação de seus serviços e aplicativos somente se compreender totalmente sua composição. Você mapeia essa composição em uma configuração de monitoramento detalhada para ser aplicada pela plataforma de monitoramento. Essa configuração inclui os Estados de falha previsíveis (os sintomas, não a causa da falha) que fazem sentido para o alerta.

Considere os seguintes princípios para determinar se um sintoma é um candidato apropriado para alertas:

- **Isso é importante?** É o problema sintoma de um problema real ou problema que influencia a integridade geral do aplicativo? Por exemplo, você se importa se a utilização da CPU está alta no recurso? Ou que uma consulta SQL específica em execução em uma instância do banco de dados SQL nesse recurso está consumindo alta utilização da CPU em um período sustentado? Como a condição de utilização da CPU é um problema real, você deve alertá-la. Mas você não precisa notificar a equipe, pois ela não ajuda a indicar o que está causando a condição em primeiro lugar. O alerta e a notificação sobre o problema de utilização do processo de consulta do SQL são relevantes e acionáveis.
- **É urgente?** O problema é real e precisa de atenção urgente? Nesse caso, a equipe responsável deve ser notificada imediatamente.
- **Seus clientes são afetados?** Os usuários do serviço ou aplicativo foram afetados como resultado do problema?
- **Outros sistemas dependentes são afetados?** Há alertas de dependências que estão inter-relacionados e que podem ser correlacionados para evitar a notificação de diferentes equipes que estão trabalhando no mesmo problema?

Faça essas perguntas quando estiver desenvolvendo inicialmente uma configuração de monitoramento. Teste e valide as suposições em um ambiente de não produção e, em seguida, implante na produção. As configurações de monitoramento são derivadas de modos de falha conhecidos, resultados de teste de falhas simuladas e experiência de diferentes membros da equipe.

Após o lançamento da sua configuração de monitoramento, você pode aprender muito sobre o que está funcionando e o que não é. Considere o alto volume de alertas, problemas despercebidos pelo monitoramento, mas observados pelos usuários finais, e quais foram as melhores ações a serem tomadas como parte dessa avaliação. Identifique as alterações a serem implementadas para melhorar a entrega de serviços, como parte de um processo contínuo de aperfeiçoamento de monitoramento contínuo. Não se trata apenas de avaliar o ruído do alerta ou os alertas perdidos, mas também a eficácia de como você está monitorando a carga de trabalho. É a eficácia de suas políticas de alerta, processo e cultura geral para determinar se você está melhorando.

System Center Operations Manager e Azure Monitor dão suporte a alertas com base em limites estáticos ou até mesmo dinâmicos e ações configuradas em cima deles. Os exemplos incluem alertas para chamadas de email, SMS e voz para notificações simples. Ambos os serviços também dão suporte à integração de gerenciamento de serviços de TI (ITSM) para automatizar a criação de registros de incidentes e escalonar para a equipe de suporte correta ou qualquer outro sistema de gerenciamento de alertas que use um webhook.

Quando possível, você pode usar qualquer um dos vários serviços para automatizar as ações de recuperação. Isso inclui o System Center Orchestrator, a automação do Azure, os aplicativos lógicos do Azure ou o dimensionamento automático no caso de cargas de trabalho elásticas. Embora a notificação das equipes responsáveis seja a ação mais comum para o alerta, a automatização das ações corretivas também pode ser apropriada. Essa automação pode ajudar a simplificar todo o processo de gerenciamento de incidentes. Automatizar essas tarefas de recuperação também pode reduzir o risco de erro humano.

## <a name="azure-monitor-alerting"></a>Alertas de Azure Monitor

Se você estiver usando Azure Monitor exclusivamente, siga estas diretrizes ao considerar a velocidade, o custo e o volume de armazenamento.

Dependendo do recurso e da configuração que você está usando, você pode armazenar dados de monitoramento em qualquer um dos seis repositórios:

- **Banco de dados de métricas Azure monitor:** Um banco de dados de série temporal usado principalmente para métricas de plataforma Azure Monitor, mas também tem Application Insights dados de métricas espelhados nele. As informações que entram nesse banco de dados têm os tempos de alerta mais rápidos.

- **Armazenamento de logs de Application insights:** Um banco de dados que armazena a maior parte Application Insights telemetria no formulário de log.

- **Armazenamento de logs de Azure monitor:** O repositório primário para dados de log do Azure. Outras ferramentas podem rotear dados para ela e podem ser analisadas em logs de Azure Monitor. Devido à ingestão e indexação, as consultas de alerta de log têm maior latência. Essa latência geralmente é de 5-10 minutos, mas pode ser maior em determinadas circunstâncias.

- **Repositório de logs de atividades:** Usado para todos os eventos do log de atividades e de integridade do serviço. O alerta dedicado é possível. Contém eventos de nível de assinatura que ocorrem em objetos em sua assinatura, como visto do fora desses objetos. Um exemplo pode ser quando uma política é definida ou um recurso é acessado ou excluído.

- **Armazenamento do Azure:** Armazenamento de uso geral com suporte pelo Diagnóstico do Azure e outras ferramentas de monitoramento. É uma opção de baixo custo para retenção de longo prazo de telemetria de monitoramento. O alerta não tem suporte dos dados armazenados nesse serviço.

- **Hubs de eventos:** Geralmente usado para transmitir dados para o monitoramento do local ou de outros parceiros ou para as ferramentas de ITSM.

Azure Monitor tem quatro tipos de alertas, cada um de certa forma vinculado ao repositório no qual os dados são armazenados:

- [Alerta de métrica](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric): alertas em dados no banco de dado de métricas de Azure monitor. Os alertas ocorrem quando um valor monitorado cruza um limite definido pelo usuário e, em seguida, novamente quando ele retorna ao estado "normal".

- [Alerta de consulta de log](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-log-query): disponível para alertas de conteúdo nos repositórios Application insights ou logs do Azure. Ele também pode alertar com base em consultas entre espaços de trabalho.

- [Alerta do log de atividades](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log): alertas em itens no repositório de logs de atividades, com exceção dos dados de integridade do serviço.

- [Alerta de integridade do serviço](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-activity-log-service-notifications): um tipo especial de alerta que é usado somente para problemas de integridade do serviço provenientes do repositório de logs de atividades, como interrupções e manutenção planejada futura. Observe que esse tipo de alerta é configurado por meio da [integridade do serviço do Azure](https://docs.microsoft.com/azure/service-health/service-health-overview), um serviço complementar para Azure monitor.

### <a name="enable-alerting-through-partner-tools"></a>Habilitar alertas por meio de ferramentas de parceiro

Se você estiver usando uma solução de alertas externos, encaminhe o máximo possível por meio dos hubs de eventos do Azure, que é o caminho mais rápido do Azure Monitor. Você precisará pagar pela ingestão no Hub de eventos. Se o custo for um problema e uma velocidade não for, você poderá usar o armazenamento do Azure como uma alternativa menos dispendiosa. Apenas certifique-se de que suas ferramentas de monitoramento ou ITSM possam ler o armazenamento do Azure para extrair os dados.

O Azure Monitor inclui suporte para integração com outras plataformas de monitoramento e software de ITSM, como o ServiceNow. Você pode usar os alertas do Azure e ainda disparar ações fora do Azure, conforme exigido pelo processo de gerenciamento de incidentes ou DevOps. Se você quiser alertar em Azure Monitor e automatizar a resposta, poderá iniciar ações automatizadas usando Azure Functions, aplicativos lógicos do Azure ou a automação do Azure, com base em seu cenário e requisitos.

### <a name="specialized-azure-monitoring-offerings"></a>Ofertas de monitoramento do Azure especializadas

As [soluções de gerenciamento](https://docs.microsoft.com/azure/azure-monitor/insights/solutions-inventory) geralmente armazenam seus dados no repositório de logs do Azure. As duas exceções são Azure Monitor para VMs e Azure Monitor para contêineres. A tabela a seguir descreve a experiência de alerta com base no tipo de dados específico e onde ele é armazenado.

Solução| Tipo de dados | Comportamento do alerta
:---|:---|:---
Azure Monitor para contêineres | Os dados de desempenho médio calculados de nós e pods são gravados no repositório de métricas. | Crie alertas de métrica se você quiser ser alertado com base na variação do desempenho de utilização medido, agregado ao longo do tempo.
|| Dados de desempenho calculados que usam percentils de nós, controladores, contêineres e pods são gravados no repositório de logs. Os logs de contêiner e as informações de inventário também são gravados no repositório de logs. | Crie alertas de consulta de log se desejar ser alertado com base na variação da utilização medida de clusters e contêineres. Os alertas de consulta de log também podem ser configurados com base em contagens de fase de Pod e contagens de nós de status.
Azure Monitor para VMs | Os critérios de integridade são métricas gravadas no repositório de métricas. | Os alertas são gerados quando o estado de integridade muda de íntegro para não íntegro. Esse alerta dá suporte apenas a grupos de ação que são configurados para enviar notificações por email ou SMS.
|| Os dados do log de desempenho do sistema operacional convidado e do mapa são gravados no repositório de logs. | Criar alertas de consulta de log.

### <a name="fastest-speed-driven-by-cost"></a>Velocidade mais rápida orientada por custo

A latência é uma das decisões mais críticas que impulsionam alertas e uma rápida resolução de problemas que afetam seu serviço. Se você precisar de alertas quase em tempo real menos de cinco minutos, avalie primeiro se você tiver ou puder obter alertas em sua telemetria onde eles são armazenados por padrão. Em geral, essa estratégia também é a opção mais barata, porque a ferramenta que você está usando já está enviando seus dados para esse local.

Dito isso, há algumas notas de rodapé importantes para essa regra.

A **telemetria do sistema operacional convidado** tem um número de caminhos para entrar no sistema.

- A maneira mais rápida de alertar sobre esses dados é importá-lo como métricas personalizadas. Faça isso usando a extensão Diagnóstico do Azure e, em seguida, usando um alerta de métrica. No entanto, as métricas personalizadas estão atualmente em visualização e são [mais caras do que outras opções](https://azure.microsoft.com/pricing/details/monitor).

- O método menos caro, mas mais lento, é enviá-lo para o repositório Kusto do Azure logs. A execução do agente de Log Analytics na VM é a melhor maneira de obter todos os dados de log e de métrica do sistema operacional convidado nesse armazenamento.

- Você pode enviá-lo para ambos os repositórios executando a extensão e o agente na mesma VM. Em seguida, você pode alertar rapidamente, mas também usar os dados do sistema operacional convidado como parte de pesquisas mais complexas ao combiná-lo com outra telemetria.

**Importando dados do local:** Se você estiver tentando consultar e monitorar entre computadores em execução no Azure e no local, poderá usar o agente de Log Analytics para coletar dados do sistema operacional convidado. Você pode usar um recurso chamado [logs para métricas](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric-logs) para simplificar as métricas no repositório de métricas. Esse método ignora parte do processo de ingestão no repositório de logs do Azure e os dados estão, portanto, disponíveis mais cedo no banco de dados de métricas.

### <a name="minimize-alerts"></a>Minimizar alertas

Se você usar uma solução como Azure Monitor para VMs e encontrar os critérios de integridade padrão que monitoram a utilização de desempenho aceitável, não crie alertas de consulta de log ou métricas de sobreposição com base nos mesmos contadores de desempenho.

Se você não estiver usando Azure Monitor para VMs, torne o trabalho de criação de alertas e gerenciamento de notificações mais fácil explorando os seguintes recursos:

> [!NOTE]
> Esses recursos se aplicam somente a alertas de métricas, alertas com base nos dados que estão sendo enviados para o banco de dado de métricas Azure Monitor. Os recursos não se aplicam aos outros tipos de alertas. Conforme mencionado anteriormente, o objetivo principal dos alertas de métrica é a velocidade. Se receber um alerta em menos de cinco minutos não for uma preocupação principal, você poderá usar um alerta de consulta de log.

- [Limites dinâmicos](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-dynamic-thresholds): os limites dinâmicos examinam a atividade do recurso durante um período de tempo e criam limites de "comportamento normal" superior e inferior. Quando a métrica que está sendo monitorada cair fora desses limites, você receberá um alerta.

- [Alertas multiassinados](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts): você pode criar um alerta de métrica que usa a combinação de duas entradas diferentes de dois tipos de recursos diferentes. Por exemplo, se você quiser acionar um alerta quando a utilização da CPU de uma VM estiver acima de 90% e o número de mensagens em uma determinada fila do barramento de serviço do Azure alimentando essa VM exceder uma determinada quantidade, você poderá fazer isso sem criar uma consulta de log. Esse recurso funciona somente para dois sinais. Se você tiver uma consulta mais complexa, alimentar os dados de métrica no repositório de log de Azure Monitor e usar uma consulta de log.

- [Alertas de multirecursos](https://azure.microsoft.com/blog/monitor-at-scale-in-azure-monitor-with-multi-resource-metric-alerts): Azure monitor permite uma única regra de alerta de métrica que se aplica a todos os recursos da VM. Esse recurso pode poupar tempo porque você não precisa criar alertas individuais para cada VM. Os preços para esse tipo de alerta são os mesmos. Se você criar alertas de 50 para monitorar a utilização de CPU para 50 VMs ou um alerta que monitora a utilização da CPU para todas as 50 VMs, ele custa a mesma quantia. Você também pode usar esses tipos de alertas em combinação com limites dinâmicos.

Usados juntos, esses recursos podem poupar tempo, minimizando as notificações de alerta e o gerenciamento dos alertas subjacentes.

### <a name="alerts-limitations"></a>Limitações de alertas

Lembre-se de anotar as [limitações](https://docs.microsoft.com/azure/azure-subscription-service-limits#azure-monitor-limits) no número de alertas que você pode criar. Alguns limites (mas não todos eles) podem ser aumentados chamando o suporte.

### <a name="best-query-experience"></a>Melhor experiência de consulta

Se você estiver procurando tendências em todos os seus dados, faz sentido importar todos os seus dados para os logs do Azure, a menos que já esteja em Application Insights. Você pode criar consultas em ambos os espaços de trabalho, portanto, não há necessidade de mover dados entre eles. Você também pode importar o log de atividades e os dados de integridade do serviço para seu espaço de trabalho do Log Analytics. Você paga por essa ingestão e armazenamento, mas obtém todos os dados em um único lugar para análise e consulta. Essa abordagem também oferece a capacidade de criar condições complexas de consulta e alertar sobre elas.
