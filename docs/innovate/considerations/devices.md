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
ms.openlocfilehash: 5a9ec9f38d89683482d7f98923aa0ef2ccf201b9
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683228"
---
# <a name="ambient-experiences-interact-with-devices"></a>Experiências de ambiente: interagir com dispositivos

Ao [criar com o empatia](./build.md), discutimos os três testes de verdadeira inovação: solucionar uma necessidade do cliente, manter o cliente voltado, dimensionar em uma base de coortes do cliente. Cada teste de sua hipótese exigirá esforço e iterações sobre a abordagem da adoção. Este artigo fornecerá informações sobre algumas abordagens avançadas para reduzir esse esforço por meio de **experiências de ambiente**. Ao interagir com dispositivos, em vez de um aplicativo, talvez seja mais provável que o cliente se transforme em sua solução primeiro para ter suas necessidades atendidas.

## <a name="ambient-experiences"></a>Experiências de ambiente

Uma experiência de ambiente é uma experiência digital que se relaciona com os arredores imediatos. Uma solução que apresenta experiências de ambiente se esforça para atender ao cliente em seu momento de necessidade. Quando possível, a solução atende às necessidades do cliente sem deixar o fluxo natural do que estava fazendo.

A vida útil da economia digital está cheia de distrações. Estamos todos bombarded com mensagens sociais, de email, Web, Visual e verbal, cada uma delas é um risco de distração. O risco de distração aumenta a cada segundo entre o ponto de necessidade do cliente e uma interação com a solução. Inúmeros clientes são perdidos nesse breve intervalo de tempo. Para promover aumentos na adoção de repetição, reduza o número de distrações reduzindo o tempo de solução (TTS).

## <a name="interacting-with-devices"></a>Interagindo com dispositivos

Uma experiência Web padrão é a técnica de desenvolvimento de aplicativos mais comum usada para atender às necessidades de um cliente. A suposição inclusas nessa abordagem é que o cliente estará na frente de seus computadores. Se o cliente atender consistentemente ao seu ponto de necessidade enquanto estiver na frente do laptop, crie um aplicativo Web. Esse aplicativo Web fornecerá uma "experiência de ambiente" para esse cliente, nesse cenário. Mas sabemos que esse cenário é cada vez menos provável na sociedade moderna.

![Experiências de ambiente](../../_images/innovate/ambient-experiences.png)

As experiências de ambiente, conforme ilustrado acima, geralmente exigem mais do que um aplicativo Web. Por meio de [medição](./measure.md) e [aprendizado com o cliente](./learn.md) , o comportamento que leva ao gatilho de necessidade do cliente pode ser observado, acompanhado e usado para criar uma experiência mais ambiental. A seguir, é resumido algumas abordagens para a integração de soluções de ambiente em suas ações, mais detalhes sobre cada um nos parágrafos a seguir.

- **[Experiência móvel](#mobile-experience)** : muito parecido com um laptop, os aplicativos móveis normalmente são parte dos arredores dos clientes. Em alguns cenários, isso pode fornecer um nível suficiente de interatividade para tornar um ambiente de solução.
- **[Realidade misturada](#mixed-reality):** Às vezes, os arredores naturais de um cliente devem ser alterados para criar um ambiente de interação. Isso cria um pouco de uma realidade falsa na qual o cliente pode interagir com a solução e ter uma necessidade de cumprir. Nesse caso, a solução é ambiente na realidade falsa.
- **[Realidade integrada](#integrated-reality):** Indo mais perto do verdadeiro Ambience, as soluções de realidade integradas se concentram no uso de um dispositivo que existe dentro da realidade do cliente para integrar a solução em comportamentos naturais. Um assistente virtual é um ótimo exemplo de integração da realidade ao ambiente ao redor. Uma opção menos conhecida é usar as tecnologias de IoT (Internet das Coisas) para integrar dispositivos que já existem no ambiente do cliente.
- **[Realidade ajustada](#adjusted-reality):** Quando qualquer uma das soluções de ambiente acima usa a análise preditiva na nuvem para definir e fornecer uma interação com o cliente por meio de arredores naturais, a solução ajustou a realidade.

Entender a necessidade do cliente e medir o impacto do cliente ajudará a determinar se uma interação do dispositivo ou uma experiência ambiental será necessária para validar sua hipótese. Com cada um desses pontos de dados, as seções a seguir ajudarão a encontrar a melhor solução.

## <a name="mobile-experience"></a>Experiência móvel

O primeiro estágio da experiência de ambiente é sair do computador. Os consumidores de hoje e os profissionais de negócios mudam de fluido entre dispositivos móveis e de PC. Cada uma das plataformas ou dispositivos usados por seu cliente cria uma nova experiência potencial para o cliente. Adicionar uma experiência móvel que estende a solução principal é a maneira mais rápida de melhorar a integração nos arredores imediatos do cliente. Embora um dispositivo móvel esteja longe do ambiente, ele pode ficar mais próximo do ponto de necessidade do cliente.

Quando os clientes são móveis e alteram os locais com frequência, essa pode ser a forma mais relevante de experiência de ambiente para uma determinada solução. Uma fonte comum de inovação na última década foi a expansão das soluções existentes para integrar uma experiência móvel.

Exemplos dessa abordagem podem ser vistos em serviços Azure Apps. Durante as iterações iniciais, o [recurso de aplicativo Web do serviço de Azure app](/azure/app-service/overview) pode ser usado para testar a hipótese. Como as mesmas se tornam mais complexas, o [recurso de aplicativo móvel dos serviços Azure app](/azure/app-service-mobile/) pode estender o aplicativo Web para ser executado em uma variedade de plataformas móveis.

## <a name="mixed-reality"></a>Realidade misturada

O próximo nível de maturidade para experiências de ambiente é o aumento ou a replicação do ambiente do cliente por meio de soluções de realidade misturada. Nessa abordagem, a solução se torna mais ambiente, criando uma extensão da realidade para o cliente operar no.

> [!IMPORTANT]
> Se um dispositivo VR (realidade virtual) for necessário e *ainda não fizer parte de seus comportamentos adjacentes ou naturais*, a realidade aumentada/virtual será mais uma experiência alternativa e menos uma experiência de ambiente.

Essa forma de experiência é cada vez mais comum para forças de força remotas. O uso dessas experiências está crescendo ainda mais rapidamente em setores que exigem habilidades de colaboração ou de especialidade que não estão prontamente disponíveis no mercado local. Um cenário comum que requer realidade aumentada como parte de um comportamento natural é o suporte de implementação centralizado de um produto complexo para uma força de trabalho remota. Nesses cenários, a equipe de suporte central e o funcionário remoto podem aproveitar a realidade aumentada para trabalhar com a solução de problemas ou instalar o produto.

Para o cenário acima ou outros cenários semelhantes, um exemplo de experiência de ambiente seria o uso de âncoras espaciais. As âncoras espaciais permitem que você crie experiências mistas de realidade com objetos que persistem seu local entre dispositivos ao longo do tempo. Por meio de âncoras espaciais, um comportamento específico pode ser capturado, gravado e persistido fornecendo uma experiência de ambiente, na próxima vez que o usuário estiver operando dentro desse ambiente aumentado. As [âncoras espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/overview) são um serviço que move essa lógica para a nuvem, permitindo que as experiências sejam compartilhadas entre dispositivos e até mesmo em soluções.

## <a name="integrated-reality"></a>Realidade integrada

Além da realidade móvel ou até mesmo a realidade misturada é o uso da realidade integrada. Nessa abordagem, o objetivo é remover totalmente a experiência digital. Todos em nosso lugar são dispositivos com recursos de computação e conectividade. Esses dispositivos podem ser usados para coletar dados de arredores imediatos sem que o cliente tenha que nunca tocar em um telefone, laptop ou dispositivo VR.

Essa forma de experiência é ideal quando alguma forma de dispositivo está consistente no mesmo ambiente em que o cliente precisa ocorrer. Os cenários comuns incluem pisos de fábrica, elevadors ou até mesmo seu carro. Esses tipos de dispositivos grandes já contêm potência de computação. Você também pode usar dados do próprio dispositivo para detectar comportamentos do cliente e enviar esses comportamentos para a nuvem. Essa captura automática de dados de comportamento do cliente reduz drasticamente a necessidade de um cliente inserir dados. Além disso, a experiência Web, móvel ou VR pode ser usada como um loop de comentários para compartilhar o que foi aprendido com a solução de realidade integrada.

Exemplos de realidade integrada no Azure podem incluir:

- As [soluções de IOT (Internet das coisas do Azure)](https://docs.microsoft.com/azure/iot-fundamentals), uma coleção de serviços no Azure e cada um auxilia no gerenciamento de dispositivos e no fluxo de dados desses dispositivos para a nuvem e vice-versa para os usuários finais.
- [Azure Sphere](/azure-sphere), uma combinação de hardware e software, o Azure Sphere é uma maneira segura de permitir que um dispositivo existente transmita dados com segurança entre o dispositivo e as soluções de IOT do Azure.
- [Kit de desenvolvedores de Kinect do Azure](https://docs.microsoft.com/azure/Kinect-dk), sensores de ia com modelos de fala e visão de computador avançado, que podem coletar dados visuais e de áudio dos arredores imediatos e alimentar essas entradas em sua solução.

Todos os três podem ser usados para coletar dados dentro dos arredores naturais, no ponto de necessidade do cliente. A partir daí, sua solução pode responder a essas entradas de dados para resolver a necessidade, às vezes antes que o cliente esteja até mesmo ciente de que um gatilho para essa necessidade ocorreu.

## <a name="adjusted-reality"></a>Realidade ajustada

A forma mais alta de experiência ambiente é ajustada à realidade, muitas vezes conhecida como inteligência ambiental. A realidade ajustada é uma abordagem para o uso de informações de sua solução para alterar a realidade do cliente, sem a necessidade de interagir diretamente com um aplicativo. Nessa abordagem, o aplicativo que você criou inicialmente para provar que sua hipótese pode não ser mais relevante. Em vez disso, os dispositivos no ambiente facilitariam as entradas e saídas para atender às necessidades dos clientes.

Assistentes virtuais/alto-falantes inteligentes podem fornecer um ótimo exemplo de realidade ajustada. Sozinho, um palestrante inteligente é um exemplo de realidade integrada simples. Adicione uma luz inteligente e um bom movimento a uma solução de palestrante inteligente e é fácil criar uma solução básica com ativar as luzes quando você inserir uma sala.

Os pisos de fábrica em todo o mundo fornecem cenários adicionais de realidade ajustada. Durante os estágios iniciais da realidade integrada, os sensores em dispositivos detectaram condições, como o superaquecimento, e relataram uma necessidade de uma mudança em um aplicativo que está sendo um processo humano. Na realidade ajustada, o cliente ainda pode estar envolvido. Mas, o loop de comentários é mais rígido. Em uma base de fábrica ajustada da realidade, um dispositivo detectaria o superaquecimento em um computador vital em algum lugar dentro da linha do assembly. Em outro lugar no andar, um segundo dispositivo tornaria uma produção levemente lenta para permitir que a máquina esfriasse e retome o ritmo quando a condição fosse resolvida. Nesse cenário, o cliente é uma participação de segunda mão. O cliente usa seu aplicativo para definir as regras e entender como essas regras afetam a produção, mas não seria uma parte necessária do loop de comentários.

Os serviços do Azure na seção anterior, [soluções de Internet das coisas do Azure (IOT)](https://docs.microsoft.com/azure/iot-fundamentals), [Azure Sphere](/azure-sphere)e [Kit de desenvolvedores de Kinect do Azure](https://docs.microsoft.com/azure/Kinect-dk) podem ser componentes de uma solução de realidade ajustada. Seu aplicativo original e a lógica de negócios servirão como intermediário entre a entrada ambiental e a alteração que deve ser feita no ambiente físico.

Outro exemplo de realidade ajustada é a criação de uma teledigital, que é uma representação digital de um dispositivo físico, apresentada por meio de formatos de computador, móvel ou de realidade mista. Ao contrário de modelos 3D menos sofisticados, uma teledigital reflete os dados coletados de um dispositivo real no ambiente físico. Isso permite que o usuário interaja com a representação digital de maneiras que nunca poderiam ser feitas no mundo real. Nessa abordagem, os dispositivos físicos estão ajustando um ambiente de realidade misturada. Mas a solução ainda está coletando dados de uma solução de realidade integrada e usando isso para moldar a realidade dos arredores atuais do cliente.

No Azure, as gêmeos digitais são criadas e acessadas por meio de um serviço chamado [Azure digital gêmeos](https://docs.microsoft.com/azure/digital-twins/about-digital-twins).

## <a name="next-steps"></a>Próximos passos

Com uma compreensão mais profunda das interações de dispositivos e da experiência ambiente ideal para sua solução, agora você está pronto para explorar a disciplina final de inovação, [previsão e influência](./predict.md).

> [!div class="nextstepaction"]
> [Prever e influenciar](./predict.md)
