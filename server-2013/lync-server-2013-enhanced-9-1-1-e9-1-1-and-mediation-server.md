---
title: 'Lync Server 2013: 9-1-1 Avançado (E9-1-1) e Servidor de Mediação'
TOCTitle: 9-1-1 Avançado (E9-1-1) e Servidor de Mediação
ms:assetid: d231221f-5596-4a87-a463-269f5bcce65f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398903(v=OCS.15)
ms:contentKeyID: 49308183
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 9-1-1 Avançado (E9-1-1) e Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-29_

O Servidor de Mediação ampliou suas capacidades para poder interagir corretamente com os provedores de serviço do E9-1-1. Nenhuma configuração especial é necessária no Servidor de Mediação; as extensões SIP necessárias para a interação com o E9-1-1 por padrão estão incluídas no protocolo SIP do Servidor de Mediação com um par de gateway (gateway PSTN, IP-PBX ou um SBC de um provedor de serviços de telefonia da Internet, incluindo provedores de serviços E9-1-1)

Se o tronco SIP para um provedor de serviço de E9-1-1 pode ser encerrado em um pool do Servidor de Mediação existente ou precisar de Servidores de Mediação autônomos dependerá se o E9-1-1 SBC pode interagir com um pool de Servidores de Mediação. Para obter detalhes, consulte [Tronco M:N no Lync Server 2013](lync-server-2013-m-n-trunk.md).

