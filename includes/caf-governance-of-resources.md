<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->
> [!NOTE]
>No caso de alterações aos seus requisitos comerciais, os grupos de gerenciamento do Azure permitem que você reorganize com facilidade suas atribuições de grupo de assinaturas e hierarquia de gerenciamento. No entanto, lembre-se de que as atribuições de função e política aplicadas a um grupo de gerenciamento são herdadas por todas as assinaturas abaixo na hierarquia de grupo. Se você planeja reatribuir as assinaturas entre grupos de gerenciamento, esteja ciente de qualquer alteração de atribuição de política e a função que possa resultar. Confira a [documentação dos grupos de gerenciamento do Azure](/azure/governance/management-groups) para obter mais informações.

### <a name="governance-of-resources"></a>Governança de recursos

Um conjunto de políticas globais e funções de RBAC fornecerá um nível de linha de base de imposição de governança. Para atender aos requisitos da política da equipe de Governança de Nuvem, a implementação do MVP de governança exige a conclusão das seguintes tarefas:

1. Identificar as definições do Azure Policy necessárias para impor os requisitos comerciais. Isso pode incluir o uso de definições internas e a criação de definições personalizadas.
2. Criar uma definição de blueprint usando essa política interna e personalizada e as atribuições de função necessárias para o MVP de governança.
3. Aplicar políticas e configuração globalmente atribuindo a definição de blueprint a todas as assinaturas.

#### <a name="identify-policy-definitions"></a>Identificar as definições de política

O Azure fornece várias políticas internas e definições de função que você pode atribuir a qualquer grupo de gerenciamento, assinatura ou grupo de recursos. Muitos requisitos comuns de governança podem ser gerenciados usando definições internas. No entanto, é provável que você também precise criar definições de política personalizada para lidar com seus requisitos específicos.

Definições de políticas personalizadas são salvas em um grupo de gerenciamento ou em uma assinatura e são herdadas por meio da hierarquia de grupo de gerenciamento. Se a localização para salvar uma definição de política for um grupo de gerenciamento, essa definição de política estará disponível para ser atribuída a qualquer uma das assinaturas ou dos grupos de gerenciamento filho desse grupo.

Como as políticas necessárias para dar suporte ao MVP de governança destinam-se a serem aplicadas a todas as assinaturas atuais, os seguintes requisitos comerciais serão implementados com uma combinação de definições internas e personalizadas criadas no grupo de gerenciamento raiz:

1. Restrinja a lista de atribuições de função disponíveis a um conjunto de funções internas do Azure autorizadas por sua equipe de Governança de Nuvem. Isso exigirá uma [definição de política personalizada](https://github.com/Azure/azure-policy/tree/master/samples/Authorization/allowed-role-definitions). 
2. Exija o uso das seguintes marcações em todos os recursos: *Unidade de Cobrança/Departamento*, *Geografia*, *Classificação de Dados*, *Nível de Importância*, *SLA*, *Ambiente*, *Arquétipo do Aplicativo*, *Aplicativo* e *Proprietário do Aplicativo*. Isso pode ser tratado usando a definição interna "Exigir a marca especificada".
3. Exija que a marca *Aplicativo* para recursos deva corresponder ao nome do grupo de recursos relevante. Isso pode ser tratado usando a definição interna "Exigir a marca e seu valor'".

Para obter informações sobre como definir as políticas personalizadas, veja a [documentação do Azure Policy](/azure/governance/policy/tutorials/create-custom-policy-definition). Para obter instruções e exemplos de políticas personalizadas, veja o [site de exemplos do Azure Policy](/azure/governance/policy/samples) e o respectivo [repositório do GitHub](https://github.com/Azure/azure-policy).

#### <a name="assign-azure-policy-and-rbac-roles-using-azure-blueprints"></a>Atribuir funções do Azure Policy e do RBAC usando o Azure Blueprints

As políticas do Azure podem ser atribuídas no nível do grupo de recursos, da assinatura e do grupo de gerenciamento, assinatura e podem ser incluídas nas definições do [Azure Blueprints](/azure/governance/blueprints/overview). Embora os requisitos de política definidos neste MVP de governança se apliquem a todas as assinaturas atuais, é muito provável que as futuras implantações exijam exceções ou políticas alternativas. Como resultado, a atribuição de política usando grupos de gerenciamento, com todas as assinaturas filho herdando essas atribuições, poderá não ser flexível o suficiente para dar suporte a esses cenários.

O Azure Blueprints permite a atribuição consistente de política e funções, a aplicação de modelos do Resource Manager e a implantação de grupos de recursos em várias assinaturas. Como ocorre com definições de política, definições de blueprint são salvas em grupos de gerenciamento ou em assinaturas e estão disponíveis por meio de herança para qualquer filho na hierarquia de grupo de gerenciamento.

A equipe de Governança de Nuvem decidiu que a imposição de atribuições obrigatórias do Azure Policy e RBAC entre assinaturas será implementada por meio do Azure Blueprints e artefatos associados:

1. No grupo de gerenciamento raiz, crie uma definição de blueprint chamada `governance-baseline`.
2. Adicione os seguintes artefatos do blueprint à definição de blueprint:
    1. Atribuições de política para as definições do Azure Policy personalizadas determinadas na raiz do grupo de gerenciamento.
    2. Definições do grupo de recursos para quaisquer grupos necessários em assinaturas criadas ou regidas pelo MVP de Governança.
    3. Atribuições de função padrão necessárias nas assinaturas criadas ou regidas pelo MVP de Governança.
3. Publique a definição do blueprint.
4. Atribua a definição de blueprint `governance-baseline` a todas as assinaturas.

Veja a [documentação do Azure Blueprints](/azure/governance/blueprints/overview) para obter mais informações sobre como criar e usar definições de blueprint.

### <a name="secure-hybrid-vnet"></a>VNET híbrida segura

Assinaturas específicas costumam exigir algum nível de acesso aos recursos locais. Isso é comum em cenários de migração ou de desenvolvimento em que os recursos dependentes residem no datacenter local.

Até que a confiança no ambiente de nuvem seja totalmente estabelecida, é importante controlar e monitorar rigidamente qualquer permissão de comunicação entre as cargas de trabalho de nuvem e o ambiente local e que a rede local esteja protegida contra potencial acesso não autorizado de recursos baseados em nuvem. Para dar suporte a esses cenários, o MVP de governança adiciona as seguintes melhores práticas:

1. Estabeleça uma VNET híbrida de nuvem segura.
    1. A [arquitetura de referência de VPN](/azure/architecture/reference-architectures/hybrid-networking/vpn) estabelece um padrão e um modelo de implantação para criar um Gateway de VPN no Azure.
    2. Confirme se os mecanismos de gerenciamento de segurança e tráfego locais tratam as redes de nuvem conectadas como não confiáveis. Recursos e serviços hospedados na nuvem devem ter apenas acesso a serviços autorizados locais.
    3. Valide que o dispositivo de borda local no datacenter local é compatível com [requisitos do Gateway de VPN do Azure](/azure/vpn-gateway/vpn-gateway-about-vpn-devices) e está configurado para acessar a Internet pública.
1. No grupo de gerenciamento raiz, criar uma segunda definição de blueprint chamada `secure-hybrid-vnet`.
    1. Adicione o modelo do Resource Manager do Gateway de VPN como um artefato à definição de blueprint.
    2. Adicione o modelo do Resource Manager da rede virtual como um artefato à definição de blueprint.
    3. Publique a definição do blueprint.
1. Atribuir a definição de blueprint `secure-hybrid-vnet` a qualquer assinatura que exija conectividade local. Essa definição deve ser atribuída além da definição de blueprint de `governance-baseline`.

Uma das principais preocupações manifestadas pelas equipes de segurança de TI e governança tradicionais é o risco de que a adoção de nuvem em estágio inicial comprometa os ativos existentes. A abordagem acima permite que as equipes de adoção de nuvem criem e migrem soluções híbridas com risco reduzido para ativos locais. Conforme a confiança no ambiente de nuvem aumenta, evoluções posteriores podem remover essa solução temporária.

> [!NOTE]
> O descrito acima é um ponto de partida para criar rapidamente um MVP de governança de linha de base. Este é apenas o começo do percurso de governança. Mais evolução será necessária na medida em que a empresa continuar a adotar a nuvem e assumir mais riscos nas seguintes áreas:
>
> - Cargas de trabalho críticas
> - Dados protegidos
> - Gerenciamento de custo
> - Cenários multinuvem
>
> Além disso, os detalhes específicos deste MVP são baseados no exemplo de percurso de uma empresa fictícia, descrito nos artigos a seguir. É altamente recomendável familiarizar-se com os outros artigos desta série, antes de implementar essa melhor prática.
