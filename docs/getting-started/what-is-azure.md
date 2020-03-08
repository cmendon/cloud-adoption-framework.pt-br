---
title: Como funciona o Azure?
description: Aprenda as noções básicas sobre a estrutura interna e o funcionamento da plataforma de nuvem do Azure e da virtualização de nuvem.
author: alexbuckgit
ms.author: abuck
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: governance
ms.openlocfilehash: 39373c0f2c4c7d96613fd10d5734a2826b6f1933
ms.sourcegitcommit: 58ea417a7df3318e3d1a76d3807cc4e7e3976f52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78892057"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-does-azure-work"></a>Como funciona o Azure?

O Azure é a plataforma de nuvem pública da Microsoft. O Azure oferece uma grande coleção de serviços, incluindo PaaS (plataforma como serviço), IaaS (infraestrutura como serviço) e recursos de serviço de banco de dados gerenciado. Mas o que exatamente é o Azure e como ele funciona?

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ixGo]

O Azure, como outras plataformas de nuvem, se baseia em uma tecnologia conhecida como _virtualização_. A maior parte do hardware do computador pode ser emulada em software, porque a maior parte dele é apenas um conjunto de instruções codificado de forma permanente ou semipermanente em silício. Usando uma camada de emulação que mapeia instruções de software para instruções de hardware, o hardware virtualizado pode ser executado em um software como se fosse o próprio hardware real.

Basicamente, a nuvem é um conjunto de servidores físicos em um ou mais datacenters que executam o hardware virtualizado em nome dos clientes. Então, como a nuvem cria, inicia, interrompe e exclui milhões de instâncias de hardware virtualizado para milhões de clientes simultaneamente?

Para entender isso, vamos examinar a arquitetura do hardware no datacenter. Dentro de cada datacenter está uma coleção de servidores localizados em racks de servidor. Cada rack de servidor contém muitas **folhas** de servidor, bem como um comutador de rede que fornece conectividade de rede e uma PDU (unidade de distribuição de energia) que fornece energia. Às vezes, os racks são agrupados em unidades maiores conhecidas como _clusters_.

Em cada rack ou cluster, a maioria dos servidores é designada para executar essas instâncias de hardware virtualizado em nome do usuário. No entanto, alguns dos servidores executam o software de gerenciamento de nuvem conhecido como controlador de malha. O _controlador de malha_ é um aplicativo distribuído com muitas responsabilidades. Ele aloca serviços, monitora a integridade do servidor e dos serviços em execução nele e restaura servidores quando ocorre uma falha.

Cada instância do controlador de malha está conectada a outro conjunto de servidores que executam o software de orquestração da nuvem, normalmente conhecido como um _front-end_. O front-end hospeda os serviços Web, as APIs RESTful e os bancos de dados internos do Azure usados para todas as funções executadas pela nuvem.

Por exemplo, o front-end hospeda os serviços que lidam com as solicitações do cliente para alocar recursos do Azure, como [máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines), e serviços como [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction). Primeiro, o front-end valida o usuário e verifica se o usuário está autorizado a alocar os recursos solicitados. Nesse caso, o front-end verifica um banco de dados para localizar um rack de servidor com capacidade suficiente e, em seguida, instrui o controlador de malha nesse rack para alocar o recurso.

Fundamentalmente, o Azure é uma enorme coleção de servidores e hardware de rede que executam um conjunto complexo de aplicativos distribuídos para orquestrar a configuração e a operação do hardware e software virtualizados nesses servidores. É essa orquestração que torna o Azure tão potente&mdash;os usuários não são mais responsáveis por manter e atualizar o hardware, pois o Azure faz tudo isso por trás dos bastidores.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Saiba mais sobre a adoção de nuvem com a [estrutura de adoção Microsoft Cloud para o Azure](https://docs.microsoft.com/azure/cloud-adoption-framework).

> [!div class="nextstepaction"]
> [Saiba mais sobre a estrutura de adoção do Microsoft Cloud para o Azure](https://docs.microsoft.com/azure/cloud-adoption-framework)
