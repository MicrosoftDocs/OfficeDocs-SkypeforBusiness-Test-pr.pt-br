---
title: Cmdlets que não usam um escopo nem uma identidade
TOCTitle: Cmdlets que não usam um escopo nem uma identidade
ms:assetid: 9c50c732-3c64-4b6a-96fd-8f528eb739ce
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362824(v=OCS.15)
ms:contentKeyID: 56270450
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que não usam um escopo nem uma identidade

 

_**Tópico modificado em:** 2015-06-22_

Os cmdlets utilizados ao modificar as listas permitidas e as listas bloqueadas (listas que determinam com quais organizações de terceiros os usuários estão autorizados a comunicar) não usam um escopo nem uma identidade. Na verdade, o cmdlet **New-CsEdgeAllowAllKnownDomains** não tem nenhum parâmetro. Os cmdlets que não usam um escopo ou uma identidade são:

  - [New-CsEdgeAllowAllKnownDomains](https://docs.microsoft.com/powershell/module/skype/New-CsEdgeAllowAllKnownDomains)

  - [New-CsEdgeAllowList](https://docs.microsoft.com/powershell/module/skype/New-CsEdgeAllowList)

  - [New-CsEdgeDomainPattern](https://docs.microsoft.com/powershell/module/skype/New-CsEdgeDomainPattern)

Observe que, tanto com o cmdlet **New-CsEdgeAllowList** quanto com o cmdlet **New-CsEdgeDomainPattern**, você deve incluir o parâmetro Domain. Por exemplo:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

