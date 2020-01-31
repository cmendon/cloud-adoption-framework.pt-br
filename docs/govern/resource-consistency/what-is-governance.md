---
title: O que é a governança dos recursos da nuvem?
description: Governança de recursos de nuvem de explicação no Azure
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 9277bf82d9034108b478536a699f96918c38ae0d
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807267"
---
<!-- markdownlint-disable MD026 -->

# <a name="cloud-resource-governance"></a>Governança de recursos de nuvem?

Em [como funciona o Azure?](../../getting-started/what-is-azure.md), você aprendeu que o Azure é uma coleção de servidores e hardware de rede executando hardware e software virtualizados em nome dos usuários. O Azure permite que os departamentos de ti e desenvolvimento de aplicativos da sua organização sejam ágeis, facilitando a criação, a leitura, a atualização e a exclusão de recursos, conforme necessário.

No entanto, embora irrestrito para recursos possa tornar os desenvolvedores mais ágeis, isso também pode levar a custos inesperados. Por exemplo, uma equipe de desenvolvimento pode ser aprovada para implantar um conjunto de recursos para teste, mas esquecer de excluí-las quando o teste for concluído. Esses recursos continuarão a acumular custos, mesmo que não sejam mais aprovados ou necessários.

A solução é governança de acesso a recursos. **Governança** é o processo contínuo de gerenciar, monitorar e auditar o uso de recursos do Azure para atender às metas e aos requisitos da sua organização.

<!-- markdownlint-disable MD034 -->

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE2ii94]

<!-- markdownlint-enable MD034 -->

Esses requisitos são exclusivos para cada organização, portanto, uma abordagem única para a governança não é útil. Em vez disso, cabe a cada organização criar seu modelo de governança usando as duas principais ferramentas de governança do Azure: **RBAC (controle de acesso baseado em função)** e **política de recursos**.

O RBAC define funções e as funções definem as operações permitidas para cada usuário atribuído a essa função. Por exemplo, a função **proprietário** permite todas as operações (criar, ler, atualizar e excluir) em um recurso, enquanto a função **leitor** permite apenas operações de leitura. As funções podem ser definidas amplamente e aplicadas a muitos tipos de recursos, ou são definidas de forma mais restrita e aplicadas a apenas alguns tipos de recursos.

As políticas de recursos definem regras para a criação de recursos. Por exemplo, uma política de recursos pode limitar a SKU de uma máquina virtual a um tamanho específico predeterminado. Outra política de recursos pode impor o aplicativo de uma marca para um centro de custo atribuído quando a solicitação é feita para criar o recurso.

Ao configurar essas ferramentas, é importante balancear a governança e a agilidade organizacional. Quanto mais restritiva for sua política de governança, menos ágil serão os desenvolvedores e os profissionais de ti. Uma política de governança restritiva pode exigir mais etapas manuais, como exigir que um desenvolvedor preencha um formulário ou envie um email a um membro da equipe de governança para criar manualmente um recurso. A equipe de governança tem capacidade finita e pode se tornar um afunilamento, resultando em equipes de desenvolvimento aguardando inprodutivamente que seus recursos sejam criados, ou recursos desnecessários que acumulam custos antes de serem excluídos.

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu o conceito de governança de recursos de nuvem, saiba mais sobre como o acesso aos recursos é gerenciado no Azure.

> [!div class="nextstepaction"]
> [Saiba mais sobre o acesso de recursos no Azure](./resource-access-management.md)
