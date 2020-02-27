---
title: Definir política corporativa de governança de nuvem
description: Use a estrutura de adoção de nuvem para o Azure para aprender a estabelecer a política que aborda riscos conhecidos e tolerâncias de risco durante sua jornada de transformação na nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: 94e49d8f6682d4f5edb6b1d00bd93d47ba600bc8
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706669"
---
# <a name="define-corporate-policy-for-cloud-governance"></a>Definir política corporativa para governança de nuvem

Depois de analisar os riscos conhecidos e as tolerâncias de risco relacionadas para a jornada de transformação em nuvem de sua organização, a próxima etapa é estabelecer uma política que resolverá esses riscos explicitamente e definir as etapas necessárias para corrigi-los sempre que possível.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-corporate-it-policy-become-cloud-ready"></a>Como a política de TI corporativa pode se tornar pronta para a nuvem?

No controle tradicional e governança incremental, a política corporativa cria a definição de trabalho de governança. A maioria das ações de governança de TI busca implementar a tecnologia para monitorar, impor, operar e automatizar essas políticas corporativas. A governança de nuvem é criada em conceitos semelhantes.

![Governança corporativa e disciplinas de governança](../../_images/operational-transformation-govern-highres.png)

*Figura 1 – governança corporativa e disciplinas de governança.*

A imagem acima ilustra a relação entre riscos de negócios, políticas e conformidade, além de mecanismos de monitoramento e imposição que precisarão interagir como parte da sua estratégia de governança. As cinco disciplinas de governança de nuvem permitem que você gerencie essas interações e perceba sua estratégia.

A governança de nuvem é o produto de um esforço de adoção contínua ao longo do tempo, como uma transformação verdadeira contínua que não acontece da noite para o dia. A tentativa de entregar a governança de nuvem completa antes de abordar as alterações de política corporativa de chave usando um método rápido agressivo raramente produz os resultados desejados. Em vez disso, é recomendável uma abordagem incremental.

O que é diferente em relação a uma estrutura de adoção de nuvem é o ciclo de compra e pode habilitar a transformação autêntica. Como não há um grande requisito de aquisição de despesas de capital, os engenheiros podem começar a experimentação e a adoção mais cedo. Em culturas mais corporativas, eliminar a barreira de despesa de capital para a adoção pode levar a loops de comentários mais rigorosos, crescimento orgânico e execução incremental.

A mudança para a adoção da nuvem exige uma mudança na governança. Em muitas organizações, a transformação de política corporativa permite governança aprimorada e taxas mais altas de conformidade por meio de alterações incrementais de política e a aplicação automática dessas alterações, alimentado por recursos definidos recentemente que você configurar com seu provedor de serviços de nuvem.

<!-- markdownlint-enable MD026 -->

## <a name="review-existing-policies"></a>Revisão das políticas existentes

Como a governança é um processo contínuo, a política deve ser analisada regularmente com a equipe de ti e os participantes para garantir que os recursos hospedados na nuvem continuem a manter a conformidade com os requisitos e as metas corporativas gerais. A compreensão dos novos riscos e a tolerância aceitável pode impulsionar uma [revisão de políticas existentes](./cloud-policy-review.md) para determinar o nível necessário de governança que apropriado para sua organização.

> [!TIP]
> Se sua organização usa fornecedores ou outros parceiros de negócios confiáveis, um dos maiores riscos de negócios a considerar pode ser uma falta de adesão à [conformidade regulatória](./regulatory-compliance.md) por essas organizações externas. Esse risco geralmente não pode ser corrigido e, em vez disso, pode exigir uma rigorosa adesão aos requisitos por todas as partes. Verifique se você identificou e entendeu os requisitos de conformidade de terceiros antes de iniciar uma revisão de política.

## <a name="create-cloud-policy-statements"></a>Criar instruções de política de nuvem

As políticas de TI baseadas em nuvem estabelecem requisitos, padrões e objetivos que sua equipe de TI e os sistemas automatizados precisarão dar suporte. Decisões de política são o fator principal de seu [design de arquitetura de nuvem](./governance-alignment.md) e como você irá implementar seus [processos de conformidade de política](./processes.md).

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Embora essas políticas possam ser integradas em sua documentação de política corporativa mais ampla, as instruções de política de nuvem discutidas em todas as diretrizes da estrutura de adoção de nuvem tendem a ser um resumo mais conciso dos riscos e planos para lidar com elas. Cada definição deve incluir essas duas informações:

- **Risco para os negócios:** Um resumo do risco que essa política abordará.
- **Declaração de política:** Uma explicação concisa dos requisitos e das metas da política.
- **Design ou orientação técnica:** Recomendações, especificações ou outras diretrizes acionáveis para dar suporte e impor essa política que as equipes de ti e os desenvolvedores podem usar ao projetar e criar suas implantações na nuvem.

Se você precisar de ajuda para iniciar as políticas de definição, consulte as [disciplinas de governança](../governance-disciplines.md) apresentadas na visão geral de seção de governança. Os artigos para cada uma dessas disciplinas incluem exemplos de riscos comerciais comuns encontrados ao migrar para a nuvem e amostras de políticas usadas para corrigir esses riscos (por exemplo, consulte as definições de política de [exemplo](../cost-management/policy-statements.md)da disciplina de gerenciamento de custos).

## <a name="incremental-governance-and-integrating-with-existing-policy"></a>Governança incremental e integração com a política existente

Adições planejadas para o seu ambiente de nuvem sempre devem ser verificadas quanto à conformidade com a política existente e política atualizada para a conta para qualquer problema não abordado. Realize também a [revisão regular da política de nuvem](./cloud-policy-review.md) para garantir que sua nuvem política esteja atualizada e em sincronia com qualquer nova política corporativa.

A necessidade de integrar a política de nuvem às suas políticas de TI herdadas, depende em grande parte da maturidade dos processos de governança de nuvem e do tamanho do seu acervo de nuvem. Consulte o artigo sobre [governança incremental e política de MVP](./index.md) para uma discussão mais ampla sobre como lidar com a integração de política durante sua transformação de nuvem.

## <a name="next-steps"></a>Próximas etapas

Depois de definir suas políticas, faça um rascunho de um guia de design de arquitetura para fornecer a equipe de TI e desenvolvedores de diretrizes de ações.

> [!div class="nextstepaction"]
> [Alinhar seu guia de design de governança com a política corporativa](./governance-alignment.md)
