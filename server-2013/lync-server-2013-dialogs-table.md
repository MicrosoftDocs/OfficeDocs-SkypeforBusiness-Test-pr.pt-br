---
title: 'Lync Server 2013: Tabela Dialogs'
TOCTitle: Tabela Dialogs
ms:assetid: 487a430b-af66-4ea6-b28e-4e33cfdb7f9e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425954(v=OCS.15)
ms:contentKeyID: 49306596
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Dialogs no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela de Caixas de Diálogo é uma tabela de suporte que armazena as informações sobre DialogIDs para sessões ponto a ponto.


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
<td><p>Primário</p></td>
<td><p>Tempo de solicitação de sessão; usado em conjunto com SessionIDSeq para identificar exclusivamente uma sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número de identificação para identificar a sessão. Usado em conjunto com SessionIDTime para identificar exclusivamente uma sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalChecksum</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Soma de verificação de ExternalID. Este campo é usado para aumentar a velocidade das pesquisas de banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExternalId</strong></p></td>
<td><p>varbinary(775)</p></td>
<td><p> </p></td>
<td><p>Identificação da caixa de diálogo SIP, armazenada como um binário. O formato do binário é:</p>
<p>diálogo;de-marca;para-marca</p>
<p>Este dado pode ser convertido para o formato de texto usando esta sintaxe:</p>
<p><code>cast(cast(ExternalId as varbinary(max)) as varchar(max))</code></p></td>
</tr>
</tbody>
</table>

