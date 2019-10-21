---
title: Estratégia de governança ou conformidade
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Estratégia de governança ou conformidade
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a6371fe5f3d90e72b29ecfc1e66b3d4991ef5822
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549241"
---
# <a name="governance-or-compliance-strategy"></a>Estratégia de governança ou conformidade

Quando a governança ou a conformidade é necessária durante um esforço de migração, é necessário um escopo adicional. As diretrizes a seguir expandirão o escopo do [Guia de migração do Azure](../azure-migration-guide/index.md) para abordar abordagens diferentes para atender aos requisitos de governança ou de conformidade.

## <a name="general-scope-expansion"></a>Expansão de escopo geral

As atividades de pré-requisito são afetadas quanto mais quando a governança ou a conformidade são necessárias. Ajustes adicionais podem ser necessários durante a avaliação, a migração e a otimização.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

A configuração do ambiente base do Azure pode mudar significativamente ao integrar os requisitos de governança ou de conformidade. Para entender como os pré-requisitos mudam, é importante entender a natureza dos requisitos. Antes de iniciar qualquer migração que exija governança ou conformidade, uma abordagem deve ser escolhida e implementada no ambiente de nuvem. Veja a seguir algumas abordagens de alto nível normalmente vistas durante as migrações:

**Abordagem de governança comum:** Para a maioria das organizações, o [modelo de governança da estrutura de adoção da nuvem](../../govern/guides/index.md) é uma abordagem suficiente que consiste em uma implementação do MVP (produto viável) mínima, seguida pelas iterações direcionadas da maturidade de governança para abordar os riscos tangíveis identificado no plano de adoção. Essa abordagem fornece as ferramentas mínimas necessárias para estabelecer governança consistente, para que a equipe possa entender as ferramentas. Em seguida, ele se expande nessas ferramentas para resolver preocupações comuns de governança.

**Plantas de conformidade ISO 27001:** Para clientes que precisam aderir aos padrões de conformidade ISO, os exemplos de [plantas de serviços compartilhados iso 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-shared/index) podem servir como um MVP mais eficaz para produzir restrições de governança mais avançadas no processo iterativo anteriormente. O [exemplo de banco de dados ambiente do serviço de aplicativo/SQL do ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-ase-sql-workload) expande o plano gráfico para mapear controles e implantar uma arquitetura comum para um ambiente de aplicativo. Conforme os planos de conformidade adicionais são lançados, eles também serão referenciados aqui.

**Datacenter virtual:** Um ponto de partida de governança mais robusto pode ser necessário. Nesses casos, considere o [Azure virtual datacenter (VDC)](../../reference/vdc.md). Essa abordagem é comumente sugerida durante os esforços de adoção de escala empresarial e, especialmente, para esforços que excedem 10.000 ativos. Também é a escolha de fato para cenários de governança complexos quando qualquer uma das seguintes opções são necessárias: requisitos de conformidade de terceiros abrangentes, profundo conhecimento do domínio ou paridade com políticas de governança de ti e requisitos de conformidade maduros.

### <a name="partnership-option-to-complete-prerequisites"></a>Opção de parceria para concluir os pré-requisitos

**Serviços da Microsoft:** Os serviços da Microsoft fornecem ofertas de soluções que podem se alinhar ao modelo de governança da estrutura de adoção da nuvem, plantas de conformidade ou opções de datacenter virtual para garantir o modelo de governança ou conformidade mais apropriado. Use a solução de [ficção (proteção de nuvem segura)](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) para estabelecer uma imagem orientada por dados de uma implantação de cliente no Azure e validar a maturidade de implementação do mercado do cliente ao identificar a otimização das arquiteturas de implantação existentes , remova os riscos de segurança e disponibilidade de governança. Com base em informações do cliente, você deve conduzir com as seguintes abordagens:

- **Base da nuvem:** Estabeleça os principais designs, padrões e arquitetura de governança do Azure do cliente com a oferta de solução de [HCF (híbrido Cloud Foundation)](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf) . Mapeie os requisitos do cliente para a arquitetura de referência mais apropriada. Implemente um produto viável mínimo que consiste em serviços compartilhados e cargas de trabalho de IaaS.
- **Modernização de nuvem:** Use a oferta de solução de [modernização de nuvem](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) como uma abordagem abrangente para mover aplicativos, dados e infraestrutura para uma nuvem pronta para a empresa, bem como para otimizar e modernizar uma vez na nuvem.
- **Inovar com nuvem:** Envolva clientes por meio de uma abordagem inovadora e exclusiva [de solução de CCOE (Cloud Center of Excellence)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) que cria uma organização de ti moderna para permitir a agilidade em escala com o DevOps enquanto permanece no controle. Implementa uma abordagem ágil para capturar requisitos de negócios, reutilizar pacotes de implantação alinhados com políticas de segurança, conformidade e gerenciamento de serviços e mantém a plataforma do Azure alinhada com procedimentos operacionais.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Durante a avaliação, são necessárias decisões adicionais para alinhar-se à abordagem de governança necessária. A equipe de governança de nuvem deve fornecer a todos os membros da equipe de adoção de nuvem qualquer declaração de política, diretrizes arquitetônicas ou requisitos de governança/conformidade antes da avaliação de uma carga de trabalho.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

Os requisitos de avaliação de governança e conformidade são muito específicos do cliente para fornecer orientação geral sobre as etapas reais realizadas durante a avaliação. No entanto, é recomendável que o processo inclua tarefas e alocações de tempo para "alinhamento aos requisitos de conformidade/governança". Para obter mais noções básicas sobre esses requisitos, consulte os links a seguir:

Para uma compreensão mais profunda da governança, examine as [cinco disciplinas de visão geral do governança de nuvem](../../govern/governance-disciplines.md). Esta seção da estrutura de adoção de nuvem também inclui modelos para documentar as políticas, as diretrizes e os requisitos de cada uma das cinco seções:

- [Gerenciamento de custos](../../govern/cost-management/template.md)
- [Linha de base de segurança](../../govern/security-baseline/template.md)
- [Consistência de recursos].. /.. /govern/resource-consistency/template.md)
- [Linha de base de identidade].. /.. /govern/identity-baseline/template.md)
- [Aceleração da implantação](../../govern/deployment-acceleration/template.md)

Para obter orientação sobre como desenvolver diretrizes de governança com base no modelo de governança da estrutura de adoção da nuvem, consulte [implementando uma estratégia de governança de nuvem](../../govern/corporate-policy.md).

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Durante os processos de otimização e promoção, é recomendável que a equipe de governança de nuvem investe tempo para testar e validar a adesão aos padrões de governança e conformidade. Além disso, essa etapa é um bom momento para injetar processos para a equipe de governança de nuvem para organizar modelos que podem fornecer [aceleração de implantação](../../govern/deployment-acceleration/index.md) adicional para projetos futuros.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Ação sugerida durante o processo de otimização e promoção

Durante esse processo, é recomendável que o plano de projeto inclua alocações de tempo para a equipe de governança de nuvem executar uma análise de conformidade para cada carga de trabalho planejada para promoção de produção.

## <a name="next-steps"></a>Próximos passos

Como o item final na [lista de verificação de escopo expandido](./index.md), o leitor é aconselhado a retornar à lista de verificação e reavaliar os requisitos de escopo adicionais para o esforço de migração.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
