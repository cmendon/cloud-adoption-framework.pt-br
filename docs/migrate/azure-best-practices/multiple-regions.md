---
title: Guia de decisão de regiões
description: Saiba mais sobre regiões da plataforma de nuvem e os fatores e características que podem afetar suas seleções de região do Azure.
author: doodlemania2
ms.author: dermar
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 65e2331dca7756306c875dae092faaaf41030765
ms.sourcegitcommit: d660484d534bc61fc60470373f3fcc885a358219
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508331"
---
# <a name="azure-regions"></a>Regiões do Azure

O Azure é composto por muitas regiões ao redor do mundo. Cada [região do Azure](https://azure.microsoft.com/global-infrastructure/regions) tem características específicas que fazem com que a escolha da região a ser usada seja uma etapa extremamente importante.

1. **Serviços disponíveis:** Os serviços implantados em cada região diferem com base em vários fatores. Selecione uma região para sua carga de trabalho que contenha o serviço desejado. Para obter mais informações sobre os serviços disponíveis em cada região, confira [Produtos disponíveis por região](https://azure.microsoft.com/global-infrastructure/services).
1. **Capacidade:** Cada região tem uma capacidade máxima. Embora isso seja normalmente abstrato fora do usuário final, ele pode afetar quais tipos de assinaturas podem implantar quais tipos de serviços e em que circunstâncias. Isso é diferente de cotas de assinatura. Se você estiver planejando uma migração maciça de datacenter para o Azure, talvez queira consultar sua equipe de campo do Azure local ou gerente de conta para confirmar que você pode implantar na escala necessária.
1. **Restrições:** Determinadas restrições são colocadas na implantação de serviços em determinadas regiões. Por exemplo, algumas regiões só estão disponíveis como um destino de backup ou de failover. Outras restrições importantes a serem observadas são os [requisitos de soberania de dados](https://azure.microsoft.com/global-infrastructure/geographies).
1. **Soberania nacional:** Determinadas regiões são dedicadas a entidades soberanas específicas. Embora todas as regiões sejam do Azure, essas regiões soberanas são completamente isoladas do restante do Azure, não são necessariamente gerenciadas pela Microsoft e podem ser restritas a determinados tipos de clientes. Essas regiões soberanas são:
    1. [Azure China:](https://azure.microsoft.com/global-infrastructure/china)
    1. [Azure Alemanha](https://azure.microsoft.com/global-infrastructure/germany) (está sendo preterida para dar lugar às regiões não soberanas padrão do Azure na Alemanha)
    1. [Governo dos EUA para Azure](https://azure.microsoft.com/global-infrastructure/government)
    1. Observação: duas regiões na [Austrália](https://azure.microsoft.com/global-infrastructure/australia) são gerenciadas pela Microsoft, mas são fornecidas para o governo australiano e seus clientes e prestadores de serviços e, portanto, apresentam restrições de clientes semelhantes às outras nuvens soberanas.

## <a name="operate-in-multiple-geographic-regions"></a>Operar em várias regiões geográficas

Quando as empresas operam em várias regiões geográficas, embora seja essencial para resiliência, uma complexidade adicional pode ser introduzida. Essas complexidades se manifestam de quatro formas principais:

- Distribuição de ativos
- Perfis de acesso do usuário
- Requisitos de conformidade
- Resiliência regional

À medida que considerarmos ainda mais as complexidades acima, você começará a entender como a seleção regional é importante para sua estratégia geral de adoção da nuvem. Vamos começar com as considerações de rede.

## <a name="networking-considerations"></a>Considerações de rede

Qualquer implantação robusta de nuvem requer uma rede bem considerada que leva em conta as regiões do Azure. Depois de considerar as características acima para em quais regiões implantar, a rede deve ser implantada. Embora uma discussão exaustiva sobre a rede esteja além do escopo deste artigo, alguns pontos devem ser considerados:

- As regiões do Azure são implantadas em pares. No caso de uma falha catastrófica de uma região, outra região no mesmo limite geopolítico* será designada como sua região emparelhada. Deve-se considerar a implantação em regiões emparelhadas como a estratégia de resiliência primária e secundária. *O Azure Brasil é uma exceção notável cuja região emparelhada é o Centro-Sul dos EUA. Para saber mais, consulte [Regiões emparelhadas do Azure](https://docs.microsoft.com/azure/best-practices-availability-paired-regions).

  - O Armazenamento do Azure dá suporte ao [GRS (Armazenamento com Redundância Geográfica)](https://docs.microsoft.com/azure/storage/common/storage-redundancy-grs), o que significa que três cópias de seus dados são armazenadas em sua região primária e três cópias adicionais são armazenadas na região emparelhada. Não é possível alterar o emparelhamento de armazenamento para o GRS.
  - Os serviços que dependem do GRS do Armazenamento do Azure podem aproveitar essa funcionalidade de região emparelhada. Para fazer isso, seus aplicativos e a rede devem ser orientados a dar suporte a isso.
  - Se você não planeja usar o GRS para dar suporte às suas necessidades de resiliência regionais, sugerimos que você _NÃO_ use a região emparelhada como sua secundária. No caso de uma falha regional, haverá pressão intensa em recursos na região emparelhada conforme os recursos forem migrados. Evitar essa pressão pode proporcionar uma velocidade adicional durante sua recuperação recuperando-se para um site alternativo.
  > [!WARNING]
  > Não tente usar o GRS do Azure para backups ou recuperação de VM. Nesse caso, aproveite o [Backup do Azure](https://azure.microsoft.com/services/backup) e o [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery) juntamente com os [discos gerenciados do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) para dar suporte à resiliência de carga de trabalho de IaaS.

- O Backup do Azure e o Azure Site Recovery funcionam em conjunto com seu design de rede para facilitar a resiliência regional para suas necessidades de IaaS e backup de dados. Verifique se a rede está otimizada para que as transferências de dados permaneçam no backbone da Microsoft e usem o [Emparelhamento VNET](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview), se possível. Algumas organizações maiores com implantações globais podem usar o [ExpressRoute Premium](https://docs.microsoft.com/azure/expressroute/expressroute-introduction) para rotear o tráfego entre regiões que podem economizar encargos de saída regionais.

- Os grupos de recursos do Azure são constructos específicos regionais. Contudo, é normal que os recursos dentro de um grupo de recursos abranjam várias regiões. Ao fazer isso, é importante considerar que, no caso de uma falha regional, as operações do painel de controle em um grupo de recursos falharão na região afetada, mesmo que os recursos em outras regiões (nesse grupo de recursos) continuem a funcionar. Isso pode afetar o design de rede e o design do grupo de recursos.

- Muitos serviços PaaS no Azure dão suporte a [Pontos de Extremidade de Serviços](https://docs.microsoft.com/azure/virtual-network/virtual-network-service-endpoints-overview) ou a um [Link Privado](https://docs.microsoft.com/azure/private-link/private-link-overview). Essas duas soluções afetam suas considerações de rede substancialmente ao considerar a resiliência, migração e governança regionais.

- Muitos serviços PaaS dependem de suas próprias soluções de resiliência regional. Por exemplo, o Banco de Dados SQL do Azure e o Cosmos DB permitem uma replicação fácil para _x_ regiões adicionais. Alguns serviços não apresentam nenhuma dependência de região, como o DNS do Azure. Enquanto você considera quais serviços usará no processo de adoção, procure entender claramente as funcionalidades de failover e as etapas de recuperação que podem ser necessárias para cada serviço do Azure.

- Além de implantar em várias regiões para dar suporte à recuperação de desastre, muitas organizações optam por implantar em um padrão Ativo-Ativo para que nenhum failover seja necessário. Isso tem o benefício adicional de fornecer balanceamento de carga global e mais aumentos de desempenho de rede e tolerância a falhas. Para usar esse padrão, seus aplicativos devem dar suporte à execução de Ativo-Ativo em várias regiões.

> [!WARNING]
> As regiões do Azure são constructos altamente disponíveis com SLAs aplicados aos serviços em execução nelas. No entanto, você nunca deve usar uma dependência de região única em aplicativos críticos. Sempre planeje a falha regional e pratique etapas de recuperação e mitigação.

Após considerar a topologia de rede que será necessária para mantê-lo em operação, serão necessários uma documentação adicional e o alinhamento de processos. A abordagem a seguir pode ajudar a avaliar os desafios potenciais e estabelecer um curso geral de ação:

- Considere uma implementação mais eficiente de preparação e governança.
- Faça o inventário das geografias afetadas. Compile uma lista de regiões e países afetados.
- Documente os requisitos de soberania de dados. Os países identificados têm requisitos de conformidade que controlam a soberania de dados?
- Documente a base de usuários. Os funcionários, parceiros ou clientes no país identificado serão afetados pela migração na nuvem?
- Documente datacenters e ativos. Há ativos no país identificado que possam ser incluídos no esforço de migração?
- Documente os requisitos de failover e disponibilidade do SKU regional.

Alinhe as alterações no processo de migração para abordar o inventário inicial.

## <a name="document-complexity"></a>Complexidade do documento

A tabela a seguir pode auxiliar na documentação das descobertas das etapas acima:

| Região        | País     | Funcionários locais | Usuários externos locais   | Datacenters locais ou ativos | Requisitos de soberania de dados |
|---------------|-------------|-----------------|------------------------|-----------------------------|-------------------------------|
| América do Norte | EUA         | Sim             | Parceiros e clientes | Sim                         | Não                            |
| América do Norte | Canadá      | Não              | Clientes              | Sim                         | Sim                           |
| Europa        | Germany     | Sim             | Parceiros e clientes | Não – Apenas rede           | Sim                           |
| Pacífico Asiático  | Coreia do Sul | Sim             | Parceiros               | Sim                         | Não                            |

<!-- markdownlint-disable MD026 -->

## <a name="data-sovereignty-relevancy"></a>Relevância da soberania de dados

Em todo o mundo, as organizações governamentais começaram a estabelecer os requisitos da soberania de dados, como o RGPD (Regulamento Geral sobre a Proteção de Dados). Os requisitos de conformidade dessa natureza geralmente exigem a localização em uma região específica ou mesmo em um país específico para proteger seus cidadãos. Em alguns casos, os dados pertencentes a clientes, funcionários ou parceiros devem ser armazenados em uma plataforma de nuvem na mesma região que o usuário final.

Abordar esse desafio foi uma motivação significativa para migrações de nuvem para empresas que operam em uma escala global. Para manter os requisitos de conformidade, algumas empresas optaram por implantar ativos de TI duplicados em provedores de nuvem na região. Na tabela acima, a Alemanha é um bom exemplo desse cenário. Nesse exemplo, há clientes, parceiros e funcionários na Alemanha, mas não há ativos de TI existentes. Essa empresa pode optar por implantar alguns ativos em um datacenter na área de RGPD, potencialmente até mesmo usando os datacenters do Azure em alemão. Uma compreensão dos dados afetados pelo RGPD ajudaria a equipe de adoção da nuvem a entender a melhor abordagem de migração nesse caso.

### <a name="why-is-the-location-of-end-users-relevant"></a>Por que a localização dos usuários finais é relevante?

As empresas que dão suporte a usuários finais em vários países desenvolveram soluções técnicas para lidar com o tráfego do usuário final. Em alguns casos, isso envolve a localização de ativos. Em outros cenários, a empresa pode escolher, em vez disso, implementar soluções de WAN globais para abordar bases de usuários diferentes por meio de soluções focadas na rede. Em ambos os casos, a estratégia de migração pode ser afetada pelos perfis de uso desses usuários finais distintos.

Como a empresa dá suporte a funcionários, parceiros e clientes na Alemanha, mas não há datacenters atualmente nesse país, é provável que essa empresa tenha implementado alguma forma de solução de linha concedida para encaminhar esse tráfego para datacenters em outros países. Esse roteamento existente apresenta um risco significativo para o desempenho percebido dos aplicativos migrados. Injetar saltos adicionais em uma WAN global estabelecida e ajustada pode criar a percepção de aplicativos com desempenho abaixo do esperado após a migração. Encontrar e corrigir esses problemas pode adicionar atrasos significativos a um projeto. Em cada um dos processos abaixo, as diretrizes para tratar essa complexidade estão incluídas em pré-requisitos, avaliar, migrar e otimizar processos. Entender os perfis de usuário em cada país é essencial para gerenciar adequadamente essa complexidade.

### <a name="why-is-the-location-of-datacenters-relevant"></a>Por que a localização dos datacenters é relevante?

A localização dos datacenters existentes pode afetar uma estratégia de migração. A seguir, estão alguns dos impactos mais comuns:

**Decisões de arquitetura:** A região de destino é uma das primeiras etapas no design da estratégia de migração. Isso geralmente é influenciado pela localização dos ativos existentes. Além disso, a disponibilidade dos serviços de nuvem e o custo unitário desses serviços podem variar de uma região para a outra. Dessa forma, entender a localização atual e futura dos ativos afeta as decisões de arquitetura e também pode afetar as estimativas de orçamento.

**Dependências do datacenter:** Com base nos dados na tabela acima, é provável que existam dependências entre os vários data centers em todo o mundo. Em muitas organizações que operam nesse tipo de escala, essas dependências podem não ser documentadas ou bem compreendidas. As abordagens usadas para avaliar os perfis de usuário ajudarão a identificar algumas dessas dependências. No entanto, são sugeridas etapas adicionais durante o processo de avaliação para atenuar os riscos associados a essa complexidade.

## <a name="implementing-the-general-approach"></a>Implementar a abordagem geral

Essa abordagem é orientada por informações quantificáveis. Como tal, a abordagem a seguir seguirá um modelo controlado por dados para abordar as complexidades de migração global.

Quando o escopo de uma migração inclui várias regiões, as seguintes considerações de preparação devem ser avaliadas pela equipe de adoção da nuvem:

- A soberania de dados pode exigir a localização de alguns ativos, mas muitos ativos podem não ser controlados por essas restrições de conformidade. Itens como registro em log, relatórios, roteamento de rede, identidade e outros serviços de TI central podem estar qualificados para serem hospedados como serviços compartilhados em várias assinaturas ou até mesmo em várias regiões. A equipe de adoção de nuvem deve avaliar o uso de um modelo de serviço compartilhado para esses serviços, conforme descrito na [arquitetura de referência para uma topologia hub-spoke com serviços compartilhados](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- Ao implantar várias instâncias de ambientes semelhantes, um alocador de ambiente poderia criar consistência, melhorar a governança e acelerar a implantação. O [guia de governança para empresas complexas](../../govern/guides/complex/index.md) estabelece uma abordagem que cria um ambiente dimensionado em várias regiões.

Quando a equipe está adaptada à abordagem de linha de base e a preparação está alinhada, alguns pré-requisitos controlados por dados devem ser considerados:

- **Descoberta geral:** Conclua a tabela de [complexidade de documentação](#document-complexity) acima.
- **Executar uma análise de perfil de usuário em cada país afetado:** É importante entender o roteamento geral do usuário final no processo de migração. Alterar as linhas de concessão globais e adicionar conexões como o ExpressRoute a um datacenter na nuvem pode exigir meses de atrasos de rede. Resolva isso o quanto antes no processo.
- **Racionalização de imóveis digital inicial:** Sempre que a complexidade é introduzida em uma estratégia de migração, uma racionalização de imóveis digitais inicial deve ser concluída. Confira as diretrizes sobre [racionalização de propriedade digital](../../digital-estate/index.md) para obter assistência.
  - **Requisitos de imóveis digitais adicionais:** Estabeleça políticas de marcação para identificar qualquer carga de trabalho afetada pelos requisitos da soberania de dados. As marcas necessárias devem começar na racionalização de propriedade digital e ser transferida para os ativos migrados.
- **Avaliar um modelo de Hub e spoke:** Os sistemas distribuídos geralmente compartilham dependências comuns. Essas dependências geralmente podem ser abordadas por meio da implementação de um modelo de hub e spoke. Embora esse modelo esteja fora do escopo do processo de migração, ele deve ser sinalizado para consideração durante iterações futuras dos [Processos prontos](../../ready/index.md).
- **Priorização da pendência de migração:** Quando as alterações de rede são necessárias para dar suporte à implantação de produção de uma carga de trabalho que dá suporte a várias regiões, é importante que a equipe de estratégia de nuvem acompanhe e gerencie escalonamento em relação a essas alterações de rede. O nível mais alto de suporte executivo auxiliará na aceleração da alteração. No entanto, o impacto mais importante é que ele dá à equipe de estratégia uma capacidade de priorizar novamente a lista de pendências para verificar se as cargas de trabalho globais não são bloqueadas pelas alterações de rede. Essas cargas de trabalho só deverão ser priorizadas depois que as alterações de rede forem concluídas.

Esses pré-requisitos ajudarão a estabelecer processos que possam resolver essa complexidade durante a execução da estratégia de migração.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Ao lidar com as complexidades globais da base de usuários e dos ativos, há algumas atividades importantes que devem ser adicionadas à avaliação de qualquer candidato à migração. Cada uma dessas alterações trará clareza ao impacto sobre os usuários e ativos globais, por meio de uma abordagem controlada por dados.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

**Avaliar dependências entre datacenters:** As [ferramentas de visualização de dependência nas migrações para Azure](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization) podem ajudar a identificar dependências. O uso dessas ferramentas antes da migração é uma prática recomendada. Mas ao lidar com a complexidade global, ela se torna uma etapa obrigatória no processo de avaliação. Por meio do [agrupamento de dependências](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies), a visualização pode ajudar a identificar os endereços IP e as portas de ativos necessários para dar suporte à carga de trabalho.

> [!IMPORTANT]
> Duas observações importantes: primeiro, um especialista no assunto com uma compreensão do posicionamento do ativo e dos esquemas de endereço IP é necessário para identificar os ativos que residem em um datacenter secundário. Depois, é importante avaliar as dependências de downstream e os Clientes no visual para entender as dependências bidirecionais.

**Identifique o impacto do usuário global:** As saídas da análise de perfil de usuário de pré-requisito devem identificar qualquer carga de trabalho afetada por perfis de usuário globais. Quando um candidato à migração está na lista de cargas de trabalho afetadas, o arquiteto que está se preparando para a migração deve consultar especialistas no assunto de redes e operações para validar as expectativas de desempenho e de roteamento de rede. No mínimo, a arquitetura deve incluir uma conexão do ExpressRoute entre o NOC (centro de operações de rede) mais próximo e o Azure. A [arquitetura de referência para conexões do ExpressRoute](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/expressroute) pode auxiliar na configuração da conexão necessária.

**Design para conformidade:** As saídas da análise de perfil de usuário de pré-requisito devem identificar qualquer carga de trabalho afetada pelos requisitos da soberania de dados. Durante as atividades de arquitetura do processo de avaliação, o arquiteto atribuído deve consultar especialistas no assunto de conformidade para entender os requisitos de migração/implantação em várias regiões. Esses requisitos afetarão significativamente as estratégias de design. As arquiteturas de referência para [aplicativos Web de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server) podem auxiliar no design.

> [!WARNING]
> Ao usar qualquer uma das arquiteturas de referência acima, pode ser necessário excluir elementos de dados específicos dos processos de replicação para aderir aos requisitos da soberania de dados. Isso adicionará mais uma etapa ao processo de promoção.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Ao migrar um aplicativo que precisa ser implantado em várias regiões, há algumas considerações que a equipe de adoção de nuvem precisa levar em conta. Essas considerações são compostas pelo design do cofre do Azure Site Recovery, design do servidor de processo/configuração, designs de largura de banda de rede e sincronização de dados.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

**Design do cofre de Azure site Recovery:** Azure Site Recovery é a ferramenta sugerida para replicação nativa de nuvem e sincronização de ativos digitais para o Azure. O Site Recovery replica dados sobre o ativo para um cofre do Site Recovery, que está associado a uma assinatura específica em uma região específica e em um datacenter do Azure. Ao replicar ativos para uma segunda região, um segundo cofre do Site Recovery pode ser necessário.

**Configuração/design do servidor de processo:** Site Recovery trabalha com uma instância local de um servidor de configuração e de processo, que está associada a um único cofre de Site Recovery. Isso significa que uma segunda instância desses servidores pode precisar ser instalada no datacenter de origem para facilitar a replicação.

**Design de largura de banda de rede:** Durante a replicação e a sincronização contínua, os dados binários são movidos pela rede do datacenter de origem para o cofre de Site Recovery no datacenter do Azure de destino. Esse processo consome largura de banda. A duplicação da carga de trabalho para uma segunda região duplicará a quantidade de largura de banda consumida. Quando a largura de banda é limitada ou uma carga de trabalho envolve uma grande quantidade de configuração ou de descompasso de dados, ela pode interferir no tempo necessário para concluir a migração. O mais importante é que isso poderia afetar a experiência de usuários ou aplicativos que ainda dependem da largura de banda do datacenter de origem.

**Sincronização de dados:** Geralmente, o maior consumo de largura de banda vem da sincronização da plataforma de dados. Conforme definido nas arquiteturas de referência para [aplicativos Web de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), a sincronização de dados geralmente é necessária para manter os aplicativos alinhados. Se esse for o estado operacional desejado do aplicativo, poderá ser recomendável concluir uma sincronização entre a plataforma de dados de origem e cada uma das plataformas de nuvem antes de migrar o aplicativo e ativos da camada intermediária.
**Sincronização de dados:** Geralmente, o maior consumo de largura de banda vem da sincronização da plataforma de dados. Conforme definido nas arquiteturas de referência para [aplicativos Web de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](https://docs.microsoft.com/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), a sincronização de dados geralmente é necessária para manter os aplicativos alinhados. Se esse for o estado operacional desejado do aplicativo, poderá ser recomendável concluir uma sincronização entre a plataforma de dados de origem e cada uma das plataformas de nuvem antes de migrar o aplicativo e ativos da camada intermediária.

**Recuperação de desastre do Azure para o Azure:** Uma opção alternativa pode reduzir ainda mais a complexidade. Se as linhas do tempo e as abordagens de sincronização de dados abordarem uma implantação em duas etapas, a [recuperação de desastre do Azure para o Azure](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-architecture) poderá ser uma solução aceitável. Nesse cenário, a carga de trabalho é migrada para o primeiro datacenter do Azure usando um único cofre do Site Recovery e o design do servidor de processo ou configuração. Depois que a carga de trabalho é testada, ela pode ser recuperada para um segundo datacenter do Azure por meio dos ativos migrados. Essa abordagem reduz o impacto dos recursos no datacenter de origem e aproveita as velocidades de transferência mais rápidas e limites de largura de banda altos disponíveis entre datacenters do Azure.

> [!NOTE]
> Essa abordagem pode aumentar o custo de curto prazo da migração, pois ela pode resultar em encargos adicionais de largura de banda de saída.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Abordar a complexidade global durante a otimização e a promoção pode exigir esforços duplicados em cada uma das regiões adicionais. Quando uma única implantação é aceitável, a duplicação de testes empresariais e de planos de mudança empresarial ainda pode ser necessária.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Ação sugerida durante o processo de otimização e promoção

**Otimização de teste:** O teste de automação inicial pode identificar possíveis oportunidades de otimização, assim como ocorre com qualquer esforço de migração. No caso de cargas de trabalho globais, é importante testar a carga de trabalho em cada região independentemente, pois alterações de configuração secundárias na rede ou no datacenter do Azure de destino poderiam afetar o desempenho.

**Planos de mudança de negócios:** Para qualquer cenário de migração complexo, um plano de alteração comercial deve ser criado para garantir a comunicação clara em relação a quaisquer alterações nos processos de negócios, experiências do usuário e tempo dos esforços necessários para a integração das alterações. No caso de esforços de migração global, o plano deve incluir considerações para usuários finais em cada geografia afetada.

**Testes de negócios:** Em conjunto com o plano de mudança de negócios, os testes de negócios podem ser necessários em cada região para garantir o desempenho adequado e a adesão aos padrões de roteamento de rede modificados.

**Vôos de promoção:** Geralmente, a promoção ocorre como uma única atividade, redirecionando o tráfego de produção para as cargas de trabalho migradas. No caso de esforços de lançamento global, a promoção deve ser entregue em versões de pré-lançamento (ou coleções de usuários predefinidas). Isso permite que a equipe de estratégia da nuvem e a equipe de adoção da nuvem observem melhor o desempenho e melhorem o suporte aos usuários em cada região. As versões de pré-lançamento de promoção geralmente são controladas no nível da rede por meio da alteração do roteamento de intervalos de IP específicos desde os ativos de carga de trabalho de origem até os ativos recém-migrados. Depois que uma coleção especificada de usuários finais tiver sido migrada, o próximo grupo poderá ser reencaminhado.

**Otimização do vôo:** Um dos benefícios dos vôos de promoção é que ele permite observações mais aprofundadas e otimização adicional dos ativos implantados. Após um breve período de uso de produção pela primeira versão de pré-lançamento, será sugerido outro refinamento dos ativos migrados, quando permitido pelos procedimentos de operação de TI.
