---
title: "Lync Server 2013: Res. de DNS - Pool de diret. em escala, balanc. de carga do hardware"
TOCTitle: Resumo de DNS - Pool de diretores em escala, balanceadores de carga do hardware
ms:assetid: 08ba48e6-bfa1-4ab0-bc89-d58ddb9c20af
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204655(v=OCS.15)
ms:contentKeyID: 49305806
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - Pool de diretores em escala, balanceadores de carga do hardware no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir contém um resumo dos registros DNS necessários para suportar o Diretor com carga de hardware balanceada. A função do Diretor exige registros DNS parecidos com os do Servidor Front-End. O número de registros necessários é refletido nos nomes de entidade alternativas exigidas no certificado Diretor. Diferente do Servidor Front-End, o Pool de diretores não hospeda contas de usuário ou os Serviços de Mobilidade.

### Registros DNS exigidos para o Pool de diretores usando um Balanceador de carga de hardware e Balanceamento de carga DNS

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
<td><p>Registro de host Diretor usado para replicação e comunicação de servidor com servidor</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>dirpool01.contoso.net</p></td>
<td><p>VIP HLB do pool de Pool de diretores</p></td>
<td><p>Registro host para o Pool de diretores com carga DNS balanceada</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>VIP HLB Pool de diretores</p></td>
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
<td><p>Carga de hardware balanceada e definida pelos serviços Web externos de Tíquete da Web de proxy reverso para o Pool de diretores</p></td>
</tr>
</tbody>
</table>

