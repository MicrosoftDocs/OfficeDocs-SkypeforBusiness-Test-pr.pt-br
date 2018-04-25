---
title: Verificar o ambiente do Office Communications Server 2007 R2
TOCTitle: Verificar o ambiente do Office Communications Server 2007 R2
ms:assetid: e051bdd5-e7ef-4754-8705-900b2c57f37c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721906(v=OCS.15)
ms:contentKeyID: 49886446
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar o ambiente do Office Communications Server 2007 R2

 

_**Tópico modificado em:** 2012-10-16_

Antes de implantar o Lync Server 2013 em um estado de coexistência com o Office Communications Server 2007 R2, você precisa verificar se os serviços do Office Communications Server 2007 R2 estão configurados e foram iniciados.

**Verifique se o pool é iniciado usando a Ferramenta Administrativa do Office Communications Server 2007 R2**

1.  Abra a ferramenta administrativa do Office Communications Server 2007 R2.

2.  Expanda o nó **Floresta**, expanda o nó **ServidoresStandard Edition** ou **Pools Enterprise** e expanda o pool ou o nome do servidor.

3.  Certifique-se de que os serviços estejam sendo executado no servidor Standard Edition ou pool Enterprise.
    
    ![Console administrativo do Office Communications Server 2007 R2](images/JJ204914.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Console administrativo do Office Communications Server 2007 R2")

**Revisar os usuários configurados para o Office Communications Server 2007 R2**

1.  Abra a ferramenta administrativa do Office Communications Server 2007 R2.

2.  Expanda o nó **Floresta**, expanda o nó **ServidoresStandard Edition** ou **Pools Enterprise** e expanda o pool ou o nome do servidor.

3.  Clique em **Usuários**.

4.  Verifique a lista de usuários do Office Communications Server 2007 R2.
    
    ![Lista de usuários na ferramenta OCS Admin](images/JJ721906.f6bb7c4f-cbed-4389-8d0a-69a28577f17a(OCS.15).jpg "Lista de usuários na ferramenta OCS Admin")

**Verificar a Configuração do parceiro federado XMPP herdado**

1.  Do servidor de XMPP herdado, navegue para o applet Serviços/Ferramentas Administrativas.

2.  Verifique se o serviço de Gateway XMPP do Office Communications Server foi iniciado.
    
    ![Servidor de Gateway XMPP do Office Communications Server](images/JJ721906.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Servidor de Gateway XMPP do Office Communications Server")

