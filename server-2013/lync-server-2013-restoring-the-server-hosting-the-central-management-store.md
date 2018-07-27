---
title: Restaurar o servidor que hospeda o Repositório de Gerenciamento Central
TOCTitle: Restaurar o servidor que hospeda o Repositório de Gerenciamento Central
ms:assetid: 3bd6c82c-07fb-4798-b8f9-e7c78a5a83d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202172(v=OCS.15)
ms:contentKeyID: 52057604
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurar o servidor que hospeda o Repositório de Gerenciamento Central

 

_**Tópico modificado em:** 2013-02-21_

Uma implantação do Lync Server tem um único Repositório de Gerenciamento Central, uma cópia replicada para cada servidor que executa uma função de servidor do Lync Server. Este tópico descreve como restaurar um Servidor Back-End ou um Servidor Standard Edition que hospeda o Repositório de Gerenciamento Central.

Para encontrar o pool onde o Servidor de Gerenciamento Central está localizado, abra o Construtor de Topologias, clique em **Lync Server** e procure no painel central em **Servidor de Gerenciamento Central**.

Se o Servidor de Back End que hospeda o repositório do Gerenciamento Central Server estiver em um banco de dados espelhado que ainda é funcional, recomendamos que você faça back-up do espelho ainda funcional e, então, faça uma restauração completa no banco de dados principal e no espelhado usando este backup ao seguir o procedimento de restauração abaixo. Isso é necessário porque a restauração do Back End requer a modificação e a publicação da topologia, e isso pode ser feito apenas se o banco de dados primário hospedando o CMS estiver operacional. Observe ainda que as funções de banco de dados primário e espelho não podem ser intercambiados se a topologia não puder ser publicada.

> [!NOTE]  
> Se um Servidor Back End ou um Servidor Standard Edition que não hospeda o Repositório de Gerenciamento Central falhou, consulte <a href="lync-server-2013-restoring-an-enterprise-edition-back-end-server.md">Restaurando um servidor de back-end do Enterprise Edition</a> ou <a href="lync-server-2013-restoring-a-standard-edition-server.md">Restaurando um servidor do Standard Edition</a>. Se um servidor de Back End que hospeda o repositório de Gerenciamento Central estiver em uma configuração espelhada e esse espelho falhar, consulte <a href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md">Restaurando um servidor back-end Enterprise Edition espelhado – espelho</a>. Se qualquer outro servidor tiver falhado, consulte <a href="lync-server-2013-restoring-an-enterprise-edition-member-server.md">Restaurando um servidor membro do Enterprise Edition</a>.


> [!TIP]
> Recomendamos fazer uma cópia da imagem do sistema antes de iniciar a restauração. Você pode usar essa imagem como um ponto de reversão caso algo dê errado durante a restauração. Convém tirar a cópia da imagem depois de instalar o sistema operacional e o SQL Server e restaurar ou registrar novamente os certificados.



## Para restaurar o Repositório de Gerenciamento Central

1.  Inicie com um servidor novo ou limpo que tenha o mesmo FQDN (nome de domínio totalmente qualificado) que o computador que falhou, instale o sistema operacional e, em seguida, restaure ou registre novamente os certificados.
    
    > [!NOTE]  
    > Siga os procedimentos de implantação do servidor da organização para executar esta etapa.

2.  Em uma conta de usuário que seja membro do grupo RTCUniversalServerAdmins e da Administração Local, faça logon no servidor que você está restaurando.

3.  Se você estiver restaurando um Servidor Standard Edition, restaure o Repositório de Arquivos, copiando o Repositório de Arquivos apropriado de $Backup para o local Repositório de Arquivos no servidor e, em seguida, compartilhe a pasta.
    
    > [!IMPORTANT]  
    > O caminho e o nome de arquivo para o Repositório de Arquivos restaurado deve ser exatamente o mesmo que o Repositório de Arquivos do backup para que os componentes que usam arquivos possam acessá-los.

4.  Siga um destes procedimentos:
    
      - Se você estiver instalando um Servidor Standard Edition, navegue até a pasta ou a mídia de instalação do Lync Server e inicie o Assistente de Implantação do Lync Server localizado em \\setup\\amd64\\Setup.exe. No Assistente de Implantação, clique em **Preparar primeiro servidor Standard Edition** e siga o assistente para instalar o Repositório de Gerenciamento Central.
    
      - Se você estiver instalando um Servidor Back-End Corporativo, instale o SQL Server 2012, o SQL Server 2012 R2 ou o SQL Server 2008 R2, mantendo os nomes de instância iguais estavam antes da falha.
        
        > [!NOTE]  
        > Dependendo do servidor que você está restaurando e da sua implantação, o servidor pode incluir vários bancos de dados colocados ou separados. Siga o mesmo procedimento para instalar o SQL Server que você usou originalmente para implantar o servidor, incluindo permissões de SQL Server e logons.

5.  De um Servidor de Front End, Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

6.  Recrie o Repositório de Gerenciamento Central. Na linha de comando, digite:
    
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
    
    Por exemplo:
    
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose

7.  Defina o ponto de controle Serviços de Domínio Active Directory para o Repositório de Gerenciamento Central. Na linha de comando, digite:
    
        Set-CsConfigurationStoreLocation -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
    
    Por exemplo:
    
        Set-CsConfigurationStoreLocation -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose
    
    > [!NOTE]  
    > Se você perder o ponto de conexão, poderá executar esse cmdlet novamente.

8.  Importe os dados do Repositório de Gerenciamento Central de $Backup. Na linha de comando, digite:
    
        Import-CsConfiguration -FileName <CMS backup file name>
    
    Por exemplo:
    
        Import-CsConfiguration -FileName "C:\Config.zip"

9.  Habilite as alterações feitas por você. Na linha de comando, digite:
    
        Enable-CsTopology
    
    > [!NOTE]  
    > Após habilitar a topologia, você pode encontrar o documento da topologia no banco de dados.

10. Se você estiver restaurando um Enterprise EditionServidor Back-End que também hospedou o CMS, ou precisa recriar um espelho do CMS, siga essas etapas. Caso contrário, pule para a etapa 11.
    
    Instale os bancos de dados independentes fazendo o seguinte:
    
    1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.
    
    2.  Clique em **Baixar Topologia da implantação existente** e clique em **OK**.
    
    3.  Selecione a topologia e clique em **Salvar**. Clique em **Sim** para confirmar sua seleção.
    
    4.  Clique com o botão direito do mouse no nó **Lync Server 2013** e clique em **Instalar banco de dados**.
    
    5.  Siga o assistente **Instalar banco de dados**. Se você estiver restaurando um banco de dados diferente do Repositório de Gerenciamento Centralneste servidor, na página **Criar bancos de dados**, selecione os bancos de dados que deseja recriar.
        
        > [!NOTE]  
        > Somente bancos de dados autônomos são exibidos na página <strong>Criar bancos de dados</strong>. Os bancos de dados colocados são criados quando você executa o Assistente de Implantação do Lync Server.    
    6.  Se você estiver restaurando um Servidor de Back End que era espelhado, continue a seguir o assistente até que a solicitação Criar banco de dados espelhado apareça. Selecione o banco de dados que deseja instalar e conclua o processo.
    
    7.  Siga o restante do assistente e clique em **Concluir**.
    

    > [!TIP]
    > Em vez de executar o Construtor de Topologias, você pode usar o cmdlet <STRONG>Install-CsDatabase</STRONG> para criar cada banco de dados, e o cmdlet <STRONG>Install-CsMirrorDatabase</STRONG> para configurar o espelhamento. Para obter detalhes, consulte <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Install-CsDatabase">Install-CsDatabase</A> e <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Install-CsMirrorDatabase">Install-CsMirrorDatabase</A>.



11. Se você estiver restaurando um Servidor Standard Edition, navegue para a pasta ou mídia de instalação do Lync Server e inicie o Assistente de Implantação do Lync Server localizado em \\setup\\amd64\\Setup.exe. Use o Assistente de Implantação do Lync Server para fazer o seguinte:
    
    1.  Execute **Etapa 1: Instalar Repositório de Configuração Local** para instalar os arquivos de configuração locais.
    
    2.  Execute **Etapa 2: Instalar ou Remover Componentes do Lync Server** para instalar as funções de servidor do Lync Server.
    
    3.  Execute **Etapa 3: Solicitar, Instalar ou Ceder Certificados** para atribuir os certificados.
    
    4.  Execute **Etapa 4: Iniciar Serviços** para iniciar serviços no servidor.
    
    Para obter detalhes sobre como executar o Assistente de Implantação, consulte a Documentação de implantação referente à função de servidor que você está restaurando.

12. Restaure dados do usuário executando o seguinte:
    
    1.  Copie ExportedUserData.zip de $Backup\\ para um diretório local.
    
    2.  Antes de restaurar os dados do usuário, você deve interromper os serviços do Lync. Para fazer isso, digite:
        
            Stop-CsWindowsService
    
    3.  Para restaurar os dados do usuário, na linha de comando, digite:
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        Por exemplo:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    4.  Reinicie os serviços do Lync digitando:
        
            Start-CsWindowsService

13. Restaure os dados de Informações de Local no Repositório de Gerenciamento Central. Na linha de comando, digite:
    
        Import-CsLisConfiguration -FileName <LIS backup file name>
    
    Por exemplo:
    
        Import-CsLisConfiguration -FileName "D:\E911Config.zip"

14. Se você implantou o Grupo de Resposta nesse pool ou o Servidor Standard Edition, restaure os dados de sincronização do Grupo de Resposta. Para obter detalhes, consulte [Restaurando as configurações do grupo de resposta](lync-server-2013-restoring-response-group-settings.md).

15. Se você estiver restaurando um Servidor Back-End que inclui os bancos de dados Arquivamento ou Monitoramento, restaure os dados de Arquivamento ou Monitoramento usando uma ferramenta de gerenciamento do SQL Server, como SQL Server Management Studio. Para obter detalhes, consulte [Restauração de monitoramento ou arquivamento de dados](lync-server-2013-restoring-monitoring-or-archiving-data.md).

