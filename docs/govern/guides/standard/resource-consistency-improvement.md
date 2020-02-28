---
title: 'Governança empresarial padrão: melhorar a consistência de recursos'
description: Use a estrutura de adoção de nuvem para o Azure para saber mais sobre como melhorar a linha de base de governança e adicionar controles de recuperação, dimensionamento e monitoramento para corrigir riscos.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 57358a9933c6f18d72678c3c4ba82bef90e713a0
ms.sourcegitcommit: 10637acba8c857a6f5aa8c4a80c0649903f60402
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78170810"
---
# <a name="standard-enterprise-governance-guide-improving-resource-consistency"></a>Guia de governança empresarial padrão: melhorando a consistência de recursos

Este artigo avança na narração adicionando controles de consistência de recursos para dar suporte a aplicativos de missão crítica.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

Novas experiências do cliente, novas ferramentas de previsão e infraestrutura migrada continuam a evoluir. A empresa está pronta para começar a usar esses ativos em uma capacidade de produção.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

Na fase anterior desse narrativa, as equipes de BI e o desenvolvimento de aplicativos estavam quase prontos para integrar clientes e dados financeiros em cargas de trabalho de produção. A equipe de TI estava no processo de desativação do datacenter de recuperação de desastre.

Desde então, ocorreram algumas mudanças que afetarão a governança:

- A IT desativou 100% do datacenter de recuperação de desastres, à frente do cronograma. No processo, um conjunto de ativos no datacenter de produção foi identificado como candidatos à migração na nuvem.
- As equipes de desenvolvimento de aplicativo estão agora prontas para o tráfego de produção.
- A equipe de BI está pronta para alimentar previsões e informações de volta para os sistemas operacionais no data center de produção.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

Antes de usar as implantações do Azure em processos de negócios de produção, as operações de nuvem devem amadurecer. Em conjunto, alterações de governança adicionais são necessárias para garantir que os ativos possam ser operados corretamente.

As alterações ao estado atual e futuro expõem novos riscos que exigem novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Interrupção dos negócios:** Há um risco inerente de qualquer nova plataforma causando interrupções em processos de negócios de missão crítica. A equipe de operações de TI e as equipes que executam em várias adoções de nuvem são relativamente inexperientes com operações na nuvem. Isso aumenta o risco de interrupção e deve ser corrigido e regido.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

1. Uma invasão externa ou ataques de negação de serviço podem causar uma interrupção dos negócios.
2. Os ativos de missão crítica podem não ser descobertos corretamente e, portanto, podem não ser operados corretamente.
3. Ativos não descobertos ou rotulados incorretamente podem não ser suportados pelos processos de gerenciamento operacionais existentes.
4. A configuração de ativos implantados pode não atender às expectativas de desempenho.
5. Registro em log pode não ser corretamente registrado e centralizado para permitir a correção dos problemas de desempenho.
6. As políticas de recuperação podem falhar ou levar mais tempo do que o esperado.
7. Os processos de implantação podem resultar em falhas de segurança, o que pode levar a perdas de dados ou interrupções.
8. Desvio de configuração ou patches ausentes pode resultar em falhas de segurança não intencionais, o que pode levar a vazamentos de dados ou interrupções.
9. Configuração não pode impor os requisitos de SLAs ou requisitos de recuperação confirmados.
10. Os sistemas operacionais ou aplicativos implantados podem falhar ao atender aos requisitos de proteção.
11. Com numerosas equipes trabalhando na nuvem, há um risco de inconsistência.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece longa, mas adotar essas políticas talvez seja mais fácil do que parece.

1. Todos os ativos implantados devem ser categorizados por nível de importância e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.
2. Sub-redes que contêm aplicativos de missão crítica devem ser protegidas por uma solução de firewall capaz de detecção de invasões e responder a ataques.
3. As ferramentas de governança devem realizar a auditoria e impor requisitos de configuração de rede definidos pela equipe de gerenciamento de segurança.
4. Ferramentas de governança devem validar que todos os ativos relacionados a aplicativos de missão crítica ou dados protegidos são incluídos no monitoramento para otimização e esgotamento de recursos.
5. As ferramentas de governança devem validar se o nível apropriado de dados de registro em log está sendo coletado para todos os aplicativos críticos ou dados protegidos.
6. O processo de governança deve validar o backup, recuperação e o cumprimento de SLA são implementados corretamente para aplicativos de missão crítica e dados protegidos.
7. As ferramentas de governança devem limitar as implantações da VM somente a imagens aprovadas.
8. Ferramentas de governança devem impor que as atualizações automáticas estejam impedidas em todos os ativos implantados que dão suporte a aplicativos de missão crítica. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Ativos que não são atualizados automaticamente devem ser incluídos nos processos pertencentes às Operações de TI.
9. Ferramentas de governança devem validar a marcação relacionadas à classificação de custo, nível de importância, SLA, aplicativos e dados. Todos os valores devem ser alinhados a valores predefinidos gerenciados pela equipe de governança.
10. Os processos de governança devem incluir auditorias no momento da implantação e em ciclos regulares para garantir a consistência em todos os ativos.
11. Tendências e explorações que possam afetar as implantações de nuvem devem ser examinadas regularmente pela equipe de segurança para que sejam fornecidas atualizações às ferramentas de gerenciamento de segurança usadas na nuvem.
12. Antes do lançamento para a produção, todos os aplicativos de missão crítica e dados protegidos devem ser adicionados à solução de monitoramento operacional designada. Ativos que não podem ser descobertos pelas ferramentas de operações de TI escolhidas, não podem ser liberados para uso em produção. Quaisquer alterações necessárias para tornar os ativos detectáveis devem ser feitas aos processos de implantação relevantes para garantir que os ativos sejam detectáveis em implantações futuras.
13. Quando descoberto, as equipes de gerenciamento operacional vão dimensionar ativos para garantir que os ativos atendam aos requisitos de desempenho.
14. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
15. Os scripts de implantação devem ser mantidos em um repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
16. Processos de revisão de governança devem validar que os ativos implantados estão configurados corretamente alinhados aos requisitos de SLA e recuperação.

## <a name="incremental-improvement-of-governance-practices"></a>Melhoria incremental de práticas de governança

Esta seção do artigo alterará o design MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

1. A equipe de operações de nuvem definirá as ferramentas de monitoramento operacional e as ferramentas de correção automatizadas. A equipe de governança de nuvem dará suporte a esses processos de descoberta. Nesse caso de uso, a equipe de operações de nuvem escolheu Azure Monitor como a principal ferramenta para monitorar aplicativos de missão crítica.
2. Crie um repositório no Azure DevOps para armazenar e controlar a versão de todos os modelos do Gerenciador de Recursos relevantes e configurações com script.
3. Implementação do cofre dos serviços de recuperação do Azure:
    1. Defina e implante o cofre dos serviços de recuperação do Azure para processos de backup e recuperação.
    2. Criar um modelo do Gerenciador de Recursos para criação de um cofre em cada assinatura.
4. Atualizar o Azure Policy para todas as assinaturas:
    1. Realize auditoria e imponha o nível de importância e classificação de dados em todas as assinaturas para identificar todas as assinaturas com ativos de missão crítica.
    2. Realize uma auditoria e imponha o uso exclusivo de imagens aprovadas.
5. Implementação do Azure Monitor:
    1. Depois que uma carga de trabalho de missão crítica for identificada, crie um espaço Azure Monitor.
    2. Durante o teste de implantação, a equipe de operações de nuvem implanta os agentes e a descoberta de testes necessários.
6. Atualize o Azure Policy para todas as assinaturas que contêm aplicativos de missão crítica.
    1. Realize uma auditoria e imponha a aplicação de um NSG para todas as NICs e sub-redes. Rede e de Segurança de TI definirão o NSG.
    2. Realize uma auditoria e imponha o uso de sub-redes e VNets para cada interface de rede.
    3. Realize uma auditoria e imponha a limitação das tabelas de roteamento definidas pelo usuário.
    4. Audite e imponha a implantação de agentes do Azure Monitor para todas as máquinas virtuais.
    5. Auditar e impor que os cofres dos serviços de recuperação do Azure existam na assinatura.
7. Configuração do firewall:
    1. Identifique uma configuração do Firewall do Azure que atenda aos requisitos de segurança. Como alternativa, identifique um dispositivo de terceiros que seja compatível com o Azure.
    1. Crie um modelo do Resource Manager para implantar o firewall com as configurações necessárias.
8. Blueprint do Azure:
    1. Crie um novo blueprint do Azure chamado `protected-data`.
    2. Adicione o firewall e os modelos Azure Vault ao blueprint.
    3. Adicione as novas políticas para assinaturas de dados protegidos.
    4. Publique o Blueprint em qualquer grupo de gerenciamento que hospedará aplicativos de missão crítica.
    5. Aplique o novo blueprint a cada assinatura afetada, bem como os blueprints existentes.

## <a name="conclusion"></a>Conclusão

Esses processos adicionais e as alterações no MVP de governança ajudam a corrigir muitos dos riscos associados à governança de recursos. Juntos, aumentam a recuperação, dimensionamento e controles de monitoramento que capacitam as operações de recuperação de nuvem.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para a empresa fictícia neste guia, o próximo gatilho é quando a escala da implantação excede 100 ativos para a nuvem ou gastos mensais excedem $1000 por mês. Neste ponto, a equipe de governança de nuvem adiciona controles de gerenciamento de custos.

> [!div class="nextstepaction"]
> [Melhorando o gerenciamento de custos](./cost-management-improvement.md)
