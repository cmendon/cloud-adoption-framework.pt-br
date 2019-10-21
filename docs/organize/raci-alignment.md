---
title: Alinhando as responsabilidades entre as equipes
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Aprenda a alinhar as responsabilidades entre as equipes.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 40ccd0c17a55a87c84d40abd749bf8e61f891e6c
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549083"
---
# <a name="align-responsibilities-across-teams"></a>Alinhar responsabilidades entre equipes

Aprenda a alinhar as responsabilidades entre as equipes, desenvolvendo uma matriz entre equipes que identifica partes responsáveis, acessadas *, consultadas e informadas* (RACI). Este artigo fornece um exemplo de matriz RACI para as estruturas organizacionais descritas em [estabelecer estruturas de equipe](./organization-structures.md):

- [Somente equipe de adoção de nuvem](#cloud-adoption-team-only)
- [Prática recomendada do MVP](#best-practice-minimum-viable-product-mvp)
- [TI central](#central-it)
- [Alinhamento estratégico](#strategic-alignment)
- [Alinhamento operacional](#operational-alignment)
- [Cloud Center of Excellence (CCoE)](#cloud-center-of-excellence-ccoe)

Para acompanhar as decisões da estrutura organizacional ao longo do tempo, baixe e modifique o [modelo de planilha RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx).

Os exemplos neste artigo especificam essas construções RACI:

- A única equipe *que é* proficada para uma função.
- As equipes que são *responsáveis* pelos resultados.
- As equipes que devem ser *consultadas* durante o planejamento.
- As equipes que devem ser *informadas* quando o trabalho é concluído.

A última linha de cada tabela (exceto a primeira) contém um link para o recurso de nuvem mais alinhado para informações adicionais.

## <a name="cloud-adoption-team-only"></a>Somente equipe de adoção de nuvem

|  |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de adoção de nuvem |Accountable|Accountable|Accountable|Accountable|Accountable|Accountable|Accountable|Accountable|

## <a name="best-practice-minimum-viable-product-mvp"></a>Prática recomendada: produto (MVP) mínimo viável

|  |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de adoção de nuvem|Accountable|Accountable|Accountable|Accountable|Consultada|Consultada|Consultada|Informado|
|Equipe de governança de nuvem|Consultada|Informado|Informado|Informado|Accountable|Accountable|Accountable|Accountable|
||||||||||
|Recurso de nuvem alinhado|[Adoção de nuvem](./cloud-adoption.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Operações de nuvem](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governança de nuvem](./cloud-governance.md)|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Automação de[nuvem](./cloud-automation.md) do [CCOE](./cloud-center-of-excellence.md) -|

## <a name="central-it"></a>TI central

| |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de adoção de nuvem  |Accountable|Accountable|Responsabiliza    |Responsabiliza|Informado   |Informado   |Informado   |Informado   |
|Equipe de governança de nuvem|Consultada  |Informado   |Informado   |Informado   |Accountable|Consultada  |Responsabiliza|Informado   |
|TI central           |Consultada  |Informado   |Accountable   |Accountable   |Responsabiliza  |Accountable|Accountable|Accountable|
||||||||||
|Recurso de nuvem alinhado|[Adoção de nuvem](./cloud-adoption.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Operações de nuvem](./cloud-operations.md)|[Governança de nuvem](./cloud-governance.md)|[TI central](./central-it.md)|[TI central](./central-it.md)|[TI central](./central-it.md)|

## <a name="strategic-alignment"></a>Alinhamento estratégico

|  |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de estratégia de nuvem  |Consultada  |Accountable|Accountable|Consultada  |Consultada  |Informado   |Informado   |Informado   |
|Equipe de adoção de nuvem  |Accountable|Consultada  |Responsabiliza|Accountable|Informado   |Informado   |Informado   |Informado   |
|CCoE modelo RACI      |Consultada  |Informado   |Informado   |Informado   |Accountable|Accountable|Accountable|Accountable|
||||||||||
|Recurso de nuvem alinhado|[Adoção de nuvem](./cloud-adoption.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Operações de nuvem](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governança de nuvem](./cloud-governance.md)|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Automação de[nuvem](./cloud-automation.md) do [CCOE](./cloud-center-of-excellence.md) -|

## <a name="operational-alignment"></a>Alinhamento operacional

|  |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de estratégia de nuvem  |Consultada  |Accountable|Accountable|Consultada  |Consultada  |Informado   |Informado   |Informado   |
|Equipe de adoção de nuvem  |Accountable|Consultada  |Responsabiliza|Consultada  |Informado   |Informado   |Informado   |Informado   |
|Equipe de operações de nuvem|Consultada  |Consultada  |Responsabiliza|Accountable|Consultada  |Informado   |Accountable|Consultada  |
|CCoE modelo RACI      |Consultada  |Informado   |Informado   |Informado   |Accountable|Accountable|Responsabiliza|Accountable|
||||||||||
|Recurso de nuvem alinhado|[Adoção de nuvem](./cloud-adoption.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Operações de nuvem](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governança de nuvem](./cloud-governance.md)|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Automação de[nuvem](./cloud-automation.md) do [CCOE](./cloud-center-of-excellence.md) -|

## <a name="cloud-center-of-excellence-ccoe"></a>Cloud Center of Excellence (CCoE)

|  |Entrega da solução  |Alinhamento de negócios  |Gerenciamento de alterações  |Operações de solução  |Governança |Maturidade da plataforma  |Operações de plataforma  |Automação de plataforma  |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|Equipe de estratégia de nuvem  |Consultada  |Accountable|Accountable|Consultada  |Consultada  |Informado   |Informado   |Informado   |
|Equipe de adoção de nuvem  |Accountable|Consultada  |Responsabiliza|Consultada  |Informado   |Informado   |Informado   |Informado   |
|Equipe de operações de nuvem|Consultada  |Consultada  |Responsabiliza|Accountable|Consultada  |Informado   |Accountable|Consultada  |
|Equipe de governança de nuvem|Consultada  |Informado   |Informado   |Consultada  |Accountable|Consultada  |Responsabiliza|Informado   |
|Equipe da plataforma de nuvem  |Consultada  |Informado   |Informado   |Consultada  |Consultada  |Accountable|Responsabiliza|Responsabiliza|
|Equipe de automação de nuvem|Consultada  |Informado   |Informado   |Informado   |Consultada  |Responsabiliza|Responsabiliza|Accountable|
||||||||||
|Recurso de nuvem alinhado|[Adoção de nuvem](./cloud-adoption.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Estratégia de nuvem](./cloud-strategy.md)|[Operações de nuvem](./cloud-operations.md)|[CCoE](./cloud-center-of-excellence.md) -[governança de nuvem](./cloud-governance.md)|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Plataforma de[nuvem](./cloud-platform.md) [CCOE](./cloud-center-of-excellence.md) -|Automação de[nuvem](./cloud-automation.md) do [CCOE](./cloud-center-of-excellence.md) -|

## <a name="next-steps"></a>Próximos passos

Para controlar as decisões sobre a estrutura da organização ao longo do tempo, baixe e modifique o [modelo de planilha RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx). Copie e modifique o exemplo alinhado mais próximo das matrizes RACI neste artigo.

> [!div class="nextstepaction"]
> [Baixar o modelo de planilha RACI](https://archcenter.blob.core.windows.net/cdn/fusion/management/raci-template.xlsx)
