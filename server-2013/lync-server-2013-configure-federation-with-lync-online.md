---
title: 'Lync Server 2013: Configurar federação com Lync Online'
TOCTitle: Configurar federação com Lync Online
ms:assetid: a10bd1d5-c003-46db-9f57-7d55d3fa08da
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205126(v=OCS.15)
ms:contentKeyID: 49307646
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar federação do Lync Server 2013 com Lync Online

 

_**Tópico modificado em:** 2016-12-08_

Siga as etapas nesta seção para configurar a interoperabilidade entre sua implantação no local e o Skype for Business Online.

## Configure seu serviço de borda local para federação com o Skype for Business Online

A federação permite que os usuários em sua implantação no local se comuniquem com usuários do Office 365 em sua organização. Para configurar a federação, execute o cmdlets a seguir:

```
    Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting
```
```
    New-CSHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
```

## Configurar seu locatário do Skype for Business Online para um espaço de endereço SIP compartilhado

Um endereço SIP (Session Initiation Protocol) é um identificador único em uma rede, semelhante a um número de telefone ou endereço de e-mail. Antes de tentar mover os usuários do Lync do local para Skype for Business Online, será necessário configurar o locatário do Office 365 para compartilhar o espaço do endereço SIP compartilhado com sua implantação local. Se ele não estiver configurado, talvez você veja esta mensagem:

Move-CsUser : HostedMigration fault: Error=(510), Description=(O locatário deste usuário não está habilitado para o espaço de endereço sip compartilhado.)

Para configurar um espaço de endereço SIP, estabeleça uma sessão remota do PowerShell com o Skype for Business Online e depois execute este cmdlet:

    Set-CsTenantFederationConfiguration -SharedSipAddressSpace $true

Para estabelecer uma sessão remota do PowerShell com o Skype for Business Online, primeiro é necessário instalar o módulo Skype for Business Online para Windows PowerShell, que você pode obter aqui: [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911).

Depois de instalar o módulo, você pode estabelecer uma sessão remota com os seguintes cmdlets:

```
    Import-Module LyncOnlineConnector
```
```
    $cred = Get-Credential
```
```
    $CSSession = New-CsOnlineSession -Credential $cred
```
```
    Import-PSSession $CSSession -AllowClobber
```

Para obter mais informações sobre como estabelecer uma sessão remota do PowerShell com o Skype for Business Online, consulte [Conectando ao Lync Online Usando o Windows PowerShell](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

Para obter mais informações sobre como usar o módulo Skype for Business Online PowerShell, consulte [Usar o Windows PowerShell para gerenciar o Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

## Consulte Também

#### Outros Recursos

[New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider)

