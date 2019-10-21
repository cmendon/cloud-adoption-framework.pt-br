---
title: 'Guia de governança empresarial padrão: aprimoramento de multinuvem'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança empresarial padrão: aprimoramento de multinuvem'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 78ffb3b3d91f1f00fb92d70147fd7177ffa9f1b0
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547510"
---
# <a name="standard-enterprise-governance-guide-multicloud-improvement"></a>Guia de governança empresarial padrão: aprimoramento de multinuvem

Este artigo avança na narração adicionando controles para a adoção de nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A Microsoft reconhece que os clientes podem adotar várias nuvens para fins específicos. O cliente fictício neste guia não é exceção. Em paralelo com a jornada de adoção do Azure, o sucesso dos negócios levou à aquisição de um negócio pequeno, mas complementar. Essa empresa está executando todas as suas operações de ti em um provedor de nuvem diferente.

Este artigo descreve como as coisas mudam ao integrar a nova organização. Para fins da narração, supomos que essa empresa concluiu cada uma das iterações de governança descritas neste guia de governança.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narração, a empresa começou a enviar ativamente aplicativos de produção para a nuvem por meio de pipelines de CI/CD.

Desde então, algumas coisas mudaram que afetarão a governança:

- A identidade é controlada por uma instância local do Active Directory. A identidade híbrida é facilitada por meio da replicação para Azure Active Directory.
- Operações de ti ou operações de nuvem são amplamente gerenciadas por Azure Monitor e automaçãos relacionadas.
- A recuperação de desastres/continuidade dos negócios é controlada pelas instâncias do cofre do Azure.
- A central de segurança do Azure é usada para monitorar violações e ataques de segurança.
- A central de segurança do Azure e os Azure Monitor são usados para monitorar a governança da nuvem.
- Os planos gráficos do Azure, Azure Policy e grupos de gerenciamento do Azure são usados para automatizar a conformidade com a política.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

O objetivo é integrar a empresa de aquisição em operações existentes sempre que possível.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Custo de aquisição de negócios:** A aquisição da nova empresa é estimada para ser lucrativa em aproximadamente cinco anos. Devido à taxa de retorno lenta, o quadro deseja controlar os custos de aquisição, tanto quanto possível. Há um risco de controle de custo e de integração técnica entre si.

Esse risco comercial pode ser expandido em alguns riscos técnicos:

- A migração na nuvem pode produzir custos de aquisição adicionais.
- O novo ambiente pode não ser controlado adequadamente, o que pode resultar em violações de política.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As seguintes alterações na política ajudarão a corrigir os novos riscos e a implementação do guia:

- Todos os ativos em uma nuvem secundária devem ser monitorados por meio de ferramentas de monitoramento de segurança e de gerenciamento operacional existentes.
- Todas as unidades organizacionais devem ser integradas ao provedor de identidade existente.
- O provedor de identidade principal deve governar a autenticação para ativos na nuvem secundária.

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas alterações de design atenderão às novas instruções de política corporativa.

1. Conecte as redes. Esta etapa é executada pelas equipes de segurança de rede e de ti e com suporte da equipe de governança de nuvem. A adição de uma conexão do provedor MPLS/de linha dedicada para a nova nuvem integrará redes. Adicionar tabelas de roteamento e configurações de firewall controlará o acesso e o tráfego entre os ambientes.
2. Consolide provedores de identidade. Dependendo das cargas de trabalho que estão sendo hospedadas na nuvem secundária, há uma variedade de opções para a consolidação do provedor de identidade. Veja a seguir alguns exemplos:
    1. Para aplicativos que se autenticam usando o OAuth 2, os usuários de Active Directory na nuvem secundária podem simplesmente ser replicados para o locatário existente do Azure AD. Isso garante que todos os usuários possam ser autenticados no locatário.
    2. No outro extremo, a Federação permite que as UOs fluam para Active Directory locais e, em seguida, para a instância do Azure AD.
3. Adicionar ativos a Azure Site Recovery.
    1. Azure Site Recovery foi projetado desde o início como uma ferramenta híbrida ou de nuvem.
    2. As VMs na nuvem secundária podem ser protegidas pelo mesmo Azure Site Recovery processos usados para proteger ativos locais.
4. Adicione ativos ao gerenciamento de custos do Azure.
    1. O gerenciamento de custos do Azure foi projetado desde o início como uma ferramenta de nuvem.
    2. As máquinas virtuais na nuvem secundária podem ser compatíveis com o gerenciamento de custos do Azure para alguns provedores de nuvem. Podem ser aplicados custos adicionais.
5. Adicionar ativos a Azure Monitor.
    1. A Azure Monitor foi projetada como uma ferramenta de nuvem híbrida desde o início.
    2. As máquinas virtuais na nuvem secundária podem ser compatíveis com agentes de Azure Monitor, permitindo que eles sejam incluídos em Azure Monitor para monitoramento operacional.
6. Adote as ferramentas de imposição de governança.
    1. A imposição de governança é específica da nuvem.
    2. As políticas corporativas estabelecidas no guia de governança não são específicas da nuvem. Embora a implementação possa variar de nuvem para nuvem, as políticas podem ser aplicadas ao provedor secundário.

A adoção de multinuvem deve estar contida em onde é necessário com base em necessidades técnicas ou em requisitos de negócios específicos. À medida que a adoção de nuvem cresce, isso aumenta a complexidade e os riscos de segurança.

## <a name="conclusion"></a>Conclusão

Esta série de artigos descreveu o desenvolvimento incremental de práticas recomendadas de governança, alinhado com as experiências desta empresa fictícia. Iniciando o pequeno, mas com a base certa, a empresa pode se mover rapidamente e, ainda assim, aplicar a quantidade certa de governança no momento certo. O MVP por si só não protegeu o cliente. Em vez disso, ele criou a base para gerenciar riscos e adicionar proteções. A partir daí, as camadas de governança foram aplicadas para corrigir os riscos tangíveis. A jornada exata apresentada aqui não alinhará 100% com as experiências de qualquer leitor. Em vez disso, ele serve como um padrão para governança incremental. O leitor é aconselhado a moldar essas práticas recomendadas para ajustar suas próprias restrições exclusivas e requisitos de governança.
