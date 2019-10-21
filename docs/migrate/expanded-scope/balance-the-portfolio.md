---
title: Balancear o portfólio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Para balancear seu portfólio de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 2b26f8c763d477d95b21e302158c318e3ab4b101
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548593"
---
# <a name="balance-the-portfolio"></a>Balancear o portfólio

A adoção de nuvem é um esforço de gerenciamento de portfólio, disfarçado de forma inteligente como implementação técnica. Como qualquer exercício de gerenciamento de portfólio, o balanceamento do portfólio é crítico. Em um nível estratégico, isso significa balancear a migração, a inovação e a experimentação para aproveitar ao máximo a nuvem. Quando o esforço de adoção da nuvem é muito distante em uma direção ou outra, a complexidade encontra seu caminho no esforço de migração. Este artigo orientará o leitor por meio de abordagens para obter o equilíbrio no portfólio.

## <a name="general-scope-expansion"></a>Expansão de escopo geral

Este tópico é estratégico por natureza. Como tal, a abordagem adotada neste artigo é igualmente estratégica. Para impulsionar a estratégia em decisões controladas por dados, este artigo pressupõe que o leitor avaliou o [espaço digital](../../digital-estate/index.md) existente (ou está no processo de fazer isso). O objetivo dessa abordagem é auxiliar na avaliação de cargas de trabalho para garantir um equilíbrio adequado entre o portfólio, por meio de perguntas qualitativas e refinamento de portfólio.

### <a name="documenting-business-outcomes"></a>Documentando resultados de negócios

Antes de balancear o portfólio, é importante documentar e compartilhar os resultados de negócios que levam ao esforço de migração na nuvem. Para alguns exemplos de resultados de negócios gerais relacionados a migrações na nuvem, consulte o [Resumo executivo de migração de nuvem](../../getting-started/migrate.md).

A tabela a seguir pode ajudar a documentar e compartilhar os resultados de negócios desejados. É importante observar que a maioria das empresas está buscando vários resultados por vez. A importância deste exercício é esclarecer os resultados que estão mais diretamente relacionados ao esforço de migração na nuvem:

|Saída  |Medido por  |Goal  |Período de tempo  |Prioridade para esse esforço  |
|---------|---------|---------|---------|---------|
|Reduzir os custos de ti     |Orçamento do datacenter         |Reduzir em US $2 milhões         |12 meses         |#1         |
|Saída do datacenter     |Sair dos data centers         |2 data centers         |6 meses         |#2         |
|Aumentar a agilidade dos negócios     |Melhorar o tempo de colocação no mercado  |Reduzir o tempo de implantação em seis meses         |2 anos         |#3        |
|Melhorar a experiência do cliente     |Satisfação do cliente (CSAT)         |melhoria de 10%         |12 meses         |#4         |

> [!IMPORTANT]
> A tabela acima é um exemplo fictício e não deve ser usada para definir prioridades. Em muitos casos, essa tabela pode ter considerado um antipadrão colocando economia de custos acima das experiências do cliente.

A tabela acima pode representar com precisão as prioridades da equipe de estratégia de nuvem e a equipe de adoção da nuvem supervisionando uma migração na nuvem. Devido a restrições de curto prazo, essa equipe está dando uma ênfase maior na redução de custos de ti e priorizando uma saída de datacenter como meio de atingir as reduções de custo de ti desejadas. No entanto, ao documentar as prioridades concorrentes nesta tabela, a equipe de adoção de nuvem é capacitada para ajudar a equipe de estratégia de nuvem a identificar oportunidades para alinhar melhor a implementação da estratégia de portfólio abrangente.

### <a name="move-fast-while-maintaining-balance"></a>Mover rapidamente enquanto mantém o saldo

A orientação sobre a [racionalização incremental do estado digital](../../digital-estate/index.md) sugere uma abordagem na qual a racionalização começa com uma posição desbalanceada. A equipe de estratégia de nuvem deve avaliar cada carga de trabalho para compatibilidade com uma abordagem de rehospedagem. Essa abordagem é sugerida porque permite a rápida avaliação de um espaço digital complexo baseado em dados quantitativos. Fazer essa suposição inicial permite que a equipe de adoção de nuvem se envolva rapidamente, reduzindo o tempo para resultados de negócios. No entanto, conforme indicado neste artigo, as perguntas qualitativas fornecerão o saldo necessário no portfólio. Este artigo documenta o processo de criação do saldo prometido.

### <a name="importance-of-sunset-and-retire-decisions"></a>Importância do pôr do sol e das decisões de desativação

A tabela na seção [documentando os resultados de negócios](#documenting-business-outcomes) acima perde um resultado importante que seria compatível com o objetivo número um de redução dos custos de ti. Quando os custos das reduções de ti se classificam em qualquer lugar da lista de resultados de negócios, é importante considerar o potencial de pôr o sol ou desativar as cargas de trabalho. Em alguns cenários, a economia de custos pode vir de não migrar cargas de trabalho que não asseguram um investimento de curto prazo. Alguns clientes relataram economias de custos em excesso de 20% de reduções de custo total ao desativar cargas de trabalho subutilizadas.

Para balancear o portfólio, melhorando as decisões sobre o pôr do sol e de desativação, a equipe de estratégia de nuvem e a equipe de adoção de nuvem são incentivadas a fazer as seguintes perguntas de cada carga de trabalho nos processos de avaliação e migração:

- A carga de trabalho foi usada pelos usuários finais nos últimos seis meses?
- O tráfego do usuário final está consistente ou crescendo?
- Essa carga de trabalho será exigida pelos negócios de 12 meses a partir de agora?

Se a resposta a qualquer uma dessas perguntas for "não", a carga de trabalho poderá ser um candidato para aposentadoria. Se o potencial de aposentadoria for confirmado com o proprietário do aplicativo, talvez não faça sentido migrar a carga de trabalho. Isso solicita algumas perguntas de qualificação:

- É possível estabelecer um plano de aposentadoria ou um plano de pôr-se nessa carga de trabalho?
- Essa carga de trabalho pode ser desativada antes da saída do datacenter?

Se a resposta para essas duas perguntas for "Sim", seria prudente considerar _não_ migrar a carga de trabalho. Essa abordagem ajudaria a atender aos objetivos da redução de custos e à saída do datacenter.

Se a resposta para qualquer uma das perguntas for "não", pode ser conveniente estabelecer um plano para hospedar a carga de trabalho até que ela possa ser desativada. Esse plano pode incluir a movimentação de ativos para um datacenter de menor custo ou um datacenter alternativo, o que também atingiria os objetivos da redução de custos e a saída de um datacenter.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Os pré-requisitos especificados no guia de linha de base ainda devem ser suficientes para abordar esse tópico de complexidade. No entanto, o inventário de ativos e o estado digital devem ser realçados e estar em negrito entre esses pré-requisitos, pois esses dados direcionarão as atividades a seguir.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

O balanceamento do portfólio requer uma análise qualitativa adicional durante o processo de avaliação, o que ajudará a impulsionar a racionalização do portfólio simples.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

Com base nos dados da tabela na seção [documentando os resultados de negócios](#documenting-business-outcomes) acima, há um risco provável de que o portfólio se torne muito distante em um modelo de execução focado em migração. Se a experiência do cliente foi a prioridade principal, um portfólio pesado de inovação seria mais provável. Nenhuma delas está certa ou errada, mas a retratação muito distante em uma direção normalmente resulta em redução de retornos, adiciona complexidade desnecessária e aumenta o tempo de execução relacionado aos esforços de adoção da nuvem.

Para reduzir a complexidade, é recomendável que o leitor siga uma abordagem tradicional para a racionalização do portfólio, mas em um modelo iterativo. As etapas a seguir descrevem um modelo qualitativo para essa abordagem:

- A equipe de estratégia de nuvem mantém uma acumulação priorizada de cargas de trabalho a serem migradas.
- A equipe de estratégia de nuvem e a equipe de adoção de nuvem hospedam uma reunião de planejamento de lançamento antes da conclusão de cada versão.
- Na reunião de planejamento de liberação, as equipes concordam com as 5 a 10 cargas de trabalho da lista de pendências priorizadas.
- Fora da reunião de planejamento de versão, a equipe de adoção de nuvem faz as seguintes perguntas de proprietários de aplicativos e especialistas no assunto:
  - Este aplicativo pode ser substituído por um equivalente de plataforma como serviço (PaaS)?
  - Este aplicativo é um aplicativo de terceiros?
  - O orçamento foi aprovado para investir no desenvolvimento contínuo do aplicativo nos próximos 12 meses?
  - O desenvolvimento adicional desse aplicativo melhoraria a experiência do cliente? Criar um diferencial competitivo? Impulsionar receita adicional para os negócios?
  - Os dados nessa carga de trabalho contribuem para uma inovação de downstream relacionada a BI, Machine Learning, IoT ou tecnologias relacionadas?
  - A carga de trabalho é compatível com plataformas de aplicativos modernas, como Azure App Service?
- As respostas às perguntas acima e qualquer outra análise qualitativa necessária influenciaria os ajustes na pendência priorizada. Esses ajustes podem incluir:
  - Se uma carga de trabalho puder ser substituída por uma solução PaaS, ela poderá ser removida da pendência de migração inteiramente. No mínimo, a auditoria detalhada adicional para decidir entre Rehost e substituição seria adicionada como uma tarefa, reduzindo temporariamente a prioridade da carga de trabalho da pendência de migração.
  - Se uma carga de trabalho estiver passando por um avanço de desenvolvimento (ou deveria ser), ela poderá se ajustar melhor a um modelo de refatoração/recriação/reconstrução. Como a inovação e a migração exigem habilidades técnicas diferentes, geralmente é recomendável que os aplicativos que se alinham a uma abordagem de refatoração/recriação/reconstrução sejam gerenciados por meio de uma pendência de inovação, em oposição a uma pendência de migração.
  - Se uma carga de trabalho fizer parte de uma inovação de downstream, poderá fazer sentido refatorar a plataforma de dados, mas deixar as camadas do aplicativo como um candidato de host. A refatoração secundária da plataforma de dados de uma carga de trabalho geralmente pode ser resolvida em uma migração ou em uma pendência de inovação. Esse resultado de racionalização pode resultar em itens de trabalho mais detalhados na pendência, mas, caso contrário, nenhuma alteração nas prioridades.
  - Se uma carga de trabalho não for estratégica, mas for compatível com plataformas de Hospedagem de aplicativos modernas e baseadas em nuvem, poderá ser prudente executar refatoração secundária no aplicativo para implantá-lo como um aplicativo moderno. Isso pode contribuir para a economia geral, reduzindo os requisitos gerais de licenciamento de IaaS e so da migração na nuvem.
  - Se uma carga de trabalho for um aplicativo de terceiros e os dados da carga de trabalho não estiverem planejados para uso em uma inovação de downstream, pode ser melhor deixá-lo como uma opção de novo host na pendência.

Essas perguntas não devem ser a extensão da análise qualitativa concluída para cada carga de trabalho, mas destinam-se a orientar uma conversa que ajuda a resolver a complexidade de um portfólio desbalanceado.

## <a name="migrate-process-changes"></a>Migrar alterações de processo

Durante a migração, as atividades de balanceamento de portfólio podem ter um impacto negativo na velocidade de migração (a rapidez na qual os ativos são migrados). As diretrizes a seguir se expandirão sobre por que e como alinhar o trabalho para evitar interrupções no esforço de migração.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

A racionalização do portfólio requer diversidade de esforço técnico. É tentador que as equipes de adoção de nuvem correspondam à diversidade de portfólio nos esforços de migração. Os interessados comerciais de pedir uma única equipe de adoção de nuvem para atender à pendência de migração inteira. Isso raramente é uma abordagem aconselhável, em muitos casos, isso pode ser produtivo.

É recomendável que esses diversos esforços sejam segmentados em duas ou mais equipes de adoção de nuvem. Usando um modelo de duas equipes como um modo de execução de exemplo, a equipe 1 é a equipe de migração e a equipe 2 é a equipe de inovação. Para esforços maiores, essas equipes podem ser mais segmentadas para abordar outras abordagens, como esforços de substituição/PaaS ou refatoração secundária. A seguir, é descrita as habilidades e as funções necessárias para rehospedar, refatorar ou fazer uma reformulação secundária:

**Hospedar novamente:** O Rehost exige que os membros da equipe implementem alterações focadas na infraestrutura. Geralmente, usar uma ferramenta como Azure Site Recovery para migrar VMs ou outros ativos para o Azure. Esse trabalho se alinha bem aos administradores do Datacenter ou implementadores de ti. A equipe de migração de nuvem está bem estruturada para fornecer esse trabalho em alta escala. Essa é a abordagem mais rápida para migrar ativos existentes na maioria dos cenários.

**Refatorar:** O Refactor exige que os membros da equipe modifiquem o código-fonte, alterem a arquitetura de um aplicativo ou adotem novos serviços de nuvem. Geralmente, esse esforço usaria ferramentas de desenvolvimento como o Visual Studio e ferramentas de pipeline de implantação como o Azure DevOps para reimplantar aplicativos modernos no Azure. Esse trabalho se alinha bem às funções de desenvolvimento de aplicativos ou às funções de desenvolvimento de pipeline DevOps. A equipe de inovação na nuvem é mais bem estruturada para fornecer esse trabalho. Pode levar mais tempo para substituir ativos existentes por ativos de nuvem nessa abordagem, mas os aplicativos podem aproveitar os recursos nativos de nuvem.

**Refatoração secundária:** Alguns aplicativos podem ser modernizados com refatoração secundária no nível de dados ou de aplicativo. Esse trabalho exige que os membros da equipe implantem dados em plataformas de dados baseadas em nuvem ou façam alterações de configuração secundárias no aplicativo. Isso pode exigir suporte limitado para especialistas no assunto do desenvolvimento de aplicativos ou de dados. No entanto, esse trabalho é semelhante ao trabalho realizado por implementadores de ti ao implantar aplicativos de terceiros. Esse trabalho pode facilmente se alinhar com a equipe de migração na nuvem ou com a equipe de estratégia de nuvem. Embora esse esforço não seja tão rápido quanto uma migração de novo host, leva menos tempo para ser executado do que os esforços de refatoração.

Durante a migração, é recomendável que os esforços sejam segmentados nas três maneiras listadas acima, e que esses esforços sejam executados pela equipe apropriada na iteração apropriada. Embora seja recomendável que o portfólio seja diversificado, também é recomendável que os esforços fiquem muito concentrados e separados.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Nenhuma alteração adicional é necessária durante a otimização e a promoção de processos dentro do esforço de migração.

## <a name="secure-and-manage-process-changes"></a>Proteger e gerenciar alterações de processo

Nenhuma alteração adicional é necessária durante os processos de segurança e gerenciamento no esforço de migração.

## <a name="next-steps"></a>Próximos passos

Retorne à [lista de verificação de escopo expandido](./index.md) para garantir que o método de migração esteja totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
