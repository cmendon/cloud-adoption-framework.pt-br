---
title: Priorizar e definir cargas de trabalho para um plano de adoção de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Priorizar e definir cargas de trabalho para um plano de adoção de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: e7582df81e305ab602c8172b5e93531eb8112432
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022277"
---
# <a name="prioritize-and-define-workloads-for-a-cloud-adoption-plan"></a>Priorizar e definir cargas de trabalho para um plano de adoção de nuvem

Estabelecer prioridades claras e acionáveis é um dos segredos para uma adoção de nuvem bem-sucedida. A tentação natural é investir tempo na definição de todas as cargas de trabalho que possam ser afetadas durante a adoção da nuvem. Mas isso é coproduto, especialmente no início do processo de adoção.

Em vez disso, recomendamos que sua equipe se concentre em priorizar minuciosamente e documentar as 10 primeiras cargas de trabalho. Após a implementação do plano de adoção começar, a equipe poderá manter uma lista das próximas 10 cargas de trabalho de prioridade mais alta. Essa abordagem fornece informações suficientes para planejar as próximas iterações.

Limitar o plano a 10 cargas de trabalho incentiva a agilidade e o alinhamento das prioridades à medida que os critérios de negócios mudam. Essa abordagem também faz espaço para a equipe de adoção de nuvem aprender e refinar as estimativas. Mais importante, ele remove o planejamento extensivo como uma barreira para uma mudança de negócios efetiva.

## <a name="what-is-a-workload"></a>O que é uma carga de trabalho?

No contexto de uma adoção de nuvem, uma carga de trabalho é uma coleção de ativos de ti (servidores, VMs, aplicativos, dados ou dispositivos) que, coletivamente, dá suporte a um processo definido. As cargas de trabalho podem dar suporte a mais de um processo. As cargas de trabalho também podem depender de outros ativos compartilhados ou plataformas maiores. No entanto, uma carga de trabalho deve ter limites definidos em relação aos ativos dependentes e aos processos que dependem da carga de trabalho. Muitas vezes, as cargas de trabalho podem ser visualizadas monitorando o tráfego de rede entre os ativos de ti.

## <a name="prerequisites"></a>Pré-requisitos

As entradas estratégicas da lista de verificação de pré-requisitos tornam as tarefas a seguir muito mais fáceis de realizar. Para obter ajuda com a coleta dos dados discutidos neste artigo, examine a [lista de verificação de pré-requisitos](./prerequisites.md).

## <a name="initial-workload-prioritization"></a>Priorização de carga de trabalho inicial

Durante o processo de [racionalização incremental](../digital-estate/rationalize.md), sua equipe deve concordar com uma abordagem de "potência de 10", que consiste em 10 cargas de trabalho de prioridade. Essas cargas de trabalho servem como um limite inicial para o planejamento de adoção.

Se você decidir que uma racionalização de imóveis digital não é necessária, recomendamos que as equipes de adoção de nuvem e a equipe de estratégia de nuvem concordem em uma lista de 10 aplicativos para servir como o foco inicial da migração. Recomendamos que essas 10 cargas de trabalho contenham uma mistura de cargas de trabalho simples (menos de 10 ativos em uma implantação independente) e cargas de trabalho mais complexas. Essas 10 cargas de trabalho iniciarão o processo de priorização da carga de trabalho.

> [!NOTE]
> A potência de 10 serve como um limite inicial para o planejamento, para focar a energia e o investimento na análise de estágio inicial. No entanto, o ato de analisar e definir cargas de trabalho provavelmente causará alterações na lista de cargas de trabalho de prioridade.

## <a name="add-workloads-to-your-cloud-adoption-plan"></a>Adicionar cargas de trabalho ao seu plano de adoção de nuvem

No artigo anterior, [plano de adoção de nuvem e DevOps do Azure](./template.md), você criou um plano de adoção de nuvem no Azure DevOps.

Agora você pode representar as cargas de trabalho na potência de 10 listas em seu plano de adoção de nuvem. A maneira mais fácil de fazer isso é por meio da edição em massa no Microsoft Excel. Para preparar sua estação de trabalho para edição em massa, confira [Adicionar ou modificar itens em massa com o Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

A etapa 5 deste artigo indica que você selecionou a **lista de entrada**. Em vez disso, selecione **lista de consulta**. Em seguida, na lista suspensa **selecionar uma consulta** , selecione a consulta do **modelo de carga de trabalho** . Essa consulta carrega todos os esforços relacionados à migração de uma única carga de trabalho em sua planilha.

Depois que os itens de trabalho para o modelo de carga de trabalho forem carregados, siga estas etapas para começar a adicionar novas cargas de trabalhos:

1. Copie todos os itens que têm a marca do **modelo de carga de trabalho** na coluna da extrema direita.
2. Cole as linhas copiadas abaixo do último item de linha na tabela.
3. Altere a célula de título do novo recurso do **modelo de carga de trabalho** para o nome da nova carga de trabalho.
4. Cole a célula nome da nova carga de trabalho na coluna marca de todas as linhas abaixo do novo recurso. Tenha cuidado para não alterar as marcas ou o nome das linhas relacionadas ao recurso de **modelo de carga de trabalho** real. Você precisará desses itens de trabalho ao adicionar a próxima carga de trabalho ao plano de adoção de nuvem.
5. Pule para a etapa 8 nas instruções de edição em massa para publicar a planilha. Esta etapa cria todos os itens de trabalho necessários para migrar sua carga de trabalho.

Repita as etapas de 1 a 5 para cada uma das cargas de trabalho na potência de 10.

## <a name="define-workloads"></a>Definir cargas de trabalho

Depois que as prioridades iniciais tiverem sido definidas e as cargas de trabalho tiverem sido adicionadas ao plano, cada uma das cargas de trabalho poderá ser definida por meio de uma análise qualitativa mais profunda. Antes de incluir qualquer carga de trabalho no plano de adoção de nuvem, tente fornecer os seguintes pontos de dados para cada carga de trabalho.

### <a name="business-inputs"></a>Entradas comerciais

| Ponto de dados | Descrição | Entrada |
|---|---|---|
| Nome da carga de trabalho | O que essa carga de trabalho é chamada? |         |
| Descrição da carga de trabalho | Em uma frase, o que essa carga de trabalho faz? |         |
| Motivações de adoção | Quais das motivações de adoção de nuvem são afetadas por essa carga de trabalho? |         |
| Patrocinador principal | Desses participantes afetados, quem é o patrocinador principal solicitando as motivações anteriores? |         |
| Unidade de negócios | Qual unidade de negócios é responsável pelo custo dessa carga de trabalho? |         |
| Processos de negócios | Quais processos de negócios serão afetados pelas alterações na carga de trabalho? |         |
| Equipes de negócios | Quais equipes de negócios serão afetadas pelas alterações? |         |
| Participantes comerciais | Há executivos cujos negócios serão afetados pelas alterações? |         |
| Resultados dos negócios | Como a empresa vai medir o sucesso desse esforço? |         |
| metrics | Quais métricas serão usadas para acompanhar o sucesso? |         |
| Conformidade | Há algum requisito de conformidade de terceiros para essa carga de trabalho? |         |
| Proprietários do aplicativo | Quem é responsável pelo impacto nos negócios de todos os aplicativos associados a essa carga de trabalho? |         |
| Períodos de congelamento de negócios | Há algum tempo durante o qual a empresa não permitirá alterações? |         |
| Localidades | As geografias são afetadas por essa carga de trabalho? |         |

### <a name="technical-inputs"></a>Entradas técnicas

| Ponto de dados | Descrição | Entrada |
|---|---|---|
| Abordagem de adoção | Essa adoção é um candidato para migração ou inovação? |         |
| Líder de ops do aplicativo | Liste as partes responsáveis pelo desempenho e pela disponibilidade dessa carga de trabalho. |         |
| SLAs | Listar qualquer contrato de nível de serviço (requisitos de RTO/RPO). |         |
| Importância | Liste a criticalidade do aplicativo atual. |         |
| Classificação de dados | Liste a classificação de sensibilidade de dados. |         |
| Geografias operacionais | Listar qualquer região geográfica na qual a carga de trabalho seja ou deve ser hospedada. |         |
| Aplicativos | Especifique uma lista inicial ou contagem de todos os aplicativos incluídos nessa carga de trabalho. |         |
| VMs | Especifique uma lista inicial ou a contagem de quaisquer VMs ou servidores incluídos na carga de trabalho. |         |
| Fontes de dados | Especifique uma lista inicial ou a contagem de quaisquer fontes de dados incluídas na carga de trabalho. |         |
| Dependências | Listar quaisquer dependências de ativos não incluídas na carga de trabalho. |         |
| Geografia do tráfego do usuário | Listar geografias que têm uma coleção significativa de tráfego de usuário. |         |

## <a name="confirm-priorities"></a>Confirmar prioridades

Com base nos dados montados, a equipe de estratégia de nuvem e a equipe de adoção de nuvem devem se reunir para reavaliar as prioridades. O esclarecimento dos pontos de dados comerciais pode solicitar alterações nas prioridades. Complexidade ou dependências técnicas podem resultar em alterações relacionadas a alocações de equipe, linhas do tempo ou sequenciamento de esforços técnicos.

Após uma análise, ambas as equipes devem estar confortáveis com a confirmação das prioridades resultantes. Esse conjunto de prioridades documentadas, validadas e confirmadas é a pendência de adoção de nuvem priorizada.

## <a name="next-steps"></a>Próximas etapas

Para qualquer carga de trabalho na pendência de adoção de nuvem priorizada, a equipe agora está pronta para alinhar os [ativos](./assets.md).

> [!div class="nextstepaction"]
> [Alinhar ativos para cargas de trabalho priorizadas](./assets.md)
