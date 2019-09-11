---
title: Práticas recomendadas para empresas que estão migrando para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve um andaime que as empresas podem usar para garantir um ambiente seguro e gerenciável.
author: rdendtler
ms.author: rodend
ms.date: 09/22/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: abe40fe152d661aa5c9c25c77a332b850a7c1fbc
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905959"
---
# <a name="azure-enterprise-scaffold-prescriptive-subscription-governance"></a>Andaime do Azure Enterprise: Governança de assinatura prescritiva

> [!NOTE]
> O Azure Enterprise scaffolding foi integrado à estrutura de adoção Microsoft Cloud. O conteúdo deste artigo agora está representado na seção [pronta](../ready/index.md) da nova estrutura. Este artigo será preterido no início de 2020. Para começar a usar o novo processo, consulte a [visão geral pronta](../ready/index.md), [criando sua primeira zona](../ready/azure-readiness-guide/migration-landing-zone.md)de aterrissagem e/ou [Considerações sobre a zona](../ready/considerations/index.md)de aterrissagem.

As empresas estão adotando cada vez mais a nuvem pública em busca de agilidade e flexibilidade. Eles contam com os pontos fortes da nuvem para gerar receita e otimizar o uso de recursos para os negócios. O Microsoft Azure fornece diversos serviços e recursos que as empresas montam como blocos de construção para atender a uma ampla gama de aplicativos e cargas de trabalho.

Decidir usar o Microsoft Azure é apenas a primeira etapa para obter o benefício da nuvem. A segunda etapa é entender como a empresa pode usar o Azure efetivamente e identificar os recursos de linha de base que precisam estar em vigor para responder a perguntas como:

- “Estou preocupado com o domínio de dados; como posso garantir que meus dados e sistemas atendam aos nossos requisitos regulatórios?”
- "Como saber o que cada recurso aceita para que eu possa responsabilizá-lo e cobrá-lo de volta precisamente?"
- “Eu quero ter certeza de que tudo o que podemos implantar ou fazer na nuvem pública comece com a ideia da segurança em primeiro lugar; como ajudar a facilitar isso?"

O cliente potencial de uma assinatura vazia sem guardrails é assustador. Esse espaço em branco pode atrasar sua migração para o Azure.

Este artigo fornece um ponto de partida para que profissionais técnicos atendam à necessidade da governança e a equilibrem com a necessidade da agilidade. Aqui é apresentado o conceito de um andaime empresarial que orienta as organizações na implementação e no gerenciamento de seus ambientes do Azure de uma maneira segura. O artigo fornece a estrutura para desenvolver controles eficazes e eficientes.

## <a name="need-for-governance"></a>Necessidade de governança

Ao migrar para o Azure, você deve abordar o tópico de governança antecipadamente para garantir o uso bem-sucedido da nuvem dentro da empresa. Infelizmente, o tempo e a burocracia necessários para criar um sistema abrangente de governança significam que alguns grupos de negócios chegam diretamente aos fornecedores sem se envolverem com a TI empresarial. Essa abordagem pode comprometer a empresa se os recursos não forem gerenciados corretamente. As características da agilidade de nuvem&mdash;pública, a flexibilidade e os preços&mdash;baseados em consumo são importantes para os grupos de negócios que precisam atender rapidamente às demandas de clientes (internos e externos). Mas a ti empresarial precisa garantir que os dados e os sistemas sejam protegidos efetivamente.

Ao construir um prédio, o andaime é usado para criar a base de uma estrutura. O andaime guia o plano geral, além de fornecer pontos de ancoragem para que mais sistemas permanentes sejam montados. Um andaime empresarial é igual: um conjunto de controles flexíveis e recursos do Azure que fornecem estrutura ao ambiente, bem como âncoras para serviços criados com base na nuvem pública. Ele fornece aos criadores (TI e grupos de negócios) uma base para criar e agregar novos serviços, mantendo a agilidade na entrega em mente.

Um andaime se baseia em práticas que coletamos dos muitos compromissos com clientes de vários tamanhos. Esses clientes variam de pequenas organizações que desenvolvem soluções na nuvem para grandes empresas multinacionais e fornecedores de software independentes que estão migrando cargas de trabalho e desenvolvendo soluções nativas de nuvem. O Enterprise Scaffold é "criado especificamente" para ser flexível para dar suporte a cargas de trabalho de ti tradicionais e a cargas Agile, como os desenvolvedores que criam aplicativos SaaS (software como serviço) baseados em recursos da plataforma Azure.

O andaime empresarial destina-se a ser a base de cada nova assinatura no Azure. Ele permite aos administradores garantir que as cargas de trabalho atendam aos requisitos mínimos de governança de uma organização sem impedir que grupos de negócios e desenvolvedores cumpram rapidamente suas próprias metas. Nossa experiência mostra que isso acelera bastante o crescimento da nuvem pública, em vez de impedi-lo.

> [!NOTE]
> A Microsoft lançou a versão prévia de um novo recurso chamado [Azure Blueprints](/azure/governance/blueprints/overview), que permitirá a você empacotar, gerenciar e implantar imagens, modelos, políticas e scripts comuns em assinaturas e grupos de gerenciamento. Esse recurso é a ponte entre a finalidade do andaime como modelo de referência e a implantação desse modelo na organização.
>
A imagem a seguir mostra os componentes do andaime. A base depende de um plano sólido para a hierarquia de gerenciamento e para as assinaturas. Os pilares consistem em políticas do Resource Manager e sólidos padrões de nomenclatura. O restante do andaime é composto pelos principais recursos e funcionalidades do Azure, que possibilitam e conectam um ambiente seguro e gerenciável.

![andaime empresarial](./_images/scaffoldv2.png)

## <a name="define-your-hierarchy"></a>Definir sua hierarquia

A base do andaime é a hierarquia e o relacionamento do Registro empresarial do Azure para assinaturas e grupos de recursos. O Registro empresarial define a forma e o uso dos serviços do Azure em uma empresa de um ponto de vista contratual. Dentro do Enterprise Agreement, você pode subdividir ainda mais o ambiente em departamentos, contas, assinaturas e grupos de recursos para corresponder à estrutura da sua organização.

![hierarquia](./_images/agreement.png)

Uma assinatura do Azure é a unidade básica onde todos os recursos estão contidos. Ela também define vários limites dentro do Azure, como o número de núcleos, de redes virtuais e outros recursos. Os grupos de recursos são usados para refinar ainda mais o modelo de assinatura e habilitar um agrupamento mais natural de recursos.

Cada empresa é diferente e a hierarquia na imagem acima permite flexibilidade significativa em como o Azure é organizado dentro da sua empresa. Modelar sua hierarquia para refletir a cobrança, o gerenciamento de recursos e as necessidades de acesso aos recursos de sua empresa é a primeira e mais importante decisão que você faz ao iniciar na nuvem pública.

### <a name="departments-and-accounts"></a>Departamentos e contas

Os três padrões comuns para inscrições do Azure são:

- O padrão **funcional** :

  ![O padrão funcional](./_images/functional.png)

- O padrão de **unidade de negócios** :

  ![O padrão de unidade de negócios](./_images/business.png)

- O padrão **geográfico** :

  ![O padrão geográfico](./_images/geographic.png)

Embora cada um desses padrões tenha o seu lugar, o padrão de **unidade de negócios** está sendo cada vez mais adotado devido à sua flexibilidade na criação de um modelo de custo da organização e porque ele reflete o alcance de controle. O Microsoft Core Engineering and Operations Group criou um subconjunto efetivo do padrão de **unidade de negócios** modelado em **Federal**, **estadual**e **local**. Para obter mais informações, consulte [organizando assinaturas e grupos de recursos dentro da empresa](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).

### <a name="azure-management-groups"></a>Grupos de gerenciamento do Azure

A Microsoft agora fornece outra maneira de modelar sua hierarquia: [Grupos de gerenciamento do Azure](/azure/azure-resource-manager/management-groups-overview). Os grupos de gerenciamento são muito mais flexíveis do que os departamentos e as contas, e podem ser aninhados até seis níveis. Os grupos de gerenciamento permitem criar uma hierarquia separada da sua hierarquia de cobrança, exclusivamente para o gerenciamento eficiente de recursos. Os grupos de gerenciamento podem espelhar sua hierarquia de cobrança; e as empresas começam desse modo muitas vezes. No entanto, o poder dos grupos de gerenciamento é quando você os utiliza para modelar sua organização, agrupando as assinaturas relacionadas (independentemente de sua localização na hierarquia de cobrança) e atribuindo funções, políticas e iniciativas comuns. Eis alguns exemplos:

- **Produção versus não produto.** Algumas empresas criam grupos de gerenciamento para identificar suas assinaturas de produção e não produções. Os grupos de gerenciamento permitem que esses clientes gerenciem mais facilmente funções e políticas. Por exemplo, a assinatura de não produção pode permitir o acesso de "colaborador" de desenvolvedores, mas em produção, eles têm apenas acesso "leitor".
- **Serviços internos vs. serviços externos.** As empresas geralmente têm requisitos, políticas e funções diferentes para serviços internos versus serviços voltados para o cliente.

Os grupos de gerenciamento bem projetados são, juntamente com Azure Policy e iniciativas, o backbone da governança eficiente do Azure.

### <a name="subscriptions"></a>Inscrições

Ao decidir sobre seus departamentos e contas (ou grupos de gerenciamento), você está examinando principalmente como dividir seu ambiente do Azure para corresponder à sua organização. No entanto, as assinaturas são onde acontecem o trabalho real e suas decisões aqui afetam a segurança, a escalabilidade e a cobrança. Muitas organizações examinam os seguintes padrões como guias:

- **Aplicativo/serviço:** as assinaturas representam um aplicativo ou um serviço (portfólio de aplicativos)
- **Lifecycle** as assinaturas representam um ciclo de vida de um serviço, como desenvolvimento ou produção.
- **Departamento:** as assinaturas representam departamentos na organização.

Os dois primeiros padrões são mais comumente utilizados, e ambos são altamente recomendáveis. A abordagem de Ciclo de vida é apropriada para a maioria das organizações. Nesse caso, a recomendação geral é usar duas assinaturas `Production` base e `Nonproduction`, em seguida, usar grupos de recursos para separar ainda mais os ambientes.

### <a name="resource-groups"></a>Grupos de recursos

O Azure Resource Manager permite colocar recursos em grupos significativos para gerenciamento, cobrança ou afinidade natural. Os grupos de recursos são contêineres de recursos que têm um ciclo de vida comum ou compartilham um atributo, como "todos os servidores SQL" ou "Aplicativo A".

Os grupos de recursos não podem ser aninhados e os recursos podem pertencer apenas a um grupo de recursos. Algumas ações podem agir em todos os recursos em um grupo de recursos. Por exemplo, a exclusão de um grupo de recursos remove todos os recursos do grupo de recursos. Assim como as assinaturas, existem padrões comuns durante a criação de grupos de recursos e eles vão variar de cargas de trabalho de “TI tradicional” a cargas de trabalho de “TI Agile”:

- As cargas de trabalho "TI Tradicional" são mais frequentemente agrupadas por itens no mesmo ciclo de vida, como um aplicativo. O agrupamento por aplicativo permite o gerenciamento individual de aplicativo.
- As cargas de trabalho "TI da Agile" tendem a se concentrar nos aplicativos de nuvem voltados para o cliente. Os grupos de recursos muitas vezes refletem as camadas da implantação (como camada da web, camada de aplicativo) e o gerenciamento.

> [!NOTE]
> Noções básicas sobre sua carga de trabalho ajudam a desenvolver uma estratégia de grupo de recursos. Esses padrões podem ser misturados e combinados. Por exemplo, um grupo de recursos de serviços compartilhados na mesma assinatura como grupos de recursos “Agile”.

## <a name="naming-standards"></a>Padrões de nomenclatura

O primeiro pilar do andaime é um padrão consistente de nomenclatura. Os padrões de nomenclatura bem definidos permitem identificar recursos no portal, em uma cobrança e dentro de scripts. Você provavelmente já tem padrões de nomenclatura para a infraestrutura local. Ao adicionar o Azure ao seu ambiente, você deve estender esses padrões de nomenclatura para os recursos do Azure.

> [!TIP]
> Para convenções de nomenclatura:
>
> - Analise e adote onde possível as [Orientações de padrões e práticas](/azure/architecture/best-practices/naming-conventions). Essas diretrizes ajudam a decidir sobre um padrão de nomenclatura significativo e fornece exemplos abrangentes.
> - Usar políticas do Resource Manager para ajudar a reforçar os padrões de nomenclatura.
>
> Lembre-se de que é difícil alterar nomes mais tarde, portanto, alguns minutos agora evitarão problemas mais tarde.

Concentre-se nos padrões de nomenclatura desses recursos que são mais comumente usados e pesquisados. Por exemplo, todos os grupos de recursos devem seguir um padrão bem definido para maior clareza.

### <a name="resource-tags"></a>Marcações de recursos

As marcas de recurso estão alinhadas diretamente com padrões de nomenclatura. Conforme recursos são adicionados às assinaturas, torna-se cada vez mais importante categorizá-los logicamente para fins operacionais, de gerenciamento e de cobrança. Para obter mais informações, veja [Usar marcas para organizar os recursos do Azure](/azure/azure-resource-manager/resource-group-using-tags).

> [!IMPORTANT]
> As marcas podem conter informações pessoais e podem estar enquadradas nos regulamentos do RGPD. Planeje cuidadosamente o gerenciamento de suas marcas. Se você estiver procurando informações gerais sobre GDPR, consulte a seção GDPR do portal de [confiança do serviço](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

As marcas são usadas de várias maneiras, além de gerenciamento e cobrança. Geralmente, eles são usados como parte da automação (consulte a seção posterior). Isso pode causar conflitos se não for considerado de antemão. A prática recomendada é identificar todas as marcas comuns no nível corporativo (como ApplicationOwner e CostCenter) e aplicá-las de forma consistente ao implantar recursos usando a automação.

## <a name="azure-policy-and-initiatives"></a>Azure Policy e Iniciativas do Azure

O segundo pilar do Scaffold envolve o uso de [Azure Policy e iniciativas](/azure/azure-policy/azure-policy-introduction) para gerenciar riscos ao impor regras (com efeitos) sobre os recursos e serviços em suas assinaturas. Iniciativas do Azure são coleções de políticas que são projetadas para alcançar uma única meta. As políticas e iniciativas são então atribuídas a um escopo de recurso para iniciar a imposição dessas políticas.

As políticas e iniciativas são ainda mais poderosas quando usadas com os grupos de gerenciamento mencionados anteriormente. Os grupos de gerenciamento permitem a atribuição de uma iniciativa ou política para um conjunto inteiro de assinaturas.

### <a name="common-uses-of-resource-manager-policies"></a>Usos comuns das políticas do Resource Manager

Políticas e iniciativas são uma ferramenta poderosa no kit de ferramentas do Azure. As políticas permitem que as empresas forneçam controles para cargas de trabalho de "ti tradicional" que habilitam a estabilidade necessária para aplicativos de linha de negócios e também permitem cargas de&mdash;trabalho "Agile", por exemplo, desenvolvimento de aplicativos para clientes sem expor a empresa a um risco adicional. Os padrões mais comuns para políticas são:

- **Conformidade geográfica e soberania de dados.** O Azure tem uma lista crescente de regiões em todo o mundo. Muitas vezes, as empresas precisam garantir que os recursos em um escopo específico permaneçam em uma região geográfica para atender aos requisitos regulatórios.
- **Evite expor servidores publicamente.** Azure Policy pode proibir a implantação de determinados tipos de recursos. É comum criar uma política para negar a criação de um IP público dentro de um escopo específico, evitando a exposição involuntária de um servidor à Internet.
- **Gerenciamento de custos e metadados.** As marcas de recurso geralmente são usadas para adicionar dados de cobrança importantes a recursos e grupos de recursos, como CostCenter, proprietário e muito mais. Essas marcas são imprescindíveis para uma cobrança e gerenciamento precisos dos recursos. As políticas podem impor a aplicação de marcas de recursos a todos os recursos implantados, facilitando o gerenciamento destes.

### <a name="common-uses-of-initiatives"></a>Usos comuns de iniciativas

As iniciativas fornecem às empresas a capacidade de agrupar políticas lógicas e rastreá-las como uma única entidade. As iniciativas ajudam a empresa a atender às necessidades das cargas de trabalho Agile e tradicional. Os usos comuns das iniciativas incluem:

- **Habilite o monitoramento na central de segurança do Azure.** Essa é uma iniciativa padrão no Azure Policy e um excelente exemplo de quais iniciativas são. Ele permite políticas que identificam bancos de dados SQL não criptografados, vulnerabilidades de VM (máquina virtual) e necessidades mais comuns relacionadas à segurança.
- **Iniciativa específica de regulamentação.** As empresas geralmente agrupam políticas comuns em um requisito regulatório (como HIPAA) para que os controles e a conformidade a esses controles sejam acompanhados com eficiência.
- **Tipos de recursos e SKUs.** A criação de uma iniciativa que restringe os tipos de recursos que podem ser implantados, bem como as SKUs que podem ser implantadas, pode ajudar a controlar os custos e garantir que sua organização esteja apenas implantando recursos para os quais sua equipe tem o conjunto de habilidades e os procedimentos para dar suporte.

> [!TIP]
> É recomendável que você use sempre definições de iniciativa em vez de definições de política. Depois de atribuir uma iniciativa a um escopo, como assinatura ou grupo de gerenciamento, você pode adicionar facilmente outra política à iniciativa sem precisar alterar as atribuições. Isso facilita bastante entender o que é aplicado e o acompanhamento da conformidade.

### <a name="policy-and-initiative-assignments"></a>Atribuições de Iniciativa e Política

Após criar políticas e agrupá-las em iniciativas lógicas você deve atribuir a política a um escopo, se ela um grupo de gerenciamento, uma assinatura ou até mesmo um grupo de recursos. As atribuições permitem que você também exclua um subescopo da atribuição de uma política. Por exemplo, se você negar a criação de IPs públicos em uma assinatura, você pode criar uma atribuição com uma exclusão para um grupo de recursos conectado à sua rede de perímetro protegida.

Você encontrará vários exemplos de política que mostram como iniciativas e políticas podem ser aplicadas a vários recursos no Azure neste repositório [GitHub](https://github.com/Azure/azure-policy).

## <a name="identity-and-access-management"></a>Gerenciamento de identidade e de acesso

Uma das primeira e mais importantes perguntas que você se faz ao começar a usar a nuvem pública é “quem devem ter acesso aos recursos?” e "como controlar esse acesso?" Controlar o acesso ao portal do Azure e aos recursos no portal é essencial para a segurança de longo prazo de seus ativos na nuvem.

Para proteger o acesso aos seus recursos, primeiro você configurará seu provedor de identidade e, em seguida, configurará funções e acesso. O Azure Active Directory (Azure AD), conectado ao seu Active Directory local, é a base da identidade do Azure Identity. Dito isso, o Azure AD *não* é o mesmo local Active Directory, e é importante entender o que é um locatário do Azure AD e como ele se relaciona com o registro do Azure. Examine as [informações](../governance/resource-consistency/azure-resource-access.md) disponíveis para obter uma base sólida sobre o Azure AD e o Active Directory local. Para conectar e sincronizar seu Active Directory com o Azure AD, instale e configure a [ferramenta de Azure ad Connect](/azure/active-directory/connect/active-directory-aadconnect) local.

![arch.png](./_images/arch.png)

Quando o Azure foi inicialmente lançado, os controles de acesso para uma assinatura eram básicos: Administrador ou Coadministrador. O acesso a uma assinatura no modelo Clássico implicava acesso a todos os recursos no portal. Essa falta de um controle refinado levou à proliferação de assinaturas para fornecer um nível de controle de acesso razoável para uma Inscrição no Azure. Essa proliferação de assinaturas não é mais necessária. Com o RBAC (controle de acesso baseado em função), você pode atribuir usuários a funções padrão que fornecem acesso comum, como "proprietário", "colaborador" ou "leitor", ou até mesmo criar suas próprias funções.

Ao implementar acesso baseado em função, o código a seguir é altamente recomendável:

- Controle o Administrador/Coadministrador de uma assinatura já que essas funções têm permissões abrangentes. Você só precisa adicionar o Proprietário da Assinatura como um Coadministrador caso ele precise gerenciar implantações clássicas do Azure.
- Use grupos de gerenciamento para atribuir [funções](/azure/azure-resource-manager/management-groups-overview#management-group-access) entre várias assinaturas e reduzir a carga de gerenciá-las no nível da assinatura.
- Adicione usuários do Azure a um grupo (por exemplo, Proprietários do Aplicativo X) no Active Directory. Use o grupo sincronizado para fornecer aos membros do grupo os direitos apropriados para gerenciar o grupo de recursos que contém o aplicativo.
- Siga o princípio de conceder o **privilégio mínimo** exigido para realizar o trabalho esperado.

> [!IMPORTANT]
>Considere o uso dos recursos de [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure), [Autenticação Multifator](/azure/active-directory/authentication/howto-mfa-getstarted) do Azure e [Acesso Condicional](/azure/active-directory/active-directory-conditional-access-azure-portal) para fornecer uma melhor segurança e mais visibilidade para ações administrativas em suas assinaturas do Azure. Esses recursos são provenientes de uma licença válida do Azure AD Premium (dependendo do recurso) para proteger ainda mais e gerenciar sua identidade. O Azure AD PIM habilita a acesso administrativo “Just In Time” com o fluxo de trabalho de aprovação, bem como uma auditoria completa de atividades e ativações do administrador. A autenticação multifator do Azure é outro recurso crítico e permite a verificação em duas etapas para fazer logon no portal do Azure. Combinados com Controles de Acesso Condicional você pode gerenciar com eficiência o risco de ameaça à segurança.

Planejar e preparar a sua identidade e os controles de acesso e seguir a prática recomendada do Azure Identity Management ([link](/azure/security/azure-security-identity-management-best-practices)) é uma das melhores estratégias de mitigação de risco que você pode empregar e deve ser considerada obrigatória para cada implantação.

## <a name="security"></a>Segurança

Talvez um dos maiores impedimentos à adoção da nuvem de forma tradicional tenham sido as preocupações com a segurança. Os gerentes de risco em TI e os departamentos de segurança precisam garantir que os recursos no Azure estejam protegidos e seguros por padrão. O Azure fornece recursos que você pode usar para proteger recursos ao detectar e eliminar ameaças contra esses recursos.

### <a name="azure-security-center"></a>Central de Segurança do Azure

A [Central de Segurança do Azure](/azure/security-center/security-center-intro) oferece uma exibição unificada do status de segurança dos recursos em seu ambiente, além de proteção avançada contra ameaças. A Central de Segurança do Azure é uma plataforma aberta que permite aos parceiros da Microsoft criar software que se conecte à Central de Segurança do Azure e aprimorar seus recursos. Os recursos de linha de base da central de segurança do Azure (camada gratuita) fornecem avaliação e recomendações que aprimorarão sua postura de segurança. Suas camadas pagas permitem recursos adicionais e valiosos, como acesso de administrador just-in-time e controles de aplicativo adaptáveis (lista de permissões).

> [!TIP]
>A central de segurança do Azure é uma ferramenta poderosa que é aprimorada regularmente com novos recursos que você pode usar para detectar ameaças e proteger sua empresa. É altamente recomendável habilitar sempre a central de segurança do Azure.

### <a name="azure-resource-locks"></a>Bloqueios de recursos do Azure

À medida que sua organização adiciona serviços principais às assinaturas, ela se torna cada vez mais importante para evitar a interrupção dos negócios. Um tipo de interrupção que vemos com frequência é consequências não intencionais de scripts e ferramentas trabalhando contra uma assinatura do Azure, excluindo recursos por engano. Os [Bloqueios de recursos](/azure/azure-resource-manager/resource-group-lock-resources) permitem restringir operações nos recursos de alto valor, onde sua modificação ou exclusão teria um impacto significativo. Os bloqueios são aplicados a uma assinatura, grupo de recursos ou até mesmo recursos individuais. O caso de uso comum é aplicar bloqueios a recursos fundamentais, como redes virtuais, gateways, grupos de segurança de rede e contas de armazenamento de chaves.

### <a name="secure-devops-toolkit"></a>Kit de ferramentas de DevOps seguro

O Secure DevOps Kit for Azure (AzSK) é uma coleção de scripts, ferramentas, extensões e recursos de automação originalmente criados pela própria equipe de ti da Microsoft e [lançado como software livre por meio do GitHub](https://github.com/azsk/DevOpsKit-docs). O AzSK atende às necessidades de segurança de recursos e assinatura do Azure de ponta a ponta para equipes que usam automação abrangente e integram a segurança em fluxos de trabalho nativos do DevOps, ajudando a atingir DevOps seguras com estas seis áreas de enfoque:

- Proteger a assinatura
- Permitir o desenvolvimento seguro
- Integrar a segurança ao CI/CD
- Garantia contínua
- Alertas e monitoramento
- Governança de riscos na nuvem

![Kit de ferramentas de DevOps seguro](_images/Secure_DevOps_Kit_Azure.png)

O AzSK é um rico conjunto de ferramentas, scripts e informações que são uma parte importante de um plano de governança do Azure completo e incorporando isso em seu Scaffold é crucial para dar suporte às metas de gerenciamento de riscos de suas organizações.

### <a name="azure-update-management"></a>Gerenciamento de Atualizações do Azure

Uma das principais tarefas que podem ser feitas para proteger o ambiente é garantir que os servidores tenham as atualizações mais recentes. Embora haja várias ferramentas para fazer isso, o Azure fornece a solução de [Gerenciamento de Atualizações do Azure](/azure/automation/automation-update-management) para tratar da identificação e da distribuição de patches críticos do sistema operacional. Usa a Automação do Azure, abordada na seção [Automatizar](#automate) mais adiante neste guia.

## <a name="monitor-and-alerts"></a>Monitoramento e alertas

Coletar e analisar a telemetria que fornece a linha de visão sobre as atividades, as métricas de desempenho, a integridade e a disponibilidade dos serviços que você está usando em suas assinaturas do Azure é essencial para gerenciar proativamente seus aplicativos e infraestrutura e é uma necessidade fundamental de cada assinatura do Azure. Cada serviço do Azure emite a telemetria na forma de logs de atividades, métricas e logs de diagnóstico.

- Os **logs de atividades** descrevem todas as operações executadas nos recursos em suas assinaturas.
- **Métricas** são informações numéricas emitidas por um recurso que descrevem o desempenho e a integridade de um recurso.
- **Os logs de diagnóstico** são emitidos por um serviço do Azure e fornecem dados avançados e frequentes sobre a operação do serviço.

Essas informações podem ser exibidas e acionadas em vários níveis e estão continuamente sendo aprimoradas. O Azure fornece recursos de monitoramento **compartilhados**, **básicos**e profundos dos recursos do Azure por meio dos serviços descritos no diagrama a seguir.

![monitoramento](./_images/monitoring.png)

### <a name="shared-capabilities"></a>Funcionalidades compartilhadas

- **Alertas** Você pode coletar todos os logs, eventos e métricas dos recursos do Azure, mas sem a capacidade de ser notificado sobre condições críticas e agir, esses dados só são úteis para fins de histórico e análise forense. O Azure Alerts notifica proativamente sobre condições que você define para todos os seus aplicativos e infraestrutura. Você cria regras de alerta entre logs, eventos e métricas que usam grupos de ação para notificar conjuntos de destinatários. Os grupos de ação também fornecem a capacidade de automatizar a correção usando ações externas, como webhooks para executar runbooks de Automação do Azure e o Azure Functions.

- **Painéis** os painéis permitem que você agregue exibições de monitoramento e combine dados de recursos e assinaturas para dar a você uma visão de toda a empresa sobre a telemetria dos recursos do Azure. Você pode criar e configurar seus próprios modos de exibição e compartilhá-los com outras pessoas. Por exemplo, você pode criar um painel que consiste em vários blocos para que os administradores de banco de dados forneçam informações em todos os serviços de banco de dados do Azure, incluindo o BD SQL do Azure, o BD do Azure para PostgreSQL e o BD do Azure para MySQL.

- **Metrics Explorer:** As métricas são valores numéricos gerados pelos recursos do Azure (como% CPU ou e/s de disco) que fornecem informações sobre a operação e o desempenho de seus recursos. Usando Metrics Explorer, você pode definir e enviar as métricas que lhe interessam para Log Analytics para agregação e análise.

### <a name="core-monitoring"></a>Monitoramento principal

- **Azure Monitor:** é o serviço de plataforma principal que fornece uma única fonte para monitorar os recursos do Azure. A interface portal do Azure do Azure Monitor fornece um ponto de desligamento centralizado para todos os recursos de monitoramento no Azure, incluindo os recursos de monitoramento profundo de Application Insights, Log Analytics, monitoramento de rede, soluções de gerenciamento e Mapas de serviço. Com Azure Monitor você pode visualizar, consultar, rotear, arquivar e agir sobre as métricas e os logs provenientes dos recursos do Azure em todo o seu estado de nuvem. Além do portal, você pode recuperar dados por meio dos cmdlets do PowerShell monitor, da CLI entre plataformas ou das APIs REST do Azure Monitor.

- **Assistente do Azure:** O Azure Advisor monitora constantemente a telemetria em suas assinaturas e ambientes e fornece recomendações sobre as práticas recomendadas sobre como otimizar seus recursos do Azure para economizar dinheiro e melhorar o desempenho, a segurança e a disponibilidade dos recursos que compõem seus aplicativos.

- **Integridade do Serviço:** A integridade do serviço do Azure identifica quaisquer problemas com os serviços do Azure que podem afetar seus aplicativos e ajuda você a planejar as janelas de manutenção agendadas.

- **Log de atividades:** O log de atividades descreve todas as operações em recursos em suas assinaturas. Ele fornece uma trilha de auditoria para determinar “o que”, “quem” e “quando” de qualquer operação de criação, atualização e exclusão de recursos. Os eventos do log de atividades são armazenados na plataforma e estão disponíveis para consulta por 90 dias. Você pode ingerir logs de atividades em Log Analytics para períodos de retenção mais longos e consulta e análise mais profundas em vários recursos.

### <a name="deep-application-monitoring"></a>Monitoramento profundo de aplicativos

- **Application Insights:** Application Insights permite coletar telemetria específica do aplicativo e monitorar o desempenho, a disponibilidade e o uso de aplicativos na nuvem ou no local. Instrumentando seu aplicativo com SDKs com suporte para vários idiomas, incluindo .NET, JavaScript, JAVA, Node. js, Ruby e Python. Os eventos do Application Insights são ingeridos no mesmo armazenamento de dados do Log Analytics que dá suporte à infraestrutura e monitoramento de segurança para que você possa correlacionar e agregar eventos ao longo do tempo por meio de uma linguagem de consulta avançada.

### <a name="deep-infrastructure-monitoring"></a>Monitoramento profundo de infraestrutura

- **Log Analytics:** o Log Analytics desempenha um papel central no monitoramento do Azure ao coletar a telemetria e outros dados de diversas fontes e fornecer um mecanismo de linguagem de consulta e de análise que fornece informações sobre a operação de seus aplicativos e recursos. Você pode interagir diretamente com Log Analytics dados por meio de exibições e pesquisas de logs rápidas ou pode usar ferramentas de análise em outros serviços do Azure que armazenam seus dados em Log Analytics como Application Insights ou a central de segurança do Azure.

- **Monitoramento de rede:** Os serviços de monitoramento de rede do Azure permitem que você tenha informações sobre o fluxo de tráfego de rede, desempenho, segurança, conectividade e afunilamentos. Um design de rede bem planejado deve incluir a configuração de serviços de monitoramento de rede do Azure, como o Observador de Rede e o Monitor do ExpressRoute.

- **Soluções de gerenciamento:** As soluções de gerenciamento são conjuntos de lógica, informações e consultas predefinidas de Log Analytics para um aplicativo ou serviço. Elas dependem do Log Analytics como base para armazenar e analisar dados de evento. Os exemplos de soluções de gerenciamento incluem o monitoramento de contêineres e análise de Banco de Dados SQL do Azure.

- **Mapa do Serviço:** Mapa do Serviço fornece uma exibição gráfica dos seus componentes de infraestrutura, seus processos e interdependências em outros computadores e processos externos. Ele integra soluções de gerenciamento, eventos e dados de desempenho ao Log Analytics.

> [!TIP]
> Antes de criar alertas individuais, crie e mantenha um conjunto compartilhado de Grupos de Ação que pode ser usado para os Alertas do Azure. Isso permitirá que você mantenha centralmente o ciclo de vida de listas de destinatários, métodos de entrega de notificação (email, números de telefone para SMS) e webhooks para ações externas (runbooks de Automação do Azure, Azure Functions / Aplicativos Lógicos, ITSM).

## <a name="cost-management"></a>Gerenciamento de custos

Uma das principais alterações que você enfrentará mudar da nuvem local para a nuvem pública é a mudança de gastos de capital (comprar hardware) para gastos operacionais (pagar por serviço conforme você o utiliza). Essa opção também exige um gerenciamento mais cuidadoso dos custos. O benefício da nuvem é que você pode afetar de maneira fundamental e positiva o custo de um serviço usado simplesmente desligando ou redimensionando-o quando não for necessário. Deliberadamente gerenciar seus custos na nuvem é uma prática recomendada e que os clientes maduros fazem diariamente.

A Microsoft fornece várias ferramentas para que você possa visualizar, acompanhar e gerenciar seus custos. Nós também fornecemos um conjunto completo de APIs para que você possa personalizar e integrar o gerenciamento de custos em suas próprias ferramentas e painéis. Essas ferramentas são agrupadas de forma flexível em recursos de portal do Azure e recursos externos.

### <a name="azure-portal-capabilities"></a>Recursos de portal do Azure

Essas são ferramentas para fornecer informações instantâneas sobre o custo, bem como a capacidade de executar ações.

- **Custo do recurso de assinatura:** Localizado no portal, a exibição de [análise de custo do Azure](/azure/cost-management/overview) fornece uma visão rápida de seus custos e informações sobre gastos diários por recurso ou grupo de recursos.
- **Gerenciamento de custos do Azure:** Este produto é o resultado da compra do Cloudyn pela Microsoft e permite que você gerencie e analise seus gastos do Azure, bem como o que você gasta em outros provedores de nuvem pública. Há uma camada gratuita e outra paga, com uma grande variedade de recursos conforme visto na [visão geral](/azure/cost-management/overview).
- **Orçamentos do Azure e grupos de ações:** Saber quais são os custos e fazer algo sobre ele até recentemente ter sido mais um exercício manual. Com a introdução dos orçamentos do Azure e suas APIs, agora é possível criar ações (como visto neste [exemplo](https://channel9.msdn.com/Shows/Azure-Friday/Managing-costs-with-the-Azure-Budgets-API-and-Action-Groups)) quando os custos atingem um limite. Por exemplo, desligar um grupo de recursos de “teste” quando este atinge 100% de seu orçamento ou [outro exemplo].
- **Assistente do Azure**: saber quanto algo custa é apenas a metade; a outra metade é saber o que fazer com essas informações. O [Assistente do Azure](/azure/advisor/advisor-overview) fornece recomendações sobre as ações necessárias para economizar dinheiro, melhorar a confiabilidade ou até mesmo aumentar a segurança.

### <a name="external-cost-management-tools"></a>Ferramentas de gerenciamento de custos externas

- **Power BI Azure Consumption Insights:** Você deseja criar suas próprias visualizações para sua organização? Nesse caso, o pacote de conteúdo do Azure Consumption Insights para Power BI é sua ferramenta de escolha. Usando este pacote de conteúdo e Power BI você pode criar visualizações personalizadas para representar sua organização, fazer uma análise mais profunda dos custos e adicionar outras fontes de dados para aprimorar ainda mais.

- **API de consumo:** As [APIs de consumo](/rest/api/consumption) fornecem acesso programático aos dados de custo e de uso, além das informações sobre orçamentos, instâncias reservadas e encargos do Marketplace. Essas APIs são acessíveis somente para Registros Enterprise e algumas assinaturas Web Direct, porém oferecem a capacidade de integrar seus dados de custo em suas próprias ferramentas e data warehouses. Você também pode [acessar essas APIs por meio do CLI do Azure](/cli/azure/consumption?view=azure-cli-latest).

Os clientes que são usuários de nuvem maduras e de longo prazo seguem algumas práticas altamente recomendadas:

- **Monitore os custos ativamente.** As organizações que são usuários maduros do Azure monitoram constantemente os custos e executam ações quando necessário. Algumas organizações até possuem pessoas dedicadas a fazer a análise e sugerir alterações para uso, e essas pessoas mais que compensam o preço dos seus serviços na primeira vez que encontram um cluster HDInsight não utilizado que estava em execução durante meses.
- **Use instâncias de VM reservadas.** Outra prática essencial para o gerenciamento de custos na nuvem é usar a ferramenta certa para o trabalho. Se você tiver uma VM IaaS que deve permanecer em 24x7, usar uma instância de VM reservada economizará dinheiro significativo. Encontrar o equilíbrio certo entre automatizar o desligamento de VMs e usar instâncias de VM reservadas usa a experiência e a análise.
- **Use a automação com eficiência.** Muitas cargas de trabalho não precisam ser executadas todos os dias. A desativação de uma VM por um período de quatro horas todos os dias pode poupar 15% do seu custo. A automação se pagará rapidamente.
- **Use marcas de recurso para obter visibilidade.** conforme mencionado em outro lugar neste documento, usar as marcas de recurso permitirá uma melhor análise de custos.

Gerenciamento de custos é uma disciplina essencial para uma execução eficaz e eficiente de uma nuvem pública. As empresas que obtêm êxito podem controlar seus custos e corresponderem à demanda real, em vez de comprar e esperar que a demanda venha.

## <a name="automate"></a>Automatizar

Um dos muitos recursos que diferencia a maturidade das organizações que usam provedores de nuvem é o nível de automação que elas têm incorporado. A automação é um processo contínuo e conforme sua organização se move para a nuvem é uma área na qual você precisa investir tempo e recursos. A automação atende a vários propósitos, incluindo a distribuição consistente de recursos (em que ele se vincula diretamente a outro conceito de Scaffold principal, modelos e DevOps) à correção de problemas. A automação é o “tecido conjuntivo” do andaime do Azure e vincula cada área.

Várias ferramentas podem ajudá-lo a criar esse recurso, desde ferramentas de terceiros, como a automação do Azure, a grade de eventos e a CLI do Azure, até um número abrangente de ferramentas de terceiros, como Terraform, Jenkins, chefe e Puppet. As principais ferramentas de automação incluem a automação do Azure, a grade de eventos e a Azure Cloud Shell.

- **Automação do Azure** O é um recurso baseado em nuvem que permite que você crie runbooks (tanto no PowerShell quanto no Python) e permite automatizar processos, configurar recursos e até mesmo aplicar patches. A [Automação do Azure](/azure/automation/automation-intro) tem um conjunto abrangente de recursos de plataforma cruzada que fazem parte da sua implantação, mas são muito extensos para serem abordado em detalhes aqui.
- A **grade de eventos** é um sistema de roteamento de eventos totalmente gerenciado que permite reagir a eventos no ambiente do Azure. Assim como a automação do Azure é a tecido de conexão das organizações de nuvem maduras, a [grade de eventos](/azure/event-grid) é a tecido de conexão de boa automação. Usando a grade de eventos, você pode criar uma ação simples sem servidor para enviar um email a um administrador sempre que um novo recurso é criado e registrar esse recurso em um banco de dados. Essa mesma Grade de Eventos pode notificar quando um recurso é excluído e remover o item do banco de dados.
- **Azure cloud Shell** é um [shell](/azure/cloud-shell/overview) interativo baseado em navegador para gerenciar recursos no Azure. Ele fornece um ambiente completo para o PowerShell ou Bash que é iniciado conforme necessário (e mantido por você) para que você tenha um ambiente consistente para executar seus scripts. O Azure Cloud Shell fornece acesso a ferramentas-chave adicionais – já instaladas – para automatizar seu ambiente, incluindo [CLI do Azure](/cli/azure/get-started-with-azure-cli?view=azure-cli-latest), [Terraform](/azure/virtual-machines/linux/terraform-install-configure) e uma lista crescente de [ferramentas](https://azure.microsoft.com/updates/cloud-shell-new-cli-tools-and-font-size-selection) adicionais para gerenciar contêineres, bancos de dados (sqlcmd) e cada.

A automação é um trabalho em tempo integral e rapidamente se tornará uma das tarefas operacionais mais importantes em sua equipe de nuvem. As organizações que usam a abordagem de “primeiro automatizar” tem maior sucesso usando o Azure:

- **Gerenciando custos:** Buscando ativamente oportunidades e criando automação para redimensionar recursos, escalar ou reduzir verticalmente e desativar recursos não utilizados.
- **Flexibilidade operacional:** Com a automação (juntamente com modelos e DevOps), você tem um nível de repetição que aumenta a disponibilidade, aumenta a segurança e permite que sua equipe se concentre na solução de problemas de negócios.

## <a name="templates-and-devops"></a>Modelos e DevOps

Conforme realçado na seção Automação, sua meta como uma organização deve ser provisionar recursos por meio de scripts e modelos controlados por código-fonte e para minimizar a configuração interativa de seus ambientes. Essa abordagem de “infraestrutura como código”, juntamente com um processo de DevOps disciplinado para implantação contínua pode garantir a consistência e reduzir desvios em seus ambientes. Quase todos os recursos do Azure podem ser implantados por meio de [modelos JSON do Azure Resource Manager](/azure/azure-resource-manager/resource-group-template-deploy) em conjunto com o PowerShell ou com a CLI da plataforma Azure e ferramentas como a Terraform da Hashicorp (que tem um suporte de primeira classe e é integrado ao Azure Cloud Shell).

O artigo como [as práticas recomendadas para usar modelos de Azure Resource Manager](https://blogs.msdn.microsoft.com/mvpawardprogram/2018/05/01/azure-resource-manager) fornece uma excelente discussão sobre as práticas recomendadas e as lições aprendidas para aplicar uma abordagem de DevOps a modelos de Azure Resource Manager com o [Azure DevOps](/azure/devops/user-guide/?view=vsts) ferramentas . Reserve tempo e esforço para desenvolver um conjunto principal de modelos específicos para os requisitos da sua organização e para desenvolver pipelines de entrega contínua com DevOps cadeias (como Azure DevOps, Jenkins, bambu, TeamCity e concurso), especialmente para seu ambientes de produção e de QA. Há uma grande biblioteca de [modelos de início rápido do Azure](https://github.com/Azure/azure-quickstart-templates) no GitHub que você pode usar como ponto de partida para modelos, e você pode criar rapidamente pipelines de entrega baseados em nuvem com o Azure DevOps.

Como prática recomendada para assinaturas de produção ou grupos de recursos, sua meta deve usar a segurança RBAC para não permitir usuários interativos por padrão e usar pipelines de entrega contínua automatizados com base em entidades de serviço para provisionar todos os recursos e Entregue todo o código do aplicativo. Nenhum administrador ou desenvolvedor deve tocar no portal do Azure para configurar os recursos interativamente. Esse nível de DevOps leva um esforço em conjunto e usa todos os conceitos da Scaffold do Azure, fornecendo um ambiente consistente e mais seguro que atenderá às necessidades da sua organização em escala.

> [!TIP]
> Ao projetar e desenvolver modelos complexos do Azure Resource Manager, use [modelos vinculados](/azure/azure-resource-manager/resource-group-linked-templates) para organizar e refatorar relacionamentos complexos de arquivos JSON monolíticos. Isso permitirá que você gerencie recursos individualmente e torne seus modelos mais legíveis, que podem ser testados e reutilizáveis.

O Azure é um provedor de nuvem de hiperescala. À medida que você move sua organização de servidores locais para a nuvem, contando com os mesmos conceitos que os provedores de nuvem e os aplicativos SaaS usam ajudarão sua organização a reagir às necessidades da empresa de maneira muito mais eficiente.

## <a name="core-network"></a>Rede principal

O componente final do modelo de referência de andaime do Azure é essencial para como sua organização acessa o Azure, de forma segura. O acesso a recursos pode ser interno (dentro da rede da empresa) ou externo (por meio da Internet). É fácil para os usuários em sua organização colocar recursos inadvertidamente no ponto errado e potencialmente abri-los para o acesso mal-intencionado. Assim como acontece com dispositivos locais, as empresas devem adicionar os controles adequados para garantir que os usuários do Azure tomam as decisões certas. Para governança da assinatura, identificamos recursos principais que fornecem controle básico de acesso. Os principais recursos consistem em:

- **Redes virtuais** são objetos de contêiner para sub-redes. Embora não sejam estritamente necessárias, geralmente elas são usadas ao conectar aplicativos aos recursos corporativos internos.
- As **rotas definidas pelo usuário** permitem que você manipule a tabela de rotas em uma sub-rede, permitindo que você envie tráfego por meio de uma solução de virtualização de rede ou para um gateway remoto em uma rede virtual emparelhada.
- O **emparelhamento de rede virtual** permite que você conecte diretamente duas ou mais redes virtuais do Azure, criando designs de Hub e spoke mais complexos ou redes de serviços compartilhados.
- **Pontos de extremidade de serviço.** No passado, os serviços de PaaS contavam com métodos diferentes para proteger o acesso aos recursos de suas redes virtuais. Os pontos de extremidade de serviço permitem proteger o acesso aos serviços PaaS habilitados **somente** a partir de pontos de extremidade conectados, aumentando a segurança geral.
- Os **grupos de segurança** são um amplo conjunto de regras que fornecem a capacidade de permitir ou negar o tráfego de entrada e saída de/para recursos do Azure. [Grupos de segurança](/azure/virtual-network/security-overview) consistem em regras de segurança que podem ser aumentadas com **marcas de serviço** (que definem serviços comuns do Azure, como Azure Key Vault ou banco de dados SQL do Azure) e grupos de **segurança de aplicativo** (que definem e o aplicativo estrutura, como servidores Web ou servidores de aplicativos.

> [!TIP]
> Use marcas de serviço e grupos de segurança de aplicativo em seus grupos de segurança de rede não apenas para aprimorar&mdash;a legibilidade de suas regras,&mdash;o que é crucial para entender o impacto, mas também para habilitar o microsegmentação eficaz dentro de um sub-rede maior, reduzindo a proliferação e aumentando a flexibilidade.

### <a name="azure-virtual-datacenter"></a>Datacenter Virtual do Azure

O Azure fornece recursos internos e recursos de terceiros da nossa extensa rede de parceiros que permitem que você tenha uma postura eficaz em relação à segurança. Mais importante, a Microsoft fornece as práticas recomendadas e orientações na forma de [VDC (datacenter virtual) do Azure](/azure/architecture/vdc/networking-virtual-datacenter). À medida que você passa de uma única carga de trabalho para várias cargas de trabalho que usam recursos híbridos, as diretrizes de VDC fornecerão "receitas" para permitir uma rede flexível e que aumentará à medida que suas cargas de trabalho no Azure crescem.

## <a name="next-steps"></a>Próximas etapas

A governança é essencial para o sucesso do Azure. Este artigo foca na implementação técnica de um andaime empresarial, mas toca apenas no processo mais amplo e nas relações entre os componentes. A governança da política flui de cima para baixo e é determinada por aquilo que a empresa quer alcançar. Naturalmente, a criação de um modelo de governança para o Azure inclui representantes da TI, mas o mais importante é ter uma forte representação dos líderes do grupo de negócios, além de gerenciamento de segurança e risco. No fim, um andaime empresarial é sobre reduzir o risco aos negócios para facilitar a missão e os objetivos de uma organização.

Agora que você aprendeu sobre governança de assinatura, é hora de ver essas recomendações na prática. Veja [Exemplos de implementação da governança de assinatura do Azure](azure-scaffold-examples.md).
