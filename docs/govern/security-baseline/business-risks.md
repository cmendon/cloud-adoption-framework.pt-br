---
title: Motivações da linha de base de segurança e riscos de negócios
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivações da linha de base de segurança e riscos de negócios
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a77df6b190db7f9fd5f44e233e175670ff7f4855
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029328"
---
# <a name="security-baseline-motivations-and-business-risks"></a>Motivações da linha de base de segurança e riscos de negócios

Este artigo aborda os motivos pelos quais os clientes normalmente adotam uma disciplina de Linha de base de segurança dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios potenciais que podem conduzir as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="is-a-security-baseline-relevant"></a>É uma Linha de base de segurança relevante?

A segurança é uma preocupação importante para qualquer organização de TI. As implantações de nuvem enfrentam muitos dos mesmos riscos de segurança como cargas de trabalho hospedadas em datacenters tradicionais no local. No entanto, a natureza das plataformas de nuvem pública, com a falta de propriedade direta do armazenamento de hardware físico e execução das cargas de trabalho, significa que a segurança de nuvem requer sua própria política e processos.

Uma das coisas principais que define o controle de segurança na nuvem, além da política de segurança tradicional, é a facilidade com a qual os recursos podem ser criados, potencialmente adicionando vulnerabilidades se a segurança não for considerada antes da implantação. A flexibilidade que as tecnologias, como [rede definida pelo software (SDN)](../../decision-guides/software-defined-network/index.md), fornecem para sua topologia de rede baseada em nuvem que mudam rapidamente, podem também modificar facilmente a superfície de ataque de rede geral de formas imprevisíveis. Plataformas de nuvem também fornecem ferramentas e recursos que podem melhorar os recursos de segurança de maneiras nem sempre possíveis em ambientes locais.

O valor que você investe na política de segurança e processos dependerá muito da natureza de sua implantação de nuvem. Implantações de teste inicial talvez só precisam da mais básica das políticas de segurança em vigor, enquanto uma carga de trabalho de missão crítica envolve atribuir necessidades de segurança abrangentes e complexas. Todas as implantações precisarão se envolver com a disciplina em algum nível.

A disciplina de Linha de base de segurança aborda as políticas corporativas e os processos manuais que você pode colocar em vigor para proteger sua implantação de nuvem contra riscos de segurança.

> [!NOTE]
>Embora seja importante entender a [Linha de Base de Identidade](../identity-baseline/index.md) no contexto de Linha de Base de Segurança e como se relaciona com o Serviço de Controle de Acesso, as [Cinco disciplinas de governança de nuvem](../index.md) chamam a [Linha de base de identidade](../identity-baseline/index.md) como sua própria disciplina, separada da Linha de base de segurança.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de linha de base de segurança tenta abordar riscos de negócios relacionados à segurança. Trabalhar com seus negócios para identificar esses riscos e monitorar cada um deles para relevância como planejar e implementar suas implantações de nuvem.

Os riscos serão diferentes entre a organização, mas os seguintes servem como riscos comuns relacionados à segurança que você pode usar como ponto de partida para discussões em sua equipe de governança de nuvem:

- **Violação de dados:** Exposição acidental ou perda de dados confidenciais hospedados na nuvem pode levar à perda de clientes, problemas contratuais ou consequências jurídicas.
- **Interrupção do serviço:** Interrupções e outros problemas de desempenho devido à infraestrutura insegura interrompe as operações normais e pode resultar em perda de produtividade ou perda de negócios.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Entenda os indicadores, métricas e tolerância a risco](./metrics-tolerance.md)
