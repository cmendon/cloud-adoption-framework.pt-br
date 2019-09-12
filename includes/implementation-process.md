<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="dependent-decisions"></a>Decisões dependentes

As decisões a seguir são provenientes de equipes fora da equipe de governança de nuvem. A implementação de cada uma decorrerá dessas mesmas equipes. No entanto, a equipe de governança de nuvem é responsável pela implementação de uma solução para validar que essas implementações sejam aplicadas consistentemente.

### <a name="identity-baseline"></a>Linha de base de identidade

A Linha de Base da Identidade é o ponto de partida fundamental para toda a governança. A identidade deverá ser estabelecida antes de tentar aplicar a governança. Em seguida, a estratégia de identidade estabelecida será aplicada pelas soluções de governança.
Neste guia de governança, a equipe de gerenciamento de identidade implementa o padrão de **[sincronização de diretórios](/azure/architecture/cloud-adoption/decision-guides/identity/overview#directory-synchronization)** :

- O RBAC será fornecido pelo AD (Azure Active Directory), usando a sincronização de diretório ou o "Mesmo Logon" que foi implementado durante a migração da empresa para o Office 365. Para obter as diretrizes de implementação, consulte [Arquitetura de referência para integração do Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
- O locatário do Azure AD também governará a autenticação e o acesso de ativos implantados no Azure.

No MVP de governança, a equipe de governança impedirá a aplicação do locatário replicado por meio de ferramentas de governança de assinatura, discutidas posteriormente neste artigo. Em iterações futuras, a equipe de governança também pode impor ferramentas avançadas no Azure AD para estender esse recurso.

### <a name="security-baseline-networking"></a>Linha de Base de Segurança: Rede

A Rede Definida pelo Software é um aspecto inicial importante da Linha de Base de Segurança. Estabelecer o MVP de governança depende de decisões antecipadas da equipe de Gerenciamento de Segurança para definir como as redes podem ser configuradas com segurança.

Devido à falta de requisitos, a segurança de ti está jogando em segurança e exigiu um padrão de **[DMZ de nuvem](/azure/architecture/cloud-adoption/decision-guides/software-defined-network/cloud-dmz)** . Isso significa que a governança das implantações do Azure será muito leve.

- As assinaturas do Azure podem se conectar a um datacenter existente via VPN, mas devem seguir todas as políticas de governança de ti locais existentes relativas à conexão de uma zona desmilitarizada a recursos protegidos. Para obter diretrizes sobre a implementação de conectividade VPN, consulte [Arquitetura de referência de VPN](/azure/architecture/reference-architectures/hybrid-networking/vpn).
- Decisões relacionadas a sub-rede, firewall e roteamento estão sendo adiadas para cada cliente potencial de carga de trabalho/aplicativo.
- Uma análise adicional será necessária antes da liberação de dados protegidos ou cargas de trabalho críticas.

Nesse padrão, as redes de nuvem só podem se conectar a recursos locais por meio de uma VPN existente que seja compatível com o Azure. O tráfego nessa conexão será tratado como qualquer tráfego proveniente de uma zona desmilitarizada. Considerações adicionais poderão ser necessárias no dispositivo de borda local para manipular com segurança o tráfego do Azure.

A equipe de governança de nuvem convidou proativamente membros das equipes de rede e de segurança de ti para reuniões regulares, a fim de se manter à frente das demandas e dos riscos de rede.

### <a name="security-baseline-encryption"></a>Linha de Base de Segurança: Criptografia

A criptografia é outra decisão fundamental dentro da disciplina de Linha de Base de Segurança. Como a empresa atualmente ainda não armazena dados protegidos na nuvem, a Equipe de Segurança decidiu um padrão menos agressivo de criptografia.
Neste ponto, um **[padrão de nuvem nativa para criptografia](/azure/architecture/cloud-adoption/decision-guides/encryption/overview#key-management)** é sugerido, mas não é necessário para qualquer equipe de desenvolvimento.

- Nenhum requisito de governança foi definido relacionado ao uso de criptografia porque a atual política corporativa não permite dados protegidos ou críticos na nuvem.
- Serão necessárias análises adicionais antes de liberar dados protegidos ou cargas de trabalho críticas.

## <a name="policy-enforcement"></a>Imposição de política

A primeira decisão ser tomada em relação à Aceleração de Implantação é o padrão da imposição. Nesta narra, a equipe de governança decidiu implementar o padrão de **[imposição automatizada](/azure/architecture/cloud-adoption/decision-guides/policy-enforcement/overview#automated-enforcement)** .

- A Central de Segurança do Azure será disponibilizada às equipes de segurança e identidade para monitorar os riscos de segurança. As duas equipes também têm probabilidade de usar a central de segurança para identificar novos riscos e aprimorar a política corporativa.
- O RBAC é obrigatório em todas as assinaturas para governar a imposição de autenticação.
- O Azure Policy será publicado para cada grupo de gerenciamento e aplicado a todas as assinaturas. No entanto, o nível de políticas sendo aplicadas será muito limitado neste MVP de Governança inicial.
- Embora os grupos de gerenciamento do Azure estejam sendo utilizados, espera-se uma hierarquia relativamente simples.
- O Azure Blueprints será utilizado para implantar e atualizar assinaturas, aplicando requisitos de RBAC, Modelos do Resource Manager e Azure Policy nos grupos de gerenciamento.

## <a name="applying-the-dependent-patterns"></a>Aplicar padrões dependentes

As decisões a seguir representam os padrões a serem impostos por meio da estratégia de imposição da política descrita acima:

**Linha de base de identidade.** O Azure Blueprints definirá os requisitos de RBAC em um nível de assinatura para garantir que a identidade consistente seja configurada para todas as assinaturas.

**Linha de Base de Segurança: Rede.** A equipe de governança de nuvem mantém um modelo do Resource Manager para estabelecer um gateway de VPN entre o Azure e o dispositivo VPN local. Quando uma equipe de aplicativo exigir uma conexão VPN, a equipe de governança de nuvem aplicará o modelo do Resource Manager do gateway por meio dos planos gráficos do Azure.

**Linha de Base de Segurança: Encripta.** Neste ponto, nenhuma imposição de política é necessária nessa área. Isso será revisitado durante as iterações posteriores.
