---
title: 'Guia de governança para empresas complexas: melhorar a disciplina de linha de base de identidade'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guia de governança para empresas complexas: melhorar a disciplina de linha de base de identidade'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/06/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 7decae6a0b9e0c8b41d30f5f3ccac2fdeab41feb
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547721"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-identity-baseline-discipline"></a>Guia de governança para empresas complexas: melhorar a disciplina de linha de base de identidade

Este artigo avança a narração adicionando controles de linha de base de identidade ao MVP de governança.

## <a name="advancing-the-narrative"></a>Aprimorando a narração

A justificativa de negócios para a migração de nuvem dos dois datacenters foi aprovada pelo CFO. Durante o estudo de viabilidade técnica, vários obstáculos foram descobertos:

- Os dados protegidos e os aplicativos de missão crítica representam 25% das cargas de trabalho nos dois data centers. Nenhuma delas pode ser eliminada até que as políticas de governança atuais relacionadas a dados pessoais confidenciais e aplicativos de missão crítica tenham sido modernizadas.
- 7% dos ativos nesses data centers não são compatíveis com a nuvem. Eles serão movidos para um datacenter alternativo antes do término do contrato de datacenter.
- 15% dos ativos no datacenter (750 máquinas virtuais) têm uma dependência de autenticação herdada ou autenticação multifator de terceiros.
- A conexão VPN que conecta os data centers existentes e o Azure não oferece velocidade ou latência de transmissão de dados suficiente para migrar o volume de ativos dentro da linha do tempo de dois anos para desativar o datacenter.

Os dois primeiros obstáculos estão sendo gerenciados em paralelo. Este artigo abordará a resolução do terceiro e do quarto empecilho.

### <a name="expanding-the-cloud-governance-team"></a>Expandindo a equipe de governança de nuvem

A equipe de governança de nuvem está se expandindo. Devido à necessidade de suporte adicional em relação ao gerenciamento de identidade, um administrador de sistemas da equipe de linha de base de identidade agora participa de uma reunião semanal para manter os integrantes da equipe existentes cientes das alterações.

### <a name="changes-in-the-current-state"></a>Alterações no estado atual

A equipe de ti tem aprovação para avançar com os planos do CIO e do CFO para desativar dois data centers. No entanto, é preocupado que 750 (15%) dos ativos nesses data centers precisarão ser movidos para outro lugar que não seja a nuvem.

### <a name="incrementally-improve-the-future-state"></a>Melhorar incrementalmente o estado futuro

Os novos planos de estado futuros exigem uma solução de linha de base de identidade mais robusta para migrar as máquinas virtuais 750 com requisitos de autenticação herdados. Além desses dois data centers, espera-se que esse desafio afete percentuais semelhantes de ativos em outros data centers.

O estado futuro agora também requer uma conexão do provedor de nuvem à solução MPLS/concessão de linha da empresa.

As alterações no estado atual e no futuro expõem novos riscos que exigirão novas instruções de política.

## <a name="changes-in-tangible-risks"></a>Alterações em riscos tangíveis

**Interrupção de negócios durante a migração.** A migração para a nuvem cria um risco controlado por tempo limitado que pode ser gerenciado. Mover o hardware de envelhecimento para outra parte do mundo é um risco muito maior. Uma estratégia de mitigação é necessária para evitar interrupções nas operações de negócios.

**Dependências de identidade existentes.** As dependências dos serviços de identidade e de autenticação existentes podem atrasar ou impedir a migração de algumas cargas de trabalho para a nuvem. A falha ao retornar os dois datacenters no tempo incorrerá em milhões de dólares em taxas de concessão de datacenter.

Esse risco comercial pode ser expandido em alguns riscos técnicos:

- A autenticação herdada pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.
- A solução de autenticação multifator de terceiros atual pode não estar disponível na nuvem, limitando a implantação de alguns aplicativos.
- A referramenta ou a movimentação pode criar interrupções ou adicionar custos.
- A velocidade e a estabilidade da VPN podem impedir a migração.
- O tráfego entrando na nuvem pode causar problemas de segurança em outras partes da rede global.

## <a name="incremental-improvement-of-the-policy-statements"></a>Melhoria incremental das instruções de política

As alterações a seguir na política ajudarão a corrigir os novos riscos e a implementação do guia.

- O provedor de nuvem escolhido deve oferecer um meio de autenticação por meio de métodos herdados.
- O provedor de nuvem escolhido deve oferecer um meio de autenticação com a solução de autenticação multifator de terceiros atual.
- Uma conexão privada de alta velocidade deve ser estabelecida entre o provedor de nuvem e o provedor de telecomunicações da empresa, conectando o provedor de nuvem à rede global de data centers.
- Até que requisitos de segurança suficientes sejam estabelecidos, nenhum tráfego público de entrada poderá acessar os ativos da empresa hospedados na nuvem. Todas as portas são bloqueadas de qualquer fonte fora da WAN global.

## <a name="incremental-improvement-of-the-best-practices"></a>Melhoria incremental das práticas recomendadas

O design do MVP de governança é alterado para incluir novas políticas do Azure e uma implementação de Active Directory em uma máquina virtual. Juntas, essas duas alterações de design atendem às novas instruções de política corporativa.

Aqui estão as novas práticas recomendadas:

- **Plantas de VNet híbrida segura:** O lado local da rede híbrida deve ser configurado para permitir a comunicação entre a solução a seguir e os servidores de Active Directory locais. Essa prática recomendada requer uma DMZ para habilitar Active Directory Domain Services entre limites de rede.
- **Modelos de Azure Resource Manager:**
    1. Defina um NSG para bloquear o tráfego externo e permitir o tráfego interno.
    2. Implante duas máquinas virtuais Active Directory em um par de balanceamento de carga com base em uma imagem dourada. Na primeira inicialização, essa imagem executa um script do PowerShell para ingressar no domínio e registrá-lo com os serviços de domínio. Para obter mais informações, consulte [estender Active Directory Domain Services (AD DS) para o Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/adds-extend-domain).
- Azure Policy: aplique o NSG a todos os recursos.
- Especificações técnicas do Azure:
    1. Crie um plano gráfico chamado `active-directory-virtual-machines`.
    2. Adicione cada um dos modelos de Active Directory e políticas ao plano gráfico.
    3. Publique o Blueprint em qualquer grupo de gerenciamento aplicável.
    4. Aplique o plano gráfico a qualquer assinatura que exija autenticação multifator herdada ou de terceiros.
    5. A instância do Active Directory em execução no Azure agora pode ser usada como uma extensão da solução de Active Directory local, permitindo que ele se integre à ferramenta de autenticação multifator existente e forneça a autenticação baseada em declarações, por meio de funcionalidade de Active Directory existente.

## <a name="conclusion"></a>Conclusão

A adição dessas alterações ao MVP de governança ajuda a corrigir muitos dos riscos neste artigo, permitindo que cada equipe de adoção da nuvem se movimente rapidamente após esse obstáculo.

## <a name="next-steps"></a>Próximos passos

À medida que a adoção de nuvem continua e entrega o valor comercial adicional, os riscos e as necessidades de governança de nuvem também serão alterados. Veja a seguir algumas alterações que podem ocorrer. Para essa empresa fictícia, o próximo gatilho é a inclusão de dados protegidos no plano de adoção de nuvem. Essa alteração requer controles de segurança adicionais.

> [!div class="nextstepaction"]
> [Melhorar a disciplina de linha de base de segurança](./security-baseline-improvement.md)
