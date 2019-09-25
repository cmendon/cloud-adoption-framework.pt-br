---
title: 'Guia empresarial Standard: Melhoria em nuvem'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia empresarial Standard: Melhoria em nuvem'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2616193b01b252a74ad17a241d97bfd0ebc4860c
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223791"
---
# <a name="small-to-medium-enterprise-guide-multicloud-improvement"></a>Guia empresarial de pequeno a médio porte: Melhoria em nuvem

Este artigo avança na narração adicionando controles para a adoção de nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A Microsoft reconhece que os clientes podem adotar várias nuvens para fins específicos. O cliente fictício neste guia não é exceção. Em paralelo com a jornada de adoção do Azure, o sucesso dos negócios levou à aquisição de um negócio pequeno, mas complementar. Essa empresa está executando todas as suas operações de TI em um provedor de nuvem diferente.

Este artigo descreve as mudanças decorrentes da integração com a nova organização. Para fins da narração, supomos que essa empresa concluiu cada uma das iterações de governança descritas neste guia de governança.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior dessa narrativa, a empresa começou a enviar ativamente os aplicativos de produção para a nuvem por meio de pipelines de CI/CD.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- A identidade é controlada por uma instância local do Active Directory Domain Services. A identidade híbrida é facilitada por meio da replicação para o Azure Active Directory.
- Operações de TI ou operações na nuvem em grande parte são gerenciadas pelo Azure Monitor e relacionados automações.
- A Recuperação de Desastres/Continuidade dos Negócios é controlada pelas instâncias do Azure Vault.
- A Central de Segurança do Azure é utilizada para monitorar violações de segurança e ataques.
- A Central de Segurança do Azure e o Azure Monitor são usados para monitorar a governança de nuvem.
- O Azure Blueprints, Azure Policy e os grupos de gerenciamento do Azure são usados para automatizar a conformidade com a política.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

A meta é integrar a empresa de aquisição nas operações existentes, sempre que possível.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Custo de aquisição de negócios:** A aquisição da nova empresa é estimada para ser lucrativa em aproximadamente cinco anos. Devido à taxa de retorno lenta, o conselho quer controlar os custos de aquisição o máximo possível. Há um risco de controle de custos e integração técnica conflitantes entre si.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

- A migração na nuvem pode produzir custos de aquisição adicionais.
- O novo ambiente pode não ser controlado adequadamente, o que pode resultar em violações de política.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As seguintes alterações na política ajudarão a corrigir os novos riscos e a implementação do guia:

- Todos os ativos em uma nuvem secundária devem ser monitorados por meio do gerenciamento operacional e das ferramentas de monitoramento de segurança existentes.
- Todas as unidades organizacionais devem ser integradas ao provedor de identidade existente.
- O provedor de identidade primário deve reger a autenticação para ativos na nuvem secundária.

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas alterações de design atenderão às novas instruções de política corporativa.

1. Conectar as redes. Esta etapa é executada pelas equipes de segurança de rede e de ti e com suporte da equipe de governança de nuvem. Adicionar uma conexão do provedor de MPLS/baseado em linha à nova nuvem irá integrar as redes. Adicionar tabelas de roteamento e configurações de firewall irá controlar o acesso e o tráfego entre os ambientes.
2. Consolidar provedores de identidade. Dependendo das cargas de trabalho que estão sendo hospedadas na nuvem secundária, há uma variedade de opções para a consolidação do provedor de identidade. Seguem alguns exemplos:
    1. Para aplicativos que se autenticam usando o OAuth 2, os usuários do Active Directory na nuvem secundária simplesmente podem ser replicados para o locatário existente do Active Directory Domain Services. Isso garante que todos os usuários podem ser autenticados no locatário.
    2. Por outro lado, a federação permite UOs fluam para o Active Directory local, em seguida, para a instância do Active Directory Domain Services.
3. Adicionar ativos ao Azure Site Recovery.
    1. Azure Site Recovery foi projetado desde o início como uma ferramenta híbrida ou de nuvem.
    2. As VMs na nuvem secundária poderão ser protegidas pelos mesmos processos do Azure Site Recovery usados para proteger ativos locais.
4. Adicione ativos ao gerenciamento de custos do Azure.
    1. O gerenciamento de custos do Azure foi projetado desde o início como uma ferramenta de nuvem.
    2. Máquinas virtuais na nuvem secundária podem ser compatíveis com o Gerenciamento de Custos do Azure para alguns provedores de nuvem. Custos adicionais podem ser aplicados.
5. Adicione ativos para o Azure Monitor.
    1. O Azure Monitor foi projetado como uma ferramenta de nuvem híbrida desde o início.
    2. Máquinas virtuais na nuvem secundária podem ser compatíveis com os agentes do Azure Monitor, permitindo que sejam incluídos no Azure Monitor para monitoramento operacional.
6. Adote as ferramentas de imposição de governança.
    1. A imposição de governança é específica da nuvem.
    2. As políticas corporativas estabelecidas no guia de governança não são específicas da nuvem. Embora a implementação possa variar da nuvem para nuvem, as políticas podem ser aplicadas ao provedor secundário.

A adoção de várias nuvens deve estar contida em onde é necessário com base em necessidades técnicas ou em requisitos de negócios específicos. À medida que a adoção de várias nuvens cresce, isso aumenta a complexidade e os riscos de segurança.

## <a name="conclusion"></a>Conclusão

Esta série de artigos descreveu o desenvolvimento incremental de práticas recomendadas de governança, alinhado com as experiências desta empresa fictícia. Iniciando pequena, mas com a base certa, a empresa pode se mover rapidamente e ainda assim se aplica a quantidade certa de governança no momento certo. O MVP por si só não protege o cliente. Em vez disso, ele criou a base para gerenciar riscos e adicionar proteções. A partir daí, as camadas de governança foram aplicadas para corrigir os riscos tangíveis. O percurso exato apresentado aqui não se alinha 100% com as experiências de qualquer leitor. Em vez disso, serve como um padrão de governança incremental. O leitor é aconselhado a fim de adaptar essas práticas recomendadas de acordo com suas próprias restrições exclusivas e requisitos de governança.
