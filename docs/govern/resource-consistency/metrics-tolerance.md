---
title: Métricas de consistência de recursos, indicadores e tolerância a riscos
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Métricas de consistência de recursos, indicadores e tolerância a riscos
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2a6f59c09533fc400871d549e32c9b7d56024551
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548074"
---
# <a name="resource-consistency-metrics-indicators-and-risk-tolerance"></a>Métricas de consistência de recursos, indicadores e tolerância a riscos

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com a consistência dos recursos. Definir métricas e indicadores ajuda a criar um caso comercial para tornar um investimento em desenvolvimento da disciplina de consistência de recursos.

## <a name="metrics"></a>Métricas

A disciplina de consistência de recursos concentra-se em abordar os riscos relacionados ao gerenciamento operacional de suas implantações na nuvem. Como parte de sua análise de riscos, você desejará reunir dados relacionados às suas operações de ti para determinar a quantidade de riscos enfrentados e como o investimento importante no controle de consistência de recursos é para suas implantações de nuvem planejadas.

Cada organização tem diferentes cenários operacionais, mas os itens a seguir representam exemplos úteis das métricas que você deve coletar ao avaliar a tolerância a riscos na disciplina de consistência de recursos:

- **Ativos de nuvem.** Número total de recursos implantados na nuvem.
- **Recursos não marcados.** Número de recursos sem contabilidade necessária, impacto nos negócios ou marcas organizacionais.
- **Ativos subutilizados.** Número de recursos em que a memória, a CPU ou os recursos de rede são todos inutilizados consistentemente.
- **Esgotamento de recursos.** Número de recursos em que a memória, a CPU ou os recursos de rede são esgotados por carga.
- **Idade do recurso.** Tempo desde que o recurso foi implantado pela última vez ou modificado.
- **VMs em condição crítica.** Número de VMs implantadas em que um ou mais problemas críticos são detectados e que precisam ser resolvidos para restaurar a funcionalidade normal.
- **Alertas por severidade.** Número total de alertas em um ativo implantado, dividido por severidade.
- **Links de rede não íntegros.** Número de recursos com problemas de conectividade de rede.
- **Pontos de extremidade de serviço não íntegros.** Número de problemas com pontos de extremidade de rede externa.
- **Incidentes de integridade do serviço do provedor de nuvem.** Número de interrupções ou incidentes de desempenho causados pelo provedor de nuvem.
- **Contratos de nível de serviço.** Isso pode incluir os compromissos da Microsoft quanto ao tempo de atividade e à conectividade dos serviços do Azure, bem como compromissos feitos pelos negócios para seus clientes externos e internos.
- **Disponibilidade do serviço.** Porcentagem de cargas de trabalho de tempo de atividade hospedadas em nuvem em comparação com o tempo de atividade esperado.
- **RTO (objetivo de tempo de recuperação).** O tempo máximo aceitável que um aplicativo pode ficar indisponível após um incidente.
- **Objetivo de ponto de recuperação (RPO).** A duração máxima da perda de dados aceitável durante um desastre. Por exemplo, se você armazenar dados em um único banco de dado, sem replicação para outros bancos e executar backups por hora, poderá perder até uma hora de dados.
- **Tempo médio de recuperação (MTTR).** O tempo médio necessário para restaurar um componente após uma falha.
- **Tempo médio entre falhas (MTBF).** A duração que um componente pode esperar para ser executado entre interrupções. Essa métrica pode ajudá-lo a calcular a frequência com que um serviço ficará indisponível.
- **Integridade do backup.** Número de backups que estão sendo sincronizados ativamente.
- **Integridade da recuperação.** Número de operações de recuperação executadas com êxito.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

As plataformas de nuvem oferecem um conjunto de linhas de base de recursos que permitem que as equipes de implantação gerenciem efetivamente pequenas implantações sem o planejamento ou processos adicionais. Como resultado, pequenas cargas de trabalho de desenvolvimento/teste ou experimentais que incluem uma quantidade relativamente pequena de ativos baseados em nuvem representam baixo nível de risco e provavelmente não precisarão muito na forma de uma política de consistência de recursos formal.

No entanto, como o tamanho do seu espaço na nuvem aumenta a complexidade de gerenciar seus ativos torna-se significativamente mais difícil. Com mais ativos na nuvem, a capacidade de identificar a propriedade dos recursos e controlar os recursos úteis se torna crítica para minimizar os riscos. À medida que mais cargas de trabalho de missão crítica são implantadas na nuvem, o tempo de atividade do serviço se torna mais crítico e a tolerância para a interrupção dos custos potenciais de interrupções de serviço diminui rapidamente.

Nos primeiros estágios da adoção de nuvem, trabalhe com sua equipe de operações de ti e com os participantes de negócios para identificar [os riscos de negócios](./business-risks.md) relacionados à consistência de recursos e, em seguida, determinar uma linha de base aceitável para a tolerância a riscos. Esta seção da estrutura de adoção de nuvem fornece exemplos, mas os riscos e as linhas de base detalhados para sua empresa ou implantações podem ser diferentes.

Quando você tiver uma linha de base, estabeleça os parâmetros de comparação mínimos que representam um aumento inaceitável nos seus riscos identificados. Esses benchmarks atuam como gatilhos para quando você precisa tomar medidas para corrigir esses riscos. Veja a seguir alguns exemplos de como as métricas operacionais, como as discutidas acima, podem justificar um maior investimento na disciplina de consistência de recursos.

- **Gatilho de marcação e nomenclatura.** Uma empresa com mais de _x_ recursos sem informações de marcação necessárias ou não obedecer aos padrões de nomenclatura deve considerar investindo na disciplina de consistência de recursos para ajudar a refinar esses padrões e garantir um aplicativo consistente deles para ativos implantados na nuvem.
- **Gatilho de recursos superprovisionados.** Se uma empresa tiver mais de _x%_ dos ativos regularmente usando pequenas quantidades de memória disponível, CPU ou recursos de rede, o investimento na disciplina de consistência de recursos é sugerido para ajudar a otimizar o uso de recursos para esses itens.
- **Gatilho de recursos subprovisionados.** Se uma empresa tiver mais de _x%_ dos ativos que esgotam a maioria de seus recursos de memória, CPU ou rede disponíveis, o investimento na disciplina de consistência de recursos é sugerido para ajudar a garantir que esses ativos tenham os recursos necessários para prevenir interrupções de serviço.
- **Gatilho de idade do recurso.** Uma empresa com mais de _x_ recursos que não foram atualizados em mais de _y_ meses poderia se beneficiar do investimento na disciplina de consistência de recursos voltada para garantir que os recursos ativos sejam corrigidos e íntegros, ao mesmo tempo em que se aposentam obsoletos ou caso contrário, ativos não utilizados.
- **Gatilho de contrato de nível de serviço.** Uma empresa que não atende aos seus contratos de nível de serviço para seus clientes externos ou parceiros internos deve investir na disciplina de aceleração de implantação para reduzir o tempo de inatividade do sistema.
- **Gatilhos de tempo de recuperação.** Se uma empresa exceder os limites necessários para o tempo de recuperação após uma falha do sistema, ele deverá investir em melhorar sua disciplina de aceleração de implantação e o design de sistemas para reduzir ou eliminar falhas ou o efeito de um tempo de inatividade individual do componente.
- **Gatilho de integridade da VM.** Uma empresa com mais de _x%_ das VMs que estão enfrentando um problema de integridade crítico deve investir na disciplina de consistência de recursos para identificar problemas e melhorar a estabilidade da VM.
- **Gatilho de integridade da rede.** Uma empresa com mais de _x%_ das sub-redes de rede ou pontos de extremidade que enfrentam problemas de conectividade deve investir na disciplina de consistência de recursos para identificar e resolver problemas de rede.
- **Gatilho de cobertura de backup.** Uma empresa com _x%_ de ativos de missão crítica sem backups atualizados pode se beneficiar de um maior investimento na disciplina de consistência de recursos para garantir uma estratégia de backup consistente.
- **Gatilho de integridade de backup.** Uma empresa com mais de _x%_ de falha das operações de restauração deve investir na disciplina de consistência de recursos para identificar problemas de backup e garantir que recursos importantes sejam protegidos.

As métricas e os gatilhos exatos que você usa para medir a tolerância a riscos e o nível de investimento na disciplina de consistência de recursos serão específicos para sua organização, mas os exemplos acima devem servir como uma base útil para discussão em sua governança de nuvem time.

## <a name="next-steps"></a>Próximos passos

Usando o [modelo de gerenciamento de nuvem](./template.md), as métricas de documento e os indicadores de tolerância que se alinham ao plano de adoção de nuvem atual.

Examine as políticas de consistência de recursos de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos de negócios específicos que se alinham com seus planos de adoção de nuvem.

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
