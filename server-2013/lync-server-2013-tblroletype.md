---
title: 'Lync Server 2013: tblRoleType'
TOCTitle: tblRoleType
ms:assetid: 1eac3a54-656a-40ac-b771-edfc64d6e34b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558623(v=OCS.15)
ms:contentKeyID: 49306084
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblRoleType no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblRoleType é uma tabela de pesquisa estática com tipos de funções e seus conjuntos de permissões associados.

### Colunas

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>rtypeID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do tipo de função.</p></td>
</tr>
<tr class="even">
<td><p>rtypeDesc</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Descrição do tipo de função. Existem quatro funções disponíveis:</p>
<ul>
<li><p>Membro: Membro da sala de chat</p></li>
<li><p>Gerente: Gerente da sala de chat</p></li>
<li><p>Com voz: Apresentador para uma sala de chat de auditório</p></li>
<li><p>Criador: Pode criar salas de bate-papo</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>rtypeAllowedPermSet</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Permissão configurada para a função. Os bits usados são:</p>
<ul>
<li><p>2: True se a função puder gerenciar nós.</p></li>
<li><p>4: True se a função puder criar nós filhos.</p></li>
<li><p>7: True se a função puder entrar em uma sala de chat (ou nas salas filhos de uma categoria).</p></li>
<li><p>8: True se a função puder conversar em uma sala de chat (ou nas salas filhos de uma categoria).</p></li>
<li><p>10: True se a função puder ler o histórico do chat mesmo quando não tiver entrado na sala de chat.</p></li>
<li><p>11: True se a função puder ver a sala de chat (refinado por fatores como escopo e visibilidade).</p></li>
<li><p>12: True se a função puder conversar em uma sala de chat de auditório.</p></li>
<li><p>13: True se a função puder ignorar as regras de visibilidade ao exibir nós.</p></li>
</ul></td>
</tr>
</tbody>
</table>


### Chave

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>rtypeID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

