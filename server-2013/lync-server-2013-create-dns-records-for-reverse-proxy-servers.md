---
title: 'Lync Server 2013: Criar registros de DNS para servidores de proxy reverso'
TOCTitle: Criar registros de DNS para servidores de proxy reverso
ms:assetid: b3513339-e49b-4665-80f1-b5a1c81a0e2e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429719(v=OCS.15)
ms:contentKeyID: 49307839
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar registros de DNS para servidores de proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-29_

Crie registros DNS A externos que apontam para a interface externa pública do seu Microsoft Internet Security and Acceleration (ISA) Server 2006 SP1 ou Forefront Threat Management Gateway 2010 Server ou Roteamento de Solicitação de Aplicativo do Servidor de Informação da Internet, como descrito em [Configurar DNS para suporte à borda no Lync Server 2013](lync-server-2013-configure-dns-for-edge-support.md). Você precisa de registros DNS para os FQDNs de serviço Web externos para cada pool, o Diretor (ou o Pool de diretores) e cada URL simples.

É necessário criar os seguintes registros para os registros DNS mínimos para a resolução de cliente do proxy reverso:

  - O(s) registro(s) do host (A) que definem os serviços Web externos publicados para os pools do Diretores e Diretor (por exemplo, **webdirext.contoso.com**)

  - O(s) registro(s) do host (A) que definem os serviços Web externos publicados para serviços Web externos hospedados em qualquer funções do Pools de Front-Ends e Servidor Standard Edition (por exemplo, **webext.contoso.com** )

  - Registros do host (A) para os URLs simples (por exemplo, **dialin.contoso.com** e **meet.contoso.com**)

  - Registro do host (A) para o registro do Lync Discover External e também fornece o ponteiro até AutoDiscover para todos os aplicativos Web, incluindo o Lync Web App, o agendador e a Mobilidade (por exemplo, **lyncdiscover.contoso.com**)

  - Registros do Host (A) para o Servidor Office Web Apps URL (por exemplo, **officewebapp01.contoso.com** )

Para obter detalhes, consulte [Resumo de DNS - Proxy reverso no Lync Server 2013](lync-server-2013-dns-summary-reverse-proxy.md).

