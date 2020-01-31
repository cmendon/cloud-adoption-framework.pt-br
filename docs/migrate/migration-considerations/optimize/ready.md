---
title: Preparar um aplicativo migrado para promoção de produção
description: Um processo na migração na nuvem que se concentra nas tarefas de migrar cargas de trabalho para a nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: f3aad7a2b7c592478f9d48a50dc96d5fee607dc8
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76801606"
---
# <a name="prepare-a-migrated-application-for-production-promotion"></a>Preparar um aplicativo migrado para promoção de produção

Depois que uma carga de trabalho é promovida, o tráfego do usuário de produção é encaminhado para os ativos migrados. As atividades de preparação fornecem uma oportunidade de preparar a carga de trabalho para esse tráfego. Veja a seguir algumas considerações tecnológicas e empresariais para ajudar a orientar as atividades de preparação.

## <a name="validate-the-business-change-plan"></a>Validar o plano de mudança empresarial

A transformação ocorre quando os usuários ou clientes empresariais tiram proveito de uma solução técnica para executar processos que conduzem os negócios. A preparação é uma boa oportunidade para validar o [plano de mudança empresarial](./business-change-plan.md) e garantir um treinamento adequado para as equipes empresariais e técnicas envolvidas. Em particular, certifique-se de que os seguintes aspectos relacionados à tecnologia do plano de mudança estejam conectados corretamente:

- O treinamento do usuário final foi concluído (ou pelo menos planejado).
- Todas as janelas de interrupção foram comunicadas e aprovadas.
- Os dados de produção foram sincronizados e validados pelos usuários finais.
- Validar o tempo para promoção e adoção; garantir que as linhas do tempo e as alterações foram comunicadas aos usuários finais.

## <a name="final-technical-readiness-tests"></a>Testes finais de reparação técnica

*Pronto* é a última etapa antes do lançamento para a produção. Isso significa que é também a última chance de testar a carga de trabalho. A seguir são descritos alguns testes sugeridos durante esta fase:

- **Teste de isolamento de rede.** Teste e monitore o tráfego de rede para garantir o isolamento adequado e que não haja nenhuma vulnerabilidade de rede inesperada. Além disso, valide que qualquer roteamento de rede a ser interrompido durante a substituição não esteja apresentando tráfego inesperado.
- **Teste de dependência.** Certifique-se de que todas as dependências do aplicativo de carga de trabalho foram migradas e estão acessíveis dos ativos migrados.
- **Teste de BCDR (continuidade dos negócios e recuperação de desastres).** Valide se todos os SLAs de backup e recuperação foram estabelecidos. Se possível, execute uma recuperação completa dos ativos da solução de BCDR.
- **Teste de rota do usuário final.** Valide os padrões de tráfego e o roteamento do tráfego do usuário final. Certifique-se de que o desempenho da rede esteja alinhado às expectativas.
- **Verificação de desempenho final.** Certifique-se de que o teste de desempenho tenha sido concluído e aprovado pelos usuários finais. Execute qualquer teste de desempenho automatizado.

## <a name="final-business-validation"></a>Validação empresarial final

Após o plano de mudança empresarial e a prontidão técnica tiverem sido validados, as etapas finais a seguir poderão concluir a validação empresarial:

- **Validação de custo (planejado versus real).** É provável que os testes produzam alterações no dimensionamento e na arquitetura. Verifique se o preço real da implantação ainda se alinha ao plano original.
- **Comunicar e executar o plano de substituição.** Antes da substituição, comunique a substituição e execute-a.

## <a name="next-steps"></a>Próximos passos

Após todas as atividades de preparação terem sido concluídas, é hora de [promover a carga de trabalho](./promote.md).

> [!div class="nextstepaction"]
> [O que é necessário para promover um recurso migrado para produção?](./promote.md)
