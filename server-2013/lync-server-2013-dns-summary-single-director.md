---
title: 'Lync Server 2013: Resumo de DNS - Diretor Único'
TOCTitle: Resumo de DNS - Diretor Único
ms:assetid: 790ecb56-92cd-41f4-baf6-c290a707aa4d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205021(v=OCS.15)
ms:contentKeyID: 49307191
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - Diretor Único no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir contém um resumo de registros DNS obrigatórios para oferecer suporte ao Diretor único. A função do Diretor exige registros DNS semelhantes como Servidor Front-End. O número de registros necessários é refletido nos nomes alternativos de entidade obrigatórios no certificado do Diretor. Ao contrário do Servidor Front-End, o Diretor não hospeda contas de usuários nem Serviços de Mobilidade.

### Registros DNS obrigatórios para Diretor

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
<td><p>sip.contoso.com</p></td>
<td><p>Diretor</p></td>
<td><p>Protocolo SIP da interface de borda interna do Servidor de Borda</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Diretor</p></td>
<td><p>Serviços Web de discagem publicados do proxy reverso</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Diretor</p></td>
<td><p>Serviços Web de reunião publicados do proxy reverso</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A interno</p></td>
<td><p>webdirexternal.contoso.com</p></td>
<td><p>Diretor</p></td>
<td><p>Publicado e definido pelos serviços Web externos de Tíquete da Web de proxy reverso para o Diretor</p></td>
</tr>
</tbody>
</table>

