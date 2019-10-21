---
title: 'Migração de mainframe: migração de aplicativo de mainframe'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migre aplicativos de ambientes de mainframe para o Azure, uma infraestrutura comprovada, altamente disponível e escalonável para sistemas que atualmente são executados em mainframes.
author: njray
ms.author: v-nanra
ms.date: 12/26/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ba2d68a2b382ccccf0d124a57d33d1344476c3dc
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547951"
---
# <a name="mainframe-application-migration"></a>Migração de aplicativos de mainframe

Ao migrar aplicativos de ambientes de mainframe para o Azure, a maioria das equipes segue uma abordagem pragmática: reutilização sempre que possível e, em seguida, inicie uma implantação em fases em que os aplicativos são reescritos ou substituídos.

A migração de aplicativos normalmente envolve uma ou mais das seguintes estratégias:

- **Hospedar novamente:** Você pode mover o código existente, os programas e os aplicativos do mainframe e, em seguida, recompilar o código para ser executado em um emulador de mainframe hospedado em uma instância de nuvem. Essa abordagem normalmente começa com a movimentação de aplicativos para um emulador baseado em nuvem e, em seguida, a migração do banco de dados para um banco de dados baseado em nuvem. Alguns engenheiros e refatoração são necessários juntamente com conversões de dados e arquivos.

    Como alternativa, você pode hospedar novamente usando um provedor de hospedagem tradicional. Um dos principais benefícios da nuvem é terceirizar o gerenciamento de infraestrutura. Você pode encontrar um provedor de datacenter que hospedará suas cargas de trabalho de mainframe para você. Esse modelo pode comprar tempo, reduzir o bloqueio do fornecedor e produzir economias de custo provisórias.

- **Desativar:** Todos os aplicativos que não são mais necessários devem ser desativados antes da migração.

- **Recompilação:** Algumas organizações optam por reescrever completamente os programas usando técnicas modernas. Devido ao custo e à complexidade adicionais dessa abordagem, isso não é tão comum quanto uma abordagem de "deslocamento e mudança". Geralmente após esse tipo de migração, faz sentido começar a substituir módulos e código usando mecanismos de transformação de código.

- **Substituir:** Essa abordagem substitui a funcionalidade de mainframe por recursos equivalentes na nuvem. O SaaS (software como serviço) é uma opção, que está usando uma solução criada especificamente para uma preocupação empresarial, como finanças, recursos humanos, fabricação ou planejamento de recursos empresariais. Além disso, muitos aplicativos específicos do setor agora estão disponíveis para resolver problemas que as soluções de mainframe personalizadas usaram anteriormente para resolver.

Você deve considerar a partir do planejamento das cargas de trabalho que deseja migrar inicialmente e, em seguida, determinar esses requisitos para mover aplicativos associados, bases de código herdadas e bancos de dados.

## <a name="mainframe-emulation-in-azure"></a>Emulação de mainframe no Azure

Os serviços de nuvem do Azure podem emular ambientes de mainframe tradicionais, permitindo que você reutilize aplicativos e código de mainframe existentes. Os componentes comuns do servidor que você pode emular incluem OLTP (processamento de transações online), lote e sistemas de ingestão de dados.

### <a name="oltp-systems"></a>Sistemas OLTP

Muitos mainframes têm sistemas OLTP que processam milhares ou milhões de atualizações para um grande número de usuários. Esses aplicativos geralmente usam o processamento de transações e o software de manuseio de formulário de tela, como CICS (sistema de controle de informações do cliente), IMS (sistemas de gerenciamento de informações) e TIP (processador de interface de terminal).

Ao mover aplicativos OLTP para o Azure, os emuladores para monitores TP (processamento de transações de mainframe) estão disponíveis para execução como IaaS (infraestrutura como serviço) usando VMs (máquinas virtuais) no Azure. A funcionalidade de manipulação de tela e de formulário também pode ser implementada por servidores Web. Essa abordagem pode ser combinada com APIs de banco de dados, como ADO (ActiveX Data Objects), ODBC (Open Database Connectivity) e JDBC (Java Database Connectivity) para acesso a dados e transações.

### <a name="time-constrained-batch-updates"></a>Atualizações de lote com restrição de tempo

Muitos sistemas de mainframe executam atualizações mensais ou anuais de milhões de registros de conta, como aqueles usados em serviços bancários, seguros e governamentais. Os mainframes lidam com esses tipos de cargas de trabalho oferecendo sistemas de manipulação de dados de alta taxa de transferência. Os mainframes em lotes geralmente são de natureza serial e dependem das operações de entrada/saída por segundo (IOPS) fornecidas pelo backbone de mainframe para desempenho.

Ambientes de lote baseados em nuvem usam computação paralela e redes de alta velocidade para desempenho. Se você precisar otimizar o desempenho do lote, o Azure fornecerá várias opções de computação, armazenamento e rede.

### <a name="data-ingestion-systems"></a>Sistemas de ingestão de dados

Os mainframes ingerim grandes lotes de dados de varejo, serviços financeiros, manufatura e outras soluções para processamento. Com o Azure, você pode usar utilitários de linha de comando simples, como [AzCopy](https://docs.microsoft.com/azure/storage/common/storage-use-azcopy) , para copiar dados de e para o local de armazenamento. Você também pode usar o serviço de [Azure data Factory](https://docs.microsoft.com/azure/data-factory/introduction) , permitindo que você ingerir dados de armazenamentos de dados diferentes para criar e agendar fluxos de trabalho controlados por dados.

Além dos ambientes de emulação, o Azure fornece o PaaS (plataforma como serviço) e os serviços de análise que podem aprimorar os ambientes de mainframe existentes.

## <a name="migrate-oltp-workloads-to-azure"></a>Migrar cargas de trabalho OLTP para o Azure

A abordagem de "comparação e deslocamento" é a opção sem código para migrar rapidamente os aplicativos existentes para o Azure. Cada aplicativo é migrado como está, o que fornece os benefícios da nuvem sem os riscos ou os custos de fazer alterações de código. O uso de um emulador para monitores de processamento de transações de mainframe (TP) no Azure dá suporte a essa abordagem.

Os monitores TP estão disponíveis de vários fornecedores e são executados em máquinas virtuais, uma opção de infraestrutura como serviço (IaaS) no Azure. Os diagramas anteriores e posteriores mostram uma migração de um aplicativo online apoiado pelo IBM DB2, um DBMS (sistema de gerenciamento de banco de dados relacional), em um mainframe IBM z/OS. O DB2 para z/OS usa arquivos de VSAM (método de acesso de armazenamento virtual) para armazenar os dados e o método de acesso sequencial (ISAM) indexado para arquivos simples. Essa arquitetura também usa CICS para o monitoramento de transações.

![Migração de "deslocamento e mudança" de um ambiente de mainframe para o Azure usando o software de emulação](../../_images/mainframe-migration/mainframe-vs-azure.png)

No Azure, os ambientes de emulação são usados para executar o Gerenciador de TP e os trabalhos em lotes que usam o JCL. Na camada de dados, o DB2 é substituído pelo banco de dado [SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), embora Microsoft SQL Server, DB2 LUW ou Oracle Database também possam ser usados. Um emulador dá suporte a IMS, VSAM e SEQ. As ferramentas de gerenciamento do sistema do mainframe são substituídas pelos serviços do Azure e por software de outros fornecedores, que são executados em VMs.

A funcionalidade de manipulação de tela e de entrada de formulário é normalmente implementada usando servidores Web, que podem ser combinados com APIs de banco de dados, como ADO, ODBC e JDBC para acesso a data e transações. A linha exata dos componentes do Azure IaaS a ser usada depende do sistema operacional que você preferir. Por exemplo:

- VMs baseadas no Windows: IIS (servidor de informações da Internet) junto com o ASP.NET para o manuseio de tela e a lógica de negócios. Use ADO.NET para acesso a dados e transações.

- VMs baseadas em Linux: os servidores de aplicativos baseados em Java que estão disponíveis, como Apache Tomcat para manipulação de tela e funcionalidade comercial baseada em Java. Use JDBC para acesso a dados e transações.

## <a name="migrate-batch-workloads-to-azure"></a>Migrar cargas de trabalho do lote para o Azure

As operações em lote no Azure diferem do ambiente de lote típico em mainframes. Os trabalhos em lote de mainframe normalmente são de natureza serial e dependem do IOPS fornecido pelo backbone de mainframe para o desempenho. Ambientes de lote baseados em nuvem usam computação paralela e redes de alta velocidade para desempenho.

Para otimizar o desempenho do lote usando o Azure, considere as opções de [computação](https://docs.microsoft.com/azure/virtual-machines/windows/overview), [armazenamento](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction), [rede](https://azure.microsoft.com/blog/maximize-your-vm-s-performance-with-accelerated-networking-now-generally-available-for-both-windows-and-linux)e [monitoramento](https://docs.microsoft.com/azure/azure-monitor/overview) da seguinte maneira.

### <a name="compute"></a>Computação

Use:

- VMs com a velocidade de clock mais alta. Os aplicativos de mainframe geralmente são de thread único e as CPUs de mainframe têm uma velocidade de clock muito alta.

- VMs com grande capacidade de memória para permitir o armazenamento em cache de áreas de trabalho de dados e aplicativos.

- VMs com maior densidade vCPUs para aproveitar o processamento multi-threaded se o aplicativo der suporte a vários threads.

- Processamento paralelo, pois o Azure é facilmente dimensionado para processamento paralelo, fornecendo mais poder de computação para uma execução em lote.

### <a name="storage"></a>Armazenamento

Use:

- [SSD Premium do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/premium-storage) ou [ultra SSD do Azure](https://docs.microsoft.com/azure/virtual-machines/windows/disks-ultra-ssd) para o IOPS máximo disponível.

- Distribuição com vários discos para mais IOPS por tamanho de armazenamento.

- Particionamento de armazenamento para distribuir e/s em vários dispositivos de armazenamento do Azure.

### <a name="networking"></a>Rede

- Use a [rede acelerada do Azure](https://docs.microsoft.com/azure/virtual-network/create-vm-accelerated-networking-powershell) para minimizar a latência.

### <a name="monitoring"></a>Monitoramento

- Use ferramentas de monitoramento, [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview), [aplicativo Azure insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)e até mesmo os logs do Azure permitem que os administradores monitorem qualquer desempenho de execuções em lote e ajudem a eliminar afunilamentos.

## <a name="migrate-development-environments"></a>Migrar ambientes de desenvolvimento

As arquiteturas distribuídas da nuvem dependem de um conjunto diferente de ferramentas de desenvolvimento que fornecem a vantagem das práticas modernas e linguagens de programação. Para facilitar essa transição, você pode usar um ambiente de desenvolvimento com outras ferramentas que foram projetadas para emular ambientes IBM z/OS. A lista a seguir mostra opções da Microsoft e de outros fornecedores:

| Componente        | Opções do Azure                                                                                                                                  |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| z/OS             | Windows, Linux ou UNIX                                                                                                                      |
| CICS             | Serviços do Azure oferecidos pelos dados micro Focus, Oracle, GT software (Fujitsu), TmaxSoft, Raincode e NTT, ou reescreva usando o kubernetes |
| IMS              | Serviços do Azure oferecidos pelo micro Focus e pela Oracle                                                                                  |
| Assembler        | Serviços do Azure de Raincode e TmaxSoft; ou COBOL, C ou Java, ou mapear para funções do sistema operacional               |
| JCL              | JCL, PowerShell ou outras ferramentas de script                                                                                                   |
| COBOL            | COBOL, C ou Java                                                                                                                            |
| Natural          | Natural, COBOL, C ou Java                                                                                                                  |
| FORTRAN e PL/I | FORTRAN, PL/I, COBOL, C ou Java                                                                                                           |
| REXX e PL/I    | REXX, PowerShell ou outras ferramentas de script                                                                                                  |

## <a name="migrate-databases-and-data"></a>Migrar bancos de dados e data

A migração de aplicativos geralmente envolve a rehospedagem da camada de dados. Você pode migrar SQL Server, software livre e outros bancos de dados relacionais para soluções totalmente gerenciadas no Azure, como [instância gerenciada do banco de dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), [serviço de banco de dados do Azure para PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview)e [banco de dados do Azure para MySQL](https://docs.microsoft.com/azure/mysql/overview) com [ Serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/dms-overview).

Por exemplo, você pode migrar se a camada de dados do mainframe usar:

- O IBM DB2 ou um banco de dados do IMS, use o banco de dados SQL do Azure, SQL Server, DB2 LUW ou Oracle Database no Azure.

- VSAM e outros arquivos simples, use arquivos simples de ISAM (método de acesso sequencial indexado) para SQL do Azure, SQL Server, DB2 LUW ou Oracle.

- GDGs (grupos de datas de geração), migre para arquivos no Azure que usam uma Convenção de nomenclatura e extensões de nome de arquivo que fornecem funcionalidade semelhante à GDGs.

A camada de dados IBM inclui vários componentes importantes que você também deve migrar. Por exemplo, ao migrar um banco de dados, você também migrará uma coleção de dado contidos em pools, cada um contendo dbextents, que são conjuntos de dados do VSAM de z/OS. A migração deve incluir o diretório que identifica os locais de dados nos pools de armazenamento. Além disso, seu plano de migração deve considerar o log de banco de dados, que contém um registro de operações executadas no banco de dados. Um banco de dados pode ter um, dois (duplo ou alternativo) ou quatro logs (duplo e alternativo).

A migração de banco de dados também inclui estes componentes:

- **Gerenciador de banco de dados:** Fornece acesso aos dados no banco de dado. O Gerenciador de banco de dados é executado em sua própria partição em um ambiente z/OS.
- **Solicitante do aplicativo:** Aceita solicitações de aplicativos antes de passá-las para um servidor de aplicativos.
- **Adaptador de recursos online:** Inclui componentes de solicitação de aplicativo para uso em transações CICS.
- **Adaptador de recursos do lote:** Implementa componentes do solicitante de aplicativo para aplicativos de lote z/OS.
- **SQL interativo (isql):** É executado como um aplicativo e uma interface CICS, permitindo que os usuários insiram instruções SQL ou comandos de operador.
- **Aplicativo CICS:** É executado sob o controle de CICS, usando recursos disponíveis e fontes de dados no CICS.
- **Aplicativo do lote:** Executa a lógica do processo sem comunicação interativa com os usuários para, por exemplo, produzir atualizações de dados em massa ou gerar relatórios de um banco de dado.

## <a name="optimize-scale-and-throughput-for-azure"></a>Otimizar a escala e a produtividade do Azure

Em termos gerais, os mainframes são escalados verticalmente, enquanto a nuvem é dimensionada. Para otimizar a escala e a taxa de transferência de aplicativos em estilo de mainframe em execução no Azure, é importante entender como os mainframes podem separar e isolar aplicativos. Um mainframe z/OS usa um recurso chamado de partições lógicas (LPARs) para isolar e gerenciar os recursos de um aplicativo específico em uma única instância.

Por exemplo, um mainframe pode usar uma LPAR (partição lógica) para uma região CICS com programas COBOL associados e um LPAR separado para DB2. Os LPARs adicionais são frequentemente usados para os ambientes de desenvolvimento, teste e preparo.

No Azure, é mais comum usar VMs separadas para atender a essa finalidade. As arquiteturas do Azure normalmente implantam VMs para a camada de aplicativo, um conjunto separado de VMs para a camada de dados, outro conjunto para desenvolvimento e assim por diante. Cada camada de processamento pode ser otimizada usando o tipo mais adequado de VMs e recursos para esse ambiente.

Além disso, cada camada também pode fornecer serviços de recuperação de desastre apropriados. Por exemplo, as VMs de produção e de banco de dados podem exigir uma recuperação quente ou quente, enquanto as VMs de desenvolvimento e teste dão suporte a uma recuperação fria.

A figura a seguir mostra uma possível implantação do Azure usando um site primário e um secundário. No site primário, as VMs de produção, preparo e teste são implantadas com alta disponibilidade. O site secundário é para backup e recuperação de desastres.

![Uma possível implantação do Azure usando um site primário e um secundário](../../_images/mainframe-migration/migration-backup-dr.png)

## <a name="perform-a-staged-mainframe-to-azure"></a>Executar um mainframe preparado para o Azure

A movimentação de soluções de um mainframe para o Azure pode envolver uma migração em *etapas* , na qual alguns aplicativos são movidos primeiro e outros permanecem no mainframe de forma temporária ou permanente. Essa abordagem normalmente requer sistemas que permitam que aplicativos e bancos de dados interoperem entre o mainframe e o Azure.

Um cenário comum é mover um aplicativo para o Azure mantendo os dados usados pelo aplicativo no mainframe. O software específico é usado para permitir que os aplicativos no Azure acessem dados do mainframe. Felizmente, uma ampla gama de soluções fornece integração entre o Azure e ambientes de mainframe existentes, suporte para cenários híbridos e migração ao longo do tempo. Os parceiros da Microsoft, fornecedores independentes de software e integradores de sistemas podem ajudá-lo em sua jornada.

Uma opção é o [Microsoft Host Integration Server](https://docs.microsoft.com/host-integration-server), uma solução que fornece a DRDA (arquitetura de banco de dados relacional distribuída) necessária para que aplicativos no Azure acessem dados no DB2 que permanecem no mainframe. Outras opções de integração entre mainframe e Azure incluem soluções da IBM, Attunity, Codit, outros fornecedores e opções de software livre.

## <a name="partner-solutions"></a>Soluções de parceiro

Se você estiver considerando uma migração de mainframe, o ecossistema de parceiros estará disponível para ajudá-lo.

O Azure fornece uma infraestrutura comprovada, altamente disponível e escalonável para sistemas que atualmente são executados em mainframes. Algumas cargas de trabalho podem ser migradas com uma facilidade relativa. Outras cargas de trabalho que dependem de software de sistema herdado, como CICS e IMS, podem ser rehospedadas usando soluções de parceiros e migradas para o Azure ao longo do tempo. Independentemente da escolha que você faz, a Microsoft e nossos parceiros estão disponíveis para ajudá-lo a otimizar o Azure, mantendo a funcionalidade de software do sistema de mainframe.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações, consulte os seguintes recursos:

- [Introdução ao Azure](https://docs.microsoft.com/azure)

- [Implantar o IBM DB2 pureScale no Azure](https://azure.microsoft.com/resources/deploy-ibm-db2-purescale-on-azure)

- [Documentação do Host Integration Server](https://docs.microsoft.com/host-integration-server)
