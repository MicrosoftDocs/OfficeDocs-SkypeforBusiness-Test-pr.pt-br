---
title: Usando o Windows PowerShell em uma Implantação Híbrida
TOCTitle: Usando o Windows PowerShell em uma Implantação Híbrida
ms:assetid: b19625d4-4b68-403c-a072-5296aa590556
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362835(v=OCS.15)
ms:contentKeyID: 56270461
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o Windows PowerShell em uma Implantação Híbrida

 

_**Tópico modificado em:** 2015-06-22_

Em uma implantação híbrida, uma organização tem alguns usuários hospedados em uma versão local do Lync Server 2013 e outros hospedados no Skype for Business Online. É possível usar uma versão única do Windows PowerShell para gerenciar simultaneamente tanto a versão local do Lync Server quanto a do seu Skype for Business Online inquilino. Para isso, é necessário compreender dois fatores chave:

1.  Como executar uma conexão simultânea entre o Lync Server e o Skype for Business Online

2.  Como referenciar Skype for Business Online as configurações dessa conexão simultânea.

Criar uma conexão simultânea entre Lync Server e Skype for Business Online é surpreendentemente fácil. Conecte o Lync Server do jeito que você sempre faz, seja iniciando o Shell de Gerenciamento do Lync Server ou criando uma conexão remota do pool de Front-End. Depois de se conectar à versão local com êxito, Lync Server, faça a conexão com o Skype for Business Online usando o mesmo procedimento que usaria se estivesse se conectando somente ao Skype for Business Online. Para fazer essa conexão, você deve primeiro criar uma credencial do objeto Windows PowerShell usando as informações de logon do seu domínio do Office 365. Para isso, digite o seguinte no prompt Windows PowerShell e pressione ENTER:

    $credential = Get-Credential

Após pressinar ENTER, a caixa de diálogo da **Windows PowerShell Credencial** vai mostrar:

![Credenciais de logon do Windows PowerShell](images/Dn362795.0f04e0a1-c9d6-4341-a0bb-ef721c4815fd(OCS.15).png "Credenciais de logon do Windows PowerShell")

Na caixa **Nome de usuário** , digite o seu Skype for Business Online nome. Na caixa **Senha** , digite a sua Skype for Business Online senha (esta será ocultada e não estará visível na tela). Por exemplo, se o seu nome de usuário for alguém@exemplo.com e a sua senha for s3nh@\! a caixa de diálogo se parecerá com isto:

![Logon de credenciais do Windows PowerShell](images/Dn362795.85977a0e-b14a-4aec-a45e-8548e9c9f691(OCS.15).png "Logon de credenciais do Windows PowerShell")

Para criar as credenciais do objeto clique em **OK**. Depois de criar as credenciais do objeto você pode se conectar a Skype for Business Online executando o seguinte comando

    $session = New-CsOnlineSession -Credential $credential

Verifique se você digitou o comando exatamente como mostrado. Note que não importa qual o nome do seu domínio Skype for Business Online. O **New-CsOnlineSession** cmdlet conectará ao Office 365 e fará o login usando as credenciais fornecidas. Depois de conectar e fazer a autenticação, você será automaticamente encaminhado para o URI apropriado.

Se a conexão for bem-sucedida, uma mensagem similar a esta Windows PowerShell será mostrada no console:

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

Depois de estabelecer a conexão com o Skype for Business Online com sucesso, importe essa sessão executando um comando similar ao seguinte:

    Import-PSSession $session -AllowClobber

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>O parâmetro AllowClobber garante que todos os cmdlets Skype for Business Online sejam importados, incluindo os com o mesmo nome dos cmdlets Lync Server regulares. Haverá um grande número desses cmdlets porque a maioria dos parâmetros cmdlets Skype for Business Online, incluindo <a href="get-csmeetingconfiguration.md">Get-CsMeetingConfiguration</a>, <a href="new-csexumcontact.md">New-CsExUmContact</a>, <a href="remove-csvoicepolicy.md">Remove-CsVoicePolicy</a>, e assim por diante, tem um equivalente local. Os pares de cmdlet (por exemplo, o cmdlet Lync Server<strong>Get-CsMeetingConfiguration</strong> e o Skype for Business Online<strong>Get-CsMeetingConfiguration</strong>) são idênticos: não importa qual cmdlet seja usado. A única razão para usar o parâmetro AllowClobber é para prevenir que mensagens de aviso apareçam na sua tela.</td>
</tr>
</tbody>
</table>


Neste momento, você está pronto para começar a gerenciar tanto a versão local Lync Server quanto a Skype for Business Online. E pode ser que você também se pergunte: como diferenciar políticas e definições do Lync Server e do Skype for Business Online? Por exemplo, você pode querer alterar as definições da configuração global de reuniões. Para isso, execute este comando:

    Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False

Esse comando modifica as configurações globais. Mas que configurações, globais? Lync Server locais? Skype for Business Online? Ambas? Nenhuma?

Nesse caso em particular, as definições locais serão modificadas. E como isso acontece? Porque o parâmetro Tenant não estava incluído no comando. Se você está conectado simultaneamente a Lync Server local e a Skype for Business Online, os cmdlets que trabalham com qualquer plataforma serão executados em Lync Server, a menos que estes sejam configurados para não fazê-lo. E a única forma de configurá-los para tal é incluindo o parâmetro Tenant ao executar o comando. Por exemplo, esse comando atualiza configurações globais para o Skype for Business Online inquilino com o ID bf19b7db-6960-41e5-a139-2aa373474354:

    Set-CsMeetingConfiguration -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AdmitAnonymousUsersByDefault $False

O parâmetro Tenant é a chave. Esse comando retorna as políticas globais de acesso externo para Lync Server locais:

    Get-CsExternalAccessPolicy -Identity "global"

E esse comando retorna as políticas globais de acesso externo para o seu Skype for Business Online inquilino:

    Get-CsExternalAccessPolicy -Identity "global" -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Lembre-se de que há bem mais que 700 cmdlets locais. No entanto, a grande maioria desses cmdlets não tem um parâmetro Tenant, o que significa que eles não podem ser usados com Skype for Business Online. Note, também, que uma variedade de cmdlets de tem parâmetros Tenant, mas estes não estão disponíveis para uso com Skype for Business Online. Para recuperar o conjunto exato de cmdlets que podem ser usados com Skype for Business Online, execute este comando em Windows PowerShell prompt:

    Get-Module

Informações similares às seguintes serão mostradas na tela:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

O módulo junto ao Script ModuleType é o que contém os cmdlets Skype for Business Online. Para retornar uma lista com esses cmdlets, execute o cmdlet **Get-Command**, usando o nome do módulo Script como nome do módulo:

    Get-Command -Module tmp_5astd3uh.m5v

Windows PowerShell exibirá uma lista com todos os cmdlets Skype for Business Online cmdlets.

**Resolvendo Problemas de Conexão em uma Implantação Híbrida**

Em alguns casos, os administradores podem encontrar problemas para se conectar no Office 365 utilizando uma conta local (por exemplo, administrator@litwareinc.net) em vez de uma conta do Office 365 (como administrator@litwareinc.onmicrosoft.com). Se uma sincronização de diretório estiver funcionando adequadamente, então, você pode se conectar usando outra conta; essa é uma das vantagens de uma implantação híbrida. Entretanto, houve algumas instâncias em que um administrador não pôde se conectar usando sua conta local. Isso deve-se normalmente a uma descoberta automática que sinaliza a tentativa de conexão a uma instalação local do Lync Server em vez do Office 365.

Felizmente, há uma maneira simples de resolver esse problema. Ao usar o cmdlet **New-CsOnlineSession** para se conectar ao Office 365, inclua o parâmetro OverrideAdminDomain seguido pelo nome de domínio do Office 365. Por exemplo, para se conectar ao Office 365 usando account administrator@litwareinc.net, inclua o parâmetro OverrideAdminDomain seguido pelo nome de domínio litwareinc.onmicrosoft.com:

    $session = New-CsOnlineSession -Credential $credential -OverrideAdminDomain "litwareinc.onmicrosoft.com"

Esse comando direcionará a tentativa de conexão aos servidores do Office 365 e ao domínio litwareinc.onmicrosoft.com.

