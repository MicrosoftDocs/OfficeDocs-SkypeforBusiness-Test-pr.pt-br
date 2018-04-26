---
title: Obter informações sobre seu locatário do Lync Online
TOCTitle: Obter informações sobre seu locatário do Lync Online
ms:assetid: 06467515-9114-45bb-8d09-26a915c3fc4d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362768(v=OCS.15)
ms:contentKeyID: 56270367
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Obter informações sobre seu locatário do Lync Online

 

_**Tópico modificado em:** 2015-06-22_

Para retornar informações sobre seu locatário do Skype for Business Online, chame o cmdlet [Get-CsTenant](get-cstenant.md) sem qualquer parâmetro adicional:

    Get-CsTenant

Para retornar somente o nome do locatário e a ID (o valor do parâmetro TenantID será obrigatório ao executar cmdlets como [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) e [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)), use este comando:

    Get-CsTenant | Select-Object Name, TenantID

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

