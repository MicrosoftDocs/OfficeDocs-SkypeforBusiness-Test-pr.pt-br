---
title: Monitorando a mobilidade de desempenho no Lync Server 2013
TOCTitle: Monitorando a mobilidade de desempenho no Lync Server 2013
ms:assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690033(v=OCS.15)
ms:contentKeyID: 49307609
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitorando a mobilidade de desempenho no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-14_

O Serviço de Mobilidade do Lync Server aumenta a carga no Servidores Front-End e no Pools de Front-Ends. Dispositivos móveis que mantêm uma conexão com o servidor mesmo quando o aplicativo móvel está minimizado, como dispositivos Android e Nokia, impõem uma carga maior do que dispositivos que encerram suas conexões com o servidor quando o aplicativo móvel está minimizado. Conforme seu uso de mobilidade cresce, é necessário monitorar o desempenho da mobilidade para determinar quando é necessário aumentar a capacidade.

Vários limites influenciam o desempenho da mobilidade:

  - Memória disponível

  - Limite da fila de solicitações

  - Conexões concorrentes

  - Tamanho da fila do IIS

Outros limites em servidores que podem influenciar o desempenho da mobilidade são um máximo de vinte conexões concorrentes, autenticações e renovações e encerramentos de sessão. Esses máximos não precisam ser modificados para a maioria das implantações.

## Nesta seção

  - [Monitoramento de limites de capacidade de memória do servidor](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

  - [Monitorando o uso do serviço de mobilidade e do UCWA](lync-server-2013-monitoring-mobility-service-and-ucwa-usage.md)

  - [Configurando o serviço de mobilidade para alto desempenho](lync-server-2013-configuring-mobility-service-for-high-performance.md)

  - [Monitoramento de arquivos de log de rastreamento de solicitação do IIS](lync-server-2013-monitoring-iis-request-tracing-log-files.md)

  - [Contadores de desempenho de mobilidade](lync-server-2013-mobility-performance-counters.md)

