---
title: Encerrar os ativos desativados
description: Use a estrutura de adoção de nuvem para o Azure para saber como desativar corretamente os recursos desativados com interrupções de negócios mínimas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a62ef520f948d8bea415e4a65749944b91bb16c8
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092770"
---
# <a name="decommission-retired-assets"></a>Encerrar os ativos desativados

Depois que uma carga de trabalho é promovida para produção, os ativos que anteriormente hospedavam a carga de trabalho de produção não são mais necessários para dar suporte às operações de negócios. Nesse ponto, os ativos mais antigos são considerados desativados. Os ativos desativados podem então ser encerrados, reduzindo os custos operacionais. O encerramento de um recurso poderia ser algo simples, assim como funciona o desativamento e descarte responsável de um ativo. Mas infelizmente, o encerramento de recursos às vezes pode ter consequências indesejadas. As orientações a seguir podem ajudar no encerramento adequado de recursos desativados, com interrupções mínimas nos negócios.

## <a name="cost-savings-realization"></a>Concepção de redução de custos

Quando a redução de custos é a principal motivação para uma migração, o encerramento é um passo importante. Até que um ativo seja encerrado, ele continua consumindo energia, suporte ambiental e outros recursos que geram custos. Depois que o ativo é encerrado, a economia de custos pode começar a ser realizada.

## <a name="continued-monitoring"></a>Monitoramento contínuo

Depois que uma carga de trabalho migrada é promovida, os ativos a serem desativados devem continuar a ser monitorados para verificar se nenhum tráfego de produção adicional está sendo roteado para os ativos incorretos.

## <a name="testing-windows-and-dependency-validation"></a>Testando janelas e validação de dependência

Mesmo com o melhor planejamento, as cargas de trabalho de produção ainda podem conter dependências de ativos que são presumidos como desativados. Nesses casos, encerrar um ativo desativado pode causar falhas inesperadas no sistema. Portanto, o encerramento de quaisquer ativos deve ser tratada com o mesmo nível de rigor que uma atividade de manutenção do sistema. Janelas adequadas de teste e interrupção devem ser estabelecidas para facilitar o encerramento do recurso.

## <a name="holding-period-and-data-validation"></a>Período de espera e validação de dados

Não é incomum que dados sejam perdidos durante os processos de replicação. E isso ocorre mais frequentemente com dados mais antigos, que não são usados regularmente. Depois que um ativo é desativado, ainda é aconselhável mantê-lo por um tempo para servir como um backup temporário de dados. As empresas devem testar a infraestrutura e manter esses dados por, pelo menos, 30 dias antes de destruir ativos desativados.

## <a name="next-steps"></a>Próximas etapas

Depois que os ativos desativados são encerrados, a migração é concluída. Isso cria uma boa oportunidade para melhorar o processo de migração e uma [retrospectiva](./retrospective.md) envolve a equipe de adoção da nuvem na revisão da versão, em um esforço para aprender e melhorar.

> [!div class="nextstepaction"]
> [Retrospectiva](./retrospective.md)
