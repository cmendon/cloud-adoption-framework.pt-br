---
title: O que é uma zona de destino?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como as zonas de aterrissagem fornecem os blocos de construção básicos de qualquer ambiente de adoção da nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: fe53435fe09873a619b2860a63e7bf67fe7bca93
ms.sourcegitcommit: d660484d534bc61fc60470373f3fcc885a358219
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508297"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-a-landing-zone"></a>O que é uma zona de destino?

A infraestrutura como código é uma transição natural durante a maioria dos esforços de adoção da nuvem. A implantação das suas primeiras zonas de destino na nuvem é um ponto de partida comum para fazer a transição para a criação de ambientes que priorizam o código. Este artigo ajudará a entender o termo _zona de destino_ e outros termos relacionados.

## <a name="landing-zone-definition"></a>Definição de zona de destino

Uma zona de aterrissagem é o bloco de construção básico de qualquer ambiente de adoção da nuvem. O termo _zona de destino_ se refere a um constructo lógico que captura tudo o que deve ser verdadeiro para habilitar a adoção de nuvem desejada.

**Escopo:** uma zona de destino totalmente funcional considera todos os recursos de plataforma necessários para dar suporte às necessidades de adoção do cliente.

**Refatoração:** Uma zona de destino totalmente funcional é a entrega final de uma iteração da metodologia de preparação do Cloud Adoption Framework. Durante cada iteração, a base de código que define a zona de destino será refatorada ou expandida. Após a refatoração, a zona de destino pode ser modificada ou reimplantada para permitir novas necessidades de adoção de nuvem.

**Meta:** A meta da abordagem de zona de destino é criar um conjunto comum de implementações de plataforma consistentes. Essas implementações consistentes devem estar em vigor para garantir que seus aplicativos tenham acesso aos componentes requisitados quando implantadas. Consequentemente, cada iteração da zona de destino deve ser projetada e implantada de acordo com os requisitos do plano de adoção da nuvem e da estratégia de design da assinatura.

**Finalidade do princípio:** A finalidade do princípio da zona de destino é garantir que, quando um aplicativo se chegar ao Azure, a configuração necessária já esteja em vigor.

## <a name="landing-zone-usage"></a>Uso da zona de destino

As zonas de destino não diferenciam necessariamente a adoção de IaaS ou PaaS. No entanto, as zonas de destino são criadas para apoiar o plano de adoção seguindo a estratégia de assinatura. Apoiar o plano de adoção pode exigir várias zonas de destino com uma mistura de componentes necessários.

A finalidade e o escopo do plano geral de adoção de nuvem definirão o que é necessário para a configuração. Os requisitos adicionais de governança, conformidade, segurança e gerenciamento operacional provavelmente serão adicionados ao escopo inicial da zona de destino. Durante os estágios iniciais de adoção, as zonas de destino podem incluir menos configuração como resultado de requisitos definidos e riscos aceitáveis.  Quando existem várias zonas de destino, é muito comum que cada uma seja dependente de hubs que fornecem os controles necessários por meio de um modelo de serviço compartilhado.

## <a name="related-terms"></a>Termos relacionados

- **Serviços compartilhados:** Geralmente, as cargas de trabalho têm dependências compartilhadas que são usadas por várias cargas de trabalho diferentes. A abordagem de serviços compartilhados move muitas dessas dependências comuns para um constructo lógico.

- **Modelo hub e spoke:** Uma implementação da abordagem de serviços compartilhados é um modelo hub e spoke. Nesse modelo, o hub é um único constructo lógico para hospedar todos os serviços compartilhados. As zonas de destino agem como spokes radiando do hub, com base em dependências comuns.

- **Zona de destino independente:** Algumas abordagens de zonas de destino não chamam especificamente um hub dedicado. Isso é mais comumente visto quando todos os ativos de produção (aplicativos, dados e VMs) no plano de adoção de nuvem podem ser hospedados, gerenciados e governados com segurança em um único ambiente.

## <a name="next-steps"></a>Próximas etapas

Para começar a usar as zonas de destino, [escolha sua primeira zona de destino](./first-landing-zone.md).

> [!div class="nextstepaction"]
> [Escolha sua primeira zona de destino](./first-landing-zone.md)
