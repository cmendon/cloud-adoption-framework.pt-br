---
title: Aprovar alterações de arquitetura antes da migração
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Compreendendo a importância da aprovação antes da migração
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: cdc6abe2be94bb0d91047d4d64a0774bac6a8e0e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549208"
---
# <a name="approve-architecture-changes-before-migration"></a>Aprovar alterações de arquitetura antes da migração

Durante o processo de avaliação da migração, cada carga de trabalho é avaliada, arquitetada e estimada para desenvolver um plano de estado futuro para a carga de trabalho. Algumas cargas de trabalho podem ser migradas para a nuvem sem alteração na arquitetura. Manter a configuração e a arquitetura locais pode reduzir o risco e simplificar o processo de migração. Infelizmente, nem todo aplicativo pode ser executado na nuvem sem alterações na arquitetura. Quando as alterações de arquitetura são necessárias, este artigo pode ajudar a classificar a alteração e pode fornecer algumas diretrizes sobre as atividades de aprovação adequadas.

## <a name="business-impact-and-approval"></a>Impacto e aprovação nos negócios

Durante a migração, é provável que algumas coisas sejam alteradas de maneiras que afetem os negócios. Embora as alterações às vezes não possam ser evitadas, surpresas como resultado de alterações não reveladas ou não documentadas devem ser. Para manter o suporte do stakeholder durante o esforço de migração, é importante evitar surpresas. Os proprietários de aplicativos surpreendentes ou os participantes de negócios podem reduzir ou interromper um esforço de adoção de nuvem.

Antes da migração, é importante preparar o proprietário de negócios da carga de trabalho para quaisquer alterações que possam afetar os processos de negócios, como alterações em:

- Contratos de nível de serviço.
- Padrões de acesso ou requisitos de segurança que afetam o usuário final.
- Práticas de retenção de dados.
- Desempenho do aplicativo principal.

Mesmo quando uma carga de trabalho pode ser migrada com pouca ou nenhuma alteração, ainda pode haver um impacto nos negócios. Os processos de replicação podem reduzir o desempenho dos sistemas de produção. As alterações no ambiente em preparação para a migração têm o potencial de causar limitações de desempenho de rede ou roteamento. Há muitos impactos adicionais que podem resultar de atividades de replicação, preparo ou promoção.

Atividades de aprovação regulares podem ajudar a minimizar ou evitar surpresas como resultado de alterações ou impactos comerciais controlados por desempenho. A equipe de adoção de nuvem deve executar um processo de aprovação de alteração no final do processo de avaliação, antes de iniciar o processo de migração.

## <a name="existing-culture"></a>Cultura existente

Suas equipes de ti provavelmente têm mecanismos existentes para gerenciar alterações envolvendo seus ativos locais. Normalmente, esses mecanismos são regidos por processos tradicionais de gerenciamento de alterações baseados em biblioteca de infraestrutura de tecnologia da informação (baseado em ITIL). Em muitas migrações empresariais, esses processos envolvem um CAB (Conselho Consultivo de alterações) que é responsável por revisar, documentar e aprovar todas as solicitações relacionadas a ti (RFC).

O CAB geralmente inclui especialistas de várias equipes de ti e de negócios, oferecendo uma variedade de perspectivas e revisão detalhada para todas as alterações relacionadas a ti. Um processo de aprovação do CAB é uma maneira comprovada de reduzir riscos e minimizar o impacto nos negócios das alterações que envolvem cargas de trabalho estáveis gerenciadas pelas operações de ti.

## <a name="technical-approval"></a>Aprovação técnica

A prontidão organizacional para a aprovação da mudança técnica é entre os motivos mais comuns de falha de migração na nuvem. Mais projetos são interrompidos por uma série de aprovações técnicas do que qualquer déficit em uma plataforma de nuvem. Preparar a organização para a aprovação de alterações técnicas é um requisito importante para o sucesso da migração. A seguir estão algumas práticas recomendadas para garantir que a organização esteja pronta para aprovação técnica.

### <a name="itil-change-advisory-board-challenges"></a>Desafios do Conselho Consultivo de alterações de ITIL

Cada abordagem de gerenciamento de alterações tem seu próprio conjunto de controles e processos de aprovação. A migração é uma série de alterações contínuas que começam com um alto grau de ambiguidade e desenvolvem mais clareza por meio do curso de execução. Dessa forma, a migração é melhor governada por abordagens de gerenciamento de alterações baseadas em Agile, com a equipe de estratégia de nuvem que serve de proprietário de produto.

No entanto, a escala e a frequência de alteração durante uma migração de nuvem não se ajustam bem à natureza dos processos de ITIL. Os requisitos de uma aprovação do CAB podem arriscar o sucesso de uma migração, reduzindo ou interrompendo o esforço. Além disso, nos estágios iniciais da migração, a ambiguidade é alta e a experiência do assunto tende a ser baixa. Para as primeiras migrações ou versões de carga de trabalho, a equipe de adoção de nuvem geralmente está em um modo de aprendizado. Como tal, pode ser difícil para a equipe fornecer os tipos de dados necessários para passar uma aprovação do CAB.

As práticas recomendadas a seguir podem ajudar o CAB a manter um grau de conforto durante a migração sem se tornar um bloqueador problemático.

### <a name="standardize-change"></a>Padronizar alteração

É tentador de uma equipe de adoção de nuvem considerar decisões de arquitetura detalhadas para cada carga de trabalho que está sendo migrada para a nuvem. É uma tentação igualmente usar a migração de nuvem como um Catalyst para refatorar as decisões de arquitetura anteriores. Para organizações que estão migrando algumas centenas de VMs ou algumas dúzias de cargas de trabalho, qualquer abordagem pode ser gerenciada adequadamente. Ao migrar um datacenter que consiste em 1.000 ou mais ativos, cada uma dessas abordagens é considerada um antipadrão de alto risco que reduz significativamente a probabilidade de sucesso. Modernizar, Refatorar e rearquitetar todos os aplicativos exigem diversas habilidades e uma variedade significativa de alterações, e essas tarefas criam dependências de esforços humanos em escala. Cada uma dessas dependências injeta risco no esforço de migração.

O artigo sobre a [racionalização digital de imóveis](../../../digital-estate/rationalize.md) discute a agilidade e o impacto sobre as suposições básicas ao racionalizar um espaço digital. Há um benefício adicional de alteração padronizada. Ao escolher uma abordagem de racionalização padrão para controlar o esforço de migração, o BBS de nuvem ou o proprietário do produto pode revisar e aprovar o aplicativo de uma alteração para uma longa lista de cargas de trabalho. Isso reduz a aprovação técnica de cada carga de trabalho para aquelas que exigem uma alteração significativa na arquitetura para serem compatíveis com a nuvem.

### <a name="clarify-expectations-and-roles-of-approvers"></a>Esclareça expectativas e funções de aprovadores

Antes que a primeira carga de trabalho seja avaliada, a equipe de estratégia de nuvem deve documentar e comunicar as expectativas de qualquer pessoa envolvida na aprovação da alteração. Essa atividade simples pode evitar atrasos dispendiosos quando a equipe de adoção de nuvem está totalmente envolvida.

### <a name="seek-approval-early"></a>Aprovação de busca antecipada

Quando possível, a alteração técnica deve ser detectada e documentada durante o processo de avaliação. Independentemente dos processos de aprovação, a equipe de adoção de nuvem deve envolver os aprovadores no início. Quanto antes essa aprovação de alteração pode começar, menor é a probabilidade de um processo de aprovação bloquear atividades de migração.

## <a name="next-steps"></a>Próximos passos

Com a ajuda dessas práticas recomendadas, é mais fácil integrar a aprovação adequada e de baixo risco aos esforços de migração. Depois que as alterações de carga de trabalho forem aprovadas, a equipe de adoção de nuvem estará pronta para [migrar cargas de trabalho](../migrate/index.md).

> [!div class="nextstepaction"]
> [Migrar cargas de trabalho](../migrate/index.md)
