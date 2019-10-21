---
title: Política de linha de base de segurança nativa de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Política de linha de base de segurança nativa de nuvem
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 037cfa2a10ecce9bc56d747eb658824014758827
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548027"
---
# <a name="cloud-native-security-baseline-policy"></a>Política de linha de base de segurança nativa de nuvem

A [linha de base de segurança](./index.md) é uma das [cinco disciplinas de governança de nuvem](../governance-disciplines.md). Essa disciplina se concentra em tópicos gerais de segurança, incluindo a proteção da rede, ativos digitais, dados etc. Conforme descrito no [Guia de revisão de política](../policy-compliance/cloud-policy-review.md), a estrutura de adoção de nuvem inclui três níveis de política de **exemplo**: a nuvem nativa, a empresa e o princípio de design de nuvem em conformidade com cada uma das disciplinas. Este artigo discute a política de exemplo nativa de nuvem para a disciplina de linha de base de segurança.

> [!NOTE]
> A Microsoft não está em nenhuma posição para ditar a política corporativa ou de ti. Este artigo ajudará você a se preparar para uma revisão de política interna. Supõe-se que essa política de exemplo será estendida, validada e testada em sua política corporativa antes de tentar usá-la. Qualquer uso dessa política de exemplo como está desencorajado.

## <a name="policy-alignment"></a>Alinhamento da política

Esta política de exemplo sintetiza um cenário de nuvem nativa, o que significa que as ferramentas e plataformas fornecidas pelo Azure são suficientes para gerenciar os riscos de negócios envolvidos em uma implantação. Nesse cenário, supõe-se que uma configuração simples dos serviços padrão do Azure fornece proteção de ativos suficiente.

## <a name="cloud-security-and-compliance"></a>Segurança e conformidade de nuvem

A segurança é integrada a todos os aspectos do Azure, oferecendo vantagens de segurança exclusivas derivadas da inteligência de segurança global, de controles sofisticados voltados para o cliente e de uma infraestrutura segura e protegida. Essa poderosa combinação ajuda a proteger seus aplicativos e dados, dar suporte a seus esforços de conformidade e fornecer segurança econômica para organizações de todos os tamanhos. Essa abordagem cria uma posição de início forte para qualquer política de segurança, mas não nega a necessidade de práticas de segurança igualmente fortes relacionadas aos serviços de segurança que estão sendo usados.

### <a name="built-in-security-controls"></a>Controles de segurança internos

É difícil manter uma infra-estrutura de segurança forte quando os controles de segurança não são intuitivos e precisam ser configurados separadamente. O Azure inclui controles de segurança internos em uma variedade de serviços que ajudam a proteger dados e cargas de trabalho rapidamente e a gerenciar riscos em ambientes híbridos. As soluções de parceiros integradas também permitem que você migre facilmente as proteções existentes para a nuvem.

### <a name="cloud-native-identity-policies"></a>Políticas de identidade nativa de nuvem

A identidade está se tornando o novo plano de controle de limite para segurança, assumindo essa função da perspectiva centrada na rede tradicional. Os perímetros de rede se tornaram cada vez mais porosos e a defesa do perímetro não pode ser tão eficiente quanto antes do advento do BYOD (Traga seu próprio dispositivo) e de aplicativos de nuvem. O gerenciamento de identidades e o controle de acesso do Azure permitem acesso contínuo e seguro a todos os seus aplicativos.

Um exemplo de política nativa de nuvem para identidade em diretórios locais e de nuvem, pode incluir requisitos como o seguinte:

- Acesso autorizado a recursos com RBAC (controle de acesso baseado em função), autenticação multifator e SSO (logon único).
- Mitigação rápida de identidades de usuário suspeita de comprometimento.
- JIT (just-in-time), acesso apenas suficiente concedido em uma base tarefa por tarefa para limitar a exposição de credenciais de administrador com privilégios elevados.
- Identidade estendida de usuário e acesso a políticas em vários ambientes por meio de Azure Active Directory.

Embora seja importante entender a [linha de base de identidade](../identity-baseline/index.md) no contexto da linha de base de segurança, as [cinco disciplinas de governança de nuvem](../index.md) chamam a [linha de base de identidade](../identity-baseline/index.md) como sua própria disciplina, separada da linha de base de segurança.

### <a name="network-access-policies"></a>Políticas de acesso à rede

O controle de rede inclui a configuração, o gerenciamento e a proteção de elementos de rede, como rede virtual, balanceamento de carga, DNS e gateways. Os controles fornecem um meio para que os serviços se comuniquem e interoperem. O Azure inclui uma infraestrutura de rede robusta e segura para dar suporte aos seus requisitos de conectividade de serviço e aplicativo. A conectividade de rede é possível entre os recursos localizados no Azure, entre os recursos hospedados no local e o Azure e de e para a Internet e o Azure.

Uma política nativa de nuvem para controles de rede pode incluir requisitos como o seguinte:

- Conexões híbridas para recursos locais podem não ser permitidas em uma política nativa de nuvem. Se uma conexão híbrida for necessária, um exemplo de política de segurança empresarial mais robusto seria uma referência mais relevante.
- Os usuários podem estabelecer conexões seguras para e dentro do Azure usando redes virtuais e grupos de segurança de rede.
- O firewall nativo do Windows Azure protege os hosts do tráfego de rede mal-intencionado por acesso limitado à porta. Um bom exemplo dessa política é um requisito para bloquear (ou não habilitar) o tráfego diretamente para uma VM por SSH/RDP.
- Serviços como o WAF (firewall do aplicativo Web) do gateway Aplicativo Azure e a proteção contra DDoS do Azure protegem aplicativos e garantem a disponibilidade para máquinas virtuais em execução no Azure. Esses recursos não devem ser desabilitados.

### <a name="data-protection"></a>Proteção de dados

Uma das chaves para a proteção de dados na nuvem é a conta dos possíveis Estados nos quais os dados podem ocorrer e quais controles estão disponíveis para cada Estado. Para fins de segurança de dados do Azure e práticas recomendadas de criptografia, as recomendações se concentram nos seguintes Estados de dados:

- Os controles de criptografia de dados são incorporados em serviços de máquinas virtuais para armazenamento e banco de dados SQL.
- À medida que os dados se movem entre nuvens e clientes, eles podem ser protegidos usando protocolos de criptografia padrão do setor.
- Azure Key Vault permite que os usuários protejam e controlem chaves criptográficas, senhas, cadeias de conexão e certificados usados por aplicativos e serviços de nuvem.
- A proteção de informações do Azure ajudará a classificar, rotular e proteger seus dados confidenciais em aplicativos.

Embora esses recursos sejam criados no Azure, cada um dos itens acima requer configuração e pode aumentar os custos. O alinhamento de cada recurso nativo de nuvem com uma [estratégia de classificação de dados](../policy-compliance/data-classification.md) é altamente sugerido.

### <a name="security-monitoring"></a>Monitoramento de segurança

O monitoramento de segurança é uma estratégia proativa que audita seus recursos para identificar sistemas que não atendem aos padrões organizacionais ou práticas recomendadas. A central de segurança do Azure fornece linha de base de segurança unificada e proteção avançada contra ameaças em cargas de trabalho de nuvem híbrida Com a central de segurança, você pode aplicar políticas de segurança em suas cargas de trabalho, limitar sua exposição a ameaças e detectar e responder a ataques, incluindo:

- Exibição unificada de segurança em todas as cargas de trabalho locais e na nuvem com a central de segurança do Azure.
- Monitoramento contínuo e avaliações de segurança para garantir a conformidade e corrigir quaisquer vulnerabilidades.
- Ferramentas interativas e inteligência de ameaças contextuais para investigação simplificada.
- Log extensivo e integração com as informações de segurança existentes.
- Reduz a necessidade de soluções de segurança caras e não integradas.

### <a name="extending-cloud-native-policies"></a>Estendendo políticas nativas de nuvem

O uso da nuvem pode reduzir parte da carga de segurança. A Microsoft fornece segurança física para data centers do Azure e ajuda a proteger a plataforma de nuvem contra ameaças de infraestrutura, como um ataque de DDoS. Considerando que a Microsoft tem milhares de especialistas em segurança cibernética trabalhando na segurança todos os dias, os recursos para detectar, impedir ou mitigar os ataques cibernéticos são consideráveis. Na verdade, enquanto as organizações se preocupavam com a proteção da nuvem, a maior parte agora compreende que o nível de investimento em pessoas e infraestrutura especializada feita por fornecedores como a Microsoft torna a nuvem mais segura do que a mais local datacenters.

Mesmo com esse investimento em uma linha de base de segurança nativa de nuvem, é recomendável que qualquer diretiva de linha de base de segurança estenda as políticas nativas de nuvem padrão. Veja a seguir exemplos de políticas estendidas que devem ser consideradas, mesmo em um ambiente nativo de nuvem:

- **VMs seguras.** A segurança deve ser a prioridade principal de cada organização, e fazer isso efetivamente requer várias coisas. Você deve avaliar seu estado de segurança, proteger contra ameaças de segurança e, em seguida, detectar e responder rapidamente às ameaças que ocorrem.
- **Proteger o conteúdo da VM.** A configuração de backups automatizados regulares é essencial para proteger contra erros do usuário. No entanto, isso não é suficiente; Você também deve certificar-se de que os backups estão protegidos do ataques cibernéticos e estão disponíveis quando você precisar deles.
- **Monitorar aplicativos.** Esse padrão abrange várias tarefas, incluindo a obtenção de informações sobre a integridade de suas VMs, a compreensão das interações entre elas e o estabelecimento de maneiras de monitorar os aplicativos executados por essas VMs. Todas essas tarefas são essenciais para manter seus aplicativos em execução 24 horas por dia.
- **Acesso de dados seguro e de auditoria.** As organizações devem auditar todo o acesso a dados e aproveitar os recursos avançados de aprendizado de máquina para chamar desvios de padrões de acesso regulares.
- **Prática de failover.** As operações de nuvem que têm tolerâncias baixas para a falha devem ser capazes de fazer failover ou de uma recuperação de um incidente de segurança cibernética ou plataforma. Esses procedimentos não devem ser simplesmente documentados, mas devem ser praticado trimestralmente.

## <a name="next-steps"></a>Próximos passos

Agora que você analisou a política de linha de base de segurança de exemplo para soluções nativas de nuvem, retorne ao [Guia de revisão de política](../policy-compliance/cloud-policy-review.md) para começar a criar esse exemplo para criação de suas próprias políticas para adoção de nuvem.

> [!div class="nextstepaction"]
> [Crie suas próprias políticas usando o guia de revisão de política](../policy-compliance/cloud-policy-review.md)
