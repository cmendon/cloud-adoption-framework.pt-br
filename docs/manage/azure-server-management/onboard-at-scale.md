---
title: Configurar os serviços de gerenciamento do Azure para uma assinatura
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurar os serviços de gerenciamento do Azure para uma assinatura
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a5b1d551f52ae8800e9a29d4c8a92c14965645cc
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71221505"
---
# <a name="configure-azure-management-services-at-scale"></a>Configurar os serviços de gerenciamento do Azure em escala

A integração dos serviços de gerenciamento do Azure aos seus servidores envolve duas tarefas: implantar agentes de serviço em seus servidores e habilitar as soluções de gerenciamento. Este artigo aborda os seguintes processos que lhe permitirão concluir estas tarefas:

- [Implantando agentes necessários para VMs do Azure usando Azure Policy](#deploy-extensions-to-azure-vms-using-azure-policy)
- [Implantando agentes necessários em servidores locais](#install-required-agents-on-on-premises-servers)
- [Habilitar e configurar soluções](#enable-and-configure-solutions)

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de integrar máquinas virtuais aos serviços de gerenciamento do Azure.

## <a name="deploy-extensions-to-azure-vms-using-azure-policy"></a>Implantar extensões para VMs do Azure usando Azure Policy

Todas as soluções de gerenciamento discutidas em [serviços e ferramentas de gerenciamento do Azure](./tools-services.md) exigem que o agente de log Analytics seja instalado em VMS (máquinas virtuais) do Azure e em servidores locais. Você pode carregar suas VMs do Azure em escala usando Azure Policy. Atribua a política para garantir que o agente esteja instalado em todas as suas VMs do Azure e conectado ao espaço de trabalho do Log Analytics correto.

O Azure Policy tem uma iniciativa de [diretiva](/azure/governance/policy/index#initiative-definition) interna que inclui o agente de log Analytics e o [Microsoft Dependency Agent](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-onboard#the-microsoft-dependency-agent), que é exigido pelo Azure monitor para VMs.

<!-- TODO: Add these when available.
- [Preview]: Enable Azure Monitor for virtual machine scale sets.
- [Preview]: Enable Azure Monitor for VMs.
 -->

> [!NOTE]
> Para obter mais informações sobre vários agentes para o monitoramento do Azure, consulte [visão geral dos agentes de monitoramento do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/agents-overview).

### <a name="assign-policies"></a>Atribuir políticas

Para atribuir as políticas listadas na seção anterior:

1. Na portal do Azure, vá para **Azure Policy** > **atribuições** > **atribuir iniciativa**.

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale1.png)

2. Na página **atribuir política** , selecione o **escopo** clicando nas reticências (...) e, em seguida, selecione um grupo de gerenciamento ou uma assinatura. Opcionalmente, selecione um grupo de recursos. Um escopo determina a quais recursos ou grupo de recursos a política é atribuída. Em seguida, escolha **selecionar** na parte inferior da página **escopo** .

3. Selecione as reticências (...) ao lado de **definição de política** para abrir a lista de definições disponíveis. Você pode filtrar a definição de iniciativa digitando **Azure monitor** na caixa de **pesquisa** :

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale2.png)

4. O **nome da atribuição** é preenchido automaticamente com o nome da política que você selecionou, mas você pode alterá-lo. Você também pode adicionar uma descrição opcional para fornecer mais informações sobre esta atribuição de política. O campo **atribuído por** é preenchido automaticamente com base em quem está conectado. Esse campo é opcional e os valores personalizados podem ser inseridos.

5. Para essa política, selecione **log Analytics espaço de trabalho** para o agente do log Analytics a ser associado.

    ![Captura de tela da interface de política do portal](./media/onboarding-at-scale3.png)

6. Verifique o **local de identidade gerenciada**. Se essa política for do tipo [DeployIfNotExists](https://docs.microsoft.com/azure/governance/policy/concepts/effects#deployifnotexists), ela exigirá uma identidade gerenciada para implantar a política. No portal, a conta será criada conforme indicado com a seleção da caixa de seleção.

7. Selecione **Atribuir**.

Depois de concluir o assistente, a atribuição de política será implantada no ambiente. Pode levar até 30 minutos para que a política entre em vigor. Você pode testá-lo criando novas VMs após 30 minutos e, em seguida, verificando se a Microsoft Monitoring Agent (MMA) está habilitada na VM por padrão.

## <a name="install-required-agents-on-on-premises-servers"></a>Instalar os agentes necessários nos servidores locais

> [!NOTE]
> Crie o [espaço de trabalho log Analytics necessário e a conta de automação do Azure](./prerequisites.md#create-a-workspace-and-automation-account) antes de integrar os servidores aos serviços de gerenciamento do Azure.

Para servidores locais, você precisará baixar e instalar o [agente de log Analytics e o agente de dependência da Microsoft](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-enable-hybrid-cloud) manualmente e configurá-los para se conectar ao espaço de trabalho correto. Faça isso especificando a ID do espaço de trabalho e as informações de chave, que você pode encontrar acessando seu espaço de trabalho do log Analytics na portal do Azure e selecionando **configurações** > configurações**avançadas**.

![Captura de tela das configurações avançadas do espaço de trabalho do Log Analytics no portal do Azure](./media/onboarding-on-premises.png)

## <a name="enable-and-configure-solutions"></a>Habilitar e configurar soluções

Para habilitar as soluções, você precisa configurar o espaço de trabalho Log Analytics. As VMs do Azure e os servidores locais integrados receberão as soluções dos espaços de trabalho Log Analytics aos quais elas estão conectadas.

As soluções a seguir são abordadas nesta seção:

- [Gerenciamento de atualizações](#update-management)
- [Controle de Alterações e inventário](#change-tracking-and-inventory-solutions)
- [Log de atividades do Azure](#azure-activity-log)
- [Integridade do Agente Log Analytics do Azure](#azure-log-analytics-agent-health)
- [Avaliação antimalware](#antimalware-assessment)
- [Azure Monitor para VMs](#azure-monitor-for-vms)
- [Central de Segurança do Azure](#azure-security-center)

### <a name="update-management"></a>Gerenciamento de Atualizações

As soluções de Gerenciamento de Atualizações, Controle de Alterações e inventário exigem um espaço de trabalho Log Analytics e uma conta de automação. Para garantir que esses recursos estejam configurados corretamente, recomendamos que você integre a conta de automação. Para obter mais informações, consulte [integrado gerenciamento de atualizações, controle de alterações e soluções de inventário](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

É recomendável habilitar a solução de Gerenciamento de Atualizações para todos os servidores. Gerenciamento de Atualizações é gratuito para VMs do Azure e servidores locais. Se você habilitar Gerenciamento de Atualizações por meio de sua conta de automação, uma [configuração de escopo](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account#scope-configuration) será criada no espaço de trabalho. Você precisará atualizar manualmente o escopo para incluir computadores cobertos pelo serviço de atualização.

Para abranger todos os servidores existentes, bem como servidores futuros, você precisa remover a configuração de escopo. Para fazer isso, exiba sua conta de automação na portal do Azure e selecione **Gerenciamento de atualizações** > **gerenciar máquina** > **habilitar em todos os computadores disponíveis e futuros**. Habilitar essa configuração permite que todas as VMs do Azure conectadas ao espaço de trabalho usem Gerenciamento de Atualizações.

![Captura de tela de Gerenciamento de Atualizações no portal do Azure](./media/onboarding-configuration1.png)

### <a name="change-tracking-and-inventory-solutions"></a>Soluções de Controle de Alterações e inventário

Para integrar as soluções de Controle de Alterações e inventário, siga as mesmas etapas para Gerenciamento de Atualizações. Para obter mais informações sobre a integração dessas soluções de sua conta de automação, consulte [integração gerenciamento de atualizações, controle de alterações e soluções de inventário](https://docs.microsoft.com/azure/automation/automation-onboard-solutions-from-automation-account).

A solução Controle de Alterações é gratuita para VMs do Azure e custa $6 por nó por mês para servidores locais. Esse custo cobre Controle de Alterações, inventário e configuração de estado desejado. Se você quiser registrar apenas servidores locais específicos, poderá optar por esses servidores. Recomendamos que você integre todos os seus servidores de produção.

#### <a name="opt-in-via-the-azure-portal"></a>Aceitar por meio do portal do Azure

1. Acesse a conta de automação que tem o Controle de Alterações e o inventário habilitados.
2. Selecione **controle de alterações**.
3. Selecione **gerenciar computadores** no painel superior direito.
4. Selecione **habilitar em computadores selecionados**e selecione os computadores a serem habilitados clicando em **Adicionar** ao lado do nome do computador.
5. Selecione **habilitar** para habilitar a solução para esses computadores.

![Captura de tela de Controle de Alterações no portal do Azure](./media/onboarding-configuration2.png)

#### <a name="opt-in-by-using-saved-searches"></a>Aceitar usando pesquisas salvas

Como alternativa, você pode configurar a configuração de escopo para aceitar servidores locais. A configuração de escopo usa pesquisas salvas.

Para criar ou modificar a pesquisa salva, use as seguintes etapas:

1. Vá para o espaço de trabalho Log Analytics que está vinculado à sua conta de automação que você configurou nas etapas anteriores.

2. Em **Geral**, selecione **Pesquisas salvas**.

3. Na caixa **filtro** , digite **controle de alterações** para filtrar a lista de pesquisas salvas. Nos resultados, selecione **MicrosoftDefaultComputerGroup**.

4. Insira o nome do computador ou o VMUUID para incluir os computadores que você deseja aceitar por Controle de Alterações.

    ```kusto
    Heartbeat
    | where AzureEnvironment=~"Azure" or Computer in~ ("list of the on-premises server names", "server1")
    | distinct Computer
    ```

    > [!NOTE]
    > O nome do servidor deve corresponder exatamente ao valor incluído na expressão e não deve conter um sufixo de nome de domínio.

5. Clique em **Salvar**.

6. Por padrão, a configuração de escopo é vinculada à pesquisa salva **MicrosoftDefaultComputerGroup** e será atualizada automaticamente.

### <a name="azure-activity-log"></a>Log de Atividades do Azure

O [log de atividades do Azure](https://docs.microsoft.com/azure/azure-monitor/platform/activity-logs-overview) também faz parte do Azure monitor. Ele fornece informações sobre eventos de nível de assinatura que ocorrem no Azure.

Para adicionar esta solução:

1. No portal do Azure, abra **todos os serviços** e selecione **Gerenciamento +**  > **soluções**de governança.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Procure **análise do log de atividades** e selecione-o.
4. Selecione **Criar**.

Você precisará especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

### <a name="azure-log-analytics-agent-health"></a>Integridade do Agente do Azure Log Analytics

A solução de Integridade do Agente Log Analytics do Azure fornece informações sobre a integridade, o desempenho e a disponibilidade de seus servidores Windows e Linux.

Para adicionar esta solução:

1. No portal do Azure, abra **todos os serviços** e selecione **Gerenciamento +**  > **soluções**de governança.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Pesquise a **integridade do agente de log Analytics do Azure** e selecione-o.
4. Selecione **Criar**.

Você precisará especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

Após a conclusão da criação, a instância de recurso do espaço de trabalho exibe **AgentHealthAssessment** quando você seleciona **Exibir** > **soluções**.

### <a name="antimalware-assessment"></a>Avaliação Antimalware

A solução Avaliação de Antimalware ajuda a identificar servidores infectados ou a aumentar o risco de infecção por malware.

Para adicionar esta solução:

1. No portal do Azure, abra **todos os serviços** e selecione **Gerenciamento +**  > **soluções**de governança.
2. No modo de exibição **soluções** , selecione **Adicionar**.
3. Procure **avaliação de antimalware** e selecione-o.
4. Selecione **Criar**.

Você precisará especificar o **nome do espaço** de trabalho do espaço de trabalho que você criou na seção anterior em que a solução está habilitada.

Após a conclusão da criação, a instância de recurso do espaço de trabalho exibe o antimalware quando você seleciona **Exibir** > **soluções**.

### <a name="azure-monitor-for-vms"></a>Azure Monitor para VMs

Você pode habilitar [Azure monitor para VMs](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-overview) por meio da página de exibição da instância de VM, conforme descrito no artigo anterior, [habilitar serviços de gerenciamento em uma única VM para avaliação](./onboard-single-vm.md). Você não deve habilitar soluções diretamente da página **soluções** , como fez para as outras soluções descritas neste artigo. Para implantações em larga escala, pode ser mais fácil usar a [automação](./onboarding-automation.md) para habilitar as soluções corretas no espaço de trabalho.

### <a name="azure-security-center"></a>Central de Segurança do Azure

Nestas diretrizes, recomendamos que você integre todos os servidores à camada *gratuita* da central de segurança do Azure por padrão. Essa opção oferece um nível básico de avaliações de segurança e recomendações de segurança acionáveis para seu ambiente. A atualização para a camada *Standard* da central de segurança oferece benefícios adicionais, que são discutidos em detalhes na [página de preços da central de segurança](https://docs.microsoft.com/azure/security-center/security-center-pricing).

Para habilitar a camada gratuita da central de segurança do Azure, use as seguintes etapas:

1. Vá para a página do portal da **central de segurança** .
2. Selecione **política de segurança** em **política & conformidade**.
3. Localize o recurso de espaço de trabalho Log Analytics que você criou no painel mais à direita.
4. Selecione **Editar configurações >** para esse espaço de trabalho.
5. Selecione **Tipo de preço**.
6. Escolha a opção **gratuito** .
7. Clique em **Salvar**.

## <a name="next-steps"></a>Próximas etapas

Saiba como usar a automação para carregar servidores e criar alertas.

> [!div class="nextstepaction"]
> [Automatizar a integração e a configuração de alertas](./onboarding-automation.md)
