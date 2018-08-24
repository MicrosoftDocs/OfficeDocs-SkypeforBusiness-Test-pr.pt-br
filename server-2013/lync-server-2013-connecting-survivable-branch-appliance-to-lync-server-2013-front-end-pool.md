---
title: "Lync Server 2013: Conect. Ap. de Filial Persist. ao pool Front-End do Lync Server 2013"
TOCTitle: Conectando Aparelho de Filial Persistente ao pool Front-End do Lync Server 2013
ms:assetid: 3c7ca33f-5295-4d82-9152-41d8bc6f35cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688026(v=OCS.15)
ms:contentKeyID: 49886182
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectando Aparelho de Filial Persistente ao pool Front-End do Lync Server 2013

 

_**Tópico modificado em:** 2012-10-05_

Todo Aparelho de Filial Persistente (SBA) está associado a um Pool de Front-Ends, que serve como um Registrador para o SBA. Quando o Pool de Front-Ends é atualizado para Lync Server 2013, o SBA deve ser desassociado do Pool de Front-Ends enquanto o Pool de Front-Ends é atualizado. Após o Pool de Front-Ends ser atualizado, o SBA pode ser reassociado com o Pool de Front-Ends. Isso envolve a exclusão do SBA da topologia no Construtor de Topologia e, então, adicionando o SBA novamente no Construtor de Topologia. Os usuários hospedados no SBA devem ser movidos para outro Pool de Front-Ends antes de remover o SBA da topologia. Depois que o SBA for adicionado novamente à topologia, tais usuários poderão ser movidos de volta ao SBA.

Essas etapas estão resumidas abaixo:

1.  Mova os usuários da ramificação hospedada no SBA para outro Pool de Front-Ends.

2.  Remova o SBA da sua topologia para desassociar o Pool de Front-Ends existente como o Registrador de backup.

3.  Atualize o Pool de Front-Ends para Microsoft Lync Server 2013.

4.  Adicione o SBA novamente à topologia.

5.  Associe o novo Pool de Front-Ends ao SBA como Registrador de backup.

6.  Mova os usuários da ramificação de volta para o SBA.

## Nesta seção

  - [Adicionar Aparelho de Filial Persistente do Lync Server 2013 a sua topologia](lync-server-2013-add-lync-server-2013-survivable-branch-appliance-branch-site-to-your-topology.md)

  - [Adicionar site de Aparelho de Filial Persistente do Lync Server 2010 a sua topologia](lync-server-2013-add-lync-server-2010-survivable-branch-appliance-branch-site-to-your-topology.md)

