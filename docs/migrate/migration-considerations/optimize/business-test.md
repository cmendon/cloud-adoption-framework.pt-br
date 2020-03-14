---
title: Diretrizes de teste de negócios durante a migração
description: Saiba como os testes de negócios são usados para solicitar a validação de que o desempenho da solução está em linha com expectativas e não impede os processos de negócios.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 675eda4aeb2109c21c2e3f47a100a985fd6e2861
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311738"
---
# <a name="guidance-for-business-testing-uat-during-migration"></a>Diretrizes para teste de negócios (UAT) durante a migração

Tradicionalmente visto como uma função de TI, o teste de aceitação do usuário durante uma transformação empresarial pode ser organizado exclusivamente pela TI. No entanto, essa função é geralmente executada de forma mais efetiva como uma função de negócios. Em seguida, a TI fornece suporte a essa atividade empresarial facilitando os testes, desenvolvendo planos de testes e automatizando testes quando possível. Embora a TI geralmente possa servir como substituta para o teste, não há nenhuma substituição para uma observação em primeira mão de usuários reais que tentam aproveitar uma nova solução no contexto de um processo de negócios real ou replicado.

> [!NOTE]
> Quando disponível, o teste automatizado é um meio muito mais eficaz e eficiente de testar qualquer sistema. Mas as migrações de nuvem geralmente se concentram bastante em sistemas herdados ou em sistemas de produção menos estáveis. Normalmente esses sistemas não são gerenciados por testes automatizados abrangentes e bem mantidos. Este artigo pressupõe que esses testes não estão disponíveis no momento da migração.

Em segundo lugar, o teste automatizado testa as alterações de processo e tecnologia por usuários avançados. Usuários avançados são aqueles que normalmente executam um processo real que exige interações com uma ferramenta ou um conjunto de ferramentas de tecnologia. Podem ser representados por um cliente externo usando um site de comércio eletrônico para adquirir bens ou serviços. Usuários avançados também podem ser representados por um grupo de funcionários que executam um processo de negócios, como um Call Center que atende aos clientes e registra suas experiências.

O objetivo do teste de negócios é solicitar a validação de usuários avançados para certificar que a nova solução funciona de acordo com as expectativas e não impede os processos de negócios. Se essa meta não for atendida, o teste de negócios servirá como um loop de comentários que pode ajudar a definir por que e como a carga de trabalho não atendeu às expectativas.

## <a name="business-activities-during-business-testing"></a>Atividades empresariais durante o teste de negócios

Durante testes de negócios, a primeira iteração é controlada manualmente diretamente com os clientes. Essa é a forma mais simples, mas mais demorada, do loop de comentários.

- **Identifique os usuários avançados.** A empresa geralmente sabe quais são os usuários avançados mais afetados por uma mudança técnica.
- **Alinhe e prepare os usuários avançados.** Certifique-se de que os usuários avançados compreendam os objetivos de negócios, os resultados desejados e as alterações esperadas nos processos de negócios. Prepare os usuários e a estrutura de gerenciamento para o processo de teste.
- **Participe da interpretação do loop de comentários.** Ajude a equipe de TI a entender o impacto de vários pontos dos comentários dos usuários avançados.
- **Esclareça a alteração do processo.** Quando a transformação puder disparar uma alteração nos processos de negócios, comunique essa alteração e seus impactos no downstream.
- **Priorize os comentários.** Ajude a equipe de TI a priorizar os comentários com base no impacto nos negócios.

Às vezes, a TI pode empregar analistas ou proprietários de produtos que podem servir como proxies para atividades discriminadas dos testes de negócios. No entanto, a participação nos negócios é altamente incentivada e provavelmente produzirá resultados favoráveis nos negócios.

## <a name="it-activities-during-business-testing"></a>Atividades de TI durante o teste de negócios

A TI serve como um dos destinatários da saída do teste de negócios. Os loops de comentários expostos durante o teste de negócios eventualmente se tornam itens de trabalho que definem alterações técnicas ou do processo. Como um destinatário, espera-se que a TI auxilie na facilitação, na coleta de comentários e no gerenciamento das ações técnicas resultantes. As atividades típicas que a TI realiza durante os testes de negócios incluem:

- Fornecer estrutura e logística para testes de negócios.
- Auxiliar na facilitação durante o teste.
- Fornecer um meio e um processo para registrar comentários.
- Ajudar a empresa a priorizar e validar os comentários.
- Desenvolver planos de ação para alterações técnicas.
- Identificar os testes automatizados existentes que podem simplificar o teste para os usuários avançados.
- Para alterações que possam exigir a repetição da implantação ou de testes, estude os processos de testes, defina os parâmetros de comparação e projete a automação para simplificar ainda mais os testes de usuários avançados.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Em conjunto com os testes de negócios, a [otimização dos ativos migrados](./optimize.md) pode refinar os custos e o desempenho da carga de trabalho.

> [!div class="nextstepaction"]
> [Parâmetros de comparação e redimensionamento de ativos de nuvem](./optimize.md)
