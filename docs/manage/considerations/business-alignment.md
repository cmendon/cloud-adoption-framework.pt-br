---
title: Alinhamento de negócios no gerenciamento de nuvem
description: Use a estrutura de adoção de nuvem para o Azure para saber como gerenciar melhor suas operações de nuvem e desenvolver um alinhamento de negócios mais rígido.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: ee88c1fc88e5c678f7356aa15b473d0fe61eaa2d
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140647"
---
# <a name="create-business-alignment-in-cloud-management"></a>Criar alinhamento de negócios no gerenciamento de nuvem

Em ambientes locais, os ativos de ti (aplicativos, máquinas virtuais, hosts de VM, disco, servidores, dispositivos e fontes de dados) são gerenciados pelo ti para dar suporte a operações de carga de trabalho. Nos termos de ti, uma carga de trabalho é uma coleção de ativos de ti que dão suporte a uma operação de negócios específica. Para ajudar a oferecer suporte a operações de negócios, o gerenciamento de ti fornece processos projetados para minimizar as interrupções nesses ativos. Quando uma organização passa para a nuvem, o gerenciamento e as operações mudam um pouco, criando uma oportunidade para desenvolver um alinhamento de negócios mais rígido.

## <a name="business-vernacular"></a>Idioma de negócios

A primeira etapa na criação do alinhamento comercial é garantir o alinhamento do termo. O gerenciamento de ti, como a maioria das profissão de engenharia, tem reuniu uma coleção de jargão ou termos altamente técnicos. Esses termos podem levar à confusão para os participantes da empresa e dificultar o mapeamento dos serviços de gerenciamento para o valor comercial.

Felizmente, o processo de desenvolvimento de uma estratégia de adoção de nuvem e plano de adoção de nuvem cria uma oportunidade ideal para remapear esses termos. O processo também cria oportunidades para reconsiderar os compromissos com o gerenciamento operacional, em parceria com a empresa. A série de artigos a seguir orienta você pela nova abordagem em três termos específicos que podem ajudar a melhorar as conversas entre os participantes comerciais:

- **[Criticalidade](./criticality.md):** Mapeando cargas de trabalho para processos de negócios. Classificação da importância para concentrar os investimentos.
- **[Impacto](./impact.md):** Entender o impacto de possíveis interrupções para ajudar na avaliação do retorno sobre o investimento para o gerenciamento de nuvem.
- **[Compromisso](./commitment.md):** desenvolver parcerias verdadeiras, criando e documentando contratos *com os negócios*.

> [!NOTE]
> Esses termos subjacentes são os termos de ti clássicos, como SLA, RTO e RPO. O mapeamento de termos de ti e de negócios específicos é abordado em mais detalhes no artigo de [compromisso](./commitment.md) .

## <a name="ops-management-planning-workbook"></a>Pasta de trabalho de planejamento do Ops Management

Para ajudar a capturar decisões que resultam dessa conversa sobre o alinhamento de termos, uma [pasta de trabalho do gerenciamento de operações](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) está disponível em nosso site do github. Esta pasta de trabalho não executa cálculos de custo ou SLA. Ele serve apenas para ajudar a capturar essas medidas e prever o retorno sobre os esforços de eliminação de perda.

Como alternativa, essas mesmas cargas de trabalho e ativos associados podem ser marcados diretamente no Azure, se as soluções já estiverem implantadas na nuvem.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Comece a criar o alinhamento comercial definindo a [importância da carga de trabalho](./criticality.md).

> [!div class="nextstepaction"]
> [Definir a criticalidade da carga de trabalho](./criticality.md)
