---
title: Considerações de coexistência
TOCTitle: Considerações de coexistência
ms:assetid: 9d1a3c0f-492a-4e37-bc2f-63509e328785
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205131(v=OCS.15)
ms:contentKeyID: 49307599
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Considerações de coexistência

 

_**Tópico modificado em:** 2012-10-06_

Após a migração, apenas um Lync Server 2013, Pool de Servidor de Chat Persistente existirá, e você poderá descomissionar sua implantação antiga.

Antes da migração ser concluída e antes de você descomissionar sua implantação atual do Servidor de Chat de Grupo completamente, você pode ter alguma das seguintes implantações:

  - Lync Server 2013, Pool de Servidor de Chat Persistente, que deve ser hospedado em um pool do Lync Server 2013.

  - Pool Lync Server 2010, Chat de Grupo, que deve ser hospedado em um pool do Lync Server 2010.

  - Pool Office Communications Server 2007 R2Chat de Grupo, que deve ser hospedado em um pool do Office Communications Server 2007 R2.

Essas implantações podem coexistir. No entanto, as categorias, salas e complementos em uma implantação não interagem com aquelas na implantação acompanhante.

Usando uma configuração manual, um cliente herdado (cliente Chat de Grupo) pode se conectar a um pool por vez do Office Communications Server 2007 R2, Lync Server 2010, Chat de Grupo, ou Lync Server 2013.

O Lync 2013 (cliente) pode interagir apenas com o Lync Server 2013, Pool de Servidor de Chat Persistente, não com pools antigos do Servidor de Chat de Grupo. Para usar o Chat Persistente em um Lync 2013 (cliente), o usuário deve estar hospedado no Lync 2013 e permitido pela política.

