---
title: 'Lync Server 2013: Criar um comunicado'
TOCTitle: Criar um comunicado
ms:assetid: a6fd5922-fe46-41ba-94e3-c76b1101a31b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412783(v=OCS.15)
ms:contentKeyID: 49307714
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Para criar um novo comunicado, é necessário executar as seguintes etapas:

1.  Para prompts de áudio, grave o arquivo de áudio usando seu aplicativo de gravação de áudio favorito.

2.  Para prompts de áudio, execute o cmdlet **Import-CsAnnouncementFile** para importar o conteúdo do arquivo de áudio para o Repositório de Arquivos.

3.  Execute o cmdlet **New-CsAnnouncement** para criar e nomear o comunicado. Execute esta etapa para criar comunicados com um prompt de áudio, um prompt TTS (text-to-speech), ou sem prompt.
    

    > [!TIP]
    > Pode ser desejável criar um comunicado sem prompt (por exemplo, se você deseja transferir chamadas para um destino específico sem reproduzir uma mensagem).



4.  Atribua o novo comunicado a um intervalo numérico na tabela de números não atribuídos.

Este tópico descreve como importar e criar comunicados. Para obter detalhes sobre como atribuir comunicados na tabela de números não atribuídos, consulte [Configurar a tabela de número não atribuído no Lync Server 2013](lync-server-2013-configure-the-unassigned-number-table.md).

## Para criar um novo comunicado

1.  Para prompts de áudio, crie o arquivo de áudio.

2.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Para prompts de áudio, execute:
    
        Import-CsAnnouncementFile -Parent <service of the Application Server running the Announcement application> -FileName <name for file in File Store> -Content Byte [<contents of file in byte array>]

5.  Execute:
    
        New-CsAnnouncement -Parent <service of Application Server running the Announcement application, in the form: service:ApplicationServer:<fqdn>> -Name <unique name to be used as destination in unassigned number table> [-AudioFilePrompt <FileName specified in Import-CsAnnouncementFile>] [-TextToSpeechPrompt <text string to be converted to speech>] [-Language <Language for playing the TTS prompt (required for PromptTts)>] [-TargetUri sip:SIPAddress for transferring caller after announcement]
    
    Para transferir chamadas para a caixa postal, digite o SIPAddress no formato sip:nomedousuário@nomedodomínio;opaque=app:voicemail (por exemplo, sip:bob@contoso.com;opaque=app:voicemail). Para transferir chamadas para um número de telefone, digite o SIPAddress no formato sip:número@nomedodomínio;user=phone (por exemplo, sip:+ 14255550121@contoso.com;user=phone).
    
    Por exemplo, para especificar um prompt de áudio:
    
        $a = Get-Content ".\PromptFile.wav" -ReadCount 0 -Encoding Byte
        Import-CsAnnouncementFile -Parent service:ApplicationServer:pool0@contoso.com -FileName "ChangedNumberMessage.wav" -Content $a
        New-CsAnnouncement -Parent service:ApplicationServer:pool0.contoso.com -Name "Number Changed Announcement" -AudioFilePrompt "ChangedNumberMessage.wav"
    
    Por exemplo, para especificar um prompt TTS:
    
        New-CsAnnouncement -Parent service:ApplicationServer:pool0.contoso.com -Name "Help Desk Announcement" -TextToSpeechPrompt "The Help Desk number has changed. Please dial 5550100." -Language "en-US"
    
    Para mais detalhes sobre estes cmdlets e para ver uma lista dos códigos de linguagem a serem usados no parâmetro **TextToSpeechPrompt**, consulte [New-CsAnnouncement](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAnnouncement).

## Consulte Também

#### Outros Recursos

[Import-CsAnnouncementFile](https://docs.microsoft.com/en-us/powershell/module/skype/Import-CsAnnouncementFile)  
[New-CsAnnouncement](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAnnouncement)  
[Configurar a tabela de número não atribuído no Lync Server 2013](lync-server-2013-configure-the-unassigned-number-table.md)

