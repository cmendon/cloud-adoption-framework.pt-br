---
title: Guia de monitoramento de nuvem – estratégia de monitoramento para modelos de implantação em nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Escolha quando usar Azure Monitor ou System Center Operations Manager no Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: badf03f3616de8e6612221282aa24996f0b6e8f8
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221137"
---
# <a name="cloud-monitoring-guide-monitoring-strategy-for-cloud-deployment-models"></a>Guia de monitoramento de nuvem: Estratégia de monitoramento para modelos de implantação em nuvem

Este artigo inclui nossa estratégia de monitoramento recomendada para cada um dos modelos de implantação de nuvem, com base nos seguintes critérios:

- Você precisa de compromisso contínuo com Operations Manager ou outra plataforma de monitoramento corporativo. Isso ocorre devido à integração com seus processos de operações de ti, conhecimento e experiência, ou porque determinada funcionalidade ainda não está disponível em Azure Monitor.
- Você precisa monitorar cargas de trabalho locais e na nuvem pública ou apenas na nuvem.
- Sua estratégia de migração de nuvem inclui modernizar operações de ti e migrar para nossos serviços de monitoramento de nuvem e soluções.
- Você pode ter sistemas críticos que são gapped ou isolados fisicamente, hospedados em uma nuvem privada ou em hardware físico, e precisam ser monitorados.

Nossa estratégia inclui suporte para monitoramento de infraestrutura (cargas de trabalho de computação, armazenamento e servidor), aplicativo (usuário final, exceções e cliente) e recursos de rede para fornecer uma perspectiva de monitoramento completa orientada a serviços.

## <a name="azure-cloud-monitoring"></a>Monitoramento de nuvem do Azure

O Azure Monitor é o serviço de plataforma que fornece uma única fonte para monitorar os recursos do Azure. Ele foi projetado para soluções de nuvem criadas no Azure e que dão suporte a um recurso comercial baseado em cargas de trabalho de VM ou arquiteturas complexas que usam microserviços e outros recursos de plataforma. Ele monitora todas as camadas da pilha, começando com serviços de locatário, como Azure Active Directory Domain Services, e eventos de nível de assinatura e integridade de serviço do Azure. Ele também monitora recursos de infraestrutura, como VMs, armazenamento e recursos de rede, e, na camada superior, seu aplicativo. Monitorar cada uma dessas dependências e coletar os sinais certos que cada um pode emitir oferece a observação de aplicativos e a principal infraestrutura de que você precisa.

A tabela a seguir resume a abordagem recomendada para monitorar cada camada da pilha.

<!-- markdownlint-disable MD033 -->

Camada | Resource | Escopo | Método
---|---|---|----
Aplicativo | Aplicativo baseado na Web em execução em .NET, .NET Core, Java, JavaScript e plataforma node. js em uma VM do Azure, serviços de Azure App, Service Fabric do Azure, Azure Functions e serviços de nuvem do Azure | Monitore um aplicativo Web ao vivo para detectar automaticamente anomalias de desempenho, identificar exceções de código e problemas e coletar telemetria de usabilidade. |  Application Insights
Contêineres | Instâncias de contêiner do Azure/serviço kubernetes do Azure | Monitore a capacidade, a disponibilidade e o desempenho das cargas de trabalho em execução em contêineres e instâncias de contêiner. | Azure Monitor para contêineres
Sistema operacional convidado | Sistema operacional de VM Linux e Windows | Monitore a capacidade, a disponibilidade e o desempenho. Mapeie as dependências hospedadas em cada VM, incluindo a visibilidade de conexões de rede ativas entre servidores, latência de conexão de entrada e saída e portas em qualquer arquitetura conectada a TCP. | Azure Monitor para VMs
Recursos do Azure – PaaS | Serviços de banco de dados do Azure (por exemplo, SQL ou mySQL) | Banco de dados do Azure para métricas de desempenho do SQL. | Habilite o log de diagnóstico para transmitir dados SQL para logs de Azure Monitor.
Recursos do Azure – IaaS | 1. Armazenamento do Azure<br/> 2. Gateway de Aplicativo do Azure<br/> 3. Azure Key Vault<br/> 4. Grupos de segurança de rede<br/> 5. Gerenciador de Tráfego do Azure | 1. Capacidade, disponibilidade e desempenho.<br/> 2. Logs de diagnóstico e desempenho (atividade, acesso, desempenho e firewall).<br/> 3. Monitore como e quando os cofres de chaves são acessados e por quem.<br/> 4. Monitore eventos quando as regras são aplicadas e o contador de regras de quantas vezes uma regra é aplicada para negar ou permitir.<br/>5. Monitore a disponibilidade do status do ponto de extremidade. | 1. Métricas de armazenamento para armazenamento de BLOBs.<br/> 2. Habilite o log de diagnóstico e configure o streaming para Azure Monitor logs.<br/> 3. Habilite o log de diagnóstico e configure o streaming para Azure Monitor logs e habilite a [solução de análise de Azure Key Vault](https://docs.microsoft.com/azure/azure-monitor/insights/azure-key-vault). <br/> 4. Habilite o log de diagnóstico de grupos de segurança de rede e configure o streaming para Azure Monitor logs.<br/> 5. Habilite o log de diagnóstico dos pontos de extremidade do Gerenciador de tráfego e configure o streaming para Azure Monitor logs.
Rede| Comunicação entre sua máquina virtual e um ou mais pontos de extremidade (outra VM, um nome de domínio totalmente qualificado, um identificador de recurso uniforme ou um endereço IPv4). | Monitore a acessibilidade, a latência e as alterações de topologia de rede que ocorrem entre a VM e o ponto de extremidade. | Observador de Rede do Azure
Assinatura do Azure | Integridade do serviço do Azure e integridade básica do recurso | <li> Ações administrativas executadas em um serviço ou recurso.<br/><li> A integridade do serviço com um serviço do Azure está em um estado degradado ou indisponível.<br/><li> Problemas de integridade detectados com um recurso do Azure da perspectiva do serviço do Azure.<br/><li> Operações executadas com o dimensionamento automático do Azure indicando uma falha ou exceção. <br/><li> Operações executadas com Azure Policy indicando que ocorreu uma ação permitida ou negada.<br/><li> Registro de alertas gerados pela central de segurança do Azure. |Entregue no log de atividades para monitoramento e alertas usando Azure Resource Manager.
Locatário do Azure|Active Directory do Azure || Habilite o log de diagnóstico e configure o streaming para Azure Monitor logs.

<!-- markdownlint-enable MD033 -->

## <a name="hybrid-cloud-monitoring"></a>Monitoramento de nuvem híbrida

Esta seção está em desenvolvimento no momento para fornecer um conjunto abrangente de recomendações que abordam seu interesse para esse modelo de nuvem e serão disponibilizadas em breve.  

## <a name="private-cloud-monitoring"></a>Monitoramento de nuvem privada

Você pode obter o monitoramento holístico de Azure Stack com System Center Operations Manager. Especificamente, você pode monitorar as cargas de trabalho em execução no locatário, no nível de recurso, nas máquinas virtuais e na infraestrutura que hospeda Azure Stack (servidores físicos e comutadores de rede). Você também pode obter um monitoramento holístico com uma combinação de [recursos de monitoramento de infraestrutura](https://docs.microsoft.com/azure/azure-stack/azure-stack-monitor-health) incluídos no Azure Stack. Esses recursos ajudam a exibir a integridade e os alertas de uma região Azure Stack e o [serviço de Azure monitor](https://docs.microsoft.com/azure/azure-stack/user/azure-stack-metrics-azure-data) no Azure Stack, que fornece métricas de infraestrutura de nível básico e logs para a maioria dos serviços.

Se você já investiu em Operations Manager, use o pacote de gerenciamento do Azure Stack para monitorar a disponibilidade e o estado de integridade de implantações de Azure Stack. Isso inclui regiões, provedores de recursos, atualizações, execuções de atualização, unidades de escala, nós de unidade, funções de infraestrutura e suas instâncias (entidades lógicas compostas pelos recursos de hardware). Ele usa as APIs REST de provedor de recursos de integridade e atualização para se comunicar com Azure Stack. Para monitorar servidores físicos e dispositivos de armazenamento, use o pacote de gerenciamento de fornecedores de OEM (por exemplo, fornecido pela Lenovo, Hewlett Packard ou Dell). Operations Manager pode monitorar nativamente os comutadores de rede para coletar estatísticas básicas usando o protocolo SNMP. O monitoramento das cargas de trabalho de locatário é possível com o pacote de gerenciamento do Azure seguindo duas etapas básicas. Configure a assinatura que você deseja monitorar e, em seguida, adicione os monitores para essa assinatura.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Como coletar os dados certos](./data-collection.md)
