---
title: 'Lync Server 2013: Suporte a armazenamento de arquivo'
TOCTitle: Suporte a armazenamento de arquivo
ms:assetid: ed66430d-3c19-4267-938c-956a51005073
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399073(v=OCS.15)
ms:contentKeyID: 49308519
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a armazenamento de arquivo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Lync Server 2013 usa o mesmo armazenamento de arquivos para todos os armazenamentos. O suporte do armazenamento de arquivos inclui o seguinte:

  - Um compartilhamento de arquivos no DAS (armazenamento anexado direto) ou na SAN (rede de área de armazenamento), incluindo o DFS (Sistema de Arquivos Distribuídos), e na RAID (conjunto redundante de discos independentes) para repositórios de arquivos. Para obter detalhes sobre os requisitos de armazenamento, consulte [Requisitos técnicos para Servidores Front-End, sistema de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-technical-requirements-for-front-end-servers-instant-messaging-and-presence.md) e [Requisitos de hardware e de software para o Diretor no Lync Server 2013](lync-server-2013-hardware-and-software-requirements-for-the-director.md) na documentação de Planejamento. Para obter detalhes sobre o DFS para Sistema operacional Windows Server 2008, consulte o Guia Passo a Passo do DFS para Windows Server 2008 em [http://go.microsoft.com/fwlink/p/?linkId=202835](http://go.microsoft.com/fwlink/p/?linkid=202835).

  - Um cluster compartilhado para o compartilhamento de arquivo. Se você usar um cluster compartilhado, deverá usar os servidores de cluster que executam o Windows Server 2008 ou o Windows Server 2008 R2. O uso de servidores de cluster executando uma versão anterior do Windows pode ocasionar em problemas de permissão que impedem alguns recursos de serem disponibilizados. Use o Administrador de cluster para criar os compartilhamentos de arquivo. Para obter detalhes sobre como usar o Administrador de cluster, consulte o artigo 284838 da Base de Conhecimento da Microsoft, "Como criar um compartilhamento de arquivo de cluster de servidor com cluster.exe" em [http://go.microsoft.com/fwlink/p/?linkId=140899](http://go.microsoft.com/fwlink/p/?linkid=140899).

