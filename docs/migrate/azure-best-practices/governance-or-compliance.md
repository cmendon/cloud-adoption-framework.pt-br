---
title: Estratégia de governança ou conformidade
description: Estratégia de governança ou conformidade
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 17952dc4c3ff28f2fcfe1a378a9efb969d65925b
ms.sourcegitcommit: 58ea417a7df3318e3d1a76d3807cc4e7e3976f52
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78897973"
---
# <a name="governance-or-compliance-strategy"></a>Estratégia de governança ou conformidade

Quando a governança ou a conformidade é necessária durante um esforço de migração, é necessário um escopo adicional. As orientações a seguir expandem o escopo do [guia de migração do Azure](../azure-migration-guide/index.md) para tratar de abordagens diferentes para atender a requisitos de governança ou de conformidade.

## <a name="general-scope-expansion"></a>Expansão do escopo geral

As atividades de pré-requisito são mais afetadas quando a governança ou a conformidade são necessárias. Ajustes adicionais podem ser necessários durante a avaliação, a migração e a otimização.

## <a name="suggested-prerequisites"></a>Pré-requisitos sugeridos

A configuração do ambiente base do Azure pode mudar significativamente ao integrar requisitos de governança ou de conformidade. Para entender como os pré-requisitos mudam, é importante entender a natureza deles. Antes de iniciar qualquer migração que exija governança ou conformidade, uma abordagem deve ser escolhida e implementada no ambiente de nuvem. Veja a seguir algumas abordagens de alto nível normalmente vistas durante migrações:

**Abordagem de governança comum:** Para a maioria das organizações, o [modelo de governança da estrutura de adoção da nuvem](../../govern/guides/index.md) é uma abordagem suficiente que consiste em uma implementação do MVP (produto viável) mínima, seguida pelas iterações direcionadas da maturidade de governança para resolver os riscos tangíveis identificados no plano de adoção. Essa abordagem fornece as ferramentas mínimas necessárias para estabelecer uma governança consistente para que a equipe possa entender as ferramentas. Em seguida, ela se expande quanto a essas ferramentas para resolver preocupações de governança comuns.

**Plantas de conformidade ISO 27001:** Para clientes que precisam aderir aos padrões de conformidade ISO, os exemplos de [plantas de serviços compartilhados iso 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-shared/index) podem servir como um MVP mais eficaz para produzir restrições de governança mais avançadas no processo iterativo anteriormente. O [exemplo de Ambiente do Serviço de Aplicativo/Banco de Dados SQL para ISO 27001](https://docs.microsoft.com/azure/governance/blueprints/samples/iso27001-ase-sql-workload) expande o blueprint para mapear controles e implantar uma arquitetura comum para um ambiente de aplicativo. Conforme blueprints de conformidade adicionais forem lançados, eles também serão referenciados aqui.

**Datacenter virtual:** Um ponto de partida de governança mais robusto pode ser necessário. Nesses casos, considere usar o [VDC (Datacenter Virtual do Azure)](../../reference/vdc.md). Essa abordagem é sugerida normalmente durante os esforços de adoção de escala empresarial, especialmente naqueles que ultrapassam dez mil ativos. É também a escolha concreta para cenários complexos de governança quando qualquer um dos itens a seguir é necessário: requisitos abrangentes de conformidade de terceiros, conhecimento profundo de domínio ou paridade com políticas de controle de TI e requisitos de conformidade.

### <a name="partnership-option-to-complete-prerequisites"></a>Opção de parceria para concluir os pré-requisitos

**Serviços da Microsoft:** Os serviços da Microsoft fornecem ofertas de soluções que podem se alinhar ao modelo de governança da estrutura de adoção da nuvem, plantas de conformidade ou opções de datacenter virtual para garantir o modelo de governança ou conformidade mais apropriado. Use a oferta da solução [SCI (Secure Cloud Insights)](https://download.microsoft.com/download/C/7/C/C7CEA89D-7BDB-4E08-B998-737C13107361/Secure_Cloud_Insights_Datasheet_EN_US.pdf) para estabelecer uma imagem orientada por dados de uma implantação do cliente no Azure e validar a maturidade da implementação do cliente enquanto identifica a otimização de arquiteturas de implantação existentes e remove riscos de disponibilidade e de segurança de governança. Com base em insights do cliente, você deve conduzir com as seguintes abordagens:

- **Base da nuvem:** Estabeleça os principais designs, padrões e arquitetura de governança do Azure do cliente com a oferta de solução de [HCF (híbrido Cloud Foundation)](https://download.microsoft.com/download/D/8/7/D872DFD0-1C46-4145-95E4-B5EAB2958B96/Hybrid_Cloud_Foundation_Datasheet_EN_US.pdf) . Mapeie os requisitos do cliente para a arquitetura de referência mais apropriada. Implemente um produto viável mínimo composto por serviços compartilhados e cargas de trabalho de IaaS.
- **Modernização de nuvem:** Use a oferta de solução de [modernização de nuvem](https://download.microsoft.com/download/3/7/3/373F90E3-8568-44F3-B096-CD9C1CD28AB7/Cloud_Modernization_Datasheet_EN_US.pdf) como uma abordagem abrangente para mover aplicativos, dados e infraestrutura para uma nuvem pronta para a empresa, bem como para otimizar e modernizar após a implantação na nuvem.
- **Inovar com nuvem:** Envolva clientes por meio de uma abordagem inovadora e exclusiva [de solução de CCOE (Cloud Center of Excellence)](https://download.microsoft.com/download/F/8/B/F8BBE4BD-E5F8-4DFB-82F7-C0A4E17051BB/Cloud_Center_of_Excellence_Datasheet_EN_US.pdf) que cria uma organização de ti moderna para permitir a agilidade em escala com o DevOps enquanto permanece no controle. Implemente uma abordagem ágil para capturar requisitos de negócios, reutilizar pacotes de implantação alinhados com políticas de segurança, conformidade e gerenciamento de serviços e mantenha a plataforma do Azure alinhada com procedimentos operacionais.

## <a name="assess-process-changes"></a>Avaliar alterações no processo

Durante a avaliação, são necessárias decisões adicionais para alinhar-se à abordagem de governança necessária. A equipe de governança da nuvem deve fornecer a todos os membros da equipe de adoção da nuvem todas as declarações de política, diretrizes arquitetônicas ou requisitos de governança/conformidade antes da avaliação de uma carga de trabalho.

### <a name="suggested-action-during-the-assess-process"></a>Ação sugerida durante o processo de avaliação

Os requisitos de avaliação de governança e conformidade são muito específicos do cliente para que possamos fornecer orientações gerais sobre as etapas reais realizadas durante a avaliação. No entanto, o processo deve incluir tarefas e alocações de tempo para "alinhamento aos requisitos de conformidade/governança". Para ter uma compreensão mais detalhada desses requisitos, confira os links a seguir:

Para ter uma compreensão mais profunda da governança, examine as [Cinco disciplinas da governança de nuvem](../../govern/governance-disciplines.md). Esta seção da Cloud Adoption Framework também inclui modelos para documentar as políticas, as diretrizes e os requisitos de cada uma das cinco seções:

- [Gerenciamento de Custos](../../govern/cost-management/template.md)
- [Linha de Base de Segurança](../../govern/security-baseline/template.md)
- [Consistência de recursos].. /.. /govern/resource-consistency/template.md)
- [Linha de base de identidade].. /.. /govern/identity-baseline/template.md)
- [Aceleração de Implantação](../../govern/deployment-acceleration/template.md)

Para obter orientações de como desenvolver diretrizes de governança com base no modelo de governança da Estrutura de Adoção da Nuvem, confira [Implementando uma estratégia de governança de nuvem](../../govern/corporate-policy.md).

## <a name="optimize-and-promote-process-changes"></a>Otimizar e promover alterações no processo

Durante os processos de otimização e promoção, a equipe de governança de nuvem shluld investir tempo para testar e validar a adesão aos padrões de governança e de conformidade. Além disso, essa etapa é um bom momento para injetar processos para a equipe de governança da nuvem organizar modelos que podem fornecer [aceleração de implantação](../../govern/deployment-acceleration/index.md) adicional para projetos futuros.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Ação sugerida durante o processo de otimização e promoção

Durante esse processo, o plano de projeto deve incluir alocações de tempo para que a equipe de governança de nuvem execute uma análise de conformidade para cada carga de trabalho planejada para promoção de produção.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Como o item final na [lista de verificação de escopo expandido](./index.md), retorne à lista de verificação e reavalie os requisitos de escopo adicionais para o esforço de migração.

> [!div class="nextstepaction"]
> [Lista de verificação de escopo expandido](./index.md)
