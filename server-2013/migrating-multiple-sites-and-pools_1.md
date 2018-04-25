---
title: Migrando vários sites e pools
TOCTitle: Migrando vários sites e pools
ms:assetid: 3bf677d4-a5af-4f73-8fad-1abf5b668cc1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688025(v=OCS.15)
ms:contentKeyID: 49886180
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrando vários sites e pools

 

_**Tópico modificado em:** 2012-08-26_

O Lync Server 2013 oferece suporte a implantações de vários locais e vários pools. O processo de migração de vários pools do Office Communications Server 2007 R2 para o Lync Server 2013 requer as seguintes considerações:

1.  Depois de implantar um pool piloto do Lync Server 2013, será necessário definir um subconjunto de usuários piloto que serão movidos para o Lync Server 2013 e uma metodologia para validação da funcionalidade dos usuários.

2.  Após implantar um servidor de borda no pool piloto, será necessário validar que os usuários externos podem se comunicar com o pool Lync Server 2013.

3.  Depois de fazer a transição das rotas federadas dos Servidores de Borda do Office Communications Server 2007 R2 para os Servidores de Borda do Lync Server 2013 piloto, será necessário validar que os usuários federados podem se comunicar com o pool Lync Server 2013.

4.  Depois de mover todos os objetos de contato de usuários e não usuários, é necessário validar se o pool do Office Communications Server 2007 R2 está vazio.

5.  Depois de verificar se o pool do Office Communications Server 2007 R2 está vazio, será possível desativar o pool.
    
    Para obter detalhes sobre como desativar o pool e servidores herdados do Office Communications Server 2007 R2, consulte [Fase 10: Site herdado encerrado](phase-10-decommission-legacy-site.md).

