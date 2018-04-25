---
title: 'Lync Server 2013: tblEnumValue'
TOCTitle: tblEnumValue
ms:assetid: a33df20c-d19d-4f5c-b012-29dab8fb9200
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615025(v=OCS.15)
ms:contentKeyID: 49307669
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblEnumValue no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela tblEnumValue é uma tabela embutida em código que contém os valores de Visibilidade e Comportamento dos atributos usados na tabela Nó.

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
<td><p>valueID</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>ID do valor.</p></td>
</tr>
<tr class="even">
<td><p>attributeID</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>ID do atributo.</p></td>
</tr>
<tr class="odd">
<td><p>attributeValue</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Nome do valor.</p></td>
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
<td><p>valueID</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>attributeID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblEnumAttribute.attributeID.</p></td>
</tr>
</tbody>
</table>


### Valores da tabela

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>valueID</th>
<th>attributeID</th>
<th>attributeValue</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
<td><p>private</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>1</p></td>
<td><p>escopo</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>2</p></td>
<td><p>normal</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>2</p></td>
<td><p>auditório</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>1</p></td>
<td><p>aberto</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[tblNode no Lync Server 2013](lync-server-2013-tblnode.md)

