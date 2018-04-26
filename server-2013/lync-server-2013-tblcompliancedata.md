---
title: 'Lync Server 2013: tblComplianceData'
TOCTitle: tblComplianceData
ms:assetid: 05b28f9b-4aba-4b69-ba8d-2ceeb6cbfaac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558606(v=OCS.15)
ms:contentKeyID: 49305739
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblComplianceData no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela ComplianceData inclui eventos de conformidade que ainda não foram processados pelo adaptador de conformidade

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
<td><p>cmplEventID</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>ID do evento.</p></td>
</tr>
<tr class="even">
<td><p>entryDate</p></td>
<td><p>smalldatetime, não nulo</p></td>
<td><p>Hora de inserção (pode está longe no futuro para cmplType=9, pois a entrada é apenas um espaço reservado neste caso).</p></td>
</tr>
<tr class="odd">
<td><p>cmplType</p></td>
<td><p>int, não nulo</p></td>
<td><p>Tipo de evento de conformidade:</p>
<ul>
<li><p>1: Chat</p></li>
<li><p>2: Backchat</p></li>
<li><p>3: Download de arquivo</p></li>
<li><p>4: Carregamento de arquivo</p></li>
<li><p>9: Transferência de arquivo provisional</p></li>
<li><p>10: Exclusão de chat (com substituição)</p></li>
<li><p>11: Limpeza de chat</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>cmplTime</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data/hora para o evento.</p></td>
</tr>
<tr class="odd">
<td><p>cmplChannelUri</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>Identificador de Recurso Uniforme do Canal (URI).</p></td>
</tr>
<tr class="even">
<td><p>cmplChatID</p></td>
<td><p>bigint</p></td>
<td><p>ID do chat (correspondendo à tabela do Chat.chatId).</p></td>
</tr>
<tr class="odd">
<td><p>cmplUserID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID principal do pôster (correspondendo à tabela do Principal.prinID).</p></td>
</tr>
<tr class="even">
<td><p>cmplUserUri</p></td>
<td><p>nvarchar (255), não nulo</p></td>
<td><p>URI do usuário.</p></td>
</tr>
<tr class="odd">
<td><p>cmplMessage</p></td>
<td><p>nvarchar (máx)</p></td>
<td><p>Mensagem (codificação depende de cmplType).</p></td>
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
<td><p>cmplEventID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>

