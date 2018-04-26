---
title: 'Lync Server 2013: tblChat'
TOCTitle: tblChat
ms:assetid: b7fcf1b4-7a3f-4585-a6d9-95e7f030c7dc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615031(v=OCS.15)
ms:contentKeyID: 49307900
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblChat no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela tblChat contém todas as mensagens de chat.

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
<td><p>channelId</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do nó.</p></td>
</tr>
<tr class="even">
<td><p>chatId</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Número sequencial exclusivo (por ID do nó) que define a ordem da sala de chat, gerado pela tabela tblLastChatId.</p></td>
</tr>
<tr class="odd">
<td><p>chatDate</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de hora para a mensagem de chat.</p></td>
</tr>
<tr class="even">
<td><p>userId</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID principal do pôster.</p></td>
</tr>
<tr class="odd">
<td><p>isAlert</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se a mensagem for uma mensagem de alerta.False se não for.</p></td>
</tr>
<tr class="even">
<td><p>content</p></td>
<td><p>nvarchar (max), não nulo</p></td>
<td><p>Conteúdo de chat (a versão de texto). O conteúdo está normalmente em texto sem formatação com as seguintes exceções:</p>
<ul>
<li><p>Os arquivos são representados como links ma-filelink:.</p></li>
<li><p>Links são representados como um elemento HTML (embora o tipo de conteúdo não possa ser considerado HTML).</p></li>
<li><p>Histórias são codificadas como um formato parecido com “[STORY]....”.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>rtf</p></td>
<td><p>varchar(máx)</p></td>
<td><p>Conteúdo do chat (a versão RTF). Pode ser Nulo se o cliente não o fornecer.</p></td>
</tr>
</tbody>
</table>


### Chave

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;channelID, chatD&gt;</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

