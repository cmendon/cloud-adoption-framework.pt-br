---
title: Controlar os custos em unidades de negócios, ambientes ou projetos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como acompanhar os custos em unidades de negócios, ambientes ou projetos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 4b181faf89d8196c3bbecd153e92e6f44d076166
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906161"
---
# <a name="track-costs-across-business-units-environments-or-projects"></a>Controlar os custos em unidades de negócios, ambientes ou projetos

[A criação de uma organização sensível ao custo](../../organization/cost-conscious-organization.md) exige visibilidade e acesso (ou escopo) definido corretamente a dados relacionados ao custo. Este artigo de melhores práticas descreve as decisões e abordagens de implementação para criar mecanismos de acompanhamento.

![Descrição do processo sensível ao custo](../../_images/ready/cost-optimization-process.png)

## <a name="establish-a-well-managed-environment-hierarchy"></a>Estabeleça uma hierarquia de ambiente bem gerenciada

O controle de custo, de forma bastante semelhante à governança e outras construções de gerenciamento, depende de um ambiente bem gerenciado. Estabelecer um ambiente desse tipo (especialmente um que seja complexo) requer processos consistentes na classificação e na organização de todos os ativos.

Os ativos (também conhecidos como recursos) incluem todas as máquinas virtuais, fontes de dados e aplicativos implantados na nuvem. O Azure fornece vários mecanismos para classificar e organizar ativos. [O dimensionamento com várias assinaturas do Azure](../considerations/scaling-subscriptions.md) detalha opções para organizar recursos com base em diversos critérios a fim de estabelecer um ambiente bem gerenciado. Este artigo se concentra na aplicação dos conceitos fundamentais do Azure para proporcionar visibilidade de custo na nuvem.

### <a name="classification"></a>Classificação

A *marcação* é uma maneira fácil de classificar ativos. A marcação associa metadados a um ativo. Esses metadados podem ser usados para classificar o ativo com base em diversos pontos de dados. Quando as marcações são usadas para classificar ativos como parte de um esforço de gerenciamento de custos, as empresas geralmente precisam das seguintes marcações: unidade de negócios, departamento, código de cobrança, geografia, ambiente, projeto e carga de trabalho ou "categorização de aplicativo". O Gerenciamento de Custos do Azure pode usar essas marcações para criar diferentes exibições de dados de custo.

A marcação é uma das principais maneiras de entender os dados de um relatório de custo. Trata-se de uma parte fundamental de todo ambiente bem gerenciado. Também é a primeira etapa para estabelecer uma governança adequada em qualquer ambiente.

A primeira etapa para acompanhar com precisão as informações de custo em unidades de negócios, ambientes e projetos é definir um padrão de marcação. A segunda etapa é garantir que o padrão de marcação seja aplicado de forma consistente. Os artigos a seguir podem ajudar a realizar cada uma dessas etapas:

- [Desenvolver padrões de nomenclatura e marcação](../considerations/name-and-tag.md)
- [Estabelecer um MVP de governança para impor os padrões de marcação](../../governance/journeys/complex-enterprise/index.md)

### <a name="resource-organization"></a>Organização do recurso

Há várias abordagens para a organização de ativos. Esta seção descreve uma melhor prática com base nas necessidades de uma empresa de grande porte que tem suas estruturas de custo espalhadas em unidades de negócios, geografias e organizações de TI. Uma melhor prática semelhante para organizações menores e menos complexas está disponível em [Percurso de governança para empresas de pequeno e médio porte](../../governance/journeys/standard-enterprise/index.md).

Para uma empresa de grande porte, o modelo a seguir de grupos de gerenciamento, assinaturas e grupos de recursos criará uma hierarquia que permite a cada equipe ter o nível certo de visibilidade para executar suas tarefas. Quando a empresa precisa de controles de custo para evitar o estouro do orçamento, ela pode aplicar ferramentas de governança como o Azure Blueprints ou o Azure Policy às assinaturas dentro dessa estrutura para bloquear rapidamente erros de custo futuros.

![Diagrama de organização de recursos para uma empresa de grande porte](../../_images/governance/large-enterprise-resource-organization.png)

No diagrama anterior, a raiz da hierarquia do grupo de gerenciamento contém um nó para cada unidade de negócios. Neste exemplo, a empresa multinacional precisa de visibilidade sobre as unidades de negócios regionais e, portanto, cria um nó de geografia em cada uma das unidades de negócios da hierarquia.

Em cada geografia há um nó separado para ambientes de produção e não produção a fim de isolar os controles de custo, acesso e governança. Para permitir operações mais eficientes e investimentos em operações mais sensatos, a empresa usa assinaturas a fim de isolar ainda mais os ambientes de produção com diferentes graus de compromissos de desempenho operacional. Por fim, a empresa usa grupos de recursos para capturar as unidades implantáveis de uma função, chamadas de aplicativos.

O diagrama mostra melhores práticas, mas não inclui as seguintes opções:

- Muitas empresas limitam as operações a uma única região geopolítica. Tal abordagem reduz a necessidade de diversificar as disciplinas de governança ou os dados de custo com base nos requisitos de soberania de dados locais. Nesses casos, o nó de geografia é desnecessário.
- Algumas empresas preferem segregar ainda mais os ambientes de desenvolvimento, teste e controle de qualidade em assinaturas separadas.
- Quando uma empresa integra uma equipe de CCoE (Centro de Excelência em Nuvem), as assinaturas de serviços compartilhados em cada nó da Geografia podem reduzir os ativos duplicados.
- Esforços de adoção menores podem ter uma hierarquia de gerenciamento muito menor. É comum ver um único nó raiz para a TI corporativa, com um único nível de nós subordinados na hierarquia para vários ambientes. Isso não é uma violação das melhores práticas para um ambiente bem gerenciado. Mas certamente torna mais difícil fornecer um modelo de acesso com direitos mínimos para controle de custo e outras funções importantes.

O restante deste artigo pressupõe o uso da abordagem de melhores práticas do diagrama anterior. No entanto, os artigos a seguir podem ajudá-lo a aplicar a abordagem a uma organização de recursos que melhor se adapte à sua empresa:

- [Dimensionamento com várias assinaturas do Azure](../considerations/scaling-subscriptions.md)
- [Como implantar um MVP de governança para controlar padrões de ambiente bem gerenciados](../../governance/journeys/complex-enterprise/index.md)

## <a name="provide-the-right-level-of-cost-access"></a>Fornecer o nível certo de acesso ao custo

O gerenciamento do custo é uma atividade de equipe. A seção de preparação da organização do Cloud Adoption Framework define um pequeno número de equipes principais e descreve como essas equipes dão suporte aos esforços de adoção da nuvem. Este artigo expande as definições de equipe para determinar o escopo e as funções a serem atribuídas aos membros de cada equipe a fim de alcançar o nível apropriado de visibilidade sobre os dados de gerenciamento de custos.

- As *funções* definem o que o usuário pode fazer com vários ativos.
- O *escopo* define com quais ativos (usuário, grupo, entidade de serviço ou identidade gerenciada) o usuário pode fazer essas coisas.

Como uma melhor prática geral, sugerimos um modelo de privilégios mínimos ao atribuir as pessoas aos diversos escopos e funções.

### <a name="roles"></a>Funções

O Gerenciamento de Custos do Azure é compatível com as seguintes funções internas para cada escopo:

- [Proprietário](/azure/role-based-access-control/built-in-roles#owner). Pode exibir os custos e gerenciar tudo, inclusive a configuração de custos.
- [Colaborador](/azure/role-based-access-control/built-in-roles#contributor). Pode exibir os custos e gerenciar tudo (inclusive a configuração de custos), com exceção do controle de acesso.
- [Leitor](/azure/role-based-access-control/built-in-roles#reader). Pode exibir tudo, inclusive os dados e a configuração de custos, mas não pode fazer nenhuma alteração.
- [Colaborador do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor). Pode exibir os custos e gerenciar a configuração de custos.
- [Leitor do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-reader) Pode exibir os dados e a configuração de custos.

Como uma melhor prática geral, os membros de todas as equipes devem ser designados com a função de Colaborador do Gerenciamento de Custos. Essa função concede acesso para criar e gerenciar orçamentos e exportações a fim de monitorar e gerar relatórios de custos com mais eficiência. No entanto, os membros da [equipe de estratégia de nuvem](../../organization/cloud-strategy.md) devem ser designados apenas com a função de Leitor de Gerenciamento de Custos. Isso porque eles não participam da definição de orçamentos na ferramenta de Gerenciamento de Custos do Azure.

### <a name="scope"></a>Escopo

As configurações de escopo e função a seguir criarão a visibilidade necessária sobre o gerenciamento de custos. Essa melhor prática pode exigir pequenas alterações para se alinhar às decisões da organização de ativos.

- [Equipe de adoção da nuvem](../../organization/cloud-adoption.md). As responsabilidades por alterações de otimização contínuas exigem acesso de Colaborador do Gerenciamento de Custos no nível do grupo de recursos.

  - **Ambiente de trabalho**. No mínimo, a equipe de adoção da nuvem já deve ter acesso de [Colaborador](/azure/role-based-access-control/built-in-roles#contributor) a todos os grupos de recursos afetados ou pelo menos aos grupos relacionados a atividades de desenvolvimento/teste ou de implantação contínua. Nenhuma configuração de escopo adicional é necessária.
  - **Ambientes de produção**. Quando a separação adequada de responsabilidade tiver sido estabelecida, a equipe do Cloud Adoption provavelmente não continuará a ter acesso aos grupos de recursos relacionados aos seus projetos. Os grupos de recursos que dão suporte às instâncias de produção de suas cargas de trabalho precisarão de escopo adicional para proporcionar à equipe visibilidade sobre o impacto de suas decisões a respeito dos custos de produção. A definição do escopo do [Colaborador do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor) como grupos de recursos de produção para esta equipe permitirá que a equipe monitore os custos e defina os orçamentos com base no uso e no investimento contínuo em cargas de trabalho compatíveis.

- [Equipe de Estratégia de Nuvem](../../organization/cloud-strategy.md). As responsabilidades por acompanhar os custos em vários projetos e unidades de negócios exigem acesso de Leitor do Gerenciamento de Custos no nível da raiz da hierarquia do grupo de gerenciamento.

  - Atribua acesso de [Leitor do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-reader) a essa equipe no grupo de gerenciamento. Isso proporcionará visibilidade contínua sobre todas as implantações associadas às assinaturas controladas por aquela hierarquia do grupo de gerenciamento.

- [Equipe de governança de nuvem](../../organization/cloud-governance.md). As responsabilidades por gerenciamento de custos, alinhamento de orçamentos e geração de relatórios em todos os esforços de adoção exigem acesso de Colaborador do Gerenciamento de Custos no nível da raiz da hierarquia do grupo de gerenciamento.

  - Em um ambiente bem gerenciado, a equipe de governança de nuvem provavelmente já tem um grau mais alto de acesso, tornando desnecessária a atribuição de escopo adicional para o [Colaborador do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor).

- [Centro de excelência em nuvem](../../organization/cloud-center-excellence.md). A responsabilidade pelo gerenciamento de custos relacionados a serviços compartilhados exige acesso de Colaborador do Gerenciamento de Custos no nível da assinatura. Além disso, essa equipe pode exigir acesso de Colaborador do Gerenciamento de Custos para grupos de recursos ou assinaturas que contêm ativos implantados por automações do CCoE para entender como essas automações afetam os custos.

  - **Serviços compartilhados**. Quando um Centro de Excelência em Nuvem está envolvido, a melhor prática sugere que os ativos gerenciados pelo CCoE têm suporte de uma assinatura de serviço compartilhado centralizado dentro de um modelo de hub/spoke. Nesse cenário, o CCoE provavelmente tem acesso de Colaborador ou Proprietário a essa assinatura, tornando desnecessária a atribuição de escopo adicional para o [Colaborador do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor).
  - **Automação/controles do CCoE**. O CCoE normalmente fornece controles e scripts de implantação automatizados para equipes de adoção da nuvem. O CCoE tem a responsabilidade de entender como esses aceleradores afetam os custos. Para obter essa visibilidade, a equipe precisa de acesso de [Colaborador de Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor) a quaisquer grupos de recursos ou assinaturas que executam esses aceleradores.

- **Equipe de operações de nuvem**. A responsabilidade pelo gerenciamento dos custos contínuos de ambientes de produção requer acesso de Colaborador do Gerenciamento de Custos a todas as assinaturas de produção.

  - A recomendação geral coloca os ativos de produção e não produto em assinaturas separadas que são governadas por nós da hierarquia do grupo de gerenciamento associada a ambientes de produção. Em um ambiente bem gerenciado, os membros da equipe de operações provavelmente já têm acesso de Proprietário ou Colaborador às assinaturas de produção, tornando desnecessária a função de [Colaborador do Gerenciamento de Custos](/azure/role-based-access-control/built-in-roles#cost-management-contributor).

## <a name="additional-cost-management-resources"></a>Recursos adicionais de gerenciamento de custos

O Gerenciamento de Custos do Azure é uma ferramenta bem documentada para definir orçamentos e obter visibilidade sobre os custos de nuvem para o Azure ou o AWS. Depois de estabelecer o acesso à hierarquia de um ambiente bem gerenciado, os artigos a seguir podem ajudá-lo a usar essa ferramenta para monitorar e controlar os custos.

### <a name="get-started-with-azure-cost-management"></a>Introdução ao Gerenciamento de Custos do Azure

Para obter mais informações sobre como começar a usar o Gerenciamento de Custos do Azure, confira [Como otimizar seu investimento em nuvem com o Gerenciamento de Custos do Azure](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/bread/toc.json).

### <a name="use-azure-cost-management"></a>Usar o Gerenciamento de Custos do Azure

- [Crie e gerencie orçamentos](/azure/cost-management/tutorial-acm-create-budgets)
- [Exportar dados de custo](/azure/cost-management/tutorial-export-acm-data)
- [Otimizar os custos com base em recomendações](/azure/cost-management/tutorial-acm-opt-recommendations)
- [Usar alertas de custo para monitorar o uso e os gastos](/azure/cost-management/cost-mgt-alerts-monitor-usage-spending)

### <a name="use-azure-cost-management-to-govern-aws-costs"></a>Usar o Gerenciamento de Custos do Azure para controlar os custos do AWS

- [Integração dos relatórios de Custos e Uso do AWS](/azure/cost-management/aws-integration-set-up-configure)
- [Gerenciar custos do AWS](/azure/cost-management/aws-integration-manage)

### <a name="establish-access-roles-and-scope"></a>Estabelecer acesso, funções e escopo

- [Compreensão do escopo do gerenciamento de custos](/azure/cost-management/understand-work-scopes)
- [Definição do escopo de um grupo de recursos](/azure/role-based-access-control/quickstart-assign-role-user-portal)
