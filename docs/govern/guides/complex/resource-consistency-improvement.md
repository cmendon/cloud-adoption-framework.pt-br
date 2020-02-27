---
title: 'Governança empresarial complexa: melhorar a disciplina de consistência de recursos'
description: Use a estrutura de adoção de nuvem para o Azure para aprender sobre os controles de recuperação, dimensionamento e monitoramento para melhorar a linha de base de governança e corrigir riscos.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: d7148df4bb06a0dc4ca035b89f7077888fb7306c
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77708930"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-resource-consistency-discipline"></a>Guia de governança para empresas complexas: melhorar a disciplina de consistência de recursos

Este artigo avança na narração adicionando controles de consistência de recursos ao MVP de governança para dar suporte a aplicativos de missão crítica.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

As equipes de adoção de nuvem têm atendido todos os requisitos para mover os dados protegidos. Com esses aplicativos vêm compromissos de SLA para os negócios e a necessidade de suporte das operações de TI. Logo atrás da equipe migrando os dois data centers, várias equipes de desenvolvimento de aplicativos e BI estão prontas para começar a lançar novas soluções na produção. As operações de ti são novas nas operações de nuvem e precisam integrar rapidamente os processos operacionais existentes.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

- A TI está movendo ativamente as cargas de trabalho de produção com dados protegidos no Azure. Algumas cargas de trabalho de baixa prioridade estão servindo tráfego de produção. Mais pode ser recortado assim que as operações de ti são desligadas na preparação para dar suporte às cargas de trabalho.
- As equipes de desenvolvimento de aplicativo estão prontas para o tráfego de produção.
- A equipe do BI está pronta para integrar as previsões e ideias sobre os sistemas que executam operações para as três unidades de negócios.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

- As operações de ti são novas nas operações de nuvem e precisam integrar rapidamente os processos operacionais existentes.
- As alterações ao estado atual e futuro expõem novos riscos que exigem novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Interrupção dos negócios:** Há um risco inerente de qualquer nova plataforma causando interrupções em processos de negócios de missão crítica. A equipe de operações de TI e as equipes que executam em várias adoções de nuvem são relativamente inexperientes com operações na nuvem. Isso aumenta o risco de interrupção e deve ser corrigido e regido.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

1. Processos operacionais desalinhados podem levar a interrupções que não podem ser detectadas ou atenuadas rapidamente.
2. Uma invasão externa ou ataques de negação de serviço podem causar uma interrupção dos negócios.
3. Ativos críticos não estão corretamente descobertos e, portanto, não operados corretamente.
4. Ativos não descobertos ou rotulados incorretamente podem não ser suportados pelos processos de gerenciamento operacionais existentes.
5. Configuração de ativos implantados pode não atender às expectativas de desempenho.
6. Registro em log pode não ser corretamente registrado e centralizado para permitir a correção dos problemas de desempenho.
7. As políticas de recuperação podem falhar ou levar mais tempo do que o esperado.
8. Os processos de implantação podem resultar em falhas de segurança, o que pode levar a perdas de dados ou interrupções.
9. Desvio de configuração ou patches ausentes pode resultar em falhas de segurança não intencionais, o que pode levar a vazamentos de dados ou interrupções.
10. Configuração não pode impor os requisitos de SLAs ou requisitos de recuperação confirmados.
11. Sistemas operacionais implantados ou aplicativos poderão não atender requisitos de proteção de aplicativo e de sistema operacional.
12. Há um risco de inconsistência devido a várias equipes trabalharem na nuvem.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece longa, mas a adoção dessas políticas pode ser mais fácil do que parece.

1. Todos os ativos implantados devem ser categorizados por nível de importância e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.
2. Sub-redes que contêm aplicativos de missão crítica devem ser protegidas por uma solução de firewall capaz de detecção de invasões e responder a ataques.
3. As ferramentas de governança devem realizar auditoria e impor requisitos de configuração de rede definidos pela equipe de Linha de Base de segurança.
4. As ferramentas de governança devem validar que todos os ativos relacionados a aplicativos críticos ou dados protegidos sejam incluídos no monitoramento para otimização e degradação de recursos.
5. As ferramentas de governança devem validar se o nível apropriado de dados de registro em log está sendo coletado para todos os aplicativos críticos ou dados protegidos.
6. O processo de governança deve validar o backup, recuperação e o cumprimento de SLA são implementados corretamente para aplicativos de missão crítica e dados protegidos.
7. As ferramentas de governança devem limitar a implantação da VM somente a imagens aprovadas.
8. Ferramentas de governança devem impor que as atualizações automáticas estejam **impedidas** em todos os ativos implantados que dão suporte a aplicativos de missão crítica. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Os ativos que não são atualizados automaticamente devem ser incluídos em processos de propriedade de operações de ti para atualizar esses servidores de forma rápida e eficiente.
9. Ferramentas de governança devem validar a marcação relacionadas à classificação de custo, nível de importância, SLA, aplicativos e dados. Todos os valores devem ser alinhados aos valores predefinidos gerenciados pela equipe de governança de nuvem.
10. Os processos de governança devem incluir auditorias no momento da implantação e em ciclos regulares para garantir a consistência em todos os ativos.
11. Tendências e explorações que podem afetar as implantações de nuvem devem ser revisadas regularmente pela equipe de segurança para que sejam fornecidas atualizações às ferramentas de Linha de Base de Segurança usadas na nuvem.
12. Antes da liberação para produção, todos os aplicativos de missão crítica e os dados protegidos devem ser adicionados à solução de monitoramento operacional designada. Ativos que não podem ser descobertos pelas ferramentas de operações de TI escolhidas, não podem ser liberados para uso em produção. Quaisquer alterações necessárias para tornar os ativos detectáveis devem ser feitas aos processos de implantação relevantes para garantir que os ativos sejam detectáveis em implantações futuras.
13. Quando descoberto, o dimensionamento de ativos é para ser validado pelas equipes de gerenciamento operacional para validar que o ativo atende aos requisitos de desempenho.
14. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
15. Os scripts de implantação devem ser mantidos no repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
16. Processos de revisão de governança devem validar que os ativos implantados estão configurados corretamente alinhados aos requisitos de SLA e recuperação.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhorará o design do MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Em conjunto, essas duas alterações de design atenderão às novas declarações da política corporativa.

Seguindo a experiência desse exemplo fictício, supõe-se que as alterações de dados protegidos já tenham ocorrido. Aproveitando essa prática recomendada, o seguinte adicionará requisitos operacionais de monitoramento, preparando uma assinatura para aplicativos de missão crítica.

**Assinatura de ti corporativa:** Adicione o seguinte à assinatura de ti corporativa, que atua como um Hub.

1. Como uma dependência externa, a equipe de operações de nuvem precisará definir ferramentas de monitoramento operacional, ferramentas de continuidade de negócios e recuperação de desastres (BCDR) e ferramentas de correção automatizadas. Em seguida, a equipe de governança de nuvem pode dar suporte aos processos de descoberta necessários.
    1. Nesse caso de uso, a equipe de operações de nuvem escolheu Azure Monitor como a principal ferramenta para monitorar aplicativos de missão crítica.
    2. A equipe também escolheu o Azure Site Recovery como as principais ferramentas de BCDR.
2. Implementação de Azure Site Recovery.
    1. Defina e implante o cofre de Azure Site Recovery para processos de backup e recuperação.
    2. Crie um modelo de gerenciamento de recursos do Azure para a criação de um cofre em cada assinatura.
3. Implementação de Azure Monitor.
    1. Depois que uma assinatura de missão crítica é identificada, um espaço de trabalho do log Analytics pode ser criado.

**Assinatura de adoção de nuvem individual:** O seguinte garantirá que cada assinatura seja detectável pela solução de monitoramento e pronta para ser incluída nas práticas de BCDR.

1. Azure Policy para nós de missão crítica:
    1. Realize uma auditoria e imponha o uso das funções apenas.
    2. Realize uma auditoria e imponha o aplicativo de criptografia para todas as contas de armazenamento.
    3. Realize uma auditoria e imponha o uso de uma sub-rede de rede aprovada e VNet por adaptador de rede
    4. Realize uma auditoria e imponha a limitação das tabelas de roteamento definidas pelo usuário.
    5. Realize uma auditoria e imponha a implantação dos agentes do Log Analytics para máquinas virtuais Windows ou Linux.
2. Blueprint do Azure:
    1. Criar um blueprint nomeado `mission-critical-workloads-and-protected-data`. Este blueprint aplicará ativos, além do blueprint dos dados protegidos.
    2. Adicione as novas políticas do Azure para o blueprint.
    3. Aplique o blueprint para qualquer assinatura que é esperada para hospedar um aplicativo de missão crítica.

## <a name="conclusion"></a>Conclusão

Adicionar esses processos e alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados à governança de recursos. Juntos, aumentam a recuperação, dimensionamento e controles de monitoramento necessários para capacitar as operações de reconhecimento de nuvem.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem cresce e fornece valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para a empresa fictícia neste guia, o próximo gatilho é quando a escala de implantação excede 1.000 ativos para a nuvem ou gastos mensais excedem $10000 USD por mês. Neste ponto, a equipe de governança de nuvem adiciona controles de gerenciamento de custos.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de gerenciamento de custos](./cost-management-improvement.md)
