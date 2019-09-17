---
title: Motivações da linha de base de identidade e riscos de negócios
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivações da linha de base de identidade e riscos de negócios
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 9c838063c77b02af4ec86187854a15d93b2998ef
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026850"
---
# <a name="identity-baseline-motivations-and-business-risks"></a>Motivações da linha de base de identidade e riscos de negócios

Este artigo aborda os motivos que os clientes normalmente adotam uma disciplina de Linha de base de identidade dentro de uma estratégia de governança de nuvem. Também fornece alguns exemplos de riscos de negócios que conduzem as instruções de política.

<!-- markdownlint-disable MD026 -->

## <a name="is-identity-baseline-relevant"></a>É uma Linha de base de identidade relevante?

Diretórios locais tradicionais são projetados para permitir que as empresas estritamente controlem permissões e políticas para os usuários, grupos e funções dentro de suas redes internas e datacenters. Geralmente, isso serve para dar suporte a implementações de único locatário, com os serviços aplicáveis somente dentro do ambiente local.

Os serviços de identidade de nuvem destinam-se a expandir a autenticação de uma organização e acessar recursos de controle para a internet. Eles oferecem suporte a multilocação e podem ser usados para gerenciar usuários e política de acesso em aplicativos de nuvem e implantações. Plataformas de nuvem pública têm alguma forma de serviços de identidade nativa de nuvem com suporte a tarefas de gerenciamento e implantação e podem [variar os níveis de integração](../../decision-guides/identity/index.md) com as soluções de identidade locais existentes. Todos esses recursos podem resultar na política de identidade de nuvem que está sendo mais complicada do que suas soluções locais tradicionais exigem.

A importância da disciplina da Linha de base de identidade para sua implantação de nuvem dependerá do tamanho da sua equipe e precisará integrar sua solução de identidade baseada em nuvem com um serviço de identidade no local. As implantações de teste iniciais podem não exigir muito a respeito da organização do usuário ou de gerenciamento, mas à medida que o seu acervo de nuvem amadurece, provavelmente será necessário dar suporte ao gerenciamento centralizado e integração organizacional mais complicada.

## <a name="business-risk"></a>Riscos de negócios

A disciplina de Linha de base de identidade tenta abordar os riscos comerciais principais relacionados aos serviços de identidade e controle de acesso. Trabalhar com seus negócios para identificar esses riscos e monitorar cada um deles para relevância como planejar e implementar suas implantações de nuvem.

Os riscos serão diferentes entre a organização, mas os seguintes servem como riscos comuns relacionados à identidade que você pode usar como ponto de partida para discussões em sua equipe de governança de nuvem:

- **Acesso não autorizado.** Dados confidenciais e recursos que podem ser acessados por usuários não autorizados podem levar a vazamentos de dados ou interrupções de serviço, violando o perímetro de segurança da sua organização e pondo os negócios em risco ou processos judiciais.
- **Ineficiência devido a várias soluções de identidade.** As organizações com vários locatários de serviços de identidade podem exigir várias contas para os usuários. Isso pode levar a ineficiência para usuários que precisam se lembrar de vários conjuntos de credenciais e a área de TI no gerenciamento de contas em vários sistemas. Se as atribuições de acesso do usuário não forem atualizadas em soluções de identidade, uma vez que equipes e metas de negócios mudam, seus recursos de nuvem podem estar vulneráveis a acesso não autorizado ou usuários que não podem acessar os recursos necessários.
- **Incapacidade de compartilhar recursos com parceiros externos.** Dificuldade para adição de parceiros comerciais externos às suas soluções de identidade existente pode impedir a comunicação eficiente de recursos de compartilhamento e de negócios.
- **Dependências de identidade local.** Mecanismos de autenticação herdados ou autenticação de multifator de terceiros pode não estar disponível na nuvem, exigindo migrar as cargas de trabalho para serem alteradas ou serviços de identidade adicional a serem implantado para a nuvem. Nenhum dos dois requisitos pode atrasar ou evitar a migração e aumentar os custos.

## <a name="next-steps"></a>Próximas etapas

Usando o [modelo de gerenciamento de nuvem](./template.md), documente os riscos de negócios que provavelmente serão introduzidos pelo plano de adoção de nuvem atual.

Quando um entendimento dos riscos de negócios realista é estabelecido, a próxima etapa é documentar a tolerância do negócio quanto a risco e os indicadores e métricas de chave para monitorar essa tolerância.

> [!div class="nextstepaction"]
> [Entenda os indicadores, métricas e tolerância a risco](./metrics-tolerance.md)
