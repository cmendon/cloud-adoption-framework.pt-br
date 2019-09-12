---
title: Centro de excelência de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Descreve a formação de um CCoE (Cloud Center of Excellence).
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 9726cc5bea1d8f7852dbb8831fc211dda2f4f4f7
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906304"
---
# <a name="cloud-center-of-excellence"></a>Centro de excelência de nuvem

A agilidade comercial e técnica são os principais objetivos da maioria das organizações de ti. O Cloud Center of Excellence (CCoE) é uma função que cria um equilíbrio entre velocidade e estabilidade.

## <a name="function-structure"></a>Estrutura de função

O CCoE requer colaboração entre cada um dos seguintes recursos:

- Adoção de nuvem (especificamente arquitetos de solução)
- Estratégia de nuvem (especificamente o programa e os gerentes de projeto)
- Governança de nuvem
- Plataforma de nuvem
- Automação de nuvem

## <a name="impact-and-cultural-change"></a>Impacto e alteração cultural

Quando essa função é corretamente estruturada e com suporte, os participantes podem acelerar os esforços de inovação e de migração e, ao mesmo tempo, reduzir o custo geral da alteração e aumentar a agilidade dos negócios. Quando implementada com êxito, essa função pode produzir reduções perceptíveis no tempo de colocação no mercado. Conforme as práticas de equipe amadurecem, os aumentos nos indicadores de qualidade podem ser vistos, incluindo confiabilidade, eficiência de desempenho, segurança, facilidade de manutenção e satisfação do cliente. Esses ganhos em eficiência, agilidade e qualidade são especialmente vitais se a empresa planeja implementar esforços de migração em larga escala na nuvem ou se quiser usar a nuvem para gerar inovações associadas à diferenciação do mercado.

Quando for bem-sucedido, um modelo CCoE criará uma mudança cultural significativa nele. A premissa fundamental de uma abordagem CCoE é que ela serve como um corretor, parceiro ou representante para a empresa. Esse modelo é uma mudança de paradigma para longe da exibição tradicional de ti como uma unidade de operações ou uma camada de abstração entre os ativos de negócios e de ti.

A imagem a seguir fornece uma analogia para essa alteração cultural. Sem uma abordagem CCoE, ela tende a se concentrar em fornecer controle e responsabilidade central, agindo como os alertas em uma interseção. Quando o CCoE é bem-sucedido, o foco é a liberdade e a responsabilidade delegada, que é mais como um completo em uma interseção.

![Analogia para uma mudança de paradigma CCoE](../_images/ready/ccoe-paradigm-shift.png)

Nenhuma das abordagens ilustradas na imagem analógica acima está certa ou errada, são apenas exibições alternativas de responsabilidade e gerenciamento. Se o desejo for estabelecer um modelo de autoatendimento que permita que as unidades de negócios tomem suas próprias decisões enquanto obedecem a um conjunto de diretrizes e controles estabelecidos e repetíveis, um modelo de CCoE poderia se ajustar à estratégia de tecnologia.

## <a name="key-responsibilities"></a>Principais responsabilidades

O principal imposto da equipe de CCoE é acelerar a adoção de nuvem por meio de soluções híbridas ou nativas de nuvem.

O objetivo do CCoE é:

- Ajude a criar uma organização de ti moderna por meio de abordagens ágeis para capturar e implementar requisitos de negócios.
- Use pacotes de implantação reutilizáveis que se alinhem às políticas de segurança, conformidade e gerenciamento de serviços.
- Mantenha uma plataforma funcional do Azure em alinhamento com procedimentos operacionais.
- Examine e aprove o uso de ferramentas nativas de nuvem.
- Ao longo do tempo, padronize e automatize componentes e soluções de plataforma comumente necessários.

## <a name="meeting-cadence"></a>Cadência da reunião

O CCoE é uma função da equipe de quatro equipes de alta demanda. É importante permitir a colaboração orgânica e acompanhar o crescimento por meio de um catálogo de solução/repositório comum. Maximize as interações naturais, mas minimize as reuniões. Quando essa função amadurece, as equipes devem tentar limitar as reuniões dedicadas. A participação em reuniões recorrentes, como reuniões de lançamentos hospedadas pela equipe de adoção de nuvem, fornecerá entradas de dados. Em paralelo, uma reunião após cada plano de versão é compartilhada pode fornecer um ponto de toque mínimo para essa equipe.

## <a name="solutions-and-controls"></a>Soluções e controles

Cada membro da CCoE é tarefa com a compreensão das restrições, dos riscos e das proteções necessárias que levaram ao conjunto atual de controles de ti. Os esforços coletivo do CCoE devem transformar essa compreensão em soluções ou controles nativos (ou híbridos) da nuvem, que habilitam os resultados de negócios de autoatendimento desejados. À medida que as soluções são criadas, elas são compartilhadas com várias equipes na forma de controles ou automaçãos que servem como guardrails para vários esforços. Essas guardrails ajudam a rotear as atividades de fluxo livre de várias equipes, ao mesmo tempo em que delegam responsabilidades aos participantes em vários esforços de migração ou inovação.

Exemplos dessa transição:

| Cenário | Solução CCoE | Solução CCoE |
|---------|---------|---------|
| Provisionar um SQL Server de produção | As equipes de rede, ti e plataforma de dados provisionam vários componentes durante os dias ou até mesmo semanas. | A equipe que exige o servidor implanta uma instância de PaaS do banco de dados SQL do Azure. Como alternativa, um modelo preaprovado pode ser usado para implantar todos os ativos de IaaS na nuvem em horas. |
| Provisionar um ambiente de desenvolvimento | As equipes de rede, ti, desenvolvimento e DevOps concordam com especificações e implantam um ambiente. | A equipe de desenvolvimento define suas próprias especificações e implanta um ambiente com base no orçamento alocado. |
| Atualizar os requisitos de segurança para melhorar a proteção de dados | As equipes de rede, ti e segurança atualizam vários dispositivos de rede e VMs em vários ambientes para adicionar proteções. | As ferramentas de governança de nuvem são usadas para atualizar políticas que podem ser aplicadas imediatamente a todos os ativos em todos os ambientes de nuvem. |

## <a name="negotiations"></a>Negociações

Na raiz de qualquer esforço de CCoE, há um processo de negociação em andamento. A equipe CCoE negocia com as funções de ti existentes para reduzir o controle central. As compensações para os negócios nessa negociação são liberdade, agilidade e velocidade. O valor da compensação para equipes de ti existentes é fornecido como novas soluções. As novas soluções fornecem à equipe de ti existente um ou mais dos seguintes benefícios:

- Capacidade de automatizar problemas comuns.
- Melhorias na consistência (redução nas frustrações cotidianas).
- Oportunidade de aprender e implantar novas soluções técnicas.
- Reduções em incidentes de alta gravidade (menos correções rápidas ou respostas de imposto de pager de noite tardia).
- Capacidade de ampliar seu escopo técnico, abordando tópicos mais amplos.
- Participação em soluções de negócios de nível superior, abordando o impacto da tecnologia.
- Redução nas tarefas de manutenção de braçais.
- Aumente a automação e a estratégia de tecnologia.

No Exchange para esses benefícios, a função de ti existente pode estar negociando os valores a seguir, seja real ou percebido:

- Sensação de controle dos processos de aprovação manual.
- Sensação de estabilidade do controle de alterações.
- Sentido de segurança de trabalho desde a conclusão de tarefas ainda repetitivas necessárias.
- Sentido de consistência que vem da adesão aos fornecedores de soluções de ti existentes.

Em empresas íntegras em nuvem, esse processo de negociação é uma conversa dinâmica entre os colegas e as equipes de ti de parceria. Os detalhes técnicos podem ser complexos, mas são gerenciáveis quando compreendem o objetivo e estão em apoio aos esforços de CCoE. Quando for menor do que o de apoio, a seção a seguir sobre como habilitar o sucesso do CCoE pode ajudar a superar os bloqueadores culturais.

## <a name="enabling-ccoe-success"></a>Habilitando o êxito do CCoE

Antes de prosseguir com esse modelo, é importante validar a tolerância da empresa para uma mentalidade de crescimento e é confortável com a liberação de responsabilidades centrais. Conforme mencionado acima, a finalidade de um CCoE é o controle do Exchange para agilidade e velocidade.

Esse tipo de alteração leva tempo, experimentação e negociação. Haverá choques e definirá as retenções durante esse processo de desenvolvimento. No entanto, se a equipe continuar e não for desencorajada da experimentação, haverá uma alta probabilidade de sucesso ao melhorar a agilidade, a velocidade e a confiabilidade. Um dos maiores fatores no sucesso ou na falha de um CCoE é o suporte da liderança e das principais partes interessadas.

### <a name="key-stakeholders"></a>Principais acionistas

A liderança de ti é o primeiro e mais óbvio participante. Os gerentes de ti participarão de uma parte importante. No entanto, o suporte do CIO e de outros líderes de ti de nível executivo é necessário durante esse processo.

Menos óbvio é a necessidade de participantes comerciais. A agilidade dos negócios e o tempo de colocação no mercado são motivações-chave para a formação de CCoE. Assim, as principais partes interessadas devem ter um interesse corelevante nessas áreas. Exemplos de participantes de negócios incluem líderes de linha de negócios, executivos de finanças, executivos de operações e proprietários de produtos de negócios.

### <a name="business-stakeholder-support"></a>Suporte a parceiros comerciais

Os esforços de CCoE podem ser acelerados com o suporte dos participantes comerciais. Grande parte do foco dos esforços de CCoE é centrada em termos de fazer melhorias de longo prazo na agilidade e na velocidade dos negócios. Definir o impacto dos modelos operacionais atuais e o valor dos aprimoramentos é valioso como uma ferramenta de guia e negociação para o CCoE. A documentação dos seguintes itens é sugerida para o suporte do CCoE:

- Estabeleça um conjunto de resultados de negócios e metas que são esperadas como resultado da agilidade e da velocidade dos negócios.
- Defina claramente os pontos problemáticos criados por processos de ti atuais (como velocidade, agilidade, estabilidade e desafios de custo).
- Defina claramente o impacto histórico desses pontos problemáticos (como perda de mercado perdido, ganhos de concorrentes em recursos e funções, experiências de clientes ruins e aumentos de orçamento).
- Defina oportunidades de aprimoramento de negócios que são bloqueadas pelos pontos problemáticos e modelos operacionais atuais.
- Estabeleça cronogramas e métricas relacionados a essas oportunidades.

Esses pontos de dados não são um ataque a ele. Em vez disso, eles ajudam a CCoE a aprender com o passado e estabelecer uma pendência realista e planejar a melhoria.

**Suporte e envolvimento contínuos:** As equipes do CCoE podem demonstrar retornos rápidos em algumas áreas. No entanto, as metas de nível superior, como agilidade de negócios e tempo de colocação no mercado, podem levar muito mais tempo. Durante o desenvolvimento, há um alto risco de os CCoE serem desencorajados ou sendo desligados para se concentrar em outros esforços de ti.

Durante os seis primeiros a nove meses de esforços de CCoE, recomendamos que os participantes de negócios aloquem tempo para atender mensalmente com a liderança de ti e o CCoE. Há pouca necessidade de cerimônia formal nessas reuniões. Simplesmente lembrar os membros do CCoE e sua liderança da importância desse programa pode ir além de conduzir o sucesso do CCoE.

Além disso, recomendamos que os participantes da empresa fiquem informados sobre o progresso e os bloqueadores experientes pela equipe de CCoE. Muitos de seus esforços se parecerão minúciass técnicos. No entanto, é importante que os participantes de negócios compreendam o progresso do plano, para que possam se envolver quando a equipe perder o fluxo ou se tornar distraídos por outras prioridades.

### <a name="it-stakeholder-support"></a>Suporte do stakeholder de ti

**Suporte à visão:** Um esforço de CCoE bem-sucedido requer uma grande dose de negociação com os membros existentes da equipe de ti. Quando tudo pronto, todos eles contribuem para a solução e se sentem à vontade com a alteração. Quando esse não for o caso, alguns membros da equipe de ti existente talvez queiram manter o controle de mecanismos por vários motivos. O suporte dos participantes de ti será vital para o sucesso do CCoE quando essas situações ocorrerem. A encorajação e a reforço dos objetivos gerais do CCoE é importante para resolver os bloqueadores para a negociação adequada. Em raras ocasiões, os participantes de ti podem até mesmo precisar entrar e dividir um deadlock ou um voto associado para manter o progresso do CCoE.

**Manter foco:** Um CCoE pode ser um compromisso significativo para qualquer equipe de ti restrita por recursos. Remover arquitetos fortes de projetos de curto prazo para se concentrar em ganhos de longo prazo pode criar dificuldade para membros da equipe que não fazem parte do CCoE. É importante que a liderança de ti e os participantes de ti Fiquem concentrados no objetivo do CCoE. O suporte dos líderes de ti e dos participantes de ti é necessário para despriorizar as interrupções das operações cotidianas em favor das tarefas CCoEs.

**Criar um buffer:** A equipe do CCoE experimentará novas abordagens. Algumas dessas abordagens não se alinharão bem com as operações existentes ou restrições técnicas. Há um risco real do CCoE que está experimentando pressão ou recurso de outras equipes quando os experimentos falham. A encorajação e o armazenamento em buffer da equipe das consequências de oportunidades de aprendizado de "falha rápida" são importantes. É igualmente importante manter a equipe em uma mentalidade de crescimento, garantindo que eles estejam aprendendo com esses experimentos e encontrem soluções melhores.

## <a name="next-steps"></a>Próximas etapas

O Cloud Center of Excellence requer tanto [recursos de plataforma de nuvem](./cloud-platform.md) quanto recursos de automação de [nuvem](./cloud-automation.md). A próxima etapa é alinhar os [recursos da plataforma de nuvem](./cloud-platform.md).

> [!div class="nextstepaction"]
> [Alinhar os recursos da plataforma de nuvem](./cloud-platform.md)
