---
title: 'Lync Server 2013: Tabela Dialog'
TOCTitle: Tabela Dialog
ms:assetid: 4d93424f-9072-43f5-83c2-3d539e3e9ca6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398313(v=OCS.15)
ms:contentKeyID: 49306660
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Dialog no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela da Caixa de Diálogo é uma tabela de suporte; cada registro representa uma caixa de diálogo de protocolo SIP.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primário</p></td>
<td><p>Horário em que o agente de QoE (Qualidade de Excelência) recebe o primeiro relatório do chamador ou receptor. Usado em conjunto com SessionSeq para identificar exclusivamente uma sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número de sequência para diferenciar sessões quando tiverem o mesmo ConferenceDateTime.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogID</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p></p></td>
<td><p>ID da caixa de diálogo que é globalmente exclusiva.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogIDChecksum</strong></p></td>
<td><p>int</p></td>
<td><p>index</p></td>
<td><p>Soma de verificação da ID da Caixa de Diálogo.</p></td>
</tr>
</tbody>
</table>

