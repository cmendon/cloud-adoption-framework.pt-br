---
title: 'Inovação em nuvem: interagir com dispositivos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação na nuvem – interagir com dispositivos
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: c226c765390805bf4b9ae52ebaf74d337286b90e
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73047680"
---
# <a name="ambient-experiences-interact-with-devices"></a>Experiências de ambiente: interagir com dispositivos

Em [Build com o Customer empatia](./build.md), discutimos os três testes de verdadeira inovação: resolver uma necessidade do cliente, manter o cliente voltado e dimensionar em uma base de coortes do cliente. Cada teste de sua hipótese requer esforço e iterações sobre a abordagem de adoção. Este artigo oferece informações sobre algumas abordagens avançadas para reduzir esse esforço por meio de *experiências de ambiente*. Ao interagir com dispositivos, em vez de um aplicativo, talvez seja mais provável que o cliente se transforme em sua solução primeiro.

## <a name="ambient-experiences"></a>Experiências de ambiente

Uma experiência de ambiente é uma experiência digital relacionada aos arredores imediatos. Uma solução que apresenta experiências de ambiente se esforça para atender ao cliente em seu momento de necessidade. Quando possível, a solução atende às necessidades do cliente sem deixar o fluxo de atividade que a disparou.

A vida útil da economia digital está cheia de distrações. Somos todos bombarded com mensagens sociais, de email, Web, visuais e verbal, cada uma delas é um risco de distração. Esse risco aumenta com cada segundo que decorre entre o ponto de necessidade do cliente e o momento em que eles encontram uma solução. Inúmeros clientes são perdidos nesse breve intervalo de tempo. Para promover um aumento na adoção de repetição, você precisa reduzir o número de distrações reduzindo o tempo de solução (TTS).

## <a name="interacting-with-devices"></a>Interagindo com dispositivos

Uma experiência Web padrão é a técnica de desenvolvimento de aplicativos mais comum usada para atender às necessidades de um cliente. Essa abordagem pressupõe que o cliente esteja em frente ao seu computador. Se o cliente atender consistentemente ao seu ponto de necessidade enquanto estiver na frente do laptop, crie um aplicativo Web. Esse aplicativo Web fornecerá uma experiência de ambiente para esse cliente nesse cenário. No entanto, sabemos que esse cenário é menos e menos provável em nossa época atual.

![Experiências de ambiente](../../_images/innovate/ambient-experiences.png)

As experiências de ambiente normalmente exigem mais do que um aplicativo Web hoje em dia. Por meio de [medição](./measure.md) e [aprendizado com o cliente](./learn.md) , o comportamento que dispara a necessidade do cliente pode ser observado, acompanhado e usado para criar uma experiência mais ambiental. A lista a seguir resume algumas abordagens para a integração de soluções de ambiente em suas mesmas, com mais detalhes sobre cada um nos parágrafos a seguir.

- **[Experiência móvel](#mobile-experience):** Assim como acontece com laptops, os aplicativos móveis são onipresentes em ambientes de clientes. Em algumas situações, isso pode fornecer um nível suficiente de interatividade para tornar um ambiente de solução.
- **[Realidade misturada](#mixed-reality):** Às vezes, os arredores típicos de um cliente devem ser alterados para criar um ambiente de interação. Esse fator cria algo de uma realidade falsa na qual o cliente interage com a solução e tem uma necessidade de cumprir. Nesse caso, a solução é ambiente na realidade falsa.
- **[Realidade integrada](#integrated-reality):** Indo mais perto do verdadeiro Ambience, as soluções de realidade integradas se concentram no uso de um dispositivo que existe dentro da realidade do cliente para integrar a solução em seus comportamentos naturais. Um assistente virtual é um ótimo exemplo de integração da realidade ao ambiente ao redor. Uma opção menos conhecida diz respeito a tecnologias de Internet das Coisas (IoT), que integram dispositivos que já existem no ambiente do cliente.
- **[Realidade ajustada](#adjusted-reality):** Quando qualquer uma dessas soluções de ambiente usa análise preditiva na nuvem para definir e fornecer uma interação com o cliente por meio de arredores naturais, a solução ajustou a realidade.

Entender a necessidade do cliente e medir o impacto do cliente ajuda a determinar se uma interação de dispositivo ou uma experiência de ambiente são necessárias para validar sua hipótese. Com cada um desses pontos de dados, as seções a seguir irão ajudá-lo a encontrar a melhor solução.

## <a name="mobile-experience"></a>Experiência móvel

No primeiro estágio da experiência de ambiente, o usuário sai do computador. Os consumidores de hoje e os profissionais de negócios mudam de fluido entre dispositivos móveis e de PC. Cada uma das plataformas ou dispositivos usados por seu cliente cria uma nova experiência em potencial. Adicionar uma experiência móvel que estende a solução principal é a maneira mais rápida de melhorar a integração nos arredores imediatos do cliente. Embora um dispositivo móvel esteja longe do ambiente, ele pode se aproximar mais do ponto de necessidade do cliente.

Quando os clientes são móveis e alteram os locais com frequência, isso pode representar a forma mais relevante de experiência de ambiente para uma solução específica. Na última década, a inovação foi disparada com frequência pela integração de soluções existentes com uma experiência móvel.

Azure App serviços é um ótimo exemplo dessa abordagem. Durante as iterações iniciais, o [recurso de aplicativo Web dos serviços de Azure app](/azure/app-service/overview) pode ser usado para testar a hipótese. Como as mesmas se tornam mais complexas, o [recurso de aplicativo móvel dos serviços Azure app](/azure/app-service-mobile/) pode estender o aplicativo Web para ser executado em uma variedade de plataformas móveis.

## <a name="mixed-reality"></a>Realidade misturada

As soluções de realidade misturada representam o próximo nível de maturidade para experiências de ambiente. Essa abordagem aumenta ou Replica o ambiente do cliente; Ele cria uma extensão da realidade para o cliente operar no.

> [!IMPORTANT]
> Se um dispositivo VR (realidade virtual) é necessário e *ainda não faz parte dos comportamentos imediatos ou naturais do cliente*, o aumento ou a realidade virtual é mais uma experiência alternativa e uma experiência de ambiente menor.

As experiências de realidade misturada são cada vez mais comuns entre as forças de força remotas. Seu uso está crescendo ainda mais rapidamente em setores que exigem habilidades de colaboração ou de especialidade que não estão prontamente disponíveis no mercado local. As situações que exigem suporte de implementação centralizado de um produto complexo para uma força de trabalho remota são particularmente fértils para a realidade aumentada. Nesses cenários, a equipe de suporte central e os funcionários remotos podem aproveitar a realidade aumentada para trabalhar, solucionar problemas e instalar o produto.

Por exemplo, considere o caso de âncoras espaciais. As âncoras espaciais permitem que você crie experiências mistas de realidade com objetos que persistem seus respectivos locais entre dispositivos ao longo do tempo. Por meio de âncoras espaciais, um comportamento específico pode ser capturado, gravado e persistido, fornecendo, assim, uma experiência ambiente na próxima vez que o usuário operar dentro desse ambiente aumentado. As [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/overview) são um serviço que move essa lógica para a nuvem, permitindo que as experiências sejam compartilhadas entre dispositivos e até mesmo em soluções.

## <a name="integrated-reality"></a>Realidade integrada

Além da realidade móvel, ou até mesmo a realidade misturada está na realidade integrada. A realidade integrada visa remover totalmente a experiência digital. Todos em nosso lugar são dispositivos com recursos de computação e conectividade. Esses dispositivos podem ser usados para coletar dados de arredores imediatos sem que o cliente tenha que nunca tocar em um telefone, laptop ou dispositivo VR.

Essa experiência é ideal quando alguma forma de dispositivo está consistente no mesmo ambiente em que o cliente precisa ocorrer. Os cenários comuns incluem pisos de fábrica, elevadors e até mesmo seu carro. Esses tipos de dispositivos grandes já contêm potência de computação. Você também pode usar dados do próprio dispositivo para detectar comportamentos do cliente e enviar esses comportamentos para a nuvem. Essa captura automática de dados de comportamento do cliente reduz drasticamente a necessidade de um cliente inserir dados. Além disso, a experiência Web, móvel ou VR pode funcionar como um loop de comentários para compartilhar o que foi aprendido com a solução de realidade integrada.

Exemplos de realidade integrada no Azure podem incluir:

- As [soluções de IOT (Internet das coisas do Azure)](https://docs.microsoft.com/azure/iot-fundamentals), uma coleção de serviços no Azure que cada um auxilia no gerenciamento de dispositivos e no fluxo de dados desses dispositivos para a nuvem e vice-versa para os usuários finais.
- [Azure Sphere](/azure-sphere), uma combinação de hardware e software. Azure Sphere é uma maneira segura de permitir que um dispositivo existente transmita dados com segurança entre o dispositivo e as soluções de IoT do Azure.
- [Kit de desenvolvedores de Kinect do Azure](https://docs.microsoft.com/azure/Kinect-dk), sensores de ia com visão avançada do computador e modelos de fala. Esses sensores podem coletar dados visuais e de áudio dos arredores imediatos e alimentar essas entradas em sua solução.

Você pode usar todas essas três ferramentas para coletar dados de arredores naturais e no ponto de necessidade do cliente. A partir daí, sua solução pode responder a essas entradas de dados para resolver a necessidade, às vezes antes que o cliente esteja até mesmo ciente de que um gatilho para essa necessidade ocorreu.

## <a name="adjusted-reality"></a>Realidade ajustada

A forma mais alta de experiência ambiente é ajustada à realidade, muitas vezes conhecida como *inteligência ambiental*. A realidade ajustada é uma abordagem para o uso de informações de sua solução para alterar a realidade do cliente sem exigir que eles interajam diretamente com um aplicativo. Nessa abordagem, o aplicativo que você criou inicialmente para provar que sua hipótese pode não ser mais relevante. Em vez disso, os dispositivos no ambiente ajudam a modular as entradas e saídas para atender às necessidades do cliente.

Os assistentes virtuais e os auto-falantes inteligentes oferecem ótimos exemplos de realidade ajustada. Sozinho, um palestrante inteligente é um exemplo de realidade integrada simples. Mas adicione um sensor inteligente de luz e movimento a uma solução de palestrante inteligente e é fácil criar uma solução básica que acende as luzes quando você insere uma sala.

Os pisos de fábrica em todo o mundo fornecem exemplos adicionais de realidade ajustada. Durante os estágios iniciais da realidade integrada, os sensores em dispositivos detectaram condições como o superaquecimento e, em seguida, alertava um humano sendo por meio de um aplicativo. Na realidade ajustada, o cliente ainda pode estar envolvido, mas o loop de comentários é mais rígido. Em uma fábrica de realidade ajustada, um dispositivo pode detectar superaquecimento em uma máquina vital em algum lugar ao longo da linha do assembly. Em outro lugar no andar, um segundo dispositivo reduz um pouco a produção para permitir que a máquina seja fria e, em seguida, retome o ritmo completo quando a condição for resolvida. Nessa situação, o cliente é um participante de segunda mão. O cliente usa seu aplicativo para definir as regras e entender como essas regras afetam a produção, mas não são necessárias para o loop de comentários.

Os serviços do Azure descritos nas [soluções de IOT (azure Internet das coisas)](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](/azure-sphere)e kit de [desenvolvedores de Kinect do Azure](https://docs.microsoft.com/azure/Kinect-dk) podem ser componentes de uma solução de realidade ajustada. O aplicativo original e a lógica de negócios servirão como o intermediário entre a entrada ambiental e a alteração que deve ser feita no ambiente físico.

Uma teledigital é outro exemplo da realidade ajustada. Este termo refere-se a uma representação digital de um dispositivo físico, apresentada por meio de formatos de computadores, móveis ou de realidade mista. Ao contrário de modelos 3D menos sofisticados, uma teledigital reflete os dados coletados de um dispositivo real no ambiente físico. Essa solução permite que o usuário interaja com a representação digital de maneiras que nunca poderiam ser feitas no mundo real. Nessa abordagem, os dispositivos físicos ajustam um ambiente de realidade misturada. No entanto, a solução ainda coleta dados de uma solução de realidade integrada e usa esses dados para moldar a realidade dos arredores atuais do cliente.

No Azure, as gêmeos digitais são criadas e acessadas por meio de um serviço chamado [Azure digital gêmeos](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Próximos passos

Agora que você tem uma compreensão mais profunda das interações de dispositivos e da experiência ambiente ideal para sua solução, você está pronto para explorar a disciplina final de inovação, [previsão e influência](./predict.md).

> [!div class="nextstepaction"]
> [Prever e influenciar](./predict.md)
