---
title: Planejamento de pré-requisitos para os serviços de gerenciamento de servidor do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ferramentas de pré-requisito e planejamento para os serviços de gerenciamento de servidor do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ac4ece6c5daec788d116e67c79429572722fc618
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548233"
---
# <a name="phase-1-prerequisite-planning-for-azure-server-management-services"></a>Fase 1: planejamento de pré-requisitos para os serviços de gerenciamento de servidor do Azure

Nesta fase, você se familiarizará com o conjunto de serviços do Azure Server Management e planejará como implantar os recursos necessários para implementar essas soluções de gerenciamento.

## <a name="understand-the-tools-and-services"></a>Entenda as ferramentas e os serviços

Examine as [ferramentas e os serviços de gerenciamento do servidor do Azure](./tools-services.md) para obter uma visão geral detalhada das áreas de gerenciamento envolvidas nas operações contínuas do Azure e nos serviços e ferramentas do Azure que ajudam a dar suporte a você nessas áreas. Atender aos seus requisitos de gerenciamento envolverá o uso de vários desses serviços juntos. Essas ferramentas são referenciadas com frequência em todas as diretrizes.

As seções a seguir discutem o planejamento e a preparação necessários para usar essas ferramentas e serviços.

## <a name="log-analytics-workspace-and-automation-account-planning"></a>Planejamento de Log Analytics de trabalho e de conta de automação

Muitos dos serviços que você usará para carregar os serviços de gerenciamento do Azure exigem um espaço de trabalho Log Analytics e uma conta de automação do Azure vinculada.

Um [espaço de trabalho log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) é um ambiente exclusivo para armazenar Azure monitor dados de log. Cada espaço de trabalho tem seu próprio repositório de dados e configuração. As fontes de dados e as soluções são configuradas para armazenar seus dados em espaços de trabalho específicos. As soluções de monitoramento do Azure exigem que todos os servidores estejam conectados a um espaço de trabalho, para que os dados de log possam ser armazenados e acessados.

Alguns dos serviços de gerenciamento exigem uma conta de [automação do Azure](https://docs.microsoft.com/azure/automation/automation-intro) . Usando essa conta e os recursos da automação do Azure, você pode integrar os serviços do Azure e outros sistemas públicos para implantar, configurar e gerenciar seus processos de gerenciamento de servidor.

Os seguintes serviços de gerenciamento do servidor do Azure exigem um espaço de trabalho Log Analytics vinculado e uma conta de automação para funcionar:

- [Gerenciamento de Atualizações do Azure](https://docs.microsoft.com/azure/automation/automation-update-management)
- [Controle de Alterações e inventário](https://docs.microsoft.com/azure/automation/change-tracking)
- [Runbook Worker Híbrido](https://docs.microsoft.com/azure/automation/automation-hybrid-runbook-worker)
- [Configuração de estado desejado](https://docs.microsoft.com/azure/virtual-machines/extensions/dsc-overview)

A segunda fase desta orientação concentra-se na implantação de serviços e scripts de automação. Ele mostra como criar um Log Analytics espaço de trabalho e uma conta de automação. Esta orientação também mostra como usar Azure Policy para garantir que novas VMs estejam conectadas ao espaço de trabalho correto.

Os exemplos abordados nesta diretriz pressupõem uma implantação que ainda não tem servidores implantados na nuvem. Para saber mais sobre os princípios e considerações envolvidos no planejamento de seus espaços de trabalho, consulte [gerenciar dados de log e espaços de trabalho no Azure monitor](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).

## <a name="planning-considerations"></a>Considerações sobre planejamento

Ao preparar os espaços de trabalho e as contas que você cria para serviços de gerenciamento de integração, consulte as seguintes discussões sobre problemas:

- **Geografia do Azure e conformidade regulatória**. As regiões do Azure são organizadas em *geografias*. Uma [Geografia do Azure](https://azure.microsoft.com/global-infrastructure/geographies) garante que os requisitos de residência de dados, soberania, conformidade e resiliência sejam respeitados dentro dos limites geográficos. Se suas cargas de trabalho estiverem sujeitas à soberania de dados ou outros requisitos de conformidade, as contas de espaço de trabalho e de automação deverão ser implantadas em regiões na mesma Geografia do Azure que os recursos de carga que eles dão suporte.
- **Número de espaços de trabalho**. Como princípio de orientação, crie o número mínimo de espaços de trabalho necessários por geografia do Azure. É recomendável pelo menos um espaço de trabalho para cada Geografia do Azure onde os recursos de computação ou armazenamento estão localizados. Esse alinhamento inicial ajuda a evitar problemas regulatórios futuros ao migrar dados para geografias diferentes.
- **Retenção de dados e limitação**. Talvez você também precise tomar as políticas de retenção de dados ou os requisitos de data capping em consideração ao criar espaços de trabalho ou contas de automação. Para obter mais informações sobre esses princípios e considerações adicionais ao planejar seus espaços de trabalho, consulte [gerenciar dados de log e espaços de trabalho no Azure monitor](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access).
- **Mapeamento de região**. Só há suporte para a vinculação de um espaço de trabalho Log Analytics e uma conta de automação do Azure entre determinadas regiões do Azure. Por exemplo, se o espaço de trabalho Log Analytics estiver hospedado na região *lesteus* , a conta de automação vinculada deverá ser criada na região *EastUS2* para ser usada com os serviços de gerenciamento. Se você tiver uma conta de automação que foi criada em outra região, ela não será capaz de vincular a um espaço de trabalho no *lesteus*. A escolha da região de implantação pode afetar significativamente os requisitos de Geografia do Azure. Consulte a [tabela de mapeamento de região](https://docs.microsoft.com/azure/automation/how-to/region-mappings) para decidir qual região deve hospedar seus espaços de trabalho e contas de automação.
- **Hospedagem múltipla do espaço de trabalho**. O Log Analytics Agent dá suporte a hospedagem múltipla em alguns cenários, mas o agente enfrenta várias limitações e problemas ao executar nessa configuração. A menos que a Microsoft tenha recomendado usar a hospedagem múltipla para seu cenário, não recomendamos configurar a hospedagem múltipla no agente de Log Analytics.

## <a name="resource-placement-examples"></a>Exemplos de posicionamento de recursos

Há vários modelos diferentes para escolher a assinatura na qual você coloca o espaço de trabalho Log Analytics e a conta de automação. Em suma, você deve posicionar as contas de espaço de trabalho e automação em uma assinatura de propriedade da equipe responsável pela implementação dos serviços de Gerenciamento de Atualizações e Controle de Alterações e de inventário.

Os exemplos a seguir ilustram algumas maneiras que os espaços de trabalho e as contas de automação podem ser implantados.

### <a name="placement-by-geography"></a>Posicionamento por geografia

Para ambientes pequenos e médios com uma única assinatura e centenas de recursos que abrangem várias regiões geográficas do Azure, crie um Log Analytics espaço de trabalho e uma conta de automação do Azure em cada geografia.

Você pode criar um espaço de trabalho e uma conta de automação do Azure — um par — em cada grupo de recursos e implantar o par na geografia correspondente às máquinas virtuais. Como alternativa, se suas políticas de conformidade de dados não ditarem que os recursos residem em regiões específicas, você poderá criar um par para gerenciar todas as máquinas virtuais. Também recomendamos que você coloque o espaço de trabalho e os pares de conta de automação em grupos de recursos separados para fornecer RBAC (controle de acesso baseado em função) mais granular.

O exemplo no diagrama a seguir tem uma assinatura com dois grupos de recursos, cada um localizado em uma geografia diferente.

![Modelo de espaço de trabalho para ambientes de pequeno a médio porte](./media/workspace-model-small.png)

### <a name="placement-in-a-management-subscription"></a>Posicionamento em uma assinatura de gerenciamento

Para ambientes maiores que abrangem várias assinaturas e têm um departamento de ti central que possui monitoramento e conformidade, crie pares de espaços de trabalho e contas de automação em uma assinatura de gerenciamento de ti. Nesse modelo, os recursos de máquina virtual em uma geografia armazenam seus dados no espaço de trabalho geografia correspondente na assinatura de gerenciamento de ti. As equipes de aplicativos que precisam executar tarefas de automação, mas que não precisam de contas de automação e espaço de trabalho vinculadas, podem criar contas de automação separadas em suas próprias assinaturas de aplicativo.

![Modelo de espaço de trabalho para ambientes grandes](./media/workspace-model-large.png)

### <a name="decentralized-placement"></a>Posicionamento descentralizado

Em um modelo alternativo para ambientes grandes, a responsabilidade pela aplicação de patches e gerenciamento pode estar na equipe de desenvolvimento de aplicativos. Nesse caso, você deve posicionar os pares de contas de espaço de trabalho e de automação nas assinaturas da equipe de aplicativo junto com seus outros recursos.

  ![Modelo de conta de espaço de trabalho para ambientes descentralizados](./media/workspace-model-decentralized.png)

## <a name="create-a-workspace-and-automation-account"></a>Criar um espaço de trabalho e uma conta de automação

Depois de decidir a melhor maneira de colocar e organizar os pares de espaço de trabalho e de conta, você precisará garantir que criou esses recursos antes de iniciar o processo de integração. Os exemplos de automação incluídos posteriormente nesta diretriz criam um par de espaço de trabalho e de conta de automação para você. No entanto, se você não tiver um par de conta de automação e espaço de trabalho existente, será necessário criar um se desejar carregar usando o Portal.

Para criar um Log Analytics espaço de trabalho por meio do portal do Azure, consulte [criar um espaço de trabalho](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace#create-a-workspace). Em seguida, crie uma conta de automação de correspondência para cada espaço de trabalho seguindo as etapas em [criar uma conta de automação do Azure](https://docs.microsoft.com/azure/automation/automation-quickstart-create-account).

> [!NOTE]
> Ao criar uma conta de automação por meio do portal do Azure, o comportamento padrão tenta criar contas Executar como para os recursos de Azure Resource Manager e modelo de implantação clássico. Se você não tiver VMs clássicas em seu ambiente e não for o coadministrador na assinatura, o portal criará uma conta Executar como para o Gerenciador de recursos, mas irá gerar um erro ao implantar a conta Executar como clássica. Se você não pretende dar suporte a recursos clássicos, pode ignorar esse erro.
>
> Você também pode criar contas Executar como usando o [PowerShell](https://docs.microsoft.com/azure/automation/manage-runas-account#create-run-as-account-using-powershell).

## <a name="next-steps"></a>Próximos passos

Saiba como integrar [seus servidores](./onboarding-overview.md) aos serviços de gerenciamento do Azure.

> [!div class="nextstepaction"]
> [Integração com os serviços de gerenciamento do servidor do Azure](./onboarding-overview.md)
