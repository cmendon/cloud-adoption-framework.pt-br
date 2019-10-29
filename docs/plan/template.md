---
title: Implantar o plano de adoção de nuvem no Azure DevOps
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Implantar o modelo para o plano de adoção de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 3bd26321eca1747e5ed579e4394b0a4b7b713294
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048210"
---
# <a name="cloud-adoption-plan-and-azure-devops"></a>Plano de adoção de nuvem e DevOps do Azure

O Azure DevOps é o conjunto de ferramentas baseadas em nuvem para clientes do Azure que gerenciam projetos iterativos. Ele também inclui ferramentas para gerenciar pipelines de implantação e outros aspectos importantes do DevOps. 

Neste artigo, você aprenderá a implantar rapidamente uma pendência no Azure DevOps usando um modelo de plano de adoção de nuvem. Este modelo alinha os esforços de adoção de nuvem a um processo padronizado com base nas diretrizes da estrutura de adoção de nuvem.

## <a name="create-your-cloud-adoption-plan"></a>Criar seu plano de adoção de nuvem

Para implantar o plano de adoção de nuvem, abra o [gerador de demonstração do Azure DevOps](https://aka.ms/adopt/plan/generator). Essa ferramenta implantará o modelo em seu locatário DevOps do Azure. O uso da ferramenta requer as seguintes etapas:

1. Verifique se o campo de **modelo selecionado** está definido como **plano de adoção de nuvem**. Se não estiver, selecione **escolher modelo** para escolher o modelo correto.
2. Selecione sua organização do Azure DevOps na caixa de listagem suspensa **selecionar organização** .
3. Insira um nome para o novo projeto. O plano de adoção de nuvem terá esse nome quando for implantado no locatário do Azure DevOps.
4. Selecione **criar projeto** para criar um novo projeto em seu locatário, com base no modelo de plano. Uma barra de progresso mostra seu progresso na implantação do projeto.
5. Quando a implantação for concluída, selecione **navegar para o projeto** para ver o novo projeto.

Depois que o projeto tiver sido criado, continue nesta série de artigos para ver como você pode modificar o modelo para alinhá-lo ao seu plano de adoção de nuvem.

Para obter suporte adicional e orientação sobre essa ferramenta, consulte [Azure DevOps Services gerador de demonstração](https://docs.microsoft.com/azure/devops/demo-gen/?toc=%2Fazure%2Fdevops%2Fdemo-gen%2Ftoc.json&bc=%2Fazure%2Fdevops%2Fdemo-gen%2Fbreadcrumb%2Ftoc.json&view=azure-devops).

## <a name="bulk-edit-the-cloud-adoption-plan"></a>Editar em massa o plano de adoção de nuvem

Quando o projeto de plano tiver sido implantado, você poderá usar o Microsoft Excel para modificá-lo. É muito mais fácil criar novas cargas de trabalho ou ativos no plano usando o Excel do que usando a experiência do navegador DevOps do Azure.

Para preparar sua estação de trabalho para edição em massa, confira [Adicionar ou modificar itens em massa com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

## <a name="use-the-cloud-adoption-plan"></a>Usar o plano de adoção de nuvem

O plano de adoção de nuvem organiza as atividades por tipo de atividade:

- **Epics:** Um *Epic* representa uma fase geral do ciclo de vida de adoção da nuvem.
- **Recursos do:** Os recursos são usados para organizar objetivos específicos em cada fase. Por exemplo, a migração de uma carga de trabalho específica seria um recurso.
- **Histórias de usuários:** As histórias de usuário agrupam o trabalho em coleções lógicas de atividades com base em uma meta específica.
- **Tarefas:** As tarefas são o trabalho real a ser feito.

Em cada camada, as atividades são então sequenciadas com base em dependências. As atividades são vinculadas a artigos na estrutura de adoção de nuvem para esclarecer o objetivo ou a tarefa em questão.

A exibição mais clara do plano de adoção de nuvem vem da exibição da pendência de **Epics** . Para obter ajuda com a alteração da exibição da pendência de **Epics** , consulte o artigo sobre como [exibir uma pendência](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops#view-a-backlog-or-portfolio-backlog). Nessa exibição, é fácil planejar e gerenciar o trabalho necessário para concluir a fase atual do ciclo de vida de adoção.

> [!NOTE]
> O estado atual do plano de adoção de nuvem se concentra muito nos esforços de migração. As tarefas relacionadas à governança, inovação ou operações devem ser preenchidas manualmente.

## <a name="align-the-cloud-adoption-plan"></a>Alinhar o plano de adoção de nuvem

As páginas de visão geral das fases de estratégia e planejamento do ciclo de vida de adoção de nuvem fazem referência ao [modelo de estratégia e planejamento da estrutura de adoção de nuvem](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/Microsoft-Cloud-Adoption-Framework-Strategy-and-Plan-Template.docx). Esse modelo organiza as decisões e os pontos de dados que alinharão o modelo para o plano de adoção de nuvem com seus planos específicos de adoção. Se você ainda não fez isso, talvez queira concluir os exercícios relacionados à [estratégia](../strategy/index.md) e ao [planejamento](../plan/index.md) antes de alinhar seu novo projeto.

Os artigos a seguir dão suporte ao alinhamento do plano de adoção de nuvem:

- [Cargas de trabalho](./workloads.md): alinhar recursos dentro do migração na nuvem Epic para capturar cada carga de trabalho a ser migrada ou modernizada. Adicione e modifique esses recursos para capturar o esforço para migrar as 10 principais cargas de trabalho.
- [Ativos](./assets.md): cada ativo (VM, aplicativo ou dados) é representado pelas histórias de usuário em cada carga de trabalho. Adicione e modifique as histórias de usuários para alinhá-las ao seu espaço digital.
- [Racionalização](./review-rationalization.md): como cada carga de trabalho é definida, as suposições iniciais sobre essa carga de trabalho podem ser desafiadas. Isso pode resultar em alterações nas tarefas de cada ativo.
- [Criar planos de lançamento](./iteration-paths.md): os caminhos de iteração estabelecem planos de liberação alinhando esforços com várias versões e iterações.
- [Estabelecer linhas](./timelines.md)do tempo: a definição de datas de início e término para cada iteração cria uma linha do tempo para gerenciar o projeto geral.

Esses cinco artigos ajudam com cada uma das tarefas de alinhamento necessárias para começar a gerenciar seus esforços de adoção. A próxima etapa o ajudará a começar a usar o exercício de alinhamento.

## <a name="next-steps"></a>Próximos passos

Comece a alinhar seu projeto de plano [definindo e priorizando cargas de trabalho](./workloads.md).

> [!div class="nextstepaction"]
> [Definir e priorizar cargas de trabalho](./workloads.md)
