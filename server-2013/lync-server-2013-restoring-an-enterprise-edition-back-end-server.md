---
title: Restaurando um servidor de back-end do Enterprise Edition
TOCTitle: Restaurando um servidor de back-end do Enterprise Edition
ms:assetid: 1450eb4e-3315-4d02-8f02-6e1791fb1550
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202163(v=OCS.15)
ms:contentKeyID: 52057557
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um servidor de back-end do Enterprise Edition

 

_**Tópico modificado em:** 2013-02-18_

Use o procedimento descrito neste tópico nos dois casos a seguir:

  - Tanto o banco de dados primário e espelhado quanto o Enterprise Edition Back End Server espelhado falhou.

  - Um Enterprise Edition Back End Server que não teve falha espelhada.

Se você tiver um Enterprise Edition Back End espelhado e apenas o banco de dados espelhado ou primário falhar, consulte [Restaurando um servidor back-end Enterprise Edition espelhado – primário](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md) para restaurar o banco de dados primário e [Restaurando um servidor back-end Enterprise Edition espelhado – espelho](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md) para restaurar o espelho.

Se o Repositório de Gerenciamento Central falhar, consulte [Restaurar o servidor que hospeda o Repositório de Gerenciamento Central](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md). Se um servidor membro do Enterprise Edition que não seja o Servidor de Back End falhar, consulte [Restaurando um servidor membro do Enterprise Edition](lync-server-2013-restoring-an-enterprise-edition-member-server.md).


> [!TIP]
> Recomendamos que você obtenha uma imagem de cópia do sistema antes de começar a restauração. Você pode usar essa imagem como ponto de reversão em caso de algo dar errado durante a restauração. Talvez você queira obter essa imagem depois de instalar o sistema operacional e o SQL Server, e restaurar ou registrar novamente os certificados.



## Para restaurar um Servidor de Back End do Enterprise Edition

1.  Comece com um servidor limpo ou novo que tenha o mesmo nome de domínio totalmente qualificado (FQDN) que o computador que falhou, instale o sistema operacional e restaure ou registre novamente os certificados.
    
    > [!NOTE]  
    > Siga os procedimentos de implantação de servidor da sua organização para realizar essa etapa.

2.  A partir de uma conta de usuário que seja membro do grupo RTCUniversalServerAdmins, faça logon no servidor que você está restaurando.

3.  Instale o SQL Server 2012 ou o SQL Server 2008 R2, mantendo os nomes de instância iguais a antes da falha.
    
    > [!NOTE]  
    > Dependendo da sua implantação, o Servidor de Back End pode incluir vários bancos de dados colocados ou separados. Siga o mesmo procedimento para instalar o SQL Server que você usou originalmente para implantar o servidor, incluindo as permissões e os logins do SQL Server.

4.  Depois de instalar o SQL Server, realize o seguinte:
    
    1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
    2.  Clique em **Baixar Topologia de uma implantação existente**, depois clique em **OK**.
    
    3.  Selecione a topologia, depois clique em **Salvar**. Clique em **Sim** para confirmar sua seleção.
    
    4.  Clique com o botão direito no nó **Lync Server 2013**, depois clique em **Publicar Topologia**.
    
    5.  Siga o assistente de **Publicar Topologia**. Na página **Criar bancos de dados**, selecione os bancos de dados que você deseja recriar.
        
        > [!NOTE]  
        > Somente bancos de dados autônomos são exibidos na página <strong>Criar bancos de dados</strong>.    
    6.  Se você estiver restaurando um Back End que era espelhado, continue a seguir o assistente até que a solicitação **Criar banco de dados espelhado** apareça. Selecione o banco de dados que deseja instalar e conclua o processo.
    
    7.  Siga o restante do assistente e clique em **Concluir**.
    

    > [!TIP]
    > Em vez de executar o Construtor de Topologias, você pode usar o cmdlet do <STRONG>Install-CsDatabase</STRONG> para criar cada banco de dados, e o cmdlet <STRONG>Install-CsMirrorDatabase</STRONG> para espelhamento da configuração. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.



5.  Restaure os dados de usuário fazendo o seguinte:
    
    1.  Copie o ExportedUserData.zip do $Backup\\ para um diretório local.
    
    2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.
    
    3.  Antes de restaurar os dados do usuário, você deve interromper os serviços do Lync. Para fazer isso, digite:
        
            Stop-CsWindowsService
    
    4.  Para restaurar os dados do usuário, na linha de comando, digite:
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        Por exemplo:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    5.  Reinicie os serviços do Lync digitando:
        
            Start-CsWindowsService

6.  Se você implantou o Grupo de Resposta neste pool, restaure os dados de configuração do Grupo de Resposta. Para obter informações detalhadas, consulte [Restaurando as configurações do grupo de resposta](lync-server-2013-restoring-response-group-settings.md).

7.  Se você estiver restaurando um Servidor de Back End que incluía os bancos de dados do Arquivamento ou do Monitoramento, restaure os dados do Arquivamento ou do Monitoramento usando uma ferramenta do SQL Server, como o SQL Server Management Studio. Para obter informações detalhadas, consulte [Restauração de monitoramento ou arquivamento de dados](lync-server-2013-restoring-monitoring-or-archiving-data.md).

