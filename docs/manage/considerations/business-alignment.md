---
title: Alinhamento de negócios-gerenciamento de nuvem e operações
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Alinhamento de negócios-gerenciamento de nuvem e operações
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9c6884d57b9238f58921b14ec3ddbbe3623506af
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558136"
---
# <a name="create-business-alignment-in-cloud-management"></a>Criar alinhamento de negócios no gerenciamento de nuvem

Em ambientes locais, os ativos de ti (aplicativos, máquinas virtuais, hosts de VM, disco, servidores, dispositivos e fontes de dados) são gerenciados pelo ti para dar suporte a operações de carga de trabalho. Nos termos de ti, uma carga de trabalho é uma coleção de ativos de ti que dão suporte a uma operação de negócios específica. Em ambientes locais, o gerenciamento de ti fornece um design de processos para minimizar as interrupções nesses ativos de ti, em uma tentativa de minimizar as interrupções nas operações de negócios de suporte. Ao mudar para a nuvem, o gerenciamento e as operações mudam um pouco, criando uma oportunidade para desenvolver um alinhamento de negócios mais rígido.

## <a name="business-vernacular"></a>Idioma de negócios

A primeira etapa na criação do alinhamento de negócios é o alinhamento de termos. O gerenciamento de ti, como a maioria das profissão de engenharia, inclui um pouco de jargão ou termos altamente técnicos. Esses termos podem levar à confusão para os participantes de negócios e dificultar o mapeamento dos serviços de gerenciamento para o valor comercial.

Felizmente, os processos para desenvolver uma estratégia de adoção de nuvem e plano de adoção de nuvem criam uma situação de ideia para o remapeamento de termos. Ele também cria uma grande oportunidade para reconsiderar os compromissos com o gerenciamento operacional, em parceria com os negócios. A série de artigos a seguir percorre essa nova abordagem em três termos específicos que podem melhorar as conversas com os participantes comerciais:

- **[Criticalidade](./criticality.md)** : mapeando cargas de trabalho para processos de negócios. Classificação da importância para concentrar os investimentos.
- **[Impacto](./impact.md)** : entenda o impacto de interrupções potenciais para ajudar a avaliar o retorno do investimento para o gerenciamento de nuvem.
- **[Compromisso](./commitment.md)** : desenvolva parcerias verdadeiras, criando e documentando contratos **com os negócios**.

> [!NOTE]
> Abaixo de cada um desses termos estão os termos de ti clássicos, como SLA, RTO e RPO. O mapeamento de termos de ti e de negócios é abordado em mais detalhes no artigo sobre o compromisso.

## <a name="ops-management-planning-workbook"></a>Pasta de trabalho de planejamento do Ops Management

Para ajudar a capturar decisões como resultado dessa conversa, uma [pasta de trabalho de gerenciamento do Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) está disponível em nosso repositório github. Esta pasta de trabalho não executa cálculos de custo ou SLA. Ele serve apenas como um guia para capturar essas medidas e prever o retorno sobre os esforços de contenção de perda.

Como alternativa, essas mesmas cargas de trabalho e ativos associados podem ser marcados diretamente no Azure, se as soluções já estiverem implantadas na nuvem.

## <a name="next-steps"></a>Próximas etapas

Comece a criar o alinhamento comercial definindo a [importância da carga de trabalho](./criticality.md).

> [!div class="nextstepaction"]
> [Definir a criticalidade da carga de trabalho](./criticality.md)
