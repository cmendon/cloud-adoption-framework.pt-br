---
title: 'Guia de governança para empresas complexas: melhoria em nuvem'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: melhoria em nuvem'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4279f088dd985b26c87d28a580b8351d45d9384e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547662"
---
# <a name="governance-guide-for-complex-enterprises-multicloud-improvement"></a>Guia de governança para empresas complexas: melhoria em nuvem

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A Microsoft reconhece que os clientes podem adotar várias nuvens para fins específicos. A empresa fictícia neste guia não é exceção. Em paralelo com a jornada de adoção do Azure, o sucesso dos negócios levou à aquisição de um negócio pequeno, mas complementar. Essa empresa está executando todas as suas operações de ti em um provedor de nuvem diferente.

Este artigo descreve como as coisas mudam ao integrar a nova organização. Para fins da narração, supomos que essa empresa concluiu cada uma das iterações de governança descritas neste guia de governança.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narração, a empresa começou a implementar controles de custo e de monitoramento de custos, pois os gastos de nuvem se tornam parte das despesas operacionais normais da empresa.

Desde então, algumas coisas mudaram que afetarão a governança:

- A identidade é controlada por uma instância local do Active Directory. A identidade híbrida é facilitada por meio da replicação para Azure Active Directory.
- Operações de ti ou operações de nuvem são amplamente gerenciadas por Azure Monitor e recursos de automação relacionados.
- A recuperação de desastres e a DRBC (continuidade dos negócios) são controladas pelas instâncias do cofre do Azure.
- A central de segurança do Azure é usada para monitorar violações e ataques de segurança.
- A central de segurança do Azure e os Azure Monitor são usados para monitorar a governança da nuvem.
- Os planos gráficos do Azure, Azure Policy e grupos de gerenciamento são usados para automatizar a conformidade com a política.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

O objetivo é integrar a empresa de aquisição em operações existentes sempre que possível.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Custo de aquisição de negócios:** A aquisição da nova empresa é estimada para ser lucrativa em aproximadamente cinco anos. Devido à taxa de retorno lenta, o quadro deseja controlar os custos de aquisição, tanto quanto possível. Há um risco de controle de custo e de integração técnica entre si.

Esse risco comercial pode ser expandido em alguns riscos técnicos:

- Há um risco de a migração de nuvem produzir custos de aquisição adicionais.
- Também há um risco de o novo ambiente não ser administrado adequadamente ou resultar em violações de política.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- Todos os ativos em uma nuvem secundária devem ser monitorados por meio de ferramentas de monitoramento de segurança e de gerenciamento operacional existentes.
- Todas as unidades organizacionais devem ser integradas ao provedor de identidade existente.
- O provedor de identidade principal deve governar a autenticação para ativos na nuvem secundária.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhora o design de MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas duas alterações de design atenderão às novas instruções de política corporativa.

1. Conecte as redes. Executado pela rede e segurança de ti, com suporte do governança.
    1. A adição de uma conexão do provedor de linha de MPLS ou concessão à nova nuvem integrará redes. Adicionar tabelas de roteamento e configurações de firewall controlará o acesso e o tráfego entre os ambientes.
2. Consolide provedores de identidade. Dependendo das cargas de trabalho que estão sendo hospedadas na nuvem secundária, há uma variedade de opções para a consolidação do provedor de identidade. Veja a seguir alguns exemplos:
    1. Para aplicativos que se autenticam usando o OAuth 2, os usuários na Active Directory na nuvem secundária poderiam simplesmente ser replicados para o locatário existente do Azure AD.
    2. Por outro lado, a Federação entre os dois provedores de identidade local permite que os usuários da nova Active Directory domínios sejam replicados para o Azure.
3. Adicionar ativos a Azure Site Recovery.
    1. A Azure Site Recovery foi criada como uma ferramenta híbrida e multinuvem desde o início.
    2. As máquinas virtuais na nuvem secundária podem ser protegidas pelo mesmo Azure Site Recovery processos usados para proteger ativos locais.
4. Adicione ativos ao gerenciamento de custos do Azure.
    1. O gerenciamento de custos do Azure foi criado como uma ferramenta de multinuvem desde o início.
    2. As máquinas virtuais na nuvem secundária podem ser compatíveis com o gerenciamento de custos do Azure para alguns provedores de nuvem. Podem ser aplicados custos adicionais.
5. Adicionar ativos a Azure Monitor.
    1. A Azure Monitor foi criada como uma ferramenta de nuvem híbrida desde o início.
    2. As máquinas virtuais na nuvem secundária podem ser compatíveis com agentes de Azure Monitor, permitindo que eles sejam incluídos em Azure Monitor para monitoramento operacional.
6. Ferramentas de imposição de governança.
    1. A imposição de governança é específica da nuvem.
    2. As políticas corporativas estabelecidas no guia de governança não são específicas da nuvem. Embora a implementação possa variar de nuvem para nuvem, as instruções de política podem ser aplicadas ao provedor secundário.

A adoção de multinuvem deve estar contida em onde é necessário com base em necessidades técnicas ou em requisitos de negócios específicos. À medida que a adoção de nuvem cresce, isso aumenta a complexidade e os riscos de segurança.

## <a name="next-steps"></a>Próximos passos

Em muitas grandes empresas, as cinco disciplinas de governança de nuvem podem ser bloqueadores para adoção. O próximo artigo tem algumas opiniões adicionais sobre como tornar a governança um esporte de equipe para ajudar a garantir o sucesso a longo prazo na nuvem.

> [!div class="nextstepaction"]
> [Várias camadas de governança](./multiple-layers-of-governance.md)
