---
title: Guias de decisão de arquitetura
description: Use esses modelos e padrões principais de componentes de infraestrutura de implantação de nuvem para dar suporte a seus cenários de implantação de nuvem específicos.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: 9552ba8b168e79f247916ae86f8e7721282baddb
ms.sourcegitcommit: 388e32dd4861039149c846c926c0e9230cf28ae3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79140228"
---
# <a name="architectural-decision-guides"></a>Guias de decisão de arquitetura

Guias de decisão de arquitetura em que a estrutura de adoção da nuvem descrevem padrões e modelos que ajudam durante a criação de diretrizes de design de governança de nuvem. Cada guia de decisão se concentra em um componente de infraestrutura de núcleo de implantações de nuvem e lista padrões e modelos que podem dar suporte a cenários de implantação de nuvem específica.

Quando você começa a estabelecer a governança de nuvem para sua organização, percursos de governança acionáveis fornecem um roteiro de linha de base. No entanto, esses percursos fazem suposições sobre os requisitos e as prioridades que podem não refletir a realidade da organização.

Esses guias de decisão complementam os percursos de governança de exemplo, fornecendo padrões alternativos e modelos que ajudam você a alinhar as escolhas de design arquitetônico feitas nas diretrizes de design de exemplo pelos seus próprios requisitos.

## <a name="decision-guidance-categories"></a>Categorias de orientação de decisão

Cada uma das categorias a seguir representa uma tecnologia de base de todas as implantações de nuvem. Os percursos de governança de exemplo tomam decisões de design relacionadas a essas tecnologias com base nas necessidades de negócios de exemplo e algumas dessas decisões podem não corresponder às necessidades da sua própria organização. As seções a seguir discutem opções alternativas a cada uma dessas categorias, permitindo que você escolha um modelo ou padrão mais adequado às suas necessidades.

[Assinaturas](./subscriptions/index.md): Planeje a estrutura de design e conta de assinatura da sua implantação para corresponder com a propriedade da sua organização, faturamento e capacidades de gerenciamento.

[Identidade](./identity/index.md): integre os serviços de identidade baseados em nuvem aos seus recursos de identidade existentes para dar suporte a controle de acesso e autorização em seu ambiente de TI.

[Imposição de Política](./policy-enforcement/index.md): defina e imponha regras de política organizacional a recursos e cargas de trabalho implantados na nuvem alinhados a seus requisitos de governança.

[Consistência de Recursos](./resource-consistency/index.md): Certifique-se que implantação e a organização dos seus recursos baseados em nuvem se alinham para impor requisitos de gerenciamento e a política de recursos.

[Marcação de Recursos](./resource-tagging/index.md): organize seus recursos baseados em nuvem para dar suporte a modelos de cobrança, abordagens de contabilidade da nuvem e gerenciamento e para otimizar o custo e a utilização de recursos. A marcação de recursos exige um esquema de nomenclatura e de metadados consistente e bem organizado.

[Rede Definida por Software](./software-defined-network/index.md): Implante cargas de trabalho seguras para a nuvem usando a implantação rápida e modificação de recursos de rede virtualizados. Redes definidas por software podem ser compatíveis com fluxos de trabalho ágeis, isolar os recursos e integrar sistemas baseados em nuvem com sua infraestrutura de TI existente.

[Criptografia](./encryption/index.md): proteja seus dados confidenciais usando criptografia para alinhar-se aos requisitos da política de segurança e conformidade da sua organização.

[Registro em log e relatórios](./logging-and-reporting/index.md): Monitorar dados de log gerados pelos recursos baseados em nuvem. A análise de dados fornece insights relacionados à integridade para operações, manutenção e status de conformidade das cargas de trabalho.

## <a name="next-steps"></a>Próximas etapas

Saiba como as assinaturas e contas servem como a base de uma implantação de nuvem.

> [!div class="nextstepaction"]
> [Design de assinaturas](./subscriptions/index.md)
