---
title: 'Lync Server 2013: Configurar o Servidor de Chat Persistente'
TOCTitle: Configurar o Servidor de Chat Persistente
ms:assetid: 85028aff-a38e-4748-958e-59e707a47532
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205054(v=OCS.15)
ms:contentKeyID: 49307339
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Para criar uma nova configuração do Chat Persistente

    New-CsPersistentChatConfiguration -Identity <XdsIdentity> [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

Para obter a configuração do Chat Persistente

    Get-CsPersistentChatConfiguration [-LocalStore <Switch Parameter>] [-Identity <XdsIdentity>]

Para remover a configuração do Chat Persistente

    Remove-CsPersistentChatConfiguration -Identity <XdsIdentity>

Para definir a configuração do Chat Persistente

    Set-CsPersistentChatConfiguration [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject >] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

Para o Lync Server 2013, todo o tráfego dos serviços da web é suportado no Lync Server 2013, Servidores Front-End. Portanto, o endereço gcweb01 no Servidor de Chat Persistente não é necessário. Ainda oferecemos suporte ao acesso de serviço web interno porque fornecemos serviços de upload/download de arquivos na web somente para o site *interno* (e não para o site *externo* para usuários remotos).

