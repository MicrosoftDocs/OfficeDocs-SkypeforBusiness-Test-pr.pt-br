---
title: 'Lync Server 2013: Resumo de DNS - Cargas de DNS e de HLB balanceadas'
TOCTitle: Resumo de DNS - Cargas de DNS e de HLB balanceadas
ms:assetid: d2132695-1956-4190-a98e-cd7255cbded6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205273(v=OCS.15)
ms:contentKeyID: 49308181
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - Cargas de DNS e de HLB balanceadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir contém um resumo dos registros DNS exigidos para suportar a carga DNS balanceada e a carga de hardware balanceada do Diretor. A função do Diretor exige registros DNS semelhantes como o Servidor Front-End. O número de registros necessários é refletido nos nomes alternativos do assunto exigidos no certificado do Diretor. Diferente do Servidor Front-End, o Pool de diretores não hospeda contas do usuário ou os Serviços de Mobilidade.

### Registros DNS necessários para o Pool de Diretor usando o balanceamento de carga DNS e o balanceador de carga de hardware

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>Registro de FQDN/DNS</th>
<th>Endereço IP/FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Diretor</p></td>
<td><p>O Diretor hospeda o registro usado para replicação e servidor para servidor</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>Pool de diretores</p></td>
<td><p>Hospeda o registro para o balanceamento de carga DNS do Pool de diretores para servidor para servidor</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Pool de diretores</p></td>
<td><p>SIP de entrada da interface interna do Servidor de Borda</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>VIP HLB Pool de diretores</p></td>
<td><p>Carga de hardware balanceada publicada nos serviços da Web de discagem do proxy inverso</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>VIP HLB Pool de diretores</p></td>
<td><p>Carga de hardware balanceada publicada pelos serviços da Web de reunião do proxy inverso</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>VIP HLB Pool de diretores</p></td>
<td><p>Carga de hardware balanceada publicada e definida pelos Serviços da Web externos de Ticket da Web do proxy inverso do pool de Diretores</p></td>
</tr>
</tbody>
</table>

