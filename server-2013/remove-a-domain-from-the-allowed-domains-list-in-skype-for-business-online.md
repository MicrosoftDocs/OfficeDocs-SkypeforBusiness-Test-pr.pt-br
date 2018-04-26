---
title: Remover um domínio da lista de domínios permitidos
TOCTitle: Remover um domínio da lista de domínios permitidos
ms:assetid: 04948582-363b-49bd-8305-166c4c1d0dd9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362766(v=OCS.15)
ms:contentKeyID: 56270366
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover um domínio da lista de domínios permitidos

 

_**Tópico modificado em:** 2015-06-22_

A remoção de um domínio da lista dos domínios permitidos envolve uma série de etapas. Primeiro, você deverá usar um comando semelhante ao seguinte para recuperar uma coleção de todos os domínios atualmente na lista:

    $x = (Get-CsTenantFederationConfiguration).AllowedDomains

Em seguida, execute este comando para examinar esses domínios:

``` 
$x
```

Tome nota da posição numérica do domínio a ser removido. Se o domínio for o primeiro domínio da lista, então terá um valor de índice 0. Se o domínio for o segundo domínio da lista, terá um valor de índice 1 e assim por diante.

Depois que você souber o número do índice, use um comando como o a seguir para remover o domínio especificado, certificando-se de usar o número de índice correto. Esse comando remove o primeiro domínio da lista (número de índice 0):

    $x.AllowedDomain.RemoveAt(0)

Por fim, chame o cmdlet [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) para gravar suas alterações no Skype for Business Online:

    Set-CsTenantFederationConfiguration -AllowedDomains $x

## Consulte Também

#### Conceitos

[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

