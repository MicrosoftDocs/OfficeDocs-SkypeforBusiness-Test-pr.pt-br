---
title: Entendendo associações do Chat Persistente
TOCTitle: Entendendo associações do Chat Persistente
ms:assetid: 900392d6-6e9f-4dae-93d6-39d7474409ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398730(v=OCS.15)
ms:contentKeyID: 49307436
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Entendendo associações do Chat Persistente

 

_**Tópico modificado em:** 2013-02-22_

O acesso do usuário às salas do Chat Persistente é gerenciado por associação; os usuários devem ser membros de uma sala de chat para poder postar e ler mensagens. Apenas **Apresentadores** que projetaram a afiliação com salas de chat têm permissão para usar a **publicação às salas de auditório**. Um auditório é um tipo de sala de chat (a outra é a **Normal**), onde apenas Apresentadores podem postar e todos podem ler.

Além disso, Chat Persistente as salas operam sob as regras de uma categoria. Para obter detalhes sobre categorias, consulte [Gerenciando categotias, salas e suplementos no Lync Server 2013](lync-server-2013-managing-categories-rooms-and-add-ins.md), e também as seções "Como o escopo de categorias funciona" e "Estratégias de categorias de sala", posteriormente neste tópico.

Um administrador do Chat Persistente pode criar e gerenciar as categorias de sala de chat. Como parte da criação e gerenciamento das categorias da sala de chat, o administrador do Chat Persistente pode configurar princípios ( Serviços de Domínio Active Directory grupos, contêineres e usuários) que têm acesso para serem membros ou criadores de salas de chat de uma categoria específica.

## Serviços de Domínio Active Directory e Chat Persistente

O Servidor de Chat Persistente confia no Active Directory para o pool de usuários internos do Chat Persistente. Depois de instalar o Chat Persistente (cliente), você poderá adicionar domínios de usuários e grupos ao escopo à categoria de sala. Você poderá depois adicionar esses usuários e grupos aos membros de suas categorias de salas.

> [!IMPORTANT]  
> É necessário garantir que não existam nomes duplicados para usuários que desejam fazer alterações nas salas do Chat Persistente. Se nomes de usuários duplicados existirem, altere-os para nomes diferentes para desbloquear os usuários para fazer essas alterações. Se o usuário tiver nomes duplicados no Active Directory e tentar fazer alterações em suas salas, uma mensagem de erro será exibida avisando ao usuário para entrar em contato com o administrador para solucionar o caso.

## Como funciona a associação de categoria

Uma categoria especifica todos os usuários e grupos que podem ser membros na lista de associação de uma sala de Chat Persistente na categoria, com base na propriedade **Membros Permitidos**. Por exemplo, se você configurar a categoria **Membros Permitidos** para contoso.com, é possível adicionar qualquer grupo ou usuário em *Contoso* como membro nas salas de chat na categoria. Se você configurar **Membros Permitidos** na categoria *Vendas*, apenas grupos e usuários desta lista de distribuição poderão ser adicionados como membros nas salas de chat na categoria. Da mesma forma, a propriedade **Criadores** permite que você controle quem pode criar salas de chat na categoria. Após a criação da sala de chat, qualquer pessoa do grupo **Membros Permitidos** pode ser designada como **Gerente** para as operações de gerenciamento contínuas nas salas (por exemplo, alterações e aprovações de associação).

Definindo **Membros Permitidos** e **Criadores** na categoria com os seguintes benefícios:

  - Todas as salas de chat nesta categoria estão sujeitas às restrições definidas no nível da categoria. Você pode usar isso para segregar as salas de chat baseando-se nas necessidades de negócios e políticas de acesso.

  - Um usuário membro na lista **Criadores** pode criar novas salas de chat naquela categoria. Se você desejar implantar um sistema onde um número restrito de pessoas na organização possa criar salas de chat, este controle pode ser usado para atender a essa exigência.

## Estratégias de categoria de salas

Os **Membros Permitidos** de uma categoria devem incluir todos os usuários que usarão qualquer sala do Chat Persistente nesta categoria. Dependendo dos seus requisitos para proteger dados empresariais e garantir o nível correto de acesso, você poderá definir uma ou mais categorias para especificar quem pode pesquisar e participar das salas. Se desejar permitir apenas um conjunto específico de usuários (um helpdesk central ou apenas funcionários de tempo integral) para criar salas, você pode fazer o escopo dos **Criadores** de uma categoria para satisfazer esse requisito.

As categorias podem ser também usadas para criar barreiras éticas. As barreiras éticas evitam qualquer conflito de interesses em uma organização. Por exemplo, um administrador pode criar salas de chat em uma categoria apenas para comerciantes, ao passo que as salas de chat em outra categoria podem ser usadas somente por analistas.

> [!NOTE]  
> No Lync Server 2013, Servidor de Chat Persistente, nós não suportamos acesso a usuários federados. Se houver chats de usuários federados em versões anteriores do Servidor de Chat Persistente, eles serão migrados. Os usuários federados são adicionados como princípios desativados.

## Como estreitar o escopo para grupos de usuário

Ao adicionar um domínio ao escopo da categoria raiz, os grupos de usuários cujos objetos de grupo estão contidos nesse domínio serão disponibilizados a você para serem especificados como membros das categorias e salas de chat no servidor.

Recomendamos, como regra geral, que você use contêineres do Active Directory, como domínios e unidades organizacionais para definir os **Membros Permitidos** e **Criadores** de uma categoria. Você pode adicionar objetos de qualquer domínio a uma lista de **Membros Permitidos** ou **Criadores**. Apenas objetos dentro da lista de **Membros Permitidos** ou **Criadores** pode ser adicionada a salas sob esta categoria.

