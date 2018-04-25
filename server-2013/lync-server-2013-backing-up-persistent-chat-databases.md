---
title: Fazendo backup dos bancos de dados de chat persistente
TOCTitle: Fazendo backup dos bancos de dados de chat persistente
ms:assetid: b99ebdc0-a025-44d7-9d74-37a7365f330d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945646(v=OCS.15)
ms:contentKeyID: 52057716
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fazendo backup dos bancos de dados de chat persistente

 

_**Tópico modificado em:** 2013-02-17_

O conteúdo da sala do Chat Persistente está armazenado no banco de dados do Chat Persistente (Mgc.mdf). Deve-se gravar com frequência uma cópia de segurança desses dados que são corporativamente essenciais. Além do conteúdo da sala de chat, o banco de dados do Chat Persistente também armazena informações sobre os diretores (como usuários e grupos de usuários) e as funções e acesso que eles têm em relação às salas de chat e à sala de chat.

Há dois modos de realizar cópia de segurança dos dados do Chat Persistente.

  - Backup do SQL Server

  - O cmdlet `Export-CsPersistentChatData`, que exporta os dados do Chat Persistente como um arquivo

Dados criados pelo uso do backup do SQL Server requerem espaço em disco significativamente maior - possivelmente 20 vezes mais - que os dados criados pelo `Export-CsPersistentChatData`, mas o backup do SQL Server tem mais tendência a ser um procedimento com o qual os administradores já estejam familiarizados.

