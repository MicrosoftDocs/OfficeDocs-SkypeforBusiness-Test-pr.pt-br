---
title: 'Lync Server 2013: Tabela MediationServers'
TOCTitle: Tabela MediationServers
ms:assetid: 9f757377-ab79-4795-aaa9-1163cb9c8a59
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412743(v=OCS.15)
ms:contentKeyID: 49307619
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela MediationServers no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela MediationServers é uma tabela de suporte. Cada registro armazena informações sobre um Servidor de Mediação envolvido em chamadas com registros no banco de dados.


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
<td><p><strong>MediationServerId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica este Servidor de Mediação</p></td>
</tr>
<tr class="even">
<td><p><strong>MediationServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>Nome do Servidor de Mediação.</p></td>
</tr>
</tbody>
</table>

