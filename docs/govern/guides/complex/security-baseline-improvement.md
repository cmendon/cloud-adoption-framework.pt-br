---
title: 'Guia de governança para empresas complexas: melhorar a disciplina de linha de base de segurança'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: melhorar a disciplina de linha de base de segurança'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2e2e075b6f051af003d4c8d542e592943084c1e7
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547615"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-security-baseline-discipline"></a>Guia de governança para empresas complexas: melhorar a disciplina de linha de base de segurança

Este artigo avança na narração adicionando controles de segurança que dão suporte à movimentação de dados protegidos para a nuvem.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

O CIO passou meses colaborando com colegas e com a equipe legal da empresa. Um consultor de gerenciamento com experiência no segurança cibernética foi envolvido para ajudar a segurança de ti existente e as equipes de governança de ti a rascunhar uma nova política em relação aos dados protegidos. O grupo foi capaz de estimular o suporte a placas para substituir a política existente, permitindo que dados confidenciais pessoais e financeiros sejam hospedados por provedores de nuvem aprovados. Isso exigiu a adoção de um conjunto de requisitos de segurança e um processo de governança para verificar e documentar a adesão a essas políticas.

Nos últimos 12 meses, as equipes de adoção de nuvem removeram a maioria dos ativos 5.000 dos dois data centers a serem desativados. Os 350 ativos incompatíveis foram movidos para um datacenter alternativo. Somente as máquinas virtuais 1.250 que contêm dados protegidos permanecem.

### <a name="changes-in-the-cloud-governance-team"></a>Alterações na equipe de governança de nuvem

A equipe de governança de nuvem continua a mudar junto com a narração. Os dois membros encontrados da equipe agora estão entre os arquitetos de nuvem mais respeitados na empresa. A coleção de scripts de configuração cresceu conforme novas equipes lidam com novas implantações inovadoras. A equipe de governança de nuvem também cresceu. Mais recentemente, os membros da equipe de operações de ti uniram as atividades da equipe de governança de nuvem para se preparar para operações de nuvem. Os arquitetos de nuvem que ajudaram a promover essa comunidade são vistos como guardiões de nuvem e aceleradores de nuvem.

Embora a diferença seja sutil, é uma distinção importante ao criar uma cultura de ti focada em governança. Um dos responsáveis pela nuvem limpa as bagunças feitas pelos arquitetos de nuvem inovadores, e as duas funções têm objetivos naturais e opostos. Um guardião de nuvem ajuda a manter a nuvem segura, de modo que outros arquitetos de nuvem podem se mover mais rapidamente com menos confusão. Um acelerador de nuvem executa ambas as funções, mas também está envolvida na criação de modelos para acelerar a implantação e a adoção, tornando-se um acelerador de inovação, bem como um defender das cinco disciplinas de governança de nuvem.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desta narração, a empresa começou o processo de desativação de dois data centers. Esse esforço contínuo inclui a migração de alguns aplicativos com requisitos de autenticação herdados, que exigiam melhorias incrementais na linha de base de identidade, descritas no [artigo anterior](./identity-baseline-improvement.md).

Desde então, algumas coisas mudaram que afetarão a governança:

- Milhares de ativos de ti e de negócios foram implantados na nuvem.
- A equipe de desenvolvimento de aplicativos implementou um pipeline de CI/CD (integração contínua e implantação contínua) para implantar um aplicativo nativo de nuvem com uma experiência de usuário aprimorada. Esse aplicativo ainda não interage com dados protegidos, portanto, não está pronto para produção.
- A equipe de Business Intelligence dentro dela organizada ativamente os dados na nuvem de logística, inventário e dados de terceiros. Esses dados estão sendo usados para gerar novas previsões, que podem moldar os processos de negócios. No entanto, essas previsões e ideias não são acionáveis até que os dados de clientes e financeiros possam ser integrados à plataforma de dados.
- A equipe de ti está progredindo com os planos do CIO e do CFO para desativar dois data centers. Quase 3.500 dos ativos nos dois data centers foram desativados ou migrados.
- As políticas relativas a dados confidenciais pessoais e financeiros foram modernizadas. No entanto, as novas políticas corporativas são contingentes com a implementação de políticas relacionadas de segurança e governança. As equipes ainda estão paralisadas.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

- Os experimentos iniciais do desenvolvimento de aplicativos e das equipes de BI mostraram possíveis aprimoramentos nas experiências do cliente e decisões controladas por dados. Ambas as equipes gostariam de expandir a adoção da nuvem nos próximos 18 meses, implantando essas soluções em produção.
- Ele desenvolveu uma justificativa de negócios para migrar mais cinco data centers para o Azure, o que reduzirá ainda mais os custos de ti e proporcionará maior agilidade nos negócios. Embora seja menor em escala, a desativação desses data centers deve dobrar a economia de custo total.
- Despesas de capital e orçamentos de despesas operacionais foram aprovados para implementar as políticas, as ferramentas e os processos necessários de segurança e governança. A economia de custos esperada da aposentadoria do datacenter é mais do que suficiente para pagar por essa nova iniciativa. A liderança de ti e de negócios está confiante de que esse investimento acelerará a realização de Devoluções em outras áreas. A equipe de governança de nuvem todas tornou-se uma equipe reconhecida com liderança e pessoal dedicados.
- Coletivamente, as equipes de adoção de nuvem, a equipe de governança de nuvem, a equipe de segurança de ti e a equipe de governança de ti implementarão os requisitos de segurança e governança para permitir que as equipes de adoção da nuvem migrem dados protegidos para a nuvem.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Violação de dados:** Há um aumento inerente em passivos relacionados a violações de dados ao adotar qualquer nova plataforma de dados. Os técnicos que adotam tecnologias de nuvem têm maior responsabilidades para implementar soluções que podem diminuir esse risco. Uma estratégia robusta de segurança e governança deve ser implementada para garantir que esses técnicos atendam a essas responsabilidades.

Esse risco comercial pode ser expandido em vários riscos técnicos:

1. Aplicativos de missão crítica ou dados protegidos podem ser implantados involuntariamente.
2. Os dados protegidos podem ser expostos durante o armazenamento devido a decisões de criptografia insatisfatórias.
3. Usuários não autorizados podem acessar dados protegidos.
4. A intrusão externa pode resultar em acesso a dados protegidos.
5. A invasão externa ou ataques de negação de serviço podem causar uma interrupção nos negócios.
6. Alterações de organização ou de emprego podem permitir o acesso não autorizado a dados protegidos.
7. Novas explorações podem criar oportunidades de intrusão ou acesso não autorizado.
8. Processos de implantação inconsistentes podem resultar em lacunas de segurança que podem levar a vazamentos de dados ou interrupções.
9. A descompasso de configuração ou patches perdidos podem resultar em lacunas de segurança indesejadas que podem levar a vazamentos de dados ou interrupções.
10. Dispositivos de borda diferentes podem aumentar os custos de operações de rede.
11. Configurações de dispositivo diferentes podem levar a insights na configuração e comprometimentos na segurança.
12. A equipe segurança cibernética insiste que há um risco de que o bloqueio do fornecedor gere chaves de criptografia em uma plataforma de único provedor de nuvem. Embora essa declaração não seja constatada, ela foi aceita pela equipe pelo tempo.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece muito longa, mas a adoção dessas políticas pode ser mais fácil do que seria exibida.

1. Todos os ativos implantados devem ser categorizados por criticalidade e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo aplicativo antes da implantação na nuvem.
2. Os aplicativos que armazenam ou acessam dados protegidos devem ser gerenciados de forma diferente daqueles que não o fazem. No mínimo, eles devem ser segmentados para evitar o acesso não intencional de dados protegidos.
3. Todos os dados protegidos devem ser criptografados quando em repouso.
4. Permissões elevadas em qualquer segmento que contém dados protegidos devem ser uma exceção. Essas exceções serão registradas com a equipe de governança de nuvem e auditadas regularmente.
5. As sub-redes de rede que contêm dados protegidos devem ser isoladas de quaisquer outras sub-redes. O tráfego de rede entre sub-redes de dados protegidos será auditado regularmente.
6. Nenhuma sub-rede contendo dados protegidos pode ser acessada diretamente pela Internet pública ou por data centers. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que pode executar a verificação de pacotes e as funções de bloqueio.
7. As ferramentas de governança devem auditar e aplicar os requisitos de configuração de rede definidos pela equipe de gerenciamento de segurança.
8. As ferramentas de governança devem limitar a implantação de VM somente a imagens aprovadas.
9. Sempre que possível, o gerenciamento de configuração de nó deve aplicar requisitos de política à configuração de qualquer sistema operacional convidado. O gerenciamento de configuração de nó deve respeitar o investimento existente no objeto de Política de Grupo (GPO) para a configuração de recurso.
10. As ferramentas de governança irão auditar se as atualizações automáticas estão habilitadas em todos os ativos implantados. Quando possível, as atualizações automáticas serão impostas. Quando não são impostas por ferramentas, as violações no nível de nó devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Os ativos que não são atualizados automaticamente devem ser incluídos em processos de propriedade de operações de ti.
11. A criação de novas assinaturas ou grupos de gerenciamento para qualquer aplicativo de missão crítica ou dados protegidos requer uma análise da equipe de governança de nuvem para garantir uma atribuição de diagrama adequada.
12. Um modelo de acesso com privilégios mínimos será aplicado a qualquer assinatura que contenha aplicativos de missão crítica ou dados protegidos.
13. O fornecedor de nuvem deve ser capaz de integrar chaves de criptografia gerenciadas pela solução local existente.
14. O fornecedor de nuvem deve ser capaz de dar suporte à solução de dispositivo de borda existente e a qualquer configuração necessária para proteger qualquer limite de rede exposto publicamente.
15. O fornecedor de nuvem deve ser capaz de dar suporte a uma conexão compartilhada com a WAN global, com a transmissão de dados roteada por meio da solução de dispositivo de borda existente.
16. As tendências e explorações que poderiam afetar as implantações na nuvem devem ser examinadas regularmente pela equipe de segurança para fornecer atualizações para as ferramentas de linha de base de segurança usadas na nuvem.
17. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
18. Os scripts de implantação devem ser mantidos em um repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
19. Os processos de governança devem incluir auditorias no ponto de implantação e em ciclos regulares para garantir a consistência em todos os ativos.
20. A implantação de qualquer aplicativo que exija autenticação do cliente deve usar um provedor de identidade aprovado que seja compatível com o provedor de identidade principal para usuários internos.
21. Os processos de governança de nuvem devem incluir revisões trimestrais com equipes de linha de base de identidade para identificar atores mal-intencionados ou padrões de uso que devem ser impedidos pela configuração de ativos de nuvem.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas duas alterações de design atenderão às novas instruções de política corporativa.

As novas práticas recomendadas se enquadram em duas categorias: ti corporativa (Hub) e adoção de nuvem (spoke).

**Estabelecendo um hub de ti corporativo e uma assinatura do spoke para centralizar a linha de base de segurança:** Nesta prática recomendada, a capacidade de governança existente é encapsulada por uma [topologia de Hub e spoke com serviços compartilhados](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services), com algumas adições importantes da equipe de governança de nuvem.

1. Repositório DevOps do Azure. Crie um repositório no Azure DevOps para armazenar e versão todos os modelos de Azure Resource Manager relevantes e configurações com script.
2. Modelo de Hub e spoke:
    1. As diretrizes na [topologia hub e spoke com](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services) arquitetura de referência de serviços compartilhados podem ser usadas para gerar modelos do Resource Manager para os ativos necessários em um hub de ti corporativo.
    2. Usando esses modelos, essa estrutura pode se tornar repetível, como parte de uma estratégia de governança central.
    3. Além da arquitetura de referência atual, é recomendável que um modelo de grupo de segurança de rede seja criado, capturando quaisquer requisitos de bloqueio de porta ou de lista de permissões para a VNet para hospedar o firewall. Esse grupo de segurança de rede é diferente dos grupos anteriores, pois será o primeiro grupo de segurança de rede a permitir o tráfego público em uma VNet.
3. Criar políticas do Azure. Crie uma política chamada `Hub NSG Enforcement` para impor a configuração do grupo de segurança de rede atribuído a qualquer VNet criada nesta assinatura. Aplique as políticas internas para a configuração de convidado da seguinte maneira:
    1. Auditar que os servidores Web do Windows estão usando protocolos de comunicação seguros.
    2. Auditar que as configurações de segurança de senha estão definidas corretamente dentro de computadores Linux e Windows.
4. Plano gráfico de ti corporativo
    1. Crie uma especificação técnica do Azure chamada `corporate-it-subscription`.
    2. Adicione os modelos Hub e spoke e a política de `Hub NSG Enforcement`.
5. Expandindo na hierarquia inicial do grupo de gerenciamento.
    1. Para cada grupo de gerenciamento que solicitou suporte para dados protegidos, o plano gráfico `corporate-it-subscription-blueprint` fornece uma solução de Hub acelerada.
    2. Como os grupos de gerenciamento neste exemplo fictício incluem uma hierarquia regional além de uma hierarquia de unidade de negócios, este projeto será implantado em cada região.
    3. Para cada região na hierarquia do grupo de gerenciamento, crie uma assinatura chamada `Corporate IT Subscription`.
    4. Aplique o `corporate-it-subscription-blueprint` Blueprint a cada instância regional.
    5. Isso estabelecerá um hub para cada unidade de negócios em cada região. Observação: podem ser obtidas mais economias de custos, mas o compartilhamento de hubs entre unidades de negócios em cada região.
6. Integre GPOs (objetos de diretiva de grupo) por meio da configuração de estado desejado (DSC):
    1. Converter o GPO em DSC – o [projeto de gerenciamento de linha de base da Microsoft](https://github.com/Microsoft/BaselineManagement) no GitHub pode acelerar esse esforço. * Certifique-se de armazenar o DSC no repositório em paralelo com modelos do Resource Manager.
    2. Implante a configuração de estado da automação do Azure em qualquer instância da assinatura de ti corporativa. A automação do Azure pode ser usada para aplicar a DSC às VMs implantadas em assinaturas com suporte no grupo de gerenciamento.
    3. O roteiro atual planeja habilitar políticas de configuração de convidado personalizadas. Quando esse recurso for lançado, o uso da automação do Azure nesta prática recomendada não será mais necessário.

**Aplicando governança adicional a uma assinatura de adoção de nuvem (spoke):** Com base no `Corporate IT Subscription`, pequenas mudanças no MVP de governança aplicadas a cada assinatura dedicada ao suporte de arquétipos de aplicativo podem produzir um aperfeiçoamento rápido.

Em alterações iterativas anteriores à prática recomendada, definimos grupos de segurança de rede para bloquear o tráfego público e o tráfego interno na lista de permissões. Além disso, a planta técnica do Azure criou temporariamente os recursos de DMZ e Active Directory. Nessa iteração, iremos ajustar esses ativos um pouco, criando uma nova versão da especificação técnica do Azure.

1. Modelo de emparelhamento de rede. Esse modelo emparelhará a VNet em cada assinatura com a VNet do Hub na assinatura de ti corporativa.
    1. A arquitetura de referência da seção anterior, do [Hub e da topologia do spoke com serviços compartilhados](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/shared-services), gerou um modelo do Resource Manager para habilitar o emparelhamento VNet.
    2. Esse modelo pode ser usado como um guia para modificar o modelo DMZ da iteração de governança anterior.
    3. Agora estamos adicionando o emparelhamento VNet à VNet da DMZ que foi conectada anteriormente ao dispositivo de borda local pela VPN.
    4. Também é recomendável que a VPN seja removida desse modelo também para garantir que nenhum tráfego seja roteado diretamente para o datacenter local, sem passar pela solução de firewall e assinatura de ti corporativa. Você também pode definir essa VPN como um circuito de failover no caso de um circuito de ExpressRoute outge.
    5. A [configuração de rede](https://docs.microsoft.com/azure/automation/automation-dsc-overview#network-planning) adicional será exigida pela automação do Azure para aplicar a DSC às VMs hospedadas.
2. Modifique o grupo de segurança de rede. Bloquear todo o tráfego local público **e** direto no grupo de segurança de rede. O único tráfego de entrada deve ser proveniente do par VNet na assinatura de ti corporativa.
    1. Na iteração anterior, um grupo de segurança de rede foi criado, bloqueando todo o tráfego público e listando todo o tráfego interno. Agora, queremos mudar um pouco esse grupo de segurança de rede.
    2. A nova configuração de grupo de segurança de rede deve bloquear todo o tráfego público, juntamente com todo o tráfego do datacenter local.
    3. O tráfego que entra nessa VNet só deve vir da VNet no outro lado do par VNet.
3. Implementação da central de segurança do Azure:
    1. Configure a central de segurança do Azure para qualquer grupo de gerenciamento que contenha classificações de dados protegidas.
    2. Defina o provisionamento automático como ativado por padrão para garantir a conformidade da aplicação de patch.
    3. Estabeleça configurações de segurança do sistema operacional. Segurança de ti para definir a configuração.
    4. Dê suporte à segurança de ti no uso inicial da central de segurança do Azure. Fazer a transição do uso da central de segurança para a segurança de ti, mas manter o acesso para fins de aperfeiçoamento contínuo de governança.
    5. Crie um modelo do Resource Manager que reflete as alterações necessárias para a configuração da central de segurança do Azure em uma assinatura.
4. Atualize Azure Policy para todas as assinaturas.
    1. Auditar e impor a criticalidade e a classificação de dados em todos os grupos de gerenciamento e assinaturas para identificar assinaturas com classificações de dados protegidas.
    2. Auditar e impor o uso apenas de imagens de sistema operacional aprovadas.
    3. Auditar e impor configurações de convidado com base nos requisitos de segurança para cada nó.
5. Atualize Azure Policy para todas as assinaturas que contêm classificações de dados protegidas.
    1. Auditar e impor o uso somente de funções padrão
    2. Auditar e aplicar a aplicação de criptografia para todas as contas de armazenamento e arquivos em repouso em nós individuais.
    3. Auditar e impor o aplicativo da nova versão do grupo de segurança de rede DMZ.
    4. Auditar e impor o uso de sub-rede de rede aprovada e VNet por interface de rede.
    5. Auditar e impor a limitação de tabelas de roteamento definidas pelo usuário.
6. Especificações técnicas do Azure:
    1. Crie uma especificação técnica do Azure chamada `protected-data`.
    2. Adicione os modelos de par VNet, grupo de segurança de rede e central de segurança do Azure ao plano gráfico.
    3. Verifique se o modelo para Active Directory da iteração anterior **não** está incluído no plano gráfico. Todas as dependências em Active Directory serão fornecidas pela assinatura corporativa de ti.
    4. Encerre todas as VMs Active Directory existentes implantadas na iteração anterior.
    5. Adicione as novas políticas para assinaturas de dados protegidos.
    6. Publique o Blueprint em qualquer grupo de gerenciamento que hospedará dados protegidos.
    7. Aplique o novo Blueprint a cada assinatura afetada junto com os planos gráficos existentes.

## <a name="conclusion"></a>Conclusão

Adicionar esses processos e alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados à governança de segurança. Juntos, eles adicionam as ferramentas de rede, identidade e monitoramento de segurança necessárias para proteger os dados.

## <a name="next-steps"></a>Próximos passos

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também mudam. Para a empresa fictícia neste guia, a próxima etapa é oferecer suporte a cargas de trabalho de missão crítica. Esse é o ponto quando os controles de consistência de recursos são necessários.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de consistência do recurso](./resource-consistency-improvement.md)
