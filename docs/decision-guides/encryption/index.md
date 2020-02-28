---
title: Guia de decisão de criptografia
description: Implemente uma política de criptografia, um serviço principal em migrações do Azure que fornece camadas adicionais de segurança para suas cargas de trabalho e dados baseados em nuvem.
author: rotycenh
ms.author: v-tyhopk
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: decision-guide
ms.custom: governance
ms.openlocfilehash: c81096576934aa55bd0381e7ac26dd8666b827ea
ms.sourcegitcommit: af45c1c027d7246d1a6e4ec248406fb9a8752fb5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77707978"
---
# <a name="encryption-decision-guide"></a>Guia de decisão de criptografia

A criptografia dos dados os protege contra acessos não autorizados. Uma política de criptografia implementada apropriadamente proporciona camadas adicionais de segurança para suas cargas de trabalho baseadas em nuvem e protege contra invasores e outros usuários não autorizados dentro e fora de sua organização e suas redes.

Ir para: [Gerenciamento de chaves](#key-management) | [Criptografia de dados](#data-encryption) | [Saiba mais](#learn-more)

A estratégia de criptografia de nuvem se concentra em políticas corporativas e normas de conformidade. Recursos de criptografia são desejáveis e muitos serviços do Azure, como Armazenamento do Azure e Banco de Dados SQL do Azure, habilitam a criptografia por padrão. No entanto, a criptografia tem custos que podem aumentar a latência e uso geral de recursos.

Para cargas de trabalho exigentes, alcançar o equilíbrio correto entre desempenho e criptografia e determinar como dados e tráfego são criptografados podem ser essenciais. Mecanismos de criptografia podem variar em termos de custo e complexidade e requisitos tanto técnicos quanto de política podem influenciar suas decisões sobre como a criptografia é aplicada e como armazenar e gerenciar chaves e segredos críticos.

A política corporativa e a conformidade de terceiros são os maiores impulsionadores ao planejar uma estratégia de criptografia. O Azure fornece vários mecanismos padrão que podem atender aos requisitos comuns de criptografia de dados, seja em repouso ou em trânsito. No entanto, para as políticas e os requisitos de conformidade que exigem controles mais rígidos, como segredos padronizados e gerenciamento de chaves, criptografia em uso ou criptografia específica de dados, você precisará desenvolver uma estratégia de criptografia mais sofisticada para oferecer suporte a esses requisitos.

## <a name="key-management"></a>Gerenciamento de chaves

A criptografia de dados na nuvem depende do armazenamento, do gerenciamento e do uso operacional seguro das chaves de criptografia. Um sistema de gerenciamento de chaves é essencial para a habilidade da sua organização de criar, armazenar e gerenciar chaves de criptografia, bem como senhas importantes, cadeias de conexão e outras informações confidenciais de TI.

Modernos sistemas de gerenciamento de chaves, como armazenamento de suporte do Azure Key Vault e o gerenciamento de chaves protegidas por software para uso em desenvolvimento e teste e chaves protegidas por HSM (módulo de segurança de hardware) para a máxima proteção de cargas de trabalho de produção.

Ao planejar uma migração na nuvem, a tabela a seguir pode ajudá-lo a decidir como armazenar e gerenciar chaves de criptografia, certificados e segredos, que são críticos para a criação de implantações de nuvem segura e gerenciável:

| Pergunta | Nativo da nuvem | Bring your own key | Reter sua própria chave |
|---------------------------------------------------------------------------------------------------------------------------------------|--------------|--------|-------------|
| Há uma falta de gerenciamento centralizado de chaves e segredos na sua organização?                                                                    | Sim          | Não     | Não          |
| Você precisará limitar a criação de chaves e segredos em dispositivos para seu hardware local ao usar essas chaves na nuvem? | Não           | Sim    | Não          |
| Sua organização tem regras ou políticas em vigor que impediriam que as chaves fossem armazenadas fora do local?                | Não           | Não     | Sim         |

### <a name="cloud-native"></a>Nativo da nuvem

Com o gerenciamento de chaves nativo de nuvem, todas as chaves e segredos são gerados, gerenciados e armazenados em um cofre baseado em nuvem, como o Azure Key Vault. Essa abordagem simplifica muitas tarefas de TI relacionadas ao gerenciamento de chaves, como o backup, armazenamento e renovação de chave.

Usar um sistema de gerenciamento de chaves nativo da nuvem inclui estas suposições:

- Você confia a criação, o gerenciamento e a hospedagem de chaves e segredos da sua organização à solução de gerenciamento de chaves de nuvem.
- Você habilita todos os aplicativos e serviços locais que dependam do acesso a serviços ou segredos de criptografia para acessar o sistema de gerenciamento de chaves em nuvem.

### <a name="bring-your-own-key"></a>Bring your own key

Com uma abordagem do tipo "Bring Your Own Key", você gera chaves em hardware HSM dedicado em seu ambiente local, então transfere com segurança essas chaves para um sistema de gerenciamento baseado em nuvem como o Azure Key Vault para uso com os recursos hospedados na nuvem.

**Pressuposições sobre "Bring Your Own Key":** Gerar chaves localmente e usá-las com um sistema de gerenciamento de chaves baseado em nuvem inclui estas suposições:

- Você confia a segurança subjacente e a infraestrutura de controle de acesso da plataforma de nuvem para hospedar e usar suas chaves e segredos.
- Seus aplicativos ou serviços hospedados na nuvem são capazes de acessar e usar chaves e segredos de modo robusto e seguro.
- Conforme a política organizacional ou regulatória, você é obrigado a manter a criação e o gerenciamento de segredos e chaves local da sua organização.

### <a name="on-premises-hold-your-own-key"></a>Local (mantenha sua própria chave)

Em determinados cenários, é possível que haja motivos regulamentares, de política ou técnicos que impeçam o armazenamento de chaves em um sistema de gerenciamento de chaves baseado em nuvem. Nesses casos, você precisa gerar chaves usando hardware local, armazenar e gerenciar essas chaves usando um sistema de gerenciamento de chaves local e estabelecer uma maneira para que os recursos baseados em nuvem acessem essas chaves para fins de criptografia. A opção de manter a sua própria chave pode não ser compatível com todos os serviços baseados no Azure.

**Suposições sobre o gerenciamento de chaves local:** Usar um sistema de gerenciamento de chaves local inclui estas suposições:

- Conforme a política organizacional ou regulatória, você é obrigado a manter a criação, o gerenciamento e a hospedagem de segredos e chaves local da sua organização.
- Quaisquer aplicativos ou serviços baseados em nuvem que dependam do acesso a serviços ou segredos de criptografia podem acessar o sistema de gerenciamento de chaves local.

## <a name="data-encryption"></a>Criptografia de dados

Considere vários estados diferentes de dados com diferentes necessidades de criptografia ao planejar sua política de criptografia:

| Estado de dados | Dados |
|-----|-----|
| Dados em trânsito | Tráfego interno, conexões de Internet, conexões entre datacenters ou redes virtuais |
| Dados em repouso    | Bancos de dados, arquivos, discos virtuais, armazenamento de PaaS |
| Dados em uso     | Dados carregados na memória RAM ou em caches da CPU |

### <a name="data-in-transit"></a>Dados em trânsito

Dados em trânsito são dados que se movem entre recursos nas redes internas, entre datacenters ou externas ou pela Internet.

Os dados em trânsito geralmente são criptografados exigindo protocolos SSL/TLS para o tráfego de rede. Sempre criptografe o tráfego entre seus recursos hospedados na nuvem e as redes externas ou a Internet pública. Os recursos de PaaS normalmente impõem a criptografia SSL/TLS por padrão. Suas equipes de adoção de nuvem e os proprietários de cargas de trabalho devem considerar a imposição da criptografia para o tráfego entre os recursos de IaaS hospedados em suas redes virtuais.

**Suposições sobre a criptografia de dados em trânsito:** Para a implementação de uma política de criptografia adequada a dados em trânsito, pressupõe-se o seguinte:

- Todos os pontos de extremidade publicamente acessíveis em seu ambiente de nuvem vão comunicar com a Internet pública usando protocolos SSL/TLS.
- Ao conectar redes em nuvem a outras redes externas ou locais na Internet pública, use protocolos VPN criptografados.
- Ao conectar redes de nuvem a redes locais ou a outras redes externas usando uma conexão WAN dedicada, como o ExpressRoute, você usará uma VPN ou outro dispositivo de criptografia local emparelhado com um dispositivo correspondente de VPN virtual ou de criptografia implantado na sua rede de nuvem.
- Caso tenha dados confidenciais que não devam ser incluídos em logs de tráfego ou outros relatórios de diagnóstico visíveis à equipe de TI, você criptografará todo o tráfego entre recursos em sua rede virtual.

### <a name="data-at-rest"></a>Dados em repouso

Dados em repouso representam quaisquer dados que não estão sendo ativamente movidos ou processados, incluindo arquivos, bancos de dados, unidades de máquina virtual, as contas de armazenamento de PaaS ou ativos semelhantes. A criptografia de dados armazenados protege dispositivos ou arquivos virtuais contra o acesso não autorizado a partir de uma invasão de rede externa, usuários internos mal-intencionados ou liberações acidentais.

Por padrão, recursos de armazenamento e banco de dados de PaaS geralmente impõem a criptografia. Recursos de IaaS podem ser protegidos criptografando dados no nível do disco virtual ou criptografando toda a conta de armazenamento que hospeda suas unidades virtuais. Todos esses ativos podem usar suas chaves gerenciadas pelo cliente ou pela Microsoft armazenadas no Azure Key Vault.

A criptografia de dados em repouso também abrange técnicas mais avançadas de criptografia de banco de dados, como criptografia em nível de coluna e em nível de linha, oferecendo muito mais controle quanto a exatamente quais dados estão sendo protegidos.

Seus requisitos gerais de política e conformidade, a confidencialidade dos dados sendo armazenados e os requisitos de desempenho de suas cargas de trabalho devem determinar quais ativos exigem criptografia.

### <a name="assumptions-about-encrypting-data-at-rest"></a>Suposições sobre a criptografia de dados em repouso

A criptografia de dados em repouso pressupõe o seguinte:

- Você está armazenando dados que não são destinados ao uso público.
- Suas cargas de trabalho podem aceitar o custo de latência de criptografia de disco.

### <a name="data-in-use"></a>Dados em uso

A criptografia de dados em uso envolve a proteção de dados em armazenamento não persistente, como memória RAM ou caches de CPU. O uso de tecnologias, como criptografia de memória cheia e tecnologias de enclave, como as SGXs (Extensões de proteção segura) da Intel. Isso também inclui técnicas de criptografia, como a criptografia homomórfica, a qual pode ser usada para criar ambientes de execução confiáveis e seguros.

**Suposições sobre a criptografia de dados em uso:** A criptografia de dados em uso pressupõe o seguinte:

- Você deve manter a propriedade dos dados separada da plataforma de nuvem subjacente em todos os momentos, incluindo no nível de memória RAM e CPU.

## <a name="learn-more"></a>Saiba mais

Para obter mais informações sobre a criptografia e o gerenciamento de chaves no Azure, veja:

- [Visão geral da criptografia do Azure](https://docs.microsoft.com/azure/security/security-azure-encryption-overview). Uma descrição detalhada de como o Azure usa a criptografia para proteger os dados em repouso e em trânsito.
- [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-overview). O Key Vault é o sistema de gerenciamento de chave primária para armazenar e gerenciar chaves de criptografia, segredos e certificados no Azure.
- [Melhores práticas de segurança de dados e criptografia do Azure](https://docs.microsoft.com/azure/security/azure-security-data-encryption-best-practices). Uma discussão das melhores práticas de segurança e criptografia de dados do Azure.
- [Computação confidencial no Azure](https://azure.microsoft.com/solutions/confidential-compute). A iniciativa de computação confidencial do Azure fornece ferramentas e tecnologias para criar ambientes confiáveis de execução ou outros mecanismos de criptografia para proteger os dados em uso.

## <a name="next-steps"></a>Próximas etapas

Criptografia é apenas um dos componentes fundamentais da infraestrutura que exigem decisões de arquitetura durante um processo de adoção da nuvem. Acesse a [visão geral de guias de decisão](../index.md) para saber mais sobre padrões ou modelos alternativos usados ao tomar decisões de design para outros tipos de infraestrutura.

> [!div class="nextstepaction"]
> [Guias de decisão de arquitetura](../index.md)
