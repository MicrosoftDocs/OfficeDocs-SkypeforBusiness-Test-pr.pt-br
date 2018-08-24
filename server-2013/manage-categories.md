---
title: Gerenciar categorias
TOCTitle: Gerenciar categorias
ms:assetid: 1b118d91-b4c4-4b2f-b842-b451417ec2c6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204719(v=OCS.15)
ms:contentKeyID: 49306042
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar categorias

 

_**Tópico modificado em:** 2012-10-06_

Para criar uma nova Categoria do Servidor de Chat Persistente

    New-CsPersistentChatCategory -Name Foo -PersistentChatPoolFqdn client.contoso1b118d91-b4c4-4b2f-b842-b451417ec2c6.com [other parameters]

> [!IMPORTANT]  
> O PersistentChatPoolFqdn é necessário apenas se existe mais de um Pool de Servidor de Chat Persistente.

Para fazer alterações em uma Categoria do Servidor de Chat Persistente já existente

    Set-CsPersistentChatCategory -Identity testCat -AllowedMembers @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}  -DeniedMembers @{Add="sip:user2@contoso.com"}
    Set-CsPersistentChatCategory -Identity testCat -Creators @{Add="sip:user1@contoso.com"}

Windows PowerShell: AllowedMembers, DeniedMembers, e Creators podem ser definidos simultaneamente. Creators deve ser o subconjunto de AllowedMembers menos DeniedMembers. Você também pode configurar as propriedades de uma categoria ao mesmo tempo que os membros e criadores.

## Criar, obter, configurar ou remover uma categoria

Para criar uma nova Categoria

    New-CsPersistentChatCategory -Name <String> [-PersistentChatPoolFqdn <String>] [-Description <String>] [-EnableInvitations<Switch Parameter>] [-EnableFileUpload <Switch Parameter>] [-RemoveChatHistory <Switch Parameter>] [-MaxContentSize <Integer>]

Para obter uma Categoria

    Get-CsPersistentChatCategory -Identity <String>

ou

    Get-CsPersistentChatCategory -PersistentChatPoolFqdn <String>

Para configurar uma Categoria

    Set-CsPersistentChatCategory -Instance <CategoryObject> [-WhatIf] [-Confirm] [<CommonParameters>]

ou

    Set-CsPersistentChatCategory [-Identity] <string> [-Name <string>] [-Description <string>] [-Invitations <bool>] [-FileUpload <bool>] [-ChatHistory <bool>] [-AllowedMembers <PSListModifier[string]>] [-DeniedMembers <PSListModifier[string]>] [-Creators <PSListModifier[string]>] [-WhatIf] [-Confirm]  [<CommonParameters>]

Para remover uma Categoria

    Remove-CsPersistentChatCategory -Instance <CategoryObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

ou

    Remove-CsPersistentChatCategory -Identity <String> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

