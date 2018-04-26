---
title: Alterações feitas pela preparação de domínio no Lync Server 2013
TOCTitle: Alterações feitas pela preparação de domínio no Lync Server 2013
ms:assetid: 9191221e-6166-4c2b-837e-fa73d90fdf80
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398742(v=OCS.15)
ms:contentKeyID: 49307455
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações feitas pela preparação de domínio no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir lista as ACEs (entradas de controle de acesso) que a preparação de domínio cria na raiz do domínio. Todas as ACEs serão herdadas, salvo indicação em contrário.

### ACEs adicionadas à raiz do domínio

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
<th>RTCUniversal-UserAdmins</th>
<th>RTCHSUniversal-Services</th>
<th>Usuários autenticados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ler contêiner (não herdado)</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Ler User PropertySet User-Account-Restrictions</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Ler User PropertySet Personal-Information</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Ler User PropertySet General-Information</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Ler User PropertySet Public-Information</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Ler User PropertySet RTCUserSearchProperty-Set</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p><strong>Sim</strong></p></td>
</tr>
<tr class="odd">
<td><p>Ler User PropertySet RTCPropertySet</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Gravar User Property Proxy-Addresses</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Gravar User PropertySet RTCUserSearchProperty-Set</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Gravar User PropertySet RTCPropertySet</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Ler PropertySet DS-Replication-Get-Changes de todos os objetos do Active Directory</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p>Não</p></td>
</tr>
</tbody>
</table>


A tabela a seguir lista as ACEs que a preparação do domínio cria nos três contêineres internos: Usuários, Computadores e Controladores de Domínio. Todas as ACEs são herdadas, a menos que especificado de outra forma.

### ACEs adicionadas à contêineres internos

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversal-UserReadOnly-Group</th>
<th>RTCUniversal-ServerReadOnly-Group</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ler contêiner (não herdado)</p></td>
<td><p><strong>Sim</strong></p></td>
<td><p><strong>Sim</strong></p></td>
</tr>
</tbody>
</table>

