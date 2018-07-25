---
title: Cmdlets que usam uma identidade e usuário e o escopo de marca]
TOCTitle: Cmdlets que usam uma identidade e usuário e o escopo de marca]
ms:assetid: 344a21b0-5301-4e77-853a-970bb1c11e1d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362781(v=OCS.15)
ms:contentKeyID: 56270381
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que usam uma identidade e usuário e o escopo de marca\]

 

_**Tópico modificado em:** 2015-06-22_

Os cmdlets **Grant-Cs** (usados para atribuir políticas a usuários) exigem dois identificadores? uma identidade de usuário (o parâmetro Identidade) e a identidade de uma política por usuário (o parâmetro PolicyName). Por exemplo, para atribuir a política de voz, RedmondVoicePolicy, ao usuário Paulo Neves, você usa o seguinte comando:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

Existem duas coisas a se ter em mente ao atribuir políticas a usuários ao atribuir políticas a usuários. Primeiro, somente políticas por usuário podem ser atribuídas. Não é possível atribuir a política global a um usuário. Por exemplo, este comando falhará:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "global"

Este comando falha porque não há necessidade de atribuir a política global. Se você quiser gerenciar um usuário usando a política global, não atribua uma política por usuário a esse usuário. Se nenhuma política por usuário tiver sido atribuída a um usuário, o usuário será automaticamente gerenciado por meio da política global.

> [!NOTE]  
> E se uma política por usuário tiver sido anteriormente atribuída ao usuário, e se você quiser cancelar a atribuição dessa política e ter o usuário gerenciado pela política global? Nesse caso, primeiro você usará a sintaxe a seguir, que cancela a atribuição de uma política por usuário ao conceder uma política nula ao usuário:<br />
Grant-CsVoicePolicy –Identity &quot;Paulo Neves&quot; –PolicyName $Null


Segundo, tenha em mente que as políticas por usuário são criadas no escopo da marca. Entretanto, você pode omitir o **prefixo** da marca ao especificar um nome de política. Esses dois comandos são idênticos:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "tag:RedmondVoicePolicy"
    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

Se você quiser retornar as identidades para todas as suas políticas por usuário (ou, pelo menos, todas as políticas por usuário de tipo especificado, como políticas de voz), use um comando semelhante a este:

    Get-CsVoicePolicy -Filter "tag:*"

Os cmdlets a seguir usam uma Identidade de usuário e o escopo de marca:

  - [Grant-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsClientPolicy)

  - [Grant-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsConferencingPolicy)

  - [Grant-CsDialPlan](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsDialPlan)

  - [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)

  - [Grant-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsHostedVoicemailPolicy)

  - [Grant-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsVoicePolicy)

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

