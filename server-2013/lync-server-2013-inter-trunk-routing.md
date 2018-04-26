---
title: 'Lync Server 2013: Roteamento entre troncos'
TOCTitle: Roteamento entre troncos
ms:assetid: f687a548-1f2e-48ed-9745-a13dc1f3698f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721940(v=OCS.15)
ms:contentKeyID: 49886488
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento entre troncos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-08_

O Lync Server 2013 fornece gerenciamento básico de sessão através do suporte a roteamento entre troncos. Esse novo recurso permite que o Lync Server ofereça funcionalidades de controle de chamada para sistemas de telefonia downstream. O roteamento entre troncos pode interconectar um IP-PBX a um gateway de rede de telefone pública comutada (PSTN) de forma que as chamadas de um telefone de central privada de comutação telefônica (PBX) possam ser encaminhadas para o PSTN, e as chamas PSTN de entrada possam ser encaminhadas para um telefone PBX. De maneira similar, o Lync Server pode interconectar dois ou mais sistemas IP-PBX para que as chamas possam ser feitas e recebidas entre telefones PBX de diferentes sistemas IP-PBX.

A imagem a seguir ilustra o Lync Server 2013 fornecendo interconectividade entre um gateway PSTN e um IP-PBX.

![Diagrama do gateway PSTN de conexão/IP-PBX do Lync Server](images/JJ721940.cc3858ca-2ee3-4d51-8a51-db078366b50b(OCS.15).jpg "Diagrama do gateway PSTN de conexão/IP-PBX do Lync Server")

A próxima imagem ilustra o Lync Server 2013 conectado a dois sistemas IP-PBX.

![Diagrama de sistemas IP-PAX de interconexão do Lync Server](images/JJ721940.6ba18ec9-df70-498a-9cf7-7fc41e5ec432(OCS.15).jpg "Diagrama de sistemas IP-PAX de interconexão do Lync Server")

