---
title: Gerenciar suplementos
TOCTitle: Gerenciar suplementos
ms:assetid: b84f868e-b36e-4ab4-b284-7db212d401c3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205193(v=OCS.15)
ms:contentKeyID: 49307895
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar suplementos

 

_**Tópico modificado em:** 2012-10-06_

Para criar um novo suplemento Servidor de Chat Persistente

    New-CsPersistentChatAddin -Name Contoso -PersistentChatPoolFqdn client.contoso.com -Url http://contoso.com 

## Criar, obter, definir ou remover um suplemento

Para criar um novo suplemento

    New-CsPersistentChatAddin -PersistentChatPoolFqdn <String> -Name <String> -Url<String>

> [!IMPORTANT]  
> PersistentChatPoolFqdn &lt;String&gt; é necessário somente se há mais de um Pool de Servidor de Chat Persistente.

Para obter um suplemento

    Get-CsPersistentChatAddin -Identity <String>]

ou

    Get-CsPersistentChatAddin -PersistentChatPoolFqdn <String>

Para definir um suplemento

    Set-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

ou

    Set-CsPersistentChatAddIn -Identity <String> [-Name <String>] [-Url<String>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

Para remover um suplemento

    Remove-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

ou

    Remove-CsPersistentChatAddIn -Identity <String> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

