---
title: Racionalização de nuvem
description: Saiba mais sobre a racionalização de nuvem, o processo de avaliação de ativos para determinar a melhor maneira de migrar ou modernizar cada ativo na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/16/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: 74a384cd3bf5688979a848423e0740ff15f08a34
ms.sourcegitcommit: 10637acba8c857a6f5aa8c4a80c0649903f60402
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78170147"
---
# <a name="cloud-rationalization"></a>Racionalização de nuvem

A racionalização na nuvem é o processo de avaliação de ativos para determinar a melhor maneira de migrar ou modernizar cada ativo na nuvem. Para obter mais informações sobre o processo de racionalização, consulte [o que é um espaço digital?](./index.md).

## <a name="rationalization-context"></a>Contexto de racionalização

A "cinco RS de racionalização" listada neste artigo são uma ótima maneira de identificar um estado futuro potencial para qualquer carga de trabalho considerada como um candidato à nuvem. No entanto, esse processo de rotulação deve ser colocado no contexto correto antes de tentar racionalizar um ambiente. Examine os mitos a seguir para fornecer esse contexto:

- **Mito: é fácil tomar decisões de racionalização no início do processo.** A racionalização precisa exige um profundo conhecimento da carga de trabalho e dos ativos associados (aplicativos, VMs e dados). O mais importante é que as decisões de racionalização precisas levam tempo. É recomendável usar um [processo de racionalização incremental](./rationalize.md#incremental-rationalization).

- **Mito: a adoção de nuvem precisa aguardar que todas as cargas de trabalho sejam racionalizadas.** Racionalizar um portfólio de ti inteiro ou até mesmo um único datacenter pode atrasar a realização do valor comercial em meses ou até mesmo anos. A racionalização completa deve ser evitada quando possível. Em vez disso, use o [poder de 10 abordagens para liberar o planejamento](./rationalize.md#release-planning) para tomar decisões inteligentes sobre as próximas 10 cargas de trabalho que são destinadas à adoção da nuvem.

- **Mito: a justificativa de negócios precisa esperar que todas as cargas de trabalho sejam racionalizadas.** Para desenvolver uma justificativa de negócios para um esforço de adoção de nuvem, faça algumas suposições básicas no nível do portfólio. Quando as motivações estão alinhadas à inovação, suponha a rearquitetura. Quando as motivações estiverem alinhadas à migração, suponha que o rehospede. Essas suposições podem acelerar o processo de justificativa de negócios. As suposições são desafiadas e os Orçamentos refinados durante a fase de avaliação dos ciclos de adoção de cada carga de trabalho.

Agora, examine os cinco RS de racionalização a seguir para se familiarizar com o processo de longo prazo. Ao desenvolver seu plano de adoção de nuvem, escolha a opção que melhor se alinha com suas motivações, resultados de negócios e ambiente de estado atual. A meta na racionalização de imóveis é definir uma linha de base, não para racionalizar cada carga de trabalho.

## <a name="the-five-rs-of-rationalization"></a>Os cinco RS de racionalização

Os cinco RS de racionalização listados aqui descrevem as opções mais comuns de racionalização.

## <a name="rehost"></a>Hospedar novamente

Também conhecida como migração de comparação de _precisão e deslocamento_ , um esforço de rehospedagem move um ativo de estado atual para o provedor de nuvem escolhido, com alteração mínima na arquitetura geral.

Os drivers comuns podem incluir:

- Reduzindo despesas de capital
- Liberando espaço do datacenter
- Obtendo rápido retorno sobre o investimento na nuvem

Fatores de análise quantitativa:

- Tamanho da VM (CPU, memória, armazenamento)
- Dependências (tráfego de rede)
- Compatibilidade de ativo

Fatores de análise qualitativa:

- Tolerância à alteração
- Prioridades dos negócios
- Eventos comerciais críticos
- Dependências de processo

## <a name="refactor"></a>Refatoração

As opções de PaaS (plataforma como serviço) podem reduzir os custos operacionais associados a vários aplicativos. É uma boa ideia refatorar ligeiramente um aplicativo para se ajustar a um modelo baseado em PaaS.

"Refactor" também se refere ao processo de desenvolvimento de aplicativos de refatoração de código para permitir que um aplicativo seja entregue em novas oportunidades de negócios.

Os drivers comuns podem incluir:

- Atualizações mais rápidas e mais curtas
- Portabilidade do código
- Maior eficiência na nuvem (recursos, velocidade, custo, operações gerenciadas)

Fatores de análise quantitativa:

- Tamanho do ativo de aplicativo (CPU, memória, armazenamento)
- Dependências (tráfego de rede)
- Tráfego do usuário (exibições de página, hora na página, tempo de carregamento)
- Plataforma de desenvolvimento (linguagens, plataforma de dados, serviços de camada intermediária)
- Banco de dados (CPU, memória, armazenamento, versão)

Fatores de análise qualitativa:

- Investimento contínuo nos negócios
- Opções/linhas do tempo de intermitência
- Dependências de processo comercial

## <a name="rearchitect"></a>Recriação da arquitetura

Alguns aplicativos de envelhecimento não são compatíveis com os provedores de nuvem devido às decisões arquitetônicas que foram feitas quando o aplicativo foi criado. Nesses casos, o aplicativo pode precisar ser rearquitetado antes da transformação.

Em outros casos, os aplicativos que são compatíveis com a nuvem, mas não são nativos da nuvem, podem criar eficiências de custo e eficiências operacionais rearquitetando a solução em um aplicativo nativo de nuvem.

Os drivers comuns podem incluir:

- Agilidade e escala do aplicativo
- Facilidade da adoção de novos recursos de nuvem
- Combinação de pilhas de tecnologia

Fatores de análise quantitativa:

- Tamanho do ativo de aplicativo (CPU, memória, armazenamento)
- Dependências (tráfego de rede)
- Tráfego do usuário (exibições de página, hora na página, tempo de carregamento)
- Plataforma de desenvolvimento (linguagens, plataforma de dados, serviços de camada intermediária)
- Banco de dados (CPU, memória, armazenamento, versão)

Fatores de análise qualitativa:

- Investimentos comerciais em expansão
- Custos operacionais
- Possíveis loops de comentários e investimentos DevOpss.

## <a name="rebuild"></a>Recriar

Em alguns cenários, o Delta que deve ser superado para carregar um aplicativo pode ser muito grande para justificar um investimento adicional. Isso é especialmente verdadeiro para aplicativos que atendem anteriormente às necessidades de um negócio, mas que agora não têm suporte ou estão desalinhados com os processos de negócios atuais. Nesse caso, uma nova base de código é criada para se alinhar com uma abordagem [nativa de nuvem](https://azure.microsoft.com/overview/cloudnative) .

Os drivers comuns podem incluir:

- Acelerar a inovação
- Compilar aplicativos mais rápido
- Reduzir o custo operacional

Fatores de análise quantitativa:

- Tamanho do ativo de aplicativo (CPU, memória, armazenamento)
- Dependências (tráfego de rede)
- Tráfego do usuário (exibições de página, hora na página, tempo de carregamento)
- Plataforma de desenvolvimento (linguagens, plataforma de dados, serviços de camada intermediária)
- Banco de dados (CPU, memória, armazenamento, versão)

Fatores de análise qualitativa:

- Redução da satisfação do usuário final
- Processos de negócio limitados pela funcionalidade
- Possíveis ganhos de custo, experiência ou receita

## <a name="replace"></a>Substitua

As soluções são normalmente implementadas usando a melhor tecnologia e abordagem disponíveis no momento. Às vezes, aplicativos SaaS (software como serviço) podem fornecer toda a funcionalidade necessária para o aplicativo hospedado. Nesses cenários, uma carga de trabalho pode ser agendada para substituição futura, removendo-a efetivamente do esforço de transformação.

Os drivers comuns podem incluir:

- Padronização em relação às práticas recomendadas do setor
- Acelerando a adoção de abordagens controladas por processos empresariais
- Realocando investimentos de desenvolvimento em aplicativos que criam vantagens ou diferenciações competitivas

Fatores de análise quantitativa:

- Reduções de custo operacional geral
- Tamanho da VM (CPU, memória, armazenamento)
- Dependências (tráfego de rede)
- Ativos para desativação
- Banco de dados (CPU, memória, armazenamento, versão)

Fatores de análise qualitativa:

- Análise de custo-benefício da arquitetura atual versus a solução de SaaS
- Mapas de processo de negócios
- Esquemas de dados
- Processos personalizados ou automatizados

## <a name="next-steps"></a>Próximas etapas

Coletivamente, você pode aplicar esses cinco RS de racionalização a um espaço digital para ajudá-lo a tomar decisões de racionalização sobre o estado futuro de cada aplicativo.

> [!div class="nextstepaction"]
> [O que é uma propriedade digital?](./index.md)
