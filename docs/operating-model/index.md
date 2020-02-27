---
title: Introdução ao modelo operacional
description: Entenda o modelo operacional do Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.custom: operating-model
ms.openlocfilehash: 093f404ce4e8a5a9c5f60b5ee3bb81064ba5b3f8
ms.sourcegitcommit: 10f687bb1316db509fc1a3dbde72e107a467d72a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77629276"
---
# <a name="establish-an-operating-model-for-the-cloud"></a>Estabelecer um modelo operacional para a nuvem

A adoção de nuvem é um esforço iterativo que se concentra no que você faz na nuvem. A estratégia de nuvem descreve a transformação digital para guiar os programas de negócios como várias equipes executando projetos de adoção. O planejamento e a preparação ajudam a garantir o sucesso de cada um desses elementos importantes. Todas as etapas de adoção de nuvem são equivalentes a projetos tangíveis, com objetivos, cronogramas e orçamentos gerenciáveis.

Esses esforços de adoção são relativamente fáceis de acompanhar e medir, mesmo quando envolvem várias iterações e versões projetadas. Cada fase do ciclo de vida de adoção é importante. Cada fase está sujeita a possíveis empecilhos em restrições de negócios, de cultura e de tecnologia. Mas cada fase depende muito do modelo operacional subjacente.

**Se a adoção descreve o que você está fazendo, o modelo operacional define o quem e o como subjacentes que permitem a adoção.**

"A cultura come a estratégia no café da manhã." O modelo operacional é a materialização da cultura de TI, capturada em vários processos mensuráveis. Quando a nuvem é alimentada por um modelo de operação forte, a cultura impulsionará a estratégia, acelerando a adoção e a realização dos valores de negócios. Por outro lado, quando a adoção é bem-sucedida mas não há nenhum modelo operacional, o retorno pode ser impressionante, mas de vida muito curta. Para sucesso a longo prazo, é vital que os modelos de adoção e de operação avancem em paralelo.

## <a name="establish-your-operating-model"></a>Estabelecer seu modelo operacional

Os modelos operacionais atuais podem ser dimensionados para apoiar a adoção da nuvem. Um modelo operacional moderno ajudará você a remover obstáculos não técnicos à adoção da nuvem.

Esta seção do Cloud Adoption Framework fornece um modelo operacional acionável para orientar as decisões não técnicas. Esse modelo operacional consiste em três metodologias para auxiliar na criação de seu próprio modelo operacional na nuvem:

- [Controlar](../govern/index.md): Garanta a consistência entre os esforços de adoção. Alinhe-os com os requisitos de governança ou conformidade para manter um ambiente entre nuvens bem gerenciado.
- [Gerenciar](../manage/index.md): alinhe processos em andamento para o gerenciamento operacional da tecnologia para maximizar a obtenção de valor e minimizar as interrupções.
- [Organizar](../organize/index.md): À medida que o modelo operacional amadurecer, o mesmo ocorrerá com a organização de várias equipes e funcionalidades que dão suporte ao modelo operacional.

## <a name="align-operating-models"></a>Alinhe modelos operacionais

A nuvem e a economia digital expuseram a necessidade de vários modelos operacionais. Às vezes, essa necessidade é orientada por um requisito de dar suporte a várias nuvens públicas. Mais comumente, a necessidade é realçada pela transição do local para a nuvem. Em qualquer cenário, é importante alinhar os modelos operacionais para obter o máximo de desempenho e o mínimo de redundância.

Os analistas estão prevendo a adoção de um modelo multinuvem em grandes volumes. Muitos clientes estão migrando segundo essa previsão. No entanto, os clientes estão relatando desafios significativos para operar com várias nuvens. A duplicação de recursos, processos, habilidades e tecnologias resulta em aumento de custos, não nas economias prometidas pelas previsões de nuvem. Para evitar essa tendência, os clientes devem adotar um modelo operacional especializado. Ao alinhar modelos operacionais, sempre deve haver um **modelo operacional geral**. Os outros **modelos operacionais especializados** seriam usados em cenários específicos para dar suporte aos desvios do modelo padrão.

- **Modelo operacional geral:** O modelo operacional geral se alinha a uma única plataforma de nuvem pública ou privada. As operações dessa plataforma definem padrões, políticas e processos operacionais. Esse modelo operacional deve ser o principal meio de impulsionar a estratégia de mudança em direção à nuvem. Nesse modelo, a meta é usar o provedor de nuvem primário para a maior parte da adoção de nuvem.

- **Modelo operacional especializado:** Resultados de negócios específicos podem ser uma melhor opção para um provedor de nuvem alternativo. Quando um caso comercial atraente está presente, os padrões, as políticas e os processos do modelo operacional geral são aplicados ao novo provedor de nuvem, mas, em seguida, são modificados para se ajustarem ao caso de uso especializado.

Se o Azure for a principal plataforma de escolha, os guias e as práticas recomendadas em cada uma das seções de modelo operacional listadas acima se mostrarão valiosas na criação de seu modelo operacional. Mas essa estrutura reconhece que nem todos os nossos leitores se comprometeram com o uso do Azure como a plataforma principal. Para acomodar esse público mais amplo, o conteúdo da teoria em cada seção pode ser aplicado a modelos operacionais de nuvem pública ou privada com resultados semelhantes.

## <a name="next-steps"></a>Próximas etapas

A governança é, normalmente, o primeiro passo para estabelecer um modelo operacional para a nuvem.

> [!div class="nextstepaction"]
> [Saiba mais sobre a governança de nuvem](../govern/index.md)
