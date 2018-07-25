---
title: Cmdlets que usam o escopo global e o escopo de marca
TOCTitle: Cmdlets que usam o escopo global e o escopo de marca
ms:assetid: 1e2bc055-8a72-425e-967b-e253add7018c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362774(v=OCS.15)
ms:contentKeyID: 56270376
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que usam o escopo global e o escopo de marca

 

_**Tópico modificado em:** 2015-06-22_

In Skype for Business Online, policies can be configured at either the *global scope* or at the *tag scope* (or *per-user scope*). When using the **Get-Cs** cmdlets, you do not have to specify a scope or identity. If you call one of these cmdlets without any parameters, then all the relevant items will be returned. For example, this command returns information about all your external access policies:

    Get-CsExternalAccessPolicy

You need to include only the Identity parameter or the Filter parameter if you want to limit the returned data. For example, to return only the global policy, use this command:

    Get-CsExternalAccessPolicy -Identity "global"

To return a per-user policy that has the Identity “RedmondAccessPolicy”, use this command:

    Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"

> [!NOTE]  
> When referencing a per-user policy, the tag <strong>prefix</strong> is optional. This syntax, which includes the prefix, is also valid:<br />
Get-CsExternalAccessPolicy –Identity &quot;tag:RedmondAccessPolicy&quot;


To return all policies except the global policies (that is, all the per-user policies), use this command:

    Get-CsExternalAccessPolicy -Filter "tag:*"

The following cmdlets operate against both the global scope and the per-user (tag) scope:

  - [Get-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientPolicy)

  - [Get-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsConferencingPolicy)

  - [Get-CsDialPlan](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDialPlan)

  - [Get-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExternalAccessPolicy)

  - [Get-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostedVoicemailPolicy)

  - [Get-CsPresencePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPresencePolicy)

  - [Get-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsVoicePolicy)

> [!NOTE]  
> Despite the name, dial plans are, functionally speaking, policies. The term <em>dial plan</em> is used instead of, for example, dialing policy, in order to preserve the terminology used with previous versions of Lync Server.

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

