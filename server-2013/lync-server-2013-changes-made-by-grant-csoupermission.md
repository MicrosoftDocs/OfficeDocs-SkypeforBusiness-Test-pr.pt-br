---
title: Alterações feitas por Grant-CsOUPermission no Lync Server 2013
TOCTitle: Alterações feitas por Grant-CsOUPermission no Lync Server 2013
ms:assetid: d744d352-1ad9-4447-8e2b-28e768d2ed1b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205310(v=OCS.15)
ms:contentKeyID: 49308260
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações feitas por Grant-CsOUPermission no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para delegar a administração do Lync Server 2013, você pode adicionar permissões a unidades organizacionais especificadas para que os membros dos grupos universais RTC criados pela preparação da floresta possam acessar os OUs sem serem membros do grupo Administradores de Domínio.

O cmdlet **Grant-CsOuPermission** concede permissões para objetos no OU especificado conforme mostrado nas tabelas a seguir.

## Concedendo permissões para objetos do usuário

Ao executar o cmdlet **Grant-CsOuPermission** para objetos do Usuário em um OU, os grupos são concedidos com permissões exibidas na tabela a seguir.

### Permissões concedidas para objetos do usuário

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo</th>
<th>Permissão</th>
<th>Aplicável a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicando mudanças de diretório</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Ler RTCUserSearchPropertySet</p>
<p>Ler RTCUserProvisioningPropertySet</p>
<p>Ler RTCPropertySet</p>
<p>Ler Public-Information</p>
<p>Ler General-Information</p>
<p>Ler User-Account-Restrictions</p></td>
<td><p>Objetos do usuário descendente</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Gravara RTCUserSearchPropertySet</p>
<p>Gravar msExchUCVoiceMailSettings</p>
<p>Gravar RTCUserProvisioningPropertySet</p>
<p>Gravar RTCPropertySet</p>
<p>Gravar proxyAddresses</p></td>
<td><p>Objetos do usuário descendente</p></td>
</tr>
</tbody>
</table>


## Conceder permissões para objetos do computador

Ao executar o cmdlet **Grant-CsOuPermission** para objetos de computador em um OU, os grupos são concedidos com as permissões mostradas na tabela a seguir.

### Permissões concedidas para objetos do computador

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo</th>
<th>Permissão</th>
<th>Aplicável a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicando mudanças de diretório</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Ler Public-Information</p>
<p>Ler Validated-DNS-Host-Name</p></td>
<td><p>Objetos do computador descendente</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Ler Public-Information</p>
<p>Ler Validated-DNS-Host-Name</p></td>
<td><p>Objetos do computador descendente</p></td>
</tr>
</tbody>
</table>


## Concedendo permissões para contato ou objetos AppContact

Ao executar o cmdlet **Grant-CsOuPermission** para objetos de Contato ou AppContact em um OU, os grupos são concedidos com permissões conforme mostrado na tabela a seguir.

### Permissões concedidas para os objetos Contato ou AppContact

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo</th>
<th>Permissão</th>
<th>Aplicável a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicando mudanças de diretório</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Ler RTCUserSearchPropertySet</p>
<p>Ler RTCUserProvisioningPropertySet</p>
<p>Ler RTCPropertySet</p>
<p>Ler Public-Information</p>
<p>Ler General-Information</p>
<p>Ler Personal-Information</p>
<p>Ler User-Account-Restrictions</p></td>
<td><p>Objetos de contato descendente</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Gravar RTCUserSearchPropertySet</p>
<p>Gravar otherIpPhone</p>
<p>Gravar displayName</p>
<p>Descrição de gravação</p>
<p>Gravar telephoneNumber</p>
<p>Gravar msExchUCVoiceMailSettings</p>
<p>Gravar RTCUserProvisioningPropertySet</p>
<p>Gravar RTCPropertySet</p>
<p>Gravar proxyAddresses</p></td>
<td><p>Objetos de contato descendente</p></td>
</tr>
</tbody>
</table>


## Concedendo permissões para objetos de dispositivo

Ao executar o cmdlet **Grant-CsOuPermission** para objetos de Dispositivo em um OU, os grupos são concedidos com permissões conforme mostrado na tabela a seguir.

### Permissões concedidos para objetos de Dispositivo

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo</th>
<th>Permissão</th>
<th>Aplicável a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicando mudanças de diretório</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Ler RTCUserSearchPropertySet</p>
<p>Ler RTCUserProvisioningPropertySet</p>
<p>Ler RTCPropertySet</p>
<p>Ler Public-Information</p>
<p>Ler Personal-Information</p>
<p>Ler General-Information</p>
<p>Ler User-Account-Restrictions</p></td>
<td><p>Objetos de contato descendente</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Criar filho</p>
<p>Excluir filho</p>
<p>Excluir árvore</p></td>
<td><p>Contato</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Gravar displayName</p>
<p>Descrição de gravação</p>
<p>Gravar telephoneNumber</p></td>
<td><p>Objetos do usuário descendente</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Gravar RTCUserSearchPropertySet</p>
<p>Gravar otherIpPhone</p>
<p>Gravar displayName</p>
<p>Descrição de gravação</p>
<p>Gravar telephoneNumber</p>
<p>Gravar msExchUCVoiceMailSettings</p>
<p>Gravar RTCUserProvisioningPropertySet</p>
<p>Gravar RTCPropertySet</p>
<p>Gravar proxyAddresses</p></td>
<td><p>Objetos de contato descendente</p></td>
</tr>
</tbody>
</table>


## Concedendo permissões para objetos InetOrgPerson

Ao executar o cmdlet **Grant-CsOuPermission** para objetos InetOrgPerson em um OU, os grupos são concedidos com permissões conforme mostrado na tabela a seguir.

### Permissões concedidas para objetos InetOrgPerson

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo</th>
<th>Permissão</th>
<th>Aplicável a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Replicando mudanças de diretório</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Conteúdo da lista</p>
<p>Ler todas as propriedades</p>
<p>Permissões de leitura</p></td>
<td><p>Apenas este objeto</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Ler RTCUserSearchPropertySet</p>
<p>Ler RTCUserProvisioningPropertySet</p>
<p>Ler RTCPropertySet</p>
<p>Ler Personal-Information</p>
<p>Ler Public-Information</p>
<p>Ler General-Information</p>
<p>Ler User-Account-Restrictions</p></td>
<td><p>Objetos inetOrgPerson descendentes</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Gravar RTCUserSearchPropertySet</p>
<p>Gravar RTCUserProvisioningPropertySet</p>
<p>Gravar RTCPropertySet</p>
<p>Gravar proxyAddresses</p></td>
<td><p>Objetos inetOrgPerson descendentes</p></td>
</tr>
</tbody>
</table>

