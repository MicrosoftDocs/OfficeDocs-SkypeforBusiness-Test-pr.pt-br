---
title: Gerenciando o Lync Online e o Microsoft Exchange da mesma sessão remota do Windows PowerShell
TOCTitle: Gerenciando o Lync Online e o Microsoft Exchange da mesma sessão remota do Windows PowerShell
ms:assetid: 4eb4b5f0-f407-46bd-a2ac-a7ccbc387d51
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362787(v=OCS.15)
ms:contentKeyID: 56270391
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando o Lync Online e o Microsoft Exchange da mesma sessão remota do Windows PowerShell

 

_**Tópico modificado em:** 2015-06-22_

Ao se inscrever para Office 365, você não só terá acesso ao Skype for Business Online, mas também terá acesso ao Exchange Online. Você pode usar uma sessão remota de Windows PowerShell para gerenciar Skype for Business Online. Você também pode usar uma sessão remota de Windows PowerShell para gerenciar Exchange. No entanto, Skype for Business Online e Exchange Online não compartilham a mesma URI, nem usam o mesmo método de conexão. Isso implica ue você precisa usar sessões separadas para gerenciar Skype for Business Online e Exchange. Há alguma forma de gerenciar os dois produtos usando uma única sessão remota de Windows PowerShell?

Como se vê, você não só pode gerenciar os dois produtos na mesma instância Windows PowerShell, pois definir essa sessão de gerenciamento duplo é incrivelmente fácil. Para começar, inicie Windows PowerShell e conecteao Skype for Business Online como você sempre faz: criar um objeto de Credenciais, e depois criar uma nova sessão que conecta ao Skype for Business Online:

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $lyncSession = New-CsOnlineSession -Credential $credential

Depois, utilize um processo similar para conectar ao Exchange Online. Veja que você não precisa criar um novo objeto de Credenciais. Você pode continuar usando o mesmo objeto ($credential) que vocÊ usou quando efetuou o login no Skype for Business Online:

    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection

Sempre use a URI https://outlook.office365.com/powershell-liveid/ ao se conectar ao Exchange Online e faça isso independentemente da URI do Office 365. Depois que for autenticado, você será redirecionado automaticamente para a URI apropriada. Isso torna especialmente importante a inclusão do parâmetro AllowRedirection. Se esse parâmetro for omitido, você será autenticado, mas o redirecionamento falhará e a conexão com o Exchange Online não será realizada:

    New-PSSession : [ps.outlook.com] The WinRM service cannot process the request because the request needs to be sent to a different machine. Use the redirect information to send the request to a new machine.  Redirect location reported: https://pod51043psh.outlook.com/powershell-liveid?PSVersion=3.0 . To automatically connect to the redirected URI, verify  MaximumConnectionRedirectionCount" property of session preference variable "PSSessionOption" and use "AllowRedirection" parameter on the cmdlet.

Nestet ponto, você deve ter duas sessões remotas funcionando no seu computador. Para verificar isto, insira o seguinte comando do prompt no Windows PowerShell :

    Get-PSSession

Você deverá ver informações similares para esta exibição na tela:

    Id Name      ComputerName  State   ConfigurationName     Availability
    -- ----      ------------  -----   -----------------     ------------
     1 Session1  pod510w43...  Opened  Microsoft.PowerShell     Available
     2 Session2  up02921vd...  Opened  Microsoft.Exchange       Available

Agora, você tem duas sessões remotas que podem ser importadas para a sua sessão local de Windows PowerShell. Para fazer isso, execute estes dois comandos:

    Import-PSSession $lyncSession
    Import-PSSession $exchangeSession

Agora, você terá ambos, Skype for Business Online e Exchange Online cmdlets estão disponíveis para o uso. Para verificar isto, execute o seguinte comando e certifique-se de que você recebeu as informações do usuário:

    Get-CsOnlineUser -ResultSize 1

Então, execute o seguinte comando Exchange e verifique se as informações estão na sua caixa de email:

    Get-Mailbox -ResultSize 1

Quando você quiser encerrar sua sessão de gerenciamento, certifique-se de que você fechou as duas sessões remotas:

    Remove-PSSession $lyncSession
    Remove-PSSession $exchangeSession

## Consulte Também

#### Conceitos

[Configurando o Computador Gerenciamento do Lync Online](configuring-your-computer-for-skype-for-business-online-management.md)

