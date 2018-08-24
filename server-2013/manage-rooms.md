---
title: Gerenciar salas
TOCTitle: Gerenciar salas
ms:assetid: d4835cf4-cd09-4769-a08e-e92706861b64
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205292(v=OCS.15)
ms:contentKeyID: 49308218
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar salas

 

_**Tópico modificado em:** 2013-02-21_

Para criar uma nova sala do Servidor de Chat Persistente

    New-CsPersistentChatRoom -Name Foo1 -PersistentChatPoolFqdn client.contoso.com -Category client.contoso.com\Foo [other parameters]

> [!IMPORTANT]  
> -PersistentChatPoolFqdn não é necessário se um dos seguintes for verdadeiro:<ul>
> <li><p>Há apenas um Pool de Servidor de Chat Persistente.</p></li>
> 
> <li><p>Você oferece um FQDN do pool para a categoria.</p></li>
> 
> 
> <li><p>Você oferece um FQDN do pool para adicionar a sala.</p></li></ul>


Para realizar alterações em uma sala do Servidor de Chat Persistente existente

    Set-CsPersistentChatRoom -Identity testCat -Members @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}
    Set-CsPersistentChatRoom -Identity testCat -Managers @{Add="sip:user2@contoso.com"}
    Set-CsPersistentChatRoom -Identity testCat -Presenters @{Add="sip:user1@contoso.com"}

Windows PowerShell: Membros, Gerentes e Apresentadores podem ser definidos simultaneamente. Todos eles devem ser um subconjunto de AllowedMembers menos DeniedMembers da Categoria de host. Uma sala que é type=normal não pode incluir Apresentadores.

## Criar, Obter, Definir, Limpar ou Remover uma sala

Para criar uma nova sala

    New-CsPersistentChatRoom -Name <String> [-PersistentChatPoolFqdn <String>]-Category <String> [-Description <String>] [-Disabled <Switch Parameter>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Switch Parameter>]

Para definir ma sala

    Set-CsPersistentChatRoom -Identity <String> [-Name <String>] [-Category <String>] [-Description <String>] [-Disabled <boolean>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Enum>] [-Members <PSListModifier<String>>] [-Managers <PSListModifier<String>>] [-Presenters <PSListModifier<String>>] [-Force < Switch Parameter >] [-Confirm <Switch Parameter>][-WhatIf <Switch Parameter>]

Para obter uma sala

    Get-CsPersistentChatRoom -Identity <String>

ou

    Get-CsPersistentChatRoom -filter <String> [-PersistentChatPoolFqdn <String>] [-SearchDescription] [-Member <String>] [-Manager <string>] [-Category <string>] [-Addin <string>] [-Disabled <bool>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Type <ChatRoomType> {Normal | Auditorium}] [-Invitations <ChatRoomInvitations> {False | Inherit}] [-ChatContentExceedsMB <int>] [-ResultSize <int>]

onde -filter suporta apenas Nome e Descrição e ajuda a encontrar salas cujo Nome/Descrição corresponde a cadeia de caracteres de palavra chave. O PoolFqdn pesquisa em um determinado Pool de Servidor de Chat Persistente.

Para limpar uma sala e mensagens de uma sala

    Clear-CsPersistentChatRoom [-Identity] <string> -EndDate <DateTime> [-WhatIf] [-Confirm]  [<CommonParameters>]

ou

    Clear-CsPersistentChatRoom [-Instance] <ChatRoomObject> -EndDate <DateTime> [-WhatIf] [-Confirm] [<CommonParameters>]

Para remover uma sala

    Remove-CsPersistentChatRoom [-Identity] <string> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]

ou

    Remove-CsPersistentChatRoom [-Instance] <ChatRoomObject> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]

