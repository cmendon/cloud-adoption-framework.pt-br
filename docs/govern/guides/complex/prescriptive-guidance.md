---
title: 'Guia de governança para empresas complexas: Diretrizes prescritivas explicadas'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre diretrizes prescritivas para governança em empresas complexas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 651144a519103c1a35f6a189af88e2f3690ecbfc
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028484"
---
# <a name="governance-guide-for-complex-enterprises-prescriptive-guidance-explained"></a>Guia de governança para empresas complexas: Diretrizes prescritivas explicadas

O guia de governança começa com um conjunto de [políticas corporativas](./initial-corporate-policy.md)iniciais. Essas políticas são usadas para estabelecer um produto viável mínimo (MVP) para governança que reflita as [práticas recomendadas](./index.md).

Neste artigo, discutiremos as estratégias de alto nível que são necessárias para a criação de um MVP de governança. O ponto central do MVP de governança é a disciplina [Aceleração da Implantação](../../deployment-acceleration/index.md). As ferramentas e os padrões aplicados neste estágio habilitarão as melhorias incrementais necessárias para expandir a governança no futuro.

## <a name="governance-mvp-initial-governance-foundation"></a>MVP de governança (Initial Governance Foundation)

A adoção rápida da governança e a política corporativa é uma realidade graças a alguns princípios simples e ferramentas de governança baseadas em nuvem. Essas são as primeiras das três Disciplinas de governança a serem abordadas em qualquer processo de governança. Cada disciplina será explicada mais adiante neste artigo.

Para estabelecer o ponto de partida, este artigo discutirá as estratégias de alto nível por trás da Linha de Base de Identidade, Linha de Base de Segurança e Aceleração de Implantação que são necessárias para criar um MVP de governança e que servirão como a base para a adoção como um todo.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-mvp.png)

## <a name="implementation-process"></a>Processo de implementação

A implementação do MVP de governança possui dependências de Identidade, Segurança e Rede. Depois que as dependências forem resolvidas, a equipe de governança de nuvem decidirá alguns aspectos de governança. As decisões da equipe de governança de nuvem e das equipes de suporte serão implementadas por meio de um único pacote de ativos de imposição.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-mvp-implementation-flow.png)

Essa implementação também pode ser descrita usando uma lista de verificação simples:

1. Solicite decisões relacionadas às dependências básicas: Identidade, Rede e Criptografia.
1. Determine o padrão a ser usado durante a imposição da política corporativa.
1. Determine os padrões de governança apropriados para a consistência de recursos, a marcação de recursos e as disciplinas de registro em log e relatório.
1. Implemente as ferramentas de governança alinhadas ao padrão de imposição de política escolhido para aplicar as decisões dependentes e as decisões de governança.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Aplicação de padrões definidos por governança

A equipe de governança de nuvem será responsável pelas seguintes decisões e implementações. Muitos precisarão de entradas de outras equipes, mas a equipe de governança de nuvem provavelmente terá a decisão e a implementação. As seções a seguir descrevem as decisões tomadas para esse caso de uso e os detalhes de cada decisão.

### <a name="subscription-design"></a>Design de assinatura

A decisão sobre qual design de assinatura usar determina como as assinaturas do Azure são estruturadas e como os grupos de gerenciamento do Azure serão usados para gerenciar com eficiência o acesso, as políticas e a conformidade dessas assinaturas. Nesta narração, a equipe de governança escolheu o padrão de design de assinatura **[mista](../../../decision-guides/subscriptions/index.md#mixed-patterns)** .

- Conforme surgem novas solicitações para recursos do Azure, um "Departamento" deve ser estabelecido para cada unidade de negócios importantes em cada geografia operacional. Dentro de cada um dos Departamentos, "Assinaturas" devem ser criadas para cada arquétipo do aplicativo.
- Um arquétipo de aplicativo é uma maneira de agrupar aplicativos com necessidades semelhantes. Exemplos comuns incluem: Aplicativos com dados protegidos, aplicativos governados (como HIPAA ou FedRAMP), aplicativos de baixo risco, aplicativos com dependências locais, SAP ou outros aplicativos de mainframe no Azure ou aplicativos que estendem SAP ou mainframes locais aplicativos. Cada organização tem necessidades únicas baseadas nas classificações de dados e nos tipos de aplicativos que são compatíveis com os negócios. O mapeamento de dependência do estado digital pode ajudar a definir arquétipos de aplicativo em uma organização.
- Uma convenção de nomenclatura comum deve ser aceita como parte do design da assinatura com base nos dois marcadores anteriores.

### <a name="resource-consistency"></a>Consistência de recursos

Decisões de consistência de recursos determinam as ferramentas, os processos e os esforços necessários para garantir que os recursos do Azure sejam implantados, configurados e gerenciados de forma consistente em uma assinatura. Nesta narração, a **[consistência hierárquica](../../../decision-guides/resource-consistency/index.md#hierarchical-consistency)** foi escolhida como o padrão de consistência do recurso primário.

- Grupos de recursos devem ser criados para cada aplicativo. Grupos de gerenciamento são criados para cada arquétipo de aplicativo. O Azure Policy deve ser aplicado a todas as assinaturas no grupo de gerenciamento associado.
- Como parte do processo de implantação, os modelos de Consistência de recursos para todos os ativos devem ser armazenados o controle de origem.
- Cada grupo de recursos deve associar a um aplicativo ou carga de trabalho específica.
- A hierarquia do grupo de gerenciamento do Azure definida deve representar a responsabilidade de cobrança e a propriedade de aplicativo usando grupos aninhados.
- Uma ampla implementação do Azure Policy pode exceder os compromissos de tempo da equipe e pode não fornecer muito valor neste momento. No entanto, uma política padrão simples deve ser criada e aplicada a cada grupo de para impor as primeiras poucas declarações de política de governança de nuvem. Isso serve para definir a implementação de requisitos de governança específicos. Essas implementações poderão então ser aplicadas em todos os ativos implantados.

### <a name="resource-tagging"></a>Marcação de recursos

As decisões de marcação de recursos determinam como os metadados são aplicados aos recursos do Azure em uma assinatura para dar suporte a operações, gerenciamento e fins contábeis. Nesta narração, o padrão de **[contabilidade](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns)** foi escolhido como o modelo padrão para a marcação de recursos.

- Os ativos implantados devem ser marcados com valores para:
  - Unidade de departamento/cobrança
  - Geografia
  - Classificação de dados
  - Importância
  - SLA
  - Ambiente
  - Arquétipo do aplicativo
  - Aplicativo
  - Proprietário do Aplicativo
- Esses valores junto com o grupo de gerenciamento do Azure e a assinatura associada a um ativo implantado impulsionarão as decisões de governança, operações e segurança.

### <a name="logging-and-reporting"></a>Registro em log e relatórios

As decisões de registro e relatório determinam como os dados de log da loja e como as ferramentas de monitoramento e relatório que mantêm a equipe de ti informada sobre a integridade operacional são estruturados. Nesta narra, um padrão de **[monitoramento híbrido](../../../decision-guides/logging-and-reporting/index.md)** para registro em log e relatório é sugerido, mas não é necessário para qualquer equipe de desenvolvimento neste momento.

- Nenhum requisito de governança está definido atualmente em relação aos dados a serem coletados para fins de registro em log ou relatório. Isso é específico para esse narrativa fictícia e deve ser considerado um antipadrão. Padrões de registro em log devem ser determinados e impostos assim que possível.
- Uma análise adicional será necessária antes da liberação de dados protegidos ou cargas de trabalho críticas.
- Antes de dar suporte a dados protegidos ou a cargas de trabalho de missão crítica, a solução de monitoramento operacional local existente deve ter acesso ao Workspace usado para registro em log. Aplicativos são necessários para atender a requisitos de segurança e registro em log com o uso do locatário, se o aplicativo for compatível com um SLA definido.

## <a name="incremental-of-governance-processes"></a>Incremental de processos de governança

Algumas das instruções de política não podem ou não devem ser controladas por ferramentas automatizadas. Outras políticas exigirão esforço periódico de segurança de TI e as equipes de linha de base de identidade local. A equipe de governança de nuvem precisará supervisionar os seguintes processos para implementar as oito últimas instruções de política:

**Alterações de política corporativa:** A equipe de governança de nuvem fará alterações no design de MVP de governança para adotar as novas políticas. O valor de governança de MVP é que ele permite a aplicação automática de novas políticas.

**Aceleração de adoção:** A equipe de governança de nuvem tem revisado scripts de implantação em várias equipes. Ela mantém um conjunto de scripts que atuam como modelos de implantação. Esses modelos são usados pelas equipes de adoção de nuvem e equipes DevOps para definir implantações mais rapidamente. Cada script contém requisitos para impor políticas de controle e não é necessário esforço adicional dos engenheiros de adoção da nuvem. Como curadores desses scripts, eles implementam mais rapidamente as alterações de política. Além disso, são exibidos como aceleradores de adoção. Isso garante consistência entre implantações, sem forçar estritamente a aderência.

**Treinamento de engenharia:** A equipe de governança de nuvem oferece sessões de treinamento Bimonthly e criou dois vídeos para engenheiros. Ambos os recursos ajudam os engenheiros a acelerar rapidamente sobre a cultura de governança e as implantações executadas. A equipe está adicionando ativos de treinamento para demonstrar a diferença entre implantações de produção e não produtos de desenvolvimento, o que ajuda os engenheiros a entender como as novas políticas afetam a adoção. Isso garante consistência entre implantações, sem forçar estritamente a aderência.

**Planejamento de implantação**: Antes de implantar qualquer ativo que contenha dados protegidos, a equipe de governança de nuvem será responsável por revisar os scripts de implantação para validar o alinhamento de governança. Equipes existentes com implantações aprovadas anteriormente serão auditadas usando ferramentas programáticas.

**Auditoria e relatórios mensais:** Todos os meses, a equipe de governança de nuvem executa uma auditoria de todas as implantações na nuvem para validar o alinhamento contínuo à política. Quando são encontrados desvios, eles são documentados e compartilhados com as equipes de adoção da nuvem. Quando a imposição não representa um risco de interrupção dos negócios ou de perda de dados, as políticas serão automaticamente aplicadas. No final da auditoria, a equipe de governança de nuvem compila um relatório para a equipe de estratégia de nuvem e cada equipe de adoção de nuvem para comunicar a adesão geral à política. O relatório também é armazenado para fins de auditoria e legais.

**Análise trimestral da política:** Cada trimestre, a equipe de governança de nuvem e a equipe de estratégia de nuvem para examinar os resultados de auditoria e sugerir alterações na política corporativa. Muitas dessas sugestões são o resultado de melhorias contínuas e da observação dos padrões de uso. As alterações de política aprovadas são integradas às ferramentas de governança durante ciclos posteriores de auditoria.

## <a name="alternative-patterns"></a>Padrões alternativos

Se qualquer um dos padrões escolhidos neste guia de governança não se alinhar com os requisitos do leitor, as alternativas para cada padrão estarão disponíveis:

- [Padrões de criptografia](../../../decision-guides/encryption/index.md)
- [Padrões de identidade](../../../decision-guides/identity/index.md)
- [Padrões de registro em log e relatórios](../../../decision-guides/logging-and-reporting/index.md)
- [Padrões de imposição de política](../../../decision-guides/policy-enforcement/index.md)
- [Padrões de consistência de recursos](../../../decision-guides/resource-consistency/index.md)
- [Padrões de marcação de recursos](../../../decision-guides/resource-tagging/index.md)
- [Padrões de rede definidos pelo software](../../../decision-guides/software-defined-network/index.md)
- [Padrões de design de assinatura](../../../decision-guides/subscriptions/index.md)

## <a name="next-steps"></a>Próximas etapas

Depois que este guia for implementado, cada equipe de adoção da nuvem poderá continuar com uma base sólida sobre governança. A equipe de governança de nuvem trabalhará em paralelo para atualizar continuamente as políticas corporativas e as disciplinas de governança.

As duas equipes usarão os indicadores de tolerância para identificar o próximo conjunto de aprimoramentos necessários para continuar a dar suporte à adoção na nuvem. A próxima etapa para essa empresa é a melhoria incremental de sua linha de base de governança para dar suporte a aplicativos com requisitos de autenticação multifator herdados ou de terceiros.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de linha de base de identidade](./identity-baseline-improvement.md)
