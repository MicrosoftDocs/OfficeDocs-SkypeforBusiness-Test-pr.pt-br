---
title: Remover o banco de dados do Servidor SQL de um servidor de Arquivamento
TOCTitle: Remover o banco de dados do Servidor SQL de um servidor de Arquivamento
ms:assetid: 6e8a1fcd-ed09-43b0-82c9-60e7ce116a01
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688087(v=OCS.15)
ms:contentKeyID: 49886257
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover o banco de dados do Servidor SQL de um servidor de Arquivamento

 

_**Tópico modificado em:** 2012-10-04_

Depois de remover um Servidor de Arquivamento do Microsoft Lync Server 2010, você pode remover os bancos de dados do SQL Server que hospedaram os dados do pool. Use os procedimentos a seguir para remover as definições de Construtor de Topologias e, em seguida, remova o banco de dados e os arquivos de log do servidor de banco de dados.

## Para remover o banco de dados do SQL Server usando o Construtor de Topologias

1.  No servidor Front-End do Lync Server 2013, abra a Construtor de Topologias.

2.  Em Construtor de Topologias, navegue até **Componentes Compartilhados** e até **Repositórios do SQL Server**, clique com o botão direito na instância do SQL Server associada ao Servidor de Arquivamento removido ou reconfigurado e clique em **Excluir**.

3.  Publique a topologia e verifique o status da replicação.

## Para remover os arquivos do banco de dados do SQL Server

1.  Para remover os bancos de dados do SQL Server, você deve ser um membro do grupo sysadmins do SQL Server que você está removendo os arquivos do banco de dados.

2.  Abra o Shell de Gerenciamento do Lync Server.

3.  Na linha de comando, digite o seguinte:
    
        Uninstall-CsDataBase -DatabaseType Archiving -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Onde o *\<FQDN\>* é o nome de domínio totalmente qualificado (FQDN) do servidor do banco de dados e o *\<instance\>* é a instância do banco de dados nomeado (isto é, se houver uma definida).

4.  Quando o cmdlet **Uninstall-CsDataBase** solicitar que você confirme as ações, leia as informações e pressione **Y** (ou Enter) para continuar, ou pressione **N** e em seguida Enter se você deseja interromper o cmdlet (em caso de erros).

