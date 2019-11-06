---
title: Melhores práticas para proteger e gerenciar cargas de trabalho migradas para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Depois de migrar para o Azure, obtenha as melhores práticas para operar, gerenciar e proteger as cargas de trabalho migradas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 34659cb5cd3a223fe084ba8975f0f7a39b2b74f6
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656703"
---
# <a name="best-practices-for-securing-and-managing-workloads-migrated-to-azure"></a>Melhores práticas para proteger e gerenciar cargas de trabalho migradas para o Azure

À medida que você planeja e projeta a migração, além de pensar sobre a migração em si, é necessário considerar seu modelo de segurança e gerenciamento no Azure após a migração. Este artigo descreve o planejamento e as melhores práticas para proteger a implantação do Azure após a migração e manter a implantação em execução em um nível ideal para tarefas em andamento.

> [!IMPORTANT]
> As melhores práticas e as opiniões descritas neste artigo baseiam-se na plataforma Azure e nos recursos do serviço disponíveis no momento em que o artigo foi escrito. Os recursos e as funcionalidades mudam ao longo do tempo.

## <a name="secure-migrated-workloads"></a>Proteger cargas de trabalho migradas

Após a migração, a tarefa mais importante é proteger cargas de trabalho migradas de ameaças internas e externas. Estas melhores práticas ajudam você a:

- [Trabalhar com a central de segurança do Azure](#best-practice-follow-azure-security-center-recommendations): saiba como trabalhar com o monitoramento, as avaliações e as recomendações fornecidas pela central de segurança do Azure.
- [Criptografar seus dados](#best-practice-encrypt-data): Obtenha as práticas recomendadas para criptografar seus dados no Azure.
- [Configure o antimalware](#best-practice-protect-vms-with-antimalware): Proteja suas VMs contra malware e ataques mal-intencionados.
- [Proteger aplicativos Web](#best-practice-secure-web-apps): manter informações confidenciais seguras em aplicativos Web migrados.
- [Examinar assinaturas](#best-practice-review-subscriptions-and-resource-permissions): Verifique quem pode acessar suas assinaturas e recursos do Azure após a migração.
- [Trabalhar com logs](#best-practice-review-audit-and-security-logs): revise os logs de segurança e auditoria do Azure regularmente.
- [Examine outros recursos de segurança](#best-practice-evaluate-other-security-features): entenda e avalie os recursos de segurança avançados que o Azure oferece.

## <a name="best-practice-follow-azure-security-center-recommendations"></a>Prática recomendada: siga as recomendações da central de segurança do Azure

A Microsoft trabalha duro para fazer com que os administradores de locatários do Azure tenham as informações necessárias para habilitar os recursos de segurança que protegem suas cargas de trabalho contra ataques. A Central de Segurança do Azure fornece gerenciamento unificado de segurança. Na Central de Segurança, você pode aplicar políticas de segurança em cargas de trabalho, limitar a exposição a riscos e detectar e responder a ataques. A Central de Segurança analisa as configurações e os recursos entre locatários do Azure e faz recomendações de segurança, incluindo:

- **Gerenciamento de política centralizado** – garanta a conformidade com requisitos de segurança da empresa ou de regulamentação, gerenciando políticas de segurança de forma centralizada em todas as suas cargas de trabalho de nuvem híbrida.
- **Avaliação de segurança contínua** – monitore a postura de segurança de computadores, redes, armazenamento e serviços de dados e aplicativos para descobrir problemas potenciais de segurança.
- **Recomendações acionáveis** – corrija a vulnerabilidades de segurança antes que elas sejam exploradas por invasores, usando recomendações de segurança priorizadas e práticas.
- **Alertas e incidentes priorizados** – concentre-se primeiro nas ameaças mais importantes com alertas de segurança e incidentes priorizados.

Além de avaliações e recomendações, a Central de Segurança do Azure fornece outros recursos de segurança que podem ser habilitados para recursos específicos.

- **Acesso JIT (Just-In-Time).** reduza a superfície de ataque da rede com o acesso Just-In-Time e controlado às portas de gerenciamento em VMs do Azure.
  - Ter a porta RDP 3389 da VM aberta na Internet expõe VMs a atividades contínuas de atores mal-intencionados. Os endereços IP do Azure são conhecidos e os hackers os investigam continuamente para atacar portas 3389 abertas.
  - O Just-In-Time usa NSGs (grupos de segurança de rede) e regras de entrada que limitam a quantidade de tempo que uma porta específica fica aberta.
  - Com o Just-In-Time habilitado, a Central de Segurança verifica se um usuário tem permissões de acesso de gravação RBAC (controle de acesso baseado em função) para uma VM. Além disso, ela especifica regras sobre como os usuários podem se conectar às VMs. Se as permissões estiverem corretas, uma solicitação de acesso será aprovada e a Central de Segurança configurará NSGs, a fim de permitir tráfego de entrada para as portas selecionadas pelo período de tempo especificado. Os NSGs retornam ao estado anterior quando o tempo expira.
- **Controles de aplicativos adaptáveis.** Mantenha software e malware fora das VMs, controlando quais aplicativos são executados nesses computadores por meio de uma lista de permissões dinâmica.
  - Os controles de aplicativo adaptáveis permitem que você aprove os aplicativos e impeça que usuários ou administradores não autorizados instalem aplicativos de software de habilitação ou não aprovados em suas VMs.
    - Você pode bloquear ou criar alertas para tentativas de execução de aplicativos mal-intencionados, evitar aplicativos mal-intencionados ou indesejados e garantir a conformidade com a política de segurança de aplicativo de sua organização.
- **Monitoramento de integridade do arquivo.** garanta a integridade dos arquivos em execução nas VMs.
  - Você não precisa instalar o software para causar problemas de VM. A alteração de um arquivo do sistema também pode causar degradação de desempenho ou falha da VM. O Monitoramento de Integridade de Arquivo verifica alterações nos arquivos de sistema e nas configurações de registro e notifica você quando algo é atualizado.
  - A Central de Segurança recomenda os arquivos que você deve monitorar.

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-intro) sobre a Central de Segurança do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-just-in-time) sobre acesso à VM Just-In-Time.
- [Saiba mais sobre](https://docs.microsoft.com/azure/security-center/security-center-adaptive-application) como aplicar controles de aplicativo adaptáveis.
- [Introdução](https://docs.microsoft.com/azure/security-center/security-center-file-integrity-monitoring) ao Monitoramento de Integridade de Arquivo.

## <a name="best-practice-encrypt-data"></a>Prática recomendada: criptografar dados

A criptografia é uma parte importante das práticas de segurança do Azure. Habilitar a criptografia em todos os níveis ajuda a evitar que partes não autorizadas obtenham acesso a dados confidenciais, incluindo dados em trânsito e em repouso.

### <a name="encryption-for-iaas"></a>Criptografia para IaaS

- **Máquinas virtuais:** Para VMs, você pode usar Azure Disk Encryption para criptografar seus discos de VM IaaS Windows e Linux.
  - A criptografia de disco usa o BitLocker para Windows e o DM-Crypt para Linux a fim de fornecer criptografia do volume para o SO e os discos de dados.
  - Você pode usar uma chave de criptografia criada pelo Azure ou fornecer suas próprias chaves de criptografia guardadas no Azure Key Vault.
  - Com a Criptografia de Disco, os dados da VM IaaS são protegidos em repouso (no disco) e durante a inicialização da VM.
    - A Central de Segurança do Azure alertará você se tiver VMs não criptografadas.
- **Armazenamento:** Proteger dados em repouso armazenados no armazenamento do Azure.
  - Dados armazenados nas contas de armazenamento do Azure podem ser criptografados usando chaves AES geradas pela Microsoft que tenham a certificação FIPS 140-2, ou então, você pode usar suas próprias chaves.
  - A Criptografia do Serviço de Armazenamento está habilitada para todas as contas de armazenamento novas e existentes e não pode ser desabilitada.

### <a name="encryption-for-paas"></a>Criptografia para PaaS

Ao contrário do IaaS, na qual você gerencia suas próprias VMs e infraestrutura, em um modelo de PaaS a plataforma e a infraestrutura são gerenciadas pelo provedor, permitindo que você se concentre na lógica de aplicativo e nas funcionalidades principais. Com tantos tipos de serviços de PaaS diferentes, cada serviço é avaliado individualmente para fins de segurança. Por exemplo, vamos ver como podemos habilitar a criptografia para o Banco de Dados SQL do Azure.

- **Always Encrypted:** Use o assistente de Always Encrypted no SQL Server Management Studio para proteger dados em repouso.
  - Crie a chave Always Encrypted para criptografar dados de colunas individuais.
  - As chaves Always Encrypted podem ser armazenadas em metadados do banco de dados, ou armazenadas em repositórios de chaves confiáveis, como o Azure Key Vault.
  - As alterações no aplicativo provavelmente precisarão usar esse recurso.
- **TDE (Transparent Data Encryption):** Proteja o banco de dados SQL do Azure com criptografia e descriptografia em tempo real do banco de dados, backups associados e arquivos de log de transações em repouso.
  - A TDE permite que as atividades de criptografia ocorram na camada do aplicativo sem alterações.
  - A TDE pode usar chaves de criptografia fornecidas pela Microsoft, ou você pode fornecer suas próprias chaves usando o suporte do Bring Your Own Key.

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-overview) Azure Disk Encryption para VMs IaaS.
- [Habilitar](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-windows) criptografia para VMs IaaS do Windows.
- [Saiba mais](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) sobre a Criptografia do Serviço de Armazenamento do Azure para dados em repouso.
- [Leia](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) uma visão geral do Always Encrypted.
- [Leia sobre](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-azure-sql?view=sql-server-2017) TDE para o Banco de Dados SQL do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql) sobre TDE com Bring Your Own Key.

## <a name="best-practice-protect-vms-with-antimalware"></a>Prática recomendada: proteger VMs com Antimalware

As VMs mais antigas migradas do Azure podem não ter o nível apropriado de antimalware instalado. O Azure fornece uma solução de ponto de extremidade gratuita que ajuda a proteger VMs contra vírus, spyware e outros tipos de malware.

- O Microsoft Antimalware para Azure gera alertas quando software mal-intencionado ou indesejado tenta se instalar na máquina.
- É uma solução de agente único que é executada em segundo plano sem intervenção humana.
- Na Central de Segurança do Azure, você pode identificar facilmente as VMs que não têm a proteção de ponto de extremidade em execução e instalar o Microsoft Antimalware conforme a necessidade.

![Antimalware para VMs](./media/migrate-best-practices-security-management/antimalware.png)
*Antimalware para VMs*

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/security/azure-security-antimalware) sobre o Microsoft Antimalware.

## <a name="best-practice-secure-web-apps"></a>Prática recomendada: proteger aplicativos Web

Os aplicativos Web migrados enfrentam alguns problemas:

- A maioria dos aplicativos Web herdados tendem a ter informações confidenciais nos arquivos de configuração. Os arquivos que contêm essas informações podem apresentar problemas de segurança quando o backup dos aplicativos é feito ou quando o código do aplicativo é inserido no controle do código-fonte ou recuperado dele.
- Além disso, ao migrar aplicativos Web que residem em uma VM, você provavelmente estará movendo essa máquina de uma rede local e de um ambiente protegido por firewall para um ambiente conectado à Internet. Configure uma solução que faça o mesmo trabalho dos recursos de proteção locais.

O Azure fornece algumas soluções:

- **Azure Key Vault:** Hoje, os desenvolvedores de aplicativos Web estão realizando etapas para garantir que as informações confidenciais não sejam vazadas desses arquivos. Um método para proteger as informações é extraí-las dos arquivos e colocá-las em um Azure Key Vault.
  - Você pode usar o Key Vault para centralizar o armazenamento de segredos do aplicativo e controlar sua distribuição. Ele evita a necessidade de armazenar informações de segurança nos arquivos de aplicativo.
  - Os aplicativos podem obter informações de acesso de modo seguro no cofre usando URIs, sem a necessidade de código personalizado.
  - O Azure Key Vault permite que você bloqueie o acesso por meio de controles de segurança do Azure e implemente “chaves de sobreposição” sem interrupção. A Microsoft não vê ou extrai seus dados.
- **Ambiente do serviço de aplicativo:** Se um aplicativo que você migrar precisar de proteção extra, você poderá considerar adicionar um Ambiente do Serviço de Aplicativo e um firewall do aplicativo Web para proteger os recursos do aplicativo.
  - O Ambiente do Serviço de Aplicativo do Azure fornece um ambiente totalmente isolado e dedicado para a execução de aplicativos do Serviço de Aplicativo, por exemplo, aplicativos Web Windows e Linux, contêineres do Docker, aplicativos móveis e funções.
  - É útil para aplicativos com escala muito alta, que exigem isolamento e acesso de rede seguros ou com alta utilização de memória.
- **Firewall do aplicativo Web:** Um recurso do gateway de Aplicativo Azure que fornece proteção centralizada para aplicativos Web.
  - Ele protege aplicativos Web sem a necessidade de modificações no código de back-end.
  - Ele protege vários aplicativos Web ao mesmo tempo por trás de um gateway de aplicativo.
  - Um firewall do aplicativo Web pode ser monitorado com o Azure Monitor e está integrado à Central de Segurança do Azure.

![proteger aplicativos Web](./media/migrate-best-practices-security-management/web-apps.png)

*Cofre da Chave do Azure*

**Saiba mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/key-vault/key-vault-overview) do Azure Key Vault.
- [Saiba mais sobre](https://docs.microsoft.com/azure/application-gateway/waf-overview) o firewall do aplicativo Web.
- [Obtenha uma introdução](https://docs.microsoft.com/azure/app-service/environment/intro) aos Ambientes do Serviço de Aplicativo.
- [Saiba como](https://docs.microsoft.com/azure/key-vault/tutorial-web-application-keyvault) configurar um aplicativo Web para ler segredos do Key Vault.
- [Saiba mais sobre](https://docs.microsoft.com/azure/application-gateway/waf-overview) o firewall do aplicativo Web.

## <a name="best-practice-review-subscriptions-and-resource-permissions"></a>Prática recomendada: examinar as assinaturas e as permissões de recurso

À medida que você migra suas cargas de trabalho e as executa no Azure, as equipes com acesso à carga de trabalho vão mudando. Sua equipe de segurança deve examinar o acesso aos grupos de recursos e de locatário do Azure regularmente. O Azure tem ofertas de gerenciamento de identidade e segurança de controle de acesso, incluindo RBAC (controle de acesso baseado em função), a fim de autorizar permissões para acessar recursos do Azure.

- O RBAC atribui permissões de acesso para entidades de segurança. As entidades de segurança representam usuários, grupos (um conjunto de usuários), entidades de serviço (identidade usada por aplicativos e serviços) e identidades gerenciadas (uma identidade do Azure Active Directory gerenciada automaticamente pelo Azure).
- O RBAC pode atribuir funções a entidades de segurança, como proprietário, colaborador e leitor, e definições de função (uma coleção de permissões) que definem as operações que podem ser executadas pelas funções.
- O RBAC também pode definir escopos que definem o limite de uma função. O escopo pode ser definido em vários níveis, incluindo um grupo de gerenciamento, uma assinatura, um grupo de recursos ou um recurso.
- Garanta que os administradores com acesso do Azure só possam acessar os recursos que você deseja permitir. Se as funções predefinidas no Azure não forem suficientemente granulares, você poderá criar funções personalizadas para separar e limitar as permissões de acesso.

![Controle de acesso](./media/migrate-best-practices-security-management/subscription.png)
*Controle de acesso – IAM*

**Saiba mais:**

- [Sobre](https://docs.microsoft.com/azure/role-based-access-control/overview) RBAC.
- [Aprenda](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) a gerenciar o acesso usando o RBAC e o portal do Azure.
- [Saiba mais sobre](https://docs.microsoft.com/azure/role-based-access-control/custom-roles) funções personalizadas.

## <a name="best-practice-review-audit-and-security-logs"></a>Prática recomendada: examinar logs de auditoria e segurança

O Azure AD (Azure Active Directory) fornece logs de atividade que aparecem no Azure Monitor. Os logs capturam as operações executadas na locação do Azure, onde elas ocorreram e quem as executou.

- Os logs de auditoria mostram o histórico de tarefas no locatário. Os logs de atividade de entrada mostram quem realizou as tarefas.
- O acesso aos relatórios de segurança depende da sua licença do Azure AD. Em gratuito e básico, você obtém uma lista de usuários e entradas arriscados. Nas edições Premium 1 e Premium 2, você obtém informações de evento subjacentes.
- É possível rotear os logs de atividade para vários pontos de extremidade para retenção de longo prazo e insights sobre os dados.
- Torne uma prática comum rever os logs ou integrar sua ferramenta SIEM (gerenciamento de eventos e informações de segurança) para examinar as anomalias automaticamente. Se você não estiver usando Premium 1 ou 2, precisará fazer grande parte da análise por conta própria ou usar o sistema SIEM. A análise inclui a procura por entradas e eventos de risco e outros padrões de ataque de usuários.

![Usuários e Grupos](./media/migrate-best-practices-security-management/azure-ad.png)

*Usuários e grupos do Azure AD*

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor) sobre logs de atividades do Azure AD no Azure Monitor.
- [Saiba como](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs) auditar relatórios de atividade no portal do Azure AD.

## <a name="best-practice-evaluate-other-security-features"></a>Prática recomendada: avaliar outros recursos de segurança

O Azure oferece outros recursos de segurança que fornecem opções avançadas de segurança. Algumas dessas melhores práticas exigem licenças complementares e opções premium.

- **Implementar AUs (unidades administrativas) do Azure AD.** a delegação de tarefas administrativas para a equipe de suporte pode ser difícil com apenas o controle de acesso do Azure básico. Dar acesso à equipe de suporte para administrar todos os grupos no Azure AD pode não ser a abordagem ideal para a segurança da organização. O uso de AUs permite separar recursos do Azure em contêineres de maneira semelhante às UOs (unidades organizacionais ) locais. Para usar a AU, o administrador da AU deve ter uma licença do Azure AD premium. [Saiba mais](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-administrative-units).
- **Usar a autenticação multifator.** Se você tiver uma licença do Azure AD premium, poderá habilitar e impor a autenticação multifator em suas contas de administrador. O phishing é a maneira mais comum de comprometer as credenciais de conta. Quando um ator mal-intencionado obtém credenciais de conta do administrador, é impossível impedi-lo de realizar ações com graves consequências, como excluir todos os grupos de recursos. Você pode estabelecer a autenticação multifator de várias maneiras, inclusive com email, um aplicativo autenticador e mensagens de SMS. Como administrador, você pode selecionar a opção menos intrusiva. A autenticação multifator integra-se às políticas de acesso condicional e à análise de ameaças para exigir aleatoriamente uma resposta ao desafio de autenticação multifator. Saiba mais sobre as [diretrizes de segurança](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices) e [como configurar a autenticação multifator](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices).
- **Implementar acesso condicional.** na maioria das organizações de pequeno e médio porte, os administradores do Azure e a equipe de suporte provavelmente estão localizados em uma mesma área geográfica. Nesse caso, a maioria dos logons virão das mesmas áreas. Se os endereços IP desses locais são razoavelmente estáticos, faz sentido que você não consiga ver logons de administrador fora dessas áreas. Mesmo em uma situação em que um ator mal-intencionado remoto tenha comprometido credenciais de administrador, você poderá implementar recursos de segurança, como acesso condicional, combinados com autenticação multifator para impedir o logon de locais remotos ou locais falsificados de endereços IP aleatórios. [Saiba mais](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) sobre o acesso condicional e [reveja as melhores práticas](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices) para acesso condicional no Azure AD.
- **Rever permissões de aplicativo empresarial.** Ao longo do tempo, os administradores selecionam links da Microsoft e de terceiros sem saber seu impacto na organização. Os links podem apresentar telas de consentimento que atribuem permissões aos aplicativos do Azure e podem permitir acesso de leitura de dados do Azure AD, ou mesmo acesso completo para gerenciar sua assinatura inteira do Azure. Você deve examinar os aplicativos aos quais seus administradores e usuários deram permissão para acessar recursos do Azure regularmente. Verifique se esses aplicativos têm somente as permissões necessárias. Além disso, a cada trimestre ou semestre, você pode enviar um email para os usuários com um link para as páginas de aplicativo, informando a quais aplicativos eles concederam acesso aos dados organizacionais. [Saiba mais](https://docs.microsoft.com/azure/active-directory/manage-apps/application-types) sobre os tipos de aplicativo e [como controlar](https://docs.microsoft.com/azure/active-directory/manage-apps/remove-user-or-group-access-portal) as atribuições de aplicativo no Azure AD.

## <a name="managed-migrated-workloads"></a>Cargas de trabalho migradas gerenciadas

Nesta seção, recomendaremos algumas melhores práticas para gerenciamento do Azure, incluindo:

- [Gerenciar recursos](#best-practice-name-resource-groups): práticas recomendadas para recursos e grupos de recursos do Azure, incluindo nomes inteligentes, prevenção de exclusão acidental, gerenciamento de permissões de recursos e marcação de recursos eficaz.
- [Use plantas](#best-practice-implement-blueprints): Obtenha uma visão geral rápida sobre o uso de plantas para criar e gerenciar seus ambientes de implantação.
- [Revisar arquiteturas](#best-practice-review-azure-reference-architectures): examine as arquiteturas de exemplo do Azure para aprender com a criação de suas implantações após a migração.
- [Configurar grupos de gerenciamento](#best-practice-manage-resources-with-azure-management-groups): se você tiver várias assinaturas, poderá reuni-las em grupos de gerenciamento e aplicar as configurações de governança a esses grupos.
- [Configurar políticas de acesso](#best-practice-deploy-azure-policy): aplique políticas de conformidade aos recursos do Azure.
- [Implemente uma estratégia de BCDR](#best-practice-implement-a-bcdr-strategy): Reúna uma estratégia de BCDR (continuidade dos negócios e recuperação de desastre) para manter os dados seguros, o seu ambiente resiliente e os recursos em funcionamento quando ocorrerem interrupções.
- [Gerenciar VMs](#best-practice-use-managed-disks-and-availability-sets): agrupe VMs em grupos de disponibilidade para resiliência e alta disponibilidade. Use discos gerenciados para facilitar o gerenciamento de armazenamentos e discos de VM.
- [Monitorar o uso de recursos](#best-practice-monitor-resource-usage-and-performance): habilite o log de diagnóstico para recursos do Azure, crie alertas e guias estratégicos para solução de problemas proativas e use o painel do Azure para uma exibição unificada de sua integridade e status de implantação.
- [Gerenciar suporte e atualizações](#best-practice-manage-updates): entenda seu plano de suporte do Azure e como implementá-lo, obtenha as práticas recomendadas para manter as VMs atualizadas e colocar os processos em vigor para o gerenciamento de alterações.

## <a name="best-practice-name-resource-groups"></a>Prática recomendada: nomear grupos de recursos

Ter grupos de recursos com nomes significativos que os administradores e os membros da equipe de suporte possam reconhecer e navegar melhorará drasticamente a produtividade e a eficiência.

- Recomendamos seguir as convenções de nomenclatura do Azure.
- Se você estiver sincronizando seu AD DS local com o Azure AD usando o Azure AD Connect, considere a possibilidade de corresponder os nomes dos grupos de segurança locais com os nomes dos grupos de recursos no Azure.

![Nomenclatura](./media/migrate-best-practices-security-management/naming.png)

*Nomenclatura do grupo de recursos*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) convenções de nomenclatura.

## <a name="best-practice-implement-delete-locks-for-resource-groups"></a>Prática recomendada: implementar bloqueios de exclusão para grupos de recursos

A pior coisa que poderia acontecer é você perder um grupo de recursos porque o excluiu acidentalmente. Por isso, recomendamos que você implemente bloqueios de exclusão para que isso não aconteça.

![Excluir bloqueios](./media/migrate-best-practices-security-management/locks.png)

*Excluir bloqueios*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) como bloquear recursos para evitar alterações inesperadas.

## <a name="best-practice-understand-resource-access-permissions"></a>Prática recomendada: entender as permissões de acesso a recursos

Um proprietário de assinatura tem acesso a todos os recursos e grupos de recursos em sua assinatura.

- Tenha cuidado ao adicionar pessoas a essa atribuição valiosa. Entender as implicações desses tipos de permissão é importante para manter seu ambiente seguro e estável.
- Coloque recursos nos grupos de recursos apropriados:
  - Faça a correspondência entre recursos com ciclos de vida semelhantes. O ideal é que não seja necessário mover um recurso quando você precisar excluir um grupo de recursos inteiro.
  - Recursos que dão suporte a uma função ou a uma carga de trabalho devem ser colocados juntos para simplificar o gerenciamento.

**Saiba mais:**

- [Saiba mais sobre](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise) como organizar grupos de recursos e assinaturas.

## <a name="best-practice-tag-resources-effectively"></a>Prática recomendada: marcar recursos com eficiência

Muitas vezes, usar apenas um nome de grupo de recursos relacionado aos recursos não fornecerá metadados suficientes para a implementação eficaz de mecanismos como cobrança interna ou gerenciamento dentro de uma assinatura.

- Como prática recomendada, você deve usar marcas do Azure para adicionar metadados úteis que podem ser consultados e informados.
- As marcas fornecem uma maneira de organizar recursos logicamente com as propriedades que você definir. As marcas podem ser aplicadas a grupos de recursos ou recursos diretamente.
- As marcas podem ser aplicadas a um grupo de recursos ou a recursos individuais. As marcas do grupo de recursos não são herdadas pelos recursos no grupo.
- Você pode automatizar a marcação usando o PowerShell, a Automação do Azure ou marcando grupos e recursos individualmente. – Abordagem de marcação ou serviço de autoatendimento. Se você tiver uma solicitação e um sistema de gerenciamento de alterações em vigor, poderá usar facilmente as informações na solicitação para preencher as marcas de recursos específicas da empresa.

![Marcação](./media/migrate-best-practices-security-management/tagging.png)
*Marcação*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) marcação e limitações de marca.
- [Reveja](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags#powershell) exemplos do PowerShell e da CLI para configurar a marcação e aplicar marcas de um grupo de recursos a seus recursos.
- [Leia](https://www.azurefieldnotes.com/2016/07/18/azure-resource-tagging-best-practices) as melhores práticas de marcação do Azure.

## <a name="best-practice-implement-blueprints"></a>Prática recomendada: implementar plantas

Assim como um blueprint permite que engenheiros e arquitetos desenhem os parâmetros de um projeto, o Azure Blueprints permite que arquitetos de nuvem e grupos centrais de TI definam um conjunto repetitivo de recursos do Azure que implementa e adere aos padrões e requisitos de uma organização. Usando o Azure Blueprints, as equipes de desenvolvimento do Azure podem compilar e criar rapidamente novos ambientes que atendam aos requisitos de conformidade organizacional e que tenham um conjunto de componentes internos, como rede, para acelerar o desenvolvimento e a entrega.

- Use blueprints para coordenar a implantação de grupos de recursos, modelos do Azure Resource Manager e atribuições de função e política.
- Os blueprints são armazenados em um Azure Cosmos DB distribuído globalmente. Objetos de blueprint são replicados para várias regiões do Azure. A replicação fornece baixa latência, alta disponibilidade e acesso consistente ao blueprint, independentemente da região na qual o projeto implanta os recursos.

**Saiba mais:**

- [Leia](https://docs.microsoft.com/azure/governance/blueprints/overview) sobre blueprints.
- [Reveja](https://azure.microsoft.com/blog/customizing-azure-blueprints-to-accelerate-ai-in-healthcare) um exemplo de blueprint usado para acelerar a Inteligência Artificial nos serviços de saúde.

## <a name="best-practice-review-azure-reference-architectures"></a>Prática recomendada: examinar as arquiteturas de referência do Azure

A criação de cargas de trabalho seguras, escalonáveis e gerenciáveis no Azure pode ser complicada. Com alterações contínuas, pode ser difícil saber o status de diferentes recursos para ter um ambiente ideal. Ter uma referência para consulta pode ser útil ao projetar e migrar suas cargas de trabalho. O Azure e os parceiros do Azure criaram várias arquiteturas de referência de exemplo para vários tipos de ambientes. Esses exemplos são projetados para fornecer ideias com as quais você pode aprender e desenvolver.

As arquiteturas de referência são organizadas por cenário. Eles contêm práticas recomendadas e conselhos sobre gerenciamento, disponibilidade, escalabilidade e segurança.
O Ambiente do Serviço de Aplicativo do Azure fornece um ambiente totalmente isolado e dedicado para a execução de aplicativos do Serviço de Aplicativo, incluindo aplicativos Web Windows e Linux, contêineres do Docker, aplicativos móveis e funções. O Serviço de Aplicativo adiciona o poder do Azure ao seu aplicativo, com segurança, balanceamento de carga, dimensionamento automático e gerenciamento automatizado. Você também pode aproveitar seus recursos de DevOps, como implantação contínua do Azure DevOps e do GitHub, gerenciamento de pacote, ambientes de preparo, domínio personalizado e certificados SSL. O Serviço de Aplicativo é útil para aplicativos que precisam de isolamento e acesso seguro à rede e para os que usam grande quantidade de memória e outros recursos que precisam ser dimensionados.

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/architecture/reference-architectures) arquiteturas de referência do Azure.
- [Reveja](https://docs.microsoft.com/azure/architecture/example-scenario) os cenários de exemplo do Azure.

## <a name="best-practice-manage-resources-with-azure-management-groups"></a>Prática recomendada: gerenciar recursos com grupos de gerenciamento do Azure

Se sua organização tiver várias assinaturas, você precisará gerenciar o acesso, as políticas e a conformidade delas. Os grupos de gerenciamento do Azure fornecem um nível de escopo acima das assinaturas.

- Você organiza assinaturas em contêineres chamados grupos de gerenciamento e aplica as condições de governança a eles.
- Todas as assinaturas em um grupo de gerenciamento herdam automaticamente as condições do grupo de gerenciamento.
- Os grupos de gerenciamento fornecem gerenciamento de nível empresarial de larga escala, independentemente do tipo de assinaturas que você tenha.
- Por exemplo, você pode aplicar uma política de grupo de gerenciamento que limita as regiões em que as VMs podem ser criadas. Essa política é, então, aplicada a todos os grupos de gerenciamento, assinaturas e recursos nesse grupo de gerenciamento.
- É possível criar uma estrutura flexível de grupos de gerenciamento e assinaturas, com o objetivo de organizar seus recursos em uma hierarquia para políticas unificadas e gerenciamento de acesso.

O diagrama a seguir mostra um exemplo de criação de uma hierarquia para governança usando grupos de gerenciamento.

![Grupos de gerenciamento](./media/migrate-best-practices-security-management/management-groups.png)
*Grupos de gerenciamento*

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/governance/management-groups/index) sobre como organizar recursos em grupos de gerenciamento.

## <a name="best-practice-deploy-azure-policy"></a>Prática recomendada: implantar Azure Policy

O Azure Policy é um serviço no Azure que você pode usar para criar, atribuir e gerenciar políticas.

- As políticas impõem diferentes regras e efeitos sobre os recursos para que esses recursos permaneçam em conformidade com seus padrões corporativos e contratos de nível de serviço.
- O Azure Policy avalia os recursos, verificando aqueles que não são compatíveis com suas políticas.
- Por exemplo, você poderia criar uma política que permite que apenas um tamanho de SKU específico para VMs em seu ambiente. O Azure Policy avaliará essa configuração durante a criação e a atualização de recursos e ao verificar os recursos existentes.
- O Azure fornece algumas políticas internas para você atribuir, mas você também pode criar suas próprias políticas.

![Azure Policy](./media/migrate-best-practices-security-management/policy.png)
*Azure Policy*

**Saiba mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/governance/policy/overview) do Azure Policy.
- [Saiba mais sobre](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)como criar e gerenciar políticas para impor conformidade.

## <a name="best-practice-implement-a-bcdr-strategy"></a>Prática recomendada: implementar uma estratégia de BCDR

O planejamento de BCDR (continuidade dos negócios e recuperação de desastres) é um exercício crítico que precisa ser concluído como parte do processo de planejamento de migração do Azure. Em termos jurídicos, seu contrato pode incluir uma cláusula de força maior que exclui obrigações não cumpridas por conta de casos de força maior, como furacões e terremotos. No entanto, você também tem a obrigação de garantir que os serviços continuarão a ser executados e serão recuperados sempre que necessário durante um desastre. Sua capacidade de fazer isso pode significar o sucesso ou o fim de sua empresa.

De maneira geral, sua estratégia de BCDR deve considerar:

- **Backup de dados:** Como manter seus dados seguros para que você possa recuperá-los facilmente se ocorrerem interrupções.
- **Recuperação de desastre:** Como manter seus aplicativos resilientes e disponíveis se ocorrerem interrupções.

### <a name="set-up-bcdr"></a>Configurar a BCDR

Ao migrar para o Azure, é importante entender que, embora a plataforma Azure forneça esses recursos de resiliência embutidos, você precisará projetar sua implantação do Azure para tirar proveito dos recursos e serviços do Azure que fornecem alta disponibilidade, recuperação de desastre e backup.

- Sua solução de BCDR dependerá dos objetivos da empresa e será influenciada por sua estratégia de implantação do Azure. As implantações de IaaS (infraestrutura como serviço) e PaaS (plataforma como serviço) apresentam desafios diferentes de BCDR.
- Uma vez em vigor, suas soluções de BCDR devem ser testadas regularmente para verificar que a estratégia permanece viável.

### <a name="back-up-an-iaas-deployment"></a>Fazer backup de uma implantação de IaaS

Na maioria dos casos, uma carga de trabalho local é desativada após a migração e sua estratégia local para fazer backup dos dados precisa ser estendida ou substituída. Se você migrar todo o data center para o Azure, precisará projetar e implementar uma solução de backup completa usando as tecnologias do Azure ou soluções integradas de terceiros.

Para cargas de trabalho em execução em VMs IaaS do Azure, considere estas soluções de backup:

- **Backup do Azure:** Fornece backups consistentes com o aplicativo para VMs Windows e Linux do Azure.
- **Instantâneos de armazenamento:** Usa instantâneos do armazenamento de BLOBs.

#### <a name="azure-backup"></a>Backup do Azure

O Backup do Azure cria pontos de recuperação de dados que são armazenados no armazenamento do Azure. O Backup do Azure pode fazer backup de discos de VM do Azure e arquivos do Azure (versão prévia). Os Arquivos do Azure oferecem compartilhamentos de arquivos na nuvem, que podem ser acessados por meio de SMB.

Você pode usar o Backup do Azure para fazer backup de VMs de duas maneiras.

- **Backup direto das configurações de VM.** você pode fazer backup de VMs com o Backup do Azure diretamente nas opções de VM no portal do Azure. Você pode fazer backup da VM uma vez por dia e pode restaurar o disco da VM conforme necessário. O Backup do Azure usa instantâneos de dados com reconhecimento de aplicativo (VSS) e nenhum agente é instalado na VM.
- **Backup direto em um cofre dos Serviços de Recuperação.** você pode fazer backup de VMs IaaS implantando um cofre dos Serviços de Recuperação do Backup do Azure. Isso fornece um local único para controlar e gerenciar backups, bem como opções de backup e restauração granulares. O Backup ocorre até três vezes por dia, no nível de arquivo/pasta. Ele não tem reconhecimento de aplicativo e não tem suporte para Linux. Instale o agente MARS (Serviços de Recuperação do Microsoft Azure) em cada VM em que você deseja realizar o backup usando esse método.
- **Proteja a VM no Servidor de Backup do Azure.** O Servidor de Backup do Azure é fornecido gratuitamente com o Backup do Azure. O backup da VM é feito no armazenamento local do Servidor de Backup do Azure. Depois disso, você faz o backup do Servidor de Backup do Azure no Azure em um cofre. O backup tem reconhecimento de aplicativo com granularidade completa sobre a frequência e a retenção de backup. Você pode fazer backup no nível do aplicativo, por exemplo, ao fazer backup do SQL Server ou do SharePoint.

Para segurança, o Backup do Azure criptografa os dados em trânsito usando AES 256 e os envia por HTTPS para o Azure. Os dados de backup em repouso no Azure são criptografados com [SSE (Criptografia do Serviço de Armazenamento)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption?toc=%2fazure%2fstorage%2fqueues%2ftoc.json) e os dados para armazenamento e transmissão.

![Backup do Azure](./media/migrate-best-practices-security-management/iaas-backup.png)
*Backup do Azure*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) diferentes tipos de backups.
- [Planejar uma infraestrutura de backup](https://docs.microsoft.com/azure/backup/backup-azure-vms-introduction) para VMs do Azure.

#### <a name="storage-snapshots"></a>Instantâneos de armazenamento

As VMs do Azure são armazenadas como blobs de páginas no Armazenamento do Azure.

- Os instantâneos capturam o estado do blob em um momento específico.
- Como método alternativo de backup para discos de VM do Azure, você pode capturar um instantâneo de blobs de armazenamento e copiá-lo para outra conta de armazenamento.
- Você pode copiar um blob inteiro ou usar uma cópia de instantâneo incremental para copiar somente alterações delta e reduzir o espaço de armazenamento.
- Como precaução extra, você pode habilitar a exclusão reversível para contas de armazenamento de blobs. Com esse recurso habilitado, um blob excluído é marcado para exclusão, mas não é limpo imediatamente. Durante o período intermediário, o blob pode ser restaurado.

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) o Armazenamento de Blobs do Azure.
- [Saiba](https://docs.microsoft.com/azure/storage/blobs/storage-blob-snapshots) como criar um instantâneo de blob.
- [Reveja um cenário de exemplo](https://azure.microsoft.com/blog/microsoft-azure-block-blob-storage-backup) para o backup de armazenamento de blobs.
- [Leia sobre](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete) exclusão reversível.
- [Recuperação de desastre e failover forçado (versão prévia) no Armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-disaster-recovery-guidance?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)

#### <a name="third-party-backup"></a>Backup de terceiros

Além disso, você pode usar soluções de terceiros para fazer backup de VMs do Azure e contêineres de armazenamento para o armazenamento local ou para outros provedores de nuvem. [Saiba mais](https://azuremarketplace.microsoft.com/marketplace/apps?search=backup&page=1) sobre soluções de backup no Azure Marketplace.

### <a name="set-up-disaster-recovery-for-iaas-apps"></a>Configurar a recuperação de desastre para aplicativos de IaaS

Além de proteger dados, o planejamento de BCDR precisa considerar como manter os aplicativos e cargas de trabalho disponíveis em caso de desastre. Para cargas de trabalho em execução em VMs IaaS do Azure e no armazenamento do Azure, considere estas soluções:

#### <a name="azure-site-recovery"></a>Recuperação de Site do Azure

O Azure Site Recovery é o principal serviço do Azure para fazer com que as VMs do Azure possam ser colocadas online e os aplicativos VM possam ser disponibilizados quando ocorrem paralisações.

O Site Recovery replica as VMs de uma região primária para uma região secundária do Azure. Quando ocorre um desastre, faça failover das VMs da região primária e continue a acessá-las normalmente na região secundária. Quando as operações voltarem ao normal, você poderá fazer failback das VMs para a região primária.

![Recuperação de Site do Azure](./media/migrate-best-practices-security-management/site-recovery.png)

*Recuperação de Site*

**Saiba mais:**

- [Reveja](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-disaster-recovery-guidance) os cenários de recuperação de desastre para VMs do Azure.
- [Saiba como](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-replicate-after-migration) configurar a recuperação de desastre para uma VM do Azure após a migração.

## <a name="best-practice-use-managed-disks-and-availability-sets"></a>Prática recomendada: usar discos gerenciados e conjuntos de disponibilidade

O Azure usa conjuntos de disponibilidade para agrupar as VMs logicamente e isolar as VMs em um conjunto de outros recursos. As VMs no conjunto de disponibilidade são distribuídas entre vários domínios de falha com subsistemas separados, para proteção contra falhas locais, e também são distribuídas entre vários domínios de atualização, de modo que nem todas as VMs em um conjunto reiniciam ao mesmo tempo.

Os discos gerenciados do Azure simplificam o gerenciamento de discos para VMs IaaS do Azure por meio do gerenciamento de contas de armazenamento associadas aos discos de VM.

- Recomendamos que você use discos gerenciados sempre que possível. Você só precisa especificar o tipo de armazenamento que deseja usar e o tamanho do disco necessário, em seguida, o Azure cria e gerencia o disco para você em segundo plano.
- Você pode converter discos existentes em gerenciados.
- Você deve criar VMs em conjuntos de disponibilidade para ter alta resiliência e disponibilidade. Quando ocorrem paralisações, planejadas ou não, os conjuntos de disponibilidade fazem com que pelo menos uma das VMs no conjunto permaneça disponível.

![Managed Disks](./media/migrate-best-practices-security-management/managed-disks.png)

*Discos gerenciados*

**Saiba mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) sobre discos gerenciados.
- [Saiba mais sobre](https://docs.microsoft.com/azure/virtual-machines/windows/convert-unmanaged-to-managed-disks) como converter discos gerenciados.
- [Saiba como](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability) gerenciar a disponibilidade de VMs Windows no Azure.

## <a name="best-practice-monitor-resource-usage-and-performance"></a>Prática recomendada: monitorar o uso e o desempenho dos recursos

Você pode ter movido suas cargas de trabalho para o Azure por causa de seus grandes recursos de dimensionamento. No entanto, mover a carga de trabalho não significa que o Azure implementará o dimensionamento automaticamente sem sua indicação. Por exemplo:

- Se sua organização de marketing envia um novo anúncio de TV que gera 300% a mais de tráfego, isso pode causar problemas de disponibilidade do site. Sua carga de trabalho recém-migrada poderá atingir limites atribuídos e falhar.
- Outro exemplo pode ser um ataque de DDoS (negação de serviço distribuído) na carga de trabalho migrada. Nesse caso, talvez seja melhor não dimensionar e, sim, impedir que a origem dos ataques alcance os recursos.

Esses dois casos tem resoluções diferentes, mas para ambos você precisa de uma visão geral do que está acontecendo com o monitoramento de desempenho e uso.

- O Azure Monitor pode ajudar a revelar essas métricas e a fornecer uma resposta com alertas, dimensionamento automático, hubs de eventos, aplicativos lógicos e muito mais.
- Além do monitoramento do Azure, você pode integrar seu aplicativo de SIEM de terceiros para monitorar os logs do Azure em relação a eventos de auditoria e de desempenho.

![Azure Monitor](./media/migrate-best-practices-security-management/monitor.png)
*Azure Monitor*

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/azure-monitor/overview) sobre o Azure Monitor.
- [Obtenha as melhores práticas](https://docs.microsoft.com/azure/architecture/best-practices/monitoring) para monitoramento e diagnóstico.
- [Saiba mais sobre](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling) dimensionamento automático.
- [Saiba como](https://docs.microsoft.com/azure/security-center/security-center-export-data-to-siem) rotear dados do Azure para uma ferramenta SIEM.

## <a name="best-practice-enable-diagnostic-logging"></a>Prática recomendada: habilitar o log de diagnóstico

Os recursos do Azure geram um número razoável de métricas de registro em log e dados telemétricos.

- Por padrão, a maioria dos tipos de recurso não tem o log de diagnóstico habilitado.
- Ao habilitar o log de diagnóstico em seus recursos, você poderá consultar os dados de registro em log e criar alertas e guias estratégicos com base neles.
- Quando você habilita o log de diagnóstico, cada recurso ganha um conjunto específico de categorias. Selecione uma ou mais categorias de registro em log e um local para os dados de log. Os logs podem ser enviados para uma conta de armazenamento, um hub de eventos ou aos logs do Azure Monitor.

![Registro em log de diagnóstico](./media/migrate-best-practices-security-management/diagnostics.png)
*Registro em log de diagnóstico*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs) como coletar e consumir dados de log.
- [Saiba o que tem suporte](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-diagnostic-logs-schema) para registro em log de diagnóstico.

## <a name="best-practice-set-up-alerts-and-playbooks"></a>Prática recomendada: configurar alertas e guias estratégicos

Com o log de diagnóstico habilitado para os recursos do Azure, você pode começar a usar dados de registro em log para criar alertas personalizados.

- Os alertas trabalham de forma proativa, mandando notificações quando encontram condições em seus dados de monitoramento. Com isso, você pode lidar com problemas antes que os usuários do sistema os percebam. Você pode gerar alertas sobre itens como valores de métrica, consultas de pesquisa de log, eventos de log de atividades, integridade de plataforma e disponibilidade do site.
- Quando os alertas são disparados, você pode executar um Guia Estratégico de Aplicativo Lógico. Um guia estratégico ajuda você a automatizar e a orquestrar uma resposta a um alerta específico. Os guias estratégicos se baseiam nos Aplicativos Lógicos do Azure. Você pode usar modelos de Aplicativo Lógico para criar guias estratégicos ou criar seus próprios.
- Como um exemplo simples, você pode criar um alerta que dispara quando uma verificação de porta é feita em relação a um grupo de segurança de rede. Você pode configurar um guia estratégico que é executado e bloqueia o endereço IP de origem da verificação.
- Outro exemplo pode ser um aplicativo com perda de memória. Quando o uso da memória chega a um determinado ponto, um guia estratégico pode reciclar o processo.

![Alertas](./media/migrate-best-practices-security-management/alerts.png)
*Alertas*

**Saiba mais:**

- [Saiba mais](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-alerts) sobre os alertas.
- [Saiba mais sobre](https://docs.microsoft.com/azure/security-center/security-center-playbooks) guias estratégicos de segurança que respondem a alertas da Central de Segurança.

## <a name="best-practice-use-the-azure-dashboard"></a>Prática recomendada: usar o painel do Azure

O portal do Azure é um console unificado e baseado na Web que permite compilar, gerenciar e monitorar tudo, desde aplicativos Web simples até aplicativos complexos na nuvem. Ele inclui um painel personalizável e opções de acessibilidade.

- Você pode criar vários painéis e compartilhá-los com outras pessoas que tenham acesso às suas assinaturas do Azure.
- Com esse modelo compartilhado, sua equipe consegue ver o ambiente do Azure, o que permite que eles sejam proativos ao gerenciar sistemas na nuvem.

![Painel do Azure](./media/migrate-best-practices-security-management/dashboard.png)
*Painel do Azure*

**Saiba mais:**

- [Saiba como](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards) criar um painel.
- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards-structure) estrutura de painéis.

## <a name="best-practice-understand-support-plans"></a>Prática recomendada: entender os planos de suporte

Em algum momento, você precisará colaborar com sua equipe de suporte ou a equipe de suporte da Microsoft. É essencial ter um conjunto de políticas e procedimentos de suporte para cenários como recuperação de desastre. Além disso, sua equipe de suporte e os administradores devem receber treinamento sobre a implementação dessas políticas.

- Na remota hipótese de um problema no serviço do Azure afetar sua carga de trabalho, os administradores precisam saber como enviar um tíquete de suporte para a Microsoft da forma mais apropriada e eficiente.
- Familiarize-se com os vários planos de suporte oferecidos para o Azure. Eles vão desde tempos de resposta dedicados para instâncias de desenvolvedor a suporte Premier com um tempo de resposta de menos de 15 minutos.

![Planos de suporte](./media/migrate-best-practices-security-management/support.png)
*Planos de suporte*

**Saiba mais:**

- [Obtenha uma visão geral](https://azure.microsoft.com/support/options) dos planos de suporte do Azure.
- [Saiba mais](https://azure.microsoft.com/support/legal/sla) sobre os SLA (contratos de nível de serviço).

## <a name="best-practice-manage-updates"></a>Prática recomendada: gerenciar atualizações

Manter as VMs do Azure atualizadas com o sistema operacional e as atualizações de software mais recentes é uma tarefa árdua. A capacidade de revelar todas as VMs para descobrir de quais atualizações elas precisam e efetuar push automaticamente dessas atualizações é extremamente valiosa.

- Você pode usar o Gerenciamento de Atualizações na Automação do Azure a fim de gerenciar atualizações do sistema operacional para computadores executando Windows e Linux implantados no Azure, localmente e em outros provedores de nuvem.
- Use o Gerenciamento de Atualizações para avaliar rapidamente o status das atualizações disponíveis em todos os computadores agentes e gerenciar a instalação da atualização.
- Você pode habilitar o Gerenciamento de Atualizações para VMs diretamente de uma conta da Automação do Azure. Você também pode atualizar uma única VM na página de VMs no portal do Azure.
- Além disso, as VMs do Azure podem ser registradas no System Center Configuration Manager. Você pode, em seguida, migrar a carga de trabalho do Configuration Manager para o Azure e fazer atualizações de software e relatórios em uma única interface da Web.

![Atualizações de VM](./media/migrate-best-practices-security-management/updates.png)
*Atualizações*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/automation/automation-update-management) gerenciamento de atualizações no Azure.
- [Saiba como](https://docs.microsoft.com/azure/automation/oms-solution-updatemgmt-sccmintegration) integrar o Configuration Manager com o gerenciamento de atualizações.
- [Perguntas frequentes](https://docs.microsoft.com/sccm/core/understand/configuration-manager-on-azure) sobre o Configuration Manager no Azure.

## <a name="implement-a-change-management-process"></a>Implementar um processo de gerenciamento de alterações

Assim como em qualquer sistema de produção, fazer alterações de qualquer tipo pode afetar seu ambiente. Um processo de gerenciamento de alterações que exige o envio de solicitações para a realização das alterações em sistemas de produção é uma adição valiosa ao ambiente migrado.

- Você pode criar estruturas de melhores práticas para gerenciamento de alterações a fim de aumentar a conscientização da equipe de suporte e dos administradores.
- Você pode usar a Automação do Azure para ajudar no gerenciamento de configuração e no controle de alterações dos fluxos de trabalho migrados.
- Ao impor o processo de gerenciamento de alterações, você poderá usar logs de auditoria para vincular os logs de alterações do Azure a solicitações de alteração supostamente (ou não) existentes. Assim, se você vir uma alteração feita sem uma solicitação de alteração correspondente, poderá investigar o que deu errado no processo.

O Azure tem uma solução de controle de alterações na Automação do Azure:

- A solução rastreia as alterações no software e nos arquivos Windows e Linux, nas chaves de registro do Windows, nos serviços Windows e nos daemons do Linux.
- As alterações nos servidores monitorados são enviadas para o serviço do Azure Monitor na nuvem para processamento.
- A lógica é aplicada aos dados recebidos e o serviço de nuvem registra os dados.
- No painel Controle de Alterações, você pode ver facilmente as alterações feitas à sua infraestrutura de servidor.

![Gerenciamento de alterações](./media/migrate-best-practices-security-management/change.png)
*Gerenciamento de alterações*

**Saiba mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/automation/automation-change-tracking) Controle de Alterações.
- [Saiba mais sobre](https://docs.microsoft.com/azure/automation/automation-intro) recursos da Automação do Azure.

## <a name="next-steps"></a>Próximos passos

Examine outras melhores práticas:

- [Melhores práticas](./migrate-best-practices-networking.md) de rede após a migração.
- [Melhores práticas](./migrate-best-practices-costs.md) de gerenciamento de custos após a migração.
