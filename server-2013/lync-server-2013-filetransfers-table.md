---
title: 'Lync Server 2013: Tabela FileTransfers'
TOCTitle: Tabela FileTransfers
ms:assetid: 5368e67c-d8a9-43a1-9472-a839950dedb3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398353(v=OCS.15)
ms:contentKeyID: 49306721
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela FileTransfers no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro representa uma sessão de transferência de arquivos.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Hora da solicitação da sessão. Usado em conjunto com <strong>SessionIdSeq</strong> para identificar exclusivamente uma sessão. Consulte <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primária, estrangeira</p></td>
<td><p>Número para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar uma sessão. Consulte a <a href="lync-server-2013-dialogs-table.md">Tabela Dialogs no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nome do arquivo</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>Nome do arquivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>FileIdentity</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p></p></td>
<td><p>Identificador exclusivo para distinguir entre transferências de arquivo envolvendo o mesmo nome de arquivo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Cookie</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Primário</p></td>
<td><p>Usado para identificar cada mensagem de acompanhamento como sendo associado a este.</p></td>
</tr>
<tr class="even">
<td><p><strong>Accept</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Rejeitar e Cancelar serão NULL.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reject</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Aceitar e Cancelar serão NULL.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cancel</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Pode ser TRUE ou NULL. Se for TRUE, Aceitar e Rejeitar serão NULL.</p></td>
</tr>
</tbody>
</table>

