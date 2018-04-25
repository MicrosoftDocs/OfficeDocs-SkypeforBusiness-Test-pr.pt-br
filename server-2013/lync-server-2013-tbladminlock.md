---
title: 'Lync Server 2013: tblAdminLock'
TOCTitle: tblAdminLock
ms:assetid: 785a43c0-6892-474c-821c-fa9cdbeb99d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558665(v=OCS.15)
ms:contentKeyID: 49307177
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblAdminLock no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblAdminLock contém o bloqueio do administrador necessário para a execução de alguns comandos de administrador.

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
<td><p>lockExpiresTime</p></td>
<td><p>datetime, não nulo</p></td>
<td><p>Data de expiração de bloqueio. O proprietário pode estender esse valor periodicamente.</p></td>
</tr>
<tr class="even">
<td><p>lockServerID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Identificação do servidor que possui o bloqueio.</p></td>
</tr>
<tr class="odd">
<td><p>lockActorID</p></td>
<td><p>int, não nulo</p></td>
<td><p>Identificação da entidade que possui o bloqueio.</p></td>
</tr>
</tbody>
</table>

