---
title: Dimensionar uma migração para o Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Saiba como a contoso lida com uma migração dimensionada para o Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/08/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 1e8b42170a4db025087acdabba14544cea9c8194
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548111"
---
# <a name="scale-a-migration-to-azure"></a>Dimensionar uma migração para o Azure

Este artigo demonstra como a empresa fictícia Contoso executa uma migração em escala para o Azure. Eles consideram como planejar e executar uma migração de mais de 3000 cargas de trabalho, 8000 bancos de dados e mais de 10.000 VMs.

## <a name="business-drivers"></a>Drivers de negócios

A equipe de liderança de ti trabalhou junto com parceiros de negócios para entender o que eles querem alcançar com essa migração:

- **Resolva o crescimento dos negócios.** A Contoso está crescendo, causando pressão na infraestrutura e nos sistemas locais.
- **Aumente a eficiência.** A contoso precisa remover procedimentos desnecessários e simplificar processos para desenvolvedores e usuários. A empresa precisa que ela seja rápida e não gaste tempo nem dinheiro, o que proporciona mais rapidez nos requisitos do cliente.
- **Aumente a agilidade.** A contoso IT precisa ser mais responsiva às necessidades dos negócios. Ele deve ser capaz de reagir mais rápido do que as alterações no Marketplace, para habilitar o sucesso em uma economia global. Ele não deve o caminho, ou se torna um bloqueador de negócios.
- **Escala.** À medida que os negócios crescem com êxito, a equipe de ti da Contoso deve fornecer sistemas capazes de crescer no mesmo ritmo.
- **Melhorar os modelos de custo.** A contoso deseja reduzir os requisitos de capital no orçamento de ti. A contoso deseja usar recursos de nuvem para dimensionar e reduzir a necessidade de hardware caro.
- **Reduzir os custos de licenciamento.** A contoso deseja minimizar os custos de nuvem.

## <a name="migration-goals"></a>Metas de migração

A equipe de nuvem da Contoso detectou metas para essa migração. Essas metas foram usadas para determinar o melhor método de migração.

**Requisitos** | **Detalhes**
--- | ---
**Mover para o Azure rapidamente** | A contoso deseja começar a mover aplicativos e VMs para o Azure o mais rápido possível.
**Compilar um inventário completo** | A contoso quer um inventário completo de todos os aplicativos, bancos de dados e VMs na organização.
**Avaliar e classificar aplicativos** | A contoso deseja aproveitar totalmente a nuvem. Como um padrão, a contoso pressupõe que todos os serviços serão executados como PaaS. A IaaS será usada em que a PaaS não é apropriada.
**Treinar e mover para o DevOps** | A contoso deseja mudar para um modelo DevOps. A contoso fornecerá treinamento do Azure e do DevOps e reorganizará as equipes, conforme necessário.

Depois de fixar as metas e os requisitos, a contoso revisa a superfície de ti e identifica o processo de migração.

## <a name="current-deployment"></a>Implantação atual

Depois de planejar e configurar uma [infraestrutura do Azure](./contoso-migration-infrastructure.md) e experimentar combinações de migração de POC (prova de conceito) diferentes, conforme detalhado na tabela acima, a Contoso está pronta para embarcar em uma migração completa para o Azure em escala. Veja o que a contoso deseja migrar.

<!--markdownlint-disable MD033 -->

**Item** | **Volume** | **Detalhes**
--- | --- | ---
**Cargas** | Mais de 3.000 aplicativos | Aplicativos executados em VMs.<br/><br/>  Os aplicativos são uma lâmpada do Windows, baseada em SQL e OSS.
**Bancos de dados** | Cerca de 8.500 | Os bancos de dados incluem SQL Server, MySQL, PostgreSQL.
**VMs** | Mais de 35.000 | As VMs são executadas em hosts VMware e gerenciadas por servidores vCenter.

<!--markdownlint-enable MD033 -->

## <a name="migration-process"></a>Processo de migração

Agora que a contoso se deparava com os drivers comerciais e as metas de migração, ela determina uma abordagem de quatro pontas para o processo de migração:

- **Fase 1: avaliar.** Descobrir os ativos atuais e descobrir se eles são adequados para a migração para o Azure.
- **Fase 2: migrar.** Mova os ativos para o Azure. A forma como eles movem aplicativos e objetos para o Azure dependerá do aplicativo e do que eles desejam obter.
- **Fase 3: otimizar.** Depois de mover os recursos para o Azure, a contoso precisa melhorar e simplificar a ti para obter o máximo de desempenho e eficiência.
- **Fase 4: proteger e gerenciar.** Com tudo em vigor, a contoso agora usa recursos e serviços de segurança e gerenciamento do Azure para controlar, proteger e monitorar seus aplicativos de nuvem no Azure.

Essas fases não são seriais em toda a organização. Cada parte do projeto de migração da Contoso estará em um estágio diferente do processo de avaliação e migração. A otimização, a segurança e o gerenciamento serão contínuos ao longo do tempo.

## <a name="phase-1-assess"></a>Fase 1: avaliar

A contoso começa o processo descobrindo e avaliando aplicativos, dados e infraestrutura locais. Veja o que a contoso fará:

- A contoso precisa descobrir aplicativos, mapear dependências entre aplicativos e decidir sobre a ordem de migração e a prioridade.
- Como a contoso avalia, ela criará um inventário abrangente de aplicativos e recursos. Junto com o novo inventário, a Contoso usará e atualizará o banco de dados de gerenciamento de configuração (CMDB) e o catálogo de serviços existentes.
  - O CMDB contém configurações técnicas para aplicativos da contoso.
  - O catálogo de serviços documenta os detalhes operacionais dos aplicativos, incluindo parceiros comerciais associados e SLAs (contratos de nível de serviço).

### <a name="discover-apps"></a>Descobrir aplicativos

A contoso executa milhares de aplicativos em uma variedade de servidores. Além do CMDB e do catálogo de serviços, a contoso precisa de ferramentas de descoberta e avaliação.

- As ferramentas devem fornecer um mecanismo que possa alimentar dados de avaliação no processo de migração.
- As ferramentas de avaliação devem fornecer dados que ajudem a criar um inventário inteligente dos recursos físicos e virtuais da contoso. Os dados devem incluir informações de perfil e métricas de desempenho.
- Quando a descoberta for concluída, a contoso deverá ter um inventário completo dos ativos e os metadados associados a eles. Esse inventário será usado para definir o plano de migração.

### <a name="identify-classifications"></a>Identificar classificações

A contoso identifica algumas categorias comuns para classificar ativos no inventário. Essas classificações são essenciais para a tomada de decisões da Contoso para a migração. A lista de classificação ajuda a estabelecer prioridades de migração e a identificar problemas complexos.

**Categorias** | **Valor atribuído** | **Detalhes**
--- | --- | ---
Grupo de negócios | Lista de nomes de grupos de negócios | Qual grupo é responsável pelo item de inventário?
Candidato à POC | S/N | O aplicativo pode ser usado como uma POC ou um pioneiro para a migração na nuvem?
Dívida técnica | Nenhum/alguns/severos | O item de inventário está em execução ou usando um produto, plataforma ou sistema operacional fora de suporte?
Implicações de firewall | S/N | O aplicativo se comunica com a Internet/tráfego externo?  Ele se integra a um firewall?
Problemas de segurança | S/N | Há problemas de segurança conhecidos com o aplicativo?  O aplicativo usa dados descriptografados ou plataformas desatualizadas?

### <a name="discover-app-dependencies"></a>Descobrir dependências de aplicativo

Como parte do processo de avaliação, a contoso precisa identificar onde os aplicativos estão em execução e descobrir as dependências e conexões entre os servidores de aplicativos. A contoso mapeia o ambiente em etapas.

1. Como primeira etapa, a contoso descobre como os servidores e computadores são mapeados para aplicativos individuais, locais de rede e grupos.
2. Com essas informações, a Contoso pode identificar claramente os aplicativos que têm poucas dependências e, portanto, são adequadas para uma migração rápida.
3. A Contoso pode usar o mapeamento para ajudá-los a identificar dependências e comunicações mais complexas entre servidores de aplicativos. Em seguida, a Contoso pode agrupar esses servidores logicamente para representar aplicativos e planejar uma estratégia de migração com base nesses grupos.

Com o mapeamento concluído, a Contoso pode garantir que todos os componentes do aplicativo sejam identificados e contabilizados durante a criação do plano de migração.

![Mapeamento de dependência](./media/contoso-migration-scale/dependency-map.png)

### <a name="evaluate-apps"></a>Avaliar aplicativos

Como a última etapa do processo de descoberta e avaliação, a Contoso pode avaliar os resultados da avaliação e do mapeamento para descobrir como migrar cada aplicativo no catálogo de serviços.

Para capturar esse processo de avaliação, eles adicionam algumas classificações adicionais ao inventário.

**Categorias** | **Valor atribuído** | **Detalhes**
--- | --- | ---
Grupo de negócios | Lista de nomes de grupos de negócios | Qual grupo é responsável pelo item de inventário?
Candidato à POC | S/N | O aplicativo pode ser usado como uma POC ou um pioneiro para a migração na nuvem?
Dívida técnica | Nenhum/alguns/severos | O item de inventário está em execução ou usando um produto, plataforma ou sistema operacional fora de suporte?
Implicações de firewall | S/N | O aplicativo se comunica com a Internet/tráfego externo?  Ele se integra a um firewall?
Problemas de segurança | S/N | Há problemas de segurança conhecidos com o aplicativo?  O aplicativo usa dados descriptografados ou plataformas desatualizadas?
Estratégia de migração | Rehospedar/refatorar/recriar/redesenvolver/recompilar | Que tipo de migração é necessária para o aplicativo? Como o aplicativo será implantado no Azure? [Saiba mais](./contoso-migration-overview.md#migration-patterns).
Complexidade técnica | 1-5 | Quão complexa é a migração? Esse valor deve ser definido pelo contoso DevOps e por parceiros relevantes.
Importância dos negócios | 1-5 | Quão importante é o aplicativo para a empresa? Por exemplo, um pequeno aplicativo de grupo de trabalho pode receber uma pontuação de um, enquanto um aplicativo crítico usado em toda a organização pode receber uma pontuação de cinco. Essa Pontuação afetará o nível de prioridade de migração.
Prioridade de migração | 1/2/3 | Qual é a prioridade de migração para o aplicativo?
Risco de migração | 1-5 | Qual é o nível de risco para migrar o aplicativo? Esse valor deve ser acordado por contoso DevOps e parceiros relevantes.

### <a name="figure-out-costs"></a>Descobrir custos

Para descobrir os custos e a economia potencial da migração do Azure, a Contoso pode usar a [calculadora de custo total de propriedade (TCO)](https://azure.microsoft.com/pricing/tco/calculator) para calcular e comparar o TCO do Azure com uma implantação local comparável.

### <a name="identify-assessment-tools"></a>Identificar ferramentas de avaliação

A Contoso decide qual ferramenta usar para descoberta, avaliação e criação do inventário. A contoso identifica uma combinação de ferramentas e serviços do Azure, ferramentas e scripts de aplicativos nativos e ferramentas de parceiros. Em particular, a Contoso está interessada em como as migrações para Azure podem ser usadas para avaliar em grande escala.

#### <a name="azure-migrate"></a>Migrações para Azure

O serviço de migrações para Azure ajuda a descobrir e avaliar VMs VMware locais, em preparação para a migração para o Azure. Veja o que as migrações para Azure:

1. Descobrir: descobrir VMs VMware locais.
    - As migrações para Azure dão suporte à descoberta de vários servidores vCenter (em série) e podem executar descobertas em projetos separados de migrações para Azure.
    - As migrações para Azure executam a descoberta por meio de uma VM VMware que executa o coletor de migrações. O mesmo coletor pode descobrir VMs em servidores vCenter diferentes e enviar dados para projetos diferentes.
2. Avalie a preparação: avalie se os computadores locais são adequados para execução no Azure. A avaliação inclui:
    - Recomendações de tamanho: Obtenha recomendações de tamanho para VMs do Azure, com base no histórico de desempenho de VMs locais.
    - Custos mensais estimados: Obtenha custos estimados para executar computadores locais no Azure.
3. Identificar dependências: visualize dependências de computadores locais, para criar grupos de computadores ideais para avaliação e migração.

![Migrações para Azure](./media/contoso-migration-scale/azure-migrate.png)

##### <a name="migrate-at-scale"></a>Migrar em escala

A contoso precisa usar as migrações para Azure corretamente Considerando a escala dessa migração.

- A contoso fará uma avaliação de aplicativo por aplicativo com as migrações para Azure. Isso garante que as migrações para Azure retornem dados oportunos para o portal do Azure.
- Administradores da Contoso Leia sobre [a implantação de migrações do Azure em escala](https://docs.microsoft.com/azure/migrate/how-to-scale-assessment)
- A contoso anota os limites de migrações para Azure resumidos na tabela a seguir.

**Ação** | **Limite**
--- | ---
Criar projeto de migrações para Azure | 10.000 VMs
Descoberta | 10.000 VMs
Avaliação | 10.000 VMs

A Contoso usará as migrações para Azure da seguinte maneira:

- No vCenter contoso, organizará as VMs em pastas. Isso tornará mais fácil para eles se concentrarem enquanto executam uma avaliação em relação às VMs em uma pasta específica.
- As migrações para Azure usam o Azure Mapa do Serviço para avaliar as dependências entre as máquinas. Isso requer que os agentes sejam instalados nas VMs a serem avaliadas.
  - A Contoso usará scripts automatizados para instalar os agentes Windows ou Linux necessários.
  - Por script, a Contoso pode enviar por push a instalação para VMs em uma pasta do vCenter.

#### <a name="database-tools"></a>Ferramentas de banco de dados

Além das migrações para Azure, a contoso se concentrará no uso de ferramentas especificamente para a avaliação do banco de dados. Ferramentas como o [Assistente de migração de dados](/sql/dma/dma-overview?view=sql-server-2017) ajudarão a avaliar SQL Server bancos de dados para migração.

O Assistente de Migração de Dados (DMA) pode ajudar a Contoso a descobrir se os bancos de dados locais são compatíveis com uma variedade de soluções de banco de dados do Azure, como o banco de dados SQL do Azure, SQL Server em execução em uma VM IaaS do Azure e Instância Gerenciada SQL do Azure.

Além do DMS, a contoso tem alguns outros scripts que eles usam para descobrir e documentar os bancos de dados do SQL Server. Eles estão localizados no repositório GitHub.

#### <a name="partner-assessment-tools"></a>Ferramentas de avaliação do parceiro

Há várias outras ferramentas de parceiros que podem ajudar a Contoso a avaliar o ambiente local para a migração para o Azure. [Saiba mais](https://azure.microsoft.com/migration/partners) sobre os parceiros de migração do Azure.

## <a name="phase-2-migrate"></a>Fase 2: migrar

Com sua avaliação concluída, a contoso precisa identificar ferramentas para mover seus aplicativos, dados e infraestrutura para o Azure.

### <a name="migration-strategies"></a>Estratégias de migração

Há quatro estratégias de migração amplas que a Contoso pode considerar.

<!--markdownlint-disable MD033 -->

**Estratégia** | **Detalhes** | **Uso**
--- | --- | ---
**Novo host** | Geralmente conhecida como migração de "deslocamento e mudança", essa é uma opção sem código para migrar aplicativos existentes para o Azure rapidamente.<br/><br/> Um aplicativo é migrado no estado em que se encontra, com os benefícios da nuvem, sem os riscos ou os custos associados às alterações de código. | A Contoso pode hospedar novamente aplicativos menos estratégicos, não exigindo alterações de código.
**Refatorar** | Também conhecido como "reempacotamento", essa estratégia requer código mínimo de aplicativo ou alterações de configuração precisam conectar o aplicativo ao PaaS do Azure e aproveitar melhor os recursos de nuvem. | A Contoso pode refatorar aplicativos estratégicos para manter a mesma funcionalidade básica, mas movê-los para execução em uma plataforma do Azure, como Azure App Service.<br/><br/> Isso requer alterações mínimas de código.<br/><br/> Por outro lado, a contoso precisará manter uma plataforma de VM, pois ela não será gerenciada pela Microsoft.
**Recriação** | Essa estratégia modifica ou estende uma base de código de aplicativo para otimizar a arquitetura do aplicativo para recursos de nuvem e escala.<br/><br/> Ele Modernizr um aplicativo em uma arquitetura resiliente, altamente escalonável e implantável de forma independente.<br/><br/> Os serviços do Azure podem acelerar o processo, dimensionar aplicativos com confiança e gerenciar aplicativos com facilidade.
**Constitui** | Essa estratégia recria um aplicativo do zero usando tecnologias nativas de nuvem.<br/><br/> O PaaS (plataforma como serviço) do Azure fornece um ambiente completo de desenvolvimento e implantação na nuvem. Ele elimina algumas despesas e complexidade de licenças de software e elimina a necessidade de uma infraestrutura de aplicativo subjacente, middleware e outros recursos. | A Contoso pode reescrever aplicativos críticos desde o início, para aproveitar as tecnologias de nuvem, como o computador sem servidor, ou os microserviços.<br/><br/> A contoso gerenciará o aplicativo e os serviços que ele desenvolve, e o Azure gerencia todo o resto.

<!--markdownlint-enable MD033 -->

Os dados também devem ser considerados, especialmente com o volume de bancos que a contoso tem. A abordagem padrão da Contoso é usar serviços de PaaS, como o banco de dados SQL do Azure, para aproveitar ao máximo os recursos de nuvem. Ao migrar para um serviço de PaaS para bancos de dados, a contoso só precisará manter o dado, deixando a plataforma subjacente à Microsoft.

### <a name="evaluate-migration-tools"></a>Avaliar ferramentas de migração

A Contoso está usando principalmente alguns serviços e ferramentas do Azure para a migração:

- [Azure site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview): Orquestra a recuperação de desastre e migra VMs locais para o Azure.
- [Serviço de migração de banco de dados do Azure](https://docs.microsoft.com/azure/dms/dms-overview): migra bancos de dados locais, como SQL Server, MySQL e Oracle para o Azure.

#### <a name="azure-site-recovery"></a>Recuperação de Site do Azure

Azure Site Recovery é o serviço principal do Azure para orquestrar a recuperação de desastres e a migração de dentro do Azure e de sites locais para o Azure.

1. O Site Recovery permite, orquestra a replicação de seus sites locais para o Azure.
2. Quando a replicação estiver configurada e em execução, as máquinas locais poderão fazer failover no Azure, concluindo a migração.

A contoso já [concluiu uma POC](./contoso-migration-rehost-vm.md) para ver como site Recovery pode ajudá-los a migrar para a nuvem.

##### <a name="using-site-recovery-at-scale"></a>Usando Site Recovery em escala

A contoso planeja executar várias migrações de "comparação e deslocamento". Para garantir que isso funcione, Site Recovery irá replicar lotes de cerca de 100 VMs por vez. Para descobrir como isso funcionará, a contoso precisa executar o planejamento de capacidade para a migração de Site Recovery proposta.

- A contoso precisa coletar informações sobre seus volumes de tráfego. Especificamente:
  - A contoso precisa determinar a taxa de alteração para as VMs que deseja replicar.
  - A contoso também precisa levar em conta a conectividade de rede do site local para o Azure.
- Em resposta aos requisitos de capacidade e volume, a contoso precisará alocar largura de banda suficiente com base na taxa diária de alteração de dados para as VMs necessárias, para atender a seu RPO (objetivo de ponto de recuperação).
- Por fim, eles precisam descobrir quantos servidores são necessários para executar os componentes de Site Recovery que são necessários para a implantação.

###### <a name="gather-on-premises-information"></a>Reunir informações locais

A Contoso pode usar a ferramenta de [planejador de implantações de site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-deployment-planner) para concluir estas etapas:

- A Contoso pode usar a ferramenta para criar o perfil de VMs remotamente sem afetar o ambiente de produção. Isso ajuda a identificar os requisitos de largura de banda e armazenamento para replicação e failover.
- A Contoso pode executar a ferramenta sem instalar Site Recovery componentes locais.
- A ferramenta reúne informações sobre VMs compatíveis e incompatíveis, discos por VM e variação de dados por disco. Ele também identifica os requisitos de largura de banda da rede e a infraestrutura do Azure necessária para replicação e failover bem-sucedidos.
- A contoso precisa garantir que, em seguida, executar a ferramenta de planejador em um computador Windows Server que corresponda aos requisitos mínimos para o servidor de configuração Site Recovery. O servidor de configuração é uma máquina Site Recovery necessária para replicar VMs VMware locais.

###### <a name="identify-site-recovery-requirements"></a>Identificar requisitos de Site Recovery

Além das VMs que estão sendo replicadas, o Site Recovery requer vários componentes para a migração do VMware.

<!--markdownlint-disable MD033 -->

**Componente** | **Detalhes**
--- | ---
**Servidor de configuração** | Geralmente, uma VM VMware é configurada usando um modelo OVF.<br/><br/> O componente do servidor de configuração coordena as comunicações entre o local e o Azure e gerencia a replicação de dados.
**Servidor de processo** | Instalado por padrão no servidor de configuração.<br/><br/> O componente do servidor de processo recebe dados de replicação; otimiza-o com caching, compactação e criptografia; e o envia para o armazenamento do Azure.<br/><br/> O servidor de processo também instala Azure Site Recovery serviço de mobilidade nas VMs que você deseja replicar e executa a descoberta automática de computadores locais.<br/><br/> As implantações em escala precisam de servidores de processo adicionais e autônomos para lidar com grandes volumes de tráfego de replicação.
**Serviço de mobilidade** | O agente do serviço de mobilidade é instalado em cada VM do VMware que será migrada com Site Recovery.

<!--markdownlint-enable MD033 -->

A contoso precisa descobrir como implantar esses componentes, com base nas considerações sobre capacidade.

<!--markdownlint-disable MD033 -->

**Componente** | **Requisitos de capacidade**
--- | ---
**Taxa de alteração diária máxima** | Um único servidor de processo pode lidar com uma taxa de alteração diária de até 2 TB. Como uma VM só pode usar um servidor de processo, a taxa máxima diária de alteração de dados com suporte para uma VM replicada é 2 TB.
**Taxa de transferência máxima** | Uma conta de armazenamento padrão do Azure pode lidar com um máximo de 20.000 solicitações por segundo, e as operações de entrada/saída por segundo (IOPS) em uma VM de replicação devem estar dentro desse limite. Por exemplo, se uma VM tiver 5 discos e cada disco gerar 120 IOPS (8 k de tamanho) na VM, ele estará dentro do limite de 500 de IOPS por disco do Azure.<br/><br/> Observe que o número de contas de armazenamento necessárias é igual ao IOPS total do computador de origem, dividido por 20.000. Um computador replicado só pode pertencer a uma única conta de armazenamento no Azure.
**Servidor de configuração** | Com base na estimativa da Contoso de replicar 100 = 200 VMs juntas, e os [requisitos de dimensionamento do servidor de configuração](https://docs.microsoft.com/azure/site-recovery/site-recovery-plan-capacity-vmware#size-recommendations-for-the-configuration-server-and-inbuilt-process-server), a contoso Estimate precisa de um computador do servidor de configuração da seguinte maneira:<br/><br/> CPU: 16 vCPUs (2 soquetes * 8 núcleos @ 2,5 GHz)<br/><br/> Memória: 32 GB<br/><br/> Disco de cache: 1 TB<br/><br/> Taxa de alteração de dados: 1 TB a 2 TB.<br/><br/> Além dos requisitos de dimensionamento, a contoso precisará garantir que o servidor de configuração esteja localizado de forma ideal, na mesma rede e no mesmo segmento de LAN que as VMs que serão migradas.
**Servidor de processo** | A contoso implantará um servidor de processo dedicado autônomo com a capacidade de replicar 100-200 VMs:<br/><br/> CPU: 16 vCPUs (2 soquetes * 8 núcleos @ 2,5 GHz)<br/><br/> Memória: 32 GB<br/><br/> Disco de cache: 1 TB<br/><br/> Taxa de alteração de dados: 1 TB a 2 TB.<br/><br/> O servidor de processo estará trabalhando duro e, como tal, deve estar localizado em um host ESXi que possa lidar com a e/s de disco, o tráfego de rede e a CPU necessários para a replicação. A contoso considerará um host dedicado para essa finalidade.
**Rede** | A contoso analisou a infraestrutura de VPN site a site atual e decidiu implementar o Azure ExpressRoute. A implementação é crítica porque reduzirá a latência e melhorará a largura de banda para a região principal do Azure leste dos EUA 2 da contoso.<br/><br/> **Monitoramento:** A contoso precisará monitorar cuidadosamente o fluxo de dados do servidor de processo. Se os dados sobrecarregam a largura de banda da rede, a contoso considerará [a limitação da largura de banda do servidor de processo](https://docs.microsoft.com/azure/site-recovery/site-recovery-plan-capacity-vmware#control-network-bandwidth).
**Armazenamento do Azure** | Para a migração, a Contoso deve identificar o tipo e o número corretos de contas de armazenamento do Azure de destino. Site Recovery replica os dados da VM para o armazenamento do Azure.<br/><br/> Site Recovery pode replicar para contas de armazenamento Standard ou Premium (SSD).<br/><br/> Para decidir sobre o armazenamento, a Contoso deve revisar [os limites de armazenamento](https://docs.microsoft.com/azure/virtual-machines/windows/disks-types)e considerar o crescimento esperado e aumentar o uso ao longo do tempo. Dada a velocidade e a prioridade das migrações, a Contoso decidiu usar o SSDs Premium<br/><br/>
A contoso tomou a decisão de usar discos gerenciados para todas as VMs implantadas no Azure. O IOPS necessário determinará se os discos serão HDD Standard, SSD Standard ou Premium (SSD).<br/><br/>

<!--markdownlint-enable MD033 -->

#### <a name="azure-database-migration-service"></a>Serviço de migração de banco de dados do Azure

O serviço de migração de banco de dados do Azure é um serviço totalmente gerenciado que permite migrações diretas de várias fontes de banco de dados para plataformas de data do Azure com tempo de inatividade mínimo

- O DMS integra a funcionalidade de ferramentas e serviços existentes. Ele usa o Assistente de Migração de Dados (DMA) para gerar relatórios de avaliação que apontam as recomendações sobre compatibilidade de banco de dados e quaisquer modificações necessárias.
- O DMS usa um processo de migração simples e autoguiado, com avaliação inteligente que ajuda a resolver problemas potenciais antes da migração.
- O DMS pode migrar em escala de várias fontes para o banco de dados do Azure de destino.
- O DMS fornece suporte de SQL Server 2005 a SQL Server 2017.

O DMS não é a única ferramenta de migração de banco de dados da Microsoft. Obtenha uma [comparação de ferramentas e serviços](https://blogs.msdn.microsoft.com/datamigration/2017/10/13/differentiating-microsofts-database-migration-tools-and-services).

##### <a name="using-dms-at-scale"></a>Usando DMS em escala

A Contoso usará o DMS ao migrar do SQL Server.

- Ao provisionar o DMS, a contoso precisa dimensioná-lo corretamente e defini-lo para otimizar o desempenho de migrações de dados. A contoso selecionará a opção "camada comercialmente crítica com 4 vCores", permitindo assim que o serviço Aproveite vários vCPUs para paralelização e transferência de dados mais rápida.

    ![Dimensionamento DMS](./media/contoso-migration-scale/dms.png)

- Outra tática de dimensionamento para a contoso é expandir temporariamente a instância de destino do banco de dados SQL ou MySQL do Azure para a SKU da camada Premium durante a migração de dados. Isso minimiza a limitação do banco de dados que pode afetar as atividades de transferência de dados ao usar SKUs de nível inferior.

##### <a name="using-other-tools"></a>Usando outras ferramentas

Além do DMS, a Contoso pode usar outras ferramentas e serviços para identificar informações da VM.

- Eles têm scripts para ajudar com as migrações manuais. Eles estão disponíveis no repositório GitHub.
- Várias [ferramentas de parceiros](https://azure.microsoft.com/migration/partners) também podem ser usadas para migração.

## <a name="phase-3-optimize"></a>Fase 3: otimizar

Depois que a contoso move os recursos para o Azure, eles precisam simplificar a ti para melhorar o desempenho e maximizar o ROI com ferramentas de gerenciamento de custos. Considerando que o Azure é um serviço de pagamento por uso, é essencial para a contoso entender como os sistemas estão sendo executados e garantir que eles sejam dimensionados corretamente.

### <a name="azure-cost-management"></a>Gerenciamento de Custos do Azure

Para aproveitar ao máximo seu investimento em nuvem, a contoso aproveitará a ferramenta gratuita de gerenciamento de custos do Azure.

- Essa solução licenciada criada por Cloudyn, uma subsidiária da Microsoft, permite que a contoso gerencie gastos de nuvem com transparência e precisão. Ele fornece ferramentas para monitorar, alocar e aparar os custos de nuvem.
- O gerenciamento de custos do Azure fornece relatórios de painel simples para ajudar com a alocação de custos, os retornos e os estorno.
- O gerenciamento de custos pode otimizar os gastos com a nuvem identificando recursos subutilizados que a Contoso pode gerenciar e ajustar.
- [Saiba mais](https://docs.microsoft.com/azure/cost-management/overview) sobre o gerenciamento de custos do Azure.

![Gerenciamento de custos](./media/contoso-migration-scale/cost-management.png)

### <a name="native-tools"></a>Ferramentas nativas

A contoso também usará scripts para localizar recursos não utilizados.

- Durante grandes migrações, muitas vezes há dados restantes, como VHDs (discos rígidos virtuais), que incorrem em um encargo, mas não fornecem valor para a empresa. Os scripts estão disponíveis no repositório GitHub.
- A contoso aproveitará o trabalho feito pelo departamento de ti da Microsoft e considerará a implementação do kit de ferramentas de otimização de recursos do Azure (toa).
- A Contoso pode implantar uma conta de automação do Azure com runbooks pré-configurados e agendas para sua assinatura e começar a economizar dinheiro. A otimização de recursos do Azure ocorre automaticamente em uma assinatura depois que uma agenda é habilitada ou criada, incluindo a otimização em novos recursos.
- Isso fornece recursos de automação descentralizados para reduzir os custos. Os recursos incluem:
  - Adiar as VMs do Azure com base em baixa CPU.
  - Agende as VMs do Azure para adiar e desadiar.
  - Agende as VMs do Azure para adiar ou desadiar em ordem crescente e decrescente usando as marcas do Azure.
  - Exclusão em massa de grupos de recursos sob demanda.
- Introdução ao kit de ferramentas do ARO neste [repositório GitHub](https://github.com/Azure/azure-quickstart-templates/tree/master/azure-resource-optimization-toolkit).

### <a name="partner-optimization-tools"></a>Ferramentas de otimização do parceiro

Ferramentas de parceiros, como [Hanu](https://hanu.com/insight) e [scalr]( https://www.scalr.com/cost-optimization) , podem ser usadas.

## <a name="phase-4-secure-and-manage"></a>Fase 4: proteger e gerenciar

Nesta fase, a contoso usa recursos de segurança e gerenciamento do Azure para controlar, proteger e monitorar aplicativos de nuvem no Azure. Esses recursos ajudam a executar um ambiente seguro e bem gerenciado durante o uso de produtos disponíveis no portal do Azure. A contoso começa a usar esses serviços durante a migração e, com o suporte híbrido do Azure, continua usando muitos deles para uma experiência consistente em toda a nuvem híbrida.

### <a name="security"></a>Segurança

A contoso contará com a central de segurança do Azure para gerenciamento de segurança unificada e proteção avançada contra ameaças em cargas de trabalho de nuvem híbrida.

- A central de segurança fornece visibilidade total e controle sobre a segurança de aplicativos de nuvem no Azure.
- A Contoso pode detectar e tomar medidas rapidamente em resposta a ameaças e reduzir a exposição da segurança, permitindo a proteção adaptativa contra ameaças.

[Saiba mais](https://azure.microsoft.com/services/security-center) sobre a central de segurança.

### <a name="monitoring"></a>Monitoramento

A contoso precisa de visibilidade da integridade e do desempenho dos aplicativos, da infraestrutura e dos dados migrados recentemente que estão executando o Azure. A Contoso usará as ferramentas internas de monitoramento de nuvem do Azure, como Azure Monitor, Log Analytics espaço de trabalho e Application Insights.

- Usando essas ferramentas, a Contoso pode coletar facilmente dados de fontes e obter ideias avançadas. Por exemplo, a Contoso pode medir a utilização de disco e memória de CPU para VMs, exibir aplicativos e dependências de rede em várias VMs e acompanhar o desempenho do aplicativo.
- A Contoso usará essas ferramentas de monitoramento de nuvem para realizar ações e integrá-las às soluções de serviço.
- [Saiba mais](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview) sobre o monitoramento do Azure.

### <a name="business-continuity-and-disaster-recovery"></a>Continuidade dos negócios e recuperação de desastres

A contoso precisará de uma estratégia de BCDR (continuidade de negócios e recuperação de desastre) para seus recursos do Azure.

- O Azure fornece [recursos internos de BCDR](https://docs.microsoft.com/azure/architecture/resiliency/disaster-recovery-azure-applications) para manter os dados seguros e aplicativos/serviços em funcionamento.
- Além dos recursos internos, a contoso deseja garantir que ele possa se recuperar de falhas, evitar interrupções de negócios dispendiosas, atender às metas de conformidade e proteger os dados contra ransomware e erros humanos. Para fazer isso:
  - A contoso implantará o backup do Azure como uma solução econômica para o backup de recursos do Azure. Como ele é interno, a Contoso pode configurar backups de nuvem em algumas etapas simples.
  - A contoso configurará a recuperação de desastres para VMs do Azure usando Azure Site Recovery para replicação, failover e failback entre as regiões do Azure que ele especifica. Isso garante que os aplicativos em execução nas VMs do Azure permanecerão disponíveis em uma região secundária da Contoso escolhendo se ocorrer uma interrupção na região primária. [Saiba mais](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart).

## <a name="conclusion"></a>Conclusão

Neste artigo, a contoso planejou uma migração do Azure em escala. Eles dividiram o processo de migração em quatro estágios. Da avaliação e da migração até a otimização, a segurança e o gerenciamento após a conclusão da migração. Na maioria das vezes, é importante planejar um projeto de migração como um processo completo, mas migrar sistemas dentro de uma organização dividindo os conjuntos de classificações e números que fazem sentido para os negócios. Ao avaliar dados e aplicar classificações, o projeto pode ser dividido em uma série de migrações menores, o que pode ser executado com segurança e rapidez. A soma dessas migrações menores se transforma rapidamente em uma grande migração bem-sucedida para o Azure.
