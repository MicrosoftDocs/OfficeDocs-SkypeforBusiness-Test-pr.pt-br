---
title: "Lync Server 2013: Usando Constr.r de Topol. p/ config. alta dispon. e recup. desastre"
TOCTitle: Usando o Construtor de Topologia para configurar alta disponibilidade e recuperação de desastre
ms:assetid: abc1a25d-1f5e-46ef-91d2-0144fc847206
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205172(v=OCS.15)
ms:contentKeyID: 49307763
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o Construtor de Topologia para configurar alta disponibilidade e recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

Execute as seguintes etapas no Construtor de Topologias para configurar a alta disponibilidade e a recuperação de desastres do Servidor de Chat Persistente.

1.  Adicione os bancos de dados espelho e o banco de dados secundário de envio de logs de repositórios do SQL Server.

2.  Edite as propriedades de serviço do Servidor de Chat Persistente para:
    
    1.  Ativar espelhamento do banco de dados primário.
    
    2.  Adicione o armazenamento SQL Server do espelho primário.
    
    3.  Ativar o banco de dados de envio de logs do SQL Server.
    
    4.  Adicionar o armazenamento SQL Server secundário de envio de logs do repositório do SQL Server.
    
    5.  Adicionar o espelho de armazenamento do SQL Server para o banco de dados secundário.
    
    6.  Publique a topologia.

