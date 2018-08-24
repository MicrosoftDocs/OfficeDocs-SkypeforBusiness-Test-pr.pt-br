---
title: Atribuir políticas a um telefone de área comum
TOCTitle: Atribuir políticas a um telefone de área comum
ms:assetid: f0554fd1-b237-49b3-9eb4-26f4b91f5604
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994082(v=OCS.15)
ms:contentKeyID: 52057753
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir políticas a um telefone de área comum

 

_**Tópico modificado em:** 2013-02-20_

Depois de criar sua política de telefones de área comum (para obter detalhes, consulte [Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)), você poderá atribui-la a um telefone de área comum usando o Windows PowerShell e o cmdlet **Grant-Cs** apropriado. Esses cmdlets podem ser executados a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).


## Atribuindo uma política a um único telefone de área comum

  - O comando a seguir atribui a política de voz RedmondVoice por usuário ao telefone de área comum cuja identidade é Saguão do Edifício 14.
    
        Grant-CsVoicePolicy -Identity "Building 14 Lobby" -PolicyName "RedmondVoicePolicy"

## Atribuindo uma política a vários telefones de área comum

  - Neste exemplo, a política de voz RedmondVoice por usuário é atribuída a todos os telefones de área comum configurados para o uso na organização.
    
        Get-CsCommonAreaPhone | Grant-CsVoicePolicy  -PolicyName "RedmondVoicePolicy"

Para obter detalhes, consulte os tópicos da Ajuda para [Grant-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsVoicePolicy).

## Consulte Também

#### Outros Recursos

[Get-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCommonAreaPhone)

