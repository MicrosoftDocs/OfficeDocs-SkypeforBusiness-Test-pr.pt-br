---
title: Remover um domínio da lista de domínios bloqueados
TOCTitle: Remover um domínio da lista de domínios bloqueados
ms:assetid: a11ea475-bb8b-44be-a5a5-4abb2fed42b8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362830(v=OCS.15)
ms:contentKeyID: 56270452
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover um domínio da lista de domínios bloqueados

 

_**Tópico modificado em:** 2015-06-22_

Duas etapas são necessárias para remover um domínio da lista de domínios bloqueados. Primeiro, você deve usar o cmdlet [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) para criar um objeto de domínio para o domínio a ser removido:

    $x = New-CsEdgeDomainPattern "fabrikam.com"

Depois de criar esse objeto, use a seguinte sintaxe para remover o domínio (neste exemplo, o domínio armazenado na variável $x) a partir da lista de domínios bloqueados:

    Set-CsTenantFederationConfiguration -BlockedDomains @{Remove=$x}

Para remover todos os domínios da lista de domínios bloqueados, defina o valor da propriedade BlockedDomains como nulo ($Null):

    Set-CsTenantFederationConfiguration -BlockedDomains $Null

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

