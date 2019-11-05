---
title: 'Inovação em nuvem: prever e influenciar'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação na nuvem – prever e influenciar
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 8aa0e1d86bb679241bc8e769bb8a09fc436c6906
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565581"
---
# <a name="predict-and-influence"></a>Prever e influenciar

Há duas classes de aplicativos na economia digital: *históricas* e *preditivas*. Muitas necessidades do cliente podem ser atendidas somente usando dados históricos, incluindo dados quase em tempo real. A maioria das soluções se concentra principalmente na agregação de dados no momento. Em seguida, eles processam e compartilham esses dados de volta para o cliente na forma de uma experiência digital ou de ambiente.

Como a modelagem preditiva se torna mais econômica e prontamente disponível, os clientes exigem experiências de atendimento antecipado que levam a melhores decisões e ações. No entanto, essa demanda nem sempre sugere uma solução preditiva. Na maioria dos casos, um modo de exibição histórico pode fornecer dados suficientes para capacitar o cliente a tomar uma decisão por conta própria.

Infelizmente, os clientes geralmente adotam uma exibição myopic que leva a decisões com base em seus arredores imediatos e Sphere de influência. À medida que as opções e decisões crescem em número e impacto, essa exibição myopic pode não atender às necessidades do cliente. Ao mesmo tempo, como uma hipótese é comprovada em escala, a empresa que fornece a solução pode ver em milhares ou milhões de decisões de clientes. Essa abordagem de visão geral torna possível ver padrões amplos e os impactos desses padrões. A capacidade preditiva é um investimento inteligente quando uma compreensão desses padrões é necessária para tomar decisões que melhor atendam ao cliente.

## <a name="examples-of-predictions-and-influence"></a>Exemplos de previsões e influência

Uma variedade de aplicativos e experiências de ambiente usam dados para fazer previsões:

- **Comércio eletrônico:** Com base no que outros consumidores semelhantes compraram, um site de comércio eletrônico sugere produtos que podem valer a pena adicionar ao seu carrinho.
- **Realidade ajustada:** A IoT oferece instâncias mais avançadas de funcionalidade preditiva. Por exemplo, um dispositivo em uma linha de assembly detecta um aumento na temperatura de um computador. Um modelo de previsão baseado em nuvem determina como responder. Com base nessa previsão, outro dispositivo retarda a linha do assembly até que a máquina possa ser fria.
- **Produtos de consumo:** Celulares, Smart Homes, até mesmo seu carro, todos usam recursos de previsão, que eles exploram para sugerir o comportamento do usuário com base em fatores como o local ou a hora do dia. Quando uma previsão e a hipótese inicial são alinhadas, a previsão leva a ação. Em um estágio muito maduro, esse alinhamento pode tornar produtos como um carro de autoatendimento uma realidade.

## <a name="develop-predictive-capabilities"></a>Desenvolver recursos de previsão

As soluções que fornecem de forma consistente recursos de previsão precisos normalmente incluem cinco características principais: *dados*, *ideias*, *padrões*, *previsões*e *interações*. Cada aspecto é necessário para desenvolver recursos de previsão. Como todas as grandes inovações, o desenvolvimento de recursos de previsão exige um [compromisso com a iteração](./index.md#commitment-to-iteration). Em cada iteração, uma ou mais das características a seguir são amadurecedas para validar as subações de clientes cada vez mais complexas.

![Etapas para recursos de previsão](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Se a hipótese do cliente desenvolvida no [Build com o cliente empatia](./build.md) inclui recursos de previsão, os princípios descritos podem se aplicar. No entanto, os recursos de previsão exigem um investimento significativo de tempo e energia. Quando os recursos de previsão são [picos técnicos](./build.md#reduce-complexity-and-delay-technical-spikes), em oposição a uma fonte de valor real do cliente, sugerimos que você adie previsões até que as subpartes do cliente tenham sido validadas em escala.

## <a name="data"></a>Dados

Os dados são a mais elementar das características mencionadas anteriormente. Cada uma das disciplinas para o desenvolvimento de invenções digitais gera dados. Esses dados, é claro, contribuem para o desenvolvimento de previsões. Para obter mais diretrizes sobre maneiras de obter dados em uma solução preditiva, consulte [dados do democratizando](./data.md) e [interagindo com dispositivos](./devices.md).

Uma variedade de fontes de dados pode ser usada para fornecer recursos de previsão:

## <a name="insights"></a>Insights

Os especialistas no assunto aproveitam os dados sobre as necessidades e os comportamentos dos clientes para desenvolver informações de negócios básicas de um estudo de dados brutos. Essas informações podem identificar ocorrências dos comportamentos de clientes desejados (ou, como alternativa, resultados indesejáveis). Durante as iterações nas previsões, essas informações podem ajudar a identificar possíveis correlações que poderiam, em última análise, gerar resultados positivos. Para obter orientação sobre como habilitar especialistas no assunto para desenvolver informações, consulte [democratizando data](./data.md).

## <a name="patterns"></a>Padrões

As pessoas sempre tentaram detectar padrões em grandes volumes de dados. Os computadores foram projetados para essa finalidade. O Machine Learning acelera essa quest detectando precisamente tais padrões, uma habilidade que compreende o modelo de aprendizado de máquina. Esses padrões são aplicados por meio de algoritmos de aprendizado de máquina para prever resultados quando um novo conjunto de dados é inserido nos algoritmos.

Usando percepções como ponto de partida, o Machine Learning desenvolve e aplica modelos de previsão para aproveitar os padrões nos dados. Por meio de várias iterações de treinamento, teste e adoção, esses modelos e algoritmos podem prever resultados futuros com precisão.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) é o serviço nativo de nuvem no Azure para criar e treinar modelos com base em seus dados. Essa ferramenta também inclui um [fluxo de trabalho para acelerar o desenvolvimento de algoritmos de aprendizado de máquina](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Esse fluxo de trabalho pode ser usado para desenvolver algoritmos por meio de uma interface visual ou Python.

Para modelos de aprendizado de máquina mais robustos, os [serviços de ml no Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fornecem uma plataforma de aprendizado de máquina criada em clusters de Apache Hadoop. Essa abordagem permite um controle mais granular dos clusters subjacentes, armazenamento e nós de computação. O Azure HDInsight também oferece integração mais avançada por meio de ferramentas como scaler e Sparkr para criar previsões com base em dados integrados e ingeridos, mesmo trabalhando com dados de um fluxo. A [solução de previsão de atraso de voo](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) demonstra cada um desses recursos avançados quando usada para prever atrasos de voo com base em condições de clima. A solução HDInsight também permite controles corporativos, como segurança de dados, acesso à rede e monitoramento de desempenho para colocar em operação os padrões.

## <a name="predictions"></a>Previsões

Depois que um padrão é criado e treinado, você pode aplicá-lo por meio de APIs, o que pode fazer previsões durante a entrega de uma experiência digital. A maioria dessas APIs é criada a partir de um modelo bem treinado com base em um padrão em seus dados. À medida que mais clientes implantam cargas de trabalho diárias na nuvem, as APIs de previsão usadas pelos provedores de nuvem levam a uma adoção sempre mais rápida.

Os [Serviços cognitivas do Azure](https://docs.microsoft.com/azure/cognitive-services) são um exemplo de uma API preditiva criada por um fornecedor de nuvem. Esse serviço inclui APIs preditivas para moderação de conteúdo, detecção de anomalias e sugestões para personalizar o conteúdo. Essas APIs estão prontas para uso e se baseiam em padrões de conteúdo bem conhecidos, que a Microsoft usou para treinar modelos. Cada uma dessas APIs faz previsões com base nos dados que você feedu na API.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning) permite implantar algoritmos personalizados, que você pode criar e treinar com base apenas em seus próprios dados. Saiba mais sobre como implantar previsões com [Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

[Configurar clusters HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) discute os processos para expor previsões desenvolvidas para serviços de ml no Azure HDInsight.

## <a name="interactions"></a>Interações

Depois que uma previsão é disponibilizada por meio de uma API, você pode usá-la para influenciar o comportamento do cliente. Essa influência assume a forma de interações. Uma interação com um algoritmo de aprendizado de máquina ocorre em suas outras experiências digitais ou de ambiente. À medida que os dados são coletados por meio do aplicativo ou da experiência, eles são executados por meio dos algoritmos de aprendizado de máquina. Quando o algoritmo prevê um resultado, essa previsão pode ser compartilhada de volta com o cliente por meio da experiência existente.

Saiba mais sobre como criar uma experiência de ambiente por meio de uma [solução de realidade ajustada](./devices.md#adjusted-reality).

## <a name="next-steps"></a>Próximas etapas

Tendo se familiarizado com as [disciplinas de invenção](./invention.md) e com a [metodologia inovar](./index.md), agora você está pronto para aprender a [criar com empatia de clientes](./build.md).

> [!div class="nextstepaction"]
> [Compilar com empatia](./build.md)
