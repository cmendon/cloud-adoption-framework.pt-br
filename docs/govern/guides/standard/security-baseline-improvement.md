---
title: 'Guia de governança empresarial padrão: melhorar a disciplina de linha de base de segurança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança empresarial padrão: melhorar a disciplina de linha de base de segurança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b1f43bdf0e0d58c40f11e45caf0221f7983c9624
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547529"
---
# <a name="standard-enterprise-governance-guide-improve-the-security-baseline-discipline"></a>Guia de governança empresarial padrão: melhorar a disciplina de linha de base de segurança

Este artigo avança na narração adicionando controles de segurança que dão suporte à movimentação de dados protegidos para a nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A liderança de ti e de negócios tem se satisfeito com os resultados da experimentação de estágio antecipada pelas equipes de ti, desenvolvimento de aplicativos e BI. Para obter os valores de negócios tangíveis desses experimentos, essas equipes devem ter permissão para integrar dados protegidos em soluções. Isso dispara alterações na política corporativa, mas também requer melhoria incremental das implementações de governança de nuvem antes que os dados protegidos possam chegar à nuvem.

### <a name="changes-to-the-cloud-governance-team"></a>Alterações na equipe de governança de nuvem

Devido ao efeito da mudança de narração e suporte fornecidos até agora, a equipe de governança de nuvem agora é exibida de maneira diferente. Os dois administradores de sistema que iniciaram a equipe agora são exibidos como arquitetos de nuvem experientes. À medida que essa narração for desenvolveda, a percepção delas mudará de ser responsáveis por nuvem para mais de uma função de guardião de nuvem.

Embora a diferença seja sutil, trata-se de uma distinção importante ao criar uma cultura de ti focada em governança. Um dos responsáveis pela nuvem limpa as bagunças feitas pelos arquitetos de nuvem inovadores. As duas funções têm um conflito natural e os objetivos opostos. Por outro lado, um guardião de nuvem ajuda a manter a nuvem segura, de modo que outros arquitetos de nuvem podem se mover mais rapidamente, com menos confusão. Além disso, um guardião de nuvem está envolvido na criação de modelos que aceleram a implantação e a adoção, tornando-os um acelerador de inovação, bem como um defender das cinco disciplinas de governança de nuvem.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

No início desta narração, as equipes de desenvolvimento de aplicativos ainda estavam trabalhando em uma capacidade de desenvolvimento/teste, e a equipe de BI ainda estava na fase experimental. Ele operava dois ambientes de infraestrutura hospedados, chamados prod e DR.

Desde então, algumas coisas mudaram que afetarão a governança:

- A equipe de desenvolvimento de aplicativos implementou um pipeline de CI/CD para implantar um aplicativo nativo de nuvem com uma experiência de usuário aprimorada. Esse aplicativo ainda não interage com os dados protegidos e, portanto, não está pronto para produção.
- A equipe de Business Intelligence dentro dela organizada ativamente os dados na nuvem da logística, do inventário e de fontes de terceiros. Esses dados estão sendo usados para gerar novas previsões, que podem moldar os processos de negócios. No entanto, essas previsões e ideias não são acionáveis até que os dados de clientes e financeiros possam ser integrados à plataforma de dados.
- A equipe de ti está progredindo com os planos do CIO e do CFO para desativar o datacenter de recuperação de desastres. Mais de 1.000 dos ativos 2.000 no datacenter de recuperação de desastre foram desativados ou migrados.
- As políticas com rigidez de definição relacionadas a dados pessoais e dados financeiros foram modernizadas. No entanto, as novas políticas corporativas são contingentes com a implementação de políticas relacionadas de segurança e governança. As equipes ainda estão paralisadas.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

Os experimentos iniciais das equipes de desenvolvimento e BI do aplicativo mostram possíveis aprimoramentos nas experiências do cliente e decisões controladas por dados. Ambas as equipes desejam expandir a adoção da nuvem nos próximos 18 meses implantando essas soluções em produção.

Durante os seis meses restantes, a equipe de governança de nuvem implementará os requisitos de segurança e governança para permitir que as equipes de adoção da nuvem migrem os dados protegidos nesses data centers.

As alterações no estado atual e no futuro expõem novos riscos que exigem novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Violação de dados:** Ao adotar qualquer nova plataforma de dados, há um aumento inerente em passivos relacionados a possíveis violações de dados. Os técnicos que adotam tecnologias de nuvem têm maior responsabilidades para implementar soluções que podem diminuir esse risco. Uma estratégia robusta de segurança e governança deve ser implementada para garantir que esses técnicos atendam a essas responsabilidades.

Esse risco comercial pode ser expandido em alguns riscos técnicos:

1. Aplicativos de missão crítica ou dados protegidos podem ser implantados involuntariamente.
2. Os dados protegidos podem ser expostos durante o armazenamento devido a decisões de criptografia insatisfatórias.
3. Usuários não autorizados podem acessar dados protegidos.
4. A invasão externa pode resultar em acesso aos dados protegidos.
5. A invasão externa ou ataques de negação de serviço podem causar uma interrupção nos negócios.
6. Alterações de organização ou de trabalho podem permitir o acesso não autorizado a dados protegidos.
7. Novas explorações podem criar novas oportunidades de invasão ou de acesso.
8. Processos de implantação inconsistentes podem resultar em lacunas de segurança, o que pode levar a vazamentos de dados ou interrupções.
9. Descompasso de configuração ou patches perdidos podem resultar em lacunas de segurança indesejadas, o que pode levar a vazamentos de dados ou interrupções.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece muito longa, mas a adoção dessas políticas pode ser mais fácil do que aparece.

1. Todos os ativos implantados devem ser categorizados por criticalidade e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.
2. Os aplicativos que armazenam ou acessam dados protegidos devem ser gerenciados de forma diferente daqueles que não o fazem. No mínimo, eles devem ser segmentados para evitar o acesso não intencional de dados protegidos.
3. Todos os dados protegidos devem ser criptografados quando em repouso. Embora esse seja o padrão para todas as contas de armazenamento do Azure, outras estratégias de criptografia podem ser necessárias, incluindo a criptografia dos dados dentro da conta de armazenamento, a criptografia de VMs e a criptografia no nível do banco de dado se estiver aproveitando o SQL em uma VM (TDE e coluna criptografia).
4. Permissões elevadas em qualquer segmento que contém dados protegidos devem ser uma exceção. Essas exceções serão registradas com a equipe de governança de nuvem e auditadas regularmente.
5. As sub-redes de rede que contêm dados protegidos devem ser isoladas de quaisquer outras sub-redes. O tráfego de rede entre sub-redes de dados protegidos será auditado regularmente.
6. Nenhuma sub-rede contendo dados protegidos pode ser acessada diretamente pela Internet pública ou por data centers. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que possa executar a verificação de pacotes e as funções de bloqueio.
7. As ferramentas de governança devem auditar e aplicar os requisitos de configuração de rede definidos pela equipe de gerenciamento de segurança.
8. As ferramentas de governança devem limitar a implantação de VM somente a imagens aprovadas.
9. Sempre que possível, o gerenciamento de configuração de nó deve aplicar requisitos de política à configuração de qualquer sistema operacional convidado.
10. As ferramentas de governança devem impor que as atualizações automáticas estejam habilitadas em todos os ativos implantados. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Os ativos que não são atualizados automaticamente devem ser incluídos em processos de propriedade de operações de ti.
11. A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos exigirá uma análise da equipe de governança de nuvem, para garantir que o plano gráfico adequado seja atribuído.
12. Um modelo de acesso com privilégios mínimos será aplicado a qualquer grupo de gerenciamento ou assinatura que contenha aplicativos de missão crítica ou dados protegidos.
13. As tendências e explorações que poderiam afetar as implantações na nuvem devem ser examinadas regularmente pela equipe de segurança para fornecer atualizações para as ferramentas de gerenciamento de segurança usadas na nuvem.
14. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
15. Os scripts de implantação devem ser mantidos em um repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
16. Os processos de governança devem incluir auditorias no ponto de implantação e em ciclos regulares para garantir a consistência em todos os ativos.
17. A implantação de qualquer aplicativo que exija autenticação do cliente deve usar um provedor de identidade aprovado que seja compatível com o provedor de identidade principal para usuários internos.
18. Os processos de governança de nuvem devem incluir revisões trimestrais com equipes de gerenciamento de identidade. Essas revisões podem ajudar a identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativos de nuvem.

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

O design do MVP de governança será alterado para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas duas alterações de design atenderão às novas instruções de política corporativa.

1. As equipes de segurança de ti e de rede definirão os requisitos de rede. A equipe de governança de nuvem dará suporte à conversa.
2. A identidade e as equipes de segurança de ti definirão requisitos de identidade e farão as alterações necessárias na implementação de Active Directory local. A equipe de governança de nuvem examinará as alterações.
3. Crie um repositório no Azure DevOps para armazenar e versão todos os modelos de Azure Resource Manager relevantes e configurações com script.
4. Implementação da central de segurança do Azure:
    1. Configure a central de segurança do Azure para qualquer grupo de gerenciamento que contenha classificações de dados protegidas.
    2. Defina o provisionamento automático como ativado por padrão para garantir a conformidade da aplicação de patch.
    3. Estabeleça configurações de segurança do sistema operacional. A equipe de segurança de ti definirá a configuração.
    4. Dê suporte à equipe de segurança de ti no uso inicial da central de segurança. Migre o uso da central de segurança para a equipe de segurança de ti, mas mantenha o acesso com a finalidade de melhorar continuamente a governança.
    5. Crie um modelo do Resource Manager que reflita as alterações necessárias para a configuração da central de segurança em uma assinatura.
5. Atualizar políticas do Azure para todas as assinaturas:
    1. Auditar e impor a criticalidade e a classificação de dados em todos os grupos de gerenciamento e assinaturas, para identificar todas as assinaturas com classificações de dados protegidas.
    2. Auditar e impor o uso somente de imagens aprovadas.
6. Atualize as políticas do Azure para todas as assinaturas que contêm classificações de dados protegidas:
    1. Auditar e impor o uso somente das funções RBAC padrão do Azure.
    2. Auditar e impor a criptografia para todas as contas de armazenamento e arquivos em repouso em nós individuais.
    3. Auditar e impor a aplicação de um NSG a todas as NICs e sub-redes. As equipes de segurança de ti e de rede definirão o NSG.
    4. Auditar e impor o uso de sub-rede de rede aprovada e vNet por interface de rede.
    5. Auditar e impor a limitação de tabelas de roteamento definidas pelo usuário.
    6. Aplique as políticas internas para a configuração de convidado da seguinte maneira:
        1. Auditar que os servidores Web do Windows estão usando protocolos de comunicação seguros.
        2. Auditar que as configurações de segurança de senha estão definidas corretamente dentro de computadores Linux e Windows.
7. Configuração do firewall:
    1. Identifique uma configuração do firewall do Azure que atenda aos requisitos de segurança necessários. Como alternativa, identifique um dispositivo de terceiros compatível que seja compatível com o Azure.
    2. Crie um modelo do Resource Manager para implantar o firewall com as configurações necessárias.
8. Especificações técnicas do Azure:
    1. Crie um novo plano gráfico chamado `protected-data`.
    2. Adicione o firewall e os modelos da central de segurança do Azure ao plano gráfico.
    3. Adicione as novas políticas para assinaturas de dados protegidos.
    4. Publique o Blueprint em qualquer grupo de gerenciamento que atualmente planeja hospedar dados protegidos.
    5. Aplique o novo Blueprint a cada assinatura afetada, além de plantas existentes.

## <a name="conclusion"></a>Conclusão

Adicionar os processos acima e as alterações ao MVP de governança ajudará a corrigir muitos dos riscos associados ao controle de segurança. Juntos, eles adicionam as ferramentas de rede, identidade e monitoramento de segurança necessárias para proteger os dados.

## <a name="next-steps"></a>Próximos passos

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também mudam. Para a empresa fictícia neste guia, a próxima etapa é oferecer suporte a cargas de trabalho de missão crítica. Esse é o ponto quando os controles de consistência de recursos são necessários.

> [!div class="nextstepaction"]
> [Melhorando a consistência de recursos](./resource-consistency-improvement.md)
