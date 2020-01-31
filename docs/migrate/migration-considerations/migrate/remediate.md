---
title: Corrigir ativos antes da migração
description: Corrigir ativos incompatíveis antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 23045cf48dd26400bbad07bbde927e29c3189f8d
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802099"
---
# <a name="remediate-assets-prior-to-migration"></a>Corrigir ativos antes da migração

Durante o processo de avaliação da migração, a equipe busca identificar as configurações que tornaram um ativo incompatível com o provedor de nuvem escolhido. *Corrigir* é um ponto de verificação no processo de migração que visa garantir que essas incompatibilidades foram resolvidas. Este artigo discute algumas tarefas de correção comuns como referência. Também estabelece um processo de esqueleto para decidir se a correção é um investimento inteligente.

## <a name="common-remediation-tasks"></a>Tarefas de correção comuns

Em qualquer ambiente corporativo, a dívida técnica existe. Algumas são saudáveis e esperadas. As decisões de arquitetura que foram bem adequadas para um ambiente local podem não ser totalmente adequadas para uma plataforma de nuvem. Em ambos os casos, as tarefas de correção comuns podem ser necessárias para preparar os ativos para a migração. A seguir, estão alguns exemplos:

- **Atualizações secundárias do host.** Às vezes é necessário atualizar um host antigo antes da replicação.
- **Atualizações secundárias do sistema operacional convidado.** É bem provável que um sistema operacional precise da aplicação de um patch ou atualização antes da replicação.
- **Modificações de SLA.** O backup e a recuperação mudam significativamente em uma plataforma de nuvem. É provável que os ativos precisem de pequenas modificações em seus processos de backup para garantir a continuação das funções na nuvem.
- **Migração PaaS.** Em alguns casos, pode haver a necessidade de uma implantação de PaaS em uma estrutura de dados ou aplicativo a fim de acelerar a implantação. Modificações secundárias podem ser necessárias para preparar a solução para a implantação de PaaS.
- **Alterações de códigos de PaaS.** Não é incomum que aplicativos personalizados exijam modificações secundárias de códigos para que a PaaS esteja pronta. Os exemplos podem incluir métodos que gravam no disco local ou usam estado de sessão na memória, entre outros.
- **Alterações de configurações de aplicativos.** Os aplicativos migrados podem exigir alterações em variáveis, como caminhos de rede para ativos dependentes, alterações de contas de serviço ou atualizações de endereços IP dependentes.
- **Alterações secundárias em caminhos de rede.** Pode ser necessário modificar os padrões de roteamento para rotear corretamente o tráfego do usuário para os novos ativos.
    > [!NOTE]
    > Isso não é o roteamento de produção para os novos ativos, mas sim a configuração para permitir o roteamento adequado para os ativos em geral.

## <a name="large-scale-remediation-tasks"></a>Tarefas de correção em grande escala

Quando um datacenter é mantido, corrigido e atualizado corretamente, é provável que haja pouca necessidade de correção. Os ambientes com correção avançadas tendem a ser comuns entre grandes empresas, organizações que passaram por grandes downsizing de TI, alguns ambientes com serviços gerenciados herdados e ambientes de aquisição avançada. Em cada um desses tipos de ambientes, a correção pode consumir uma grande parte do esforço de migração. Quando as seguintes tarefas de correção são exibidas com frequência e afetam negativamente a velocidade ou a consistência da migração, pode ser recomendável dividir a correção em um esforço com equipes paralelas (semelhante a como a adoção de nuvem e a governança de nuvem são executadas em paralelo).

- **Atualizações frequentes do host.** Quando é necessário atualizar um grande número de hosts para concluir a migração de uma carga de trabalho, a equipe de migração provavelmente sofrerá atrasos. Pode ser conveniente interromper os aplicativos afetados e resolver as correções antes de incluir os aplicativos afetados em quaisquer lançamentos planejados.
- **Atualização frequente do sistema operacional convidado.** Grandes empresas normalmente têm servidores em execução com versões desatualizadas do Linux ou Windows. Além dos riscos de segurança aparentes de operar um sistema operacional desatualizado, também há problemas de incompatibilidade que impedem a migração das cargas de trabalho afetadas. Quando um grande número de VMs exige correções do sistema operacional, pode ser conveniente dividir esses esforços em uma iteração paralela.
- **Grandes alterações de código.** Aplicativos personalizados mais antigos podem exigir modificações significativamente maiores para prepará-los para a implantação de PaaS. Quando esse for o caso, pode ser recomendável removê-los totalmente da pendência de migração para gerenciá-los em um programa totalmente separado.

## <a name="decision-framework"></a>Estrutura de decisão

Embora a correção de cargas de trabalho menores possa ser simples, esse é um dos motivos pelos quais é recomendável escolher cargas de trabalho menores para a migração inicial. No entanto, à medida que seus esforços de migração amadurecem e você começa a lidar com cargas de trabalho maiores, a correção pode ser um processo demorado e dispendioso. Por exemplo, os esforços de correção para uma migração do Windows Server 2003 envolvendo um pool de mais de 5.000 VMs podem atrasar uma migração por meses. Quando essa correção em grande escala é necessária, as perguntas a seguir podem ajudar a orientar as decisões:

- Todas as cargas de trabalho afetadas pela correção foram identificadas e relacionadas na lista de pendências da migração?
- Nas cargas de trabalho que não são afetadas, uma migração produzirá um ROI (retorno de investimento) semelhante?
- Os ativos afetados podem ser corrigidos em alinhamento com a linha do tempo original da migração? Qual o impacto da linha do tempo sobre o ROI?
- É economicamente viável corrigir os ativos em paralelo com os esforços de migração?
- Há largura de banda suficiente na equipe para a correção e a migração? É necessário incluir um parceiro para executar uma ou ambas as tarefas?

Se essas perguntas não produzirem respostas favoráveis, pode valer a pena considerar algumas abordagens alternativas que vão além de uma estratégia básica ao efetuar uma nova hospedagem de IaaS:

- **Utilização de contêineres.** Alguns ativos podem ser hospedados em um ambiente em contêineres sem correção, o que pode produzir um desempenho menos favorável e não soluciona problemas de segurança ou de conformidade.
- **Automação.** Dependendo dos requisitos das cargas de trabalho e de correção, pode ser mais lucrativo gerar o script da implantação para novos ativos usando uma abordagem de DevOps.
- **Recompilação.** Quando os custos de correção são muito altos e o valor comercial é igualmente alto, uma carga de trabalho pode ser uma boa candidata para a recompilação ou a uma nova arquitetura.

## <a name="next-steps"></a>Próximos passos

Depois de concluir a correção, as [atividades de replicação](./replicate.md) estarão prontas.

> [!div class="nextstepaction"]
> [Replicar ativos](./replicate.md)
