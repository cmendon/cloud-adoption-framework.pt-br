---
title: 'Guia de governança para empresas complexas: Melhoria em nuvem'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia empresarial grande: Melhoria em nuvem'
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6f015fcc7a0cb4000502d90ff971341fd6d26ca5
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908638"
---
# <a name="large-enterprise-guide-multicloud-improvement"></a>Guia empresarial grande: Melhoria em nuvem

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A Microsoft reconhece que os clientes estão adotando várias nuvens para fins específicos. A empresa fictícia neste guia não é exceção. Paralelamente ao percurso de adoção do Azure, o sucesso da empresa resultou na aquisição de uma empresa de pequeno porte, mas complementar. Essa empresa está executando todas as suas operações de TI em um provedor de nuvem diferente.

Este artigo descreve as mudanças decorrentes da integração com a nova organização. Para fins da narração, supomos que essa empresa concluiu cada uma das iterações de governança descritas neste guia de governança.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narração, a empresa começou a implementar controles de custo e de monitoramento de custos, pois os gastos de nuvem se tornam parte das despesas operacionais normais da empresa.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- A identidade é controlada por uma instância local do Active Directory. A identidade híbrida é facilitada por meio da replicação para o Azure Active Directory.
- Operações de ti ou operações de nuvem são amplamente gerenciadas por Azure Monitor e recursos de automação relacionados.
- A recuperação de desastres e a DRBC (continuidade dos negócios) são controladas pelas instâncias do cofre do Azure.
- A Central de Segurança do Azure é utilizada para monitorar violações de segurança e ataques.
- A Central de Segurança do Azure e o Azure Monitor são utilizados para monitorar a governança da nuvem.
- O Azure Blueprints, Azure Policy e os grupos de gerenciamento são usados para automatizar a conformidade com a política.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

A meta é integrar a empresa de aquisição nas operações existentes, sempre que possível.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Custo de aquisição de negócios:** A aquisição da nova empresa é estimada para ser lucrativa em aproximadamente cinco anos. Devido à taxa de retorno lenta, o conselho quer controlar os custos de aquisição o máximo possível. Há um risco de controle de custos e integração técnica conflitantes entre si.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

- Há um risco de a migração de nuvem produzir custos de aquisição adicionais.
- Também há o risco do novo ambiente não ser regido adequadamente ou resultar em violações da política.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- Todos os ativos em uma nuvem secundária devem ser monitorados por meio do gerenciamento operacional e das ferramentas de monitoramento de segurança existentes.
- Todas as unidades organizacionais devem ser integradas no provedor de identidade existente.
- O provedor de identidade primário deve reger a autenticação para ativos na nuvem secundária.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhora o design de MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

1. Conectar as redes. Executado pela rede e segurança de ti, com suporte do governança.
    1. A adição de uma conexão do provedor de linha de MPLS ou concessão à nova nuvem integrará redes. Adicionar tabelas de roteamento e configurações de firewall controlará o acesso e o tráfego entre os ambientes.
1. Consolidar provedores de identidade. Dependendo das cargas de trabalho que estão sendo hospedadas na nuvem secundária, há uma variedade de opções para a consolidação do provedor de identidade. A seguir, estão alguns exemplos:
    1. Para aplicativos que autenticam usando OAuth 2, os usuários no Active Directory na nuvem secundária podem ser simplesmente replicados para o locatário do Azure AD existente.
    1. Por outro lado, a federação entre os dois provedores de identidade locais permitiria que os usuários dos novos domínios do Active Directory fossem replicados para o Azure.
1. Adicionar ativos ao Azure Site Recovery.
    1. A Azure Site Recovery foi criada como uma ferramenta híbrida e multinuvem desde o início.
    1. As máquinas virtuais na nuvem secundária podem ser protegidas pelos mesmos processos do Azure Site Recovery usados para proteger os ativos locais.
1. Adicione ativos ao gerenciamento de custos do Azure.
    1. O gerenciamento de custos do Azure foi criado como uma ferramenta de multinuvem desde o início.
    1. As máquinas virtuais na nuvem secundária podem ser compatíveis com o Gerenciamento de Custos do Azure para alguns provedores de nuvem. Custos adicionais podem ser aplicados.
1. Adicione ativos para o Azure Monitor.
    1. O Azure Monitor foi desenvolvido como uma ferramenta de nuvem híbrida desde o início.
    1. As máquinas virtuais na nuvem secundária podem ser compatíveis com os agentes do Azure Monitor, permitindo que sejam incluídas no Azure Monitor para monitoramento operacional.
1. Ferramentas de imposição de governança.
    1. A imposição de governança é específica da nuvem.
    1. As políticas corporativas estabelecidas no guia de governança não são específicas da nuvem. Embora a implementação possa variar de nuvem para nuvem, as declarações da política podem ser aplicadas ao provedor secundário.

À medida que a adoção de nuvem cresce, o design de governança acima continuará a amadurecer.

## <a name="next-steps"></a>Próximas etapas

Em muitas grandes empresas, as cinco disciplinas de governança de nuvem podem ser bloqueadores para adoção. O próximo artigo tem algumas opiniões adicionais sobre como tornar a governança um esporte de equipe para ajudar a garantir o sucesso a longo prazo na nuvem.

> [!div class="nextstepaction"]
> [Múltiplas camadas de governança](./multiple-layers-of-governance.md)
