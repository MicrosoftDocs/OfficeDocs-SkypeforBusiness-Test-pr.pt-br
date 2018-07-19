---
title: Cmdlets que Usam uma Identidade de Provedor Audioconferência
TOCTitle: Cmdlets que Usam uma Identidade de Provedor Audioconferência
ms:assetid: be5621b6-ec11-4b12-83ec-075af269ca6a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362841(v=OCS.15)
ms:contentKeyID: 56270469
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que Usam uma Identidade de Provedor Audioconferência

 

_**Tópico modificado em:** 2015-06-22_

Para retornar informações sobre provedores de áudioconferência com os quais a sua organização tem contato, contacte o cmdlet [Get-CsAudioConferencingProvider](https://docs.microsoft.com/powershell/module/skype/Get-CsAudioConferencingProvider) sem qualquer parâmetro:

    Get-CsAudioConferencingProvider

Se deseja limitar os dados a um único provedor (neste exemplo, o provedor é Serviços de Áudio de Contoso), use o parâmetro Identity:

    Get-CsAudioConferencingProvider -Identity "Contoso Audio Services"

Há somente um cmdlet Skype for Business Online que aceita um ID de provedor de audioconferência:

  - [Get-CsAudioConferencingProvider](https://docs.microsoft.com/powershell/module/skype/Get-CsAudioConferencingProvider)

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

