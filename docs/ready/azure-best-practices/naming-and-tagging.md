---
title: Convenções de nomenclatura e de marcação recomendadas
description: Conheça as recomendações detalhadas de nomenclatura e marcação de recursos destinadas especificamente ao suporte a esforços de adoção de nuvem empresarial.
author: BrianBlanchard
ms.author: brblanch
ms.date: 03/05/2020
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness, fasttrack-edit
ms.openlocfilehash: 119a0b64fe81e593404735e5ce6bc0c656ab23e2
ms.sourcegitcommit: 011332538dbc6774b732f7b9f2b89d6c8aa90c36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79023718"
---
<!-- cSpell:ignore eastus westus westeurope usgovia accountlookup messagequery -->

# <a name="recommended-naming-and-tagging-conventions"></a>Convenções de nomenclatura e de marcação recomendadas

Organize seus ativos de nuvem para dar suporte a requisitos de gerenciamento e contabilidade operacionais. As convenções de nomenclatura e de marcação de metadados bem definidas ajudam a localizar e gerenciar rapidamente os recursos. Essas convenções também ajudam a associar os custos de uso de nuvem com as equipes de negócios por meio de mecanismos de estorno e de contabilidade de reversão.

As diretrizes de Centro de Arquitetura do Azure para a [nomenclatura de regras e restrições para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) fornecem recomendações gerais e limitações de plataforma. A discussão a seguir estende essa orientação com recomendações mais detalhadas voltadas especificamente para o suporte a esforços de adoção de nuvem empresarial.

A alteração de nomes de recursos pode ser difícil. Estabeleça uma Convenção de nomenclatura abrangente antes de começar qualquer implantação de nuvem grande.

> [!NOTE]
> Cada negócio tem requisitos organizacionais e de gerenciamento diferentes. Essas recomendações fornecem um ponto de partida para discussões em suas equipes de adoção de nuvem.
>
> Conforme essas discussões continuarem, use o modelo a seguir para capturar as decisões de nomenclatura e marcação que você faz ao alinhar essas recomendações às suas necessidades de negócios específicas.
>
> Baixe o [modelo de acompanhamento de convenção de nomenclatura e de marcação](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Recursos de nomenclatura e de marcação

Uma estratégia de nomenclatura e de marcação inclui detalhes empresariais e operacionais como componentes de nomes de recursos e marcas de metadados:

- O lado comercial dessa estratégia garante que nomes de recursos e marcas incluam as informações organizacionais necessárias para identificar as equipes. Use um recurso junto com os proprietários empresariais responsáveis por custos de recursos.
- O lado operacional verifica se os nomes e marcas incluem informações que as equipes de TI usam para identificar a carga de trabalho, o aplicativo, o ambiente, a severidade e outras informações úteis para gerenciar recursos.

## <a name="resource-naming"></a>Nomenclatura de recursos

Uma convenção de nomenclatura efetiva monta nomes de recursos usando informações de recursos importantes como partes do nome de um recurso. Por exemplo, usando essas [convenções de nomenclatura recomendadas](#example-names), um recurso de IP público para uma carga de trabalho de produção do SharePoint é nomeado da seguinte maneira: `pip-sharepoint-prod-westus-001`.

Com base no nome, você pode identificar rapidamente o tipo de recurso, sua carga de trabalho associada, seu ambiente de implantação e a região do Azure que está hospedando-o.

### <a name="naming-scope"></a>Escopo de nomenclatura

Todos os tipos de recursos do Azure têm um escopo que define o nível que os nomes de recursos devem ser exclusivos. Um recurso deve ter um nome exclusivo dentro de seu escopo.

Por exemplo, uma rede virtual tem um escopo de grupo de recursos, o que significa que pode haver apenas uma rede chamada `vnet-prod-westus-001` em um determinado grupo de recursos. Outros grupos de recursos podem ter sua própria rede virtual chamada `vnet-prod-westus-001`. Sub-redes, para dar outro exemplo, têm como escopo redes virtuais, o que significa que cada sub-rede dentro de uma rede virtual deve ser nomeada exclusivamente.

Alguns nomes de recursos, como serviços PaaS com pontos de extremidade públicos ou rótulos DNS de máquina virtual, têm escopos globais, o que significa que eles devem ser exclusivos em toda a plataforma do Azure.

Nomes de recursos têm limites de comprimento. O balanceamento do contexto inserido em um nome com seu escopo e comprimento é importante quando você desenvolve suas convenções de nomenclatura. Para saber mais sobre regras de nomenclatura para caracteres permitidos, escopos e comprimentos de nome para tipos de recursos, confira [Convenções de nomenclatura para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming).

### <a name="recommended-naming-components"></a>Componentes de nomenclatura recomendados

Ao construir sua convenção de nomenclatura, identifique as principais partes de informações que você deseja refletir em um nome de recurso. Diferentes informações são relevantes para diferentes tipos de recurso. A lista a seguir fornece exemplos de informações úteis quando você cria nomes de recursos.

Mantenha o comprimento dos componentes de nomenclatura pequeno para evitar exceder os limites de comprimento de nome do recurso.

| Componente de nomenclatura            | DESCRIÇÃO                                                                                                                                                                                                      | Exemplos                                         |
|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| Unidade de negócios               | Divisão de nível superior da sua empresa que tem a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, esse componente pode representar um único elemento organizacional corporativo de nível superior. | _fin_, _mktg_, _product_, _it_, _corp_           |
| Tipo de assinatura           | Descrição resumida da finalidade da assinatura que contém o recurso. É geralmente dividida pelo tipo de ambiente de implantação ou cargas de trabalho específicas.                                                       | _prod_, _compartilhado_, _cliente_                       |
| Nome do aplicativo ou do serviço | Nome do aplicativo, da carga de trabalho ou do serviço do qual o recurso faz parte.                                                                                                                                    | _navigator_, _emissions_, _sharepoint_, _hadoop_ |
| Ambiente de implantação      | A fase do ciclo de vida de desenvolvimento da carga de trabalho compatível com o recurso.                                                                                                                              | _prod_, _dev_, _QA_, _estágio_, _teste_             |
| Região                      | A região do Azure em que o recurso é implantado.                                                                                                                                                                 | _westus_, _eastus2_, _westeurope_, _usgovia_     |

### <a name="recommended-resource-type-prefixes"></a>Prefixos de tipo de recurso recomendados

Cada carga de trabalho é composta por muitos recursos e serviços individuais. A incorporação de prefixos de tipo de recurso em seus nomes de recursos facilita a identificação visual de componentes de serviço ou aplicativo.

A lista a seguir fornece prefixos de tipo de recurso do Azure recomendados para usar quando você define suas convenções de nomenclatura.

<!-- cSpell:disable -->

### <a name="general"></a>Geral

| Tipo de ativo                      | Prefixo do nome |
|---------------------------------|-------------|
| Resource group                  | rg-         |
| Definição de política               | regras     |
| Instância do serviço de gerenciamento de API | APIM       |

### <a name="networking"></a>Rede

| Tipo de ativo                       | Prefixo do nome |
|----------------------------------|-------------|
| Rede virtual                  | vnet-       |
| Sub-rede                           | snet-       |
| NIC (adaptador de rede)          | nic-        |
| Endereço IP público                | pip-        |
| Balanceador de carga (interno)         | bin        |
| Balanceador de carga (externo)         | lbe-        |
| NSG (Grupo de Segurança de Rede)     | nsg-        |
| Grupo de segurança de aplicativo (ASG) | ASG        |
| Gateway de rede local            | lgw-        |
| Gateway de rede virtual          | vgw-        |
| Conexão VPN                   | cn-         |
| Gateway de Aplicativo              | agw-        |
| Tabela de rotas                      | rota      |
| Perfil do Gerenciador de Tráfego          | traf-       |

### <a name="compute-and-web"></a>Computação e Web

| Tipo de ativo                  | Prefixo do nome |
|-----------------------------|-------------|
| Máquina virtual             | vm          |
| Conjunto de escala de máquina virtual   | vmss       |
| Conjunto de disponibilidade            | avalia      |
| Conta de armazenamento da VM          | stvm        |
| Máquina conectada do Arc do Azure | arcm-       |
| Instância de contêiner          | ACI        |
| Cluster AKS                 | AKs        |
| Cluster do Service Fabric      | If         |
| Ambiente do serviço de aplicativo     | ASE        |
| Plano do Serviço de Aplicativo            | intenção       |
| Aplicativo Web                     | aplicação        |
| Aplicativo de funções                | Func       |
| serviço de nuvem               | era        |
| Hubs de Notificação           | NTF        |
| Namespace dos hubs de notificação | ntfns-      |

### <a name="databases"></a>Bancos de dados

| Tipo de ativo                     | Prefixo do nome |
|--------------------------------|-------------|
| Servidor de banco de dados SQL do Azure      | SQL        |
| Banco de Dados SQL do Azure             | sqldb-      |
| Banco de dados Cosmos DB             | Cosmos     |
| Cache do Azure para instância de Redis | redis-      |
| Banco de dados MySQL                 | mysql-      |
| Banco de dados PostgreSQL            | psql       |
| SQL Data Warehouse do Azure       | sqldw-      |
| SQL Server Stretch Database    | sqlstrdb-   |

### <a name="storage"></a>Armazenamento

| Tipo de ativo       | Prefixo do nome |
|------------------|-------------|
| Conta de armazenamento  | st          |
| Azure StorSimple | ssimp       |

### <a name="ai--machine-learning"></a>IA + Machine Learning

| Tipo de ativo                       | Prefixo do nome |
|----------------------------------|-------------|
| Pesquisa Cognitiva do Azure           | srch-       |
| Serviços Cognitivos do Azure         | engrenagem        |
| Workspace do Azure Machine Learning | mlw-        |

### <a name="analytics-and-iot"></a>Análise e IoT

| Tipo de ativo                      | Prefixo do nome |
|---------------------------------|-------------|
| Servidor de Azure Analysis Services  | como         |
| Espaço de trabalho Azure Databricks      | dbw-        |
| Stream Analytics do Azure          | asa-        |
| Fábrica de dados do Azure              | ADF        |
| Conta de Data Lake Store         | dls         |
| Conta de Data Lake Analytics     | dla         |
| Hub de Eventos                       | evh-        |
| HDInsight-cluster Hadoop      | Hadoop     |
| HDInsight-cluster HBase       | HBase      |
| Cluster HDInsight-Kafka       | Kafka      |
| Cluster HDInsight-Spark       | Spark      |
| Cluster HDInsight-Storm       | tempestade      |
| Cluster de serviços do HDInsight-ML | MLS        |
| Hub IoT                         | IOT        |
| Power BI Embedded               | PBI        |

### <a name="integration"></a>Integração

| Tipo de ativo        | Prefixo do nome |
|-------------------|-------------|
| Aplicativos lógicos        | lógica      |
| Barramento de Serviço       | sb-         |
| Fila do Barramento de Serviço | sbq-        |
| Tópico do barramento de serviço | SBT        |

### <a name="management-and-governance"></a>Gerenciamento e governança

| Tipo de ativo              | Prefixo do nome |
|-------------------------|-------------|
| Blueprint               | BP         |
| Cofre de chaves               | kV         |
| Espaço de trabalho do Log Analytics | Façam        |
| Application Insights    | appi-       |
| Cofre dos Serviços de Recuperação | rsv-        |

### <a name="migration"></a>Migração

| Tipo de ativo                          | Prefixo do nome |
|-------------------------------------|-------------|
| Projeto de migrações para Azure               | migr-       |
| Instância do serviço de migração de banco de dados | DMS        |
| Cofre dos Serviços de Recuperação             | rsv-        |

<!-- cSpell:enable -->

## <a name="metadata-tags"></a>Marcas de metadados

Quando você aplica marcas de metadados aos seus recursos de nuvem, pode incluir informações sobre esses ativos que não poderiam ser incluídas no nome do recurso. Você pode usar essas informações para executar filtragem e relatórios mais sofisticados sobre os recursos. Convém que essas marcas incluam contexto sobre a carga de trabalho ou aplicativo associado, requisitos operacionais e informações de propriedade do recurso. Essas informações podem ser usadas pelas equipes empresariais ou de TI para encontrar recursos ou gerar relatórios sobre o uso e a cobrança de recursos.

Quais as marcas que você aplica a recursos e quais marcas são obrigatórias ou opcionais são diferentes entre organizações. A lista a seguir fornece exemplos de marcas comuns que capturam informações e contexto importantes sobre um recurso. Use esta lista como um ponto de partida para estabelecer suas próprias convenções de marcação.

| Nome da marca                  | DESCRIÇÃO                                                                                                                                                                                                          | Chave               | Valor de exemplo                                              |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|------------------------------------------------------------|
| Nome do aplicativo          | Dê um nome ao aplicativo, ao serviço ou à carga de trabalho a que o recurso está associado.                                                                                                                                       | _ApplicationName_ | _{app name}_                                               |
| Nome do aprovador             | Pessoa responsável por aprovar custos relacionados a esse recurso.                                                                                                                                                     | _Approver_        | _{email}_                                                  |
| Orçamento necessário/aprovado  | Dinheiro alocado para este aplicativo, serviço ou carga de trabalho.                                                                                                                                                          | _BudgetAmount_    | _{\$}_                                                     |
| Unidade de negócios             | Divisão de nível superior da sua empresa que tem a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, essa tag pode representar um único elemento organizacional corporativo ou compartilhado de nível superior. | _BusinessUnit_    | _Finanças_, _marketing_, _{nome do produto}_ , _Corp_, _compartilhado_ |
| Centro de custo               | O centro de custo de contabilidade associado a este recurso.                                                                                                                                                                | _CostCenter_      | _{number}_                                                 |
| Recuperação de desastre         | Nível de importância empresarial do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                       | _DR_              | _Missão crítica_, _crítica_, _essencial_                |
| Data de término do projeto   | Data quando o aplicativo, a carga de trabalho ou o serviço foi agendado para desativação.                                                                                                                                         | _EndDate_         | _{date}_                                                   |
| Ambiente               | Ambiente de implantação do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                     | _Env_             | _Prod_, _dev_, _QA_, _estágio_, _teste_                       |
| Nome do proprietário                | Proprietário do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                                      | _Proprietário_           | _{email}_                                                  |
| Nome do solicitante            | Usuário que solicitou a criação deste aplicativo.                                                                                                                                                                 | _Solicitante_       | _{email}_                                                  |
| Classe de serviço             | Nível do contrato de nível de serviço do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                              | _ServiceClass_    | _Desenvolvimento_, _bronze_, _prata_, _ouro_                          |
| Data de início do projeto | Data quando o aplicativo, carga de trabalho ou serviço foi implantado pela primeira vez.                                                                                                                                                  | _StartDate_       | _{date}_                                                   |

## <a name="example-names"></a>Nomes de exemplo

A seção a seguir fornece alguns exemplos de nomes para tipos de recursos comuns do Azure em uma implantação de nuvem corporativa.

<!-- cSpell:disable -->

<!-- markdownlint-disable MD024 MD033 -->

### <a name="example-names-general"></a>Nomes de exemplo: geral

| Tipo de ativo                      | Escopo                              | Formatar                                                      | Exemplos                                                                                                                |
|---------------------------------|------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| Subscription                    | Considerar <br/>Contrato Enterprise | \<Unidade de negócios\>-\<Tipo de assinatura\>-\<\#\#\#\>          | <ul><li>mktg-prod-001 </li><li>corp-shared-001 </li><li>fin-client-001</li></ul>                                        |
| Resource group                  | Subscription                       | RG-\<nome do serviço ou aplicativo\>-\<tipo de assinatura\>-\<\#\#\#\> | <ul><li>rg-mktgsharepoint-prod-001 </li><li>rg-acctlookupsvc-share-001 </li><li>rg-ad-dir-services-shared-001</li></ul> |
| Instância do serviço de gerenciamento de API | Global                             | APIM-\<nome do aplicativo ou do serviço\>                                | APIM-Navigator-prod                                                                                                     |

### <a name="example-names-networking"></a>Nomes de exemplo: rede

| Tipo de ativo                   | Escopo           | Formatar                                                               | Exemplos                                                                                                                      |
|------------------------------|-----------------|----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Rede virtual              | Resource group  | vnet-\<Tipo de assinatura\>-\<Região\>-\<\#\#\#\>                     | <ul><li>vnet-shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-client-eastus2-001</li></ul>                      |
| Sub-rede                       | Rede virtual | snet-\<subscription\>-\<subregion\>-\<\#\#\#\>                       | <ul><li>snet-shared-eastus2-001 </li><li>snet-prod-westus-001 </li><li>snet-client-eastus2-001</li></ul>                      |
| NIC (adaptador de rede)      | Resource group  | nic-\<\#\#\>-\<vmname\>-\<assinatura\>\<\#\#\#\>                   | <ul><li>nic-01-dc1-shared-001 </li><li>nic-02-vmhadoop1-prod-001 </li><li>nic-02-vmtest1-client-001</li></ul>                 |
| Endereço IP público            | Resource group  | pip-\<nome da VM ou do aplicativo\>-\<Ambiente\>-\<sub-região\>-\<\#\#\#\> | <ul><li>pip-dc1-shared-eastus2-001 </li><li>pip-hadoop-prod-westus-001</li></ul>                                              |
| Balanceador de carga                | Resource group  | lb-\<nome do aplicativo ou função\>\<Ambiente\>\<\#\#\#\>                     | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                                        |
| NSG (Grupo de Segurança de Rede) | Sub-rede ou NIC   | NSG-nome da política de\<ou nome do aplicativo\>-\<\#\#\#\>                           | <ul><li>nsg-weballow-001 </li><li>nsg-rdpallow-001 </li><li>nsg-sqlallow-001 </li><li>nsg-dnsbloked-001</li></ul>             |
| Gateway de rede local        | Gateway virtual | LGW-\<tipo de assinatura\>-\<região\>-\<\#\#\#\>                      | <ul><li>LGW-Shared-eastus2-001 </li><li>LGW-prod-westus-001 </li><li>LGW-Client-eastus2-001</li></ul>                         |
| Gateway de rede virtual      | Rede virtual | vgw-\<tipo de assinatura\>-\<região\>-\<\#\#\#\>                      | <ul><li>vgw-Shared-eastus2-001 </li><li>vgw-prod-westus-001 </li><li>vgw-Client-eastus2-001</li></ul>                         |
| Conexão site a site      | Resource group  | cn-\<nome do gateway local\>-to-\<nome do gateway virtual\>                | <ul><li>CN-LGW-Shared-eastus2-001-to-vgw-Shared-eastus2-001 </li><li>CN-LGW-Shared-eastus2-001-to-Shared-oesteus-001</li></ul> |
| Conexão VPN               | Resource group  | cn-\<subscription1\>\<region1\>-to-\<subscription2\>\<region2\>-     | <ul><li>cn-shared-eastus2-to-shared-westus </li><li>cn-prod-eastus2-to-prod-westus</li></ul>                                  |
| Tabela de rotas                  | Resource group  | nome da tabela de rotas de\<de rota\>                                           | <ul><li>lb-navigator-prod-001 </li><li>lb-sharepoint-dev-001</li></ul>                                                        |
| Rótulo do DNS                    | Global          | \<Um registro de VM\>.[\<região\>.cloudapp.azure.com]                   | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                                      |

### <a name="example-names-compute-and-web"></a>Nomes de exemplo: computação e Web

| Tipo de ativo                  | Escopo          | Formatar                                                              | Exemplos                                                                                                                          |
|-----------------------------|----------------|---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Máquina virtual             | Resource group | VM\<nome da política ou appname\>\<\#\#\#\>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Conta de armazenamento da VM          | Global         | stvm\<tipo de desempenho\>\<appname ou prodname\>\<região\>\<\#\#\#\> | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Aplicativo Web                     | Global         | App-\<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{azurewebsites.net}]   | <ul><li>app-navigator-prod-001.azurewebsites.net </li><li>app-accountlookup-dev-001.azurewebsites.net</li></ul>                   |
| Aplicativo de funções                | Global         | Func-\<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{azurewebsites.net}]  | <ul><li>func-navigator-prod-001.azurewebsites.net </li><li>func-accountlookup-dev-001.azurewebsites.net</li></ul>                 |
| serviço de nuvem               | Global         | \<nome do aplicativo\>-\<ambiente\>-\<\#\#\#\>. [{cloudapp.net}]        | <ul><li>could-navigator-prod-001.azurewebsites.net </li><li>could-accountlookup-dev-001.azurewebsites.net</li></ul>                   |
| Hub de notificação            | Resource group | NTF-\<nome do aplicativo\>-\<ambiente\>                                    | <ul><li>NTF-Navigator-prod </li><li>NTF-emissões-dev</li></ul>                                                                   |
| Namespace dos hubs de notificação | Global         | ntfns-\<nome do aplicativo\>-\<ambiente\>                                  | <ul><li>ntfns-Navigator-prod </li><li>ntfns-emissões-dev</li></ul>                                                               |

### <a name="example-names-databases"></a>Nomes de exemplo: bancos de dados

| Tipo de ativo                     | Escopo              | Formatar                                 | Exemplos                                                                  |
|--------------------------------|--------------------|----------------------------------------|---------------------------------------------------------------------------|
| Servidor de banco de dados SQL do Azure      | Global             | SQL-\<nome do aplicativo\>-\<ambiente\>       | <ul><li>SQL-Navigator-prod </li><li>SQL-emissões-dev</li></ul>           |
| Banco de Dados SQL do Azure             | Banco de Dados SQL do Azure | SQLDB-\<nome do banco de dados >-\<ambiente\> | <ul><li>SQLDB-Users-prod </li><li>SQLDB-usuários-dev</li></ul>               |
| Banco de dados Cosmos DB             | Global             | Cosmos-\<nome do aplicativo\>-\<ambiente\>    | <ul><li>Cosmos-Navigator-prod </li><li>Cosmos-emissões-dev</li></ul>     |
| Cache do Azure para instância de Redis | Global             | redis-\<Nome do Aplicativo\>-\<Ambiente\>     | <ul><li>redis-navigator-prod </li><li>redis-emissions-dev</li></ul>       |
| Banco de dados MySQL                 | Global             | mysql-\<Nome do Aplicativo\>-\<Ambiente\>     | <ul><li>mysql-navigator-prod </li><li>mysql-emissions-dev</li></ul>       |
| Banco de dados PostgreSQL            | Global             | psql-\<nome do aplicativo\>-\<ambiente\>      | <ul><li>psql-Navigator-prod </li><li>psql-emissões-dev</li></ul>         |
| SQL Data Warehouse do Azure       | Global             | sqldw-\<Nome do Aplicativo\>-\<Ambiente\>     | <ul><li>sqldw-navigator-prod </li><li>sqldw-emissions-dev</li></ul>       |
| SQL Server Stretch Database    | Banco de Dados SQL do Azure | sqlstrdb-\<Nome do Aplicativo\>-\<Ambiente\>  | <ul><li>sqlstrdb-navigator-prod </li><li>sqlstrdb-emissions-dev</li></ul> |

### <a name="example-names-storage"></a>Nomes de exemplo: armazenamento

| Tipo de ativo                        | Escopo  | Formatar                                                                        | Exemplos                                                              |
|-----------------------------------|--------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| Conta de armazenamento (uso geral)     | Global | st\<nome do armazenamento\>\<\#\#\#\>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Conta de armazenamento (logs de diagnóstico) | Global | stdiag\<as duas primeiras letras do nome da assinatura e número\>\<região\>\<\#\#\#\> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                  | Global | ssimp\<Nome do Aplicativo\>\<Ambiente\>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="example-names-ai--machine-learning"></a>Nomes de exemplo: ia + Machine Learning

| Tipo de ativo                       | Escopo          | Formatar                            | Exemplos                                                          |
|----------------------------------|----------------|-----------------------------------|-------------------------------------------------------------------|
| Pesquisa Cognitiva do Azure           | Global         | srch-\<Nome do Aplicativo\>-\<Ambiente\> | <ul><li>srch-navigator-prod </li><li>srch-emissions-dev</li></ul> |
| Serviços Cognitivos do Azure         | Resource group | engrenagem-\<nome do aplicativo\>-\<ambiente\>  | <ul><li>engrenagem-Navigator-prod </li><li>engrenagem-emissões-dev</li></ul>   |
| Workspace do Azure Machine Learning | Resource group | MLW-\<nome do aplicativo\>-\<ambiente\>  | <ul><li>MLW-Navigator-prod </li><li>MLW-emissões-dev</li></ul>   |

### <a name="example-names-analytics-and-iot"></a>Nomes de exemplo: análise e IoT

| Tipo de ativo                  | Escopo          | Formatar                              | Exemplos                                                              |
|-----------------------------|----------------|-------------------------------------|-----------------------------------------------------------------------|
| Fábrica de dados do Azure          | Global         | ADF-\<nome do aplicativo\>ambiente de \<\>     | <ul><li>ADF-Navigator-prod </li><li>ADF-emissões-dev</li></ul>       |
| Stream Analytics do Azure      | Resource group | asa-\<Nome do Aplicativo\>-\<Ambiente\>    | <ul><li>asa-navigator-prod </li><li>asa-emissions-dev</li></ul>       |
| Conta de Data Lake Analytics | Global         | dla\<Nome do Aplicativo\>\<Ambiente\>      | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>           |
| Conta de Data Lake Storage   | Global         | dls\<Nome do Aplicativo\>\<Ambiente\>      | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>           |
| Hub de Eventos                   | Global         | evh-\<Nome do Aplicativo\>-\<Ambiente\>    | <ul><li>evh-navigator-prod </li><li>evh-emissions-dev</li></ul>       |
| HDInsight-cluster HBase   | Global         | HBase-\<nome do aplicativo\>-\<ambiente\>  | <ul><li>HBase-Navigator-prod </li><li>HBase-emissões-dev</li></ul>   |
| HDInsight-cluster Hadoop  | Global         | Hadoop-\<nome do aplicativo\>-\<ambiente\> | <ul><li>Hadoop-Navigator-prod </li><li>Hadoop-emissões-dev</li></ul> |
| Cluster HDInsight-Spark   | Global         | Spark-\<nome do aplicativo\>-\<ambiente\>  | <ul><li>Spark-Navigator-prod </li><li>Spark-emissões-dev </li></ul>  |
| Hub IoT                     | Global         | Nome do aplicativo IOT-\<\>-ambiente \<\>    | <ul><li>IOT-Navigator-prod </li><li>IOT-emissões-dev</li></ul>       |
| Power BI Embedded           | Global         | PBI-\<nome do aplicativo\>\<ambiente\>     | <ul><li>PBI-Navigator-prod </li><li>PBI-emissões-dev</li></ul>       |

### <a name="example-names-integration"></a>Nomes de exemplo: integração

| Tipo de ativo        | Escopo       | Formatar                                                     | Exemplos                                                      |
|-------------------|-------------|------------------------------------------------------------|---------------------------------------------------------------|
| Barramento de Serviço       | Global      | sb-\<Nome do Aplicativo\>-\<Ambiente\>.[{servicebus.windows.net}] | <ul><li>sb-navigator-prod </li><li>sb-emissions-dev</li></ul> |
| Fila do Barramento de Serviço | Barramento de Serviço | sbq-\<descritor da consulta\>                                   | <ul><li>sbq-messagequery</li></ul>                            |
| Tópico do barramento de serviço | Barramento de Serviço | SBT\<descritor de consulta\>                                   | <ul><li>SBT-MessageQuery</li></ul>                            |
