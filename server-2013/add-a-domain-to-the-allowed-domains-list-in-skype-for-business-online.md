---
title: 'Lync Online: Adicionar um domínio à lista de domínios permitidos'
TOCTitle: Adicionar um domínio à lista de domínios permitidos
ms:assetid: 7b7f76c8-3047-40be-a938-8ac2868a6bc8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362818(v=OCS.15)
ms:contentKeyID: 56270434
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar um domínio à lista de domínios permitidos no Lync Online

 

_**Tópico modificado em:** 2015-06-22_

Adicionar um primeiro domínio à lista de domínios permitidos é um processo com três etapas. Primeiro, use o cmdlet [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) para criar um objeto do domínio para o domínio a ser adicionado:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

Em seguida, use o cmdlet [New-CsEdgeAllowList](new-csedgeallowlist.md) para criar uma nova lista permitida que inclui o objeto do domínio:

    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x

Finalmente, use o cmdlet [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) para gravar a nova lista permitida em Skype for Business Online:

    Set-CsTenantFederationConfiguration -AllowedDomains $newAllowList

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

