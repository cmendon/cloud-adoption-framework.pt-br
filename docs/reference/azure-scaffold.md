---
title: Práticas recomendadas para empresas que se movem para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve um Scaffold que as empresas podem usar para garantir um ambiente seguro e gerenciável.
author: rdendtler
ms.author: rodend
ms.date: 09/22/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: 2e605766e06b106fab61576e64bd5059569c8b38
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548773"
---
# <a name="azure-enterprise-scaffold-prescriptive-subscription-governance"></a>Azure Enterprise Scaffold: governança de assinatura prescritiva

> [!NOTE]
> O Azure Enterprise scaffolding foi integrado à estrutura de adoção Microsoft Cloud. O conteúdo deste artigo agora está representado na seção [pronta](../ready/index.md) da nova estrutura. Este artigo será preterido no início de 2020. Para começar a usar o novo processo, consulte a [visão geral pronta](../ready/index.md), [criando sua primeira zona de aterrissagem](../ready/azure-setup-guide/migration-landing-zone.md)e/ou [Considerações sobre a zona de aterrissagem](../ready/considerations/index.md).

As empresas estão adotando cada vez mais a nuvem pública para sua agilidade e flexibilidade. Eles contam com os pontos fortes da nuvem para gerar receita e otimizar o uso de recursos para os negócios. O Microsoft Azure fornece uma infinidade de serviços e recursos que as empresas montam como blocos de construção para lidar com uma ampla gama de cargas de trabalho e aplicativos.

Decidir usar Microsoft Azure é apenas a primeira etapa para alcançar o benefício da nuvem. A segunda etapa é entender como a empresa pode efetivamente usar o Azure e identificar os recursos de linha de base que precisam estar em vigor para abordar perguntas como:

- "Estou preocupado com a soberania dos dados; Como garantir que meus dados e sistemas atendam aos nossos requisitos regulatórios? "
- "Como fazer saber qual é o suporte de cada recurso para que eu possa fazer sua conta e cobrar com precisão?"
- "Quero ter certeza de que tudo que implantamos ou fazemos na nuvem pública começa com a mentalidade da segurança primeiro, como posso ajudar a facilitar isso?"

O cliente potencial de uma assinatura vazia sem guardrails é assustador. Esse espaço em branco pode dificultar a mudança para o Azure.

Este artigo fornece um ponto de partida para que os profissionais técnicos atendam à necessidade de governança e equilibrem a ti com a necessidade de agilidade. Ele apresenta o conceito de uma Scaffold empresarial que orienta as organizações na implementação e gerenciamento de seus ambientes do Azure de maneira segura. Ele fornece a estrutura para desenvolver controles eficazes e eficientes.

## <a name="need-for-governance"></a>Necessidade de governança

Ao mudar para o Azure, você deve abordar o tópico de governança antecipadamente para garantir o uso bem-sucedido da nuvem dentro da empresa. Infelizmente, o tempo e a burocracia de criação de um sistema de governança abrangente significam que alguns grupos de negócios vão diretamente para os provedores sem envolver a ti empresarial. Essa abordagem pode deixar a empresa aberta para ser comprometida se os recursos não forem gerenciados corretamente. As características da nuvem pública &mdash;agility, flexibilidade e preço baseado em consumo &mdash;are importantes para grupos de negócios que precisam atender rapidamente às demandas de clientes (internos e externos). Mas a ti empresarial precisa garantir que os dados e os sistemas sejam protegidos efetivamente.

Ao criar uma compilação, scaffolding é usado para criar a base de uma estrutura. O scaffold guia a estrutura de tópicos geral e fornece pontos de ancoragem para que sistemas mais permanentes sejam montados. Um Scaffold empresarial é o mesmo: um conjunto de controles flexíveis e recursos do Azure que fornecem a estrutura para o ambiente e âncoras para serviços criados na nuvem pública. Ele fornece aos construtores (grupos de negócios) uma base para criar e anexar novos serviços, mantendo a velocidade de entrega em mente.

O scaffold é baseado em práticas que coletamos de muitos compromissos com clientes de vários tamanhos. Esses clientes variam de pequenas organizações que desenvolvem soluções na nuvem para grandes empresas multinacionais e fornecedores de software independentes que estão migrando cargas de trabalho e desenvolvendo soluções nativas de nuvem. O Enterprise Scaffold é "criado especificamente" para ser flexível para dar suporte a cargas de trabalho de ti tradicionais e a cargas Agile, como os desenvolvedores que criam aplicativos SaaS (software como serviço) baseados em recursos da plataforma Azure.

A Scaffold empresarial deve ser a base de cada nova assinatura no Azure. Ele permite que os administradores garantam que as cargas de trabalho atendam aos requisitos mínimos de governança de uma organização sem impedir que grupos de negócios e desenvolvedores atendam rapidamente às suas próprias metas. Nossa experiência mostra que isso acelera bastante, em vez de impedir o crescimento da nuvem pública.

> [!NOTE]
> A Microsoft lançou-se na versão prévia de uma nova funcionalidade chamada [plantas do Azure](https://docs.microsoft.com/azure/governance/blueprints/overview) que permitirá empacotar, gerenciar e implantar imagens, modelos, políticas e scripts comuns em assinaturas e grupos de gerenciamento. Esse recurso é a ponte entre a finalidade do Scaffold como modelo de referência e a implantação desse modelo em sua organização.
>
A imagem a seguir mostra os componentes do Scaffold. A base depende de um plano sólido para a hierarquia de gerenciamento e as assinaturas. Os pilares consistem em políticas do Resource Manager e em padrões de nomenclatura fortes. O restante do Scaffold são recursos e recursos principais do Azure que habilitam e conectam um ambiente seguro e gerenciável.

![Scaffold empresarial](../_images/reference/scaffoldv2.png)

## <a name="define-your-hierarchy"></a>Definir sua hierarquia

A base do Scaffold é a hierarquia e a relação do registro do Azure Enterprise por meio de assinaturas e grupos de recursos. O registro Enterprise define a forma e o uso dos serviços do Azure em sua empresa a partir de um ponto de vista contratual. Dentro do Enterprise Agreement, você pode subdividir ainda mais o ambiente em departamentos, contas, assinaturas e grupos de recursos para corresponder à estrutura da sua organização.

![hierárquica](../_images/reference/agreement.png)

Uma assinatura do Azure é a unidade básica em que todos os recursos estão contidos. Ele também define vários limites no Azure, como o número de núcleos, redes virtuais e outros recursos. Os grupos de recursos são usados para refinar ainda mais o modelo de assinatura e habilitar um agrupamento mais natural de recursos.

Toda empresa é diferente e a hierarquia na imagem acima permite uma flexibilidade significativa na forma como o Azure é organizado em sua empresa. Modelar sua hierarquia para refletir a cobrança, o gerenciamento de recursos e as necessidades de acesso aos recursos de sua empresa é a primeira e mais importante decisão que você faz ao iniciar na nuvem pública.

### <a name="departments-and-accounts"></a>Departamentos e contas

Os três padrões comuns para registros do Azure são:

- O padrão **funcional** :

  ![O padrão funcional](../_images/reference/functional.png)

- O padrão de **unidade de negócios** :

  ![O padrão de unidade de negócios](../_images/reference/business.png)

- O padrão **geográfico** :

  ![O padrão geográfico](../_images/reference/geographic.png)

Embora cada um desses padrões tenha seu lugar, o padrão de **unidade de negócios** está sendo adotado cada vez mais por sua flexibilidade na modelagem do modelo de custo de uma organização, além de refletir o alcance do controle. O Microsoft Core Engineering and Operations Group criou um subconjunto efetivo do padrão de **unidade de negócios** modelado em **Federal**, **estadual**e **local**. Para obter mais informações, consulte [organizando assinaturas e grupos de recursos dentro da empresa](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).

### <a name="azure-management-groups"></a>Grupos de gerenciamento do Azure

A Microsoft agora fornece outra maneira de modelar sua hierarquia: [grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview). Os grupos de gerenciamento são muito mais flexíveis do que os departamentos e as contas, e podem ser aninhados até seis níveis. Os grupos de gerenciamento permitem criar uma hierarquia separada da sua hierarquia de cobrança, exclusivamente para o gerenciamento eficiente de recursos. Os grupos de gerenciamento podem espelhar sua hierarquia de cobrança e, muitas vezes, as empresas iniciam dessa maneira. No entanto, o poder dos grupos de gerenciamento é quando você os utiliza para modelar sua organização, agrupando as assinaturas relacionadas (independentemente de sua localização na hierarquia de cobrança) e atribuindo funções, políticas e iniciativas comuns. Alguns exemplos incluem:

- **Produção versus não produto.** Algumas empresas criam grupos de gerenciamento para identificar suas assinaturas de produção e não produções. Os grupos de gerenciamento permitem que esses clientes gerenciem funções e políticas com mais facilidade. Por exemplo, a assinatura de não produção pode permitir o acesso de "colaborador" de desenvolvedores, mas em produção, eles têm apenas acesso "leitor".
- **Serviços internos vs. serviços externos.** As empresas geralmente têm requisitos, políticas e funções diferentes para serviços internos versus serviços voltados para o cliente.

Os grupos de gerenciamento bem projetados são, juntamente com Azure Policy e iniciativas, o backbone da governança eficiente do Azure.

### <a name="subscriptions"></a>Assinaturas

Ao decidir sobre seus departamentos e contas (ou grupos de gerenciamento), você está vendo principalmente como está dividindo seu ambiente do Azure para corresponder à sua organização. No entanto, as assinaturas são onde acontecem o trabalho real e suas decisões aqui afetam a segurança, a escalabilidade e a cobrança. Muitas organizações analisam os seguintes padrões como seus guias:

- **Aplicativo/serviço:** As assinaturas representam um aplicativo ou um serviço (portfólio de aplicativos)
- **Ciclo de vida:** As assinaturas representam um ciclo de vida de um serviço, como produção ou desenvolvimento.
- **Departamento:** As assinaturas representam os departamentos da organização.

Os dois primeiros padrões são os mais comumente usados, e ambos são altamente recomendados. A abordagem do ciclo de vida é apropriada para a maioria das organizações. Nesse caso, a recomendação geral é usar duas assinaturas base, `Production` e `Nonproduction` e, em seguida, usar grupos de recursos para separar ainda mais os ambientes.

### <a name="resource-groups"></a>Grupos de recursos

Azure Resource Manager permite colocar recursos em grupos significativos para gerenciamento, cobrança ou afinidade natural. Os grupos de recursos são contêineres de recursos que têm um ciclo de vida comum ou compartilham um atributo como "todos os SQL Servers" ou "aplicativo A".

Os grupos de recursos não podem ser aninhados e os recursos só podem pertencer a um grupo de recursos. Algumas ações podem agir em todos os recursos em um grupo de recursos. Por exemplo, a exclusão de um grupo de recursos remove todos os recursos dentro do grupo de recursos. Assim como as assinaturas, há padrões comuns ao criar grupos de recursos e variam de cargas de trabalho de "ti tradicional" a cargas de trabalho de "ti Agile":

- As cargas de trabalho de "ti tradicional" geralmente são agrupadas por itens dentro do mesmo ciclo de vida, como um aplicativo. O agrupamento por aplicativo permite o gerenciamento de aplicativos individuais.
- As cargas de trabalho "ti Agile" tendem a se concentrar em aplicativos de nuvem voltados para o cliente. Os grupos de recursos geralmente refletem as camadas de implantação (como uma camada da Web ou camada de aplicativo) e gerenciamento.

> [!NOTE]
> Entender sua carga de trabalho ajuda a desenvolver uma estratégia de grupo de recursos. Esses padrões podem ser combinados e combinados. Por exemplo, um grupo de recursos de serviços compartilhados na mesma assinatura que os grupos de recursos "Agile".

## <a name="naming-standards"></a>Padrões de nomenclatura

O primeiro pilar do Scaffold é um padrão de nomenclatura consistente. Os padrões de nomenclatura bem projetados permitem que você identifique recursos no portal, em uma fatura e em scripts. Provavelmente você já tem padrões de nomenclatura existentes para a infraestrutura local. Ao adicionar o Azure ao seu ambiente, você deve estender esses padrões de nomenclatura para os recursos do Azure.

> [!TIP]
> Para convenções de nomenclatura:
>
> - Analise e adote onde possível as [Orientações de padrões e práticas](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions). Este guia ajuda você a decidir sobre um padrão de nomenclatura significativo e fornece exemplos extensivos.
> - Usar políticas do Resource Manager para ajudar a reforçar os padrões de nomenclatura.
>
> Lembre-se de que é difícil alterar nomes posteriormente, portanto, alguns minutos agora vão poupar problemas mais tarde.

Concentre seus padrões de nomenclatura nesses recursos que são mais comumente usados e pesquisados. Por exemplo, todos os grupos de recursos devem seguir um padrão forte para maior clareza.

### <a name="resource-tags"></a>Marcas de recurso

As marcas de recurso estão estreitamente alinhadas com os padrões de nomenclatura. À medida que os recursos são adicionados às assinaturas, se torna cada vez mais importante categorizá-los logicamente para fins de cobrança, gerenciamento e operação. Para obter mais informações, consulte [usar marcas para organizar os recursos do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

> [!IMPORTANT]
> As marcas podem conter informações pessoais e podem estar sob as regulamentações de GDPR. Planeje o gerenciamento de suas marcas com cuidado. Se você estiver procurando informações gerais sobre GDPR, consulte a seção GDPR do portal de [confiança do serviço](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

As marcas são usadas de muitas maneiras além da cobrança e do gerenciamento. Eles são frequentemente usados como parte da automação (consulte a seção mais adiante). Isso pode causar conflitos se não for considerado antecipado. A prática recomendada é identificar todas as marcas comuns no nível empresarial (como ApplicationOwner e CostCenter) e aplicá-las de forma consistente ao implantar recursos usando a automação.

## <a name="azure-policy-and-initiatives"></a>Azure Policy e iniciativas

O segundo pilar do Scaffold envolve o uso de [Azure Policy e iniciativas](https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction) para gerenciar riscos ao impor regras (com efeitos) sobre os recursos e serviços em suas assinaturas. As iniciativas do Azure são coleções de políticas que são projetadas para atingir uma única meta. As políticas e iniciativas são então atribuídas a um escopo de recurso para iniciar a imposição dessas políticas.

As políticas e iniciativas são ainda mais poderosas quando usadas com os grupos de gerenciamento mencionados anteriormente. Os grupos de gerenciamento permitem a atribuição de uma iniciativa ou política a um conjunto inteiro de assinaturas.

### <a name="common-uses-of-resource-manager-policies"></a>Usos comuns de políticas do Resource Manager

Políticas e iniciativas são uma ferramenta poderosa no kit de ferramentas do Azure. As políticas permitem que as empresas forneçam controles para cargas de trabalho de "ti tradicional" que habilitam a estabilidade necessária para aplicativos de linha de negócios e, ao mesmo tempo, permitem cargas de trabalho "Agile" &mdash;for exemplo, desenvolvendo aplicativos de clientes sem expondo a empresa a um risco adicional. Os padrões mais comuns para políticas são:

- **Conformidade geográfica e soberania de dados.** O Azure tem uma lista cada vez maior de regiões em todo o mundo. Muitas vezes, as empresas precisam garantir que os recursos em um escopo específico permaneçam em uma região geográfica para atender aos requisitos regulatórios.
- **Evite expor servidores publicamente.** Azure Policy pode proibir a implantação de determinados tipos de recursos. É comum criar uma política para negar a criação de um IP público dentro de um escopo específico, evitando a exposição involuntária de um servidor à Internet.
- **Gerenciamento de custos e metadados.** As marcas de recurso geralmente são usadas para adicionar dados de cobrança importantes a recursos e grupos de recursos, como CostCenter, proprietário e muito mais. Essas marcas são inestimáveis para a cobrança precisa e o gerenciamento de recursos. As políticas podem impor a aplicação de marcas de recursos a todos os recursos implantados, facilitando o gerenciamento.

### <a name="common-uses-of-initiatives"></a>Usos comuns de iniciativas

As iniciativas fornecem às empresas a capacidade de agrupar políticas lógicas e rastreá-las como uma única entidade. As iniciativas ajudam a empresa a atender às necessidades das cargas de trabalho Agile e tradicional. Os usos comuns das iniciativas incluem:

- **Habilite o monitoramento na central de segurança do Azure.** Essa é uma iniciativa padrão no Azure Policy e um excelente exemplo de quais iniciativas são. Ele permite políticas que identificam bancos de dados SQL não criptografados, vulnerabilidades de VM (máquina virtual) e necessidades mais comuns relacionadas à segurança.
- **Iniciativa específica de regulamentação.** As empresas geralmente agrupam políticas comuns a um requisito normativo (como a HIPAA) para que os controles e conformidade para esses controles sejam acompanhados com eficiência.
- **Tipos de recursos e SKUs.** A criação de uma iniciativa que restringe os tipos de recursos que podem ser implantados, bem como as SKUs que podem ser implantadas, pode ajudar a controlar os custos e garantir que sua organização esteja apenas implantando recursos para os quais sua equipe tem o conjunto de habilidades e os procedimentos para dar suporte.

> [!TIP]
> Recomendamos que você sempre use definições de iniciativa em vez de definições de política. Depois de atribuir uma iniciativa a um escopo, como assinatura ou grupo de gerenciamento, você pode adicionar facilmente outra política à iniciativa sem precisar alterar nenhuma atribuição. Isso torna a compreensão do que é aplicado e o controle da conformidade muito mais fácil.

### <a name="policy-and-initiative-assignments"></a>Atribuições de política e iniciativa

Depois de criar políticas e agrupá-las em iniciativas lógicas, você deve atribuir a política a um escopo, seja um grupo de gerenciamento, uma assinatura ou até mesmo um grupo de recursos. As atribuições permitem que você também exclua um subescopo da atribuição de uma política. Por exemplo, se você negar a criação de IPs públicos em uma assinatura, poderá criar uma atribuição com uma exclusão para um grupo de recursos conectado à DMZ protegida.

Você encontrará vários exemplos de política que mostram como a política e as iniciativas podem ser aplicadas a vários recursos no Azure neste repositório [GitHub](https://github.com/Azure/azure-policy) .

## <a name="identity-and-access-management"></a>Gerenciamento de identidades e acessos

Uma das primeiras e mais importantes perguntas que você se pergunta ao começar com a nuvem pública é "quem deve ter acesso aos recursos?" e "como faço para controlar esse acesso?" Controlar o acesso ao portal do Azure e aos recursos no portal é essencial para a segurança de longo prazo de seus ativos na nuvem.

Para proteger o acesso aos seus recursos, primeiro você configurará seu provedor de identidade e, em seguida, configurará funções e acesso. O Azure Active Directory (Azure AD), conectado à sua Active Directory local, é a base da identidade do Azure. Dito isso, o Azure AD *não* é o mesmo local Active Directory, e é importante entender o que é um locatário do Azure AD e como ele se relaciona com o registro do Azure. Examine as [informações](../govern/resource-consistency/resource-access-management.md) disponíveis para obter uma base sólida sobre o Azure AD e o Active Directory local. Para conectar e sincronizar seu Active Directory com o Azure AD, instale e configure a [ferramenta de Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) local.

![Diagrama da arquitetura do AD](../_images/reference/ad-architecture.png)

Quando o Azure foi lançado inicialmente, os controles de acesso a uma assinatura eram básicos: administrador ou coadministrador. Acesso a uma assinatura no modelo clássico acesso implícito a todos os recursos no Portal. Essa falta de controle refinado levou à proliferação de assinaturas para fornecer um nível de controle de acesso razoável para um registro do Azure. Essa proliferação de assinaturas não é mais necessária. Com o RBAC (controle de acesso baseado em função), você pode atribuir usuários a funções padrão que fornecem acesso comum, como "proprietário", "colaborador" ou "leitor", ou até mesmo criar suas próprias funções.

Ao implementar o acesso baseado em função, as seguintes opções são altamente recomendadas:

- Controle o administrador/coadministrador de uma assinatura, pois essas funções têm permissões extensivas. Você só precisa adicionar o proprietário da assinatura como um coadministrador se precisar gerenciar implantações clássicas do Azure.
- Use grupos de gerenciamento para atribuir [funções](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview#management-group-access) em várias assinaturas e reduzir a carga de gerenciá-las no nível de assinatura.
- Adicione usuários do Azure a um grupo (por exemplo, proprietários de aplicativo X) em Active Directory. Use o grupo sincronizado para fornecer aos membros do grupo os direitos apropriados para gerenciar o grupo de recursos que contém o aplicativo.
- Siga o princípio de conceder o **privilégio mínimo** necessário para fazer o trabalho esperado.

> [!IMPORTANT]
>Considere usar [Azure ad Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure), [autenticação multifator](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) do Azure e recursos de [acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) para fornecer melhor segurança e mais visibilidade para ações administrativas em todo o Azure assinaturas. Esses recursos são provenientes de uma licença de Azure AD Premium válida (dependendo do recurso) para proteger ainda mais e gerenciar sua identidade. O PIM do Azure AD permite o acesso administrativo "Just-in-time" com o fluxo de trabalho de aprovação, bem como uma auditoria completa de ativações e atividades do administrador. A autenticação multifator do Azure é outro recurso crítico e permite a verificação em duas etapas para fazer logon no portal do Azure. Quando combinado com controles de acesso condicional, você pode gerenciar efetivamente o risco de comprometimento.

Planejar e preparar para seus controles de identidade e de acesso e seguir a prática recomendada de gerenciamento de identidade do Azure ([link](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices)) é uma das melhores estratégias de mitigação de risco que você pode empregar e deve ser considerado obrigatório para cada implantação.

## <a name="security"></a>Segurança

Um dos maiores bloqueadores para a adoção de nuvem tradicionalmente tem sido preocupado com a segurança. Os gerentes de risco de ti e os departamentos de segurança precisam garantir que os recursos no Azure estejam protegidos e seguros por padrão. O Azure fornece recursos que você pode usar para proteger recursos ao detectar e eliminar ameaças contra esses recursos.

### <a name="azure-security-center"></a>Central de Segurança do Azure

A [central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) fornece uma exibição unificada do status de segurança dos recursos em seu ambiente, além da proteção avançada contra ameaças. A central de segurança do Azure é uma plataforma aberta que permite que os parceiros da Microsoft criem softwares que se conectam e aprimoram seus recursos. Os recursos de linha de base da central de segurança do Azure (camada gratuita) fornecem avaliação e recomendações que aprimorarão sua postura de segurança. Suas camadas pagas permitem recursos adicionais e valiosos, como acesso de administrador just-in-time e controles de aplicativo adaptáveis (lista de permissões).

> [!TIP]
>A central de segurança do Azure é uma ferramenta poderosa que é aprimorada regularmente com novos recursos que você pode usar para detectar ameaças e proteger sua empresa. É altamente recomendável habilitar sempre a central de segurança do Azure.

### <a name="azure-resource-locks"></a>Bloqueios de recursos do Azure

À medida que sua organização adiciona serviços principais às assinaturas, ela se torna cada vez mais importante para evitar a interrupção dos negócios. Um tipo de interrupção que muitas vezes vemos são consequências indesejadas de scripts e ferramentas que trabalham em uma assinatura do Azure excluindo os recursos erroneamente. Os [bloqueios de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) permitem restringir operações em recursos de alto valor, onde modificá-las ou excluí-las teria um impacto significativo. Os bloqueios são aplicados a uma assinatura, grupo de recursos ou até mesmo recursos individuais. O caso de uso comum é aplicar bloqueios a recursos fundamentais, como redes virtuais, gateways, grupos de segurança de rede e contas de armazenamento de chaves.

### <a name="secure-devops-toolkit"></a>Kit de ferramentas do Secure DevOps

O Secure DevOps Kit for Azure (AzSK) é uma coleção de scripts, ferramentas, extensões e recursos de automação originalmente criados pela própria equipe de ti da Microsoft e [lançado como software livre por meio do GitHub](https://github.com/azsk/DevOpsKit-docs). O AzSK atende às necessidades de segurança de recursos e assinatura do Azure de ponta a ponta para equipes que usam automação abrangente e integram a segurança em fluxos de trabalho nativos do DevOps, ajudando a atingir DevOps seguras com estas seis áreas de enfoque:

- Proteger a assinatura
- Habilitar o desenvolvimento seguro
- Integrar a segurança ao CI/CD
- Garantia contínua
- Alertas e monitoramento
- Governança de riscos na nuvem

![Kit de ferramentas do Azure DevOps](../_images/reference/secure-devops-kit.png)

O AzSK é um rico conjunto de ferramentas, scripts e informações que são uma parte importante de um plano de governança do Azure completo e incorporando isso em seu Scaffold é crucial para dar suporte às metas de gerenciamento de riscos de suas organizações.

### <a name="azure-update-management"></a>Gerenciamento de Atualizações do Azure

Uma das principais tarefas que você pode fazer para manter seu ambiente seguro é garantir que os servidores sejam corrigidos com as atualizações mais recentes. Embora haja muitas ferramentas para fazer isso, o Azure fornece a solução de [Gerenciamento de atualizações do Azure](https://docs.microsoft.com/azure/automation/automation-update-management) para resolver a identificação e a distribuição de patches críticos do sistema operacional. Ele usa a automação do Azure, abordada na seção [automatizada](#automate) posteriormente neste guia.

## <a name="monitor-and-alerts"></a>Monitorar e alertas

Coletar e analisar a telemetria que fornece a linha de visão sobre as atividades, as métricas de desempenho, a integridade e a disponibilidade dos serviços que você está usando em suas assinaturas do Azure é essencial para gerenciar proativamente seus aplicativos e infraestrutura e é uma necessidade fundamental de cada assinatura do Azure. Cada serviço do Azure emite a telemetria na forma de logs de atividades, métricas e logs de diagnóstico.

- Os **logs de atividades** descrevem todas as operações executadas nos recursos em suas assinaturas.
- **Métricas** são informações numéricas emitidas por um recurso que descrevem o desempenho e a integridade de um recurso.
- **Os logs de diagnóstico** são emitidos por um serviço do Azure e fornecem dados avançados e frequentes sobre a operação do serviço.

Essas informações podem ser exibidas e acionadas em vários níveis e estão continuamente sendo aprimoradas. O Azure fornece recursos de monitoramento **compartilhados**, **básicos**e **profundos** dos recursos do Azure por meio dos serviços descritos no diagrama a seguir.

![Monitoriza](../_images/reference/monitoring.png)

### <a name="shared-capabilities"></a>Recursos compartilhados

- **Alertas:** Você pode coletar todos os logs, eventos e métricas dos recursos do Azure, mas sem a capacidade de ser notificado sobre condições críticas e agir, esses dados só são úteis para fins de histórico e análise forense. Os alertas do Azure notificam proativamente sobre as condições que você define em todos os seus aplicativos e infraestrutura. Você cria regras de alerta entre logs, eventos e métricas que usam grupos de ação para notificar conjuntos de destinatários. Os grupos de ação também fornecem a capacidade de automatizar a correção usando ações externas, como WebHooks, para executar runbooks e Azure Functions de automação do Azure.

- **Painéis:** Os painéis permitem agregar exibições de monitoramento e combinar dados entre recursos e assinaturas para dar a você uma visão empresarial da telemetria dos recursos do Azure. Você pode criar e configurar seus próprios modos de exibição e compartilhá-los com outras pessoas. Por exemplo, você pode criar um painel que consiste em vários blocos para que os administradores de banco de dados forneçam informações em todos os serviços de banco de dados do Azure, incluindo o BD SQL do Azure, o BD do Azure para PostgreSQL e o BD do Azure para MySQL.

- **Metrics Explorer:** As métricas são valores numéricos gerados pelos recursos do Azure (como% CPU ou e/s de disco) que fornecem informações sobre a operação e o desempenho de seus recursos. Usando Metrics Explorer, você pode definir e enviar as métricas que lhe interessam para Log Analytics para agregação e análise.

### <a name="core-monitoring"></a>Monitoramento de núcleo

- **Azure monitor:** Azure Monitor é o serviço de plataforma principal que fornece uma única fonte para monitorar os recursos do Azure. A interface portal do Azure do Azure Monitor fornece um ponto de desligamento centralizado para todos os recursos de monitoramento no Azure, incluindo os recursos de monitoramento profundo de Application Insights, Log Analytics, monitoramento de rede, soluções de gerenciamento e Mapas de serviço. Com Azure Monitor você pode visualizar, consultar, rotear, arquivar e agir sobre as métricas e os logs provenientes dos recursos do Azure em todo o seu estado de nuvem. Além do portal, você pode recuperar dados por meio dos cmdlets do PowerShell monitor, da CLI entre plataformas ou das APIs REST do Azure Monitor.

- Assistente **do Azure:** O Azure Advisor monitora constantemente a telemetria em suas assinaturas e ambientes e fornece recomendações sobre as práticas recomendadas sobre como otimizar seus recursos do Azure para economizar dinheiro e melhorar o desempenho, a segurança e a disponibilidade dos recursos que compõem seus aplicativos.

- **Integridade do serviço:** A integridade do serviço do Azure identifica quaisquer problemas com os serviços do Azure que podem afetar seus aplicativos e ajuda você a planejar as janelas de manutenção agendadas.

- **Log de atividades:** O log de atividades descreve todas as operações em recursos em suas assinaturas. Ele fornece uma trilha de auditoria para determinar o ' What ', ' quem ' e ' When ' de qualquer operação de criação, atualização e exclusão em recursos. Os eventos do log de atividades são armazenados na plataforma e estão disponíveis para consulta por 90 dias. Você pode ingerir logs de atividades em Log Analytics para períodos de retenção mais longos e consulta e análise mais profundas em vários recursos.

### <a name="deep-application-monitoring"></a>Monitoramento profundo de aplicativos

- **Application insights:** Application Insights permite coletar telemetria específica do aplicativo e monitorar o desempenho, a disponibilidade e o uso de aplicativos na nuvem ou no local. Instrumentando seu aplicativo com SDKs com suporte para vários idiomas, incluindo .NET, JavaScript, JAVA, Node. js, Ruby e Python. Application Insights eventos são ingeridos no mesmo armazenamento de dados Log Analytics que dá suporte à infraestrutura e ao monitoramento de segurança para permitir que você correlacione e agregue eventos ao longo do tempo por meio de uma linguagem de consulta rica.

### <a name="deep-infrastructure-monitoring"></a>Monitoramento de infraestrutura profunda

- **Log Analytics:** Log Analytics desempenha uma função central no monitoramento do Azure coletando telemetria e outros dados de uma variedade de fontes e fornecendo um mecanismo de linguagem de consulta e análise que fornece informações sobre a operação de seus aplicativos e recursos. Você pode interagir diretamente com Log Analytics dados por meio de exibições e pesquisas de logs rápidas ou pode usar ferramentas de análise em outros serviços do Azure que armazenam seus dados em Log Analytics como Application Insights ou a central de segurança do Azure.

- **Monitoramento de rede:** Os serviços de monitoramento de rede do Azure permitem que você tenha informações sobre o fluxo de tráfego de rede, desempenho, segurança, conectividade e afunilamentos. Um design de rede bem planejado deve incluir a configuração de serviços de monitoramento de rede do Azure, como o observador de rede e o monitor do ExpressRoute.

- **Soluções de gerenciamento:** As soluções de gerenciamento são conjuntos de lógica, informações e consultas predefinidas de Log Analytics para um aplicativo ou serviço. Eles contam com Log Analytics como base para armazenar e analisar dados de evento. Soluções de gerenciamento de exemplo incluem contêineres de monitoramento e análise de banco de dados SQL do Azure.

- **Mapa do serviço:** Mapa do Serviço fornece uma exibição gráfica dos seus componentes de infraestrutura, seus processos e interdependências em outros computadores e processos externos. Ele integra eventos, dados de desempenho e soluções de gerenciamento no Log Analytics.

> [!TIP]
> Antes de criar alertas individuais, crie e mantenha um conjunto de grupos de ações compartilhadas que podem ser usados em alertas do Azure. Isso permitirá que você mantenha centralmente o ciclo de vida de suas listas de destinatários, métodos de entrega de notificação (email, números de telefone de SMS) e WebHooks para ações externas (runbooks de automação do Azure, aplicativos de Azure Functions/lógica, ITSM).

## <a name="cost-management"></a>Gerenciamento de custos

Uma das principais alterações que você enfrentará ao mudar da nuvem local para a nuvem pública é a mudança de despesas de capital (compra de hardware) para as despesas operacionais (pagando pelo serviço ao usá-lo). Essa opção também exige um gerenciamento mais cuidadoso dos custos. O benefício da nuvem é que você pode afetar de maneira fundamental e positiva o custo de um serviço usado simplesmente desligando ou redimensionando-o quando não for necessário. O gerenciamento deliberado dos custos na nuvem é uma prática recomendada e um que os clientes maduros fazem diariamente.

A Microsoft fornece várias ferramentas para que você possa visualizar, acompanhar e gerenciar seus custos. Também fornecemos um conjunto completo de APIs para permitir que você personalize e integre o gerenciamento de custos em suas próprias ferramentas e painéis. Essas ferramentas são agrupadas de forma flexível em recursos de portal do Azure e recursos externos.

### <a name="azure-portal-capabilities"></a>Recursos de portal do Azure

Essas são ferramentas para fornecer informações instantâneas sobre o custo, bem como a capacidade de executar ações.

- **Custo do recurso de assinatura:** Localizado no portal, a exibição de [análise de custo do Azure](https://docs.microsoft.com/azure/cost-management/overview) fornece uma visão rápida de seus custos e informações sobre gastos diários por recurso ou grupo de recursos.
- **Gerenciamento de custos do Azure:** Este produto é o resultado da compra do Cloudyn pela Microsoft e permite que você gerencie e analise seus gastos do Azure, bem como o que você gasta em outros provedores de nuvem pública. Há camadas gratuitas e pagas, com uma grande variedade de recursos, como visto na [visão geral](https://docs.microsoft.com/azure/cost-management/overview).
- **Orçamentos do Azure e grupos de ações:** Saber quais são os custos e fazer algo sobre ele até recentemente ter sido mais um exercício manual. Com a introdução dos orçamentos do Azure e suas APIs, agora é possível criar ações (como visto neste [exemplo](https://channel9.msdn.com/Shows/Azure-Friday/Managing-costs-with-the-Azure-Budgets-API-and-Action-Groups)) quando os custos atingem um limite. Por exemplo, desligar um grupo de recursos de "teste" quando atinge 100% de seu orçamento ou [outro exemplo].
- Assistente **do Azure** Saber quais são as coisas que os custos são apenas metade da batalha; a outra metade é saber o que fazer com essas informações. O assistente [do Azure](https://docs.microsoft.com/azure/advisor/advisor-overview) fornece recomendações sobre as ações a serem tomadas para economizar dinheiro, melhorar a confiabilidade ou até mesmo aumentar a segurança.

### <a name="external-cost-management-tools"></a>Ferramentas de gerenciamento de custo externo

- **Power BI Azure consumption insights:** Deseja criar suas próprias visualizações para sua organização? Nesse caso, o pacote de conteúdo do Azure Consumption Insights para Power BI é sua ferramenta de escolha. Usando este pacote de conteúdo e Power BI você pode criar visualizações personalizadas para representar sua organização, fazer uma análise mais profunda dos custos e adicionar outras fontes de dados para aprimorar ainda mais.

- **API de consumo:** As [APIs de consumo](/rest/api/consumption) fornecem acesso programático aos dados de custo e de uso, além das informações sobre orçamentos, instâncias reservadas e encargos do Marketplace. Essas APIs são acessíveis somente para registros empresariais e algumas assinaturas do Web Direct, mas oferecem a você a capacidade de integrar seus dados de custo em suas próprias ferramentas e data warehouses. Você também pode [acessar essas APIs por meio do CLI do Azure](/cli/azure/consumption?view=azure-cli-latest).

Os clientes que são usuários de nuvem de longo prazo e maduram seguem determinadas práticas recomendadas:

- **Monitore os custos ativamente.** As organizações que são maduras os usuários do Azure monitoram constantemente os custos e tomam ações quando necessário. Algumas organizações dedicam as pessoas a fazer análises e sugerem alterações no uso, e essas pessoas têm mais do que pagar pela primeira vez que localizam um cluster HDInsight não utilizado que está sendo executado por meses.
- **Use instâncias de VM reservadas.** Outra filosofia importante para gerenciar os custos na nuvem é usar a ferramenta certa para o trabalho. Se você tiver uma VM IaaS que deve permanecer em 24x7, usar uma instância de VM reservada economizará dinheiro significativo. Encontrar o equilíbrio certo entre automatizar o desligamento de VMs e usar instâncias de VM reservadas usa a experiência e a análise.
- **Use a automação com eficiência.** Muitas cargas de trabalho não precisam ser executadas todos os dias. A desativação de uma VM por um período de quatro horas todos os dias pode poupar 15% do seu custo. A automação pagará por si própria rapidamente.
- **Use marcas de recurso para obter visibilidade.** Como mencionado em outro lugar neste documento, o uso de marcas de recurso permitirá uma melhor análise dos custos.

O gerenciamento de custos é uma disciplina que é fundamental para a execução eficaz e eficiente de uma nuvem pública. As empresas que obtêm êxito podem controlar seus custos e corresponderem à demanda real, em vez de comprar e esperar que a demanda venha.

## <a name="automate"></a>Automatizar

Um dos muitos recursos que diferencia a maturidade das organizações que usam provedores de nuvem é o nível de automação que eles incorporaram. A automação é um processo que nunca termina e, à medida que sua organização se move para a nuvem, é qualquer área de que você precise investir em recursos e tempo na criação. A automação atende a vários propósitos, incluindo a distribuição consistente de recursos (em que ele se vincula diretamente a outro conceito de Scaffold principal, modelos e DevOps) à correção de problemas. A automação é a "tecido de conexão" do Scaffold do Azure e vincula cada área ao mesmo tempo.

Várias ferramentas podem ajudá-lo a criar esse recurso, desde ferramentas de terceiros, como a automação do Azure, a grade de eventos e a CLI do Azure, até um número abrangente de ferramentas de terceiros, como Terraform, Jenkins, chefe e Puppet. As principais ferramentas de automação incluem a automação do Azure, a grade de eventos e a Azure Cloud Shell.

- **Automação do Azure** O é um recurso baseado em nuvem que permite que você crie runbooks (tanto no PowerShell quanto no Python) e permite automatizar processos, configurar recursos e até mesmo aplicar patches. A [automação do Azure](https://docs.microsoft.com/azure/automation/automation-intro) tem um amplo conjunto de recursos de plataforma cruzada que são integrantes à sua implantação, mas são muito abrangentes para serem abordados em detalhes aqui.
- A **grade de eventos** é um sistema de roteamento de eventos totalmente gerenciado que permite reagir a eventos no ambiente do Azure. Assim como a automação do Azure é a tecido de conexão das organizações de nuvem maduras, a [grade de eventos](https://docs.microsoft.com/azure/event-grid) é a tecido de conexão de boa automação. Usando a grade de eventos, você pode criar uma ação simples sem servidor para enviar um email a um administrador sempre que um novo recurso é criado e registrar esse recurso em um banco de dados. Essa mesma grade de eventos pode notificar quando um recurso é excluído e remover o item do banco de dados.
- **Azure cloud Shell** é um [shell](https://docs.microsoft.com/azure/cloud-shell/overview) interativo baseado em navegador para gerenciar recursos no Azure. Ele fornece um ambiente completo para o PowerShell ou bash que é iniciado conforme necessário (e mantido para você) para que você tenha um ambiente consistente do qual executar seus scripts. O Azure Cloud Shell fornece acesso a ferramentas-chave adicionais – já instaladas – para automatizar seu ambiente, incluindo [CLI do Azure](/cli/azure/get-started-with-azure-cli?view=azure-cli-latest), [Terraform](https://docs.microsoft.com/azure/virtual-machines/linux/terraform-install-configure) e uma lista crescente de [ferramentas](https://azure.microsoft.com/updates/cloud-shell-new-cli-tools-and-font-size-selection) adicionais para gerenciar contêineres, bancos de dados (sqlcmd) e cada.

A automação é um trabalho em tempo integral e rapidamente se tornará uma das tarefas operacionais mais importantes em sua equipe de nuvem. As organizações que usam a abordagem "automatizar primeiro" têm maior sucesso no uso do Azure:

- **Gerenciando custos:** Buscando ativamente oportunidades e criando automação para redimensionar recursos, escalar ou reduzir verticalmente e desativar recursos não utilizados.
- **Flexibilidade operacional:** Com a automação (juntamente com modelos e DevOps), você tem um nível de repetição que aumenta a disponibilidade, aumenta a segurança e permite que sua equipe se concentre na solução de problemas de negócios.

## <a name="templates-and-devops"></a>Modelos e DevOps

Conforme destacado na seção automatizar, seu objetivo como uma organização deve ser provisionar recursos por meio de modelos e scripts controlados por origem e minimizar a configuração interativa de seus ambientes. Essa abordagem de "infraestrutura como código", juntamente com um processo de DevOps disciplinado para implantação contínua, pode garantir a consistência e reduzir a descompasso entre seus ambientes. Quase todos os recursos do Azure são implantáveis por meio de [modelos de JSON Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-template-deploy) em conjunto com o PowerShell ou a CLI de plataforma cruzada do Azure e ferramentas como Terraform de Hashicorp (que tem suporte de primeira classe e integrado ao Azure Cloud Shell).

O artigo como [as práticas recomendadas para usar modelos de Azure Resource Manager](https://blogs.msdn.microsoft.com/mvpawardprogram/2018/05/01/azure-resource-manager) fornece uma excelente discussão sobre as práticas recomendadas e as lições aprendidas para aplicar uma abordagem de DevOps a modelos de Azure Resource Manager com o [Azure DevOps](https://docs.microsoft.com/azure/devops/user-guide/?view=vsts) ferramentas . Reserve tempo e esforço para desenvolver um conjunto principal de modelos específicos para os requisitos da sua organização e para desenvolver pipelines de entrega contínua com DevOps cadeias (como Azure DevOps, Jenkins, bambu, TeamCity e concurso), especialmente para seu ambientes de produção e de QA. Há uma grande biblioteca de [modelos de início rápido do Azure](https://github.com/Azure/azure-quickstart-templates) no GitHub que você pode usar como ponto de partida para modelos, e você pode criar rapidamente pipelines de entrega baseados em nuvem com o Azure DevOps.

Como prática recomendada para assinaturas de produção ou grupos de recursos, sua meta deve usar a segurança RBAC para não permitir usuários interativos por padrão e usar pipelines de entrega contínua automatizados com base em entidades de serviço para provisionar todos os recursos e Entregue todo o código do aplicativo. Nenhum administrador ou desenvolvedor deve tocar no portal do Azure para configurar os recursos interativamente. Esse nível de DevOps leva um esforço em conjunto e usa todos os conceitos da Scaffold do Azure, fornecendo um ambiente consistente e mais seguro que atenderá às necessidades da sua organização em escala.

> [!TIP]
> Ao criar e desenvolver modelos de Azure Resource Manager complexos, use [modelos vinculados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-linked-templates) para organizar e refatorar relações de recursos complexos de arquivos JSON monolíticos. Isso permitirá que você gerencie recursos individualmente e torne seus modelos mais legíveis, que podem ser testados e reutilizáveis.

O Azure é um provedor de nuvem de hiperescala. À medida que você move sua organização de servidores locais para a nuvem, contando com os mesmos conceitos que os provedores de nuvem e os aplicativos SaaS usam ajudarão sua organização a reagir às necessidades da empresa de maneira muito mais eficiente.

## <a name="core-network"></a>Rede principal

O componente final do modelo de referência do Azure Scaffold é fundamental para como sua organização acessa o Azure, de maneira segura. O acesso aos recursos pode ser interno (dentro da rede da empresa) ou externo (através da Internet). É fácil para os usuários em sua organização colocar recursos inadvertidamente no local errado e potencialmente abri-los para acesso mal-intencionado. Assim como ocorre com dispositivos locais, as empresas devem adicionar controles apropriados para garantir que os usuários do Azure tomem as decisões certas. Para governança de assinatura, identificamos os principais recursos que fornecem controle básico do acesso. Os principais recursos consistem em:

- **Redes virtuais** são objetos de contêiner para sub-redes. Embora não seja estritamente necessário, geralmente é usado ao conectar aplicativos a recursos corporativos internos.
- As **rotas definidas pelo usuário** permitem que você manipule a tabela de rotas em uma sub-rede, permitindo que você envie tráfego por meio de uma solução de virtualização de rede ou para um gateway remoto em uma rede virtual emparelhada.
- O **emparelhamento de rede virtual** permite que você conecte diretamente duas ou mais redes virtuais do Azure, criando designs de Hub e spoke mais complexos ou redes de serviços compartilhados.
- **Pontos de extremidade de serviço.** No passado, os serviços de PaaS contavam com métodos diferentes para proteger o acesso a esses recursos de suas redes virtuais. Os pontos de extremidade de serviço permitem proteger o acesso aos serviços PaaS habilitados **somente** a partir de pontos de extremidade conectados, aumentando a segurança geral.
- Os **grupos de segurança** são um amplo conjunto de regras que fornecem a capacidade de permitir ou negar o tráfego de entrada e saída de/para recursos do Azure. [Grupos de segurança](https://docs.microsoft.com/azure/virtual-network/security-overview) consistem em regras de segurança que podem ser aumentadas com **marcas de serviço** (que definem serviços comuns do Azure, como Azure Key Vault ou banco de dados SQL do Azure) e grupos de **segurança de aplicativo** (que definem e o aplicativo estrutura, como servidores Web ou servidores de aplicativos.

> [!TIP]
> Use marcas de serviço e grupos de segurança de aplicativo em seus grupos de segurança de rede não apenas para melhorar a legibilidade das suas regras &mdash;which é crucial para entender o impacto &mdash;but também para habilitar o microsegmentação efetivo em uma sub-rede maior, reduzir a proliferação e aumentar a flexibilidade.

### <a name="azure-virtual-datacenter"></a>Datacenter virtual do Azure

O Azure fornece recursos internos e recursos de terceiros de nossa ampla rede de parceiros que permitem que você tenha uma postura de segurança eficaz. Mais importante, a Microsoft fornece as práticas recomendadas e orientações na forma de [VDC (datacenter virtual) do Azure](./networking-vdc.md). À medida que você passa de uma única carga de trabalho para várias cargas de trabalho que usam recursos híbridos, as diretrizes de VDC fornecerão "receitas" para permitir uma rede flexível e que aumentará à medida que suas cargas de trabalho no Azure crescem.

## <a name="next-steps"></a>Próximos passos

A governança é crucial para o sucesso do Azure. Este artigo destina-se à implementação técnica de um Scaffold empresarial, mas só aborda o processo e as relações mais amplas entre os componentes. O controle de política flui de cima para baixo e é determinado pelo que a empresa deseja alcançar. Naturalmente, a criação de um modelo de governança para o Azure inclui representantes de ti, mas, mais importante, ele deve ter uma forte representação de líderes de grupos de negócios e gerenciamento de segurança e riscos. No final das empresas, uma Scaffold empresarial está prestes a reduzir os riscos de negócios para facilitar a missão e os objetivos de uma organização.

Agora que você aprendeu sobre governança de assinatura, é hora de ver essas recomendações na prática. Veja [Exemplos de implementação da governança de assinatura do Azure](./azure-scaffold-examples.md).
