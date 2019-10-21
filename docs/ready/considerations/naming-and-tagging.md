---
title: 'Pronto: convenções de nomenclatura e marcação recomendadas'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Este artigo fornece recomendações detalhadas de nomenclatura e marcação de recursos destinados especificamente ao suporte a esforços de adoção de nuvem empresarial.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.custom: readiness
ms.openlocfilehash: 242b397312fe466670d3f1a315059f72447b300b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548845"
---
# <a name="ready-recommended-naming-and-tagging-conventions"></a>Pronto: convenções de nomenclatura e marcação recomendadas

Organizar ativos baseados em nuvem de maneiras que auxiliam o gerenciamento operacional e os requisitos de contabilidade de suporte é um desafio comum que enfrenta grandes esforços de adoção de nuvem. Aplicando convenções de nomenclatura bem definidas e de marcação de metadados a recursos hospedados na nuvem, a equipe de ti pode localizar e gerenciar recursos rapidamente. Nomes e marcas bem definidos também ajudam a alinhar os custos de uso da nuvem com as equipes de negócios usando os mecanismos de estorno e de contabilidade de reversão.

As regras de [nomenclatura do centro de arquitetura do Azure e as restrições das diretrizes de recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) fornecem recomendações gerais e limitações da plataforma. A discussão a seguir estende essa orientação genérica com recomendações mais detalhadas voltadas especificamente para o suporte a esforços de adoção de nuvem empresarial.

Os nomes de recursos podem ser difíceis de alterar. Torne-o uma prioridade para que suas equipes de adoção de nuvem estabeleçam uma Convenção de nomenclatura abrangente antes de começar qualquer implantação de nuvem grande.

> [!NOTE]
> Cada empresa tem diferentes requisitos organizacionais e de gerenciamento. As recomendações neste artigo servem como ponto de partida para discussões em suas equipes de adoção de nuvem.
>
> À medida que essas discussões progredirem, use o modelo a seguir para capturar as decisões de nomenclatura e marcação que você faz ao alinhar essas recomendações às suas necessidades de negócios específicas.
>
> Baixe o [modelo de controle de nomenclatura e marcação de Convenção](https://archcenter.blob.core.windows.net/cdn/fusion/readiness/CAF%20Readiness%20Naming%20and%20Tagging%20tracking%20template.xlsx).

## <a name="naming-and-tagging-resources"></a>Nomenclatura e marcação de recursos

Uma estratégia de nomenclatura e marcação inclui detalhes comerciais e operacionais como componentes de nomes de recursos e marcas de metadados:

- O lado relacionado aos negócios dessa estratégia garante que nomes e marcas de recursos incluam as informações organizacionais necessárias para identificar as equipes. Use um recurso junto com os proprietários de negócios responsáveis pelos custos de recursos.
- O lado operacional garante que os nomes e as marcas incluem informações que as equipes de ti usam para identificar a carga de trabalho, o aplicativo, o ambiente, a criticalidade e outras informações úteis para o gerenciamento de recursos.

### <a name="resource-naming"></a>Nomeação de recursos

Uma Convenção de nomenclatura efetiva monta nomes de recursos usando informações de recursos importantes como partes do nome de um recurso. Por exemplo, usando as convenções de nomenclatura recomendadas discutidas [posteriormente neste artigo](#sample-naming-convention), um recurso de IP público para uma carga de trabalho de produção do SharePoint é nomeado da seguinte maneira: `pip-sharepoint-prod-westus-001`.

A partir do nome, você pode identificar rapidamente o tipo do recurso, sua carga de trabalho associada, seu ambiente de implantação e a região do Azure que o hospeda.

#### <a name="naming-scope"></a>Escopo de nomenclatura

Todos os tipos de recursos do Azure têm um escopo que define o nível que os nomes de recursos devem ser exclusivos. Um recurso deve ter um nome exclusivo dentro de seu escopo.

Por exemplo, uma rede virtual tem um escopo de grupo de recursos, o que significa que pode haver apenas uma rede chamada `vnet-prod-westus-001` em um determinado grupo de recursos. Outros grupos de recursos podem ter sua própria rede virtual chamada `vnet-prod-westus-001`. Sub-redes, para fornecer outro exemplo, têm escopo para redes virtuais, o que significa que cada sub-rede em uma rede virtual deve ser nomeada exclusivamente.

Alguns nomes de recursos, como serviços PaaS com pontos de extremidade públicos ou rótulos de DNS de máquina virtual, têm escopos globais, o que significa que eles devem ser exclusivos em toda a plataforma do Azure.

Nomes de recursos têm limites de comprimento. O balanceamento do contexto inserido em um nome com seu escopo e comprimento é importante quando você desenvolve suas convenções de nomenclatura. Para obter mais informações sobre regras de nomenclatura para caracteres permitidos, escopos e comprimentos de nome para tipos de recursos, consulte [convenções de nomenclatura para recursos do Azure](https://docs.microsoft.com/azure/architecture/best-practices/naming-conventions).

#### <a name="recommended-naming-components"></a>Componentes de nomenclatura recomendados

Ao construir sua Convenção de nomenclatura, identifique as principais partes de informações que você deseja refletir em um nome de recurso. Informações diferentes são relevantes para diferentes tipos de recursos. A lista a seguir fornece exemplos de informações que são úteis quando você constrói nomes de recursos.

Mantenha o comprimento dos componentes de nomenclatura curtos para evitar exceder os limites de comprimento do nome do recurso.

| Componente de nomenclatura | Descrição | Exemplos |
| --- | --- | --- |
| Unidade de negócios | Divisão de nível superior da sua empresa que possui a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, esse componente pode representar um único elemento organizacional de nível superior corporativo. | *Fin*, *mktg*, *produto*, *ti*, *Corp* |
| Tipo de assinatura | Descrição resumida da finalidade da assinatura que contém o recurso. Frequentemente dividido por tipo de ambiente de implantação ou cargas de trabalho específicas. | *prod,* s*hados, cliente* |
| Nome do aplicativo ou do serviço | Nome do aplicativo, da carga de trabalho ou do serviço do qual o recurso faz parte. | *navegador*, *emissões*, *SharePoint*, *Hadoop* |
| Ambiente de implantação | O estágio do ciclo de vida de desenvolvimento da carga de trabalho com suporte do recurso. | *prod, dev, QA, estágio, teste* |
| Região | A região do Azure em que o recurso é implantado. | *westus, eastus2, westeurope, usgovia* |

#### <a name="recommended-resource-type-prefixes"></a>Prefixos de tipo de recurso recomendados

Cada carga de trabalho pode consistir em muitos recursos e serviços individuais. A incorporação de prefixos de tipo de recurso em seus nomes de recursos facilita a identificação visual de aplicativos ou componentes de serviço.

A lista a seguir fornece prefixos de tipo de recurso do Azure recomendados para usar ao definir suas convenções de nomenclatura.

| Tipo de recurso                       | Prefixo do nome do recurso |
| ----------------------------------- | -------------------- |
| Grupo de recursos                      | RT                  |
| Rede Virtual do Azure               | virtual                |
| Gateway de rede virtual             | vnet-GW-             |
| Conexão de gateway                  | Hong                  |
| Redes                              | NIAD                |
| Grupo de segurança de rede              | NSG                 |
| Tabela de rotas                         | rota               |
| Máquinas Virtuais do Azure              | VM                  |
| Conta de armazenamento de VM                  | stvm                 |
| IP público                           | pontos                 |
| Balanceador de carga do Azure                 | lb                  |
| NIC                                 | NIC                 |
| Azure Key Vault                     | kV                  |
| Serviço do Kubernetes do Azure            | AKs                 |
| Service Bus do Azure                   | SB                  |
| Filas do barramento de serviço do Azure            | sbq-                 |
| Aplicativos de serviço Azure App              | azapp-               |
| Azure Functions aplicativos                | azfun-               |
| Serviços de nuvem do Azure                | azcs-                |
| Banco de dados SQL do Azure                  | SQLDB               |
| Azure Cosmos DB (anteriormente Azure DocumentDB) | cosdb-               |
| Cache Redis do Azure               | Redis               |
| Banco de Dados do Azure para MySQL            | MySQL               |
| Azure SQL Data Warehouse            | sqldw               |
| SQL Server Stretch Database         | sqlstrdb-            |
| Armazenamento do Azure                       | arma                 |
| Azure StorSimple                    | ssimp                |
| Azure Search                        | srch-                |
| Serviços Cognitivos do Azure            | CS                  |
| Espaço de trabalho Azure Machine Learning    | AML                 |
| Azure Data Lake Store             | DL                  |
| Azure Data Lake Analytics           | dla                  |
| Azure HDInsight-Spark             | hdis                |
| Azure HDInsight-Hadoop            | hdihd-               |
| Azure HDInsight-servidor R          | hdir-                |
| Azure HDInsight-HBase             | hdihb-               |
| Power BI Embedded                   | pbiemb               |
| Azure Stream Analytics              | asa                 |
| Azure Data Factory                  | ativo                  |
| Hubs de Eventos do Azure                    | evh-                 |
| Hub IoT do Azure                       | aih-                 |
| Hubs de Notificação do Azure             | anh-                 |
| Namespace dos hubs de notificação do Azure   | anhns-               |

### <a name="metadata-tags"></a>Marcas de metadados

Ao aplicar marcas de metadados aos seus recursos de nuvem, você pode incluir informações sobre os ativos que não puderam ser incluídos no nome do recurso. Você pode usar essas informações para executar filtragem e relatórios mais sofisticados sobre os recursos. Você deseja que essas marcas incluam contexto sobre a carga de trabalho ou o aplicativo associado do recurso, requisitos operacionais e informações de propriedade. Essas informações podem ser usadas pelas equipes de ti ou de negócios para encontrar recursos ou gerar relatórios sobre o uso e a cobrança de recursos.

Quais marcas você aplica aos recursos e quais marcas são necessárias ou opcionais diferem entre as organizações. A lista a seguir fornece exemplos de marcas comuns que capturam contexto e informações importantes sobre um recurso. Use esta lista como um ponto de partida para estabelecer suas próprias convenções de marcação.

| Nome da marca                  | Descrição                                                                                                                                                                                                    | Chave               | Valor de exemplo                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------|
| Nome do aplicativo          | Nome do aplicativo, serviço ou carga de trabalho ao qual o recurso está associado.                                                                                                                                 | *ApplicationName* | *{nome do aplicativo}*                                    |
| Nome do aprovador             | Pessoa responsável por aprovar os custos relacionados a esse recurso.                                                                                                                                               | *Aprovador*        | *enviando*                                       |
| Orçamento necessário/aprovado  | Dinheiro alocado para este aplicativo, serviço ou carga de trabalho.                                                                                                                                                    | *BudgetAmount*    | *{\$}*                                          |
| Unidade de negócios             | Divisão de nível superior da sua empresa que possui a assinatura ou a carga de trabalho à qual o recurso pertence. Em organizações menores, essa marca pode representar um único elemento organizacional corporativo ou compartilhado de nível superior. | *BusinessUnit*    | *Finanças, MARKETING, {nome do produto}, CORP, compartilhado* |
| Centro de custo               | Centro de custo contábil associado a este recurso.                                                                                                                                                          | *CostCenter*      | *automática*                                      |
| Recuperação de desastre         | A importância comercial do aplicativo, da carga de trabalho ou do serviço.                                                                                                                                                | *Recovery*              | *Missão crítica, crítica, essencial*         |
| Data de término do projeto   | Data em que o aplicativo, a carga de trabalho ou o serviço está agendado para desativação.                                                                                                                                  | *Término*         | *Date*                                        |
| Ambiente               | Ambiente de implantação do aplicativo, carga de trabalho ou serviço.                                                                                                                                              | *Variável*             | *Prod, dev, QA, estágio, teste*                    |
| Nome do proprietário                | Proprietário do aplicativo, carga de trabalho ou serviço.                                                                                                                                                                | *Proprietário*           | *enviando*                                       |
| Nome do solicitante            | Usuário que solicitou a criação deste aplicativo.                                                                                                                                                          | *Solicitante*       | *enviando*                                       |
| Classe de serviço             | Nível de contrato de nível de serviço do aplicativo, carga de trabalho ou serviço.                                                                                                                                       | *Classe*    | *Desenvolvimento, bronze, prata, ouro*                     |
| Data de início do projeto | Data em que o aplicativo, a carga de trabalho ou o serviço foi implantado pela primeira vez.                                                                                                                                           | *StartDate*       | *Date*                                        |

## <a name="sample-naming-convention"></a>Convenção de nomenclatura de exemplo

A seção a seguir fornece exemplos de esquemas de nomenclatura para tipos de recursos comuns do Azure que são implantados durante uma implantação de nuvem empresarial.

<!-- markdownlint-disable MD033 -->

### <a name="subscriptions"></a>Assinaturas

| Tipo de ativo   | Escopo                        | ao                                             | Exemplos                                     |
|--------------|------------------------------|----------------------------------------------------|----------------------------------------------|
| Scriçõe | Conta/Enterprise Agreement | \<Business unidade \> - \<Subscription tipo \> - \< \# \# \# | <ul><li>mktg-prod-001 </li><li>Corp-compartilhado-001 </li><li>Fin-cliente-001</li></ul> |

### <a name="resource-groups"></a>Grupos de recursos

| Tipo de ativo     | Escopo        | ao                                                     | Exemplos                                                                            |
|----------------|--------------|------------------------------------------------------------|-------------------------------------------------------------------------------------|
| Grupo de recursos | Scriçõe | RG-\<App/Service Name \> - \<Subscription tipo \> - \< \# \# \# 0 | <ul><li>RG-mktgsharepoint-prod-001 </li><li>RG-acctlookupsvc-share-001 </li><li>RG-ad-Dir-Services-Shared-001</li></ul> |

### <a name="virtual-networking"></a>Rede virtual

| Tipo de ativo               | Escopo           | ao                                                                | Exemplos                                                                                              |
|--------------------------|-----------------|-----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Rede Virtual do Azure          | Grupo de recursos  | vnet-\<Subscription tipo \> - \<Region \> - \< \# \# \# 0                      | <ul><li>vnet-Shared-eastus2-001 </li><li>vnet-prod-westus-001 </li><li>vnet-Client-eastus2-001</li></ul>                                  |
| Gateway virtual de rede virtual     | rede virtual | vnet-GW-v-\<Subscription tipo \> - \<Region \> - \< \# \# \# 0                 | <ul><li>vnet-GW-v-Shared-eastus2-001 </li><li>vnet-GW-v-prod-westus-001 </li><li>vnet-GW-v-Client-eastus2-001</li></ul>                   |
| Gateway local da rede virtual       | Gateway virtual | vnet-GW-l-\<Subscription tipo \> - \<Region \> - \< \# \# \# 0                 | <ul><li>vnet-GW-l-Shared-eastus2-001 </li><li>vnet-GW-l-prod-westus-001 </li><li>vnet-GW-l-Client-eastus2-001</li></ul>                   |
| Conexões site a site | Grupo de recursos  | CN-\<local nome do gateway \>-to-\<virtual nome do gateway \>                 | <ul><li>CN-l-GW-Shared-eastus2-001-to-v-GW-Shared-eastus2-001 </li><li>CN-l-GW-Shared-eastus2-001-to-Shared-oesteus-001</li></ul> |
| Conexões de rede virtual         | Grupo de recursos  | CN-\<subscription1 \> \<region1 \>-para-\<subscription2 \> \<region2 \> -      | <ul><li>CN-Shared-eastus2 para compartilhado-westus </li><li>CN-prod-eastus2-to-prod-westus</li></ul>                                     |
| Redes                   | rede virtual | NIAD-\<subscription \> - \<subregion \> - \< \# \# \# 0                       | <ul><li>NIAD-Shared-eastus2-001 </li><li>NIAD-prod-westus-001 </li><li>NIAD-Client-eastus2-001</li></ul>                                  |
| Grupo de segurança de rede   | Sub-rede ou NIC   | NSG-\<policy Name ou AppName \> - \< \# \# \# \>                             | <ul><li>NSG-weballow-001 </li><li>NSG-rdpallow-001 </li><li>NSG-sqlallow-001 </li><li>NSG-dnsbloked-001</li></ul>                                  |
| IP público                | Grupo de recursos  | Pip-\<vm nome ou nome do aplicativo \> - \<Environment \> - \<subregion \> - \< 0 1 2 3 | <ul><li>Pip-DC1-Shared-eastus2-001 </li><li>Pip-Hadoop-prod-westus-001</li></ul>                                                 |

### <a name="azure-virtual-machines"></a>Máquinas Virtuais do Azure

| Tipo de ativo         | Escopo          | ao                                                              | Exemplos                                                                             |
|--------------------|----------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| Máquinas Virtuais do Azure    | Grupo de recursos | nome do \<policy da VM ou AppName \> \< \# \# \# \>                              | <ul><li>vmnavigator001 </li><li>vmsharepoint001 </li><li>vmsqlnode001 </li><li>vmhadoop001</li></ul>                              |
| Conta de armazenamento de VM | Global         | STVM \<performance Type \> \<appname ou prodname \> \<region \> \< \# \# \# 0 | <ul><li>stvmstcoreeastus2001 </li><li>stvmpmcoreeastus2001 </li><li>stvmstplmeastus2001 </li><li>stvmsthadoopeastus2001</li></ul> |
| Rótulo DNS          | Global         | \<A registro de \> da VM. [\<region \>. cloudapp.azure.com]                  | <ul><li>dc1.westus.cloudapp.azure.com </li><li>web1.eastus2.cloudapp.azure.com</li></ul>                        |
| Balanceador de carga do Azure      | Grupo de recursos | lb-\<app nome ou função \> \<Environment \> \< \# \# \# \>                    | <ul><li>lb-Navigator-prod-001 </li><li>lb-SharePoint-dev-001</li></ul>                                          |
| NIC                | Grupo de recursos | NIC-\< \# \# \> - \<vmname \> - \<subscription \> 0 1 2 3 4                  | <ul><li>NIC-01-DC1-Shared-001 </li><li>NIC-02-vmhadoop1-prod-001 </li><li>NIC-02-vmtest1-Client-001</li></ul>            |

### <a name="paas-services"></a>Serviços PaaS

| Tipo de ativo     | Escopo  | ao                                                              | Exemplos                                                                                 |
|----------------|--------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Serviço de Aplicativos do Azure    | Global | azapp-\<App Name \> - \<Environment \> - \< \# \# \# 0. [{azurewebsites.net}] | <ul><li>azapp-navigator-prod-001.azurewebsites.net </li><li>azapp-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Azure Functions aplicativo   | Global | azfun-\<App Name \> - \<Environment \> - \< \# \# \# 0. [{azurewebsites.net}] | <ul><li>azfun-navigator-prod-001.azurewebsites.net </li><li>azfun-accountlookup-dev-001.azurewebsites.net</li></ul> |
| Serviços de nuvem do Azure | Global | AZCS-\<App Name \> - \<Environment \> - \< \# \# \# 0. [{cloudapp.net}]       | <ul><li>azcs-navigator-prod-001.azurewebsites.net </li><li>azcs-accountlookup-dev-001.azurewebsites.net</li></ul>   |

### <a name="azure-service-bus"></a>Service Bus do Azure

| Tipo de ativo         | Escopo       | ao                                                     | Exemplos                           |
|--------------------|-------------|------------------------------------------------------------|------------------------------------|
| Service Bus do Azure        | Global      | SB-\<App nome \> - \<Environment \>. [{servicebus.windows.net}] | <ul><li>SB-Navigator-prod </li><li>SB-emissões-dev</li></ul> |
| Filas do barramento de serviço do Azure | Service Bus | SBQ-descritor de \<query \>                                   | <ul><li>sbq-messagequery</li></ul>                   |

### <a name="databases"></a>Bancos de dados

| Tipo de ativo                          | Escopo              | ao                                | Exemplos                                       |
|-------------------------------------|--------------------|---------------------------------------|------------------------------------------------|
| Banco de dados SQL do Azure                  | Global             | SQLDB-\<App nome \> - \<Environment \>    | <ul><li>SQLDB-Navigator-prod </li><li>SQLDB-emissões-dev</li></ul>       |
| Azure Cosmos DB (anteriormente DocumentDB) | Global             | cosdb-\<App nome \> - \<Environment \>    | <ul><li>cosdb-Navigator-prod </li><li>cosdb-emissões-dev</li></ul>       |
| Cache Redis do Azure               | Global             | Redis-\<App nome \> - \<Environment \>    | <ul><li>Redis-Navigator-prod </li><li>Redis-emissões-dev</li></ul>       |
| Banco de Dados do Azure para MySQL            | Global             | MySQL-\<App nome \> - \<Environment \>    | <ul><li>MySQL-Navigator-prod </li><li>MySQL-emissões-dev</li></ul>       |
| Azure SQL Data Warehouse                  | Global             | sqldw-\<App nome \> - \<Environment \>    | <ul><li>sqldw-Navigator-prod </li><li>sqldw-emissões-dev</li></ul>       |
| SQL Server Stretch Database         | Banco de dados SQL do Azure | sqlstrdb-\<App nome \> - \<Environment \> | <ul><li>sqlstrdb-Navigator-prod </li><li>sqlstrdb-emissões-dev</li></ul> |

### <a name="storage"></a>Armazenamento

| Tipo de ativo                              | Escopo  | ao                                                                        | Exemplos                                   |
|-----------------------------------------|--------|-------------------------------------------------------------------------------|--------------------------------------------|
| Conta de armazenamento do Azure-uso geral     | Global | St \<storage Name \> \< \# \# \# \>                                                  | <ul><li>stnavigatordata001 </li><li>stemissionsoutput001</li></ul>    |
| Conta de armazenamento do Azure-logs de diagnóstico | Global | o \<first as duas letras do nome da assinatura e do número \> \<region \> \< \# \# \# \> | <ul><li>stdiagsh001eastus2001 </li><li>stdiagsh001westus001</li></ul> |
| Azure StorSimple                              | Global | ssimp nome de \<App \> \<Environment \>                                              | <ul><li>ssimpnavigatorprod </li><li>ssimpemissionsdev</li></ul>       |

### <a name="ai--machine-learning"></a>IA + Machine Learning

| Tipo de ativo                       | Escopo          | ao                            | Exemplos                               |
|----------------------------------|----------------|-----------------------------------|----------------------------------------|
| Azure Search                     | Global         | srch-\<App nome \> - \<Environment \> | <ul><li>srch-Navigator-prod </li><li>srch-emissões-dev</li></ul> |
| Serviços Cognitivos do Azure               | Grupo de recursos | CS-\<App Name \> - \<Environment \>   | <ul><li>CS-Navigator-prod </li><li>CS-emissões-dev</li></ul>     |
| Espaço de trabalho Azure Machine Learning | Grupo de recursos | AML-\<App nome \> - \<Environment \>  | <ul><li>AML-Navigator-prod </li><li>AML-emissões-dev</li></ul>   |

### <a name="analytics"></a>Análises

| Tipo de ativo                | Escopo  | ao                             | Exemplos                                 |
|---------------------------|--------|------------------------------------|------------------------------------------|
| Azure Data Factory        | Global | \> de nome DF-\<App \<Environment \>     | <ul><li>DF-Navigator-prod </li><li>DF-emissões-dev</li></ul>       |
| Azure Data Lake Store   | Global | Nome de \<App DLS \> \<Environment \>     | <ul><li>dlsnavigatorprod </li><li>dlsemissionsdev</li></ul>         |
| Azure Data Lake Analytics | Global | dla \<App nome \> \<Environment \>     | <ul><li>dlanavigatorprod </li><li>dlaemissionsdev</li></ul>         |
| Azure HDInsight-Spark         | Global | hdis-\<App nome \> - \<Environment \>  | <ul><li>hdis-Navigator-prod </li><li>hdis-emissões-dev </li></ul>  |
| Azure HDInsight-Hadoop        | Global | hdihd-\<App nome \> - \<Environment \> | <ul><li>hdihd-Hadoop-prod </li><li>hdihd-emissões-dev</li></ul>    |
| Azure HDInsight-servidor R      | Global | HDIR-\<App nome \> - \<Environment \>  | <ul><li>HDIR-Navigator-prod </li><li>HDIR-emissões-dev</li></ul>   |
| Azure HDInsight-HBase         | Global | hdihb-\<App nome \> - \<Environment \> | <ul><li>hdihb-Navigator-prod </li><li>hdihb-emissões-dev</li></ul> |
| Power BI Embedded         | Global | pbiemb nome de \<App \> \<Environment \>  | <ul><li>pbiem-Navigator-prod </li><li>pbiem-emissões-dev</li></ul> |

### <a name="internet-of-things-iot"></a>IoT (Internet das Coisas)

| Tipo de ativo                         | Escopo          | ao                             | Exemplos                                 |
|------------------------------------|----------------|------------------------------------|------------------------------------------|
| Azure Stream Analytics no IoT Edge | Grupo de recursos | asa-\<App nome \> - \<Environment \>   | <ul><li>asa-Navigator-prod </li><li>asa-emissões-dev</li></ul>     |
| Hub IoT do Azure                      | Global         | AIH-\<App nome \> - \<Environment \>   | <ul><li>AIH-Navigator-prod </li><li>AIH-emissões-dev</li></ul>     |
| Hubs de Eventos do Azure                          | Global         | EVH-\<App nome \> - \<Environment \>   | <ul><li>EVH-Navigator-prod </li><li>EVH-emissões-dev</li></ul>     |
| Hubs de Notificação do Azure                   | Grupo de recursos | Anh-\<App nome \> - \<Environment \>   | <ul><li>EVH-Navigator-prod </li><li>EVH-emissões-dev</li></ul>     |
| Namespace dos hubs de notificação do Azure         | Global         | anhns-\<App nome \> - \<Environment \> | <ul><li>anhns-Navigator-prod </li><li>anhns-emissões-dev</li></ul> |
