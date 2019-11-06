---
title: Rehospedar um aplicativo em VMs do Azure com Azure Site Recovery
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como a contoso rehospeda um aplicativo local com uma migração de comparação de precisão e deslocamento de computadores locais para o Azure, usando o serviço de Azure Site Recovery.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 3de31e419ea701f8e7e7091d14db1884a4b641d2
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566472"
---
# <a name="rehost-an-on-premises-app-on-azure-vms"></a>Rehospedar um aplicativo local em VMs do Azure

Este artigo demonstra como a empresa fictícia Contoso hospeda novamente um aplicativo de front-end do Windows .NET de duas camadas em execução em VMs VMware, migrando as VMs do aplicativo para a VMs do Azure.

O aplicativo SmartHotel360 usado neste exemplo é fornecido como software livre. Se quiser usá-lo em seus próprios testes, você poderá baixá-lo do [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Geradores de negócios

A equipe de liderança de TI trabalhou em conjunto com parceiros comerciais para entender o que eles desejam obter com essa migração:

- **Lidar com o crescimento da empresa.** A Contoso está crescendo e, como resultado, há pressão sobre seus sistemas e infraestrutura locais.
- **Limitar riscos.** O aplicativo SmartHotel360 é crítico para o negócio da Contoso. Ela deseja passar o aplicativo para o Azure sem nenhum risco.
- **Estender.** A Contoso não quer modificar o aplicativo, mas deseja garantir que ele fique estável.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem da Contoso fixou metas para esta migração. Essas metas são usadas para determinar o melhor método de migração:

- Após a migração, o aplicativo no Azure deve ter os mesmos recursos de desempenho de hoje no VMware. O aplicativo permanecerá essencial tanto na nuvem quanto localmente.
- A contoso não quer investir nesse aplicativo. Ele é importante para os negócios, mas, em sua forma atual, a Contoso apenas deseja passá-lo com segurança para a nuvem.
- A Contoso não quer alterar o modelo de operações para este aplicativo. A Contoso deseja interagir com ele na nuvem da mesma forma que faz agora.
- A Contoso não quer alterar nenhuma funcionalidade do aplicativo. Somente o local do aplicativo será alterado.

## <a name="solution-design"></a>Design da solução

Depois de fixar metas e requisitos, a Contoso cria e examina uma solução de implantação e identifica o processo de migração, incluindo os serviços do Azure que ela usará para a migração.

### <a name="current-app"></a>Aplicativo atual

- O aplicativo está em camadas em duas VMs (**WEBVM** e **SQLVM**).
- As VMs estão localizadas no host VMware ESXi **contosohost1.contoso.com** (versão 6.5).
- O ambiente VMware é gerenciado pelo vCenter Server 6.5 (**vcenter.contoso.com**) em execução em uma VM.
- A Contoso tem um datacenter local (contoso-datacenter), com um controlador de domínio local (**contosodc1**).

### <a name="proposed-architecture"></a>Arquitetura proposta

- Como o aplicativo é uma carga de trabalho de produção, as VMs no Azure residirão no grupo de recursos de produção ContosoRG.
- As VMs do aplicativo serão migradas para a região principal do Azure (Leste dos EUA 2) e colocadas na rede de produção (VNET-PROD-EUS2).
- A VM do front-end da Web residirá na sub-rede do front-end (PROD-FE-EUS2), na rede de produção.
- A VM do banco de dados residirá na sub-rede do banco de dados (PROD-DB-EUS2) na rede de produção.
- As VMs locais no datacenter Contoso, serão descomissionadas após a migração.

![Arquitetura de cenário](./media/contoso-migration-rehost-vm/architecture.png)

### <a name="database-considerations"></a>Considerações do banco de dados

Como parte do processo para criar a solução, a Contoso fez uma comparação de recursos entre o Banco de Dados SQL do Azure e o SQL Server. As seguintes considerações os ajudaram a optar pelo SQL Server em execução em uma VM de IaaS do Azure:

- Usar uma VM do Azure que executa o SQL Server parece ser uma solução ideal se a Contoso precisa personalizar o sistema operacional ou o servidor de banco de dados ou se ela deseja colocar a executar aplicativos de terceiros na mesma VM.
- Com o Software Assurance, futuramente, a Contoso poderá trocar suas licenças existentes por taxas com desconto em uma Instância Gerenciada do Banco de Dados SQL usando o Benefício Híbrido do Azure para SQL Server. Com essa opção, é possível economizar até 30% na Instância Gerenciada.

### <a name="solution-review"></a>Análise de solução

A Contoso avalia o design proposto reunindo uma lista de prós e contras.

<!-- markdownlint-disable MD033 -->

**Consideração** | **Detalhes**
--- | ---
**Prós** | As duas VMs do aplicativo serão movidas para o Azure sem alterações, simplificando a migração.<br/><br/> Como a Contoso está usando uma abordagem de comparação e de deslocamento para ambas as VMs de aplicativo, nenhuma ferramenta especial de configuração ou migração é necessária para o banco de dados de aplicativo.<br/><br/> A Contoso pode aproveitar seu investimento em Software Assurance usando o Benefício Híbrido do Azure.<br/><br/> A Contoso manterá o controle total sobre as VMs do aplicativo no Azure.
**Contras** | A WEBVM e a SQLVM estão em execução no Windows Server 2008 R2. O sistema operacional é compatível com o Azure para funções específicas (julho de 2018). [Saiba mais](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines).<br/><br/> As camadas da Web e de dados do aplicativo continuarão sendo um ponto único de failover.<br/><br/> A SQLVM está em execução no SQL Server 2008 R2, que não faz parte do suporte base. No entanto, há suporte para ele nas VMs do Azure (julho de 2018). [Saiba mais](https://support.microsoft.com/help/956893).<br/><br/> A Contoso precisará continuar dando suporte ao aplicativo como VMs do Azure, em vez de passar para um serviço gerenciado, como o Serviço de Aplicativo do Azure e o Banco de Dados SQL do Azure.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo de migração

A Contoso migrará o front-end do aplicativo e as VMs do banco de dados para VMs do Azure usando o método sem agente da ferramenta de Migração de Servidor das Migrações para Azure.

- Como primeira etapa, a Contoso prepara e configura os componentes do Azure para a Migração de Servidor das Migrações para Azure e prepara a infraestrutura do VMware local.
- Eles já têm a [infraestrutura do Azure](./contoso-migration-infrastructure.md) estabelecida, portanto, a Contoso precisa apenas adicionar e configurar a replicação das VMs usando a ferramenta de Migração de Servidor das Migrações para Azure.
- Com tudo preparado, a Contoso pode iniciar a replicação das VMs.
- Depois que a replicação estiver habilitada e funcionando, a Contoso migrará a VM efetuando failover para o Azure.

![Processo de migração](./media/contoso-migration-rehost-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Serviços do Azure

**Serviço** | **Descrição** | **Custo**
--- | --- | ---
[Migração de Servidor das Migrações para Azure](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm) | O serviço orquestra e gerencia a migração de seus aplicativos e cargas de trabalho locais, bem como de instâncias de VM do AWS/GCP. | Durante a replicação para o Azure, são gerados encargos do Armazenamento do Azure. As VMs do Azure são criadas e incorrem em encargos quando ocorre failover. [Saiba mais](https://azure.microsoft.com/pricing/details/azure-migrate) sobre encargos e preços.

## <a name="prerequisites"></a>Pré-requisitos

Aqui está o que a Contoso precisa para executar esse cenário.

<!-- markdownlint-disable MD033 -->

**Requisitos** | **Detalhes**
--- | ---
**Assinatura do Azure** | A Contoso criou assinaturas em um artigo anterior desta série. Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se você criar uma conta gratuita, será o administrador da assinatura e poderá executar todas as ações.<br/><br/> Se você usar uma assinatura existente e não for o administrador, será necessário trabalhar com o administrador para receber permissões de Proprietário ou de Colaborador.<br/><br/> Se forem necessárias permissões mais granulares, leia [este artigo](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infraestrutura do Azure** | [ Saiba como ](./contoso-migration-infrastructure.md) a Contoso configurou uma infraestrutura do Azure.<br/><br/> Saiba mais sobre os [pré-requisitos](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prerequisites) específicos necessários para a Migração de Servidor das Migrações para Azure.
**Servidores locais** | vCenter Servers locais devem estar executando a versão 5.5, 6.0 ou 6.5<br/><br/> Hosts ESXi devem executar a versão 5.5, 6.0 ou 6.5<br/><br/> Uma ou mais VMs do VMware devem estar em execução no host ESXi.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Etapas do cenário

Aqui está como os administradores da Contoso executarão a migração:

> [!div class="checklist"]
>
> - **Etapa 1: preparar a migração de servidor do Azure para migrações para Azure.** Eles adicionam a ferramenta de Migração de Servidor ao projeto das Migrações para Azure.
> - **Etapa 2: preparar a migração local do VMware para o Azure migrar servidor.** Eles preparam contas para a descoberta de VMs e se preparam para a conexão com VMs do Azure após o failover.
> - **Etapa 3: replicar VMs.** Configuram a replicação e começam a replicar as VMs para armazenamento do Azure.
> - **Etapa 4: migre as VMs com a migração de servidor de migrações para Azure.** Executam um failover de teste para certificar-se de que tudo está funcionando e, em seguida, executam um failover completo para migrar as VMs para o Azure.

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Etapa 1: preparar o Azure para a ferramenta de migração de servidor de migrações para Azure

Aqui estão os componentes do Azure que a Contoso precisa para migrar as máquinas virtuais para o Azure:

- Uma rede virtual na qual as VMs do Azure serão localizadas quando forem criadas durante o failover.
- A ferramenta de Migração de Servidor das Migrações para Azure provisionada.

Eles configuram isso tudo da seguinte maneira:

1. Configurar uma rede – a Contoso já configurou uma rede que pode ser usada para a Migração de Servidor das Migrações para Azure quando [implantou a infraestrutura do Azure](./contoso-migration-infrastructure.md)

    - O aplicativo SmartHotel360 é um aplicativo de produção e as VMs serão migradas para a rede de produção do Azure (VNET-PROD-EUS2) na região primária do leste dos EUA 2.
    - As duas máquinas virtuais serão colocadas no grupo de recursos ContosoRG, que é usado para recursos de produção.
    - A VM do front-end do aplicativo (WEBVM) migrará para a sub-rede de front-end (PROD-FE-EUS2), na rede de produção.
    - A VM do banco de dados do aplicativo (SQLVM) será migrada para a sub-rede do banco de dados (PROD-DB-EUS2), na rede de produção.

2. Provisionar a ferramenta de Migração de Servidor das Migrações para Azure – com a rede e a conta de armazenamento prontas, a Contoso cria um cofre dos Serviços de Recuperação (ContosoMigrationVault) e coloca-o no grupo de recursos ContosoFailoverRG na região Leste dos EUA 2 primária.

    ![Ferramenta de Migração de Servidor das Migrações para Azure](./media/contoso-migration-rehost-vm/server-migration-tool.png)

**Precisa de mais ajuda?**

[Saiba mais](https://docs.microsoft.com/azure/migrate) sobre como configurar a ferramenta de Migração de Servidor das Migrações para Azure.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Preparar para conectar VMs do Azure após o failover

Após o failover, a Contoso deseja se conectar a máquinas virtuais do Azure. Para fazer isso, os administradores da Contoso fazem o seguinte antes da migração:

1. Para acesso pela internet, eles:

    - Habilitam o RDP na VM local antes do failover.
    - Assegure-se de que as regras TCP e UDP sejam incluídas para o perfil **Público**.
    - Verifique se o RDP é permitido no **Firewall do Windows**  >  **Aplicativos permitidos** para todos os perfis.

2. Para acesso por VPN site-to-site, eles:

    - Ative o RDP na máquina no local.
    - Permitir o RDP no **Firewall do Windows**  ->  **Aplicativos e recursos permitidos**, para **Domínio e redes particulares**.
    - Defina a política de SAN do sistema operacional na VM local para **OnlineAll**.

Além disso, quando eles executam um failover, precisam verificar o seguinte:

- Não deve haver atualizações do Windows pendentes na VM ao acionar um failover. Se houver, eles não poderão efetuar login na VM até que a atualização seja concluída.
- Após o failover, eles podem verificar **Diagnósticos de inicialização** para exibir uma captura de tela da VM. Se isso não funcionar, eles devem verificar se a VM está em execução e revisar essas [ dicas de solução de problemas ](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Precisa de mais ajuda?**

- [Saiba mais](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prepare-vms-for-migration) sobre a preparação de VMs para migração

## <a name="step-3-replicate-the-on-premises-vms"></a>Etapa 3: Replicar VMs locais

Antes que os administradores da Contoso possam executar uma migração para o Azure, eles precisam configurar e habilitar a replicação.

Com a descoberta concluída, é possível começar a replicação de VMs do VMware no Azure.

1. No projeto de migração do Azure > **servidores**, **migrações para Azure: migração de servidor**, clique em **replicar**.

    ![Replicar VMs](./media/contoso-migration-rehost-vm/select-replicate.png)

2. Em **Replicar**, > **Configurações de origem** > **Seus computadores estão virtualizados?** , selecione **Sim, com o VMware vSphere**.

3. Em **Dispositivo local**, selecione o nome do dispositivo de Migrações para Azure que você configurou > **OK**.

    ![Configurações de origem](./media/contoso-migration-rehost-vm/source-settings.png)

4. Em **Máquinas virtuais**, selecione os computadores que deseja replicar.
    - Se você tiver executado uma avaliação das VMs, poderá aplicar recomendações de dimensionamento de VM e de tipo de disco (Premium/Standard) dos resultados da avaliação. Para fazer isso, em **Importar configurações de migração de uma avaliação de Migrações para Azure?** , selecione a opção **Sim**.
    - Se você não tiver executado uma avaliação ou não quiser usar as configurações de avaliação, selecione a opção **Não**.
    - Se você optou por usar a avaliação, selecione o grupo de VMs e o nome da avaliação.

    ![Selecionar avaliação](./media/contoso-migration-rehost-vm/select-assessment.png)

5. Em **Máquinas virtuais**, pesquise as VMs conforme necessário e marque cada VM que você deseja migrar. Em seguida, clique em **Avançar: configurações de destino**.

6. Em **Configurações de destino**, selecione a assinatura e a região de destino para a qual você migrará e especifique o grupo de recursos no qual as VMs do Azure residirão após a migração. Em **Rede Virtual**, selecione a VNet/sub-rede do Azure na qual as VMs do Azure serão ingressadas após a migração.

7. Em **benefício híbrido do Azure**, selecione o seguinte:

    - Selecione **Não** se não desejar aplicar o Benefício Híbrido do Azure. Em seguida, clique em **Próximo**.
    - Selecione **Sim** se você tiver computadores Windows Server cobertos com assinaturas ativas do Software Assurance ou do Windows Server e quiser aplicar o benefício aos computadores que estão sendo migrados. Em seguida, clique em **Próximo**.

8. Em **Computação**, examine o nome da VM, o tamanho, o tipo de disco do sistema operacional e o conjunto de disponibilidade. As VMs devem estar em conformidade com os [requisitos do Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#agentless-migration-vmware-vm-requirements).

    - **Tamanho da VM:** Se você estiver usando recomendações de avaliação, a lista suspensa tamanho da VM conterá o tamanho recomendado. Caso contrário, as Migrações para Azure escolherão um tamanho com base na correspondência mais próxima na assinatura do Azure. Como alternativa, escolha um tamanho manual em **Tamanho da VM do Azure**.
    - **Disco do so:** Especifique o disco do sistema operacional (inicialização) para a VM. O disco do sistema operacional é o disco que tem o carregador de inicialização e o instalador do sistema operacional.
    - **Conjunto de disponibilidade:** Se a VM deve estar em um conjunto de disponibilidade do Azure após a migração, especifique o conjunto. O conjunto precisa estar no grupo de recursos de destino especificado para a migração.

9. Em **Discos**, especifique se os discos de VM devem ser replicados no Azure e selecione o tipo de disco (discos gerenciados Premium ou HDD/SSD Standard) no Azure. Em seguida, clique em **Próximo**.
    - Você pode excluir discos da replicação.
    - Se você excluir os discos, eles não estarão presentes na VM do Azure após a migração.

10. Em **Examinar e iniciar a replicação**, examine as configurações e clique em **Replicar** para iniciar a replicação inicial dos servidores.

> [!NOTE]
> É possível atualizar configurações de replicação a qualquer momento antes que a replicação seja iniciada em **Gerenciar** > **Replicando computadores**. Não é possível alterar as configurações após o início da replicação.

## <a name="step-4-migrate-the-vms"></a>Etapa 4: Migrar as VMs

Os administradores da Contoso executam um failover de teste rápido e, em seguida, um failover completo para migrar as máquinas virtuais.

### <a name="run-a-test-failover"></a>Execute um teste de failover

1. Em **metas de migração** > **servidores** > **migrações para Azure: migração de servidor**, clique em **testar servidores migrados**.

     ![Testar servidores migrados](./media/contoso-migration-rehost-vm/test-migrated-servers.png)

2. Clique com o botão direito do mouse na VM a ser testada e clique em **Migração de teste**.

    ![Migração de teste](./media/contoso-migration-rehost-vm/test-migrate.png)

3. Em **Migração de Teste**, selecione a VNet do Azure na qual a VM do Azure estará localizada após a migração. Recomendamos que você use uma VNet que não seja de produção.
4. O trabalho **Migração de teste** é iniciado. Monitore o trabalho nas notificações do portal.
5. Após a conclusão da migração, veja a VM do Azure migrada em **Máquinas Virtuais** no portal do Azure. O nome do computador tem o sufixo **-Test**.
6. Depois que o teste for realizado, clique com o botão direito do mouse na VM do Azure em **Replicando computadores** e clique em **Limpar migração de teste**.

    ![Limpar migração](./media/contoso-migration-rehost-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Migrar as VMs

Agora os administradores da Contoso podem executar um failover completo para concluir a migração.

1. No projeto de migração do Azure > **servidores** > **migrações para Azure: migração de servidor**, clique em **replicar servidores**.

    ![Replicando servidores](./media/contoso-migration-rehost-vm/replicating-servers.png)

2. Em **Replicando computadores**, clique com o botão direito do mouse na VM > **Migrar**.
3. Em **Migrar** > **Desligar máquinas virtuais e realizar uma migração planejada sem perda de dados**, selecione **Sim** > **OK**.
    - Por padrão, as Migrações para Azure desligam a VM local e executam uma replicação sob demanda para sincronizar as alterações de VM ocorridas desde a última replicação. Isso garante que não haja nenhuma perda de dados.
    - Se você não quiser desligar a VM, selecione **Não**
4. Um trabalho de migração é iniciado para a VM. Acompanhe o trabalho nas notificações do Azure.
5. Após a conclusão do trabalho, você poderá exibir e gerenciar a VM na página **Máquinas Virtuais**.

**Precisa de mais ajuda?**

- [Saiba mais](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) sobre como executar failovers de teste.
- [Saiba mais](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) sobre a migração de VMs para o Azure.

## <a name="clean-up-after-migration"></a>Limpeza após a migração

Com a migração concluída, as camadas de aplicativos do SmartHotel360 agora estão em execução nas VMs do Azure.

Agora, a Contoso precisa concluir estas etapas de limpeza:

- Após a conclusão da migração, pare a replicação.
- Remova a máquina WEBVM do inventário do vCenter.
- Remova a máquina do SQLVM do inventário do vCenter.
- Remover WEBVM e SQLVM dos trabalhos de backup locais.
- Atualizar a documentação interna para mostrar o novo local e endereços IP para as máquinas virtuais.
- Examinar todos os recursos que interagem com as máquinas virtuais e atualizar configurações relevantes ou documentação para refletir a nova configuração.

## <a name="review-the-deployment"></a>Revisar a implantação

Com o aplicativo em execução, a Contoso agora precisa utilizá-lo totalmente e protegê-lo no Azure.

### <a name="security"></a>Segurança

A equipe de segurança da Contoso revisa as VMs do Azure, para determinar os problemas de segurança.

- Para controlar o acesso, a equipe examina os NSGs (Grupos de Segurança de Rede) das VMs. Os NSGs são usados para garantir que somente o tráfego permitido para o aplicativo pode acessá-lo.
- A equipe também considera a proteção dos dados no disco usando o Azure Disk Encryption e o Key Vault.

Para obter mais informações, consulte [práticas recomendadas de segurança para cargas de trabalho de IaaS no Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

## <a name="bcdr"></a>BCDR

Para a BCDR (continuidade dos negócios e recuperação de desastres), a Contoso executa as seguintes ações:

- Mantém os dados seguros: a Contoso faz backup dos dados nas VMs usando o serviço de Backup do Azure. [Saiba mais](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
- Mantém os aplicativos em funcionamento: a Contoso replica as VMs do aplicativo no Azure para uma região secundária usando o Site Recovery. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart).

### <a name="licensing-and-cost-optimization"></a>Licenciamento e otimização de custo

1. A Contoso tem o licenciamento existente para suas VMs e aproveitará o Benefício Híbrido do Azure. A Contoso converterá as VMs do Azure existentes para aproveitar esses preços.
2. A Contoso habilitará o Gerenciamento de Custos do Azure licenciado pela Cloudyn, uma subsidiária da Microsoft. É uma solução de gerenciamento de custos em várias nuvens que ajuda a usar e gerenciar o Azure e outros recursos de nuvem. [Saiba mais](https://docs.microsoft.com/azure/cost-management/overview) sobre o Gerenciamento de Custos do Azure.

## <a name="conclusion"></a>Conclusão

Neste artigo, a Contoso hospedou novamente o aplicativo SmartHotel360 no Azure, migrando as VMs do aplicativo para VMs do Azure usando a ferramenta de Migração de Servidor das Migrações para Azure.
