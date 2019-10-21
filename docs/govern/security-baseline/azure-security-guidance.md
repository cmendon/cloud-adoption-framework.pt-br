---
title: Diretrizes de segurança do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Quais diretrizes de segurança a Microsoft fornece?
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8449878d46c939c58f690e585aac07fa0e827484
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548052"
---
<!-- markdownlint-disable MD026 -->

# <a name="microsoft-security-guidance"></a>Diretrizes de segurança da Microsoft

## <a name="tools"></a>Ferramentas

A Microsoft introduziu a [plataforma de confiança de serviço](https://servicetrust.microsoft.com) e o gerente de conformidade para ajudar com o seguinte:

- Superar os desafios de gerenciamento de conformidade.
- Atender às responsabilidades de atender aos requisitos regulatórios.
- Realize auditorias de autoatendimento e avaliações de risco da utilização do serviço de nuvem empresarial.

Essas ferramentas foram projetadas para ajudar as organizações a atender às obrigações de conformidade complexas e a melhorar os recursos de proteção de dados ao escolher e usar os serviços Microsoft Clouds.

A **plataforma de confiança de serviço (STP)** fornece informações e ferramentas detalhadas para ajudar a atender às suas necessidades de uso de serviços Microsoft Cloud, incluindo Azure, Office 365, Dynamics 365 e Windows. O STP é uma loja única para informações de segurança, regulamentação, conformidade e privacidade relacionadas à Microsoft Cloud. É aí que publicamos as informações e os recursos necessários para executar avaliações de risco de autoatendimento de serviços e ferramentas de nuvem. O STP foi criado para ajudar a acompanhar as atividades de conformidade regulatória no Azure, incluindo:

- **Gerente de conformidade:** O Compliance Manager, uma ferramenta de avaliação de riscos baseada em fluxo de trabalho na plataforma de confiança de serviços da Microsoft, permite que você controle, atribua e verifique as atividades de conformidade regulatória de sua organização relacionadas a serviços de Microsoft Cloud, como o Office 365, Dynamics 365 e o Azure. Você pode encontrar mais detalhes na próxima seção.
- **Documentos de confiança:** Atualmente, há três categorias de guias que fornecem recursos abundantes para avaliar Microsoft Cloud; Saiba mais sobre as operações da Microsoft em segurança, conformidade e privacidade; e ajudar você a agir em aprimorar seus recursos de proteção de dados. Estão incluídas:
- **Relatórios de auditoria:** Os relatórios de auditoria permitem que você se mantenha atualizado sobre as informações mais recentes relacionadas à privacidade, segurança e conformidade para serviços de Microsoft Cloud. Isso inclui ISO, SOC, FedRAMP e outros relatórios de auditoria, cartas de ponte e materiais relacionados a auditorias de terceiros independentes de serviços de Microsoft Cloud, como o Azure, o Office 365, o Dynamics 365 e outros.
- **Guias de proteção de dados:** Os guias de proteção de dados fornecem informações sobre como Microsoft Cloud serviços protegem seus dados e como você pode gerenciar a segurança de dados de nuvem e a conformidade para sua organização. Isso inclui White papers aprofundados que fornecem detalhes sobre como a Microsoft projeta e opera serviços de nuvem, perguntas frequentes, relatórios de avaliações de segurança de fim do ano, resultados de teste de penetração e orientação para ajudá-lo a realizar a avaliação de riscos e melhorar seus dados recursos de proteção.
- **Plano de segurança e conformidade do Azure:** Os planos gráficos fornecem recursos para ajudá-lo na criação e inicialização de aplicativos capacitados para a nuvem que o ajudarão a cumprir regulamentações e padrões rígidos. Com mais certificações do que qualquer outro provedor de nuvem, você pode ter confiança para implantar suas cargas de trabalho críticas no Azure, com plantas que incluem:
  - Visão geral e diretrizes específicas do setor.
  - Matriz de responsabilidades do cliente.
  - Arquiteturas de referência com modelos de ameaça.
  - Matrizes de implementação de controle.
  - Automação para implantar arquiteturas de referência.
  - Recursos de privacidade: a documentação para avaliações de impacto de proteção de dados, DSRs (solicitações de entidade de dados) e notificação de violação de dados é fornecida para incorporar seu próprio programa de responsabilidade ao suporte do Regulamento Geral sobre a Proteção de Dados (GDPR).
- **Introdução ao GDPR:** Os produtos e serviços da Microsoft ajudam as organizações a atender aos requisitos de GDPR ao coletar ou processar dados pessoais. O STP foi projetado para fornecer informações sobre os recursos dos serviços da Microsoft que você pode usar para atender a requisitos específicos do GDPR. A documentação pode ajudar sua responsabilidade GDPR e sua compreensão de medidas técnicas e organizacionais. A documentação para avaliações de impacto de proteção de dados, DSRs (solicitações de entidade de dados) e notificação de violação de dados é fornecida para incorporar a seu próprio programa de responsabilidade o suporte do GDPR.
  - **Solicitações de entidade de dados:** O GDPR concede a indivíduos (ou entidades de dados) determinados direitos em conexão com o processamento de seus dados pessoais. Isso inclui o direito de corrigir dados imprecisos, apagar dados ou restringir seu processamento, bem como receber seus dados e atender a uma solicitação para transmitir seus dados para outro controlador.
  - **Violação de dados:** O GDPR exige requisitos de notificação para controladores de dados e processadores no caso de uma violação de dados pessoais. O STP fornece informações sobre como a Microsoft tenta evitar violações em primeiro lugar, como a Microsoft detecta uma violação e como a Microsoft responderá no caso de uma violação e o notificará como um controlador de dados.
  - **Avaliação de impacto da proteção de dados:** A Microsoft ajuda os controladores a concluir as avaliações de impacto da proteção de dados GDPR. O GDPR fornece uma lista completa de casos em que o DPIAs deve ser executado, como o processamento automatizado para fins de criação de perfil e atividades semelhantes; processamento em uma grande escala de categorias especiais de dados pessoais e monitoramento sistemático de uma área publicamente acessível em grande escala.
  - **Outros recursos:** Além das diretrizes de ferramentas discutidas nas seções acima, o STP também fornece outros recursos, incluindo conformidade regional, recursos adicionais para o centro de segurança e conformidade e perguntas frequentes sobre a plataforma de confiança de serviço, Compliance Manager e Privacy/GDPR.
- **Conformidade regional:** O STP fornece vários documentos de conformidade e orientações para o Microsoft serviços online atender aos requisitos de conformidade para diferentes regiões, incluindo República Tcheca, Polônia e Romênia.

## <a name="unique-intelligent-insights"></a>Insights inteligentes exclusivos

À medida que o volume e a complexidade dos sinais de segurança crescem, determinar se esses sinais são ameaças confiáveis e, em seguida, agir, leva muito tempo. A Microsoft oferece uma amplitude incomparável de inteligência de segurança fornecida em escala de nuvem para ajudar a detectar e corrigir rapidamente as ameaças. [Leia mais](https://docs.microsoft.com/azure/security-center/security-center-intro)

## <a name="azure-threat-intelligence"></a>Inteligência contra ameaças do Azure

Usando a opção inteligência contra ameaças disponível na central de segurança, os administradores de ti podem identificar as ameaças à segurança em relação ao ambiente. Por exemplo, eles podem identificar se um computador específico faz parte de um botnet. Os computadores podem se tornar nós em uma botnet quando os invasores instalam de forma ilícita o malware que conecta secretamente o computador ao comando e ao controle. A inteligência contra ameaças também pode identificar possíveis ameaças provenientes de canais de comunicação Underground, como a Web escura.

Para criar essa inteligência contra ameaças, a central de segurança usa dados provenientes de várias fontes na Microsoft. A central de segurança usa isso para identificar possíveis ameaças em relação ao seu ambiente. O painel inteligência contra ameaças é composto de três opções principais:

- Tipos de ameaças detectados
- Origem da ameaça
- Mapa de inteligência contra ameaças

## <a name="machine-learning-in-azure-security-center"></a>Machine Learning na central de segurança do Azure

A central de segurança do Azure analisa profundamente uma infinidade de dados de uma variedade de soluções de parceiros e da Microsoft para ajudá-lo a obter maior segurança. Para aproveitar esses dados, a empresa usa ciência de dados e aprendizado de máquina para prevenção de ameaças, detecção e, eventualmente, investigação.

Em grande escala, Azure Machine Learning ajuda a alcançar dois resultados:

## <a name="next-generation-detection"></a>Detecção de próxima geração

Os invasores são cada vez mais automatizados e sofisticados. Eles usam a ciência de dados também. Eles protegem a engenharia reversa e criam sistemas que dão suporte a mutações em comportamento. Eles disfarçam suas atividades como ruído e aprendem rapidamente contra erros. O aprendizado de máquina nos ajuda a responder a esses desenvolvimentos.

## <a name="simplified-security-baseline"></a>Linha de base de segurança simplificada

Tomar decisões de segurança efetivas não é fácil. Ele requer experiência de segurança e experiência. Embora algumas organizações de grande porte tenham tais especialistas na equipe, muitas empresas não têm. Azure Machine Learning permite que os clientes se beneficiem da sabedoria de outras organizações ao tomar decisões de segurança.

## <a name="behavioral-analytics"></a>Análise comportamental

A análise comportamental é uma técnica que analisa e compara dados a uma coleção de padrões conhecidos. No entanto, esses padrões não são assinaturas simples. Eles são determinados por meio de algoritmos de aprendizado de máquina complexos que são aplicados a grandes conjuntos de dados. Eles também são determinados por meio de uma análise cuidadosa de comportamentos mal-intencionados por analistas especialistas. A central de segurança do Azure pode usar a análise comportamental para identificar recursos comprometidos com base na análise de logs de máquina virtual, logs de dispositivo de rede virtual, logs de malha, despejos de memória e outras fontes.
