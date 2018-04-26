---
title: Tabela CodecDescription no Lync Server 2013
TOCTitle: Tabela CodecDescription no Lync Server 2013
ms:assetid: 3598acb8-7ea6-4748-8417-149c971c32a2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204797(v=OCS.15)
ms:contentKeyID: 49306357
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela CodecDescription no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela CodecDescription associa identificadores exclusivos de codec a seus codecs correspondentes. Os codecs são usados para codificar sinais digitais para transmissão e divulgação e, depois, para decodificar esses sinais para reprodução. Essa tabela foi introduzida no Microsoft Lync Server 2013


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
<th><strong>Tipos de dados</strong></th>
<th><strong>Chave/índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Chave de descrição do codec</strong></p></td>
<td><p>smallint</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo atribuído ao codec.</p></td>
</tr>
<tr class="even">
<td><p><strong>Descrição do codec</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Descrição exclusiva do codec correspondendo à chave de descrição do codec.</p></td>
</tr>
</tbody>
</table>

