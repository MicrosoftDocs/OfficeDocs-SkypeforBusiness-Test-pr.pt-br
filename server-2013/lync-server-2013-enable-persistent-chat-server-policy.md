---
title: 'Lync Server 2013: Habilitar política de Servidor de Chat Persistente'
TOCTitle: Habilitar política de Servidor de Chat Persistente
ms:assetid: 87063d6c-2e38-4970-b76d-2aa15f0de29e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205056(v=OCS.15)
ms:contentKeyID: 49307359
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar política de Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

No Painel de Controle do Lync Server 2013, é possível usar a página de **Chat PersistentePolítica** do grupo do **Chat Persistente** para gerenciar políticas em níveis global, de pool, de site ou de usuário, incluindo a configuração da política global padrão e a criação de uma ou mais políticas adicionais de usuários e sites para sua implantação. Se o usuário estiver habilitado para Servidor de Chat Persistente de acordo com a política, o ambiente do Servidor de Chat Persistente será exibido no cliente do Lync 2013.

> [!NOTE]  
> Na topologia, as políticas de site do Servidor de Chat Persistente aplicam-se globalmente, por pool de usuários, por site de usuários ou por usuário.

O política global é criada automaticamente quando o Servidor de Chat Persistente é implantado. É possível configurá-la, mas não excluí-la. Como a política global aplica-se a todos os usuários, não é preciso configurá-la para cada usuário.

Você pode criar e configurar diversas políticas de site e usuário, o que, com a política global, habilita os usuários para Servidor de Chat Persistente. As políticas de pool e de site do Servidor de Chat Persistente substituem a política global do Servidor de Chat Persistente, mas somente para usuários do site em questão. As políticas de usuário substituem as políticas globais, de pool e de site para os usuários aos quais são atribuídas.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.

## Nesta seção

  - [Configurar a política global para Chat Persistente no Lync Server 2013](lync-server-2013-configure-the-global-policy-for-persistent-chat.md)

  - [Criar uma política de site para chat persistente no Lync Server 2013](lync-server-2013-create-a-site-policy-for-persistent-chat.md)

  - [Criar uma política de usuário para Chat Persistente no Lync Server 2013](lync-server-2013-create-a-user-policy-for-persistent-chat.md)

  - [Aplicar uma política de Chat Persistente a um usuário ou grupo de usuários no Lync Server 2013](lync-server-2013-apply-a-persistent-chat-policy-to-a-user-or-user-group.md)

