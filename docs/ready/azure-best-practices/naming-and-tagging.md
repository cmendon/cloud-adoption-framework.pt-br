---
title: Convenções de nomenclatura e de marcação recomendadas
description: Conheça as recomendações detalhadas de nomenclatura e marcação de recursos destinadas especificamente ao suporte a esforços de adoção de nuvem empresarial.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness, fasttrack-edit
ms.openlocfilehash: 915e974e3968e873c8cf23ec7696f66469f01c82
ms.sourcegitcommit: 0ea426f2f471eb7310c6f09478be1306cf7bf0d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78342007"
---
# <a name="recommended-naming-and-tagging-conventions"></a>Convenções de nomenclatura e de marcação recomendadas

Organizar ativos baseados em nuvem de maneiras que auxiliam o gerenciamento operacional e os requisitos de contabilidade de suporte é um desafio comum em grandes esforços de adoção de nuvem. Aplicando convenções de nomenclatura e de marcação de metadados bem definidas aos recursos hospedados em nuvem, a equipe de TI pode encontrar e gerenciar recursos com rapidez. Nomes e marcas bem definidos também ajudam a alinhar os custos de uso da nuvem com as equipes empresariais usando os mecanismos de contabilidade de estorno e de showback.

As diretrizes de Centro de Arquitetura do Azure para a [nomenclatura de regras e restrições para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) fornecem recomendações gerais e limitações de plataforma. A discussão a seguir estende essa orientação com recomendações mais detalhadas voltadas especificamente para o suporte a esforços de adoção de nuvem empresarial.

Pode ser difícil alterar nomes de recursos. Priorize o estabelecimento de uma Convenção de nomenclatura abrangente antes de começar qualquer implantação em nuvem de grande porte.

> [!NOTE]
> Cada negócio tem requisitos organizacionais e de gerenciamento diferentes. Essas recomendações fornecem um ponto de partida para discussões em suas equipes de adoção de nuvem.
>
> Conforme essas discussões continuarem, use o modelo a seguir para capturar as decisões de nomenclatura e marcação que você faz ao alinhar essas recomendações às suas necessidades de negócios específicas.
>
> Baixe o [modelo de acompanhamento de convenção de nomenclatura e de marcação](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Recursos de nomenclatura e de marcação

Uma estratégia de nomenclatura e de marcação inclui detalhes empresariais e operacionais como componentes de nomes de recursos e marcas de metadados:

- O lado comercial dessa estratégia garante que nomes e marcas de recursos incluam as informações organizacionais necessárias para identificar as equipes. Use um recurso junto com os proprietários empresariais responsáveis por custos de recursos.
- O lado operacional verifica se os nomes e marcas incluem informações que as equipes de TI usam para identificar a carga de trabalho, o aplicativo, o ambiente, a severidade e outras informações úteis para gerenciar recursos.

### <a name="resource-naming"></a>Nomenclatura de recursos

Uma convenção de nomenclatura efetiva monta nomes de recursos usando informações de recursos importantes como partes do nome de um recurso. Por exemplo, usando essas [convenções de nomenclatura recomendadas](#sample-naming-convention), um recurso de IP público para uma carga de trabalho de produção do SharePoint é nomeado da seguinte maneira: `pip-sharepoint-prod-westus-001`.

Com base no nome, você pode identificar rapidamente o tipo de recurso, sua carga de trabalho associada, seu ambiente de implantação e a região do Azure que está hospedando-o.

#### <a name="naming-scope"></a>Escopo de nomenclatura

Todos os tipos de recursos do Azure têm um escopo que define o nível que os nomes de recursos devem ser exclusivos. Um recurso deve ter um nome exclusivo dentro de seu escopo.

Por exemplo, uma rede virtual tem um escopo de grupo de recursos, o que significa que pode haver apenas uma rede chamada `vnet-prod-westus-001` em um determinado grupo de recursos. Outros grupos de recursos podem ter sua própria rede virtual chamada `vnet-prod-westus-001`. Sub-redes, para dar outro exemplo, têm como escopo redes virtuais, o que significa que cada sub-rede dentro de uma rede virtual deve ser nomeada exclusivamente.

Alguns nomes de recursos, como serviços PaaS com pontos de extremidade públicos ou rótulos DNS de máquina virtual, têm escopos globais, o que significa que eles devem ser exclusivos em toda a plataforma do Azure.

Nomes de recursos têm limites de comprimento. O balanceamento do contexto inserido em um nome com seu escopo e comprimento é importante quando você desenvolve suas convenções de nomenclatura. Para saber mais sobre regras de nomenclatura para caracteres permitidos, escopos e comprimentos de nome para tipos de recursos, confira [Convenções de nomenclatura para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming).

#### <a name="recommended-naming-components"></a>Componentes de nomenclatura recomendados

Ao construir sua convenção de nomenclatura, identifique as principais partes de informações que você deseja refletir em um nome de recurso. Diferentes informações são relevantes para diferentes tipos de recurso. A lista a seguir fornece exemplos de informações úteis quando você cria nomes de recursos.

Mantenha o comprimento dos componentes de nomenclatura pequeno para evitar exceder os limites de comprimento de nome do recurso.

| Componente de nomenclatura | DESCRIÇÃO | Exemplos |
| --- | --- | --- |
| Unidade de negócios | Divisão de nível superior da sua empresa que tem a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, esse componente pode representar um único elemento organizacional corporativo de nível superior. | _fin_, _mktg_, _product_, _it_, _corp_ |
| Tipo de assinatura | Descrição resumida da finalidade da assinatura que contém o recurso. É geralmente dividida pelo tipo de ambiente de implantação ou cargas de trabalho específicas. | _prod_, _compartilhado_, _cliente_ |
| Nome do aplicativo ou do serviço | Nome do aplicativo, da carga de trabalho ou do serviço do qual o recurso faz parte. | _navigator_, _emissions_, _sharepoint_, _hadoop_ |
| Ambiente de implantação | A fase do ciclo de vida de desenvolvimento da carga de trabalho compatível com o recurso. | _prod_, _dev_, _QA_, _estágio_, _teste_ |
| Região | A região do Azure em que o recurso é implantado. | _westus_, _eastus2_, _westeurope_, _usgovia_ |

#### <a name="recommended-resource-type-prefixes"></a>Prefixos de tipo de recurso recomendados

Cada carga de trabalho é composta por muitos recursos e serviços individuais. A incorporação de prefixos de tipo de recurso em seus nomes de recursos facilita a identificação visual de componentes de serviço ou aplicativo.

A lista a seguir fornece prefixos de tipo de recurso do Azure recomendados para usar quando você define suas convenções de nomenclatura.

| Tipo de recurso                       | Prefixo do nome do recurso |
| ----------------------------------- | -------------------- |
| Resource group                      | rg-                  |
| Conjunto de disponibilidade                    | avalia               |
| Serviço de gerenciamento de API              | API                 |
| Rede virtual                     | vnet-                |
| Gateway de rede virtual             | vnetgw-              |
| Conexão de gateway                  | cn-                  |
| Sub-rede                              | snet-                |
| Grupo de segurança de rede              | nsg-                 |
| Tabela de rotas                         | rota               |
| Máquina virtual                     | vm                   |
| Computadores conectados ao arco do Azure        | arcm-                |
| Conta de armazenamento da VM                  | stvm                 |
| IP público                           | pip-                 |
| Balanceador de carga (interno)            | ILB                 |
| Balanceador de carga (externo)            | Elb                 |
| NIC                                 | nic-                 |
| Cofre de chaves                           | kV                  |
| Cluster AKS                         | AKs                 |
| Contêiner AKS                       | telefonema                 |
| Barramento de Serviço                         | sb-                  |
| Fila do Barramento de Serviço                   | sbq-                 |
| Tópico do barramento de serviço                   | SBT                 |
| Plano do Serviço de Aplicativo                    | intenção                |
| Aplicativo Web                             | aplicação                 |
| Aplicativo de funções                        | Func                |
| Aplicativo lógico                           | lógica               |
| serviço de nuvem                       | era                 |
| Servidor de banco de dados SQL do Azure           | SQL                 |
| Banco de Dados SQL do Azure                  | sqldb-               |
| Banco de dados Cosmos DB                  | Cosmos              |
| Cache do Azure para cache Redis         | redis-               |
| Banco de dados MySQL                      | mysql-               |
| Banco de dados PostgreSQL                 | psql                |
| SQL Data Warehouse do Azure            | sqldw-               |
| SQL Server Stretch Database         | sqlstrdb-            |
| Conta de armazenamento                     | st                   |
| Azure StorSimple                    | ssimp                |
| Azure Search                        | srch-                |
| Serviços Cognitivos do Azure            | engrenagem                 |
| Workspace do Azure Machine Learning    | mlw-                 |
| Armazenamento do Azure Data Lake             | dls                  |
| Análise Azure Data Lake           | dla                  |
| Azure HDInsight – Spark             | hdis-                |
| Azure HDInsight – Hadoop            | hdihd-               |
| Azure HDInsight – Microsoft R Server          | hdir-                |
| Azure HDInsight – HBase             | hdihb-               |
| Power BI Embedded                   | PBI                 |
| Stream Analytics do Azure              | asa-                 |
| Fábrica de dados do Azure                  | ADF                 |
| Hub de Eventos                           | evh-                 |
| Hub IoT                             | IOT                 |
| Hubs de notificação                   | NTF                 |
| Namespace dos hubs de notificação         | ntfns-               |
| Espaço de Trabalho do Log Analytics             | Façam                 |
| Application Insights                | appi-                |
| Cofre dos Serviços de Recuperação             | rsv-                 |

### <a name="metadata-tags"></a>Marcas de metadados

Quando você aplica marcas de metadados aos seus recursos de nuvem, pode incluir informações sobre esses ativos que não poderiam ser incluídas no nome do recurso. Você pode usar essas informações para executar filtragem e relatórios mais sofisticados sobre os recursos. Convém que essas marcas incluam contexto sobre a carga de trabalho ou aplicativo associado, requisitos operacionais e informações de propriedade do recurso. Essas informações podem ser usadas pelas equipes empresariais ou de TI para encontrar recursos ou gerar relatórios sobre o uso e a cobrança de recursos.

Quais as marcas que você aplica a recursos e quais marcas são obrigatórias ou opcionais são diferentes entre organizações. A lista a seguir fornece exemplos de marcas comuns que capturam informações e contexto importantes sobre um recurso. Use esta lista como um ponto de partida para estabelecer suas próprias convenções de marcação.

| Nome da marca                  | DESCRIÇÃO                                                                                                                                                                                                    | Chave               | Valor de exemplo                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------|
| Nome do aplicativo          | Dê um nome ao aplicativo, ao serviço ou à carga de trabalho a que o recurso está associado.                                                                                                                                 | _ApplicationName_ | _{app name}_                                    |
| Nome do aprovador             | Pessoa responsável por aprovar custos relacionados a esse recurso.                                                                                                                                               | _Approver_        | _{email}_                                       |
| Orçamento necessário/aprovado  | Dinheiro alocado para este aplicativo, serviço ou carga de trabalho.                                                                                                                                                    | _BudgetAmount_    | _{\$}_                                          |
| Unidade de negócios             | Divisão de nível superior da sua empresa que tem a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, essa tag pode representar um único elemento organizacional corporativo ou compartilhado de nível superior. | _BusinessUnit_    | _Finanças_, _marketing_, _{nome do produto}_ , _Corp_, _compartilhado_ |
| Centro de custo               | O centro de custo de contabilidade associado a este recurso.                                                                                                                                                          | _CostCenter_      | _{number}_                                      |
| Recuperação de desastre         | Nível de importância empresarial do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                | _DR_              | _Missão crítica_, _crítica_, _essencial_         |
| Data de término do projeto   | Data quando o aplicativo, a carga de trabalho ou o serviço foi agendado para desativação.                                                                                                                                  | _EndDate_         | _{date}_                                        |
| Ambiente               | Ambiente de implantação do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                              | _Env_             | _Prod_, _dev_, _QA_, _estágio_, _teste_                    |
| Nome do proprietário                | Proprietário do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                                | _Proprietário_           | _{email}_                                       |
| Nome do solicitante            | Usuário que solicitou a criação deste aplicativo.                                                                                                                                                          | _Solicitante_       | _{email}_                                       |
| Classe de serviço             | Nível do contrato de nível de serviço do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                       | _ServiceClass_    | _Desenvolvimento_, _bronze_, _prata_, git _Gold_                     |
| Data de início do projeto | Data quando o aplicativo, carga de trabalho ou serviço foi implantado pela primeira vez.                                                                                                                                           | _StartDate_       | _{date}_                                        |

## <a name="sample-naming-convention"></a>Convenção de nomenclatura de exemplo

A seção a seguir fornece exemplos de esquemas de nomenclatura para tipos de recurso comuns do Azure implantados durante uma implantação de nuvem empresarial.

<!-- markdownlint-disable MD033 -->

### <a name="subscriptions"></a>Assinaturas

| Tipo de ativo   | Escopo                        | Formatar                                             | Exemplos                                     |
|--------------|------------------------------|----------------------------------------------------|----------------------------------------------|
| Subscription | Conta/Contrato Enterprise | \<Unidade de negócios\>-\<Tipo de assinatura\>-\<\#\#\#\> | <ul><li>mktg-prod-001 </li><li>corp-shared-001 </li><li>fin-client-001</li></ul> |

### <a name="resource-groups"></a>Grupos de recursos

| Tipo de ativo     | Escopo        | Formatar                                                     | Exemplos                                                                            |
|----------------|--------------|------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Resource group | Subscription | RG-\<nome do serviço ou aplicativo\>-\<tipo de assinatura\>-\<\#\#\#\> | <ul><li>rg-mktgsharepoint-prod-001 </li><li>rg-acctlookupsvc-share-001 </li><li>rg-ad-dir-services-shared-001</li></ul> |

### <a name="virtual-networking"></a>Rede Virtual

| Tipo de ativo               | Escopo           | Formatar                                                                | Exemplos                                                                                              |
|--------------------------|-----------------|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Rede Virtual do Azure          | Resource group  | vnet-\<Tipo de assinatura\>-\<Região\>-\<\#\#\#\>                      | <ul><li>vnet-shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-client-eastus2-001</li></ul>                                  |
| Gateway virtual de rede virtual     | Rede virtual | vnetgw-v-\<tipo de assinatura\>-\<região\>-\<\#\#\#\>                 | <ul><li>vnetgw-v-Shared-eastus2-001 </li><li>vnetgw-v-prod-westus-001 </li><li>vnetgw-v-Client-eastus2-001</li></ul>                   |
| Gateway local de rede virtual       | Gateway virtual | vnetgw-l-\<tipo de assinatura\>-\<região\>-\<\#\#\#\>                 | <ul><li>vnetgw-l-Shared-eastus2-001 </li><li>vnetgw-l-prod-westus-001 </li><li>vnetgw-l-Client-eastus2-001</li></ul>                   |
| Conexões site a site | Resource group  | cn-\<nome do gateway local\>-to-\<nome do gateway virtual\>                 | <ul><li>cn-l-gw-shared-eastus2-001-to-v-gw-shared-eastus2-001 </li><li>cn-l-gw-shared-eastus2-001-to-shared-westus-001</li></ul> |
| Conexões de rede virtual         | Resource group  | cn-\<subscription1\>\<region1\>-to-\<subscription2\>\<region2\>-      | <ul><li>cn-shared-eastus2-to-shared-westus </li><li>cn-prod-eastus2-to-prod-westus</li></ul>                                     |
| Sub-rede                   | Rede virtual | snet-\<subscription\>-\<subregion\>-\<\#\#\#\>                       | <ul><li>snet-shared-eastus2-001 </li><li>snet-prod-westus-001 </li><li>snet-client-eastus2-001</li></ul>                                  |
| Grupo de segurança de rede   | Sub-rede ou NIC   | nsg-\<nome da política ou appname\>-\<\#\#\#\>                             | <ul><li>nsg-weballow-001 </li><li>nsg-rdpallow-001 </li><li>nsg-sqlallow-001 </li><li>nsg-dnsbloked-001</li></ul>                                  |
| IP público                | Resource group  | pip-\<nome da VM ou do aplicativo\>-\<Ambiente\>-\<sub-região\>-\<\#\#\#\> | <ul><li>pip-dc1-shared-eastus2-001 </li><li>pip-hadoop-prod-westus-001</li></ul>                                                 |

### <a name="azure-virtual-machines"></a>Máquinas Virtuais do Azure

| Tipo de ativo         | Escopo          | Formatar                                                              | Exemplos                                                                             |
|--------------------|----------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Máquinas Virtuais do Azure    | Resource group | VM\<nome da política ou appname\>\<\#\#\#\>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Conta de armazenamento da VM | Global         | stvm\<tipo de desempenho\>\<appname ou prodname\>\<região\>\<\#\#\#\> | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Rótulo do DNS          | Global         | \<Um registro de VM\>.[\<região\>.cloudapp.azure.com]                  | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                        |
| Azure Load Balancer      | Resource group | lb-\<nome do aplicativo ou função\>\<Ambiente\>\<\#\#\#\>                    | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                          |
| NIC                | Resource group | nic-\<\#\#\>-\<vmname\>-\<assinatura\>\<\#\#\#\>                  | <ul><li>nic-01-dc1-shared-001 </li><li>nic-02-vmhadoop1-prod-001 </li><li>nic-02-vmtest1-client-001</li></ul>            |

### <a name="paas-services"></a>Serviços PaaS

| Tipo de ativo           | Escopo  | Formatar                                                              | Exemplos                                                                                 |
|----------------------|--------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Aplicativos Web do Azure       | Global | App-\<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{azurewebsites.net}] | <ul><li>app-navigator-prod-001.azurewebsites.net </li><li>app-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Funções do Azure      | Global | Func-\<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{azurewebsites.net}] | <ul><li>func-navigator-prod-001.azurewebsites.net </li><li>func-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Serviços de nuvem do Azure | Global | \<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{cloudapp.net}]       | <ul><li>could-navigator-prod-001.azurewebsites.net </li><li>could-accountlookup-dev-001.azurewebsites.net</li></ul>   |

### <a name="azure-service-bus"></a>Barramento de Serviço do Azure

| Tipo de ativo         | Escopo       | Formatar                                                     | Exemplos                           |
|--------------------|-------------|------------------------------------------------------------|------------------------------------|
| Barramento de Serviço do Azure        | Global      | sb-\<Nome do Aplicativo\>-\<Ambiente\>.[{servicebus.windows.net}] | <ul><li>sb-navigator-prod </li><li>sb-emissions-dev</li></ul> |
| Filas do Barramento de Serviço do Azure | Barramento de Serviço | sbq-\<descritor da consulta\>                                   | <ul><li>sbq-messagequery</li></ul>                   |
| Tópicos do barramento de serviço do Azure | Barramento de Serviço | SBT\<descritor de consulta\>                                   | <ul><li>SBT-MessageQuery</li></ul>                   |

### <a name="databases"></a>Bancos de dados

| Tipo de ativo                          | Escopo              | Formatar                                | Exemplos                                       |
|-------------------------------------|--------------------|---------------------------------------|------------------------------------------------|
| Servidor de banco de dados SQL do Azure           | Global             | SQL-\<nome do aplicativo\>-\<ambiente\>      | <ul><li>SQL-Navigator-prod </li><li>SQL-emissões-dev</li></ul>           |
| Banco de Dados SQL do Azure                  | Banco de Dados SQL do Azure | SQLDB-\<nome do banco de dados >-\<ambiente\>| <ul><li>SQLDB-Users-prod </li><li>SQLDB-usuários-dev</li></ul>               |
| Azure Cosmos DB                     | Global             | Cosmos-\<nome do aplicativo\>-\<ambiente\>   | <ul><li>Cosmos-Navigator-prod </li><li>Cosmos-emissões-dev</li></ul>       |
| Cache Redis do Azure               | Global             | redis-\<Nome do Aplicativo\>-\<Ambiente\>    | <ul><li>redis-navigator-prod </li><li>redis-emissions-dev</li></ul>       |
| Banco de Dados do Azure para MySQL            | Global             | mysql-\<Nome do Aplicativo\>-\<Ambiente\>    | <ul><li>mysql-navigator-prod </li><li>mysql-emissions-dev</li></ul>       |
| Banco de Dados do Azure para PostgreSQL       | Global             | psql-\<nome do aplicativo\>-\<ambiente\>     | <ul><li>psql-Navigator-prod </li><li>psql-emissões-dev</li></ul>         |
| SQL Data Warehouse do Azure            | Global             | sqldw-\<Nome do Aplicativo\>-\<Ambiente\>    | <ul><li>sqldw-navigator-prod </li><li>sqldw-emissions-dev</li></ul>       |
| SQL Server Stretch Database         | Banco de Dados SQL do Azure | sqlstrdb-\<Nome do Aplicativo\>-\<Ambiente\> | <ul><li>sqlstrdb-navigator-prod </li><li>sqlstrdb-emissions-dev</li></ul> |

### <a name="storage"></a>Armazenamento

| Tipo de ativo                              | Escopo  | Formatar                                                                        | Exemplos                                   |
|-----------------------------------------|--------|-------------------------------------------------------------------------------|--------------------------------------------|
| Conta de Armazenamento do Azure – uso geral     | Global | st\<nome do armazenamento\>\<\#\#\#\>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Conta de Armazenamento do Azure – logs de diagnóstico | Global | stdiag\<as duas primeiras letras do nome da assinatura e número\>\<região\>\<\#\#\#\> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                        | Global | ssimp\<Nome do Aplicativo\>\<Ambiente\>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="ai--machine-learning"></a>IA + Machine Learning

| Tipo de ativo                       | Escopo          | Formatar                            | Exemplos                               |
|----------------------------------|----------------|-----------------------------------|----------------------------------------|
| Azure Search                     | Global         | srch-\<Nome do Aplicativo\>-\<Ambiente\> | <ul><li>srch-navigator-prod </li><li>srch-emissions-dev</li></ul> |
| Serviços Cognitivos do Azure         | Resource group | engrenagem-\<nome do aplicativo\>-\<ambiente\>   | <ul><li>engrenagem-Navigator-prod </li><li>engrenagem-emissões-dev</li></ul>     |
| Workspace do Azure Machine Learning | Resource group | MLW-\<nome do aplicativo\>-\<ambiente\>   | <ul><li>MLW-Navigator-prod </li><li>MLW-emissões-dev</li></ul>     |

### <a name="analytics"></a>Análise

| Tipo de ativo                | Escopo  | Formatar                             | Exemplos                                 |
|---------------------------|--------|------------------------------------|------------------------------------------|
| Fábrica de dados do Azure        | Global | ADF-\<nome do aplicativo\>ambiente de \<\>    | <ul><li>ADF-Navigator-prod </li><li>ADF-emissões-dev</li></ul>     |
| Armazenamento do Azure Data Lake   | Global | dls\<Nome do Aplicativo\>\<Ambiente\>     | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>         |
| Análise Azure Data Lake | Global | dla\<Nome do Aplicativo\>\<Ambiente\>     | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>         |
| Azure HDInsight – Spark   | Global | hdis-\<Nome do Aplicativo\>-\<Ambiente\>  | <ul><li>hdis-navigator-prod </li><li>hdis-emissions-dev </li></ul>  |
| Azure HDInsight – Hadoop  | Global | hdihd-\<Nome do Aplicativo\>-\<Ambiente\> | <ul><li>hdihd-hadoop-prod </li><li>hdihd-emissions-dev</li></ul>    |
| Azure HDInsight – Microsoft R Server| Global | hdir-\<Nome do Aplicativo\>-\<Ambiente\>  | <ul><li>hdir-navigator-prod </li><li>hdir-emissions-dev</li></ul>   |
| Azure HDInsight – HBase   | Global | hdihb-\<Nome do Aplicativo\>-\<Ambiente\> | <ul><li>hdihb-navigator-prod </li><li>hdihb-emissions-dev</li></ul> |
| Power BI Embedded         | Global | PBI-\<nome do aplicativo\>\<ambiente\>    | <ul><li>PBI-Navigator-prod </li><li>PBI-emissões-dev</li></ul> |

### <a name="data-streams--internet-of-things-iot"></a>Data streams/Internet das Coisas (IoT)

| Tipo de ativo                         | Escopo          | Formatar                             | Exemplos                                 |
|------------------------------------|----------------|------------------------------------|------------------------------------------|
| Stream Analytics do Azure             | Resource group | asa-\<Nome do Aplicativo\>-\<Ambiente\>   | <ul><li>asa-navigator-prod </li><li>asa-emissions-dev</li></ul>     |
| Hub IoT do Azure                      | Global         | Nome do aplicativo IOT-\<\>-ambiente \<\>   | <ul><li>IOT-Navigator-prod </li><li>IOT-emissões-dev</li></ul>     |
| Hubs de eventos do Azure                   | Global         | evh-\<Nome do Aplicativo\>-\<Ambiente\>   | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>     |
| Hubs de Notificação do Azure            | Resource group | NTF-\<nome do aplicativo\>-\<ambiente\>   | <ul><li>NTF-Navigator-prod </li><li>NTF-emissões-dev</li></ul>     |
| Namespace dos Hubs de Notificação do Azure  | Global         | ntfns-\<nome do aplicativo\>-\<ambiente\> | <ul><li>ntfns-Navigator-prod </li><li>ntfns-emissões-dev</li></ul> |
