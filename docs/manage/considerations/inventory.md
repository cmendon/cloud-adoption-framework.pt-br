---
title: Inventário e visibilidade – gerenciamento de nuvem e operações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Inventário e visibilidade – gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5b38b5d52ee5151a2ccd696f0049a9feea0d21a0
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752810"
---
# <a name="inventory-and-visibility-in-cloud-management"></a>Inventário e visibilidade no gerenciamento de nuvem

O gerenciamento operacional tem uma clara dependência dos dados. O gerenciamento consistente requer uma compreensão sobre o que é gerenciado (inventário) e como essas cargas de trabalho e ativos gerenciados mudam ao longo do tempo (visibilidade). Limpar informações sobre o inventário e a visibilidade ajudam a equipe a gerenciar o ambiente com eficiência. Todas as outras atividades de gerenciamento operacional e processos se baseiam nessas duas áreas.

Algumas frases clássicas sobre a importância das medições definem o Tom deste artigo:

- Gerencie o que importa.
- Você só pode gerenciar o que pode medir.
- Se você não puder medir, talvez não seja importante.

A disciplina de inventário e visibilidade baseia-se nessas frases de atemporal. Antes de poder estabelecer efetivamente os processos de gerenciamento operacional, é importante coletar dados e criar o nível certo de visibilidade para as equipes certas.

## <a name="common-customer-challenges"></a>Desafios comuns do cliente

A menos que os processos de inventário e visibilidade sejam aplicados consistentemente, as equipes de gerenciamento operacional podem sofrer um grande volume de interrupções de negócios, mais tempo para recuperação e maiores quantidades de esforço necessário para solucionar problemas e fazer a triagem. Conforme as alterações afetam negativamente os aplicativos de prioridade mais alta e um número maior de ativos, cada uma dessas métricas aumenta ainda mais rapidamente.

Esses desafios se originam de um pequeno número de perguntas que podem ser respondidas somente por meio de dados/telemetria consistentes:

- Como o desempenho do estado atual se desvia da telemetria de desempenho operacional padrão?
- Quais ativos estão causando interrupções de negócios no nível de carga de trabalho?
- Quais ativos devem ser corrigidos para retornar ao desempenho aceitável dessa carga de trabalho ou processo comercial?
- Quando o desvio foi iniciado? Qual foi o gatilho?
- Quais alterações foram feitas nos ativos subjacentes? Por quem?
- As alterações eram intencionais? Detecção?
- Como as alterações afetam a telemetria de desempenho?

É difícil, se não impossível, responder a essas perguntas sem uma fonte avançada e centralizada para dados de logs e telemetria. Para habilitar o gerenciamento de nuvem garantindo a configuração consistente necessária para centralizar os dados, o serviço de linha de base deve primeiro começar pela definição dos processos. Os processos devem capturar como tal configuração impõe a coleta de dados para dar suporte aos componentes de inventário e visibilidade na próxima seção.

## <a name="components-of-inventory-and-visibility"></a>Componentes de inventário e visibilidade

A criação de visibilidade em qualquer plataforma de nuvem requer alguns componentes principais:

- Responsabilidade e visibilidade
- Inventário
- Log central
- Controle de alterações
- Telemetria de desempenho

### <a name="responsibility-and-visibility"></a>Responsabilidade e visibilidade

Quando você estabelece compromissos para cada carga de trabalho, a [responsabilidade de gerenciamento](./commitment.md#management-responsibility) é um fator fundamental. A responsabilidade delegada cria uma necessidade de visibilidade delegada. A primeira etapa para o inventário e a visibilidade é garantir que as partes responsáveis tenham acesso aos dados corretos. Antes de implementar todas as ferramentas nativas de nuvem para visibilidade, verifique se cada ferramenta de monitoramento foi configurada com o acesso e o escopo adequados para cada equipe de operações.

### <a name="inventory"></a>Inventário

Se ninguém sabe que um ativo existe, é difícil gerenciar o ativo. Antes que um ativo ou carga de trabalho possa ser gerenciado, ele deve ser inventariado e classificado. A primeira etapa técnica para operações estáveis é a validação do inventário e da classificação desse inventário.

### <a name="central-logging"></a>Log central

O registro em log centralizado é essencial para a visibilidade necessária dia a dia pelas equipes de gerenciamento de operações. Todos os ativos implantados na nuvem devem gravar logs em um local central. No Azure, esse local central é o log Analytics. A centralização de unidades de registro em log relata sobre o gerenciamento de alterações, a integridade do serviço, a configuração e a maioria dos outros aspectos das operações de ti.

Impor o uso consistente do log central é a primeira etapa para estabelecer operações repetíveis. A imposição pode ser realizada por meio da política corporativa. Quando possível, no entanto, a imposição deve ser automatizada para garantir a consistência.

### <a name="change-tracking"></a>Controle de alterações

A alteração é a única constante em um ambiente de tecnologia. A conscientização e a compreensão das alterações em várias cargas de trabalho são essenciais para operações confiáveis. Qualquer solução de gerenciamento de nuvem deve incluir um meio de entender o quando, como e por que as mudanças técnicas. Sem esses pontos de dados, os esforços de correção são significativamente prejudicados.

### <a name="performance-telemetry"></a>Telemetria de desempenho

Os compromissos comerciais sobre o gerenciamento de nuvem são orientados por dados. Para manter os compromissos adequadamente, a equipe de operações de nuvem deve primeiro compreender a telemetria sobre a estabilidade, o desempenho e as operações da carga de trabalho e os ativos que dão suporte à carga de trabalho.

A integridade e as operações contínuas da rede, do DNS, dos sistemas operacionais e de outros aspectos fundamentais do ambiente são pontos de dados críticos que fatoram na integridade geral de qualquer carga de trabalho.

## <a name="processes"></a>Processos

Talvez mais importante do que os recursos da plataforma de gerenciamento de nuvem, os processos de gerenciamento de nuvem perceberão os compromissos de operações com os negócios. Qualquer metodologia de gerenciamento de nuvem deve incluir, no mínimo, os seguintes processos:

- **Monitoramento reativo:** Quando os desvios afetam negativamente as operações de negócios, quem resolve esses desvios? Quais ações são executadas para corrigir os desvios?
- **Monitoramento proativo:** Quando os desvios são detectados, mas as operações de negócios não são afetadas, como esses desvios são resolvidos e por quem?
- **Relatório de compromisso:** Como a adesão ao compromisso de negócios se comunica com os participantes da empresa?
- **Revisões orçamentárias:** Qual é o processo para revisar esses compromissos em relação aos custos orçados? Qual é o processo para ajustar a solução implantada ou os compromissos para criar o alinhamento?
- **Caminhos de escalonamento:** Quais caminhos de escalonamento estão disponíveis quando algum dos processos anteriores falha ao atender às necessidades dos negócios?

Há vários outros processos relacionados ao inventário e à visibilidade. A lista anterior foi projetada para provoquem pensar na equipe de operações. Responder a essas perguntas ajudará a desenvolver alguns dos processos necessários, bem como a possibilidade de disparar novas perguntas mais aprofundadas.

## <a name="responsibilities"></a>Responsabilidades

Quando você estiver desenvolvendo processos para monitoramento operacional, é igualmente importante determinar as responsabilidades da operação diária e o suporte regular de cada processo.

Em uma organização de ti central, ele forneceria o conhecimento operacional. A empresa seria consultiva por natureza, quando os problemas exigirem correção.

Em um Cloud Center da organização de excelência, as operações de negócios forneceriam a experiência e a responsabilidade de gerenciamento desses processos. Ele se concentraria na automação e no suporte das equipes, pois operam o ambiente.

Mas essas são as responsabilidades comuns. As organizações geralmente exigem uma mistura de responsabilidades para atender aos compromissos de negócios.

## <a name="act-on-inventory-and-visibility"></a>Aja no inventário e na visibilidade

Independentemente da plataforma de nuvem, os cinco componentes de inventário e visibilidade são usados para impulsionar a maioria dos processos operacionais. Todas as disciplinas subsequentes serão criadas nos dados que estão sendo capturados. Os próximos artigos desta série descrevem maneiras de agir sobre esses dados e integrar outras fontes de dados.

### <a name="share-visibility"></a>Visibilidade do compartilhamento

Os dados sem ação produzem pouco retorno. O gerenciamento de nuvem pode se expandir além de ferramentas e processos nativos da nuvem. Para acomodar processos mais amplos, uma linha de base de gerenciamento de nuvem pode precisar ser aprimorada para incluir relatórios, integração de gerenciamento de serviços de ti ou centralização de dados. O gerenciamento de nuvem pode precisar incluir um ou mais dos itens a seguir durante várias fases de maturidade operacional.

### <a name="report"></a>Relate

Processos offline e comunicação sobre compromissos com os participantes de negócios geralmente exigem relatórios. Relatórios de autoatendimento ou relatórios periódicos podem ser um componente necessário de uma linha de base de gerenciamento aprimorado.

### <a name="it-service-management-itsm-integration"></a>Integração de ITSM (Gerenciamento de serviços de TI)

A integração de ITSM é geralmente o primeiro exemplo de atuar em inventário e visibilidade. Quando surgem os desvios dos padrões de desempenho esperados, a integração de ITSM usa alertas da plataforma de nuvem para disparar tíquetes em uma ferramenta de gerenciamento de serviços separada para disparar atividades de correção. Alguns modelos operacionais podem exigir integração de ITSM como um aspecto da linha de base de gerenciamento aprimorado.

### <a name="data-centralization"></a>Centralização de dados

Há uma variedade de motivos pelos quais uma empresa pode exigir vários locatários em um único provedor de nuvem. Nesses cenários, a centralização de dados é um componente necessário da linha de base de gerenciamento avançado, pois pode fornecer visibilidade em cada um desses locatários ou ambientes.

## <a name="next-steps"></a>Próximos passos

A conformidade operacional baseia-se em recursos de inventário aplicando a automação e os controles de gerenciamento. Veja como a [conformidade operacional](./operational-compliance.md) é mapeada para seus processos.

> [!div class="nextstepaction"]
> [Planejar a conformidade operacional](./operational-compliance.md)
