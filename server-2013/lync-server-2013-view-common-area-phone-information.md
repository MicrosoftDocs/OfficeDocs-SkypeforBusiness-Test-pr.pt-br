---
title: Exibir informações sobre os telefones de área comum
TOCTitle: Exibir informações sobre os telefones de área comum
ms:assetid: e652240c-6a3f-4be7-a083-32f24c08e655
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994081(v=OCS.15)
ms:contentKeyID: 52057744
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações sobre os telefones de área comum

 

_**Tópico modificado em:** 2013-02-20_

Você pode exibir informações sobre os telefones de área comum configurados para uso em sua organização utilizando o cmdlet **Get-CsCommonAreaPhone**. Usado sem nenhum parâmetro, este cmdlet retorna informações sobre todos os telefone de área comum. Parâmetros opcionais oferecem formas diferentes de filtrar as informações. Por exemplo, você pode retornar todos os telefones de área comum que tenham objetos de contato em uma UO (unidade organizacional) especificada ou todos os objetos de contato localizados em um edifício especificado. Para obter detalhes sobre os parâmetros **Get-CsCommonAreaPhone**, consulte [Get-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCommonAreaPhone).

Execute **Get-CsCommonAreaPhone** a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.


## Exibindo informações sobre todos os telefones de área comum

  - Para exibir informações sobre todos os seus telefones de área comum, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione Enter:
    
        Get-CsCommonAreaPhone
    
    Você obterá informações semelhantes a estas:
    
        Identity           : CN=Building 14 Lobby,OU=Redmond,
                             DC=litwareinc,DC=com
        RegistrarPool      : atl-cs-001.litwareinc.com
        Enabled            : True
        SipAddress         : sip:4714e34b-9781-421d-b07a-
                             52056b5b4a56@litwareinc.com
        ClientPolicy       :
        PinPolicy          :
        VoicePolicy        :
        MobilityPolicy     :
        GroupChatPolicy    :
        ConferencingPolicy :
        LineURI            : tel:+14255550712
        DisplayNumber      : 1-425-555-0712
        DisplayName        : Building 14 Lobby
        Description        :
        ExUmEnabled        : False

Para obter detalhes, consulte o tópico da Ajuda para o cmdlet [Get-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCommonAreaPhone).

