---
title: Cmdlets que usam o parâmetro Tenant
TOCTitle: Cmdlets que usam o parâmetro Tenant
ms:assetid: e7fe7c12-fbe0-49c1-9e8c-eef6958f27d0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362850(v=OCS.15)
ms:contentKeyID: 56270482
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets que usam o parâmetro Tenant

 

_**Tópico modificado em:** 2015-06-22_

Ao modificar suas definições do provedor público, você sempre precisará fornecer uma identidade Tenant; isto ocorrerá mesmo que você tenha apenas um único locatário. Por exemplo, este comando define Windows Live como o único provedor púlico com o qual seus usuários têm permissão de se comunicar

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

Felizmente, você não precisa digitar o ID do locatário (por exemplo, bf19b7db-6960-41e5-a139-2aa373474354) sempre que executa esses cmdlets. Ao contrário, poderá recuperar o ID executando o cmdlet [Get-CsTenant](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenant), armazenando o ID do locatário em uma variável, então, usando essa variável quando chamar um dos outros cmdlets. Por exemplo:

    $x = (Get-CsTenant).TenantId
    Set-CsTenantPublicProvider -Tenant $x -Provider "WindowsLive"

Como alternativa, você pode fazer isto em um único comando recuperando o ID do locatário,então, canalizando esse valor para o cmdlet Set-CsTenantPublicProvider:

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider "WindowsLive"}

Você não precisa especificar o ID do locatário ao chamar o cmdlet **Get-CsTenant**. Esse comando retorna informações sobre seu locatário:

    Get-CsTenant

Os seguintes cmdlets aceitam a identidade de um locatário. Contudo, nestes casos, o parâmetro é opcional e não precisa ser digitado ao chamar o cmdlet. Ao contrário, Windows PowerShell digitará defetivamente a identidade do locatário para você com base no locatário Skype for Business Online ao qual você está conectado atualmente:

  - [Get-CsTenant](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenant)

  - [Set-CsTenantFederationConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsTenantFederationConfiguration)

  - [Set-CsTenantHybridConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsTenantHybridConfiguration)

  - [Get-CsTenantFederationConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsTenantFederationConfiguration)

  - [Get-CsTenantHybridConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenantHybridConfiguration)

  - [Get-CsTenantLicensingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTenantLicensingConfiguration)

Por exemplo, o cmdlet **Get-CsTenantFederationConfiguration** pode ser chamado usando este comando:

    Get-CsTenantFederationConfiguration

Embora não seja requerido, você pode incluir o parâmetro Tenant ao chamar Get-CsTenantFederationConfiguration :

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

## Consulte Também

#### Conceitos

[Identidades, escopos e locatários](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Os cmdlets do Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

