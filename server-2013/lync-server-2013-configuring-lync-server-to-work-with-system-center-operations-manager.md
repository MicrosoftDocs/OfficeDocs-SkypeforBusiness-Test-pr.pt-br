---
title: Configurando o Lync Server para Trabalhar com System Center Operations Manager
TOCTitle: Configurando o Lync Server para Trabalhar com System Center Operations Manager
ms:assetid: b55a24ab-648b-4142-b3cd-3792860ba872
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205188(v=OCS.15)
ms:contentKeyID: 49307853
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Lync Server para Trabalhar com System Center Operations Manager

 

_**Tópico modificado em:** 2012-10-22_

Para configurar a infraestrutura do Microsoft Lync Server 2013 a fim de trabalhar com o System Center Operations Manager é necessário executar estes três procedimentos:

  - Identificar e configurar seu servidor de gerenciamento primário do System Center Operations Manager. A configuração do servidor de gerenciamento inclui a instalação do System Center Operations Manager 2012 ou do System Center Operations Manager 2007 R2, bem como configurar um banco de dados de back-end usando o SQL Server. A versão do SQL Server que você deve usar depende da versão do System Center Operations Manager que estiver usando. Para obter detalhes, consulte [Configurando o Servidor de Gerenciamento Primário](lync-server-2013-configuring-the-primary-management-server.md).

  - Identifique e configure os computadores do Lync Server que você deseja monitorar. Para monitorar um computador do Lync Server usando o System Center Operations Manager você deve instalar os arquivos do agente do System Center Operations Manager e configurar cada servidor para atuar como um proxy.

  - Identifique e configure os computadores que você deseja que atuem como Lync Server*nós do inspetor*. Os nós do inspetor são computadores que executam periodicamente transações sintéticas do Lync Server, que são cmdlets do Windows PowerShell que verificam se os componentes-chave do Lync Server, como a capacidade de entrar no sistema ou de trocar mensagens instantâneas estão funcionando como esperado.

Os tópicos nesta seção contêm instruções para executar cada uma dessas tarefas.

## Nesta seção

  - [Configurando o Servidor de Gerenciamento Primário](lync-server-2013-configuring-the-primary-management-server.md)

  - [Instalando os pacotes de gerenciamento do Lync Server 2013](lync-server-2013-installing-the-lync-server-2013-management-packs.md)

  - [Definindo os computadores que serão monitorados no Lync Server](lync-server-2013-configuring-the-lync-server-computers-that-will-be-monitored.md)

  - [Instalando e configurando os nós do inspetor](lync-server-2013-installing-and-configuring-watcher-nodes.md)

