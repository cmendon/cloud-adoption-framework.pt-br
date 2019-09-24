---
title: Métricas, indicadores e tolerância a riscos da Consistência de Recursos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Métricas, indicadores e tolerância a riscos da Consistência de Recursos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 387cc7b320e50628e2f10c25ab49f200878d3636
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222953"
---
# <a name="resource-consistency-metrics-indicators-and-risk-tolerance"></a>Métricas, indicadores e tolerância a riscos da Consistência de Recursos

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com a consistência dos recursos. Definir métricas e indicadores ajuda a criar um caso de negócios para investir no amadurecimento da disciplina Consistência de Recursos.

## <a name="metrics"></a>metrics

A disciplina de Consistência de Recursos se concentra em lidar com os riscos relacionados ao gerenciamento operacional de suas implantações de nuvem. Como parte da análise de risco, você irá querer reunir os dados relacionados às suas operações de TI para determinar quanto risco você enfrenta e como é importante o investimento na governança de Consistência de Recursos em suas implantações de nuvem planejadas.

Cada organização tem cenários operacionais diferentes, mas os itens a seguir representam exemplos úteis das métricas que você deve obter ao avaliar a tolerância de risco na disciplina de Consistência de Recursos:

- **Ativos de nuvem.** Número total de recursos de implantação de nuvem.
- **Recursos não marcados.** Número de recursos sem marcas de contabilização, impacto comercial ou organizacionais.
- **Ativos subutilizados.** Número de recursos em que a memória, a CPU ou os recursos de rede são todos inutilizados consistentemente.
- **Esgotamento de recursos.** Número de recursos em que a memória, a CPU ou os recursos de rede estão esgotados por carga.
- **Idade do recurso.** Tempo desde que o recurso foi implantado ou modificado.
- **VMs em condição crítica.** Número de máquinas virtuais onde um ou mais problemas críticos são detectados que precisam ser abordados para restaurar a funcionalidade normal.
- **Alertas por severidade.** Número total de alertas em um ativo de implantado, divididos por gravidade.
- **Links de rede não íntegros.** Número de recursos com problemas de conectividade de rede.
- **Pontos de extremidade de serviço não íntegros.** Número de problemas com pontos de extremidade de rede externa.
- **Incidentes de integridade do serviço do provedor de nuvem.** Número de interrupções ou incidentes de desempenho causados pelo provedor de nuvem.
- **Contratos de nível de serviço.** Isso pode incluir compromissos da Microsoft para atualização e conectividade dos serviços do Azure, bem como compromissos realizados pela empresa para seus clientes internos e externos.
- **Disponibilidade do serviço.** Porcentagem de tempo de atividade real hospedado na nuvem cargas de trabalho comparada ao tempo de atividade esperado.
- **RTO (objetivo de tempo de recuperação).** Tempo máximo aceitável que um aplicativo pode ficar indisponível após um incidente.
- **Objetivo de ponto de recuperação (RPO).** Duração máxima de perda de dados que é aceitável durante um desastre. Por exemplo, se você armazena dados em um único banco de dados, com nenhuma replicação para outros bancos de dados, e executar backups a cada hora, poderá perder até uma hora de dados.
- **Tempo médio de recuperação (MTTR).** Tempo médio necessário para restaurar um componente após uma falha.
- **Tempo médio entre falhas (MTBF).** A duração de um componente razoável pode esperar para executar entre interrupções. Essa métrica pode ajudar você a calcular a frequência com que um serviço ficará indisponível.
- **Integridade do backup.** Número de backups que estão sendo sincronizados ativamente.
- **Integridade da recuperação.** Número de operações de recuperação executada com êxito.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

Plataformas de nuvem que oferecem um conjunto de recursos que permite que a implantação de equipes gerencie com eficácia pequenas implantações sem planejamento adicional amplo ou processos. Como resultado, Desenvolvimento/Teste pequeno ou primeiras cargas de trabalho experimentais que incluem uma quantidade relativamente pequena de ativos baseados em nuvem, representam baixo nível de risco e provavelmente não serão necessário muito em relação a uma política de Consistência de Recursos formal.

No entanto, à medida que o tamanho do seu acervo de nuvem aumenta a complexidade de gerenciar seus ativos, torna-se significativamente mais difícil. Com mais ativos na nuvem, a capacidade de identificar a propriedade dos recursos e recursos de controle úteis se torna essencial para minimizar os riscos. Conforme mais cargas de trabalho de missão crítica são implantadas para a nuvem, o tempo de atividade do serviço se torna mais crítico e a tolerância para custo potencial de interrupção diminui rapidamente.

Nos estágios iniciais de adoção da nuvem, trabalhe com a equipe de operações de TI e stakeholders de negócios para identificar os [riscos de negócios](./business-risks.md) relacionados a consistência de recursos, em seguida, determine uma linha de base aceitável para tolerância a riscos. Esta seção da estrutura de adoção de nuvem fornece exemplos, mas os riscos e as linhas de base detalhados para sua empresa ou implantações podem ser diferentes.

Assim que você tiver uma linha de base, estabeleça parâmetros de comparação mínimos que representem um aumento inaceitável em seus riscos identificados. Esses benchmarks atuam como gatilhos para quando você precisa tomar medidas para corrigir esses riscos. Veja a seguir alguns exemplos de como métricas operacionais, como as discutidas anteriormente, podem justificar o aumento de investimento na disciplina de Consistência de Recursos.

- **Gatilho de marcação e nomenclatura.** Uma empresa com mais de _x_ recursos sem informações de marcação necessárias ou não obedecer aos padrões de nomenclatura deve considerar investindo na disciplina de consistência de recursos para ajudar a refinar esses padrões e garantir um aplicativo consistente deles para ativos implantados na nuvem.
- **Gatilho de recursos superprovisionados.** Se uma empresa tiver mais de _x%_ dos ativos regularmente usando pequenas quantidades de memória disponível, CPU ou recursos de rede, o investimento na disciplina de consistência de recursos é sugerido para ajudar a otimizar o uso de recursos para esses itens.
- **Gatilho de recursos subprovisionados.** Se uma empresa tiver mais de _x%_ dos ativos que esgotam a maioria de seus recursos de memória, CPU ou rede disponíveis, o investimento na disciplina de consistência de recursos é sugerido para ajudar a garantir que esses ativos tenham os recursos necessários para prevenir interrupções de serviço.
- **Gatilho de idade do recurso.** Uma empresa com mais de _x_ recursos que não foram atualizados em mais de _y_ meses poderia se beneficiar do investimento na disciplina de consistência de recursos voltada para garantir que os recursos ativos sejam corrigidos e íntegros, ao mesmo tempo em que se aposentam obsoletos ou caso contrário, ativos não utilizados.
- **Gatilho de contrato de nível de serviço.** Uma empresa que não atende aos seus contratos de nível de serviço para seus clientes externos ou parceiros internos deve investir na disciplina de aceleração de implantação para reduzir o tempo de inatividade do sistema.
- **Gatilhos de tempo de recuperação.** Se uma empresa exceder os limites necessários para o tempo de recuperação após uma falha do sistema, ela investir em aperfeiçoar sua disciplina de aceleração de implantação e no design do sistema para reduzir ou eliminar falhas ou o efeito do tempo de inatividade do componente individual.
- **Gatilho de integridade da VM.** Uma empresa com mais de _x%_ das VMs que estão enfrentando um problema de integridade crítico deve investir na disciplina de consistência de recursos para identificar problemas e melhorar a estabilidade da VM.
- **Gatilho de integridade da rede.** Uma empresa com mais de _x%_ das sub-redes de rede ou pontos de extremidade que enfrentam problemas de conectividade deve investir na disciplina de consistência de recursos para identificar e resolver problemas de rede.
- **Gatilho de cobertura de backup.** Uma empresa com _x%_ de ativos de missão crítica sem backups atualizados pode se beneficiar de um maior investimento na disciplina de consistência de recursos para garantir uma estratégia de backup consistente.
- **Gatilho de integridade de backup.** Uma empresa com mais de _x%_ de falha das operações de restauração deve investir na disciplina de consistência de recursos para identificar problemas de backup e garantir que recursos importantes sejam protegidos.

As métricas e os gatilhos exatos que você usa para medir a tolerância a riscos e o nível de investimento na disciplina de consistência de recursos serão específicos para sua organização, mas os exemplos acima devem servir como uma base útil para discussão em sua governança de nuvem time.

## <a name="next-steps"></a>Próximas etapas

Usar o [modelo de Gerenciamento de Nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.

Examine as políticas de consistência de recursos de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos de negócios específicos que se alinham com seus planos de adoção de nuvem.

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
