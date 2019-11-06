---
title: Refatorar um aplicativo migrando-o para o Serviço de Aplicativo do Azure e o Banco de Dados SQL do Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como a Contoso hospeda novamente um aplicativo local migrando-o para um aplicativo Web do Serviço de Aplicativo do Azure e do banco de dados do Azure SQL Server.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: d0d0fa87d424cbdf33e2b8516dd43b5156b55756
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566569"
---
# <a name="refactor-an-on-premises-app-to-an-azure-app-service-web-app-and-azure-sql-database"></a>Refatorar um aplicativo local para um aplicativo Web do Serviço de Aplicativo do Azure e do banco de dados SQL do Azure

Este artigo demonstra como a empresa fictícia Contoso refatora um aplicativo de duas camadas .NET do Windows em execução em VMs VMware como parte de uma migração para o Azure. Eles migram a VM de front-end do aplicativo para um aplicativo Web do Serviço de Aplicativo do Azure e o banco de dados do aplicativo para um banco de dados SQL do Azure.

O aplicativo SmartHotel360 usado neste exemplo é fornecido como software livre. Se quiser usá-lo em seus próprios testes, você poderá baixá-lo do [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Geradores de negócios

A equipe de liderança de TI trabalhou em conjunto com parceiros comerciais para entender o que eles desejam obter com essa migração:

- **Lidar com o crescimento da empresa.** A Contoso está crescendo e há pressão sobre os sistemas e a infraestrutura locais.
- **Aumentar a eficiência.** A Contoso precisa remover procedimentos desnecessários e simplificar processos para desenvolvedores e usuários. Necessidades de negócios IT rápidas e tempo não resíduos ou money, fornecendo, assim, mais rápido nas necessidades do cliente.
- **Aumentar a agilidade.**  A TI da Contoso precisa atender melhor às necessidades empresariais. Ele deve ser capaz de reagir mais rápido do que as alterações no marketplace, para habilitar o sucesso em uma economia global. Ele não deve obter da forma ou se tornar um bloqueador de negócios.
- **Escala.** Uma vez que a empresa cresce com êxito, TI da Contoso deve fornecer sistemas que são capazes de crescer no mesmo ritmo.
- **Reduzir custos.** a Contoso quer minimizar os custos de licenciamento.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem da Contoso fixou metas para esta migração. Essas metas foram usadas para determinar o melhor método de migração.

<!-- markdownlint-disable MD033 -->

**Requisitos** | **Detalhes**
--- | ---
**Aplicativo** | O aplicativo no Azure permanecerá tão importante quanto é hoje.<br/><br/> Ele deve ter os mesmos recursos de desempenho que tem atualmente no VMware.<br/><br/> A equipe não quer investir no aplicativo. Por enquanto, os administradores simplesmente movem o aplicativo com segurança para a nuvem.<br/><br/> A equipe deseja parar de oferecer suporte ao Windows Server 2008 R2, no qual o aplicativo é executado atualmente.<br/><br/> A equipe também deseja se afastar do SQL Server 2008 R2 para uma plataforma de banco de dados PaaS moderna, o que minimizará a necessidade de gerenciamento.<br/><br/> A Contoso deseja aproveitar seu investimento em licenciamento do SQL Server e o Software Assurance quando possível.<br/><br/> Além disso, a Contoso deseja reduzir o ponto único de falha na camada da web.
**Limitações** | O aplicativo consiste em um aplicativo ASP.NET e um serviço WCF em execução na mesma VM. Eles querem dividir isso em dois aplicativos Web usando o Serviço de Aplicativo do Azure.
**As tabelas** | Contoso quer mover o aplicativo para o Azure, mas não quer executá-lo em VMs. A Contoso quer usar os serviços de PaaS do Azure para as camadas da Web e de dados.
**DevOps** | A Contoso deseja passar para um modelo de DevOps usando o Azure DevOps para o pipelines de builds e de lançamento.

<!-- markdownlint-enable MD033 -->

## <a name="solution-design"></a>Design da solução

Depois de fixar as metas e os requisitos, a Contoso projeta e analisa uma solução de implantação e identifica o processo de migração, incluindo os serviços do Azure que serão usados para migração.

### <a name="current-app"></a>Aplicativo atual

- O aplicativo local do SmartHotel360 é dividido em duas VMs (WEBVM e SQLVM).
- As VMs estão localizadas no host VMware ESXi **contosohost1.contoso.com** (versão 6.5)
- O ambiente VMware é gerenciado pelo vCenter Server 6.5 (**vcenter.contoso.com**) em execução em uma VM.
- A Contoso tem um datacenter local (contoso-datacenter), com um controlador de domínio local (**contosodc1**).
- As VMs locais no datacenter Contoso, serão descomissionadas após a migração.

### <a name="proposed-solution"></a>Solução proposta

- Para a camada de banco de dados do aplicativo, a Contoso comparou o Banco de Dados SQL do Azure com o SQL Server usando [este artigo](https://docs.microsoft.com/azure/sql-database/sql-database-features). A Contoso decidiu usar o Banco de Dados SQL do Azure por alguns motivos:
  - O Banco de Dados SQL do Azure é um serviço gerenciado de banco de dados relacional. Ele oferece desempenho previsível em vários níveis de serviço, com administração quase zero. As vantagens incluem a escalabilidade dinâmica sem tempo de inatividade, a otimização inteligente interna e a escalabilidade e a disponibilidade globais.
  - A Contoso pode usar o leve AMD (Assistente de Migração de Dados) para avaliar e migrar o banco de dados local para o Azure SQL.
  - Com o Software Assurance, a Contoso pode trocar licenças existentes por taxas com desconto em um banco de dados SQL, usando o Benefício Híbrido do Azure para SQL Server. Isso pode proporcionar uma economia de até 30%.
  - O Banco de Dados SQL fornece recursos de segurança, como o mascaramento de dados dinâmico Always Encrypted e detecção de ameaça de segurança de nível de linha.
- Para a camada da Web do aplicativo, a Contoso decidiu usar o Serviço de Aplicativo do Azure. Esse serviço de PaaS permite isso para implantar o aplicativo com apenas algumas mudanças de configuração. A Contoso usará o Visual Studio para fazer a alteração e implantar dois aplicativos da Web. Um para o site e outro para o serviço WCF.
- Para atender aos requisitos de um pipeline de DevOps, a Contoso decidiu usar o Azure DevOps para SCM (Gerenciamento de Código-fonte), com repositórios Git. As compilações e versões automáticas serão usadas para criar o código e implantá-lo no Serviço de Aplicativo do Azure.

### <a name="solution-review"></a>Análise de solução

A Contoso avalia seu projeto proposto reunindo uma lista de prós e contras.

<!-- markdownlint-disable MD033 -->

**Consideração** | **Detalhes**
--- | ---
**Prós** | O código do aplicativo SmartHotel360 não precisará ser alterado para migração para o Azure.<br/><br/> A Contoso pode aproveitar seu investimento em Software Assurance usando o Benefício Híbrido do Azure para o SQL Server e o Windows Server.<br/><br/> Após a migração, o Windows Server 2008 R2 não precisará ser suportado. [Saiba mais](https://support.microsoft.com/lifecycle).<br/><br/> A Contoso pode configurar a camada da Web do aplicativo com várias instâncias para que ela não seja mais um ponto único de falha.<br/><br/> O banco de dados não dependerá mais do antigo SQL Server 2008 R2.<br/><br/> Banco de dados SQL suporta os requisitos técnicos. A Contoso avaliou o banco de dados local usando o Assistente de Migração de Dados e descobriu que ele é compatível.<br/><br/> O Banco de Dados SQL do Azure tem tolerância a falhas interna que a Contoso não precisa configurar. Isso garante que a camada de dados não é mais um ponto único de failover.
**Contras** | O Serviço de Aplicativo do Azure oferece suporte apenas a uma implantação de aplicativo para cada aplicativo Web. Isso significa que dois aplicativos Web precisam ser provisionados (um para o site e outro para o serviço WCF).<br/><br/> Se a contoso usar o Assistente de Migração de Dados em vez do serviço de migração de banco de dados do Azure para migrar seu banco de dados, ele não terá a infraestrutura pronta para migrar bancos de dados em escala. A Contoso precisará construir outra região para garantir o failover se a região primária estiver indisponível.

<!-- markdownlint-enable MD033 -->

## <a name="proposed-architecture"></a>Arquitetura proposta

![Arquitetura de cenário](media/contoso-migration-refactor-web-app-sql/architecture.png)

### <a name="migration-process"></a>Processo de migração

1. A Contoso provisiona uma instância do SQL do Azure e migra o banco de dados do SmartHotel360 para ela.
2. A Contoso provisiona e configura os aplicativos Web e implanta o aplicativo SmartHotel360 para eles.

    ![Processo de migração](media/contoso-migration-refactor-web-app-sql/migration-process.png)

### <a name="azure-services"></a>Serviços do Azure

**Serviço** | **Descrição** | **Custo**
--- | --- | ---
[AMD (Assistente de Migração de Dados)](https://docs.microsoft.com/sql/dma/dma-overview?view=ssdt-18vs2017) | A Contoso usará o AMD para avaliar e detectar problemas de compatibilidade que possam afetar a funcionalidade do banco de dados no Azure. DMA avalia a paridade de recursos entre SQL origens e destinos e recomenda melhorias de desempenho e confiabilidade. | É uma ferramenta que pode ser baixada gratuitamente.
[Banco de Dados SQL do Azure](https://azure.microsoft.com/services/sql-database) | Um serviço de banco de dados de nuvem relacional inteligente e totalmente gerenciado. | Custo com base em recursos, taxa de transferência e tamanho. [Saiba mais](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service/overview) | Crie aplicativos de nuvem avançados usando uma plataforma totalmente gerenciada | Custo com base no tamanho, na localização e na duração do uso. [Saiba mais](https://azure.microsoft.com/pricing/details/app-service/windows).
[Azure DevOps](https://docs.microsoft.com/azure/azure-portal/tutorial-azureportal-devops) | Fornece um pipeline de CI/CD (integração contínua/implantação contínua) para o desenvolvimento de aplicativos. O pipeline começa com um repositório Git para gerenciar o código do aplicativo, um sistema de build para produzir pacotes e outros artefatos de build e um sistema Release Management para implantar as alterações nos ambientes de desenvolvimento, teste e produção.

## <a name="prerequisites"></a>Pré-requisitos

Aqui, a Contoso precisa executar este cenário:

<!-- markdownlint-disable MD033 -->

**Requisitos** | **Detalhes**
--- | ---
**Assinatura do Azure** | A Contoso criou assinaturas durante um artigo anterior. Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se você criar uma conta gratuita, será o administrador da assinatura e poderá executar todas as ações.<br/><br/> Se você usar uma assinatura existente e não for o administrador, será necessário trabalhar com o administrador para receber permissões de Proprietário ou de Colaborador.
**Infraestrutura do Azure** | [ Saiba como ](./contoso-migration-infrastructure.md) a Contoso configurou uma infraestrutura do Azure.

<!--markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Etapas do cenário

Aqui está como a Contoso executará a migração:

> [!div class="checklist"]
>
> - **Etapa 1: provisionar uma instância do banco de dados SQL no Azure.** a Contoso provisiona uma instância do SQL no Azure. Depois que o site do aplicativo for migrado para o Azure, o aplicativo da Web do serviço WCF apontará para esta instância.
> - **Etapa 2: migre o banco de dados com DMA.** A Contoso migra o banco de dados do aplicativo com o Assistente de Migração do Banco de Dados.
> - **Etapa 3: provisionar aplicativos Web.** A Contoso provisiona os dois aplicativos Web.
> - **Etapa 4: configurar o Azure DevOps.** a Contoso cria um projeto do Azure DevOps e importa o repositório Git.
> - **Etapa 5: configurar cadeias de conexão.** a Contoso configura as sequências de conexão para que o aplicativo Web da camada da web, o aplicativo Web do serviço WCF e a instância do SQL possam se comunicar.
> - **Etapa 6: configurar pipelines de Build e versão.** Como etapa final, a Contoso configura os pipelines de build e lançamento para criar o aplicativo e implanta-os em dois aplicativos Web separados.

## <a name="step-1-provision-an-azure-sql-database"></a>Etapa 1: Provisionar um Banco de Dados SQL do Azure

1. Os administradores da Contoso Selecione para criar um banco de dados SQL no Azure.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql1.png)

2. Eles especificam um nome de banco de dados para corresponder ao banco de dados em execução na VM local (**SmartHotel.Registration**). Eles colocam o banco de dados no grupo de recursos ContosoRG. Esse é o grupo de recursos que eles usam para recursos de produção no Azure.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql2.png)

3. Eles configuram uma nova instância do SQL Server (**sql-smarthotel-eus2**) na região primária.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql3.png)

4. Eles definem o tipo de preço para corresponder às suas necessidades de servidor e banco de dados. E escolhem economizar dinheiro com o Benefício Híbrido do Azure porque já tem uma licença do SQL Server.
5. Para dimensionamento eles usam a compra baseada em VCore e definem os limites para os requisitos esperados.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql4.png)

6. Em seguida, eles criam a instância de banco de dados.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql5.png)

7. Depois que a instância é criada, eles abrem o banco de dados e anotam os detalhes que serão necessários quando usarem o Assistente de Migração de Dados para a migração.

    ![Provisionar SQL](media/contoso-migration-refactor-web-app-sql/provision-sql6.png)

**Precisa de mais ajuda?**

- [Obtenha ajuda ](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal) o provisionamento de um Banco de Dados SQL.
- [Saiba mais sobre](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools) os limites de recursos do VCore.

## <a name="step-2-migrate-the-database-with-dma"></a>Etapa 2: migrar o banco de dados com o DMA

Os administradores da Contoso migrarão o banco de dados do SmartHotel360 usando o DMA.

### <a name="install-dma"></a>Instalar o DMA

1. Eles fazem o download da ferramenta do [ Centro de Download da Microsoft ](https://www.microsoft.com/download/details.aspx?id=53595) para a VM do SQL Server no local (**SQLVM**).
2. Eles executam a instalação (DownloadMigrationAssistant.msi) na VM.
3. Sobre o **concluir** página, selecione **iniciar Microsoft dados Assistente de migração** antes de concluir o assistente.

### <a name="migrate-the-database-with-dma"></a>Migrar o banco de dados com o DMA

1. No AMD, eles criam um novo projeto (**SmartHotelDB**) e selecionam **Migração**.
2. Eles escolhem o tipo de servidor de origem como **SQL Server** e o destino como **Banco de Dados SQL do Azure**.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-1.png)

3. Nos detalhes da migração, eles adicionam **SQLVM** como o servidor de origem e o banco de dados **SmartHotel.Registration**.

     ![DMA](media/contoso-migration-refactor-web-app-sql/dma-2.png)

4. Eles recebem um erro que parece estar associado à autenticação. No entanto, após investigar, o problema é o ponto (.) no nome do banco de dados. Como solução alternativa, eles decidiram provisionar um novo banco de dados SQL usando o nome **SmartHotel-Registration** para resolver o problema. Quando eles executam o DMA novamente, são capazes de selecionar **SmartHotel-Registration** e continuar com o assistente.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-3.png)

5. Em **Selecionar Objetos**, selecionam as tabelas de banco de dados e gerar um script SQL.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-4.png)

6. Depois que o AMD cria o script, eles selecionam **Implantar esquema**.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-5.png)

7. O DMA confirma que a implantação foi realizada com êxito.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-6.png)

8. Agora eles iniciam a migração.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-7.png)

9. Após a conclusão da migração, os administradores da Contoso podem verificar se o banco de dados está sendo executado na instância do Azure SQL.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-8.png)

10. Eles excluem o banco de dados SQL extra **SmartHotel.Registration** no portal do Azure.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-9.png)

## <a name="step-3-provision-web-apps"></a>Etapa 3: provisionar aplicativos Web

Com o banco de dados migrado, os administradores da Contoso agora podem provisionar os dois aplicativos da web.

1. Eles selecionam **Aplicativo Web** no portal.

    ![Aplicativo Web](media/contoso-migration-refactor-web-app-sql/web-app1.png)

2. Eles fornecem um nome de aplicativo (**SHWEB-EUS2**), executam o aplicativo no Windows e o colocam no grupo de recursos de produção **ContosoRG**. Eles criam um novo aplicativo Web e Plano do Serviço de Aplicativo do Azure.

    ![Aplicativo Web](media/contoso-migration-refactor-web-app-sql/web-app2.png)

3. Depois que o aplicativo Web é provisionado, eles repetem o processo para criar um aplicativo Web para o serviço WCF (**SHWCF-EUS2**)

    ![Aplicativo Web](media/contoso-migration-refactor-web-app-sql/web-app3.png)

4. Após concluírem, eles navegam par ao endereço dos aplicativos para verificar se foram criados com êxito.

## <a name="step-4-set-up-azure-devops"></a>Etapa 4: Configurar o Azure DevOps

A Contoso precisa criar a infraestrutura e os pipelines de DevOps para o aplicativo. Para fazer isso, os administradores da Contoso criam um projeto do Azure DevOps, importam o código e, em seguida, configuram os pipelines de build e lançamento.

1. Na conta do Azure DevOps da Contoso, eles criam um projeto (**ContosoSmartHotelRefactor**) e selecionam o **Git** para controle de versão.

    ![Novo Projeto](./media/contoso-migration-refactor-web-app-sql/vsts1.png)

2. Eles importam o repositório Git que atualmente contém seu código do aplicativo. Ele está em um [repositório público](https://github.com/Microsoft/SmartHotel360-internal-booking-apps) e você pode baixá-lo.

    ![Baixar código do aplicativo](./media/contoso-migration-refactor-web-app-sql/vsts2.png)

3. Depois que o código for importado, eles conectarão o Visual Studio ao repositório e clonarão o código usando o Team Explorer.

    ![Conectar-se ao projeto](./media/contoso-migration-refactor-web-app-sql/devops1.png)

4. Depois que o repositório for clonado para o computador do desenvolvedor, eles abrirão o arquivo de solução do aplicativo. O aplicativo Web e o serviço wccf têm, cada um, um projeto separado dentro do arquivo.

    ![Arquivo de solução](./media/contoso-migration-refactor-web-app-sql/vsts4.png)

## <a name="step-5-configure-connection-strings"></a>Etapa 5: Configurar sequências de conexão

Os administradores da Contoso precisam garantir que os aplicativos da Web e o banco de dados possam se comunicar. Para fazer isso, eles configuram cadeias de conexão no código e nos aplicativos Web.

1. No aplicativo Web para o serviço WCF (**SHWCF-EUS2**) > **Configurações** > **Configurações de aplicativo**, eles adicionam uma nova cadeia de conexão chamada **DefaultConnection**.
2. A cadeia de conexão é obtida do banco de dados **SmartHotel-Registration** e deve ser atualizada com as credenciais corretas.

    ![Cadeia de conexão](media/contoso-migration-refactor-web-app-sql/string1.png)

3. Usando o Visual Studio, eles abrem o projeto **SmartHotel.Registration.wcf** do arquivo da solução. A seção **connectionStrings** do arquivo web.config para o serviço WCF SmartHotel.Registration.Wcf deve ser atualizada com a cadeia de conexão.

     ![Cadeia de conexão](media/contoso-migration-refactor-web-app-sql/string2.png)

4. A seção **client** do arquivo web.config para o SmartHotel.Registration.Web deve ser alterada para apontar para a nova localização do serviço WCF. Esta é a URL do aplicativo Web WCF que hospeda o ponto de extremidade de serviço.

    ![Cadeia de conexão](media/contoso-migration-refactor-web-app-sql/strings3.png)

5. Depois que as alterações estão no código, os administradores precisam confirmar as alterações. Usando o Team Explorer no Visual Studio, eles confirmam e sincronizam.

## <a name="step-6-set-up-build-and-release-pipelines-in-azure-devops"></a>Etapa 6: Configurar os pipelines de build e lançamento do Azure DevOps

Agora, os administradores da Contoso configuram o Azure DevOps para executar o processo de build e lançamento.

1. No Azure DevOps, eles selecionam **Build e lançamento** > **Novo pipeline**.

    ![Novo pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline1.png)

2. Eles selecionam o **Git do Azure Repos** e o repositório relevante.

    ![Git e repositório](./media/contoso-migration-refactor-web-app-sql/pipeline2.png)

3. Em **Selecione um modelo**, eles selecionam o modelo ASP.NET para sua construção.

     ![Modelo do ASP.NET](./media/contoso-migration-refactor-web-app-sql/pipeline3.png)

4. O nome **ContosoSmartHotelRefactor-ASP.NET-CI** é usado para o build. Eles selecionam **Salvar e Fila**.

     ![Salvar e enfileirar](./media/contoso-migration-refactor-web-app-sql/pipeline4.png)

5. Isso inicia o primeiro build. Eles selecionam o número da compilação para assistir ao processo. Após a conclusão, eles podem ver os comentários do processo e selecionar **Artefatos** para examinar os resultados do build.

    ![Análise](./media/contoso-migration-refactor-web-app-sql/pipeline5.png)

6. A pasta **Destino** contém os resultados do build.

    - Os dois arquivos zip são os pacotes que contêm os aplicativos.
    - Esses arquivos são usados no pipeline de lançamento para implantação no Serviço de Aplicativo do Azure.

     ![Artefato](./media/contoso-migration-refactor-web-app-sql/pipeline6.png)

7. Eles selecionam **Lançamentos** >  **+ Novo pipeline**.

    ![Novo pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline7.png)

8. Eles selecionam o modelo de implantação no Serviço de Aplicativo do Azure.

    ![Modelo de implantação do Serviço de Aplicativo do Azure](./media/contoso-migration-refactor-web-app-sql/pipeline8.png)

9. Eles nomeiam o pipeline de lançamento como **ContosoSmartHotel360Refactor** e especificam o nome do aplicativo Web do WCF (SHWCF-EUS2) para o nome do **Estágio**.

    ![Ambiente](./media/contoso-migration-refactor-web-app-sql/pipeline9.png)

10. Nos estágios, eles selecionam **1 trabalho, 1 tarefa** para configurar a implantação do serviço WCF.

    ![Implantar o WCF](./media/contoso-migration-refactor-web-app-sql/pipeline10.png)

11. Eles verificam se a assinatura está selecionada e autorizada e selecionam o **nome do serviço de aplicativo**.

     ![Selecionar o nome do serviço de aplicativo](./media/contoso-migration-refactor-web-app-sql/pipeline11.png)

12. No pipeline > **Artefatos**, eles selecionam **+ Adicionar um artefato** e selecionam compilar com o pipeline **ContosoSmarthotel360Refactor**.

     ![Compilação](./media/contoso-migration-refactor-web-app-sql/pipeline12.png)

13. Eles selecionam o raio do artefato verificado, para ativar o gatilho de implantação contínua.

     ![Raio](./media/contoso-migration-refactor-web-app-sql/pipeline13.png)

14. O gatilho de implantação contínua deve ser definido como **Habilitado**.

    ![Implantação contínua habilitada](./media/contoso-migration-refactor-web-app-sql/pipeline14.png)

15. Agora, eles retornam ao Estágio 1 trabalho, I tarefa e selecionam **Implantar o Serviço de Aplicativo do Azure**.

    ![Implantar o Serviço de Aplicativo do Azure](./media/contoso-migration-refactor-web-app-sql/pipeline15.png)

16. Em **Selecionar um arquivo ou pasta**, localizam o arquivo **SmartHotel.Registration.Wcf.zip** que estava sendo criado durante o build e selecionam **Salvar**.

    ![Salve o WCF](./media/contoso-migration-refactor-web-app-sql/pipeline16.png)

17. Eles selecionam **Pipeline** > **Estágios** **+ Adicionar**, para adicionar um ambiente para **SHWEB-EUS2**. Eles selecionam outra implantação do Serviço de Aplicativo do Azure.

    ![Adicionar o ambiente](./media/contoso-migration-refactor-web-app-sql/pipeline17.png)

18. Eles repetem o processo para publicar o arquivo do aplicativo da web (**SmartHotel.Registration.Web.zip**) no aplicativo da Web correto.

    ![Publicar aplicativo web](./media/contoso-migration-refactor-web-app-sql/pipeline18.png)

19. Depois que ele for salvo, o pipeline de lançamento será exibido da seguinte maneira.

     ![Resumo de pipeline de versão](./media/contoso-migration-refactor-web-app-sql/pipeline19.png)

20. Eles voltam para **Build** e selecionam **Gatilhos** > **Habilitar a integração contínua**. Isso permite que o pipeline, quando as alterações são confirmadas no código, ocorra a criação e liberação completas.

    ![Ativar integração contínua](./media/contoso-migration-refactor-web-app-sql/pipeline20.png)

21. Eles selecionam **Salvar e Fila** para executar o pipeline completo. Uma nova compilação é disparada, que, por sua vez, cria a primeira versão do aplicativo para o Serviço de Aplicativo do Azure.

    ![Salve o pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline21.png)

22. Os administradores da Contoso podem seguir o processo do pipeline de build e de lançamento por meio do Azure DevOps. Após a conclusão da compilação, a liberação será iniciada.

    ![Criar e liberar aplicativo](./media/contoso-migration-refactor-web-app-sql/pipeline22.png)

23. Após o término do pipeline, os dois sites foram implantados e o aplicativo está funcionando on-line.

    ![Versão de término](./media/contoso-migration-refactor-web-app-sql/pipeline23.png)

Neste ponto, o aplicativo é migrado com êxito para o Azure.

## <a name="clean-up-after-migration"></a>Limpeza após a migração

Após a migração, a Contoso precisa concluir estas etapas de limpeza:

- Remova as VMs locais do inventário do vCenter.
- Remova as VMs das tarefas de backup locais.
- Atualize a documentação interna para mostrar os novos locais para o aplicativo SmartHotel360. Mostre o banco de dados como em execução no Banco de Dados SQL do Azure e o front-end como em execução nos dois aplicativos Web.
- Revise todos os recursos que interagem com as VMs desatribuídas e atualize quaisquer configurações ou documentação relevantes para refletir a nova configuração.

## <a name="review-the-deployment"></a>Revisar a implantação

Com os recursos migrados no Azure, a Contoso precisa operacionalizar e proteger totalmente sua nova infraestrutura.

### <a name="security"></a>Segurança

- A Contoso precisa garantir que o novo **banco de dados de Registro do SmartHotel** seja seguro. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview).
- Em particular, a Contoso deve atualizar os aplicativos da Web para usar SSL com certificados.

### <a name="backups"></a>Backups

- A Contoso precisa examinar os requisitos de backup do Banco de Dados SQL do Azure. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).
- A Contoso também precisa aprender sobre como gerenciar backups e restaurações do Banco de Dados SQL. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups) sobre backups automáticos.
- A Contoso deve considerar a implementação de grupos de failover para fornecer failover regional para o banco de dados. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview).
- A Contoso precisa considerar a implantação do aplicativo Web na região principal Leste dos EUA 2 e na região Centro dos EUA para obter resiliência. A Contoso pode configurar o Gerenciador de Tráfego para garantir o failover em caso de interrupções regionais.

### <a name="licensing-and-cost-optimization"></a>Licenciamento e otimização de custo

- Depois que todos os recursos estiverem implantados, a Contoso deverá atribuir marcações ao Azure com base no seu [planejamento de infraestrutura](./contoso-migration-infrastructure.md#set-up-tagging).
- Todo o licenciamento se baseia no custo dos serviços de PaaS que a Contoso está consumindo. Isso será deduzido do EA.
- A Contoso habilitará o Gerenciamento de Custos do Azure licenciado pela Cloudyn, uma subsidiária da Microsoft. É uma solução de gerenciamento de custos em várias nuvens que ajuda a usar e gerenciar o Azure e outros recursos de nuvem. [Saiba mais](https://docs.microsoft.com/azure/cost-management/overview) sobre o Gerenciamento de Custos do Azure.

## <a name="conclusion"></a>Conclusão

Neste artigo, a Contoso refatorou o aplicativo SmartHotel360 no Azure migrando a VM de front-end do aplicativo para dois aplicativos Web do Serviço de Aplicativo do Azure. O banco de dados do aplicativo foi mirado para um banco de dados SQL do Azure.
