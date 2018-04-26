---
title: Adicionar ou Remover um Servidor Front-End no Lync Server 2013
TOCTitle: Adicionar ou Remover um Servidor Front-End no Lync Server 2013
ms:assetid: ab748733-6bad-4c93-8dda-db8d5271653d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205153(v=OCS.15)
ms:contentKeyID: 49307779
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar ou Remover um Servidor Front-End no Lync Server 2013

 

_**Tópico modificado em:** 2016-01-21_

Ao adicionar um servidor de Front End a um pool, ou remover um servidor de Front End de um pool, você precisará reiniciar o pool. Para evitar interrupção do serviço aos usuários, siga o procedimento a seguir ao remover ou adicionar um servidor de Front End.

## Para adicionar ou remover servidores Front-End

1.  Se estiver removendo servidores de Front End, primeiro interrompa novas conexões a esses servidores. Para fazer isso, é possível usar o seguinte cmdlet:
    
        Stop -CsWindowsServices -Graceful

2.  Quando os servidores sendo removidos não têm sessões atuais, interrompa os serviços do Lync Server neles.

3.  Abra o Construtor de Topologias, e adiciona ou remova os servidores necessários.

4.  Publique a topologia.

5.  Se o pool tiver ido de dois Servidores Front-End para mais que dois, ou de mais de dois servidores para exatamente dois, será necessário digitar o seguinte cmdlet:
    
        Reset-CsPoolRegistrarState-ResetType FullReset -PoolFqdn <PoolFqdn>
    
    Se o pool tinha três ou mais servidores, então pelo menos três desses servidores deve ser executado ao digitar esse cmdlet.

6.  Reinicie todos os Servidores Front-End no pool, um de cada vez.

