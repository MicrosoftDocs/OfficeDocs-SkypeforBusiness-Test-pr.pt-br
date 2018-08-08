---
title: "Lync Server 2013: (Opcional) Dar as boas-vindas aos usuários na confer. discada"
TOCTitle: (Opcional) Dar as boas-vindas aos usuários na conferência discada
ms:assetid: caa4fd61-f506-4c09-bb5b-1aa260d7a720
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398846(v=OCS.15)
ms:contentKeyID: 49308110
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Dar as boas-vindas aos usuários na conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Depois de configurar a conferência discada e de testar para verificar se ela está funcionando corretamente, defina PINs (números de identificação pessoal) para os usuários e notifique-os sobre a disponibilidade do recurso, incluindo instruções introdutórias como o PIN inicial e o link para a página da Web de Configurações da Conferência Discada. Esta etapa é opcional. Normalmente, você usa o cmdlet **Set-CsClientPin** para redefinir PINs, mas poderá usar o procedimento deste tópico na primeira vez se quiser enviar um email de boas-vindas junto com as informações. Se não quiser enviar o email, use **Set-CsClientPin**.

É possível usar o script **Set-CsPinSendCAWelcomeMail** para definir o PIN e enviar um email de boas-vindas para um único usuário. Por padrão, o script não redefine um PIN se ele já estiver definido, mas é possível usar o parâmetro **Force** para forçar a redefinição de um PIN. A mensagem de email é enviada usando o protocolo SMTP (Simple Mail Transfer Protocol).

É possível criar um script que executa o script **Set-CsPinSendCAWelcomeMail** iterativamente a fim de definir PINs e enviar email a um grupo de usuários. É possível modificar o modelo de email (ou seja, o arquivo **CAWelcomeEmailTemplate.html**) para adicionar mais links às páginas da intranet ou modificar o texto do email.

## Para definir um PIN inicial e enviar um email de boas vindas

1.  Faça logon como membro do grupo RTCUniversalServerAdmins.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Set-CsPinSendCAWelcomeMail -UserUri <user identifier>
        -From <email address of sender> [-Subject <subject for email message>]
        [-UserEmailAddress <destination email address>]
        [-Cc <email address of recipients who receive copy of email>]
        [-Bcc <email address of recipients who receive blind copies>]
        [-TemplatePath <path for email template>]
        [-SmtpServer] <SMTP server name>]
        [-BodyAsPlainText] [-UseSsl]
        [-Pin <new numeric PIN>] [-Force] `
        [-Credential <SMTP server credentials used to send email with the specified From address>]
    
    **SmtpServer**   Por padrão, o script usa o valor da variável de ambiente reservado **$PSEmailServer** para esse parâmetro. Se a variável **$PSEmailServer** não for definida, será necessário especificar esse parâmetro.
    
    **Credential**   Por padrão, o script usa as credenciais do usuário atual. Se o usuário atual não tiver permissão para enviar email em nome do endereço do remetente, será necessário especificar esse parâmetro. Como regra geral, especifique esse parâmetro se você não especificar seu endereço de email como o endereço do remetente.
    
    Por exemplo:
    
        Set-CsPinSendCAWelcomeMail -UserUri "bob@contoso.com"
        -From "marco@contoso.com"
    
    Esse exemplo cria um novo PIN e envia um email de boas-vindas de Marco para Bob. Ele usa o texto de email do modelo padrão e cria a mensagem de email no formato HTML. O Assunto padrão é "Bem-vindo à conferência discada".
    
    Outro exemplo:
    
        Set-CsPinSendCAWelcomeMail -UserUri "bob@contoso.com"
        -From "marco@contoso.com" -Subject "Your new dial-in conferencing PIN"
        -Pin "383042650" -Force
        -Credential Admin@contoso.com -UseSsl
    
    Esse exemplo força um novo PIN com um valor de "383042650" para Bob, embora Bob já tivesse um PIN existente, e envia um email de boas-vindas de Marco para Bob. Como o parâmetro Credential é especificado, a pessoa que está executando o comando recebe uma solicitação para digitar uma senha. O email é enviado usando SSL (Secure Sockets Layer).

