---
title: Datacenter Virtual do Azure
description: Recursos para o Datacenter Virtual do Microsoft Azure
author: tracsman
ms.author: jonor
ms.date: 06/12/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: reference
keywords: Azure
layout: LandingPage
ms.openlocfilehash: 39cb6ac3c31873431206d8c6c525c9ce3467653f
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027683"
---
# <a name="azure-virtual-datacenter-and-the-enterprise-control-plane"></a>Datacenter Virtual do Azure e o Plano de controle empresarial

O Datacenter Virtual do Azure é uma abordagem para aproveitar ao máximo os recursos da plataforma de nuvem do Azure, respeitando simultaneamente suas políticas de segurança e de rede existentes. Ao implantar cargas de trabalho da empresa na nuvem, as organizações de TI e as unidades de negócios devem equilibrar a governança com a agilidade do desenvolvedor. O Datacenter Virtual do Azure fornece modelos para alcançar esse equilíbrio com ênfase na governança.

## <a name="resources"></a>Recursos

<!-- markdownlint-disable MD033 -->

<table>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Concepts"><img src="../_images/vdc/virtual-datacenter.svg" alt="Virtual Datacenter e-book" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Concepts">Datacenter Virtual do Azure: Conceitos</a></h3>
        <p>Este livro eletrônico mostra como implantar cargas de trabalho empresariais na plataforma de nuvem do Azure, respeitando simultaneamente suas políticas de segurança e de rede existentes.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="./networking-vdc.md"><img src="../_images/vdc/vdc-network.png" alt="Network Perspective" /></a></td>
    <td>
        <h3><a href="./networking-vdc.md">Datacenter Virtual do Azure: Uma perspectiva de rede</a></h3>
        <p>Este artigo online apresenta uma visão geral de padrões e designs de rede que podem ser usados para resolver as preocupações de desempenho, escala e segurança da arquitetura que muitos clientes têm quando pensam em uma transição em massa para a nuvem.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Lift"><img src="../_images/vdc/vdc-lift-and-shift.png" alt="Lift and Shift Guide" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Lift">Datacenter Virtual do Azure: Guia de Lift-and-Shift </a></h3>
        <p>Esse white paper descreve o processo que a equipe de TI empresarial e tomadores de decisão podem usar para identificar e planejar a migração de aplicativos e servidores para o Azure usando o método "lift-and-shift", minimizando custos de desenvolvimento adicionais enquanto otimiza as opções de hospedagem de nuvem.</p>
    </td>
</tr>
<tr>
    <td style="width: 64px; vertical-align: middle;"><a href="https://aka.ms/VDC/Deck"><img src="../_images/vdc/vdc-deck.png" alt="Presentation Deck" /></a></td>
    <td>
        <h3><a href="https://aka.ms/VDC/Deck">Datacenter Virtual do Azure: Conjunto de slides para apresentação </a></h3>
        <p>Esse baralho de apresentação explora as diretrizes e ferramentas do Datacenter Virtual do Azure. Ele aborda metas do Datacenter Virtual (VDC), drivers de cliente, regiões do Azure, elementos de uma automação do VDC, VDCs industrializados e confiáveis do Azure e termina com um plano de ação sobre a orientação de CIO. Também são fornecidas informações de suporte e treinamento.</p>
    </td>
</tr>
</table>

<!-- markdownlint-enable MD033 -->

<!-- markdownlint-disable MD026 -->

## <a name="what-is-the-azure-virtual-datacenter"></a>O que é o Datacenter Virtual do Azure?

A implantação de cargas de trabalho para a nuvem gera a necessidade de desenvolver e manter a confiança na nuvem no mesmo nível de confiança de seus datacenters existentes. O primeiro modelo do guia do Datacenter Virtual do Azure foi projetado para unir essa necessidade a infraestruturas virtuais por meio de uma abordagem bloqueada. Essa abordagem não é para todos. Ela foi projetada especificamente para guiar os grupos de TI empresariais quanto à extensão da sua infraestrutura local até a nuvem pública do Azure. Chamamos essa abordagem de modelo de extensão do datacenter confiável. Ao longo do tempo, vários outros modelos serão oferecidos, incluindo aqueles que permitem o acesso seguro à Internet diretamente de um datacenter virtual.

<!-- markdownlint-disable MD033 -->

<img src="../_images/vdc/vdc-components.svg" alt="Virtual Datacenter components" style="max-width:700px;"/>

<!-- markdownlint-enable MD033 -->

Estes quatro componentes possibilitam o Datacenter Virtual do Azure: identidade, criptografia, rede definida pelo software e conformidade (incluindo logs e relatórios).

No modelo do Datacenter Virtual do Azure, é possível aplicar políticas de isolamento, tornar a nuvem mais parecida com os datacenters físicos que você conhece e alcançar os níveis de segurança e confiança de que você precisa. Quatro componentes que qualquer equipe de TI empresarial pensariam em tornar possíveis: rede definida pelo software, criptografia, gerenciamento de identidade e padrões de conformidade e certificações subjacentes à plataforma do Azure. Os quatro são fundamentais para transformar um datacenter virtual em uma extensão confiável de seu investimento de infraestrutura existente.

Continue lendo o livro eletrônico [Datacenter Virtual do Azure: conceitos](https://azure.microsoft.com/resources/azure-virtual-datacenter).
