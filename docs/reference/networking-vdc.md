---
title: 'Data centers virtuais: uma perspectiva de rede'
description: Saiba como criar um datacenter virtual no Azure.
author: tracsman
ms.author: jonor
ms.date: 06/12/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
manager: rossort
tags: azure-resource-manager
ms.custom: virtual-network
ms.openlocfilehash: e5729e592fe0e602d24e2e37831c782fada73128
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566697"
---
# <a name="virtual-datacenters-a-network-perspective"></a>Data centers virtuais: uma perspectiva de rede

## <a name="overview"></a>Visão geral

A migração de aplicativos locais para o Azure fornece às organizações os benefícios de uma infraestrutura segura e econômica, mesmo se os aplicativos forem migrados com o mínimo de alterações. No entanto, para aproveitar ao máximo a agilidade com a computação em nuvem, as empresas precisam evoluir suas arquiteturas para aproveitarem os recursos do Azure.

A Microsoft Azure fornece serviços e infraestrutura de hiperescala com recursos e confiabilidade de nível empresarial. Esses serviços e infraestrutura oferecem muitas opções de conectividade híbrida para que os clientes possam escolher acessá-los pela Internet pública ou por uma conexão privada do Azure ExpressRoute. Os parceiros da Microsoft também fornecem recursos avançados, oferecendo serviços de segurança e soluções de virtualização otimizados para execução no Azure.

Os clientes podem optar por acessar esses serviços de nuvem pela Internet ou com o Azure ExpressRoute, que fornece conectividade de rede privada. Com a plataforma Microsoft Azure, os clientes podem estender diretamente sua infraestrutura para a nuvem e criar arquiteturas de várias camadas. Os parceiros da Microsoft também fornecem recursos avançados, oferecendo serviços de segurança e soluções de virtualização otimizados para execução no Azure.

<!-- markdownlint-disable MD026 -->

## <a name="what-is-the-virtual-datacenter"></a>O que é o datacenter virtual?

No início, a nuvem era, essencialmente, uma plataforma de hospedagem de aplicativos voltados ao público. As empresas começaram a entender o valor da nuvem e começaram a mover aplicativos de linha de negócios internos para ela. Esses tipos de aplicativo trouxeram mais segurança, confiabilidade, desempenho e considerações de custo que exigiam maior flexibilidade na forma de prestar os serviços de nuvem. Isso abriu caminho para novos serviços de rede e infraestrutura criados para dar essa flexibilidade, mas também para novos recursos de escala, recuperação de desastre e outras questões.

As soluções de nuvem eram projetadas para hospedar aplicativos únicos relativamente isolados no espectro público. Essa abordagem funcionou bem por alguns anos. Depois, os benefícios das soluções de nuvem tornaram-se evidentes, e cargas de trabalho em grande escala passaram a ser hospedadas na nuvem. Abordar a segurança, a confiabilidade, o desempenho e as preocupações de custos das implantações em uma ou mais regiões se tornou vital durante todo o ciclo de vida do serviço de nuvem.

O diagrama de implantação em nuvem a seguir mostra um exemplo de uma lacuna de segurança, realçada na caixa vermelha. A caixa amarela mostra espaço para otimizar dispositivos de rede virtual entre cargas de trabalho.

![0][0]

Um datacenter virtual é um conceito de uma necessidade de dimensionamento para dar suporte a cargas de trabalho corporativas, equilibrando a necessidade de lidar com os problemas introduzidos ao dar suporte a aplicativos em larga escala na nuvem pública.

Uma implementação de datacenter virtual não representa apenas as cargas de trabalho do aplicativo na nuvem, mas também a rede, segurança, gerenciamento e infraestrutura (por exemplo, DNS e serviços de diretório). À medida que mais e mais das cargas de trabalho de uma empresa se movem para o Azure, é importante pensar na infraestrutura de suporte e nos objetos em que essas cargas de trabalho são colocadas. Pensar cuidadosamente em como os recursos são estruturados pode evitar a proliferação de centenas de "ilhas de carga de trabalho" que devem ser gerenciadas separadamente com o fluxo de dados, modelos de segurança e desafios de conformidade independentes.

O conceito de datacenter virtual é um conjunto de recomendações e práticas recomendadas para implementar uma coleção de entidades separadas, mas relacionadas, com funções de suporte, recursos e infraestrutura comuns. Ao exibir suas cargas de trabalho por meio da lente de um datacenter virtual, você pode perceber um custo reduzido devido a economias de escala, segurança otimizada por meio da centralização de componentes e de fluxo de dados, juntamente com as auditorias mais fáceis, de gerenciamento e de conformidade.

> [!NOTE]
> É importante entender que um datacenter virtual **não** é um produto discreto do Azure, mas a combinação de vários recursos e recursos para atender aos seus requisitos exatos. Um datacenter virtual é uma maneira de pensar sobre suas cargas de trabalho e o uso do Azure para maximizar seus recursos e capacidades na nuvem. É uma abordagem modular de criação de serviços de TI no Azure que, ao mesmo tempo, respeita as funções organizacionais e as responsabilidades da empresa.

Uma implementação de datacenter virtual pode ajudar as empresas a obter cargas de trabalho e aplicativos no Azure para os seguintes cenários:

- Hospedagem de várias cargas de trabalho relacionadas.
- Migração de cargas de trabalho de um ambiente local para o Azure.
- Implementação de segurança compartilhada ou centralizada e requisitos de acesso entre cargas de trabalho.
- Como combinar TI centralizada e DevOps apropriadamente para uma grande empresa.

A chave para desbloquear as vantagens de um datacenter virtual é uma topologia de rede hub e spoke centralizada com uma combinação de serviços e recursos do Azure:

- [Rede virtual do Azure][VNet],
- [Grupos de segurança de rede][network-security-groups],
- [Emparelhamento de rede virtual][VNetPeering],
- [Rotas definidas pelo usuário][user-defined-routes]e
- Identidade do Azure com [RBAC (controle de acesso baseado em função)][RBAC] e, opcionalmente, o [Firewall do Azure][AzFW], o [DNS do Azure][DNS], a [porta frontal do][AFD]Azure e a [Wan virtual do Azure][vWAN].

## <a name="who-should-implement-a-virtual-datacenter"></a>Quem deve implementar um datacenter virtual?

Qualquer cliente do Azure que tenha decidido adotar a nuvem pode se beneficiar da eficiência de configurar um conjunto de recursos para uso comum por todos os aplicativos. Dependendo da magnitude, até mesmo os aplicativos únicos podem se beneficiar do uso dos padrões e componentes usados para criar uma implementação de datacenter virtual.

Se sua organização tiver equipes ou departamentos centralizados para ti, rede, segurança ou conformidade, implementar um datacenter virtual pode ajudar a impor pontos de política, diferenciação de imposto e garantir a uniformidade dos componentes comuns subjacentes, oferecendo as equipes de aplicativos são de grande liberdade e controle conforme apropriado para suas necessidades.

As organizações que procuram DevOps também podem usar os conceitos de datacenter virtual para fornecer bolsos autorizadas de recursos do Azure e garantir que eles tenham controle total dentro desse grupo (assinatura ou grupo de recursos em uma assinatura comum), mas o os limites de rede e de segurança permanecem em conformidade, conforme definido por uma política centralizada em um grupo de recursos e VNet de Hub.

<!-- markdownlint-enable MD026 -->

## <a name="considerations-for-implementing-a-virtual-datacenter"></a>Considerações sobre a implementação de um datacenter virtual

Ao projetar uma implementação de datacenter virtual, há várias questões dinâmicas a serem consideradas:

### <a name="identity-and-directory-service"></a>Identidade e serviço de diretório

Serviços de identidade e diretório são um aspecto fundamental de todos os datacenters, sejam locais ou na nuvem. A identidade está relacionada a todos os aspectos de acesso e autorização aos serviços em uma implementação de datacenter virtual. Para ajudar a garantir que somente usuários e processos autorizados acessem seus recursos e Conta do Azure, o Azure usa vários tipos de credenciais para autenticação. Eles incluem senhas (para acessar a conta do Azure), chaves de criptografia, assinaturas digitais e certificados. A [autenticação multifator do Azure][multi-factor-authentication] é uma camada adicional de segurança para acessar os serviços do Azure. A autenticação multifator fornece uma autenticação forte com uma variedade de opções de verificação fáceis (chamada telefônica, mensagem de texto ou notificação de aplicativo móvel) e permite que os clientes escolham o método de preferência.

Qualquer empresa de grande porte precisa definir um processo de gerenciamento de identidade que descreve o gerenciamento de identidades individuais, sua autenticação, autorização, funções e privilégios dentro ou entre suas implementações de datacenter virtual. Os objetivos deste processo devem ser aumentar a segurança e a produtividade e diminuir o custo, o tempo de inatividade e as tarefas manuais repetitivas.

As organizações empresariais podem exigir uma combinação exigente de serviços para diferentes linhas de negócios, e os funcionários geralmente têm funções diferentes quando envolvidas em projetos diferentes. Um datacenter virtual requer boa cooperação entre diferentes equipes, cada uma com definições de função específicas, para obter sistemas em execução com bom controle. A matriz de responsabilidades, acesso e direitos pode ser complexa. O gerenciamento de identidades em um datacenter virtual é implementado por meio [do Azure Active Directory (AD do Azure) e do][azure-ad] RBAC (controle de acesso baseado em função).

Um serviço de diretório é uma infraestrutura de informações compartilhadas que localiza, gerencia, administra e organiza itens cotidianos e recursos de rede. Esses recursos podem incluir volumes, pastas, arquivos, impressoras, usuários, grupos, dispositivos e outros objetos. Cada recurso na rede é considerado um objeto pelo servidor de diretório. Informações sobre um recurso são armazenadas como uma coleção de atributos associados a tal recurso ou objeto.

Todos os serviços comerciais do Microsoft Online dependem do Azure Active Directory (Azure AD) para entrada e outras necessidades de identidade. O Azure Active Directory é uma solução de nuvem de gerenciamento de acesso e identidade abrangente e altamente disponível que combina os serviços principais de diretório, governança avançada de identidades e gerenciamento do acesso de aplicativos. O Azure AD pode ser integrado ao Active Directory local para habilitar o logon único para todos os aplicativos hospedados localmente e baseados em nuvem (local). Os atributos do usuário do Active Directory local podem ser sincronizados automaticamente com o Azure AD.

Um único administrador global não é necessário para atribuir todas as permissões em uma implementação de datacenter virtual. Em vez disso, cada departamento específico, grupo de usuários ou serviços no serviço de diretório pode ter as permissões necessárias para gerenciar seus próprios recursos em uma implementação de datacenter virtual. Estruturar permissões requer balanceamento. Um número excessivo de permissões pode prejudicar a eficiência de desempenho, enquanto permissões de menos ou não exigentes podem aumentar os riscos de segurança. O RBAC (controle de acesso baseado em função) do Azure ajuda a resolver esse problema, oferecendo gerenciamento de acesso refinado para recursos em uma implementação de datacenter virtual.

#### <a name="security-infrastructure"></a>Infraestrutura de segurança

A infraestrutura de segurança refere-se à diferenciação de tráfego em um segmento de rede virtual específico da implementação do datacenter virtual. Essa infraestrutura especifica como a entrada e a saída são controladas em uma implementação de datacenter virtual. O Azure é baseado em uma arquitetura multilocatário que impede tráfego não autorizado e não intencional entre implantações usando isolamento de VNet, ACLs (listas de controle de acesso), balanceadores de carga, filtros de IP e políticas de fluxo de tráfego. NAT (conversão de endereços de rede) separa o tráfego de rede interno do tráfego externo.

A malha do Azure aloca recursos de infraestrutura a cargas de trabalho de locatário e gerencia comunicações para e de VMs (máquinas virtuais). O hipervisor do Azure impõe a separação de memória e processo entre VMs e encaminha com segurança o tráfego de rede a locatários do sistema operacional convidado.

#### <a name="connectivity-to-the-cloud"></a>Conectividade com a nuvem

Uma implementação de datacenter virtual exige conectividade com redes externas para oferecer serviços a clientes, parceiros e usuários internos. Essa necessidade de conectividade diz respeito não só à Internet, mas também a datacenters e redes locais.

Os clientes controlam quais serviços têm acesso e podem ser acessados pela Internet pública usando o [Firewall do Azure][AzFW] ou outros tipos de NVAs (dispositivos de rede virtual), políticas de roteamento personalizadas usando [rotas definidas pelo usuário][user-defined-routes]e rede filtragem usando [grupos de segurança de rede][network-security-groups]. Recomendamos que todos os recursos da Internet também sejam protegidos pelo [padrão de proteção contra DDoS do Azure][DDoS].

As empresas podem precisar conectar sua implementação de datacenter virtual a datacenters locais ou outros recursos. Essa conectividade entre o Azure e as redes locais é um aspecto essencial de um projeto de arquitetura eficaz. As empresas têm duas maneiras diferentes de criar essa interconexão: trânsito pela Internet ou por meio de conexões diretas privadas.

Uma [**VPN site a site do Azure**][VPN] é um serviço de interconexão pela Internet entre redes locais e uma implementação de datacenter virtual, estabelecida por meio de conexões criptografadas seguras (túneis IPsec/Ike). A conexão Site a Site do Azure é flexível e rápida de criar e não requer nenhuma compra adicional, uma vez que todas as conexões são feitas pela Internet.

Para um grande número de conexões VPN, a [**Wan virtual do Azure**][vWAN] é um serviço de rede que fornece conectividade de Branch para Branch automatizada e otimizada por meio do Azure. A WAN virtual permite que você se conecte para configurar dispositivos de ramificação para se comunicar com o Azure. A conexão e a configuração podem ser feitas manualmente ou usando os dispositivos de provedor preferidos por meio de um parceiro de WAN Virtual. O uso dos dispositivos de provedor preferidos facilitam o uso, simplificam a conectividade e permitem o gerenciamento da configuração. O painel interno de WAN do Azure fornece informações instantâneas de solução de problemas que podem ajudar você a economizar tempo e proporcionam uma maneira fácil de exibir conectividade site a site em larga escala.

O [**ExpressRoute**][ExR] é um serviço de conectividade do Azure que permite conexões privadas entre uma implementação de datacenter virtual e qualquer rede local. Conexões do ExpressRoute não passam pela Internet pública e oferecem maior segurança, confiabilidade e velocidades mais altas (até 10 Gbps), além de latência consistente. O ExpressRoute é útil para implementações de datacenter virtual, pois os clientes do ExpressRoute podem obter os benefícios das regras de conformidade associadas a conexões privadas. Com o [ExpressRoute Direct][ExRD], você pode se conectar diretamente aos roteadores da Microsoft a 100 Gbps para clientes com necessidades maiores de largura de banda.

Implantar conexões do ExpressRoute envolve normalmente a interação com um provedor de serviços do ExpressRoute. Para clientes que precisam iniciar rapidamente, é comum usar inicialmente a VPN site a site para estabelecer a conectividade entre uma implementação de datacenter virtual e recursos locais e, em seguida, migrar para a conexão do ExpressRoute quando o seu físico a interconexão com o provedor de serviços foi concluída.

#### <a name="connectivity-within-the-cloud"></a>*Conectividade na nuvem*

O emparelhamento [VNets][VNet] e [VNet][VNetPeering] são os serviços de conectividade de rede básicos dentro de uma implementação de datacenter virtual. Uma VNet garante um limite natural de isolamento para recursos de datacenter virtual, e o emparelhamento VNet permite a intercomunicação entre diferentes VNets na mesma região do Azure ou até mesmo entre regiões. O controle de tráfego dentro de uma VNet e entre VNets precisa corresponder a um conjunto de regras de segurança especificado por meio de listas de controle de acesso ([grupos de segurança de rede][network-security-groups]), dispositivos de [virtualização de rede][NVA]e tabelas de roteamento personalizadas ([rotas definidas pelo usuário][user-defined-routes]).

## <a name="virtual-datacenter-overview"></a>Visão geral do datacenter virtual

### <a name="topology"></a>Topologia

O *Hub-spoke* é um modelo para projetar a topologia de rede para uma implementação do Datacenter Virtual.

![1][1]

Como mostrado, dois tipos de design de Hub e spoke podem ser usados no Azure. Para comunicação, recursos compartilhados e a política de segurança centralizada (Hub de VNet no diagrama) ou um tipo de WAN virtual (WAN virtual no diagrama) para comunicações de Branch para Branch e Branch para o Azure de grande escala.

Um hub é a zona central da rede que controla e inspeciona o tráfego de entrada ou saída entre diferentes zonas: Internet, local e os spokes. A topologia hub-spoke dá ao departamento de TI uma maneira eficiente de impor políticas de segurança em um local central. Ela também reduz a possibilidade de erros de configuração e exposição.

O Hub geralmente contém os componentes de serviço comuns consumidos pelos spokes. Os exemplos a seguir são serviços centrais comuns:

- A infraestrutura do Windows Active Directory, necessária para a autenticação de usuários de terceiros que acessam de redes não confiáveis antes de obterem acesso às cargas de trabalho no spoke. Ela inclui os Serviços de Federação do Active Directory (AD FS).
- Um serviço DNS para resolver nomes para a carga de trabalho nos spokes, para acessar recursos locais e na Internet se o [DNS do Azure][DNS] não for usado.
- Uma infraestrutura de chave pública (PKI) para implementar logon único em cargas de trabalho.
- Controle de fluxo de tráfego TCP e UDP entre as zonas da rede de spoke e a Internet.
- Controle de fluxo entre os spokes e o local.
- Se necessário, fluxo de controle entre um spoke e outro.

O datacenter virtual reduz o custo geral usando a infraestrutura de Hub compartilhada entre vários spokes.

A função de cada spoke pode ser hospedar diferentes tipos de cargas de trabalho. Os spokes também fornecem uma abordagem modular para implantações repetíveis das mesmas cargas de trabalho. Alguns exemplos são: desenvolvimento e teste, testes de aceitação do usuário, pré-produção e produção. Os spokes também podem separar e habilitar diferentes grupos na sua organização. Um exemplo são os grupos Azure DevOps. Dentro de um spoke, é possível implantar uma carga de trabalho básica ou cargas de trabalho complexas de várias camadas com controle de tráfego entre as camadas.

#### <a name="subscription-limits-and-multiple-hubs"></a>Limites de assinatura e vários hubs

No Azure, cada componente, seja qual for o tipo, é implantado em uma Assinatura do Azure. O isolamento dos componentes do Azure em diferentes assinaturas do Azure pode atender aos requisitos de diferentes LOBs, como configurar níveis diferenciados de acesso e autorização.

Uma única implementação de datacenter virtual pode escalar verticalmente para um grande número de spokes, embora, assim como acontece com todos os sistemas de ti, há limites de plataforma. A implantação de Hub está associada a uma assinatura específica do Azure, que tem restrições e limites (por exemplo, um número máximo de emparelhamentos de VNet; consulte [assinatura do Azure e limites de serviço, cotas e restrições][limits] para obter detalhes). Em casos em que os limites possam ser um problema, a arquitetura pode ser escalada verticalmente ainda mais estendendo o modelo de um único hub-spokes para um cluster de hub e spokes. Vários hubs em uma ou mais regiões do Azure podem ser interconectados usando Emparelhamento VNET, ExpressRoute, WAN Virtual ou VPN site a site.

![2][2]

A introdução de vários hubs aumenta o esforço de gerenciamento e o custo do sistema. Ela só seria justificada por escalabilidade, limites do sistema ou redundância e replicação regional para desempenho do usuário final ou recuperação de desastre. Em cenários que exigem vários hubs, todos os hubs devem buscar oferecer o mesmo conjunto de serviços para facilidade operacional.

#### <a name="interconnection-between-spokes"></a>Interconexão entre spokes

Dentro de um único spoke, é possível implementar cargas de trabalho complexas de várias camadas. As configurações de várias camadas podem ser implementadas usando sub-redes (uma para cada camada) na mesma VNet e filtrando os fluxos usando grupos de segurança de rede.

Um arquiteto talvez queira implantar uma carga de trabalho de várias camadas em várias redes virtuais. Com um emparelhamento de redes virtuais, os spokes podem se conectar a outros spokes no mesmo hub ou em hubs diferentes. Um exemplo típico desse cenário é o caso em que os servidores de processamento do aplicativo estão em um spoke ou rede virtual. O banco de dados é implantado em um spoke ou em uma rede virtual diferente. Nesse caso, é fácil interconectar os spokes ao emparelhamento de redes virtuais e, assim, evitar trânsito pelo hub. Uma arquitetura cuidadosa e uma revisão de segurança devem ser realizadas para garantir que ignorar o Hub não ignore pontos de segurança ou de auditoria importantes que possam existir apenas no Hub.

![3][3]

Os spokes também podem ser interconectados a um spoke que atue como um hub. Essa abordagem cria uma hierarquia de dois níveis: o spoke no nível mais alto (nível 0) torna-se o hub dos spokes inferiores (nível 1) da hierarquia. Os spokes de uma implementação de datacenter virtual são necessários para encaminhar o tráfego para o hub central, de forma que o tráfego possa transitar para seu destino na rede local ou na Internet pública. Uma arquitetura com dois níveis de hubs apresenta um roteamento complexo que remove os benefícios de uma relação hub-spoke simples.

Embora o Azure permita topologias complexas, um dos principais princípios do conceito de datacenter virtual é a capacidade de repetição e simplicidade. Para minimizar o esforço de gerenciamento, o design hub-spoke simples é a arquitetura de referência do datacenter virtual que recomendamos.

### <a name="components"></a>Componentes

Um datacenter virtual é composto de quatro tipos de componentes básicos: **infraestrutura**, **redes de perímetro**, **cargas de trabalho**e **monitoramento**.

Cada tipo de componente consiste em vários recursos e funcionalidades do Azure. Sua implementação de datacenter virtual é composta de instâncias de vários tipos de componentes e várias variações do mesmo tipo de componente. Por exemplo, você pode ter muitas instâncias de carga de trabalho diferentes e logicamente separadas que representem diferentes aplicativos. Você usa esses diferentes tipos de componentes e instâncias para, por fim, criar um datacenter virtual.

![4][4]

A arquitetura conceitual de alto nível anterior de um datacenter virtual mostra tipos de componentes diferentes usados em diferentes zonas da topologia hub-spokes. O diagrama mostra os componentes da infraestrutura em várias partes da arquitetura.

Como boa prática em geral, os privilégios e direitos de acesso devem se basear nos grupos. Lidar com grupos em vez de usuários individuais facilita a manutenção de políticas de acesso, fornecendo uma maneira consistente de gerenciá-la entre equipes e ajuda na minimização de erros de configuração. Atribuir e remover usuários de e para grupos apropriados ajuda a manter os privilégios de um usuário específico atualizados.

Cada grupo de função deve ter um prefixo exclusivo em seus nomes. Esse prefixo torna mais fácil identificar qual grupo está associado a qual carga de trabalho. Por exemplo, uma carga de trabalho que hospede um serviço de autenticação pode ter grupos chamados **AuthServiceNetOps**, **AuthServiceSecOps**, **AuthServiceDevOps** e **AuthServiceInfraOps**. Funções centralizadas, ou funções não relacionadas a um serviço específico, podem ser precedidas por **Corp**. Um exemplo é **CorpNetOps**.

Muitas organizações usam uma variação dos seguintes grupos para fornecer uma divisão importante de funções:

- O grupo de TI central **Corp** tem os direitos de propriedade para controlar os componentes de infraestrutura. Exemplos de rede e segurança. O grupo deve ter a função de colaborador na assinatura, o controle do hub e direitos de colaborador de rede nos spokes. Organizações de grande porte dividem com frequência essas responsabilidades de gerenciamento entre várias equipes. Por exemplo, o grupo **CorpNetOps** de operações de rede com foco exclusivo na rede e o grupo **CorpSecOps** de operações de segurança, responsável pela política de firewall e segurança. Nesse caso específico, os dois grupos diferentes precisam ser criados para a atribuição dessas funções personalizadas.
- O grupo de desenvolvimento e teste **AppDevOps** tem a responsabilidade de implantar cargas de trabalho de aplicativos ou serviços. Esse grupo usa a função de colaborador de máquina virtual para implantações de IaaS ou uma ou mais funções de colaborador de PaaS. Consulte [funções internas para recursos do Azure][Roles]. Opcionalmente, a equipe de desenvolvimento/teste pode precisar de visibilidade das políticas de segurança (grupos de segurança de rede) e das políticas de roteamento (rotas definidas pelo usuário) dentro do Hub ou de um spoke específico. Além das funções de colaborador para cargas de trabalho, esse grupo também precisaria da função de leitor de rede.
- O grupo de operação e manutenção, **CorpInfraOps** ou **AppInfraOps,** tem a responsabilidade de gerenciar cargas de trabalho em produção. Esse grupo deve ser um colaborador de assinatura em cargas de trabalho em qualquer assinatura de produção. Algumas organizações também podem avaliar se elas precisam de um grupo de equipe de suporte de escalonamento adicional com a função de colaborador de assinatura em produção e na assinatura do hub central. O grupo adicional corrige possíveis problemas de configuração no ambiente de produção.

Um datacenter virtual é projetado para que os grupos criados para o grupo central de ti, gerenciando o Hub, tenham grupos correspondentes no nível de carga de trabalho. Em vez de apenas gerenciar os recursos de hub, o grupo de TI central é capaz de controlar o acesso externo e as permissões de nível superior na assinatura. Os grupos de cargas de trabalho também são capazes de controlar os recursos e as permissões de sua VNet independentemente da ti central.

Um datacenter virtual é particionado para hospedar com segurança vários projetos em diferentes linhas de negócios. Todos os projetos exigem diferentes ambientes isolados (Dev, UAT, produção). Assinaturas separadas do Azure para cada um desses ambientes fornecem isolamento natural.

![5][5]

O diagrama anterior mostra a relação entre projetos, usuários e grupos, bem como os ambientes de uma organização em que os componentes do Azure são implantados.

Normalmente, em TI, um ambiente (ou camada) é um sistema em que vários aplicativos são implantados e executados. Grandes empresas usam um ambiente de desenvolvimento (onde as alterações são feitas e testadas) e um ambiente de produção (o que os usuários finais usam). Esses ambientes são separados, geralmente com vários ambientes de preparo entre eles para permitir implantação em fases (distribuição), testes e reversão em caso de problemas. As arquiteturas de implantação variam significativamente, mas geralmente o processo básico de iniciar em desenvolvimento (DEV) e terminar em produção (PROD) ainda é seguido.

Uma arquitetura comum para esses tipos de ambientes de várias camadas consiste em DevOps do Azure para desenvolvimento e teste, UAT para ambientes de preparo e produção. As organizações podem aproveitar locatários do Azure AD únicos ou múltiplos para definir o acesso e os direitos para esses ambientes. O diagrama anterior mostra um caso em que dois locatários do Azure AD diferentes são usados: um para Azure DevOps e UAT e outro exclusivamente para produção.

A presença de diferentes locatários do Azure AD impõe a separação entre ambientes. O mesmo grupo de usuários, como a TI central, precisa autenticar usando um URI diferente para acessar um locatário diferente do Azure AD, a fim de modificar as funções ou permissões de ambientes do Azure DevOps ou de produção de um projeto. A presença de diferentes autenticações de usuário para acessar diferentes ambientes reduz possíveis interrupções e outros problemas causados por erros humanos.

#### <a name="component-type-infrastructure"></a>Tipo de componente: infraestrutura

Esse tipo de componente é o local em que a maioria da infraestrutura de suporte reside. Também é o ponto em que as equipes centralizadas de TI, segurança e conformidade passam a maior parte do tempo.

![6][6]

Os componentes de infraestrutura fornecem uma interconexão para os diferentes componentes de uma implementação de datacenter virtual e estão presentes no Hub e nos spokes. Normalmente, a responsabilidade por gerenciar e manter os componentes da infraestrutura é atribuída à equipe de segurança ou TI central.

Uma das principais tarefas da equipe de infraestrutura de TI é assegurar a consistência dos esquemas de endereço IP em toda a empresa. O espaço de endereço IP privado atribuído a uma implementação de datacenter virtual deve ser consistente e não se sobrepondo a endereços IP privados atribuídos em suas redes locais.

Embora NAT nos roteadores de borda locais ou em ambientes do Azure possa evitar conflitos de endereço IP, ele adiciona complicações aos componentes da sua infraestrutura. A simplicidade do gerenciamento é um dos principais objetivos do datacenter virtual, por isso usar o NAT para lidar com questões de IP não é uma solução recomendada.

Os componentes da infraestrutura contêm a seguinte funcionalidade:

- [**Serviços de identidade e diretório**][azure-ad]. Acesso a todos os tipos de recurso no Azure é controlado por uma identidade armazenada em um serviço de diretório. O serviço de diretório armazena não apenas a lista de usuários, mas também os direitos de acesso aos recursos em uma assinatura específica do Azure. Esses serviços podem existir somente em nuvem ou podem ser sincronizados com identidade local armazenada no Active Directory.
- [**Rede virtual**][VPN]. As redes virtuais são um dos principais componentes do datacenter virtual e permitem que você crie um limite de isolamento de tráfego na plataforma do Azure. Uma Rede Virtual é composta por um ou vários segmentos de rede virtual, cada um com um prefixo de rede IP específico (uma sub-rede). A rede Virtual define uma área de perímetro interna em que máquinas virtuais de IaaS e serviços de PaaS podem estabelecer uma comunicação privada. VMs (e serviços de PaaS) em uma rede virtual não podem se comunicar diretamente com VMs (e serviços de PaaS) em uma rede virtual diferente, mesmo se as duas redes virtuais forem criadas pelo mesmo cliente, na mesma assinatura. Isolamento é uma propriedade vital que garante que as VMs e as comunicações do cliente permaneçam privadas em uma rede virtual.
- [**Rotas definidas pelo usuário**][user-defined-routes]. O tráfego em uma rede virtual é roteado por padrão com base na tabela de roteamento do sistema. Uma rota definida pelo usuário é uma tabela de roteamento personalizada que os administradores de rede podem associar a uma ou mais sub-redes para substituir o comportamento da tabela de roteamento do sistema e definir um caminho de comunicação em uma rede virtual. A presença de rotas definidas pelo usuário garante que o tráfego de saída do spoke esteja de trânsito por meio de VMs personalizadas específicas ou soluções de virtualização de rede e balanceadores de carga presentes no Hub e nos spokes.
- [**Grupos de segurança de rede**][network-security-groups]. Um grupo de segurança de rede é uma lista de regras de segurança que atuam como filtragem de tráfego em fontes IP, destinos IP, protocolos, portas de origem IP e portas de destino IP. O grupo de segurança de rede pode ser aplicado a uma sub-rede, uma placa NIC virtual associada a uma VM do Azure ou ambas. Os grupos de segurança de rede são essenciais para implementar um controle de fluxo correto no Hub e nos spokes. O nível de segurança proporcionado pelo grupo de segurança de rede é uma função das portas que você abre e para qual finalidade. Os clientes devem aplicar filtros adicionais por VM com os firewalls baseados em host, como IPtables ou o Firewall do Windows.
- [**DNS**][DNS]. A resolução de nomes de recursos no VNets de uma implementação de datacenter virtual é fornecida por meio do DNS. O Azure fornece serviços DNS para a resolução de nomes [pública][DNS] e [privada][PrivateDNS] . As zonas privadas fornecem resolução de nomes em uma rede virtual e em redes virtuais. É possível ter zonas privadas que abrangem não apenas redes virtuais na mesma região, mas também regiões e assinaturas. Para resolução pública, o DNS do Azure fornece um serviço de hospedagem para domínios DNS, fornecendo resolução de nomes usando a infraestrutura do Microsoft Azure. Ao hospedar seus domínios no Azure, você pode gerenciar seus registros DNS usando as mesmas credenciais, APIs, ferramentas e cobrança que seus outros serviços do Azure.
- Gerenciamento de [**grupo de recursos**][RGMgmt]e [**assinatura**][SubMgmt] . Uma assinatura define um limite natural para criar vários grupos de recursos no Azure. Os recursos em uma assinatura são montados juntos em contêineres lógicos conhecidos como grupos de recursos. O grupo de recursos representa um grupo lógico para organizar os recursos de uma implementação de datacenter virtual.
- [**RBAC**][RBAC]. Por meio de RBAC, é possível mapear a função organizacional junto com direitos de acesso a recursos específicos do Azure, permitindo que você restrinja os usuários a somente um certo subconjunto de ações. Com RBAC, você pode conceder acesso ao atribuir a função apropriada a usuários, grupos e aplicativos no escopo relevante. O escopo de uma atribuição de função pode ser uma assinatura do Azure, um grupo de recursos ou um único recurso. RBAC permite a herança de permissões. Uma função atribuída a um escopo pai também concede acesso aos filhos contidos nele. Usando RBAC, você pode separar as tarefas e conceder aos usuários apenas o nível de acesso de que eles precisam para trabalhar. Por exemplo, use RBAC para permitir que um funcionário gerencie máquinas virtuais em uma assinatura, enquanto outro pode gerenciar bancos de dados SQL na mesma assinatura.
- [**Emparelhamento VNet**][VNetPeering]. O recurso fundamental usado para criar a infraestrutura de um datacenter virtual é o emparelhamento VNet, um mecanismo que conecta duas redes virtuais (VNets) na mesma região por meio da rede de datacenter do Azure ou usando o backbone do Azure World-Wide entre regiões .

#### <a name="component-type-perimeter-networks"></a>Tipo de componente: redes de perímetro

Os componentes de [rede de perímetro][DMZ] permitem a conectividade de rede entre suas redes de datacenters locais ou físicas, juntamente com qualquer conectividade de e para a Internet. Também é o local em que suas equipes de segurança de rede provavelmente passarão a maior parte do tempo.

Os pacotes de entrada devem fluir por dispositivos de segurança no hub antes de alcançar os servidores back-end nos spokes. Alguns exemplos são: firewall, IDS e IPS. Antes de saírem da rede, pacotes limitados à Internet das cargas de trabalho também devem fluir pelos dispositivos de segurança na rede de perímetro. As finalidades deste fluxo são a imposição de políticas, a inspeção e a auditoria.

Os componentes de rede de perímetro fornecem os seguintes recursos:

- [Redes virtuais][VNet], [rotas definidas pelo usuário][user-defined-routes] e [grupos de segurança de rede][network-security-groups]
- [Dispositivos de rede virtual][NVA]
- [Azure Load Balancer][ALB]
- [Aplicativo Azure gateway][AppGW] com o [Firewall do aplicativo Web (WAF)][AppGWWAF]
- [IPs públicos][PIP]
- [Porta frontal do Azure][AFD] com [WAF (firewall do aplicativo Web)][AFDWAF]
- [Firewall do Azure][AzFW]

Normalmente, as equipes de segurança e TI centrais têm a responsabilidade de definir requisitos e a operação das redes de perímetro.

![7][7]

O diagrama anterior mostra a imposição de dois perímetros com acesso à Internet e a uma rede local, ambos residentes no Hub DMZ. No Hub DMZ, a rede de perímetro para a Internet pode escalar verticalmente para dar suporte a um grande número de LOBs, usando vários farms de WAFs (firewalls de aplicativo Web) ou firewalls do Azure. No Hub também permite a conectividade via VPN ou ExpressRoute, conforme necessário.

[**Redes virtuais**][VNet]. O hub geralmente é criado em uma rede virtual com várias sub-redes para hospedar os diferentes tipos de serviços que filtram e inspecionam o tráfego de ou para a Internet por meio de NVAs, WAFs e instâncias de Gateway de Aplicativo do Azure.

[**Rotas definidas pelo usuário**][user-defined-routes] Usando rotas definidas pelo usuário, os clientes podem implantar firewalls, IDS/IPS e outros dispositivos virtuais e rotear o tráfego de rede por meio desses dispositivos de segurança para imposição, auditoria e inspeção da diretiva de limite de segurança. As rotas definidas pelo usuário podem ser criadas tanto no Hub quanto nos spokes para garantir que o tráfego esteja em trânsito por meio de VMs personalizadas específicas, soluções de virtualização de rede e balanceadores de carga usados por uma implementação de datacenter virtual. Para garantir que o tráfego gerado de máquinas virtuais que residem no spoke esteja em trânsito para os dispositivos virtuais corretos, uma rota definida pelo usuário precisa ser definida nas sub-redes do spoke definindo o endereço IP de front-end do balanceador de carga interno como o próximo salto. O balanceador de carga interno distribui o tráfego interno para as soluções de virtualização (pool de back-end do balanceador de carga).

O [**Firewall do Azure**][AzFW] é um serviço de segurança de rede gerenciado baseado em nuvem que protege os recursos de rede virtual do Azure. É um firewall como serviço totalmente com estado com alta disponibilidade interna e escalabilidade de nuvem irrestrita. É possível criar, impor e registrar centralmente políticas de conectividade de rede e de aplicativo em assinaturas e redes virtuais. O Firewall do Azure usa um endereço IP público estático para seus recursos de rede virtual. Ele permite firewalls externos para identificar o tráfego proveniente da sua rede virtual. O serviço é totalmente integrado ao Azure Monitor para registro em log e análise.

Soluções de [**virtualização de rede**][NVA]. No hub, a rede de perímetro com acesso à Internet normalmente é gerenciada por meio de uma instância do Firewall do Azure ou de um farm de firewalls ou do firewall de aplicativo Web (WAF).

Linhas de negócios diferentes normalmente usam muitos aplicativos Web. Esses aplicativos tendem a sofrer de diversas vulnerabilidades e explorações em potencial. Os firewalls de aplicativos Web são um tipo especial de produto usado para detectar ataques contra aplicativos Web (HTTP/HTTPS) em mais profundidade que um firewall genérico. Em comparação à tecnologia de firewall tradicional, WAFs têm um conjunto de recursos específicos para proteger os servidores Web internos contra ameaças.

Um Firewall do Azure ou firewall NVA usam, ambos, um plano de administração comum, com um conjunto de regras de segurança para proteger as cargas de trabalho hospedadas nos spokes e controlar o acesso a redes locais. O Firewall do Azure tem escalabilidade integrada, enquanto os firewalls do NVA podem ser dimensionados manualmente por um balanceador de carga. Normalmente, um farm de firewall tem software menos especializado comparado a um WAF, mas tem um escopo de aplicação mais amplo para filtrar e inspecionar qualquer tipo de tráfego de entrada e saída. Se for usada uma abordagem de NVA, ela pode ser localizada e implantada no Azure Marketplace.

Use um conjunto de Firewalls do Azure (ou NVAs) para o tráfego originado na Internet e outro para o tráfego originado localmente. Usar apenas um conjunto de firewalls para ambos é um risco à segurança, uma vez que ele não oferece nenhuma segurança de perímetro entre os dois conjuntos de tráfego de rede. Usar camadas de firewall separadas reduz a complexidade de verificar as regras de segurança e deixa claro quais regras correspondem a quais solicitações de rede de entrada.

É recomendável que você use um conjunto de instâncias do Firewall do Azure ou NVAs para tráfego originado na Internet. Use outro para o tráfego originado localmente. Usar apenas um conjunto de firewalls para ambos é um risco à segurança, uma vez que ele não oferece nenhuma segurança de perímetro entre os dois conjuntos de tráfego de rede. Usar camadas de firewall separadas reduz a complexidade da verificação das regras de segurança e deixa claro quais regras correspondem a quais solicitações de rede de entrada.

O [**Azure Load Balancer**][ALB] oferece um serviço de camada 4 de alta disponibilidade (TCP, UDP), que pode distribuir o tráfego de entrada entre as instâncias de serviço definidas em um conjunto de balanceamento de carga. O tráfego enviado para o balanceador de carga de pontos de extremidade de front-end (pontos de extremidade IP públicos ou pontos de extremidade de IP privado) pode ser redistribuído com ou sem a conversão de endereços para um conjunto de pools de endereços IP de back-end (exemplos são soluções de virtualização de rede ou VMs).

Azure Load Balancer também pode investigar a integridade das várias instâncias de servidor e quando uma instância não responde a uma investigação, o balanceador de carga para de enviar tráfego para a instância não íntegra. Em um datacenter virtual, um balanceador de carga externo é implantado no Hub e nos spokes. No hub, o balanceador de carga é usado para rotear o tráfego com eficiência para os serviços nos spokes e, nestes, os balanceadores de carga são usados para gerenciar o tráfego de aplicativo.

O [AFD (Azure front door)][AFD] é a plataforma de aceleração de aplicativos Web altamente disponível e escalonável da Microsoft, Load Balancer http global, proteção de aplicativo e rede de distribuição de conteúdo. Em execução em mais de 100 locais na borda da rede global da Microsoft, o AFD permite que você crie, opere e escale horizontalmente o seu aplicativo Web dinâmico e o conteúdo estático. O AFD oferece a seu aplicativo desempenho do usuário final de alto nível, automação de manutenção de carimbo/regional unificada, automação de BCDR, informações unificadas de cliente/usuário, insights de serviço e caching. A plataforma oferece SLAs de desempenho, confiabilidade e suporte, certificações de conformidade e práticas de segurança auditáveis desenvolvidas, operadas e com suporte nativo pelo Azure.

[**Gateway de aplicativo**][AppGW] Microsoft Azure gateway de aplicativo é um dispositivo virtual dedicado que fornece o ADC (controlador de entrega de aplicativos) como um serviço, oferecendo vários recursos de balanceamento de carga de camada 7 para seu aplicativo. Ele permite que você otimize a produtividade do Web farm descarregando a terminação SSL com uso intensivo de CPU para o Gateway de Aplicativo. Ele também fornece outros recursos de roteamento de camada 7, incluindo distribuição round robin do tráfego de entrada, afinidade de sessão, roteamento com base no caminho de URL e a capacidade de hospedar vários sites por trás de um único Gateway de Aplicativo baseado em cookie. Um WAF (firewall do aplicativo Web) também é fornecido como parte da SKU do WAF do gateway de aplicativo. Essa SKU oferece proteção para aplicativos Web contra explorações e vulnerabilidades comuns da Web. O Gateway de Aplicativo pode ser configurado como um gateway voltado para a Internet, um gateway apenas interno ou uma combinação de ambos.

[**IPS públicos**][PIP]. Com alguns recursos do Azure, você pode associar pontos de extremidade de serviço a um endereço IP público para que seu recurso possa ser acessado pela Internet. Esse ponto de extremidade usa a conversão de endereços de rede (NAT) para rotear o tráfego para a porta e o endereço internos na rede virtual do Azure. Esse caminho é a principal rota para que o tráfego externo passe para dentro da rede virtual. Você pode configurar endereços IP públicos para determinar qual tráfego é passado para dentro e como e onde ele é convertido para a rede virtual.

A [**proteção contra DDoS do Azure Standard**][DDoS] fornece recursos de mitigação adicionais na camada de [serviço básica][DDoS] que são ajustadas especificamente para recursos de rede virtual do Azure. A Proteção contra DDoS Standard é simples de habilitar e não exige nenhuma alteração no aplicativo. Políticas de proteção são ajustadas por meio do monitoramento de tráfego dedicado e algoritmos de aprendizado de máquina. As políticas são aplicadas a endereços IP públicos associados aos recursos implantados em redes virtuais. Os exemplos são instâncias do Azure Load Balancer, Gateway de Aplicativo do Azure e Azure Service Fabric. A telemetria em tempo real está disponível por meio de exibições do Azure Monitor durante um ataque e para o histórico. Proteções de camada de aplicativo podem ser adicionadas por meio do firewall do aplicativo Web do Gateway de Aplicativo do Azure. A proteção é fornecida para endereços IP públicos IPv4 do Azure.

#### <a name="component-type-monitoring"></a>Tipo de componente: monitoramento

Componentes de monitoramento oferecem visibilidade e alertas de todos os outros tipos de componentes. Todas as equipes devem ter acesso ao monitoramento para os componentes e serviços aos quais elas têm acesso. Se você tiver equipes de operações ou suporte técnico centralizadas, elas precisarão ter acesso integrado aos dados fornecidos por esses componentes.

O Azure oferece diferentes tipos de serviços de registro em log e monitoramento para controlar o comportamento de recursos hospedados do Azure. Governança e controle de cargas de trabalho no Azure baseiam-se não apenas na coleta de dados de log, mas também na capacidade de disparar ações com base em eventos relatados específicos.

[**Azure monitor**][Monitor]. O Azure inclui vários serviços que individualmente executam uma função ou tarefa específica no espaço de monitoramento. Juntos, esses serviços oferecem uma solução abrangente para coletar, analisar e agir na telemetria do seu aplicativo e os recursos do Azure compatíveis com eles. Eles também podem trabalhar para monitorar recursos críticos locais para fornecer um ambiente de monitoramento híbrido. Compreender as ferramentas e os dados que estão disponíveis é a primeira etapa no desenvolvimento de uma estratégia de monitoramento completa para seu aplicativo.

Há dois tipos principais de logs no Azure:

- O [log de atividades do Azure][ActLog], anteriormente chamado de **logs operacionais**, fornece informações sobre as operações que foram executadas em recursos na assinatura do Azure. Esses logs relatam os eventos de plano de controle para suas assinaturas. Todos os recursos do Azure geram logs de auditoria.

- [Azure monitor logs de diagnóstico][DiagLog] são logs gerados por um recurso que fornece dados avançados e frequentes sobre a operação do recurso. O conteúdo desses logs varia de acordo com o tipo de recurso.

![9][9]

É importante acompanhar os logs dos grupos de segurança de rede, principalmente essas informações:

- [Os logs de eventos][nsg-log] fornecem informações sobre quais regras de grupo de segurança de rede são aplicadas às VMs e funções de instância com base no endereço Mac.
- [Os logs de contador][nsg-log] controlam quantas vezes cada regra de grupos de segurança de rede foi executada para negar ou permitir o tráfego.

Todos os logs podem ser armazenados nas contas de armazenamento do Azure para fins de auditoria, análise estática ou backup. Quando você armazena os logs em uma conta de armazenamento do Azure, os clientes podem usar diferentes tipos de estruturas para recuperar, preparar, analisar e visualizar esses dados para relatar o status e a integridade dos recursos de nuvem.

Grandes empresas já devem ter adquirido uma estrutura padrão para monitorar sistemas locais. Elas podem estender essa estrutura para integrar logs gerados por implantações de nuvem. Usando o [Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-queries), as organizações podem manter todo o registro em log na nuvem. O Log Analytics é implementado como um serviço baseado em nuvem. Portanto, você pode colocá-lo em funcionamento rapidamente com investimento mínimo nos serviços de infraestrutura. O Log Analytics também se integra aos componentes do System Center como System Center Operations Manager para estender seus investimentos de gerenciamento existentes para a nuvem.

O Log Analytics é um serviço no Azure que ajuda a coletar, correlacionar, pesquisar e agir quanto a dados de desempenho e log gerados por sistemas operacionais, aplicativos e componentes de infraestrutura de nuvem. Ele fornece aos clientes informações operacionais em tempo real usando pesquisa integrada e painéis personalizados para analisar todos os registros em todas as suas cargas de trabalho em sua implementação de datacenter virtual.

O [observador de rede do Azure][NetWatch] fornece ferramentas para monitorar, diagnosticar e exibir métricas e habilitar ou desabilitar logs de recursos em uma rede virtual do Azure. É um serviço multifacetado que permite as seguintes funcionalidades e muito mais:

- Monitorar a comunicação entre uma máquina virtual e um ponto de extremidade.
- Exibir recursos em uma rede virtual e suas relações.
- Diagnosticar problemas de filtragem de tráfego de erro para ou de uma VM.
- Diagnosticar problemas de roteamento de rede de uma VM.
- Diagnosticar conexões de saída de uma VM.
- Capturar pacotes para e de uma VM.
- Diagnosticar problemas com conexões e gateway de rede virtual do Azure.
- Determinar as latências relativas entre regiões do Azure e provedores de serviços de Internet.
- Exibir regras de segurança para uma interface de rede.
- Exibir métricas de rede.
- Analisar o tráfego de ou para um grupo de segurança de rede.
- Exibir logs de diagnóstico para recursos de rede.

A solução [Monitor de desempenho de rede][NPM] dentro do Operations Management Suite pode fornecer informações detalhadas de rede de ponta a ponta. Essas informações incluem uma exibição única de redes do Azure e redes locais. A solução tem monitores específicos para ExpressRoute e serviços públicos.

#### <a name="component-type-workloads"></a>Tipo de componente: cargas de trabalho

Componentes de carga de trabalho são o local em que seus aplicativos reais e serviços residem. Também é o ponto em que as equipes de desenvolvimento de aplicativo passam a maior parte do tempo.

As possibilidades de carga de trabalho são infinitas. A seguir estão apenas alguns dos tipos de carga de trabalho possíveis:

**Aplicativos LOB internos:** Aplicativos de linha de negócios são aplicativos de computador críticos para a operação em andamento de uma empresa. Aplicativos de LOB têm algumas características em comum:

- **Interativo por natureza:** Os dados são inseridos e os resultados ou relatórios são retornados.
- **Controlado por dados:** Cargas de trabalho com uso intensivo de dados com acesso frequente a bancos de dados ou outro armazenamento.
- **Integrado:** As cargas de trabalho oferecem integração com outros sistemas dentro ou fora da organização.

**Sites voltados para o cliente (Internet ou face interna):** A maioria dos aplicativos que interagem com a Internet são sites da Web. O Azure oferece a capacidade de executar um site em uma VM IaaS ou de um site de [aplicativos Web do Azure][WebApps] (PaaS). Os Aplicativos Web do Azure dão suporte à integração com VNETs que permitem a implantação dos aplicativos Web na zona de rede de um spoke. Sites internos não precisam expor um ponto de extremidade de Internet público porque os recursos podem ser acessados por meio de endereços privados não roteáveis para a Internet da VNet privada.

**Big data e análise:** Quando os dados precisam ser escalados verticalmente para um grande volume, os bancos de dados podem não ser dimensionados corretamente. A tecnologia Hadoop oferece um sistema para executar consultas distribuídas em paralelo em um grande número de nós. Os clientes têm a opção de executar cargas de trabalho de dados em VMs IaaS ou PaaS ([HDInsight][HDI]). O HDInsight dá suporte à implantação em uma VNet baseada em local, pode ser implantado em um cluster em um spoke de um datacenter virtual.

**Eventos e mensagens:** os [hubs de eventos do Azure][EventHubs] são um serviço de ingestão de telemetria de hiperescala que coleta, transforma e armazena milhões de eventos. Como uma plataforma de streaming distribuída, oferece baixa latência e tempo de retenção configurável, permitindo a ingestão de grandes quantidades de telemetria no Azure e a leitura de dados de vários aplicativos. Com Hubs de Evento, um único fluxo pode dar suporte a pipelines tanto em tempo real quanto em lote.

Você pode implementar um serviço de mensagens de nuvem altamente confiável entre aplicativos e serviços por meio [do barramento de serviço do Azure][ServiceBus]. Ele oferece um sistema de mensagens agenciado e assíncrono entre o cliente e o servidor, recursos de mensagens PEPS (primeiro a entrar, primeiro a sair) e de publicação e assinatura.

![10][10]

### <a name="make-a-virtual-datacenter-highly-available-multiple-virtual-datacenters"></a>Tornar um datacenter virtual altamente disponível: vários data centers virtuais

Até agora, este artigo se concentrou no design de um único datacenter virtual, descrevendo os componentes básicos e a arquitetura que contribuem para a resiliência. Os recursos do Azure, como Azure Load Balancer, NVAs, conjuntos de disponibilidade, conjuntos de dimensionamento, juntamente com outros mecanismos contribuem para um sistema que permite que você crie níveis sólidos de SLA em seus serviços de produção.

No entanto, como um único datacenter virtual é normalmente implementado em uma única região, ele pode estar vulnerável a qualquer grande interrupção que afete toda a região. Os clientes que exigem SLAs altos devem proteger os serviços por meio de implantações do mesmo projeto em duas (ou mais) implementações de datacenter virtual colocadas em regiões diferentes.

Além das preocupações de SLA, há vários cenários comuns em que a implantação de várias implementações de datacenter virtual faz sentido:

- Presença regional ou global.
- Recuperação de desastre.
- Um mecanismo para desviar o tráfego entre datacenters.

#### <a name="regionalglobal-presence"></a>Presença regional/global

Os datacenters do Azure estão presentes em várias regiões do mundo. Ao selecionar vários datacenters do Azure, os clientes precisam considerar dois fatores relacionados: distâncias geográficas e latência. Para oferecer a melhor experiência de usuário, avalie a distância geográfica entre cada implementação de datacenter virtual, bem como a distância entre cada implementação de datacenter virtual e os usuários finais.

A região na qual as implementações de datacenter virtual são hospedadas deve estar em conformidade com os requisitos regulatórios estabelecidos por qualquer jurisdição legal sob a qual sua organização opera.

#### <a name="disaster-recovery"></a>Recuperação de desastre

O design de um plano de recuperação de desastres depende dos tipos de cargas de trabalho e da capacidade de sincronizar o estado dessas cargas de trabalho entre diferentes implementações de datacenter virtual. O ideal é que a maioria dos clientes queira um mecanismo de failover rápido, e isso pode exigir a sincronização de dados de aplicativos entre implantações que executam várias implementações de datacenter virtual. No entanto, durante a criação de planos de recuperação de desastre, é importante considerar que a maioria dos aplicativos são afetados pela latência que pode ser causada por essa sincronização de dados.

A sincronização e o monitoramento de pulsação de aplicativos em diferentes implementações de datacenter virtual exigem que eles se comuniquem pela rede. Duas implementações em regiões diferentes podem ser conectadas por meio de:

- Emparelhamento VNet-o emparelhamento VNet pode conectar hubs entre regiões.
- Emparelhamento privado do ExpressRoute quando os hubs em cada implementação de datacenter virtual estiverem conectados ao mesmo circuito de ExpressRoute.
- Vários circuitos do ExpressRoute conectados por meio de seu backbone corporativo e várias implementações de datacenter virtual conectadas aos circuitos do ExpressRoute.
- Conexões VPN site a site entre a zona do hub de suas implementações de datacenter virtual em cada região do Azure.

Normalmente, as conexões de Emparelhamento VNET ou de ExpressRoute são o tipo preferencial de conectividade de rede devido à maior largura de banda e aos níveis de latência consistentes ao transitar pelo backbone da Microsoft.

Recomendamos que os clientes executem testes de qualificação de rede para verificar a latência e a largura de banda dessas conexões e escolham a replicação de dados adequada, síncrona ou assíncrona, com base no resultado. Também é importante avaliar esses resultados tendo em vista o RTO (objetivo de tempo de recuperação) ideal.

#### <a name="disaster-recovery-diverting-traffic-from-one-region-to-another"></a>Recuperação de desastre: desviando tráfego de uma região para outra

O [Gerenciador de tráfego do Azure][traffic-manager] verifica periodicamente a integridade do serviço de pontos de extremidade públicos em diferentes implementações de datacenter virtual e, se esses pontos de extremidade falharem, ele roteia automaticamente para o datacenter virtual secundário usando o sistema de nomes de domínio ( DNS).

Como ele usa o DNS, o Gerenciador de Tráfego serve apenas para uso com pontos de extremidade públicos do Azure. Normalmente, o serviço é usado para controlar ou desviar o tráfego para VMs do Azure e aplicativos Web na instância íntegra de uma implementação de datacenter virtual. O Gerenciador de tráfego é resiliente mesmo diante de uma falha de toda a região do Azure e pode controlar a distribuição do tráfego do usuário para pontos de extremidade de serviço em diferentes data centers virtuais com base em vários critérios. Por exemplo, a falha de um serviço em uma implementação de datacenter virtual específica ou a seleção da implementação do datacenter virtual com a menor latência de rede.

### <a name="summary"></a>Resumo

Um datacenter virtual é uma abordagem para a migração do datacenter para criar uma arquitetura escalonável no Azure que maximize o uso de recursos de nuvem, reduza os custos e simplifique a governança do sistema. Um datacenter virtual é baseado em uma topologia de rede hub e spoke, fornecendo serviços compartilhados comuns no Hub e permitindo aplicativos e cargas de trabalho específicos nos spokes. Um datacenter virtual também corresponde à estrutura de funções da empresa, em que departamentos diferentes, como ti central, DevOps e operações e manutenção, funcionam juntos ao mesmo tempo em que executam suas funções específicas. Um datacenter virtual atende aos requisitos de uma migração de comparação e de deslocamento, mas também fornece muitas vantagens para as implantações de nuvem nativas.

## <a name="references"></a>Referências

Os seguintes recursos foram discutidos neste documento. Siga os links para saber mais.

<!-- markdownlint-disable MD033 -->

|Recursos de rede|Balanceamento de Carga|Conectividade|
|-|-|-|
|[Redes Virtuais do Azure][VNet]</br>[Grupos de segurança de rede][network-security-groups]</br>[Logs do grupo de segurança de rede][nsg-log]</br>[Rotas definidas pelo usuário][user-defined-routes]</br>[Soluções de virtualização de rede][NVA]</br>[Endereços IP Públicos][PIP]</br>[DDoS do Azure][DDoS]</br>[Firewall do Azure][AzFW]</br>[DNS do Azure][DNS]|[Porta frontal do Azure][AFD]</br>[Azure Load Balancer (L3)][ALB]</br>[Gateway de aplicativo (L7)][AppGW]</br>[Firewall do aplicativo Web] WAF</br>[Gerenciador de Tráfego do Azure][traffic-manager]</br></br></br></br></br> |[Emparelhamento VNet][VNetPeering]</br>[Rede virtual privada][VPN]</br>[WAN virtual][vWAN]</br>[ExpressRoute][ExR]</br>[ExpressRoute Direct][ExRD]</br></br></br></br></br>

|Identidade</br>|Monitoramento</br>|Práticas Recomendadas</br>|
|-|-|-|
|[Active Directory do Azure][azure-ad]</br>[Autenticação Multifator][multi-factor-authentication]</br>[Controles de acesso de base de função][RBAC]</br>[Funções padrão do Azure AD][Roles]</br></br></br> |[Observador de Rede][NetWatch]</br>[Azure Monitor][Monitor]</br>[Logs de Atividades][ActLog]</br>[Logs de Diagnóstico][DiagLog]</br>[Microsoft Operations Management Suite][OMS]</br>[Monitor de Desempenho de Rede][NPM]|[Práticas recomendadas de redes de perímetro][DMZ]</br>[Gerenciamento de assinatura][SubMgmt]</br>[Gerenciamento de grupo de recursos][RGMgmt]</br>[Limites de assinatura do Azure][limits] </br></br></br>|

|Outros serviços do Azure|
|-|
|[Aplicativos Web do Azure][WebApps]</br>[HDInsight (Hadoop)][HDI]</br>[Hubs de Eventos][EventHubs]</br>[Barramento de Serviço][ServiceBus]|

<!-- markdownlint-enable MD033 -->

## <a name="next-steps"></a>Próximas etapas

- Explore o [emparelhamento VNet][VNetPeering], a tecnologia de base para designs de Hub e spoke de datacenter virtual.
- Implemente o [Azure ad][azure-ad] para começar a explorar o [RBAC][RBAC] .
- Desenvolva um modelo de gerenciamento de assinaturas e recursos e um modelo de RBAC para atender à estrutura, aos requisitos e às políticas da sua organização. A atividade mais importante é o planejamento. Muito prático, planeje reorganizações, fusões, novas linhas de produtos e outras considerações.

<!-- images -->

[0]: ../_images/vdc/networking-redundant-equipment.png "Exemplos de sobreposição de componentes"
[1]: ../_images/vdc/networking-vdc-high-level.png "Exemplo de alto nível de Hub e spoke em uma implementação de datacenter virtual"
[2]: ../_images/vdc/networking-hub-spokes-cluster.png "Cluster de hubs e spokes"
[3]: ../_images/vdc/networking-spoke-to-spoke.png "Spoke a spoke"
[4]: ../_images/vdc/networking-vdc-block-level-diagram.png "Diagrama de nível de bloco de uma implementação de datacenter virtual"
[5]: ../_images/vdc/networking-users-groups-subscriptions.png "Usuários, grupos, assinaturas e projetos"
[6]: ../_images/vdc/networking-infrastructure-high-level.png "Diagrama de alto nível de infraestrutura"
[7]: ../_images/vdc/networking-high-level-perimeter-networks.png "Diagrama de alto nível de infraestrutura"
[8]: ../_images/vdc/networking-vnet-peering-perimeter-networks.png "Redes de perímetro e de emparelhamento VNet"
[9]: ../_images/vdc/networking-high-level-diagram-monitoring.png "Diagrama de alto nível para monitoramento"
[10]: ../_images/vdc/networking-high-level-workloads.png "Diagrama de alto nível para Carga de Trabalho"

<!-- links -->

[limits]: https://docs.microsoft.com/azure/azure-subscription-service-limits
[Roles]: https://docs.microsoft.com/azure/role-based-access-control/built-in-roles
[VNet]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview
[network-security-groups]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg
[DNS]: https://docs.microsoft.com/azure/dns/dns-overview
[PrivateDNS]: https://docs.microsoft.com/azure/dns/private-dns-overview
[VNetPeering]: https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview
[user-defined-routes]: https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview
[RBAC]: https://docs.microsoft.com/azure/role-based-access-control/overview
[multi-factor-authentication]: https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication
[azure-ad]: https://docs.microsoft.com/azure/active-directory/active-directory-whatis
[VPN]: https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways
[ExR]: https://docs.microsoft.com/azure/expressroute/expressroute-introduction
[ExRD]: https://docs.microsoft.com/azure/expressroute/expressroute-erdirect-about
[vWAN]: https://docs.microsoft.com/azure/virtual-wan/virtual-wan-about
[NVA]: https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: https://docs.microsoft.com/azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold
[RGMgmt]: https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview
[DMZ]: https://docs.microsoft.com/azure/best-practices-network-security
[ALB]: https://docs.microsoft.com/azure/load-balancer/load-balancer-overview
[DDoS]: https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview
[PIP]: https://docs.microsoft.com/azure/virtual-network/virtual-network-public-ip-address
[AFD]: https://docs.microsoft.com/azure/frontdoor/front-door-overview
[AFDWAF]: https://docs.microsoft.com/azure/frontdoor/waf-overview
[AppGW]: https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction
[AppGWWAF]: https://docs.microsoft.com/azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/
[ActLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-activity-logs
[DiagLog]: https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[nsg-log]: https://docs.microsoft.com/azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview
[NPM]: https://docs.microsoft.com/azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: https://docs.microsoft.com/azure/app-service/
[HDI]: https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs
[ServiceBus]: https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview
[traffic-manager]: https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview
