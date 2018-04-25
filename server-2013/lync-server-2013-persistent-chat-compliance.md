---
title: 'Lync Server 2013: Conformidade de Chat Persistente'
TOCTitle: Conformidade de Chat Persistente
ms:assetid: 508933b6-bf17-4fb7-9147-f06ff6bc886f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204882(v=OCS.15)
ms:contentKeyID: 49306689
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conformidade de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Para criar uma nova configuração de conformidade do Chat Persistente

    New-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-AdapterName <String>] [-AdapterOutputDirectory <String>] [-AdapterType <String>] [-AddChatRoomDetails <$true | $false>] [-AddUserDetails <$true | $false>] [-Confirm [<Switch Parameter>]] [-CreateFileAttachmentsManifest <$true | $false>] [-CustomConfiguration <String>] [-Force <Switch Parameter>] [-InMemory <Switch Parameter>] [-OneChatRoomPerOutputFile <$true | $false>] [-RunInterval <TimeSpan>] [-WhatIf [<Switch Parameter>]]

Para obter uma configuração de conformidade do Chat Persistente

    Get-CsPersistentChatComplianceConfiguration [-Identity <XdsIdentity>] [-LocalStore <Switch Parameter>]

Para definir uma configuração de conformidade do Chat Persistente

    Set-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-AdapterName <String>] [-AdapterOutputDirectory <String>] [-AdapterType <String>] [-AddChatRoomDetails <$true | $false>] [-AddUserDetails <$true | $false>] [-Confirm [<Switch Parameter>]] [-CreateFileAttachmentsManifest <$true | $false>] [-CustomConfiguration <String>] [-Force <Switch Parameter>] [-InMemory <Switch Parameter>] [-OneChatRoomPerOutputFile <$true | $false>] [-RunInterval <TimeSpan>] [-WhatIf [<Switch Parameter>]]

Para remover uma configuração de conformidade do Chat Persistente

    Remove-CsPersistentChatComplianceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

