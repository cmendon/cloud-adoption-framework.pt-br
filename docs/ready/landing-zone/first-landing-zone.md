---
title: Considerações sobre zonas de aterrissagem do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como as zonas de aterrissagem fornecem os blocos de construção básicos de qualquer ambiente de adoção da nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/25/2020
ms.topic: overview
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: 04293b0e0d30ae1eaa85f4c86c6c7d70b2cfac82
ms.sourcegitcommit: 959cb0f63e4fe2d01fec2b820b8237e98599d14f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092983"
---
# <a name="first-landing-zone"></a>'Primeira zona de aterrissagem

A infraestrutura como código é uma transição natural durante a maioria dos esforços de adoção da nuvem. A implantação de suas primeiras zonas de aterrissagem na nuvem é um ponto de partida comum na mudança para um ambiente orientado por código. Este artigo o ajudará a entender o termo _zona de aterrissagem_ e decidir qual zona de aterrissagem é mais apropriada para suas necessidades de adoção atuais.

## <a name="code-first-approach-to-landing-zones"></a>Abordagem de código-primeira para zonas de aterrissagem

A imagem a seguir mostra uma variedade de opções para zonas de aterrissagem. As opções a seguir auxiliam na seleção da zona de aterrissagem correta hoje. Ele também ajuda a estabelecer uma visão para suas necessidades futuras de zona de aterrissagem.

![Opções de zona de aterrissagem](../../_images/ready/landing-zone-options.png)

a. Comece com o código para produzir zonas de aterrissagem consistentes e reproduzíveis. Se você estiver familiarizado com a refatoração (ou refinar o código e a infraestrutura) à medida que aprende, comece com uma base de código leve, como a planta de migração de nuvem da estrutura de adoção do Cloud. Essa abordagem acelera o sucesso da adoção e cria oportunidades de aprendizado práticos. No entanto, esse tipo de zona de aterrissagem inicial não é projetado para dados confidenciais ou cargas de trabalho de missão crítica, sem refatoração adicional.

B. À medida que a adoção cresce e os requisitos se tornam mais claramente identificados, as equipes de adoção e plataforma refatoram as zonas de aterrissagem com base no que eles aprendem. O processo de expansão de suas zonas de aterrissagem prepara ambientes para requisitos de conformidade ou de arquitetura mais complexos. [Expandir a zona de aterrissagem](../considerations/index.md) fornece guias de decisão e links para práticas recomendadas para orientar os esforços de refatoração. Expandir a zona de aterrissagem pode ajudar a atender aos requisitos de segurança, operações e governança.

C. Alguns planos de adoção de nuvem são governados por requisitos de conformidade externos. Para reduzir a carga de atender a esses requisitos, o Azure fornece alguns exemplos de plantas do Azure. Alguns dos exemplos podem ser adicionados ao seu primeiro plano inicial. Outros exemplos também incluem uma implementação específica que pode servir como uma primeira zona de aterrissagem.

D. Quando um parceiro fornece serviços gerenciados em andamento ou é contratado para fornecer no plano de adoção, normalmente eles fornecerão sua própria zona de aterrissagem. Usar uma zona de aterrissagem de parceiro pode acelerar os esforços de adoção e garantir requisitos de gerenciamento operacional consistentes. No entanto, dê uma consideração adicional aos requisitos internos de governança e segurança para garantir o alinhamento.

> [!NOTE]
> Antes de prosseguir com uma abordagem voltada para o código e a refatoração, os leitores devem estar familiarizados com as [prioridades concorrentes por trás dessa decisão](../../strategy/balance-competing-priorities.md#balance-during-ready). Ao escolher uma abordagem de zona de aterrissagem, é importante entender o equilíbrio necessário entre "tempo de adoção" e "operações de longo prazo".

## <a name="choosing-a-first-landing-zone"></a>Escolhendo uma primeira zona de aterrissagem

A seleção da primeira zona de aterrissagem depende de várias variáveis. A grade a seguir captura algumas das opções para as primeiras zonas de aterrissagem, juntamente com variáveis que podem orientar a decisão.

| Zona de aterrissagem                                 | Experiência de nuvem  | Escala             | Tempo de descoberta | Pronto para produção | Híbrido             | Dados Confidenciais     | Missão crítica   | Conformidade         |
|----------------------------------------------|-------------------|-------------------|----------------|------------------|--------------------|--------------------|--------------------|--------------------|
| [CAF migrar](./migrate-landing-zone.md)     | Novo na nuvem      | ativos do < 1.000    | 1 a 5 dias    | Escopo limitado-> | Expansão necessária | Expansão necessária | Expansão necessária | Expansão necessária |
| [CAF Terraform](./terraform-landing-zone.md) | Vários modelos | Vários modelos | de 10 a 20 semanas | Escopo limitado-> | Módulos disponíveis  | Módulos disponíveis  | Módulos disponíveis  | Módulos disponíveis  |

A tabela a seguir mostra as mesmas zonas de aterrissagem de uma perspectiva ligeiramente diferente, para guiar mais processos de decisão técnica.

| Zona de aterrissagem                                 | Hub                          | Falou    | Modelo de nuvem | Tecnologia      |
|----------------------------------------------|------------------------------|----------|-------------|-----------------|--|--|--|
| [CAF migrar](./migrate-landing-zone.md)     | Refatoração necessária            | Incluso | Somente Azure  | Especificações Técnicas do Azure |
| [CAF Terraform](./terraform-landing-zone.md) | Incluído no módulo VDC       | Incluso | Multinuvem  | Terraform       |

## <a name="next-steps"></a>Próximas etapas

Se você ainda não tiver certeza de qual primeira zona de aterrissagem escolher, é recomendável começar com a [CAF de zona de aterrissagem de migração](./migrate-landing-zone.md).

> [!div class="nextstepaction"]
> [Plantas de CAF migrar zona de aterrissagem](./migrate-landing-zone.md)
