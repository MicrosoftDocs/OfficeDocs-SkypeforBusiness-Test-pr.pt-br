---
title: 'Lync Server 2013: tblPrincipalMeta'
TOCTitle: tblPrincipalMeta
ms:assetid: 808490d4-7d6d-47a2-b8af-b5940d47073b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615009(v=OCS.15)
ms:contentKeyID: 49307271
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalMeta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblPrincipalMeta inclui as entidades que precisam ser atualizadas dos Serviços de Domínio Active Directory.

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
<td><p>prinID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade.</p></td>
</tr>
<tr class="even">
<td><p>prinAffiliationsDirty</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se as afiliações da entidade precisam ser atualizadas.</p></td>
</tr>
<tr class="odd">
<td><p>prinAttributesDirty</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se os atributos da entidade precisam ser atualizados.</p></td>
</tr>
<tr class="even">
<td><p>prinDeleted</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se a entidade foi excluída.</p></td>
</tr>
<tr class="odd">
<td><p>tryCount</p></td>
<td><p>int</p></td>
<td><p>Número de tentativas para atualizar a entidade do AD DS que ocorreram até o momento.</p></td>
</tr>
<tr class="even">
<td><p>lastTry</p></td>
<td><p>datetime</p></td>
<td><p>Carimbo de data/hora da tentativa mais recente para atualizar a entidade. Pode ser nulo se ainda não houve tentativa de atualização.</p></td>
</tr>
<tr class="odd">
<td><p>nextTry</p></td>
<td><p>datetime</p></td>
<td><p>Carimbo de data/hora para a próxima atualização agendada. Pode ser nulo se nenhuma atualização foi agendada.</p></td>
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
<td><p>prinID</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>prinID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipal.prinID.</p></td>
</tr>
</tbody>
</table>

