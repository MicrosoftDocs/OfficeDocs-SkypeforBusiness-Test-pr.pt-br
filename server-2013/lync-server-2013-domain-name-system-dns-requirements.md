---
title: Requisitos de DNS (Sistema de Nomes de Domínio)
TOCTitle: Requisitos de DNS (Sistema de Nomes de Domínio)
ms:assetid: 586cf18e-0080-4eb1-aee5-56843277fdfc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398386(v=OCS.15)
ms:contentKeyID: 49306776
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de DNS (Sistema de Nomes de Domínio)

 

_**Tópico modificado em:** 2012-06-18_

Para implantar o Lync Server, crie registros de DNS (Sistema de Nomes de Domínio) que habilitem a descoberta de clientes e servidores e, opcionalmente, ofereçam suporte à entrada automática no cliente (se a sua organização oferecer suporte a esse recurso).

O Lync Server usa o DNS das seguintes maneiras:

  - Para descobrir pools ou servidores internos para a comunicação entre servidores.

  - Para permitir que clientes descubram o Pool de Front-Ends ou o Servidor Standard Edition usado em diversas transações SIP.

  - Para permitir que os dispositivos UC (comunicações unificadas) que não estão conectados descubram o Pool de Front-Endsou o Servidor Standard Edition que executa o serviço Web de Atualização de Dispositivo, obtenham atualizações e enviem logs.

  - Para permitir que os servidores e clientes externos se conectem aos Servidores de Borda ou ao proxy reverso HTTP para fazer uso de mensagens instantâneas ou conferências.

  - Para permitir que os dispositivos de UC externos se conectem ao Serviço Web de Atualização de Dispositivo por meio de Servidores de Borda ou do proxy reverso HTTP e obtenham atualizações.

  - Para permitir que clientes móveis descubram automaticamente os recursos dos Serviços Web sem exigir que os usuários insiram URLs manualmente nas configurações do dispositivo.

## Nesta seção

  - [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

  - [Requisitos de DNS para pools de front-end](lync-server-2013-dns-requirements-for-front-end-pools.md)

  - [Requisitos DNS para servidores do Standard Edition](lync-server-2013-dns-requirements-for-standard-edition-servers.md)

  - [Requisitos de DNS para URLs simples no Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [Requisitos DNS para conexão automática de clientes no Lync Server 2013](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)

  - [Requisitos DNS para mobilidade](lync-server-2013-dns-requirements-for-mobility.md)

  - [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md)

