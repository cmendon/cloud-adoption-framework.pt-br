---
title: 'Guia de inovação do Azure: Interagir com dispositivos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guia de inovação do Azure – interagir com dispositivos
author: umarmohamedusman
ms.author: umarm
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: cf0671d4ea4c8d008010d43379cd782ff58e38ed
ms.sourcegitcommit: 3655aa7f3e80249e0b2b562cd40dd750afc82043
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74251896"
---
::: zone target="docs"

# <a name="azure-innovation-guide-interact-through-devices"></a>Guia de inovação do Azure: Interagir com dispositivos

::: zone-end

::: zone target="chromeless"

# <a name="interact-through-devices"></a>Interagir com dispositivos

::: zone-end

Inove por meio de dispositivos de borda perceptivos e com conexão intermitente. Coordene milhões desses dispositivos, adquira e processe dados ilimitados e aproveite um número cada vez maior de experiências multissensioriais e multidispositivo. Para dispositivos na borda da rede, o Azure fornece uma estrutura para a criação de soluções comerciais de imersão e efetivas. Com a computação ubíqua, habilitada pelo Azure em combinação com a tecnologia de IA (inteligência artificial), é possível criar todos os tipos de aplicativos e sistemas inteligentes possíveis de imaginar.

Os clientes do Azure utilizam um conjunto em expansão contínua de sistemas e dispositivos conectados que coletam e analisam dados &mdash; perto de seus usuários, dos dados ou de ambos. Os usuários obtêm insights e experiências em tempo real, fornecidos por aplicativos com reconhecimento de contexto e elevada capacidade de resposta. Ao mover partes da carga de trabalho para a borda, esses dispositivos podem gastar menos tempo enviando mensagens para a nuvem e reagir mais rapidamente aos eventos espaciais.

> [!div class="checklist"]
>
> - Ativos industriais
> - HoloLens 2
> - Azure Sphere
> - Kinect DK
> - Drones
> - Banco de Dados SQL do Azure no Edge
> - IoT Plug and Play

<!-- markdownlint-disable MD025 -->

## <a name="global-scale-iot-servicetabiothub"></a>[Serviço IoT de escala global](#tab/IoTHub)

<!-- markdownlint-enable MD025 -->

Arquitete soluções que exercitam a comunicação bidirecional com dispositivos IoT na escala dos bilhões. Use dados telemétricos prontos para uso do dispositivo para a nuvem a fim de entender o estado de seus dispositivos e definir rotas de mensagens para outros serviços do Azure, apenas por meio de configuração. Fazendo uso das mensagens da nuvem para dispositivo, é possível enviar comandos e notificações de maneira confiável para seus dispositivos conectados e acompanhar a entrega de mensagem com recibos de confirmação. Além disso, você reenviará automaticamente as mensagens de dispositivos conforme necessário para ajustar-se à conectividade intermitente.

Aqui estão alguns recursos que você encontrará:

- Canal de **comunicação com segurança avançada** para enviar e receber dados de dispositivos IoT.
- **Gerenciamento de dispositivo interno** e provisionamento para conectar e gerenciar dispositivos IoT em escala.
- **Integração completa com a Grade de Eventos** e computação sem servidor, simplificando o desenvolvimento de aplicativos IoT.
- **Compatibilidade com o Azure IoT Edge** para a criação de aplicativos IoT híbridos.

::: zone target="docs"

**Ir para o [Hub IoT](https://docs.microsoft.com/azure/iot-dps)**

**Ir para os [Serviços de Provisionamento de Dispositivos](https://docs.microsoft.com/azure/iot-dps)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para criar um hub IoT:

1. Acesse o **Hub IoT**.
2. Selecione **Criar Hub IoT**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Devices%2FIotHubs]" submitText="Go to IoT Hub" :::

<!-- markdownlint-enable DOCSMD001 -->

O Serviço de Provisionamento de Dispositivos no Hub IoT é um serviço auxiliar do Hub IoT que habilita o provisionamento just-in-time e sem toque.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Ação

Para criar Serviços de Provisionamento de Dispositivos no Hub IoT:

1. Acesse os **Serviços de Provisionamento de Dispositivos no Hub IoT**.
2. Selecione **Criar Serviço de Provisionamento de Dispositivos**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Devices%2FProvisioningServices]" submitText="Go to Device Provisioning Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

<!-- markdownlint-disable MD025 -->

## <a name="azure-digital-twinstabdigitaltwins"></a>[Gêmeos Digitais do Azure](#tab/DigitalTwins)

Crie experiências reutilizáveis, altamente escalonáveis e com reconhecimento espacial que vinculam os dados de streaming entre o mundo digital e o mundo físico. Aumente o envolvimento dos clientes usando modelos abrangentes de ambientes físicos. Gere grafos de inteligência espacial para modelar relações e interações entre pessoas, locais e dispositivos. Consulte dados de um espaço físico em vez de usar sensores diferentes.

**Modelos de objeto de Gêmeos Digitais do Azure:** Uma ontologia que descreve as regiões, os locais, os andares, os escritórios, as zonas, as salas de conferência e as salas de foco de um prédio inteligente ou ainda que descreve várias estações de energia, subestações, recursos de energia e clientes de uma grade de energia pode ser modelada usando modelos de objeto de Gêmeos Digitais e ontologias.

**Grafo de inteligência espacial:** O grafo hierárquico de espaços, dispositivos e pessoas definido no modelo de objeto de Gêmeos Digitais que dá suporte a herança, filtragem, passagem, escalabilidade e extensibilidade. É possível gerenciar e interagir com o grafo espacial por meio da coleção de APIs REST hospedadas no Azure.

::: zone target="docs"

**Acessar [Gêmeos Digitais do Azure](https://docs.microsoft.com/azure/digital-twins/about-digital-twins)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para criar Gêmeos Digitais do Azure:

1. No painel esquerdo, selecione **Criar um recurso**.
2. Pesquise por **gêmeos digitais** e depois selecione **Gêmeos Digitais**.
3. Selecione **Criar** para iniciar o processo de implantação.
4. Para examinar as Gêmeos Digitais existentes, selecione este botão:

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.IoTSpaces%2FGraph]" submitText="Go to Digital Twins" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

<!-- markdownlint-disable MD025 -->

## <a name="location-intelligencetabazuremaps"></a>[Inteligência de localização](#tab/AzureMaps)

Além das funcionalidades de localização tradicionais, tais como proximidade, tráfego e roteamento, o serviço do Azure Mapas permite que as empresas criem soluções usando a inteligência de localização em tempo real impulsionada pelos parceiros de tecnologia de mobilidade de classe mundial **TomTom** e **Moovit**. Integre facilmente funcionalidades de mobilidade e localização avançadas em seus aplicativos com serviços geoespaciais.

**Versão prévia do Serviço de Dados:** Carregue e armazene dados geoespaciais para uso com operações espaciais ou composição de imagens para reduzir a latência, aumentar a produtividade e habilitar novos cenários em seus aplicativos.

**Operações espaciais:** Melhore sua inteligência de localização com uma biblioteca de cálculos matemáticos geoespaciais comuns, incluindo delimitação geográfica, ponto mais próximo, grande distância de círculo e buffers.

**Geolocalização:** Pesquise o país de um endereço IP. Personalize conteúdos e serviços com base na localização do usuário e obtenha insights sobre a distribuição geográfica dos clientes.

::: zone target="docs"

**Acesse [Azure Mapas](https://docs.microsoft.com/azure/azure-maps)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para usar a inteligência de localização:

1. Acesse **Contas do Azure Mapas**.
2. Selecione **Criar contas do Azure Mapas**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Maps%2Faccounts]" submitText="Go to Azure Maps Account" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="spatial-experiencestabspatial"></a>[Experiências espaciais](#tab/spatial)

O Âncoras Espaciais do Azure permite aos desenvolvedores trabalhar com plataformas de realidade misturada para perceber espaços, designar pontos precisos de interesse e lembrar-se dos pontos de interesse de dispositivos compatíveis.

**Adicione contexto ao mundo real:** Forneça a seus usuários um melhor entendimento sobre seus dados, bem como onde e quando eles são necessários, ao colocar seu conteúdo digital em pontos de interesse físicos e conectá-lo a esses pontos de interesse.

**Compartilhe hologramas entre dispositivos:** Acelere decisões e resultados ao levar o ambiente 3D a sua equipe e clientes em um dispositivo de escolha deles. O recurso Âncoras Espaciais torna mais fácil para pessoas no mesmo lugar participarem de aplicativos de realidade misturada multiusuário.

**Experiências envolventes:** Conecte as âncoras espaciais pela criação de relações entre elas e forneça uma experiência de usuário que possa incluir dois ou mais pontos de interesse com os quais um usuário precisa interagir para concluir uma tarefa. Seu aplicativo pode permitir que um usuário coloque um artefato virtual no mundo real. Em uma configuração industrial, um usuário pode receber informações contextuais sobre um computador apontando uma câmera de dispositivos com suporte para ele.

O recurso Âncoras Espaciais do Azure é composto por um serviço gerenciado e os SDKs do cliente para plataformas de dispositivos com suporte.

::: zone target="docs"

**Acessar [Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para usar as experiências espaciais:

1. Acesse **Contas de Âncoras Espaciais**.
2. Selecione **Criar contas de âncoras espaciais**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.MixedReality%2FspatialAnchorsAccounts]" submitText="Go to Spatial Anchors Accounts" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-remote-renderingtabremoterender"></a>[Azure Remote Rendering](#tab/RemoteRender)

Renderize conteúdo 3D interativo e de alta qualidade na nuvem e transmita para seus dispositivos em tempo real. Cargas de trabalho de renderização são muito usadas para efeitos especiais (VFX) na indústria de mídia e entretenimento. A renderização também é usada em muitos outros setores como publicidade, varejo, petróleo e gás e manufatura.

O processo de renderização usa computação intensiva. Pode haver muitos quadros ou imagens para produzir e cada imagem pode levar várias horas para ser renderizada. A renderização é, portanto, uma carga de trabalho perfeita para processamento em lotes, que pode usar o Azure e o Lote do Azure para executar muitas renderizações em paralelo.

::: zone target="docs"

**Acessar [Azure Remote Rendering](https://azure.microsoft.com/services/remote-rendering)**

**Acessar [Renderizar usando o Azure](https://docs.microsoft.com/azure/batch/batch-rendering-service)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Ação

Para usar o Remote Rendering:

1. Acesse **Contas do Lote**.
2. Selecione **Criar contas do Lote**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Batch%2FbatchAccounts]" submitText="Go to Azure Batch" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
