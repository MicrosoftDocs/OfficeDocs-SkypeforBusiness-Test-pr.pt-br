---
title: "Lync Server 2013: Usando pool estend. de Chat Persist. p/ recup. de desastre"
TOCTitle: Usando o pool estendido de Chat Persistente Chat para recuperação de desastre
ms:assetid: 74c5287e-d70d-490a-9adc-ab419917ddd9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205007(v=OCS.15)
ms:contentKeyID: 49307128
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o pool estendido de Chat Persistente Chat para recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

A solução de recuperação de desastres para Servidor de Chat Persistente é criada com base em um Pool de Servidor de Chat Persistente expandido. Ela é semelhante à resiliência de site metropolitano no Lync Server 2010; porém, não há requisitos para uma VLAN (rede local virtual) expandida. Ao expandir o Pool de Servidor de Chat Persistente, você basicamente realiza a configuração lógica de um pool na topologia, mas posiciona os servidores fisicamente no pool em dois data centers diferentes. Configure o espelhamento do SQL Server para o banco de dados do mesmo modo e implante o banco de dados e o espelho no mesmo data center. Você deve configurar um banco de dados de backup no data center secundário (com um espelho opcional para fornecer alta disponibilidade durante a recuperação de desastres). Ele é o banco de dados de backup usado para failover durante a recuperação de desastres.

Para obter detalhes sobre como configurar o espelhamento do SQL Server para alta disponibilidade, consulte [Espelhamento de SQL Server no Lync Server 2013](lync-server-2013-sql-server-mirroring.md). Para obter detalhes sobre failover do banco de dados para recuperação de desastres, consulte [Configurando o envio de logs do SQL Server no Lync Server 2013 ao banco de dados primário do servidor de chat persistente](lync-server-2013-setting-up-sql-server-log-shipping-for-the-persistent-chat-server-primary-database.md) e [Configuração do Envio de Logs do Servidor SQL entre o espelho primário e o banco de dados secundário de Envio de Logs no Lync Server 2013](lync-server-2013-setting-up-sql-server-log-shipping-between-the-primary-mirror-and-the-log-shipping-secondary-database.md).

