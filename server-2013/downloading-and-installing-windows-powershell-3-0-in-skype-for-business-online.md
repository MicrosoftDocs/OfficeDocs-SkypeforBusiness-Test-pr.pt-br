---
title: 'Lync Online: Baixando e instalando o Windows PowerShell 3.0'
TOCTitle: Baixando e instalando o Windows PowerShell 3.0
ms:assetid: 39ae065d-02d7-4ce3-9e6f-6ad550a1777e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362783(v=OCS.15)
ms:contentKeyID: 56270383
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Baixando e instalando o Windows PowerShell 3.0 no Lync Online

 

_**Tópico modificado em:** 2016-12-08_

Se você estiver usando o Windows Server 2012, Windows Server 2012 R2, Windows 8 ou Windows 8.1, já deverá ter o Windows PowerShell 3.0. Isso acontece porque esse aplicativo vem pré-instalado com esses sistemas operacionais.

Se estiver executando o Windows 7 ou o Windows Server 2008 R2, você também pode estar executando o Windows PowerShell 3.0. Entretanto, também é possível que você esteja executando a versão 2.0, a versão originalmente enviada com esses sistemas operacionais. Para determinar qual versão do Windows PowerShell você está usando, faça o seguinte em seu computador com Windows 7 ou com Windows Server 2008 R2:

1.  Clique em **Iniciar**, clique em Todos os Programas, clique em **Acessórios**, clique em **Windows PowerShell**, e então clique em **Windows PowerShell**.

2.  No console do Windows PowerShell, digite o comando a seguir e pressione ENTER:
    
        Get-Host | Select-Object Version

3.  Informações semelhantes às seguintes devem então ser exibidas na janela do console:
    
        Version
        -------
        3.0

Se o número de versão retornado for 3.0, você estará executando o Windows PowerShell 3.0. Se o número de versão retornado não for 3.0, será necessário instalar o Windows PowerShell 3.0. Você pode baixar o Windows Management Framework 3.0, que inclui o Windows PowerShell 3.0, do [Centro de Download da Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=34595).

Depois de verificar se o Windows PowerShell 3.0 está instalado, verifique se o Windows PowerShell foi configurado para executar scripts remotos. Para fazer isso, inicie o Windows PowerShell como administrador. No Windows 7, no Windows Server 2008 R2, Windows Server 2012 ou Windows Server 2012 R2, faça o seguinte:

1.  Clique em **Iniciar**, clique em **Todos os Programas**, clique em **Acessórios**, clique em **Windows PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e então clique em **Executar como administrador**.

2.  Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim** para verificar se deseja executar o Windows PowerShell com credenciais de administrador.

Se você estiver executando o Windows 8, conclua este procedimento:

1.  Acesse a barra Botões, clique em **Pesquisar** e então clique com o botão direito do mouse em **Windows PowerShell**. Você pode acessar rapidamente a barra Botões em qualquer computador com o Windows 8 (tela sensível ao toque ou não) ao manter a tecla do Windows pressionada e pressionando C.

2.  Na barra de ferramentas na parte inferior da tela, clique em **Executar como administrador**.

3.  Se a caixa de diálogo **Controle de Conta de Usuário** aparecer, clique em **Sim** para verificar se deseja executar o Windows PowerShell com credenciais de administrador.

Depois que o Windows PowerShell estiver em execução, você deverá alterar a política de execução para permitir a execução de scripts remotos. No console do Windows PowerShell, digite o comando a seguir e pressione ENTER:

    Set-ExecutionPolicy RemoteSigned -Force

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Quando você executar o comando anterior, talvez receba a seguinte mensagem de erro:<br />
Set-ExecutionPolicy: o acesso à chave do Registro 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Micrsoft.PowerShell' foi negado.<br />
Esta mensagem de erro normalmente ocorrerá se você não estiver executado o Windows PowerShell sob credenciais de administrador. Feche sua sessão do Windows PowerShell e inicie uma nova sessão como um administrador.</td>
</tr>
</tbody>
</table>


Para verificar se a política de execução foi configurada corretamente, digite o seguinte no prompt do Windows PowerShell e então pressione ENTER:

    Get-ExecutionPolicy

Se você obtiver o valor a seguir, então tudo terá sido configurado corretamente:

    RemoteSigned

Se você não estiver executando o Windows PowerShell 3.0 no momento, também precisará baixar e instalar o Windows Management Framework 3.0 do Centro de download da Microsoft. Esse é um pacote de instalação que inclui o Windows PowerShell 3.0 e o Windows Remote Management (WinRM) 3.0. Esse pacote de instalação poderá ser necessário caso você esteja executando o Windows 7 e ainda não tenha atualizado para o Windows PowerShell 3.0. Se você estiver executando o Windows Server 2012, Windows Server 2012 R2, Windows 8 ou Windows 8.1, não haverá necessidade de instalar o Windows PowerShell 3.0. O Windows PowerShell 3.0 vem pré-instalado nesses sistemas operacionais.

Antes de instalar o Windows Management Framework 3.0:

  - Verifique se baixou a versão correta do pacote de instalação. Se você estiver executando a versão de 64 bits do Windows 7, baixe o arquivo Windows6.1-KB2506143-x64.msu. Se estiver executando a versão de 32 bits do Windows 7, baixe o arquivo Windows6.1-KB2506143-x86.msu.

  - Se você estiver executando o Windows 7 em seu computador, verifique se instalou o Windows 7 Service Pack 1.

Se não tiver certeza de que versão do Windows esteja executando, ou se não tiver certeza de que instalou o Windows 7 Service Pack 1, clique em **Iniciar**, clique com o botão direito do mouse em **Computador** e então clique em **Propriedades**. Essas informações serão relatadas na caixa de diálogo System:

![Caixa de diálogo de sistema mostrando configurações](images/Dn362783.30bff2e8-2862-4dd7-828f-43732f4b9314(OCS.15).png "Caixa de diálogo de sistema mostrando configurações")

Para instalar o Windows Management Framework 3.0, conclua o seguinte procedimento:

1.  Clique duas vezes no arquivo de instalação .MSU ( **Windows6.1-KB2506143-x64.msu** ou **Windows6.1-KB2506143-x86.msu**).

2.  No assistente para Baixar e Instalar Atualizações, na página **Ler estes termos de licença (1 de 1)**, clique em **Aceito**.

3.  Quando a instalação estiver concluída, clique em **Reiniciar Agora** para reiniciar seu computador.

Após a reinicialização do computador, verifique se o Windows PowerShell poder ser iniciado e se o aplicativo pode ser executado sob credenciais administrativas. Para fazer isso:

1.  Clique em **Iniciar**, clique em **Todos os Programas**, clique em **Acessórios**, clique em **Windows PowerShell**, clique com o botão direito do mouse em **Windows PowerShell** e então clique em **Executar como administrador**.

2.  Se a caixa de diálogo Controle de Conta de Usuário aparecer, clique em **Sim** para verificar se você deseja executar o Windows PowerShell sob credenciais de administrador.

Quando o console do Windows PowerShell aparecer, verifique se o serviço WinRM está em execução e se foi configurado corretamente. Para verificar se o serviço está em execução, digite o comando a seguir no prompt do Windows PowerShell e então pressione ENTER:

    Get-Service winrm

Então, serão exibidas informações sobre o serviço WinRM na tela:

    Status   Name               DisplayName
    ------   ----               -----------
    Running  winrm              Windows Remote Management (WS-Manag...

Se o Status do serviço não for igual a "Em execução", inicie o serviço WinRM digitando o seguinte comando e pressionando ENTER:

    Start-Service winrm

Depois que o serviço tiver sido iniciado, execute o seguinte comando para garantir que o WinRM esteja usando a autenticação Básica:

    winrm set winrm/config/client/auth '@{Basic="True"}'

Informações semelhantes às seguintes deverão ser exibidas na tela:

    Auth
        Basic = true
        Digest = true
        Kerberos = true
        Negotiate = true
        Certificate = true
        CredSSP = false

Se a autenticação básica tiver sido definida como verdadeira, então você está pronto para usar o Windows PowerShell para se conectar ao Skype for Business Online.

