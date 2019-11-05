---
title: Guia de monitoramento de nuvem – estratégia de monitoramento para modelos de implantação em nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Escolha quando usar Azure Monitor ou System Center Operations Manager no Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 10/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 849c6eace1704cababd4fc40f7976f5e1915345e
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564966"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guia de monitoramento de nuvem: estratégia de monitoramento para modelos de implantação de nuvem

Este artigo inclui nossa estratégia de monitoramento recomendada para cada um dos modelos de implantação de nuvem, com base nos seguintes critérios:

- Você precisa manter seu compromisso com o Operations Manager ou outra plataforma de monitoramento corporativo, pois ele está integrado com seus processos de operações de ti, conhecimento e experiência ou alguma funcionalidade ainda não está disponível no Azure Monitor.
- Você precisa monitorar cargas de trabalho locais e na nuvem pública ou apenas na nuvem.
- Sua estratégia de migração de nuvem inclui modernizar operações de ti e migrar para nossos serviços de monitoramento de nuvem e soluções.
- Você pode ter sistemas críticos que são gapped ou isolados fisicamente, hospedados em uma nuvem privada ou em hardware físico. E os sistemas precisam ser monitorados.

Nossa estratégia inclui suporte para monitoramento de infraestrutura (cargas de trabalho de computação, armazenamento e servidor), aplicativo (usuário final, exceções e cliente) e recursos de rede. Ele fornece uma perspectiva de monitoramento orientada a serviços completa.

## <a name="azure-cloud-monitoring"></a>Monitoramento de nuvem do Azure

Azure Monitor é o serviço da plataforma nativa do Azure que fornece uma única fonte para monitorar os recursos do Azure. Ele foi projetado para soluções de nuvem que:
* São criados no Azure.
* Dê suporte a um recurso de negócios baseado em cargas de trabalho de VM (máquina virtual) ou arquiteturas complexas que usam microserviços e outros recursos de plataforma.

Ele monitora todas as camadas da pilha, começando com os serviços de locatário, como Azure Active Directory Domain Services e eventos de nível de assinatura e integridade do serviço do Azure. 

Ele também monitora os recursos de infraestrutura, como VMs, armazenamento e recursos de rede. Na camada superior, ele monitora seu aplicativo. 

Ao monitorar cada uma dessas dependências e coletar os sinais certos que cada um pode emitir, você obtém a observação de aplicativos e a principal infraestrutura de que precisa.

Nossa abordagem recomendada para monitorar cada camada da pilha é resumida na tabela a seguir:

<!-- markdownlint-disable MD033 -->

Camada | Recurso | Escopo | Método
---|---|---|----
Aplicativo | Um aplicativo baseado na Web executado em .NET, .NET Core, Java, JavaScript e plataforma node. js em uma VM do Azure, serviços de Azure App, Service Fabric do Azure, Azure Functions e serviços de nuvem do Azure. | Monitore um aplicativo Web ao vivo para detectar automaticamente anomalias de desempenho, identificar exceções de código e problemas e coletar análises de comportamento do usuário. |  Azure Monitor (Application Insights).
Recursos do Azure – PaaS (plataforma como serviço) | Serviços de banco de dados do Azure (por exemplo, SQL ou MySQL). | Banco de dados do Azure para métricas de desempenho do SQL. | Habilite o log de diagnóstico para transmitir dados SQL para logs de Azure Monitor.
Recursos do Azure – IaaS (infraestrutura como serviço) | 1. armazenamento do Azure<br/> 2. Aplicativo Azure gateway<br/> 3. grupos de segurança de rede<br/> 4. Gerenciador de tráfego do Azure<br/> 5. máquinas virtuais do Azure<br/> 6. instâncias de contêiner do Azure/serviço kubernetes do Azure | 1. capacidade, disponibilidade e desempenho.<br/> 2. logs de desempenho e diagnóstico (atividade, acesso, desempenho e firewall).<br/> 3. monitore eventos quando as regras são aplicadas e o contador de regras para quantas vezes uma regra é aplicada para negar ou permitir.<br/> 4. monitorar a disponibilidade do status do ponto de extremidade.<br/> 5. Monitore a capacidade, a disponibilidade e o desempenho em um sistema operacional de VM convidada (SO). Mapeie dependências de aplicativo hospedadas em cada VM, incluindo a visibilidade de conexões de rede ativas entre servidores, latência de conexão de entrada e saída e portas em qualquer arquitetura conectada a TCP.<br/> 6. Monitore a capacidade, a disponibilidade e o desempenho das cargas de trabalho em execução em contêineres e instâncias de contêiner. | 1. métricas de armazenamento para armazenamento de BLOBs.<br/> 2. Habilite o log de diagnóstico e configure o streaming para Azure Monitor logs.<br/> 3. Habilite o log de diagnóstico de grupos de segurança de rede e configure o streaming para Azure Monitor logs.<br/> 4. Habilite o log de diagnóstico dos pontos de extremidade do Gerenciador de tráfego e configure o streaming para Azure Monitor logs.<br/> 5. habilitar Azure Monitor para VMs.<br/> 6. habilitar Azure Monitor para contêineres.
Rede | Comunicação entre sua máquina virtual e um ou mais pontos de extremidade (outra VM, um nome de domínio totalmente qualificado, um identificador de recurso uniforme ou um endereço IPv4). | Monitore a acessibilidade, a latência e as alterações de topologia de rede que ocorrem entre a VM e o ponto de extremidade. | Observador de rede do Azure.
Assinatura do Azure | Integridade do serviço do Azure e integridade básica do recurso. | <li> Ações administrativas executadas em um serviço ou recurso.<br/><li> A integridade do serviço com um serviço do Azure está em um estado degradado ou indisponível.<br/><li> Problemas de integridade detectados com um recurso do Azure da perspectiva do serviço do Azure.<br/><li> Operações executadas com o dimensionamento automático do Azure indicando uma falha ou exceção. <br/><li> Operações executadas com Azure Policy indicando que ocorreu uma ação permitida ou negada.<br/><li> Registro de alertas gerados pela central de segurança do Azure. | Entregue no log de atividades para monitoramento e alertas usando Azure Resource Manager.
Locatário do Azure | Azure Active Directory || Habilite o log de diagnóstico e configure o streaming para Azure Monitor logs.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Monitoramento de nuvem híbrida

Para muitas organizações, a transição para a nuvem deve ser abordada gradualmente, em que o modelo de nuvem híbrida é a primeira etapa mais comum da jornada. Você seleciona cuidadosamente o subconjunto apropriado de aplicativos e a infraestrutura para iniciar a migração, ao mesmo tempo que evita a interrupção para seus negócios. No entanto, como oferecemos duas plataformas de monitoramento que dão suporte a esse modelo de nuvem, os tomadores de decisão de ti podem ser incertezas sobre qual é a melhor opção para dar suporte às suas metas operacionais comerciais e de ti. 

Nesta seção, abordaremos as incertezas examinando vários fatores e oferecendo uma compreensão de qual plataforma deve ser considerada.

Tenha em mente os seguintes aspectos técnicos principais:

- Você precisa coletar dados de recursos do Azure que dão suporte à carga de trabalho e encaminhá-los para suas ferramentas existentes ou de provedor de serviços gerenciados no local.

- Você precisa manter seu investimento atual em System Center Operations Manager e configurá-lo para monitorar os recursos de IaaS e PaaS em execução no Azure. Opcionalmente, como você está monitorando dois ambientes com características diferentes, com base em seus requisitos, você precisa determinar como a integração com o Azure Monitor dá suporte à sua estratégia.

- Como parte de sua estratégia de modernização para padronizar uma única ferramenta para reduzir o custo e a complexidade, você precisa se comprometer com Azure Monitor para monitorar os recursos no Azure e em sua rede corporativa.

A tabela a seguir resume os requisitos que Azure Monitor e System Center Operations Manager dão suporte ao monitoramento do modelo de nuvem híbrida com base em um conjunto comum de critérios.

<!-- markdownlint-disable MD033 -->

|Requisito | Azure Monitor | Operations Manager |
|:--|:---|:---|
|Requisitos de infraestrutura | Não | Sim<br> Requer no mínimo um servidor de gerenciamento e um SQL Server para hospedar o banco de dados operacional e o data warehouse de relatórios banco de dados. A complexidade aumenta quando a alta disponibilidade e a recuperação de desastres são necessárias, e há máquinas em vários sites, sistemas não confiáveis e outras considerações de design complexas.|
|Conectividade limitada-sem Internet<br> ou rede isolada | Não | Sim |
|Acesso limitado à Internet controlado por conectividade | Sim | Sim |
|Conectividade limitada – com frequência desconectada | Sim | Sim |
|Monitoramento de integridade configurável | Não | Sim |
| Teste de disponibilidade do aplicativo Web (rede isolada) | Sim, limitado<br> Azure Monitor tem suporte limitado nessa área e requer exceções de firewall personalizadas. | Sim |
| Teste de disponibilidade do aplicativo Web (distribuído globalmente) | Não | Sim |
|Monitorar cargas de trabalho de VM | Sim, limitado<br> Pode coletar logs de erros do IIS e SQL Server, eventos do Windows e contadores de desempenho. Requer a criação de consultas personalizadas, alertas e visualizações. | Sim<br> Dá suporte ao monitoramento da maioria das cargas de trabalho de servidor com pacotes de gerenciamento disponíveis. Requer o Log Analytics agente do Windows ou agente de Operations Manager na VM, relatando de volta para o grupo de gerenciamento na rede corporativa.|
|Monitorar IaaS do Azure | Sim | Sim<br> Dá suporte ao monitoramento da maior parte da infraestrutura da rede corporativa. Rastreia o estado de disponibilidade, as métricas e os alertas para VMs do Azure, SQL e armazenamento por meio do pacote de gerenciamento do Azure.|
|Monitorar o PaaS do Azure | Sim | Sim, limitado<br> Com base no que tem suporte no pacote de gerenciamento do Azure. |
|Monitoramento de serviço do Azure | Sim<br> | Sim<br> Embora não haja nenhum monitoramento nativo da integridade do serviço do Azure fornecido hoje por meio de um pacote de gerenciamento, você pode criar fluxos de trabalho personalizados para consultar alertas de integridade do serviço do Azure. Use a API REST do Azure para obter alertas por meio de suas notificações existentes.|
|Monitoramento de aplicativos Web moderno | Sim | Não |
|Monitoramento de aplicativo Web herdado | Sim, limitado, varia por SDK<br> Dá suporte ao monitoramento de versões mais antigas de aplicativos Web .NET e Java. | Sim, limitado |
|Monitorar contêineres do serviço kubernetes do Azure | Sim | Não |
|Monitorar contêineres do Docker ou do Windows | Sim | Não |
|Monitoramento de desempenho de rede | Sim | Sim, limitado<br> Dá suporte a verificações de disponibilidade e coleta estatísticas básicas de dispositivos de rede usando o SNMP (Simple Network Management Protocol) da rede corporativa.|
|Análise de dados interativa | Sim | Não<br> O depende de SQL Server Reporting Services relatórios predefinidos ou personalizados, soluções de visualização de terceiros ou uma implementação de Power BI personalizada. Há limitações de escala e desempenho com o data warehouse de Operations Manager. Integre-se com os logs de Azure Monitor como uma alternativa para os requisitos de agregação de dados. Você Obtém a integração Configurando o conector de Log Analytics.|
|Diagnóstico de ponta a ponta, análise de causa raiz e solução de problemas oportuna | Sim | Sim, limitado<br> Dá suporte a diagnóstico de ponta a ponta e solução de problemas somente para infraestrutura e aplicativos locais. O usa outros componentes do System Center ou soluções de parceiros.|
|Visualizações interativas (painéis) | Sim | Sim, limitado<br> Fornece painéis essenciais com seu console Web HTML5 ou uma experiência avançada de soluções de parceiros, como o enquadramento e o Savision. |
|Integração com ferramentas de ti ou DevOps | Sim | Sim, limitado |

<!-- markdownlint-enable MD033 -->

### <a name="collect-and-stream-monitoring-data-to-third-party-or-on-premises-tools"></a>Coletar e transmitir dados de monitoramento para ferramentas de terceiros ou locais

Para coletar métricas e logs da infraestrutura e dos recursos de plataforma do Azure, você precisa habilitar os logs de Diagnóstico do Azure para esses recursos. Além disso, com as VMs do Azure, você pode coletar métricas e logs do SO convidado habilitando a extensão de Diagnóstico do Azure. Para encaminhar os dados de diagnóstico emitidos de seus recursos do Azure para suas ferramentas locais ou provedor de serviços gerenciados, configure os [hubs de eventos](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-stream-event-hubs) para transmitir os dados para eles.

### <a name="monitor-with-system-center-operations-manager"></a>Monitorar com System Center Operations Manager

Embora System Center Operations Manager tenha sido originalmente projetado como uma solução local para monitorar entre aplicativos, cargas de trabalho e infraestrutura em execução em seu ambiente de ti, ele evoluiu para incluir recursos de monitoramento de nuvem. Ele se integra ao Azure, Office 365 e Amazon Web Services (AWS). Ele pode monitorar esses diversos ambientes com pacotes de gerenciamento que são projetados e atualizados para dar suporte a eles.  

Para clientes que fizeram investimentos significativos em Operations Manager para obter um monitoramento abrangente que esteja totalmente integrado com seus processos e ferramentas de gerenciamento de serviços de TI ou para clientes novos no Azure, é compreensível fazer o seguinte dúvidas

- Operations Manager pode continuar a agregar valor e faz sentido comercial?
- Os recursos do Operations Manager o tornam adequado para nossa organização de ti?
- A integração do Operations Manager com o Azure Monitor fornece a solução de monitoramento abrangente e econômica que precisamos?

Se você já investiu em Operations Manager, não precisa se concentrar em planejar uma migração para substituí-la imediatamente. Com o Azure ou outros provedores de nuvem que existem como uma extensão de sua própria rede local, Operations Manager pode monitorar as VMs convidadas e os recursos do Azure como se estivessem em sua rede corporativa. Essa abordagem requer uma conexão de rede confiável entre sua rede e a rede virtual do Azure com largura de banda suficiente.

Para monitorar as cargas de trabalho que estão em execução no Azure, você precisa de:

- O [pacote de gerenciamento para Azure](https://www.microsoft.com/download/details.aspx?id=50013). Ele coleta métricas de desempenho emitidas pelos serviços do Azure, como funções Web e de trabalho, Application Insights testes de disponibilidade (testes da Web), barramento de serviço do Azure e assim por diante. O pacote de gerenciamento usa a API REST do Azure para monitorar a disponibilidade e o desempenho desses recursos. Alguns tipos de serviço do Azure não têm métricas ou monitores predefinidos no pacote de gerenciamento, mas você ainda pode monitorá-los por meio das relações definidas no pacote de gerenciamento do Azure para serviços descobertos.

- O [pacote de gerenciamento do banco de dados SQL do Azure](https://www.microsoft.com/download/details.aspx?id=38829) para monitorar a disponibilidade e o desempenho de bancos de dados SQL do Azure e servidores de banco de dados SQL do Azure usando a API REST do Azure e consultas T-SQL para SQL Server exibições do sistema.

- Para monitorar o sistema operacional convidado e as cargas de trabalho em execução na VM, como SQL Server, IIS ou Apache Tomcat, você precisa baixar e importar o pacote de gerenciamento que dá suporte ao aplicativo, ao serviço e ao sistema operacional.

O conhecimento é definido no pacote de gerenciamento, que descreve como monitorar as dependências individuais e os componentes do. Ambos os pacotes de gerenciamento do Azure exigem a execução de um conjunto de etapas de configuração no Azure e Operations Manager antes que você possa começar a monitorar esses recursos.

Na camada de aplicativo, o Operations Manager oferece recursos básicos de monitoramento do desempenho de aplicativos para algumas versões herdadas do .NET e do Java. Se determinados aplicativos em seu ambiente de nuvem híbrida operam em modo offline ou isolado de rede, de forma que eles não possam se comunicar com um serviço de nuvem pública, Operations Manager APM (monitoramento do desempenho de aplicativos) pode ser uma opção viável para certos cenários limitados. Para aplicativos que não estão sendo executados em plataformas herdadas, mas são hospedados localmente e em qualquer nuvem pública que permite a comunicação por meio de um firewall (direto ou por meio de um proxy) para o Azure, use Azure Monitor Application Insights. Esse serviço oferece monitoramento de nível de código profundo, com suporte de primeira classe para ASP.NET, ASP.NET Core, Java, JavaScript e node. js.

Para qualquer aplicativo Web que possa ser acessado externamente, você deve habilitar um tipo de transação sintética conhecido como [monitoramento de disponibilidade]( https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability). É importante saber se seu aplicativo ou um ponto de extremidade HTTP/HTTPS crítico do qual seu aplicativo depende, está disponível e respondendo. Com o monitoramento de disponibilidade do Application Insights, você pode executar testes de vários data centers do Azure e fornecer informações sobre a integridade do seu aplicativo a partir de uma perspectiva global.

Embora Operations Manager seja capaz de monitorar recursos hospedados no Azure, há várias vantagens em incluir Azure Monitor, pois suas forças superam as limitações no Operations Manager e podem estabelecer uma base forte para suporte à eventual migração a partir dele. Aqui, examinamos cada um desses pontos fortes e fracos, com nossa recomendação para incluir Azure Monitor em sua estratégia de monitoramento híbrido.  

#### <a name="disadvantages-of-using-operations-manager-by-itself"></a>Desvantagens de usar o Operations Manager por si só

- A análise de dados de monitoramento em Operations Manager geralmente é realizada usando exibições predefinidas fornecidas por pacotes de gerenciamento acessados no console do, de relatórios do SQL Server Reporting Services (SSRS) ou de exibições personalizadas que os usuários finais criaram. A análise de dados ad hoc não é possível prontamente. Operations Manager relatório é inflexível. O data warehouse que fornece retenção de longo prazo dos dados de monitoramento não é dimensionado nem tem um bom desempenho. E a experiência em escrever instruções T-SQL, desenvolver uma solução Power BI ou usar soluções de terceiros é necessária para dar suporte aos requisitos para as várias pessoas da organização de ti.

- Os alertas no Operations Manager não dão suporte a expressões complexas ou incluem lógica de correlação. Para ajudar a reduzir o ruído, os alertas são agrupados para mostrar as relações entre eles e para identificar suas causas.

#### <a name="advantages-of-using-operations-manager-with-azure-monitor"></a>Vantagens de usar o Operations Manager com Azure Monitor

- Azure Monitor é a maneira de solucionar as limitações de Operations Manager. Ele complementa o banco de dados de data warehouse de Operations Manager coletando um desempenho e um dado de log importantes. Azure Monitor oferece melhor análise, desempenho (ao consultar grandes volumes de dados) e retenção do que o Operations Manager data warehouse. 

  Com a linguagem de consulta Azure Monitor, você pode criar consultas muito mais complexas e sofisticadas. Você pode executar consultas em terabytes de dados em segundos. Você pode transformar seus dados rapidamente em gráficos de pizza, gráficos de horas e muitas outras visualizações. Para analisar esses dados, você não fica mais restrito ao trabalhar com Operations Manager relatórios baseados em SQL Server Reporting Services, consultas SQL personalizadas ou outras soluções alternativas.

- Você pode fornecer uma experiência de alerta aprimorada implementando a solução de gerenciamento de alertas Azure Monitor. Os alertas gerados no grupo de gerenciamento Operations Manager podem ser encaminhados para o espaço de trabalho Azure Monitor logs Analytics. Você pode configurar a assinatura responsável por encaminhar alertas de Operations Manager para Azure Monitor logs para encaminhar apenas determinados alertas. Por exemplo, você pode encaminhar apenas alertas que atendam aos seus critérios de consulta no suporte ao gerenciamento de problemas para tendências e investigação da causa raiz de falhas ou problemas, por meio de um único painel de vidro. Além disso, você pode correlacionar outros dados de log de Application Insights ou outras fontes, para obter informações que ajudem a melhorar a experiência do usuário, aumentar o tempo de atividade e reduzir a hora de resolver incidentes.

- Você pode monitorar a infraestrutura e os aplicativos nativos de nuvem, de uma arquitetura simples ou de várias camadas no Azure, e pode usar Operations Manager para monitorar a infraestrutura local. Esse monitoramento inclui uma ou mais VMs, várias VMs colocadas em um conjunto de disponibilidade ou conjunto de dimensionamento de máquinas virtuais ou um aplicativo em contêiner implantado no AKS (serviço kubernetes do Azure) que está sendo executado em contêineres do Windows Server ou Linux.

- Você pode usar a solução Verificação de Integridade do System Center Operations Manager para avaliar proativamente o risco e a integridade de seu grupo de gerenciamento de System Center Operations Manager em intervalos regulares. Essa solução pode substituir ou complementar qualquer funcionalidade personalizada que você tenha adicionado ao seu grupo de gerenciamento.

- Usando o recurso de mapa do Azure Monitor para VMs, você pode monitorar as métricas de conectividade padrão de conexões de rede entre as VMs do Azure e as VMs locais. Essas métricas incluem tempo de resposta, solicitações por minuto, taxa de transferência de tráfego e links. Você pode identificar conexões com falha, solucionar problemas, executar a validação de migração, executar análise de segurança e verificar a arquitetura geral do serviço. O MAP pode descobrir automaticamente os componentes de aplicativos em sistemas Windows e Linux e mapear a comunicação entre os serviços. Essa automação ajuda a identificar conexões e dependências das quais você não conhece, planejar e validar a migração para o Azure e minimizar a especulação durante a resolução de incidentes.

- Usando Monitor de Desempenho de Rede, você pode monitorar a conectividade de rede entre:

   - Sua rede corporativa e o Azure.
   - Aplicativos multicamadas de missão crítica e microserviços.
   - Locais de usuário e aplicativos baseados na Web (HTTP/HTTPS).

   Essa estratégia fornece visibilidade da camada de rede, sem a necessidade de SNMP. Ele também pode apresentar, em um mapa de topologia interativo, a topologia de salto a salto de rotas entre o ponto de extremidade de origem e de destino. É uma opção melhor do que tentar realizar o mesmo resultado com o monitoramento de rede no Operations Manager ou com outras ferramentas de monitoramento de rede usadas no momento em seu ambiente.

### <a name="monitor-with-azure-monitor"></a>Monitorar com Azure Monitor

Embora uma migração para a nuvem apresente vários desafios, ela também inclui uma série de oportunidades. Ele permite que sua organização migre de uma ou mais ferramentas de monitoramento de empresa locais para não apenas reduzir as despesas de capital e custos operacionais, mas também para se beneficiar das vantagens que uma plataforma de monitoramento de nuvem, como Azure Monitor pode entregar em escala de nuvem. Examine os requisitos de monitoramento e alerta, a configuração de ferramentas de monitoramento existentes e as cargas de trabalho em transição para a nuvem. Depois que o plano for finalizado, configure Azure Monitor.

- Monitore a infraestrutura híbrida e os aplicativos, de uma arquitetura simples ou de várias camadas, na qual os componentes são hospedados entre o Azure, outros provedores de nuvem e sua rede corporativa. Os componentes podem incluir uma ou mais VMs, várias VMs colocadas em um conjunto de disponibilidade ou conjunto de dimensionamento de máquinas virtuais, ou um aplicativo em contêiner que é implantado no AKS (serviço kubernetes do Azure) em execução em contêineres do Windows Server ou Linux.

- Habilite Azure Monitor para VMs, Azure Monitor para contêineres e Application Insights para detectar e diagnosticar problemas entre infraestrutura e aplicativos. Para obter uma análise mais completa e correlação de dados coletados de vários componentes ou dependências que dão suporte ao aplicativo, você precisa usar logs de Azure Monitor.

- Crie alertas inteligentes que se aplicam a um conjunto principal de aplicativos e componentes de serviço, ajudam a reduzir o ruído de alerta com limites dinâmicos para sinais complexos e a usar a agregação de alertas com base em algoritmos de aprendizado de máquina para ajudar a identificar rapidamente o problema.

- Defina uma biblioteca de consultas e painéis para dar suporte aos requisitos das várias pessoas na organização de ti.

- Defina padrões e métodos para habilitar o monitoramento em recursos híbridos e de nuvem, uma linha de base de monitoramento para cada recurso, limites de alerta e assim por diante.  

- Configure o RBAC (controle de acesso baseado em função) para que você conceda aos usuários e grupos apenas a quantidade de acesso de que eles precisam para monitorar dados de recursos que eles são responsáveis por gerenciar.

- Inclua automação e autoatendimento para permitir que cada equipe crie, habilite e ajuste suas configurações de monitoramento e alerta, conforme necessário.

## <a name="private-cloud-monitoring"></a>Monitoramento de nuvem privada

Você pode obter o monitoramento holístico de Azure Stack com System Center Operations Manager. Especificamente, você pode monitorar as cargas de trabalho em execução no locatário, no nível de recurso, nas máquinas virtuais e na infraestrutura que hospeda Azure Stack (servidores físicos e comutadores de rede). 

Você também pode obter um monitoramento holístico com uma combinação de [recursos de monitoramento de infraestrutura](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluídos no Azure Stack. Esses recursos ajudam a exibir a integridade e os alertas de uma região Azure Stack e o [serviço de Azure monitor](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) no Azure Stack, que fornece métricas de infraestrutura de nível básico e logs para a maioria dos serviços.

Se você já investiu em Operations Manager, use o pacote de gerenciamento do Azure Stack para monitorar a disponibilidade e o estado de integridade de implantações de Azure Stack. Isso inclui regiões, provedores de recursos, atualizações, execuções de atualização, unidades de escala, nós de unidade, funções de infraestrutura e suas instâncias (entidades lógicas compostas pelos recursos de hardware). Ele usa as APIs REST de provedor de recursos de integridade e atualização para se comunicar com Azure Stack. Para monitorar servidores físicos e dispositivos de armazenamento, use o pacote de gerenciamento de fornecedores de OEM (por exemplo, fornecido pela Lenovo, Hewlett Packard ou Dell). Operations Manager pode monitorar nativamente os comutadores de rede para coletar estatísticas básicas usando SNMP. O monitoramento das cargas de trabalho de locatário é possível com o pacote de gerenciamento do Azure seguindo duas etapas básicas. Configure a assinatura que você deseja monitorar e, em seguida, adicione os monitores para essa assinatura.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Coletar os dados corretos](./data-collection.md)
