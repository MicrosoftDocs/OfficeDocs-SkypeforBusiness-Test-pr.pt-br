---
title: Alterações de esquema no Lync Server 2013
TOCTitle: Alterações de esquema no Lync Server 2013
ms:assetid: d760cb93-77d4-4d64-adb7-416b808f36f8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398944(v=OCS.15)
ms:contentKeyID: 49308264
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações de esquema no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Antes de implantar e operar o Lync Server 2013, é necessário preparar o Serviços de Domínio Active Directory estendendo o esquema. As extensões de esquema adicionam as classes e os atributos exigidos pelo Lync Server 2013.

O Lync Server 2013 exige diversas classes e atributos novos e modifica algumas classes e atributos existentes. Além disso, grande parte das informações de configuração para o Lync Server 2013 são armazenadas no Repositório de Gerenciamento Central em vez do AD DS como nas versões anteriores. As seguintes informações ainda são armazenadas no AD DS no Lync Server 2013:

  - **Extensões de esquema**:
    
      - Extensões do objeto do usuário
    
      - Extensões para as classes Office Communications Server 2007 e Office Communications Server 2007 R2 para manter compatibilidade com versões anteriores

<!-- end list -->

  - **Dados** (armazenados no esquema estendido do Lync Server e nas classes de esquema existentes):
    
      - URI (Uniform Resource Identifier) SIP do usuário e outras configurações de usuário
    
      - Objetos de contato para aplicativos, como Grupo de Respostas e Atendedor de Conferência
    
      - Um ponteiro para o Repositório de Gerenciamento Central
    
      - Conta de autenticação Kerberos (um objeto de computador opcional)

Este tópico descreve as alterações no esquema do Active Directory exigidas pelo Lync Server 2013. Ele não descreve as alterações de esquema introduzidas por versões anteriores do Office Communications Server. Para obter uma lista das classes e suas descrições, consulte [Classes e descrições de esquema no Lync Server 2013](lync-server-2013-schema-classes-and-descriptions.md). Para obter uma lista de atributos e suas descrições, consulte [Atributos e descrições de esquema no Lync Server 2013](lync-server-2013-schema-attributes-and-descriptions.md). Para obter uma lista de classes com os atributos que elas possam conter, consulte [Atributos de esquema por classe no Lync Server 2013](lync-server-2013-schema-attributes-by-class.md).

O prefixo msRTCSIP identifica classes e atributos específicos ao Lync Server.

## Novos atributos do Active Directory

A tabela a seguir descreve os atributos do Active Directory adicionados pelo Lync Server 2013.

### Atributos adicionados pelo Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Atributo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>Este atributo de vários valores mantém identificadores para manter políticas aplicadas ao usuário. Políticas de retenção preservam os itens das caixas de correio para o usuário pela duração da retenção. Este atributo é compartilhado com o Exchange 2013.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>Este é o ID do grupo de roteamento SIP. Os usuários no mesmo grupo irão ser registrados para o mesmo Servidor de Front-end.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>Este atributo é usado para armazenar o backend do SQL Server espelhado usado pelo Pool de Front-Ends.</p></td>
</tr>
</tbody>
</table>


## Classes do Active Directory modificadas

A tabela a seguir descreve as classes do Active Directory que são modificadas pelo Lync Server 2013.

### Classes modificadas pelo Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Classe</th>
<th>Alteração</th>
<th>Classe ou atributo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuário</p></td>
<td><p>add: mayContain</p>
<p>add: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="even">
<td><p>Contato</p></td>
<td><p>add: mayContain</p>
<p>add: mayContain</p></td>
<td><p>ProxyAddresses</p>
<p>msRTCSIP-UserRoutingGroupId</p></td>
</tr>
<tr class="odd">
<td><p>Mail-Recipient</p></td>
<td><p>add: mayContain</p></td>
<td><p>msExchUserHoldPolicies</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalTopologySetting</p></td>
<td><p>add: mayContain</p></td>
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
</tr>
</tbody>
</table>

