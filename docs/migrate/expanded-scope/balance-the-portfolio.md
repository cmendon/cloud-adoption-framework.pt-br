---
title: Equilibrar o portfólio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Para balancear seu portfólio de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7383f07f4d52cef640bcb1e617de60697a20b248
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753480"
---
# <a name="balance-the-portfolio"></a>Equilibrar o portfólio

A adoção da nuvem é um esforço de gerenciamento de portfólio, inteligentemente disfarçado de implementação técnica. Como qualquer exercício de gerenciamento de portfólio, o balanceamento do portfólio é crítico. Em um nível estratégico, isso significa balancear a migração, a inovação e a experimentação para aproveitar a nuvem ao máximo. Quando a tentativa de adoção da nuvem se inclina demais em uma direção ou outra, a complexidade encontra seu caminho no esforço de migração. Este artigo orientará o leitor pelas abordagens para alcançar o equilíbrio no portfólio.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

Este tópico é de natureza estratégica. Como tal, a abordagem adotada neste artigo é igualmente estratégica. Para fundamentar a estratégia em decisões baseadas em dados, este artigo pressupõe que o leitor tenha avaliado o [acervo digital](../../digital-estate/index.md) existente (ou está em vias de fazer isso). O objetivo dessa abordagem é auxiliar na avaliação das cargas de trabalho para garantir o equilíbrio adequado em todo o portfólio através de perguntas qualitativas e refinamento do portfólio.

### <a name="document-business-outcomes"></a>Documentar resultados de negócios

Antes de balancear o portfólio, é importante documentar e compartilhar os resultados de negócios que levam ao esforço de migração na nuvem. Para ver exemplos de resultados empresariais gerais relacionados às migrações na nuvem, confira o [resumo executivo de migração na nuvem](../../getting-started/migrate.md).

A tabela a seguir pode ajudar a documentar e compartilhar os resultados empresariais desejados. É importante notar que a maioria das empresas tem buscando vários resultados de cada vez. A importância deste exercício é esclarecer os resultados que estão mais diretamente relacionados ao esforço de migração na nuvem:

|Resultado  |Medido por  |Objetivo  |Período  |Prioridade do esforço  |
|---------|---------|---------|---------|---------|
|Reduzir custos de TI     |Orçamento do datacenter         |Reduzir em US$ 2 milhões         |12 meses         |Nº 1         |
|Saída do datacenter     |Saída dos datacenters         |2 datacenters         |6 meses         |Nº 2         |
|Aumentar a agilidade dos negócios     |Melhorar o tempo de comercialização  |Reduzir o tempo de implantação em seis meses         |2 anos         |Nº 3        |
|Melhorar a experiência do cliente     |Satisfação do cliente (CSAT)         |10% de melhoria         |12 meses         |Nº 4         |

> [!IMPORTANT]
> A tabela acima é um exemplo fictício e não deve ser usada para definir prioridades. Em muitos casos, essa tabela pode ser considerada um antipadrão ao se colocar economias de custos acima das experiências do cliente.

A tabela acima poderia representar com precisão as prioridades da equipe de estratégia da nuvem e da equipe de adoção da nuvem que supervisionam uma migração na nuvem. Devido a restrições de curto prazo, essa equipe tem dado maior ênfase à redução de custos de TI e priorizado a saída de um datacenter como uma forma de atingir as reduções de custos de TI desejadas. No entanto, ao documentar as prioridades concorrentes nesta tabela, a equipe de adoção da nuvem tem o poder de ajudar a equipe de estratégia da nuvem a identificar oportunidades para alinhar melhor a implementação da estratégia do portfólio abrangente.

### <a name="move-fast-while-maintaining-balance"></a>Mova-se rapidamente mantendo o equilíbrio

A orientação referente à [racionalização incremental do acervo digital](../../digital-estate/index.md) sugere uma abordagem na qual a racionalização começa com uma posição desequilibrada. A equipe de estratégia da nuvem deve avaliar cada carga de trabalho para verificar a compatibilidade com uma abordagem de nova hospedagem. Essa abordagem é sugerida porque permite a rápida avaliação de um acervo digital complexo com base em dados quantitativos. Fazer essa pressuposição inicial permite que a equipe de adoção da nuvem se envolva rapidamente e reduza o tempo de obtenção dos resultados dos negócios. No entanto, conforme indicado nesse artigo, as perguntas qualitativas fornecerão o equilíbrio necessário no portfólio. Este artigo documenta o processo de criação do equilíbrio prometido.

### <a name="importance-of-sunset-and-retire-decisions"></a>A importância das decisões de aposentadoria e caducidade

A tabela na seção de [documentação dos resultados empresariais](#document-business-outcomes) acima, deixa de fora um importante resultado que daria suporte ao primeiro objetivo de redução dos custos de TI. Quando as reduções de custos de TI ocupam um lugar na lista de resultados empresariais, é importante considerar o potencial da caducidade ou aposentadoria das cargas de trabalho. Em alguns cenários, a economia de custos pode vir da NÃO migração de cargas de trabalho que não garantem um investimento de curto prazo. Alguns clientes relataram economias de custo que ultrapassaram os 20% das reduções totais de custos quando retiraram cargas de trabalho subutilizadas.

Para equilibrar o portfólio, refletindo melhor sobre as decisões de caducidade e desativação, a equipe de estratégia da nuvem e a equipe de adoção da nuvem serão incentivadas a fazer as seguintes perguntas a cada carga de trabalho nos processos de avaliação e migração:

- A carga de trabalho foi usada pelos usuários finais nos últimos seis meses?
- O tráfego do usuário final mantém-se consistente ou tem crescido?
- Esta carga de trabalho será exigida pela empresa daqui a 12 meses?

Se a resposta a qualquer uma dessas perguntas for "Não", a carga de trabalho poderá ser uma candidata à aposentadoria. Se o potencial de aposentadoria for confirmado pelo proprietário do aplicativo, talvez não faça sentido migrar a carga de trabalho. Isso exige algumas questões de qualificação:

- É possível estabelecer um plano de aposentadoria ou caducidade para essa carga de trabalho?
- Essa carga de trabalho pode ser desativada antes da saída do datacenter?

Se a resposta para essas duas perguntas for "Sim", seria prudente considerar _não_ migrar a carga de trabalho. Essa abordagem ajudaria a atingir os objetivos de redução de custos e saída do datacenter.

Se a resposta a qualquer das perguntas for "Não", pode ser sensato estabelecer um plano para hospedar a carga de trabalho até que ela possa seja desativada. Esse plano poderia incluir a transferência dos ativos para um datacenter de custo mais reduzido ou um datacenter alternativo, o que também atingiria os objetivos de redução de custos e saída do datacenter.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

Os pré-requisitos especificados no guia de linha de base ainda devem ser suficientes para abordar esse tópico complexo. No entanto, o inventário de ativos e o estado digital devem ser realçados e estar em negrito entre esses pré-requisitos, pois esses dados direcionarão as atividades a seguir.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Equilibrar o portfólio exige uma análise qualitativa adicional durante o processo de avaliação e isso ajudará a direcionar a racionalização simples do portfólio.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

Com base nos dados da tabela da seção [documentação dos resultados empresariais](#document-business-outcomes) acima, há um risco provável do portfólio estar muito inclinado para um modelo de execução focado na migração. Se a experiência do cliente fosse a prioridade máxima, um portfólio pesado de inovação seria o mais provável. Nenhum modelo está certo nem errado, mas pender muito em uma direção geralmente leva a resultados decrescentes, adiciona complexidade desnecessária e aumenta o tempo de execução relacionado aos esforços de adoção da nuvem.

Para reduzir a complexidade, você deve seguir uma abordagem tradicional para a racionalização do portfólio, mas em um modelo iterativo. As etapas a seguir descrevem um modelo qualitativo para essa abordagem:

- A equipe de estratégia da nuvem mantém uma lista de pendências priorizada das cargas de trabalho que serão migradas.
- A equipe de estratégia da nuvem e a equipe de adoção da nuvem organizam uma reunião de planejamento de versão antes da conclusão de cada versão.
- Na reunião de planejamento do lançamento, as equipes concordam com as 5 a 10 cargas de trabalho mais importantes da lista de pendências priorizada.
- Fora da reunião de planejamento do lançamento, a equipe de adoção da nuvem faz as seguintes perguntas aos proprietários de aplicativos e especialistas no assunto:
  - Este aplicativo poderia ser substituído por um aplicativo equivalente de plataforma como serviço (PaaS)?
  - Este aplicativo é um aplicativo de terceiros?
  - O orçamento foi aprovado para investimento no desenvolvimento contínuo do aplicativo nos próximos 12 meses?
  - Um maior desenvolvimento desse aplicativo melhoraria a experiência do cliente? Criaria um diferencial competitivo? Impulsionaria uma maior geração de receita para os negócios?
  - Os dados dentro dessa carga de trabalho contribuirão para uma inovação downstream relacionada ao BI, Machine Learning, IoT ou tecnologias relacionadas?
  - A carga de trabalho é compatível com plataformas de aplicativos modernas, como o Serviço de Aplicativo do Azure?
- As respostas às perguntas acima e qualquer outra análise qualitativa necessária influenciariam os ajustes da lista de pendências priorizada. Esses ajustes podem incluir:
  - Se uma carga de trabalho puder ser substituída por uma solução PaaS, ela poderá ser totalmente removida da lista de pendências da migração. No mínimo, uma auditoria detalhada adicional para decidir entre Rehost e substituição seria adicionada como uma tarefa, reduzindo temporariamente a prioridade da carga de trabalho da pendência de migração.
  - Se uma carga de trabalho for (ou deve estar) passando por um avanço no desenvolvimento, pode ser melhor se ajustar a um modelo de recriação de reestruturação-recompilação. Como a inovação e a migração exigem habilidades técnicas diferentes, os aplicativos que se alinham a uma abordagem refatorar-recriação de recompilação devem ser gerenciados por meio de uma pendência de inovação em vez de uma pendência de migração.
  - Se uma carga de trabalho fizer parte de uma inovação downstream, talvez faça sentido refatorar a plataforma de dados, mas deixar as camadas do aplicativo disponíveis para nova hospedagem. A refatoração secundária da plataforma de dados de uma carga de trabalho geralmente pode ser tratada em uma lista de pendências de migração ou inovação. Esse resultado de racionalização pode resultar em itens de trabalho mais detalhados na lista de pendências, mas, por outro lado, sem alterações nas prioridades.
  - Se uma carga de trabalho não for estratégica, mas for compatível com plataformas de hospedagem de aplicativos modernas baseadas em nuvem, talvez seja prudente realizar pequenas refatorações no aplicativo para implantá-las como um aplicativo moderno. Isso pode contribuir para a economia geral reduzindo os requisitos gerais de licenciamento de IaaS e sistema operacional da migração na nuvem.
  - Se uma carga de trabalho for de terceiros e os dados da carga de trabalho não forem planejados para uso em uma inovação downstream, talvez seja melhor deixar como uma opção de nova hospedagem na lista de pendências.

Essas perguntas não devem ser o âmbito da análise qualitativa concluída para cada carga de trabalho, mas têm a intenção de orientar uma conversa para ajudar a resolver a complexidade de um portfólio desequilibrado.

## <a name="migrate-process-changes"></a>Alterações no processo de migração

Durante a migração, as atividades de equilíbrio do portfólio podem ter um impacto negativo na velocidade de migração (a rapidez na qual os ativos são migrados). A orientação a seguir falará mais sobre os motivos e como alinhar o trabalho para evitar interrupções no esforço de migração.

### <a name="suggested-action-during-the-migrate-process"></a>Ação sugerida durante o processo de migração

A racionalização do portfólio exige diversidade do esforço técnico. A ideia que as equipes de adoção da nuvem correspondam à diversidade do portfólio nos esforços de migração é tentadora. Os stakeholders de negócios solicitam uma única equipe de adoção da nuvem para abordar toda a lista de pendências de migração. Isso raramente é uma abordagem recomendável e, em muitos casos, pode ser contraproducente.

Esses diversos esforços devem ser segmentados em duas ou mais equipes de adoção de nuvem. Usando um modelo de duas equipes como um modo de execução de exemplo, a Equipe 1 é a Equipe de migração e a Equipe 2 é a Equipe de inovação. Para esforços maiores, essas equipes poderiam ser mais segmentadas para tratar de outras abordagens, como esforços de Substituição/PaaS ou Refatoração secundária. A seguir descrevemos as habilidades e funções necessárias para Nova hospedagem, Refatoração ou Refatoração secundária:

**Hospedar novamente:** O Rehost exige que os membros da equipe implementem alterações focadas na infraestrutura. Geralmente usando uma ferramenta como o Azure Site Recovery para migrar VMs ou outros ativos para o Azure. Este trabalho se alinha bem com os administradores do datacenter ou implementadores de TI. A equipe de migração na nuvem está bem estruturada para fornecer esse trabalho em alta escala. Essa é a abordagem mais rápida para migrar ativos existentes na maioria dos cenários.

**Refatorar:** O Refactor exige que os membros da equipe modifiquem o código-fonte, alterem a arquitetura de um aplicativo ou adotem novos serviços de nuvem. Geralmente, esse esforço usaria ferramentas de desenvolvimento como o Visual Studio e ferramentas de pipeline de implantação como o Azure DevOps para reimplantar aplicativos modernizados no Azure. Esse trabalho se alinha bem com as funções de desenvolvimento de aplicativos ou funções de desenvolvimento de pipeline do DevOps. A equipe de Inovação na nuvem está bem estruturada para fornecer esse trabalho. Nessa abordagem, pode até levar mais tempo para substituir os ativos existentes pelos recursos da nuvem, mas os aplicativos podem aproveitar os recursos nativos da nuvem.

**Refatoração secundária:** Alguns aplicativos podem ser modernizados com refatoração secundária no nível de dados ou de aplicativo. Esse trabalho exige que os membros da equipe implantem dados em plataformas de dados baseadas em nuvem ou façam alterações de configuração secundárias no aplicativo. Isso pode exigir suporte limitado para especialistas no assunto de desenvolvimento de aplicativos ou de dados. No entanto, esse trabalho é semelhante ao trabalho realizado por implementadores de TI durante a implantação de aplicativos de terceiros. Esse trabalho pode ser facilmente alinhado com a equipe de migração na nuvem ou a equipe de estratégia da nuvem. Embora esse esforço não seja tão rápido quanto uma migração de nova hospedagem, leva menos tempo para ser executado do que os esforços de refatoração.

Durante a migração, os esforços devem ser segmentados nas três maneiras listadas acima e executadas pela equipe apropriada na iteração apropriada. Embora você deva diversificar o portfólio, também garanta que os esforços fiquem muito concentrados e separados.

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Não são necessárias alterações adicionais durante os processos de Otimização e Promoção no esforço de migração.

## <a name="secure-and-manage-process-changes"></a>Proteger e gerenciar alterações no processo

Não são necessárias alterações adicionais durante os processos de Proteção e Gerenciamento no esforço de migração.

## <a name="next-steps"></a>Próximos passos

Retorne à [lista de verificação de escopo expandido](./index.md) para verificar se o método de migração está totalmente alinhado.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
