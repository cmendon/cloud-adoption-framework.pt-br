---
title: Política de linha de base de segurança nativa de nuvem
description: Veja um exemplo de política nativa de nuvem para a disciplina de linha de base de segurança, na qual as ferramentas e plataformas do Azure são suficientes para gerenciar riscos de negócios.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ce5b1a77396479b2621afab5cac025b983f14469
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223747"
---
# <a name="cloud-native-security-baseline-policy"></a>Política de linha de base de segurança nativa de nuvem

A [Linha de Base de Segurança](./index.md) é uma das [Cinco Disciplinas de Governança de Nuvem](../governance-disciplines.md). Essa disciplina se concentra em tópicos gerais de segurança, incluindo a proteção da rede, ativos digitais, dados etc. Conforme descrito no [Guia de revisão de política](../policy-compliance/cloud-policy-review.md), a estrutura de adoção de nuvem inclui três níveis de política de exemplo: a nuvem nativa, a empresa e a conformidade com o princípio de design de nuvem para cada uma das disciplinas. Este artigo discute a política de exemplo nativa de nuvem para a disciplina de linha de base de segurança.

> [!NOTE]
> A Microsoft não está em nenhuma posição de ditar política corporativa ou de TI. Este artigo ajudará você a se preparar para uma revisão de política interna. Supomos que essa política de exemplo será estendida, validada e testada com a sua política corporativa antes de usá-la. Qualquer uso dessa política de exemplo como está desencorajado.

## <a name="policy-alignment"></a>Alinhamento de políticas

Esta política de exemplo sintetiza um cenário de nuvem nativa, o que significa que as ferramentas e plataformas fornecidas pelo Azure são suficientes para gerenciar os riscos de negócios envolvidos em uma implantação. Nesse cenário, supõe-se que uma configuração simples dos serviços padrão do Azure forneçam proteção suficiente do ativo.

## <a name="cloud-security-and-compliance"></a>Segurança e conformidade de nuvem

A segurança é integrada em cada aspecto do Azure, oferecendo vantagens de segurança exclusivas derivadas da inteligência de segurança global, controles sofisticados voltados para o cliente e infraestrutura de proteção segura. Essa poderosa combinação ajuda a proteger seus aplicativos e dados, dar suporte a seus esforços de conformidade e fornecer segurança econômica para organizações de todos os tamanhos. Essa abordagem cria uma forte posição inicial para qualquer política de segurança, mas não nega a necessidade de práticas de segurança igualmente fortes relacionadas aos serviços de segurança sendo usados.

### <a name="built-in-security-controls"></a>Controles de segurança interna

É difícil manter uma infra-estrutura de segurança forte quando os controles de segurança não são intuitivos e precisam ser configurados separadamente. O Azure inclui controles de segurança integrados em uma variedade de serviços que ajudam você a proteger os dados e cargas de trabalho rapidamente e a gerenciar risco entre ambientes híbridos. Soluções integradas de parceiros também permitem fazer uma transição fácil das proteções existentes para a nuvem.

### <a name="cloud-native-identity-policies"></a>Políticas de identidade nativa de nuvem

A identidade está se tornando o novo plano de controle de limite para segurança, assumindo a função antes exercida pela perspectiva centrada em rede tradicional. Os perímetros de rede se tornaram cada vez mais porosos e a defesa do perímetro não pode ser tão eficiente quanto antes do advento do BYOD (Traga seu próprio dispositivo) e de aplicativos de nuvem. O gerenciamento de identidade do Azure e o controle de acesso permitem acesso contínuo e seguro a todos os seus aplicativos.

Um exemplo de política nativa de nuvem para identidade em diretórios locais e de nuvem, pode incluir requisitos como o seguinte:

- Acesso autorizado a recursos com RBAC (controle de acesso baseado em função), autenticação multifator e SSO (logon único).
- Mitigação rápida de identidades de usuário suspeita de comprometimento.
- JIT (just-in-time), acesso apenas suficiente concedido em uma base tarefa por tarefa para limitar a exposição de credenciais de administrador com privilégios elevados.
- Identidade estendida de usuário e acesso a políticas em vários ambientes por meio de Azure Active Directory.

Embora seja importante entender a [Linha de Base de Identidade](../identity-baseline/index.md) no contexto de linha de base de segurança, as [Cinco disciplinas de governança de nuvem](../index.md) chamam a [Linha de base de identidade](../identity-baseline/index.md) como sua própria disciplina, separada da Linha de base de segurança.

### <a name="network-access-policies"></a>Políticas de acesso de rede

O controle de rede inclui configuração, gerenciamento e proteção dos elementos de rede como redes virtuais, balanceamento de carga, DNS e gateways. Os controles fornecem um meio para os serviços se comunicarem e interoperarem. O Azure inclui uma infraestrutura de rede robusta e segura para dar suporte a seus requisitos de conectividade de aplicativo e de serviço. A conectividade de rede é possível entre os recursos localizados no Azure, entre os recursos locais e aqueles hospedados no Azure e de origem e destino à Internet e ao Azure.

Uma política nativa de nuvem para controles de rede pode incluir requisitos como o seguinte:

- Conexões híbridas para recursos locais podem não ser permitidas em uma política nativa de nuvem. Se uma conexão híbrida se provar necessária, um exemplo de política de segurança corporativa mais robusto seria uma referência mais relevante.
- Os usuários podem estabelecer conexões seguras para e dentro do Azure usando redes virtuais e grupos de segurança de rede.
- O Firewall do Azure protege os hosts do tráfego de rede mal-intencionados por acesso à porta limitado. Um bom exemplo dessa política é um requisito para bloquear (ou não habilitar) o tráfego diretamente para uma VM por SSH/RDP.
- Serviços como o WAF (firewall do aplicativo Web) do gateway Aplicativo Azure e a proteção contra DDoS do Azure protegem aplicativos e garantem a disponibilidade para máquinas virtuais em execução no Azure. Esses recursos não devem ser desabilitados.

### <a name="data-protection"></a>Proteção de dados

Uma das chaves de proteção de dados na nuvem é responsável por possíveis estados em que os dados podem ocorrer e quais controles estão disponíveis para esse estado. Em relação às práticas recomendadas de segurança de dados e criptografia do Azure, as recomendações se concentrarão nos estados de dados a seguir:

- Controles de criptografia de dados são criados nos serviços integrados de máquinas virtuais para armazenamento e banco de Dados SQL.
- Como os dados se movem entre nuvens e clientes, isso pode ser protegido usando protocolos de criptografia padrão do setor.
- Azure Key Vault permite que os usuários protejam e controlem chaves criptográficas, senhas, cadeias de conexão e certificados usados por aplicativos e serviços de nuvem.
- A proteção de informações do Azure ajudará a classificar, rotular e proteger seus dados confidenciais em aplicativos.

Embora esses recursos sejam criados no Azure, cada um dos itens acima requer configuração e pode aumentar os custos. O alinhamento de cada recurso nativo de nuvem com uma [estratégia de classificação de dados](../policy-compliance/data-classification.md) é altamente sugerido.

### <a name="security-monitoring"></a>Monitoramento de segurança

O monitoramento de segurança é uma estratégia proativa que audita os recursos para identificar sistemas que não seguem os padrões ou as melhores práticas organizacionais. A Central de Segurança do Azure fornece um gerenciamento de segurança unificado e proteção avançada contra ameaças nas cargas de trabalho de nuvem híbrida. Com a Central de Segurança, é possível aplicar políticas de segurança em suas cargas de trabalho, limitar a exposição a ameaças e detectar e responder a ataques, incluindo:

- Exibição unificada de segurança em todas as cargas de trabalho locais e na nuvem com a central de segurança do Azure.
- Monitoramento contínuo e avaliações de segurança para garantir a conformidade e corrigir quaisquer vulnerabilidades.
- Ferramentas interativas e inteligência de ameaças contextuais para investigação simplificada.
- Log extensivo e integração com as informações de segurança existentes.
- Reduz a necessidade de soluções de segurança caras e não integradas.

### <a name="extending-cloud-native-policies"></a>Estendendo políticas nativas de nuvem

Usar a nuvem pode reduzir essa carga de segurança. A Microsoft fornece a segurança física para datacenters do Azure e ajuda a proteger a plataforma de nuvem contra ameaças de infraestrutura como um ataque de DDoS. Considerando que a Microsoft tem milhares de especialistas em segurança cibernética trabalhando na segurança todos os dias, os recursos para detectar, impedir ou mitigar os ataques cibernéticos são consideráveis. Na verdade, embora as organizações tenham usado a preocupação se a nuvem fosse segura, a maioria agora entende que o nível de investimento em pessoas e infraestruturas especializadas feitas por fornecedores como a Microsoft torna a nuvem mais segura do que a maioria dos data centers locais.
Usar a nuvem pode reduzir essa carga de segurança. A Microsoft fornece a segurança física para datacenters do Azure e ajuda a proteger a plataforma de nuvem contra ameaças de infraestrutura como um ataque de DDoS. Considerando que a Microsoft tem milhares de especialistas em segurança cibernética trabalhando na segurança todos os dias, os recursos para detectar, impedir ou mitigar os ataques cibernéticos são consideráveis. Na verdade, embora as organizações tenham usado a preocupação se a nuvem fosse segura, a maioria agora entende que o nível de investimento em pessoas e infraestruturas especializadas feitas por fornecedores como a Microsoft torna a nuvem mais segura do que a maioria dos data centers locais.

Mesmo com esse investimento em uma linha de base de segurança nativa de nuvem, é recomendável que qualquer diretiva de linha de base de segurança estenda as políticas nativas de nuvem padrão. Veja a seguir exemplos de políticas estendidas que devem ser consideradas, mesmo em um ambiente nativo de nuvem:

- **VMs seguras.** A segurança deve ser a prioridade mais alta de cada organização e fazê-lo com eficiência requer várias coisas. Você deve avaliar o estado da segurança, proteger contra ameaças à segurança e, em seguida, detectar e responder rapidamente às ameaças que ocorrem.
- **Proteger o conteúdo da VM.** Configurar os backups automatizados regulares é essencial para proteger contra erros do usuário. No entanto, isso não é suficiente; Você também deve certificar-se de que os backups estão protegidos do ataques cibernéticos e estão disponíveis quando você precisar deles.
- **Monitorar aplicativos.** Esse padrão abrange várias tarefas, incluindo obter informações sobre a integridade de suas VMs, interações de compreensão entre eles e o estabelecimento de maneiras de monitorar os aplicativos que executam essas VMs. Todas essas tarefas são essenciais em manter seus aplicativos em execução o tempo todo.
- **Acesso de dados seguro e de auditoria.** As organizações devem auditar todos os acessos a dados e usar recursos avançados de aprendizado de máquina para chamar desvios de padrões de acesso normais.
- **Prática de failover.** As operações de nuvem que têm tolerâncias baixas para a falha devem ser capazes de fazer failover ou recuperação de um incidente de segurança cibernética ou plataforma. Esses procedimentos não devem ser simplesmente documentados, mas devem ser praticado trimestralmente.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Agora que você analisou a política de linha de base de segurança de exemplo para soluções nativas de nuvem, retorne ao [Guia de revisão de política](../policy-compliance/cloud-policy-review.md) para começar a criar esse exemplo para criação de suas próprias políticas para adoção de nuvem.

> [!div class="nextstepaction"]
> [Crie suas próprias políticas usando o guia de revisão de política](../policy-compliance/cloud-policy-review.md)
