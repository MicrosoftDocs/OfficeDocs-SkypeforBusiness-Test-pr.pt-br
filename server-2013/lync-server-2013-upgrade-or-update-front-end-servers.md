---
title: Atualizar servidores Front End no Lync Server 2013
TOCTitle: Atualizar servidores Front End no Lync Server 2013
ms:assetid: 20fa39ae-ecfb-4c72-9cc4-8e183d3c752f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204736(v=OCS.15)
ms:contentKeyID: 49306106
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atualizar servidores Front End no Lync Server 2013

 

_**Tópico modificado em:** 2013-06-28_

Os Servidores Front End em um pool do Enterprise Edition são organizados nos *domínios de atualização*. Estes são subconjuntos de Servidores de Front-End no pool. Os domínios de atualização são criados automaticamente pelo Construtor de Topologias.

Ao atualizar servidores, é necessário fazer um Domínio de Atualização por vez. Desative um servidor, atualize-o e reinicie antes de atualizar outro servidor. Certifique-se de manter um registro de quais Domínios de Atualização e Servidores já foram atualizados. Use o seguinte fluxograma ao atualizar cada servidor.

![Fluxograma do servidor de atualização](images/JJ204736.42ed59a4-1c26-49f7-ade4-a5a788457ab9(OCS.15).jpg "Fluxograma do servidor de atualização")

## Para aplicar uma atualização aos servidores Front End em um pool

1.  Em um Servidor de Front-End no pool, execute o seguinte cmdlet:
    
    **Get-CsPoolUpgradeReadinessState**
    
    Se o valor de *PoolUpgradeState* for **Busy**, aguarde 10 minutos e tente **Get-CsPoolUpgradeReadinessState** novamente. Se você vir **Busy** por pelo menos três vezes consecutivas, aguarde 10 minutos entre cada tentativa, ou se vir qualquer resultado do **InsufficientActiveFrontEnds** para **PoolUpgradeState,** há um problema com o pool. Se esse pool estiver emparelhado com outro pool de Front End em uma topologia de recuperação de desastres, deve falhar o pool sobre o pool de backup e atualizar os servidores neste pool. Para obter detalhes, consulte [Fazendo failover de um pool no Lync Server 2013](lync-server-2013-failing-over-a-pool.md).
    
    Se o valor de *PoolUpgradeState* é **Pronto**, vá para a etapa 2.

2.  O cmdlet **Get-CsPoolUpgradeReadinessState** também retorna informações sobre cada domínio de atualização no pool e sobre quais Servidores de Front-End estão em cada domínio de atualização. Se o valor **ReadyforUpgrade** for **True** para o domínio de atualização que contém o servidor que você deseja atualizar, é possível atualizar com segurança este servidor no momento. Para fazer isso, execute:
    
    1.  Pare as novas conexões do Servidor de Front-End usando o cmdlet `Stop-CsWindowsService -Graceful -Verbose`.
        
        > [!NOTE]  
        > Se essas atualizações de servidor estiverem acontecendo durante uma parada programada do servidor, é possível executar este cmdlet sem o parâmetro ‘-<strong>Graceful</strong>‘, da seguinte forma: <strong>Stop-CsWindowsService</strong>. Assim, os serviços são imediatamente interrompidos, sem esperar que todas as solicitações de serviços existentes sejam atendidas.    
    2.  Atualize os servidores associados a este Domínio de Atualização.
    
    3.  Reinicie os servidores e certifique-se de que estão aceitando novas conexões.

3.  Repita as Etapas 1 e 2 para cada Domínio de Atualização no pool, até que todos os Servidores Front-End tenham sido atualizados.

