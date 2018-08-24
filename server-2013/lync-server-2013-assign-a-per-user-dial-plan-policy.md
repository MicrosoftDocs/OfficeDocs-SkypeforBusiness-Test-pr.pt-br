---
title: Atribuir uma política de plano de discagem por usuário
TOCTitle: Atribuir uma política de plano de discagem por usuário
ms:assetid: 9fea861f-7770-4cae-9b1f-2a960595bfc9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688156(v=OCS.15)
ms:contentKeyID: 49886336
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma política de plano de discagem por usuário

 

_**Tópico modificado em:** 2013-02-22_

Para concluir a configuração de conta do usuário para usuários do Enterprise Voice ou de conferências discadas, o usuário deve receber um plano de discagem. As contas do usuário usarão automaticamente o plano de discagem global, se existir, ou o plano de discagem do site, quando você não atribuir explicitamente um plano de discagem por usuário. Se desejar usar o plano de discagem do site ou global para todos os usuários que estão habilitados para o Enterprise Voice, você poderá pular esta seção.

## Para atribuir um plano de discagem usando o Painel de Controle do Lync Server 2013

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou parte do nome de exibição, nome, sobrenome, nome da conta SAM, endereço SIP ou URI de linha da conta do usuário que deseja habilitar e clique em **Localizar**.

5.  Na tabela, clique na conta de usuário a qual deseja atribuir o plano de discagem.

6.  No menu **Editar**, clique em **Exibir detalhes**.

7.  Na página **Editar Lync Server**, em **Telefonia**, clique em **Enterprise Voice**.

8.  Clique em **Política do Plano de discagem** e depois escolha o plano de discagem desejado.

9.  Clique em **Confirmar**.

Para obter detalhes sobre a configuração de planos de discagem, consulte o tópico [Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md).

## Para atribuir um plano de discagem usando o Shell de Gerenciamento do Lync Server 2013

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para atribuir um plano de discagem específico do usuário, execute o seguinte no prompt de comando:
    
        Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
    
    Por exemplo:
    
        Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
    
    Neste exemplo, o usuário com o nome de exibição Bob Kelly é atribuído com o plano de discagem do usuário chamado **DialPlanJapan**.

Para obter detalhes sobre a atribuição de um plano de discagem do usuário ou sobre a execução do cmdlet **Grant-CsDialPlan**, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Atribuição de plano de discagem por usuário usando cmdlets do Windows PowerShell

Os planos de discagem por usuário podem ser também atribuídas usando o Windows PowerShell e o cmdlet **Grant-CsdialPlan**. Esse cmdlet pode ser executado tanto do Shell de Gerenciamento do Lync Server 2013 quanto de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuição de um plano de discagem por usuário a um único usuário

  - O comando a seguir atribui o plano de discagem por usuário RedmondDialPlan ao usuário Ken Myer.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName "RedmondDialPlan"

## Atribuição de plano de discagem por usuário a vários usuários

  - Esse comando atribui o plano de discagem por usuário RedmondDialPlan a todos os usuários que trabalham na cidade de Redmond. Para obter mais informações sobre o parâmetro LdapFilter usado nesse comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -LdapFilter "l=Redmond" | Grant-CsDialPlan -PolicyName "RedmondDialPlan"

## Desatribuição de um plano de discagem por usuário

  - O comando a seguir desatribui o plano de discagem por usuário anteriormente atribuído a Ken Myer. Depois que o plano de discagem por usuário é desatribuído, Ken Myer será automaticamente gerenciado usando um plano de discagem global (se existir), ou o plano de discagem de escopo de serviço atribuído ao seu Registrador ou gateway PSTN. Um plano de discagem de escopo de serviço tem precedência sobre qualquer plano de discagem local e um plano de discagem local tem precedência sobre o plano de discagem global.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName $Null

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Grant-CsDialPlan](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsDialPlan).

## Consulte Também

#### Outros Recursos

[Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md)  
[Contas de usuário habilitadas para Lync Server 2013](lync-server-2013-user-accounts-enabled-for-lync-server.md)

