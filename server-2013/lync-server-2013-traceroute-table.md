---
title: Tabela TraceRoute no Lync Server 2013
TOCTitle: Tabela TraceRoute no Lync Server 2013
ms:assetid: b9493cef-6ece-4f13-bf68-dbf132aab4f4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205205(v=OCS.15)
ms:contentKeyID: 49307918
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela TraceRoute no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela TraceRoute contém informações de roteamento de chamadas. Esta tabela foi apresentada no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Coluna</strong></th>
<th><strong>Tipo de dados</strong></th>
<th><strong>Chave/Índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Data e hora de início da chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Identificador exclusivo usado para distinguir entre várias chamadas que podem ter começado na mesma data e hora.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Representa o tipo de linha de vídeo usada na chamada. Os valores permitidos são:</p>
<ul>
<li><p>0 – Áudio</p></li>
<li><p>1 – Vídeo</p></li>
<li><p>2 – Vídeo panorâmico</p></li>
<li><p>3 – Application/Desktop sharing</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>Primário</p></td>
<td><p>Ponto de extremidade que executou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Salto</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Salto de rede/</p></td>
</tr>
<tr class="even">
<td><p><strong>IPAddressKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Identificador exclusivo do endereço IP. As informações do endereço IP estão armazenadas na <a href="lync-server-2013-ipaddress-table.md">Tabela IPAddress no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RTT</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Tempo de viagem de ida e volta. O tempo de viagem de ida e volta mede quanto tempo leva para que um pacote de voz chegue ao seu destino e retorne uma notificação de recebimento.</p></td>
</tr>
</tbody>
</table>

