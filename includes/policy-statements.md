<!-- TEMPLATE FILE - DO NOT ADD METADATA -->
<!-- markdownlint-disable MD002 MD041 -->

## <a name="policy-statements"></a>Declarações de políticas

As instruções de política a seguir estabelecem os requisitos necessários para corrigir os riscos definidos. Essas políticas definem os requisitos funcionais para a governança MVP. Cada uma será representada na implementação da governança de MVP.

Gerenciamento de Custos:

- Para fins de acompanhamento, todos os ativos devem ser atribuídos a um proprietário de aplicativo dentro de uma das funções de negócios principais.
- Quando surgirem preocupações, requisitos adicionais de governança serão estabelecidos com a equipe de finanças.

Linha de Base de Segurança:

- Qualquer ativo implantado na nuvem deve ter uma classificação de dados aprovados.
- Nenhum ativo identificado com um nível protegido de dados pode ser implantado na nuvem, até requisitos de segurança e governança suficientes podem ser aprovados e implementados.
- Até que os requisitos mínimos de segurança de rede possam ser validados e governados, os ambientes de nuvem são vistos como uma zona desmilitarizada e devem atender a requisitos de conexão semelhantes a outros data centers ou redes internas.

Consistência de Recursos:

- Como nenhuma carga de trabalho de missão crítica é implantada neste estágio, não há nenhum SLA, desempenho ou requisitos de BCDR a ser regido.
- Quando as cargas de trabalho de missão crítica são implantadas, os requisitos adicionais de controle serão estabelecidos com operações de TI.

Linha de base de identidade:

- Todos os ativos implantados na nuvem devem ser controlados usando identidades e funções aprovadas pelas políticas de governança atual.
- Todos os grupos que têm privilégios elevados na infraestrutura do Active Directory Domain Services local devem ser mapeados para uma função RBAC aprovada.

Aceleração de implantação:

- Todos os ativos devem ser agrupados e marcados de acordo com o agrupamento definido e estratégias de marcação.
- Todos os ativos devem usar um modelo de implantação aprovado.
- Depois de uma base de governança ser estabelecida para um provedor de nuvem, qualquer ferramenta de implantação deve ser compatível com as ferramentas definidas pela equipe de governança.

## <a name="processes"></a>Processos

Nenhum orçamento foi alocado para a imposição dessas políticas de governança e monitoramento contínuo. Por isso, a equipe de governança de nuvem tem algumas maneiras ad hoc de monitorar a adesão a instruções de política.

- **Faculdade** A equipe de governança de nuvem está investindo tempo para instruir as equipes de adoção de nuvem nos guias de governança que dão suporte a essas políticas.
- **Revisões de implantação:** Antes de implantar qualquer ativo, a equipe de governança de nuvem examinará o guia de governança com as equipes de adoção de nuvem.
