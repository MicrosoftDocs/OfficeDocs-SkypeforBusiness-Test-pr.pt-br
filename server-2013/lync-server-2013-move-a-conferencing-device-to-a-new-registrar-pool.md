---
title: Mover um dispositivo de conferência para um novo pool de registradores
TOCTitle: Mover um dispositivo de conferência para um novo pool de registradores
ms:assetid: 26e02ca3-e881-4f90-8bf0-b13649108100
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994025(v=OCS.15)
ms:contentKeyID: 52057574
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover um dispositivo de conferência para um novo pool de registradores

 

_**Tópico modificado em:** 2013-02-20_

Mova um dispositivo de conferência de um pool de registradores para outro usando o cmdlet **Move-CsMeetingRoom**. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


## Mover um dispositivo de conferência para um novo pool de registrador

  - Para mover um dispositivo de converência, você deve especificar a identidade da sala a ser movida, e então definir o parâmetro Alvo para o nome de domínio totalmente qualificado (FQDN) do pool de Registradores o dispositivo a ser movido. Por exemplo:
    
        Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com" -Identity "Room 14"

Para obter detalhes, consulte o tópico de Ajuda do cmdlet [Move-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsMeetingRoom). en-us

