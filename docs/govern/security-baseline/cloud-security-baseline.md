---
title: Entender a linha de base de segurança de nuvem
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba mais sobre a linha de base de segurança de nuvem.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: dfb7969d19017c003ef961c18e87b8cb110ccd4e
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030662"
---
# <a name="understand-the-cloud-security-baseline"></a>Entender a linha de base de segurança de nuvem

Este é um artigo introdutório sobre o tópico geral de uma linha de base de segurança de nuvem que se baseia nas [cinco disciplinas do controle de nuvem](../governance-disciplines.md) para estabelecer uma estrutura de governança. Informações mais detalhadas sobre segurança de nuvem estão disponíveis na [nuvem confiável do Azure](https://azure.microsoft.com/overview/trusted-cloud). Abordagens para melhorar as condições de segurança da organização podem ser localizadas no [Catálogo de Serviços de Segurança de Nuvem](https://www.microsoft.com/security/information-protection)

> [!NOTE]
> Este artigo não disponibiliza contexto suficiente para permitir que o leitor implemente uma estratégia de segurança. É apenas para conhecimento geral.

## <a name="cloud-security"></a>Segurança de Nuvem

A segurança de nuvem é uma extensão das práticas tradicionais de segurança da informação. A segurança de TI tradicional incluiria políticas e controles que controlam a segurança do computador, segurança de rede, proteção de dados, uso de informações, e assim por diante. Essas mesmas políticas e controles são necessários na nuvem. Durante qualquer transformação na nuvem, é imperativo que o CISO esteja ativamente envolvido e entenda o cenário de nuvem, para garantir que as políticas de ti herdadas sejam mapeadas para os níveis adequados de controle na nuvem.

No mínimo, qualquer estratégia de segurança de nuvem deve considerar os seguintes tópicos:

- **Classificar dados.** Classificação de dados apropriada para reconhecer todas as fontes de dados privados, protegidos ou altamente confidenciais. Isso ajudará a gerenciar risco durante o planejamento.
- **Planeje um cenário de nuvem híbrida.** Entender como as redes locais herdadas se conectarão à nuvem ajudará o CISO a identificar e corrigir riscos.
- **Planeje ataques e erros.** Nos primeiros meses de uma transformação, erros ocorrerão conforme a equipe vai aprendendo continuamente. Inicie com implantações de baixo risco e altamente restritas para aprender com segurança.
- **Priorize a privacidade.** Durante toda a transformação, toda a equipe deverá manter a privacidade do cliente e dos funcionários como prioridade. Os dados estarão seguros na nuvem, mas a equipe deverá estar ciente e ser extremamente cautelosa ao lidar com dados confidenciais.

## <a name="protecting-data-and-privacy"></a>Proteger dados e privacidade

Para organizações em todo o&mdash;mundo se os governos, organizações sem fins lucrativos&mdash;ou computação em nuvem se tornaram uma parte fundamental de sua estratégia contínua de ti. Os serviços de nuvem permitem que as organizações de todos os portes acessem virtualmente o armazenamento de dados ilimitados, enquanto as desobriga da necessidade de comprar, manter e atualizar suas próprias redes e sistemas de computadores. A Microsoft e outros provedores de nuvem oferecem infraestrutura de TI, plataforma e SaaS (software como serviço), permitindo aos clientes escalar ou reduzir verticalmente de maneira muito rápida, conforme necessário, e pagar apenas pela capacidade de computação e armazenamento que utilizarem.

No entanto, como as organizações continuam beneficiando-se dos serviços de nuvem, como escolha, agilidade e flexibilidade maiores, ao mesmo tempo que aumentam a eficiência e diminuem o custo de TI, deverão considerar como a introdução de serviços de nuvem afetará as condições de privacidade, segurança e conformidade. A Microsoft tem trabalhado para tornar as ofertas de nuvem não apenas escalonáveis, confiáveis e gerenciáveis, mas também, para garantir que os dados de nossos clientes sejam protegidos e utilizados de maneira transparente.

A segurança é um elemento fundamental para garantir proteção dos dados robusta em todos os ambientes de computação online. Porém, a segurança sozinha não é suficiente. A predisposição que os consumidores e as empresas têm para utilizar um determinado produto de computação em nuvem, também depende da capacidade de confiarem que a privacidade de suas informações será protegida e que seus dados serão utilizados somente de maneira compatível com as expectativas do cliente. Saiba mais sobre a abordagem da Microsoft para [Proteção de dados e privacidade na nuvem](https://go.microsoft.com/fwlink/?LinkId=808242&clcid=0x409)

## <a name="risk-mitigation"></a>Mitigação de risco

Os dois maiores riscos em qualquer datacenter podem ser agrupados em duas origens: Sistemas obsoletos e erro humano. Proteger contra esses dois riscos é o mínimo necessário ao definir uma estratégia de segurança de TI. O mesmo aplica-se para a nuvem. Veja a seguir alguns exemplos de controles que podem ser colocados em vigor para corrigir riscos e fortalecer sua estratégia de segurança de nuvem.

- **Sistemas herdados:** Muitos componentes em soluções de datacenter locais consistem em software, hardware e processos que antecedem os riscos de segurança atuais. Quando possível, corrija, substitua ou desative esses sistemas durante uma transformação em nuvem. Evidentemente, isso nem sempre será possível ou viável. Se qualquer sistema herdado permanecer na produção em uma solução híbrida, é importante que esses sistemas tenham sido inventariados e compreendidos durante o design do datacenter virtual. Isso permitirá que a equipe de projeto elimine ou controle o acesso a esses sistemas a partir da nuvem.
- **Controles e processos de segurança de ti:** No mínimo, as equipes de design de nuvem devem ser atualizadas em processos e controles de segurança de ti existentes para levá-los para a nuvem. Em um cenário ideal, um membro da equipe de segurança de TI seria treinado em segurança cibernética e destinado como membro das equipes de projeto e implementação.
- **Monitoramento e auditoria:** Ao projetar processos e ferramentas de governança, certifique-se de que as soluções de monitoramento e auditoria incluam riscos ou violações de segurança.

> [!NOTE]
> **Divulgação de dívida técnica:** Este tópico não possui as próximas etapas acionáveis. Artigos adicionais desenvolverão esse tópico ao longo do tempo. Informações mais detalhadas sobre Segurança de Nuvem estão disponíveis na [Nuvem Confiável do Azure](https://azure.microsoft.com/overview/trusted-cloud). Abordagens para melhorar as condições de segurança da organização podem ser localizadas no [Catálogo de Serviços de Segurança de Nuvem](https://www.microsoft.com/security/information-protection)
