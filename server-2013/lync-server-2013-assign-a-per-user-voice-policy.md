---
title: Atribuir uma política de voz por usuário
TOCTitle: Atribuir uma política de voz por usuário
ms:assetid: 9ee47ee7-1030-43b8-a4dc-bf685ea24659
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688155(v=OCS.15)
ms:contentKeyID: 49886334
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de voz por usuário

 

_**Tópico modificado em:** 2013-02-22_

As políticas de voz global e no nível do site são automaticamente atribuídas a todas as contas de usuários do Lync Server 2013 habilitadas para Enterprise Voice. Você também pode atribuir políticas de voz a usuários específicos usando o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013. Use os procedimentos neste tópico para atribuir explicitamente políticas por usuário a usuários do Lync Server.

## Para atribuir uma política de voz específica do usuário usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** e pesquise a conta de usuário que deseja configurar.

4.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar Usuário do Lync Server**, em **Política de voz**, selecione a política de usuário que você deseja aplicar.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> são aplicadas nas configurações do servidor padrão ou de política global.

## Para atribuir uma política de voz específica do usuário usando o Shell de Gerenciamento do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para atribuir uma política de voz do usuário existente para um usuário, execute o seguinte no prompt de comando:
    
        Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
    
    Por exemplo:
    
        Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
    
    Neste exemplo, o usuário com o nome de exibição Bob Kelly é atribuído com a política de voz chamada **VoicePolicyJapan**.

Para obter detalhes sobre a atribuição de uma política de voz específica do usuário ou sobre a execução do cmdlet **Grant-CsVoicePolicy**, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Atribuição de política de voz por usuário usando cmdlets do Windows PowerShell

As políticas de voz por usuário podem ser também atribuídas usando o Windows PowerShell e o cmdlet **Grant-CsVoicePolicy**. Esse cmdlet pode ser executado tanto do Shell de Gerenciamento do Lync Server 2013 quanto de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuição de política de voz por usuário a um único usuário

  - O comando a seguir atribui a política de voz por usuário RedmondVoicePolicy ao usuário Ken Myer.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

## Atribuição de política de voz por usuário a vários usuários

  - Esse comando atribui a política de voz por usuário FinanceVoicePolicy a todos os usuários que tenham contas no OU de finanças no Active Directory. Para obter mais informações sobre o parâmetro OU usado nesse comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName "FinanceVoicePolicy"

## Desatribuição de uma política de voz por usuário

  - O comando a seguir desatribui a política de voz por usuário anteriormente atribuída a Ken Myer. Depois que a política de voz por usuário é desatribuida, Ken Myer será automaticamente gerenciado usando uma política global ou, se existir, a política do seu site local. A política de site tem precedência sobre a política global.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Grant-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsVoicePolicy).

## Consulte Também

#### Tarefas

[Desabilitar um usuário para o Enterprise Voice](lync-server-2013-disable-a-user-for-enterprise-voice.md)  

#### Outros Recursos

[Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md)

