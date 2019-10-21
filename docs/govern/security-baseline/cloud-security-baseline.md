---
title: Entender a linha de base de segurança de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre a linha de base de segurança de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 216614c06f1638bf25149dac99f9bd258e9364aa
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548025"
---
# <a name="understand-the-cloud-security-baseline"></a>Entender a linha de base de segurança de nuvem

Este é um artigo introdutório sobre o tópico geral de uma linha de base de segurança de nuvem que se baseia nas [cinco disciplinas do controle de nuvem](../governance-disciplines.md) para estabelecer uma estrutura de governança. Informações mais detalhadas sobre segurança de nuvem estão disponíveis na [nuvem confiável do Azure](https://azure.microsoft.com/overview/trusted-cloud). Abordagens para melhorar a postura de segurança de suas organizações podem ser encontradas no [Catálogo de serviços de segurança de nuvem](https://www.microsoft.com/security/information-protection)

> [!NOTE]
> Este artigo não deve fornecer contexto suficiente para permitir que o leitor implemente uma estratégia de segurança. Ele é apenas para conscientização geral.

## <a name="cloud-security"></a>Segurança na nuvem

A segurança na nuvem é uma extensão das práticas tradicionais de segurança de informações. A segurança tradicional de ti inclui políticas e controles que regem a segurança de computadores, segurança de rede, proteção de dados, uso de informações e assim por diante. Essas mesmas políticas e controles são necessários na nuvem. Durante qualquer transformação na nuvem, é imperativo que o CISO esteja ativamente envolvido e entenda o cenário de nuvem, para garantir que as políticas de ti herdadas sejam mapeadas para os níveis adequados de controle na nuvem.

No mínimo, qualquer estratégia de segurança na nuvem deve considerar os seguintes tópicos:

- **Classificar dados.** Classificação de dados adequada para entender qualquer fonte de dados privada, protegida ou altamente confidencial. Isso ajudará a gerenciar o risco durante o planejamento.
- **Planeje um cenário de nuvem híbrida.** Entender como as redes locais herdadas se conectarão à nuvem ajudará o CISO a identificar e corrigir riscos.
- **Planeje ataques e erros.** Nos primeiros meses de uma transformação, os erros serão feitos à medida que a equipe aprende. Comece com implantações de baixo risco e altamente restritas para aprender com segurança.
- **Priorize a privacidade.** Em toda transformação, toda a equipe deve manter a melhor privacidade do cliente e do funcionário. Seus dados estão seguros na nuvem, mas a equipe deve estar ciente e cuidado extra ao lidar com dados confidenciais.

## <a name="protecting-data-and-privacy"></a>Protegendo dados e privacidade

Para organizações em todo o mundo &mdash;whether governos, instituições sem fins lucrativos ou empresas &mdash;cloud a computação se tornou uma parte fundamental de sua estratégia contínua de ti. Os serviços de nuvem fornecem às organizações de todos os tamanhos acesso a armazenamento de dados praticamente ilimitado, liberando-os da necessidade de comprar, manter e atualizar suas próprias redes e sistemas de computador. A Microsoft e outros provedores de nuvem oferecem infraestrutura de ti, plataforma e software como serviço (SaaS), permitindo que os clientes aumentem ou diminuam verticalmente, conforme necessário, e pagando apenas pelo poder de computação e pelo armazenamento que eles usam.

No entanto, à medida que as organizações continuam a aproveitar os benefícios dos serviços de nuvem, como maior escolha, agilidade e flexibilidade, ao mesmo tempo em que aumentam a eficiência e reduzem o custo de ti, eles devem considerar como a introdução dos serviços de nuvem afeta suas postura de privacidade, segurança e conformidade. A Microsoft trabalhou para tornar suas ofertas de nuvem não apenas escalonáveis, confiáveis e gerenciáveis, mas também para garantir que os dados de nossos clientes estejam protegidos e sejam usados de maneira transparente.

A segurança é um componente essencial de fortes proteções de dados em todos os ambientes de computação online. Mas a segurança sozinha não é suficiente. A disposição dos consumidores e das empresas de usar um determinado produto de computação em nuvem também depende de sua capacidade de confiar que a privacidade de suas informações será protegida e que seus dados só serão usados de maneira consistente com as expectativas dos clientes . Saiba mais sobre a abordagem da Microsoft para [proteger dados e privacidade na nuvem](https://go.microsoft.com/fwlink/?LinkId=808242&clcid=0x409)

## <a name="risk-mitigation"></a>Mitigação de risco

Os dois maiores riscos em qualquer datacenter podem ser agrupados em duas fontes: sistemas de envelhecimento e erro humano. A proteção contra esses dois riscos é um mínimo ao definir uma estratégia de segurança de ti. O mesmo é verdadeiro na nuvem. Veja a seguir alguns exemplos de controles que podem ser colocados em vigor para corrigir riscos e fortalecer sua estratégia de segurança de nuvem.

- **Sistemas herdados:** Muitos componentes em soluções de datacenter locais consistem em software, hardware e processos que preparam riscos de segurança atuais. Quando possível, corrija, substitua ou desative esses sistemas durante uma transformação em nuvem. É claro que isso nem sempre é viável. Se qualquer sistema herdado permanecer na produção em uma solução híbrida, é importante que esses sistemas tenham sido inventariados e compreendidos durante o design do datacenter virtual. Isso permite que a equipe de design elimine ou controle o acesso a esses sistemas da nuvem.
- **Controles e processos de segurança de ti:** No mínimo, as equipes de design de nuvem devem ser atualizadas em processos e controles de segurança de ti existentes para levá-los para a nuvem. Em um cenário ideal, um membro da equipe de segurança de ti seria treinado em segurança cibernética e dedicado como membro das equipes de design e implementação.
- **Monitoramento e auditoria:** Ao projetar processos de governança e ferramentas, verifique se as soluções de monitoramento e auditoria incluem riscos de segurança ou violações.

> [!NOTE]
> **Divulgação de dívida técnica:** Este tópico não tem as próximas etapas acionáveis. Os artigos de adição serão expandidos neste tópico ao longo do tempo. Informações mais detalhadas sobre segurança de nuvem estão disponíveis na [nuvem confiável do Azure](https://azure.microsoft.com/overview/trusted-cloud). Abordagens para melhorar a postura de segurança de suas organizações podem ser encontradas no [Catálogo de serviços de segurança de nuvem](https://www.microsoft.com/security/information-protection)
