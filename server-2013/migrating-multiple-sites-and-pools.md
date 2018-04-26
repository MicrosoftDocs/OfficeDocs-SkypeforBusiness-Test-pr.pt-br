---
title: Migrando vários sites e pools
TOCTitle: Migrando vários sites e pools
ms:assetid: a6d726d2-564d-4b39-a97c-5656a673292a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205165(v=OCS.15)
ms:contentKeyID: 49307704
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando vários sites e pools

 

_**Tópico modificado em:** 2012-09-17_

O Lync Server 2013 oferece suporte a implantações de vários locais e vários pools. O processo de migração de vários pools do Lync Server 2010 para o Lync Server 2013 requer as seguintes considerações:

1.  Depois de implantar um pool piloto do Lync Server 2013, será necessário definir um subconjunto de usuários piloto que serão movidos para o Lync Server 2013 e uma metodologia para validação da funcionalidade dos usuários. Por exemplo, depois de mover o usuário para o pool piloto, verifique se a política de conferência do usuário foi movida para o Lync Server 2013.

2.  Após implantar um servidor de borda no pool piloto, será necessário validar que os usuários externos podem se comunicar com o pool Lync Server 2013.

3.  Depois de fazer a transição das rotas federadas dos Servidores de Borda do Lync Server 2010 para os Servidores de Borda do Lync Server 2013 piloto, será necessário validar que os usuários federados podem se comunicar com o pool Lync Server 2013.

4.  Depois de mover todos os objetos de contato de usuários e não usuários, é necessário validar se o pool do Lync Server 2010 está vazio.

5.  Depois de verificar se o pool do Lync Server 2010 está vazio, será possível desativar o pool.
    
    Para obter detalhes sobre como desativar o pool e servidores herdados do Lync Server 2010, consulte [Fase 8: Encerrar os Pools herdados](phase-8-decommission-legacy-pools.md).

