---
title: 'Lync Server 2013: tblFileToken'
TOCTitle: tblFileToken
ms:assetid: 49e7dd79-1607-443c-818a-88c160e4ed06
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558646(v=OCS.15)
ms:contentKeyID: 49306621
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblFileToken no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblFileToken inclui tokens temporários para fins de transferência de arquivos.

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
<td><p>fileToken</p></td>
<td><p>nvarchar (50), não nulo</p></td>
<td><p>Token exclusivo (uma GUID).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenUserID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade de segurança que está transferindo o arquivo.</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenChannelID</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUID do nó da sala de chat.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenExpireDate</p></td>
<td><p>datetime, não nulo</p></td>
<td><p>Tempo de expiração. (Tokens expiram após 30 minutos, a menos que fixado (consultar as descrições a seguir nesta coluna).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceFileUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URL do arquivo transferido (para uso do serviço de Conformidade).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceThumbnailUrl</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>URL da miniatura para o arquivo transferido (para uso do serviço de Conformidade).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenComplianceTime</p></td>
<td><p>datetime2</p></td>
<td><p>Carimbo de data e hora para a operação de transferência de arquivo atual (para uso do serviço de Conformidade).</p></td>
</tr>
<tr class="even">
<td><p>fileTokenComplianceIsUpload</p></td>
<td><p>bit</p></td>
<td><p>Verdadeiro em caso de upload; Falso se download (para uso do serviço de Conformidade).</p></td>
</tr>
<tr class="odd">
<td><p>fileTokenCompliancePinned</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se fixado. É utilizado para manter o token na tabela até que o serviço de Conformidade tenha uma chance de recuperar os campos dele.</p></td>
</tr>
</tbody>
</table>


### Chaves

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
<td><p>fileToken</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>fileTokenChannelID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblNode.nodeGuid.</p></td>
</tr>
</tbody>
</table>

