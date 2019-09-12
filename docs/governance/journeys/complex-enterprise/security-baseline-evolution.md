---
title: 'Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de segurança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de segurança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 8db2c49ad59e80840c318d1edca55e9c7d71da24
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908885"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-security-baseline-discipline"></a>Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de segurança

Este artigo avança na narração adicionando controles de segurança que dão suporte à movimentação de dados protegidos para a nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

O CIO passou meses colaborando com colegas e a equipe jurídica da empresa. Um consultor de gerenciamento com experiência em segurança cibernética participou do processo para ajudar as equipes de segurança e governança de TI a esboçar uma nova política referente a dados protegidos. O grupo foi capaz de estimular o suporte a placas para substituir a política existente, permitindo que dados confidenciais pessoais e financeiros sejam hospedados por provedores de nuvem aprovados. Isso exigia a adoção de um conjunto de requisitos de segurança e um processo de governança para verificar e documentar o cumprimento dessas políticas.

Nos últimos 12 meses, as equipes de adoção de nuvem limparam a maioria dos 5.000 ativos dos dois datacenters que serão desativados. 350 ativos incompatíveis foram movidos para um datacenter alternativo. Somente 1.250 máquinas virtuais contêm dados protegidos.

### <a name="changes-in-the-cloud-governance-team"></a>Alterações na equipe de governança de nuvem

A equipe de governança de nuvem continua a mudar junto com a narração. Os dois membros fundadores da equipe agora estão entre os arquitetos de nuvem mais respeitados na empresa. A coleção de scripts de configuração cresceu à medida que novas equipes foram lidando com implantações inovadoras. A equipe de governança de nuvem também cresceu. Mais recentemente, os membros da equipe de operações de ti uniram as atividades da equipe de governança de nuvem para se preparar para operações de nuvem. Os arquitetos de nuvem que ajudam a criar essa comunidade são vistos como guardiões de nuvem e aceleradores de nuvem.

Embora seja sutil, a diferença entre essas duas classificações deve ser considerada durante o estabelecimento de uma cultura de TI focada em governança. O trabalho de um guardião da nuvem é "arrumar a bagunça" feita pelos arquitetos de nuvem inovadores, além do atrito natural existente entre essas duas funções que, na prática, têm objetivos opostos. Por outro lado, um guardião ajuda a proteger a nuvem para que outros arquitetos possam trabalhar com mais rapidez e menos complicações. Um acelerador de nuvem executa ambas as funções, mas também está envolvida na criação de modelos para acelerar a implantação e a adoção, tornando-se um acelerador de inovação, bem como um defender das cinco disciplinas de governança de nuvem.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narrativa, a empresa deu início ao processo de desativação de dois datacenters. Esse esforço contínuo inclui a migração de alguns aplicativos com requisitos de autenticação herdados, que exigiam melhorias incrementais na linha de base de identidade, descritas no [artigo anterior](identity-baseline-evolution.md).

Desde então, ocorreram algumas mudanças que afetarão a governança:

- Milhares de ativos de negócios e de TI foram implantados na nuvem.
- A equipe de desenvolvimento de aplicativos implementou um pipeline de CI/CD (integração contínua e implantação contínua) para implantar um aplicativo nativo de nuvem com uma experiência de usuário aprimorada. Esse aplicativo ainda não interage com os dados protegidos, portanto, não está pronto para produção.
- A equipe de Business Intelligence dentro da TI organiza ativamente os dados na nuvem a partir de dados de logística, inventário e de terceiros. Esses dados estão sendo usados para gerar novas previsões, o que poderia moldar os processos de negócios. No entanto, essas previsões e informações não são acionáveis até que os dados financeiros e do cliente possam ser integrados à plataforma de dados.
- A equipe de TI está em andamento nos planos do CIO e CFO para desativar dois datacenters. Quase 3.500 dos ativos nos dois datacenters foram desativados ou migrados.
- As políticas relativas a dados confidenciais pessoais e financeiros foram modernizadas. No entanto, as novas políticas corporativas dependem da implementação das políticas de segurança e governança relacionadas. As equipes ainda estão trabalhando nisso.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

- Experimentos iniciais das equipes de BI e desenvolvimento de aplicativo mostraram melhorias potenciais nas experiências do cliente e decisões orientadas por dados. As duas equipes querem expandir a adoção da nuvem nos próximos 18 meses ao implantar essas soluções na produção.
- A TI desenvolveu uma justificativa comercial para migrar mais cinco datacenters para Azure, o que diminuirá ainda mais os custos de TI e proporcionará maior agilidade nos negócios. Embora menor em escala, espera-se que a desativação desses datacenters duplique a economia total de custos.
- Despesas de capital e orçamentos de despesas operacionais foram aprovados para implementar as políticas, as ferramentas e os processos necessários de segurança e governança. As economias de custo esperadas da desativação do datacenter são mais do que suficiente para pagar por essa nova iniciativa. TI e liderança de negócios estão confiantes que esse investimento acelerará a realização de retornos em outras áreas. A equipe de governança de nuvem todas tornou-se uma equipe reconhecida com liderança e pessoal dedicados.
- Coletivamente, as equipes de adoção de nuvem, a equipe de governança de nuvem, a equipe de segurança de ti e a equipe de governança de ti implementarão os requisitos de segurança e governança para permitir que as equipes de adoção da nuvem migrem dados protegidos para a nuvem.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Violação de dados:** Há um aumento inerente nos passivos relacionados a possíveis violações de dados ao adotar qualquer nova plataforma de dados. Os técnicos que adotam as tecnologias de nuvem têm maiores responsabilidades de implementar soluções que possam diminuir esse risco. Uma estratégia de governança e segurança robusta deve ser implementada para garantir que os técnicos cumpram essas responsabilidades.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

1. Aplicativos críticos ou dados protegidos podem ser implantados acidentalmente.
2. Dados protegidos podem ser expostos durante o armazenamento devido a decisões de criptografia ineficientes.
3. Usuários não autorizados podem acessar dados protegidos.
4. Uma invasão externa pode resultar no acesso aos dados protegidos.
5. Uma invasão externa ou ataques de negação de serviço pode causar uma interrupção dos negócios.
6. Alterações de emprego ou da organização podem resultar em acesso não autorizado aos dados protegidos.
7. Novas explorações podem criar oportunidades de invasão ou acesso não autorizado.
8. Os processos de implantação podem resultar em falhas de segurança, o que pode levar a perdas de dados ou interrupções.
9. Desvio de configuração ou patches ausentes pode resultar em falhas de segurança não intencionais, o que pode levar a vazamentos de dados ou interrupções.
10. Dispositivos de borda diferentes podem aumentar os custos das operações de rede.
11. Configurações de dispositivo diferentes podem levar a descuidos na configuração e comprometimentos de segurança.
12. A equipe de segurança cibernética insiste que há um risco de bloqueio de fornecedor gerando chaves de criptografia na plataforma de um único provedor de nuvem. Embora essa afirmação não esteja fundamentada, ela é aceita pela equipe até o momento.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece longa, mas a adoção dessas políticas pode ser mais fácil do que parece.

1. Todos os ativos implantados devem ser categorizados por nível de importância e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo aplicativo antes da implantação na nuvem.
2. Aplicativos que armazenam ou acessam dados protegidos devem ser gerenciados diferentemente daqueles que não são. No mínimo, eles devem ser segmentados para evitar acesso não intencional de dados protegidos.
3. Todos os dados protegidos devem ser criptografados quando estão em repouso.
4. As permissões elevadas em qualquer segmento que contenha dados protegidos devem ser uma exceção. Essas exceções serão registradas com a equipe de governança de nuvem e auditadas regularmente.
5. As sub-redes de rede que contêm dados protegidos devem ser isoladas de todas as outras sub-redes. O tráfego de rede entre as sub-redes de dados protegidos será auditado regularmente.
6. Nenhuma sub-rede que contém os dados protegidos pode ser acessada diretamente pela Internet pública ou em datacenters. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que pode executar a verificação de pacotes e as funções de bloqueio.
7. As ferramentas de governança devem realizar a auditoria e impor requisitos de configuração de rede definidos pela equipe de gerenciamento de segurança.
8. As ferramentas de governança devem limitar a implantação da VM (máquina virtual) apenas às imagens aprovadas.
9. Sempre que possível, o gerenciamento de configuração de nó deverá aplicar os requisitos da política à configuração de qualquer sistema operacional convidado. O gerenciamento de configuração de nó deve respeitar o investimento atual no GPO (Objeto de Política de Grupo) para configuração de recurso.
10. As ferramentas de governança devem impor que as atualizações automáticas sejam habilitadas em todos os ativos implantados. Quando possível, as atualizações automáticas serão impostas. Quando não forem impostas por ferramentas, as violações de nível de nó deverão ser analisadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Ativos que não são atualizados automaticamente devem ser incluídos nos processos pertencentes às Operações de TI.
11. A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos requer uma análise da equipe de governança de nuvem para garantir uma atribuição de diagrama adequada.
12. Um modelo de acesso de privilégios mínimos será aplicado a qualquer assinatura que contenha aplicativos críticos ou dados protegidos.
13. O fornecedor de nuvem deve ser capaz de integrar chaves de criptografia gerenciadas pela solução local atual.
14. O fornecedor de nuvem deve ser capaz de oferecer suporte para a solução de dispositivo de borda atual e todas as configurações necessárias para proteger qualquer limite de rede exposto publicamente.
15. O fornecedor de nuvem deve ser capaz de oferecer suporte a uma conexão compartilhada à WAN global, com a transmissão de dados roteados por meio da solução de dispositivo de borda atual.
16. Tendências e explorações que podem afetar as implantações de nuvem devem ser revisadas regularmente pela equipe de segurança para que sejam fornecidas atualizações às ferramentas de Linha de Base de Segurança usadas na nuvem.
17. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
18. Os scripts de implantação devem ser mantidos em um repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
19. Os processos de governança devem incluir auditorias no momento da implantação e em ciclos regulares para garantir a consistência em todos os ativos.
20. A implantação de qualquer aplicativo que exija a autenticação do cliente deve usar um provedor de identidade aprovado que seja compatível com o provedor de identidade principal para usuários internos.
21. Os processos de Governança de Nuvem devem incluir revisão trimestral com as equipes de Linha de Base de Identidade para identidade atores mal-intencionados ou padrões de uso que devem ser evitados pela configuração de ativos de nuvem.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

As novas práticas recomendadas enquadram-se em duas categorias: TI corporativa (Hub) e adoção de nuvem (spoke).

**Estabelecendo um hub de ti corporativo e uma assinatura do spoke para centralizar a linha de base de segurança:** Nesta prática recomendada, a capacidade de governança existente é encapsulada por uma [topologia de Hub e spoke com serviços compartilhados][shared-services], com algumas adições importantes da equipe de governança de nuvem.

1. Repositório de Azure DevOps. Crie um repositório no Azure DevOps para armazenar e controlar a versão de todos os modelos do Azure Resource Manager relevantes e configurações com script.
1. Modelo de Hub e spoke:
    1. As diretrizes na [topologia hub e spoke com][shared-services] arquitetura de referência de serviços compartilhados podem ser usadas para gerar modelos do Resource Manager para os ativos necessários em um hub de ti corporativo.
    1. Ao usar esses modelos, essa estrutura pode ser feita repetidamente, como parte de uma estratégia de governança central.
    1. Além da arquitetura de referência atual, é recomendável que um modelo de grupo de segurança de rede seja criado, capturando quaisquer requisitos de bloqueio de porta ou de lista de permissões para a VNet para hospedar o firewall. Esse grupo de segurança de rede é diferente dos grupos anteriores, pois será o primeiro grupo de segurança de rede a permitir o tráfego público em uma VNet.
1. Crie políticas do Azure. Crie uma política chamada `Hub NSG Enforcement` para impor a configuração do grupo de segurança de rede atribuído a qualquer VNet criada nesta assinatura. Aplique as Políticas internas para configuração do convidado, conforme a seguir:
    1. Realize uma auditoria para verificar se os servidores Web do Windows estão usando protocolos de comunicação segura.
    1. Realize uma auditoria para verificar se as configurações de segurança de senha estão definidas corretamente em computadores Linux e Windows.
1. Blueprint de TI corporativa
    1. Crie um novo blueprint do Azure nomeado `corporate-it-subscription`.
    1. Adicione os modelos Hub e spoke e `Hub NSG Enforcement` a política.
1. Expandindo na hierarquia do grupo de gerenciamento inicial.
    1. Para cada grupo de gerenciamento que solicitou suporte para dados protegidos, o `corporate-it-subscription-blueprint` blueprint fornece uma solução acelerada de hub.
    1. Como os grupos de gerenciamento neste exemplo fictício incluem uma hierarquia regional, além de uma hierarquia de unidade de negócios, este projeto será implantado em cada região.
    1. Para cada região na hierarquia de grupo de gerenciamento, crie uma assinatura nomeada `Corporate IT Subscription`.
    1. Aplique o `corporate-it-subscription-blueprint` blueprint para cada instância regional.
    1. Isso estabelecerá um hub para cada unidade de negócios em cada região. Observação: É possível obter mais economia de custos, simplesmente compartilhando hubs entre unidades de negócios em cada região.
1. Integre GPO (objetos de política de grupo) por meio de DSC (Desired State Configuration):
    1. Converter o GPO em DSC – o [projeto de gerenciamento de linha de base da Microsoft](https://github.com/Microsoft/BaselineManagement) no GitHub pode acelerar esse esforço. * Certifique-se de armazenar a DSC no repositório em paralelo aos modelos do Resource Manager.
    1. Implante a Configuração de Estado de Automação do Azure nas instâncias da assinatura de TI Corporativa. A Automação do Azure pode ser usada para aplicar a DSC para VMs (máquinas virtuais) implantadas em assinaturas com suporte no grupo de gerenciamento.
    1. O roteiro atual planeja habilitar políticas de configuração de convidado personalizadas. Quando esse recurso for liberado, o uso da Automação do Azure nessa prática recomendada não será mais necessário.

**Aplicando governança adicional a uma assinatura de adoção de nuvem (spoke):** Com base no `Corporate IT Subscription`, pequenas mudanças no MVP de governança aplicadas a cada assinatura dedicada ao suporte de arquétipos de aplicativo podem produzir uma melhoria rápida.

Em alterações iterativas anteriores à prática recomendada, definimos grupos de segurança de rede para bloquear o tráfego público e o tráfego interno na lista de permissões. Além disso, o blueprint do Azure criou temporariamente os recursos da DMZ e do Active Directory. Nessa iteração, iremos ajustar esses ativos um pouco, criando uma nova versão da especificação técnica do Azure.

1. Modelo de emparelhamento de rede. Esse modelo irá emparelhar a VNet em cada assinatura com a VNet de Hub na assinatura de TI Corporativa.
    1. A arquitetura de referência da seção anterior, do [Hub e da topologia do spoke com serviços compartilhados][shared-services], gerou um modelo do Resource Manager para habilitar o emparelhamento VNet.
    1. Esse modelo pode ser usado como um guia para modificar o modelo DMZ da iteração de governança anterior.
    1. Essencialmente, agora estamos adicionando emparelhamento VNet para a VNet de DMZ que foi previamente conectada ao dispositivo de borda local pela VPN (rede virtual privada).
    1. *** Também é recomendável que a VPN seja removida desse modelo para garantir que nenhum tráfego seja roteado diretamente para o datacenter local, sem passar pela assinatura de TI corporativa e pela solução de Firewall.
    1. [Configuração de rede](/azure/automation/automation-dsc-overview#network-planning) adicional será exigida pela Automação do Azure para aplicar a DSC às VMs hospedadas.
1. Modifique o grupo de segurança de rede. Bloquear todo o tráfego local público **e** direto no grupo de segurança de rede. Somente o tráfego de entrada deve ser proveniente do par de VNet na assinatura de TI corporativa.
    1. Na iteração anterior, um grupo de segurança de rede foi criado, bloqueando todo o tráfego público e listando todo o tráfego interno. Agora, queremos mudar um pouco esse grupo de segurança de rede.
    1. A nova configuração de grupo de segurança de rede deve bloquear todo o tráfego público, juntamente com todo o tráfego do datacenter local.
    1. O tráfego entrando nessa VNet deve ser proveniente somente da VNet no outro lado do par de VNet.
1. Implementação da Central de Segurança do Azure:
    1. Configure a Central de Segurança do Azure para qualquer grupo de gerenciamento que contenha classificações de dados protegidos.
    1. Defina o provisionamento Automático para ativado por padrão para garantir a conformidade da aplicação de patch.
    1. Estabeleça configurações de segurança do sistema operacional Segurança de TI para definir a configuração.
    1. Suporte à Segurança de TI no uso inicial da Central de Segurança do Azure. Fazer a transição do uso da central de segurança para a segurança de ti, mas manter o acesso para fins de aperfeiçoamento contínuo de governança.
    1. Crie um modelo do Resource Manager que reflita as alterações necessárias para a configuração da Central de Segurança do Azure em uma assinatura.
1. Atualizar o Azure Policy para todas as assinaturas.
    1. Realize uma auditoria e imponha a criticidade e a classificação de dados em todos os grupos e assinaturas de gerenciamento para identificar quaisquer assinaturas com classificações de dados protegidas.
    1. Realize uma auditoria e imponha o uso apenas de imagens aprovadas do sistema operacional.
    1. Realize uma auditoria e imponha as configurações de convidado com base nos requisitos de segurança para cada nó.
1. Atualize o Azure Policy para todas as assinaturas que contenham classificações de dados protegidos.
    1. Realize uma auditoria e imponha apenas o uso de funções padrão
    1. Realize uma auditoria e imponha o aplicativo de criptografia para todas as contas de armazenamento e arquivos em repouso nos nós individuais.
    1. Auditar e impor o aplicativo da nova versão do grupo de segurança de rede DMZ.
    1. Realize uma auditoria e imponha o uso de uma sub-rede de rede aprovada e VNet por adaptador de rede
    1. Realize uma auditoria e imponha a limitação das tabelas de roteamento definidas pelo usuário.
1. Blueprint do Azure:
    1. Crie um novo blueprint do Azure nomeado `protected-data`.
    1. Adicione os modelos de par VNet, grupo de segurança de rede e central de segurança do Azure ao plano gráfico.
    1. Verifique se o modelo para Active Directory da iteração anterior **não** está incluído no plano gráfico. Todas as dependências do Active Directory serão fornecidas pela assinatura de TI corporativa.
    1. Encerre todas as VMs Active Directory existentes implantadas na iteração anterior.
    1. Adicione as novas políticas para assinaturas de dados protegidos.
    1. Publique o blueprint em qualquer grupo de gerenciamento destinado a hospedar dados protegidos.
    1. Aplique o novo blueprint a cada assinatura afetada junto com blueprints atuais.

## <a name="conclusion"></a>Conclusão

Adicionar esses processos e alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados à governança de segurança. Em conjunto, eles adicionam ferramentas de monitoramento de segurança, identidade e rede necessárias para proteger os dados.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também mudam. Para a empresa fictícia neste guia, a próxima etapa é oferecer suporte a cargas de trabalho de missão crítica. Essa é a situação em que os controles de Consistência de Recursos são necessários.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de consistência do recurso](./resource-consistency-evolution.md)

<!-- links -->

[shared-services]: https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services
