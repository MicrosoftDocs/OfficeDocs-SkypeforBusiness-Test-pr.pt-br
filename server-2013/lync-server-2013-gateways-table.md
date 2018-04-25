---
title: 'Lync Server 2013: Tabela Gateways'
TOCTitle: Tabela Gateways
ms:assetid: a909daad-d137-45e0-b149-1de9f8e1e029
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412795(v=OCS.15)
ms:contentKeyID: 49307736
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Gateways no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Gateways é uma tabela de suporte. Cada registro armazena informações sobre um gateway envolvido em chamadas de PSTN (rede telefônica pública comutada) com registros no banco de dados.


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
<td><p><strong>GatewayId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único que identifica este gateway.</p></td>
</tr>
<tr class="even">
<td><p><strong>Gateway</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>Nome do gateway.</p></td>
</tr>
</tbody>
</table>

