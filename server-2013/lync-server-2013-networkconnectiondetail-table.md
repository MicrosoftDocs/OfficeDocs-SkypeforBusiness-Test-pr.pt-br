---
title: Tabela NetworkConnectionDetail no Lync Server 2013
TOCTitle: Tabela NetworkConnectionDetail no Lync Server 2013
ms:assetid: b48cc9a6-5232-48b5-bd20-53b68229336b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205185(v=OCS.15)
ms:contentKeyID: 49307847
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela NetworkConnectionDetail no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela NetworkConnectionDetail mapeia os tipos de conexão de rede em identificadores de conexão de rede usados em outro lugar no banco de dados de Qualidade da Experiência. Esta tabela foi apresentada no Microsoft Lync Server 2013.


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
<td><p><strong>NetworkConnectionDetailKey</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo do tipo de conexão de rede.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkConnectionDetail</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Tipo de conexão de rede que corresponde a NetworkConnectionDetailKey. Os valores permitidos são:</p>
<ol>
<li><p>0 -- Com fio</p></li>
<li><p>1 -- Wi-Fi</p></li>
<li><p>2 -- Ethernet</p></li>
</ol></td>
</tr>
</tbody>
</table>

