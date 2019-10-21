---
title: Práticas recomendadas para proteger e gerenciar cargas de trabalho migradas para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Depois de migrar para o Azure, obtenha as práticas recomendadas para operar, gerenciar e proteger suas cargas de trabalho migradas.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: f7782aeedf794441a7ba4e1f6a97f162fa33abfb
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548547"
---
# <a name="best-practices-for-securing-and-managing-workloads-migrated-to-azure"></a>Práticas recomendadas para proteger e gerenciar cargas de trabalho migradas para o Azure

Ao planejar e projetar a migração, além de pensar sobre a migração em si, você precisa considerar seu modelo de segurança e gerenciamento no Azure após a migração. Este artigo descreve o planejamento e as práticas recomendadas para proteger sua implantação do Azure após a migração e para tarefas contínuas para manter a implantação em execução em um nível ideal.

> [!IMPORTANT]
> As práticas recomendadas e as opiniões descritas neste artigo baseiam-se na plataforma e nos recursos de serviço do Azure disponíveis no momento da gravação. Recursos e funcionalidades mudam com o passar do tempo.

## <a name="secure-migrated-workloads"></a>Cargas de trabalho migradas seguras

Após a migração, a tarefa mais crítica é proteger as cargas de trabalho migradas de ameaças internas e externas. Essas práticas recomendadas ajudam você a fazer isso:

- [Trabalhar com a central de segurança do Azure](#best-practice-follow-azure-security-center-recommendations): saiba como trabalhar com o monitoramento, as avaliações e as recomendações fornecidas pela central de segurança do Azure.
- [Criptografar seus dados](#best-practice-encrypt-data): Obtenha as práticas recomendadas para criptografar seus dados no Azure.
- [Configure o antimalware](#best-practice-protect-vms-with-antimalware): Proteja suas VMs contra malware e ataques mal-intencionados.
- [Proteger aplicativos Web](#best-practice-secure-web-apps): manter informações confidenciais seguras em aplicativos Web migrados.
- [Examinar assinaturas](#best-practice-review-subscriptions-and-resource-permissions): Verifique quem pode acessar suas assinaturas e recursos do Azure após a migração.
- [Trabalhar com logs](#best-practice-review-audit-and-security-logs): revise os logs de segurança e auditoria do Azure regularmente.
- [Examine outros recursos de segurança](#best-practice-evaluate-other-security-features): entenda e avalie os recursos de segurança avançados que o Azure oferece.

## <a name="best-practice-follow-azure-security-center-recommendations"></a>Prática recomendada: siga as recomendações da central de segurança do Azure

A Microsoft trabalha difícil para garantir que os administradores de locatários do Azure tenham as informações necessárias para habilitar os recursos de segurança que protegem as cargas de trabalho contra ataques. A central de segurança do Azure fornece gerenciamento de segurança unificado. Na central de segurança, você pode aplicar políticas de segurança entre cargas de trabalho, limitar a exposição à ameaça e detectar e responder a ataques. A central de segurança analisa os recursos e as configurações nos locatários do Azure e faz recomendações de segurança, incluindo:

- **Gerenciamento de política centralizado** – garanta a conformidade com os requisitos de segurança da empresa ou regulatória gerenciando centralmente políticas de segurança em todas as suas cargas de trabalho de nuvem híbrida.
- **Avaliação de segurança contínua** – monitore a postura de segurança de máquinas, redes, armazenamento e serviços de dados e aplicativos para descobrir possíveis problemas de segurança.
- **Recomendações acionáveis** – corrija vulnerabilidades de segurança antes que elas possam ser exploradas por invasores com recomendações de segurança priorizadas e acionáveis.
- **Alertas e incidentes priorizados** – concentre-se primeiro nas ameaças mais críticas, com alertas e incidentes de segurança priorizados.

Além das avaliações e recomendações, a central de segurança do Azure fornece outros recursos de segurança que podem ser habilitados para recursos específicos.

- **Acesso just-in-time (JIT).** Reduza sua superfície de ataque de rede com acesso controlado just-in-time a portas de gerenciamento em VMs do Azure.
  - Ter VM RDP porta 3389 aberta na Internet expõe VMs para atividade de ator inadequada. Os endereços IP do Azure são bem conhecidos e os hackers os investigam continuamente em busca de ataques em portas abertas de 3389.
  - Just in time usa NSGs (grupos de segurança de rede) e regras de entrada que limitam a quantidade de tempo em que uma porta específica é aberta.
  - Com o just in time habilitado, a central de segurança verifica se um usuário tem permissões de acesso de gravação de RBAC (controle de acesso baseado em função) para uma VM. Além disso, especifique regras para como os usuários podem se conectar às VMs. Se as permissões estiverem OK, uma solicitação de acesso será aprovada e a central de segurança configurará o NSGs para permitir o tráfego de entrada para as portas selecionadas durante o período especificado. NSGs são retornados ao estado anterior quando o tempo expira.
- **Controles de aplicativo adaptáveis.** Mantenha o software e o malware fora das VMs controlando quais aplicativos são executados usando listas de permissões dinâmicas.
  - Controles de aplicativo adaptáveis permitem que você aprove aplicativos e impeça que usuários ou administradores não autorizados instalem aplicativos de software não aprovados ou habilitação em suas VMs.
    - Você pode bloquear ou alertar tentativas de execução de aplicativos mal-intencionados, evitar aplicativos indesejados ou mal-intencionados e garantir a conformidade com a política de segurança de aplicativo da sua organização.
- **Monitoramento de integridade de arquivo.** Garanta a integridade dos arquivos em execução nas VMs.
  - Você não precisa instalar o software para causar problemas de VM. A alteração de um arquivo do sistema também pode causar uma falha na VM ou degradação do desempenho. O monitoramento de integridade de arquivo examina os arquivos do sistema e as configurações do registro para alterações e notifica se algo está atualizado.
  - A central de segurança recomenda quais arquivos você deve monitorar.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-intro) sobre a central de segurança do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/security-center/security-center-just-in-time) sobre o acesso à VM just in time.
- [Saiba como](https://docs.microsoft.com/azure/security-center/security-center-adaptive-application) aplicar controles de aplicativo adaptáveis.
- [Introdução](https://docs.microsoft.com/azure/security-center/security-center-file-integrity-monitoring) ao monitoramento de integridade de arquivo.

## <a name="best-practice-encrypt-data"></a>Prática recomendada: criptografar dados

A criptografia é uma parte importante das práticas de segurança do Azure. Garantir que a criptografia esteja habilitada em todos os níveis ajuda a impedir que partes não autorizadas obtenham acesso a dados confidenciais, incluindo dados em trânsito e em repouso.

### <a name="encryption-for-iaas"></a>Criptografia para IaaS

- **Máquinas virtuais:** Para VMs, você pode usar Azure Disk Encryption para criptografar seus discos de VM IaaS Windows e Linux.
  - A criptografia de disco usa o BitLocker para Windows e o DM-cript para Linux para fornecer criptografia de volume para o sistema operacional e os discos de dados.
  - Você pode usar uma chave de criptografia criada pelo Azure ou pode fornecer suas próprias chaves de criptografia, protegidas em Azure Key Vault.
  - Com a criptografia de disco, os dados da VM IaaS são protegidos em repouso (no disco) e durante a inicialização da VM.
    - A central de segurança do Azure alertará se você tiver VMs que não estão criptografadas.
- **Armazenamento:** Proteger dados em repouso armazenados no armazenamento do Azure.
  - Os dados armazenados em contas de armazenamento do Azure podem ser criptografados usando chaves AES geradas pela Microsoft que são compatíveis com FIPS 140-2 ou você pode usar suas próprias chaves.
  - O Criptografia do Serviço de Armazenamento está habilitado para todas as contas de armazenamento novas e existentes e não pode ser desabilitado.

### <a name="encryption-for-paas"></a>Criptografia para PaaS

Ao contrário de IaaS, em que você gerencia suas próprias VMs e infraestrutura, em uma plataforma de modelo de PaaS e infraestrutura é gerenciada pelo provedor, deixando você se concentrar na lógica e nos recursos do aplicativo principal. Com tantos tipos diferentes de serviços de PaaS, cada serviço é avaliado individualmente para fins de segurança. Como exemplo, vamos ver como podemos habilitar a criptografia para o banco de dados SQL do Azure.

- **Always Encrypted:** Use o assistente de Always Encrypted no SQL Server Management Studio para proteger dados em repouso.
  - Você cria Always Encrypted chave para criptografar dados de coluna individuais.
  - Always Encrypted chaves podem ser armazenadas como criptografadas em metadados de banco de dados ou armazenadas em repositórios de chaves confiáveis, como Azure Key Vault.
  - As alterações do aplicativo provavelmente serão necessárias para usar esse recurso.
- **TDE (Transparent Data Encryption):** Proteja o banco de dados SQL do Azure com criptografia e descriptografia em tempo real do banco de dados, backups associados e arquivos de log de transações em repouso.
  - O TDE permite que as atividades de criptografia ocorram sem alterações na camada de aplicativo.
  - O TDE pode usar as chaves de criptografia fornecidas pela Microsoft ou você pode fornecer suas próprias chaves usando o suporte a Bring Your Own Key.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-overview) Azure Disk Encryption para VMs IaaS.
- [Habilite](https://docs.microsoft.com/azure/security/azure-security-disk-encryption-windows) a criptografia para VMs IaaS Windows.
- [Saiba mais](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) Criptografia do Serviço de Armazenamento do Azure para dados em repouso.
- [Leia](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) uma visão geral do Always Encrypted.
- [Leia sobre](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-azure-sql?view=sql-server-2017) TDE para o banco de dados SQL do Azure.
- [Saiba mais](https://docs.microsoft.com/azure/sql-database/transparent-data-encryption-byok-azure-sql) TDE com Bring Your Own Key.

## <a name="best-practice-protect-vms-with-antimalware"></a>Prática recomendada: proteger VMs com Antimalware

Em particular, as VMs mais antigas migradas para Azure podem não ter o nível apropriado de antimalware instalado. O Azure fornece uma solução de ponto de extremidade gratuita que ajuda a proteger as VMs contra vírus, spyware e outros tipos de malware.

- O Microsoft antimalware para Azure gera alertas quando um software mal-intencionado ou indesejado conhecido tenta se instalar.
- É uma solução de agente única que é executada em segundo plano sem intervenção humana.
- Na central de segurança do Azure, você pode identificar facilmente as VMs que não têm o Endpoint Protection em execução e instalar o Microsoft Antimalware conforme necessário.

![Antimalware para VMs ](./media/migrate-best-practices-security-management/antimalware.png)
*antimalware para VMs*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/security/azure-security-antimalware) Microsoft antimalware.

## <a name="best-practice-secure-web-apps"></a>Prática recomendada: proteger aplicativos Web

Aplicativos Web migrados enfrentam alguns problemas:

- A maioria dos aplicativos Web herdados tendem a ter informações confidenciais dentro dos arquivos de configuração. Os arquivos que contêm essas informações podem apresentar problemas de segurança quando é feito o backup dos aplicativos ou quando o código do aplicativo é verificado ou está fora do controle do código-fonte.
- Além disso, ao migrar aplicativos Web que residem em uma VM, você provavelmente está movendo esse computador de uma rede local e um ambiente protegido por firewall para um ambiente voltado para a Internet. Certifique-se de configurar uma solução que faça o mesmo trabalho que os recursos de proteção local.

O Azure fornece algumas soluções:

- **Azure Key Vault:** Hoje, os desenvolvedores de aplicativos Web estão realizando etapas para garantir que as informações confidenciais não sejam vazadas desses arquivos. Um método para proteger informações é extraí-lo de arquivos e colocá-lo em um Azure Key Vault.
  - Você pode usar Key Vault para centralizar o armazenamento de segredos do aplicativo e controlar sua distribuição. Ele evita a necessidade de armazenar informações de segurança em arquivos de aplicativo.
  - Os aplicativos podem acessar com segurança as informações no cofre usando URIs, sem a necessidade de código personalizado.
  - Azure Key Vault permite que você bloqueie o acesso por meio de controles de segurança do Azure e implemente "chaves sem interrupção" diretamente. A Microsoft não vê nem extrai seus dados.
- **Ambiente do serviço de aplicativo:** Se um aplicativo que você migrar precisar de proteção extra, você poderá considerar adicionar um Ambiente do Serviço de Aplicativo e um firewall do aplicativo Web para proteger os recursos do aplicativo.
  - O Ambiente do Serviço de Aplicativo do Azure fornece um ambiente totalmente isolado e dedicado no qual executar aplicativos do serviço de aplicativo, como aplicativos Web do Windows e Linux, contêineres do Docker, aplicativos móveis e funções.
  - É útil para aplicativos que são de grande escala, exigem isolamento e acesso seguro à rede ou têm alta utilização de memória.
- **Firewall do aplicativo Web:** Um recurso do gateway de Aplicativo Azure que fornece proteção centralizada para aplicativos Web.
  - Ele protege os aplicativos Web sem a necessidade de modificações de código de back-end.
  - Ele protege vários aplicativos Web ao mesmo tempo por trás de um gateway de aplicativo.
  - Um firewall do aplicativo Web pode ser monitorado usando Azure Monitor e é integrado à central de segurança do Azure.

![Proteger aplicativos Web](./media/migrate-best-practices-security-management/web-apps.png)

*Cofre da Chave do Azure*

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/key-vault/key-vault-overview) do Azure Key Vault.
- [Saiba mais sobre](https://docs.microsoft.com/azure/application-gateway/waf-overview) o Firewall do aplicativo Web.
- [Obtenha uma introdução](https://docs.microsoft.com/azure/app-service/environment/intro) aos ambientes do serviço de aplicativo.
- [Saiba como](https://docs.microsoft.com/azure/key-vault/tutorial-web-application-keyvault) configurar um aplicativo Web para ler segredos de Key Vault.
- [Saiba mais sobre](https://docs.microsoft.com/azure/application-gateway/waf-overview) o Firewall do aplicativo Web.

## <a name="best-practice-review-subscriptions-and-resource-permissions"></a>Prática recomendada: examinar as assinaturas e as permissões de recurso

Ao migrar suas cargas de trabalho e executá-las no Azure, a equipe com acesso à carga de trabalho é movida. Sua equipe de segurança deve examinar o acesso ao seu locatário do Azure e aos grupos de recursos regularmente. O Azure tem ofertas para segurança de controle de acesso e gerenciamento de identidade, incluindo o RBAC (controle de acesso baseado em função) para autorizar permissões para acessar recursos do Azure.

- O RBAC atribui permissões de acesso para entidades de segurança. As entidades de segurança representam usuários, grupos (um conjunto de usuários), entidades de serviço (identidade usada por aplicativos e serviços) e identidades gerenciadas (uma Azure Active Directory identidade gerenciada automaticamente pelo Azure).
- O RBAC pode atribuir funções a princípios de segurança, como proprietário, colaborador e leitor, e definições de função (uma coleção de permissões) que definem as operações que podem ser executadas pelas funções.
- O RBAC também pode definir escopos que definem o limite para uma função. O escopo pode ser definido em vários níveis, incluindo um grupo de gerenciamento, uma assinatura, um grupo de recursos ou um recurso.
- Verifique se os administradores com acesso do Azure só podem acessar os recursos que você deseja permitir. Se as funções predefinidas no Azure não forem granulares o suficiente, você poderá criar funções personalizadas para separar e limitar permissões de acesso.

controle de ![Access ](./media/migrate-best-practices-security-management/subscription.png)
*controle de acesso-iam*

**Saiba Mais:**

- [Sobre](https://docs.microsoft.com/azure/role-based-access-control/overview) o RBAC.
- [Saiba](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) como gerenciar o acesso usando o RBAC e o portal do Azure.
- [Saiba mais sobre](https://docs.microsoft.com/azure/role-based-access-control/custom-roles) as funções personalizadas.

## <a name="best-practice-review-audit-and-security-logs"></a>Prática recomendada: examinar logs de auditoria e segurança

O Azure Active Directory (AD do Azure) fornece logs de atividade que aparecem no Azure Monitor. Os logs capturam as operações executadas no aluguel do Azure, quando elas ocorreram e quem as realizou.

- Os logs de auditoria mostram o histórico das tarefas no locatário. Os logs de atividade de entrada mostram quem realizou as tarefas.
- O acesso a relatórios de segurança depende da sua licença do Azure AD. Em gratuito e básico, você obtém uma lista de usuários e entradas arriscados. Nas edições Premium 1 e Premium 2, você obtém informações de evento subjacentes.
- Você pode rotear logs de atividade para vários pontos de extremidade para retenção de longo prazo e informações de dados.
- Torne-o uma prática comum para examinar os logs ou integrar suas ferramentas de SIEM (gerenciamento de informações e eventos de segurança) para examinar as anormalidades automaticamente. Se você não estiver usando o Premium 1 ou 2, precisará fazer muita análise por conta própria ou usando seu sistema SIEM. A análise inclui a procura de eventos e entradas arriscados e outros padrões de ataque do usuário.

![Usuários e grupos](./media/migrate-best-practices-security-management/azure-ad.png)

*Usuários e grupos do Azure AD*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor) Logs de atividades do Azure AD no Azure Monitor.
- [Saiba como](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs) auditar relatórios de atividade no portal do Azure AD.

## <a name="best-practice-evaluate-other-security-features"></a>Prática recomendada: avaliar outros recursos de segurança

O Azure fornece outros recursos de segurança que fornecem opções de segurança avançadas. Algumas dessas práticas recomendadas exigem licenças complementares e opções Premium.

- **Implemente as AU (unidades administrativas) do Azure AD.** Delegar tarefas administrativas à equipe de suporte pode ser complicado com apenas o controle de acesso básico do Azure. Dar acesso à equipe de suporte para administrar todos os grupos no Azure AD pode não ser a abordagem ideal para a segurança organizacional. O uso de AU permite separar os recursos do Azure em contêineres de uma maneira semelhante às unidades organizacionais (UO) locais. Para usar AU, o administrador de AU deve ter uma licença Premium do Azure AD. [Saiba mais](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-administrative-units).
- **Use a autenticação multifator.** Se você tiver uma licença Premium do Azure AD, poderá habilitar e impor a autenticação multifator em suas contas de administrador. O phishing é a maneira mais comum de comprometimento das credenciais de contas. Quando um ator inadequado tem credenciais de conta de administrador, não há nenhuma interrupção das ações de alcance, como excluir todos os grupos de recursos. Você pode estabelecer a autenticação multifator de várias maneiras, incluindo com email, um aplicativo autenticador e mensagens de texto de telefone. Como administrador, você pode selecionar a opção menos intrusiva. A autenticação multifator integra-se à análise de ameaças e às políticas de acesso condicional para exigir aleatoriamente uma resposta de desafio de autenticação multifator. Saiba mais sobre as [diretrizes de segurança](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices)e [como configurar a autenticação multifator](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices).
- **Implemente o acesso condicional.** Na maioria das organizações de pequeno e médio porte, os administradores do Azure e a equipe de suporte estão provavelmente localizados em uma única geografia. Nesse caso, a maioria dos logons será proveniente das mesmas áreas. Se os endereços IP desses locais forem razoavelmente estáticos, faz sentido que você não deve ver logons de administrador de fora dessas áreas. Mesmo em um evento no qual um ator inadequado remoto compromete as credenciais de um administrador, você pode implementar recursos de segurança como o acesso condicional combinado com a autenticação multifator para impedir o logon de locais remotos ou de locais falsificados de IP aleatório atende. [Saiba mais](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) sobre o acesso condicional e [examine as práticas recomendadas](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices) para acesso condicional no Azure AD.
- **Examine as permissões de aplicativo empresarial.** Ao longo do tempo, os administradores selecionam links da Microsoft e de terceiros sem saber seu impacto na organização. Os links podem apresentar telas de consentimento que atribuem permissões a aplicativos do Azure e podem permitir acesso para ler dados do Azure AD ou até mesmo acesso completo para gerenciar toda a sua assinatura do Azure. Você deve examinar regularmente os aplicativos aos quais os administradores e usuários têm permissão de acesso aos recursos do Azure. Verifique se esses aplicativos têm apenas as permissões necessárias. Além disso, trimestral ou semianual, você pode enviar por email aos usuários um link para páginas de aplicativo para que eles estejam cientes dos aplicativos aos quais têm permissão para acessar seus dados organizacionais. [Saiba mais](https://docs.microsoft.com/azure/active-directory/manage-apps/application-types) sobre os tipos de aplicativos e [como controlar](https://docs.microsoft.com/azure/active-directory/manage-apps/remove-user-or-group-access-portal) as atribuições de aplicativo no Azure AD.

## <a name="managed-migrated-workloads"></a>Cargas de trabalho migradas gerenciadas

Nesta seção, recomendamos algumas práticas recomendadas para o gerenciamento do Azure, incluindo:

- [Gerenciar recursos](#best-practice-name-resource-groups): práticas recomendadas para recursos e grupos de recursos do Azure, incluindo nomes inteligentes, prevenção de exclusão acidental, gerenciamento de permissões de recursos e marcação de recursos eficaz.
- [Use plantas](#best-practice-implement-blueprints): Obtenha uma visão geral rápida sobre o uso de plantas para criar e gerenciar seus ambientes de implantação.
- [Revisar arquiteturas](#best-practice-review-azure-reference-architectures): examine as arquiteturas de exemplo do Azure para aprender com a criação de suas implantações após a migração.
- [Configurar grupos de gerenciamento](#best-practice-manage-resources-with-azure-management-groups): se você tiver várias assinaturas, poderá reuni-las em grupos de gerenciamento e aplicar as configurações de governança a esses grupos.
- [Configurar políticas de acesso](#best-practice-deploy-azure-policy): aplique políticas de conformidade aos recursos do Azure.
- [Implemente uma estratégia de BCDR](#best-practice-implement-a-bcdr-strategy): Reúna uma estratégia de BCDR (continuidade dos negócios e recuperação de desastre) para manter os dados seguros, o seu ambiente resiliente e os recursos em funcionamento quando ocorrerem interrupções.
- [Gerenciar VMs](#best-practice-use-managed-disks-and-availability-sets): agrupe VMs em grupos de disponibilidade para resiliência e alta disponibilidade. Use discos gerenciados para facilitar o gerenciamento de disco e armazenamento de VM.
- [Monitorar o uso de recursos](#best-practice-monitor-resource-usage-and-performance): habilite o log de diagnóstico para recursos do Azure, crie alertas e guias estratégicos para solução de problemas proativas e use o painel do Azure para uma exibição unificada de sua integridade e status de implantação.
- [Gerenciar suporte e atualizações](#best-practice-manage-updates): entenda seu plano de suporte do Azure e como implementá-lo, obtenha as práticas recomendadas para manter as VMs atualizadas e colocar os processos em vigor para o gerenciamento de alterações.

## <a name="best-practice-name-resource-groups"></a>Prática recomendada: nomear grupos de recursos

Garantir que seus grupos de recursos tenham nomes significativos que os administradores e os membros da equipe de suporte possam reconhecer e navegar de forma drástica aumentam a produtividade e a eficiência.

- É recomendável seguir as convenções de nomenclatura do Azure.
- Se você estiver sincronizando suas Active Directory locais com o Azure AD usando Azure AD Connect, considere a correspondência dos nomes dos grupos de segurança locais com os nomes dos grupos de recursos no Azure.

![Nomenclatura](./media/migrate-best-practices-security-management/naming.png)

*Nomeação de grupo de recursos*

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions) convenções de nomenclatura.

## <a name="best-practice-implement-delete-locks-for-resource-groups"></a>Prática recomendada: implementar bloqueios de exclusão para grupos de recursos

A última coisa que você precisa é que um grupo de recursos desapareça porque ele foi excluído acidentalmente. Recomendamos que você implemente os bloqueios de exclusão para que isso não aconteça.

![Excluir bloqueios](./media/migrate-best-practices-security-management/locks.png)

*Excluir bloqueios*

**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) bloquear recursos para evitar alterações inesperadas.

## <a name="best-practice-understand-resource-access-permissions"></a>Prática recomendada: entender as permissões de acesso a recursos

Um proprietário de assinatura tem acesso a todos os grupos de recursos e recursos em sua assinatura.

- Adicione pessoas com moderação a essa atribuição valiosa. Compreender as ramificações desses tipos de permissões é importante para manter seu ambiente seguro e estável.
- Certifique-se de colocar os recursos nos grupos de recursos apropriados:
  - Combine recursos com um ciclo de vida semelhante em conjunto. O ideal é que você não precise mover um recurso quando precisar excluir um grupo de recursos inteiro.
  - Recursos que dão suporte a uma função ou carga de trabalho devem ser colocados em conjunto para gerenciamento simplificado.

**Saiba Mais:**

- [Saiba mais sobre como](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise) organizar assinaturas e grupos de recursos.

## <a name="best-practice-tag-resources-effectively"></a>Prática recomendada: marcar recursos com eficiência

Geralmente, o uso de apenas um nome de grupo de recursos relacionado a recursos não fornecerá metadados suficientes para a implementação efetiva de mecanismos, como cobrança interna ou gerenciamento em uma assinatura.

- Como prática recomendada, você deve usar as marcas do Azure para adicionar metadados úteis que podem ser consultados e relatados.
- As marcas fornecem uma maneira de organizar logicamente os recursos com as propriedades que você define. As marcas podem ser aplicadas a grupos de recursos ou recursos diretamente.
- As marcas podem ser aplicadas em um grupo de recursos ou em recursos individuais. As marcas do grupo de recursos não são herdadas pelos recursos no grupo.
- Você pode automatizar a marcação usando o PowerShell ou a automação do Azure, ou marcar grupos e recursos individuais. -abordagem de marcação ou autoatendimento. Se você tiver um sistema de gerenciamento de solicitações e alterações em vigor, poderá usar facilmente as informações na solicitação para preencher as marcas de recursos específicos da empresa.

*marcação* de ](./media/migrate-best-practices-security-management/tagging.png)
 de ![Tagging

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags) limitações de marca e marcação.
- [Examinar](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags#powershell) Exemplos do PowerShell e da CLI para configurar a marcação e aplicar marcas de um grupo de recursos a seus recursos.
- [Ler](https://www.azurefieldnotes.com/2016/07/18/azure-resource-tagging-best-practices) Práticas recomendadas de marcação do Azure.

## <a name="best-practice-implement-blueprints"></a>Prática recomendada: implementar plantas

Da mesma forma que o Blueprint permite que engenheiros e arquitetos esboçom dos parâmetros de design de um projeto, os planos gráficos do Azure permitem que os arquitetos de nuvem e os grupos de ti centrais definam um conjunto repetível de recursos do Azure que implementam e aderem aos padrões de uma organização, padrões e requisitos. Usando plantas do Azure, as equipes de desenvolvimento podem criar e criar rapidamente novos ambientes que atendam aos requisitos de conformidade organizacional e que têm um conjunto de componentes internos, como a rede, para acelerar o desenvolvimento e a entrega.

- Use plantas para orquestrar a implantação de grupos de recursos, modelos de Azure Resource Manager e atribuições de política e função.
- Os planos gráficos são armazenados em um Azure Cosmos DB distribuído globalmente. Os objetos Blueprint são replicados para várias regiões do Azure. A replicação fornece baixa latência, alta disponibilidade e acesso consistente ao plano gráfico, independentemente da região em que o plano gráfico implanta recursos.

**Saiba Mais:**

- [Leia](https://docs.microsoft.com/azure/governance/blueprints/overview) sobre plantas.
- [Examine](https://azure.microsoft.com/blog/customizing-azure-blueprints-to-accelerate-ai-in-healthcare) um exemplo de Blueprint usado para acelerar o ia na área de saúde.

## <a name="best-practice-review-azure-reference-architectures"></a>Prática recomendada: examinar as arquiteturas de referência do Azure

Criar cargas de trabalho seguras, escalonáveis e gerenciáveis no Azure pode ser assustador. Com alterações contínuas, pode ser difícil acompanhar recursos diferentes para um ambiente ideal. Ter uma referência para aprender com o pode ser útil ao projetar e migrar suas cargas de trabalho. Os parceiros do Azure e do Azure criaram várias arquiteturas de referência de exemplo para vários tipos de ambientes. Esses exemplos foram projetados para fornecer ideias que você pode aprender e criar.

As arquiteturas de referência são organizadas por cenário. Eles contêm práticas recomendadas e conselhos sobre gerenciamento, disponibilidade, escalabilidade e segurança.
O Ambiente do Serviço de Aplicativo do Azure fornece um ambiente totalmente isolado e dedicado no qual executar aplicativos do serviço de aplicativo, incluindo aplicativos Web do Windows e Linux, contêineres do Docker, aplicativos móveis e funções. O serviço de aplicativo adiciona o poder do Azure ao seu aplicativo, com segurança, balanceamento de carga, dimensionamento automático e gerenciamento automatizado. Você também pode aproveitar seus recursos de DevOps, como implantação contínua do Azure DevOps e GitHub, gerenciamento de pacotes, ambientes de preparo, domínio personalizado e certificados SSL. O serviço de aplicativo é útil para aplicativos que precisam de isolamento e acesso seguro à rede, e aqueles que usam altas quantidades de memória e outros recursos que precisam ser dimensionados.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/architecture/reference-architectures) Arquiteturas de referência do Azure.
- [Examinar](https://docs.microsoft.com/azure/architecture/example-scenario) Cenários de exemplo do Azure.

## <a name="best-practice-manage-resources-with-azure-management-groups"></a>Prática recomendada: gerenciar recursos com grupos de gerenciamento do Azure

Se sua organização tiver várias assinaturas, você precisará gerenciar o acesso, as políticas e a conformidade para elas. Os grupos de gerenciamento do Azure fornecem um nível de escopo acima das assinaturas.

- Você organiza as assinaturas em contêineres chamados grupos de gerenciamento e aplica condições de governança a eles.
- Todas as assinaturas em um grupo de gerenciamento herdam automaticamente as condições do grupo de gerenciamento.
- Os grupos de gerenciamento fornecem gerenciamento de nível empresarial em grande escala, independentemente do tipo de assinatura que você tem.
- Por exemplo, você pode aplicar uma política de grupo de gerenciamento que limita as regiões nas quais as VMs podem ser criadas. Essa política é aplicada a todos os grupos de gerenciamento, assinaturas e recursos sob esse grupo de gerenciamento.
- Você pode criar uma estrutura flexível de grupos de gerenciamento e assinaturas para organizar seus recursos em uma hierarquia para gerenciamento de acesso e política unificado.

O diagrama a seguir mostra um exemplo de criação de uma hierarquia para governança usando grupos de gerenciamento.

grupos de ![Management ](./media/migrate-best-practices-security-management/management-groups.png)
*grupos de gerenciamento*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/governance/management-groups/index) sobre como organizar recursos em grupos de gerenciamento.

## <a name="best-practice-deploy-azure-policy"></a>Prática recomendada: implantar Azure Policy

Azure Policy é um serviço no Azure que você usa para criar, atribuir e gerenciar políticas.

- As políticas impõem diferentes regras e efeitos sobre seus recursos, para que esses recursos permaneçam em conformidade com seus padrões corporativos e contratos de nível de serviço.
- Azure Policy avalia seus recursos, verificando aqueles que não estão em conformidade com suas políticas.
- Por exemplo, você pode criar uma política que permita apenas um tamanho de SKU específico para VMs em seu ambiente. Azure Policy avaliará essa configuração ao criar e atualizar recursos e ao verificar os recursos existentes.
- O Azure fornece algumas políticas internas que podem ser atribuídas ou você pode criar as suas próprias.

](./media/migrate-best-practices-security-management/policy.png)
 de política de ![Azure*Azure Policy*

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/governance/policy/overview) do Azure Policy.
- [Saiba mais sobre como](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) criar e gerenciar políticas para impor a conformidade.

## <a name="best-practice-implement-a-bcdr-strategy"></a>Prática recomendada: implementar uma estratégia de BCDR

Planejar a continuidade dos negócios e a recuperação de desastres (BCDR) é um exercício crítico que você deve concluir como parte do processo de planejamento de migração do Azure. Em termos legais, seus contratos podem incluir uma cláusula Force maior que faz desculpas em obrigações devido a uma força maior, como furacões ou terremotos. No entanto, você também tem obrigações em relação à sua capacidade de garantir que os serviços continuem a ser executados e se recupere onde for necessário, quando houver desastre. Sua capacidade de fazer isso pode fazer ou interromper o futuro da sua empresa.

Em grande escala, sua estratégia de BCDR deve considerar:

- **Backup de dados:** Como manter seus dados seguros para que você possa recuperá-los facilmente se ocorrerem interrupções.
- **Recuperação de desastre:** Como manter seus aplicativos resilientes e disponíveis se ocorrerem interrupções.

### <a name="set-up-bcdr"></a>Configurar o BCDR

Ao migrar para o Azure, é importante entender que, embora a plataforma do Azure forneça esses recursos de resiliência embutidos, você precisa projetar sua implantação do Azure para aproveitar os recursos e serviços do Azure que fornecem alta disponibilidade, recuperação de desastres e backup.

- Sua solução BCDR dependerá dos objetivos da sua empresa e será influenciada pela sua estratégia de implantação do Azure. As implantações de IaaS (infraestrutura como serviço) e PaaS (plataforma como serviço) apresentam desafios diferentes para o BCDR.
- Uma vez em vigor, suas soluções BCDR devem ser testadas regularmente para verificar se sua estratégia permanece viável.

### <a name="back-up-an-iaas-deployment"></a>Fazer backup de uma implantação de IaaS

Na maioria dos casos, uma carga de trabalho local é desativada após a migração, e sua estratégia local para fazer backup de dados deve ser estendida ou substituída. Se você migrar todo o datacenter para o Azure, precisará projetar e implementar uma solução de backup completa usando as tecnologias do Azure ou soluções integradas de terceiros.

Para cargas de trabalho em execução em VMs IaaS do Azure, considere estas soluções de backup:

- **Backup do Azure:** Fornece backups consistentes com o aplicativo para VMs Windows e Linux do Azure.
- **Instantâneos de armazenamento:** Usa instantâneos do armazenamento de BLOBs.

#### <a name="azure-backup"></a>Backup do Azure

O backup do Azure cria pontos de recuperação de dados que são armazenados no armazenamento do Azure. O backup do Azure pode fazer backup de discos de VM do Azure e arquivos do Azure (versão prévia). Os arquivos do Azure fornecem compartilhamentos de arquivos na nuvem, acessíveis via SMB.

Você pode usar o backup do Azure para fazer backup de VMs de duas maneiras.

- **Backup direto de configurações da VM.** Você pode fazer backup de VMs com o backup do Azure diretamente das opções de VM na portal do Azure. Você pode fazer backup da VM uma vez e dia e restaurar o disco da VM conforme necessário. O backup do Azure usa o VSS (instantâneos de dados com reconhecimento de aplicativo) e nenhum agente está instalado na VM.
- **Backup direto em um cofre dos serviços de recuperação.** Você pode fazer backup de suas VMs de IaaS implantando um cofre dos serviços de recuperação de backup do Azure. Isso fornece um único local para acompanhar e gerenciar backups, bem como opções granulares de backup e restauração. O backup é de até três vezes por dia, no nível de arquivo/pasta. Não é compatível com o aplicativo e não há suporte para o Linux. Instale o agente de Serviços de Recuperação do Microsoft Azure (MARS) em cada VM que você deseja fazer backup usando esse método.
- **Proteja a VM para Servidor de Backup do Azure.** Servidor de Backup do Azure é fornecido gratuitamente com o backup do Azure. O backup da VM é feito no armazenamento de Servidor de Backup do Azure local. Em seguida, faça backup da Servidor de Backup do Azure no Azure em um cofre. O backup tem reconhecimento de aplicativo, com granularidade total sobre a frequência de backup e a retenção. Você pode fazer backup no nível do aplicativo, por exemplo, fazendo backup do SQL Server ou do SharePoint.

Por segurança, o backup do Azure criptografa dados em trânsito usando o AES 256 e os envia por HTTPS para o Azure. Os dados de backup em repouso no Azure são criptografados usando [criptografia do serviço de armazenamento (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption?toc=%2fazure%2fstorage%2fqueues%2ftoc.json)e dados para transmissão e armazenamento.

backup do ![Azure ](./media/migrate-best-practices-security-management/iaas-backup.png)
*backup do Azure*

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) os diferentes tipos de backups.
- [Planejar uma infraestrutura de backup](https://docs.microsoft.com/azure/backup/backup-azure-vms-introduction) para VMs do Azure.

#### <a name="storage-snapshots"></a>Instantâneos de armazenamento

As VMs do Azure são armazenadas como BLOBs de páginas no armazenamento do Azure.

- Instantâneos capturam o estado do blob em um ponto específico no tempo.
- Como um método de backup alternativo para discos de VM do Azure, você pode tirar um instantâneo dos BLOBs de armazenamento e copiá-los para outra conta de armazenamento.
- Você pode copiar um blob inteiro ou usar uma cópia de instantâneo incremental para copiar apenas as alterações delta e reduzir o espaço de armazenamento.
- Como uma precaução extra, você pode habilitar a exclusão reversível para contas de armazenamento de BLOBs. Com esse recurso habilitado, um blob que é excluído é marcado para exclusão, mas não é limpo imediatamente. Durante o período intermediário, o blob pode ser restaurado.

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) Armazenamento de BLOBs do Azure.
- [Saiba como](https://docs.microsoft.com/azure/storage/blobs/storage-blob-snapshots) criar um instantâneo de BLOB.
- [Examine um cenário de exemplo](https://azure.microsoft.com/blog/microsoft-azure-block-blob-storage-backup) para backup de armazenamento de BLOBs.
- [Leia sobre](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete) exclusão reversível.
- [Recuperação de desastre e failover forçado (visualização) no armazenamento do Azure](https://docs.microsoft.com/azure/storage/common/storage-disaster-recovery-guidance?toc=%2fazure%2fstorage%2fblobs%2ftoc.json)

#### <a name="third-party-backup"></a>Backup de terceiros

Além disso, você pode usar soluções de terceiros para fazer backup de VMs do Azure e contêineres de armazenamento no armazenamento local ou em outros provedores de nuvem. [Saiba mais](https://azuremarketplace.microsoft.com/marketplace/apps?search=backup&page=1) sobre soluções de backup no Azure Marketplace.

### <a name="set-up-disaster-recovery-for-iaas-apps"></a>Configurar a recuperação de desastre para aplicativos de IaaS

Além de proteger os dados, o planejamento do BCDR deve considerar como manter os aplicativos e as cargas de trabalho disponíveis em caso de desastre. Para cargas de trabalho em execução em VMs IaaS do Azure e armazenamento do Azure, considere estas soluções:

#### <a name="azure-site-recovery"></a>Recuperação de Site do Azure

Azure Site Recovery é o serviço principal do Azure para garantir que as VMs do Azure possam ser colocadas online e aplicativos de VM disponibilizados quando ocorrem paralisações.

Site Recovery Replica VMs de uma região primária para a secundária do Azure. Quando ocorre um desastre, você faz failover de VMs da região primária e continua acessando-as normalmente na região secundária. Quando as operações retornam para normal, você pode fazer failback de VMs para a região primária.

![Recuperação de Site do Azure](./media/migrate-best-practices-security-management/site-recovery.png)

*Recuperação de Site*

**Saiba Mais:**

- [Examine](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-disaster-recovery-guidance) os cenários de recuperação de desastres para VMs do Azure.
- [Saiba como configurar a](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-replicate-after-migration) recuperação de desastre para uma VM do Azure após a migração.

## <a name="best-practice-use-managed-disks-and-availability-sets"></a>Prática recomendada: usar discos gerenciados e conjuntos de disponibilidade

O Azure usa conjuntos de disponibilidade para agrupar logicamente as VMs e para isolar as VMs em um conjunto de outros recursos. As VMs em um conjunto de disponibilidade são distribuídas entre vários domínios de falha com subsistemas separados, para proteger contra falhas locais e também se disseminam entre vários domínios de atualização para que nem todas as VMs em um conjunto sejam reinicializadas ao mesmo tempo.

Os discos gerenciados do Azure simplificam o gerenciamento de disco para VMs IaaS do Azure gerenciando as contas de armazenamento associadas aos discos de VM.

- Recomendamos que você use o Managed disks sempre que possível. Você só precisa especificar o tipo de armazenamento que deseja usar e o tamanho do disco necessário, e o Azure cria e gerencia o disco para você, nos bastidores.
- Você pode converter discos existentes para gerenciados.
- Você deve criar VMs em conjuntos de disponibilidade para alta resiliência e disponibilidade. Quando ocorrem interrupções planejadas ou não planejadas, os conjuntos de disponibilidade garantem que pelo menos uma de suas VMs no conjunto continua disponível.

![Managed Disks](./media/migrate-best-practices-security-management/managed-disks.png)

*Discos gerenciados*

**Saiba Mais:**

- [Obtenha uma visão geral](https://docs.microsoft.com/azure/virtual-machines/windows/managed-disks-overview) dos Managed disks.
- [Saiba como](https://docs.microsoft.com/azure/virtual-machines/windows/convert-unmanaged-to-managed-disks) converter discos para gerenciados.
- [Saiba como](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability) gerenciar a disponibilidade de VMs do Windows no Azure.

## <a name="best-practice-monitor-resource-usage-and-performance"></a>Prática recomendada: monitorar o uso e o desempenho dos recursos

Você pode ter movido suas cargas de trabalho para o Azure para seus recursos de escala imensa. No entanto, mover sua carga de trabalho não significa que o Azure implementará automaticamente o dimensionamento sem a sua entrada. Como exemplo:

- Se sua organização de marketing envia um novo anúncio de TV que impulsiona 300% de mais tráfego, isso pode causar problemas de disponibilidade do site. Sua carga de trabalho migrada recentemente pode atingir limites e falhas atribuídos.
- Outro exemplo pode ser um ataque de DDoS (negação de serviço distribuído) em sua carga de trabalho migrada. Nesse caso, talvez você não queira dimensionar, mas para impedir que a origem dos ataques atinja seus recursos.

Esses dois casos têm resoluções diferentes, mas, para ambos, você precisa de uma percepção do que está acontecendo com o monitoramento de desempenho e uso.

- Azure Monitor pode ajudar a trazer essas métricas e fornecer respostas com alertas, dimensionamento automático, hubs de eventos, aplicativos lógicos e muito mais.
- Além do monitoramento do Azure, você pode integrar seu aplicativo SIEM de terceiros para monitorar os logs do Azure para auditoria e eventos de desempenho.

](./media/migrate-best-practices-security-management/monitor.png)
 do monitor de ![Azure*Azure monitor*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/azure-monitor/overview) Azure Monitor.
- [Obtenha as práticas recomendadas](https://docs.microsoft.com/azure/architecture/best-practices/monitoring) para monitoramento e diagnóstico.
- [Saiba mais sobre](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling) o dimensionamento automático.
- [Saiba como](https://docs.microsoft.com/azure/security-center/security-center-export-data-to-siem) rotear dados do Azure para uma ferramenta Siem.

## <a name="best-practice-enable-diagnostic-logging"></a>Prática recomendada: habilitar o log de diagnóstico

Os recursos do Azure geram um número razoável de métricas de registro em log e dados de telemetria.

- Por padrão, a maioria dos tipos de recursos não tem o log de diagnóstico habilitado.
- Ao habilitar o log de diagnóstico em seus recursos, você pode consultar os dados de log e criar alertas e guias estratégicos com base nele.
- Quando você habilitar o log de diagnóstico, cada recurso terá um conjunto específico de categorias. Você seleciona uma ou mais categorias de registro em log e um local para os dados de log. Os logs podem ser enviados para uma conta de armazenamento, Hub de eventos ou para Azure Monitor logs.

registro em log de*diagnóstico* do ![Diagnostic ](./media/migrate-best-practices-security-management/diagnostics.png)


**Saiba Mais:**

- [Saiba mais sobre como](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs) coletar e consumir dados de log.
- [Saiba o que tem suporte para o](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-diagnostic-logs-schema) log de diagnóstico.

## <a name="best-practice-set-up-alerts-and-playbooks"></a>Prática recomendada: configurar alertas e guias estratégicos

Com o log de diagnóstico habilitado para recursos do Azure, você pode começar a usar os dados de log para criar alertas personalizados.

- Os alertas notificam proativamente quando condições são encontradas nos dados de monitoramento. Em seguida, você pode resolver problemas antes que os usuários do sistema os percebam. Você pode alertar sobre itens como valores de métrica, consultas de pesquisa de log, eventos do log de atividades, integridade da plataforma e disponibilidade do site.
- Quando os alertas são disparados, você pode executar um manual do aplicativo lógico. Um guia estratégico ajuda a automatizar e orquestrar uma resposta a um alerta específico. Os guias estratégicos são baseados em aplicativos lógicos do Azure. Você pode usar modelos de aplicativo lógico para criar guias estratégicos ou criar seus próprios.
- Como exemplo simples, você pode criar um alerta que dispara quando uma verificação de porta ocorre em relação a um grupo de segurança de rede. Você pode configurar um guia estratégico que executa e bloqueia o endereço IP da origem da verificação.
- Outro exemplo pode ser um aplicativo com um vazamento de memória. Quando o uso de memória chega a um determinado ponto, um guia estratégico pode reciclar o processo.

![Alerts ](./media/migrate-best-practices-security-management/alerts.png)
*alertas*

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-alerts) alertas.
- [Saiba mais sobre](https://docs.microsoft.com/azure/security-center/security-center-playbooks) guias estratégicos de segurança que respondem aos alertas da central de segurança.

## <a name="best-practice-use-the-azure-dashboard"></a>Prática recomendada: usar o painel do Azure

O portal do Azure é um console unificado baseado na Web que permite criar, gerenciar e monitorar tudo, desde aplicativos Web simples a aplicativos de nuvem complexos. Ele inclui um painel personalizável e opções de acessibilidade.

- Você pode criar vários painéis e compartilhá-los com outras pessoas que tenham acesso às suas assinaturas do Azure.
- Com esse modelo compartilhado, sua equipe tem visibilidade do ambiente do Azure, permitindo que eles sejam proativos ao gerenciar sistemas na nuvem.

painel do ![Azure ](./media/migrate-best-practices-security-management/dashboard.png)
*painel do Azure*

**Saiba Mais:**

- [Saiba como](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards) criar um painel.
- [Saiba mais sobre](https://docs.microsoft.com/azure/azure-portal/azure-portal-dashboards-structure) a estrutura do painel.

## <a name="best-practice-understand-support-plans"></a>Prática recomendada: entender os planos de suporte

Em algum momento, você precisará colaborar com a equipe de suporte ou com a equipe de suporte da Microsoft. Ter um conjunto de diretivas e procedimentos para o suporte durante cenários como a recuperação de desastres é vital. Além disso, os administradores e a equipe de suporte devem ser treinados para implementar essas políticas.

- No caso improvável de um problema de serviço do Azure afetar sua carga de trabalho, os administradores devem saber como enviar um tíquete de suporte à Microsoft da maneira mais apropriada e eficiente.
- Familiarize-se com os vários planos de suporte oferecidos para o Azure. Elas vão desde tempos de resposta dedicados a instâncias de desenvolvedor até o suporte Premier com um tempo de resposta de menos de 15 minutos.

planos de ![Support ](./media/migrate-best-practices-security-management/support.png)
*planos de suporte*

**Saiba Mais:**

- [Obtenha uma visão geral](https://azure.microsoft.com/support/options) dos planos de suporte do Azure.
- [Saiba mais sobre](https://azure.microsoft.com/support/legal/sla) SLAs (contratos de nível de serviço).

## <a name="best-practice-manage-updates"></a>Prática recomendada: gerenciar atualizações

Manter as VMs do Azure atualizadas com o sistema operacional e as atualizações de software mais recentes é uma tarefa massiva. A capacidade de colocar todas as VMs em superfície para descobrir quais atualizações precisam e enviar automaticamente essas atualizações é extremamente valiosa.

- Você pode usar Gerenciamento de Atualizações na automação do Azure para gerenciar atualizações do sistema operacional para máquinas que executam computadores Windows e Linux implantados no Azure, no local e em outros provedores de nuvem.
- Use Gerenciamento de Atualizações para avaliar rapidamente o status das atualizações disponíveis em todos os computadores do agente e gerenciar a instalação da atualização.
- Você pode habilitar Gerenciamento de Atualizações para VMs diretamente de uma conta de automação do Azure. Você também pode atualizar uma única VM da página VM no portal do Azure.
- Além disso, as VMs do Azure podem ser registradas com System Center Configuration Manager. Em seguida, você pode migrar a carga de trabalho do Configuration Manager para o Azure e fazer relatórios e atualizações de software de uma única interface da Web.

*atualizações de ](./media/migrate-best-practices-security-management/updates.png)
 de* ![VM atualizações

**Saiba Mais:**

- [Saiba mais sobre](https://docs.microsoft.com/azure/automation/automation-update-management) o gerenciamento de atualizações no Azure.
- [Saiba como integrar o](https://docs.microsoft.com/azure/automation/oms-solution-updatemgmt-sccmintegration) Configuration Manager com o gerenciamento de atualizações.
- [Perguntas](https://docs.microsoft.com/sccm/core/understand/configuration-manager-on-azure) frequentes sobre Configuration Manager no Azure.

## <a name="implement-a-change-management-process"></a>Implementar um processo de gerenciamento de alterações

Assim como acontece com qualquer sistema de produção, fazer qualquer tipo de alteração pode afetar o ambiente. Um processo de gerenciamento de alterações que exige que as solicitações sejam enviadas para fazer alterações em sistemas de produção é uma adição valiosa no ambiente migrado.

- Você pode criar estruturas de práticas recomendadas para o gerenciamento de alterações para aumentar a conscientização em administradores e equipe de suporte.
- Você pode usar a automação do Azure para ajudar com o gerenciamento de configuração e o controle de alterações para seus fluxos de trabalho migrados.
- Ao impor o processo de gerenciamento de alterações, você pode usar logs de auditoria para vincular os logs de alterações do Azure às solicitações de alteração presumivelmente (ou não) existentes. Assim, se você vir uma alteração feita sem uma solicitação de alteração correspondente, poderá investigar o que deu errado no processo.

O Azure tem uma solução de controle de alterações na automação do Azure:

- A solução controla alterações em software e arquivos do Windows e Linux, chaves do registro do Windows, serviços do Windows e daemons do Linux.
- As alterações nos servidores monitorados são enviadas para o serviço de Azure Monitor na nuvem para processamento.
- A lógica é aplicada aos dados recebidos e o serviço de nuvem registra os dados.
- No painel Controle de Alterações, você pode ver facilmente as alterações feitas na sua infraestrutura de servidor.

gerenciamento de ![Change ](./media/migrate-best-practices-security-management/change.png)
*Change Management*

**Saiba Mais:**

- [Saiba mais](https://docs.microsoft.com/azure/automation/automation-change-tracking) Controle de Alterações.
- [Saiba mais](https://docs.microsoft.com/azure/automation/automation-intro) Recursos de automação do Azure.

## <a name="next-steps"></a>Próximos passos

Examine outras práticas recomendadas:

- [Práticas recomendadas](./migrate-best-practices-networking.md) para rede após a migração.
- [Práticas recomendadas](./migrate-best-practices-costs.md) para o gerenciamento de custos após a migração.
