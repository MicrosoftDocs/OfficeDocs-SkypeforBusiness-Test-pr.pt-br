---
title: Remover o banco de dados do Servidor SQL para um pool Front-End
TOCTitle: Remover o banco de dados do Servidor SQL para um pool Front-End
ms:assetid: 6bb932df-3ed7-49b6-ae17-61e4c6a5fe82
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688084(v=OCS.15)
ms:contentKeyID: 49886253
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover o banco de dados do Servidor SQL para um pool Front-End

 

_**Tópico modificado em:** 2012-10-04_

Depois de remover um Microsoft Lync Server 2010Pool de Front-Ends ou reconfigurar o pool para usar um banco de dados diferente, você pode remover os bancos de dados do SQL Server que hospedavam os dados do pool. Use os procedimentos a seguir para remover as definições do Construtor de Topologias e depois os arquivos de log e o banco de dados do servidor do banco de dados.

## Para remover o banco de dados do SQL Server usando o Construtor de Topologias

1.  No Servidor Front-End do Lync Server 2013, abra o Construtor de Topologias e baixe a topologia existente.

2.  Em Construtor de Topologias, navegue até **Componentes Compartilhados** e até **Repositórios do SQL Server**, clique com o botão direito do mouse na instância do SQL Server associada ao Pool de Front-Ends removido ou reconfigurado e clique em **Excluir**.

3.  Publique a topologia e verifique o status da replicação.

## Para remover os bancos de dados de usuário e de aplicativo do SQL Server

1.  Para remover os bancos de dados do SQL Server, você deve ser um membro do grupo sysadmins do SQL Server que você está removendo os arquivos do banco de dados.

2.  Abra o Shell de Gerenciamento do Lync Server

3.  Para remover o banco de dados do repositório de usuários do pool, digite:
    
        Uninstall-CsDataBase -DatabaseType User -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Onde o *\<FQDN\>* é o nome de domínio totalmente qualificado (FQDN) do servidor do banco de dados e o *\<instance\>* é a instância do banco de dados nomeado (isto é, se houver uma definida).

4.  Para remover o banco de dados do repositório de aplicativos do pool, digite:
    
        Uninstall-CsDataBase -DatabaseType Application -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Onde *\<FQDN\>* é o FQDN do servidor de banco de dados e *\<instância\>* é a instância de banco de dados nomeada (isto é, se houver uma definida).

5.  Quando o cmdlet **Uninstall-CsDataBase** solicitar que você confirme as ações, leia as informações e pressione **Y** (ou Enter) para continuar, ou pressione **N** e em seguida Enter se você deseja interromper o cmdlet (em caso de erros).

