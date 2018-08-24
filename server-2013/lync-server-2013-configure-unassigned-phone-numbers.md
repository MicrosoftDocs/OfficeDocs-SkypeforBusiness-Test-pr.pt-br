---
title: Configurar números telefônicos não atribuídos
TOCTitle: Configurar números telefônicos não atribuídos
ms:assetid: a0650659-dce7-455f-8977-02454bbfa400
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182559(v=OCS.15)
ms:contentKeyID: 49307637
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar números telefônicos não atribuídos

 

_**Tópico modificado em:** 2012-11-01_

O Lync Server permite que você configure o que acontece com chamadas recebidas para números de telefone que são válidos para a sua organização, mas que não estão atribuídos a um usuário ou telefone. Para configurar o tratamento de tais chamadas, configure uma tabela de números não atribuídos. Você pode usar a tabela para rotear as chamadas a um Aplicativo Comunicado ou servidor UM do Exchange.

Como configurar a tabela de números não atribuídos dependerá de como você deseja usá-la. Você pode configurar a tabela com todas as extensões válidas para a sua organização, somente com extensões não atribuídas ou com uma combinação de ambos os tipos de números. A tabela de números não atribuídos pode incluir ambos, números atribuídos e não atribuídos, mas será invocada somente quando um chamador discar um número que não esteja atribuído atualmente. Se você incluir todas as extensões válidas na tabela de números não atribuídos, pode especificar a ação que ocorre sempre que alguém sair da sua organização, sem a necessidade de reconfigurar a tabela. Se você incluir extensões não atribuídas na tabela, pode ajustar a ação que ocorre para números específicos. Por exemplo, se você alterar a extensão para seu serviço de atendimento ao cliente, poderá incluir o número do atendimento ao cliente antigo na tabela e atribuí-lo a um comunicado que fornece o novo número.

> [!IMPORTANT]  
> Antes de configurar a tabela de números não atribuídos, você deverá definir um ou mais comunicados ou ter configurado um Atendedor Automático do UM do Exchange. Para obter detalhes sobre a criação de comunicados, consulte <a href="lync-server-2013-create-an-announcement.md">Criar um comunicado no Lync Server 2013</a>. Para ver se você configurou o UM do Exchange, execute o cmdlet <strong>Get-CsExUmContact</strong>. Para obter detalhes, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExUmContact">Get-CsExUmContact</a>.

## Nesta seção

  - [Criar ou modificar um intervalo de números não atribuídos no Lync Server 2013](lync-server-2013-create-or-modify-an-unassigned-number-range.md)

  - [Excluir um intervalo de número não atribuído no Lync Server 2013](lync-server-2013-delete-an-unassigned-number-range.md)

