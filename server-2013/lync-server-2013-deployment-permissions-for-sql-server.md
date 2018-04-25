---
title: 'Lync Server 2013: Permissões de implantação para Servidor SQL'
TOCTitle: Permissões de implantação para Servidor SQL
ms:assetid: 56ea0c02-bcf5-4d45-aa13-570531c29074
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398375(v=OCS.15)
ms:contentKeyID: 49306760
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Permissões de implantação para Servidor SQL no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Microsoft SQL Server 2012 tem requisitos específicos para instalação e implantação do Lync Server 2013. Como o Windows e o SQL Server definem sua segurança de forma diferente, o logon como administrador no domínio do Active Directory não concede as permissões para o SQL Server implicitamente. Você também deve ser membro da entidade sysadmin no servidor baseado no SQL Server que está configurando.

## Permissões necessárias para a instalação do banco de dados e do Lync Server

As opções a seguir detalham as três permissões e as associações de membros do grupo para a instalação dos arquivos do Lync Server 2013 e dos bancos de dados do SQL Server. Escolha o cenário que melhor atenda às necessidades de sua organização.

### Permissões e associações de membros do grupo

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>SQL Server ou função do Lync Server 2013</th>
<th>Permissões e membros de grupo típicos de função do SQL Server</th>
<th>Permissões e membros de grupo típicos de função do Lync Server 2013</th>
<th>Resultado de permissões</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Administrador do Lync Server 2013</p></td>
<td><p>Deve ser concedido a membros do grupo de segurança sysadmins do SQL Server e a membros do grupo Administradores local do SQL Server</p></td>
<td><p>Deve ser um membro do grupo RTCUniversalServerAdmins</p></td>
<td><p>O administrador do Lync Server 2013 tem as permissões adequadas para instalar os bancos de dados do Lync Server 2013e do SQL Server.</p></td>
</tr>
<tr class="even">
<td><p>Administrador do SQL Server</p></td>
<td><p>Membro do grupo sysadmin do SQL Server (ou equivalente) e membro do grupo Administradores local do SQL Server</p></td>
<td><p>Deve ser um membro do grupo RTCUniversalServerReadOnly</p></td>
<td><p>O administrador do SQL Server tem as permissões adequadas para instalar os bancos de dados do Lync Server 2013 e do SQL Server.</p></td>
</tr>
<tr class="odd">
<td><p>Os dois administradores compartilham as tarefas de instalação</p></td>
<td><p>O administrador do SQL Server é membro do grupo de sysadmins (ou equivalente) e membro do grupo Administradores local do SQL Server</p></td>
<td><p>O administrador do Lync Server 2013 é membro de RTCUniversalServerAdmins</p></td>
<td><p>O administrador do Lync Server 2013 pode instalar o Lync Server 2013, mas não pode instalar os bancos de dados. O administrador do SQL Server usa os cmdlets Shell de Gerenciamento do Lync Server e Windows PowerShell fornecidos pelo administrador do Lync Server 2013 para instalar os bancos de dados. O Shell de Gerenciamento do Lync Server 2013 usado pelo administrador do SQL Server está instalado no Servidor Front-End. Isso elimina a necessidade de instalar as ferramentas administrativas do Lync Server 2013 no servidor baseado no SQL Server.</p></td>
</tr>
</tbody>
</table>

