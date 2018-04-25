---
title: 'Lync Server 2013: tabela DeRegisterType'
TOCTitle: Tabela DeRegisterType
ms:assetid: 09148118-6209-4fd7-a494-99118689a245
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398142(v=OCS.15)
ms:contentKeyID: 49305812
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela DeRegisterType no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

DeRegisterType é uma tabela estática que armazena a lista de possíveis tipos de cancelamento de registro de usuário, como "cliente iniciado", "registro vencido" ou "cliente não responde".


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
<td><p><strong>DeRegisterTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primário</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>DeRegisterReason</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Valores permitidos:</p>
<ul>
<li><p>0 - Desconhecido</p></li>
<li><p>1 - Iniciado o cancelamento do registro pelo cliente</p></li>
<li><p>2 - Registro expirado</p></li>
<li><p>3 - Client crashed</p></li>
<li><p>4 - Atributos do usuário mudaram</p></li>
<li><p>5 - Registrador preferido mudou</p></li>
<li><p>6 - Cliente herdado em Modo de sobrevivência</p></li>
</ul></td>
</tr>
</tbody>
</table>

