---
title: Importar regras de atualização de dispositivo
TOCTitle: Importar regras de atualização de dispositivo
ms:assetid: 919e9c87-912b-4bc9-92e7-5998fc2e0bf0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994056(v=OCS.15)
ms:contentKeyID: 52057653
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importar regras de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

As regras de atualização do dispositivo pode ser importadas somente usando o Windows PowerShell e o cmdlet **Import-CsDeviceUpdate**. Esse cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


## Para importar as regras de atualização do dispositivo para um único servidor Web

  - O seguinte comando importa as regras de atualização do dispositivo para o servidor Web atl-cs-001.litwareinc.com:
    
        Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName C:\Updates\UCUpdates.cab

## Para importar as regras de atualização do dispositivo para todos os seus servidores

  - Neste exemplo, as regras de atualização do dispositivo são importadas para todos os servidores Web implantados na sua organização. Para esse comando funcionar, a pasta \\\\atl-fs-001.litwareinc.com\\Updates deve estar compartilhada e disponível para todos os servidores Web.
    
        Get-CsService -WebServer | ForEach-Object {Import-CsDeviceUpdate -Identity $_.Identity -FileName \\atl-fs-001.litwareinc.com\Updates\UCUpdates.cab}

Para obter detalhes, consulte o tópico de Ajuda para o cmdlet [Import-CsDeviceUpdate](https://docs.microsoft.com/en-us/powershell/module/skype/Import-CsDeviceUpdate).

## Consulte Também

#### Tarefas

[Exibir informações sobre as regras de atualização de dispositivo](lync-server-2013-view-information-about-device-update-rules.md)  
[Aprovar uma regra de atualização de dispositivo](lync-server-2013-approve-a-device-update-rule.md)

