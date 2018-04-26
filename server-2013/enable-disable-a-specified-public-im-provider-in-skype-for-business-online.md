---
title: Habilitar/Desabilitar um provedor de IM público específico
TOCTitle: Habilitar/Desabilitar um provedor de IM público específico
ms:assetid: 9d3e2607-01c0-4ae9-accc-39f03ce253bb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362825(v=OCS.15)
ms:contentKeyID: 56270451
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar/Desabilitar um provedor de IM público específico

 

_**Tópico modificado em:** 2015-06-22_

Skype for Business Online permite estabelecer federação com usuários de um ou mais dos seguintes provedores públicos de mensagens instantâneas (IM):

  - Rede do Windows Live de serviços da Internet

  - Yahoo\!

  - AOL

Para permitir que a federação com um ou mais desses provedores, utilize o cmdlet [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) e defina o valor da propriedade Provider para um ou mais dos seguintes valores:

  - Windows Live

  - Yahoo

  - AOL

Por exemplo, este comando estabelece federação com Windows Live e AOL:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

Observe que sempre que você desejar adicionar ou remover um provedor, deve incluir todos os provedores federados relevantes no comando. Por exemplo, para adicionar o Yahoo\! é preciso executar o seguinte comando:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo"

Este comando deixará o Yahoo\! como o único provedor federado, porque é o provedor chamado no comando. Para estabelecer federação com todos os três provedores públicos de mensagens instantâneas, inclua todos os três provedores:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo", "AOL","WindowsLive"

Observe que você deve incluir o parâmetro Tenant ao chamar o cmdlet Set-CsTenantPublicProvider; se não o incluir, não será solicitado a inserir a ID de inquilino. Você pode retornar à ID de inquilino de seu inquilino do Skype for Business Online usando este comando:

    Get-CsTenant | Select-Object TenantID

Ou, use este comando para armazenar a ID de inquilino em uma variável:

    $tenantID = (Get-CsTenant | Select-Object TenantID)

Então, você pode usar essa variável (neste exemplo, $tenantID) ao chamar o Set-CsTenantPublicProvider:

    Set-CsTenantPublicProvider -Tenant $tenantID -Provider "Yahoo", "AOL","WindowsLive"

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

