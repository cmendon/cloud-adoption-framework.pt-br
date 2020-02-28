---
title: Riscos de negócios da aceleração de implantação
description: Use a estrutura de adoção de nuvem para o Azure para entender os riscos de negócios da disciplina de aceleração de implantação, que pode ser usada na estratégia de governança.
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: dc80f889442fd7139e9f3930da1304d1a25e3e98
ms.sourcegitcommit: 10637acba8c857a6f5aa8c4a80c0649903f60402
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78171422"
---
# <a name="deployment-acceleration-motivations-and-business-risks"></a>Motivações de aceleração de implantação e os riscos de negócios

Este artigo aborda os motivos que os clientes normalmente adotam uma disciplina de Aceleração de implantação dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios que conduzem as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="deployment-acceleration-relevancy"></a>Relevância de aceleração da implantação

Em sistemas locais normalmente são implantados usando imagens de linha de base ou scripts de instalação. A configuração adicional é geralmente necessária, o que pode envolver várias etapas ou intervenção humana. Esses processos manuais são propensos a erro e geralmente resultam em "descompassos de configuração", que exigem tarefas demoradas de solução de problemas e correção.

A maioria dos recursos do Azure pode ser implantada e configurada manualmente por meio do portal do Azure. Esta abordagem pode ser suficiente para suas necessidades quando houver apenas alguns recursos para gerenciar. No entanto, à medida que seu estado de nuvem cresce, sua organização deve começar a integrar a automação em seus processos de implantação para garantir que seus recursos de nuvem evitem descompassos de configuração ou outros problemas introduzidos por processos manuais. A adoção de uma abordagem DevOps ou [DevSecOps](https://www.microsoft.com/en-us/securityengineering/devsecops) geralmente é a melhor maneira de gerenciar suas implantações à medida que os esforços de adoção de nuvem amadurecem.

<!-- "en-us" location is required for the URL above. -->

Um plano de aceleração de implantação robusto garante que seus recursos de nuvem sejam implantados, atualizados, configurados corretamente e consistentemente e que permaneçam assim. A maturidade da sua estratégia de aceleração de implantação também pode ser um fator importante na sua [estratégia de Gerenciamento de Custos](../cost-management/index.md). O provisionamento automatizado e a configuração de seus recursos de nuvem permitem que você reduza ou desaloque os recursos quando a demanda estiver baixa ou limite de tempo, portanto, você paga apenas pelos recursos conforme necessário.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de Aceleração de implantação tenta abordar os seguintes riscos de negócios. Durante a adoção da nuvem, monitore cada uma das seguintes opções de relevância:

- **Interrupção do serviço:** A falta de processos de implantação reproduzíveis previsíveis ou alterações não gerenciadas nas configurações do sistema podem interromper as operações normais e pode resultar em perda de produtividade ou perda de negócios.
- **Sobreexecuções de custo:** Alterações inesperadas na configuração de recursos do sistema podem dificultar a identificação da causa raiz dos problemas, aumentando os custos de desenvolvimento, operações e manutenção.
- **Ineficiências organizacionais:** As barreiras entre desenvolvimento, operações e equipes de segurança podem causar inúmeros desafios para a adoção efetiva de tecnologias de nuvem e o desenvolvimento de um modelo de governança de nuvem unificado.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Métricas, indicadores e tolerância a risco](./metrics-tolerance.md)
