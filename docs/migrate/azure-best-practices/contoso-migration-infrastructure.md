---
title: Implante uma infraestrutura de migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como a Contoso configura uma infraestrutura do Azure para migração para o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/1/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 93c0bb52159b4573ed796ca3a1aa7cb0ac2d8149
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547338"
---
# <a name="deploy-a-migration-infrastructure"></a>Implante uma infraestrutura de migração

Este artigo mostra como a empresa fictícia Contoso prepara sua infraestrutura local para migração, configura uma infraestrutura do Azure em preparação para a migração e executa a empresa em um ambiente híbrido. Ao usar este exemplo para ajudar a planejar seus próprios esforços de migração de infraestrutura, tenha em mente o seguinte:

- A arquitetura de exemplo fornecida é específica para a contoso. Examine as necessidades de negócios, a estrutura e os requisitos técnicos da sua organização ao tomar decisões de infraestrutura importantes sobre design de assinatura ou arquitetura de rede.
- Se você precisa de todos os elementos descritos neste artigo depende de sua estratégia de migração. Por exemplo, se você estiver criando apenas aplicativos nativos de nuvem no Azure, talvez precise de uma estrutura de rede menos complexa.

## <a name="overview"></a>Visão Geral

Antes que a contoso possa migrar para o Azure, é essencial preparar uma infraestrutura do Azure. Em geral, há seis áreas amplas que a contoso precisa pensar:

> [!div class="checklist"]
>
> - **Etapa 1: assinaturas do Azure.** Como a contoso comprará o Azure e interagirá com a plataforma e os serviços do Azure?
> - **Etapa 2: identidade híbrida.** Como ele gerenciará e controlará o acesso a recursos locais e do Azure após a migração? Como a contoso estende ou move o gerenciamento de identidades para a nuvem?
> - **Etapa 3: recuperação de desastres e resiliência.** Como a contoso garantirá que seus aplicativos e infraestrutura sejam resilientes se ocorrerem interrupções e desastres?
> - **Etapa 4: rede.** Como a Contoso deve projetar uma infra-estrutura de rede e estabelecer a conectividade entre seu datacenter local e o Azure?
> - **Etapa 5: segurança.** Como protegerá a implantação híbrida/do Azure?
> - **Etapa 6: governança.** Como a contoso manterá a implantação alinhada aos requisitos de segurança e governança?

## <a name="before-you-start"></a>Antes de começar

Antes de começarmos a examinar a infraestrutura, talvez você queira ler algumas informações básicas sobre os recursos do Azure que discutimos neste artigo:

- Várias opções estão disponíveis para a compra de acesso do Azure, incluindo pré-pago, Enterprise Agreements (EA), licenciamento aberto de revendedores da Microsoft ou de parceiros da Microsoft conhecidos como CSPs (provedores de soluções de nuvem). Saiba mais sobre [as opções de compra](https://azure.microsoft.com/pricing/purchase-options)e leia sobre como as [assinaturas do Azure são organizadas](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).
- Obtenha uma visão geral do [Gerenciamento de identidade e acesso](https://www.microsoft.com/trustcenter/security/identity)do Azure. Em particular, saiba mais sobre [o Azure AD e estendendo Active Directory locais para a nuvem](https://docs.microsoft.com/azure/active-directory/identity-fundamentals). Há um livro eletrônico para download útil sobre [iam (gerenciamento de identidade e acesso) em um ambiente híbrido](https://azure.microsoft.com/resources/hybrid-cloud-identity).
- O Azure fornece uma infraestrutura de rede robusta com opções de conectividade híbrida. Obtenha uma visão geral da [rede e do controle de acesso à rede](https://docs.microsoft.com/azure/security/security-network-overview).
- Obtenha uma introdução à [segurança do Azure](https://docs.microsoft.com/azure/security/azure-security)e leia sobre como criar um plano para [governança](https://docs.microsoft.com/azure/security/governance-in-azure).

## <a name="on-premises-architecture"></a>Arquitetura local

Aqui está um diagrama que mostra a atual infraestrutura local da contoso.

 ![Arquitetura da contoso](./media/contoso-migration-infrastructure/contoso-architecture.png)

- A contoso tem um datacenter principal localizado na cidade de Nova York na Estados Unidos Oriental.
- Há três ramificações locais adicionais no Estados Unidos.
- O datacenter principal está conectado à Internet com uma conexão Ethernet metro de fibra (500 Mbps).
- Cada ramificação é conectada localmente à Internet usando conexões de classe de negócios, com túneis de VPN IPSec de volta para o datacenter principal. Isso permite que toda a rede seja permanentemente conectada e otimize a conectividade com a Internet.
- O datacenter principal é totalmente virtualizado com o VMware. A contoso tem dois hosts de virtualização de ESXi 6,5, gerenciados pelo vCenter Server 6,5.
- A contoso usa Active Directory para gerenciamento de identidade e servidores DNS na rede interna.
- Os controladores de domínio no datacenter são executados em VMs VMware. Os controladores de domínio em branches locais são executados em servidores físicos.

## <a name="step-1-buy-and-subscribe-to-azure"></a>Etapa 1: comprar e assinar o Azure

A contoso precisa descobrir como comprar o Azure, como arquitetar assinaturas e como licenciar serviços e recursos.

### <a name="buy-azure"></a>Comprar o Azure

A Contoso está indo com um [Enterprise Agreement (ea)](https://azure.microsoft.com/pricing/enterprise-agreement). Isso envolve um compromisso monetário inicial com o Azure, entitling a Contoso para obter ótimos benefícios, incluindo opções de cobrança flexíveis e preços otimizados.

- A contoso estimou o que seus gastos anuais com o Azure serão. Quando ele assinou o contrato, a contoso pagou pelo primeiro ano por completo.
- A contoso precisa usar todos os compromissos antes de o ano terminar ou perder o valor desses dólares.
- Se, por algum motivo, a contoso exceder seu compromisso e passar mais, a Microsoft faturará a eles pela diferença.
- Qualquer custo incorrido acima do compromisso será de acordo com as mesmas tarifas do contrato da contoso. Não há penalidades a serem passadas.

### <a name="manage-subscriptions"></a>Gerenciar Assinaturas

Depois de pagar pelo Azure, a contoso precisa descobrir como gerenciar assinaturas do Azure. A contoso tem um EA e, portanto, não há limite para o número de assinaturas do Azure que ele pode configurar.

- Um registro do Azure Enterprise define como as formas da empresa usam os serviços do Azure e define uma estrutura de governança principal.
- Como primeira etapa, a contoso definiu uma estrutura conhecida como Scaffold empresarial para registro empresarial. A contoso usou [Este artigo](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-subscription-governance) para ajudar a entender e criar um Scaffold.
- Por enquanto, a Contoso decidiu usar uma abordagem funcional para gerenciar assinaturas.
  - Dentro da empresa, ele usará um único departamento de ti que controla o orçamento do Azure. Esse será o único grupo com assinaturas.
  - A contoso estenderá esse modelo no futuro, para que outros grupos corporativos possam ingressar como departamentos no registro corporativo.
  - Dentro do departamento de ti, a contoso tem estruturado duas assinaturas, produção e desenvolvimento.
  - Se a contoso exigir assinaturas adicionais no futuro, precisará gerenciar o acesso, as políticas e a conformidade para essas assinaturas. A contoso fará isso apresentando os [grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview), como uma camada adicional acima das assinaturas.

  ![Estrutura empresarial](./media/contoso-migration-infrastructure/enterprise-structure.png)

### <a name="examine-licensing"></a>Examinar o licenciamento

Com as assinaturas configuradas, a Contoso pode examinar o licenciamento da Microsoft. A estratégia de licenciamento dependerá dos recursos que a contoso deseja migrar para o Azure e como as VMs e os serviços do Azure são selecionados e implantados.

#### <a name="azure-hybrid-benefit"></a>Benefício Híbrido do Azure

Ao implantar VMs no Azure, as imagens padrão incluem uma licença que cobrará a contoso por minuto para o software que está sendo usado. No entanto, a contoso tem sido um cliente de longo prazo da Microsoft e manteve licenças de EAs e abertas com o Software Assurance (SA).

O Benefício Híbrido do Azure fornece um método econômico para a migração da Contoso, permitindo salvar em VMs do Azure e SQL Server cargas de trabalho convertendo ou reutilizando licenças do Windows Server Datacenter e Standard Edition cobertas pelo Software Assurance. Isso permitirá que a contoso pague uma taxa de computação com base mais baixa para VMs e SQL Server. [Saiba mais](https://azure.microsoft.com/pricing/hybrid-benefit).

#### <a name="license-mobility"></a>Mobilidade de licenças

Mobilidade de Licenças por meio do SA oferece aos clientes de licenciamento por volume da Microsoft como a Contoso a flexibilidade para implantar aplicativos de servidor qualificados com o SA ativo no Azure. Isso elimina a necessidade de comprar novas licenças. Sem taxas de mobilidade associadas, as licenças existentes podem ser facilmente implantadas no Azure. [Saiba mais](https://azure.microsoft.com/pricing/license-mobility).

#### <a name="reserve-instances-for-predictable-workloads"></a>Reservar instâncias para cargas de trabalho previsíveis

Cargas de trabalho previsíveis são aquelas que sempre precisam estar disponíveis com VMs em execução. Por exemplo, aplicativos de linha de negócios, como um sistema SAP ERP. Por outro lado, cargas de trabalho imprevisíveis são aquelas que são variáveis, como as VMs que estão no durante a alta demanda e quando a demanda está baixa.

![Instância reservada](./media/contoso-migration-infrastructure/reserved-instance.png)

No Exchange para usar instâncias reservadas para instâncias de VM específicas devem ser mantidas por grandes durações de tempo, o console pode obter um desconto e capacidade priorizada. Usando as [instâncias reservadas do Azure](https://azure.microsoft.com/pricing/reserved-vm-instances), junto com a benefício híbrido do Azure, a Contoso pode economizar até 82% de desconto regular pago conforme o uso (abril de 2018).

## <a name="step-2-manage-hybrid-identity"></a>Etapa 2: gerenciar a identidade híbrida

Dar e controlar o acesso do usuário aos recursos do Azure com IAM (gerenciamento de acesso e identidade) é uma etapa importante para reunir uma infraestrutura do Azure.

- A Contoso decide estender seu Active Directory local para a nuvem, em vez de criar um novo sistema separado no Azure.
- Ele cria um Active Directory baseado no Azure para fazer isso.
- A contoso não tem o Office 365 em vigor, portanto, precisa provisionar um novo Azure AD.
- O Office 365 usa o Azure AD para gerenciamento de usuários. Se a Contoso estivesse usando o Office 365, ele já teria um locatário do Azure AD e poderá usá-lo como o diretório primário.
- [Saiba mais](https://support.office.com/article/understanding-office-365-identity-and-azure-active-directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9) sobre o Azure ad para Office 365 e saiba [como adicionar uma assinatura](https://docs.microsoft.com/azure/active-directory/active-directory-how-subscriptions-associated-directory) a um locatário existente do Azure AD.

### <a name="create-an-azure-ad"></a>Criar um Azure AD

A Contoso está usando a edição Azure AD Gratuito incluída com uma assinatura do Azure. Os administradores da Contoso configuram um diretório da seguinte maneira:

1. No [portal do Azure](https://portal.azure.com), eles navegam para **criar um recurso**  > **identidade**  > **Azure Active Directory**.
2. Em **criar diretório**, eles especificam um nome para o diretório, um nome de domínio inicial e uma região na qual o diretório do Azure ad deve ser criado.

    ![Criar Azure AD](./media/contoso-migration-infrastructure/azure-ad-create.png)

    > [!NOTE]
    > O diretório criado tem um nome de domínio inicial no formato **DomainName.onmicrosoft.com**. O nome não pode ser alterado ou excluído. Em vez disso, eles precisam adicionar seu nome de domínio registrado ao Azure AD.

### <a name="add-the-domain-name"></a>Adicionar o nome de domínio

Para usar seu nome de domínio padrão, os administradores da Contoso precisam adicioná-lo como um nome de domínio personalizado ao Azure AD. Essa opção permite que eles atribuam nomes de usuário familiares. Por exemplo, um usuário pode fazer logon com o endereço de email billg@contoso.com, em vez de precisar de billg@contosomigration.microsoft.com.

Para configurar um nome de domínio personalizado, adicione-o ao diretório, adicione uma entrada DNS e, em seguida, verifique o nome no Azure AD.

1. Em **nomes de domínio personalizados**  > **Adicionar domínio personalizado**, eles adicionam o domínio.
2. Para usar uma entrada DNS no Azure, eles precisam registrá-lo em seu registrador de domínio.

    - Na lista **nomes de domínio personalizados** , eles observam as informações de DNS para o nome. Ele está usando uma entrada MX.
    - Eles precisam de acesso ao servidor de nomes para fazer isso. Eles fazem logon no domínio Contoso.com e criam um novo registro MX para a entrada DNS fornecida pelo Azure AD, usando os detalhes indicados.

3. Depois que os registros DNS são propagados, no nome de detalhes do domínio, eles selecionam **verificar** para verificar o nome de domínio personalizado.

     ![DNS do Azure AD](./media/contoso-migration-infrastructure/azure-ad-dns.png)

### <a name="set-up-on-premises-and-azure-groups-and-users"></a>Configurar grupos e usuários locais e do Azure

Agora que o Azure AD está em execução, os administradores da Contoso precisam adicionar funcionários a grupos de Active Directory locais que serão sincronizados com o Azure Active Directory. Eles devem usar nomes de grupos locais que correspondam aos nomes de grupos de recursos no Azure. Isso facilita a identificação de correspondências para fins de sincronização.

#### <a name="create-resource-groups-in-azure"></a>Criar grupos de recursos no Azure

Os grupos de recursos do Azure reúnem recursos do Azure juntos. O uso de uma ID de grupo de recursos permite que o Azure execute operações nos recursos do grupo.

- Uma assinatura do Azure pode ter vários grupos de recursos, mas um grupo de recursos só pode existir em uma única assinatura.
- Além disso, um único grupo de recursos pode ter vários recursos, mas um recurso só pode pertencer a um único grupo de recursos.

Os administradores da Contoso configuram grupos de recursos do Azure como resumidos na tabela a seguir.

<!-- markdownlint-disable MD033 -->

**Grupo de recursos** | **Detalhes**
--- | ---
**ContosoCobRG** | Esse grupo contém todos os recursos relacionados à continuidade de negócios (COB). Ele inclui cofres que a Contoso usará para o serviço de Azure Site Recovery e o serviço de backup do Azure.<br/><br/> Ele também incluirá os recursos usados para migração, incluindo migrações para Azure e serviço de migração de banco de dados do Azure.
**ContosoDevRG** | Este grupo contém recursos de desenvolvimento e teste.
**ContosoFailoverRG** | Esse grupo serve como uma zona de aterrissagem para recursos com failover.
**ContosoNetworkingRG** | Esse grupo contém todos os recursos de rede.
**ContosoRG** | Esse grupo contém recursos relacionados a bancos de dados e aplicativos de produção.

<!-- markdownlint-disable MD026 -->

Eles criam grupos de recursos da seguinte maneira:

1. No portal do Azure > **grupos de recursos**, eles adicionam um grupo.
2. Para cada grupo, eles especificam um nome, a assinatura à qual o grupo pertence e a região.
3. Os grupos de recursos aparecem na lista **grupos de recursos** .

    ![Grupos de recursos](./media/contoso-migration-infrastructure/resource-groups.png)

##### <a name="scaling-resource-groups"></a>Dimensionando grupos de recursos

No futuro, a contoso adicionará outros grupos de recursos com base nas necessidades. Por exemplo, eles podem definir um grupo de recursos para cada aplicativo ou serviço, para que eles possam ser gerenciados e protegidos de forma independente.

#### <a name="create-matching-security-groups-on-premises"></a>Criar grupos de segurança correspondentes locais

1. No Active Directory local, os administradores da Contoso configuram grupos de segurança com nomes que correspondem aos nomes dos grupos de recursos do Azure.

    ![Grupos de segurança Active Directory locais](./media/contoso-migration-infrastructure/on-prem-ad.png)

2. Para fins de gerenciamento, eles criam um grupo adicional que será adicionado a todos os outros grupos. Esse grupo terá direitos a todos os grupos de recursos no Azure. Um número limitado de administradores globais será adicionado a esse grupo.

### <a name="synchronize-active-directory"></a>Sincronizar Active Directory

A contoso deseja fornecer uma identidade comum para acessar recursos locais e na nuvem. Para fazer isso, ele integrará o Active Directory local ao Azure AD. Com este modelo:

- Os usuários e as organizações podem aproveitar uma única identidade para acessar aplicativos locais e serviços de nuvem, como o Office 365, ou milhares de outros sites na Internet.
- Os administradores podem usar os grupos em Active Directory para implementar o [RBAC (controle de acesso baseado em função)](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) no Azure.

Para facilitar a integração, a contoso usa a [ferramenta de Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Quando você instala e configura a ferramenta em um controlador de domínio, ele sincroniza as identidades locais de Active Directory local para o Azure AD.

### <a name="download-the-tool"></a>Baixar a ferramenta

1. Na portal do Azure, os administradores da Contoso vão para **Azure Active Directory**  > **Azure ad Connect**e baixe a versão mais recente da ferramenta para o servidor que está usando para sincronização.

    ![Baixar Azure AD Connect](./media/contoso-migration-infrastructure/download-ad-connect.png)

2. Eles iniciam a instalação do **AzureADConnect. msi** , com o **uso de configurações expressas**. Essa é a instalação mais comum e pode ser usada para uma topologia de floresta única, com a sincronização de hash de senha para autenticação.

    ![Assistente de Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz1.png)

3. Em **conectar-se ao Azure ad**, eles especificam as credenciais para se conectar ao Azure AD (no formato admin@contoso.com ou admin@contoso.onmicrosoft.com).

    ![Assistente de Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz2.png)

4. Em **conectar a AD DS**, eles especificam credenciais para o Active Directory local (no formato CONTOSO\admin ou contoso. com\admin).

     ![Assistente de Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz3.png)

5. Em **pronto para configurar**, eles selecionam **iniciar o processo de sincronização quando a configuração for concluída** para iniciar a sincronização imediatamente. Em seguida, eles são instalados.

Observe que:

- A contoso tem uma conexão direta com o Azure. Se sua Active Directory local estiver atrás de um proxy, leia este [artigo](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-connectivity).

- Após a primeira sincronização, os objetos de Active Directory locais ficam visíveis no diretório do AD do Azure.

    ![Active Directory locais no Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

- A equipe de ti da Contoso é representada em cada grupo, com base em sua função.

    ![Membros do Active Directory local no Azure](./media/contoso-migration-infrastructure/on-prem-ad-group-members.png)

### <a name="set-up-rbac"></a>Configurar o RBAC

O [RBAC (controle de acesso baseado em função)](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) do Azure permite o gerenciamento de acesso refinado para o Azure. Usando o RBAC, você pode conceder apenas a quantidade de acesso que os usuários precisam para executar tarefas. Você atribui a função RBAC apropriada para usuários, grupos e aplicativos em um nível de escopo. O escopo de uma atribuição de função pode ser uma assinatura, um grupo de recursos ou um único recurso.

Os administradores da Contoso agora atribui funções aos grupos de Active Directory que eles sincronizaram do local.

1. No grupo de recursos **ControlCobRG** , eles selecionam o **controle de acesso (iam)**  > **Adicionar atribuição de função**.
2. Em **Adicionar atribuição de função**  > **função**> **colaborador**, eles selecionam o grupo **ContosoCobRG** da lista. Em seguida, o grupo aparece na lista **Membros selecionados** .
3. Eles repetim isso com as mesmas permissões para os outros grupos de recursos (exceto para **ContosoAzureAdmins**), adicionando as permissões de colaborador à conta que corresponde ao grupo de recursos.
4. Para o grupo **ContosoAzureAdmins** , eles atribuem a função **proprietário** .

    ![Membros do Active Directory local no Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

## <a name="step-3-design-for-resiliency"></a>Etapa 3: design para resiliência

### <a name="set-up-regions"></a>Configurar regiões

Os recursos do Azure são implantados em regiões.

- As regiões são organizadas em Geografia e os requisitos de residência de dados, soberania, conformidade e resiliência são respeitados dentro dos limites geográficos.
- Uma região é composta por um conjunto de data centers. Esses data centers são implantados em um perímetro definido por latência e conectados por meio de uma rede regional de baixa latência.
- Cada região do Azure é emparelhada com uma região diferente para resiliência.
- Leia sobre [regiões do Azure](https://azure.microsoft.com/global-infrastructure/regions)e entenda [como as regiões são emparelhadas](https://docs.microsoft.com/azure/best-practices-availability-paired-regions).

A Contoso decidiu ir com o leste dos EUA 2 (localizado em Virgínia) como a região primária e EUA Central (localizada em Iowa) como a região secundária. Há alguns motivos para isso:

- O Data Center da Contoso está localizado em Nova York e a contoso considerou a latência para o datacenter mais próximo.
- A região leste dos EUA 2 tem todos os serviços e produtos que a contoso precisa usar. Nem todas as regiões do Azure são as mesmas em termos de produtos e serviços disponíveis. Você pode examinar os [produtos do Azure por região](https://azure.microsoft.com/global-infrastructure/services).
- EUA Central é a região emparelhada do Azure para o leste dos EUA 2.

Como ele pensa no ambiente híbrido, a contoso precisa considerar como criar resiliência e uma estratégia de recuperação de desastres no design de região. Em grande medida, as estratégias variam de uma implantação de região única, que se baseia nos recursos da plataforma Azure, como domínios de falha e emparelhamento regional para resiliência, até um modelo ativo-ativo completo no qual os serviços de nuvem e o banco de dados são implantados e atendentes usuários de duas regiões.

A Contoso decidiu fazer uma estrada central. Ele implantará aplicativos e recursos em uma região primária e manterá uma cópia completa da infraestrutura na região secundária, de modo que esteja pronto para agir como um backup completo em caso de desastre de aplicativo completo ou falha regional.

### <a name="set-up-availability"></a>Configurar disponibilidade

**Conjuntos de disponibilidade:**

Os conjuntos de disponibilidade ajudam a proteger aplicativos e dados de uma interrupção de rede e de hardware local em um datacenter.

- Os conjuntos de disponibilidade distribuem VMs do Azure entre diferentes hardwares físicos em um datacenter.
- Os domínios de falha representam o hardware subjacente com uma fonte de energia e um comutador de rede comuns no datacenter. As VMs em um conjunto de disponibilidade são distribuídas entre diferentes domínios de falha para minimizar interrupções causadas por uma única falha de hardware ou de rede.
- Os domínios de atualização representam o hardware subjacente que pode passar por manutenção ou ser reinicializado ao mesmo tempo. Os conjuntos de disponibilidade também distribuem VMs em vários domínios de atualização para garantir que pelo menos uma instância seja executada em todos os momentos.

A contoso implementará conjuntos de disponibilidade sempre que as cargas de trabalho de VM exigirem alta disponibilidade. [Saiba mais](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability).

**Zonas de disponibilidade:**

As zonas de disponibilidade ajudam a proteger aplicativos e dados contra falhas que afetam um datacenter inteiro dentro de uma região.

- Cada zona de disponibilidade representa um local físico exclusivo dentro de uma região do Azure.
- Cada zona é composta por um ou mais data centers equipados com energia, resfriamento e rede independentes.
- Há um mínimo de três zonas separadas em todas as regiões habilitadas.
- A separação física de zonas em uma região protege aplicativos e dados de falhas do datacenter.

A contoso implantará zonas de disponibilidade como aplicativos chamados para escalabilidade, alta disponibilidade e resiliência. [Saiba mais](https://docs.microsoft.com/azure/availability-zones/az-overview).

### <a name="set-up-backup"></a>Configurar backup

**Backup do Azure:**

O backup do Azure permite que você faça backup e restaure discos de VM do Azure.

- O backup do Azure permite backups automatizados de imagens de disco de VM, armazenadas no armazenamento do Azure.
- Os backups são consistentes com o aplicativo, garantindo que os dados de backup sejam transacionalmente consistentes e que os aplicativos sejam inicializados após a restauração.
- O backup do Azure dá suporte ao LRS (armazenamento com redundância local) para replicar várias cópias dos dados de backup em um datacenter, no caso de uma falha de hardware local.
- No caso de uma interrupção regional, o backup do Azure também dá suporte ao GRS (armazenamento com redundância geográfica), replicando os dados de backup para uma região emparelhada secundária.
- O backup do Azure criptografa dados em trânsito usando o AES 256. Os dados de backup em repouso são criptografados usando o [criptografia do serviço de armazenamento (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption?toc=%2fazure%2fstorage%2fqueues%2ftoc.json).

A Contoso usará o backup do Azure com o GRS em todas as VMs de produção para garantir que o backup dos dados de carga de trabalho seja feito e possa ser restaurado rapidamente em caso de interrupção ou outra interrupção. [Saiba mais](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup).

### <a name="set-up-disaster-recovery"></a>Configurar a recuperação de desastre

**Azure Site Recovery:**

Azure Site Recovery ajuda a garantir a continuidade dos negócios mantendo os aplicativos de negócios e as cargas de trabalho em execução durante interrupções regionais.

- Azure Site Recovery Replica continuamente VMs do Azure de um primário para uma região secundária, garantindo cópias funcionais em ambos os locais.
- No caso de uma interrupção na região primária, seu aplicativo ou serviço faz failover para usar as instâncias de VMs replicadas na região secundária, minimizando a interrupção em potencial.
- Quando as operações retornam para normal, seus aplicativos ou serviços podem fazer failback para VMs na região primária.

A contoso implementará Azure Site Recovery para todas as VMs de produção usadas em cargas de trabalho de missão crítica, garantindo interrupção mínima durante uma interrupção na região primária. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

## <a name="step-4-design-a-network-infrastructure"></a>Etapa 4: criar uma infraestrutura de rede

Com o design regional em vigor, a Contoso está pronta para considerar uma estratégia de rede. Ele precisa pensar sobre como o datacenter local e o Azure Connect e se comunicam entre si e como projetar a infraestrutura de rede no Azure. Especificamente, a contoso precisa:

- **Planejar a conectividade de rede híbrida.** Descubra como ele vai conectar redes entre locais e o Azure.
- **Projete uma infraestrutura de rede do Azure.** Decida como ele implantará redes em regiões. Como as redes se comunicarão dentro da mesma região e entre regiões?
- **Projete e configure redes do Azure.** Configure redes e sub-redes do Azure e decida o que residirá nelas.

### <a name="plan-hybrid-network-connectivity"></a>Planejar a conectividade de rede híbrida

A contoso considerou uma [série de arquiteturas](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking) para rede híbrida entre o Azure e o datacenter local. [Leia mais](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations) sobre as opções de comparação.

Como lembrete, a infraestrutura de rede local da Contoso consiste atualmente no datacenter em Nova York e nas ramificações locais na parte leste dos EUA. Todos os locais têm uma conexão de classe de negócios com a Internet. Cada uma das ramificações é então conectada ao datacenter por meio de um túnel VPN IPSec pela Internet.

![Rede contoso](./media/contoso-migration-infrastructure/contoso-networking.png)

Veja como a Contoso decidiu implementar a conectividade híbrida:

1. Configure uma nova conexão VPN site a site entre o datacenter da Contoso em Nova York e as duas regiões do Azure no leste dos EUA 2 e EUA Central.
2. O tráfego de filial associado a redes virtuais do Azure será roteado pelo datacenter principal da contoso.
3. À medida que a contoso dimensionar a implantação do Azure, ela estabelecerá uma conexão de ExpressRoute entre o datacenter e as regiões do Azure. Quando isso acontecer, a contoso manterá a conexão VPN site a site somente para fins de failover.
    - [Saiba mais](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations) sobre como escolher entre uma solução híbrida de VPN e de ExpressRoute.
    - Verifique os [locais e o suporte do ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-locations-providers).

**Somente VPN:**

![VPN contoso](./media/contoso-migration-infrastructure/hybrid-vpn.png)

**VPN e ExpressRoute:**

![VPN/ExpressRoute da contoso](./media/contoso-migration-infrastructure/hybrid-vpn-expressroute.png)

### <a name="design-the-azure-network-infrastructure"></a>Projetar a infraestrutura de rede do Azure

É essencial que a contoso Coloque redes em vigor de forma a tornar a implantação híbrida segura e escalonável. Para fazer isso, a Contoso está adotando uma abordagem de longo prazo e está projetando redes virtuais (VNets) para ser resiliente e pronto para empresas. [Saiba mais](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm) sobre o planejamento de VNets.

Para conectar as duas regiões, a Contoso decidiu implementar um modelo de rede hub a Hub:

- Em cada região, a Contoso usará um modelo de Hub e spoke.
- Para conectar redes e hubs, a Contoso usará o emparelhamento de rede do Azure.

#### <a name="network-peering"></a>Emparelhamento de rede

O Azure fornece emparelhamento de rede para conectar VNets e hubs. O emparelhamento global permite conexões entre VNets/hubs em regiões diferentes. O emparelhamento local conecta VNets na mesma região. O emparelhamento VNet fornece várias vantagens:

- O tráfego de rede entre VNets emparelhadas é privado.
- O tráfego entre o VNets é mantido na rede de backbone da Microsoft. Nenhuma criptografia, gateways ou Internet pública é necessária na comunicação entre o VNets.
- O emparelhamento fornece uma conexão padrão de baixa latência e alta largura de banda entre os recursos em diferentes VNets.

[Saiba mais](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) sobre o emparelhamento de rede.

#### <a name="hub-to-hub-across-regions"></a>Hub para hub entre regiões

A contoso implantará um Hub em cada região. Um hub é uma rede virtual (VNet) no Azure que atua como um ponto central de conectividade para sua rede local. O Hub VNets se conectará entre si usando o emparelhamento de VNet global. O emparelhamento de VNet global conecta o VNets nas regiões do Azure.

- O Hub em cada região é emparelhado com o Hub parceiro na outra região.
- O Hub é emparelhado a cada rede em sua região e pode se conectar a todos os recursos de rede.

    ![Emparelhamento global](./media/contoso-migration-infrastructure/global-peering.png)

#### <a name="hub-and-spoke-model-within-a-region"></a>Modelo de Hub e spoke dentro de uma região

Em cada região, a contoso implantará VNets para finalidades diferentes, como redes spoke do hub de região. VNets em uma região use o emparelhamento para se conectar ao Hub e entre si.

#### <a name="design-the-hub-network"></a>Criar a rede de Hub

No modelo de Hub e spoke que a contoso escolheu, ele precisa pensar em como o tráfego do datacenter local e da Internet será roteado. Veja como a Contoso decidiu lidar com o roteamento para os hubs leste dos EUA 2 e EUA Central:

- A Contoso está criando uma rede conhecida como "reverso c", pois esse é o caminho que os pacotes seguem da entrada para a rede de saída.
- A arquitetura de rede tem dois limites, uma zona de perímetro de front-end não confiável e uma zona confiável de back-end.
- Um firewall terá um adaptador de rede em cada zona, controlando o acesso a zonas confiáveis.
- Da Internet:
  - O tráfego da Internet atingirá um endereço IP público com balanceamento de carga na rede de perímetro.
  - Esse tráfego é roteado pelo firewall e sujeito a regras de firewall.
  - Depois que os controles de acesso à rede são implementados, o tráfego será encaminhado para o local apropriado na zona confiável.
  - O tráfego de saída da VNet será roteado para a Internet usando rotas definidas pelo usuário. O tráfego é forçado pelo firewall e inspecionado em linha com as políticas da contoso.
- Do datacenter da Contoso:
  - O tráfego de entrada por VPN site a site (ou ExpressRoute) atinge o endereço IP público do gateway de VPN do Azure.
  - O tráfego é roteado pelo firewall e sujeito a regras de firewall.
  - Depois de aplicar as regras de firewall, o tráfego é encaminhado para um balanceador de carga interno (SKU padrão) na sub-rede da zona interna confiável.
  - O tráfego de saída da sub-rede confiável para o datacenter local por VPN é roteado pelo firewall e as regras são aplicadas antes de passar pela conexão VPN site a site.

### <a name="design-and-set-up-azure-networks"></a>Projetar e configurar redes do Azure

Com uma topologia de rede e de roteamento em vigor, a Contoso está pronta para configurar redes e sub-redes do Azure.

- A contoso implementará uma rede privada de classe no Azure (0.0.0.0 a 127.255.255.255). Isso funciona, já que ele atualmente tem um espaço de endereço privado de classe B 172.160.0/16 para que a contoso possa ter certeza de que não haverá qualquer sobreposição entre intervalos de endereços.
- Vai implantar VNets nas regiões primária e secundária.
- A Contoso usará uma Convenção de nomenclatura que inclui o prefixo **VNET** e a abreviação de região **EUS2** ou **cus**. Usando esse padrão, as redes de Hub serão nomeadas **vnet-Hub-EUS2** (leste dos EUA 2) e **VNET-Hub-cus** (EUA Central).
- A contoso não tem uma [solução IPAM](https://docs.microsoft.com/windows-server/networking/technologies/ipam/ipam-top), portanto, precisa planejar o roteamento de rede sem NAT.

#### <a name="virtual-networks-in-east-us-2"></a>Redes virtuais no leste dos EUA 2

Leste dos EUA 2 é a região primária que a Contoso usará para implantar recursos e serviços. Veja como a contoso arquitetará redes dentro dela:

- **Hub:** A VNet do Hub no leste dos EUA 2 é o ponto central de conectividade principal com o datacenter local.
- **VNets:** Spoke VNets no leste dos EUA 2 pode ser usado para isolar cargas de trabalho, se necessário. Além da VNet do Hub, a contoso terá dois VNets spoke no leste dos EUA 2:
  - **VNET-dev-EUS2**. Essa VNet fornecerá à equipe de desenvolvimento e teste uma rede totalmente funcional para projetos de desenvolvimento. Ele atuará como uma área piloto de produção e dependerá da infraestrutura de produção para funcionar.
    - **VNET-prod-EUS2**. Os componentes de produção IaaS do Azure estarão localizados nesta rede.
  - Cada VNet terá seu próprio espaço de endereço exclusivo, sem sobreposição. A Contoso pretende configurar o roteamento sem a necessidade de NAT.
- **Sub-redes:**
  - Haverá uma sub-rede em cada rede para cada camada de aplicativo
  - Cada sub-rede na rede de produção terá uma sub-rede correspondente na VNet de desenvolvimento.
  - Além disso, a rede de produção tem uma sub-rede para controladores de domínio.

VNets no leste dos EUA 2 estão resumidos na tabela a seguir.

**Rede virtual** | **Range** | **Pares**
--- | --- | ---
**VNET-HUB-EUS2** | 10.240.0.0/20 | VNET-HUB-CUS2, VNET-DEV-EUS2, VNET-PROD-EUS2
**VNET-DEV-EUS2** | 10.245.16.0/20 | VNET-HUB-EUS2
**VNET-PROD-EUS2** | 10.245.32.0/20 | VNET-HUB-EUS2, VNET-PROD-CUS

![Modelo de Hub e spoke na região primária](./media/contoso-migration-infrastructure/primary-hub-peer.png)

#### <a name="subnets-in-the-east-us-2-hub-network-vnet-hub-eus2"></a>Sub-redes na rede de Hub leste dos EUA 2 (VNET-HUB-EUS2)

**Sub-rede/zona** | **CIDR** | \* * Endereços IP utilizáveis
--- | --- | ---
**IB-UntrustZone** | 10.240.0.0/24 | 251
**IB-TrustZone** | 10.240.1.0/24 | 251
**OB-UntrustZone** | 10.240.2.0/24 | 251
**OB-TrustZone** | 10.240.3.0/24 | 251
**GatewaySubnets** | 10.240.10.0/24 | 251

#### <a name="subnets-in-the-east-us-2-dev-network-vnet-dev-eus2"></a>Sub-redes na rede de desenvolvimento leste dos EUA 2 (VNET-DEV-EUS2)

A VNet de desenvolvimento é usada pela equipe de desenvolvimento como uma área piloto de produção. Ele tem três sub-redes.

**Sub-rede** | **CIDR** | **Atende** | **Na sub-rede**
--- | --- | --- | ---
**DEV-FE-EUS2** | 10.245.16.0/22 | 1019 | VMs de camada front-end/web
**DEV-APP-EUS2** | 10.245.20.0/22 | 1019 | VMs da camada de aplicativo
**DEV-DB-EUS2** | 10.245.24.0/23 | 507 | VMs de banco de dados

#### <a name="subnets-in-the-east-us-2-production-network-vnet-prod-eus2"></a>Sub-redes na rede de produção leste dos EUA 2 (VNET-PROD-EUS2)

Os componentes do Azure IaaS estão localizados na rede de produção. Cada camada de aplicativo tem sua própria sub-rede. As sub-redes correspondem àquelas na rede de desenvolvimento, com a adição de uma sub-rede para controladores de domínio.

**Sub-rede** | **CIDR** | **Atende** | **Na sub-rede**
--- | --- | --- | ---
**PROD-FE-EUS2** | 10.245.32.0/22 | 1019 | VMs de camada front-end/web
**PROD-APP-EUS2** | 10.245.36.0/22 | 1019 | VMs da camada de aplicativo
**PROD-DB-EUS2** | 10.245.40.0/23 | 507 | VMs de banco de dados
**PROD-DC-EUS2** | 10.245.42.0/24 | 251 | VMs do controlador de domínio

![Arquitetura de rede de Hub](./media/contoso-migration-infrastructure/azure-networks-eus2.png)

#### <a name="virtual-networks-in-central-us-secondary-region"></a>Redes virtuais em EUA Central (região secundária)

EUA Central é a região secundária da contoso. Veja como a contoso arquitetará redes dentro dela:

- **Hub:** A VNet do Hub no leste dos EUA 2 é o ponto central de conectividade com o datacenter local, e o VNets de spoke no leste dos EUA 2 pode ser usado para isolar cargas de trabalho, se necessário, gerenciado separadamente de outros spokes.
- **VNets:** A contoso terá duas VNets no EUA Central:
  - VNET-PROD-CUS. Essa VNet é uma rede de produção, semelhante a VNET-PROD_EUS2.
  - VNET-ASR-CUS. Essa VNet atuará como um local em que as VMs são criadas após o failover do local ou como um local para VMs do Azure que são transferidas a partir da região primária para a secundária. Essa rede é semelhante às redes de produção, mas sem nenhum controlador de domínio.
  - Cada VNet na região terá seu próprio espaço de endereço, sem sobreposição. A contoso configurará o roteamento sem NAT.
- **Sub-redes:** As sub-redes serão arquitetadas de forma semelhante àquelas no leste dos EUA 2. A exceção é que a contoso não precisa de uma sub-rede para controladores de domínio.

Os VNets em EUA Central são resumidos na tabela a seguir.

**Rede virtual** | **Range** | **Pares**
--- | --- | ---
**VNET-HUB-CUS** | 10.250.0.0/20 | VNET-HUB-EUS2, VNET-ASR-CUS, VNET-PROD-CUS
**VNET-ASR-CUS** | 10.255.16.0/20 | VNET-HUB-CUS, VNET-PROD-CUS
**VNET-PROD-CUS** | 10.255.32.0/20 | VNET-HUB-CUS, VNET-ASR-CUS, VNET-PROD-EUS2

![Modelo de Hub e spoke em região emparelhada](./media/contoso-migration-infrastructure/paired-hub-peer.png)

#### <a name="subnets-in-the-central-us-hub-network-vnet-hub-cus"></a>Sub-redes na rede de Hub de EUA Central (VNET-HUB-CUS)

**Sub-rede** | **CIDR** | **Endereços IP utilizáveis**
--- | --- | ---
**IB-UntrustZone** | 10.250.0.0/24 | 251
**IB-TrustZone** | 10.250.1.0/24 | 251
**OB-UntrustZone** | 10.250.2.0/24 | 251
**OB-TrustZone** | 10.250.3.0/24 | 251
**GatewaySubnet** | 10.250.2.0/24 | 251

#### <a name="subnets-in-the-central-us-production-network-vnet-prod-cus"></a>Sub-redes na rede de produção EUA Central (VNET-PROD-CUS)

Em paralelo com a rede de produção na região principal leste dos EUA 2, há uma rede de produção na região de EUA Central secundária.

**Sub-rede** | **CIDR** | **Atende** | **Na sub-rede**
--- | --- | --- | ---
**PROD-FE-CUS** | 10.255.32.0/22 | 1019 | VMs de front-ends/camada da Web
**PROD-APP-CUS** | 10.255.36.0/22 | 1019 | VMs da camada de aplicativo
**PROD-DB-CUS** | 10.255.40.0/23 | 507 | VMs de banco de dados
**PROD-DC-CUS** | 10.255.42.0/24 | 251 | VMs do controlador de domínio

#### <a name="subnets-in-the-central-us-failoverrecovery-network-in-central-us-vnet-asr-cus"></a>Sub-redes na EUA Central rede de failover/recuperação no EUA Central (VNET-ASR-CUS)

A rede VNET-ASR-CUS é usada para fins de failover entre regiões. Site Recovery será usado para replicar e fazer failover de VMs do Azure entre as regiões. Ele também funciona como um datacenter da Contoso para a rede do Azure para cargas de trabalho protegidas que permanecem no local, mas fazer failover para o Azure para recuperação de desastre.

VNET-ASR-CUS é a mesma sub-rede básica que a VNet de produção no leste dos EUA 2, mas sem a necessidade de uma sub-rede do controlador de domínio.

**Sub-rede** | **CIDR** | **Atende** | **Na sub-rede**
--- | --- | --- | ---
**ASR-FE-CUS** | 10.255.16.0/22 | 1019 | VMs de front-ends/camada da Web
**ASR-APP-CUS** | 10.255.20.0/22 | 1019 | VMs da camada de aplicativo
**ASR-DB-CUS** | 10.255.24.0/23 | 507 | VMs de banco de dados

![Arquitetura de rede de Hub](./media/contoso-migration-infrastructure/azure-networks-cus.png)

#### <a name="configure-peered-connections"></a>Configurar conexões emparelhadas

O Hub em cada região será emparelhado com o Hub na outra região e para todos os VNets dentro da região do Hub. Isso permite que os hubs se comuniquem e exibam todos os VNets em uma região. Observe que:

- O emparelhamento cria uma conexão de dois lados. Um do par inicial na primeira VNet e outro na segunda VNet.
- Em uma implantação híbrida, o tráfego que passa entre os pares precisa estar visível na conexão VPN entre o datacenter local e o Azure. Para habilitar isso, há algumas configurações específicas que devem ser definidas em conexões emparelhadas.

Para todas as conexões do spoke VNets por meio do hub para o datacenter local, a contoso precisa permitir que o tráfego seja encaminhado e transversal os gateways de VPN.

##### <a name="domain-controller"></a>Controlador de domínio

Para os controladores de domínio na rede VNET-PROD-EUS2, a contoso deseja que o tráfego flua entre a rede de Hub/produção EUS2 e pela conexão VPN para o local. Para fazer isso, os administradores da Contoso devem permitir o seguinte:

1. **Permitir tráfego encaminhado** e **permitir configurações de trânsito de gateway** na conexão emparelhada. Em nosso exemplo, essa seria a conexão VNET-HUB-EUS2 para VNET-PROD-EUS2.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering1.png)

2. **Permita o tráfego encaminhado** e **use gateways remotos** no outro lado do emparelhamento, na conexão VNET-prod-EUS2 para VNET-Hub-EUS2.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering2.png)

3. No local, eles configurarão uma rota estática que direciona o tráfego local para rotear pelo túnel VPN para a VNet. A configuração seria concluída no gateway que fornece o túnel VPN da Contoso para o Azure. Eles usam o RRAS para isso.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering3.png)

##### <a name="production-networks"></a>Redes de produção

Uma rede de mesmo nível spoke não pode ver uma rede de mesmo nível spoke em outra região por meio de um Hub.

Para redes de produção da Contoso em ambas as regiões para ver entre si, os administradores da Contoso precisam criar uma conexão emparelhada direta para VNET-PROD-EUS2 e ventilação-PROD-CUS.

![Emparelhamento](./media/contoso-migration-infrastructure/peering4.png)

### <a name="set-up-dns"></a>Configurar o DNS

Ao implantar recursos em redes virtuais, você tem algumas opções para a resolução de nomes de domínio. Você pode usar a resolução de nomes fornecida pelo Azure ou fornecer servidores DNS para resolução. O tipo de resolução de nomes que você usa depende de como seus recursos precisam se comunicar entre si. Obtenha [mais informações](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances#azure-provided-name-resolution) sobre o serviço DNS do Azure.

Os administradores da Contoso decidiram que o serviço DNS do Azure não é uma boa opção no ambiente híbrido. Em vez disso, eles usarão os servidores DNS locais.

- Como essa é uma rede híbrida, todas as VMs locais e no Azure precisam ser capazes de resolver nomes para funcionar corretamente. Isso significa que as configurações de DNS personalizadas devem ser aplicadas a todos os VNets.
- Atualmente, a contoso tem DCs implantados no datacenter da Contoso e nas filiais. Os servidores DNS primários são CONTOSODC1 (172.16.0.10) e CONTOSODC2 (172.16.0.1)
- Quando os VNets forem implantados, os controladores de domínio locais serão definidos para serem usados como servidores DNS nas redes.
- Para configurar isso, ao usar o DNS personalizado na VNet, o endereço IP de resolvedores recursivos do Azure (como 168.63.129.16) deve ser adicionado à lista DNS. Para fazer isso, a Contoso configura as configurações do servidor DNS em cada VNet. Por exemplo, as configurações de DNS personalizadas para a rede VNET-HUB-EUS2 seriam as seguintes:

    ![DNS personalizado](./media/contoso-migration-infrastructure/custom-dns.png)

Além dos controladores de domínio locais, a contoso vai implementar mais quatro para dar suporte às redes do Azure, duas para cada região. Veja o que a contoso implantará no Azure.

**Região** | **ORIGEM** | **Rede virtual** | **Sub-rede** | **Endereço IP**
--- | --- | --- | --- | ---
EUS2 | CONTOSODC3 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.4
EUS2 | CONTOSODC4 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.5
CUS | CONTOSODC5 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4
CUS | CONTOSODC6 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4

Depois de implantar os controladores de domínio locais, a contoso precisa atualizar as configurações de DNS em redes em qualquer região para incluir os novos controladores de domínio na lista de servidores DNS.

#### <a name="set-up-domain-controllers-in-azure"></a>Configurar controladores de domínio no Azure

Depois de atualizar as configurações de rede, os administradores da Contoso estão prontos para criar os controladores de domínio no Azure.

1. No portal do Azure, eles implantam uma nova VM do Windows Server na VNet apropriada.
2. Eles criam conjuntos de disponibilidade em cada local para a VM. Os conjuntos de disponibilidade fazem o seguinte:

    - Verifique se a malha do Azure separa as VMs em diferentes infraestruturas na região do Azure.
    - Permite que a contoso esteja qualificada para o SLA de 99,95% para VMs no Azure. [Saiba mais](https://docs.microsoft.com/azure/virtual-machines/windows/tutorial-availability-sets).

    ![Grupo de disponibilidade](./media/contoso-migration-infrastructure/availability-group.png)

3. Depois que a VM é implantada, ela abre a interface de rede para a VM. Eles definem o endereço IP privado como estático e especificam um endereço válido.

    ![NIC DA VM](./media/contoso-migration-infrastructure/vm-nic.png)

4. Agora, eles anexam um novo disco de dados à VM. Esse disco contém o banco de dados Active Directory e o compartilhamento SYSVOL.
    - O tamanho do disco determinará o número de IOPS que ele suporta.
    - Com o tempo, o tamanho do disco pode precisar aumentar conforme o ambiente cresce.
    - A unidade não deve ser definida como leitura/gravação para o cache de host. Active Directory bancos de dados não dão suporte a isso.

     ![Active Directory disco](./media/contoso-migration-infrastructure/ad-disk.png)

5. Depois que o disco é adicionado, eles se conectam à VM por Área de Trabalho Remota e abrem Gerenciador do Servidor.

6. Em seguida, nos **serviços de arquivo e armazenamento**, eles executam o assistente de novo volume, garantindo que a unidade receba a letra F: ou acima na VM local.

     ![Assistente de novo volume](./media/contoso-migration-infrastructure/volume-wizard.png)

7. No Gerenciador do Servidor, eles adicionam a função de **Active Directory Domain Services** . Em seguida, eles configuram a VM como um controlador de domínio.

      ![Função de servidor](./media/contoso-migration-infrastructure/server-role.png)

8. Depois que a VM é configurada como um DC e reinicializada, ela abre o Gerenciador de DNS e configura o resolvedor de DNS do Azure como um encaminhador. Isso permite que o DC encaminhe as consultas DNS que ele não pode resolver no DNS do Azure.

    ![Encaminhador DNS](./media/contoso-migration-infrastructure/dns-forwarder.png)

9. Agora, eles atualizam as configurações de DNS personalizadas para cada VNet com o controlador de domínio apropriado para a região da VNet. Eles incluem DCs locais na lista.

### <a name="set-up-active-directory"></a>Configurar o Active Directory

Active Directory é um serviço crítico em rede e deve ser configurado corretamente. Os administradores da Contoso criarão Active Directory sites para o datacenter da Contoso e para as regiões EUS2 e CUS.

1. Eles criam dois novos sites (AZURE-EUS2 e AZURE-CUS) junto com o site do datacenter (ContosoDatacenter).
2. Depois de criar os sites, eles criam sub-redes nos sites, para corresponder ao VNets e ao datacenter.

    ![Sub-redes DC](./media/contoso-migration-infrastructure/dc-subnets.png)

3. Em seguida, eles criam dois links de site para conectar tudo. Os controladores de domínio devem ser movidos para seu local.

    ![Links de DC](./media/contoso-migration-infrastructure/dc-links.png)

4. Depois que tudo estiver configurado, a topologia de replicação do Active Directory estará em vigor.

    ![Replicação de DC](./media/contoso-migration-infrastructure/ad-resolution.png)

5. Com tudo concluído, uma lista de controladores de domínio e sites é mostrada no Centro Administrativo do Active Directory local.

    ![Centro Administrativo do Active Directory](./media/contoso-migration-infrastructure/ad-center.png)

## <a name="step-5-plan-for-governance"></a>Etapa 5: planejar a governança

O Azure fornece uma variedade de controles de governança entre serviços e a plataforma Azure. [Leia mais](https://docs.microsoft.com/azure/security/governance-in-azure) para obter uma compreensão básica das opções.

À medida que eles configuram o controle de acesso e identidade, a contoso já começou a colocar alguns aspectos de governança e segurança em vigor. Em grande escala, há três áreas que precisam ser consideradas:

- **Política:** Azure Policy aplica e impõe regras e efeitos sobre seus recursos, para que os recursos permaneçam em conformidade com os requisitos e SLAs corporativos.
- **Bloqueios:** O Azure permite que você bloqueie assinaturas, grupos de recursos e outros recursos, para que eles só possam ser modificados por aqueles com autoridade para fazer isso.
- **Marcas:** Os recursos podem ser controlados, auditados e gerenciados com marcas. As marcas anexam metadados a recursos, fornecendo informações sobre recursos ou proprietários.

### <a name="set-up-policies"></a>Configurar políticas

O serviço de Azure Policy avalia seus recursos, verificando aqueles que não estão em conformidade com as definições de política que você tem em vigor. Por exemplo, você pode ter uma política que permite apenas determinados tipos de VMs ou requer que os recursos tenham uma marca específica.

As políticas especificam uma definição de política e uma atribuição de política especifica o escopo no qual uma política deve ser aplicada. O escopo pode variar de um grupo de gerenciamento para um grupo de recursos. [Saiba mais](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) sobre como criar e gerenciar políticas.

A contoso deseja começar com algumas políticas:

- Ele quer uma política para garantir que os recursos só possam ser implantados nas regiões EUS2 e CUS.
- Ele deseja limitar os SKUs de VM somente a SKUs aprovados. A intenção é garantir que os SKUs de VM caros não sejam usados.

#### <a name="limit-resources-to-regions"></a>Limitar recursos a regiões

A contoso usa os **locais permitidos** de definição de política interna para limitar as regiões de recursos.

1. Na portal do Azure, selecione **todos os serviços**e procure **política**.
2. Selecione **atribuições**  > **atribuir política**.
3. Na lista de políticas, selecione **locais permitidos**.
4. Defina **escopo** como o nome da assinatura do Azure e selecione as duas regiões na lista de permissões.

    ![Regiões permitidas da política](./media/contoso-migration-infrastructure/policy-region.png)

5. Por padrão, a política é definida com **Deny**, o que significa que, se alguém iniciar uma implantação na assinatura que não está em EUS2 ou cus, a implantação falhará. Veja o que acontece se alguém na assinatura da Contoso tentar configurar uma implantação no oeste dos EUA.

    ![Falha na política](./media/contoso-migration-infrastructure/policy-failed.png)

#### <a name="allow-specific-vm-skus"></a>Permitir SKUs de VM específicas

A Contoso usará a definição de política interna **permitir que as SKUs de máquinas virtuais** limitem o tipo de VMs que podem ser criadas na assinatura.

![SKU da política](./media/contoso-migration-infrastructure/policy-sku.png)

#### <a name="check-policy-compliance"></a>Verificar conformidade da política

As políticas entram em vigor imediatamente e a Contoso pode verificar os recursos quanto à conformidade.

1. No portal do Azure, selecione o link **conformidade** .
2. O painel conformidade é exibido. Você pode fazer uma busca detalhada para obter mais detalhes.

    ![Conformidade de política](./media/contoso-migration-infrastructure/policy-compliance.png)

### <a name="set-up-locks"></a>Configurar bloqueios

A contoso vem muito usando a estrutura de ITIL para o gerenciamento de seus sistemas. Um dos aspectos mais importantes da estrutura é o controle de alterações e a contoso deseja garantir que o controle de alterações seja implementado na implantação do Azure.

A contoso vai implementar bloqueios da seguinte maneira:

- Qualquer componente de produção ou de failover deve estar em um grupo de recursos que tenha um bloqueio somente leitura. Isso significa que para modificar ou excluir itens de produção, o bloqueio deve ser removido.
- Os grupos de recursos de não produção terão bloqueios de CanNotDelete. Isso significa que os usuários autorizados podem ler ou modificar um recurso, mas não podem excluí-lo.

[Saiba mais](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) sobre bloqueios.

### <a name="set-up-tagging"></a>Configurar marcação

Para acompanhar os recursos conforme eles são adicionados, será cada vez mais importante para a contoso associar recursos a um departamento, cliente e ambiente apropriados.

Além de fornecer informações sobre os recursos e proprietários, as marcas permitirão que a contoso agregue e agrupe recursos e use esses dados para fins de estorno.

A contoso precisa visualizar seus ativos do Azure de uma maneira que faça sentido para os negócios. Por exemplo, por função ou departamento. Observe que os recursos não precisam residir no mesmo grupo de recursos para compartilhar uma marca. A contoso criará uma taxonomia de marca simples para que todos usem as mesmas marcas.

**Nome da marca** | **Valor**
--- | ---
CostCenter | 12345: deve ser um centro de custo válido do SAP.
BusinessUnit | Nome da unidade de negócios (do SAP). Corresponde a CostCenter.
ApplicationTeam | Alias de email da equipe que possui suporte para o aplicativo.
CatalogName | Nome do aplicativo ou Shareservices, de acordo com o catálogo de serviços ao qual o recurso dá suporte.
ServiceManager | Alias de email do Service Manager ITIL para o recurso.
COBPriority | Prioridade definida pelo negócio para BCDR. Valores de 1-5.
VARIÁVEL | DEV, STG, PROD são os valores possíveis. Representando o desenvolvimento, o preparo e a produção.

Por exemplo:

 ![Marcas do Azure](./media/contoso-migration-infrastructure/azure-tag.png)

Depois de criar a marca, a contoso voltará e criará novas definições e atribuições de política para impor o uso das marcas necessárias em toda a organização.

## <a name="step-6-consider-security"></a>Etapa 6: considerar a segurança

A segurança é crucial na nuvem, e o Azure fornece uma ampla variedade de ferramentas e recursos de segurança. Eles ajudam você a criar soluções seguras, na plataforma segura do Azure. Leia [a confiança na nuvem confiável](https://azure.microsoft.com/overview/trusted-cloud) para saber mais sobre a segurança do Azure.

Há alguns aspectos a serem considerados pela contoso:

- **Central de segurança do Azure:** A central de segurança do Azure fornece gerenciamento de segurança unificado e proteção avançada contra ameaças em cargas de trabalho de nuvem híbrida. Com a central de segurança, você pode aplicar políticas de segurança em suas cargas de trabalho, limitar sua exposição a ameaças e detectar e responder a ataques. [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-intro).
- **NSGs (grupos de segurança de rede):** Um NSG é um filtro (firewall) que contém uma lista de regras de segurança que, quando aplicada, permitem ou nega o tráfego de rede aos recursos conectados ao VNets do Azure. [Saiba mais](https://docs.microsoft.com/azure/virtual-network/security-overview).
- **Criptografia de dados:** Azure Disk Encryption é um recurso que ajuda você a criptografar seus discos de máquina virtual IaaS Windows e Linux. [Saiba mais](https://docs.microsoft.com/azure/security/azure-security-encryption-atrest).

### <a name="work-with-the-azure-security-center"></a>Trabalhar com a central de segurança do Azure

A Contoso está procurando uma visão rápida da postura de segurança de sua nova nuvem híbrida e, especificamente, de suas cargas de trabalho do Azure. Como resultado, a Contoso decidiu implementar a central de segurança do Azure, começando com os seguintes recursos:

- Gerenciamento de política centralizado
- Avaliação contínua
- Recomendações acionáveis

#### <a name="centralize-policy-management"></a>Centralizar o gerenciamento de políticas

Com o gerenciamento centralizado de políticas, a contoso garantirá a conformidade com os requisitos de segurança ao gerenciar centralmente políticas de segurança em todo o ambiente. Ele pode simplesmente implementar rapidamente uma política que se aplica a todos os seus recursos do Azure.

![Política de segurança](./media/contoso-migration-infrastructure/security-policy.png)

#### <a name="assess-and-action"></a>Avaliação e ação

A contoso aproveitará a avaliação de segurança contínua que monitora a segurança de computadores, redes, armazenamento, dados e aplicativos; para descobrir possíveis problemas de segurança.

- A central de segurança analisará o estado de segurança da computação, da infraestrutura e dos recursos de dados da Contoso e dos aplicativos e serviços do Azure.
- A avaliação contínua ajuda a equipe de operações da Contoso a descobrir possíveis problemas de segurança, como sistemas com atualizações de segurança ausentes ou portas de rede expostas.
- Em particular, a contoso deseja ter certeza de que todas as VMs estão protegidas. A central de segurança ajuda com isso, verificando a integridade da VM e fazendo recomendações priorizadas e acionáveis para corrigir vulnerabilidades de segurança antes que elas sejam exploradas.

![Monitoramento](./media/contoso-migration-infrastructure/monitoring.png)

### <a name="work-with-nsgs"></a>Trabalhar com NSGs

A Contoso pode limitar o tráfego de rede para recursos em uma rede virtual usando grupos de segurança de rede.

- Um grupo de segurança de rede contém uma lista de regras de segurança que permitem ou negam o tráfego de rede de entrada ou saída com base no endereço IP de origem ou de destino, porta e protocolo.
- Quando aplicado a uma sub-rede, as regras são aplicadas a todos os recursos na sub-rede. Além das interfaces de rede, isso inclui instâncias dos serviços do Azure implantados na sub-rede.
- Os ASGs (grupos de segurança de aplicativo) permitem que você configure a segurança de rede como uma extensão natural de uma estrutura de aplicativo, permitindo que você agrupe as VMs e defina as políticas de segurança de rede com base nesses grupos.
  - Os grupos de segurança de aplicativo significam que a Contoso pode reutilizar a política de segurança em escala, sem a manutenção manual de endereços IP explícitos. A plataforma lida com a complexidade de endereços IP explícitos e vários conjuntos de regras, permitindo que você se concentre na lógica de negócios.
  - A Contoso pode especificar um grupo de segurança de aplicativo como a origem e o destino em uma regra de segurança. Depois que uma política de segurança é definida, a Contoso pode criar VMs e atribuir as NICs da VM a um grupo.

A contoso implementará uma mistura de NSGs e ASGs. A contoso se preocupa com o gerenciamento de NSG. Também está preocupado com o uso excessivo do NSGs e a complexidade adicional para a equipe de operações. Veja o que a contoso fará:

- Todo o tráfego dentro e fora de todas as sub-redes (Norte-Sul), estará sujeito a uma regra de NSG, exceto para o GatewaySubnets nas redes de Hub.
- Todos os firewalls ou controladores de domínio serão protegidos por NSGs de sub-rede e NIC NSGs.
- Todos os aplicativos de produção terão ASGs aplicados.

A contoso criou um modelo de como isso irá procurar seus aplicativos.

![Segurança](./media/contoso-migration-infrastructure/asg.png)

Os NSGs associados ao ASGs serão configurados com privilégios mínimos para garantir que apenas os pacotes permitidos possam fluir de uma parte da rede para seu destino.

**Ação** | **Nome** | **Origem** | **Destino** | **Porta**
--- | --- | --- | --- | ---
PERMITIR | AllowiInternetToFE | VNET-HUB-EUS1/IB-TrustZone | APP1-FE 80, 443
PERMITIR | AllowWebToApp | APP1-FE | APP1 – APLICATIVO | 80, 443
PERMITIR | AllowAppToDB | APP1 – APLICATIVO | APP1 – BD | 1433
Negar | DenyAllInbound | Outro | Outro | Outro

### <a name="encrypt-data"></a>Criptografar dados

Azure Disk Encryption integra-se com o Azure Key Vault para ajudar a controlar e gerenciar as chaves de criptografia de disco e os segredos em uma assinatura Key Vault. Ele garante que todos os dados em discos de VM sejam criptografados em repouso no armazenamento do Azure.

- A contoso determinou que VMs específicas exigem Criptografia.
- A contoso aplicará criptografia a VMs com dados de cliente, confidenciais ou PPI.

## <a name="conclusion"></a>Conclusão

Neste artigo, a contoso configurou uma infraestrutura e uma política do Azure para assinatura do Azure, identidade híbrida, recuperação de desastre, rede, governança e segurança.

Nem todas as etapas que a contoso concluiu aqui são necessárias para uma migração para a nuvem. Nesse caso, ele queria planejar uma infraestrutura de rede que pode ser usada para todos os tipos de migrações e é segura, resiliente e escalonável.

Com essa infraestrutura em vigor, a Contoso está pronta para prosseguir e experimentar a migração.

## <a name="next-steps"></a>Próximos passos

Depois de configurar sua infraestrutura do Azure, a Contoso está pronta para começar a migrar as cargas de trabalho para a nuvem. Consulte a seção [visão geral dos padrões de migração e exemplos](./contoso-migration-overview.md#windows-server-workloads) para uma seleção de cenários usando essa infraestrutura de exemplo como um destino de migração.
