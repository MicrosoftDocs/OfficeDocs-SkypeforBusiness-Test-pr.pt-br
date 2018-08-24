---
title: Exibir informações sobre o dispositivo de conferência
TOCTitle: Exibir informações sobre o dispositivo de conferência
ms:assetid: 838bdbf8-8b68-4eb6-8fa3-45bfd5b0b1cd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994043(v=OCS.15)
ms:contentKeyID: 52057667
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações sobre o dispositivo de conferência

 

_**Tópico modificado em:** 2013-02-20_

Você pode visualizar as informações sobre os dispositivos de conferência configurados para serem usados na sua organização usando o Windows PowerShell e o cmdlet **Get-CsMeetingRoom**. Execute o cmdlet **Get-CsMeetingRoom** a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

Se você usar o cmdlet **Get-CsMeetingRoom** sem qualquer parâmetro, ele retornará informações sobre todos os seus dispositivos de conferência. Os parâmetros opcionais fornecem maneiras diferentes para você filtrar informações. Para obter detalhes, consulte a seção Parâmetros do [Get-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingRoom).


## Exibindo as informações sobre todos os seus dispositivos de conferência

  - Para visualizar os detalhes sobre todos os seus dispositivos de conferência, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione Enter:
    
        Get-CsMeetingRoom
    
    Este cmdlet retorna informações semelhantes às seguintes para cada dispositivo de conferência. Observe que este exemplo mostra apenas algumas das informações que você vai ver quando executar este cmdlet:
    
        ContactOptionFlags                : 64
        OwnerUrn                          : urn:device:roomsystem
        OriginatorSid                     :
        SamAccountName                    : room12129
        UserPrincipalName                 : room1219@litwareinc.com
        FirstName                         : 
        LastName                          :
        WindowsEmailAddress               :
        Sid                               : S-1-5-21-2831376166-2963252556-2165051629-1257
        LineServerURI                     :
        AudioVideoDisabled                : False
        IPPBXSoftPhoneRoutingEnabled      : False
        RemoteCallControlTelephonyEnabled : False
        PrivateLine                       :
        AcpInfo                           : {}
        HostedVoiceMail                   :
        DisplayName                       : Room 1219

## Visualizando informações sobre um dispositivo de conferência específico

  - Para visualizar as informações de um dispositivo de conferência específico, inclua o parâmetro Identity seguido da identidade do dispositivo de conferência (geralmente, o nome exibido no Active Directory). Por exemplo:
    
        Get-CsMeetingRoom -Identity "Room 1219"

Para obter detalhes, consulte o tópico de Ajuda para o cmdlet [Get-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingRoom).

