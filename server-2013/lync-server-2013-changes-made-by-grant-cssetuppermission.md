---
title: Alterações feitas por Grant-CsSetupPermission no Lync Server 2013
TOCTitle: Alterações feitas por Grant-CsSetupPermission no Lync Server 2013
ms:assetid: c5801f48-14e3-4fdd-8f14-d52e7af07a57
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205250(v=OCS.15)
ms:contentKeyID: 49308063
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações feitas por Grant-CsSetupPermission no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para configurar o delegado, é possível conceder permissões para o grupo universal RTCUniversalServerAdmins de uma unidade organizacional (OU) do Active Directory específico, habilitando os membros do grupo RTCUniversalServerAdmins neste OU para instalar o Lync Server 2013 no domínio especificado sem ser membro do grupo de Administradores de Domínio.

O cmdlet **Grant-CsSetupPermission** concede permissões do grupo RTCUniversalServerAdmins em um OU, conforme especificado na tabela a seguir:

### Permissões concedidas para Objetos no OU

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>As permissões aplicam-se:</th>
<th>As permissões concedidas são:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalServerAdmins</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Ler servicePrincipalName</p></li>
<li><p>Gravar servicePrincipalName</p></li>
<li><p>Excluir árvore</p></li>
<li><p>Replicando mudanças de diretório</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Objetos do serviceConnectionPoint descendente</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Permissões de leitura</p></li>
<li><p>Permissões de gravação</p></li>
<li><p>Criar filho</p></li>
<li><p>Excluir filho</p></li>
<li><p>Conteúdo da lista</p></li>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Objetos msRTCSIP-Server descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Objetos msRTCSIP-WebComponents descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Objetos msRTCSIP-MCU descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Objetos msRTCSIP-MediationServer descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Objetos msRTCSIP-ApplicationServer descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Objetos msRTCSIP-ConnectionPoint descendentes</p></td>
<td><p>Acesso especial:</p>
<ul>
<li><p>Gravar propriedade</p></li>
<li><p>Ler propriedade</p></li>
<li><p>Excluir árvore</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Objetos do computador descendentes</p></td>
<td><p>Acesso especial para serviceConnectionPoint:</p>
<ul>
<li><p>Criar objetos filhos</p></li>
<li><p>Excluir objetos filhos</p></li>
<li><p>Excluir árvore</p></li>
</ul>
<p>Acesso especial para informação pública:</p>
<ul>
<li><p>Ler propriedade</p></li>
</ul>
<p>Acesso especial para nome de host DNS:</p>
<ul>
<li><p>Ler propriedade</p></li>
</ul></td>
</tr>
</tbody>
</table>

