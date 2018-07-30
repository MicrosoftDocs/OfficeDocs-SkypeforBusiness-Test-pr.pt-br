---
title: Usando categorias para administrar o Servidor de Chat Persistente
TOCTitle: Usando categorias para administrar o Servidor de Chat Persistente
ms:assetid: dfcb3ad1-da90-467e-b08c-f4e68673b7b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398988(v=OCS.15)
ms:contentKeyID: 49308351
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando categorias para administrar o Servidor de Chat Persistente

 

_**Tópico modificado em:** 2013-10-01_

Sua implantação do Servidor de Chat Persistente pode hospedar muitas salas de Chat Persistente. As salas de chat podem ser organizadas hierarquicamente em um conjunto de categorias no servidor. Cada sala de chat tem somente uma categoria pai, apesar de as categorias poderem ser aninhadas em outras categorias para formarem uma hierarquia de vários níveis. Essa organização cria uma estrutura útil para identificar conversas baseadas no objetivo comercial e facilita a administração delegada e o gerenciamento simplificado.

> [!NOTE]  
> Apesar de muitos dos recursos de gerenciamento das salas de chat estarem disponíveis em computadores executando o Chat Persistente (cliente do Lync) para o usuário, os Administradores do Chat Persistente (na função <strong>cspersistentchatadministrator</strong>) devem usar o Painel de Controle do Lync Server ou os cmdlets do Windows PowerShell para criar ou gerenciar categorias.

Os administradores do Chat Persistente usam o Painel de Controle do Lync Server ou cmdlets do Windows PowerShell para criar e gerenciar categorias e para projetar acesso para salas de chat de usuários em sua organização.

Gerentes de sala do Chat Persistente, que possuem a capacidade de gerenciar uma ou mais salas de chat, podem usar o cliente do Lync para lançar um aplicativo da Web de gerenciamento de sala para criar e gerenciar salas (ou clientes podem criar soluções personalizadas e fluxos de trabalho a serem invocadas). Os administradores do Chat Persistente também podem usar o Painel de Controle do Lync Server ou cmdlets do Windows PowerShell para criar e gerenciar salas.

> [!NOTE]  
> Uma Chat Persistente sala não pode ter o mesmo nome de uma Chat Persistente categoria.

Os gerentes de sala de chat podem realizar alterações em todas as propriedades de sala de chat, exceto alterar a categoria da sala. Não podem ser restritos a realizar as seguintes ações:

  - Desabilitar uma sala de chat

  - Alterar um nome de sala de chat

  - Alterar a descrição de uma sala de chat

  - Alterar um tipo de sala de chat (Auditório versus Normal)

  - Alterar a privacidade de uma sala (aberta verso fechada verso secreta)

  - Adicionar ou remover membros

  - Adicionar ou remover gerentes de sala de chat

  - Adicionar ou remover um suplemento

  - Alterando as configurações como convites (de acordo com o que é permitido pela categoria)

## Administração delegada

Criar e gerenciar salas do Chat Persistente é muito mais fácil com o uso correto das categorias. Um administrador do Chat Persistente podem definir **AllowedMembers** e **Criadores** para cada categoria e também podem definir as configurações de sala de chat padrão e comportamentos que serão aplicados a todas as salas de chat criadas na categoria. Os administradores do Chat Persistente criam e gerenciam categorias usando o Painel de Controle do Lync Server ou cmdlets do Windows PowerShell.

Usuários, Unidades Organizacionais (OUs) e grupos de usuários identificados como Criadores da categoria são os únicos indivíduos e grupos que porem criar salas na categoria. Após a categoria ser criada, eles podem escolher usuários, OUs e grupos de usuários da lista **AllowedMembers** da categoria como gerentes da sala de chat e membros para gerenciar e participar da sala.

As salas de chat criadas em uma categoria aderem às políticas e configurações forçadas pela categoria (como quem pode se associar à sala, quem pode gerenciar a sala, se os carregamentos de arquivo são permitidos, se os convites foram enviados e assim por diante).

