<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="dependent-decisions"></a>Decisões dependentes

As decisões a seguir são provenientes de equipes fora da equipe de governança de nuvem. A implementação de cada um será proveniente dessas mesmas equipes. No entanto, a equipe de governança de nuvem é responsável pela implementação de uma solução para validar que essas implementações sejam aplicadas consistentemente.

### <a name="identity-baseline"></a>Linha de base de identidade

A linha de base de identidade é o ponto de partida fundamental para todas as governança. Antes de tentar aplicar a governança, a identidade deve ser estabelecida. A estratégia de identidade estabelecida será então imposta pelas soluções de governança.
Neste guia de governança, a equipe de gerenciamento de identidade implementa o padrão de **[sincronização de diretórios](~/decision-guides/identity/index.md#directory-synchronization)** :

- O RBAC será fornecido pelo Azure Active Directory (Azure AD), usando a sincronização de diretório ou o "mesmo logon" que foi implementado durante a migração da empresa para o Office 365. Para obter diretrizes de implementação, consulte [arquitetura de referência para a integração do Azure ad](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad).
- O locatário do Azure AD também controlará a autenticação e o acesso para os ativos implantados no Azure.

No MVP de governança, a equipe de governança impedirá a aplicação do locatário replicado por meio de ferramentas de governança de assinatura, discutidas posteriormente neste artigo. Em iterações futuras, a equipe de governança também pode impor ferramentas avançadas no Azure AD para estender esse recurso.

### <a name="security-baseline-networking"></a>Linha de base de segurança: rede

A rede definida pelo software é um aspecto inicial importante da linha de base de segurança. Estabelecer o MVP de governança depende das decisões iniciais da equipe de gerenciamento de segurança para definir como as redes podem ser configuradas com segurança.

Devido à falta de requisitos, a segurança de ti está reproduzindo segurança e requer um padrão de **[DMZ de nuvem](~/decision-guides/software-defined-network/cloud-dmz.md)** . Isso significa que a governança das implantações do Azure em si será muito leve.

- As assinaturas do Azure podem se conectar a um datacenter existente via VPN, mas devem seguir todas as políticas de governança de ti locais existentes relativas à conexão de uma zona desmilitarizada a recursos protegidos. Para obter diretrizes de implementação sobre a conectividade VPN, consulte [arquitetura de referência de VPN](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/vpn).
- As decisões relacionadas à sub-rede, ao firewall e ao roteamento estão sendo adiadas atualmente para cada cliente potencial de aplicativo/carga de trabalho.
- Uma análise adicional é necessária antes da liberação de qualquer dado protegido ou de cargas de trabalho de missão crítica.

Nesse padrão, as redes de nuvem só podem se conectar a recursos locais por meio de uma VPN existente que seja compatível com o Azure. O tráfego nessa conexão será tratado como qualquer tráfego proveniente de uma zona desmilitarizada. Considerações adicionais podem ser necessárias no dispositivo de borda local para controlar com segurança o tráfego do Azure.

A equipe de governança de nuvem convidou proativamente membros das equipes de rede e de segurança de ti para reuniões regulares, a fim de se manter à frente das demandas e dos riscos de rede.

### <a name="security-baseline-encryption"></a>Linha de base de segurança: criptografia

A criptografia é outra decisão fundamental na disciplina de linha de base de segurança. Como a empresa atualmente ainda não armazena nenhum dado protegido na nuvem, a equipe de segurança decidiu um padrão menos agressivo para a criptografia.
Neste ponto, um **[padrão de nuvem nativa para criptografia](~/decision-guides/encryption/index.md#key-management)** é sugerido, mas não é necessário para qualquer equipe de desenvolvimento.

- Nenhum requisito de governança foi definido com relação ao uso da criptografia, pois a política corporativa atual não permite dados críticos ou protegidos na nuvem.
- Serão necessárias análises adicionais antes de liberar dados protegidos ou cargas de trabalho críticas.

## <a name="policy-enforcement"></a>Aplicação de políticas

A primeira decisão a tomar em relação à aceleração da implantação é o padrão para a imposição. Nesta narra, a equipe de governança decidiu implementar o padrão de **[imposição automatizada](~/decision-guides/policy-enforcement/index.md#automated-enforcement)** .

- A central de segurança do Azure será disponibilizada para as equipes de segurança e identidade para monitorar os riscos de segurança. As duas equipes também têm probabilidade de usar a central de segurança para identificar novos riscos e aprimorar a política corporativa.
- O RBAC é necessário em todas as assinaturas para controlar a imposição de autenticação.
- Azure Policy será publicado em cada grupo de gerenciamento e aplicado a todas as assinaturas. No entanto, o nível de políticas que estão sendo impostas será muito limitado neste MVP de governança inicial.
- Embora os grupos de gerenciamento do Azure estejam sendo usados, uma hierarquia relativamente simples é esperada.
- Os planos gráficos do Azure serão usados para implantar e atualizar assinaturas aplicando requisitos de RBAC, modelos do Resource Manager e Azure Policy em grupos de gerenciamento.

## <a name="applying-the-dependent-patterns"></a>Aplicando os padrões dependentes

As decisões a seguir representam os padrões a serem aplicados por meio da estratégia de imposição de política acima:

**Linha de base de identidade.** Os planos gráficos do Azure definirão os requisitos de RBAC em um nível de assinatura para garantir que a identidade consistente esteja configurada para todas as assinaturas.

**Linha de base de segurança: rede.** A equipe de governança de nuvem mantém um modelo do Resource Manager para estabelecer um gateway de VPN entre o Azure e o dispositivo VPN local. Quando uma equipe de aplicativo exigir uma conexão VPN, a equipe de governança de nuvem aplicará o modelo do Resource Manager do gateway por meio dos planos gráficos do Azure.

**Linha de base de segurança: criptografia.** Neste ponto, nenhuma imposição de política é necessária nessa área. Isso será revisitado durante as iterações posteriores.
