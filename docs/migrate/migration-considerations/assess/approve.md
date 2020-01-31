---
title: Aprovar alterações de arquitetura antes da migração
description: Entender a importância da aprovação antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3776f468c48e7483d884a0c6cae8654218ac1a94
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76802745"
---
# <a name="approve-architecture-changes-before-migration"></a>Aprovar alterações de arquitetura antes da migração

Durante o processo de avaliação da migração, cada carga de trabalho é avaliada, arquitetada e estimada a fim de desenvolver um futuro plano de estado para a carga de trabalho. Algumas das cargas de trabalho podem ser migradas para a nuvem sem nenhuma alteração na arquitetura. Manter uma configuração e uma arquitetura local pode reduzir o risco e simplificar o processo de migração. Infelizmente, nem todos os aplicativos podem ser executados na nuvem sem alterações na arquitetura. Quando for necessário alterar a arquitetura, este artigo poderá esclarecer a alteração e fornecer algumas orientações sobre as devidas atividades de aprovação.

## <a name="business-impact-and-approval"></a>Impacto nos negócios e aprovação

Durante a migração, é provável que ocorram algumas alterações de maneiras que afetem a empresa. Embora as alterações às vezes não possam ser evitadas, surpresas como resultado de alterações não reveladas ou não documentadas devem ser. Para manter o suporte do stakeholder durante o esforço de migração, é importante evitar surpresas. Surpreender os proprietários de aplicativos ou stakeholders de empresas pode retardar ou interromper um esforço de adoção de nuvem.

Antes da migração, é importante preparar o proprietário de negócios da carga de trabalho para quaisquer alterações que possam afetar os processos de negócios, como alterações em:

- Contratos de nível de serviço.
- Padrões de acesso ou requisitos de segurança que afetam o usuário final.
- Práticas de retenção de dados.
- Desempenho do aplicativo básico.

Mesmo quando é possível migrar uma carga de trabalho com alterações mínimas ou sem nenhuma mudança, ainda assim pode haver um impacto para os negócios. Os processos de replicação podem tornar mais lento o desempenho dos sistemas de produção. As mudanças no ambiente na preparação para a migração têm o potencial de causar limitações de roteamento ou de desempenho da rede. Há vários outros impactos que podem resultar da replicação, do preparo ou de atividades de promoção.

As atividades de aprovação regulares podem ajudar a minimizar ou evitar surpresas em virtude de alterações ou impactos comerciais voltados ao desempenho. A equipe de adoção da nuvem deve executar um processo de aprovação de alterações ao final do procedimento de avaliação, antes de iniciar o processo de migração.

## <a name="existing-culture"></a>Cultura existente

Suas equipes de TI provavelmente têm mecanismos para gerenciar alterações envolvendo ativos locais. Geralmente, esses mecanismos são controlados por processos de gerenciamento de alterações baseados em ITIL (Biblioteca de Infraestrutura de Tecnologia da Informação). Em muitas migrações empresariais, esses processos envolvem um CAB (Comitê de aconselhamento sobre mudanças) que é responsável por revisar, documentar e aprovar todas as RFC (solicitações de alteração) relacionadas a TI.

O CAB costuma incluir especialistas de várias equipes de TI e de negócios, oferecendo uma série de perspectivas e uma análise detalhada para todas as alterações relacionadas à TI. Um processo de aprovação do CAB é uma forma comprovada de reduzir os riscos e minimizar o impacto nos negócios das alterações que envolvem cargas de trabalho gerenciadas por operações de TI.

## <a name="technical-approval"></a>Aprovação técnica

A preparação organizacional para a aprovação da alteração técnica está entre os motivos mais comuns para as falhas de migração para a nuvem. Mais projetos são interrompidos pela série de aprovações técnicas do que por déficits em uma plataforma de nuvem. A preparação da organização para as alterações técnicas é um requisito importante para o sucesso da migração. A seguir estão algumas melhores práticas para garantir que a organização esteja pronta para a aprovação técnica.

### <a name="itil-change-advisory-board-challenges"></a>Desafios do Comitê de aconselhamento sobre mudanças da ITIL

Todas as abordagens de gerenciamento de alterações têm seus próprios conjuntos de controles e processos de aprovação. A migração é uma série de alterações contínuas que começam com um alto grau de ambiguidade e desenvolvem maior clareza ao longo da execução. Assim, a migração é mais bem controlada por abordagens de gerenciamento de alterações baseadas na agilidade, com a equipe de estratégia da nuvem atuando como proprietária do produto.

Contudo, a escala e a frequência da alteração durante a migração para a nuvem não se ajustam à natureza dos processos da ITIL. Os requisitos para uma aprovação do CAB podem colocar em risco o sucesso de uma migração, interrompendo ou retardando o esforço. Além disso, nas etapas iniciais da migração, a ambiguidade é alta e o conhecimento sobre o assunto tende a ser baixo. Em geral, nas primeiras versões ou migrações de carga de trabalho a equipe de adoção da nuvem está em modo de aprendizado. Portanto, pode ser difícil para a equipe fornecer os tipos de dados necessários para passar pela aprovação do CAB.

As melhores práticas a seguir podem ajudar o CAB a manter um grau de conforto durante a migração sem se tornar um bloqueador incômodo.

### <a name="standardize-change"></a>Padronizar a alteração

É tentador para uma equipe de adoção da nuvem considerar decisões de arquitetura detalhadas para cada carga de trabalho que está sendo migrada para a nuvem. É igualmente tentador usar a migração para a nuvem como catalizador para refatorar decisões de arquitetura anteriores. Para organizações que estão migrando algumas centenas de VMs ou algumas dezenas de cargas de trabalho, ambas as abordagens podem ser devidamente gerenciadas. Ao migrar um datacenter com 1.000 ativos ou mais, cada uma dessas abordagens é considerada um antipadrão de alto risco que reduz significativamente a probabilidade de sucesso. Modernizar, Refatorar e rearquitetar cada aplicativo requer diversos conjuntos de habilidades e uma variedade significativa de alterações, e essas tarefas criam dependências em esforços humanos em escala. Cada uma dessas dependências aumenta o risco dos esforços de migração.

O artigo sobre [racionalização do estado digital](../../../digital-estate/rationalize.md) debate a agilidade e o impacto na redução do tempo de suposições básicas ao racionalizar um estado digital. Há um benefício adicional na padronização das alterações. Ao escolher uma abordagem de racionalização padrão para controlar os esforços de migração, o Comitê de aconselhamento da nuvem ou proprietário do produto pode revisar e aprovar a aplicação de uma alteração a uma longa lista de cargas de trabalho. Isso reduz a aprovação técnica de cada carga de trabalho para aquelas que exigem uma alteração significativa na arquitetura para serem compatíveis com a nuvem.

### <a name="clarify-expectations-and-roles-of-approvers"></a>Esclarecer expectativas e funções de aprovadores

Antes que a primeira carga de trabalho seja avaliada, a equipe de estratégia da nuvem deve documentar e comunicar as expectativas de todos os envolvidos na aprovação da alteração. Essa atividade simples poderá evitar atrasos dispendiosos quando a equipe de adoção da nuvem estiver totalmente envolvida.

### <a name="seek-approval-early"></a>Buscar aprovação desde o início

Quando possível, as alterações técnicas devem ser detectadas e documentadas durante o processo de avaliação. Independentemente dos processos de aprovação, a equipe de adoção da nuvem deve envolver os aprovadores desde o início. Quanto antes começar essa aprovação da alteração, menor será a probabilidade de que um processo de aprovação bloqueie as atividades de migração.

## <a name="next-steps"></a>Próximos passos

Com a ajuda das melhores práticas, deverá ficar mais fácil integrar as devidas aprovações de baixo risco aos esforços de migração. Depois que as alterações a uma carga de trabalho forem aprovadas, a equipe de adoção da nuvem estará pronta para [migrar as cargas de trabalho](../migrate/index.md).

> [!div class="nextstepaction"]
> [Migrar cargas de trabalho](../migrate/index.md)
