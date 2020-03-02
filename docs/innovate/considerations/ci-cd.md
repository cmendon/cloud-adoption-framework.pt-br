---
title: Capacite a adoção com a invenção digital
description: Use o modelo de maturidade da metodologia inovar para reduzir o conflito que reduz a adoção e, ao mesmo tempo, mantém as práticas recomendadas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 59ef9ad61c9e3545fbcdbd62e05711e20de38a29
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223483"
---
# <a name="empower-adoption"></a>Capacitar a adoção

O teste final da inovação é a reação do cliente à sua invenção. A hipótese é verdadeira? Os clientes usam a solução? Ele é dimensionado para atender às necessidades do percentual de usuários desejado? O mais importante é que eles continuam voltando? Nenhuma dessas perguntas pode ser solicitada até que a solução MVP (produto viável) mínima tenha sido implantada. Neste artigo, nos concentraremos na disciplina de capacitar a adoção.

## <a name="reduce-friction-that-affects-adoption"></a>Reduzir o conflito que afeta a adoção

Há alguns pontos principais de conflitos na adoção que podem ser minimizados por meio de uma combinação de tecnologia e processos. Para leitores com conhecimento dos processos de CI (integração contínua) e de implantação contínua (CD) ou DevOps, o seguinte será familiar. Este artigo estabelece um ponto de partida para equipes de adoção de nuvem que impulsionam loops de inovação e de comentários. No futuro, esse ponto de partida pode estimular abordagens mais robustas de CI/CD ou DevOps à medida que os produtos e as equipes amadurecem.

Conforme descrito em [medida para o impacto do cliente](./measure.md), a validação positiva de qualquer hipótese requer iteração e determinação. Você experimentará muito mais falhas do que o WINS durante qualquer ciclo de inovação. Isso é esperado. No entanto, quando um cliente precisa, uma hipótese e uma solução são alinhadas em escala, o mundo muda rapidamente. Este artigo tem como objetivo minimizar os [picos técnicos](./build.md#reduce-complexity-and-delay-technical-spikes) que tornam a inovação lenta, mas que ainda garantem que você mantenha algumas práticas recomendadas sólidas. Isso ajudará o design da equipe para o sucesso futuro, oferecendo as necessidades atuais do cliente.

## <a name="empowering-adoption-the-maturity-model"></a>Capacitação de adoção: o modelo de maturidade

O objetivo principal da [metodologia inovar](./index.md) é criar parcerias de clientes e acelerar os loops de comentários, o que levará a inovações no mercado. A imagem e as seções a seguir descrevem as implementações iniciais que dão suporte a essa metodologia.

![Capacitação de adoção: o modelo de maturidade](../../_images/innovate/empower-adoption-maturity.png)

- [Solução compartilhada](#shared-solution): estabeleça um repositório centralizado para todos os aspectos da solução.
- [Loops de comentários](#feedback-loops): Verifique se os loops de comentários podem ser gerenciados consistentemente por meio de iterações.
- [Integração contínua](#continuous-integration): compile e consolide regularmente a solução.
- [Teste confiável](#reliable-testing): valide a qualidade da solução e as alterações esperadas para garantir a confiabilidade de suas métricas de teste.
- [Implantação de solução](#solution-deployment): implante soluções para que a equipe possa compartilhar rapidamente as alterações com os clientes.
- [Medição integrada](#integrated-measurements): Adicione métricas de aprendizado ao loop de comentários para uma análise clara por toda a equipe.

Para minimizar os picos técnicos, suponha que a maturidade inicialmente estará baixa em cada um desses princípios. Mas, definitivamente, planeje-se alinhando a ferramentas e processos que podem ser dimensionados, pois as mesmas se tornam mais refinadas. No Azure, o [GitHub](https://guides.github.com) e o [Azure DevOps](https://docs.microsoft.com/azure/devops) permitem que pequenas equipes comecem com pouco conflito. Essas equipes podem crescer para incluir milhares de desenvolvedores que colaboram em soluções de escala e testam centenas de percursos de clientes. O restante deste artigo ilustra a abordagem de plano grande/inicial pequeno para capacitar a adoção em cada um desses princípios.

## <a name="shared-solution"></a>Solução compartilhada

Conforme descrito em [medida para o impacto do cliente](./measure.md), a validação positiva de qualquer hipótese requer iteração e determinação. Você experimentará muito mais falhas do que o WINS durante qualquer ciclo de inovação. Isso é esperado. No entanto, quando um cliente precisa, uma hipótese e uma solução são alinhadas em escala, o mundo muda rapidamente.

Quando você está dimensionando a inovação, não há uma ferramenta mais valiosa do que uma base de código compartilhada para a solução. Infelizmente, não existe uma maneira confiável de prever qual iteração ou qual MVP produzirá a combinação vencedora. É por isso que nunca é muito cedo estabelecer uma base de código ou um repositório compartilhado. Esse é o único [aumento técnico](./build.md#reduce-complexity-and-delay-technical-spikes) que nunca deve ser atrasado. À medida que a equipe itera por meio de várias soluções de MVPs, um repositório compartilhado permite a colaboração fácil e o desenvolvimento acelerado. Quando as alterações na solução arrastam as métricas de aprendizado, o controle de versão permite reverter para uma versão anterior e mais efetiva da solução.

A ferramenta mais amplamente adotada para gerenciar repositórios de código é o [GitHub](https://guides.github.com), que permite criar um repositório de código compartilhado em apenas algumas etapas. Além disso, o recurso [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) do Azure DevOps pode ser usado para criar um repositório do [git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) ou do [Team Foundation](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="feedback-loops"></a>Loops de comentários

Tornar a parte do cliente da solução é a chave para a criação de parcerias de clientes durante ciclos de inovação. Isso é feito, em parte, [medindo o impacto do cliente](./measure.md). Ele requer conversas e testes diretos com o cliente. Ambos geram comentários que devem ser gerenciados com eficiência.

Cada ponto de comentário é uma solução potencial para a necessidade do cliente. O mais importante é que todos os comentários diretos dos clientes representam uma oportunidade de melhorar a parceria. Se os comentários fizerem isso em uma solução MVP, comemoraremos isso com o cliente. Mesmo que alguns comentários não sejam acionáveis, simplesmente ser transparente com a decisão de despriorizar os comentários demonstra uma [mentalidade de crescimento](./learn.md#growth-mindset) e um foco no [aprendizado contínuo](./learn.md#continuous-learning).

O [Azure DevOps](https://docs.microsoft.com/azure/devops) inclui maneiras de [solicitar, fornecer e gerenciar comentários](https://docs.microsoft.com/azure/devops/project/feedback). Cada uma dessas ferramentas centraliza os comentários para que a equipe possa agir e fornecer acompanhamento em serviço de um loop de comentários transparente.

## <a name="continuous-integration"></a>Integração contínua

À medida que a adoção é dimensionada e uma hipótese chega mais perto da verdadeira inovação em escala, o número de hipóteses menores a serem testadas tende a crescer rapidamente. Para fazer loops de comentários precisos e processos de adoção suave, é importante que cada uma dessas hipóteses esteja integrada e se apoio à hipótese primária por trás da inovação. Isso significa que você também precisa se mover rapidamente para inovar e aumentar, o que exige vários desenvolvedores para testar variações da hipótese principal. Para esforços de desenvolvimento de estágios posteriores, você pode até mesmo precisar de várias equipes de desenvolvedores, cada uma construindo em direção a uma solução compartilhada. A integração contínua é a primeira etapa para o gerenciamento de todas as partes móveis.

Na integração contínua, as alterações de código são frequentemente mescladas na ramificação principal. Os processos de compilação e teste automatizados garantem que o código na ramificação principal seja sempre a qualidade da produção. Isso garante que os desenvolvedores estejam trabalhando juntos para desenvolver soluções compartilhadas que forneçam loops de comentários precisos e confiáveis.

O Azure DevOps e [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines) fornecem recursos de integração contínua com apenas algumas etapas no GitHub ou em uma variedade de outros repositórios.
Saiba mais sobre a [integração contínua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-integration)ou para obter mais informações, confira o [laboratório prático](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration). Também há arquiteturas de solução para acelerar a criação de seus [pipelines de CI/CD por meio do Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="reliable-testing"></a>Testes confiáveis

Defeitos em qualquer solução podem criar falsos positivos ou falsos negativos. Erros inesperados podem facilmente levar a uma má interpretação das métricas de adoção do usuário. Eles também podem gerar comentários negativos de clientes que não representam com precisão o teste de sua hipótese.

Durante as iterações iniciais de uma solução MVP, são esperados defeitos; os pioneiros podem até mesmo encontrá-los. Em versões anteriores, o teste de aceitação normalmente não existe. No entanto, um aspecto da criação com empatia se preocupa com a validação da necessidade e da hipótese. Ambos podem ser concluídos por meio de testes de unidade em um nível de código e testes de aceitação manual antes da implantação. Juntos, eles fornecem alguns meios de confiabilidade no teste. Você deve se esforçar para automatizar uma série bem definida de testes de compilação, unidade e aceitação. Eles garantirão métricas confiáveis relacionadas a ajustes mais granulares para a hipótese e a solução resultante.

O recurso [Azure Test Plans](https://docs.microsoft.com/azure/devops/test/track-test-status?view=azure-devops) fornece ferramentas para desenvolver e operar planos de teste durante a execução de teste manual ou automatizada.

## <a name="solution-deployment"></a>Implantação da solução

Talvez o aspecto mais significativo da capacitação da adoção esteja relacionado à sua capacidade de controlar o lançamento de uma solução para os clientes. Ao fornecer um pipeline automatizado ou de autoatendimento para lançar uma solução para os clientes, você acelerará o loop de comentários. Ao permitir que os clientes interajam rapidamente com as alterações na solução, você os convida para o processo. Essa abordagem também dispara testes mais rápidos de hipóteses, reduzindo assim suposições e potencial retrabalho.

O são vários métodos para implantação de solução. Os seguintes representam os três mais comuns:

- A **implantação contínua** é o método mais avançado, pois implanta automaticamente alterações de código em produção. Para equipes maduras que estão testando hipóteses maduras, a implantação contínua pode ser extremamente valiosa.
- Durante os estágios iniciais do desenvolvimento, a **entrega contínua** pode ser mais apropriada. Na entrega contínua, todas as alterações de código são implantadas automaticamente em um ambiente semelhante à produção. Os desenvolvedores, tomadores de decisões de negócios e outros membros da equipe podem usar esse ambiente para verificar se o trabalho está pronto para produção. Você também pode usar esse método para testar uma hipótese com os clientes sem afetar as atividades de negócios em andamento.
- A **implantação manual** é a abordagem menos sofisticada para o gerenciamento de liberações. Como o nome sugere, alguém na equipe implanta manualmente as alterações de código mais recentes. Essa abordagem é propenso a erros, não confiável e é considerada um antipadrão por engenheiros mais experientes.

Durante a primeira iteração de uma solução MVP, a implantação manual é comum, apesar da avaliação anterior. Quando a solução é extremamente fluida e os comentários dos clientes são desconhecidos, há um risco significativo na redefinição de toda a solução (ou até mesmo a hipótese principal). Aqui está a regra geral para implantação manual: sem prova de cliente, sem automação de implantação.

Investir cedo pode levar a perda de tempo. O mais importante é que ele pode criar dependências no pipeline de lançamento que tornam a equipe mais resistente a um pivô inicial. Após as primeiras iterações ou quando os comentários dos clientes sugerem um sucesso potencial, um modelo mais avançado de implantação deve ser rapidamente adotado.

Em qualquer estágio da validação de hipóteses, o Azure DevOps e o [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines) fornecem recursos de entrega contínua e implantação contínua. Saiba mais sobre a [entrega contínua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-delivery)ou confira o [laboratório prático](https://www.azuredevopslabs.com/labs/azuredevops/continuousdeployment). A arquitetura da solução também pode acelerar a criação de seus [pipelines de CI/CD por meio do Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="integrated-measurements"></a>Medidas integradas

Ao [medir o impacto do cliente](./measure.md), é importante entender como os clientes reagem às alterações na solução. Esses dados, conhecidos como *telemetria*, fornecem informações sobre as ações que um usuário (ou coorte de usuários) levou ao trabalhar com a solução. A partir desses dados, é fácil obter uma validação quantitativa da hipótese. Essas métricas podem, então, ser usadas para ajustar a solução e gerar as mesmas mais refinadas. Essas alterações mais sutis ajudam a impulsionar a solução inicial em iterações subsequentes, levando, em última análise, a adotar a adoção em escala.

No Azure, [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) fornece as ferramentas e a interface para coletar e examinar dados de experiências do cliente. Você pode aplicar essas observações e ideias para refinar a pendência usando [Azure boards](https://docs.microsoft.com/azure/devops/boards).

## <a name="next-steps"></a>Próximas etapas

Depois de ter obtido uma compreensão das ferramentas e dos processos necessários para capacitar a adoção, é hora de examinar uma disciplina de inovação mais avançada: [interagir com dispositivos](./devices.md). Essa disciplina pode ajudar a reduzir as barreiras entre experiências físicas e digitais, tornando sua solução ainda mais fácil de adotar.

> [!div class="nextstepaction"]
> [Interagir com dispositivos](./devices.md)
