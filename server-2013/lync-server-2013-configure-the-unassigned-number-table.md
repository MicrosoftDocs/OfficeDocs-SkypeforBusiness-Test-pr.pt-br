---
title: 'Lync Server 2013: Configurar a tabela de número não atribuído'
TOCTitle: Configurar a tabela de número não atribuído
ms:assetid: eaa01986-e92f-4328-acf6-4e46c4306a04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399053(v=OCS.15)
ms:contentKeyID: 49308495
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar a tabela de número não atribuído no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-30_

No Lync Server 2013, é possível especificar o que acontece com as chamadas de entrada para números de telefone que são válidos para a sua organização, mas que não estão atribuídos a um usuário ou telefone. Os chamadores podem ouvir uma mensagem e/ou ser encaminhados para outro destino.

O modo como você configura a tabela de números não atribuída depende de como você deseja usá-la. É possível configurar a tabela com todas as extensões válidas para sua organização, com apenas extensões não atribuídas ou com uma combinação de ambos os tipos de números. A tabela de números não atribuída pode incluir números atribuídos e não atribuídos, mas é chamada somente quando um chamador disca um número que não está atribuído no momento. Se você incluir todas as extensões válidas na tabela de números não atribuída, você poderá especificar a ação que ocorre sempre que alguém deixa sua organização, sem a necessidade de reconfigurar a tabela. Se você incluir extensões não atribuídas na tabela, poderá personalizar a ação que ocorre para números específicos. Por exemplo, se você alterar a extensão para seu atendimento ao cliente, poderá incluir o número antigo de atendimento ao cliente na tabela, e atribui-lo a um anúncio que fornece o novo número.

> [!IMPORTANT]  
> Antes desconfigurar a tabela de números não atribuída, é necessário que Announcements já esteja definido no sistema ou que já haja um atendedor automático do Unificação de Mensagens (UM) do Exchange configurado.


> [!TIP]
> Quando alguém chama um número não atribuído, o Lync Server pesquisa a tabela de número não atribuído do início ao fim e usa o primeiro intervalo correspondente. Portanto, uma ação que você deseja executar como última alternativa deve ser especificada para o último intervalo na tabela.



## Nesta seção

[Criar ou modificar um intervalo de números não atribuídos no Lync Server 2013](lync-server-2013-create-or-modify-an-unassigned-number-range.md) [Criar um comunicado no Lync Server 2013](lync-server-2013-create-an-announcement.md)

