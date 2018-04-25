---
title: 'Lync Server 2013: Tabela UserSite'
TOCTitle: Tabela UserSite
ms:assetid: 1c2a3cf2-dc05-472e-8097-a31f3a1aafcb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398256(v=OCS.15)
ms:contentKeyID: 49306054
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela UserSite no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela UserSite é uma tabela de suporte. Cada registro representa um site de usuário definido nas configurações de rede.


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
<td><p><strong>UserSiteKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número único de identificação do site de usuário.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserSiteName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Nome do site do usuário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RegionKey</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Referência da <a href="lync-server-2013-region-table.md">Tabela de regiões no Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>

