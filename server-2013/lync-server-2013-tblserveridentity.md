---
title: 'Lync Server 2013: tblServerIdentity'
TOCTitle: tblServerIdentity
ms:assetid: 5411c9bc-b0b3-41fc-8b7e-fa71cccd770b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558648(v=OCS.15)
ms:contentKeyID: 49306729
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblServerIdentity no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O tblServerIdentity inclui os servidores de chat ativos no Pool de Servidor de Chat Persistente.

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
<td><p>serverID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Identificação do Servidor. Corresponde à ID da Instância do Repositório de Gerenciamento Central.</p></td>
</tr>
<tr class="even">
<td><p>serverAddress</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Endereço do Servidor utilizando o endereço do Windows Communication Foundation.</p></td>
</tr>
<tr class="odd">
<td><p>serverLastPingTime</p></td>
<td><p>datetime</p></td>
<td><p>A última vez em que o Servidor de Canal atualizou esta linha para fornecer evidências de que está sendo executado.</p></td>
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
<td><p>serverID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

