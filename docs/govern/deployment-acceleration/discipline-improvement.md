---
title: Melhoria da disciplina de aceleração de implantação
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Melhoria da disciplina de aceleração de implantação
author: alexbuckgit
ms.author: abuck
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: b1b4395efd909a0f4456a39a6b2b933d25e4f002
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547774"
---
# <a name="deployment-acceleration-discipline-improvement"></a>Melhoria da disciplina de aceleração de implantação

A disciplina de aceleração da implantação concentra-se no estabelecimento de políticas que garantem que os recursos sejam implantados e configurados de forma consistente e repetida, e permaneçam em conformidade em todo o ciclo Dentro das cinco disciplinas de governança de nuvem, a aceleração de implantação inclui decisões relacionadas à automação de implantações, ao controle de origem de artefatos de implantação, ao monitoramento de recursos implantados para manter o estado desejado e à auditoria de qualquer conformidade edições.

Este artigo descreve algumas tarefas potenciais pelas quais sua empresa pode se envolver para desenvolver melhor e amadurecer a disciplina de aceleração de implantação. Essas tarefas podem ser divididas em fases de planejamento, criação, adoção e operação de implementação de uma solução de nuvem, que são então iteradas para permitir o desenvolvimento de uma [abordagem incremental para governança de nuvem](../guides/index.md#an-incremental-approach-to-cloud-governance).

![Quatro fases de adoção](../../_images/govern/adoption-phases.png)

*Figura 1-fases de adoção da abordagem incremental para governança de nuvem.*

É impossível para qualquer documento considerar os requisitos de todas as empresas. Como tal, este artigo descreve as atividades de exemplo mínimas e potenciais do sugerido para cada fase do processo de desenvolvimento de governança. O objetivo inicial dessas atividades é ajudá-lo a criar um [MVP de política](../guides/index.md#an-incremental-approach-to-cloud-governance) e estabelecer uma estrutura para aperfeiçoamento da política incremental. Sua equipe de governança de nuvem precisará decidir quanto investir nessas atividades para melhorar seus recursos de governança de linha de base de identidade.

> [!CAUTION]
> Nem as atividades mínimas ou potenciais descritas neste artigo estão alinhadas a políticas corporativas específicas ou a requisitos de conformidade de terceiros. Estas diretrizes foram projetadas para ajudar a facilitar as conversas que levarão ao alinhamento dos dois requisitos com um modelo de governança de nuvem.

## <a name="planning-and-readiness"></a>Planejamento e preparação

Essa fase de maturidade de governança preenche a divisão entre resultados de negócios e estratégias acionáveis. Durante esse processo, a equipe de liderança define métricas específicas, mapeia essas métricas para o espaço digital e começa a planejar o esforço geral de migração.

**Mínimo de atividades sugeridas:**

- Avalie suas opções de [ferramentas de aceleração de implantação](./toolchain.md) e implemente uma estratégia híbrida apropriada para sua organização.
- Desenvolva um documento de diretrizes de arquitetura de rascunho e distribua para as principais partes interessadas.
- Instrua e envolva as pessoas e equipes afetadas pelo desenvolvimento de diretrizes de arquitetura.
- Treine as equipes de desenvolvimento e a equipe de ti para entender os princípios e as estratégias do DevSecOps e a importância das implantações totalmente automatizadas na disciplina de aceleração da implantação.

**Atividades potenciais:**

- Defina as funções e atribuições que controlarão a aceleração da implantação na nuvem.

## <a name="build-and-predeployment"></a>Compilação e pré-implantação

**Mínimo de atividades sugeridas:**

- Para novos aplicativos baseados em nuvem, apresente implantações totalmente automatizadas no início do processo de desenvolvimento. Esse investimento melhorará a confiabilidade dos seus processos de teste e garantirá a consistência em seus ambientes de desenvolvimento, controle de qualidade e produção.
- Armazene todos os artefatos de implantação, como modelos de implantação ou scripts de configuração usando uma plataforma de controle de origem, como GitHub ou Azure DevOps.
- Armazene todos os segredos, senhas, certificados e cadeias de conexão no [Azure Key Vault](https://docs.microsoft.com/azure/key-vault)
- Considere um teste piloto antes de implementar seu [ferramentas de aceleração de implantação](./toolchain.md), garantindo que ele simplifique suas implantações o máximo possível. Aplique comentários dos testes piloto durante a fase de pré-implantação, repetindo conforme necessário.
- Avalie a arquitetura lógica e física de seus aplicativos e identifique oportunidades para automatizar a implantação de recursos do aplicativo ou melhorar partes da arquitetura usando outros recursos baseados em nuvem.
- Atualize o documento de diretrizes de arquitetura para incluir os planos de implantação e adoção de usuário, e distribua para as principais partes interessadas.
- Continue a treinar as pessoas e as equipes mais afetadas pelas diretrizes de arquitetura.

**Atividades potenciais:**

- Defina um pipeline de CI/CD (integração contínua e implantação contínua) para gerenciar totalmente a liberação de atualizações para seu aplicativo por meio de ambientes de desenvolvimento, de qualidade e de produção.

## <a name="adopt-and-migrate"></a>Adote e migre

A migração é um processo incremental que se concentra na movimentação, no teste e na adoção de aplicativos ou cargas de trabalho em um espaço digital existente.

**Mínimo de atividades sugeridas:**

- Migre seu [ferramentas de aceleração de implantação](./toolchain.md) de desenvolvimento para produção.
- Atualize o documento de diretrizes de arquitetura e distribua para as principais partes interessadas.
- Desenvolva materiais educacionais e documentação, comunicações de conscientização, incentivos e outros programas para ajudar a impulsionar o desenvolvedor e a adoção de ti.

**Atividades potenciais:**

- Valide se as práticas recomendadas definidas durante as fases de compilação e pré-implantação foram executadas corretamente.
- Verifique se cada aplicativo ou carga de trabalho se alinha com a estratégia de aceleração de implantação antes do lançamento.

## <a name="operate-and-post-implementation"></a>Operar e pós-implementação

Depois que a transformação for concluída, a governança e as operações deverão residir para o ciclo de vida natural de um aplicativo ou carga de trabalho. Essa fase de maturidade de governança se concentra nas atividades que normalmente vêm depois que a solução é implementada e o ciclo de transformação começa a estabilizar.

**Mínimo de atividades sugeridas:**

- Personalize seu [ferramentas de aceleração de implantação](./toolchain.md) com base nas alterações nas necessidades de identidade dinâmicas de sua organização.
- Automatize notificações e relatórios para alertar sobre possíveis problemas de configuração ou ameaças mal-intencionadas.
- Monitorar e relatar o uso de aplicativos e recursos.
- Relate as métricas pós-implantação e distribua para os participantes.
- Revise as diretrizes de arquitetura para orientar processos futuros de adoção.
- Continue a se comunicar com o e treinar as pessoas e equipes afetadas regularmente para garantir a adesão contínua às diretrizes de arquitetura.

**Atividades potenciais:**

- Configure uma ferramenta de monitoramento e relatório de configuração de estado desejado.
- Examine regularmente as ferramentas e os scripts de configuração para melhorar os processos e identificar problemas comuns.
- Trabalhe com equipes de desenvolvimento, operações e segurança para ajudar as práticas DevSecOpss maduras e dividir os silos organizacionais que levam a ineficiências.

## <a name="next-steps"></a>Próximos passos

Agora que você entendeu o conceito de governança de identidade de nuvem, examine o [ferramentas de linha de base de identidade](./toolchain.md) para identificar as ferramentas e os recursos do Azure que você precisará ao desenvolver a disciplina de governança de linha de base de identidade na plataforma Azure.

> [!div class="nextstepaction"]
> [Ferramentas de linha de base de identidade para o Azure](./toolchain.md)
