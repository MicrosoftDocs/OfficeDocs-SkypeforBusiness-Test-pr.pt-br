---
title: Definindo os computadores que serão monitorados no Lync Server
TOCTitle: Definindo os computadores que serão monitorados no Lync Server
ms:assetid: 9f1b2b91-d5af-42ad-a27d-b0815f762ad8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205118(v=OCS.15)
ms:contentKeyID: 49307615
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo os computadores que serão monitorados no Lync Server

 

_**Tópico modificado em:** 2012-10-20_

Como o Lync Server 2013não usa o processo de descoberta central usado no Microsoft Lync Server 2010, cada computador do Lync Server 2013 que você deseja monitorar deve poder auto-relatar sua existência ao servidor de gerenciamento. Para que isso seja possível, é necessário instalar os arquivos do agente Operations Manager em cada computador a ser monitorado. Após os arquivos do agente serem instalados, será necessário configurar o computador para agir como um proxy do System Center. Observe que esses procedimentos devem ser efetuados após a instalação e configuração do Lync Server nesses computadores.

