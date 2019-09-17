---
title: Motivações e riscos de negócios que direcionam a aceleração da implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre a disciplina de Aceleração de implantação como parte de uma estratégia de governança de nuvem.
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: feaf5a7f0f2622c2b2289fe81315ea9ccf2ada4e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030889"
---
# <a name="deployment-acceleration-motivations-and-business-risks"></a>Motivações de aceleração de implantação e os riscos de negócios

Este artigo aborda os motivos que os clientes normalmente adotam uma disciplina de Aceleração de implantação dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios que conduzem as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="is-deployment-acceleration-relevant"></a>A aceleração de implantação é relevante?

Em sistemas locais normalmente são implantados usando imagens de linha de base ou scripts de instalação. A configuração adicional é geralmente necessária, o que pode envolver várias etapas ou intervenção humana. Esses processos manuais são propensos a erro e geralmente resultam em "descompassos de configuração", que exigem tarefas demoradas de solução de problemas e correção.

A maioria dos recursos do Azure pode ser implantada e configurada manualmente por meio do portal do Azure. Esta abordagem pode ser suficiente para suas necessidades quando houver apenas alguns recursos para gerenciar. No entanto, à medida que seu estado de nuvem cresce, sua organização deve começar a integrar a automação em seus processos de implantação para garantir que seus recursos de nuvem evitem descompassos de configuração ou outros problemas introduzidos por processos manuais. A adoção de uma abordagem DevOps ou [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) geralmente é a melhor maneira de gerenciar suas implantações à medida que os esforços de adoção de nuvem amadurecem.

<!-- "en-us" location is required for the URL above. -->

Um plano de aceleração de implantação robusto garante que seus recursos de nuvem sejam implantados, atualizados, configurados corretamente e consistentemente e que permaneçam assim. A maturidade da sua estratégia de aceleração de implantação também pode ser um fator importante na sua [estratégia de Gerenciamento de Custos](../cost-management/index.md). O provisionamento automatizado e a configuração de seus recursos de nuvem permitem que você reduza ou desaloque os recursos quando a demanda estiver baixa ou limite de tempo, portanto, você paga apenas pelos recursos conforme necessário.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de Aceleração de implantação tenta abordar os seguintes riscos de negócios. Durante a adoção da nuvem, monitore cada uma das seguintes opções de relevância:

- **Interrupção do serviço:** Falta de processos de implantação repetíveis previsíveis ou mudanças inalteradas para configurações do sistema podem interromper as operações normais e podem resultar em perda de produtividade ou perda de negócios.
- **Sobreexecuções de custo:** Alterações inesperadas na configuração de recursos do sistema podem tornar mais difícil a identificação da causa raiz, elevar os custo de desenvolvimento, operações e manutenção.
- **Ineficiências organizacionais:** Barreiras entre o desenvolvimento, operações e as equipes de segurança podem causar vários desafios para a adoção efetiva das tecnologias de nuvem e o desenvolvimento de um modelo de governança de nuvem unificada.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Métricas, indicadores e tolerância a risco](./metrics-tolerance.md)
