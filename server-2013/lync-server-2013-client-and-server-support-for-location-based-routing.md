---
title: 'Lync Server 2013: Suporte a cliente e servidor para Roteamento Baseado em Local'
TOCTitle: Suporte a cliente e servidor para Roteamento Baseado em Local
ms:assetid: 26c2ca3d-026d-4dd7-94fa-15ebb4406953
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994024(v=OCS.15)
ms:contentKeyID: 52057583
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a cliente e servidor para Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Roteamento com Base no Local é imposto pelo Lync Server. O Lync Server pode identificar os locais da rede dos quais os usuários estão se conectando em uma rede corporativa. Uma vez que os usuários remotos estão fora da rede corporativa, sua localização é considerada desconhecida.

## Suporte do Lync Server

O Roteamento com Base no Local requer que o CU1 do Lync Server 2013 seja implementado em todos os Pools de Front-Ends e Servidores Standard Edition em uma determinada topologia. Se a CU1 do Lync Server 2013 não for instalado em certos componentes do Lync na topologia, as restrições de Roteamento com Base no Local não poderão ser totalmente aplicadas.

A tabela a seguir identifica a combinação de versões e funções de servidores com suporte do Roteamento com Base no Local.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Versão do pool</th>
<th>Versão do Servidor de Mediação</th>
<th>Com suporte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Atualização Cumulativa de fevereiro de 2013 do Lync Server 2013</p></td>
<td><p>Atualização Cumulativa de fevereiro de 2013 do Lync Server 2013</p></td>
<td><p>sim</p></td>
</tr>
<tr class="even">
<td><p>Atualização Cumulativa de fevereiro de 2013 do Lync Server 2013</p></td>
<td><p>Lync Server 2013</p></td>
<td><p>não</p></td>
</tr>
<tr class="odd">
<td><p>Atualização Cumulativa de fevereiro de 2013 do Lync Server 2013</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>não</p></td>
</tr>
<tr class="even">
<td><p>Atualização Cumulativa de fevereiro de 2013 do Lync Server 2013</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>não</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013</p></td>
<td><p>qualquer um</p></td>
<td><p>não</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010</p></td>
<td><p>qualquer um</p></td>
<td><p>não</p></td>
</tr>
<tr class="odd">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>qualquer um</p></td>
<td><p>não</p></td>
</tr>
</tbody>
</table>


## Suporte ao cliente Lync

A tabela a seguir identifica os clientes com suporte do Roteamento com Base no Local.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de cliente</th>
<th>Com suporte</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>sim</p></td>
<td><p>Incluindo a atualização cumulativa de fevereiro de 2013 do Lync 2013</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>sim</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>não</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>sim</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Atendedor</p></td>
<td><p>sim</p></td>
<td> </td>
</tr>
<tr class="even">
<td><p>Lync para Windows 8</p></td>
<td><p>não</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Lync Mobile 2013</p></td>
<td><p>não</p></td>
<td><p>O VoIP deve estar desativado para os clientes do Lync Mobile 2013 se usado por usuários com o Roteamento com Base no Local habilitado.</p></td>
</tr>
<tr class="even">
<td><p>Lync Mobile 2010</p></td>
<td><p>sim</p></td>
<td> </td>
</tr>
</tbody>
</table>

  

> [!NOTE]  
> Para desativar o VoIP para os clientes do Lync Mobile 2013, atribua uma política de mobilidade com a configuração Áudio/Vídeo IP desabilitada para todos os usuários habilitados para o Roteamento com Base no Local. Para maiores detalhes sobre a política de mobilidade, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy">New-CsMobilityPolicy</a>.

## Consulte Também

#### Outros Recursos

[Planejamento de Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)

