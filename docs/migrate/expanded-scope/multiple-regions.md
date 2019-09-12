---
title: Abordar a complexidade de migrar várias regiões geográficas
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aborde a complexidade de migrar várias regiões geográficas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3977618981212e2c0dc4dcd95ae14bf4dc773499
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905600"
---
# <a name="multiple-geographic-regions"></a>Várias regiões geográficas

Quando as empresas operam em várias regiões geográficas, uma complexidade adicional pode ser introduzida nos esforços de migração na nuvem. Essas complexidades se manifestam em três formulários principais: distribuição de ativos, perfis de acesso do usuário e requisitos de conformidade. Antes de abordar as complexidades relacionadas a várias regiões, é importante entender a extensão da complexidade potencial.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

A abordagem a seguir pode ajudar a avaliar os desafios potenciais e estabelecer um curso geral de ação:

- Considere uma implementação mais eficiente de preparação e governança.
- Faça o inventário das geografias afetadas. Compile uma lista das regiões e dos países afetados pela migração na nuvem.
- Documente os requisitos de soberania de dados: Os países identificados têm requisitos de conformidade que controlam a soberania de dados?
- Documente a base de usuários: Os funcionários, parceiros ou clientes no país identificado serão afetados pela migração na nuvem?
- Documente datacenters e ativos: Há ativos no país identificado que possam ser incluídos no esforço de migração?

Alinhe as alterações no processo de migração para abordar o inventário inicial.

### <a name="documenting-complexity"></a>Documentar a complexidade

A tabela a seguir pode auxiliar na documentação das descobertas das etapas acima:

|Região  |País  |Funcionários locais  |Usuários externos locais  |Datacenters locais ou ativos |Requisitos de soberania de dados  |
|---------|---------|---------|---------|---------|---------|
|América do Norte     |USA         |Sim         |Parceiros e clientes         |Sim         |Não         |
|América do Norte     |Canadá         |Não         |Clientes         |Sim         |Sim         |
|Europa     |Alemanha         |Sim         |Parceiros e clientes         |Não – Apenas rede         |Sim         |
|Pacífico Asiático     |Coreia do Sul         |Sim         |Parceiros         |Sim         |Não         |

<!-- markdownlint-disable MD026 -->

### <a name="why-is-data-sovereignty-relevant"></a>Por que a soberania de dados é relevante?

Em todo o mundo, as organizações governamentais começaram a estabelecer os requisitos da soberania de dados, como o RGPD (Regulamento Geral sobre a Proteção de Dados). Os requisitos de conformidade dessa natureza geralmente exigem a localização em uma região específica ou mesmo em um país específico para proteger seus cidadãos. Em alguns casos, os dados pertencentes a clientes, funcionários ou parceiros devem ser armazenados em uma plataforma de nuvem na mesma região que o usuário final.

Abordar esse desafio foi uma motivação significativa para migrações de nuvem para empresas que operam em uma escala global. Para manter os requisitos de conformidade, algumas empresas optaram por implantar ativos de TI duplicados em provedores de nuvem na região. Na tabela de exemplo acima, Alemanha seria um bom exemplo desse cenário. Neste exemplo, há clientes, parceiros e funcionários na Alemanha, mas não há ativos de TI existentes. Essa empresa pode optar por implantar alguns ativos em um datacenter na área de RGPD, potencialmente até mesmo usando os datacenters do Azure em alemão. Uma compreensão dos dados afetados pelo RGPD ajudaria a equipe de adoção da nuvem a entender a melhor abordagem de migração nesse caso.

### <a name="why-is-the-location-of-end-users-relevant"></a>Por que a localização dos usuários finais é relevante?

As empresas que dão suporte a usuários finais em vários países desenvolveram soluções técnicas para lidar com o tráfego do usuário final. Em alguns casos, isso envolve a localização de ativos. Em outros cenários, a empresa pode escolher, em vez disso, implementar soluções de WAN globais para abordar bases de usuários diferentes por meio de soluções focadas na rede. Em ambos os casos, a estratégia de migração pode ser afetada pelos perfis de uso desses usuários finais distintos.

Como a empresa dá suporte a funcionários, parceiros e clientes na Alemanha, mas não há datacenters atualmente nesse país, é provável que essa empresa tenha implementado alguma forma de solução de linha concedida para rotear esse tráfego para datacenters em outros países. Esse roteamento existente apresenta um risco significativo para o desempenho percebido dos aplicativos migrados. Injetar saltos adicionais em uma WAN global estabelecida e ajustada pode criar a percepção de aplicativos com desempenho abaixo do esperado após a migração. Encontrar e corrigir esses problemas pode adicionar atrasos significativos a um projeto. Em cada um dos processos abaixo, as diretrizes para tratar essa complexidade estão incluídas em pré-requisitos, avaliar, migrar e otimizar processos. Entender os perfis de usuário em cada país é essencial para gerenciar adequadamente essa complexidade.

### <a name="why-is-the-location-of-datacenters-relevant"></a>Por que a localização dos datacenters é relevante?

A localização dos datacenters existentes pode afetar uma estratégia de migração. A seguir, estão alguns dos impactos mais comuns:

**Decisões de arquitetura:** região/localização de destino é uma das primeiras etapas no design da estratégia de migração. Isso geralmente é influenciado pela localização dos ativos existentes. Além disso, a disponibilidade dos serviços de nuvem e o custo unitário desses serviços podem variar de uma região para a outra. Dessa forma, entender a localização atual e futura dos ativos afeta as decisões de arquitetura e também pode afetar as estimativas de orçamento.

**Dependências de datacenters:** com base nos dados na tabela acima, é provável que existam dependências entre os vários datacenters em todo o mundo. Em muitas organizações que operam nesse tipo de escala, essas dependências podem não ser documentadas ou bem compreendidas. As abordagens usadas para avaliar os perfis de usuário ajudarão a identificar algumas dessas dependências. No entanto, são sugeridas etapas adicionais durante o processo de avaliação para atenuar os riscos associados a essa complexidade.

## <a name="implementing-the-general-approach"></a>Implementar a abordagem geral

Essa abordagem é orientada por informações quantificáveis. Como tal, a abordagem a seguir seguirá um modelo controlado por dados para abordar as complexidades de migração global.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

É recomendável que a equipe de adoção da nuvem comece com a migração de uma carga de trabalho simples usando o [guia de migração do Azure](../azure-migration-guide/index.md) antes de tentar abordar a escala global. Com isso, a equipe estará familiarizada com o processo geral de migração na nuvem antes de tentar um cenário de migração mais complexo.

Quando o escopo de uma migração inclui várias regiões, as seguintes considerações de preparação devem ser avaliadas pela equipe de adoção da nuvem:

- A soberania de dados pode exigir a localização de alguns ativos, mas há muitos ativos que podem não ser controlados por essas restrições de conformidade. Itens como registro em log, relatórios, roteamento de rede, identidade e outros serviços de TI central podem estar qualificados para serem hospedados como serviços compartilhados em várias assinaturas ou até mesmo em várias regiões. É recomendável que a equipe de adoção de nuvem avalie um modelo de serviço de compartilhamento para esses serviços, conforme descrito na [arquitetura de referência para uma topologia de hub e spoke com serviços compartilhados](/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- Ao implantar várias instâncias de ambientes semelhantes, um alocador de ambiente poderia criar consistência, melhorar a governança e acelerar a implantação. O [grande percurso de governança empresarial](../../governance/journeys/complex-enterprise/index.md) estabelece uma abordagem que cria um alocador de ambiente dimensionado em várias regiões.

Quando a equipe se sentir confortável com a abordagem de linha de base e a preparação estiver alinhada, haverá alguns pré-requisitos controlados por dados a serem considerados:

- **Descoberta geral:** preencha a tabela [Documentar complexidade](#documenting-complexity) acima.
- **Executar uma análise de perfil do usuário em cada país afetado:** é importante entender o roteamento geral do usuário final no processo de migração. Alterar as linhas de concessão globais e adicionar conexões como o ExpressRoute a um datacenter na nuvem pode exigir meses de atrasos de rede. Resolva isso o quanto antes no processo.
- **Racionalização de propriedade digital inicial:** sempre que a complexidade é introduzida em uma estratégia de migração, uma racionalização de propriedade digital inicial deve ser concluída. Confira as diretrizes sobre [racionalização de propriedade digital](../../digital-estate/index.md) para obter assistência.
  - **Outros requisitos de propriedade digital:** estabeleça políticas de marcação para identificar qualquer carga de trabalho afetada pelos requisitos da soberania de dados. As marcas necessárias devem começar na racionalização de propriedade digital e ser transferida para os ativos migrados.
- **Avaliar um modelo de hub e spoke:** os sistemas distribuídos geralmente compartilham dependências comuns. Essas dependências geralmente podem ser abordadas por meio da implementação de um modelo de hub e spoke. Embora esse modelo esteja fora do escopo do processo de migração, ele deve ser sinalizado para consideração durante iterações futuras dos [Processos prontos](../../ready/index.md).
- **Priorização da lista de pendências de migração:** Quando são necessárias alterações de rede para dar suporte à implantação de produção de uma carga de trabalho que é compatível com várias regiões, é importante que a equipe de estratégia da nuvem acompanhe e gerencie os escalonamentos relacionados a tais alterações de rede. O nível mais alto de suporte executivo auxiliará na aceleração da alteração. No entanto, o impacto mais importante é que ele dá à equipe de estratégia uma capacidade de priorizar novamente a lista de pendências para verificar se as cargas de trabalho globais não são bloqueadas pelas alterações de rede. Essas cargas de trabalho só deverão ser priorizadas depois que as alterações de rede forem concluídas.

Esses pré-requisitos ajudarão a estabelecer processos que possam resolver essa complexidade durante a execução da estratégia de migração.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Ao lidar com complexidades de base de usuário e de ativo global, há algumas atividades importantes que devem ser adicionadas à avaliação de qualquer candidato à migração. Cada uma dessas alterações trará clareza ao impacto sobre os usuários e ativos globais, por meio de uma abordagem controlada por dados.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

**Avaliar dependências entre datacenters:** as [ferramentas de visualização de dependência nas Migrações para Azure](/azure/migrate/concepts-dependency-visualization) podem ajudar a identificar dependências. O uso desse conjunto de ferramentas antes da migração é uma melhor prática geral. No entanto, ao lidar com a complexidade global, ela se torna uma etapa necessária para o processo de avaliação. Por meio do [agrupamento de dependências](/azure/migrate/how-to-create-group-machine-dependencies), a visualização pode ajudar a identificar os endereços IP e as portas de ativos necessários para dar suporte à carga de trabalho.

> [!IMPORTANT]
> Duas observações importantes: Primeiro, é necessário um especialista no assunto com compreensão do posicionamento do ativo e dos esquemas de endereço IP para identificar os ativos que residem em um datacenter secundário. Depois, é importante avaliar as dependências de downstream e os Clientes no visual para entender as dependências bidirecionais.

**Identificar o impacto do usuário global:** as saídas da análise de perfil do usuário de pré-requisito devem identificar qualquer carga de trabalho afetada por perfis de usuário globais. Quando um candidato à migração está na lista de cargas de trabalho afetadas, o arquiteto que está se preparando para a migração deve consultar especialistas no assunto de redes e operações para validar as expectativas de desempenho e de roteamento de rede. No mínimo, a arquitetura deve incluir uma conexão do ExpressRoute entre o NOC (centro de operações de rede) mais próximo e o Azure. A [arquitetura de referência para conexões do ExpressRoute](/azure/architecture/reference-architectures/hybrid-networking/expressroute) pode auxiliar na configuração da conexão necessária.

**Design para conformidade:** as saídas da análise de perfil do usuário de pré-requisito devem identificar qualquer carga de trabalho afetada por requisitos de soberania de dados. Durante as atividades de arquitetura do processo de avaliação, o arquiteto atribuído deve consultar especialistas no assunto de conformidade para entender os requisitos de migração/implantação em várias regiões. Esses requisitos afetarão significativamente as estratégias de design. As arquiteturas de referência para [aplicativos Web de várias regiões](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server) podem auxiliar no design.

> [!WARNING]
> Ao usar qualquer uma das arquiteturas de referência acima, pode ser necessário excluir elementos de dados específicos dos processos de replicação para aderir aos requisitos da soberania de dados. Isso adicionará mais uma etapa ao processo de promoção.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Ao migrar um aplicativo que deve ser implantado em várias regiões, há algumas considerações que a equipe de adoção da nuvem deve levar em conta. Essas considerações são compostas pelo design do cofre do Azure Site Recovery, design do servidor de processo/configuração, designs de largura de banda de rede e sincronização de dados.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

**Design do cofre do Azure Site Recovery:** o Azure Site Recovery é a ferramenta sugerida para replicação nativa de nuvem e sincronização de ativos digitais com o Azure. O Site Recovery replica dados sobre o ativo para um cofre do Site Recovery, que está associado a uma assinatura específica em uma região específica e em um datacenter do Azure. Ao replicar ativos para uma segunda região, um segundo cofre do Site Recovery pode ser necessário.

**Design do servidor de processo/configuração:** o Site Recovery trabalha com uma instância local de um servidor de configuração e de processo, que está associada a um único cofre do Site Recovery. Isso significa que uma segunda instância desses servidores pode precisar ser instalada no datacenter de origem para facilitar a replicação.

**Design de largura de banda de rede:** durante a replicação e a sincronização contínua, os dados binários são movidos pela rede do datacenter de origem para o cofre do Site Recovery no datacenter do Azure de destino. Esse processo consome largura de banda. A duplicação da carga de trabalho para uma segunda região duplicará a quantidade de largura de banda consumida. Quando a largura de banda é limitada ou uma carga de trabalho envolve uma grande quantidade de configuração ou de descompasso de dados, ela pode interferir no tempo necessário para concluir a migração. O mais importante é que isso poderia afetar a experiência de usuários ou aplicativos que ainda dependem da largura de banda do datacenter de origem.

**Sincronização de dados:** geralmente, o maior consumo de largura de banda vem da sincronização da plataforma de dados. Conforme definido nas arquiteturas de referência para [aplicativos Web de várias regiões](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), a sincronização de dados geralmente é necessária para manter os aplicativos alinhados. Se esse for o estado operacional desejado do aplicativo, poderá ser recomendável concluir uma sincronização entre a plataforma de dados de origem e cada uma das plataformas de nuvem antes de migrar o aplicativo e ativos da camada intermediária.
**Sincronização de dados:** geralmente, o maior consumo de largura de banda vem da sincronização da plataforma de dados. Conforme definido nas arquiteturas de referência para [aplicativos Web de várias regiões](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e [aplicativos de n camadas de várias regiões](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), a sincronização de dados geralmente é necessária para manter os aplicativos alinhados. Se esse for o estado operacional desejado do aplicativo, poderá ser recomendável concluir uma sincronização entre a plataforma de dados de origem e cada uma das plataformas de nuvem antes de migrar o aplicativo e ativos da camada intermediária.

**Recuperação de desastre do Azure para o Azure:** há uma opção alternativa que pode reduzir ainda mais a complexidade. Se as linhas do tempo e as abordagens de sincronização de dados abordarem uma implantação em duas etapas, a [recuperação de desastre do Azure para o Azure](/azure/site-recovery/azure-to-azure-architecture) poderá ser uma solução aceitável. Nesse cenário, a carga de trabalho é migrada para o primeiro datacenter do Azure usando um único cofre do Site Recovery e o design do servidor de processo ou configuração. Depois que a carga de trabalho é testada, ela pode ser recuperada para um segundo datacenter do Azure dos ativos migrados. Essa abordagem reduz o impacto dos recursos no datacenter de origem e aproveita as velocidades de transferência mais rápidas e limites de largura de banda altos disponíveis entre datacenters do Azure.

> [!NOTE]
> Essa abordagem pode aumentar o custo de curto prazo da migração, pois ela pode resultar em encargos adicionais de largura de banda de saída.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Abordar a complexidade global durante a otimização e a promoção pode exigir esforços duplicados em cada uma das regiões adicionais. Quando uma única implantação é aceitável, a duplicação de testes empresariais e de planos de mudança empresarial ainda pode ser necessária.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Ação sugerida durante o processo de otimização e promoção

**Otimização pré-teste:** o teste de automação inicial pode identificar potenciais oportunidades de otimização, como ocorre com qualquer esforço de migração. No caso de cargas de trabalho globais, é importante testar a carga de trabalho em cada região independentemente, pois alterações de configuração secundárias na rede ou no datacenter do Azure de destino poderiam afetar o desempenho.

**Planos de mudança empresarial:** para qualquer cenário de migração complexo, é recomendável que um plano de mudança empresarial seja criado para garantir a comunicação clara com relação a alterações para processos empresariais, experiências de usuário e tempo dos esforços necessários para a integração das alterações. No caso de esforços de migração global, o plano deve incluir considerações para usuários finais em cada geografia afetada.

**Teste empresarial:** em conjunto com o plano de mudança empresarial, os testes empresariais podem ser necessários em cada região para garantir o desempenho adequado e a adesão aos padrões de roteamento de rede modificados.

**Versões de pré-lançamento de promoção:** geralmente, a promoção ocorre como uma única atividade, reencaminhando o tráfego de produção para as cargas de trabalho migradas. No caso de esforços de lançamento global, é recomendável que a promoção seja entregue em versões de pré-lançamento (ou coleções de usuários predefinidas). Isso permite que a equipe de estratégia da nuvem e a equipe de adoção da nuvem observem melhor o desempenho e melhorem o suporte aos usuários em cada região. As versões de pré-lançamento de promoção geralmente são controladas no nível da rede por meio da alteração do roteamento de intervalos de IP específicos desde os ativos de carga de trabalho de origem até os ativos recém-migrados. Depois que uma coleção especificada de usuários finais tiver sido migrada, o próximo grupo poderá ser reencaminhado.

**Otimização da versão de pré-lançamento:** um dos benefícios das versões de pré-lançamento de promoção é que isso possibilita observações mais detalhadas e otimização adicional dos ativos implantados. Após um breve período de uso de produção pela primeira versão de pré-lançamento, será sugerido outro refinamento dos ativos migrados, quando permitido pelos procedimentos de operação de TI.

## <a name="next-steps"></a>Próximas etapas

Um ponto de complexidade separado, geralmente relacionado a várias regiões, é a necessidade de se preparar para a migração de [vários datacenters](./multiple-datacenters.md). Embora seja semelhante por natureza, essa complexidade lida com o volume de ativos a ser migrado ao mover vários datacenters para a nuvem.

> [!div class="nextstepaction"]
> [Migrar vários datacenters](./multiple-datacenters.md)
