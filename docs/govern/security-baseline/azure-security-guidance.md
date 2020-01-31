---
title: Diretrizes de segurança do Azure
description: Quais diretrizes de segurança a Microsoft fornece?
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: cc57de575b7ad208748595a82b9726ebf85fa3fd
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76804904"
---
<!-- markdownlint-disable MD026 -->

# <a name="microsoft-security-guidance"></a>Diretrizes de segurança da Microsoft

## <a name="tools"></a>Ferramentas

A Microsoft introduziu a [Plataforma de Confiança do Serviço](https://servicetrust.microsoft.com) e o Gerenciador de Conformidade para ajudar a:

- Superar os desafios de gerenciamento de conformidade.
- Atender às responsabilidades de atender aos requisitos regulatórios.
- Realize auditorias de autoatendimento e avaliações de risco da utilização do serviço de nuvem empresarial.

Essas ferramentas são projetadas para auxiliar as organizações a cumprirem as obrigações de conformidade complexas e melhorarem os recursos de proteção de dados ao escolherem utilizar os serviços do Microsoft Cloud.

A **STP (Plataforma de Confiança do Serviço)** fornece informações detalhadas e ferramentas para ajudar a atender às necessidades de uso dos serviços do Microsoft Cloud, incluindo Azure, Office 365, Dynamics 365 e Windows. A STP é uma solução completa para informações de segurança, regulamentação, conformidade e privacidade relacionadas ao Microsoft Cloud. É onde publicamos as informações e os recursos necessários para realizar avaliações de risco de autoatendimento de serviços de nuvem e ferramentas. A STP foi criada para ajudar a acompanhar as atividades de conformidade regulatória no Azure, incluindo:

- **Gerente de conformidade:** O Compliance Manager, uma ferramenta de avaliação de riscos baseada em fluxo de trabalho na plataforma de confiança de serviços da Microsoft, permite que você controle, atribua e verifique as atividades de conformidade regulatória de sua organização relacionadas a serviços de Microsoft Cloud, como o Office 365, o Dynamics 365 e o Azure. Você pode encontrar mais detalhes na próxima seção.
- **Documentos de confiança:** Atualmente, há três categorias de guias que fornecem recursos abundantes para avaliar Microsoft Cloud; Saiba mais sobre as operações da Microsoft em segurança, conformidade e privacidade; e ajudar você a agir em aprimorar seus recursos de proteção de dados. Estão incluídas:
- **Relatórios de auditoria:** Os relatórios de auditoria permitem que você se mantenha atualizado sobre as informações mais recentes relacionadas à privacidade, segurança e conformidade para serviços de Microsoft Cloud. Isso inclui ISO, SOC, FedRAMP e outros relatórios de auditoria, notificações de avaliação e materiais relacionados a auditorias independentes de terceiros dos serviços do Microsoft Cloud como Azure, Office 365, Dynamics 365, e outros.
- **Guias de proteção de dados:** Os guias de proteção de dados fornecem informações sobre como Microsoft Cloud serviços protegem seus dados e como você pode gerenciar a segurança de dados de nuvem e a conformidade para sua organização. Isso inclui white papers aprofundados que fornecem detalhes sobre como a Microsoft desenvolve e opera serviços de nuvem, perguntas frequentes, relatórios de avaliações de segurança de fim de ano, resultados de testes de penetração e diretrizes para ajudá-lo a realizar avaliações de risco e aprimorar os recursos de proteção de dados.
- **Plano de segurança e conformidade do Azure:** Os planos gráficos fornecem recursos para ajudá-lo na criação e inicialização de aplicativos capacitados para a nuvem que o ajudarão a cumprir regulamentações e padrões rígidos. Com mais certificações do que qualquer outro provedor de nuvem, você pode confiar na implantação das cargas de trabalho críticas no Azure com blueprints, que incluem:
  - Visão geral e diretrizes específicas do setor.
  - Matriz de responsabilidades do cliente.
  - Arquiteturas de referência com modelos de ameaça.
  - Matrizes de implementação de controle.
  - Automação para implantar arquiteturas de referência.
  - Recursos de privacidade: a documentação para avaliações de impacto de proteção de dados, DSRs (solicitações de entidade de dados) e notificação de violação de dados é fornecida para incorporar seu próprio programa de responsabilidade ao suporte do Regulamento Geral sobre a Proteção de Dados (GDPR).
- **Introdução ao GDPR:** Os produtos e serviços da Microsoft ajudam as organizações a atender aos requisitos de GDPR ao coletar ou processar dados pessoais. A STP foi projetada para fornecer informações sobre os recursos dos serviços da Microsoft que podem ser utilizados para atender aos requisitos específicos de RGPD. A documentação pode ajudá-lo na responsabilidade de GDPR e a reconhecer medidas técnicas e organizacionais. Documentação para Avaliações de Impacto da Proteção de Dados, DSRs (Solicitações do Titular dos Dados) e Notificação de Violação de Dados são fornecidos para incorporar ao seu próprio programa de responsabilidade em suporte ao RGPD.
  - **Solicitações de entidade de dados:** O GDPR concede a indivíduos (ou entidades de dados) determinados direitos em conexão com o processamento de seus dados pessoais. Isso inclui o direito de corrigir dados imprecisos, apagar dados ou restringir o processamento, bem como receber dados e atender a uma solicitação para transmitir os dados a outro controlador.
  - **Violação de dados:** O GDPR exige requisitos de notificação para controladores de dados e processadores no caso de uma violação de dados pessoais. A STP fornece informações sobre como a Microsoft tenta evitar violações, como a Microsoft detecta uma violação e como a Microsoft irá responder no caso de uma violação e notificá-lo como um controlador de dados.
  - **Avaliação de impacto da proteção de dados:** A Microsoft ajuda os controladores a concluir as avaliações de impacto da proteção de dados GDPR. O RGPD fornece uma lista abrangente de casos em que DPIAs devem ser realizadas, como processamento automatizado para fins de criação de perfis e atividades semelhantes, processamento em larga escala de categorias especiais de dados pessoais e monitoramento sistemático de uma área de acesso público em larga escala.
  - **Outros recursos:** Além das diretrizes de ferramentas discutidas nas seções acima, o STP também fornece outros recursos, incluindo conformidade regional, recursos adicionais para o centro de segurança e conformidade e perguntas frequentes sobre a plataforma de confiança do serviço, o Compliance Manager e o Privacy/GDPR.
- **Conformidade regional:** O STP fornece vários documentos de conformidade e orientações para o Microsoft serviços online atender aos requisitos de conformidade para diferentes regiões, incluindo República Tcheca, Polônia e Romênia.

## <a name="unique-intelligent-insights"></a>Insights inteligentes exclusivos

Na medida em que o volume e a complexidade dos sinais de segurança aumentam, determinar se esses sinais são ameaças credíveis para, em seguida, agir, demora muito tempo. A Microsoft oferece uma variedade incomparável de inteligência de segurança oferecida em escala de nuvem para ajudar a detectar e corrigir ameaças rapidamente. Para obter mais informações, consulte a [visão geral da central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro).

## <a name="azure-threat-intelligence"></a>Inteligência contra ameaças do Azure

Ao usar a opção Inteligência contra Ameaças disponível na Central de Segurança, os administradores de TI poderão identificar as ameaças à segurança no ambiente. Por exemplo, eles podem identificar se determinado computador faz parte de um botnet. Os computadores podem se tornar nós em um botnet quando os invasores instalam de forma ilícita malware que conecta secretamente o computador ao comando e ao controle. A inteligência contra ameaças também pode identificar possíveis ameaças recebidas de canais de comunicação escondidos, como a dark Web.

Para criar essa inteligência contra ameaças, a Central de Segurança usa dados recebidos de várias fontes da Microsoft. A Central de Segurança usa-os para identificar possíveis ameaças contra o ambiente. O painel Inteligência contra Ameaças é composto de três opções principais:

- Tipos de ameaças detectados
- Origem da ameaça
- Mapa de inteligência contra ameaças

## <a name="machine-learning-in-azure-security-center"></a>Machine Learning na Central de Segurança do Azure

A Central de Segurança do Azure analisa profundamente uma grande variedade de dados de várias soluções da Microsoft e de parceiros para ajudá-lo a obter maior segurança. Para aproveitar esses dados, a empresa usa ciência de dados e aprendizado de máquina para prevenção contra ameaças, detecção e, eventualmente, investigação.

Em geral, o Azure Machine Learning ajuda a alcançar dois resultados:

## <a name="next-generation-detection"></a>Detecção de próxima geração

Os invasores estão cada vez mais automatizados e sofisticados. Eles também usam ciência de dados. Eles fazem engenharia reversa de proteções e desenvolvem sistemas que dão suporte a mutações no comportamento. Eles mascaram as atividades como ruídos e aprendem rapidamente com os erros. O aprendizado de máquina ajuda-nos a responder a esses desenvolvimentos.

## <a name="simplified-security-baseline"></a>Linha de Base de Segurança simplificada

Tomar decisões de segurança eficazes não é fácil. Isso exige experiência e especialização em segurança. Embora algumas organizações de grande porte tenham tais especialistas na equipe, muitas empresas não têm. O Azure Machine Learning permite que os clientes se beneficiem com a sabedoria de outras organizações ao tomar decisões de segurança.

## <a name="behavioral-analytics"></a>Análise comportamental

A análise de comportamento é uma técnica que analisa e compara dados em uma coleção de padrões conhecidos. No entanto, esses padrões não são assinaturas simples. Os padrões são determinados por meio de algoritmos complexos de aprendizado de máquina aplicados a conjuntos de dados massivos. Eles também são determinados pela análise cuidadosa de comportamentos mal-intencionados por analistas especialistas. A Central de Segurança do Azure pode usar a análise de comportamento para identificar recursos comprometidos baseado na análise dos logs de máquina virtual, dos logs de dispositivo de rede virtual, dos logs da malha, dos despejos de memória e de outras fontes.
