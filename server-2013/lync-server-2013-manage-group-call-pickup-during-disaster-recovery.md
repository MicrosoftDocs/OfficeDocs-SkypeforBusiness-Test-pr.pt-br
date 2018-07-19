---
title: Gerenciar o recebimento de chamadas em grupo durante a recuperação de desastres
TOCTitle: Gerenciar o recebimento de chamadas em grupo durante a recuperação de desastres
ms:assetid: 2d32f19f-c649-4a72-a4fb-edd338e3a7cc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945618(v=OCS.15)
ms:contentKeyID: 52057591
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar o recebimento de chamadas em grupo durante a recuperação de desastres

 

_**Tópico modificado em:** 2015-03-09_

Quando um Pool de Front-Ends se torna indisponível devido a um incidente não planejado, ocorre failover do serviço no pool de backup. Durante o failover para um pool de backup, os usuários são redirecionados ao pool de backup e estão no modo de resiliência. Enquanto no modo de resiliência, os usuários não podem receber chamadas de outros usuários ou ter suas chamadas atendidas por outros usuários. Quando o failover é concluído, os usários podem utilizar novamente o Atendimento de chamada de grupo normalmente.

Durante o failover para um pool primário, os usuários são redirecionados ao pool primário e estão no modo de resiliência novamente. A funcionalidade de Recebimento de chamada de grupo nao está disponível até que os usuários saiam do modo de resiliência.

Essa seção discute algumas considerações para Recebimento de chamada de grupo durante a recuperação de desastres e também descreve a experiência de usuário.

## Considerações para Recebimento de chamada de grupo durante a recuperação de desastres

Durante a recuperação de desastres, os usuários que foram redirecionados para o pool de backup como parte do processo de failover usam o Aplicativo de Estacionamento de Chamada executado no pool de backup para os números de grupo de recebimento de chamada. Portanto, o suporte ao Recebimento de chamada de grupo durante a recuperação de desastres requer que o Aplicativo de Estacionamento de Chamada esteja implantado e ativado no pool primário e no pool de backup.

As faixas de número de Recebimento de chamada de grupo na tabela de órbita de estacionamento de chamada devem ser redirecionados para o pool de backup após o processo de failover para o pool de backup ser concluído. As faixas de número devem ser redirecionadas de volta ao pool primário após o processo de failback para o pool primário ser concluído. Para redirecionar as faixas de Recebimento de chamda de grupo, use o cmdlet **Set-CsCallParkOrbit**.

Se você implantar um novo pool com um nome de domínio totalmente qualificado (FQDN) diferente para substituir o pool primário, você precisará reatribuir todas as faixas de número de Recebimento de chamada de grupo associadas ao pool primário ao FQDN do novo pool. Para rearibuir as faixas de número ao novo pool, você pode usar o cmdlet **Set-CsCallParkOrbit**. Para obter detalhes sobre o cmdlet **Set-CsCallParkOrbit**, consulte [Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit).

## Experiência de Recebimento de chamada de grupo durante uma falha de pool

A tabela a seguir resume a experiência de Recebimento de chamada de grupo pelas fases da recuperação de desastres.

### Experiência do usuário durante a recuperação de desastres

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Estado da chamada</th>
<th>Failover para o pool de backup</th>
<th>Failback para o pool primário</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Novas chamadas</p></td>
<td><p><strong>Durante o processo de failover:</strong></p>
<ul>
<li><p>O recebimento de chamadas de grupo não está disponível para usuários no modo de resiliência</p></li>
</ul>
<p><strong>Após o failover ser concluído:</strong></p>
<ul>
<li><p>O Recebimento de chamada de grupo disponível quando usuários fora da resiliência e faixas de número de Recebimento de chamada de grupo são redirecionados para o pool de backup</p></li>
</ul></td>
<td><p><strong>Durante o processo de failback:</strong></p>
<ul>
<li><p>O recebimento de chamadas de grupo não está disponível para usuários no modo de resiliência</p></li>
</ul>
<p><strong>Após o failback ser concluído:</strong></p>
<ul>
<li><p>Recebimento de chamada de grupo disponível quando usuários fora da resiliência e faixas de número de Recebimento de chamada de grupo são direcionados de volta ao pool primário</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Chamadas na fila do Recebimento de chamada de grupo</p></td>
<td><p><strong>Durante o processo de failover:</strong></p>
<ul>
<li><p>As chamadas na fila não podem ser atendidas pelo recebimento de chamadas de grupo.</p></li>
</ul>
<p><strong>Após o failover ser concluído:</strong></p>
<ul>
<li><p>Nenhuma chamada neste estado</p></li>
</ul></td>
<td><p><strong>Durante o processo de failback:</strong></p>
<ul>
<li><p>As chamadas na fila não podem ser atendidas pelo recebimento de chamadas de grupo.</p></li>
</ul>
<p><strong>Após o failback ser concluído:</strong></p>
<ul>
<li><p>As chamadas na fila não podem ser atendidas pelo recebimento de chamadas de grupo.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Chamada estabelecida</p></td>
<td><p><strong>Durante o processo de failover:</strong></p>
<ul>
<li><p>As chamadas permanecem conectadas</p></li>
</ul>
<p><strong>Após o failover ser concluído:</strong></p>
<ul>
<li><p>As chamadas permanecem conectadas</p></li>
</ul></td>
<td><p><strong>Durante o processo de failback:</strong></p>
<ul>
<li><p>As chamadas permanecem conectadas</p></li>
</ul>
<p><strong>Após o failback ser concluído:</strong></p>
<ul>
<li><p>As chamadas permanecem conectadas</p></li>
</ul></td>
</tr>
</tbody>
</table>

