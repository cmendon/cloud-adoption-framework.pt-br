---
title: Instruções de política de exemplo de Linha de base de segurança
description: Instruções de política de exemplo de Linha de base de segurança
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ba0887b93664ac77fc2933c24631110dfab14be0
ms.sourcegitcommit: 2362fb3154a91aa421224ffdb2cc632d982b129b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76808865"
---
# <a name="security-baseline-sample-policy-statements"></a>Instruções de política de exemplo de Linha de base de segurança

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que essa política abordará.
- **Declaração de política:** Uma explicação resumida clara dos requisitos de política.
- **Opções técnicas:** Recomendações, especificações ou outras diretrizes acionáveis que as equipes de ti e os desenvolvedores podem usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à segurança comuns. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de negócios, de segurança e de ti para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="asset-classification"></a>Classificação de ativo

**Risco técnico:** Ativos que não são corretamente identificados como de missão crítica ou que envolvem dados confidenciais podem não receber proteções suficientes, levando a possíveis vazamentos de dados ou interrupções de negócios.

**Declaração de política:** Todos os ativos implantados devem ser categorizados por criticalidade e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.

**Possível opção de design:** Estabeleça [padrões de marcação de recursos](../../decision-guides/resource-tagging/index.md) e garanta que a equipe de ti as aplique de forma consistente a qualquer recurso implantado usando as [marcas de recurso do Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

## <a name="data-encryption"></a>Criptografia de dados

**Risco técnico:** Há um risco de os dados protegidos serem expostos durante o armazenamento.

**Declaração de política:** Todos os dados protegidos devem ser criptografados quando em repouso.

**Possível opção de design:** Consulte o artigo [visão geral da criptografia do Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview) para obter uma discussão sobre como os dados em repouso são executados na plataforma do Azure. Controles adicionais, como a criptografia de dados de conta e o controle sobre como as configurações de conta de armazenamento podem ser alteradas, também devem ser considerados.

## <a name="network-isolation"></a>Isolamento da rede

**Risco técnico:** A conectividade entre redes e sub-redes em redes introduz possíveis vulnerabilidades que podem resultar em vazamentos de dados ou interrupção de serviços de missão crítica.

**Declaração de política:** As sub-redes de rede que contêm dados protegidos devem ser isoladas de quaisquer outras sub-redes. O tráfego de rede entre as sub-redes de dados protegidos será auditado regularmente.

**Possível opção de design:** No Azure, o isolamento de rede e sub-rede é gerenciado por meio de [redes virtuais do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="secure-external-access"></a>Acesso externo seguro

**Risco técnico:** Permitir o acesso a cargas de trabalho da Internet pública apresenta um risco de intrusão, resultando em exposição não autorizada de dados ou interrupção dos negócios.

**Declaração de política:** Nenhuma sub-rede contendo dados protegidos pode ser acessada diretamente pela Internet pública ou por data centers. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que pode executar a verificação de pacotes e funções de bloqueio.

**Possível opção de design:** No Azure, proteja os pontos de extremidade públicos implantando uma [DMZ entre a Internet pública e sua rede baseada em nuvem](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz?toc=https://docs.microsoft.com/azure/cloud-adoption-framework/toc.json&bc=https://docs.microsoft.com/azure/cloud-adoption-framework/_bread/toc.json). Considere a implantação, a configuração e a automação do [Firewall do Azure](https://docs.microsoft.com/azure/firewall).

## <a name="ddos-protection"></a>Proteção de DDoS

**Risco técnico:** Ataques de DDoS (negação de serviço distribuído) podem resultar em uma interrupção de negócios.

**Declaração de política:** Implante mecanismos de mitigação de DDoS automatizados para todos os pontos de extremidade de rede acessíveis publicamente. Nenhum site voltado para o público apoiado por IaaS deve ser exposto à Internet sem DDoS.

**Possível opção de design:** Use a [proteção contra DDoS do Azure](https://docs.microsoft.com/azure/virtual-network/ddos-protection-overview) padrão para minimizar as interrupções causadas por ataques de DDoS.

## <a name="secure-on-premises-connectivity"></a>Conectividade local segura

**Risco técnico:** O tráfego não criptografado entre a rede de nuvem e o local pela Internet pública é vulnerável à interceptação, apresentando o risco de exposição de dados.

**Declaração de política:** Todas as conexões entre as redes locais e na nuvem devem ocorrer por meio de uma conexão VPN criptografada segura ou um link WAN privado dedicado.

**Possível opção de design:** No Azure, use o ExpressRoute ou a VPN do Azure para estabelecer conexões privadas entre suas redes locais e na nuvem.

## <a name="network-monitoring-and-enforcement"></a>Monitoramento de rede e imposição

**Risco técnico:** As alterações na configuração de rede podem levar a novas vulnerabilidades e riscos de exposição de dados.

**Declaração de política:** As ferramentas de governança devem auditar e aplicar os requisitos de configuração de rede definidos pela equipe de linha de base de segurança.

**Possível opção de design:** No Azure, a atividade de rede pode ser monitorada usando o [observador de rede do Azure](https://docs.microsoft.com/azure/network-watcher/network-watcher-monitoring-overview)e a [central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-network-recommendations) pode ajudar a identificar vulnerabilidades de segurança. O Azure Policy permite restringir os recursos de rede e a política de configuração de recursos de acordo com limites definidos pela equipe de segurança.

## <a name="security-review"></a>Revisão de segurança

**Risco técnico:** Ao longo do tempo, novas ameaças à segurança e tipos de ataque surgem, aumentando o risco de exposição ou interrupção de seus recursos de nuvem.

**Declaração de política:** As tendências e possíveis explorações que poderiam afetar as implantações de nuvem devem ser examinadas regularmente pela equipe de segurança para fornecer atualizações para as ferramentas de linha de base de segurança usadas na nuvem.

**Possível opção de design:** Estabeleça uma reunião de revisão de segurança regular que inclua Membros relevantes da equipe de ti e governança. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política atual e nas ferramentas de linha de base de segurança, e atualize a política para corrigir quaisquer riscos novos. Aproveite o [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) e a [central de segurança do Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) para obter informações acionáveis sobre ameaças emergentes específicas às suas implantações.

## <a name="next-steps"></a>Próximos passos

Use as amostras mencionadas neste artigo como ponto de partida para desenvolver políticas que abordem os riscos comerciais específicos que alinham-se aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas à Linha de Base de Segurança, baixe o [modelo de Linha de base de segurança](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../guides/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Usar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a adesão com a política de Linha de base de segurança.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
