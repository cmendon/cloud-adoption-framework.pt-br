---
title: Como funciona o Azure?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Explicação sobre o funcionamento interno do Azure
author: alexbuckgit
ms.author: abuck
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: governance
ms.openlocfilehash: 6aabf9545aa6774b63d3dbd201373273c3f8f1ab
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70829144"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-does-azure-work"></a>Como funciona o Azure?

O Azure é a plataforma de nuvem pública da Microsoft. O Azure oferece uma grande coleção de serviços, incluindo PaaS (plataforma como serviço), IaaS (infraestrutura como serviço) e recursos de serviço de banco de dados gerenciado. Mas o que exatamente é o Azure e como ele funciona?

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ixGo]

O Azure, como outras plataformas de nuvem, se baseia em uma tecnologia conhecida como **virtualização**. A maior parte do hardware do computador pode ser emulada em software, porque a maior parte dele é apenas um conjunto de instruções codificado de forma permanente ou semipermanente em silício. Usando uma camada de emulação que mapeia instruções de software para instruções de hardware, o hardware virtualizado pode ser executado em um software como se fosse o próprio hardware real.

Basicamente, a nuvem é um conjunto de servidores físicos em um ou mais datacenters que executam o hardware virtualizado em nome dos clientes. Então, como a nuvem cria, inicia, interrompe e exclui milhões de instâncias de hardware virtualizado para milhões de clientes simultaneamente?

Para entender isso, vamos examinar a arquitetura do hardware no datacenter. Dentro de cada datacenter está uma coleção de servidores localizados em racks de servidor. Cada rack de servidor contém muitas **folhas** de servidor, bem como um comutador de rede que fornece conectividade de rede e uma PDU (unidade de distribuição de energia) que fornece energia. Às vezes, os racks são agrupados em unidades maiores conhecidas como **clusters**.

Em cada rack ou cluster, a maioria dos servidores é designada para executar essas instâncias de hardware virtualizado em nome do usuário. No entanto, alguns dos servidores executam o software de gerenciamento de nuvem conhecido como controlador de malha. O **controlador de malha** é um aplicativo distribuído com muitas responsabilidades. Ele aloca serviços, monitora a integridade do servidor e dos serviços em execução nele e restaura servidores quando ocorre uma falha.

Cada instância do controlador de malha está conectada a outro conjunto de servidores que executam o software de orquestração da nuvem, normalmente conhecido como um **front-end**. O front-end hospeda os serviços Web, as APIs RESTful e os bancos de dados internos do Azure usados para todas as funções executadas pela nuvem.

Por exemplo, o front-end hospeda os serviços que lidam com as solicitações do cliente para alocar recursos do Azure, como [máquinas virtuais](/azure/virtual-machines), e serviços como [Cosmos DB](/azure/cosmos-db/introduction). Primeiro, o front-end valida o usuário e verifica se o usuário está autorizado a alocar os recursos solicitados. Nesse caso, o front-end verifica um banco de dados para localizar um rack de servidor com capacidade suficiente e, em seguida, instrui o controlador de malha nesse rack para alocar o recurso.

Fundamentalmente, o Azure é uma enorme coleção de servidores e hardware de rede que executam um conjunto complexo de aplicativos distribuídos para orquestrar a configuração e a operação do hardware e software virtualizados nesses servidores. É essa orquestração que torna o Azure tão potente&mdash;que os usuários não são mais responsáveis por manter e atualizar o hardware, pois o Azure faz tudo isso por trás dos bastidores.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende os elementos internos do Azure, saiba mais sobre a governança de recursos de nuvem.

> [!div class="nextstepaction"]
> [Saiba mais sobre governança de recursos](../governance/resource-consistency/what-is-governance.md)

<!-- links -->

[docs-add-users-to-aad]: /azure/active-directory/add-users-azure-active-directory?toc=/azure/architecture/cloud-adoption-guide/toc.json
