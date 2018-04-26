---
title: 'Lync Server 2013: Tabela ErrorDef'
TOCTitle: Tabela ErrorDef
ms:assetid: 6acf3b86-da61-4923-9812-300db6f66dec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398503(v=OCS.15)
ms:contentKeyID: 49307006
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela ErrorDef no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ErrorDef armazena informações sobre cada tipo de erro que possa ocorrer. Cada registro é um tipo de erro.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Chave/Índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número de identificação exclusivo que identifica esse tipo de erro.</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Código de resposta SIP padrão associado a esse erro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>ID de Diagnóstico da Microsoft.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Tipo da chamada. Consulte <a href="lync-server-2013-calltype-table.md">Tabela CallType no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RequestType</strong></p></td>
<td><p>varbinary(33)</p></td>
<td><p> </p></td>
<td><p>Tipo de solicitação que falhou.</p>
<p>Este dado pode ser convertido para o formato de texto usando esta sintaxe:</p>
<p><code>cast(cast(RequestType as varbinary(max)) as varchar(max))</code></p></td>
</tr>
<tr class="even">
<td><p><strong>ContentType</strong></p></td>
<td><p>varbinary(257)</p></td>
<td><p> </p></td>
<td><p>Tipo de conteúdo da solicitação que falhou.</p>
<p>Esses dados podem ser convertidos para o formato de texto com o uso desta sintaxe:</p>
<p><code>cast(cast(ContentType as varbinary(max)) as varchar(max))</code></p></td>
</tr>
</tbody>
</table>

