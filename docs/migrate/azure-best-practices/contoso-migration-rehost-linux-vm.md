---
title: Hospede novamente um aplicativo Linux local para VMs do Azure
description: Saiba como a Contoso muda o host de um aplicativo Linux local migrando-o para VMs do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: b629cc932b54b7ef7c633cefc847ac3263477674
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807335"
---
# <a name="rehost-an-on-premises-linux-app-to-azure-vms"></a>Hospede novamente um aplicativo Linux local para VMs do Azure

Este artigo mostra como a empresa fictícia Contoso muda o host de um aplicativo LAMP (Apache MySQL PHP baseado em Linux) de dois níveis, usando VMs de IaaS do Azure.

O osTicket, o aplicativo de central de serviços usado neste exemplo, é fornecido como software livre. Se quiser usá-lo em seus próprios testes, você poderá baixá-lo do [GitHub](https://github.com/osTicket/osTicket).

## <a name="business-drivers"></a>Geradores de negócios

A equipe de liderança de TI trabalhou em conjunto com parceiros comerciais para entender o que eles desejam obter com essa migração:

- **Lidar com o crescimento da empresa.** A Contoso está crescendo e, como resultado, há pressão sobre os sistemas e a infraestrutura locais.
- **Limitar riscos.** O aplicativo da Central de Serviços é essencial para o negócio da Contoso. A Contoso quer movê-lo para o Azure com zero risco.
- **Estender.** Atualmente, a Contoso não quer alterar o aplicativo. Simplesmente deseja garantir que o aplicativo esteja estável.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem Contoso foi fixado para baixo objetivos para a migração, para determinar o melhor método de migração:

- Após a migração, o aplicativo no Azure deve ter as mesmas funcionalidades de desempenho atuais em seu ambiente de VMware local. O aplicativo permanecerá essencial tanto na nuvem quanto localmente.
- A contoso não quer investir nesse aplicativo. Ele é importante para os negócios, mas, em sua forma atual, a Contoso apenas deseja passá-lo com segurança para a nuvem.
- A Contoso não quer alterar o modelo de operações para este aplicativo. Ela deseja interagir com o aplicativo na nuvem da mesma maneira que faz agora.
- A Contoso não quer alterar a funcionalidade do aplicativo. Somente o local do aplicativo será alterado.
- Depois de concluir algumas migrações de aplicativo do Windows, a Contoso deseja aprender a usar uma infraestrutura baseada em Linux no Azure.

## <a name="solution-design"></a>Design da solução

Depois de fixar metas e requisitos, a Contoso cria e examina uma solução de implantação e identifica o processo de migração, incluindo os serviços do Azure que ela usará para a migração.

### <a name="current-app"></a>Aplicativo atual

- O aplicativo OSTicket é em camadas em duas VMs (**OSTICKETWEB** e **OSTICKETMYSQL**).
- As VMs estão localizadas no host VMware ESXi **contosohost1.contoso.com** (versão 6.5).
- O ambiente VMware é gerenciado pelo vCenter Server 6.5 (**vcenter.contoso.com**) em execução em uma VM.
- A Contoso tem um datacenter local (**contoso-datacenter**), com um controlador de domínio local ( **contosodc1**)

### <a name="proposed-architecture"></a>Arquitetura proposta

- Como o aplicativo é uma carga de trabalho de produção, as VMs no Azure residirão no grupo de recursos de produção **ContosoRG**.
- As máquinas virtuais serão migradas para a região principal (Leste dos EUA 2) e colocadas na rede de produção (VNET-PROD-EUS2):
  - A VM Web reside na sub-rede de front-end (PROD-FE-EUS2).
  - O banco de dados de máquina virtual residem na sub-rede de banco de dados (PROD-DB-EUS2).
- As VMs locais no datacenter da Contoso serão descomissionadas após a migração.

![Arquitetura de cenário](./media/contoso-migration-rehost-linux-vm/architecture.png)

### <a name="solution-review"></a>Análise de solução

A Contoso avalia o design proposto reunindo uma lista de prós e contras.

<!-- markdownlint-disable MD033 -->

**Consideração** | **Detalhes**
--- | ---
**Prós** | As duas VMs do aplicativo serão movidas para o Azure sem alterações, simplificando a migração.<br/><br/> Como a Contoso está usando uma abordagem de comparação e de deslocamento para ambas as VMs de aplicativo, nenhuma ferramenta especial de configuração ou migração é necessária para o banco de dados de aplicativo.<br/><br/> A Contoso manterá o controle total sobre as VMs do aplicativo no Azure. <br/><br/> As VMs do aplicativo executam o Ubuntu 16.04-TLS, que é uma distribuição endossada do Linux. [Saiba mais](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros).
**Contras** | A camada da Web e de dados do aplicativo continuará sendo um ponto único de failover. <br/><br/> A Contoso precisará continuar dando suporte ao aplicativo como VMs do Azure, em vez de mover para um serviço gerenciado, como o Serviço de Aplicativo do Azure e o Banco de Dados do Azure para MySQL.<br/><br/> A Contoso está ciente de que, ao manter as coisas simples com uma migração de VM de mudança e precisão, elas não aproveitam totalmente os recursos fornecidos pelo [banco de dados do Azure para MySQL](https://docs.microsoft.com/azure/mysql/overview) (alta disponibilidade interna, desempenho previsível, dimensionamento simples, backups automáticos e segurança interna).

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo de migração

A Contoso migrará da seguinte maneira:

- Como primeira etapa, a Contoso prepara e configura os componentes do Azure para a Migração de Servidor das Migrações para Azure e prepara a infraestrutura do VMware local.
- Eles já têm a [infraestrutura do Azure](./contoso-migration-infrastructure.md) estabelecida, portanto, a Contoso precisa apenas adicionar e configurar a replicação das VMs usando a ferramenta de Migração de Servidor das Migrações para Azure.
- Com tudo preparado, a Contoso pode iniciar a replicação das VMs.
- Depois que a replicação estiver habilitada e funcionando, a Contoso migrará a VM efetuando failover para o Azure.

![Processo de migração](./media/contoso-migration-rehost-linux-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Serviços do Azure

**Serviço** | **Descrição** | **Custo**
--- | --- | ---
[Migração de Servidor das Migrações para Azure](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm) | O serviço orquestra e gerencia a migração de seus aplicativos e cargas de trabalho locais, bem como de instâncias de VM do AWS/GCP. | Durante a replicação para o Azure, são gerados encargos do Armazenamento do Azure. As VMs do Azure são criadas e incorrem em encargos quando ocorre failover. [Saiba mais](https://azure.microsoft.com/pricing/details/azure-migrate) sobre encargos e preços.

## <a name="prerequisites"></a>Pré-requisitos

Veja o que a Contoso precisa para esse cenário.

<!-- markdownlint-disable MD033 -->

**Requisitos** | **Detalhes**
--- | ---
**Assinatura do Azure** | A Contoso criou assinaturas em um artigo anterior nesta série. Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se você criar uma conta gratuita, será o administrador da assinatura e poderá executar todas as ações.<br/><br/> Se você usar uma assinatura existente e não for o administrador, será necessário trabalhar com o administrador para receber permissões de Proprietário ou de Colaborador.<br/><br/> Se forem necessárias permissões mais granulares, leia [este artigo](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infraestrutura do Azure** |  [ Saiba como ](./contoso-migration-infrastructure.md) a Contoso configurou uma infraestrutura do Azure.<br/><br/> Saiba mais sobre os [pré-requisitos](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prerequisites) específicos necessários para a Migração de Servidor das Migrações para Azure.
**Servidores locais** | O servidor vCenter local deve estar executando a versão 5.5, 6.0 ou 6.5<br/><br/> Um host ESXi que executa a versão 5.5, 6.0 ou 6.5<br/><br/> Uma ou mais VMs do VMware em execução no host ESXi.
**VMs locais** | [Examine os computadores Linux](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros) endossados para execução no Azure.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Etapas do cenário

É assim que a Contoso concluirá a migração:

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

Eles configuram estes da seguinte forma:

1. **Configurar uma rede:** A contoso já configurou uma rede que pode ser para migração de servidor de migrações para Azure quando [implantou a infraestrutura do Azure](./contoso-migration-infrastructure.md)

    - O aplicativo SmartHotel360 é um aplicativo de produção e as VMs serão migradas para a rede de produção do Azure (VNET-PROD-EUS2) na região primária do leste dos EUA 2.
    - As duas máquinas virtuais serão colocadas no grupo de recursos ContosoRG, que é usado para recursos de produção.
    - A VM do front-end do aplicativo (WEBVM) migrará para a sub-rede de front-end (PROD-FE-EUS2), na rede de produção.
    - A VM do banco de dados do aplicativo (SQLVM) será migrada para a sub-rede do banco de dados (PROD-DB-EUS2), na rede de produção.

2. **Provisione a ferramenta de migração de servidor de migrações para Azure:** Com a conta de rede e de armazenamento em vigor, a contoso agora cria um cofre dos serviços de recuperação (ContosoMigrationVault) e o coloca no grupo de recursos do ContosoFailoverRG na região principal do leste dos EUA 2.

    ![Ferramenta de Migração de Servidor das Migrações para Azure](./media/contoso-migration-rehost-linux-vm/server-migration-tool.png)

**Precisa de mais ajuda?**

[Saiba mais](https://docs.microsoft.com/azure/migrate) sobre como configurar a ferramenta de Migração de Servidor das Migrações para Azure.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Preparar para conectar VMs do Azure após o failover

Após o failover no Azure, a Contoso deseja ser capaz de se conectar às VMs replicadas no Azure. Para fazer isso, os administradores da Contoso precisam executar algumas ações:

- Para acessar as VMs do Azure pela Internet, eles habilitam SSH na VM Linux local antes da migração. No cado do Ubuntu, isso pode ser feito usando o seguinte comando: **Sudo apt-get ssh install -y**.
- Depois de executar a migração (failover), eles devem verificar os **Diagnósticos de inicialização** para exibir uma captura de tela da VM.
- Se isso não funcionar, será necessário verificar se a VM está em execução e revisar estas [dicas de solução de problemas](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Precisa de mais ajuda?**

- [Saiba mais](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prepare-vms-for-migration) sobre a preparação de VMs para migração

## <a name="step-3-replicate-the-on-premises-vms"></a>Etapa 3: Replicar máquinas virtuais no local

Antes que os administradores da Contoso possam executar uma migração para o Azure, eles precisam configurar e habilitar a replicação.

Com a descoberta concluída, é possível começar a replicação de VMs do VMware no Azure.

1. No projeto de migração do Azure > **servidores**, **migrações para Azure: migração de servidor**, clique em **replicar**.

    ![Replicar VMs](./media/contoso-migration-rehost-linux-vm/select-replicate.png)

2. Em **Replicar**, > **Configurações de origem** > **Seus computadores estão virtualizados?** , selecione **Sim, com o VMware vSphere**.

3. Em **Dispositivo local**, selecione o nome do dispositivo de Migrações para Azure que você configurou > **OK**.

    ![Configurações de origem](./media/contoso-migration-rehost-linux-vm/source-settings.png)

4. Em **Máquinas virtuais**, selecione os computadores que deseja replicar.
    - Se você tiver executado uma avaliação das VMs, poderá aplicar recomendações de dimensionamento de VM e de tipo de disco (Premium/Standard) dos resultados da avaliação. Para fazer isso, em **Importar configurações de migração de uma avaliação de Migrações para Azure?** , selecione a opção **Sim**.
    - Se você não tiver executado uma avaliação ou não quiser usar as configurações de avaliação, selecione a opção **Não**.
    - Se você optou por usar a avaliação, selecione o grupo de VMs e o nome da avaliação.

    ![Selecionar avaliação](./media/contoso-migration-rehost-linux-vm/select-assessment.png)

5. Em **Máquinas virtuais**, pesquise as VMs conforme necessário e marque cada VM que você deseja migrar. Em seguida, clique em **Avançar: configurações de destino**.

6. Em **Configurações de destino**, selecione a assinatura e a região de destino para a qual você migrará e especifique o grupo de recursos no qual as VMs do Azure residirão após a migração. Em **Rede Virtual**, selecione a VNet/sub-rede do Azure na qual as VMs do Azure serão ingressadas após a migração.

7. Em **benefício híbrido do Azure**, selecione o seguinte:

    - Selecione **Não** se não desejar aplicar o Benefício Híbrido do Azure. Em seguida, clique em **Próximo**.
    - Selecione **Sim** se você tiver computadores Windows Server cobertos com assinaturas ativas do Software Assurance ou do Windows Server e quiser aplicar o benefício aos computadores que estão sendo migrados. Em seguida, clique em **Próximo**.

8. Em **Computação**, examine o nome da VM, o tamanho, o tipo de disco do sistema operacional e o conjunto de disponibilidade. As VMs devem estar em conformidade com os [requisitos do Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#vmware-requirements).

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

     ![Testar servidores migrados](./media/contoso-migration-rehost-linux-vm/test-migrated-servers.png)

2. Clique com o botão direito do mouse na VM a ser testada e clique em **Migração de teste**.

    ![Migração de teste](./media/contoso-migration-rehost-linux-vm/test-migrate.png)

3. Em **Migração de Teste**, selecione a VNet do Azure na qual a VM do Azure estará localizada após a migração. Recomendamos que você use uma VNet que não seja de produção.
4. O trabalho **Migração de teste** é iniciado. Monitore o trabalho nas notificações do portal.
5. Após a conclusão da migração, veja a VM do Azure migrada em **Máquinas Virtuais** no portal do Azure. O nome do computador tem o sufixo **-Test**.
6. Depois que o teste for realizado, clique com o botão direito do mouse na VM do Azure em **Replicando computadores** e clique em **Limpar migração de teste**.

    ![Limpar migração](./media/contoso-migration-rehost-linux-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Migrar as VMs

Agora os administradores da Contoso podem executar um failover completo para concluir a migração.

1. No projeto de migração do Azure > **servidores** > **migrações para Azure: migração de servidor**, clique em **replicar servidores**.

    ![Replicando servidores](./media/contoso-migration-rehost-linux-vm/replicating-servers.png)

2. Em **Replicando computadores**, clique com o botão direito do mouse na VM > **Migrar**.
3. Em **Migrar** > **Desligar máquinas virtuais e realizar uma migração planejada sem perda de dados**, selecione **Sim** > **OK**.
    - Por padrão, as Migrações para Azure desligam a VM local e executam uma replicação sob demanda para sincronizar as alterações de VM ocorridas desde a última replicação. Isso garante que não haja nenhuma perda de dados.
    - Se você não quiser desligar a VM, selecione **Não**
4. Um trabalho de migração é iniciado para a VM. Acompanhe o trabalho nas notificações do Azure.
5. Após a conclusão do trabalho, você poderá exibir e gerenciar a VM na página **Máquinas Virtuais**.

### <a name="connect-the-vm-to-the-database"></a>Conectar a VM ao banco de dados

Como a etapa final no processo de migração, os administradores da Contoso atualizam a cadeia de conexão do aplicativo para apontar para o banco de dados do aplicativo na VM **OSTICKETMYSQL**.

1. Eles fazer uma conexão SSH para a **OSTICKETWEB** VM usando Putty ou outro cliente SSH. A VM é particular e, portanto, ela se conecta usando o endereço IP privado.

    ![Conectar ao banco de dados](./media/contoso-migration-rehost-linux-vm/db-connect.png)

    ![Conectar ao banco de dados](./media/contoso-migration-rehost-linux-vm/db-connect2.png)

2. Eles precisam para se certificar de que o **OSTICKETWEB** VM pode se comunicar com o **OSTICKETMYSQL** VM. Atualmente, a configuração está codificada com o endereço IP local 172.16.0.43.

    **Antes da atualização:**

    ![Atualizar IP](./media/contoso-migration-rehost-linux-vm/update-ip1.png)

    **Após a atualização:**

    ![Atualizar IP](./media/contoso-migration-rehost-linux-vm/update-ip2.png)

3. Ela reinicia o serviço com **systemctl restart apache2**.

    ![Reiniciar](./media/contoso-migration-rehost-linux-vm/restart.png)

4. Por fim, eles atualizar os registros DNS para **OSTICKETWEB** e **OSTICKETMYSQL**, em um dos controladores de domínio Contoso.

    ![Atualizar o DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

    ![Atualizar o DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

**Precisa de mais ajuda?**

- [Saiba mais](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) sobre como executar failovers de teste.
- [Saiba mais](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) sobre a migração de VMs para o Azure.

## <a name="clean-up-after-migration"></a>Limpar após a migração

Migração concluída, as camadas de aplicativo osTicket agora estão em execução em VMs do Azure.

Agora, a Contoso precisa fazer uma limpeza, da seguinte maneira:

- Remova as VMs locais do inventário do vCenter.
- Remover as VMs locais de trabalhos de backup locais.
- Atualizar sua documentação interna para mostrar o novo local e endereços IP para OSTICKETWEB e OSTICKETMYSQL.
- Examinar todos os recursos que interagem com as máquinas virtuais e atualizar configurações relevantes ou documentação para refletir a nova configuração.
- Contoso usado o serviço de migração do Azure com o mapeamento de dependência para avaliar as máquinas virtuais para migração. Os administradores devem remover o Microsoft Monitoring Agent e o Microsoft Dependency Agent que eles instalaram para essa finalidade, da VM.

## <a name="review-the-deployment"></a>Revisar a implantação

Com o aplicativo em execução, a Contoso precisa totalmente colocar e proteger sua infraestrutura de novo.

### <a name="security"></a>Segurança

A equipe de segurança da Contoso examine o OSTICKETWEB e OSTICKETMYSQLVMs para determinar os problemas de segurança.

- A equipe revisa os NSGs (grupos de segurança de rede) para que as VMs controlem o acesso. Os NSGs são usados para garantir que somente o tráfego permitido para o aplicativo pode passar.
- A equipe também planeja proteger os dados nos discos da VM usando a criptografia de disco e o Azure Key Vault.

Para obter mais informações, consulte [práticas recomendadas de segurança para cargas de trabalho de IaaS no Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

### <a name="bcdr"></a>BCDR

Para continuidade dos negócios e recuperação de desastres, a Contoso executa as seguintes ações:

- **Manter os dados seguros.** A Contoso faz backup dos dados nas VMs usando o serviço de Backup do Azure. [Saiba mais](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
- **Manter os aplicativos em funcionamento.** A Contoso replica as VMs do aplicativo no Azure para uma região secundária usando o Site Recovery. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart).

### <a name="licensing-and-cost-optimization"></a>Licenciamento e otimização de custo

- Após a implantação de recursos, a Contoso atribui marcas do Azure conforme definido durante a [implantação de infraestrutura do Azure](./contoso-migration-infrastructure.md#set-up-tagging).
- A Contoso não tem nenhum problema de licenciamento com os servidores do Ubuntu.
- A Contoso habilitará o Gerenciamento de Custos do Azure licenciado pela Cloudyn, uma subsidiária da Microsoft. É uma solução de gerenciamento de custos em várias nuvens que ajuda a usar e gerenciar o Azure e outros recursos de nuvem. [Saiba mais](https://docs.microsoft.com/azure/cost-management/overview) sobre o Gerenciamento de Custos do Azure.
