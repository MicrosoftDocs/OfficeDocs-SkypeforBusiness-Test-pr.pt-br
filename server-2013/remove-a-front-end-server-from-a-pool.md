---
title: Remover um Servidor Front-End de um pool
TOCTitle: Remover um Servidor Front-End de um pool
ms:assetid: 767225c9-7c0b-4d54-a407-d77134ba2abe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688095(v=OCS.15)
ms:contentKeyID: 49886266
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover um Servidor Front-End de um pool

 

_**Tópico modificado em:** 2012-10-04_

O Microsoft Lync Server 2010 Enterprise Edition Servidor Front-End não pode existir como um computador autônomo. Ele deverá ser definido como um Pool de Front-Ends, mesmo se houver apenas um único computador no pool.

Este tópico o guia através do processo de remoção de um Servidor Front-End individual de um Pool de Front-Ends existente. Se o Servidor Front-End for o último servidor do pool ou se você remover o pool completamente, consulte [Remover pool Front-End ou servidor Standard Edition](remove-front-end-pool-or-standard-edition-server.md). Não é necessário remover o Servidores Front-End individual antes de remover o Pool de Front-Ends. Quando você remover o pool, remova cada Servidor Front-End.

## Para remover um servidor Front-End de um pool

1.  Abra o servidor de front-end do Lync Server 2013, abra o Construtor de Topologia.

2.  Navegue para o nó Lync Server 2010.

3.  Expanda **pools de Front-Ends do Enterprise Edition** , expanda o Pool de Front-Ends com o Servidor Front-End que você deseja remover, clique com botão direito do mouse no Servidor Front-End que você deseja remover e clique em **Excluir** .

