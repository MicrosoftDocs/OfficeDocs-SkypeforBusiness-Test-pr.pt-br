---
title: "Lync Server 2013: Experiência de Estacionamento de Chamadas durante falha de pool"
TOCTitle: Experiência de Estacionamento de Chamadas durante falha de pool
ms:assetid: f6303e69-8771-492a-9e8b-c3d7ba231309
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205383(v=OCS.15)
ms:contentKeyID: 49308621
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Experiência de Estacionamento de Chamadas no Lync Server 2013 durante falha de pool

 

_**Tópico modificado em:** 2015-03-09_

Quando um Pool de Front-Ends se torna indisponível devido a um incidente não planejado, as chamadas que foram estacionadas, mas ainda não recuperadas são desconectadas. Durante o failover para um pool de backup, os usuários são redirecionados ao pool de backup e estão no modo de resiliência. Enquanto estão no modo de resiliência, os usuários não podem estacionar chamadas, mas podem colocar chamadas em espera e transferi-las. Quando o failover estiver concluído, as chamadas podem novamente ser estacionadas e recuperadas normalmente. Durante o failback, os usuários não podem estacionar chamadas até saírem do modo de resiliência.

Durante a recuperação de desastres, os usuários que foram redirecionados para o pool de backup como parte do processo de failover usam o Aplicativo de Estacionamento de Chamada implantado no pool de backup. Portanto, os usuários redirecionados para o pool de backup usam as configurações de estacionamento de chamadas configuradas para o Aplicativo de Estacionamento de Chamada no pool de backup.

A tabela a seguir resume a experiência de Estacionamento de Chamada pelas fases da recuperação de desastres.

### Experiência do usuário durante a recuperação de desastres

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Estado da chamada</th>
<th>Quando ocorre uma interrupção</th>
<th>Durante o failover</th>
<th>Durante o failback</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamada ainda não estacionada</p></td>
<td><p>A chamada permanece conectada, mas não pode ser estacionada.</p></td>
<td><ul>
<li><p>Durante o failover, a chamada não pode ser estacionada enquanto os usuários estão no modo de resiliência, mas podem ser colocadas em espera e transferidas.</p></li>
<li><p>Quando o failover é concluído, a chamada pode ser estacionada e recuperada.</p></li>
</ul></td>
<td><ul>
<li><p>Durante o failback, a chamada não pode ser estacionada enquanto os usuários estão no modo de resiliência, mas podem ser colocadas em espera e transferidas.</p></li>
<li><p>Quando o failback é concluído, a chamada pode ser estacionada e recuperada.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Chamada estacionada, mas ainda não recuperada</p></td>
<td><p>A chamada é desconectada.</p></td>
<td><p>Nenhuma chamada neste estado.</p></td>
<td><p>A chamada é mantida estacionada.</p></td>
</tr>
<tr class="odd">
<td><p>Chamada estacionada já recuperada.</p></td>
<td><p>A chamada é mantida conectada.</p></td>
<td><p>A chamada é mantida conectada.</p></td>
<td><p>A chamada é mantida conectada.</p></td>
</tr>
</tbody>
</table>

