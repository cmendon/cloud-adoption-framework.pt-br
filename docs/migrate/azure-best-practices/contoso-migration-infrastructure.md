---
title: Implante uma infraestrutura de migração
description: Saiba como a Contoso define uma infraestrutura do Azure para a migração para o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/1/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 4d8a7b53722de4b356753626d0cc695fa1a77596
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807505"
---
# <a name="deploy-a-migration-infrastructure"></a>Implante uma infraestrutura de migração

Este artigo mostra como a empresa fictícia Contoso preparou sua infraestrutura local para migração, configurou uma infraestrutura do Azure para preparar a migração e vem realizando negócios em um ambiente híbrido. Ao consultar este exemplo para planejar seus próprios esforços de migração de infraestrutura, lembre-se do seguinte:

- A arquitetura de exemplo fornecida é específica da Contoso. Examine as necessidades de negócios, a estrutura e os requisitos técnicos da sua organização ao tomar decisões de infraestrutura importantes sobre design de assinatura ou arquitetura de rede.
- Sua estratégia de migração é que definirá se você precisará de todos os elementos descritos neste artigo ou não. Por exemplo, se você estiver criando aplicativos de nuvem nativo somente no Azure, talvez seja necessário uma estrutura de rede menos complexa.

## <a name="overview"></a>Visão Geral

Antes de a Contoso poder migrar para o Azure, é fundamental preparar uma infraestrutura do Azure. Em geral, a Contoso precisa pensar em seis áreas amplas:

> [!div class="checklist"]
>
> - **Etapa 1: assinaturas do Azure.** Como a Contoso comprará o Azure e interagirá com os serviços e a plataforma do Azure?
> - **Etapa 2: identidade híbrida.** Como ela gerenciará e controlará o acesso a recursos locais e do Azure após a migração? Como a Contoso estende ou move o gerenciamento de identidade para a nuvem?
> - **Etapa 3: recuperação de desastres e resiliência.** Como a Contoso garantirá que seus aplicativos e infraestrutura sejam resilientes em caso de interrupções e desastres?
> - **Etapa 4: rede.** Como a Contoso deve criar uma infraestrutura de rede e estabelecer a conectividade entre o datacenter local e o Azure?
> - **Etapa 5: segurança.** Como isso protegerá a implantação híbrida/do Azure?
> - **Etapa 6: governança.** Como a Contoso manterá a implantação alinhada aos requisitos de governança e de segurança?

## <a name="before-you-start"></a>Antes de começar

Antes de começar olhando para a infraestrutura, você talvez queira ler algumas informações básicas sobre os recursos do Azure que discutimos neste artigo:

- Há várias opções disponíveis para a compra de acesso ao Azure, incluindo o modelo de Pagamento Conforme o Uso, o EA (Contrato Enterprise), o Licenciamento Open de revendedores ou Parceiros da Microsoft, conhecidos como CSPs (Provedores de Soluções na Nuvem). Saiba mais sobre [opções de compra](https://azure.microsoft.com/pricing/purchase-options)e leia sobre como [assinaturas do Azure são organizadas](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).
- Obtenha uma visão geral da [identidade e do gerenciamento de acesso do Azure](https://www.microsoft.com/trustcenter/security/identity). Em particular, saiba mais sobre o [Azure Active Directory e sobre como estender o Active Directory local para a nuvem](https://docs.microsoft.com/azure/active-directory/identity-fundamentals). Há um livro eletrônico útil para download sobre [de identidade e acesso de gerenciamento (IAM) em um ambiente híbrido](https://azure.microsoft.com/resources/hybrid-cloud-identity).
- O Azure fornece uma poderosa infraestrutura de rede com as opções para conectividade híbrida. Obter uma visão geral de [controle de acesso de rede e a rede](https://docs.microsoft.com/azure/security/security-network-overview).
- Obter uma introdução à [segurança do Azure](https://docs.microsoft.com/azure/security/azure-security)e leia sobre como criar um plano para [governança](https://docs.microsoft.com/azure/security/governance-in-azure).

## <a name="on-premises-architecture"></a>Arquitetura local

Aqui está um diagrama que mostra a atual infraestrutura local Contoso.

 ![Arquitetura da Contoso](./media/contoso-migration-infrastructure/contoso-architecture.png)

- A Contoso tem um data center principal localizado na cidade de Nova York do Leste dos Estados Unidos.
- Há três branches locais adicionais nos Estados Unidos.
- O data center principal está conectado à internet com uma conexão de ethernet metro fibra (500 mbps).
- Cada ramificação está conectada localmente à internet usando conexões da classe de negócios, com túneis VPN IPSec para o data center principal. Isso permite que toda a rede fique permanentemente conectada e otimiza a conectividade com a Internet.
- O data center principal é totalmente virtualizado com o VMware. A Contoso tem dois hosts de virtualização ESXi 6.5, gerenciados pelo vCenter Server 6.5.
- A Contoso usa o Active Directory para gerenciamento de identidade e os servidores DNS na rede interna.
- Executam os controladores de domínio no data center em máquinas virtuais do VMware. Os controladores de domínio no locais branches executados em servidores físicos.

## <a name="step-1-buy-and-subscribe-to-azure"></a>Etapa 1: Comprar e inscrever-se no Azure

A Contoso deve descobrir como comprar o Azure, como criar assinaturas e como licenciar serviços e recursos.

### <a name="buy-azure"></a>Comprar o Azure

A Contoso acompanha um [EA (Contrato Enterprise)](https://azure.microsoft.com/pricing/enterprise-agreement). Isso envolve um investimento antecipado no Azure, dando direito à Contoso para obter grandes benefícios, incluindo opções flexíveis de cobrança e otimização de preços.

- A Contoso estimou qual será o gasto anual do Azure. Quando assinou o contrato, a Contoso pagou integralmente pelo primeiro ano.
- A Contoso precisa usar todos os compromissos antes do final do ano ou perderá o valor desses dólares.
- Se, por algum motivo, a Contoso exceder seu compromisso e gastar mais, a Microsoft a cobrará pela diferença.
- Qualquer custo incorrido acima do compromisso será cobrado pelas mesmas taxas que as do contrato da Contoso. Não há penalidades para ultrapassar.

### <a name="manage-subscriptions"></a>Gerenciar Assinaturas

Depois de pagar pelo Azure, a Contoso precisa descobrir como gerenciar as assinaturas do Azure. A Contoso tem um Contrato Enterprise e, portanto, nenhum limite no número de assinaturas do Azure que podem ser configuradas.

- Um Registro Enterprise do Azure define como uma empresa modela e usa os serviços do Azure e define uma estrutura de controle central.
- Como primeira etapa, a Contoso definiu uma estrutura conhecida como um scaffold corporativo para seu Registro Enterprise. A Contoso usou [este artigo](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-subscription-governance) para ajudar a entender e criar um scaffold.
- Por enquanto, a Contoso decidiu usar uma abordagem funcional para gerenciar assinaturas.
  - Dentro de empresa, ela usará um único departamento de TI que controlará o orçamento do Azure. Esse será o único grupo com assinaturas.
  - A Contoso estenderá esse modelo no futuro para que outros grupos corporativos possam participar como departamentos no Registro Enterprise.
  - Dentro do departamento de TI, a Contoso estruturou duas assinaturas, Produção e Desenvolvimento.
  - Se a Contoso exigir assinaturas adicionais no futuro, ela precisará gerenciar o acesso, as políticas e a conformidade dessas assinaturas. A Contoso fará isso introduzindo [grupos de gerenciamento do Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview), como uma camada adicional acima de assinaturas.

  ![Estrutura do Enterprise](./media/contoso-migration-infrastructure/enterprise-structure.png)

### <a name="examine-licensing"></a>Examine o licenciamento

Com as assinaturas configuradas, a Contoso pode examinar o licenciamento da Microsoft. A estratégia de licenciamento dependerá dos recursos que a Contoso deseja migrar para o Azure e como as VMs e serviços do Azure serão selecionados e implantados.

#### <a name="azure-hybrid-benefit"></a>Benefício Híbrido do Azure

Ao implantar VMs no Azure, as imagens padrão incluem uma licença que cobrará Contoso por minuto pelo software que está sendo usado. No entanto, a Contoso tem sido um cliente de longo prazo da Microsoft e tem mantido EAs e licenças abertas com SA (Software Assurance).

O Benefício Híbrido do Azure fornece um método econômico para a migração da Contoso, permitindo que ela seja salva em VMs do Azure e em cargas de trabalho do SQL Server convertendo ou reutilizando licenças do Windows Server Datacenter e Standard Edition cobertas pelo Software Assurance. Isso permitirá que a Contoso pague uma taxa mais baixa de computação baseada em máquinas virtuais e o SQL Server. [Saiba mais](https://azure.microsoft.com/pricing/hybrid-benefit).

#### <a name="license-mobility"></a>Mobilidade de licenças

A Mobilidade de Licenças por meio do SA oferece aos clientes de Licenciamento por Volume da Microsoft, como a Contoso, a flexibilidade de implantar aplicativos de servidor qualificados com um SA ativo no Azure. Isso elimina a necessidade de adquirir novas licenças. Sem taxas de mobilidade associadas, licenças existentes podem facilmente ser implantadas no Azure. [Saiba mais](https://azure.microsoft.com/pricing/license-mobility).

#### <a name="reserve-instances-for-predictable-workloads"></a>Instâncias de reserva para cargas de trabalho previsíveis

Cargas de trabalho previsíveis são aquelas que sempre precisam estar disponíveis com as VMs em execução. Por exemplo, aplicativos de linha de negócios, como um sistema SAP ERP. Por outro lado, cargas de trabalho imprevisíveis são variáveis, como VMs ativadas durante a alta demanda e desativadas quando a demanda é baixa.

![Instância reservada](./media/contoso-migration-infrastructure/reserved-instance.png)

Em troca de usar instâncias reservadas para instâncias de VM específicas que precisam ser mantidas por longos períodos de tempo, o Console pode obter um desconto e uma capacidade priorizada. Usando [ Instâncias Reservadas do Azure ](https://azure.microsoft.com/pricing/reserved-vm-instances), junto com o Benefício Híbrido do Azure, a Contoso pode economizar até 82% de desconto nos preços normais de pagamento conforme o uso (abril de 2018).

## <a name="step-2-manage-hybrid-identity"></a>Etapa 2: Gerenciar identidade híbrida

Dar e controlar o acesso do usuário aos recursos do Azure com o IAM (gerenciamento de Identidades e Acesso) é uma etapa importante para reunir sua infraestrutura do Azure.

- A Contoso decide estender seu Active Directory local para a nuvem, em vez de criar um novo sistema separado no Azure.
- Ela cria um Active Directory baseado no Azure para fazer isso.
- A Contoso não tem o Office 365 implantado, portanto, ela precisa provisionar um novo Azure AD.
- O Office 365 usa o AD do Azure para gerenciamento de usuário. Se a Contoso estivesse usando o Office 365, ela já teria um locatário do Azure Active Directory e poderia usá-lo como o diretório primário.
- [Saiba mais](https://support.office.com/article/understanding-office-365-identity-and-azure-active-directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9) sobre o Azure AD para Office 365 e saiba [como adicionar uma assinatura](https://docs.microsoft.com/azure/active-directory/active-directory-how-subscriptions-associated-directory) a um locatário existente do Azure AD.

### <a name="create-an-azure-ad"></a>Criar um Azure AD

A Contoso está usando a edição Azure AD Gratuito incluída com uma assinatura do Azure. Os administradores da Contoso configuram um diretório da seguinte maneira:

1. No [portal do Azure](https://portal.azure.com), eles navegam até **Criar um recurso** > **Identidade** > **Azure Active Directory**.
2. Em **Criar diretório**, eles especificam um nome para o diretório, um nome de domínio inicial e a região na qual o diretório do Azure Active Directory deve ser criado.

    ![Criar AD do Azure](./media/contoso-migration-infrastructure/azure-ad-create.png)

    > [!NOTE]
    > O diretório criado tem um nome de domínio inicial na forma **domainname.onmicrosoft.com**. O nome não pode ser alterado ou excluído. Em vez disso, eles precisam adicionar seu nome de domínio registrado no Azure AD.

### <a name="add-the-domain-name"></a>Adicione o nome do domínio

Para usar seu nome de domínio padrão, os administradores da Contoso precisam adicioná-lo como um nome de domínio personalizado ao Azure AD. Essa opção permite que atribuam nomes de usuário conhecidos. Por exemplo, um usuário pode fazer logon com o endereço de email billg@contoso.com, em vez de precisar de billg@contosomigration.microsoft.com.

Para configurar um nome de domínio personalizado que ele adiciona ao diretório, adicione uma entrada DNS e, em seguida, verifique o nome no Azure AD.

1. Em **nomes de domínios personalizados** > **Adicione um domínio personalizado**, eles adicionam o domínio.
2. Para usar uma entrada de DNS no Azure, eles precisam registrá-la no registrador de domínios.

    - No **nomes de domínio personalizado** lista, eles observam as informações de DNS para o nome. Ela está usando uma entrada MX.
    - Eles precisam acessar o nome do servidor para fazer isso. Eles fazem logon no domínio Contoso.com e criam um novo registro MX para a entrada DNS fornecida pelo Azure AD usando os detalhes observados.

3. Depois que os registros DNS se propagam, no nome dos detalhes do domínio, eles selecionam **Verificar** para conferir o nome de domínio personalizado.

     ![Azure AD DNS](./media/contoso-migration-infrastructure/azure-ad-dns.png)

### <a name="set-up-on-premises-and-azure-groups-and-users"></a>Definir locais e usuários e grupos do Azure

Agora que o Azure Active Directory está em funcionamento, a Contoso precisa adicionar funcionários aos grupos do Active Directory locais que serão sincronizados com o Azure Active Directory. Eles devem usar nomes de grupos locais que correspondam aos nomes de grupos de recursos no Azure. Isso torna mais fácil identificar correspondências para fins de sincronização.

#### <a name="create-resource-groups-in-azure"></a>Criar grupos de recursos no Azure

Grupos de recursos do Azure reúnem recursos do Azure. Usar um ID de grupo de recursos permite que o Azure passa executar operações em recursos dentro do grupo.

- Uma assinatura do Azure pode ter vários grupos de recursos, mas um grupo de recursos só pode existir em uma única assinatura.
- Além disso, um único grupo de recursos pode ter vários recursos, mas um recurso pode pertencer somente a um único grupo de recursos.

Os administradores da Contoso configuram os grupos de recursos do Azure conforme resumido na tabela a seguir.

<!-- markdownlint-disable MD033 -->

**Grupo de recursos** | **Detalhes**
--- | ---
**ContosoCobRG** | Esse grupo contém todos os recursos relacionados à continuidade de negócios (COB). Ele inclui os cofres que a Contoso usará para o serviço Azure Site Recovery e o serviço de Backup do Azure.<br/><br/> Ele também incluirá recursos usados para migração, incluindo as Migrações para Azure e o Serviço de Migração de Banco de Dados do Azure.
**ContosoDevRG** | Esse grupo contém recursos de desenvolvimento e teste.
**ContosoFailoverRG** | Esse grupo serve como uma zona de aterrissagem para failover de recursos.
**ContosoNetworkingRG** | Esse grupo contém todos os recursos de rede.
**ContosoRG** | Esse grupo contém recursos relacionados a bancos de dados e aplicativos de produção.

<!-- markdownlint-disable MD026 -->

Eles criam grupos de recursos, da seguinte maneira:

1. No portal do Azure > **grupos de recursos**, adicionam um grupo.
2. Para cada grupo, eles especificam um nome, a assinatura à qual pertence o grupo e a região.
3. Grupos de recursos aparecem na lista **Grupos de recursos**.

    ![Grupos de recursos](./media/contoso-migration-infrastructure/resource-groups.png)

##### <a name="scale-resource-groups"></a>Dimensionar grupos de recursos

No futuro, a Contoso adicionará outros grupos de recursos com base nas necessidades. Por exemplo, eles podem definir um grupo de recursos para cada aplicativo ou serviço para que possam ser gerenciados e protegidos independentemente.

#### <a name="create-matching-security-groups-on-premises"></a>Crie grupos de segurança correspondentes no local

1. No Active Directory local, os administradores da Contoso configuram grupos de segurança com nomes que correspondem aos nomes dos grupos de recursos do Azure.

    ![Grupos de segurança locais do Active Directory](./media/contoso-migration-infrastructure/on-prem-ad.png)

2. Para fins de gerenciamento, eles criam um grupo adicional que será adicionado a todos os outros grupos. Esse grupo terá direitos a todos os grupos de recursos no Azure. Um número limitado de administradores globais será adicionado a esse grupo.

### <a name="synchronize-active-directory"></a>Sincronizar o Active Directory

A Contoso deseja fornecer uma identidade comum para acessar recursos locais e na nuvem. Para fazer isso, ela integrará o Active Directory local ao Azure AD. Com esse modelo:

- Usuários e organizações podem aproveitar uma única identidade para acesso a aplicativos locais e na nuvem serviços como o Office 365 e milhares de outros sites na internet.
- Os administradores podem usar os grupos no Active Directory para implementar o [Controle de Acesso Baseado em Função (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) no Azure.

Para facilitar a integração, a Contoso usa a [ferramenta Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Quando você instala e configura a ferramenta em um controlador de domínio, ele sincroniza as identidades do Active Directory locais para o Azure Active Directory.

### <a name="download-the-tool"></a>Baixar a ferramenta

1. No portal do Azure, os administradores da Contoso acessam **Azure Active Directory** > **Azure AD Connect** e baixam a versão mais recente da ferramenta para o servidor que eles estão usando para sincronização.

    ![Baixar o Azure AD Connect](./media/contoso-migration-infrastructure/download-ad-connect.png)

2. Eles iniciam a instalação do **AzureADConnect.msi**, com **Usar configurações expressas**. Isso é a instalação mais comum e pode ser usado para uma topologia de floresta única com sincronização de hash de senha para autenticação.

    ![Assistente do Azure Active Directory Connect](./media/contoso-migration-infrastructure/ad-connect-wiz1.png)

3. Em **Conectar-se ao Azure Active Directory**, são especificadas as credenciais para conexão ao Azure Active Directory (no formato admin@contoso.com ou admin@contoso.onmicrosoft.com).

    ![Assistente do Azure Active Directory Connect](./media/contoso-migration-infrastructure/ad-connect-wiz2.png)

4. Em **Conectar-se ao AD DS**, são especificadas as credenciais para o Active Directory local (no formato CONTOSO\admin ou contoso.com\admin).

     ![Assistente do Azure Active Directory Connect](./media/contoso-migration-infrastructure/ad-connect-wiz3.png)

5. Em **Pronto para configurar**, a opção **Inicie o processo de sincronização quando a configuração for concluída** é selecionada para iniciar a sincronização imediatamente. Então eles instalam.

Observe que:

- A Contoso tem uma conexão direta para o Azure. Se seu Active Directory local estiver protegido por proxy, leia este [artigo](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-connectivity).

- Após a primeira sincronização, os objetos do Active Directory locais ficam visíveis no diretório do Azure Active Directory.

    ![Active Directory local no Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

- A equipe de TI da Contoso é representada em cada grupo, com base em sua função.

    ![Membros do Active Directory local no Azure](./media/contoso-migration-infrastructure/on-prem-ad-group-members.png)

### <a name="set-up-rbac"></a>Configurar o RBAC

O [controle de acesso baseado em função (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) do Azure permite o gerenciamento de acesso refinado para o Azure. Usando o RBAC, é possível conceder apenas a quantidade de acesso de que os usuários precisam para executar tarefas. Você atribui a função RBAC apropriada a usuários, grupos e aplicativos em um nível de escopo. O escopo de uma atribuição de função pode ser uma assinatura, um grupo de recursos ou um único recurso.

Agora, os administradores da Contoso atribuem funções aos grupos do Active Directory que eles sincronizaram no local.

1. No grupo de recursos **ControlCobRG**, eles selecionam **Controle de acesso (IAM)**  > **Adicionar atribuição de função**.
2. Em **Adicionar atribuição de função** > **Função**, > **Colaborador**, eles selecionam o grupo **ContosoCobRG** da lista. Em seguida, o grupo aparece na lista **Membros selecionados**.
3. Eles repetem isso com as mesmas permissões para os outros grupos de recursos (exceto para **ContosoAzureAdmins** ), adicionando as permissões de Colaborador à conta que corresponde ao grupo de recursos.
4. Para o grupo **ContosoAzureAdmins**, eles atribuem a função **Proprietário**.

    ![Membros do Active Directory local no Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

## <a name="step-3-design-for-resiliency"></a>Etapa 3: design para resiliência

### <a name="set-up-regions"></a>Configurar regiões

Recursos do Azure são implantados dentro de regiões.

- As regiões são organizadas em geografias e os requisitos de residência, soberania, conformidade e resiliência de dados são respeitados dentro dos limites geográficos.
- Uma região é composta por um conjunto de datacenters. Esses datacenters são implantados em um perímetro definido por latência e conectados por meio de uma rede regional dedicada de baixa latência.
- Cada região do Azure é associada a uma região diferente para garantir a resiliência.
- Leia sobre [regiões do Azure](https://azure.microsoft.com/global-infrastructure/regions)e entenda [como as regiões são emparelhadas](https://docs.microsoft.com/azure/best-practices-availability-paired-regions).

A Contoso escolheu o Leste dos EUA 2 (localizado na Virgínia) como a região primária e o EUA Central (localizado em Iowa) como a região secundária. Há duas razões para isso:

- O datacenter da Contoso está localizado em Nova York, e a Contoso considerou a latência para o datacenter mais próximo.
- A região Leste dos EUA 2 tem todos os serviço e os produtos que a Contoso precisa usar. Nem todas as regiões do Azure são as mesmas em termos de produtos e serviços disponíveis. Consulte [Produtos do Azure por região](https://azure.microsoft.com/global-infrastructure/services).
- O centro dos EUA é a região Azure emparelhada Leste dos EUA 2.

Como ela pensa no ambiente híbrido, a Contoso precisa considerar como criar resiliência e uma estratégia de recuperação de desastre para o design da região. Em larga escala, intervalo de estratégias de uma implantação de região única, que depende da plataforma Windows Azure, tais como domínios de falha e regional de emparelhamento para resiliência, por meio de para um ativo-ativo completo do modelo no qual os serviços de nuvem e o banco de dados de recursos são implantados e manutenção usuários de duas regiões.

A Contoso decidiu tomar uma estrada intermediária. Ela implantará aplicativos e recursos em uma região primária e manterá uma cópia completa da infraestrutura na região secundária que estará pronta para agir como um backup completo em caso de um grande desastre do aplicativo ou de falha na região.

### <a name="set-up-availability"></a>Configurar disponibilidade

**Conjuntos de disponibilidade:**

Os conjuntos de disponibilidade ajudam a proteger aplicativos e dados de uma falha de hardware e rede local em um datacenter.

- Os conjuntos de disponibilidade distribuem as VMs do Azure por diferentes hardwares físicos em um datacenter.
- Os domínios de falha representam o hardware subjacente com uma fonte de energia comum e um comutador de rede no datacenter. As VMs em um conjunto de disponibilidade são distribuídas por diferentes domínios de falha para minimizar interrupções causadas por um único hardware ou falha de rede.
- Os domínios de atualização representam o hardware subjacente que pode sofrer manutenção ou ser reiniciado ao mesmo tempo. Os conjuntos de disponibilidade também distribuem VMs em vários domínios de atualização para garantir que pelo menos uma instância seja executada o tempo todo.

A Contoso implementará conjuntos de disponibilidade sempre que as cargas de trabalho da VM exigirem alta disponibilidade. [Saiba mais](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability).

**Zonas de disponibilidade**:

As zonas de disponibilidade ajudam a proteger aplicativos e dados contra falhas que afetam um datacenter inteiro em uma região.

- Cada zona de disponibilidade representa um local físico exclusivo em uma região do Azure.
- Cada zona é composta por um ou mais datacenters equipados com energia, resfriamento e rede independentes.
- Há no mínimo três zonas separadas em todas as regiões habilitadas.
- A separação física de zonas dentro de uma região protege aplicativos e dados contra falhas no datacenter.

A Contoso implantará zonas de disponibilidade à medida que os aplicativos exigem escalabilidade, alta disponibilidade e resiliência. [Saiba mais](https://docs.microsoft.com/azure/availability-zones/az-overview).

### <a name="set-up-backup"></a>Configurar backup

**Backup do Azure:**

O Backup do Azure permite fazer backup e restaurar discos da VM do Azure.

- O backup do Azure permite fazer backups automatizados de imagens de disco da VM, colocadas no armazenamento do Azure.
- Os backups são consistentes com os aplicativos, garantindo que os dados sejam transacionalmente consistentes e que os aplicativos sejam inicializados após a restauração.
- O Backup do Azure oferece suporte ao armazenamento com redundância local (LRS) para replicar várias cópias de seus dados de backup em um datacenter, no caso de uma falha de hardware local.
- No caso de uma indisponibilidade regional, o Backup do Azure também oferece suporte ao armazenamento com redundância geográfica (GRS), replicando seus dados de backup para uma região secundária emparelhada.
- O Backup do Azure criptografa os dados em trânsito usando o AES 256. Os dados de backup em repouso são criptografados usando a [ Criptografia do Serviço de Armazenamento (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption).

A Contoso usará o Backup do Azure com GRS em todas as VMs de produção, para garantir o backup dos dados de carga de trabalho e pode ser restaurado rapidamente em caso de interrupção ou parada. [Saiba mais](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup).

### <a name="set-up-disaster-recovery"></a>Configurar recuperação de desastre

**Azure Site Recovery:**

O Azure Site Recovery ajuda a garantir a continuidade dos negócios mantendo os aplicativos de negócios e as cargas de trabalho em execução durante as interrupções.

- O Azure Site Recovery replica continuamente as VMs do Azure de uma região primária para uma secundária, garantindo cópias funcionais em ambos os locais.
- Caso haja uma indisponibilidade na região principal, seu aplicativo ou serviço passará a usar instâncias de VMs replicadas na região secundária, minimizando possíveis interrupções.
- Quando as operações retornarem ao normal, seus aplicativos ou serviços poderão fazer failback para as VMs na região primária.

A Contoso implementará o Azure Site Recovery para todas as VMs de produção usadas em cargas de trabalho críticas, garantindo o mínimo de parada durante uma interrupção na região principal. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

## <a name="step-4-design-a-network-infrastructure"></a>Etapa 4: projetar uma infraestrutura de rede

Com o design de região implementado, a Contoso está pronta para considerar uma estratégia de rede. Ela precisa pensar em como o datacenter local e o Azure se conectam e se comunicam entre si e em como projetar sua infraestrutura de rede no Azure. Especificamente a Contoso precisa:

- **Planejar a conectividade de rede híbrida.** Descubra como ela se conectará a redes locais e no Azure.
- **Projetar a infraestrutura de rede do Azure.** Decida como implantará redes em regiões. Como as redes se comunicarão dentro da mesma região e entre regiões?
- **Projetar e configurar redes do Azure.** Configurar redes do Azure e sub-redes e decidir o que residem nelas.

### <a name="plan-hybrid-network-connectivity"></a>Planejar a conectividade de rede híbrida

A Contoso considerou [inúmeras arquiteturas](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking) para redes híbridas entre o Azure e o datacenter local. Para obter mais informações, consulte [escolher uma solução para conectar uma rede local ao Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations).

Como um lembrete, a infraestrutura de rede local da Contoso atualmente é composta pelo datacenter em Nova York e branches locais na parte leste dos EUA. Todos os locais têm uma conexão de classe de negócios para a internet. Cada uma das filiais é conectada posteriormente ao datacenter através de um túnel VPN IPSec pela internet.

![Rede Contoso](./media/contoso-migration-infrastructure/contoso-networking.png)

Aqui está como a Contoso decidiu implementar conectividade híbrida:

1. Configure uma nova conexão de VPN site a site entre o datacenter da Contoso em Nova York e as duas regiões do Azure no Leste dos EUA 2 e centro dos EUA.
2. Roteará o tráfego do Branch office associado para redes virtuais do Azure por meio do data center principal da Contoso.
3. À medida que a Contoso expandir a implantação do Azure, ela estabelecerá uma conexão ExpressRoute entre o datacenter e as regiões do Azure. Quando isso acontecer, a Contoso reterá a conexão VPN site a site apenas para fins de failover.
    - [ Saiba mais ](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations) sobre como escolher entre uma solução híbrida de VPN e ExpressRoute.
    - Verifique os [ locais do ExpressRoute e suporte ](https://docs.microsoft.com/azure/expressroute/expressroute-locations-providers).

**Somente VPN:**

![Contoso VPN](./media/contoso-migration-infrastructure/hybrid-vpn.png)

**VPN e ExpressRoute:**

![Contoso VPN/rota expressa](./media/contoso-migration-infrastructure/hybrid-vpn-expressroute.png)

### <a name="design-the-azure-network-infrastructure"></a>Projetar a infraestrutura de rede do Azure

É essencial que a Contoso coloque as redes em funcionamento de forma a tornar a implantação híbrida segura e escalonável. Para fazer isso, a Contoso está adotando uma abordagem de longo prazo e está projetando VNETs (redes virtuais) para serem resilientes e preparadas para uso empresarial. [ Saiba mais ](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm) sobre o planejamento de VNets.

Para conectar as duas regiões, a Contoso decidiu implementar um modelo de rede de hub a hub:

- Dentro de cada região, a Contoso usará um modelo hub-spoke.
- Para conectar redes e hubs, a Contoso usará o emparelhamento de rede do Azure.

#### <a name="network-peering"></a>Emparelhamento de rede

O Azure fornece emparelhamento de rede para conectar VNets e hubs. O emparelhamento global permite conexões entre VNets / hubs em diferentes regiões. O emparelhamento local conecta VNets na mesma região. O emparelhamento VNet oferece várias vantagens:

- O tráfego de rede entre os VNets emparelhados é privado.
- O tráfego entre as VNets é mantido na rede backbone da Microsoft. Nenhuma Internet pública, gateways ou criptografia é necessária na comunicação entre as VNets.
- O emparelhamento fornece uma conexão padrão de baixa latência e alta largura de banda entre recursos em diferentes VNets.

[ Saiba mais ](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) sobre o emparelhamento de rede.

#### <a name="hub-to-hub-across-regions"></a>Hub a hub entre regiões

A Contoso implantará um hub em cada região. Um hub é uma rede virtual (VNet) no Azure que atua como um ponto central de conectividade à sua rede local. As VNets do hub se conectam entre si usando emparelhamento global da VNet. O emparelhamento global da VNet conecta o VNets nas regiões do Azure.

- O hub em cada região é direcionado para o hub parceiro na outra região.
- O hub é direcionado para todas as redes da região e pode se conectar a todos os recursos da rede.

    ![Emparelhamento global](./media/contoso-migration-infrastructure/global-peering.png)

#### <a name="hub-and-spoke-model-within-a-region"></a>Modelo hub-spoke dentro de uma região

Em cada região, a Contoso implantará VNets para diferentes fins, como redes spoke do hub da região. VNets dentro de uma região usam emparelhamentos para se conectar ao seu hub e entre si.

#### <a name="design-the-hub-network"></a>Projetar a rede de hub

Dentro do hub e do modelo de spoke que a Contoso escolheu, ela precisa pensar em como o tráfego do seu datacenter local, e da Internet, será roteado. Veja como a Contoso decidiu tratar o roteamento para os hubs Leste dos EUA 2 e EUA Central:

- A Contoso está criando uma rede conhecida como "reverse c", já que este é o caminho que os pacotes seguem da rede de entrada para a de saída.
- A arquitetura de rede tem dois limites, uma zona de perímetro front-end não confiável e uma zona confiável de back-end.
- Um firewall terá um adaptador de rede em cada zona, controlando o acesso a zonas confiáveis.
- Da internet:
  - O tráfego da Internet atingirá um endereço IP público com balanceamento de carga na rede de perímetro.
  - Esse tráfego é roteado pelo firewall e sujeito a regras de firewall.
  - Depois que os controles de acesso à rede forem implementados, o tráfego será encaminhado para o local apropriado na zona confiável.
  - O tráfego de saída da rede virtual será roteado para a Internet usando rotas definidas pelo usuário. O tráfego é forçado pelo firewall e inspecionado de acordo com as políticas da Contoso.
- No datacenter da Contoso:
  - O tráfego de entrada através de VPN site a site (ou ExpressRoute) atinge o endereço IP público do gateway da VPN do Azure.
  - O tráfego é roteado através do firewall e sujeito a regras de firewall.
  - Depois de aplicar regras de firewall, o tráfego é encaminhado para um balanceador de carga interno (SKU Standard) na sub-rede da zona interna confiável.
  - O tráfego de saída da sub-rede confiável para o datacenter local pela VPN é roteado através do firewall e das regras aplicadas antes de passar pela conexão VPN de site a site.

### <a name="design-and-set-up-azure-networks"></a>Projetar e configurar redes do Azure

Com uma topologia de rede e de roteamento em vigor, a Contoso está pronta para configurar suas redes e sub-redes do Azure.

- A Contoso implementará uma rede privada de Classe A no Azure (0.0.0.0 a 127.255.255.255). Isso funciona, uma vez que, localmente, ela tem um espaço de endereço privado Classe B 172.160.0/16, de modo que ela pode ter certeza de que não haverá sobreposição entre os intervalos de endereços.
- Ela implantará VNets nas regiões primárias e secundárias.
- A Contoso usará uma convenção de nomenclatura que inclui o prefixo **VNET** e a abreviação da região **EUS2** ou **CUS**. Usando este padrão, as redes de hub serão denominadas **VNET-HUB-EUS2** (Leste dos EUA 2) e **VNET-HUB-CUS** (EUA Central).
- A Contoso não tem uma [solução do IPAM](https://docs.microsoft.com/windows-server/networking/technologies/ipam/ipam-top), portanto, ela precisa planejar o roteamento de rede sem o NAT.

#### <a name="virtual-networks-in-east-us-2"></a>Redes virtuais no leste dos EUA 2

O Leste dos EUA 2 é a principal região que a Contoso usará para implantar recursos e serviços. Veja como a Contoso criará redes dentro dela:

- **Hub:** A VNet do Hub no leste dos EUA 2 é o ponto central de conectividade principal com o datacenter local.
- **VNets:** Spoke VNets no leste dos EUA 2 pode ser usado para isolar cargas de trabalho, se necessário. Além da VNet do Hub, a Contoso terá dois VNets falados no East US 2:
  - **VNET-DEV-EUS2**. Essa VNET fornecerá à equipe de desenvolvimento e teste uma rede totalmente funcional para projetos de desenvolvimento. Ele atuará como uma área piloto de produção e contará com a infraestrutura de produção para funcionar.
    - **VNET-PROD-EUS2**. Os componentes de produção de IaaS do Azure estarão localizados nessa rede.
  - Cada VNet terá seu próprio espaço de endereço exclusivo, sem sobreposição. O objetivo da Contoso é configurar o roteamento sem a necessidade de NAT.
- **Sub-redes:**
  - Haverá uma sub-rede em cada rede para cada camada de aplicativo
  - Cada sub-rede na rede de produção terá uma sub-rede correspondente na VNET de desenvolvimento.
  - Além disso, a rede de produção tem uma sub-rede para controladores de domínio.

Os VNets no Leste dos EUA 2 estão resumidos na tabela a seguir.

**Rede virtual** | **Range** | **Par**
--- | --- | ---
**VNET-HUB-EUS2** | 10.240.0.0/20 | VNET-HUB-CUS2, VNET-DEV-EUS2, VNET-PROD-EUS2
**VNET-DEV-EUS2** | 10.245.16.0/20 | VNET-HUB-EUS2
**VNET-PROD-EUS2** | 10.245.32.0/20 | VNET-HUB-EUS2, VNET-PROD-CUS

![Modelo hub-spoke na região primária](./media/contoso-migration-infrastructure/primary-hub-peer.png)

#### <a name="subnets-in-the-east-us-2-hub-network-vnet-hub-eus2"></a>Sub-redes na rede Hub 2 Leste US (rede virtual-HUB-EUS2)

**Região/sub-rede** | **CIDR** | ** Endereços IP utilizáveis
--- | --- | ---
**IB-UntrustZone** | 10.240.0.0/24 | 251
**IB-TrustZone** | 10.240.1.0/24 | 251
**OB-UntrustZone** | 10.240.2.0/24 | 251
**OB-TrustZone** | 10.240.3.0/24 | 251
**GatewaySubnets** | 10.240.10.0/24 | 251

#### <a name="subnets-in-the-east-us-2-dev-network-vnet-dev-eus2"></a>Sub-redes na rede East Dev 2 (VNET-DEV-EUS2)

A VNET de desenvolvimento é usada pela equipe de desenvolvimento, como uma área de produção piloto. Ele tem três estados.

**Sub-rede** | **CIDR** | **Endereços** | **Na Sub-rede**
--- | --- | --- | ---
**DESENVOLVIMENTO DE FE DE EUS2** | 10.245.16.0/22 | 1019 | VMs de front-ends/camadas da web
**DEV-APP-EUS2** | 10.245.20.0/22 | 1019 | Máquinas virtuais de camada de aplicativo
**DEV-APP-EUS2** | 10.245.24.0/23 | 507 | VMs de banco de dados

#### <a name="subnets-in-the-east-us-2-production-network-vnet-prod-eus2"></a>Sub-redes na rede de produção 2 Leste nos (VNET-PROD-EUS2)

Componentes de IaaS do Azure estão localizados na rede de produção. Cada camada de aplicativo tem sua própria sub-rede. As sub-redes correspondem às da rede de desenvolvimento, com a adição de uma sub-rede para controladores de domínio.

**Sub-rede** | **CIDR** | **Endereços** | **Na Sub-rede**
--- | --- | --- | ---
**PROD-FE-EUS2** | 10.245.32.0/22 | 1019 | VMs de front-ends/camadas da web
**PROD-APP-EUS2** | 10.245.36.0/22 | 1019 | Máquinas virtuais de camada de aplicativo
**PROD-DB-EUS2** | 10.245.40.0/23 | 507 | VMs de banco de dados
**PROD-DC-EUS2** | 10.245.42.0/24 | 251 | Máquinas virtuais do controlador de domínio

![Arquitetura de rede de hub](./media/contoso-migration-infrastructure/azure-networks-eus2.png)

#### <a name="virtual-networks-in-central-us-secondary-region"></a>Redes virtuais no centro dos EUA (região secundária)

Centro dos EUA é a região secundária da Contoso. Veja como a Contoso criará redes dentro dela:

- **Hub:** A VNet do Hub no leste dos EUA 2 é o ponto central de conectividade com o datacenter local, e o VNets de spoke no leste dos EUA 2 pode ser usado para isolar cargas de trabalho, se necessário, gerenciado separadamente de outros spokes.
- **VNets:** A contoso terá duas VNets no EUA Central:
  - VNET-PROD-CUS. Esta VNet é uma rede de produção, semelhante ao VNET-PROD_EUS2.
  - VNET-ASR-CUS. Essa VNet funcionará como um local no qual as VMs são criadas após o failover no local ou como um local para as VMs do Azure com failover da região primária para a secundária. Essa rede é semelhante às redes de produção, mas sem nenhum controlador de domínio.
  - Cada VNet na região terá seu próprio espaço de endereço, sem sobreposição. A Contoso configurará o roteamento sem NAT.
- **Sub-redes:** As sub-redes serão arquitetadas de forma semelhante àquelas no leste dos EUA 2. A exceção é que a Contoso não precisa de uma sub-rede para controladores de domínio.

As VNets no centro dos EUA estão resumidas na tabela a seguir.

**Rede virtual** | **Range** | **Par**
--- | --- | ---
**VNET-HUB-CUS** | 10.250.0.0/20 | VNET-HUB-EUS2, VNET-ASR-CUS, VNET-PROD-CUS
**VNET-ASR-CUS** | 10.255.16.0/20 | VNET-HUB-CUS, VNET-PROD-CUS
**VNET-PROD-CUS** | 10.255.32.0/20 | VNET-HUB-CUS, VNET-ASR-CUS, VNET-PROD-EUS2

![Modelo hub-spoke m região emparelhada](./media/contoso-migration-infrastructure/paired-hub-peer.png)

#### <a name="subnets-in-the-central-us-hub-network-vnet-hub-cus"></a>Sub-redes na rede do hub no Centro dos EUA (VNET-HUB-CUS)

**Sub-rede** | **CIDR** | **Endereços IP utilizáveis**
--- | --- | ---
**IB-UntrustZone** | 10.250.0.0/24 | 251
**IB-TrustZone** | 10.250.1.0/24 | 251
**OB-UntrustZone** | 10.250.2.0/24 | 251
**OB-TrustZone** | 10.250.3.0/24 | 251
**GatewaySubnet** | 10.250.2.0/24 | 251

#### <a name="subnets-in-the-central-us-production-network-vnet-prod-cus"></a>Sub-redes na rede de produção central dos EUA (VNET-PROD-CUS)

Em paralelo com a rede de produção na região principal leste dos EUA 2, há uma rede de produção na região de EUA Central secundária.

**Sub-rede** | **CIDR** | **Endereços** | **Na Sub-rede**
--- | --- | --- | ---
**PROD-FE-CUS** | 10.255.32.0/22 | 1019 | VMs de front-ends/camada da Web
**PROD-APP-CUS** | 10.255.36.0/22 | 1019 | Máquinas virtuais de camada de aplicativo
**PROD-DB-CUS** | 10.255.40.0/23 | 507 | VMs de banco de dados
**PROD-DC-CUS** | 10.255.42.0/24 | 251 | Máquinas virtuais do controlador de domínio

#### <a name="subnets-in-the-central-us-failoverrecovery-network-in-central-us-vnet-asr-cus"></a>Sub-redes na rede de failover / recuperação nos EUA Central (VNET-ASR-CUS)

A rede VNET-ASR-CUS é usada para propósitos de failover entre regiões. O Site Recovery será usado para replicar e fazer failover das VMs do Azure entre as regiões. Ele também funciona como um datacenter da Contoso na rede do Azure para cargas de trabalho protegidas que permanecem no local, mas faz o failover para o Azure para recuperação de desastre.

A VNET-ASR-CUS é a mesma sub-rede básica que a VNET de produção no Leste dos EUA 2, mas sem a necessidade de uma sub-rede de controlador de domínio.

**Sub-rede** | **CIDR** | **Endereços** | **Na Sub-rede**
--- | --- | --- | ---
**ASR-FE-CUS** | 10.255.16.0/22 | 1019 | VMs de front-ends/camada da Web
**ASR-APP-CUS** | 10.255.20.0/22 | 1019 | Máquinas virtuais de camada de aplicativo
**ASR-DB-CUS** | 10.255.24.0/23 | 507 | VMs de banco de dados

![Arquitetura de rede de hub](./media/contoso-migration-infrastructure/azure-networks-cus.png)

#### <a name="configure-peered-connections"></a>Configurar conexões com pares

O hub em cada região será espiado para o hub na outra região e para todas as VNets dentro da região do hub. Isso permite que os hubs se comuniquem e exibam todas as VNets dentro de uma região. Observe que:

- Peering cria uma conexão frente e verso. Um do ponto de partida no primeiro VNet e outro no segundo VNet.
- Em uma implantação híbrida, o tráfego que passa entre pares precisa ser visto a partir da conexão VPN entre o datacenter local e o Azure. Para habilitar isso, existem algumas configurações específicas que devem ser definidas em conexões com pares.

Para qualquer conexão do VNets com spoke pelo hub ao datacenter local, a Contoso precisa permitir o encaminhamento do tráfego e atravessar os gateways da VPN.

##### <a name="domain-controller"></a>Controlador de domínio

Para os controladores de domínio na rede VNET-PROD-EUS2, a Contoso deseja que o tráfego flua entre a rede de hub / produção do EUS2 e a conexão VPN para o local. Para fazer isso, os administradores da Contoso devem permitir o seguinte:

1. **Permitir tráfego encaminhado** e **Permitir configurações de trânsito de gateway** na conexão emparelhada. Em nosso exemplo, isso seria a conexão VNET-HUB-EUS2 para VNET-PROD-EUS2.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering1.png)

2. **Permitir tráfego encaminhado** e **Use gateways remotos** no outro lado do peering, na conexão VNET-PROD-EUS2 para VNET-HUB-EUS2.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering2.png)

3. Eles configurarão uma rota estática local que direciona o tráfego local para rotear o túnel da VPN para a VNet. A configuração seria concluída no gateway que fornece o túnel VPN da Contoso para o Azure. Eles usam o RRAS para isso.

    ![Emparelhamento](./media/contoso-migration-infrastructure/peering3.png)

##### <a name="production-networks"></a>Redes de produção

Uma rede par spoked não pode ver uma rede de pares spoked em outra região através de um hub.

Para que as redes de produção da Contoso em ambas as regiões vejam umas às outras, os administradores da Contoso precisam criar uma conexão emparelhada direta para VNET-PROD-EUS2 e VENT-PROD-CUS.

![Emparelhamento](./media/contoso-migration-infrastructure/peering4.png)

### <a name="set-up-dns"></a>Configurar DNS

Quando você implanta recursos em redes virtuais, você tem algumas opções para a resolução de nomes de domínio. Você pode usar a resolução de nomes fornecida pelo Azure ou fornecer servidores DNS para resolução. O tipo de resolução de nomes usado depende de como seus recursos precisam se comunicar entre si. Obtenha [ mais informações ](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances#azure-provided-name-resolution) sobre o serviço DNS do Azure.

Os administradores da Contoso decidiram que o serviço DNS do Azure não é uma boa opção no ambiente híbrido. Em vez disso, eles usarão os servidores DNS locais.

- Como essa é uma rede híbrida, todas as VMs no local e no Azure precisam ser capazes de resolver nomes para funcionar corretamente. Isso significa que as configurações de DNS personalizadas devem ser aplicadas a todas as VNets.
- No momento, a Contoso tem DCs implantados no datacenter da Contoso e nas filiais. Os servidores DNS primários são CONTOSODC1(172.16.0.10) e CONTOSODC2(172.16.0.1)
- Quando as VNETs forem implantadas, os controladores de domínio locais serão definidos para serem usados como servidores DNS nas redes.
- Para configurar isso, ao usar o DNS personalizado na VNet, o endereço IP dos resolventes recursivos do Azure (como 168.63.129.16) deve ser adicionado à lista de DNS. Para fazer isso, a Contoso define as configurações do servidor DNS em cada rede virtual. Por exemplo, as configurações de DNS personalizadas para a rede VNET-HUB-EUS2 seriam as seguintes:

    ![DNS Personalizado](./media/contoso-migration-infrastructure/custom-dns.png)

Além dos controladores de domínio locais, a Contoso implementará mais quatro para dar suporte às suas redes do Azure, duas para cada região. Veja o que a Contoso implantará no Azure.

**Região** | **DC** | **Rede virtual** | **Sub-rede** | **Endereço IP**
--- | --- | --- | --- | ---
EUS2 | CONTOSODC3 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.4
EUS2 | CONTOSODC4 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.5
CUS | CONTOSODC5 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4
CUS | CONTOSODC6 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4

Após implantar os controladores de domínio locais, a Contoso precisará atualizar as configurações de DNS nas redes nas duas regiões para incluir os novos controladores de domínio em sua lista de servidores DNS.

#### <a name="set-up-domain-controllers-in-azure"></a>Configurar controladores de domínio no Azure

Após atualizar as configurações de rede, os administradores da Contoso estarão prontos para criar os controladores de domínio no Azure.

1. No portal do Azure, eles implantam uma nova VM do Windows Server na VNet apropriada.
2. Eles criam conjuntos de disponibilidade em cada local para a VM. Os conjuntos de disponibilidade fazem o seguinte:

    - Verifique se o tecido do Azure separa as VMs em infraestruturas diferentes na Região do Azure.
    - Permite que a Contoso seja elegível para o SLA de 99,95% para VMs no Azure. [Saiba mais](https://docs.microsoft.com/azure/virtual-machines/windows/tutorial-availability-sets).

    ![grupo de disponibilidade](./media/contoso-migration-infrastructure/availability-group.png)

3. Depois que a VM for implantada, eles abrirão o adaptador de rede da VM. Eles definem o endereço IP privado como estático e especificam um endereço válido.

    ![VM NIC](./media/contoso-migration-infrastructure/vm-nic.png)

4. Agora, eles anexam um novo disco de dados à VM. Esse disco contém o banco de dados do Active Directory e o compartilhamento sysvol.
    - O tamanho do disco determinará o número de IOPS que ele suporta.
    - Com o tempo, o tamanho do disco pode precisar aumentar conforme o ambiente cresce.
    - A unidade não deve ser definida como leitura/ gravação para armazenamento em cache do host. Bancos de dados do Active Directory não suportam isso.

     ![Disco do Active Directory](./media/contoso-migration-infrastructure/ad-disk.png)

5. Depois que o disco é adicionado, eles se conectam à VM pela Área de Trabalho Remota e abrem o Gerenciador de Servidores.

6. Então, em **Serviços de Arquivo e Armazenamento**, eles executam o Assistente de Novo Volume, garantindo que a unidade receba a letra F: ou acima na VM local.

     ![Assistente de novo volume](./media/contoso-migration-infrastructure/volume-wizard.png)

7. No Gerenciador do Servidor, adicionam a função **Active Directory Domain Services**. Em seguida, eles configuram a VM como um controlador de domínio.

      ![Função de servidor](./media/contoso-migration-infrastructure/server-role.png)

8. Depois que a VM é configurada como um DC e reinicializada, eles abrem o DNS Manager e configuram o resolvedor do DNS do Azure como um encaminhador. Isso permite que o DC encaminhe consultas DNS que não podem resolver no DNS do Azure.

    ![Encaminhador de DNS](./media/contoso-migration-infrastructure/dns-forwarder.png)

9. Agora, eles atualizam as configurações de DNS personalizadas para cada VNET com o controlador de domínio apropriado para a região da VNET. Eles incluem DCs locais na lista.

### <a name="set-up-active-directory"></a>Configurar o Active Directory

O Active Directory é um serviço crítico na rede e deve ser configurado corretamente. Os administradores da Contoso criarão sites do Active Directory para o datacenter da Contoso e para as regiões EUS2 e CUS.

1. Eles criam dois novos sites (AZURE-EUS2 e AZURE-CUS) juntamente com o site do datacenter (ContosoDatacenter).
2. Depois de criar os sites, eles criam sub-redes nos sites para corresponder às VNets e ao datacenter.

    ![Sub-redes DC](./media/contoso-migration-infrastructure/dc-subnets.png)

3. Em seguida, eles criam dois links de site para conectar tudo. Os controladores de domínio devem então ser movidos para sua localização.

    ![Links DC](./media/contoso-migration-infrastructure/dc-links.png)

4. Depois que tudo estiver configurado, a topologia de replicação do Active Directory estará no lugar.

    ![Replicação DC](./media/contoso-migration-infrastructure/ad-resolution.png)

5. Com tudo concluído, uma lista de controladores de domínio e sites é mostrada no Centro Administrativo do Active Directory no local.

    ![Centro Administrativo do Active Directory](./media/contoso-migration-infrastructure/ad-center.png)

## <a name="step-5-plan-for-governance"></a>Etapa 5: Planejar a governança

O Azure fornece uma variedade de controles de governança entre os serviços e a plataforma do Azure. Para obter mais informações, consulte as [Opções de governança do Azure](https://docs.microsoft.com/azure/security/governance-in-azure).

À medida que configuram o controle de identidade e de acesso, a Contoso já começou a implementar alguns aspectos de governança e segurança. Em geral, há três áreas que ela precisa considerar:

- **Política:** Azure Policy aplica e impõe regras e efeitos sobre seus recursos, para que os recursos permaneçam em conformidade com os requisitos e SLAs corporativos.
- **Bloqueios:** O Azure permite que você bloqueie assinaturas, grupos de recursos e outros recursos, para que eles possam ser modificados somente por aqueles com autoridade para fazer isso.
- **Marcas:** Os recursos podem ser controlados, auditados e gerenciados com marcas. As macas anexam metadados a recursos, fornecendo informações sobre recursos ou proprietários.

### <a name="set-up-policies"></a>Configurar políticas

O serviço de Política do Azure avalia seus recursos, procurando aqueles que não estão em conformidade com as definições de política que você tem em vigor. Por exemplo, pode haver uma política que permita apenas determinados tipos de VMs ou exija que os recursos tenham uma marca específica.

As políticas elaboram as definições e atribuições de políticas específicas de acordo com o escopo no qual estas devem ser aplicadas. O escopo pode variar de um grupo de gerenciamento para um grupo de recursos. [ Aprenda ](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) sobre como criar e gerenciar políticas.

A Contoso deseja começar com duas políticas:

- Ele quer uma política para garantir que os recursos possam ser implantados somente nas regiões EUS2 e CUS.
- Ela deseja limitar as SKUs da VM apenas aos SKUs aprovados. A intenção é garantir que não sejam usados SKUs de VMs caros.

#### <a name="limit-resources-to-regions"></a>Limitar recursos a regiões

A Contoso usa a definição de política interna **Locais permitidos** para limitar as regiões de recursos.

1. No portal do Azure, selecione **Todos os serviços** e pesquise por **Política**.
2. Selecione **Atribuições** > **Atribuir política**.
3. Na lista de políticas, selecione **Locais permitidos**.
4. Defina **Escopo** como o nome da assinatura do Azure e selecione as duas regiões na lista permitida.

    ![Regiões permitidas por política](./media/contoso-migration-infrastructure/policy-region.png)

5. Por padrão, a política é definida com **Negar**, o que significa que, se alguém iniciar uma implantação na assinatura que não esteja em EUS2 ou CUS, a implantação falhará. Veja o que acontece se alguém na assinatura Contoso tentar configurar uma implantação no oeste dos EUA.

    ![A Política falhou](./media/contoso-migration-infrastructure/policy-failed.png)

#### <a name="allow-specific-vm-skus"></a>Permitir SKUs de VMs específicos

A Contoso usará a definição de política interna **Permitir SKUs de máquinas virtuais** para limitar o tipo de VMs que podem ser criadas na assinatura.

![Política de SKU](./media/contoso-migration-infrastructure/policy-sku.png)

#### <a name="check-policy-compliance"></a>Verifique a conformidade da política

As políticas entram em vigor imediatamente e a Contoso pode verificar recursos para conformidade.

1. No portal do Azure, clique no link **Compliance**.
2. O painel de conformidade é exibido. Você pode detalhar mais detalhes.

    ![Conformidade da política](./media/contoso-migration-infrastructure/policy-compliance.png)

### <a name="set-up-locks"></a>Configurar bloqueios

A Contoso há muito tempo usa a estrutura ITIL para o gerenciamento de seus sistemas. Um dos aspectos mais importantes da estrutura é o controle de alterações, e a Contoso deseja garantir que o controle de alterações seja implementado na implantação do Azure.

A Contoso implementará os bloqueios da seguinte maneira:

- Qualquer componente de produção ou failover deve estar em um grupo de recursos que tenha um bloqueio ReadOnly. Isso significa que, para modificar ou excluir itens de produção, o bloqueio deve ser removido.
- Grupos de recursos que não são de produção terão bloqueios CanNotDelete. Isso significa que os usuários autorizados podem ler ou modificar um recurso, mas não podem excluí-lo.

[ Saiba mais ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) sobre bloqueios.

### <a name="set-up-tagging"></a>Configurar a marcação

Para rastrear recursos à medida que são adicionados, será cada vez mais importante para a Contoso associar recursos a um departamento, cliente e ambiente apropriados.

Além de fornecer informações sobre recursos e proprietários, as marcas permitirão que a Contoso agregue e agrupe recursos e use esses dados para fins de cobrança retroativa.

A Contoso precisa visualizar seus ativos do Azure de uma maneira que faça sentido para o negócio. Por exemplo, por função ou departamento. Observe que os recursos não precisam residir no mesmo grupo de recursos para compartilhar uma marca. A Contoso criará uma taxonomia de marca simples para que todos usem as mesmas marcas.

**nome da marca** | **Valor**
--- | ---
CostCenter | 12345: deve ser um centro de custo válido da SAP.
BusinessUnit | Nome da unidade de negócios (do SAP). Corresponde ao centro de custo.
ApplicationTeam | Alias de e-mail da equipe que possui suporte para o aplicativo.
CatalogName | Nome do aplicativo ou ShareServices, de acordo com o catálogo de serviços que o recurso suporta.
ServiceManager | Alias de e-mail do Gerenciador de serviços da ITIL para o recurso.
COBPriority | Prioridade definida pela empresa de BCDR. Valores de 1 a 5.
ENV | DEV, STG, PROD são os valores possíveis. Representando desenvolvimento, encenação e produção.

Por exemplo:

 ![Marcas do Azure](./media/contoso-migration-infrastructure/azure-tag.png)

Depois de criar a marca, a Contoso retornará e criará novas definições e atribuições de política para impor o uso das marcas necessárias em toda a organização.

## <a name="step-6-consider-security"></a>Etapa 6: considere a segurança

A segurança é crucial na nuvem, e o Azure fornece uma ampla variedade de ferramentas e recursos de segurança. Eles ajudam você a criar soluções seguras na plataforma segura do Azure. Leia [ Confiança na nuvem confiável ](https://azure.microsoft.com/overview/trusted-cloud) para saber mais sobre a segurança do Azure.

Há alguns aspectos que a Contoso deve considerar:

- **Central de segurança do Azure:** A central de segurança do Azure fornece gerenciamento de segurança unificado e proteção avançada contra ameaças em cargas de trabalho de nuvem híbrida. Com a Central de Segurança, é possível aplicar políticas de segurança em suas cargas de trabalho, limitar a exposição a ameaças e detectar e responder a ataques. [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-intro).
- **NSGs (grupos de segurança de rede):** Um NSG é um filtro (firewall) que contém uma lista de regras de segurança que, quando aplicada, permitem ou nega o tráfego de rede aos recursos conectados ao VNets do Azure. [Saiba mais](https://docs.microsoft.com/azure/virtual-network/security-overview).
- **Criptografia de dados:** Azure Disk Encryption é um recurso que ajuda você a criptografar seus discos de máquina virtual IaaS Windows e Linux. [Saiba mais](https://docs.microsoft.com/azure/security/azure-security-encryption-atrest).

### <a name="work-with-the-azure-security-center"></a>Trabalhar com o Centro de Segurança do Azure

A Contoso está procurando uma visão rápida da postura de segurança de sua nova nuvem híbrida e, especificamente, de suas cargas de trabalho do Azure. Como resultado, a Contoso decidiu implementar o Azure Security Center, iniciando com os seguintes recursos:

- Gerenciamento de política centralizado
- Avaliação contínua
- Recomendações práticas

#### <a name="centralize-policy-management"></a>Centralize o gerenciamento de políticas

Com o gerenciamento centralizado de políticas, a Contoso garantirá a conformidade com os requisitos de segurança gerenciando centralmente as políticas de segurança em todo o ambiente. Ela pode implementar de forma simples e rápida uma política que se aplica a todos os seus recursos do Azure.

![Política de segurança](./media/contoso-migration-infrastructure/security-policy.png)

#### <a name="assess-and-action"></a>Avaliar e ação

A Contoso aproveitará a avaliação de segurança contínua – que monitora a segurança de máquinas, redes, armazenamento, dados e aplicativos – para descobrir possíveis problemas de segurança.

- A central de segurança analisará o estado de segurança da computação, da infraestrutura e dos recursos de dados da Contoso e dos aplicativos e serviços do Azure.
- A avaliação contínua ajuda a equipe de operações da Contoso a descobrir possíveis problemas de segurança, como sistemas com atualizações de segurança ausentes ou portas de rede expostas.
- Em particular, a Contoso deseja garantir que todas as VMs estejam protegidas. A Central de Segurança ajuda com isso, verificando a integridade da VM e fazendo recomendações priorizadas e acionáveis para corrigir as vulnerabilidades de segurança antes que elas sejam exploradas.

![Monitoramento](./media/contoso-migration-infrastructure/monitoring.png)

### <a name="work-with-nsgs"></a>Trabalhar com NSGs

A Contoso pode limitar o tráfego de rede a recursos em uma rede virtual usando grupos de segurança de rede.

- Um grupo de segurança de rede contém uma lista de regras de segurança que permitem ou negam o tráfego de rede de entrada ou saída com base no endereço IP de origem ou destino, na porta e no protocolo.
- Quando aplicadas a uma sub-rede, as regras de segurança são aplicadas a todos os recursos na sub-rede. Além das interfaces de rede, isso inclui instâncias de serviços do Azure implantadas na sub-rede.
- Os grupos de segurança de aplicativos (ASGs) permitem que você configure a segurança de rede como uma extensão natural de uma estrutura de aplicativo, permitindo agrupar VMs e definir políticas de segurança de rede com base nesses grupos.
  - Os grupos de segurança de aplicativo significam que a Contoso pode reutilizar a política de segurança em escala, sem manutenção manual de endereços IP explícitos. A plataforma lida com a complexidade de endereços IP explícitos e vários conjuntos de regras, permitindo que você se concentre na sua lógica de negócios.
  - A Contoso pode especificar um grupo de segurança de aplicativo como a origem e o destino em uma regra de segurança. Depois de definir uma política de segurança, a Contoso poderá criar VMs e atribuir as NICs da VM a um grupo.

A Contoso implementará uma mistura de NSGs e ASGs. A Contoso está preocupada com o gerenciamento de NSG. Ela também está preocupada com o uso excessivo de NSGs e com a maior complexidade para a equipe de operações. A Contoso fará o seguinte:

- Todo o tráfego de entrada e saída de todas as sub-redes (norte-sul) estará sujeito a uma regra NSG, exceto as redes GatewaySubnets nas redes Hub.
- Todos os firewalls ou controladores de domínio serão protegidos por NSGs de sub-rede e NSGs de NIC.
- Todas as aplicações de produção terão ASGs aplicadas.

A Contoso criou um modelo de como será a aparência para seus aplicativos.

![Segurança](./media/contoso-migration-infrastructure/asg.png)

Os NSGs associados aos ASGs serão configurados com o menor privilégio para garantir que apenas os pacotes permitidos possam fluir de uma parte da rede para seu destino.

**Ação** | **Nome** | **Origem** | **Target (destino)** | **Porta**
--- | --- | --- | --- | ---
Permitir | AllowInternetToFE | VNET-HUB-EUS1/IB-TrustZone | APP1-FE 80, 443
Permitir | AllowWebToApp | APP1-FE | APP1-APP | 80, 443
Permitir | AllowAppToDB | APP1-APP | APP1-DB | 1433
Negar | DenyAllInBound | Qualquer | Qualquer | Qualquer

### <a name="encrypt-data"></a>Criptografar dados

O Azure Disk Encryption se integra ao Azure Key Vault para ajudar a controlar e gerenciar as chaves e as senhas da criptografia de disco em uma assinatura do Key Vault. Ele garante que todos os dados em discos da VM sejam criptografados em repouso no armazenamento do Azure.

- A Contoso determinou que as VMs específicas exigem criptografia.
- A Contoso aplicará a criptografia a VMs com os dados do cliente, confidenciais ou PPI.

## <a name="conclusion"></a>Conclusão

Neste artigo, a Contoso configurou uma infraestrutura do Azure e a política de assinatura do Azure, identificação híbrida, recuperação de desastres, rede, governança e segurança.

Nem todas as etapas que a Contoso concluiu aqui são necessárias para uma migração para a nuvem. Nesse caso, ela queria planejar uma infraestrutura de rede que pudesse ser usada para todos os tipos de migrações e fosse segura, resiliente e escalável.

Com essa infraestrutura, a Contoso está pronta para seguir em frente e experimentar a migração.

## <a name="next-steps"></a>Próximos passos

Depois de configurar sua infraestrutura do Azure, a Contoso está pronta para começar a migrar cargas de trabalho para a nuvem. Confira a seção [padrões de migração e visão geral de exemplos](./contoso-migration-overview.md#windows-server-workloads) para obter uma seleção de cenários usando essa infraestrutura de exemplo como um destino de migração.
