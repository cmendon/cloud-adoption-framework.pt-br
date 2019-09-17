---
title: 'Guia empresarial Standard: Melhorar a disciplina de linha de base de segurança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia empresarial Standard: Melhorar a disciplina de linha de base de segurança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a9b67b20f0f9169f5da7f941615612218ef29f94
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030887"
---
# <a name="standard-enterprise-guide-improve-the-security-baseline-discipline"></a>Guia empresarial Standard: Melhorar a disciplina de linha de base de segurança

Este artigo avança na narração adicionando controles de segurança que dão suporte à movimentação de dados protegidos para a nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A liderança de negócios e de TI está satisfeita com os resultados dos testes iniciais pelas equipes de TI, de Desenvolvimento de Aplicativos e de BI. Para obter valores comerciais tangíveis dessas experiências, essas equipes devem ter permissão para integrar dados protegidos a soluções. Isso dispara alterações na política corporativa, mas também requer melhoria incremental das implementações de governança de nuvem antes que os dados protegidos possam chegar à nuvem.

### <a name="changes-to-the-cloud-governance-team"></a>Alterações na equipe de governança de nuvem

Devido ao efeito da mudança de narração e suporte fornecidos até agora, a equipe de governança de nuvem agora é exibida de maneira diferente. Os dois administradores de sistema que iniciaram a equipe agora são vistos como arquitetos de nuvem experientes. Conforme essa narrativa evoluir, a percepção sobre eles mudará de Custodiantes da Nuvem para uma função de Guardiões da Nuvem.

Embora a diferença seja sutil, é uma distinção importante ao criar uma cultura de TI focada em governança. Um Custodiante da Nuvem organiza a bagunça feita pelos arquitetos de nuvem inovadores. As duas funções têm um atrito natural e objetivos opostos. Por outro lado, um Guardião da Nuvem ajuda a proteger a nuvem para que outros arquitetos de nuvem possam trabalhar mais rapidamente, com menos complicações. Além disso, um guardião de nuvem está envolvido na criação de modelos que aceleram a implantação e a adoção, tornando-os um acelerador de inovação, bem como um defender das cinco disciplinas de governança de nuvem.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

No início dessa narrativa, as equipes de Desenvolvimento de Aplicativos ainda estavam trabalhando em uma funcionalidade de desenvolvimento/teste, e a equipe de BI ainda estava na fase experimental. A TI trabalhava com dois ambientes de infraestrutura hospedada, chamados de Produção e Recuperação de desastre.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- A equipe de desenvolvimento de aplicativos implementou um pipeline de CI/CD para implantar um aplicativo nativo de nuvem com uma experiência de usuário aprimorada. Esse aplicativo ainda não interage com os dados protegidos, portanto, não está pronto para produção.
- A equipe de Business Intelligence dentro dela organizada ativamente os dados na nuvem da logística, do inventário e de fontes de terceiros. Esses dados estão sendo usados para gerar novas previsões, o que poderia moldar os processos de negócios. No entanto, essas previsões e insights não são acionáveis até que os dados financeiros e do cliente possam ser integrados à plataforma de dados.
- A equipe de TI presta ajuda aos planos do Diretor Financeiro e do Diretor de TI para desativar o datacenter de recuperação de desastre. Mais de 1.000 dos 2.000 ativos no datacenter de recuperação de desastre foram desativados ou migrados.
- As políticas com rigidez de definição relacionadas a dados pessoais e dados financeiros foram modernizadas. No entanto, as novas políticas corporativas dependem da implementação das políticas de segurança e governança relacionadas. As equipes ainda estão trabalhando nisso.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

Experimentos iniciais pelas equipes de Desenvolvimento de Aplicativos e de BI mostraram possíveis aprimoramentos nas experiências do cliente e nas decisões orientadas a dados. As duas equipes querem expandir a adoção da nuvem nos próximos 18 meses implantando essas soluções na produção.

Durante os seis meses restantes, a equipe de governança de nuvem implementará os requisitos de segurança e governança para permitir que as equipes de adoção da nuvem migrem os dados protegidos nesses data centers.

As alterações no estado atual e futuro expõem novos riscos que exigem novas declarações de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Violação de dados:** Com a adoção de uma nova plataforma de dados, há um aumento inerente no ônus relacionado a possíveis violações de dados. Os técnicos que adotam as tecnologias de nuvem têm maiores responsabilidades de implementar soluções que possam diminuir esse risco. Uma estratégia de governança e segurança robusta deve ser implementada para garantir que os técnicos cumpram essas responsabilidades.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

1. Aplicativos de missão crítica ou dados protegidos podem ser implantados involuntariamente.
2. Dados protegidos podem ser expostos durante o armazenamento devido a decisões de criptografia ineficientes.
3. Os usuários não autorizados podem acessar dados protegidos.
4. Uma invasão externa pode resultar no acesso aos dados protegidos.
5. Uma invasão externa ou ataques de negação de serviço podem causar uma interrupção dos negócios.
6. As alterações de emprego ou da organização podem resultar em acesso não autorizado aos dados protegidos.
7. Novas explorações poderiam criar novas oportunidades de invasão ou acesso.
8. Os processos de implantação inconsistentes podem resultar em falhas de segurança, o que pode levar a perdas de dados ou interrupções.
9. A inconsistência na configuração ou patches ausentes podem resultar em falhas de segurança não intencionais, o que pode levar a vazamentos de dados ou interrupções.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece longa, mas adotar essas políticas talvez seja mais fácil do que parece.

1. Todos os ativos implantados devem ser categorizados por nível de importância e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.
2. Aplicativos que armazenam ou acessam dados protegidos devem ser gerenciados diferentemente daqueles que não são. No mínimo, eles devem ser segmentados para evitar acesso não intencional de dados protegidos.
3. Todos os dados protegidos devem ser criptografados quando estão em repouso.
4. As permissões elevadas em qualquer segmento que contenha dados protegidos devem ser uma exceção. Essas exceções serão registradas com a equipe de governança de nuvem e auditadas regularmente.
5. As sub-redes de rede que contêm dados protegidos devem ser isoladas de todas as outras sub-redes. O tráfego de rede entre as sub-redes de dados protegidos será auditado regularmente.
6. Nenhuma sub-rede que contém os dados protegidos pode ser acessada diretamente pela Internet pública ou em datacenters. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que pode executar a verificação de pacotes e funções de bloqueio.
7. As ferramentas de governança devem realizar a auditoria e impor requisitos de configuração de rede definidos pela equipe de gerenciamento de segurança.
8. As ferramentas de governança devem limitar a implantação da VM somente a imagens aprovadas.
9. Sempre que possível, o gerenciamento da configuração do nó deve aplicar requisitos da política à configuração de qualquer sistema operacional convidado.
10. As ferramentas de governança devem impor que as atualizações automáticas sejam habilitadas em todos os ativos implantados. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Ativos que não são atualizados automaticamente devem ser incluídos nos processos pertencentes às Operações de TI.
11. A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos exigirá uma análise da equipe de governança de nuvem, para garantir que o plano gráfico adequado seja atribuído.
12. Um modelo de acesso de privilégio mínimo será aplicado a qualquer grupo de gerenciamento ou assinatura que contenha aplicativos críticos ou dados protegidos.
13. Tendências e explorações que possam afetar as implantações de nuvem devem ser examinadas regularmente pela equipe de segurança para que sejam fornecidas atualizações às ferramentas de gerenciamento de segurança usadas na nuvem.
14. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
15. Os scripts de implantação devem ser mantidos em um repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
16. Os processos de governança devem incluir auditorias no momento da implantação e em ciclos regulares para garantir a consistência em todos os ativos.
17. A implantação de qualquer aplicativo que exija a autenticação do cliente deve usar um provedor de identidade aprovado que seja compatível com o provedor de identidade principal para usuários internos.
18. Os processos de governança de nuvem devem incluir revisões trimestrais com equipes de gerenciamento de identidades. Essas revisões podem ajudar a identificar padrões de uso ou atores mal-intencionados que devem ser impedidos pela configuração de ativos de nuvem.

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

O design do MVP de governança será alterado para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

1. As equipes de Rede e de Segurança de TI definirão os requisitos de rede. A equipe de governança de nuvem dará suporte à conversa.
1. As equipes de Identidade e Segurança de TI definirão requisitos de identidade e farão as alterações necessárias na implementação local do Active Directory. A equipe de governança de nuvem examinará as alterações.
1. Crie um repositório no Azure DevOps para armazenar e controlar a versão de todos os modelos do Azure Resource Manager relevantes e configurações com script.
1. Implementação da Central de Segurança do Azure:
    1. Configure a Central de Segurança do Azure para qualquer grupo de gerenciamento que contenha classificações de dados protegidos.
    1. Defina o provisionamento automático como ativado por padrão para garantir a conformidade da aplicação de patch.
    1. Estabeleça configurações de segurança do sistema operacional. A equipe de Segurança de TI definirá a configuração.
    1. Dê suporte à equipe de Segurança de TI no uso inicial da Central de Segurança. Faça a transição do uso da Central de Segurança para a equipe de Segurança de TI, mas mantenha o acesso para aprimorar continuamente a governança.
    1. Crie um modelo do Resource Manager que reflita as alterações necessárias para a configuração da Central de Segurança em uma assinatura.
1. Atualize as políticas do Azure para todas as assinaturas:
    1. Realize uma auditoria e imponha o nível de importância e a classificação de dados para todos os grupos de gerenciamento e assinaturas a fim de identificar todas as assinaturas com classificações de dados protegidos.
    1. Realize uma auditoria e imponha o uso exclusivo de imagens aprovadas.
1. Atualize as políticas do Azure para todas as assinaturas que contenham classificações de dados protegidos:
    1. Realize uma auditoria e imponha o uso exclusivo das funções padrão do RBAC do Azure.
    1. Realize uma auditoria e imponha a criptografia para todas as contas de armazenamento e arquivos em repouso em nós individuais.
    1. Realize uma auditoria e imponha a aplicação de um NSG para todas as NICs e sub-redes. As equipes de Rede e de Segurança de TI definirão o NSG.
    1. Realize uma auditoria e imponha o uso de uma sub-rede de rede aprovada e rede virtual por adaptador de rede.
    1. Realize uma auditoria e imponha a limitação das tabelas de roteamento definidas pelo usuário.
    1. Aplique as políticas internas para a configuração do convidado da seguinte maneira:
        1. Realize uma auditoria para verificar se os servidores Web do Windows estão usando protocolos de comunicação segura.
        1. Realize uma auditoria para verificar se as configurações de segurança de senha estão definidas corretamente em computadores Linux e Windows.
1. Configuração do firewall:
    1. Identifique uma configuração do Firewall do Azure que atenda aos requisitos de segurança necessários. Como alternativa, identifique um dispositivo de terceiros que seja compatível com o Azure.
    1. Crie um modelo do Resource Manager para implantar o firewall com as configurações necessárias.
1. Blueprint do Azure:
    1. Crie um novo blueprint chamado `protected-data`.
    1. Adicione o firewall e os modelos da Central de Segurança do Azure ao blueprint.
    1. Adicione as novas políticas para assinaturas de dados protegidos.
    1. Publique o Blueprint em qualquer grupo de gerenciamento que atualmente planeja hospedar dados protegidos.
    1. Aplique o novo blueprint a cada assinatura afetada, além dos blueprints existentes.

## <a name="conclusion"></a>Conclusão

Adicionar os processos acima e as alterações ao MVP de governança ajudará a corrigir muitos dos riscos associados ao controle de segurança. Em conjunto, eles adicionam ferramentas de monitoramento de segurança, identidade e rede necessárias para proteger os dados.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também mudam. Para a empresa fictícia neste guia, a próxima etapa é oferecer suporte a cargas de trabalho de missão crítica. Essa é a situação em que os controles de Consistência de Recursos são necessários.

> [!div class="nextstepaction"]
> [Melhorando a consistência de recursos](./resource-consistency-improvement.md)
