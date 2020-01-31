---
title: Recompilar um aplicativo local para Azure
description: Saiba como a Contoso recompila um aplicativo no Azure usando o Serviço de Aplicativo do Azure, o Serviço de Kubernetes do Azure, o Cosmos DB, o Azure Functions e os Serviços Cognitivos do Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: e2904356871eec65b516b7a02c356c679ab86b33
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76807488"
---
# <a name="rebuild-an-on-premises-app-on-azure"></a>Recompilar um aplicativo local no Azure

Este artigo demonstra como a empresa fictícia Contoso recompila um aplicativo de duas camadas .NET do Windows em execução em VMs VMware como parte de uma migração para o Azure. A Contoso migra a VM de front-end do aplicativo para um aplicativo Web do Serviço de Aplicativo do Azure. O back-end do aplicativo é criado usando microsserviços implantados em contêineres gerenciados pelo AKS (Serviço de Kubernetes do Azure). O site interage com o Azure Functions para fornecer a funcionalidade de fotos de animais de estimação.

O aplicativo SmartHotel360 usado neste exemplo é fornecido como software livre. Se quiser usá-lo em seus próprios testes, você poderá baixá-lo do [GitHub](https://github.com/Microsoft/SmartHotel360).

## <a name="business-drivers"></a>Geradores de negócios

A equipe de liderança de TI trabalhou em conjunto com parceiros comerciais para entender o que eles desejam obter com essa migração:

- **Lidar com o crescimento da empresa.** A Contoso está crescendo e quer fornecer experiências diferenciadas aos clientes nos sites da Contoso.
- **Ser ágil.** A Contoso deve ser capaz de reagir mais rápido frente às mudanças no mercado para possibilitar o sucesso em uma economia global.
- **Escala.** Na medida em que a empresa cresce com sucesso, a equipe de TI da Contoso deve disponibilizar sistemas capazes de crescer no mesmo ritmo.
- **Reduzir custos.** a Contoso quer minimizar os custos de licenciamento.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem da Contoso fixou os requisitos do aplicativo para esta migração. Esses requisitos foram usados para determinar o melhor método de migração:

- O aplicativo no Azure ainda é tão importante quanto é hoje. Ele deve ter um bom desempenho e ser dimensionado facilmente.
- O aplicativo não deve usar componentes de IaaS. Tudo o que deve ser criado para usar PaaS ou serviços sem servidor.
- Os builds de aplicativo devem ser executados nos serviços de nuvem e os contêineres devem residir em um Registro de contêiner de toda a empresa privado na nuvem.
- O serviço de API usado para fotos de animais de estimação deve ser precisa e confiável no mundo real, uma vez que as decisões tomadas pelo aplicativo devem ser respeitadas em seus hotéis. Qualquer animal de estimação com acesso concedido pode permanecer nos hotéis.
- Para atender aos requisitos de um pipeline de DevOps, a Contoso usará o Azure DevOps no SCM (Gerenciamento de Código-fonte), com repositórios Git. Builds e versões automatizadas serão usadas para criar código e implantar no Serviço de Aplicativo do Azure, no Azure Functions e no AKS.
- São necessários diferentes pipelines de CI/CD para os microsserviços no back-end e para o site no front-end.
- Os serviços de back-end têm uma versão diferente do ciclo do aplicativo Web de front-end. Para atender a esse requisito, eles implantarão dois pipelines diferentes.
- A Contoso precisa de aprovação da gerência para todas as implantações do site de front-end e o pipeline de CI/CD precisa fornecer isso.

## <a name="solution-design"></a>Design da solução

Depois de fixar as metas e os requisitos, a Contoso projeta e analisa uma solução de implantação e identifica o processo de migração, incluindo os serviços do Azure que serão usados para migração.

### <a name="current-app"></a>Aplicativo atual

- O aplicativo local SmartHotel360 é dividido em duas VMs (WEBVM e SQLVM).
- As VMs estão localizadas no host VMware ESXi **contosohost1.contoso.com** (versão 6.5)
- O ambiente VMware é gerenciado pelo vCenter Server 6.5 (**vcenter.contoso.com**) em execução em uma VM.
- A Contoso tem um datacenter local (contoso-datacenter), com um controlador de domínio local (**contosodc1**).
- As VMs locais no datacenter da Contoso serão descomissionadas após a migração.

### <a name="proposed-architecture"></a>Arquitetura proposta

- O front-end do aplicativo é implantado como um aplicativo Web do serviço Azure App na região primária do Azure.
- Uma função do Azure fornece os uploads de fotos de animais de estimação e o site interage com essa funcionalidade.
- A função de foto animais de estimação utiliza a API da Pesquisa Visual dos Serviços Cognitivos e o Cosmos DB.
- O back-end do site é criado usando microsserviços. Eles serão implantados em contêineres gerenciados no AKS (Serviço de Kubernetes do Azure).
- Os contêineres serão criados usando o Azure DevOps e enviados por push para o ACR (Registro de Contêiner do Azure).
- Por enquanto, a Contoso implantará manualmente o aplicativo Web e o código da função usando o Visual Studio.
- Os microsserviços serão implantados usando um script do PowerShell que chama as ferramentas de linha de comando do Kubernetes.

    ![Arquitetura de cenário](./media/contoso-migration-rebuild/architecture.png)

### <a name="solution-review"></a>Análise de solução

A Contoso avalia o design proposto reunindo uma lista de prós e contras.

<!-- markdownlint-disable MD033 -->

**Consideração** | **Detalhes**
--- | ---
**Prós** | Usar o PaaS e soluções sem servidor para a implantação de ponta a ponta reduz significativamente o tempo de gerenciamento que a Contoso deve fornecer.<br/><br/> A mudança para uma arquitetura de microsserviço permite que a Contoso, com o tempo, estenda facilmente a solução.<br/><br/> A nova funcionalidade pode ser colocada online sem interromper qualquer uma das bases de código de soluções existentes.<br/><br/> O aplicativo Web será configurado com várias instâncias sem nenhum ponto único de falha.<br/><br/> O dimensionamento automático será habilitado para que o aplicativo possa lidar com diferentes volumes de tráfego.<br/><br/> Com a mudança para os serviços de PaaS, a Contoso pode desativar soluções desatualizadas em execução no sistema operacional Windows Server 2008 R2.<br/><br/> O Cosmos DB tem tolerância a falhas internas que não exige configurações realizadas pela Contoso. Isso significa que a camada de dados não é mais um ponto único de failover.
**Contras** | Contêineres são mais complexos do que outras opções de migração. A curva de aprendizado pode ser um problema para a Contoso. Eles apresentam um novo nível de complexidade que fornece bastante valor apesar da curva.<br/><br/> A equipe de operações da Contoso precisa se esforçar para entender e dar suporte ao Azure, aos contêineres e aos microsserviços do aplicativo.<br/><br/> A Contoso não implementou totalmente o DevOps para toda a solução. A Contoso precisa pensar nisso para a implantação de serviços para o AKS, Azure Functions e Serviço de Aplicativo do Azure.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo de migração

1. A Contoso provisiona o ACR, o AKS e o Cosmos DB.
2. Eles provisionam a infraestrutura para a implantação, incluindo o aplicativo Web, a conta de armazenamento, a função e a API do Serviço de Aplicativo do Azure.
3. Depois que a infraestrutura estiver em vigor, eles criarão suas imagens de contêiner de microsserviços usando o Azure DevOps, que as envia por push para o ACR.
4. A Contoso implantará esses microsserviços no AKS usando um script do PowerShell.
5. Por fim, eles implantarão o aplicativo Web e a função.

    ![Processo de migração](./media/contoso-migration-rebuild/migration-process.png)

### <a name="azure-services"></a>Serviços do Azure

**Serviço** | **Descrição** | **Custo**
--- | --- | ---
[AKS](https://docs.microsoft.com/sql/dma/dma-overview?view=ssdt-18vs2017) | Simplifica o gerenciamento, a implantação e as operações do Kubernetes. Fornece um serviço de orquestração de contêiner do Kubernetes totalmente gerenciado. | O AKS é um serviço gratuito. Pague apenas pelas máquinas virtuais, pelo armazenamento associado e pelos recursos de rede consumidos. [Saiba mais](https://azure.microsoft.com/pricing/details/kubernetes-service).
[Azure Functions](https://azure.microsoft.com/services/functions) | Acelera o desenvolvimento com uma experiência de computação sem servidor orientada por evento. Dimensione sob demanda. | Pague apenas pelos recursos consumidos. O plano é cobrado com base no consumo de recursos e execuções por segundo. [Saiba mais](https://azure.microsoft.com/pricing/details/functions).
[Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry) | Armazena imagens para todos os tipos de implantações de contêiner. | Custo com base em recursos, armazenamento e duração de uso. [Saiba mais](https://azure.microsoft.com/pricing/details/container-registry).
[Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/containers) | Crie, implante e dimensione rapidamente aplicativos de API, móveis e Web de nível corporativo para serem executados em qualquer plataforma. | Os planos do Serviço de Aplicativo são cobrados por segundo. [Saiba mais](https://azure.microsoft.com/pricing/details/app-service/windows).

## <a name="prerequisites"></a>Pré-requisitos

Veja o que a Contoso precisa para esse cenário:

<!-- markdownlint-disable MD033 -->

**Requisitos** | **Detalhes**
--- | ---
**Assinatura do Azure** | A Contoso já criou assinaturas em um artigo anterior. Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se você criar uma conta gratuita, será o administrador da assinatura e poderá executar todas as ações.<br/><br/> Se você usar uma assinatura existente e não for o administrador, será necessário trabalhar com o administrador para receber permissões de Proprietário ou de Colaborador.
**Infraestrutura do Azure** | [ Saiba como ](./contoso-migration-infrastructure.md) a Contoso configurou uma infraestrutura do Azure.
**Pré-requisitos de desenvolvedor** | A Contoso precisa das ferramentas a seguir em uma estação de trabalho de desenvolvedor:<br/><br/> - [Visual Studio 2017 Community Edition: versão 15.5](https://www.visualstudio.com)<br/><br/> Carga de trabalho .NET habilitada.<br/><br/> [Git](https://git-scm.com)<br/><br/> [PowerShell do Azure](https://azure.microsoft.com/downloads)<br/><br/> [CLI do Azure](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)<br/><br/> [Docker CE (Windows 10) ou Docker EE (Windows Server)](https://docs.docker.com/docker-for-windows/install) configurado para usar Contêineres do Windows.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Etapas do cenário

Veja como a Contoso executará a migração:

> [!div class="checklist"]
>
> - **Etapa 1: provisionar AKS e ACR.** A Contoso provisiona o cluster do AKS gerenciado e o registro de contêiner do Azure usando PowerShell.
> - **Etapa 2: criar contêineres do Docker.** Configuram a CI para contêineres do Docker usando Azure DevOp e efetuam push para o ACR.
> - **Etapa 3: implantar microserviços de back-end.** Eles implantam o restante da infraestrutura que será utilizada pelos microsserviços de back-end.
> - **Etapa 4: implantar a infraestrutura de front-end.** Implantam a infraestrutura de front-end, incluindo o armazenamento de blobs para telefones de animais de estimação, Cosmos DB e API de Pesquisa Visual.
> - **Etapa 5: migre o back-end.** Implantam microsserviços e executam no AKS para migrar o back-end.
> - **Etapa 6: publicar o front-end.** Eles publicam o aplicativo SmartHotel360 no Serviço de Aplicativo e aplicativo de funções que será chamado pelo serviço para animais de estimação.

## <a name="step-1-provision-back-end-resources"></a>Etapa 1: Provisionar recursos de back-end

Os administradores da Contoso executam um script de implantação para criar o cluster do Kubernetes gerenciado usando o AKS e o ACR (Registro de Contêiner do Azure).

- As instruções desta seção usam o repositório **SmartHotel360-Azure-backend**.
- O repositório do GitHub **SmartHotel360-Azure-backend** contém todo o software para essa parte da implantação.  

### <a name="ensure-prerequisites"></a>Garantir pré-requisitos

1. Antes de começar, os administradores da Contoso garantem que todos os softwares de pré-requisito instalados no computador de desenvolvimento estejam usando para a implantação.
2. Eles clonam o repositório local no computador de desenvolvimento usando o Git: `git clone https://github.com/Microsoft/SmartHotel360-Azure-backend.git`

### <a name="provision-aks-and-acr"></a>Provisionar o AKS e o ACR

Os administradores da Contoso provisionam da seguinte maneira:

1. Eles abrem a pasta usando o Visual Studio Code e acessam o diretório **/deploy/k8s**, que contém o script **aks-gen-env.ps1**.

2. Eles executam o script para criar o cluster do Kubernetes gerenciado, usando o AKS e o ACR.

   ![AKS](./media/contoso-migration-rebuild/aks1.png)

3. Com o arquivo aberto, eles atualizam o parâmetro $location para **eastus2** e salvam o arquivo.

   ![AKS](./media/contoso-migration-rebuild/aks2.png)

4. Eles escolhem **Exibir** > **Terminal Integrado** para abrir o terminal integrado do Visual Studio Code.

   ![AKS](./media/contoso-migration-rebuild/aks3.png)

5. No terminal integrado do PowerShell, eles entram no Azure usando o comando Connect-AzureRmAccount. [Saiba mais](https://docs.microsoft.com/powershell/azure/get-started-azureps) sobre como começar a trabalhar com o PowerShell.

   ![AKS](./media/contoso-migration-rebuild/aks4.png)

6. Eles autenticam a CLI do Azure executando o comando **az login** e seguindo as instruções para autenticar usando o navegador da Web. [Saiba mais](/cli/azure/authenticate-azure-cli?view=azure-cli-latest) sobre o logon com a CLI do Azure.

   ![AKS](./media/contoso-migration-rebuild/aks5.png)

7. Eles executam o seguinte comando, passando o nome do grupo de recursos de ContosoRG, o nome do cluster AKS smarthotel-aks-eus2 e o nome do novo Registro.

   ```PowerShell
   .\gen-aks-env.ps1  -resourceGroupName ContosoRg -orchestratorName smarthotelakseus2 -registryName smarthotelacreus2
   ```

   ![AKS](./media/contoso-migration-rebuild/aks6.png)

8. O Azure cria outro grupo de recursos, que contém os recursos para o cluster do AKS.

   ![AKS](./media/contoso-migration-rebuild/aks7.png)

9. Depois que a implantação for concluída, instale a ferramenta de linha de comando **kubectl**. A ferramenta já está instalada no Azure CloudShell.

   ```console
   az aks install-cli
   ```

10. Eles verificam a conexão com o cluster executando o comando **kubectl get nodes**. O nó tem o mesmo nome da VM no grupo de recursos criado automaticamente.

    ![AKS](./media/contoso-migration-rebuild/aks8.png)

11. Eles executam o comando a seguir para iniciar o Painel do Kubernetes:

    ```console
    az aks browse --resource-group ContosoRG --name smarthotelakseus2
    ```

12. Uma guia do navegador é aberta no Painel. Essa é uma conexão por túnel usando a CLI do Azure.

    ![AKS](./media/contoso-migration-rebuild/aks9.png)

## <a name="step-2-configure-the-back-end-pipeline"></a>Etapa 2: Configurar o pipeline de back-end

### <a name="create-an-azure-devops-project-and-build"></a>Criar um projeto e build do Azure DevOps

A Contoso cria um projeto do Azure DevOps e configura um Build de CI para criar o contêiner e, em seguida, o envia por push para o ACR. As instruções nesta seção usam o repositório [SmartHotel360-Azure-Backend](https://github.com/Microsoft/SmartHotel360-Azure-backend).

1. Do visualstudio.com, eles criam uma organização (**contosodevops360.visualstudio.com**) e configuram-na para usar o Git.

2. Eles criam um projeto (**SmartHotelBackend**) usando o Git para controle de versão e o Agile para o fluxo de trabalho.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts1.png)

3. Eles importam o [repositório do GitHub](https://github.com/Microsoft/SmartHotel360-Backend).

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts2.png)

4. Em **Pipelines**, eles escolhem **Build** e criam um pipeline usando o Azure Repos Git como uma fonte, a partir do repositório.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts3.png)

5. Eles escolhem iniciar com um trabalho vazio.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts4.png)

6. Eles selecionam **Versão Prévia do Linux Hospedado** para o pipeline de build.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts5.png)

7. Na **Fase 1**, adicionam uma tarefa **Docker Compose**. Essa tarefa cria o Docker Compose.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts6.png)

8. Eles repetem e adicionam outra tarefa **Docker Compose**. Esta envia por push os contêineres para o ACR.

     ![Azure DevOps](./media/contoso-migration-rebuild/vsts7.png)

9. Eles selecionam a primeira tarefa (para compilar) e configuram a compilação com a assinatura do Azure, a autorização e o ACR.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts8.png)

10. Eles especificam o caminho do arquivo **docket-compose.yaml** na pasta **src** do repositório. Eles escolhem criar imagens de serviço e incluem a marca mais recente. Quando a ação muda para **Criar imagens de serviço**, o nome da tarefa do Azure DevOps muda para **Criar serviços automaticamente**.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts9.png)

11. Agora, eles configuram a segunda tarefa do Docker (para enviar por push). Eles selecionam a assinatura e o ACR **smarthotelacreus2**.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts10.png)

12. Novamente, eles inserem o arquivo para o arquivo docker-compose.yaml e selecionam **Enviar imagens de serviço por push** e incluem a marcação mais recente. Quando a ação muda para **Enviar de imagens de serviço por push**, o nome da tarefa do Azure DevOps muda para **Enviar serviços por push automaticamente**.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts11.png)

13. Com as tarefas do Azure DevOps configuradas, a Contoso salva o pipeline de build e inicia o processo de build.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts12.png)

14. Eles escolhem o trabalho de build para verificar o progresso.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts13.png)

15. Após a conclusão do build, o ACR mostra os novos repositórios, que são populados com os contêineres usados pelos microsserviços.

    ![Azure DevOps](./media/contoso-migration-rebuild/vsts14.png)

### <a name="deploy-the-back-end-infrastructure"></a>Implantar a infraestrutura de back-end

Com o cluster do AKS criado e o build das imagens do Docker, a Contoso agora administra o restante da infraestrutura que será utilizada pelos microsserviços de back-end.

- As instruções na seção usam o repositório [SmartHotel360-Azure-Backend](https://github.com/Microsoft/SmartHotel360-Azure-backend).
- Na pasta **/deploy/k8s/arm** há um único script para criar todos os itens.

Eles implantam da seguinte maneira:

1. Eles abrem um Prompt de Comando do Desenvolvedor e usam o comando logon az para a assinatura do Azure.
2. Eles usam o arquivo deploy.cmd para implantar os recursos do Azure no grupo de recursos ContosoRG e na região EUS2, digitando o seguinte comando:

    ```console
    .\deploy.cmd azuredeploy ContosoRG -c eastus2
    ```

    ![Implantar back-end](./media/contoso-migration-rebuild/backend1.png)

3. No portal do Azure, eles capturam a cadeia de conexão de cada banco de dados para uso posterior.

    ![Implantar back-end](./media/contoso-migration-rebuild/backend2.png)

### <a name="create-the-back-end-release-pipeline"></a>Criar o pipeline de lançamento de back-end

Agora, os administradores da Contoso fazem o seguinte:

- Implantam o controlador de entrada NGINX para permitir o tráfego de entrada para os serviços.
- Implantam os microsserviços no cluster do AKS.
- Como uma primeira etapa, eles atualizam as cadeias de conexão dos microsserviços usando o Azure DevOps. Em seguida, eles configuram um novo pipeline de lançamento do Azure DevOps para implantar os microsserviços.
- As instruções nesta seção usam o repositório [SmartHotel360-Azure-Backend](https://github.com/Microsoft/SmartHotel360-Azure-backend).
- Algumas das definições de configuração (por exemplo Active Directory B2C) não são abordadas neste artigo. Para obter mais informações sobre essas configurações, examine o repositório acima.

Eles criam o pipeline:

1. Usando o Visual Studio, eles atualizam o arquivo **/deploy/k8s/config_local.yml** com as informações de conexão de banco de dados que já anotaram.

    ![Conexões de banco de dados](./media/contoso-migration-rebuild/back-pipe1.png)

2. Eles abrem o Azure DevOps e, no projeto SmartHotel360, em **Versões**, escolhem **+Novo Pipeline**.

    ![Novo pipeline](./media/contoso-migration-rebuild/back-pipe2.png)

3. Eles escolhem **Trabalho Vazio** para iniciar o pipeline sem um modelo.
4. Eles fornecem os nomes do estágio e do pipeline.

      ![Nome do estágio](./media/contoso-migration-rebuild/back-pipe4.png)

      ![Nome do pipeline](./media/contoso-migration-rebuild/back-pipe5.png)

5. Eles adicionam um artefato.

     ![Adicionar artefato](./media/contoso-migration-rebuild/back-pipe6.png)

6. Eles selecionam **Git** como o tipo de fonte e especificam o projeto, a fonte e o branch mestre do aplicativo SmartHotel360.

    ![Configurações de artefato](./media/contoso-migration-rebuild/back-pipe7.png)

7. Eles selecionam o link de tarefa.

    ![Link de tarefa](./media/contoso-migration-rebuild/back-pipe8.png)

8. Eles adicionam uma nova tarefa do Azure PowerShell para poderem executar um script do PowerShell em um ambiente do Azure.

    ![PowerShell no Azure](./media/contoso-migration-rebuild/back-pipe9.png)

9. Eles selecionam a assinatura do Azure para a tarefa e selecionam o script **deploy.ps1** do repositório Git.

    ![Executar script](./media/contoso-migration-rebuild/back-pipe10.png)

10. Eles adicionam argumentos ao script. O script excluirá todo o conteúdo do cluster (exceto a **entrada** e o **controlador de entrada**) e implantará os microsserviços.

    ![Argumentos de script](./media/contoso-migration-rebuild/back-pipe11.png)

11. Eles definem a versão preferencial do Azure PowerShell como a versão mais recente e salvam o pipeline.

12. Eles retornam à página **Versão** e criam uma versão manualmente.

    ![Nova versão](./media/contoso-migration-rebuild/back-pipe12.png)

13. Eles escolhem a versão depois de criá-la e, em **Ações**, escolhem **Implantar**.

      ![Implantar versão](./media/contoso-migration-rebuild/back-pipe13.png)

14. Quando a implantação é concluída, eles executam o seguinte comando para verificar o status dos serviços usando o Azure Cloud Shell: **kubectl get services**.

## <a name="step-3-provision-front-end-services"></a>Etapa 3: Provisionar serviços de front-end

Os administradores da Contoso precisam implantar a infraestrutura que será usada pelos aplicativos de front-end. Eles criam um contêiner de Armazenamento de Blobs para armazenar as imagens de animais de estimação, o banco de dados do Cosmos para armazenar documentos com as informações de animais de estimação e a API da Pesquisa Visual para o site.

As instruções desta seção usam o repositório [SmartHotel360-public-web](https://github.com/Microsoft/SmartHotel360-public-web).

### <a name="create-blob-storage-containers"></a>Criar contêineres de armazenamento de blobs

1. No portal do Azure, eles abrem a conta de armazenamento que foi criada e escolhem **Blobs**.
2. Eles criam um novo contêiner (**Pets**) com o nível de acesso público definido como o contêiner. Os usuários carregarão as fotos de seu animal de estimação para esse contêiner.

    ![Armazenamento de blobs](./media/contoso-migration-rebuild/blob1.png)

3. Eles criam um segundo novo contêiner chamado **settings**. Um arquivo com todas as configurações de aplicativo front-end será colocado nesse contêiner.

    ![Armazenamento de blobs](./media/contoso-migration-rebuild/blob2.png)

4. Eles capturam os detalhes de acesso da conta de armazenamento em um arquivo de texto para referência futura.

    ![Armazenamento de blobs](./media/contoso-migration-rebuild/blob2.png)

### <a name="provision-a-cosmos-database"></a>Provisionar um banco de dados do Cosmos

Os administradores da Contoso provisionam um banco de dados do Cosmos a ser usado para as informações sobre animais de estimação.

1. Eles criam um **Azure Cosmos DB** no Azure Marketplace.

    ![Cosmos DB](./media/contoso-migration-rebuild/cosmos1.png)

2. Eles especificam um nome (**contosomarthotel**), selecionam a API SQL e a colocam no grupo de recursos de produção ContosoRG, na região Leste dos EUA 2 principal.

    ![Cosmos DB](./media/contoso-migration-rebuild/cosmos2.png)

3. Eles adicionam uma nova coleção ao banco de dados, com a capacidade e a taxa de transferência padrão.

    ![Cosmos DB](./media/contoso-migration-rebuild/cosmos3.png)

4. Eles anotam as informações de conexão do banco de dados para referência futura.

    ![Cosmos DB](./media/contoso-migration-rebuild/cosmos4.png)

### <a name="provision-computer-vision"></a>Provisionar Pesquisa Visual Computacional

Os administradores da Contoso provisionam a API da Pesquisa Visual Computacional. A API será chamada pela função, para avaliar imagens carregadas pelos usuários.

1. Eles criam uma instância de **Pesquisa Visual Computacional** no Azure Marketplace.

     ![Visual computacional](./media/contoso-migration-rebuild/vision1.png)

2. Eles provisionam a API (**smarthotelpets**) no grupo de recursos de produção ContosoRG, na região Leste dos EUA 2 principal.

    ![Visual computacional](./media/contoso-migration-rebuild/vision2.png)

3. Eles salvam as configurações de conexão para a API em um arquivo de texto para referência posterior.

     ![Visual computacional](./media/contoso-migration-rebuild/vision3.png)

### <a name="provision-the-azure-web-app"></a>Provisionar o aplicativo Web do Azure

Os administradores da Contoso provisionam o aplicativo Web usando o portal do Azure.

1. Eles selecionam **Aplicativo Web** no portal.

    ![Aplicativo Web](media/contoso-migration-rebuild/web-app1.png)

2. Eles fornecem um nome ao aplicativo (**smarthotelcontoso**), executam-o no Windows e colocam-no no grupo de recursos de produção **ContosoRG**. Eles criam uma instância do Application Insights para o monitoramento do aplicativo.

    ![Nome do aplicativo Web](media/contoso-migration-rebuild/web-app2.png)

3. Depois de concluírem, eles navegam para o endereço do aplicativo para verificar se ele foi criado com êxito.

4. Agora, no portal do Azure, eles criam um slot de preparo para o código. O pipeline implantará neste slot. Isso garante que o código não seja colocado em produção até que os administradores executem um lançamento.

    ![Slot de preparo do aplicativo Web](media/contoso-migration-rebuild/web-app3.png)

### <a name="provision-the-azure-function-app"></a>Provisionar o aplicativo de funções do Azure

No portal do Azure, os administradores da Contoso provisionam o aplicativo de funções.

1. Eles selecionam **Aplicativo de Funções**.

   ![Criar aplicativo de funções](./media/contoso-migration-rebuild/function-app1.png)

2. Eles fornecem um nome ao aplicativo (**smarthotelpetchecker**). Eles colocam o aplicativo no grupo de recursos de produção **ContosoRG**, definem a localização de hospedagem como **Plano de Consumo** e colocam o aplicativo na região Leste dos EUA 2. Uma conta de armazenamento é criada, junto com uma instância do Application Insights para monitoramento.

   ![Configurações do aplicativo de funções](./media/contoso-migration-rebuild/function-app2.png)

3. Depois que o aplicativo é implantado, eles navegam para o endereço do aplicativo para verificar se ele foi criado com êxito.

## <a name="step-4-set-up-the-front-end-pipeline"></a>Etapa 4: Configurar o pipeline de front-end

Os administradores da Contoso criam dois projetos diferentes para o site de front-end.

1. No Azure DevOps, eles criam o projeto **SmartHotelFrontend**.

   ![Projeto de front-end](./media/contoso-migration-rebuild/function-app1.png)

2. Eles importam o repositório Git do [front-end do SmartHotel360](https://github.com/Microsoft/SmartHotel360-public-web.git) para o novo projeto.

3. Para o aplicativo de funções, eles criam outro projeto do Azure DevOps (SmartHotelPetChecker) e importam o repositório Git [PetChecker](https://github.com/sonahander/SmartHotel360-PetCheckerFunction) para esse projeto.

### <a name="configure-the-web-app"></a>Configurar o aplicativo Web

Agora os administradores da Contoso configuram o aplicativo Web para usar os recursos da Contoso.

1. Eles se conectam ao projeto do Azure DevOps e clonam o repositório localmente para o computador de desenvolvimento.
2. No Visual Studio, eles abrem a pasta para mostrar todos os arquivos no repositório.

    ![Arquivos do repositório](./media/contoso-migration-rebuild/configure-webapp1.png)

3. Eles atualizam as alterações de configuração conforme o necessário.

    - Quando o aplicativo Web é iniciado, ele procura a configuração de aplicativo **SettingsUrl**.
    - Essa variável precisa conter uma URL que aponte para um arquivo de configuração.
    - Por padrão, a configuração usada é um ponto de extremidade público.

4. Eles atualizam o arquivo /config-sample.json/sample.json.

    - Esse é o arquivo de configuração para a Web ao usar o ponto de extremidade público.
    - Eles editam as seções **urls** e **pets_config** com os valores dos pontos de extremidade da API do AKS, das contas de armazenamento e do banco de dados do Cosmos.
    - As URLs devem corresponder ao nome DNS do novo aplicativo Web que Contoso criará.
    - Para a Contoso, isso é **smarthotelcontoso.eastus2.cloudapp.azure.com**.

    ![Definições de JSON](./media/contoso-migration-rebuild/configure-webapp2.png)

5. Depois que o arquivo é atualizado, é renomeado para **smarthotelsettingsurl**e é carregado para o armazenamento de blob que foi criado anteriormente.

    ![Renomear e fazer upload](./media/contoso-migration-rebuild/configure-webapp3.png)

6. Eles escolhem o arquivo para obter a URL. A URL é usada pelo aplicativo quando ele extrai os arquivos de configuração.

    ![URL do aplicativo](./media/contoso-migration-rebuild/configure-webapp4.png)

7. No arquivo **appsettings.Production.json**, eles atualizam a **SettingsURL** para a URL do novo arquivo.

    ![URL de atualização](./media/contoso-migration-rebuild/configure-webapp5.png)

### <a name="deploy-the-website-to-azure-app-service"></a>Implantar o site para o Serviço de Aplicativo do Azure

Os administradores da Contoso agora podem publicar o site.

1. Eles abrem o Azure DevOps e, no projeto **SmartHotelFrontend**, em **Builds e Versões**, escolhem **+Novo Pipeline**.
2. Eles selecionam o **Git do Azure DevOps** como uma fonte.
3. Eles selecionam o modelo **ASP.NET Core**.
4. Eles examinam o pipeline e verificam se **Publicar Projetos Web** e **Zipar Projetos Publicados** estão selecionados.

    ![Configurações do pipeline](./media/contoso-migration-rebuild/vsts-publishfront2.png)

5. Em **Gatilhos**, eles habilitam a integração contínua e adicionam o branch mestre. Isso garante que sempre que a solução tiver um novo código confirmado para o branch mestre, o pipeline de build seja iniciado.

    ![Integração contínua](./media/contoso-migration-rebuild/vsts-publishfront3.png)

6. Eles escolhem **Salvar e enfileirar** para iniciar um build.
7. Depois que o build é concluído, eles configuram um pipeline de lançamento usando a **Implantação do Serviço de Aplicativo do Azure**.
8. Eles fornecem o nome **Preparo**.

    ![Nome do ambiente](./media/contoso-migration-rebuild/vsts-publishfront4.png)

9. Eles adicionam um artefato e selecionam o build que acabaram de configurar.

     ![Adicionar artefato](./media/contoso-migration-rebuild/vsts-publishfront5.png)

10. Eles escolhem o ícone de raio no artefato e habilitam a implantação contínua.

    ![Implantação contínua](./media/contoso-migration-rebuild/vsts-publishfront6.png)
11. Em **Ambiente**, eles escolhem **1 trabalho, 1 tarefa** em **Preparo**.
12. Depois de selecionar a assinatura e o nome do aplicativo, eles abrem a tarefa **Implantar Serviço de Aplicativo do Azure**. A implantação está configurada para usar o slot de implantação **Preparo**. Isso cria automaticamente o código para revisão e aprovação neste slot.

     ![Slot](./media/contoso-migration-rebuild/vsts-publishfront7.png)

13. No **Pipeline**, eles adicionam um novo estágio.

    ![Novo ambiente](./media/contoso-migration-rebuild/vsts-publishfront8.png)

14. Eles selecionam a **implantação do Serviço de Aplicativo do Azure com o espaço** e nomeiam o ambiente **Prod**.
15. Eles escolhem **1 trabalho, 2 tarefas** e escolhem a assinatura, o nome do serviço de aplicativo e o slot **Preparo**.

    ![Nome do ambiente](./media/contoso-migration-rebuild/vsts-publishfront10.png)

16. Eles removem a ação **Implantar o Serviço de Aplicativo do Azure no Slot** do pipeline. Ele foi colocado lá pelas etapas anteriores.

    ![Remover do pipeline](./media/contoso-migration-rebuild/vsts-publishfront11.png)

17. Eles salvam o pipeline. No pipeline, eles escolhem **Condições pós-implantação**.

    ![Pós-implantação](./media/contoso-migration-rebuild/vsts-publishfront12.png)

18. Eles habilitam as **Aprovações pós-implantação** e adicionam um desenvolvedor líder como o aprovador.

    ![Aprovação pós-implantação](./media/contoso-migration-rebuild/vsts-publishfront13.png)

19. No pipeline de build, eles iniciam um build manualmente. Isso dispara o novo pipeline de lançamento, que implanta o site no slot de preparo. Para a Contoso, a URL do slot é `https://smarthotelcontoso-staging.azurewebsites.net/`.

20. Após a conclusão do build e a implantação da versão no slot, o Azure DevOps envia um email de aprovação ao desenvolvedor líder.

21. O desenvolvedor líder escolhe **Exibir aprovação** e pode aprovar ou rejeitar a solicitação no portal do Azure DevOps.

    ![Email de aprovação](./media/contoso-migration-rebuild/vsts-publishfront14.png)

22. O líder faz um comentário e aprova. Isso inicia a troca dos slots de **preparo** e de **prod** e passa o build para a produção.

    ![Aprovar e trocar](./media/contoso-migration-rebuild/vsts-publishfront15.png)

23. O pipeline conclui a troca.

    ![Troca completa](./media/contoso-migration-rebuild/vsts-publishfront16.png)

24. A equipe verifica o slot de **prod** para saber se o aplicativo Web está em produção em `https://smarthotelcontoso.azurewebsites.net/`.

### <a name="deploy-the-petchecker-function-app"></a>Implantar o aplicativo de funções PetChecker

Os administradores da Contoso implantam o aplicativo da seguinte maneira.

1. Eles clonam o repositório localmente para o computador de desenvolvimento se conectando ao projeto do Azure DevOps.
2. No Visual Studio, eles abrem a pasta para mostrar todos os arquivos no repositório.
3. Eles abrem o arquivo **src/PetCheckerFunction/local.settings.json** e adicionam as configurações do aplicativo para armazenamento, o banco de dados do Cosmos e a API da Pesquisa Visual Computacional.

    ![Implantar a função](./media/contoso-migration-rebuild/function5.png)

4. Eles confirmam o código e sincronizam-no novamente com o Azure DevOps, enviando as alterações por push.
5. Eles adicionam um novo pipeline de build e selecionam o **Git do Azure DevOps** como a fonte.
6. Eles selecionam o modelo **ASP.NET Core (.NET Framework)** .
7. Eles aceitam os padrões do modelo.
8. Em **Gatilhos**, eles escolhem **Habilitar a integração contínua** e **Salvar e Enfileirar** para iniciar um build.
9. Depois que o build é bem-sucedido, eles criam um pipeline de lançamento adicionando a **Implantação do Serviço de Aplicativo do Azure com o slot**.
10. Eles nomeiam o ambiente como **Prod**e selecionam a assinatura. Eles definem o **Tipo de aplicativo** como **Aplicativo de Funções** e o nome do Serviço de Aplicativo como **smarthotelpetchecker**.

    ![Aplicativo de funções](./media/contoso-migration-rebuild/petchecker2.png)

11. Eles adiciona um artefato **Build**.

    ![Artefato](./media/contoso-migration-rebuild/petchecker3.png)

12. Elas habilitam o **Gatilho de implantação contínua** e escolhem **Salvar**.
13. Eles escolhem **Enfileirar novo build** para executar o pipeline de CI/CD completo.
14. Depois que a função é implantada, ela aparece no portal do Azure, com o status **Em Execução**.

    ![Implantar a função](./media/contoso-migration-rebuild/function6.png)

15. Eles navegam até o aplicativo para testar se aplicativo Pet Checker está funcionando como esperado em [http://smarthotel360public.azurewebsites.net/Pets](http://smarthotel360public.azurewebsites.net/Pets).

16. Eles escolhem o avatar para carregar uma imagem.

    ![Implantar a função](./media/contoso-migration-rebuild/function7.png)

17. A primeira foto que desejam verificar é de um cachorro pequeno.

    ![Implantar a função](./media/contoso-migration-rebuild/function8.png)

18. O aplicativo retornar uma mensagem de aceitação.

    ![Implantar a função](./media/contoso-migration-rebuild/function9.png)

## <a name="review-the-deployment"></a>Revisar a implantação

Com os recursos migrados para o Azure, agora a Contoso precisa operacionalizar e proteger completamente a nova infraestrutura.

### <a name="security"></a>Segurança

- A Contoso precisa garantir que os novos bancos de dados estejam seguros. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview).
- O aplicativo precisa ser atualizado para usar SSL com certificados. A instância de contêiner deve ser reimplantada para responder em 443.
- A Contoso deve considerar o uso do Key Vault para proteger os segredos dos aplicativos do Service Fabric. [Saiba mais](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-secret-management).

### <a name="backups-and-disaster-recovery"></a>Backup e recuperação de desastre

- A Contoso precisa examinar os requisitos de backup do Banco de Dados SQL do Azure. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).
- A Contoso deve considerar implementar grupos de failover do SQL para fornecer failover regional ao banco de dados. [Saiba mais](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview).
- A Contoso pode usar a replicação geográfica para o SKU Premium do ACR. [Saiba mais](https://docs.microsoft.com/azure/container-registry/container-registry-geo-replication).
- O Cosmos DB faz backup automaticamente. A Contoso pode [saber mais](https://docs.microsoft.com/azure/cosmos-db/online-backup-and-restore) sobre esse processo.

### <a name="licensing-and-cost-optimization"></a>Licenciamento e otimização de custo

- Depois que todos os recursos estiverem implantados, a Contoso deverá atribuir marcações ao Azure com base no seu [planejamento de infraestrutura](./contoso-migration-infrastructure.md#set-up-tagging).
- Todo o licenciamento se baseia no custo dos serviços de PaaS que a Contoso está consumindo. Isso será deduzido do EA.
- A Contoso habilitará o Gerenciamento de Custos do Azure licenciado pela Cloudyn, uma subsidiária da Microsoft. É uma solução de gerenciamento de custo de várias nuvens que ajuda você a usar e gerenciar o Azure e outros recursos de nuvem. [Saiba mais](https://docs.microsoft.com/azure/cost-management/overview) sobre o Gerenciamento de Custos do Azure.

## <a name="conclusion"></a>Conclusão

Neste artigo, a Contoso recria o aplicativo SmartHotel360 no Azure. A VM de front-end do aplicativo local é recriada nos aplicativos Web do Serviço de Aplicativo do Azure. O back-end do aplicativo é criado usando microsserviços implantados em contêineres gerenciados pelo AKS (Serviço de Kubernetes do Azure). A Contoso melhorou a funcionalidade do aplicativo com um aplicativo de foto de animal de estimação.

## <a name="suggested-skills"></a>Habilidades sugeridas

O Microsoft Learn é uma nova abordagem para o aprendizado. A preparação para as novas habilidades e responsabilidades que acompanham a adoção de nuvem não é fácil. O Microsoft Learn oferece uma abordagem mais recompensadora para o aprendizado prático que ajuda você a atingir suas metas mais rapidamente. Ganhe pontos e níveis e conquiste mais!

Aqui estão alguns exemplos de caminhos de aprendizado personalizados em Microsoft Learn que se alinham com o aplicativo contoso SmartHotel360 no Azure.

[Implantar um site no Azure com o serviço Azure app](https://docs.microsoft.com/learn/paths/deploy-a-website-with-azure-app-service/): aplicativos Web no Azure permitem que você publique e gerencie seu site facilmente sem precisar trabalhar com os servidores subjacentes, armazenamento ou ativos de rede. Em vez disso, você pode se concentrar nos recursos de seu site e contar com a robusta plataforma do Azure para fornecer acesso seguro ao seu site.

[Processar e classificar imagens com os serviços de visão cognitiva do Azure: os](https://docs.microsoft.com/learn/paths/classify-images-with-vision-services/)serviços cognitivas do Azure oferecem funcionalidade predefinida para habilitar a funcionalidade de pesquisa Visual computacional em seus aplicativos. Saiba como usar os serviços de visão cognitiva para detectar faces, marcar e classificar imagens e identificar objetos.
