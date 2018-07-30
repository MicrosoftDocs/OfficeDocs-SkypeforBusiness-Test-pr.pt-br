---
title: Aplicar uma política de arquivamento aos usuários
TOCTitle: Aplicar uma política de arquivamento aos usuários
ms:assetid: 624a7d3e-389d-403a-97e5-f7bb17023ef3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521004(v=OCS.15)
ms:contentKeyID: 49306901
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Aplicar uma política de arquivamento aos usuários

 

_**Tópico modificado em:** 2013-02-23_

Se um usuário tiver sido habilitado para o Lync Server 2013 e você tiver criado uma ou mais políticas de usuário para o arquivamento de usuários hospedados no Lync Server 2013, poderá implementar o suporte ao arquivamento para usuários específicos aplicando as políticas correspondentes a esses usuários ou grupos de usuários. Por exemplo, se você criar uma política para oferecer suporte ao arquivamento de comunicações internas, poderá aplicá-la a pelo menos um usuário ou grupo de usuários para oferecer suporte ao arquivamento das comunicações do Lync Server 2013 do usuário.

> [!NOTE]  
> Se você tiver habilitado a integração do Microsoft Exchange para sua implantação, as políticas de Bloqueio In-loco do Exchange controlarão se o arquivamento será habilitado para os usuários que estão hospedados no Exchange 2013 e cujas caixas de correio estão em Bloqueio In-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de implantação.<br />Você deve especificar todas as opções adequadas nas configurações de arquivamento antes de habilitar o arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools</a> na documentação de operações.

Use o procedimento descrito neste tópico para aplicar uma política de usuário de arquivamento criada anteriormente a uma ou mais contas de usuário ou a grupos de usuários.

## Para aplicar uma política de usuário de arquivamento a uma conta de usuário

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** e pesquise a conta de usuário que deseja configurar.

4.  Na tabela que lista os resultados da pesquisa, clique na conta do usuário, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar usuário do Lync Server** em **Política de arquivamento**, selecione a política de usuário de arquivamento que você deseja aplicar.
    
    > [!NOTE]  
    > As configurações <strong>&lt;Automáticas&gt;</strong> são aplicadas nas configurações da instalação do servidor padrão. Estas configurações são aplicadas automaticamente pelo servidor.

6.  Clique em **Confirmar**.

## Atribuindo uma política de arquivamento por usuário usando os cmdlets do Shell de Gerenciamento do Lync Server

As políticas de arquivamento por usuário também podem ser atribuídas com o uso do Lync ServerWindows PowerShell e do cmdlet **Grant-CsArchivingPolicy**. Você pode executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Atribuindo uma política de arquivamento por usuário a um único usuário

  - O comando a seguir atribui a política de arquivamento por usuário RedmondArchivingPolicy ao usuário Ken Myer.
    
        Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName "RedmondArchivingPolicy"

## Atribuindo uma política de arquivamento por usuário a vários usuários

  - Este comando atribui a política de arquivamento por usuário RedmondArchivingPolicy a todos os usuários que possuem contas hospedadas no pool de registradores atl-cs-001.litwareinc.com. Para obter detalhes sobre o parâmetro Filter usado nesse comando, consulte a documentação do cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser).
    
        Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Grant-CsArchivingPolicy -PolicyName "RedmondArchivingPolicy"

## Cancelando a atribuição de uma política de arquivamento por usuário

  - O comando a seguir cancela a atribuição de todas as políticas de arquivamento por usuário atribuídas anteriormente a Ken Myer. Após o cancelamento da atribuição da política por usuário, Ken Myer será automaticamente gerenciado pela política global ou pela política de seu site local (se houver uma). Uma política de site prevalece sobre a política global.
    
        Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName $Null

Para obter detalhes, consulte a documentação do [Grant-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsArchivingPolicy).

## Consulte Também

#### Outros Recursos

[Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)  
[Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

