---
title: 'Lync Server 2013: tblADCookie'
TOCTitle: tblADCookie
ms:assetid: 0a9102c4-47aa-40ea-8a0d-20e72ab09848
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558610(v=OCS.15)
ms:contentKeyID: 49305837
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblADCookie no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela tblADCookie inclui os cookies atuais de sincronização do Protocolo LDAP.

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
<td><p>prinGuid</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUID principal do domínio em monitoramento.</p></td>
</tr>
<tr class="even">
<td><p>prinDCHost</p></td>
<td><p>nvarchar(255)</p></td>
<td><p>Nome de domínio totalmente qualificado (FQDN) do controlador de domínio atual usado para a Sincronização de Serviços de Domínio Active Directory Sync. Possui valor informacional.</p></td>
</tr>
<tr class="odd">
<td><p>adcContent</p></td>
<td><p>imagem (binário)</p></td>
<td><p>Cookie da Sincronização do Active Directory.</p></td>
</tr>
<tr class="even">
<td><p>lastUpdated</p></td>
<td><p>datetime</p></td>
<td><p>Carimbo de data/hora com a data/hora de atualização da linha.</p></td>
</tr>
<tr class="odd">
<td><p>lockedUntil</p></td>
<td><p>datetime</p></td>
<td><p>Tempo até que a linha seja bloqueada para alterações. Isso faz parte de um mecanismo de interloque do software que garante que apenas um dos Servidores de Chat faça a sincronização do Active Directory por vez.</p></td>
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
<th>Coluna(s)</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>prinGuid</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinGuid</p></td>
<td><p>Chave estrangeira com pesquisa na tabela Principal.prinGuid.</p></td>
</tr>
</tbody>
</table>

