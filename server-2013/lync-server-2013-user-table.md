---
title: 'Lync Server 2013: Tabela User'
TOCTitle: Tabela User
ms:assetid: 6b52047e-286d-47ab-b7bc-a9b266f62d82
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398505(v=OCS.15)
ms:contentKeyID: 49307028
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela User no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela de Usuário é uma tabela de suporte que armazena uma lista de vários usuários que participaram das sessões registradas no banco de dados. Cada registro da tabela representa um usuário.


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
<td><p><strong>UserKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica este usuário.</p></td>
</tr>
<tr class="even">
<td><p><strong>URI</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Cadeia de caracteres URI.</p></td>
</tr>
<tr class="odd">
<td><p><strong>URIType</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>1 é o tipo de URI desconhecido.</p>
<p>2 é o URI do usuário.</p>
<p>4 é o URI de conferência.</p>
<p>8 é o URI do telefone.</p></td>
</tr>
<tr class="even">
<td><p><strong>TenantKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Locatário do usuário, referenciado da tabela do locatário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastPoorCallTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Carimbo de data e hora da última vez em que o usuário teve uma chamada de áudio ruim.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>Somente para uso interno.</p></td>
</tr>
</tbody>
</table>

