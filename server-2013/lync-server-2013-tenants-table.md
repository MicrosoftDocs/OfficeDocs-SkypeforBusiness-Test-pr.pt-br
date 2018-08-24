---
title: 'Lync Server 2013: Tabela Tenants'
TOCTitle: Tabela Tenants
ms:assetid: c1b070c1-2c59-4ca9-910b-43f673f97fda
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412950(v=OCS.15)
ms:contentKeyID: 49307997
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Tenants no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela Tenants é uma tabela de suporte que armazena uma lista de vários locatários. Cada registro na tabela representa um locatário.

> [!NOTE]  
> Na implantação no local, o CDR usa o ID de Inquilino integrado para indicar um tipo de autenticação diferente, como conectividade de IM pública, Federada e Anônima.


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
<td><p><strong>TenantId</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica o ID desse inquilino.</p></td>
</tr>
<tr class="even">
<td><p><strong>TenantKey</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p><ul><li><p>00000000-0000-0000-0000-000000000000 - Empresarial</p></li><li><p>00000000-0000-0000-0000-000000000001 - Federado</p></li><li><p>00000000-0000-0000-0000-000000000002 - Anônimo</p></li><li><p>00000000-0000-0000-0000-000000000003 - Conectividade de IM público</p></li></ul></td>
</tr>
</tbody>
</table>

