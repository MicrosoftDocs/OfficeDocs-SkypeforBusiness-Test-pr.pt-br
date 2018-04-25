---
title: 'Lync Server 2013: Componentes VoIP da rede de perímetro'
TOCTitle: Componentes VoIP da rede de perímetro
ms:assetid: 74230008-695d-436a-90b9-9cd060c70f7b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398559(v=OCS.15)
ms:contentKeyID: 49307119
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes VoIP da rede de perímetro do Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Os chamadores externos que utilizam os clientes de comunicação unificada para chamadas individuais ou em conferência contam com os Servidor de Borda para estabelecer comunicações de voz com colegas.

Em um Servidor de Borda, o serviço de Borda de Acesso fornece sinalização SIP para chamadas de usuários do Lync que estão fora do firewall da organização. O Serviço de Borda A/V permite o percurso de mídia de NAT e firewalls. Um chamador que usa um cliente UC (comunicações unificadas) de fora do firewall corporativo depende do serviço de Borda A/V para chamadas individuais e de conferência.

O serviço de Autenticação A/V está colocado no serviço de Borda A/V e fornece a este serviços de autenticação. Os usuários externos que tentam se conectar ao serviço de Borda A/V necessitam um token de autenticação fornecido pelo Serviço de Autenticação A/V, antes que suas chamadas possam ser feitas.

