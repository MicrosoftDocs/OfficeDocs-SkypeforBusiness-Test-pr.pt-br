---
title: Excluir um conjunto de definições de configuração de atualização de dispositivo
TOCTitle: Excluir um conjunto de definições de configuração de atualização de dispositivo
ms:assetid: 1a649136-34a9-42a7-a5b3-a78bbfe93f36
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994019(v=OCS.15)
ms:contentKeyID: 52057564
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto de definições de configuração de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-20_

As informações de configuração de atualização de dispositivo podem ser excluídas usando o Windows PowerShell e o cmdlet **Remove-CsdeviceUpdateConfiguration**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).


## Para remover um conjunto específico de definições de configuração de atualização de dispositivo

  - Este comando exclui as definições de configuração de atualização de dispositivo aplicadas ao site Redmond:
    
        Remove-CsDeviceUpdateConfiguration -Identity "site:Redmond"

## Para remover todas as definições de configuração de atualização de dispositivo aplicadas ao escopo do site

  - Este comando exclui todas as definições de configuração de atualização de dispositivo aplicadas ao escopo do site:
    
        Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration

## Para remover as informações de configuração de atualização de dispositivo com base no valor da propriedade LogCleanUpInterval

  - O comando a seguir exclui todas as informações de configuração de atualização de dispositivo onde o intervalo de limpeza do log for maior que 10 dias (10.00:00:00):
    
        Get-CsDeviceUpdateConfiguration | Where-Object {$_.LogCleanUpInterval -gt "10.00:00:00" | Remove-CsDeviceUpdateConfiguration

Para obter detalhes, consulte o tópico de Ajuda do cmdlet [Remove-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsDeviceUpdateConfiguration). en-us

