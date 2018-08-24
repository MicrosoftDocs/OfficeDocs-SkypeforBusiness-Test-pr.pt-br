---
title: Remover pool Front-End ou servidor Standard Edition
TOCTitle: Remover pool Front-End ou servidor Standard Edition
ms:assetid: 83c39a36-49a1-4ac6-9cc5-b0e441b1fdec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688115(v=OCS.15)
ms:contentKeyID: 49886289
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover pool Front-End ou servidor Standard Edition

 

_**Tópico modificado em:** 2012-10-04_

Este tópico guia o usuário pelo processo de remoção de Pool de Front-Ends ou da versão Standard Edition Servidor Front-End. Ao remover um Pool de Front-Ends, você remove todos os Servidor Front-End que pertencem ao pool como parte do processo de remoção do pool. Ao remover a versão Standard Edition Servidor Front-End, remova a definição de Repositório SQL de Construtor de Topologias.

## Para remover pools de servidor front-end

1.  Abrir o Construtor de Topologias.

2.  Navegue para o nó Lync Server 2010.

3.  Expanda os **pools de front-end Enterprise Edition** , expanda o Pool de Front-Ends, clique como botão direito no Pool de Front-Ends que deseja remover e, em seguida, clique em **Excluir** .

4.  Publique a topologia, verifique o status de replicação e execute o Assistente de Implantação do Lync Server conforme necessário.

## Para remover servidores front-end Standard Edition

1.  Abrir o Construtor de Topologias.

2.  Navegue para o nó Lync Server 2010.

3.  Expanda **Servidores front-end Standard Edition** , clique com o botão direito do mouse no Servidor Front-End que deseja remover e clique em **Excluir** .

4.  Expanda **Repositórios SQL** , clique com o botão direito do mouse no banco de dados do SQL Server que está associado à Servidor Front-End Standard Edition e clique em **Excluir** .
    
    > [!IMPORTANT]  
    > Você deve remover a definição dos bancos de dados do SQL Server colocados da Servidor Front-End Standard Edition.

5.  Publique a topologia, verifique o status de replicação e execute o Assistente de Implantação do Lync Server conforme necessário.

