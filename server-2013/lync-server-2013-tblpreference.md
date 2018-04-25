---
title: 'Lync Server 2013: tblPreference'
TOCTitle: tblPreference
ms:assetid: f94eb128-f782-42ff-a568-ed3529573bc8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615052(v=OCS.15)
ms:contentKeyID: 49308662
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPreference no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblPreference contém as preferências de clientes dos usuários. Normalmente é usado pelos clientes antes de Lync 2013.

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
<td><p>prefLabel</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>Etiqueta com um formato como: &lt;user sip uri&gt;|username.&lt;preference set&gt;.</p></td>
</tr>
<tr class="even">
<td><p>prefSeqID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Um número sequencial (por etiqueta) para fins de controle de versão.</p></td>
</tr>
<tr class="odd">
<td><p>prefContent</p></td>
<td><p>nvarchar (máx)</p></td>
<td><p>Conteúdo codificado.</p></td>
</tr>
<tr class="even">
<td><p>lastModifiedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do diretor que atualizou a preferência.</p></td>
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
<td><p>&lt;prefLabel, prefSeqID&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

