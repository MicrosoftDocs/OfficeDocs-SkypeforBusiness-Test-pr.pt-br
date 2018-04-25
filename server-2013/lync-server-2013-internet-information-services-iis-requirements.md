---
title: 'Lync Server 2013: Requisitos de Serviços de Informações da Internet (IIS)'
TOCTitle: Requisitos de Serviços de Informações da Internet (IIS)
ms:assetid: 4f57a605-a8a9-4c5a-9a18-05ecb3d9ab6b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398321(v=OCS.15)
ms:contentKeyID: 49306680
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de Serviços de Informações da Internet (IIS) no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Vários componentes do Lync Server 2013 exigem o IIS (Serviços de Informações da Internet). Este tópico descreve os recursos específicos do IIS necessários para dar suporte ao Lync Server. Os tópicos desta seção descrevem os requisitos de componentes específicos para o IIS.

Quando a função Servidor Web (IIS) está habilitada no Windows Server 2008, vários serviços de função são instalados por padrão. A tabela a seguir descreve os serviços de função adicionais que devem ser instalados quando a função Servidor Web (IIS) está habilitada no Windows Server 2008.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Serviço de função</th>
<th>Recurso</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Redirecionamento HTTP</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>ASP.NET</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Extensibilidade .NET</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Extensões ISAPI</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Filtros ISAPI</p></td>
</tr>
<tr class="even">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Ferramentas de log</p></td>
</tr>
<tr class="odd">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Rastreamento</p></td>
</tr>
<tr class="even">
<td><p>Segurança</p></td>
<td><p>Autenticação básica</p></td>
</tr>
<tr class="odd">
<td><p>Segurança</p></td>
<td><p>Autenticação do Windows</p></td>
</tr>
<tr class="even">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Ferramentas e scripts de gerenciamento IIS</p></td>
</tr>
<tr class="odd">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Compatibilidade com gerenciamento do IIS 6</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg399038.security(OCS.15).gif" title="security" alt="security" />Segurança Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Se você estiver usando o IIS 7.0 em um sistema operacional Windows Server 2008, a Configuração do Lync Serverdesabilitará a autenticação de modo kernel no IIS.</td>
</tr>
</tbody>
</table>


## Nesta seção

  - [Requisitos de IIS para pools Front-End pools e servidores Standard Edition no Lync Server 2013](lync-server-2013-iis-requirements-for-front-end-pools-and-standard-edition-servers.md)

