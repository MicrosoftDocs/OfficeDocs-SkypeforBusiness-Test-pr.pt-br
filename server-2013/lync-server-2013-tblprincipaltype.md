---
title: 'Lync Server 2013: tblPrincipalType'
TOCTitle: tblPrincipalType
ms:assetid: 32e1c1d6-80f4-4624-bf4e-b4c77d3982fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558633(v=OCS.15)
ms:contentKeyID: 49306322
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblPrincipalType no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

PrincipalType contém os tipos principais para categorizar o que está na tabela tblPrincipal.

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
<td><p>ptypeID</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>ID do tipo principal.</p></td>
</tr>
<tr class="even">
<td><p>ptypeDesc</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Descrição do tipo.</p></td>
</tr>
<tr class="odd">
<td><p>ptypeIsSystemUser</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se o tipo corresponder às entidades que são usadas para fins internos.</p></td>
</tr>
<tr class="even">
<td><p>ptypeIsUser</p></td>
<td><p>bit, não nulo</p></td>
<td><p>True se o tipo for um tipo de usuário.</p></td>
</tr>
</tbody>
</table>


### Chave

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
<td><p>ptypeID</p></td>
<td><p>Chave primária.</p></td>
</tr>
</tbody>
</table>


### Valores principais

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>ID</th>
<th>Função</th>
<th>Descrição</th>
<th>Usuário</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Qualquer um</p></td>
<td><p>Entidade genérica sem um tipo conhecido. Não usado na tabela tblPrincipal.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>AnyUser</p></td>
<td><p>Entidade de segurança genérica do tipo de usuário. Não é usada na tabela tblPrincipal.</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>AnyGroup</p></td>
<td><p>Entidade de segurança genérica com semântica de grupo. Não é usada na tabela tblPrincipal.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>SystemUser</p></td>
<td><p>Entidade usada internamente por Servidor de Chat Persistente.</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>Usuário</p></td>
<td><p>Usuário regular.</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>DC</p></td>
<td><p>Controlador de domínio do Serviços de Domínio Active Directory.</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>Grupo</p></td>
<td><p>Grupo de segurança do Active Directory.</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>Pasta</p></td>
<td><p>Unidade organizacional ou recipiente do Active Directory.</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[tblPrincipal no Lync Server 2013](lync-server-2013-tblprincipal.md)

