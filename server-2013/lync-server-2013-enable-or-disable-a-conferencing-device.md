---
title: Habilitar ou desabilitar um dispositivo de conferência
TOCTitle: Habilitar ou desabilitar um dispositivo de conferência
ms:assetid: d5140e38-d015-4706-9bde-cf2fa748c36b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994070(v=OCS.15)
ms:contentKeyID: 52057731
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar um dispositivo de conferência

 

_**Tópico modificado em:** 2013-02-20_

Habilite e desabilite um dispositivo de conferência pelo uso dos cmdlets **Enable-CsMeetingRoom** e **Disable-CsMeetingRoom**. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou então de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.


## Para habilitar um dispositivo de conferência

  - Para habilitar um dispositivo de conferência, use o cmdlet **Enable-CsMeetingRoom**. Quando habilitar um dispositivo desse tipo, você precisa incluir: a) a identidade do dispositivo de conferência; b) o pool Registrar, em que a conta da sala será hospedada; c) o endereço SIP a ser atribuído àquela conta.
    
        Enable-CsMeetingRoom -Identity "Redmond Conferencing device" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"

## Para desabilitar um dispositivo de conferência

  - Para desabilitar um dispositivo de conferência, use o cmdlet **Disable-CsMeetingRoom**. Certifique-se de especificar a identidade do dispositivo de conferência a ser desabilitado:
    
        Disable-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"

Para mais detalhes, veja os tópicos de Ajuda para os cmdlets [Enable-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Enable-CsMeetingRoom) e [Disable-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Disable-CsMeetingRoom).

