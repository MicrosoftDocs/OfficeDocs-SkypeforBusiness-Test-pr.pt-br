---
title: Remover instâncias SQL Server de bancos de dados no Servidor Back-End
TOCTitle: Remover instâncias SQL Server de bancos de dados no Servidor Back-End
ms:assetid: 32457df9-7dd9-4fca-9362-ea4de26b0296
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688016(v=OCS.15)
ms:contentKeyID: 49886166
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover instâncias SQL Server de bancos de dados no Servidor Back-End

 

_**Tópico modificado em:** 2012-10-19_

Para usar outro banco de dados, remova os bancos de dados e as instâncias do Microsoft SQL Server depois de remover os servidores que executam o Lync Server 2010 dependentes desses servidores ou depois de reconfigurar os servidores que executam o Lync Server 2010. É preciso executar o procedimento deste tópico ao desativar o SQL Server atual ou reconfigurar o servidor atual que executa o Lync Server 2010 de uma forma que renderize os bancos de dados obsoletos ou indisponíveis.

Para remover os bancos de dados ou as instâncias da Servidor de Arquivamento ou da Servidor de Monitoramento, é preciso remover primeiro a função do servidor. Da mesma forma, para remover as instâncias ou os bancos de dados do Pool de Front-Ends, é preciso primeiro remover ou reconfigurar a função do servidor dependente. Esses procedimentos não fazem distinção entre bancos de dados colocados ou instâncias separadas. Os procedimentos não são afetados pela colocação do banco de dados.

## Nesta seção

  - [Remover o banco de dados do Servidor SQL para um pool Front-End](remove-the-sql-server-database-for-a-front-end-pool.md)

  - [Remover banco de dados do SQL Server de um servidor de Monitoramento](remove-the-sql-server-database-for-a-monitoring-server.md)

  - [Remover o banco de dados do Servidor SQL de um servidor de Arquivamento](remove-the-sql-server-database-for-an-archiving-server.md)

