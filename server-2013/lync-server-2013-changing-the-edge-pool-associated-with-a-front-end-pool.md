---
title: 'Lync Server 2013: Alterando o Pool de borda associado ao pool Front-End'
TOCTitle: Alterando o Pool de borda associado ao pool Front-End
ms:assetid: 369468c7-2c0b-48cc-bbc3-825dad7b85aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688023(v=OCS.15)
ms:contentKeyID: 49886177
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterando o Pool de borda associado ao pool Front-End no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Se um pool de borda cair, mas o pool de front-ends do mesmo local ainda estiver em execução, será preciso configurar o pool de front-ends para que use o pool de borda de um local diferente até que o pool de borda com falha seja restaurado.

## Modificando o Pool de Borda Associado ao Pool de Front End

1.  NO Construtor de Topologias, navegue até o nome no pool de front-ends que precisa ser alterado.

2.  Clique com o botão direito no pool e clique em **Editar propriedades** .

3.  Na seção **Associações** , em **Associar Pool de Borda (para componentes de mídia)** , use a caixa suspensa para selecionar o pool de borda ao qual deseja associar o pool de front-ends.

4.  Clique em **OK** .

## Consulte Também

#### Conceitos

[Recuperação de desastres do servidor de borda no Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)

