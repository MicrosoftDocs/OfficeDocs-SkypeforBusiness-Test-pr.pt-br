---
title: 'Lync Server 2013: Relacionamentos de Registradores de backup'
TOCTitle: Relacionamentos de Registradores de backup
ms:assetid: 7e078271-84b9-4666-989c-c4507a0cdf4a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205033(v=OCS.15)
ms:contentKeyID: 49307239
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relacionamentos de Registradores de backup no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-28_

Além de oferecer capacidade para recuperação de desastre, dois pools pareados servem como backup de Registrars. Em Lync Server 2013, o backup das relações de Registrar entre Pools de Front-Ends são sempre 1:1 e recíprocos. Isso significa que se P1 for backup de P2, P2 deve ser o backup de P1 e nenhum pode ser backup de outro pool Front End. Isso é uma mudança do Lync Server 2010, no qual Pool de Front-Ends as relações de backup podem ser mais de uma.

Ainda que as relações de backup entre dois Pools de Front-Ends devam ser 1:1 e simétricas, cada Pool de Front-Ends ainda podem ser o backup registrar para qualquer número de Aparelho de Filial Persistente, assim como em Lync Server 2010.

Observe que Lync Server 2013 não estende o suporte de recuperação em desastre a usuários em um Aparelho de Filial Persistente. Se um pool Front End que serve como backup para Aparelho de Filial Persistente cair, os usuários registrados no Aparelho de Filial Persistente caem em modo de resiliência mesmo após os usuários no pool Front End tenham falhado o backup Pool de Front-Ends.

