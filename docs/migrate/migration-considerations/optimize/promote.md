---
title: Requisitos para promover um recurso migrado para produção
description: Use a estrutura de adoção de nuvem para o Azure para entender as tarefas comuns e os pré-requisitos padrão para promover um recurso migrado para produção.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: e2f0a0d92dfa63e0eb3f438fcc155854dfd61f8c
ms.sourcegitcommit: 5411c3b64af966b5c56669a182d6425e226fd4f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79311805"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-required-to-promote-a-migrated-resource-to-production"></a>O que é necessário para promover um recurso migrado para produção?

A promoção para produção marca a conclusão da migração de uma carga de trabalho para a nuvem. Depois que o ativo e todas as suas dependências são promovidos, o tráfego de produção é redirecionado. O redirecionamento do tráfego torna os ativos locais obsoletos, permitindo que sejam encerrados.

O processo de promoção varia de acordo com a arquitetura da carga de trabalho. No entanto, há vários pré-requisitos uniformes e algumas tarefas comuns. Este artigo descreve cada um deles e serve como um tipo de lista de verificação pré-promoção.

## <a name="prerequisite-processes"></a>Processos de pré-requisito

Cada um dos processos a seguir deve ser executado, documentado e validado antes da implantação de produção:

- **[Avaliar](../assess/index.md):** A carga de trabalho foi avaliada para compatibilidade com a nuvem.
- **[Arquiteto](../assess/architect.md):** A estrutura da carga de trabalho foi projetada corretamente para se alinhar com o provedor de nuvem escolhido.
- **[Replicar](../migrate/replicate.md):** Os ativos foram replicados para o ambiente de nuvem.
- **[Estágio](../migrate/stage.md):** Os ativos replicados foram restaurados em uma instância em etapas do ambiente de nuvem.
- **[Testes de negócios](./business-test.md):** A carga de trabalho foi totalmente testada e validada por usuários empresariais.
- **[Plano de mudança de negócios](./business-change-plan.md):** A empresa compartilhou um plano para que as alterações sejam feitas de acordo com a promoção de produção; Isso deve incluir um plano de adoção do usuário, alterações em processos de negócios, usuários que exigem treinamento e linhas do tempo para várias atividades.
- **[Pronto](./ready.md):** Em geral, uma série de alterações técnicas deve ser feita antes da promoção.

## <a name="best-practices-to-execute-prior-to-promotion"></a>Práticas recomendadas a serem executadas antes da promoção

As seguintes alterações técnicas provavelmente precisarão ser concluídas e documentadas como parte do processo de promoção:

- **Alinhamento de domínio.** Algumas políticas corporativas exigem domínios separados para preparo e produção. Verifique se todos os ativos estão ingressados no domínio apropriado.
- **Roteamento de usuários.** Valide se os usuários estão acessando a carga de trabalho por meio das rotas de rede adequadas; verifique se as expectativas de desempenho são consistentes.
- **Alinhamento de identidade.** Valide se os usuários que estão sendo redirecionados para o aplicativo têm as permissões adequadas no domínio para hospedar o aplicativo.
- **Desempenho.** Execute uma validação final do desempenho da carga de trabalho para minimizar surpresas.
- **Validação de continuidade dos negócios e recuperação de desastres.** Valide se os processos de backup e recuperação adequados estão funcionando conforme o esperado.
- **Classificação de dados.** Valide a classificação de dados para garantir que as proteções e políticas adequadas foram implementadas.
- **Verificação do CISO (diretor de segurança da informação).** Valide se o diretor de segurança da informação examinou a carga de trabalho, os riscos empresariais, a tolerância a riscos e as estratégias de mitigação.

## <a name="final-step-promote"></a>Etapa final: promover

As cargas de trabalho exigirão níveis variados de processos detalhados de análise e promoção. No entanto, o realinhamento da rede serve como a etapa final comum para todas as versões de promoção. Quando todo o resto estiver pronto, atualize os registros DNS ou endereços IP para rotear o tráfego para a carga de trabalho migrada.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

A promoção de uma carga de trabalho sinaliza a conclusão de um lançamento. No entanto, em paralelo com a migração, ativos descontinuados precisam ser [desativados](./decommission.md), removendo-os do serviço.

> [!div class="nextstepaction"]
> [Encerrar ativos desativados](./decommission.md)
