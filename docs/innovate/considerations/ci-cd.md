---
title: 'Inovação na nuvem: Capacite a adoção'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introdução à inovação na nuvem – capacitar a adoção
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 0c6f55ec7f82756658fc67fb9412d7d83d503b97
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683236"
---
# <a name="empower-adoption"></a>Capacitar a adoção

O teste final da inovação é a reação do cliente à sua invenção. A hipótese é verdadeira? Os clientes usam a solução? Ele é dimensionado para atender às necessidades do percentual de usuários desejado? O mais importante é que eles continuam voltando? Nenhuma dessas perguntas pode ser solicitada até que a solução MVP tenha sido implantada. Neste artigo, vamos nos concentrar na disciplina de capacitar a adoção.

## <a name="reducing-friction-to-adoption"></a>Reduzindo o conflito à adoção

Há alguns pontos principais de conflitos na adoção que podem ser minimizados por meio de uma combinação de tecnologia e processos. Para os leitores familiarizados com os processos de CI/CD ou DevOps, o seguinte parecerá muito semelhante. O foco deste artigo é estabelecer um ponto de partida para as equipes de adoção de nuvem, que impulsionarão os loops de inovação e de comentários. A longo prazo, esse ponto de partida pode crescer em abordagens mais robustas de CI/CD ou DevOps à medida que os produtos e as equipes amadurecem.

Um descrito em [medindo o impacto do cliente](./measure.md), A validação positiva de qualquer hipótese requer iteração e determinação. Você terá mais falhas do que o WINS durante qualquer ciclo de inovação. Isso é esperado. No entanto, quando a necessidade do cliente, a hipótese e o alinhamento da solução em grande escala, o mundo muda rapidamente. Este artigo tem como objetivo minimizar o [aumento técnico](./build.md#reduce-complexity-and-delay-technical-spikes) que tornaria a inovação lenta, mas garantiria que algumas práticas recomendadas sólidas estejam em vigor. Isso ajudará o design da equipe para o sucesso futuro, mas atenderá às necessidades atuais do cliente.

## <a name="empowering-adoption---maturity-model"></a>Capacitando o modelo de maturidade de adoção

O objetivo principal da [metodologia inovar](./index.md) é criar parcerias de clientes e acelerar os loops de comentários, o que levará a inovações no mercado.
A imagem e as seções de conteúdo a seguir descrevem as implementações iniciais, que oferecerão suporte à metodologia.

![Capacitar o modelo de maturidade de adoção](../../_images/innovate/empower-adoption-maturity.png)

- [Solução compartilhada](#shared-solution): estabeleça um repositório centralizado para todos os aspectos da solução.
- [Loops de comentários](#feedback-loops): Verifique se os loops de comentários podem ser gerenciados consistentemente por meio de iterações.
- [Integração contínua](#continuous-integration): compile e consolide regularmente a solução.
- [Teste confiável](#reliable-testing): valide a qualidade da solução e as alterações esperadas para garantir medidas.
- [Implantação de solução](#solution-deployment): implantação de uma solução para permitir que a equipe Compartilhe rapidamente as alterações com os clientes.
- [Medição integrada](#integrated-measurements): Adicione métricas de aprendizado ao loop de comentários para uma análise clara por toda a equipe.

Além de minimizar os picos técnicos, suponha que a maturidade seja baixa inicialmente em cada um desses princípios. Mas, planeje com antecedência alinhando a ferramentas e processos que podem ser dimensionados, pois as mesmas se tornam mais refinadas. No Azure, a combinação do [GitHub](https://guides.github.com) e [do Azure DevOps](https://docs.microsoft.com/azure/devops) permite que pequenas equipes comecem com pouco conflito. Em seguida, aumente para milhares de desenvolvedores colaborando em soluções de escala que testam centenas de as mesmas. O restante deste artigo ilustrará o plano grande, iniciará uma pequena abordagem para capacitar a adoção em cada um desses princípios.

## <a name="shared-solution"></a>Solução compartilhada

Um descrito em [medindo o impacto do cliente](./measure.md), A validação positiva de qualquer hipótese requer iteração e determinação. Você terá mais falhas do que o WINS durante qualquer ciclo de inovação. Isso é esperado. No entanto, quando a necessidade do cliente, a hipótese e o alinhamento da solução em grande escala, o mundo muda rapidamente.

Ao dimensionar a inovação, não há uma ferramenta mais valiosa do que uma codebase compartilhada para a solução. Infelizmente, não há nenhuma maneira de prever qual iteração ou qual MVP produzirá a combinação vencedora. É por isso que nunca é muito cedo estabelecer uma base de código ou um repositório compartilhado. Esse é o único [aumento técnico](./build.md#reduce-complexity-and-delay-technical-spikes) que nunca deve ser atrasado. À medida que a equipe itera por meio de várias soluções de MVPs, um repositório compartilhado permitirá a facilidade de colaboração e o desenvolvimento acelerado. Quando as alterações na solução resultam em um impacto negativo nas métricas de aprendizado, o controle de versão pode permitir uma reversão para a versão anterior e mais efetiva da solução.

A ferramenta mais comum para gerenciar repositórios de código é o [GitHub](https://guides.github.com) , que permite a criação de um repositório de código compartilhado com alguns cliques. Além disso, o recurso [Azure Repos](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops) do Azure DevOps pode ser usado para criar um repositório do [git](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) ou do [Team Foundation](https://docs.microsoft.com/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="feedback-loops"></a>Loops de comentários

A chave para a criação de parceiros de clientes durante os ciclos de inovação é tornar o cliente uma parte da solução. Isso é feito com um comprimento de braços por meio da [medição do impacto do cliente](./measure.md). Mais de melhor, ele requer conversas e testes diretos com o cliente. Ambos resultam em comentários que devem ser gerenciados.

Cada ponto de comentário é uma solução potencial para a necessidade do cliente. O mais importante é que todos os comentários diretamente de um cliente são uma oportunidade de melhorar a parceria. Se os comentários o fizerem em uma solução MVP, você será celebrado com o cliente. Mesmo que os comentários não sejam acionáveis, simplesmente sendo transparente com a decisão de despriorizar os comentários, demonstra uma [mentalidade de crescimento](./learn.md#growth-mindset) e um foco no [aprendizado contínuo](./learn.md#continuous-learning).

O [Azure DevOps](https://docs.microsoft.com/azure/devops) inclui maneiras de [solicitar, fornecer e gerenciar comentários](https://docs.microsoft.com/azure/devops/project/feedback). Cada uma dessas ferramentas centraliza os comentários para que a equipe possa agir e relatar comentários, fornecendo um loop transparente de comentários.

## <a name="continuous-integration"></a>Integração contínua

À medida que a adoção é dimensionada e uma hipótese cresce mais perto da verdadeira inovação em escala, o número de hipóteses menores a serem testadas aumentará rapidamente. Para fazer loops de comentários precisos e processos de adoção suave, é importante que cada uma dessas hipóteses esteja integrada e se apoio à hipótese primária por trás da inovação. Infelizmente, você também precisa se mover rapidamente para inovar e aumentar, o que exigirá que vários desenvolvedores testem variantes da hipótese principal. Para esforços de desenvolvimento de estágios posteriores, ele pode exigir várias equipes de desenvolvedores cada uma desenvolvendo para uma solução compartilhada. A integração contínua é a primeira etapa para o gerenciamento de várias partes móveis.

Na integração contínua, as alterações de código são frequentemente mescladas na ramificação principal. Processos automatizados de compilação e teste garantem que o código na ramificação principal seja sempre a qualidade da produção. Isso garante que os desenvolvedores estejam trabalhando juntos para desenvolver soluções compartilhadas que forneçam loops de comentários precisos e confiáveis.

O Azure DevOps and [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines) fornece recursos de integração contínua com alguns cliques, para o GitHub ou uma variedade de outros repositórios.
Saiba mais sobre a [integração contínua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-integration) ou execute o [laboratório prático](https://www.azuredevopslabs.com/labs/azuredevops/continuousintegration) para obter mais informações. Também há arquiteturas de solução para acelerar a criação de seus [pipelines de CI/CD usando o Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="reliable-testing"></a>Testes confiáveis

Defeitos em qualquer solução podem criar falsos positivos ou falsos negativos. Erros inesperados podem facilmente levar a uma má interpretação das métricas de adoção do usuário. Ele também pode levar a comentários negativos de clientes que não representam corretamente o teste de sua hipótese.

Durante as iterações iniciais de uma solução MVP, os defeitos são esperados, os pioneiros podem até mesmo encontrá-los. Em versões anteriores, o teste de aceitação provavelmente estará inexistente. No entanto, um aspecto da criação com empatia é a validação da necessidade e da hipótese. Ambos podem ser concluídos por meio de testes de unidade em um nível de código e testes de aceitação manual antes da implantação. Juntos, eles fornecerão alguns meios de confiabilidade no teste. O termo mais longo uma série bem definida de testes de compilação, unidade e aceitação deve ser automatizado para garantir métricas confiáveis relacionadas a ajustes mais refinados para a hipótese e a solução resultante.

O [Azure Test Plans](https://docs.microsoft.com/azure/devops/test/track-test-status?view=azure-devops) fornece ferramentas para desenvolver e operar planos de teste durante a execução de teste manual ou automatizada.

## <a name="solution-deployment"></a>Implantação da solução

Talvez o aspecto mais significativo da capacitação da adoção seja a capacidade de controlar o lançamento de uma solução para os clientes. Fornecer um pipeline automatizado ou autoatendimento para lançar uma solução para os clientes acelera o loop de comentários. Permitir que os clientes interajam com alterações na solução rapidamente, convida o cliente para o processo. Ele também permite testes mais rápidos de hipóteses, reduzindo suposições e potencial retrabalho.

O são várias abordagens para a implantação da solução, a seguinte descrição das três abordagens mais comuns:

- A abordagem mais avançada, a **implantação contínua**, implanta automaticamente as alterações de código na produção. Para equipes maduras testando hipóteses maduras, a implantação contínua pode ser extremamente valiosa.
- Durante os estágios iniciais do desenvolvimento, a **entrega contínua** pode ser mais apropriada. Na entrega contínua, todas as alterações de código são implantadas automaticamente em um ambiente semelhante à produção. Os desenvolvedores, tomadores de decisões de negócios e outros membros da equipe podem usar esse ambiente para validar que seu trabalho está pronto para produção. Ele também pode ser usado para testar uma hipótese com os clientes, sem afetar as atividades de negócios em andamento.
- A **implantação manual** é a abordagem menos avançada para o gerenciamento de liberações. Como o nome sugere, alguém da equipe implantaria manualmente as alterações de código mais recentes. Essa abordagem é propenso a erros, não confiável e é considerada um antipadrão por engenheiros mais experientes.

Durante a primeira iteração de uma solução MVP, a implantação manual é uma abordagem comum, apesar da descrição acima. Quando a solução é extremamente fluida e os comentários dos clientes são desconhecidos, há um risco significativo de redefinir toda a solução (ou até mesmo a hipótese principal). A regra geral para implantação manual: sem prova de cliente, sem automação de implantação. Investir cedo pode levar a perda de tempo. O mais importante é que ele pode criar dependências no pipeline de lançamento que tornaria a equipe mais resistente a um pivô inicial. Após as primeiras iterações ou quando os comentários dos clientes sugerem um sucesso potencial, um modelo mais avançado de implantação deve ser rapidamente adotado.

Em qualquer estágio da validação de hipóteses, o Azure DevOps e o [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines) fornecem recursos de entrega contínua e implantação contínua com apenas alguns cliques. Saiba mais sobre a [entrega contínua](https://docs.microsoft.com/azure/devops/learn/what-is-continuous-delivery) ou execute o [laboratório prático](https://www.azuredevopslabs.com/labs/azuredevops/continuousdeployment) para obter mais informações. As arquiteturas de solução também podem acelerar a criação de seus [pipelines de CI/CD usando o Azure DevOps](https://azure.microsoft.com/solutions/devops).

## <a name="integrated-measurements"></a>Medidas integradas

Ao [medir o impacto do cliente](./measure.md), é importante entender como os clientes reagem às alterações na solução. Esses dados, conhecidos como telemetria, fornecem informações sobre as ações que um uso (ou coorte de usuários) levaram ao usar a solução. A partir desses dados, é fácil obter uma validação quantitativa da hipótese. Essas métricas podem, então, ser usadas para ajustar a solução e gerar as mesmas mais refinadas. Essas alterações mais sutis ajudam a impulsionar a solução inicial em iterações subsequentes, levando, em última análise, a adotar a adoção em escala.

No Azure, [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) fornece as ferramentas e a interface para coletar e examinar os dados das experiências do cliente. Essas observações e ideias podem ser usadas para refinar a pendência usando [Azure boards](https://docs.microsoft.com/azure/devops/boards).

## <a name="next-steps"></a>Próximos passos

Com uma compreensão das ferramentas e dos processos necessários para capacitar a adoção, é hora de examinar uma disciplina de inovação mais avançada, [interagir com dispositivos](./devices.md). O que pode ajudar a reduzir as barreiras entre experiências físicas e digitais, tornando sua solução ainda mais fácil de adotar.

> [!div class="nextstepaction"]
> [Interagir com dispositivos](./devices.md)
