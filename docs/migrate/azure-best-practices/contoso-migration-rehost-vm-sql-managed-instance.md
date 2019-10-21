---
title: Rehospede um aplicativo local migrando para VMs do Azure e Instância Gerenciada do Banco de Dados SQL do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como a contoso rehospeda um aplicativo local em VMs do Azure e usando Instância Gerenciada do Banco de Dados SQL do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 4948035001cba4ba9b433a6f31811f0c66e1704f
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548155"
---
# <a name="rehost-an-on-premises-app-on-an-azure-vm-and-sql-database-managed-instance"></a>Rehospedar um aplicativo local em uma VM do Azure e Instância Gerenciada do Banco de Dados SQL

Este artigo mostra como a empresa fictícia Contoso migra um aplicativo de front-end do Windows .NET de duas camadas em execução em VMs VMware para uma VM do Azure usando o serviço Azure Site Recovery. Ele também mostra como a contoso migra o banco de dados de aplicativo para Instância Gerenciada do Banco de Dados SQL do Azure.

> [!NOTE]
> Instância Gerenciada do Banco de Dados SQL do Azure atualmente está em versão prévia.

O aplicativo SmartHotel360 usado neste exemplo é fornecido como código-fonte aberto. Se você quiser usá-lo para suas próprias finalidades de teste, você pode baixá-lo do [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Drivers de negócios

A equipe de liderança de ti da Contoso trabalhou junto com os parceiros comerciais da empresa para entender o que a empresa deseja alcançar com essa migração:

- **Resolva o crescimento dos negócios.** A Contoso está crescendo. Como resultado, a pressão aumentou na infraestrutura e nos sistemas locais da empresa.
- **Aumente a eficiência.** A contoso precisa remover procedimentos desnecessários e simplificar processos para seus desenvolvedores e usuários. A empresa precisa que seja rápida e não gaste tempo nem dinheiro, de modo que a empresa possa fornecer mais rapidez aos requisitos do cliente.
- **Aumente a agilidade.** A contoso IT precisa ser mais responsiva às necessidades dos negócios. Ele deve ser capaz de reagir mais rápido do que as alterações que ocorrem no Marketplace para que a empresa seja bem-sucedida em uma economia global. A ti da Contoso não deve ficar no caminho nem se tornar um bloqueador de negócios.
- **Escala.** À medida que os negócios da empresa crescem com êxito, a contoso IT deve fornecer sistemas que podem crescer no mesmo ritmo.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem da Contoso identificou as metas para essa migração. A empresa usa metas de migração para determinar o melhor método de migração.

- Após a migração, o aplicativo no Azure deve ter os mesmos recursos de desempenho que o aplicativo atualmente no ambiente VMware local da contoso. Mover para a nuvem não significa que o desempenho do aplicativo é menos crítico.
- A contoso não quer investir no aplicativo. O aplicativo é essencial e importante para os negócios, mas a contoso simplesmente deseja mover o aplicativo em seu formato atual para a nuvem.
- As tarefas de administração de banco de dados devem ser minimizadas depois que o aplicativo é migrado.
- A contoso não deseja usar um banco de dados SQL do Azure para este aplicativo. Ele está procurando alternativas.

## <a name="solution-design"></a>Design da solução

Depois de fixar suas metas e requisitos, a contoso projeta e revisa uma solução de implantação e identifica o processo de migração, incluindo os serviços do Azure que serão usados para a migração.

### <a name="current-architecture"></a>Arquitetura atual

- A contoso tem um datacenter principal (**contoso-datacenter**). O datacenter está localizado na cidade de Nova York no Estados Unidos Oriental.
- A contoso tem três ramificações locais adicionais no Estados Unidos.
- O datacenter principal está conectado à Internet com uma conexão Ethernet metro de fibra (500 MBps).
- Cada ramificação é conectada localmente à Internet usando conexões de classe comercial com túneis VPN IPsec de volta para o datacenter principal. A configuração permite que a rede inteira da Contoso seja conectada permanentemente e otimiza a conectividade com a Internet.
- O datacenter principal é totalmente virtualizado com o VMware. A contoso tem dois hosts de virtualização de ESXi 6,5 que são gerenciados pelo vCenter Server 6,5.
- A contoso usa Active Directory para o gerenciamento de identidades. A contoso usa servidores DNS na rede interna.
- A contoso tem um**contosodc1**(controlador de domínio local).
- Os controladores de domínio são executados em VMs VMware. Os controladores de domínio em branches locais são executados em servidores físicos.
- O aplicativo SmartHotel360 está em camadas em duas VMs (**WEBVM** e **SQLVM**) que estão localizadas em um host VMware ESXi versão 6,5 (**contosohost1.contoso.com**).
- O ambiente VMware é gerenciado pelo vCenter Server 6,5 (**vCenter.contoso.com**) em execução em uma VM.

![Arquitetura atual da contoso](./media/contoso-migration-rehost-vm-sql-managed-instance/contoso-architecture.png)

### <a name="proposed-architecture"></a>Arquitetura proposta

Nesse cenário, a contoso deseja migrar seu aplicativo de viagem local de duas camadas da seguinte maneira:

- Migre o banco de dados de aplicativo (**SmartHotelDB**) para um instância gerenciada do banco de dados SQL do Azure.
- Migre o **WebVM** de front-end para uma VM do Azure.
- As VMs locais no datacenter da Contoso serão encerradas quando a migração for concluída.

![Arquitetura do cenário](media/contoso-migration-rehost-vm-sql-managed-instance/architecture.png)

### <a name="database-considerations"></a>Considerações do banco de dados

Como parte do processo de design da solução, a contoso fez uma comparação de recursos entre o banco de dados SQL do Azure e o SQL Server Instância Gerenciada. As considerações a seguir ajudaram a decidir a ir para Instância Gerenciada.

- Instância Gerenciada tem o objetivo de fornecer quase 100% de compatibilidade com a versão mais recente do SQL Server local. A Microsoft recomenda a instância gerenciada para clientes que executam o SQL Server local ou na VM IaaS que deseja migrar seus aplicativos para um serviço totalmente gerenciado com alterações mínimas de design.
- A Contoso está planejando migrar um grande número de aplicativos do local para o IaaS. Muitos desses são fornecidos pelo ISV. A contoso percebe que o uso de Instância Gerenciada ajudará a garantir a compatibilidade do banco de dados para esses aplicativos, em vez de usar o banco de dados SQL que pode não ter suporte.
- A Contoso pode simplesmente fazer uma migração de "deslocamento e mudança" para Instância Gerenciada usando o serviço de migração de banco de dados do Azure totalmente automatizado. Com esse serviço em vigor, a Contoso pode reutilizá-lo para futuras migrações de banco de dados.
- O SQL Instância Gerenciada dá suporte a SQL Server Agent que é um problema importante para o aplicativo SmartHotel360. A contoso precisa dessa compatibilidade, caso contrário, precisará reformular os planos de manutenção exigidos pelo aplicativo.
- Com o Software Assurance, a Contoso pode trocar suas licenças existentes por tarifas com desconto em um Instância Gerenciada do Banco de Dados SQL usando o Benefício Híbrido do Azure para SQL Server. Isso pode permitir que a contoso Economize até 30% em Instância Gerenciada.
- O SQL Instância Gerenciada está totalmente contido na rede virtual e, portanto, fornece maior isolamento e segurança para os dados da contoso. A Contoso pode obter os benefícios da nuvem pública, mantendo o ambiente isolado da Internet pública.
- O Instância Gerenciada dá suporte a muitos recursos de segurança, incluindo o Always-Encrypted, máscara de dados dinâmicos, segurança em nível de linha e detecção de ameaças.

### <a name="solution-review"></a>Revisão da solução

A contoso avalia o design proposto, reunindo uma lista de prós e contras.

<!-- markdownlint-disable MD033 -->

**Reflexão** | **Detalhes**
--- | ---
**Prós** | O WEBVM será movido para o Azure sem alterações, tornando a migração simples.<br/><br/> O SQL Instância Gerenciada dá suporte às metas e aos requisitos técnicos da contoso.<br/><br/> Instância Gerenciada fornecerá uma compatibilidade de 100% com sua implantação atual, ao mesmo tempo que os move para fora do SQL Server 2008 R2.<br/><br/> Eles podem aproveitar seus investimentos no Software Assurance e usar o Benefício Híbrido do Azure para SQL Server e o Windows Server.<br/><br/> Eles podem reutilizar o serviço de migração de banco de dados do Azure para migrações futuras adicionais.<br/><br/> O SQL Instância Gerenciada tem tolerância interna a falhas que a contoso não precisa configurar. Isso garante que a camada de dados não seja mais um ponto único de failover.
**Contras** | O WEBVM está executando o Windows Server 2008 R2. Embora esse sistema operacional tenha suporte do Azure, ele não é mais compatível com plataforma. [Saiba mais](https://support.microsoft.com/help/956893).<br/><br/> A camada da Web permanece um ponto único de failover com apenas WEBVM fornecendo serviços.<br/><br/> A contoso precisará continuar a dar suporte à camada da Web do aplicativo como uma VM em vez de mudar para um serviço gerenciado, como Azure App Service.<br/><br/> Para a camada de dados, Instância Gerenciada poderá não ser a melhor solução se a contoso quiser personalizar o sistema operacional ou o servidor de banco de dados, ou se quiser executar aplicativos de terceiros junto com SQL Server. A execução de SQL Server em uma VM IaaS pode fornecer essa flexibilidade.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo de migração

A contoso migrará as camadas de dados e da Web de seu aplicativo SmartHotel360 para o Azure, concluindo estas etapas:

1. A contoso já tem sua infraestrutura do Azure em vigor e, portanto, só precisa adicionar alguns componentes específicos do Azure para esse cenário.
2. A camada de dados será migrada usando o serviço de migração de banco de dado do Azure. Esse serviço se conecta à VM de SQL Server local por meio de uma conexão VPN site a site entre o datacenter da Contoso e o Azure. Em seguida, o serviço migra o banco de dados.
3. A camada da Web será migrada usando uma migração de "comparação de precisão e deslocamento" usando Site Recovery. O processo envolve preparar o ambiente VMware local, configurar e habilitar a replicação e migrar as VMs fazendo o failover para o Azure.

     ![Arquitetura de migração](media/contoso-migration-rehost-vm-sql-managed-instance/migration-architecture.png)

### <a name="azure-services"></a>Serviços do Azure

Serviço | Descrição | Custo
--- | --- | ---
[Serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/dms-overview) | O serviço de migração de banco de dados do Azure permite a migração direta de várias fontes de banco de dado para as plataformas do Azure com tempo de inatividade | Saiba mais sobre as [regiões com suporte](https://docs.microsoft.com/azure/dms/dms-overview#regional-availability) e [preços do serviço de migração de banco de dados](https://azure.microsoft.com/pricing/details/database-migration).
[Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) | Instância Gerenciada é um serviço de banco de dados gerenciado que representa uma instância de SQL Server totalmente gerenciada na nuvem do Azure. Ele usa o mesmo código que a versão mais recente do SQL Server Mecanismo de Banco de Dados e tem os recursos, as melhorias de desempenho e os patches de segurança mais recentes. | Usar um Instância Gerenciada do Banco de Dados SQL em execução no Azure incorre em encargos com base na capacidade. Saiba mais sobre [preços de instância gerenciada](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery) | O serviço de Site Recovery orquestra e gerencia a migração e a recuperação de desastres para VMs do Azure e servidores físicos e VMs locais. | Durante a replicação para o Azure, os encargos de armazenamento do Azure são incorridos. As VMs do Azure são criadas e incorrem em encargos quando ocorre o failover. Saiba mais sobre [cobranças de site Recovery e preços](https://azure.microsoft.com/pricing/details/site-recovery).

## <a name="prerequisites"></a>Pré-requisitos

A Contoso e outros usuários devem atender aos seguintes pré-requisitos para este cenário:

<!-- markdownlint-disable MD033 -->

Requisitos | Detalhes
--- | ---
**Registrar na versão prévia do Instância Gerenciada** | Você deve estar registrado no Instância Gerenciada do Banco de Dados SQL visualização pública limitada. Você precisa de uma assinatura do Azure para [se inscrever](https://portal.azure.com#create/Microsoft.SQLManagedInstance). A inscrição pode levar alguns dias para ser concluída. portanto, lembre-se de inscrever-se antes de começar a implantar esse cenário.
**Assinatura do Azure** | Você já deve ter criado uma assinatura ao executar a avaliação no primeiro artigo desta série. Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se você criar uma conta gratuita, você é o administrador da sua assinatura e pode executar todas as ações.<br/><br/> Se você usar uma assinatura existente e não for o administrador da assinatura, precisará trabalhar com o administrador para atribuir permissões de proprietário ou colaborador.<br/><br/> Se você precisar de permissões mais granulares, consulte [usar o controle de acesso baseado em função para gerenciar o acesso ao site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infraestrutura do Azure** | A contoso configurou sua infraestrutura do Azure, conforme descrito na [infraestrutura do Azure para migração](./contoso-migration-infrastructure.md).
**Site Recovery (local)** | Sua instância de vCenter Server local deve estar executando a versão 5,5, 6,0 ou 6,5<br/><br/> Um host ESXi executando a versão 5,5, 6,0 ou 6,5<br/><br/> Uma ou mais VMs do VMware em execução no host ESXi.<br/><br/> As VMs devem atender [aos requisitos do Azure](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#azure-vm-requirements).<br/><br/> Configuração de [rede](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#network) e [armazenamento](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix#storage) com suporte.
**Serviço de migração de banco de dados** | Para o serviço de migração de banco de dados do Azure, você precisa de um [dispositivo VPN local compatível](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).<br/><br/> Você deve ser capaz de configurar o dispositivo VPN local. Ele deve ter um endereço IPv4 público voltado para o externo. O endereço não pode ser localizado atrás de um dispositivo NAT.<br/><br/> Verifique se você tem acesso ao seu banco de dados SQL Server local.<br/><br/> O Firewall do Windows deve ser capaz de acessar o mecanismo de banco de dados de origem. Saiba como [Configurar o Firewall do Windows para acesso mecanismo de banco de dados](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access).<br/><br/> Se houver um firewall na frente do seu computador de banco de dados, adicione regras para permitir o acesso ao banco de dados e aos arquivos por meio da porta SMB 445.<br/><br/> As credenciais que são usadas para se conectar à instância de SQL Server de origem e quais Instância Gerenciada de destino devem ser membros da função de servidor sysadmin.<br/><br/> Você precisa de um compartilhamento de rede no banco de dados local que o serviço de migração de banco de dados do Azure pode usar para fazer backup do banco de dados de origem.<br/><br/> Verifique se a conta de serviço que executa a instância de SQL Server de origem tem permissões de gravação no compartilhamento de rede.<br/><br/> Anote um usuário do Windows e uma senha que tenha permissões de controle total no compartilhamento de rede. O serviço de migração de banco de dados do Azure representa essas credenciais de usuário para carregar arquivos de backup no contêiner de armazenamento do Azure.<br/><br/> O processo de instalação do SQL Server Express define o protocolo TCP/IP como **desabilitado** por padrão. Verifique se ele está habilitado.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Etapas do cenário

Veja como a contoso planeja configurar a implantação:

> [!div class="checklist"]
>
> - **Etapa 1: configurar um Instância Gerenciada do Banco de Dados SQL.** A contoso precisa de uma instância gerenciada existente na qual o banco de dados do SQL Server local será migrado.
> - **Etapa 2: preparar o serviço de migração de banco de dados do Azure.** A Contoso deve registrar o provedor de migração de banco de dados, criar uma instância e criar um projeto de serviço de migração de banco de dados do Azure. A contoso também deve configurar um URI (Uniform Resource Identifier) de SAS (assinatura de acesso compartilhado) para o serviço de migração de banco de dados do Azure. Um URI SAS fornece acesso delegado aos recursos na conta de armazenamento da Contoso, para que a contoso possa conceder permissões limitadas a objetos de armazenamento. A Contoso configura um URI de SAS, de modo que o serviço de migração de banco de dados do Azure pode acessar o contêiner da conta de armazenamento para o qual o serviço carrega os arquivos de backup SQL Server.
> - **Etapa 3: preparar o Azure para Site Recovery.** A Contoso deve criar uma conta de armazenamento para manter os dados replicados para Site Recovery. Ele também deve criar um cofre dos serviços de recuperação do Azure.
> - **Etapa 4: preparar o VMware local para Site Recovery.** A contoso preparará contas para descoberta de VM e instalação de agente para se conectar a VMs do Azure após o failover.
> - **Etapa 5: replicar VMs.** Para configurar a replicação, a Contoso configura o Site Recovery ambientes de origem e de destino, configura uma política de replicação e inicia a replicação de VMs no armazenamento do Azure.
> - **Etapa 6: migre o banco de dados usando o serviço de migração de banco de dados do Azure.** A contoso migra o banco de dados.
> - **Etapa 7: migre as VMs usando Site Recovery.** A contoso executa um failover de teste para verificar se tudo está funcionando. Em seguida, a contoso executa um failover completo para migrar as VMs para o Azure.

## <a name="step-1-prepare-a-sql-database-managed-instance"></a>Etapa 1: preparar um Instância Gerenciada do Banco de Dados SQL

Para configurar um Instância Gerenciada do Banco de Dados SQL do Azure, a contoso precisa de uma sub-rede que atenda aos seguintes requisitos:

- A sub-rede deve ser dedicada. Ele deve estar vazio e não pode conter nenhum outro serviço de nuvem. A sub-rede não pode ser uma sub-rede de gateway.
- Depois que o Instância Gerenciada for criado, a contoso não deverá adicionar recursos à sub-rede.
- A sub-rede não pode ter um grupo de segurança de rede associado a ela.
- A sub-rede deve ter uma tabela de rotas definida pelo usuário. A única rota atribuída deve ser 0.0.0.0/0 próximo salto da Internet.
- DNS personalizado opcional: se o DNS personalizado for especificado na rede virtual do Azure, o endereço IP de resolvedores recursivos do Azure (como 168.63.129.16) deverá ser adicionado à lista. Saiba como [Configurar o DNS personalizado para um instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).
- A sub-rede não deve ter um ponto de extremidade de serviço (armazenamento ou SQL) associado a ela. Os pontos de extremidade de serviço devem ser desabilitados na rede virtual.
- A sub-rede deve ter um mínimo de 16 endereços IP. Saiba como [dimensionar a sub-rede instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-vnet-configuration).
- No ambiente híbrido da Contoso, são necessárias configurações personalizadas de DNS. A contoso define as configurações de DNS para usar um ou mais dos servidores DNS do Azure da empresa. Saiba mais sobre a [personalização de DNS](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-custom-dns).

### <a name="set-up-a-virtual-network-for-the-managed-instance"></a>Configurar uma rede virtual para o Instância Gerenciada

Os administradores da Contoso configuram a rede virtual da seguinte maneira:

1. Eles criam uma nova rede virtual (**VNET-SQLMI-EU2**) na região principal leste dos EUA 2. Ele adiciona a rede virtual ao grupo de recursos **ContosoNetworkingRG** .
2. Eles atribuem um espaço de endereço de 10.235.0.0/24. Eles garantem que o intervalo não se sobreponha a nenhuma outra rede em sua empresa.
3. Eles adicionam duas sub-redes à rede:
    - **SQLMI-DS-EUS2** (10.235.0.0.25)
    - **SQLMI-Serra-EUS2** (10.235.0.128/29). Essa sub-rede é usada para anexar um diretório ao Instância Gerenciada.

      ![Instância Gerenciada-criar rede virtual](media/contoso-migration-rehost-vm-sql-managed-instance/mi-vnet.png)

4. Depois que a rede virtual e as sub-redes são implantadas, elas emparelham as redes da seguinte maneira:

    - Peers **VNET-SQLMI-EUS2** com **vnet-Hub-EUS2** (a rede virtual de Hub para o leste dos EUA 2).
    - Peers **VNET-SQLMI-EUS2** com **VNET-prod-EUS2** (a rede de produção).

      ![Emparelhamento de rede](media/contoso-migration-rehost-vm-sql-managed-instance/mi-peering.png)

5. Eles definem configurações de DNS personalizadas. O DNS aponta primeiro para os controladores de domínio do Azure da contoso. O DNS do Azure é secundário. Os controladores de domínio do Azure da Contoso estão localizados da seguinte maneira:

    - Localizado na sub-rede **prod-DC-EUS2** , na rede de produção leste dos EUA 2 (**VNET-prod-EUS2**)
    - Endereço **CONTOSODC3** : 10.245.42.4
    - Endereço **CONTOSODC4** : 10.245.42.5
    - Resolvedor de DNS do Azure: 168.63.129.16

      ![Servidores DNS de rede](media/contoso-migration-rehost-vm-sql-managed-instance/mi-dns.png)

**Precisa de mais ajuda?**

- Obtenha uma visão geral do [instância gerenciada do banco de dados SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).
- Saiba como [criar uma rede virtual para um instância gerenciada do banco de dados SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-vnet-configuration).
- Saiba como [Configurar o emparelhamento](https://docs.microsoft.com/azure/virtual-network/virtual-network-manage-peering).
- Saiba como [atualizar Azure Active Directory configurações de DNS](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started-dns).

### <a name="set-up-routing"></a>Configurar o roteamento

O Instância Gerenciada é colocado em uma rede virtual privada. A contoso precisa de uma tabela de rotas para que a rede virtual se comunique com o serviço de gerenciamento do Azure. Se a rede virtual não puder se comunicar com o serviço que a gerencia, a rede virtual ficará inacessível.

A contoso considera estes fatores:

- A tabela de rotas contém um conjunto de regras (rotas) que especificam como os pacotes enviados do Instância Gerenciada devem ser roteados na rede virtual.
- A tabela de rotas está associada a sub-redes nas quais as instâncias gerenciadas são implantadas. Cada pacote que sai de uma sub-rede é tratado com base na tabela de rotas associada.
- Uma sub-rede pode ser associada a apenas uma tabela de rotas.
- Não há encargos adicionais para a criação de tabelas de rotas em Microsoft Azure.

 Para configurar o roteamento de administradores da Contoso, faça o seguinte:

1. Eles criam uma tabela de rotas definida pelo usuário no grupo de recursos **ContosoNetworkingRG** .

    ![Tabela de rotas](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table.png)

2. Para atender aos requisitos de Instância Gerenciada, depois que a tabela de rotas (**MIRouteTable**) é implantada, ela adiciona uma rota que tem um prefixo de endereço 0.0.0.0/0. A opção de **tipo do próximo salto** é definida como **Internet**.

    ![Prefixo da tabela de rotas](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-prefix.png)

3. Eles associam a tabela de rotas à sub-rede **SQLMI-DB-EUS2** (na rede **VNET-SQLMI-EUS2** ).

    ![Sub-rede da tabela de rotas](media/contoso-migration-rehost-vm-sql-managed-instance/mi-route-table-subnet.png)

**Precisa de mais ajuda?**

Saiba como [configurar rotas para um instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal).

### <a name="create-a-managed-instance"></a>Criar um Instância Gerenciada

Agora, os administradores da Contoso podem provisionar um Instância Gerenciada do Banco de Dados SQL:

1. Como o Instância Gerenciada serve a um aplicativo de negócios, eles implantam o Instância Gerenciada na região principal leste dos EUA da empresa 2. Eles adicionam o Instância Gerenciada ao grupo de recursos **ContosoRG** .
2. Eles selecionam um tipo de preço, uma computação de tamanho e um armazenamento para a instância. Saiba mais sobre [preços de instância gerenciada](https://azure.microsoft.com/pricing/details/sql-database/managed).

    ![Instância Gerenciada](media/contoso-migration-rehost-vm-sql-managed-instance/mi-create.png)

3. Depois que o Instância Gerenciada for implantado, dois novos recursos aparecerão no grupo de recursos **ContosoRG** :

    - Um cluster virtual no caso de contoso tem várias instâncias gerenciadas.
    - O Instância Gerenciada do banco de dados SQL Server.

      ![Instância Gerenciada](media/contoso-migration-rehost-vm-sql-managed-instance/mi-resources.png)

**Precisa de mais ajuda?**

Saiba como [provisionar um instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal).

## <a name="step-2-prepare-the-azure-database-migration-service"></a>Etapa 2: preparar o serviço de migração de banco de dados do Azure

Para preparar o serviço de migração de banco de dados do Azure, os administradores da Contoso precisam fazer algumas coisas:

- Registrar o provedor de serviço de migração de banco de dados do Azure no Azure.
- Forneça ao serviço de migração de banco de dados do Azure acesso ao armazenamento do Azure para carregar os arquivos de backup que são usados para migrar um banco de dados. Para fornecer acesso ao armazenamento do Azure, eles criam um contêiner de armazenamento de BLOBs do Azure. Eles geram um URI de SAS para o contêiner de armazenamento de BLOBs.
- Crie um projeto de serviço de migração de banco de dados do Azure.

Em seguida, eles concluem as seguintes etapas:

1. Eles registram o provedor de migração de banco de dados em sua assinatura.
    Serviço de migração de ![Database-registrar ](media/contoso-migration-rehost-vm-sql-managed-instance/dms-subscription.png)

2. Eles criam um contêiner de armazenamento de BLOBs. A contoso gera um URI de SAS para que o serviço de migração de banco de dados do Azure possa acessá-lo.

    ![Serviço de migração de banco de dados – gerar um URI de SAS](media/contoso-migration-rehost-vm-sql-managed-instance/dms-sas.png)

3. Eles criam uma instância do serviço de migração de banco de dados do Azure.

    ![Serviço de migração de banco de dados – criar instância](media/contoso-migration-rehost-vm-sql-managed-instance/dms-instance.png)

4. Eles colocam a instância do serviço de migração de banco de dados do Azure na sub-rede **prod-DC-EUS2** da rede virtual **VNET-prod-DC-EUS2** .
    - O serviço de migração de banco de dados do Azure é colocado aqui porque o serviço deve estar em uma rede virtual que pode acessar a VM de SQL Server local por meio de um gateway de VPN.
    - O **vnet-prod-EUS2** é emparelhado para **VNET-Hub-EUS2** e tem permissão para usar gateways remotos. A opção **usar gateways remotos** garante que o serviço de migração de banco de dados do Azure possa se comunicar conforme necessário.

        ![Serviço de migração de banco de dados – configurar rede](media/contoso-migration-rehost-vm-sql-managed-instance/dms-network.png)

**Precisa de mais ajuda?**

- Saiba como [Configurar o serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/quickstart-create-data-migration-service-portal).
- Saiba como [criar e usar SAS](https://docs.microsoft.com/azure/storage/blobs/storage-dotnet-shared-access-signature-part-2).

## <a name="step-3-prepare-azure-for-the-site-recovery-service"></a>Etapa 3: preparar o Azure para o serviço de Site Recovery

Vários elementos do Azure são necessários para que a contoso configure Site Recovery para migração de sua VM de camada da Web (**WEBMV**):

- Uma rede virtual na qual os recursos com failover estão localizados.
- Uma conta de armazenamento para manter os dados replicados.
- Um cofre dos serviços de recuperação no Azure.

Os administradores da Contoso configuram Site Recovery da seguinte maneira:

1. Como a VM é um front-end da Web para o aplicativo SmartHotel360, a contoso executa failover da VM para sua rede de produção existente (**VNET-prod-EUS2**) e sub-rede (**prod-FE-EUS2**). A rede e a sub-rede estão localizadas na região principal leste dos EUA 2. A contoso configurou a rede quando [implantou a infraestrutura do Azure](./contoso-migration-infrastructure.md).
2. Eles criam uma conta de armazenamento (**contosovmsacc20180528**). A contoso usa uma conta de finalidade geral. A contoso seleciona o armazenamento padrão e a replicação de armazenamento com redundância local.

    ![Site Recovery-criar conta de armazenamento](media/contoso-migration-rehost-vm-sql-managed-instance/asr-storage.png)

3. Com a conta de rede e de armazenamento em vigor, eles criam um cofre (**ContosoMigrationVault**). A contoso coloca o cofre no grupo de recursos **ContosoFailoverRG** , na região principal leste dos EUA 2.

    ![Serviços de recuperação-criar cofre](media/contoso-migration-rehost-vm-sql-managed-instance/asr-vault.png)

**Precisa de mais ajuda?**

Saiba como [Configurar o Azure para site Recovery](https://docs.microsoft.com/azure/site-recovery/tutorial-prepare-azure).

## <a name="step-4-prepare-on-premises-vmware-for-site-recovery"></a>Etapa 4: preparar o VMware local para Site Recovery

Para preparar o VMware para Site Recovery, os administradores da Contoso devem concluir estas tarefas:

- Prepare uma conta na instância de vCenter Server ou no host vSphere ESXi. A conta automatiza a descoberta de VM.
- Prepare uma conta que permita a instalação automática do serviço de mobilidade em VMs VMware que a contoso deseja replicar.
- Prepare VMs locais para se conectar a VMs do Azure quando elas forem criadas após o failover.

### <a name="prepare-an-account-for-automatic-discovery"></a>Preparar uma conta para a descoberta automática

Site Recovery precisa acessar servidores VMware para:

- Descobrir VMs automaticamente. É necessário um mínimo de uma conta somente leitura.
- Orquestrar a replicação, o failover e o failback. A contoso precisa de uma conta que possa executar operações como criar e remover discos e ativar VMs.

Os administradores da Contoso configuram a conta concluindo estas tarefas:

1. Cria uma função no nível do vCenter.
2. Atribui as permissões necessárias para essa função.

**Precisa de mais ajuda?**

Saiba como [criar e atribuir uma função para a descoberta automática](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-automatic-discovery).

### <a name="prepare-an-account-for-mobility-service-installation"></a>Preparar uma conta para a instalação do serviço de mobilidade

O serviço de mobilidade deve ser instalado na VM que a contoso deseja replicar. A contoso considera esses fatores sobre o serviço de mobilidade:

- Site Recovery pode fazer uma instalação automática por push deste componente quando a contoso habilita a replicação para a VM.
- Para a instalação automática por push, a Contoso deve preparar uma conta que Site Recovery usa para acessar a VM.
- Essa conta é especificada quando a replicação é configurada no console do Azure.
- A Contoso deve ter uma conta local ou de domínio com permissões para instalar na VM.

**Precisa de mais ajuda?**

Saiba como [criar uma conta para a instalação por push do serviço de mobilidade](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial-prepare-on-premises#prepare-an-account-for-mobility-service-installation).

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Preparar para conectar VMs do Azure após o failover

Após o failover para o Azure, a contoso deseja ser capaz de se conectar às VMs replicadas no Azure. Para se conectar às VMs replicadas no Azure, os administradores da Contoso devem concluir algumas tarefas na VM local antes da migração:

1. Para acesso pela Internet, eles habilitam o RDP na VM local antes do failover. Eles garantem que as regras de TCP e UDP sejam adicionadas ao perfil **público** e que o RDP seja permitido no **Firewall do Windows**  > **aplicativos permitidos** para todos os perfis.
2. Para acessar a VPN site a site da Contoso, eles habilitam o RDP no computador local. Eles permitem que o RDP no **Firewall do Windows**  > **aplicativos e recursos permitidos** para redes de **domínio e privadas** .
3. Eles definem a política de SAN do sistema operacional na VM local como **OnlineAll**.

Os administradores da Contoso também precisam verificar esses itens quando executam um failover:

- Não deve haver nenhuma atualização do Windows pendente na VM quando um failover é disparado. Se as atualizações do Windows estiverem pendentes, os usuários da Contoso não poderão entrar na máquina virtual até que a atualização seja concluída.
- Após o failover, os administradores devem verificar o **diagnóstico de inicialização** para exibir uma captura de tela da VM. Se eles não conseguirem exibir o diagnóstico de inicialização, eles deverão verificar se a VM está em execução e, em seguida, examinar as [dicas de solução de problemas](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

## <a name="step-5-replicate-the-on-premises-vms-to-azure"></a>Etapa 5: replicar as VMs locais para o Azure

Antes de executar uma migração para o Azure, os administradores da Contoso precisam configurar e habilitar a replicação para a VM local.

### <a name="set-a-replication-goal"></a>Definir uma meta de replicação

1. No cofre, no nome do cofre (**ContosoVMVault**), eles definem uma meta de replicação (**Introdução**  > **site Recovery**  > **preparar a infraestrutura**).
2. Eles especificam que os computadores estão localizados localmente, que são VMs VMware, replicando para o Azure.

    ![Preparar a infraestrutura-meta de proteção](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-goal.png)

### <a name="confirm-deployment-planning"></a>Confirmar planejamento da implantação

Para continuar, os administradores da Contoso confirmam que concluíram o planejamento da implantação. Eles selecionam **Sim, fiz isso**. Nessa implantação, a Contoso está migrando apenas uma única VM, o planejamento da implantação não é necessário.

### <a name="set-up-the-source-environment"></a>Configurar o ambiente de origem

Agora, os administradores da Contoso configuram o ambiente de origem. Para configurar seu ambiente de origem, eles baixam um modelo OVF e o usam para implantar o servidor de configuração e seus componentes associados como uma VM VMware local altamente disponível. Os componentes do servidor incluem:

- O servidor de configuração que coordena as comunicações entre a infraestrutura local e o Azure. O servidor de configuração gerencia a replicação de dados.
- O servidor de processo que atua como um gateway de replicação. O servidor de processo:
  - Recebe dados de replicação.
  - Otimiza a data de replicação usando caching, compactação e criptografia.
  - Envia a data de replicação para o armazenamento do Azure.
- O servidor de processo também instala o serviço de mobilidade nas VMs que serão replicadas. O servidor de processo executa a descoberta automática de VMs VMware locais.
- Depois que a VM do servidor de configuração é criada e iniciada, a contoso registra o servidor no cofre.

Para configurar o ambiente de origem, os administradores do contoso fazem o seguinte:

1. Eles baixam o modelo OVF do portal do Azure (**preparar infraestrutura**  > **fonte**  > **servidor de configuração**).

    ![Adicionar um servidor de configuração](./media/contoso-migration-rehost-vm-sql-managed-instance/add-cs.png)

2. Eles importam o modelo para o VMware para criar e implantar a VM.

    ![Implantar modelo OVF](./media/contoso-migration-rehost-vm-sql-managed-instance/vcenter-wizard.png)

3. Quando eles ligam a VM pela primeira vez, ele começa em uma experiência de instalação do Windows Server 2016. Eles aceitam o contrato de licença e entram em uma senha de administrador.
4. Quando a instalação for concluída, elas entrarão na VM como administrador. Na primeira vez que entrar, a ferramenta de configuração do Azure Site Recovery é executada automaticamente.
5. Na ferramenta de configuração do Site Recovery, insira um nome a ser usado para registrar o servidor de configuração no cofre.
6. A ferramenta verifica a conexão da VM com o Azure. Depois que a conexão for estabelecida, selecione **entrar** para entrar na assinatura do Azure. As credenciais devem ter acesso ao cofre no qual o servidor de configuração está registrado.

    ![Registrar o servidor de configuração](./media/contoso-migration-rehost-vm-sql-managed-instance/config-server-register2.png)

7. A ferramenta executa algumas tarefas de configuração e, em seguida, é reinicializada. Eles entram no computador novamente. O assistente de gerenciamento do servidor de configuração é iniciado automaticamente.
8. No assistente, eles selecionam a NIC para receber o tráfego de replicação. Essa configuração não pode ser alterada depois de ser configurada.
9. Eles selecionam a assinatura, o grupo de recursos e o cofre dos serviços de recuperação nos quais registrar o servidor de configuração.

    ![Selecionar cofre dos serviços de recuperação](./media/contoso-migration-rehost-vm-sql-managed-instance/cswiz1.png)

10. Eles baixam e instalam o MySQL Server e o VMmare PowerCLI. Em seguida, eles validam as configurações do servidor.
11. Após a validação, insira o FQDN ou endereço IP da instância de vCenter Server ou host vSphere. Eles deixam a porta padrão e inserem um nome de exibição para a instância de vCenter Server no Azure.
12. Eles especificam a conta criada anteriormente para que Site Recovery possa descobrir automaticamente as VMs do VMware que estão disponíveis para replicação.
13. Eles inserem credenciais e, portanto, o serviço de mobilidade é instalado automaticamente quando a replicação é habilitada. Para computadores Windows, a conta precisa de permissões de administrador local nas VMs.

    ![Configurar vCenter Server](./media/contoso-migration-rehost-vm-sql-managed-instance/cswiz2.png)

14. Quando o registro é concluído, no portal do Azure, eles verificam novamente se o servidor de configuração e o servidor VMware estão listados na página de **origem** no cofre. A descoberta pode levar 15 minutos ou mais.
15. Site Recovery se conecta a servidores VMware usando as configurações especificadas e descobre VMs.

### <a name="set-up-the-target"></a>Configurar o destino

Agora, os administradores da Contoso configuram o ambiente de replicação de destino:

1. Em **preparar infraestrutura**  > **destino**, eles selecionam as configurações de destino.
2. Site Recovery verifica se há uma conta de armazenamento e uma rede no destino especificado.

### <a name="create-a-replication-policy"></a>Criar uma política de replicação

Quando a origem e o destino são configurados, os administradores da Contoso criam uma política de replicação e associam a política ao servidor de configuração:

1. Em **preparar infraestrutura**  > **configurações de replicação**  > **política de replicação**  >  **criar e associar**, elas criam a política **ContosoMigrationPolicy** .
2. Eles usam as configurações padrão:
    - **Limite de RPO:** Padrão de 60 minutos. Esse valor define a frequência com que os pontos de recuperação são criados. Um alerta será gerado se a replicação contínua exceder esse limite.
    - **Retenção do ponto de recuperação:** Padrão de 24 horas. Esse valor especifica quanto tempo a janela de retenção é para cada ponto de recuperação. As VMs replicadas podem ser recuperadas para qualquer ponto em uma janela.
    - **Frequência de instantâneo consistente com o aplicativo:** Padrão de 1 hora. Esse valor especifica a frequência na qual os instantâneos consistentes com o aplicativo são criados.

    ![Política de replicação-criar](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-policy.png)

3. A política é associada automaticamente ao servidor de configuração.

    ![Política de replicação-associar](./media/contoso-migration-rehost-vm-sql-managed-instance/replication-policy2.png)

**Precisa de mais ajuda?**

- Você pode ler uma explicação completa dessas etapas em [Configurar a recuperação de desastre para VMs VMware locais](https://docs.microsoft.com/azure/site-recovery/vmware-azure-tutorial).
- As instruções detalhadas estão disponíveis para ajudá-lo a [Configurar o ambiente de origem](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-source), [implantar o servidor de configuração](https://docs.microsoft.com/azure/site-recovery/vmware-azure-deploy-configuration-server)e [definir as configurações de replicação](https://docs.microsoft.com/azure/site-recovery/vmware-azure-set-up-replication).

### <a name="enable-replication"></a>Habilitar replicação

Agora, os administradores da Contoso podem iniciar a replicação de WebVM.

1. No **aplicativo replicate**  > **origem**  > **replicar**, eles selecionam as configurações de origem.
2. Eles indicam que desejam habilitar máquinas virtuais, selecionar a instância de vCenter Server e definir o servidor de configuração.

    ![Habilitar a replicação-origem](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication1.png)

3. Eles especificam as configurações de destino, incluindo o grupo de recursos e a rede na qual a VM do Azure será localizada após o failover. Eles especificam a conta de armazenamento na qual os dados replicados serão armazenados.

    ![Habilitar destino de replicação](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication2.png)

4. Eles selecionam **WebVM** para replicação. Site Recovery instala o serviço de mobilidade em cada VM quando a replicação está habilitada.

    ![Habilitar replicação-selecione a VM](./media/contoso-migration-rehost-vm-sql-managed-instance/enable-replication3.png)

5. Eles verificam se a política de replicação correta está selecionada e habilita a replicação para **WEBVM**. Eles rastreiam o progresso da replicação nos **trabalhos**. Após o trabalho de **Finalizar Proteção** ser executado, o computador estará pronto para failover.

6. No **Essentials** no portal do Azure, eles podem ver o status das VMs que estão replicando para o Azure:

    ![Exibição de infraestrutura](./media/contoso-migration-rehost-vm-sql-managed-instance/essentials.png)

**Precisa de mais ajuda?**

Você pode ler uma explicação completa dessas etapas em [habilitar a replicação](https://docs.microsoft.com/azure/site-recovery/vmware-azure-enable-replication).

## <a name="step-6-migrate-the-database"></a>Etapa 6: migrar o banco de dados

Os administradores da Contoso precisam criar um projeto de serviço de migração de banco de dados do Azure e migrar o banco de dados.

### <a name="create-an-azure-database-migration-service-project"></a>Criar um projeto de serviço de migração de banco de dados do Azure

1. Eles criam um projeto de serviço de migração de banco de dados do Azure. Eles selecionam o tipo de servidor de origem **SQL Server** e **instância gerenciada do banco de dados SQL do Azure** como o destino.

     ![Serviço de migração de banco de dados – novo projeto de migração](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-project.png)

2. O assistente de migração é aberto.

### <a name="migrate-the-database"></a>Migrar o banco de dados

1. No assistente de migração, eles especificam a VM de origem na qual o banco de dados local está localizado. Eles inserem as credenciais para acessar o banco de dados.

    ![Serviço de migração de banco de dados-detalhes da origem](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-source.png)

2. Eles selecionam o banco de dados a ser migrado (**SmartHotel. Registration**):

    ![Serviço de migração de banco de dados – selecionar bancos de dados de origem](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-wizard-sourcedb.png)

3. Para o destino, eles inserem o nome do Instância Gerenciada no Azure e as credenciais de acesso.

    ![Serviço de migração de banco de dados-detalhes de destino](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-target-details.png)

4. Em uma **nova atividade**  > **executar a migração**, eles especificam as configurações para executar a migração:
    - Credenciais de origem e de destino.
    - O banco de dados a ser migrado.
    - O compartilhamento de rede criado na VM local. O serviço de migração de banco de dados do Azure leva os backups de origem para esse compartilhamento.
        - A conta de serviço que executa a instância de SQL Server de origem deve ter permissões de gravação nesse compartilhamento.
        - O caminho FQDN para o compartilhamento deve ser usado.
    - O URI de SAS que fornece o serviço de migração de banco de dados do Azure com acesso ao contêiner da conta de armazenamento para o qual o serviço carrega os arquivos de backup para migração.

        ![Serviço de migração de banco de dados – definir configurações de migração](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-migration-settings.png)

5. Eles salvam as configurações de migração e, em seguida, executam a migração.
6. Em **visão geral**, eles monitoram o status de migração.

    ![Serviço de migração de banco de dados – monitor](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-monitor1.png)

7. Quando a migração é concluída, eles verificam se os bancos de dados de destino existem no Instância Gerenciada.

    ![Serviço de migração de banco de dados – verificar a migração de banco de dados](./media/contoso-migration-rehost-vm-sql-managed-instance/dms-monitor2.png)

## <a name="step-7-migrate-the-vm"></a>Etapa 7: migrar a VM

Os administradores da Contoso executam um failover de teste rápido e, em seguida, migram a VM.

### <a name="run-a-test-failover"></a>Execute um teste de failover

Antes de migrar WEBVM, um failover de teste ajuda a garantir que tudo funcione conforme o esperado. Os administradores concluem as seguintes etapas:

1. Eles executam um failover de teste para o último ponto no tempo disponível (**mais recente processado**).
2. Eles selecionam **desligar o computador antes do início do failover**. Com essa opção selecionada, o Site Recovery tenta desligar a VM de origem antes de disparar o failover. O failover continua, mesmo se o desligamento falhar.
3. Execuções de failover de teste: a. Uma verificação de pré-requisitos é executada para garantir que todas as condições necessárias para a migração estejam em vigor.
    b. O failover processa os dados para que uma VM do Azure possa ser criada. Se o ponto de recuperação mais recente for selecionado, um ponto de recuperação será criado a partir dos dados.
    c. A VM do Azure é criada usando os dados processados na etapa anterior.
4. Quando o failover for concluído, a VM do Azure de réplica aparecerá na portal do Azure. Eles verificam se tudo está funcionando corretamente: a VM é o tamanho apropriado, está conectada à rede correta e está em execução.
5. Depois de verificar o failover de teste, eles limpam o failover e registram as observações.

### <a name="migrate-the-vm"></a>Migrar a VM

1. Depois de verificar se o failover de teste funcionou conforme o esperado, os administradores da Contoso criam um plano de recuperação para migração e adicionam WEBVM ao plano:

     ![Criar plano de recuperação-selecionar itens](./media/contoso-migration-rehost-vm-sql-managed-instance/recovery-plan.png)

2. Eles executam um failover no plano, selecionando o último ponto de recuperação. Eles especificam que Site Recovery deve tentar desligar a VM local antes de disparar o failover.

    ![Failover](./media/contoso-migration-rehost-vm-sql-managed-instance/failover1.png)

3. Após o failover, eles verificam se a VM do Azure aparece como esperado no portal do Azure.

   ![Detalhes do plano de recuperação](./media/contoso-migration-rehost-vm-sql-managed-instance/failover2.png)

4. Após a verificação, eles concluem a migração para concluir o processo de migração, interromper a replicação da VM e interromper Site Recovery cobrança para a VM.

    ![Failover – migração completa](./media/contoso-migration-rehost-vm-sql-managed-instance/failover3.png)

### <a name="update-the-connection-string"></a>Atualizar a cadeia de conexão

Como a etapa final do processo de migração, os administradores da Contoso atualizam a cadeia de conexão do aplicativo para apontar para o banco de dados migrado que está sendo executado no Instância Gerenciada da contoso.

1. No portal do Azure, eles encontram a cadeia de conexão selecionando **configurações**  > **cadeias de conexão**.

    ![Cadeias de conexão](./media/contoso-migration-rehost-vm-sql-managed-instance/failover4.png)

2. Eles atualizam a cadeia de caracteres com o nome de usuário e a senha do Instância Gerenciada do Banco de Dados SQL.
3. Depois que a cadeia de caracteres é configurada, ela substitui a cadeia de conexão atual no arquivo Web. config de seu aplicativo.
4. Depois de atualizar o arquivo e salvá-lo, eles reiniciarão o IIS no WEBVM executando `IISRESET /RESTART` em uma janela de prompt de comando.
5. Depois que o IIS é reiniciado, o aplicativo usa o banco de dados que está sendo executado no Instância Gerenciada do Banco de Dados SQL.
6. Neste ponto, eles podem desligar o computador SQLVM no local. A migração foi concluída.

**Precisa de mais ajuda?**

- Saiba como [executar um failover de teste](https://docs.microsoft.com/azure/site-recovery/tutorial-dr-drill-azure).
- Saiba como [criar um plano de recuperação](https://docs.microsoft.com/azure/site-recovery/site-recovery-create-recovery-plans).
- Saiba como fazer failover [para o Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-failover).

## <a name="clean-up-after-migration"></a>Limpar após a migração

Com a migração concluída, o aplicativo SmartHotel360 está em execução em uma VM do Azure e o banco de dados SmartHotel360 está disponível no Instância Gerenciada do Banco de Dados SQL do Azure.

Agora, a contoso precisa fazer as seguintes tarefas de limpeza:

- Remova o computador WEBVM do inventário de vCenter Server.
- Remova o computador SQLVM do inventário de vCenter Server.
- Remova WEBVM e SQLVM dos trabalhos de backup locais.
- Atualize a documentação interna para mostrar o novo local e o endereço IP para WEBVM.
- Remova o SQLVM da documentação interna. Como alternativa, a Contoso pode revisar a documentação para mostrar SQLVM como excluído e não mais no inventário de VM.
- Examine todos os recursos que interagem com as VMs descomissionadas. Atualize quaisquer configurações ou documentações relevantes para refletir a nova configuração.

## <a name="review-the-deployment"></a>Examinar a implantação

Com os recursos migrados no Azure, a contoso precisa operacionalize e proteger totalmente sua nova infraestrutura.

### <a name="security"></a>Segurança

A equipe de segurança da Contoso revisa as VMs do Azure e Instância Gerenciada do Banco de Dados SQL para verificar se há problemas de segurança com sua implementação:

- A equipe revisa os grupos de segurança de rede usados para controlar o acesso à VM. Os grupos de segurança de rede ajudam a garantir que apenas o tráfego permitido para o aplicativo possa passar.
- A equipe de segurança da Contoso também está considerando a proteção dos dados no disco usando Azure Disk Encryption e Azure Key Vault.
- A equipe habilita a detecção de ameaças no Instância Gerenciada. A detecção de ameaças envia um alerta para o sistema de equipe de segurança/serviço de suporte da Contoso para abrir um tíquete se uma ameaça for detectada. Saiba mais sobre [a detecção de ameaças para instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-threat-detection).

     ![Segurança de Instância Gerenciada-detecção de ameaças](./media/contoso-migration-rehost-vm-sql-managed-instance/mi-security.png)

Para saber mais sobre as práticas de segurança para VMs, consulte [práticas recomendadas de segurança para cargas de trabalho de IaaS no Azure](https://docs.microsoft.com/azure/security/azure-security-best-practices-vms).

### <a name="bcdr"></a>BCDR

Para a continuidade dos negócios e a recuperação de desastres (BCDR), a contoso executa as seguintes ações:

- Manter os dados seguros: a contoso faz backup dos dados nas VMs usando o serviço de backup do Azure. [Saiba mais](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
- Manter aplicativos em funcionamento: a contoso Replica as VMs de aplicativo no Azure para uma região secundária usando Site Recovery. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart).
- A contoso aprende mais sobre o gerenciamento do SQL Instância Gerenciada, incluindo [backups de banco de dados](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

### <a name="licensing-and-cost-optimization"></a>Licenciamento e otimização de custos

- A contoso tem um licenciamento existente para o WEBVM. Para aproveitar os preços com o Benefício Híbrido do Azure, a contoso converte a VM do Azure existente.
- A contoso habilita o gerenciamento de custos do Azure licenciado pelo Cloudyn, uma subsidiária da Microsoft. O gerenciamento de custos é uma solução de gerenciamento de custos de nuvem que ajuda a Contoso a usar e gerenciar o Azure e outros recursos de nuvem. Saiba mais sobre o [Gerenciamento de custos do Azure](https://docs.microsoft.com/azure/cost-management/overview).

## <a name="conclusion"></a>Conclusão

Neste artigo, a contoso rehospeda o aplicativo SmartHotel360 no Azure migrando a VM de front-end do aplicativo para o Azure usando o serviço Site Recovery. A contoso migra o banco de dados local para um Instância Gerenciada do Banco de Dados SQL do Azure usando o serviço de migração de banco de dados do Azure.
