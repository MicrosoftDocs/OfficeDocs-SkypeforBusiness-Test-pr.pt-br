---
title: Conectando ao Lync Online Usando o Windows PowerShell
TOCTitle: Conectando ao Lync Online Usando o Windows PowerShell
ms:assetid: 6167dad9-9628-4fdb-bed1-bdb3f7108e64
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362795(v=OCS.15)
ms:contentKeyID: 56270397
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectando ao Lync Online Usando o Windows PowerShell

 

_**Tópico modificado em:** 2017-03-03_

Depois de você ter instalado o software de pré-requisitos, você está pronto para começar a usar o Windows PowerShell para gerenciar Skype for Business Online. Para fazer isso, você começa abrindo uma instância padrão de Windows PowerShell. Você não precisa abrir uma instância especial de Windows PowerShell (similar a, vamos dizer, o Shell de Gerenciamento do Lync Server), nem precisa abrir um aplicativo de Painel de Controle ou qualquer tipo especial de aplicativo. Isto é porque o gerenciamento Skype for Business Online é feito usando uma sessão remota de Windows PowerShell. Por sua vez, isso significa que:

1.  Você usa uma sessão regular de Windows PowerShell para conectar ao Skype for Business Online. Quando conectar remotamente, você trabalha no seu computador local e você usa sua cópia local do Windows PowerShell, mas vcê gerencia os objetos encontrados em um sistema remoto (que é, Skype for Business Online).

2.  Todos os cmdlets, scripts, e outros itens necessários para gerenciar Skype for Business Online são baixados para seu computador. Esses itens são mantidos na memória e estão disponíveis apenas na sessão remota estabelecida com Skype for Business Online. É importante manter isso em mente. Quando voce faz uma conexão remota para Skype for Business Online, os cmdlets Skype for Business Online —tais como [Get-CsTenant](get-cstenant.md)—será copiado, na memória, para seu computador. Na sua sessão remota, você será capaz de executar esses cmdlets. No entanto, esses cmdlets estão disponíveis apenas nesta sessão remota. Por exemplo, você pode iniciar uma segunda sessão de Windows PowerShell, mas sem conectar o Skype for Business Online nesta sessão. Se você tentar executar o cmdlet **Get-CsTenant** desta sessão, você receberá a seguinte mensagem de erro:
    
        Get-CsTenant : The term 'Get-CsTenant' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
    
    Além disso, observe que procurar no seu disco rígido pelo cmdlet **Get-CsTenant** (ou qualquer outro cmdlet Skype for Business Online) aparecerá vazio. Isso é porque nada é realmente salvo para seu hard disk quando você cria uma sessão remota.

3.  Quando você fecha sua sessão remota, os itens baixados são deletados da memória do seu computador. Por exemplo, você pode iniciar uma sessão remota de Windows PowerShell com o cmdlet **Get-CsTenant**, e fecha essa sessão. Se você reiniciar Windows PowerShell, o cmdlet **Get-CsTenant** não estará mais disponível. Para ter acesso ao cmdlet **Get-CsTenant**, você precisará se reconectar ao Skype for Business Online.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Se estiver trabalhando em uma implantação híbrida, você deve seguir os procedimentos destacados no artigo <a href="using-windows-powershell-in-a-hybrid-deployment-with-skype-for-business-online.md">Usando o Windows PowerShell em uma Implantação Híbrida</a>.</td>
</tr>
</tbody>
</table>


Para criar uma conexão remota para Skype for Business Online, comece iniciando uma nova sessão de Windows PowerShell no seu computador local. Se você estiver executando o Windows 7, o Windows Server 2008 R2, ou Windows Server 2012 ou Windows Server 2012 R2, faça o seguinte:

  - Clique em **Start**, click **All Programs**, click **Accessories**, click **Windows PowerShell**, and then click **Windows PowerShell**.

If you are executando o Windows 8 ou 8.1, faça isso:

  - Acesse a barra de botões, clique em **Pesquisar**, e então clique em **Windows PowerShell**. Você pode rapidamente acessar a barra de botões em qualquer computador do Windows 8 ou 8.1 (touch screen ou sem touch screen) segurando a tecla do Windows e pressionando C.

Depois que o console Windows PowerShell aparecer, você deve criar um objeto de credenciais Windows PowerShell. O objeto de credenciais é usado para transmitir com segurança seu nome de usuário e sua senha para Skype for Business Online. Para criar um objeto de credenciais, digite o seguinte comando no prompt Windows PowerShell e depois, pressione ENTER:

    $credential = Get-Credential

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Neste exemplo, seu nome de usuário e sua senha serão armazenados na variável $credential. Você pode nomear esta variável da forma que quiser, desde que sigas as regras dos nomes de variáveis para Windows PowerShell. No entanto, você deve usar uma variável de algum tipo para armazenar o nome de usuário e a senha. Caso contrário, o objeto de credenciais que você cria desaparecerão no momento em que for criado.</td>
</tr>
</tbody>
</table>


Depois, pressione ENTER, você deve ver a caixa de diálogo **Windows PowerShell de Credencial**:

![Credenciais de logon do Windows PowerShell](images/Dn362795.0f04e0a1-c9d6-4341-a0bb-ef721c4815fd(OCS.15).png "Credenciais de logon do Windows PowerShell")

Na caixa do **Nome do usuário**, digite seu nome de usuário Skype for Business Online. Na caixa da **Senha**, digite sua senha Skype for Business Online (a senha será marcarada e não aparecerá na tela). Por exemplo, se seu nome de usuário é pedrogoncalves@litwareinc.com e sua senha é p@ssw0rd\!, a caixa de diálogo parecerá com isso:

![Logon de credenciais do Windows PowerShell](images/Dn362795.85977a0e-b14a-4aec-a45e-8548e9c9f691(OCS.15).png "Logon de credenciais do Windows PowerShell")

Para criar o objeto de credenciais, clique em **OK**. Se você quiser verificar se o objeto foi criado, simplesmente digite o nome da variável no prompt Windows PowerShell e pressione ENTER:

    $credential

Windows PowerShell responderá mostrando algo similar a isso:

    UserName                            Password
    --------                            --------
    kenmyer@litwareinc.com              System.Security.SecureString

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Tenha em mente que o cmdlet <strong>Get-Credential</strong> aceita quaisquer credenciais que você digite e não tenta verificar se você inseriu um nome de usuário e uma senha válidos.Essa validação ocorrerá apenas quando você tentar efetuar o login em Skype for Business Online.</td>
</tr>
</tbody>
</table>


Depois de criar o objeto de credenciais, você pode criar uma nova sessão Windows PowerShell remota que faz uma conexão para Skype for Business Online. Para fazer isso, digite o seguinte comando no prompt Windows PowerShell e pressione ENTER:

    $session = New-CsOnlineSession -Credential $credential

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>$session é uma variável que é usada para reter informações - neste caso, as informações sobre a conexão para Skype for Business Online. De novo, Você pode dar a essa variável o nome que quiser, desde que o nome atenda as instruções de nome de variável Windows PowerShell (por exemplo, o nome não deve incluir espaços em branco ou pontuações).</td>
</tr>
</tbody>
</table>


Certifique-se de que você digitou o comando exatamente como é mostrado (com a possível exceção do nome da variável). Observe que não importa o nome de seu Skype for Business Online domínio. Independente do seu nome de domínio, o cmdlet **New-CsOnlineSession** vai conectá-lo ao Office 365 e efetuará o seu login usando as credenciais fornecidas. Depois de fazer a cnexão e autenticar, você será automaticamente redirecionado para a URl apropriada às credenciais fornecidas.

Se sua conexão acontecer, você verá mensagens similares a essa no console Windows PowerShell:

    VERBOSE: Determining domain to admin
    VERBOSE: AdminDomain = litwareinc.com
    VERBOSE: Discovering PowerShell endpoint URI
    VERBOSE: TargetUri = https://webdir0d.litwareinc.com/OcsPowerShellLiveId
    VERBOSE: Requesting authentication token
    VERBOSE: Success
    VERBOSE: Initializing remote session
    VERBOSE: Success
    Id Name       ComputerName    State        ConfigurationName     Availability -- ----       ------------    -----        -----------------     ------------
    2 Session2    litwarein...    Opened       Microsoft.PowerShell  Available

Agora, você está pronto para começar a usar o Windows PowerShell para gerenciar Skype for Business Online? Ainda não. O cmdlet **New-CsOnlineSession** se conecta ao Skype for Business Online e cria uma nova sessão para você. No entanto, você deve importar essa nova sessão para dentro do console Windows PowerShell. Faça isso executando o seguinte comando:

    Import-PSSession $session

Quando você pressiona ENTER, você verá um medidor de andamento similar a este exibido no console Windows PowerShell:

    Creating implicit remoting module . . .
         Getting command information from remote session . . . 16 commands  
              received
         [oooooooooooooooo
         00:00:33 remaining

O que acontece neste ponto é que Windows PowerShell está fazendo o download dos cmdlets e de outros itens, necessários para gerenciar o Skype for Business Online. Quando o download for concluído, você verá informação similar a esta no console Windows PowerShell:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enable-Cs ...}

Neste ponto, você está pronto para começar a usar Windows PowerShell para gerenciar Skype for Business Online. Para verificar que o download foi feito com sucesso, e para visualizar os cmdlets Skype for Business Online disponíveis para uso, primeiro, você deve determinar o nome do módulo Windows PowerShell temporário que contém todos os cmdlets Skype for Business Online. Para fazer isso, execute esse comando a partir do prompt Windows PowerShell:

    Get-Module

As informações similares às seguintes aparecerão na tela:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

O módulo com o Módulo Tipo Script é o módulo que contém os cmdlets Skype for Business Online. Para retornar uma lista deesses cmdlets, execute o cmdlet **Get-Command**, usando o nome de módulo Script como o nome do módulo:

    Get-Command -Module tmp_5astd3uh.m5v

Windows PowerShell deve ser exibida uma lista de todos os cmdlets Skype for Business Online.

Depois de concluir suas tarefas de gerenciamento, você deve sempre executar o seguinte comando, antes de fechar o console Windows PowerShell:

    Remove-PSSession $session

O cmdlet **Remove-PSSession** desconecta você do Skype for Business Online e fecha a sessão remota. De fato, se você tentar importar a sessão (executando o cmdlet **Import-PSSession**), você receberá a seguinte mensagem de erro:

    Import-PSSession : State of runspace is not valid for this operation.

Essa mensagem, simplesmente, significa que, para reconectar ao Skype for Business Online, você precisará criar uma nova sessão.

Se você esquecer de remover a sessão antes de fechar o console Windows PowerShell (ou se o console fechar inesperadamente), nada de ruim acontecerá. Depois de 15 minutos de inatividade, a sessão automaticamente se desconectará. No entanto, por padrão, cada administrador Skype for Business Online possui permissão para apenas três conexões simultâneas para Skype for Business Online. Se você fechar o console Windows PowerShell sem remover a sessão, essa sessão fecha coontinuará contando como uma conexão, mesmo se não estiver sendo usada no momento. (E continuará sendo contada como uma conexão até o tempo acabar.) Por exemplo, você deve abrir e fechar o console Windows PowerShell três vezes, cada vez sem remover a sessão Skype for Business Online. Se você abrir Windows PowerShell e tentar fazer uma quarta conexão, seu comando travará, e nenhuma conexão será feita.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Se Windows PowerShell travar enquanto estiver tentando fazerua conexão, pressione Ctrl-C para finalizar o comando travado.</td>
</tr>
</tbody>
</table>


enquanto os administradores individuais podem ter apenas três conexões simultâneas para um locatário Skype for Business Online, uma organização pode ter, no máximo, nove conexões simultâneas.O que significa que três administradores podem ter três conexões simultãneas cada, ou nove administradores poderiam ter uma conexão para Skype for Business Online, e assim por diante. No entanto, de novo, nenhum administrador individual pode ter mais do que três sessões ativas.

## Consulte Também

#### Conceitos

[Configurando o Computador Gerenciamento do Lync Online](configuring-your-computer-for-skype-for-business-online-management.md)

