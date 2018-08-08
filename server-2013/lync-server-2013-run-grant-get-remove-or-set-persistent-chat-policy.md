---
title: "Lync Server 2013: Exec., conced., obter, remov. ou def. Pol. de Chat Persistente"
TOCTitle: Executar, conceder, obter, remover ou definir Política de Chat Persistente
ms:assetid: 39ccdbe8-fb3d-47bc-96e2-9486b6d317e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204810(v=OCS.15)
ms:contentKeyID: 49306418
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executar, conceder, obter, remover ou definir Política de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Para criar uma nova política do Chat Persistente

    New-CsPersistentChatPolicy -Identity <XdsIdentity> [-Enable <Switch Parameter>] [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>] [-InMemory <Switch Parameter>]

Para conceder a política do Chat Persistente

    Grant-CsPersistentChatPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

Para obter a política do Chat Persistente

    Get-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Filter <String>] [-LocalStore <Switch Parameter>]

Para remover a política do Chat Persistente

    Remove-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>]

Para definir a política do Chat Persistente

    Set-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Instance < PSObject>]

