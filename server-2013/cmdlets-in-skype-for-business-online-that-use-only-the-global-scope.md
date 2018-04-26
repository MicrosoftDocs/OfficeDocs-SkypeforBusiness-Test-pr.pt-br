---
title: Cmdlets que usam somente o escopo global
TOCTitle: Cmdlets que usam somente o escopo global
ms:assetid: 0ffd3bc9-a6a1-4c2e-8d52-e599acc49d2d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362771(v=OCS.15)
ms:contentKeyID: 56270371
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que usam somente o escopo global

 

_**Tópico modificado em:** 2015-06-22_

Algumas das configurações do Skype for Business Online estão disponíveis somente no *escopo global*. Isso significa que há uma única coleção de configurações que se aplica a todos os usuários que tenham sido atribuídos àquele locatário (cada locatário tem sua própria coleção de configurações globais). Quando você estiver usando cmdlets limitados ao escopo global, o parâmetro Identidade será opcional. Por exemplo, para recuperar configurações de reunião, você pode usar este comando:

    Get-CsMeetingConfiguration -Identity "global"

Como alternativa, você pode omitir o parâmetro Identidade e usar este comando mais simples em seu lugar:

    Get-CsMeetingConfiguration

Como existe somente uma coleção global de configurações de reunião, os dois comandos retornam exatamente as mesmas informações. O parâmetro Identidade também pode ser omitido quando você usar um dos cmdlets **Set-Cs**. Estes dois comandos são idênticos:

    Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False
    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

Os dois comandos são idênticos porque, por padrão, o Windows PowerShell modificará a coleção global se você não incluir o parâmetro Identidade.

Os cmdlets a seguir funcionam somente no escopo global:

  - [Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

  - [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)

  - [Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)

  - [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

  - [Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

  - [Get-CsTenantLicensingConfiguration](get-cstenantlicensingconfiguration.md)

  - [Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)

  - [Remove-CsVoicePolicy](remove-csvoicepolicy.md)

  - [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

  - [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

Observe que o cmdlet **Remove-CsVoicePolicy** é, de alguma forma, uma anomalia, Primeiro, esse cmdlet exige que você inclua o parâmetro Identidade:

    Remove-CsVoicePolicy -Identity "global"

Segundo, o cmdlet **Remove-CsVoicePolicy** não exclui realmente a política de voz global; o Skype for Business Online não permite que você exclua políticas ou configurações globais. O que ele faz é permitir que você redefina todas as propriedades da política de voz global a seus valores padrão. Por exemplo, por padrão, a propriedade AllowCallForwarding é definida como False. Entretanto, AllowCallForwarding pode ter sido modificada, com o novo valor agora definido como Verdadeiro. Quando você executa o cmdlet **Remove-CsVoicePolicy**, a propriedade AllowCallForwarding será revertida para seu valor padrão: False. A tabela a seguir resumo este cenário:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor de AllowCallForwarding</th>
<th>Cenário</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>False</p></td>
<td><p>Valor padrão</p></td>
</tr>
<tr class="even">
<td><p>True</p></td>
<td><p>Após a política padrão ter sido modificada</p></td>
</tr>
<tr class="odd">
<td><p>False</p></td>
<td><p>Após o cmdlet <strong>Remove-CsVoicePolicy</strong> ter sido executado</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)

