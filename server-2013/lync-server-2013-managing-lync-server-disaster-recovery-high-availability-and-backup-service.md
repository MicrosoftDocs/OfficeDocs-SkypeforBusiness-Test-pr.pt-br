---
title: 'Lync Server 2013: Gerenciando recuperação de desastre, alta disponibilidade e Serviço de Backup do Lync Server'
TOCTitle: Gerenciando recuperação de desastre, alta disponibilidade e Serviço de Backup do Lync Server 2013
ms:assetid: f4cd36fb-ffd6-48fa-b761-e11b3bcff91a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721939(v=OCS.15)
ms:contentKeyID: 49886484
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando recuperação de desastre, alta disponibilidade e Serviço de Backup do Lync Server 2013

 

_**Tópico modificado em:** 2012-11-12_

Esta seção contém os procedimentos para operações de recuperação de desastres, bem como para realizar a manutenção do Serviço de Backup, que sincroniza os dados de pools de Front Ends emparelhados.

Os procedimentos de recuperação de desastres, o failover e o failback, são manuais. Se ocorrer um desastre, o administrador deve chamar manualmente os procedimentos de failover. O mesmo se aplica ao failback após a reparação do pool.

Os procedimentos de recuperação de desastres no restante dessa seção pressupõem que:

  - Você tem uma implantação com pools de Front Ends emparelhados em diferentes sites, conforme descrito em [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md). O Serviço de Backup é executado nestes pools emparelhados para mantê-los sincronizados.

  - Se o Repositório de Gerenciamento Central está hospedado em ambos os pools, ele é instalado e executado em ambos os pools emparelhados, sendo que um dos pools hospeda o mestre ativo e o outro pool, o em espera.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg425939.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Nos procedimentos a seguir, o parâmetro <em>PoolFQDN</em> se refere ao FQDN do pool afetado pelo desastre, e não o pool para o qual os usuários afetados foram redirecionados. Para o mesmo conjunto de usuários afetados, ele se refere ao mesmo pool em ambos os cmdlets de failover e failback (ou seja, o pool que primeiramente hospedou os usuários antes do failover).<br />Por exemplo, pressuponha um caso em que todos os usuários hospedados no pool P1 foram transferidos para o pool de backup, o P2. Se o administrador deseja mover todos os usuários que utilizam os serviços de P2 para utilizarem os serviços de P1, o administrador deve executar as seguintes etapas:<ol>
> <li><p>Retorne do P2 para o P1 todos os usuários originalmente hospedados em P1 utilizando o cmdlet de failback. Nesse caso, <em>PoolFQDN</em> é o FQDN de P1.</p></li>
> 
> <li><p>Transfira todos os usuários originalmente hospedados em P2 para o P1 utilizando o cmdlet de failover. Nesse caso, a propriedade <em>PoolFQDN</em> é o FQDN de P2.</p></li>
> 
> 
> <li><p>Se o administrador desejar retornar posteriormente os usuários para o P2, o <em>PoolFQDN</em> é o FQDN do P2.</p></li></ol>
Observe que a etapa 1 acima deve ser realizada antes da etapa 2 para preservar a integridade do pool. Se você executar a etapa 2 antes da etapa 1, o cmdlet da etapa 2 falhará.</td>
</tr>
</tbody>
</table>


## Nesta seção

  - [Configurando e monitorando o Serviço de Backup no Lync Server 2013](lync-server-2013-configuring-and-monitoring-the-backup-service.md)

  - [Fazendo failover de um pool no Lync Server 2013](lync-server-2013-failing-over-a-pool.md)

  - [Failback de pool no Lync Server 2013](lync-server-2013-failing-back-a-pool.md)

  - [Failover de banco de dados espelhado no Lync Server 2013](lync-server-2013-failing-over-a-mirrored-database.md)

  - [Failover do pool de Borda usado para federação do Servidor Lync no Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-lync-server-federation.md)

  - [Failover do pool de Borda usado para federação de XMPP no Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md)

  - [Failback do pool de Borda usado para federação do Lync Server ou federação XMPP no Lync Server 2013](lync-server-2013-failing-back-the-edge-pool-used-for-lync-server-federation-or-xmpp-federation.md)

  - [Alterando o Pool de borda associado ao pool Front-End no Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md)

  - [Restaurando conteúdos de conferência usando o Serviço de Backup no Lync Server 2013](lync-server-2013-restoring-conference-contents-using-the-backup-service.md)

## Consulte Também

#### Conceitos

[Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)

