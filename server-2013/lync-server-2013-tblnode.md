---
title: 'Lync Server 2013: tblNode'
TOCTitle: tblNode
ms:assetid: a31d2961-aa83-4286-a12e-15d279c95f19
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615024(v=OCS.15)
ms:contentKeyID: 49307667
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# tblNode no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

tblNode contém a árvore de console (com nós de categoria e sala de bate-papo), como gerenciado no Painel de Controle do Lync Server 2013 e cmdlets administrativos.

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
<td><p>nodeID</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID do Nó (número único).</p></td>
</tr>
<tr class="even">
<td><p>nodeGuid</p></td>
<td><p>GUID, não nulo</p></td>
<td><p>GUIDO do Nó.</p></td>
</tr>
<tr class="odd">
<td><p>parentID</p></td>
<td><p>int</p></td>
<td><p>ID do nó do pai. O nó raiz (com ID 1) inclui si mesmo como pai também.</p></td>
</tr>
<tr class="even">
<td><p>nodeType</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiro se o nó for uma categoria.</p>
<p>Falso se o nó for uma sala de chat.</p></td>
</tr>
<tr class="odd">
<td><p>nodeName</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Nome do nó.</p></td>
</tr>
<tr class="even">
<td><p>nodeDesc</p></td>
<td><p>nvarchar (256), não nulo</p></td>
<td><p>Descrição do nó.</p></td>
</tr>
<tr class="odd">
<td><p>invite</p></td>
<td><p>bit</p></td>
<td><p>Para categorias:</p>
<ul>
<li><p>Verdadeiro se convites estiverem ativados.</p></li>
<li><p>Falso se convites estiverem desativados.</p></li>
</ul>
<p>Para salas:</p>
<ul>
<li><p>Falso se convites estiverem desativados (substitui a categoria pai).</p></li>
<li><p>Nulo se a configuração de convites for herdada da categoria pai.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>logged</p></td>
<td><p>bit</p></td>
<td><p>Para categorias:</p>
<ul>
<li><p>Verdadeiro se o histórico de chat estiver ativado.</p></li>
<li><p>Falso se o histórico de chat estiver desativado.</p></li>
</ul>
<p>Para salas:</p>
<ul>
<li><p>Null.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>filePost</p></td>
<td><p>bit</p></td>
<td><p>Para categorias:</p>
<ul>
<li><p>Verdadeiro se o carregamento de arquivos for permitido.</p></li>
<li><p>Falso se o carregamento de arquivos não for permitido.</p></li>
</ul>
<p>Para salas:</p>
<ul>
<li><p>Null.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>disabled</p></td>
<td><p>bit, não nulo</p></td>
<td><p>Verdadeiros se a sala de chat estiver desabilitada. Aplica-se somente a salas de chat (falso para categorias).</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
<td></td>
</tr>
<tr class="even">
<td><p>comportamento</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>Comportamento (consultado na tabela EnumValue):</p>
<ul>
<li><p>4: Normal (salas de chat normais).</p></li>
<li><p>5: Auditório (salas de chat de auditório, somente apresentadores podem contribuir).</p></li>
</ul>
<p>Aplica-se somente a salas de chat</p></td>
</tr>
<tr class="odd">
<td><p>visibilidade</p></td>
<td><p>smallint, não nulo</p></td>
<td><p>Visibilidade (consultado na tabela EnumValue):</p>
<ul>
<li><p>2: Particular</p></li>
<li><p>3: Com escopo</p></li>
<li><p>6: Abrir</p></li>
</ul>
<p>Aplica-se somente a salas de chat</p></td>
</tr>
<tr class="even">
<td><p>siopID</p></td>
<td><p>GUID</p></td>
<td><p>O GUID de um suplemento é associado a esta sala de chat (categorias não possuem suplementos).</p>
<p>As informações do suplemento são consultadas na tabela SiopWhiteList.</p></td>
</tr>
<tr class="odd">
<td><p>nodeAddedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade de segurança que criou este nó.</p></td>
</tr>
<tr class="even">
<td><p>nodeAddedOn</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data/hora da criação do nó.</p></td>
</tr>
<tr class="odd">
<td><p>nodeUpdatedBy</p></td>
<td><p>int, não nulo</p></td>
<td><p>ID da entidade de segurança que efetuou a atualização mais recente deste nó.</p></td>
</tr>
<tr class="even">
<td><p>nodeUpdatedOn</p></td>
<td><p>bigint, não nulo</p></td>
<td><p>Carimbo de data/hora da última atualização deste nó.</p></td>
</tr>
<tr class="odd">
<td><p>purgedOn</p></td>
<td><p>datetime</p></td>
<td><p>Horário da última operação de limpeza (remoção de escopos da tabela tblScopedPrincipal e funções da tabela tblPrincipalRole) que afetou este nó. Usado pelo mecanismo de atualização do cache interno do serviço de chat.</p></td>
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
<td><p>nodeID</p></td>
<td><p>Chave primária.</p></td>
</tr>
<tr class="even">
<td><p>comportamento</p></td>
<td><p>Chave estrangeira com consulta na tabela tblEnumValue.valueID.</p></td>
</tr>
<tr class="odd">
<td><p>visibilidade</p></td>
<td><p>Chave estrangeira com consulta na tabela tblEnumValue.valueID.</p></td>
</tr>
<tr class="even">
<td><p>parentID</p></td>
<td><p>Chave estrangeira com pesquisa na tabela tblNode.nodeID.</p></td>
</tr>
<tr class="odd">
<td><p>siopID</p></td>
<td><p>Chave estrangeira com consulta na tabela tblSiopWhiteList.siopId.</p></td>
</tr>
</tbody>
</table>

