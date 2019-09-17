---
title: 'Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de identidade'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de identidade'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/06/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 0c17f9043dd88f401b07293a6b93e50ccefe0137
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028693"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-identity-baseline-discipline"></a>Guia de governança para empresas complexas: Melhorar a disciplina de linha de base de identidade

Este artigo avança a narração adicionando controles de linha de base de identidade ao MVP de governança.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A justificativa comercial para a migração de nuvem dos dois datacenters foi aprovada pelo CFO. Durante o estudo da viabilidade técnica, várias dificuldades foram descobertas:

- Dados protegidos e aplicativos de missão crítica representam 25% das cargas de trabalho em dois data centers. Nenhuma delas pode ser eliminada até que as políticas de governança atuais relacionadas a dados pessoais confidenciais e aplicativos de missão crítica tenham sido modernizadas.
- % 7 dos ativos nos data centers não são compatíveis com a nuvem. Eles serão movidos para um datacenter alternativo antes do término do contrato de datacenter.
- 15% dos ativos no data center (750 máquinas de virtuais) têm uma dependência na autenticação herdada ou autenticação de multifator de terceiros.
- A conexão VPN que conecta os datacenters existentes e o Azure não oferece velocidades ou latência de transmissão de dados suficientes para migrar o volume dos ativos dentro da linha do tempo de dois para desativar o datacenter.

Os dois primeiros obstáculos estão sendo gerenciados em paralelo. Este artigo abordará a resolução das dificuldades do terceiro e quarto bloqueio.

### <a name="expanding-the-cloud-governance-team"></a>Expandindo a equipe de governança de nuvem

A equipe de governança de nuvem está se expandindo. Dada a necessidade de suporte adicionais sobre o gerenciamento de identidade, um administrador de sistemas da equipe de linha de base de identidade agora participa de uma reunião semanal para manter os membros da equipe existente ciente das alterações.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

A equipe de TI tem aprovação para prosseguir com o CIO e o CFO planeja desativar dois data centers. No entanto, a IT está preocupada que 750 (15%) dos ativos nos data centers terão de ser movidos em algum lugar diferente da nuvem.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

Os novos planos de estado futuro exigem uma solução de identidade da linha de base mais robusta para migrar as 750 máquinas virtuais com os requisitos de autenticação herdados. Além desses dois data centers, espera-se que esse desafio afete percentuais semelhantes de ativos em outros data centers.

O estado futuro agora também requer uma conexão do provedor de nuvem à solução MPLS/baseado em linha da empresa.

As alterações ao estado atual e futuro expõem novos riscos que exigem novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Interrupção de negócios durante a migração.** A migração para a nuvem cria um risco controlado e limite de tempo que pode ser gerenciado. Mover o hardware de classificação por vencimento para outra parte do mundo é um risco muito maior. Uma estratégia de mitigação é necessária para evitar interrupções para as operações de negócios.

**Dependências de identidade existentes.** As dependências em serviços de autenticação e identidade existentes podem atrasar ou evitar a migração de algumas cargas de trabalho para a nuvem. A falha ao retornar dois datacenters na hora incorrerá em milhões de dólares em valores de concessão de datacenter.

Esse risco de negócios pode ser dividido em alguns riscos técnicos:

- A autenticação herdada pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.
- A solução de autenticação multifator de terceiros atual pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.
- A referramenta ou a movimentação pode criar interrupções ou adicionar custos.
- A velocidade e a estabilidade do VPN podem impedir a migração.
- O tráfego entrando na nuvem pode causar problemas de segurança em outras partes da rede global.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- O provedor de nuvem escolhido deve oferecer um meio de autenticar por meio de métodos herdados.
- O provedor de nuvem escolhido deve oferecer um meio de autenticação com a solução de autenticação multifator de terceiros atual.
- Uma conexão privada de alta velocidade deve ser estabelecida entre o provedor de nuvem e o provedor de telecomunicações da empresa, conectando o provedor de nuvem à rede global dos datacenters.
- Até que os requisitos de segurança suficientes sejam estabelecidos, nenhum tráfego de entrada público pode acessar os ativos da empresa hospedados na nuvem. Todas as portas são bloqueadas de qualquer fonte fora da WAN global.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

O design do MVP de governança é alterado para incluir novas políticas do Azure e uma implementação de Active Directory em uma máquina virtual. Juntas, essas duas alterações de design atenderão às novas instruções da política corporativa.

Aqui estão as novas práticas recomendadas:

- **Plantas de VNet híbrida segura:** O lado local da rede híbrida deve ser configurado para permitir a comunicação entre a solução a seguir e os servidores de Active Directory locais. Essa prática recomendada requer um DMZ para habilitar o Active Directory Domain Services entre os limites de rede.
- **Modelos do Azure Resource Manager:**
    1. Defina um NSG para bloquear o tráfego externo e permitir o tráfego interno.
    1. Implante duas máquinas virtuais Active Directory em um par de balanceamento de carga com base em uma imagem dourada. Na primeira inicialização, essa imagem executa um script do PowerShell para ingressar no domínio e registrar-se aos serviços de domínio. Para obter mais informações, consulte [Estendendo o Active Directory Domain Services (AD DS) para o Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain).
- Azure Policy: Aplica o NSG a todos os recursos.
- Blueprint do Azure:
    1. Criar um blueprint nomeado `active-directory-virtual-machines`.
    1. Adicione cada um dos modelos de Active Directory e políticas ao plano gráfico.
    1. Publique o plano gráfico em qualquer grupo de gerenciamento aplicáveis.
    1. Aplique o plano gráfico a qualquer assinatura que exija autenticação multifator herdada ou de terceiros.
    1. A instância do Active Directory em execução no Azure agora pode ser usada como uma extensão da solução de Active Directory local, permitindo que ele se integre à ferramenta de autenticação multifator existente e forneça a autenticação baseada em declarações, por meio de funcionalidade de Active Directory existente.

## <a name="conclusion"></a>Conclusão

A adição dessas alterações ao MVP de governança ajuda a corrigir muitos dos riscos neste artigo, permitindo que cada equipe de adoção da nuvem se movimente rapidamente após esse obstáculo.

## <a name="next-steps"></a>Próximas etapas

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Veja a seguir algumas alterações que podem ocorrer. Para essa empresa fictícia, o próximo gatilho é a inclusão de dados protegidos no plano de adoção de nuvem. Essa alteração requer controles de segurança adicionais.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de linha de base de segurança](./security-baseline-improvement.md)
