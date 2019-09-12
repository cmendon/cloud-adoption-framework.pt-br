---
title: Instruções de política de exemplo de Linha de base de segurança
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Instruções de política de exemplo de Linha de base de segurança
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 17317cc4430259918f189b7eac563ca98a5fc2c1
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70823437"
---
# <a name="security-baseline-sample-policy-statements"></a>Instruções de política de exemplo de Linha de base de segurança

As instruções individuais da política de nuvem são diretrizes para abordar os riscos específicos identificados durante o processo de avaliação de riscos. Essas instruções oferecem um resumo conciso dos riscos e planos com os quais lidar. Cada definição de instrução deve incluir essas informações:

- **Risco técnico:** Um resumo do risco que esta política abordará.
- **Instrução da política:** Uma clara explicação de resumo dos requisitos de política.
- **Opções técnicas:** Recomendações viáveis, especificações ou outras diretrizes que as equipes de TI e desenvolvedores possam usar ao implementar a política.

As instruções de política de exemplo a seguir abordam os riscos de negócios relacionados à segurança comuns. Essas instruções são exemplos que você pode referenciar ao rascunhar instruções de política para atender às necessidades da sua organização. Esses exemplos não devem ser proexistentes e há potencialmente várias opções de política para lidar com cada risco identificado. Trabalhe junto com as equipes de negócios, de segurança e de ti para identificar as melhores políticas para seu conjunto exclusivo de riscos.

## <a name="asset-classification"></a>Classificação de ativo

**Risco técnico:** Ativos que não estão corretamente identificados como dados confidenciais de missão crítica ou que envolvem dados talvez confidenciais podem não receber proteções suficientes, levando a potencial vazamento de dados ou interrupções dos negócios.

**Instrução da política:** Todos os ativos implantados devem ser categorizados por nível de importância e classificação de dados. As classificações devem ser revisadas pela equipe de governança de nuvem e pelo proprietário do aplicativo antes da implantação na nuvem.

**Possível opção de design:** Estabelecer [padrões de marcação de recursos](../../decision-guides/resource-tagging/index.md) e certificar-se de que a equipe de TI irá aplicá-las consistentemente a qualquer recurso implantado usando [marcas de recurso do Azure](/azure/azure-resource-manager/resource-group-using-tags).

## <a name="data-encryption"></a>Criptografia de dados

**Risco técnico:** Há um risco de exposição durante o armazenamento de dados protegidos.

**Instrução da política:** Todos os dados protegidos devem ser criptografados quando estão em repouso.

**Possível opção de design:** Consulte o artigo da [visão geral da criptografia do Azure](/azure/security/security-azure-encryption-overview) para uma discussão sobre como os dados de criptografia em repouso são executados na plataforma do Azure.

## <a name="network-isolation"></a>Isolamento da rede

**Risco técnico:** Conectividade entre redes e sub-redes dentro redes apresenta possíveis vulnerabilidades que podem resultar em vazamentos de dados ou interrupção dos serviços de missão crítica.

**Instrução da política:** As sub-redes de rede que contêm dados protegidos devem ser isoladas de todas as outras sub-redes. O tráfego de rede entre as sub-redes de dados protegidos será auditado regularmente.

**Possível opção de design:** No Azure, o isolamento de rede e sub-rede é gerenciado por meio das [Redes Virtuais do Azure](/azure/virtual-network/virtual-networks-overview).

## <a name="secure-external-access"></a>Acesso externo seguro

**Risco técnico:** Permitir o acesso da internet pública para cargas de trabalho apresenta um risco de invasões, resultando em exposição não autorizada de dados ou interrupção de negócios.

**Instrução da política:** Nenhuma sub-rede que contém os dados protegidos pode ser acessada diretamente pela internet pública ou em datacenters. O acesso a essas sub-redes deve ser roteado por meio de sub-redes intermediárias. Todo o acesso a essas sub-redes deve vir por meio de uma solução de firewall que pode executar a verificação de pacotes e funções de bloqueio.

**Possível opção de design:** No Azure, proteger pontos de extremidade públicos implantando uma [DMZ entre a internet pública e a rede baseada em nuvem](/azure/architecture/reference-architectures/dmz/secure-vnet-dmz).

## <a name="ddos-protection"></a>Proteção contra DDoS

**Risco técnico:** Ataques distribuídos de negação de serviço (DDoS) podem resultar em uma interrupção de negócios.

**Instrução da política:** Implante mecanismos automatizados de mitigação de DDoS para todos os pontos de extremidade de rede acessível publicamente.

**Possível opção de design:** Use a [Proteção contra DDoS do Azure](/azure/virtual-network/ddos-protection-overview) para minimizar as interrupções causadas por ataques de DDoS.

## <a name="secure-on-premises-connectivity"></a>Conectividade local segura

**Risco técnico:** O tráfego não criptografado entre sua rede de nuvem e locais na internet pública é vulnerável a interceptação, apresentando o risco de exposição de dados.

**Instrução da política:** Todas as conexões entre o local e as redes de nuvem devem ser realizadas por meio de uma conexão de VPN criptografada segura ou um link WAN privado dedicado.

**Possível opção de design:** No Azure, use o ExpressRoute ou VPN do Azure para estabelecer conexões privadas entre seu local e as redes de nuvem.

## <a name="network-monitoring-and-enforcement"></a>Monitoramento de rede e imposição

**Risco técnico:** Alterações na configuração de rede podem levar a novas vulnerabilidades e riscos de exposição de dados.

**Instrução da política:** As ferramentas de governança devem realizar auditoria e impor requisitos de configuração de rede definidos pela equipe de Linha de Base de segurança.

**Possível opção de design:** No Azure, a atividade de rede pode ser monitorada usando [Observador de Rede do Azure](/azure/network-watcher/network-watcher-monitoring-overview), e [Central de Segurança do Azure](/azure/security-center/security-center-network-recommendations) podem ajudar a identificar vulnerabilidades de segurança. O Azure Policy permite restringir os recursos de rede e a política de configuração de recursos de acordo com limites definidos pela equipe de segurança.

## <a name="security-review"></a>Revisão de segurança

**Risco técnico:** Ao longo do tempo, novas ameaças à segurança e tipos de ataques surgem, aumentando o risco de exposição ou interrupção dos seus recursos de nuvem.

**Instrução da política:** As tendências e explorações potenciais que podem afetar as implantações de nuvem devem ser revisadas regularmente pela equipe de segurança para que sejam fornecidas atualizações às ferramentas de Linha de base de segurança usadas na nuvem.

**Possível opção de design:** Estabeleça uma reunião de análise de segurança regular que inclua membros relevantes da equipe de TI e de governança. Examine as métricas e os dados de segurança existentes para estabelecer lacunas na política atual e nas ferramentas de linha de base de segurança, e atualize a política para corrigir quaisquer riscos novos.

## <a name="next-steps"></a>Próximas etapas

Use as amostras mencionadas neste artigo como ponto de partida para desenvolver políticas que abordem os riscos comerciais específicos que alinham-se aos seus planos de adoção de nuvem.

Para começar a desenvolver suas próprias instruções de política personalizadas relacionadas à Linha de Base de Segurança, baixe o [modelo de Linha de base de segurança](./template.md).

Para acelerar a adoção dessa disciplina, escolha o [Guia de governança acionável](../journeys/index.md) que esteja mais alinhado ao seu ambiente. Em seguida, modifique o design para incorporar suas decisões específicas de política corporativa.

Usar riscos e tolerância como base e estabelecer um processo para administrar e comunicar a adesão com a política de Linha de base de segurança.

> [!div class="nextstepaction"]
> [Estabelecer processos de conformidade de política](./compliance-processes.md)
