---
title: Gerenciando configurações do grupo de resposta a nível do aplicativo
TOCTitle: Gerenciando configurações do grupo de resposta a nível do aplicativo
ms:assetid: aab749a1-fa2d-4ce8-a6c6-ebcfa37ce02a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721843(v=OCS.15)
ms:contentKeyID: 49886355
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando configurações do grupo de resposta a nível do aplicativo

 

_**Tópico modificado em:** 2012-11-01_

As configurações do aplicativo do Aplicativo Grupo de Resposta incluem a configuração de música de espera padrão, o arquivo de áudio da música de espera padrão, o período de tolerância da chamada de retorno do agente e a configuração de contexto de chamada. Você pode definir apenas um conjunto de configurações do aplicativo por pool. Para exibir as configurações do aplicativo, use o cmdlet **Get-CsRgsConfiguration**. Para modificar as configurações do aplicativo, use o cmdlet**Set-CsRgsConfiguration**.

A música de espera padrão é tocada quando uma chamada é coloca em espera, apenas se nenhuma música de espera personalizada for definida. O contexto de chamada está disponível somente para filas atribuídas aos fluxos de trabalho interativos. Se o contexto de chamada for ativado, um agente poderá ver informações como o tempo de espera do chamador ou perguntas e respostas do fluxo de trabalho quando a chamada for recebida.

## Para modificar as configurações do aplicativo do Grupo de Resposta

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute:
    
        Set-CsRgsConfiguration -Identity <name of service hosting Response Group> [-AgentRingbackGracePeriod <# seconds until call returns to agent after declined>] [-DefaultMusicOnHoldFile <audio file>] [-DisableCallContext <$true | $false>]
    
    Por exemplo:
    
        Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -AgentRingbackGracePeriod 30 -DisableCallContext $false
    
    Para especificar um arquivo de áudio para ser usado como a música de espera padrão, você precisa primeiro importar o arquivo de áudio. Por exemplo:
    
        $x = Import-CsRgsAudioFile -Identity "service:ApplicationServer:redmond.contoso.com" -FileName "MusicWhileYouWait.wav" -Content (Get-Content C:\Media\ MusicWhileYouWait.wav -Encoding byte -ReadCount 0)
        Set-CsRgsConfiguration -Identity "service:ApplicationServer:redmond.contoso.com" -DefaultMusicOnHoldFile <$x>

## Consulte Também

#### Outros Recursos

[Get-CsRgsConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration)  
[Set-CsRgsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsConfiguration)  
[Import-CsRgsAudioFile](https://docs.microsoft.com/powershell/module/skype/Import-CsRgsAudioFile)

