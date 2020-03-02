---
title: Métricas e indicadores da tolerância a riscos de linha de base de identidade.
description: Use a estrutura de adoção de nuvem para o Azure para aprender a quantificar a tolerância a riscos de negócios relacionada à linha de base de identidade.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9d50e40ba5877eab0f2aa904f2bcc1e984c309ca
ms.sourcegitcommit: 72a280cd7aebc743a7d3634c051f7ae46e4fc9ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78223873"
---
# <a name="identity-baseline-metrics-indicators-and-risk-tolerance"></a>Métricas, indicadores e tolerância a riscos da linha de base de identidade

Este artigo o ajudará a quantificar a tolerância a riscos de negócios, pois ela se relaciona com a linha de base de identidade. Definir métricas e indicadores ajuda a criar um caso de negócios para investir no amadurecimento da disciplina Linha de Base de Identidade.

## <a name="metrics"></a>Métricas

A linha de base de identidade se concentra na identificação, autenticação e autorização de indivíduos, grupos de usuários ou processos automatizados e fornece a eles o devido acesso aos recursos em suas implantações de nuvem. Como parte da análise de risco, são coletados dados relacionados aos serviços de identidade para determinar qual o grau de risco enfrentado e quão importante é o investimento em governança na linha de base de identidade para suas implantações planejadas de nuvem.

Veja a seguir exemplos de métricas úteis que devem ser coletadas para ajudar a avaliar a tolerância a riscos na disciplina Linha de Base de Identidade:

- **Tamanho dos sistemas de identidade.** Quantidade total de usuários, grupos ou outros objetos gerenciados pelos sistemas de identidade.
- **Tamanho geral da infraestrutura de serviços de diretório.** Quantidade de florestas, domínios e locatários de diretório usados pela sua organização.
- **Dependência de mecanismos de autenticação herdados ou locais.** Número de cargas de trabalho que dependem de mecanismos herdados ou de autenticação multifator ou de terceiros.
- **Extensão dos serviços de diretório implantados na nuvem.** Quantidade de florestas, domínios e locatários de diretório implantados na nuvem.
- **Servidores Active Directory implantados na nuvem.** Quantidade de servidores do Active Directory implantados na nuvem.
- **Unidades organizacionais implantadas na nuvem.** Número de Active Directory UOs (unidades organizacionais) implantadas na nuvem.
- **Extensão da Federação.** Quantidade de sistemas de linha de base de identidade federados com sistemas de sua organização.
- **Usuários elevados.** Quantidade de contas de usuário com acesso elevado para recursos ou ferramentas de gerenciamento.
- **Uso do controle de acesso baseado em função.** Número de assinaturas, grupos de recursos ou recursos individuais não gerenciados por meio do controle de acesso baseado em função (RBAC) por meio de grupos.
- **Declarações de autenticação.** Quantidade de tentativas de autenticação de usuário bem-sucedidas e com falha.
- **Declarações de autorização.** Quantidades de tentativas bem-sucedidas e com falha de acesso a recursos feitas pelos usuários.
- **Contas comprometidas.** Quantidade de contas de usuário que foram comprometidas.

## <a name="risk-tolerance-indicators"></a>Indicadores de tolerância de risco

Os riscos relacionados à linha de base de identidade estão amplamente relacionados à complexidade da infraestrutura de identidades da organização. Se todos os seus usuários e grupos forem gerenciados usando um único diretório ou provedor de identidade nativo de nuvem usando a integração mínima com outros serviços, o nível de risco provavelmente será pequeno. No entanto, como sua empresa precisa desenvolver os sistemas de linha de base de identidade, talvez seja necessário oferecer suporte a cenários mais complicados, como vários diretórios para dar suporte à organização ou federação interna com provedores de identidade externos. À medida que esses sistemas se tornam mais complexos, o risco aumenta.

Nos estágios iniciais de adoção da nuvem, trabalhe com sua equipe e segurança de TI e stakeholders de negócios para identificar [riscos de negócios](./business-risks.md) relacionados à identidade e, em seguida, determine uma linha de base aceitável para a tolerância do risco de identidade. Esta seção da estrutura de adoção de nuvem fornece exemplos, mas os riscos e as linhas de base detalhados para sua empresa ou implantações podem ser diferentes.

Assim que você tiver uma linha de base, estabeleça parâmetros de comparação mínimos que representem um aumento inaceitável em seus riscos identificados. Esses benchmarks atuam como gatilhos para quando você precisa tomar medidas para resolver esses riscos. Veja a seguir alguns exemplos de como métricas relacionadas à identidade, como as discutidas anteriormente, podem justificar o aumento de investimento na disciplina Linha de Base de Identidade.

- **Gatilho de número de conta de usuário.** Uma empresa com mais de _x_ usuários, grupos ou outros objetos gerenciados em seus sistemas de identidade pode se beneficiar do investimento na disciplina de linha de base de identidade para garantir uma governança eficiente em um grande número de contas.
- **Gatilho de dependência de identidade local.** Uma empresa que planeja migrar cargas de trabalho para a nuvem que exigem recursos de autenticação herdados ou autenticação multifator de terceiros deve investir na disciplina de linha de base de identidade para reduzir os riscos relacionados à refatoração ou nuvem adicional implantação de infraestrutura.
- **Gatilho de complexidade dos serviços de diretório.** Uma empresa que mantém mais de _x_ número of_ florestas individuais, domínios ou locatários de diretório deve investir na disciplina de linha de base de identidade para reduzir os riscos relacionados ao gerenciamento de conta e os problemas de eficiência relacionados a várias credenciais de usuário espalhadas por vários sistemas.
- **Gatilho de serviços de diretório hospedado na nuvem.** Uma empresa que hospeda máquinas virtuais (VMs) do servidor _x_ Active Directory hospedadas na nuvem ou que tenha unidades organizacionais _x_ (UOs) gerenciadas nesses servidores baseados em nuvem pode se beneficiar do investimento na disciplina de linha de base de identidade para otimizar a integração com qualquer serviço de identidade local ou outro.
- **Gatilho de Federação.** Uma empresa que implementa a Federação de identidades com sistemas de linha de base de identidade externa _x_ pode se beneficiar de investir na disciplina de linha de base de identidade para garantir uma política organizacional consistente entre membros da Federação.
- **Gatilho de acesso elevado.** Uma empresa com mais de _x%_ dos usuários com permissões elevadas para ferramentas de gerenciamento e recursos deve considerar investindo na disciplina de linha de base de identidade para minimizar o risco de excesso de provisionamento inadvertido de acesso aos usuários.
- **Gatilho do RBAC.** Uma empresa com menos de _x%_ dos recursos que usam métodos de controle de acesso baseado em função deve considerar investindo na disciplina de linha de base de identidade para identificar maneiras otimizadas de atribuir acesso de usuário aos recursos.
- **Gatilho de falha de autenticação.** Uma empresa em que as falhas de autenticação representam mais de _x%_ das tentativas deve investir na disciplina de linha de base de identidade para garantir que os métodos de autenticação não estejam sob ataque externo e que os usuários possam se autenticar corretamente.
- **Gatilho de falha de autorização.** Uma empresa em que as tentativas de acesso são rejeitadas mais de _x%_ do tempo deve investir na disciplina de linha de base de identidade para melhorar o aplicativo e atualizar os controles de acesso e identificar tentativas de acesso potencialmente mal-intencionadas.
- **Gatilho de conta comprometida.** Uma empresa com mais de 1 conta comprometida deve investir na disciplina de linha de base de identidade para melhorar a força e a segurança dos mecanismos de autenticação e melhorar os mecanismos para corrigir os riscos relacionados a contas comprometidas.

As métricas e os gatilhos exatos que você usa para medir a tolerância a riscos e o nível de investimento na disciplina de linha de base de identidade serão específicos para sua organização, mas os exemplos acima devem servir como uma base útil para discussão em sua equipe de governança de nuvem.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

Usar o [modelo de Gerenciamento de Nuvem](./template.md), de métricas do documento e de indicadores de tolerância que se alinham ao atual plano de adoção da nuvem.

Examine as políticas de linha de base de identidade de exemplo como um ponto de partida para desenvolver políticas que atendam a riscos comerciais específicos que se alinham com seus planos de adoção de nuvem

> [!div class="nextstepaction"]
> [Examinar as políticas de exemplo](./policy-statements.md)
