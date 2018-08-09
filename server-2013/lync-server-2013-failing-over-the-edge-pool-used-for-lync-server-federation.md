---
title: "Lync Server 2013: Failover do pool de Borda usado p/ federação do Serv. Lync"
TOCTitle: Failover do pool de Borda usado para federação do Servidor Lync
ms:assetid: 5c9da0f2-7429-40bb-bb3c-5cc4ecb5a13d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688071(v=OCS.15)
ms:contentKeyID: 49886237
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failover do pool de Borda usado para federação do Servidor Lync no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-17_

Se o pool de borda no qual a federação do Lync Server está configurada ficar inoperante, você precisará alterar a federação para usar outro Pool de Borda para que ela funcione.

## Pool de borda com falhas usado para federação DO Lync Server

1.  No servidor de front-end, abra o Construtor de Topologia. Expanda **Pools de borda**, clique com o botão direito no servidor de Borda ou pool do servidor de Borda atualmente configurado para Federação. Selecione **Editar propriedades**.

2.  Em **Editar propriedades**, em **Geral**, desmarque **Habilitar federação para este pool de Borda (Porta 5061)**. Clique em **OK**.

3.  Expanda **Pools de borda** e clique com o botão direito do mouse no servidor de borda ou pool de servidores de borda que agora deseja usar para federação. Selecione **Editar propriedades**.

4.  Em **Editar propriedades**, em **Geral**, selecione **Habilitar federação para este pool de Borda (Porta 5061)**. Clique em **OK**.

5.  Clique em **Ação**, selecione **Topologia**, **Publicar**. Quando solicitado em **Publicar a topologia**, clique em **Avançar**. Quando Publicar é finalizado, clique em **Concluir**.

6.  No servidor de Borda, abra o assistente de Implantação do Lync Server. Clique em **Instalar ou atualizar o sistema do Lync Server**, clique em **Instalar ou remover componentes do Lync Server**. Clique em **Executar novamente**.

7.  Em Instalar componentes do Lync Server, clique em **Avançar**. A tela de resumo mostrará ações conforme são executadas. Quando a implantação estiver concluída, clique em **Exibir log** para exibir os arquivos de log disponíveis. Clique em **Concluir** para concluir a implantação.
    
    Se o site que contém o pool de borda com falha contiver servidores front-end que ainda estão em execução, você precisará atualizar o Serviço de Webconferência e o Serviço de Conferência A/V nesses pools de frond-ends para usar um pool de borda em um site remoto que ainda esteja ativo. Para obter mais informações, consulte [Alterando o Pool de borda associado ao pool Front-End no Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md).

## Consulte Também

#### Tarefas

[Failover do pool de Borda usado para federação de XMPP no Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)  
[Failback do pool de Borda usado para federação do Lync Server ou federação XMPP no Lync Server 2013](lync-server-2013-failing-back-the-edge-pool-used-for-lync-server-federation-or-xmpp-federation.md)  

#### Conceitos

[Recuperação de desastres do servidor de borda no Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)

