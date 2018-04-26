---
title: 'Lync Server 2013: Tabela UserAgent'
TOCTitle: Tabela UserAgent
ms:assetid: d6bda1c0-b053-457a-9ffa-2ae859788775
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398939(v=OCS.15)
ms:contentKeyID: 49308255
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela UserAgent no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela UserAgent é uma tabela de suporte que armazena uma lista de vários agentes de usuário que participaram de sessões registradas no banco de dados. Cada registro na tabela representa um agente de usuário.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Coluna</strong></th>
<th><strong>Tipo de dados</strong></th>
<th><strong>Chave/Índice</strong></th>
<th><strong>Detalhes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>UserAgentKey</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Número exclusivo que identifica esse agente do usuário.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserAgent</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Exclusivo</p></td>
<td><p>Sequência do agente do usuário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UAType</strong></p></td>
<td><p>smallint</p></td>
<td><p> </p></td>
<td><p>1 é o Servidor de Mediação.</p>
<p>2 é o Servidor de Conferência A/V.</p>
<p>4 é Lync.</p>
<p>8 é Telefone IP.</p>
<p>16 é o console do Live Meeting.</p>
<p>32 é a Deployment Validation Tool (DVT).</p>
<p>64 é Lync em computadores Macintosh.</p>
<p>128 é o Office Communications Server 2007 R2 Attendant.</p>
<p>256 é o serviço Anúncio de Conferência.</p>
<p>512 é Atendedor Automático de Conferência.</p>
<p>1024 é o aplicativo Grupo de Resposta.</p>
<p>2048 é o Controle de Voz Externo.</p></td>
</tr>
</tbody>
</table>

