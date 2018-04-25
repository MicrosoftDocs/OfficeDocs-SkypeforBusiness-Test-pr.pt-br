---
title: 'Lync Server 2013: Considerações de migração e de coexistência para IPv6'
TOCTitle: Considerações de migração e de coexistência para IPv6
ms:assetid: 8c769c4f-c8a9-4cbf-9080-beee3be9848a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205068(v=OCS.15)
ms:contentKeyID: 49307414
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Considerações de migração e de coexistência para IPv6 no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-14_

IP versão 6 (IPv6) não é suportado no Lync Server 2010 ou Office Communications Server. Para projetos pilotos, você pode testar a coexistência de pilha dupla do Lync Server 2010 e Lync Server 2013. Recomendamos que todos os pools de um dado site central sejam atualizados para o Lync Server 2013, antes de permitir IPv6 (rede de pilha dupla) para qualquer um dos pools. Se for necessário configurar um pool apenas para IPv6, recomendamos que você defina um pool somente de IPv6 em seu ambiente de laboratório para testes.

Os cenários a seguir são suportados durante a migração e coexistência:

  - Os pools Lync Server 2013, Lync Server 2010 e Office Communications Server 2007 R2 em modo IPv4, coexistindo com Lync Server 2013 no modo de pilha dupla.

  - Pool Lync Server 2013 em modo apenas IPv6, se um pool apenas IPv6 estiver em silo.

