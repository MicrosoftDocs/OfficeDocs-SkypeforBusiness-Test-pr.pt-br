---
title: "Atualizar um serv. Back End ou um serv. edição Standard no Lync Server 2013"
TOCTitle: "Atualizar um serv. Back End ou um serv. edição Standard no Lync Server 2013"
ms:assetid: f95f8d3a-e039-484e-97bd-d727db21a12b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721942(v=OCS.15)
ms:contentKeyID: 49886490
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atualizar um servidor Back End ou um servidor edição Standard no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Este tópico explica como instalar uma atualização em um Enterprise EditionServidor Back-End ou um servidor Standard Edition.

Se o servidor Back End estiver inoperante por ao menos 30 minutos enquanto você o estiver atualizando, os usuários podem entrar em modo de resiliência. Quando a atualização for concluída e os servidores Back End tiver novamente se conectado aos servidores Front End no pool, os usuários são retornados à funcionalidade total. Se a atualização levar menos de 30 minutos, os usuários não serão afetados.

## Para atualizar um servidor Back End ou um servidor edição Standard

1.  Faça logon no servidor que você estiver atualizando como um membro da função CsAdministrator.

2.  Faça o download do pacote de atualizações e extraia os arquivos para um disco rígido local.

3.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

4.  Pare os serviços do Lync Server. Na linha de comando, digite:
    
        Stop-CsWindowsService

5.  Pare o serviço World Wide Web. Na linha de comando, digite:
    
        net stop w3svc

6.  Feche todas as janelas do Shell de gerenciamento do Lync Server.

7.  Atualize a atualização.

8.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

9.  Pare os serviços do Lync Server novamente para capturar os conjuntos GAC (cache de assembly global) –d. Na linha de comando, digite:
    
        Stop-CsWindowsService

10. Reinicie o serviço World Wide Web. Na linha de comando, digite:
    
        net start w3svc

11. Aplique as alterações feitas pelo LyncServerUpdateInstaller.exe para os bancos de dados SQL Server por meio de uma das seguintes ações:
    
      - Se for um Enterprise EditionServidor Back-End e não houver bancos de dados colocados neste servidor, como os bancos de dados de Arquivamento e Monitoramento, digite o seguinte na linha de comando:
        
            Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>
    
      - Se for um Enterprise EditionServidor Back-End e houver bancos de dados colocados neste servidor, digite o seguinte na linha de comando:
        
            Install-CsDatabase -Update -ConfiguredDatabases -SqlServerFqdn <SQL Server FQDN>  -ExcludeCollocatedStores
    
      - Se for um servidor Standard Edition, digite o seguinte na linha de comando:
        
            Install-CsDatabase -Update -LocalDatabases

