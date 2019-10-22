---
title: 'Guia de governança para empresas complexas: melhorar a disciplina de consistência de recursos'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: melhorar a disciplina de consistência de recursos'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 66b1d5e414ecf7b1512cb408947bc519e460c471
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683538"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-resource-consistency-discipline"></a>Guia de governança para empresas complexas: melhorar a disciplina de consistência de recursos

Este artigo avança na narração adicionando controles de consistência de recursos ao MVP de governança para dar suporte a aplicativos de missão crítica.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

As equipes de adoção de nuvem atenderam a todos os requisitos para mover dados protegidos. Com esses aplicativos, vêm os compromissos de SLA para os negócios e precisam de suporte das operações de ti. Logo atrás da equipe migrando os dois data centers, várias equipes de desenvolvimento de aplicativos e BI estão prontas para começar a lançar novas soluções na produção. As operações de ti são novas nas operações de nuvem e precisam integrar rapidamente os processos operacionais existentes.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

- Ele está movendo ativamente as cargas de trabalho de produção com dados protegidos no Azure. Algumas cargas de trabalho de baixa prioridade estão servindo tráfego de produção. Mais pode ser recortado assim que as operações de ti são desligadas na preparação para dar suporte às cargas de trabalho.
- As equipes de desenvolvimento de aplicativos estão prontas para o tráfego de produção.
- A equipe de BI está pronta para integrar previsões e informações sobre os sistemas que executam operações para as três unidades de negócios.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

- As operações de ti são novas nas operações de nuvem e precisam integrar rapidamente os processos operacionais existentes.
- As alterações no estado atual e no futuro expõem novos riscos que exigirão novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Interrupção dos negócios:** Há um risco inerente de qualquer nova plataforma causando interrupções em processos de negócios de missão crítica. A equipe de operações de ti e as equipes em execução em várias adoçãos de nuvem são relativamente inexperientes com as operações de nuvem. Isso aumenta o risco de interrupção e deve ser corrigido e regido.

Esse risco comercial pode ser expandido em vários riscos técnicos:

1. Processos operacionais desalinhados podem levar a interrupções que não podem ser detectadas ou atenuadas rapidamente.
2. A invasão externa ou ataques de negação de serviço podem causar uma interrupção nos negócios.
3. Os ativos de missão crítica podem não ser adequadamente descobertos e, portanto, não operados corretamente.
4. Ativos não detectados ou com rótulo insuficiente podem não ser suportados por processos de gerenciamento operacional existentes.
5. A configuração de ativos implantados pode não atender às expectativas de desempenho.
6. O registro em log pode não ser corretamente registrado e centralizado para permitir a correção de problemas de desempenho.
7. As políticas de recuperação podem falhar ou demorar mais do que o esperado.
8. Processos de implantação inconsistentes podem resultar em lacunas de segurança que podem levar a vazamentos de dados ou interrupções.
9. A descompasso de configuração ou patches perdidos podem resultar em lacunas de segurança indesejadas que podem levar a vazamentos de dados ou interrupções.
10. A configuração pode não impor os requisitos de SLAs definidos ou requisitos de recuperação confirmados.
11. Os sistemas operacionais ou aplicativos implantados podem não atender aos requisitos de sistema operacional e de proteção do aplicativo.
12. Há um risco de inconsistência devido a várias equipes trabalhando na nuvem.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia. A lista parece muito longa, mas a adoção dessas políticas pode ser mais fácil do que seria exibida.

1. Todos os ativos implantados devem ser categorizados por criticalidade e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.
2. As sub-redes que contêm aplicativos de missão crítica devem ser protegidas por uma solução de firewall capaz de detectar invasões e responder a ataques.
3. As ferramentas de governança devem auditar e aplicar os requisitos de configuração de rede definidos pela equipe de linha de base de segurança.
4. As ferramentas de governança devem validar que todos os ativos relacionados a aplicativos de missão crítica ou dados protegidos estejam incluídos no monitoramento de esgotamento e otimização de recursos.
5. As ferramentas de governança devem validar que o nível apropriado de dados de log está sendo coletado para todos os aplicativos de missão crítica ou dados protegidos.
6. O processo de governança deve validar que o backup, a recuperação e a conformidade do SLA são implementados corretamente para aplicativos de missão crítica e dados protegidos.
7. As ferramentas de governança devem limitar a implantação de máquinas virtuais somente a imagens aprovadas.
8. As ferramentas de governança devem impor que as atualizações automáticas sejam **impedidas** em todos os ativos implantados que dão suporte a aplicativos de missão crítica. As violações devem ser examinadas com as equipes de gerenciamento operacional e corrigidas de acordo com as políticas de operações. Os ativos que não são atualizados automaticamente devem ser incluídos em processos de propriedade de operações de ti para atualizar esses servidores de forma rápida e eficiente.
9. As ferramentas de governança devem validar a marcação relacionada ao custo, à criticalidade, ao SLA, ao aplicativo e à classificação de dados. Todos os valores devem ser alinhados aos valores predefinidos gerenciados pela equipe de governança de nuvem.
10. Os processos de governança devem incluir auditorias no ponto de implantação e em ciclos regulares para garantir a consistência em todos os ativos.
11. As tendências e explorações que poderiam afetar as implantações na nuvem devem ser examinadas regularmente pela equipe de segurança para fornecer atualizações para as ferramentas de linha de base de segurança usadas na nuvem.
12. Antes da liberação para produção, todos os aplicativos de missão crítica e os dados protegidos devem ser adicionados à solução de monitoramento operacional designada. Os ativos que não podem ser descobertos pelas ferramentas de operações de ti escolhidas não podem ser liberados para uso em produção. Todas as alterações necessárias para tornar os ativos detectáveis devem ser feitas aos processos de implantação relevantes para garantir que os ativos sejam detectáveis em implantações futuras.
13. Quando descoberto, o dimensionamento de ativos é para ser validado pelas equipes de gerenciamento operacional para validar que o ativo atende aos requisitos de desempenho.
14. As ferramentas de implantação devem ser aprovadas pela equipe de governança de nuvem para garantir a governança contínua de ativos implantados.
15. Os scripts de implantação devem ser mantidos no repositório central acessível pela equipe de governança de nuvem para revisão e auditoria periódicas.
16. Os processos de análise de governança devem validar se os ativos implantados estão adequadamente configurados em alinhamento com os requisitos de SLA e de recuperação.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

Esta seção do artigo melhorará o design do MVP de governança para incluir novas políticas do Azure e uma implementação do gerenciamento de custos do Azure. Juntas, essas duas alterações de design atenderão às novas instruções de política corporativa.

Seguindo a experiência desse exemplo fictício, supõe-se que as alterações de dados protegidos já tenham ocorrido. Com base nessa prática recomendada, os itens a seguir adicionarão os requisitos de monitoramento operacional, preparando uma assinatura para aplicativos de missão crítica.

**Assinatura de ti corporativa:** Adicione o seguinte à assinatura de ti corporativa, que atua como um Hub.

1. Como uma dependência externa, a equipe de operações de nuvem precisará definir ferramentas de monitoramento operacional, ferramentas de continuidade de negócios e recuperação de desastres (BCDR) e ferramentas de correção automatizadas. Em seguida, a equipe de governança de nuvem pode dar suporte aos processos de descoberta necessários.
    1. Nesse caso de uso, a equipe de operações de nuvem escolheu Azure Monitor como a principal ferramenta para monitorar aplicativos de missão crítica.
    2. A equipe também escolheu Azure Site Recovery como as ferramentas de BCDR primárias.
2. Implementação de Azure Site Recovery.
    1. Defina e implante o cofre de Azure Site Recovery para processos de backup e recuperação.
    2. Crie um modelo de gerenciamento de recursos do Azure para a criação de um cofre em cada assinatura.
3. Implementação de Azure Monitor.
    1. Depois que uma assinatura de missão crítica é identificada, um espaço de trabalho do log Analytics pode ser criado.

**Assinatura de adoção de nuvem individual:** O seguinte garantirá que cada assinatura seja detectável pela solução de monitoramento e pronta para ser incluída nas práticas de BCDR.

1. Azure Policy para nós de missão crítica:
    1. Auditar e impor o uso somente de funções padrão.
    2. Auditar e aplicar a aplicação de criptografia para todas as contas de armazenamento.
    3. Auditar e impor o uso de sub-rede de rede aprovada e VNet por interface de rede.
    4. Auditar e impor a limitação de tabelas de roteamento definidas pelo usuário.
    5. Auditar e impor a implantação de agentes de Log Analytics para máquinas virtuais Windows e Linux.
2. Especificações técnicas do Azure:
    1. Crie um plano gráfico chamado `mission-critical-workloads-and-protected-data`. Este projeto aplicará ativos além do plano de dados protegido.
    2. Adicione as novas políticas do Azure ao plano gráfico.
    3. Aplique o plano gráfico a qualquer assinatura que seja esperada para hospedar um aplicativo de missão crítica.

## <a name="conclusion"></a>Conclusão

Adicionar esses processos e alterações ao MVP de governança ajuda a corrigir muitos dos riscos associados à governança de recursos. Juntos, eles adicionam os controles de recuperação, dimensionamento e monitoramento necessários para capacitar as operações que reconhecem a nuvem.

## <a name="next-steps"></a>Próximos passos

À medida que a adoção de nuvem cresce e fornece valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Para a empresa fictícia neste guia, o próximo gatilho é quando a escala de implantação excede 1.000 ativos para a nuvem ou gastos mensais excedem $10000 USD por mês. Neste ponto, a equipe de governança de nuvem adiciona controles de gerenciamento de custos.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de gerenciamento de custos](./cost-management-improvement.md)
