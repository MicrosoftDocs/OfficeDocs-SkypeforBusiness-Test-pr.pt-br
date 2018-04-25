---
title: 'Lync Online: Adicionar um domínio à lista de domínios bloqueados'
TOCTitle: Adicionar um domínio à lista de domínios bloqueados
ms:assetid: ea6ebeea-3031-4c42-9a2c-88eaab790636
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362853(v=OCS.15)
ms:contentKeyID: 56270485
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar um domínio à lista de domínios bloqueados no Lync Online

 

_**Tópico modificado em:** 2015-06-22_

Para adicionar um domínio à lista de domínios bloqueados, use uma sintaxe semelhante a esta:

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -BlockedDomains @{Add=$x}

Como você pode ver, este comando exige duas etapas. Primeiro, você usa o [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) para criar um objeto de domínio representando o domínio a ser adicionado à lista bloqueada. Depois disso, você usa o cmdlet [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) e o método Add para adicionar esse domínio (neste exemplo, o domínio armazenado na variável $x) à lista.

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

