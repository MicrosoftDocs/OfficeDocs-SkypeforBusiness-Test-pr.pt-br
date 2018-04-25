---
title: 'Lync Server 2013: tblSkippedAffiliations'
TOCTitle: tblSkippedAffiliations
ms:assetid: 0b129b54-a7a8-42a6-9279-0e08410c06ec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558611(v=OCS.15)
ms:contentKeyID: 49305838
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblSkippedAffiliations no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela SkippedAffiliations inclui as afiliações que não podiam ser lidas (geralmente devido a erros de acesso dos Serviços de Domínio Active Directory).

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
<td><p>prinID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade.</p></td>
</tr>
<tr class="even">
<td><p>affDescription</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Uma cadeia identificando a afiliação.</p>
<p>O formato é: guid: <em>{0}</em> uri: <em>{1}</em> &gt; id: <em>{2}</em></p></td>
</tr>
<tr class="odd">
<td><p>updatedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da principal que atualizou essa linha. É sempre 1 (usuário do sistema) porque a Sincronização do Active Directory é a única origem dessas entradas.</p></td>
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
<th>Coluna(s)</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;prinID, affDescription&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>

