---
title: Coletar dados de inventário para uma propriedade digital
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Como coletar dados de inventário para um estado digital.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 6b6bbfef4f9e404433119d412cd4bf625cd3b480
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71023493"
---
# <a name="gather-inventory-data-for-a-digital-estate"></a>Coletar dados de inventário para uma propriedade digital

O desenvolvimento de um inventário é a primeira etapa no [planejamento de imóveis](./index.md). Nesse processo, uma lista de ativos de ti que dão suporte a funções de negócios específicas são coletadas para análise e racionalização posteriores. Este artigo pressupõe que uma abordagem de baixo para a análise é mais apropriada para o planejamento. Para saber mais, confira [Abordagens para planejamento de propriedade digital](./approach.md).

## <a name="take-inventory-of-a-digital-estate"></a>Faça o inventário de um espaço digital

O inventário que dá suporte a um espaço digital muda dependendo da transformação digital desejada e da jornada de transformação correspondente.

- **Migração na nuvem:**  Geralmente recomendamos que, durante uma migração na nuvem, você colete o inventário de ferramentas de verificação que criam uma lista centralizada de todas as VMs e servidores. Algumas ferramentas também podem criar mapeamentos e dependências de rede, o que ajuda a definir o alinhamento da carga de trabalho.

- **Inovação de aplicativos:** O inventário durante um esforço de inovação de aplicativos habilitado para nuvem começa com o cliente. O mapeamento da experiência do cliente do início ao fim é um bom lugar para começar. Alinhar esse mapa a aplicativos, APIs, dados e outros ativos cria um inventário detalhado para análise.

- **Inovação de dados:** Os esforços de inovação de dados habilitados para nuvem concentram-se no produto ou serviço. Um inventário também inclui um mapeamento das oportunidades para interromper o mercado, bem como os recursos necessários.

## <a name="accuracy-and-completeness-of-an-inventory"></a>Precisão e integridade de um inventário

Um inventário é raramente concluído em sua primeira iteração. É altamente recomendável que a equipe de estratégia de nuvem alinhe os participantes e os usuários avançados a validar o inventário. Quando possível, use ferramentas adicionais, como a análise de rede e de dependência para identificar os ativos que estão sendo enviados ao tráfego, mas que não estão no inventário.

## <a name="next-steps"></a>Próximas etapas

Depois que um inventário é compilado e validado, ele pode ser racionalizado. A racionalização de inventário é a próxima etapa para o planejamento de imóveis.

> [!div class="nextstepaction"]
> [Racionalizar a propriedade digital](./rationalize.md)
