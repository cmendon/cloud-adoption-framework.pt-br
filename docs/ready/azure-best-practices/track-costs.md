---
title: Controlar os custos entre unidades de negócios, ambientes ou projetos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Acompanhar os custos entre unidades de negócios, ambientes ou projetos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 625706fe404f2b1bde16d54170ef3be36ea35c00
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548967"
---
# <a name="track-costs-across-business-units-environments-or-projects"></a>Controlar os custos entre unidades de negócios, ambientes ou projetos

A [criação de uma organização com consciência de custo](../../organize/cost-conscious-organization.md) exige visibilidade e acesso definido corretamente (ou escopo) a dados relacionados a custos. Este artigo de práticas recomendadas descreve as decisões e abordagens de implementação para criar mecanismos de controle.

![Estrutura de tópicos do processo sensível ao custo](../../_images/ready/cost-optimization-process.png)

## <a name="establish-a-well-managed-environment-hierarchy"></a>Estabelecer uma hierarquia de ambiente bem gerenciada

O controle de custo, muito semelhante à governança e outras construções de gerenciamento, depende de um ambiente bem gerenciado. Estabelecer um ambiente desse tipo (especialmente um complexo) requer processos consistentes na classificação e na organização de todos os ativos.

Ativos (também conhecidos como recursos) incluem todas as máquinas virtuais, fontes de dados e aplicativos implantados na nuvem. O Azure fornece vários mecanismos para classificar e organizar ativos. [Dimensionamento com várias](../considerations/scaling-subscriptions.md) opções de detalhes de assinaturas do Azure para organizar recursos com base em vários critérios para estabelecer um ambiente bem gerenciado. Este artigo se concentra na aplicação dos conceitos fundamentais do Azure para fornecer visibilidade de custo de nuvem.

### <a name="classification"></a>classificação

A *marcação* é uma maneira fácil de classificar ativos. A marcação associa metadados a um ativo. Esses metadados podem ser usados para classificar o ativo com base em vários pontos de dados. Quando as marcas são usadas para classificar ativos como parte de um esforço de gerenciamento de custos, as empresas geralmente precisam das seguintes marcas: unidade de negócios, departamento, código de cobrança, geografia, ambiente, projeto e carga de trabalho ou "categorização de aplicativo". O gerenciamento de custos do Azure pode usar essas marcas para criar diferentes exibições de dados de custo.

A marcação é uma maneira primária de entender os dados em qualquer relatório de custos. É uma parte fundamental de qualquer ambiente bem gerenciado. Também é a primeira etapa para estabelecer o controle adequado de qualquer ambiente.

A primeira etapa em controlar com precisão as informações de custo em unidades de negócios, ambientes e projetos é definir um padrão de marcação. A segunda etapa é garantir que o padrão de marcação seja aplicado consistentemente. Os artigos a seguir podem ajudá-lo a realizar cada uma destas etapas:

- [Desenvolver padrões de nomenclatura e marcação](../considerations/naming-and-tagging.md)
- [Estabelecer um MVP de governança para impor padrões de marcação](../../govern/guides/complex/index.md)

### <a name="resource-organization"></a>Organização de recursos

Há várias abordagens para organizar ativos. Esta seção descreve uma prática recomendada com base nas necessidades de uma grande empresa com estruturas de custo espalhadas por unidades de negócios, geografias e organizações de ti. Uma prática recomendada semelhante para uma organização menor e menos complexa está disponível no [Guia de governança empresarial padrão](../../govern/guides/standard/index.md).

Para uma grande empresa, o modelo a seguir para grupos de gerenciamento, assinaturas e grupos de recursos criará uma hierarquia que permite que cada equipe tenha o nível certo de visibilidade para executar suas tarefas. Quando a empresa precisa de controles de custo para evitar o estouro de orçamento, ela pode aplicar ferramentas de governança como plantas do Azure ou Azure Policy às assinaturas nessa estrutura para bloquear rapidamente erros de custo futuros.

![Diagrama de organização de recursos para uma grande empresa](../../_images/govern/large-enterprise-resource-organization.png)

No diagrama anterior, a raiz da hierarquia do grupo de gerenciamento contém um nó para cada unidade de negócios. Neste exemplo, a empresa multinacional precisa de visibilidade nas unidades de negócios regionais e, portanto, cria um nó para geografia em cada unidade de negócios na hierarquia.

Em cada geografia, há um nó separado para ambientes de produção e não produtos para isolar os controles de custo, acesso e governança. Para permitir operações mais eficientes e investimentos em operações mais inteligentes, a empresa usa assinaturas para isolar ainda mais os ambientes de produção com diferentes graus de compromissos de desempenho operacional. Por fim, a empresa usa grupos de recursos para capturar unidades implantáveis de uma função, chamadas de aplicativos.

O diagrama mostra as práticas recomendadas, mas não inclui estas opções:

- Muitas empresas limitam as operações a uma única região geopolítica. Essa abordagem reduz a necessidade de diversificarr as disciplinas de governança ou os dados de custo com base em requisitos de soberania de dados locais. Nesses casos, um nó de geografia é desnecessário.
- Algumas empresas preferem separar ainda mais os ambientes de desenvolvimento, teste e controle de qualidade em assinaturas separadas.
- Quando uma empresa integra uma equipe de CCoE (Cloud Center of Excellence), as assinaturas de serviços compartilhados em cada nó de Geografia podem reduzir os ativos duplicados.
- Esforços de adoção menores podem ter uma hierarquia de gerenciamento muito menor. É comum ver um único nó raiz para ti corporativa, com um único nível de nós subordinados na hierarquia para vários ambientes. Isso não é uma violação das práticas recomendadas para um ambiente bem gerenciado. Mas isso torna mais difícil fornecer um modelo de acesso de direitos mínimos para controle de custo e outras funções importantes.

O restante deste artigo pressupõe o uso da abordagem de práticas recomendadas no diagrama anterior. No entanto, os artigos a seguir podem ajudá-lo a aplicar a abordagem a uma organização de recursos que melhor se adapta à sua empresa:

- [Dimensionamento com várias assinaturas do Azure](../considerations/scaling-subscriptions.md)
- [Implantando um MVP de governança para controlar padrões de ambiente bem gerenciados](../../govern/guides/complex/index.md)

## <a name="provide-the-right-level-of-cost-access"></a>Fornecer o nível certo de acesso de custo

O gerenciamento de custos é uma atividade de equipe. A seção de preparação da organização da estrutura de adoção de nuvem define um pequeno número de equipes principais e descreve como essas equipes dão suporte a esforços de adoção de nuvem. Este artigo expande as definições de equipe para definir o escopo e as funções a serem atribuídas aos membros de cada equipe para obter o nível apropriado de visibilidade dos dados de gerenciamento de custos.

- As *funções* definem o que um usuário pode fazer em vários ativos.
- O *escopo* define quais ativos (usuário, grupo, entidade de serviço ou identidade gerenciada) um usuário pode fazer essas coisas.

Como uma prática recomendada geral, sugerimos um modelo de privilégios mínimos para atribuir pessoas a várias funções e escopos.

### <a name="roles"></a>Funções

O gerenciamento de custos do Azure dá suporte às seguintes funções internas para cada escopo:

- [Proprietário](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#owner). Pode exibir custos e gerenciar tudo, incluindo a configuração de custos.
- [Colaborador](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor). Pode exibir custos e gerenciar tudo, incluindo a configuração de custos, mas excluindo o controle de acesso.
- [Leitor](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#reader). Pode exibir tudo, incluindo dados de custo e configuração, mas não pode fazer nenhuma alteração.
- [Colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor). Pode exibir custos e gerenciar a configuração de custo.
- [Leitor de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) Pode exibir dados de custo e configuração.

Como uma prática recomendada geral, os membros de todas as equipes devem receber a função de colaborador de gerenciamento de custos. Essa função concede acesso para criar e gerenciar orçamentos e exportações para monitorar e relatar com mais eficiência os custos. No entanto, os membros da [equipe de estratégia de nuvem](../../organize/cloud-strategy.md) devem ser definidos apenas para o leitor de gerenciamento de custos. Isso ocorre porque eles não estão envolvidos na definição de orçamentos na ferramenta de gerenciamento de custos do Azure.

### <a name="scope"></a>Escopo

As configurações de escopo e função a seguir criarão a visibilidade necessária no gerenciamento de custos. Essa prática recomendada pode exigir pequenas alterações para se alinhar às decisões da organização de ativos.

- [Equipe de adoção de nuvem](../../organize/cloud-adoption.md). As responsabilidades para alterações de otimização contínuas exigem acesso de colaborador de gerenciamento de custos no nível do grupo de recursos.

  - **Ambiente de trabalho**. No mínimo, a equipe de adoção de nuvem já deve ter acesso de [colaborador](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#contributor) a todos os grupos de recursos afetados ou pelo menos os grupos relacionados a atividades de desenvolvimento/teste ou de implantação em andamento. Nenhuma configuração de escopo adicional é necessária.
  - **Ambientes de produção**. Quando a separação adequada de responsabilidade tiver sido estabelecida, a equipe de adoção de nuvem provavelmente não continuará a ter acesso aos grupos de recursos relacionados a seus projetos. Os grupos de recursos que dão suporte às instâncias de produção de suas cargas de trabalho precisarão de escopo adicional para dar essa equipe à visibilidade do impacto do custo de produção de suas decisões. Definir o escopo do [colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) para grupos de recursos de produção para esta equipe permitirá que a equipe monitore os custos e defina os orçamentos com base no uso e investimento contínuo nas cargas de trabalho com suporte.

- [Equipe de estratégia de nuvem](../../organize/cloud-strategy.md). As responsabilidades para controlar os custos em vários projetos e unidades de negócios exigem acesso de leitor de gerenciamento de custos no nível raiz da hierarquia do grupo de gerenciamento.

  - Atribuir acesso de [leitor de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-reader) a essa equipe no grupo de gerenciamento. Isso garantirá a visibilidade contínua de todas as implantações associadas às assinaturas governadas por essa hierarquia do grupo de gerenciamento.

- [Equipe de governança de nuvem](../../organize/cloud-governance.md). As responsabilidades para gerenciar o custo, o alinhamento do orçamento e os relatórios em todos os esforços de adoção exigem acesso de colaborador de gerenciamento de custos no nível raiz da hierarquia do grupo de gerenciamento.

  - Em um ambiente bem gerenciado, a equipe de governança de nuvem provavelmente já tem um grau mais alto de acesso, tornando desnecessária a atribuição de escopo adicional para o [colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) .

- [Cloud Center de excelência](../../organize/cloud-center-of-excellence.md). A responsabilidade pelo gerenciamento de custos relacionados a serviços compartilhados exige acesso de colaborador de gerenciamento de custos no nível de assinatura. Além disso, essa equipe pode exigir acesso de colaborador de gerenciamento de custos a grupos de recursos ou assinaturas que contêm ativos implantados por CCoE automations para entender como essas automaçãos afetam os custos.

  - **Serviços compartilhados**. Quando um Cloud Center de excelência é envolvido, a prática recomendada sugere que os ativos gerenciados pelo CCoE têm suporte de uma assinatura de serviço compartilhado centralizado dentro de um modelo de hub/spoke. Nesse cenário, o CCoE provavelmente tem acesso de colaborador ou proprietário a essa assinatura, tornando desnecessária a atribuição de escopo adicional para o [colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) .
  - **Automação/controles do CCOE**. O CCoE normalmente fornece controles e scripts de implantação automatizados para equipes de adoção de nuvem. O CCoE tem a responsabilidade de entender como esses aceleradores afetam os custos. Para obter essa visibilidade, a equipe precisa de acesso de [colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) a quaisquer grupos de recursos ou assinaturas que executam esses aceleradores.

- **Equipe de operações de nuvem**. A responsabilidade pelo gerenciamento de custos contínuos de ambientes de produção requer acesso de colaborador de gerenciamento de custos a todas as assinaturas de produção.

  - A recomendação geral coloca os ativos de produção e não produto em assinaturas separadas que são governadas por nós da hierarquia do grupo de gerenciamento associada a ambientes de produção. Em um ambiente bem gerenciado, os membros da equipe de operações provavelmente têm acesso de proprietário ou colaborador às assinaturas de produção, tornando a função de [colaborador de gerenciamento de custos](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#cost-management-contributor) desnecessária.

## <a name="additional-cost-management-resources"></a>Recursos adicionais de gerenciamento de custos

O gerenciamento de custos do Azure é uma ferramenta bem documentada para definir orçamentos e obter visibilidade dos custos de nuvem para Azure ou AWS. Depois de estabelecer o acesso a uma hierarquia de ambiente bem gerenciada, os artigos a seguir podem ajudá-lo a usar essa ferramenta para monitorar e controlar os custos.

### <a name="get-started-with-azure-cost-management"></a>Introdução ao gerenciamento de custos do Azure

Para obter mais informações sobre como começar a usar o gerenciamento de custos do Azure, consulte [como otimizar seu investimento em nuvem com o gerenciamento de custos do Azure](https://docs.microsoft.com/azure/cost-management/cost-mgt-best-practices?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json).

### <a name="use-azure-cost-management"></a>Usar o gerenciamento de custos do Azure

- [Criar e gerenciar orçamentos](https://docs.microsoft.com/azure/cost-management/tutorial-acm-create-budgets)
- [Exportar dados de custo](https://docs.microsoft.com/azure/cost-management/tutorial-export-acm-data)
- [Otimize os custos com base nas recomendações](https://docs.microsoft.com/azure/cost-management/tutorial-acm-opt-recommendations)
- [Use alertas de custo para monitorar o uso e os gastos](https://docs.microsoft.com/azure/cost-management/cost-mgt-alerts-monitor-usage-spending)

### <a name="use-azure-cost-management-to-govern-aws-costs"></a>Use o gerenciamento de custos do Azure para controlar os custos de AWS

- [Integração do relatório de uso e custo do AWS](https://docs.microsoft.com/azure/cost-management/aws-integration-set-up-configure)
- [Gerenciar custos de AWS](https://docs.microsoft.com/azure/cost-management/aws-integration-manage)

### <a name="establish-access-roles-and-scope"></a>Estabelecer acesso, funções e escopo

- [Entendendo o escopo do gerenciamento de custos](https://docs.microsoft.com/azure/cost-management/understand-work-scopes)
- [Definindo o escopo de um grupo de recursos](https://docs.microsoft.com/azure/role-based-access-control/quickstart-assign-role-user-portal)
