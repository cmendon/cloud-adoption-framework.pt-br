---
title: Visão geral das plataformas de monitoramento de nuvem
description: Tenha uma visão geral de alto nível de duas plataformas de monitoramento para ajudá-lo a entender como cada uma fornece a funcionalidade de monitoramento de núcleo.
author: mgoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 5e4effaccc04ba3b534a75394f17d758141c387e
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140545"
---
<!-- cSpell:ignore opsman ITSM -->

# <a name="cloud-monitoring-guide-monitoring-platforms-overview"></a>Guia de monitoramento de nuvem: visão geral das plataformas de monitoramento

A Microsoft fornece uma variedade de recursos de monitoramento de dois produtos: System Center Operations Manager, que foi projetado para o local e, em seguida, estendido para a nuvem, e Azure Monitor, que foi projetado para a nuvem, mas também pode ser monitorado no local Systems. Essas duas ofertas fornecem serviços de monitoramento básicos, como alertas, rastreamento de tempo de atividade de serviço, monitoramento, diagnóstico e análise da integridade de aplicativos e infraestrutura.

Muitas organizações estão adotando as práticas mais recentes para agilidade DevOps e inovações em nuvem para gerenciar seus ambientes heterogêneos. Ainda assim, eles também estão preocupados com sua capacidade de tomar decisões apropriadas e responsáveis sobre como monitorar essas cargas de trabalho.

Este artigo fornece uma visão geral de alto nível de nossas plataformas de monitoramento para ajudá-lo a entender como cada uma fornece a funcionalidade de monitoramento de núcleo.

## <a name="the-story-of-system-center-operations-manager"></a>A história do System Center Operations Manager

Em 2000, inserimos o campo Operations Management com Microsoft Operations Manager (MOM) 2000. No 2007, apresentamos uma versão reprojetada do produto, chamada System Center Operations Manager. Ele passou além do monitoramento simples de um Windows Server e concentrou-se no monitoramento de aplicativos e serviços robustos e de ponta a ponta, incluindo plataformas heterogêneas, dispositivos de rede e outras dependências de aplicativo ou serviço. É uma plataforma de monitoramento de nível empresarial estabelecida para ambientes locais, na mesma classe que o IBM Tivoli ou HP Operations Manager no setor. Ele cresceu para dar suporte ao monitoramento de recursos de computação e plataforma em execução no Azure, Amazon Web Services (AWS) e em outros provedores de nuvem.

## <a name="the-story-of-azure-monitor"></a>A história do Azure Monitor

Quando o Azure foi lançado no 2010, o monitoramento dos serviços de nuvem foi fornecido com o agente de Diagnóstico do Azure, que forneceu uma maneira de coletar dados de diagnóstico dos recursos do Azure. Esse recurso foi considerado uma ferramenta de monitoramento geral em vez de uma plataforma de monitoramento de classe empresarial.  

O Application Insights foi introduzido para mudar com as alterações no setor em que a proliferação de dispositivos de nuvem, móveis e IoT estava crescendo e a introdução das práticas DevOpss. Ele cresceu do monitoramento do desempenho de aplicativos em Operations Manager para um serviço no Azure, em que ele fornece monitoramento avançado de aplicativos Web escritos em uma variedade de linguagens. Em 2015, a visualização do Application Insights para Visual Studio foi anunciada e posterior, ela se tornou conhecida como apenas Application Insights. Ele coleta detalhes sobre o desempenho, as solicitações e as exceções do aplicativo e os rastreamentos.

No 2015, o insights operacionais do Azure foi disponibilizado para o público geral. Ele forneceu o serviço de análise de Log Analytics que coletou e pesquisou dados de computadores no Azure, no local ou em outros ambientes de nuvem, e está conectado ao System Center Operations Manager. Foram oferecidas pacotes de inteligência que forneciam uma variedade de configurações de monitoramento e gerenciamento predefinidos que continham uma coleção de consulta e lógica analítica, visualizações e regras de coleta de dados para cenários como auditoria de segurança, integridade avaliações e gerenciamento de alertas. Posteriormente, as informações operacionais do Azure se tornaram conhecidas como Log Analytics.  

Em 2016, a visualização do Azure Monitor foi anunciada na conferência do Microsoft Ignite. Ele fornecia uma estrutura comum para coletar métricas de plataforma, logs de diagnóstico de recursos e eventos de log de atividades no nível de assinatura de qualquer serviço do Azure que começou a usar a estrutura. Anteriormente, cada serviço do Azure tinha seu próprio método de monitoramento.

Na conferência 2018 Ignite, anunciamos que a marca Azure Monitor expandida para incluir vários serviços diferentes originalmente desenvolvidos com funcionalidade independente:

- O **Azure monitor**original, para coletar métricas de plataforma, logs de diagnóstico de recurso e logs de atividade somente para recursos da plataforma Azure.
- **Application insights**, para o monitoramento de aplicativos.
- **Log Analytics**, o local principal para coletar e analisar dados de log.
- Um novo **serviço de alerta unificado**, que reuniu mecanismos de alerta de cada um dos outros serviços mencionados anteriormente.  
- **Observador de rede do Azure**, para monitorar, diagnosticar e exibir métricas para recursos em uma rede virtual do Azure.

## <a name="the-story-of-operations-management-suite-oms"></a>A história do OMS (Operations Management Suite)

De 2015 até abril de 2018, o OMS (Operations Management Suite) foi um agrupamento dos seguintes serviços de gerenciamento do Azure para fins de licenciamento:

- Application Insights
- Automação do Azure
- Serviço de Backup do Azure
- Insights operacionais (mais tarde, com a marca Log Analytics)
- Site Recovery

A funcionalidade dos serviços que faziam parte do OMS não foi alterada quando o OMS foi descontinuado. Elas foram realinhadas em Azure Monitor.

## <a name="infrastructure-requirements"></a>Requisitos de infraestrutura

### <a name="operations-manager"></a>Operations Manager

Operations Manager requer infraestrutura e manutenção significativas para dar suporte a um grupo de gerenciamento, que é uma unidade básica de funcionalidade. No mínimo, um grupo de gerenciamento consiste em um ou mais servidores de gerenciamento, uma instância SQL Server, hospedando o banco de dados operacional e data warehouse de relatórios e agentes. A complexidade de um design de grupo de gerenciamento depende de vários fatores, como o escopo das cargas de trabalho a serem monitoradas e o número de dispositivos ou computadores que dão suporte às cargas de trabalho. Se você precisar de alta disponibilidade e resiliência do site, como é normalmente o caso com plataformas de monitoramento corporativo, os requisitos de infraestrutura e a manutenção associada podem aumentar drasticamente.

![Diagrama de Operations Manager grupo de gerenciamento](./media/monitoring-management-guidance-cloud-and-on-premises/operations-manager-management-group-optimized.svg)

### <a name="azure-monitor"></a>Azure Monitor

O Azure Monitor é uma oferta de SaaS (software como serviço), portanto, sua infraestrutura de suporte é executada no Azure e é gerenciada pela Microsoft. Ele executa monitoramento, análise e diagnóstico em escala. Ele está disponível em todas as nuvens nacionais. As principais partes da infraestrutura (coletores, métricas e repositório de logs e análises) que oferecem suporte a Azure Monitor são mantidas pela Microsoft.  

![Diagrama de Azure Monitor](./media/monitoring-management-guidance-cloud-and-on-premises/azure-monitor-greyed-optimized.svg)

## <a name="data-collection"></a>Coleta de dados

<!-- markdownlint-disable MD024 -->

### <a name="operations-manager"></a>Operations Manager

#### <a name="agents"></a>Agentes

Operations Manager coleta dados diretamente somente de agentes que estão instalados em [computadores com Windows](https://docs.microsoft.com/system-center/scom/plan-planning-agent-deployment?view=sc-om-1807#windows-agent). Ele pode aceitar dados do SDK do Operations Manager, mas essa abordagem é normalmente usada para parceiros que estendem o produto com aplicativos personalizados, não para coletar dados de monitoramento. Ele pode coletar dados de outras fontes, como [computadores Linux](https://docs.microsoft.com/system-center/scom/plan-planning-agent-deployment?view=sc-om-1807#linuxunix-agent) e dispositivos de rede, usando módulos especiais executados no agente do Windows que acessam remotamente esses outros dispositivos.

![Diagrama do agente de Operations Manager](./media/monitoring-management-guidance-cloud-and-on-premises/data-collection-opsman-agents-optimized.svg)

O agente de Operations Manager pode coletar de várias fontes de dados no computador local, como o log de eventos, logs personalizados e contadores de desempenho. Ele também pode executar scripts, que podem coletar dados do computador local ou de fontes externas. Você pode escrever scripts personalizados para coletar dados que não podem ser coletados por outros meios ou para coletar dados de uma variedade de dispositivos remotos que não podem ser monitorados de outra forma.

#### <a name="management-packs"></a>Pacotes de gerenciamento

Operations Manager executa todo o monitoramento com fluxos de trabalho (regras, monitores e descobertas de objetos). Esses fluxos de trabalho são empacotados juntos em um [pacote de gerenciamento](https://docs.microsoft.com/system-center/scom/manage-overview-management-pack?view=sc-om-2019) e implantados em agentes. Os pacotes de gerenciamento estão disponíveis para uma variedade de produtos e serviços, que incluem regras e monitores predefinidos. Você também pode criar seu próprio pacote de gerenciamento para seus próprios aplicativos e cenários personalizados.

#### <a name="monitoring-configuration"></a>Configuração de monitoramento

Os pacotes de gerenciamento podem conter centenas de regras, monitores e regras de descoberta de objetos. Um agente executa todas essas configurações de monitoramento de todos os pacotes de gerenciamento que se aplicam, que são determinadas pelas regras de descoberta. Cada instância de cada configuração de monitoramento é executada de forma independente e age imediatamente nos dados coletados. É assim que Operations Manager pode obter alertas quase em tempo real e o estado de integridade atual dos recursos monitorados.

Por exemplo, um monitor pode amostragem de um contador de desempenho a cada poucos minutos. Se esse contador exceder um limite, ele definirá imediatamente o estado de integridade de seu objeto de destino, que dispara imediatamente um alerta no grupo de gerenciamento. Uma regra agendada pode procurar um evento específico a ser criado e acionar imediatamente um alerta quando esse evento é criado no log de eventos local.

Como essas configurações de monitoramento são isoladas umas das outras e funcionam a partir de fontes individuais de dados, Operations Manager tem desafios de correlacionar dados entre várias fontes. Também é difícil reagir aos dados depois que eles são coletados. Você pode executar fluxos de trabalho que acessam o banco de dados Operations Manager, mas esse cenário não é comum e normalmente é usado para um número limitado de fluxos de trabalho de finalidade especial.

![Diagrama de Operations Manager grupo de gerenciamento](./media/monitoring-management-guidance-cloud-and-on-premises/operations-manager-management-group-optimized.svg)

### <a name="azure-monitor"></a>Azure Monitor

#### <a name="data-sources"></a>Fontes de dados

O Azure Monitor coleta dados de uma variedade de fontes, incluindo recursos de infraestrutura e plataforma do Azure, agentes em computadores Windows e Linux e monitoramento de dados coletados no armazenamento do Azure. Qualquer cliente REST pode gravar dados de log para Azure Monitor usando uma API e você pode definir métricas personalizadas para seus aplicativos Web. Alguns dados de métrica podem ser roteados para locais diferentes, dependendo de seu uso. Por exemplo, você pode usar os dados para alertas "rápido como possível" ou para pesquisas de análise de tendência de longo prazo em conjunto com outros dados de log.

#### <a name="monitoring-solutions-and-insights"></a>Soluções e ideias de monitoramento

As soluções de monitoramento usam a plataforma de logs no Azure Monitor para fornecer monitoramento para um determinado aplicativo ou serviço. Normalmente, eles definem a coleta de dados de agentes ou de serviços do Azure e fornecem consultas de log e exibições para analisar esses dados. Normalmente, eles não fornecem regras de alerta, o que significa que você deve definir seus próprios critérios de alerta com base nos dados coletados.

As informações, como Azure Monitor para contêineres e Azure Monitor para VMs, usam a plataforma de logs e métricas do Azure Monitor para fornecer uma experiência de monitoramento Personalizada para um aplicativo ou serviço no portal do Azure. Eles podem fornecer condições de alerta e monitoramento de integridade, além da análise personalizada dos dados coletados.

#### <a name="monitoring-configuration"></a>Configuração de monitoramento

Azure Monitor separa a coleta de dados das ações executadas em relação a esses dados, o que oferece suporte a microserviços distribuídos em um ambiente de nuvem. Ele consolida dados de várias fontes em uma plataforma de dados comum e fornece recursos de análise, visualização e alertas com base nos dados coletados.

Os dados coletados pelo Azure Monitor são armazenados como logs ou métricas, e diferentes recursos do Azure Monitor contam com ambos. As métricas contêm valores numéricos na série temporal que são adequados para alertas quase em tempo real e detecção rápida de problemas. Os logs contêm texto ou dados numéricos e podem ser consultados usando uma linguagem poderosa especialmente útil para a execução de análises complexas.

Como Azure Monitor separa a coleta de dados de ações em relação a esses dados, pode não ser possível fornecer alertas quase em tempo real em muitos casos. Para alertar sobre dados de log, as consultas são executadas em um agendamento recorrente definido no alerta. Esse comportamento permite que Azure Monitor correlacione facilmente os dados de todas as fontes monitoradas, e você pode analisar de maneira interativa os dados de várias maneiras. Isso é especialmente útil para fazer a análise da causa raiz e identificar onde pode ocorrer um problema.

## <a name="health-monitoring"></a>Monitoramento de Integridade

### <a name="operations-manager"></a>Operations Manager

Os pacotes de gerenciamento no Operations Manager incluem um modelo de serviço que descreve os componentes do aplicativo que está sendo monitorado e sua relação. Os monitores identificam o estado de integridade atual de cada componente com base em dados e scripts no agente. Os Estados de integridade são acumulados para que você possa exibir rapidamente o estado de integridade resumido de computadores e aplicativos monitorados.

### <a name="azure-monitor"></a>Azure Monitor

Azure Monitor não fornece um método definido pelo usuário para implementar um modelo de serviço ou monitores que indiquem o estado de integridade atual de qualquer componente de serviço. Como as soluções de monitoramento são baseadas em recursos padrão do Azure Monitor, elas não fornecem monitoramento de nível de estado. Os seguintes recursos do Azure Monitor podem ser úteis:

- **Application insights:** Cria um mapa composto de seu aplicativo Web e fornece um estado de integridade para cada componente de aplicativo ou dependência. Isso inclui o status dos alertas e o detalhamento para um diagnóstico mais detalhado do seu aplicativo.

- **Azure monitor para VMs:** Fornece uma experiência de monitoramento de integridade para as VMs do Azure convidadas, semelhante à do Operations Manager, quando ele monitora as máquinas virtuais do Windows e do Linux. Ele avalia a integridade dos principais componentes do sistema operacional da perspectiva da disponibilidade e do desempenho para determinar o estado de integridade atual. Quando determina que a VM convidada está experimentando uma utilização de recursos sustentada, capacidade de espaço em disco ou um problema relacionado à funcionalidade principal do sistema operacional, ele gera um alerta para dar esse estado à sua atenção.

- **Azure monitor para contêineres:** Monitora o desempenho e a integridade do serviço kubernetes do Azure ou das instâncias de contêiner do Azure. Ele coleta métricas de processador e memória de controladores, nós e contêineres disponíveis no Kubernetes por meio da API Métricas. Ele também coleta logs de contêiner e dados de inventário sobre contêineres e suas imagens. Os critérios de integridade predefinidos baseados nos dados de desempenho coletados ajudam a identificar se existe um problema de capacidade ou afunilamento de recursos. Você também pode entender o desempenho geral ou o desempenho de um tipo de objeto kubernetes específico (Pod, nó, controlador ou contêiner).

## <a name="analyze-data"></a>{1&gt;{2&gt;Analisar dados&lt;2}&lt;1}{3&gt;&lt;3}

### <a name="operations-manager"></a>Operations Manager

O Operations Manager fornece quatro maneiras básicas de analisar dados depois que eles são coletados:

- **Gerenciador de integridade:** Ajuda a descobrir quais monitores estão identificando um problema de estado de integridade e revisar o conhecimento sobre o monitor e as possíveis causas de ações relacionadas a ele.

- **Modos de exibição:** O oferece visualizações predefinidas de dados coletados, como um grafo de dados de desempenho ou uma lista de componentes monitorados e seu estado de integridade atual. Exibições de diagrama visualmente apresentam o modelo de serviço de um aplicativo.

- **Relatórios:** Permite resumir os dados históricos armazenados no data warehouse de Operations Manager. Você pode personalizar os dados nos quais os modos de exibição e relatórios se baseiam. No entanto, não há nenhum recurso para permitir uma análise complexa ou interativa dos dados coletados.

- **Shell de comando Operations Manager:** Estende o Windows PowerShell com um conjunto adicional de cmdlets e pode consultar e visualizar os dados coletados. Isso inclui grafos e outras visualizações, nativamente com o PowerShell ou com o Operations Manager Console Web baseado em HTML.

### <a name="azure-monitor"></a>Azure Monitor

Com o poderoso mecanismo de análise de Azure Monitor, você pode trabalhar interativamente com dados de log e combiná-los com outros dados de monitoramento para análise de tendências e outros dados. Exibições e painéis permitem que você visualize dados de consulta de várias maneiras a partir da portal do Azure e importe-os para Power BI. As soluções de monitoramento incluem consultas e exibições para apresentar os dados coletados. Informações como Application Insights, Azure Monitor para VMs e Azure Monitor para contêineres incluem visualizações personalizadas para dar suporte a cenários de monitoramento interativos.

## <a name="alerting"></a>Alertas

### <a name="operations-manager"></a>Operations Manager

Operations Manager cria alertas em resposta a eventos predefinidos, quando um limite de desempenho é atingido e quando o estado de integridade de um componente monitorado é alterado. Ele inclui o gerenciamento completo de alertas, permitindo que você defina sua resolução e atribua-os a vários operadores ou engenheiros de sistema. Você pode definir regras de notificação que especificam quais alertas enviarão notificações proativas.

Os pacotes de gerenciamento incluem várias regras de alerta predefinidas para diferentes condições críticas no aplicativo que está sendo monitorado. Você pode ajustar essas regras ou criar regras personalizadas para os requisitos específicos do seu ambiente.

### <a name="azure-monitor"></a>Azure Monitor

Com Azure Monitor, você pode criar alertas com base em uma métrica que ultrapassa um limite ou com base em um resultado de consulta agendada. Embora alertas com base em métricas possam atingir resultados quase em tempo real, as consultas agendadas têm um tempo de resposta maior, dependendo da velocidade da ingestão e da indexação de dados. Em vez de serem limitados a um agente específico, alertas de consulta de log no Azure Monitor permitem que você analise dados em todos os dados armazenados em vários espaços de trabalho. Esses alertas também incluem dados de um aplicativo Application Insights específico usando uma consulta entre espaços de trabalho.

Embora as soluções de monitoramento possam incluir regras de alerta, você normalmente as cria com base em seus próprios requisitos.

## <a name="workflows"></a>Fluxos de trabalho

### <a name="operations-manager"></a>Operations Manager

Os pacotes de gerenciamento no Operations Manager contêm centenas de fluxos de trabalho individuais e determinam os dados a serem coletados e a ação a ser executada com esses dados. Por exemplo, uma regra pode criar amostras de um contador de desempenho a cada poucos minutos, armazenando seus resultados para análise. Um monitor pode obter um exemplo do mesmo contador de desempenho e comparar seu valor com um limite para determinar o estado de integridade de um objeto monitorado. Outra regra pode executar um script para coletar e analisar alguns dados em um computador agente e, em seguida, disparar um alerta se ele retornar um valor específico.

Os fluxos de trabalho no Operations Manager são independentes um do outro, o que torna a análise entre vários objetos monitorados difícil. Esses cenários de monitoramento devem ser baseados em dados depois de coletados, o que é possível, mas pode ser difícil, e não é comum.

### <a name="azure-monitor"></a>Azure Monitor

Azure Monitor separa a coleta de dados das ações e da análise obtida por meio desses dados. Os agentes e outras fontes de dados gravam dados de log em um espaço de trabalho Log Analytics e gravam dados de métrica no banco de dado de métrica, sem qualquer análise desses dados ou conhecimento de como ele pode ser usado. O monitor executa alertas e outras ações dos dados armazenados, o que permite que você execute a análise entre os dados de todas as fontes.

## <a name="extend-the-base-platform"></a>Estenda a plataforma base

### <a name="operations-manager"></a>Operations Manager

Operations Manager implementa toda a lógica de monitoramento em um pacote de gerenciamento, que você mesmo cria ou obtém de nós ou de um parceiro. Quando você instala um pacote de gerenciamento, ele descobre automaticamente os componentes do aplicativo ou serviço em agentes diferentes e implanta regras e monitores apropriados. O pacote de gerenciamento contém definições de integridade, regras de alerta, desempenho e regras de coleta de eventos, e exibições, para fornecer monitoramento completo que dá suporte ao aplicativo ou serviço de infraestrutura.

O SDK Operations Manager permite que Operations Manager se integre a plataformas de monitoramento de terceiros ou software gerenciamento de serviços de TI (ITSM). O SDK também é usado por alguns pacotes de gerenciamento de parceiros para dar suporte ao monitoramento de dispositivos de rede e fornecer experiências de apresentação personalizadas, como o painel do HTML5 em quadrado ou a integração com o Microsoft Office Visio.

### <a name="azure-monitor"></a>Azure Monitor

Azure Monitor coleta métricas e logs de recursos do Azure, com pouca ou nenhuma configuração. Soluções de monitoramento adicionam lógica para monitorar um aplicativo ou serviço, mas ainda funcionam nas consultas de log padrão e exibições no monitor. As informações, como Application Insights e Azure Monitor para VMs, usam a plataforma de monitor para coleta e processamento de dados. Eles também fornecem ferramentas adicionais para visualizar e analisar os dados. Você pode combinar os dados coletados por informações com outros dados, usando recursos do monitor de núcleo, como consultas de log e alertas.

O monitor oferece suporte a vários métodos para coletar dados de monitoramento ou de gerenciamento do Azure ou de recursos externos. Em seguida, você pode extrair e encaminhar dados da métrica ou dos repositórios de log para suas ferramentas de ITSM ou de monitoramento. Ou você pode executar tarefas administrativas usando a API REST do Azure Monitor.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Monitorando os modelos de implantação de nuvem](./cloud-models-monitor-overview.md)
