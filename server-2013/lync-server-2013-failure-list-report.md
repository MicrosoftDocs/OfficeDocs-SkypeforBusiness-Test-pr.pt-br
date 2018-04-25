---
title: 'Lync Server 2013: Relatório de lista de falhas'
TOCTitle: Relatório de lista de falhas
ms:assetid: b6f3a605-e0c6-461e-b17a-41d8039ace9d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615446(v=OCS.15)
ms:contentKeyID: 49307880
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de lista de falhas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

The Failure List report provides information about the individual participants who took part in a failed peer-to-peer or conferencing session. This information includes the URI of the user who experienced the problem, as well as the SIP Response code and Diagnostic ID associated with the failure.

## Accessing the Failure List Report

The Failure List Report is accessed by clicking any of the following metrics on the [Relatório de Distribuição de Falha no Lync Server 2013](lync-server-2013-failure-distribution-report.md):

  - Top diagnostic reasons (sessions)

  - Top modalities (sessions)

  - Top pools (sessions)

  - Top sources (sessions)

  - Top components (sessions)

  - Top from users (sessions)

  - Top to users (sessions)

  - Top from user agents (sessions)

From the Failure List Report you can access the [Relatório de Detalhes de Sessão Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md) by clicking the Session detail metric for a peer-to-peer session. You can also access the Conference Detail Report by clicking the Conference metric for a conference.

## Making the Best Use of the Failure List Report

In the Failure List Report, you can view a description for each Response code or each Diagnostic ID simply by holding your mouse over that value. For example, if you hold your mouse over Diagnostic ID 7025 you'll see the following displayed in a tooltip:

Internal server error creating media for user.

It's important to note that the Failure List Report does not provide a straightforward way to directly retrieve a list of all the users who participated in at least one failed session, nor does it provide a way to determine which users were most-often involved in a failed session. (For one thing, the Failure List Report has no filtering capabilities.) However, if you export the data and then convert it to a comma-separated values file, you can use Windows PowerShell to find the answers to questions like those. For example, suppose you save the data to a .CSV file named C:\\Data\\Failure\_List.csv. Based on the data saved in that file, this command lists all the users who were involved in at least one failed session:

    $failures = Import-Csv -Path " C:\Data\Failure_List.csv"
    $failure |Sort-Object "From user" | Select-Object "From user" -Unique

That command will return a list similar to this:

    From user
    ----
    Pilar.Ackerman@litwareinc.com
    Henrik.Jensen@litwareinc.com
    Gilead.Amosnino@litwareinc.com
    David.Ahs@litwareinc.com
    Ken.Myer@litwareinc.com

These two commands report back the total number of failed sessions that each user was involved in:

    $failures = Import-Csv -Path "C:\Data\Failure_List.csv"
    $failures | Group-Object "From user" | Select-Object Count, Name | Sort-Object -Property Count -Descending

That will return data similar to this:

    Count    Name
     -----    ----
        20    Pilar.Ackerman@litwareinc.com
        20    David.Ahs@litwareinc.com
        16    Gilead.Amosnino@litwareinc.com
        16    Ken.Myero@litwareinc.com
        14    Henrik.Jensen@litwareinc.com

## Filtros

Nenhum. Não é possível filtrar o Relatório de Lista de Falhas.

## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Lista de Falhas para cada chamada mal-sucedida.

### Métricas do Relatório de Lista de Falhas

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Você pode classificar este item?</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Hora de relatório</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora do registro do relatório.</p></td>
</tr>
<tr class="even">
<td><p><strong>Solicitação</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de solicitação SIP que falhou. Por exemplo, CONVIDAR ou ATÉ LOGO.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Código da resposta</strong></p></td>
<td><p>Não</p></td>
<td><p>Código da resposta SIP enviado quando a conferência falhou.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho ms-diagnostics) anexado a uma mensagem SIP que frequentemente fornece informações úteis para solução de erros.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Join cost time (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Amount of time (in milliseconds) required for the user to join the conference.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuário &quot;De&quot;</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Representante do usuário de origem</strong></p></td>
<td><p>Não</p></td>
<td><p>Software usado pelo ponto de extremidade do usuário que iniciou a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuário &quot;Para&quot;</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que estava recebendo a chamada.</p></td>
</tr>
</tbody>
</table>

