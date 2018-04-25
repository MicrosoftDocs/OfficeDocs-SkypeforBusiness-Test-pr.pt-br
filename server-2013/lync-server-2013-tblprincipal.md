---
title: 'Lync Server 2013: tblPrincipal'
TOCTitle: tblPrincipal
ms:assetid: 79a24502-b4ce-41f0-8979-8caddf535338
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558667(v=OCS.15)
ms:contentKeyID: 49307189
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipal no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblPrincipal contém todas as entidades, incluindo usuários, pastas e grupos.

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
<td><p>prinGuid</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUID da entidade. Isto é amplamente utilizado como uma chave primária alternativa porque seu significado entra no espaço do Serviços de Domínio Active Directory. (O GUID de uma entidade em cache é igual ao GUID de objeto correspondente no Active Directory).</p></td>
</tr>
<tr class="odd">
<td><p>prinUri</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>URI de entidade. O esquema do SIP é usado para usuários e o ma-grp é usado para quase tudo.</p></td>
</tr>
<tr class="even">
<td><p>prinName</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome comum. Usado apenas por tipos de usuário.</p></td>
</tr>
<tr class="odd">
<td><p>prinDisplayName</p></td>
<td><p>Nvarchar (256)</p></td>
<td><p>Nome de exibição. Usado somente pelos tipos de usuário.</p></td>
</tr>
<tr class="even">
<td><p>prinCompanyName</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome da empresa. Usado somente pelos tipos de usuário.</p></td>
</tr>
<tr class="odd">
<td><p>prinEmail</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>E-mail. Usado apenas pelos tipos de usuários.</p></td>
</tr>
<tr class="even">
<td><p>prinADPath</p></td>
<td><p>nvarchar(384)</p></td>
<td><p>Nome de domínio do objeto do Active Directory do qual a entidade é uma versão em cache. Pode ser nulo para tipos que não são objetos do Active Directory (como os usuários do sistema).</p></td>
</tr>
<tr class="odd">
<td><p>prinADUserPrincipalName</p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Nome UPN do usuário. Usado somente pelos tipos de usuário regular.</p></td>
</tr>
<tr class="even">
<td><p>prinDisabled</p></td>
<td><p>smallint, não nulo</p></td>
<td><ul>
<li><p>0: a entidade está ativa.</p></li>
<li><p>1: a entidade é desabilitada porque os recursos SIP do usuário estão desabilitados.</p></li>
<li><p>2: a entidade é excluída porque o objeto associado do AD foi excluído.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>prinTypeID</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>Tipo de entidade (da tabela tblPrincipalType).</p></td>
</tr>
<tr class="even">
<td><p>prinPoolID</p></td>
<td><p>Int</p></td>
<td><p>Atribuição do pool do Lync para a entidade.</p></td>
</tr>
<tr class="odd">
<td><p>prinPolicyID</p></td>
<td><p>Int</p></td>
<td><p>Valor de política do Servidor de Chat Persistente para o usuário, se a política de tipo de marca estiver presente.</p></td>
</tr>
<tr class="even">
<td><p>prinAddedBy</p></td>
<td><p>int</p></td>
<td><p>ID da entidade do criador.</p></td>
</tr>
<tr class="odd">
<td><p>prinAddedOn</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data/hora para a hora da criação.</p></td>
</tr>
<tr class="even">
<td><p>prinUpdatedBy</p></td>
<td><p>int</p></td>
<td><p>ID da entidade que atualizou esta entrada pela última vez.</p></td>
</tr>
<tr class="odd">
<td><p>prinUpdatedOn</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data/hora da última atualização.</p></td>
</tr>
<tr class="even">
<td><p>prinVerifiedOn</p></td>
<td><p>datetime, não nulo</p></td>
<td><p>Data e hora da última atualização de Sincronização do Active Directory para a entidade.</p></td>
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
<td><p>prinTypeID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblPrincipalType.ptypeID.</p></td>
</tr>
</tbody>
</table>

