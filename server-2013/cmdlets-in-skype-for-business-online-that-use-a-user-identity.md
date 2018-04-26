---
title: Cmdlets Que Usam Identidade de Usuário
TOCTitle: Cmdlets Que Usam Identidade de Usuário
ms:assetid: be87409f-6372-4c70-91ac-6ef13dfbe65a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362842(v=OCS.15)
ms:contentKeyID: 56270466
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets Que Usam Identidade de Usuário

 

_**Tópico modificado em:** 2015-06-22_

Em Skype for Business Online, há várias maneiras diferentes de referenciar uma Identidade de usuário individual:

  - Use o nome de exibição do usuário do Serviço de Domínio do Active Directory. Por exemplo:
    
        -Identity "Ken Myer"

  - Use o endereço de usuário SIP. Por exemplo:
    
        -Identity "sip:kenmyer@litwareinc.com"

  - Use o usuário UPN. Por exemplo:
    
        -Identity " kenmyer@litwareinc.com"

  - Use o nome diferenciado do usuário do Serviço de Domínio do Active Directory. Por exemplo:
    
        -Identity "CN=48ebd1ba-95d4-460c-b751-811ebf0c4611,OU=fa8226f5-14fa-46da-8 236-039b25bc7a27,OU=Lync Online Tenants,DC=litwareinc,DC=com"

Os cmdlets a seguir aceitam uma Identidade de usuário:

  - [Disable-CsMeetingRoom](disable-csmeetingroom.md)

  - [Enable-CsMeetingRoom](enable-csmeetingroom.md)

  - [Get-CsExUmContact](get-csexumcontact.md)

  - [Get-CsMeetingRoom](get-csmeetingroom.md)

  - [Get-CsOnlineUser](get-csonlineuser.md)

  - [Get-CsUserAcp](get-csuseracp.md)

  - [New-CsExUmContact](new-csexumcontact.md)

  - [Remove-CsExUmContact](remove-csexumcontact.md)

  - [Remove-CsUserAcp](remove-csuseracp.md)

  - [Set-CsExUmContact](set-csexumcontact.md)

  - [Set-CsMeetingRoom](set-csmeetingroom.md)

  - [Set-CsUserAcp](set-csuseracp.md)

Note que não é necessário especificar uma Identidade de usuário ao contactar um dos cmdlets **Get-Cs**. Nesse caso, os cmdlets retornam todas as instâncias de itens especificados. Por exemplo, este comando retorna informações sobre todos os usuários habilitados por Skype for Business Online:

    Get-CsOnlineUser

O parâmetro Identity é exigido somente quando se quer retornar informações para um usuário específico.

    Get-CsOnlineUser -Identity "Ken Myer"

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)

