---
title: Remover banco de dados do SQL Server de um servidor de Monitoramento
TOCTitle: Remover banco de dados do SQL Server de um servidor de Monitoramento
ms:assetid: aed5e394-d63e-4ad4-af40-f12d3a044344
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721848(v=OCS.15)
ms:contentKeyID: 49886363
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover banco de dados do SQL Server de um servidor de Monitoramento

 

_**Tópico modificado em:** 2012-10-04_

Depois de remover um Microsoft Lync Server 2010  Servidor de Monitoramento, você pode remover os bancos de dados do SQL Server que hospedavam os dados do servidor. Use os seguintes procedimentos para remover as definições de Construtor de Topologias e remover o banco de dados e os arquivos de log do servidor de banco de dados.

## Para remover o banco de dados do SQL Server usando o Construtor de Topologias

1.  No servidor Front-End do Lync Server 2013, abra a Construtor de Topologias.

2.  Na Construtor de Topologias, navegue até **Componentes compartilhados** e depois **Repositórios do SQL Server** , clique com o botão direito na instância do SQL Server associada à Servidor de Monitoramento removida ou reconfigurada e clique em **Excluir** .

3.  Publique a topologia e verifique o status da replicação.

## Para remover os arquivos do banco de dados do SQL Server

1.  Para remover os bancos de dados em um servidor baseado no SQL Server, você deve ser membro do grupo sysadmins do SQL Server de onde está removendo os arquivos de banco de dados.

2.  Abra o Shell de Gerenciamento do Lync Server.

3.  Na linha de comando, digite o seguinte:
    
        Uninstall-CsDataBase -DatabaseType Monitoring -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    Onde *\<FQDN\>* é o nome de domínio totalmente qualificado (FQDN) do servidor de banco de dados e *\<instance\>* é a instância do banco de dados nomeada opcional.

4.  Quando o cmdlet **Uninstall-CsDataBase** solicitar que você confirme as ações, leia as informações e pressione **Y** (ou Enter) para continuar, ou pressione **N** e em seguida Enter se você deseja interromper o cmdlet (em caso de erros).

