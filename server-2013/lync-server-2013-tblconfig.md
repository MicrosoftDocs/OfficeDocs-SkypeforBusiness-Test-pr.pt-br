---
title: 'Lync Server 2013: tblConfig'
TOCTitle: tblConfig
ms:assetid: 7445e7db-c574-46fa-b964-8640d77047a8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558663(v=OCS.15)
ms:contentKeyID: 49307116
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblConfig no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblConfig contém algumas configurações sem suporte do Servidor de Chat Persistente em uma linha.

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
<td><p>configLabel</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>Contém &quot;pool.&quot;</p></td>
</tr>
<tr class="even">
<td><p>configContent</p></td>
<td><p>nvarchar (máx)</p></td>
<td><p>Conteúdo de configuração.</p></td>
</tr>
<tr class="odd">
<td><p>configPoolID</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>ID exclusivo da instância de banco de dados.</p></td>
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
<td><p>configLabel</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

