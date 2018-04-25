---
title: 'Lync Server 2013: tblActivePeers'
TOCTitle: tblActivePeers
ms:assetid: b50c3f4a-bab6-4cb9-b40e-016cf1a9c607
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615030(v=OCS.15)
ms:contentKeyID: 49307865
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblActivePeers no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tblActivePeers contém as conexões ponto a ponto atuais entre Servidores de Canal.

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
<td><p>aplServerID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do servidor que postou a entrada.</p></td>
</tr>
<tr class="even">
<td><p>aplPeerID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do ponto ao qual o servidor de postagem está conectado.</p></td>
</tr>
</tbody>
</table>


### Chaves

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
<td><p>&lt;aplServerID, aplPeerID&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>aplServerID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblServerIdentity.serverID.</p></td>
</tr>
<tr class="odd">
<td><p>aplPeerID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblServerIdentity.serverID.</p></td>
</tr>
</tbody>
</table>

