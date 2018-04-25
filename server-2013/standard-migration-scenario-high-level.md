---
title: Cenário de migração padrão - nível alto
TOCTitle: Cenário de migração padrão - nível alto
ms:assetid: e768a7ca-44e3-4969-a6d9-7ed3e7029c5c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205354(v=OCS.15)
ms:contentKeyID: 49308443
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cenário de migração padrão - nível alto

 

_**Tópico modificado em:** 2013-01-30_

Use os itens a seguir como um ponto inicial ao migrar do Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2Chat de Grupo ao Lync Server 2013, Servidor de Chat Persistente. O caminho de migração padrão do Lync Server 2013 é como segue:

  - Sua organização anteriormente implantou Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2Chat de Grupo, e você deseja implantar Lync Server 2013, Servidor de Chat Persistente.

  - Implante Lync Server 2013, e então implante Pool de Servidor de Chat Persistente(s).

  - Prepare e planeje para migração de suas salas de Chat Persistente, e determine um horário adequado para desligar o sistema para migração.

  - Execute os cmdlets do Windows PowerShell para migração (**Export-CsPersistentChatData** e **Import-CsPersistentChatData**) para mover conteúdo ao Servidor de Chat Persistente.

  - Verifique se a migração foi bem-sucedida.

  - Encerre sua implantação herdada.

  - Configure o Servidor de Chat Persistente para que os clientes herdados possam se conectar ao Lync Server 2013, Servidor de Chat Persistente. Isso é necessário pois demora um tempo para implantar novos clientes, e você deseja permitir que os usuários existentes com clientes herdados tenham acesso às suas salas de chat o mais rápido possível.

  - Implante novos clientes, enquanto continua a ajudar a assegurar que trabalhadores com Chat de Grupo herdados (clientes) conseguem chegar às suas salas de chat.

