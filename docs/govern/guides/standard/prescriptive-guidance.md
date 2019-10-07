---
title: 'Guia de governança empresarial padrão: Diretrizes prescritivas explicadas'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre diretrizes prescritivas para governança em empresas padrão.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3f9149c3edc90a12b0e9dd1f99e20172cf277fb2
ms.sourcegitcommit: 945198179ec215fb264e6270369d561cb146d548
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71967505"
---
# <a name="standard-enterprise-governance-guide-prescriptive-guidance-explained"></a>Guia de governança empresarial padrão: Diretrizes prescritivas explicadas

O guia de governança começa com um conjunto de [políticas corporativas](./initial-corporate-policy.md)iniciais. Essas políticas são usadas para estabelecer um MVP de governança que reflita as [práticas recomendadas](./index.md).

Neste artigo, discutiremos as estratégias de alto nível que são necessárias para a criação de um MVP de governança. O ponto central do MVP de governança é a disciplina [Aceleração da Implantação](../../deployment-acceleration/index.md). As ferramentas e os padrões aplicados neste estágio habilitarão as melhorias incrementais necessárias para expandir a governança no futuro.

## <a name="governance-mvp-initial-governance-foundation"></a>MVP de governança (Initial Governance Foundation)

A adoção rápida da governança e a política corporativa é uma realidade graças a alguns princípios simples e ferramentas de governança baseadas em nuvem. Essas são as três primeiras disciplinas para abordagem em qualquer processo de governança. Cada disciplina será descrita neste artigo.

Para estabelecer o ponto de partida, este artigo discutirá as estratégias de alto nível por trás da Linha de Base de Identidade, Linha de Base de Segurança e Aceleração de Implantação que são necessárias para criar um MVP de governança e que servirão como a base para a adoção como um todo.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-mvp.png)

## <a name="implementation-process"></a>Processo de implementação

A implementação do MVP de governança possui dependências de Identidade, Segurança e Rede. Depois que as dependências forem resolvidas, a equipe de governança de nuvem decidirá alguns aspectos de governança. As decisões da equipe de governança de nuvem e das equipes de suporte serão implementadas por meio de um único pacote de ativos de imposição.

![Exemplo de MVP de governança incremental](../../../_images/govern/governance-mvp-implementation-flow.png)

Essa implementação também pode ser descrita usando uma lista de verificação simples:

1. Solicite decisões relacionadas às dependências básicas: Identidade, rede, monitoramento e criptografia.
2. Determine o padrão a ser usado durante a imposição da política corporativa.
3. Determine os padrões de governança apropriados para a consistência de recursos, a marcação de recursos e as disciplinas de registro em log e relatório.
4. Implemente as ferramentas de governança alinhadas ao padrão de imposição de política escolhido para aplicar as decisões dependentes e as decisões de governança.

[!INCLUDE [implementation-process](../../../../includes/implementation-process.md)]

## <a name="application-of-governance-defined-patterns"></a>Aplicação de padrões definidos por governança

A equipe de governança de nuvem é responsável pelas seguintes decisões e implementações. Muitas exigem entradas de outras equipes, mas a equipe de governança de nuvem provavelmente tem a decisão e a implementação. As seções a seguir descrevem as decisões tomadas para esse caso de uso e os detalhes de cada decisão.

### <a name="subscription-design"></a>Design de assinatura

A decisão sobre qual design de assinatura usar determina como as assinaturas do Azure são estruturadas e como os grupos de gerenciamento do Azure serão usados para gerenciar com eficiência o acesso, as políticas e a conformidade dessas assinaturas. Nesta narração, a equipe de governança escolheu o padrão de design de assinatura de [produção e não de produções](../../../decision-guides/subscriptions/index.md#production-and-nonproduction-pattern) .

- Os departamentos provavelmente não serão necessários, dado o foco atual. As implantações devem ser limitadas a uma única unidade de cobrança. No estágio de adoção, pode até não haver um Contrato Enterprise para centralizar a cobrança. É provável que esse nível de adoção seja gerenciado por uma única assinatura pré-paga do Azure.
- Independentemente do uso do portal de EA ou da existência de um Enterprise Agreement, um modelo de assinatura ainda deve ser definido e acordado para minimizar o cuidado administrativo além de apenas a cobrança.
- Uma convenção de nomenclatura comum deve ser aceita como parte do design da assinatura com base nos dois pontos anteriores.

### <a name="resource-consistency"></a>Consistência de recursos

Decisões de consistência de recursos determinam as ferramentas, os processos e os esforços necessários para garantir que os recursos do Azure sejam implantados, configurados e gerenciados de forma consistente em uma assinatura. Nesta narração, a **[consistência da implantação](../../../decision-guides/resource-consistency/index.md#deployment-consistency)** foi escolhida como o padrão de consistência do recurso primário.

- Os grupos de recursos são criados para aplicativos que usam a abordagem do ciclo de vida: tudo que é criado, mantido e desativado juntos deve residir em um único grupo de recursos. Para obter mais informações sobre grupos de recursos, consulte [aqui](../../../decision-guides/resource-consistency/index.md#basic-grouping).
- O Azure Policy deve ser aplicado a todas as assinaturas do grupo de gerenciamento associado.
- Como parte do processo de implantação, os modelos de Consistência de recursos do Azure do grupo de recursos devem ser armazenados no controle do código-fonte.
- Cada grupo de recursos é associado a uma carga de trabalho ou aplicativo específico com base na abordagem do ciclo de vida descrita acima.
- Os grupos de gerenciamento do Azure permitem a atualização de designs de governança conforme a política corporativa amadurece.
- Uma ampla implementação do Azure Policy pode exceder os compromissos de tempo da equipe e pode não ser de grande utilidade no momento. No entanto, uma política padrão simples deve ser criada e aplicada a cada grupo de gerenciamento para impor o pequeno número de instruções de políticas de governança de nuvem atual. Essa política definirá a implementação de requisitos de governança específicos. Essas implementações poderão então ser aplicadas em todos os ativos implantados.

>[!IMPORTANT]
>Sempre que um recurso em um grupo de recursos não compartilhar mais o mesmo ciclo de vida, ele deverá ser movido para outro grupo de recursos. Os exemplos incluem bancos de dados e componentes de rede comuns. Embora eles possam atender ao aplicativo que está sendo desenvolvido, eles também podem atender a outras finalidades e, portanto, devem existir em outros grupos de recursos.

### <a name="resource-tagging"></a>Marcação de recursos

As decisões de marcação de recursos determinam como os metadados são aplicados aos recursos do Azure em uma assinatura para dar suporte a operações, gerenciamento e fins contábeis. Nesta narração, o padrão de **[classificação](../../../decision-guides/resource-tagging/index.md#resource-tagging-patterns)** foi escolhido como o modelo padrão para a marcação de recursos.

- Os ativos implantados devem ser marcados com:
  - Classificação de dados
  - Importância
  - SLA
  - Ambiente
- Esses quatro valores guiarão as decisões relativas à governança, operações e segurança.
- Se este guia de governança estiver sendo implementado para uma unidade de negócios ou equipe em uma empresa maior, a marcação também deverá incluir metadados para a unidade de cobrança.

### <a name="logging-and-reporting"></a>Registro em log e relatórios

As decisões de registro e relatório determinam como os dados de log da loja e como as ferramentas de monitoramento e relatório que mantêm a equipe de ti informada sobre a integridade operacional são estruturados. Nesta narração, um [padrão nativo de nuvem](../../../decision-guides/logging-and-reporting/index.md#cloud-native)* * para registro em log e relatório é sugerido.

## <a name="incremental-improvement-of-governance-processes"></a>Melhoria incremental de processos de governança

Conforme as alterações de governança, algumas instruções de política não podem ou não devem ser controladas por ferramentas automatizadas. Outras políticas resultarão em esforços por parte da equipe de Segurança de TI e da equipe local de Gerenciamento de Identidades ao longo do tempo. Para ajudar a gerenciar novos riscos à medida que surgem, a equipe de governança de nuvem supervisionará os seguintes processos.

**Aceleração de adoção:** A equipe de governança de nuvem tem revisado scripts de implantação em várias equipes. Ela mantém um conjunto de scripts que atuam como modelos de implantação. Esses modelos são usados na adoção da nuvem e pelas equipes de DevOps para definir implantações com mais rapidez. Cada um desses scripts contém os requisitos necessários para impor um conjunto de políticas de governança sem nenhum esforço adicional dos engenheiros de adoção de nuvem. Como os curadores desses scripts, a equipe de governança de nuvem pode implementar mais rapidamente as alterações de política. Como resultado da visualização do script, a equipe de governança de nuvem é vista como uma fonte de aceleração de adoção. Isso cria consistência entre implantações, sem forçar estritamente a aderência.

**Treinamento de engenharia:** A equipe de governança de nuvem oferece sessões de treinamento Bimonthly e criou dois vídeos para engenheiros. Esses materiais ajudam os engenheiros a aprender rapidamente a cultura de governança e como as coisas são feitas durante as implantações. A equipe está adicionando ativos de treinamento que mostram a diferença entre implantações de produção e não produtos de desenvolvimento, para que os engenheiros compreendam como as novas políticas afetarão a adoção. Isso cria consistência entre implantações, sem forçar estritamente a aderência.

**Planejamento de implantação**: Antes de implantar qualquer ativo que contenha dados protegidos, a equipe de governança de nuvem examinará os scripts de implantação para validar o alinhamento de governança. Equipes existentes com implantações aprovadas anteriormente serão auditadas usando ferramentas programáticas.

**Auditoria e relatórios mensais:** Todos os meses, a equipe de governança de nuvem executa uma auditoria de todas as implantações na nuvem para validar o alinhamento contínuo à política. Quando são encontrados desvios, eles são documentados e compartilhados com as equipes de adoção da nuvem. Quando a imposição não representa um risco de interrupção dos negócios ou de perda de dados, as políticas serão automaticamente aplicadas. No final da auditoria, a equipe de governança de nuvem compila um relatório para a equipe de estratégia de nuvem e cada equipe de adoção de nuvem para comunicar a adesão geral à política. O relatório também é armazenado para fins de auditoria e legais.

**Análise trimestral da política:** Cada trimestre, a equipe de governança de nuvem e a equipe de estratégia de nuvem examinarão os resultados de auditoria e sugerirão alterações na política corporativa. Muitas dessas sugestões são o resultado de melhorias contínuas e da observação dos padrões de uso. As alterações de política aprovadas são integradas às ferramentas de governança durante ciclos posteriores de auditoria.

## <a name="alternative-patterns"></a>Padrões alternativos

Se qualquer um dos padrões selecionados neste guia de governança não se alinhar com os requisitos do leitor, as alternativas para cada padrão estarão disponíveis:

- [Padrões de criptografia](../../../decision-guides/encryption/index.md)
- [Padrões de identidade](../../../decision-guides/identity/index.md)
- [Padrões de registro em log e relatórios](../../../decision-guides/logging-and-reporting/index.md)
- [Padrões de imposição de política](../../../decision-guides/policy-enforcement/index.md)
- [Padrões de consistência de recursos](../../../decision-guides/resource-consistency/index.md)
- [Padrões de marcação de recursos](../../../decision-guides/resource-tagging/index.md)
- [Padrões de rede definidos pelo software](../../../decision-guides/software-defined-network/index.md)
- [Padrões de design de assinatura](../../../decision-guides/subscriptions/index.md)

## <a name="next-steps"></a>Próximas etapas

Depois que este guia for implementado, cada equipe de adoção da nuvem poderá continuar o trabalho com uma base sólida sobre governança. Ao mesmo tempo, a equipe de governança de nuvem trabalhará para atualizar continuamente as políticas corporativas e as disciplinas de governança.

As duas equipes usarão os indicadores de tolerância para identificar o próximo conjunto de aprimoramentos necessários para continuar a dar suporte à adoção na nuvem. Para a empresa fictícia neste guia, a próxima etapa é melhorar a linha de base de segurança para dar suporte à movimentação de dados protegidos para a nuvem.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de linha de base de segurança](./security-baseline-improvement.md)
