---
title: Lista de verificação de escopo expandido da migração na nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Lista de verificação de escopo expandido da migração na nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/19/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4daf4b01a2fde83de1040f224b8096475a24fe60
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71224362"
---
# <a name="expanded-scope-for-cloud-migration"></a>Escopo expandido para migração na nuvem

O [guia de migração do Azure](../azure-migration-guide/index.md) na Cloud Adoption Framework é o ponto de partida sugerido para leitores interessados em uma migração de novo host para o Azure, também conhecida como migração "lift-and-shift". Esse guia o orienta por uma série de pré-requisitos, ferramentas e abordagens para a migração de máquinas virtuais para a nuvem.

Embora este guia seja uma linha de base eficaz para familiarizar-se com este tipo de migração, ele faz várias suposições. Essas suposições alinham o guia com um grande percentual de leitores da Cloud Adoption Framework fornecendo uma abordagem simplificada a migrações. Esta seção da Cloud Adoption Framework aborda alguns cenários de migração de escopo expandido que ajudam a conduzir os esforços quando essas suposições não se aplicam.

## <a name="cloud-migration-expanded-scope-checklist"></a>Lista de verificação de escopo expandido da migração na nuvem

A lista de verificação a seguir descreve as áreas comuns de complexidade que podem exigir a expansão do escopo da migração para além do [guia de migração do Azure](../azure-migration-guide/index.md).

- **Alterações no escopo orientadas pelos negócios:**
  - [Balanceando o portfólio](./balance-the-portfolio.md)
  - [Dar suporte a mercados globais](../../decision-guides/regions/index.md)
  - Consciência de custos durante uma migração *(em breve no 3º trimestre de 2019)*
- **Alterações no escopo orientadas pela cultura:**
  - Processos de aprovação e gerenciamento de alterações *(em breve no 3º trimestre de 2019)*
  - Preparação executiva *(em breve no 3º trimestre de 2019)*
  - [Prontidão das habilidades](./suggested-skills.md)
  - Alinhando suporte (parceiro, serviços e suporte) *(em breve no 3º trimestre de 2019)*
- **Alterações no escopo orientadas pela estratégia técnica:**
  - Restrições existentes do datacenter *(em breve no 3º trimestre de 2019)*
  - Como fazer migração em escala – alto volume ou velocidade de migrações *(em breve no 3º trimestre de 2019)*
  - [Vários datacenters](./multiple-datacenters.md)
  - [Requisitos de dados ultrapassam a capacidade da rede](./network-capacity-exceeded.md)
  - Documentação de solução de e gerenciamento de alterações *(em breve no 3º trimestre de 2019)*
  - [Estratégia de governança ou conformidade](./governance-or-compliance.md)
- **Alterações de escopo específicas da carga de trabalho:**
  - Arquitetar cargas de trabalho para resiliência *(em breve no 3º trimestre de 2019)*
  - Alinhar a migração a padrões de aplicativo *(em breve no 3º trimestre de 2019)*

Se qualquer uma dessas complexidades estiver alinhada com seu cenário, esta seção da Cloud Adoption Framework provavelmente fornecerá o tipo de orientação necessária para alinhar adequadamente o escopo nos processos de migração.

Cada um desses cenários é abordado pelos vários artigos nesta seção da estrutura de adoção de nuvem.

## <a name="scope-options-explained"></a>Explicação de opções de escopo

Para ajudar você a entender cada cenário de expansão de escopo, a lista a seguir resumirá brevemente os títulos usados na lista de verificação acima.

### <a name="business-driven-scope-changes"></a>Alterações no escopo orientadas pelos negócios

- **Balanceamento do portfólio de adoção da nuvem:** A equipe de estratégia de nuvem está interessada em investir mais pesadamente em uma migração (nova hospedagem de cargas de trabalho existentes e aplicativos com um mínimo de modificações) ou inovação (refatoração ou recriação dessas cargas de trabalho e aplicativos que usam tecnologia de nuvem moderna). Muitas vezes, um equilíbrio entre as duas prioridades é o segredo para o sucesso. Neste guia, o tópico de balanceamento do portfólio de adoção da nuvem é comum, abordado em cada um dos processos de migração.
- **Dar suporte a mercados globais:** a empresa opera em várias regiões geográficas com requisitos de soberania de dados díspares. Para atender a esses requisitos, é preciso levar em conta fatores adicionais na análise de pré-requisitos e na distribuição de ativos durante a migração.

### <a name="culture-driven-scope-changes"></a>Alterações no escopo orientadas pela cultura

- **Processos de aprovação e gerenciamento de alterações:** quando a cultura da sua organização é complexa, muito estruturada em matrizes ou silos, os processos relacionados ao gerenciamento de alterações e aprovações tornam-se um desafio. Orientação sobre como gerenciar essa complexidade pode ser encontrada nos processos de avaliação, migração e otimização.
- **Preparação executiva:** os níveis adequados de suporte executivo e liderança são críticos para o sucesso de um esforço de migração. Se a equipe executiva não estiver pronta para participar, o suporte provavelmente não participará também. Essa complexidade é tratada durante os processos de pré-requisito e avaliação.
- **Prontidão das habilidades:** quando a equipe de adoção de nuvem ou outras equipes de suporte não estão prontas para execução, elas podem aumentar rapidamente a complexidade de todo o esforço de migração. Esse desafio é tratado durante cada um dos processos de migração em uma página específica na preparação de habilidades.
- **Alinhando suporte (opções de parceiro de serviço e suporte):** dentro de cada uma aos processos descritos, há maneiras de um parceiro, de serviços do fornecedor de nuvem e do suporte do fornecedor de nuvem ajudar na execução. Em cada uma das seções de processos, uma página sobre alinhamento de suporte discutirá as opções em mais detalhes.

### <a name="technical-strategy-driven-scope-changes"></a>Alterações no escopo orientadas pela estratégia técnica

- **Restrições existentes do datacenter:** as empresas frequentemente optam por migrar para a nuvem porque a capacidade, a velocidade e a estabilidade de um datacenter existente não são mais satisfatórias. Essas mesmas restrições adicionam complexidade ao processo de migração, exigindo um planejamento adicional durante os processos de avaliação e migração.
- **Como fazer migração em escala:** migrações que excedem 2 mil ativos provavelmente serão executadas em restrições que exigem planejamento adicional e uma abordagem disciplinada à execução. Os processos de avaliação e migração são ajustados para considerar a complexidade de escala.
- **Vários datacenters:** a migração de vários data centers adiciona muita complexidade. Durante os processos de avaliação, migração, otimização e gerenciamento, são discutidas considerações adicionais.
- **Documentação de solução e gerenciamento de alterações:** grandes inventários de acervo digital, arquiteturas da solução complexas, dívida técnica de longa duração e interdependências podem criar uma complexidade que deve ser tratada durante os processos de avaliação, migração e otimização.
- **Estratégia de governança ou conformidade:** quando governança e conformidade são vitais para o sucesso de uma migração, é necessário alinhamento adicional entre equipes de Governança de TI e a equipe de adoção de nuvem.

### <a name="workload-specific-scope-changes"></a>Alterações de escopo específicas da carga de trabalho

- **Arquitetar cargas de trabalho para resiliência:** princípios comuns de design de nuvem podem ajudar a preparar as cargas de trabalho críticas para permitir maior resiliência. Este artigo explicará o impacto a um processo de migração quando a resiliência é um requisito de carga de trabalho. Também compartilha alguns princípios comuns a serem incluídos na configuração do ambiente geral para melhorar a resiliência para o ambiente.
- **Alinhar a migração a padrões de aplicativo:** o padrão de migração de uma carga de trabalho pode afetar o caminho de migração escolhido. Este artigo descreve algumas alterações de escopo que seriam integradas no nível do item de trabalho de uma lista de pendências de migração para refletir diferentes abordagens a uma migração por carga de trabalho.

## <a name="next-steps"></a>Próximas etapas

Navegue no sumário à esquerda para abordar necessidades específicas ou alterações de escopo. Como alternativa, a primeira melhoria de escopo na lista, [balanceamento do portfólio](./balance-the-portfolio.md), é um bom ponto de partida ao examinar esses cenários.

> [!div class="nextstepaction"]
> [Balanceando o portfólio](./balance-the-portfolio.md)
