---
title: Personalizar a música de espera do estacionamento de chamada no Lync Server 2013
TOCTitle: Personalizar a música de espera do estacionamento de chamada no Lync Server 2013
ms:assetid: 3d78e6f9-a4ae-49f4-a89f-4515acb49dac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688031(v=OCS.15)
ms:contentKeyID: 49886186
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Personalizar a música de espera do estacionamento de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-10_

Você pode especificar seu próprio arquivo de música para utilizar para música em espera em vez do arquivo de música padrão que é enviado com Lync Server 2013. Para personalizar música em espera, utilize o cmdlet **Set-CsCallParkServiceMusicOnHoldFile**.

> [!NOTE]  
> Se você personalizar a música em espera e quiser a mesma música para diversos sites, você deve configurar o arquivo para cada site que executa o Aplicativo de Estacionamento de Chamada.

## Para personalizar o arquivo de música

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Set-CsCallParkServiceMusicOnHoldFile -Service <ServiceID where the Call Park application resides> -Content <Byte[]>
    

    > [!TIP]
    > Utilize o cmdlet <STRONG>Get-CsService</STRONG> para identificar o serviço. Para detalhes, consulte <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService">Get-CsService</A>.

    
    O exemplo a seguir mostra como obter o conteúdo de um arquivo, soothingmusic.wma, como uma matriz de byte e atribuí-lo a uma variável. Então, o arquivo de áudio é atribuído como o arquivo de música em espera para Estacionamento de Chamada. Para detalhes, consulte [Set-CsCallParkServiceMusicOnHoldFile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkServiceMusicOnHoldFile).
    
        $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
        Set-CsCallParkServiceMusicOnHoldFile -Service Redmond1-applicationserver-1 -Content $a

## Consulte Também

#### Outros Recursos

[Set-CsCallParkServiceMusicOnHoldFile](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkServiceMusicOnHoldFile)  
[Get-CsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService)

