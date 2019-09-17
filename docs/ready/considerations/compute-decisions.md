---
title: Decisões de design do computação para Preparação para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisões de design do computação para Preparação para o Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 0569dd472e3dd85c13bb3872a351d6eec4868e39
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71025188"
---
# <a name="compute-design-decisions"></a>Decisões de design de computação

Determinar os requisitos de computação para hospedar suas cargas de trabalho é uma consideração fundamental durante o preparo para a adesão à nuvem. Os produtos e os serviços de computação do Azure são compatíveis com uma ampla variedade de cenários e recursos de computação de carga de trabalho. A maneira como você configura o ambiente de zona de acesso para dar suporte aos requisitos de computação depende dos requisitos de governança, técnicos e empresariais referentes às cargas de trabalho.

## <a name="identify-compute-services-requirements"></a>Identificar requisitos de serviços de computação

Como parte da avaliação e preparação da zona de acesso, você precisa identificar todos os recursos de computação aos quais a zona de acesso deverá dar suporte. Esse processo envolve avaliar cada um dos aplicativos e serviços que compõem as cargas de trabalho para determinar os requisitos de computação e hospedagem. Depois de identificar e documentar os requisitos, você pode criar políticas para que a zona de acesso controle quais tipos de recursos serão permitidos com base nas necessidades das cargas de trabalho.

Para cada aplicativo ou serviço que você implantará no ambiente de zona de acesso, use a seguinte árvore de decisão como um ponto de partida para ajudá-lo a determinar os requisitos dos serviços de computação:

![Árvore de decisão de serviços de computação do Azure](../../_images/ready/compute-decision-tree.png)

> [!NOTE]
> Saiba mais sobre como avaliar as opções de computação para cada um dos seus aplicativos ou serviços no [guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-overview).

### <a name="key-questions"></a>Principais perguntas

Responda às seguintes perguntas sobre as cargas de trabalho para ajudá-lo a tomar decisões com base na árvore de decisão de serviços de computação do Azure:

- **Você está criando aplicativos e serviços novos ou migrando de cargas de trabalho locais existentes?** O desenvolvimento de novos aplicativos como parte de seus esforços da adesão à nuvem permite aproveitar ao máximo as tecnologias modernas de hospedagem baseadas em nuvem desde a fase de design.
- **Se você estiver migrando cargas de trabalho existentes, elas poderão aproveitar as tecnologias de nuvem modernas?** A migração de cargas de trabalho locais requer análise: Você pode otimizar facilmente aplicativos e serviços existentes para tirar proveito das tecnologias de nuvem modernas ou uma abordagem *lift-and-shift* funciona melhor para suas cargas de trabalho?
- **Seus aplicativos ou serviços podem tirar proveito de contêineres?** Se os aplicativos forem bons candidatos para hospedagem em contêiner, você poderá aproveitar as possibilidades de eficiência de recursos, escalabilidade e orquestração fornecidas pelos [serviços de contêiner do Azure](https://azure.microsoft.com/product-categories/containers). Os serviços [Armazenamento em Disco do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) e [Arquivos do Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) podem ser usados para armazenamento persistente para aplicativos em contêineres.
- **Os aplicativos são baseados na Web ou em API. Eles usam PHP, ASP.NET, Node.js ou tecnologias semelhantes?** Os aplicativos Web podem ser implantados em instâncias gerenciadas do [Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/overview), evitando que você tenha que manter máquinas virtuais para fins de hospedagem.
- **Você precisará de controle total sobre o sistema operacional e o ambiente de hospedagem da carga de trabalho?** Se você precisar controlar o ambiente de hospedagem, incluindo o sistema operacional, os discos, o software em execução local e outras configurações, poderá usar as [Máquinas Virtuais do Azure](https://azure.microsoft.com/services/virtual-machines) para hospedar os aplicativos e serviços. Além de escolher os tamanhos de máquina virtual e os níveis de desempenho, suas decisões relacionadas ao armazenamento em disco virtual afetarão o desempenho e os SLAs relacionados às cargas de trabalho baseadas em IaaS (infraestrutura como serviço). Para obter mais informações, confira a documentação do [Armazenamento em Disco do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview).
- **Sua carga de trabalho envolverá recursos de HPC (computação de alto desempenho)?** O [Lote do Azure](https://docs.microsoft.com/azure/batch/batch-technical-overview) fornece planejamento de trabalho e dimensionamento automático de recursos de computação como um serviço de plataforma, facilitando a execução em grande escala de aplicativos HPC e paralelos na nuvem.
- **Seus aplicativos usarão uma arquitetura de microsserviços?** Os aplicativos que usam uma arquitetura baseada em microsserviços podem aproveitar várias tecnologias de computação otimizadas. As cargas de trabalho independentes controladas por eventos podem usar o [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) para criar aplicativos escalonáveis e sem servidor que não precisam de uma infraestrutura. Para aplicativos que exigem mais controle sobre o ambiente em que os microsserviços são executados, você pode usar serviços de contêiner como as [Instâncias de Contêiner do Azure](https://docs.microsoft.com/azure/container-instances/container-instances-overview), o [Serviço de Kubernetes do Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes) e o [Service Fabric do Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).

> [!NOTE]
> A maioria dos serviços de computação do Azure é usada em combinação com o Armazenamento do Azure. Consulte as [diretrizes de decisões de armazenamento](./storage-guidance.md) para tomar decisões relacionadas a armazenamento.

## <a name="common-compute-scenarios"></a>Cenários comuns de computação

A tabela a seguir ilustra alguns cenários de uso comum e os serviços de computação recomendados para lidar com eles:

| **Cenário** | **Serviço de computação** |
| --- | --- |
| Preciso provisionar máquinas virtuais do Linux e Windows em apenas alguns segundos com as configurações de minha escolha. | [Máquinas Virtuais do Azure](https://azure.microsoft.com/services/virtual-machines) |
| Preciso alcançar alta disponibilidade por meio do dimensionamento automático para criar milhares de VMs em alguns minutos. | [Conjuntos de dimensionamento de máquinas virtuais](https://azure.microsoft.com/services/virtual-machine-scale-sets) |
| Quero simplificar a implantação, o gerenciamento e as operações do Kubernetes. | [AKS (Serviço de Kubernetes do Azure)](https://azure.microsoft.com/services/kubernetes-service) |
| Preciso acelerar o desenvolvimento de aplicativos usando uma arquitetura sem servidor orientada a eventos. | [Funções do Azure](https://azure.microsoft.com/services/functions) |
| Preciso desenvolver microsserviços e orquestrar contêineres no Windows e no Linux. | [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric) |
| Quero criar rapidamente aplicativos de nuvem para a Web e dispositivos móveis usando uma plataforma totalmente gerenciada. | [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service) |
| Quero colocar aplicativos em contêineres e executar facilmente contêineres usando apenas um comando. | [Instâncias de Contêiner do Azure](https://azure.microsoft.com/services/container-instances) |
| Preciso agendar trabalhos com escala de nuvem e gerenciamento de computação com a capacidade de escalonar a dezenas, centenas ou milhares de máquinas virtuais. | [Lote do Azure](https://azure.microsoft.com/services/batch) |
| Preciso criar aplicativos de nuvem e APIs escalonáveis e altamente disponíveis que possam ajudar a me concentrar nos aplicativos em vez do hardware. | [Serviços de Nuvem do Azure](https://azure.microsoft.com/services/cloud-services) |

## <a name="regional-availability"></a>Disponibilidade regional

O Azure permite que você ofereça serviços na escala necessária para chegar a seus clientes e parceiros, _onde quer que eles estejam_. Um fator primordial no planejamento da implantação na nuvem é determinar que região do Azure hospedará seus recursos de carga de trabalho.

Algumas opções de computação, como o Serviço de Aplicativo do Azure, estão em disponibilidade geral na maioria das regiões do Azure. No entanto, alguns serviços de computação têm suporte apenas em algumas regiões. Alguns tipos de máquina virtual e os respectivos tipos de armazenamento associados têm disponibilidade regional limitada. Antes de decidir em quais regiões você implantará seus recursos de computação, recomendamos que você consulte a [página de regiões](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=azure-vmware-cloudsimple,cloud-services,batch,container-instances,app-service,service-fabric,functions,kubernetes-service,virtual-machine-scale-sets,virtual-machines) para verificar o status mais recente da disponibilidade regional.

Para saber mais sobre a infraestrutura global do Azure, confira a [página das regiões do Azure](https://azure.microsoft.com/global-infrastructure/regions). Você também pode exibir os [produtos disponíveis por região](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) para obter detalhes específicos sobre os serviços gerais que estão disponíveis em cada região do Azure.

## <a name="data-residency-and-compliance-requirements"></a>Requisitos de conformidade e residência de dados

Os requisitos legais e contratuais relacionados ao armazenamento de dados geralmente serão aplicados às suas cargas de trabalho. Esses requisitos podem variar de acordo com a localização da sua organização, a jurisdição em que os arquivos e os dados são armazenados e processados e o setor empresarial pertinente. Os componentes das obrigações de dados a serem considerados incluem a classificação de dados, a localização dos dados e as respectivas responsabilidades de proteção de dados no modelo de responsabilidade compartilhada. Muitas soluções de computação dependem de recursos de armazenamento vinculados. Esse requisito também pode influenciar suas decisões de computação. Para obter ajuda no entendimento desses requisitos, confira o White Paper [Como conseguir residência e segurança de dados em conformidade com o Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Parte dos seus esforços de conformidade pode incluir o controle do local em que os recursos de computação ficam fisicamente. As regiões do Azure são organizadas em grupos chamados geografias. Uma [geografia do Azure](https://azure.microsoft.com/global-infrastructure/geographies) garante que os requisitos de residência, de soberania, de conformidade e de resiliência de dados sejam respeitados dentro de limites geográficos e políticos. Se as cargas de trabalho estiverem sujeitas à soberania de dados ou outros requisitos de conformidade, você deverá implantar os recursos de armazenamento em regiões em uma geografia do Azure em conformidade.

## <a name="establish-controls-for-compute-services"></a>Estabelecer controles para serviços de computação

Ao preparar o ambiente de zona de acesso, você poderá estabelecer controles que limitarão quais recursos cada usuário poderá implantar. Os controles podem ajudá-lo a gerenciar custos e limitar riscos de segurança, permitindo que os desenvolvedores e as equipes de TI implantem e configurem recursos necessários para dar suporte às suas cargas de trabalho.

Depois de identificar e documentar os requisitos da zona de acesso, você pode usar o [Azure Policy](https://docs.microsoft.com/azure/governance/policy/overview) para controlar os recursos de computação permitidos para os usuários criarem. Os controles podem assumir a forma de [permissão ou negativa da criação de tipos de recursos de computação](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). Por exemplo, você pode restringir os usuários a criarem somente recursos do Serviço de Aplicativo do Azure ou do Azure Functions. Você também pode usar a política para controlar as opções permitidas quando um recurso é criado, como [restringir quais SKUs de máquina virtual podem ser provisionadas](https://docs.microsoft.com/azure/governance/policy/samples/allowed-skus-storage) ou [permitir apenas imagens de VM específicas](https://docs.microsoft.com/azure/governance/policy/samples/allowed-custom-images).

As políticas podem ser delimitadas a recursos, grupos de recursos, assinaturas e grupos de gerenciamento. Você pode incluir suas políticas em definições do [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) e aplicá-las repetidamente em todo o estado de nuvem.

