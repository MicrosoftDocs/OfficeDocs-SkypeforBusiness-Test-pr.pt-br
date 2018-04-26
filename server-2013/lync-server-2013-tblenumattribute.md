---
title: 'Lync Server 2013: tblEnumAttribute'
TOCTitle: tblEnumAttribute
ms:assetid: 17f8b87e-36a6-4f6a-8630-7c76b61a7595
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558617(v=OCS.15)
ms:contentKeyID: 49306013
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblEnumAttribute no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblEnumAttribute é uma tabela embutida em código que inclui os atributos de Visibilidade e Comportamento usados na tabela Node.

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
<td><p>attributeID</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>ID do atributo.</p></td>
</tr>
<tr class="even">
<td><p>attributeName</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Nome do atributo.</p></td>
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
<td><p>attributeID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>


### Valores da tabela

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>attributeID</th>
<th>attributeName</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Visibilidade.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Comportamento.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[tblNode no Lync Server 2013](lync-server-2013-tblnode.md)

