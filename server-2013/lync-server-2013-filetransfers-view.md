---
title: Exibir FileTransfers
TOCTitle: Exibir FileTransfers
ms:assetid: e52c3ad0-152e-4a18-af1c-1aff0d205151
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721914(v=OCS.15)
ms:contentKeyID: 49886445
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir FileTransfers

 

_**Tópico modificado em:** 2015-03-09_

O repositório de exibição FileTranfer armazena informações sobre sessões de transferência de arquivos ponto a ponto. Esta exibição foi introduzida no Microsoft Lync Server 2013.

> [!NOTE]  
> A exibição do FileTransfers contém todas as colunas no <a href="lync-server-2013-sessiondetails-view.md">Exibir SessionDetails</a> além das colunas listadas abaixo.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>FileName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome do arquivo transferido.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cookie</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Usado para identificar cada mensagem de acompanhamento como sendo associado a este.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FileIdentity</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>Identificador exclusivo para distinguir entre transferências de arquivo envolvendo o mesmo nome de arquivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>Accept</strong></p></td>
<td><p>bit</p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Rejeitar e Cancelar serão NULL.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reject</strong></p></td>
<td><p>bit</p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Aceitar e Cancelar serão NULL.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cancel</strong></p></td>
<td><p>bit</p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Aceitar e Rejeitar serão NULL.</p></td>
</tr>
</tbody>
</table>

