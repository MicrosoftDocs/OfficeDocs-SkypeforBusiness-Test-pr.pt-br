---
title: 'Lync Server 2013: Tabela Conferences'
TOCTitle: Tabela Conferences
ms:assetid: c3da6271-b3c6-4898-894f-10456ec794d0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412964(v=OCS.15)
ms:contentKeyID: 49308025
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela Conferences no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada registro desta tabela contém detalhes de chamada sobre uma conferência.


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
<td><p>Hora na qual a solicitação de conferência foi capturada pelo agente de CDR. Usado somente como uma chave primária para identificar exclusivamente uma instância de conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número de ID para identificar a sessão. Usado em conjunto com <strong>SessionIdTime</strong> para identificar exclusivamente uma instância de conferência. *</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>URI da conferência. Consulte o <a href="lync-server-2013-conferenceuris-table.md">Tabela ConferenceUris no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConfInstance</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p> </p></td>
<td><p>Útil para conferências recorrentes; cada instância de uma conferência recorrente tem o mesmo <strong>ConferenceUri</strong> , mas terá um <strong>ConfInstance</strong> diferente.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Hora de início da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>Hora de início da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número da ID para identificar o pool no qual a conferência foi capturada. Consulte o <a href="lync-server-2013-pools-table.md">Tabela Pools no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="even">
<td><p><strong>OrganizerId</strong></p></td>
<td><p>Int</p></td>
<td><p>Estrangeiro</p></td>
<td><p>Número da ID para identificar a URI do organizador desta conferência. Consulte o <a href="lync-server-2013-users-table.md">Tabela Users no Lync Server 2013</a> para obter mais informações.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sinalizador</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>Uma máscara de bit que contém os Atributos da Conferência. Os valores possíveis são:</p>
<ul>
<li><p>0X01</p></li>
<li><p>Sintético</p></li>
<li><p>Transação</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Processado</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Campo interno usado pelo serviço de Monitoramento.</p>
<p>Este campo foi introduzido no Microsoft Lync Server 2013.</p></td>
</tr>
</tbody>
</table>


\* Para a maioria das sessões, SessionIdSeq terá o valor de 1. Se duas sessões iniciarem exatamente na mesma hora, o SessionIdSeq para uma será 1 e para a outra será 2, e assim por diante.

