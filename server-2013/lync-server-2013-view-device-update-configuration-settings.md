---
title: 'Lync Server 2013: Exibir configurações de atualização de dispositivo'
TOCTitle: Exibir configurações de atualização de dispositivo
ms:assetid: aa6a70a9-bd77-4606-b797-ea6a3bab9cf2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994059(v=OCS.15)
ms:contentKeyID: 52057711
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir configurações de atualização de dispositivo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Você pode exibir as configurações de serviço de atualização de dispositivo usando o Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsDeviceUpdateConfiguration**, que você pode executar no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.



  - 
    
    Para exibir informações sobre todas as suas rotas de voz, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione Enter:
    
        Get-CsDeviceUpdateConfiguration
    
    Este comando retorna informações semelhantes para o seguinte:
    
        Identity               : Global
        ValidLogFileTypes      : {Watson, Config, Diaglog, CELog}
        ValidLogFileExtensions : {.dmp, .clg, .clg1, .clg2...}
        MaxLogFileSize         : 1024000
        MaxLogCacheLimit       : 512000
        LogCleanUpInterval     : 10.00:00:00
        LogFlushInterval       : 00:05:00
        LogCleanUpTimeOfDay    :

Para obter informações detalhadas sobre esse cmdlet, consulte o tópico da Ajuda em [Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDeviceUpdateConfiguration).

