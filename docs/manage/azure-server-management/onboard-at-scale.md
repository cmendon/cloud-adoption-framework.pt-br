---
title: Configurar os serviços de gerenciamento de servidor do Azure para uma assinatura
description: Configurar os serviços de gerenciamento de servidor do Azure para uma assinatura
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: dd3cbd9deda4d0325f014be4bc793b59aa973788
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223382"
---
# <a name="configure-azure-server-management-services-at-scale"></a>Configurar os serviços de gerenciamento de servidor do Azure em escala

Você deve concluir essas duas tarefas para integrar os serviços de gerenciamento do servidor do Azure aos seus servidores:
- Implantar agentes de serviço em seus servidores
- Habilitar as soluções de gerenciamento

Este artigo aborda os três processos necessários para concluir estas tarefas:

1. Implantar os agentes necessários nas VMs do Azure usando Azure Policy
1. Implantar os agentes necessários nos servidores locais
1. Habilitar e configurar as soluções

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de carregar as máquinas virtuais para os serviços de gerenciamento do servidor do Azure.

## <a name="use-azure-policy-to-deploy-extensions-to-azure-vms"></a>Usar Azure Policy para implantar extensões em VMs do Azure

Todas as soluções de gerenciamento que são discutidas em [serviços e ferramentas de gerenciamento do Azure](./tools-services.md) exigem que o agente de log Analytics esteja instalado em máquinas virtuais do Azure e servidores locais. Você pode carregar suas VMs do Azure em escala usando Azure Policy. Atribua a política para garantir que o agente esteja instalado em suas VMs do Azure e conectado ao espaço de trabalho do Log Analytics correto.

O Azure Policy tem uma iniciativa de [diretiva](https://docs.microsoft.com/azure/governance/policy/concepts/definition-structure#initiatives) interna que inclui o agente de log Analytics e o [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-onboard#the-microsoft-dependency-agent), que é exigido pelo Azure monitor para VMs.

<!-- TODO: Add these when available.
- [Preview]: Enable Azure Monitor for virtual machine scale sets.
- [Preview]: Enable Azure Monitor for VMs.
 -->

> [!NOTE]
> Para obter mais informações sobre vários agentes para o monitoramento do Azure, consulte [visão geral dos agentes de monitoramento do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agents-overview).

### <a name="assign-policies"></a>Atribuir políticas

Para atribuir as políticas descritas na seção anterior:

1. Na portal do Azure, acesse **Azure Policy** > **atribuições** > a **iniciativa atribuir**.

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale1.png)

2. Na página **atribuir política** , defina o **escopo** selecionando as reticências (...) e, em seguida, selecionando um grupo de gerenciamento ou uma assinatura. Opcionalmente, selecione um grupo de recursos. Em seguida, escolha **selecionar** na parte inferior da página **escopo** . O escopo determina a quais recursos ou grupo de recursos a política é atribuída.

3. Selecione as reticências ( **...** ) ao lado de **definição de política** para abrir a lista de definições disponíveis. Para filtrar as definições de iniciativa, insira **Azure monitor** na caixa de **pesquisa** :

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale2.png)

4. O **nome da atribuição** é preenchido automaticamente com o nome da política que você selecionou, mas você pode alterá-lo. Você também pode adicionar uma descrição opcional para fornecer mais informações sobre esta atribuição de política. O campo **atribuído por** é preenchido automaticamente com base em quem está conectado. Esse campo é opcional e oferece suporte a valores personalizados.

5. Para essa política, selecione **log Analytics espaço de trabalho** para o agente do log Analytics a ser associado.

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale3.png)

6. Marque a caixa de seleção **local de identidade gerenciada** . Se essa política for do tipo [DeployIfNotExists](https://docs.microsoft.com/azure/governance/policy/concepts/effects#deployifnotexists), uma identidade gerenciada será necessária para implantar a política. No portal, a conta será criada conforme indicado pela seleção da caixa de seleção.

7. Selecione **Atribuir**.

Depois de concluir o assistente, a atribuição de política será implantada no ambiente. Pode levar até 30 minutos para que a política entre em vigor. Para testá-lo, crie novas VMs após 30 minutos e verifique se a Microsoft Monitoring Agent está habilitada na VM por padrão.

## <a name="install-agents-on-on-premises-servers"></a>Instalar agentes em servidores locais

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de integrar os serviços de gerenciamento do servidor do Azure aos servidores.

Para servidores locais, você precisa baixar e instalar o [agente de log Analytics e o agente de dependência da Microsoft](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud) manualmente e configurá-los para se conectar ao espaço de trabalho correto. Você deve especificar a ID do espaço de trabalho e as informações de chave. Para obter essas informações, vá para o espaço de trabalho do Log Analytics na portal do Azure e, em seguida, selecione **configurações** > **Configurações avançadas**.

![Captura de tela das configurações avançadas do espaço de trabalho do Log Analytics no portal do Azure](./media/onboarding-on-premises.png)

## <a name="enable-and-configure-solutions"></a>Habilitar e configurar soluções

Para habilitar soluções, você precisa configurar o workspace do Log Analytics. As VMs do Azure e os servidores locais integrados receberão as soluções dos espaços de trabalho Log Analytics aos quais estão conectados.

### <a name="update-management"></a>Gerenciamento de atualizações

As soluções de Gerenciamento de Atualizações, Controle de Alterações e inventário exigem um espaço de trabalho Log Analytics e uma conta de automação. Para garantir que esses recursos estejam configurados corretamente, recomendamos que você integre sua conta de automação. Para obter mais informações, consulte [integrado gerenciamento de atualizações, controle de alterações e soluções de inventário](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

Recomendamos que você habilite a solução de Gerenciamento de Atualizações para todos os servidores. Gerenciamento de Atualizações é gratuito para VMs do Azure e servidores locais. Se você habilitar Gerenciamento de Atualizações por meio de sua conta de automação, uma [configuração de escopo](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account#scope-configuration) será criada no espaço de trabalho. Atualize manualmente o escopo para incluir computadores cobertos pelo serviço de Gerenciamento de Atualizações.

Para abranger seus servidores existentes, bem como servidores futuros, você precisa remover a configuração de escopo. Para fazer isso, exiba sua conta de automação no portal do Azure. Selecione **Gerenciamento de Atualizações** > **gerenciar computador** > **habilitar em todos os computadores disponíveis e futuros**. Essa configuração permite que todas as VMs do Azure que estão conectadas ao espaço de trabalho usem Gerenciamento de Atualizações.

![Captura de tela de Gerenciamento de Atualizações no portal do Azure](./media/onboarding-configuration1.png)

### <a name="change-tracking-and-inventory-solutions"></a>Soluções de Controle de Alterações e inventário

Para integrar as soluções de Controle de Alterações e inventário, siga as mesmas etapas para Gerenciamento de Atualizações. Para obter mais informações sobre como integrar essas soluções de sua conta de automação, consulte [integração gerenciamento de atualizações, controle de alterações e soluções de inventário](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

A solução Controle de Alterações é gratuita para VMs do Azure e custa $6 por nó por mês para servidores locais. Esse custo cobre Controle de Alterações, inventário e configuração de estado desejado. Se você quiser registrar somente servidores locais específicos, poderá aceitar esses servidores. Recomendamos que você integre todos os seus servidores de produção.

#### <a name="opt-in-via-the-azure-portal"></a>Aceitar por meio do portal do Azure

1. Acesse a conta de automação que tem o Controle de Alterações e o inventário habilitados.
2. Selecione **controle de alterações**.
3. Selecione **gerenciar computadores** no painel superior direito.
4. Selecione **habilitar em computadores selecionados**. Em seguida, selecione **Adicionar** ao lado do nome do computador.
5. Selecione **habilitar** para habilitar a solução para esses computadores.

![Captura de tela de Controle de Alterações no portal do Azure](./media/onboarding-configuration2.png)

#### <a name="opt-in-by-using-saved-searches"></a>Aceitar usando pesquisas salvas

Como alternativa, você pode configurar a configuração de escopo para aceitar servidores locais. A configuração de escopo usa pesquisas salvas.

Para criar ou modificar a pesquisa salva, siga estas etapas:

1. Vá para o espaço de trabalho Log Analytics que está vinculado à conta de automação que você configurou nas etapas anteriores.

1. Em **Geral**, selecione **Pesquisas salvas**.

1. Na caixa **filtro** , digite **controle de alterações** para filtrar a lista de pesquisas salvas. Nos resultados, selecione **MicrosoftDefaultComputerGroup**.

1. Insira o nome do computador ou o VMUUID para incluir os computadores que você deseja aceitar por Controle de Alterações.

    ```kusto
    Heartbeat
    | where AzureEnvironment=~"Azure" or Computer in~ ("list of the on-premises server names", "server1")
    | distinct Computer
    ```

    > [!NOTE]
    > O nome do servidor deve corresponder exatamente ao valor na expressão e não deve conter um sufixo de nome de domínio.

1. Clique em **Salvar**. Por padrão, a configuração de escopo é vinculada à pesquisa salva **MicrosoftDefaultComputerGroup** . Ele será atualizado automaticamente.

### <a name="azure-activity-log"></a>Log de Atividades do Azure

O [log de atividades do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) também faz parte do Azure monitor. Ele fornece informações sobre eventos de nível de assinatura que ocorrem no Azure.

Para implementar essa solução:

1. Na portal do Azure, abra **todos os serviços**e, em seguida, selecione **gerenciamento + governança** > **soluções**.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Procure **análise do log de atividades** e selecione-o.
4. Selecione **Criar**.

Você precisa especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

### <a name="azure-log-analytics-agent-health"></a>Integridade do Agente do Azure Log Analytics

A solução de Integridade do Agente Log Analytics do Azure relata sobre a integridade, o desempenho e a disponibilidade de seus servidores Windows e Linux.

Para implementar essa solução:

1. Na portal do Azure, abra **todos os serviços**e, em seguida, selecione **gerenciamento + governança** > **soluções**.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Pesquise a **integridade do agente de log Analytics do Azure** e selecione-o.
4. Selecione **Criar**.

Você precisa especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

Após a conclusão da criação, a instância de recurso do espaço de trabalho exibe **AgentHealthAssessment** quando você seleciona **Exibir** > **soluções**.

### <a name="antimalware-assessment"></a>Avaliação antimalware

A solução Avaliação de Antimalware ajuda a identificar servidores infectados ou a aumentar o risco de infecção por malware.

Para implementar essa solução:

1. Na portal do Azure, abra **todos os serviços**, selecione **gerenciamento + governança** > **soluções**.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Pesquise e selecione **avaliação de antimalware**.
4. Selecione **Criar**.

Você precisa especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

Após a conclusão da criação, a instância de recurso do espaço de trabalho exibe o **Antimalware** quando você seleciona **exibir** **soluções**de > .

### <a name="azure-monitor-for-vms"></a>Azure Monitor para VMs

Você pode habilitar [Azure monitor para VMs](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) por meio da página de exibição da instância de VM, conforme descrito em [habilitar serviços de gerenciamento em uma única VM para avaliação](./onboard-single-vm.md). Você não deve habilitar soluções diretamente da página de **soluções** da mesma forma que faz para as outras soluções descritas neste artigo. Para implantações em larga escala, pode ser mais fácil usar a [automação](./onboarding-automation.md) para habilitar as soluções corretas no espaço de trabalho. 

### <a name="azure-security-center"></a>Central de Segurança do Azure

É recomendável que você integre todos os servidores pelo menos à camada *gratuita* da central de segurança do Azure. Essa opção fornece um nível básico de avaliações de segurança e recomendações de segurança acionáveis para seu ambiente. Se você atualizar para a camada *Standard* , obterá benefícios adicionais, que são discutidos em detalhes na [página de preços da central de segurança](https://docs.microsoft.com/azure/security-center/security-center-pricing).

Para habilitar a camada gratuita da central de segurança do Azure, siga estas etapas:

1. Vá para a página do portal da **central de segurança** .
2. Em **política &AMP; conformidade**, selecione **política de segurança**.
3. Localize o recurso de espaço de trabalho Log Analytics que você criou no painel no lado direito.
4. Selecione **Editar configurações** para esse espaço de trabalho.
5. Selecione **Tipo de preço**.
6. Escolha a opção **gratuito** .
7. Clique em **Salvar**.

## <a name="next-steps"></a>Próximas etapas

Saiba como usar a automação para carregar servidores e criar alertas.

> [!div class="nextstepaction"]
> [Automatizar a integração e a configuração de alertas](./onboarding-automation.md)
