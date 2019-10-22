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
ms.openlocfilehash: f5a2b84fead3adef17767f99d4079ac54fb421ea
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683616"
---
# <a name="inventory-and-visibility-in-cloud-management"></a>Inventário e visibilidade no gerenciamento de nuvem

O gerenciamento operacional tem uma clara dependência dos dados. O gerenciamento consistente exige uma compreensão clara do que é gerenciado (inventário) e de como essas cargas de trabalho e ativos gerenciados mudam ao longo do tempo (visibilidade). Juntos, a clareza do inventário e da visibilidade capacitam a equipe a gerenciar o ambiente com eficiência. Todas as outras atividades de gerenciamento operacional e processos se baseiam nessas duas áreas de informações.

Algumas frases clássicas sobre a importante das medições definem o Tom deste artigo: gerenciar o que importa. Você só pode gerenciar o que pode medir. Se você não puder medir, talvez não seja importante. A disciplina de inventário e visibilidade baseia-se nessas frases de atemporal. Antes de estabelecer os processos de gerenciamento operacional, é importante coletar dados e criar o nível certo de visibilidade para as equipes certas.

## <a name="common-customer-challenges"></a>Desafios comuns do cliente

Quando os processos de inventário e visibilidade não são aplicados consistentemente, as equipes de gerenciamento operacional sofrem com um grande volume de interrupções de negócios, tempo mais longo para recuperação e maiores quantidades de esforço necessário para solucionar problemas e fazer triagem. Conforme as alterações afetam os aplicativos de prioridade mais alta e um número maior de ativos, cada uma dessas métricas aumenta ainda mais rapidamente.

Esses desafios se originam de um pequeno número de perguntas que só podem ser respondidas por meio de dados/telemetria consistentes:

- Como o desempenho do estado atual se desvia da telemetria de desempenho operacional padrão?
- Quais ativos estão causando interrupções de negócios no nível de carga de trabalho?
- Quais ativos devem ser corrigidos para retornar ao desempenho aceitável desse processo de negócios/carga de trabalho?
- Quando o desvio foi iniciado? Qual foi o gatilho?
- Quais alterações foram feitas nos ativos subjacentes? Por quem?
- As alterações eram intencionais? Detecção?
- Como as alterações afetam a telemetria de desempenho?

Isso é difícil, se não for impossível responder a essas perguntas sem uma fonte avançada e centralizada para dados de logs e telemetria. Para habilitar o gerenciamento de nuvem, o serviço de linha de base deve primeiro começar com a definição dos processos para garantir a configuração consistente necessária para centralizar os dados. Esses processos devem capturar como a configuração irá impor a coleta de dados para dar suporte aos componentes de inventário e visibilidade na próxima seção.

## <a name="components-of-inventory-and-visibility"></a>Componentes de inventário e visibilidade

A criação de visibilidade em qualquer plataforma de nuvem requer alguns componentes principais:

1. Responsabilidade e visibilidade
2. Levantamento
3. Log central
4. Controle de alterações
5. Telemetria de desempenho

### <a name="responsibility-and-visibility"></a>Responsabilidade e visibilidade

Ao estabelecer compromissos para cada carga de trabalho, a [responsabilidade do gerenciamento](./commitment.md#management-responsibility) é um fator-chave. A responsabilidade delegada cria uma necessidade de visibilidade delegada. A primeira etapa para o inventário e a visibilidade é garantir que as partes responsáveis tenham acesso aos dados corretos. Antes de implementar todas as ferramentas nativas de nuvem para visibilidade, verifique se cada ferramenta de monitoramento foi configurada com o acesso e o escopo adequados para cada equipe de operações.

### <a name="inventory"></a>Levantamento

Se ninguém sabe que um ativo existe, é muito difícil para o ativo ser gerenciado. Antes que um ativo ou carga de trabalho possa ser gerenciado, ele deve ser inventariado e classificado. A primeira etapa técnica para operações estáveis é a validação do inventário e da classificação desse inventário.

### <a name="central-logging"></a>Log central

O registro em log centralizado é essencial para a visibilidade exigida por equipes de gerenciamento de operações diárias. Todos os ativos implantados na nuvem devem gravar logs em um local central. No Azure, esse local central é o log Analytics. A centralização dos relatórios de unidades de registro em relação ao gerenciamento de alterações, à integridade do serviço, à configuração e à maioria dos outros aspectos das operações de ti.

Impor o uso consistente de log central é a primeira etapa para operações reproduzíveis consistentes. A imposição pode ser realizada por meio da política corporativa. No entanto, quando uma possível imposição deve ser automatizada para garantir a consistência.

### <a name="change-tracking"></a>Controle de alterações

A alteração é a única constante em um ambiente de tecnologia. A conscientização e a compreensão das alterações em várias cargas de trabalho são essenciais para operações confiáveis. Qualquer solução de gerenciamento de nuvem deve incluir um meio de entender o quando, como e por que as mudanças técnicas. Sem esses pontos de dados, os esforços de correção são significativamente prejudicados.

### <a name="performance-telemetry"></a>Telemetria de desempenho

Os compromissos comerciais relativos ao gerenciamento de nuvem são orientados por dados. Para manter os compromissos adequadamente, a equipe de operações de nuvem deve primeiro compreender a telemetria em relação à estabilidade, ao desempenho e às operações da carga de trabalho e aos ativos que dão suporte à carga de trabalho.

A integridade e as operações contínuas da rede, do DNS, dos sistemas operacionais e de outros aspectos fundamentais do ambiente são pontos de dados críticos que fatoram na integridade geral de qualquer carga de trabalho.

## <a name="processes"></a>Processos

Talvez mais importante do que os recursos da plataforma de gerenciamento de nuvem, os processos de gerenciamento de nuvem perceberão os compromissos de operações com os negócios. Qualquer metodologia de gerenciamento de nuvem deve incluir os seguintes processos no mínimo:

- Monitoramento reativo: quando os desvios afetam as operações de negócios, quem resolve esses desvios? Quais ações são executadas para corrigir os desvios.
- Monitoramento proativo: quando os desvios são detectados, mas as operações de negócios não são afetadas, como esses desvios são resolvidos e por quem?
- Relatório de compromisso: como a adesão à empresa confirmada se comunica com os participantes da empresa?
- Análises orçamentárias: Qual é o processo para revisar esses compromissos em relação aos custos orçados? Qual é o processo para ajustar a solução implantada ou os compromissos para criar o alinhamento?
- Caminhos de escalonamento: quais caminhos de escalonamento estão disponíveis quando qualquer um dos processos acima não atende às necessidades dos negócios?

Há vários outros processos relacionados ao inventário e à visibilidade. A lista acima foi projetada para provoquem pensados entre a equipe de operações. Responder a essas perguntas desenvolverá alguns dos processos necessários. Ele provavelmente também disparará novas perguntas mais aprofundadas.

## <a name="responsibilities"></a>Consiste

Ao desenvolver processos para monitoramento operacional, é igualmente importante determinar as responsabilidades para a operação diária e o suporte regular de cada processo.

Em uma organização de ti central, ele forneceria o conhecimento operacional. A empresa seria consultiva por natureza, ao corrigir problemas.
Em um Cloud Center da organização de excelência, as operações de negócios forneceriam a experiência e a responsabilidade de gerenciamento desses processos. Ele se concentraria na automação e no suporte das equipes, pois operam o ambiente.

Mas essas são as responsabilidades comuns. As organizações geralmente exigem uma mistura de responsabilidades para atender aos compromissos de negócios.

## <a name="acting-on-inventory-and-visibility"></a>Atuando no inventário e na visibilidade

Independentemente da plataforma de nuvem, os cinco componentes de inventário e visibilidade são usados para impulsionar a maioria dos processos operacionais. Todas as disciplinas subsequentes serão criadas nos dados que estão sendo capturados. Os artigos a seguir nesta série descreverão maneiras de agir sobre esses dados e integrar outras fontes de dados.

### <a name="sharing-visibility"></a>Visibilidade do compartilhamento

Os dados sem ação produzem pouco retorno. O gerenciamento de nuvem pode se expandir além de ferramentas e processos nativos da nuvem. Para acomodar processos mais amplos, uma linha de base de gerenciamento de nuvem pode precisar ser aprimorada para incluir relatórios, integração de gerenciamento de serviços de ti ou centralização de dados. O gerenciamento de nuvem pode precisar incluir um ou mais dos itens a seguir durante várias fases de maturidade operacional.

### <a name="reporting"></a>Relatório

Processos offline e comunicação sobre compromissos com os participantes de negócios geralmente exigem relatórios. Relatórios de autoatendimento ou relatórios periódicos podem ser um componente necessário de uma linha de base de gerenciamento aprimorado.

### <a name="it-service-management-itsm-integration"></a>Integração de ITSM (gerenciamento de serviços de ti)

A integração de ITSM é geralmente o primeiro exemplo de atuar em inventário e visibilidade. Quando os desvios dos padrões de desempenho esperados surgirem, a integração do ITSM usará alertas da plataforma de nuvem para disparar tíquetes em uma ferramenta de gerenciamento de serviços separada para disparar atividades de correção. Alguns modelos operacionais podem exigir integração de ITSM como um aspecto da linha de base de gerenciamento aprimorado.

### <a name="data-centralization"></a>Centralização de dados

Há uma variedade de motivos pelos quais uma empresa pode exigir vários locatários em um único provedor de nuvem. Nesses cenários, a centralização de dados é um componente necessário da linha de base de gerenciamento aprimorado para fornecer visibilidade em cada um desses locatários ou ambientes.

## <a name="next-steps"></a>Próximos passos

A conformidade operacional baseia-se em recursos de inventário aplicando a automação e os controles de gerenciamento. Veja como a [conformidade operacional](./operational-compliance.md) é mapeada para seus processos.

> [!div class="nextstepaction"]
> [Planejar a conformidade operacional](./operational-compliance.md)
