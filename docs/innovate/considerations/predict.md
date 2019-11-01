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
ms.openlocfilehash: 83165e21882b4979d0fb3b104fa4f2c12aed326c
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73239457"
---
# <a name="predict-and-influence"></a>Prever e influenciar

Há duas classes de aplicativos na economia digital: históricas e preditivas. Muitas necessidades do cliente podem ser atendidas somente usando dados históricos, incluindo dados quase em tempo real. A maioria das soluções se concentram principalmente na agregação de dados, no momento. Em seguida, eles processam e compartilham esses dados de volta para o cliente, na forma de uma experiência digital ou de ambiente.

À medida que a modelagem preditiva se torna mais econômica e prontamente disponível, as experiências de passagem de encaminhamento de clientes levam a melhores decisões e ações. No entanto, essa demanda nem sempre precisa levar a uma solução preditiva. Na maioria dos cenários, um modo de exibição histórico pode fornecer dados suficientes para capacitar o cliente a tomar uma decisão por conta própria.

Infelizmente, os clientes têm uma exibição myopic que leva a decisões com base em seus arredores imediatos e Sphere de influência. À medida que as opções e as decisões crescem em números e impacto, essa exibição myopic pode não levar à necessidade de ser atendida pelo cliente. Ao mesmo tempo, como uma hipótese é comprovada em escala, a empresa que fornece a solução pode ver em milhares ou milhões de decisões de clientes. É possível ver os padrões e os impactos desses padrões. A capacidade preditiva é um investimento inteligente, quando uma compreensão desses padrões é necessária para tomar decisões que atendam às necessidades dos clientes.

## <a name="examples-of-predictions-and-influence"></a>Exemplos de previsões e influência

O uso de dados para fazer previsões pode ser visto em vários aplicativos e experiências de ambiente.

- **comércio eletrônico:** Os itens sugeridos são um exemplo de previsão. Com base no que os outros compraram juntos, o site pode sugerir produtos que podem valer a pena adicionar ao seu carrinho.
- **Realidade ajustada:** A IoT oferece exemplos mais avançados. Um dispositivo em uma linha de assembly detecta um aumento na temperatura de máquinas. Um modelo de previsão baseado em nuvem determina como responder. Com base nessa previsão, outro dispositivo é instruído a reduzir a linha do assembly até que a máquina possa ser fria.
- **Produtos de consumo:** Celulares, Smart Homes, até mesmo o carro contém algum grau de recursos preditivas sugerindo atividades com base em fatores como local ou hora do dia. Quando a previsão e a hipótese inicial são alinhadas, essas previsões influenciam seus comportamentos. Quando ambos se tornam muito maduros, a previsão leva a ação, como um carro de autoatendimento.

## <a name="developing-predictive-capabilities"></a>Desenvolvendo recursos de previsão

As soluções que fornecem de forma consistente recursos de previsão precisos normalmente incluem cinco características principais: dados, ideias, padrões, previsões e interações. Cada um é necessário para desenvolver recursos de previsão. Como todas as grandes inovações, o desenvolvimento de recursos de previsão exigirá um [compromisso com a iteração](./index.md#commitment-to-iteration). Em cada iteração, uma ou mais das características a seguir seriam amadurecedas para validar as subações de clientes cada vez mais complexas.

![Etapas para recursos de previsão](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Se a hipótese do cliente desenvolvida no artigo [Build com Customer empatia](./build.md) inclui recursos de previsão, este artigo pode ser aplicável. Mas, os recursos de previsão exigem um investimento significativo de tempo e energia. Quando os recursos de previsão são [picos técnicos](./build.md#reduce-complexity-and-delay-technical-spikes), ao contrário de uma fonte de valor atingível do cliente, é recomendável atrasar previsões até que a hipótese do cliente tenha sido validada em escala.

## <a name="data"></a>Dados

A mais fácil das características acima são os dados. Cada uma das disciplinas anteriores para desenvolver invenções digitais irá gerar dados. Esses dados podem contribuir para o desenvolvimento de previsões. Para obter mais diretrizes sobre maneiras de obter dados em uma solução preditiva, consulte os artigos em [dados do democratizando](./data.md) ou [interagindo com dispositivos](./devices.md).

Várias fontes de dados podem ser usadas para fornecer recursos de previsão:

## <a name="insights"></a>Visões

Os especialistas no assunto aproveitam os dados sobre as necessidades e os comportamentos dos clientes para desenvolver informações de negócios básicas de um estudo dos dados brutos. Essas informações podem identificar ocorrências dos comportamentos do cliente desejados (ou resultados indesejados alternativos). Durante as iterações nas previsões, essas informações podem ajudar a identificar possíveis correlações, o que pode ter um efeito causal em resultados positivos. Para obter orientação sobre como habilitar especialistas no assunto para desenvolver informações, consulte o artigo sobre [dados do democratizando](./data.md).

## <a name="patterns"></a>Padrões

Inerentemente à detecção de padrões em grandes volumes de dados. Os computadores foram projetados para essa finalidade. O Machine Learning acelera essa finalidade por meio da detecção de padrões em uma grande quantidade de dados, conhecida como um modelo de aprendizado de máquina. Esses padrões são aplicados, por meio de algoritmos de aprendizado de máquina, para prever o que acontecerá quando um novo conjunto de pontos de dados for inserido nos algoritmos.

Usando percepções como ponto de partida, o aprendizado de máquina treina e aplica modelos de previsão aos dados para aproveitar os padrões nos dados. Por meio de várias iterações de treinamento, teste e adoção, esses modelos e algoritmos podem prever resultados futuros com precisão.

[Azure Machine Learning serviço](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) é a ferramenta nativa de nuvem no Azure para criar e treinar modelos com base em seus dados. Essa ferramenta também inclui um [fluxo de trabalho para acelerar o desenvolvimento de algoritmos de aprendizado de máquina](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Esse fluxo de trabalho pode ser usado para desenvolver algoritmos usando a interface visual ou Python.

Para modelos de aprendizado de máquina mais robustos, os [serviços de ml no Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fornecem uma plataforma de aprendizado de máquina criada em clusters de Apache Hadoop. Essa abordagem permite um controle mais granular dos clusters subjacentes, armazenamento e nós de computação. Aproveitar o Azure HDInsight também fornece uma integração mais antecipada por meio de ferramentas como o scaler e o Sparkr para criar previsões com base em dados integrados e ingeridos, mesmo trabalhando com dados de um fluxo. A [solução de previsão de atraso de voo](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) demonstra cada um desses recursos avançados para prever atrasos de voo com base em condições de clima. A solução HDInsight também permite controles corporativos, como segurança de dados, acesso à rede e monitoramento de desempenho para colocar em operação os padrões.

## <a name="predictions"></a>Previsões

Depois que um padrão foi criado e treinado, ele pode ser aplicado usando APIs, o que pode fazer previsões durante a entrega de uma experiência digital. A maioria dessas APIs é criada a partir de um modelo bem treinado com base em um padrão dentro de seus dados. Mas, à medida que mais clientes implantam cargas de trabalho comuns na nuvem, os provedores de nuvem são capazes de fornecer APIs de previsão comuns para permitir uma adoção mais rápida de previsões.

Os [Serviços cognitivas do Azure](https://docs.microsoft.com/azure/cognitive-services) são um exemplo de uma compilação de API preditiva por um fornecedor de nuvem. Esse serviço inclui APIs preditivas para moderação de conteúdo, detecção de anomalias ou sugestões para personalizar o conteúdo. Essas APIs estão prontas para uso com base em padrões de conteúdo comuns, que a Microsoft usou para treinar modelos. Cada uma dessas APIs faz previsões com base nos dados que você feedu na API.

[Azure Machine Learning serviço](https://docs.microsoft.com/azure/machine-learning) permite a implantação de algoritmos personalizados, que você pode criar e treinar exclusivamente com base em seus próprios dados. Saiba mais sobre como implantar previsões com Azure Machine Learning, [aqui](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

O artigo sobre a [configuração de clusters HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) aborda os processos de exposição de previsões desenvolvidas para serviços de ml no Azure HDInsight.

## <a name="interactions"></a>Interações

Depois que uma previsão é disponibilizada por meio de uma API, a previsão pode ser usada influenciando os comportamentos do cliente. Essa influência vem na forma de interações. Uma interação com um algoritmo de aprendizado de máquina ocorre em suas outras experiências digitais ou de ambiente. À medida que os dados são coletados por meio do aplicativo ou da experiência, esses dados são executados por meio dos algoritmos de aprendizado de máquina. Quando o algoritmo prevê um resultado, essa previsão pode ser compartilhada de volta com o cliente por meio da experiência existente.

Saiba mais sobre as interações em uma [solução de realidade ajustada](./devices.md#adjusted-reality), para obter mais detalhes sobre a criação de uma interação dentro de uma experiência de ambiente.

## <a name="next-steps"></a>Próximos passos

Com base no conhecimento adquirido em relação às [disciplinas de invenção](./invention.md) na [metodologia inovar](./index.md) , você sabe ter as ferramentas técnicas necessárias para [criar com o empatia](./build.md).

> [!div class="nextstepaction"]
> [Compilar com empatia](./build.md)
