---
title: Métricas de Linha de base de segurança, indicadores e tolerância a risco
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Métricas de Linha de base de segurança, indicadores e tolerância a risco
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b8171839b79ffbe9e3849cf303180d1f1ee049f2
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222843"
---
# <a name="security-baseline-metrics-indicators-and-risk-tolerance"></a>Métricas de Linha de base de segurança, indicadores e tolerância a risco

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com a linha de base de segurança. Definir métricas e indicadores ajuda a criar um caso de negócios para investir no amadurecimento da disciplina Linha de Base de Segurança.

## <a name="metrics"></a>metrics

Linha de base de segurança em geral se concentra na identificação de possíveis vulnerabilidades em suas implantações de nuvem. Como parte da sua análise de risco, você desejará coletar dados relacionados ao seu ambiente de segurança para determinar o grau do risco enfrentado e quão importante é o investimento na governança da linha de base de segurança para as implantações de nuvem planejadas.

Cada organização tem requisitos e ambientes de segurança diferentes e diferentes possíveis fontes de dados de segurança. Veja a seguir exemplos de métricas úteis que devem ser coletadas para ajudar a avaliar a tolerância a riscos na disciplina Linha de base de segurança:

- **Classificação de dados:** Número de dados armazenados em nuvem e serviços que não são classificados de acordo com na privacidade, conformidade ou padrões de impacto de negócios da sua organização.
- **Número de armazenamentos de dados confidenciais:** O número de pontos de extremidade de armazenamento ou bancos de dados que contêm informações confidenciais e devem ser protegidos.
- **Número de armazenamentos de dados não criptografados:** Número de armazenamentos de dados confidenciais que não estão criptografados.
- **Superfície de ataque:** Quantas fontes de dados totais, serviços e aplicativos serão hospedados na nuvem. Qual porcentagem dessas fontes de dados ser classificada como sensível? Qual é a porcentagem desses aplicativos e serviços serem de missão crítica?
- **Padrões cobertos:** Número de padrões de segurança definidos pela equipe de segurança.
- **Recursos cobertos:** Ativos implantados que são cobertos pelos padrões de segurança.
- **Conformidade geral com os padrões:** Taxa de aderência à conformidade com os padrões de segurança.
- **Ataques por severidade:** Quantas tentativas coordenadas para interromper os serviços hospedados na nuvem, como por meio de ataques de negação de serviço distribuído (DDoS), faz a sua experiência de infraestrutura? Qual é o tamanho e a gravidade desses ataques?
- **Proteção contra malware:** Porcentagem de máquinas virtuais implantadas (VMs) que têm todos os itens necessário anti-malware, firewall ou outro software de segurança instalado.
- **Latência de patch:** Quanto tempo passou desde que as VMs tiveram patches do sistema operacional e software aplicados.
- **Recomendações de integridade de segurança:** Número de recomendações de software de segurança para resolver os padrões de integridade para recursos implantados, organizados por gravidade.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

Plataformas de nuvem fornecem um conjunto de recursos de linha de base que permitem que as equipes de implantação pequenas configurem as definições de segurança básicas sem planejamento adicional extensivo. Como resultado, pequenos desenvolvimento/teste ou as primeiras cargas de trabalho experimentais que não incluem dados confidenciais representam um nível de risco relativamente baixo e provavelmente não precisarão muito na forma de uma diretiva de linha de base de segurança formal. No entanto, assim que os dados importantes ou a funcionalidade de missão crítica for movida para a nuvem, o risco de segurança aumenta, enquanto a tolerância a esses riscos diminui rapidamente. Conforme mais dos seus dados e a funcionalidade são implantados na nuvem, será maior a probabilidade de você precisar de um investimento maior na disciplina de Linha de base de segurança.

Nos estágios iniciais de adoção da nuvem, trabalhe com sua equipe e segurança de TI e stakeholders de negócios para identificar os [riscos de negócios](./business-risks.md) relacionados à identidade e, em seguida, determine uma linha de base aceitável para a tolerância do risco de segurança. Esta seção da estrutura de adoção de nuvem fornece exemplos, mas os riscos e as linhas de base detalhados para sua empresa ou implantações podem ser diferentes.

Assim que você tiver uma linha de base, estabeleça parâmetros de comparação mínimos que representem um aumento inaceitável em seus riscos identificados. Esses benchmarks atuam como gatilhos para quando você precisa tomar medidas para corrigir esses riscos. Veja a seguir alguns exemplos de como métricas relacionadas à segurança, como as discutidas anteriormente, podem justificar o aumento de investimento na disciplina Linha de Base de Segurança.

- **Gatilhos de cargas de trabalho de missão crítica.** Uma empresa implantando cargas de trabalho de missão crítica para a nuvem deve investir na disciplina de Linha de base de segurança para impedir possíveis interrupções de serviço ou a exposição de dados confidenciais.
- **Gatilho de dados protegidos.** Uma empresa que hospeda os dados na nuvem que podem ser classificados como confidenciais, privados ou caso contrário, sujeito a preocupações com regulamentação. Precisam de uma disciplina de linha de base de segurança para garantir que esses dados não estejam sujeitos a perda, exposição ou roubo.
- **Gatilho de ataques externos.** Uma empresa que enfrenta ataques sérios em sua infraestrutura de rede _x_ vezes por mês pode se beneficiar da disciplina de linha de base de segurança.
- **Gatilho de conformidade de padrões.** Uma empresa com mais de _x%_ dos recursos da conformidade com os padrões de segurança deve investir na disciplina de linha de base de segurança para garantir que os padrões sejam aplicados consistentemente em toda a sua infraestrutura de ti.
- **Gatilho de tamanho do estado de nuvem.** Uma empresa que hospeda mais de _x_ aplicativos, serviços ou fontes de dados. Implantações de nuvem grande podem aproveitar o investimento na disciplina de linha de base de segurança para garantir que a superfície de ataque geral seja devidamente protegida contra acesso não autorizado ou outras ameaças externas.
- **Gatilho de conformidade do software de segurança.** Uma empresa em que menos de _x%_ das máquinas virtuais implantadas tenham todos os softwares de segurança necessários instalados. Uma disciplina de Linha de base de segurança pode ser usada para garantir que o software seja instalado consistentemente em todos os softwares.
- **Gatilho de aplicação de patch.** Uma empresa na qual foram implantadas máquinas virtuais ou serviços em que OS patches de sistema operacional ou software não foram aplicados nos últimos _x_ dias. A disciplina de Linha de base de segurança pode ser usada para garantir a aplicação de patch ser mantida atualizada dentro de uma agenda necessária.
- **Com foco em segurança.** Algumas empresas terão fortes requisitos de segurança e confidencialidade de dados, mesmo para teste e cargas de trabalho experimentais. Essas empresas precisarão investir na disciplina de linha de base de segurança antes de começam as implantações.

As métricas e os gatilhos exatos que você usa para medir a tolerância a riscos e o nível de investimento na disciplina de linha de base de segurança serão específicos para sua organização, mas os exemplos acima devem servir como uma base útil para discussão em sua equipe de governança de nuvem.

## <a name="next-steps"></a>Próximas etapas

Usar o [modelo de Gerenciamento de Nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.

Examine as políticas de linha de base de segurança de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos comerciais específicos que se alinham com seus planos de adoção de nuvem

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
