---
title: Relatório de detalhes da conferência
TOCTitle: Relatório de detalhes da conferência
ms:assetid: 1d61cd81-dcfe-40b4-9a41-a73b038bc216
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204728(v=OCS.15)
ms:contentKeyID: 49306071
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de detalhes da conferência

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Detalhe da Conferência oferece informações detalhadas sobre todos os usuários que participaram de uma conferência. Por exemplo, você pode ver tal informação como a data e hora que um usuário participou da conferência, a data e hora que o usuário saiu da conferência e o agente do usuário do ponto de extremidade que foi usado para conectar o usuário à conferência. Também é possível ver informações da função do usuário em cada conferência (por exemplo, Apresentador ou Participante). Talvez, o mais importante, você pode ver rapidamente quais usuários participaram com sucesso e concluíram a conferência e quais usuários não puderam participar e concluir a conferência.

## Acessar o Relatório de Detalhe da Conferência

O Relatório de Detalhe da Conferência pode ser acessado pelos seguintes relatórios:

  - O [Relatório de Ccontrole de Admissão de Chamadas no Lync Server 2013](lync-server-2013-call-admission-control-report.md) (clicando na métrica Detalhe de uma conferência)

  - O [Relatório de lista de falhas no Lync Server 2013](lync-server-2013-failure-list-report.md) (clicando na métrica Conferência)

  - O [Relatório de Atividades do Usuário no Lync Server 2013](lync-server-2013-user-activity-report.md) (clicando na métrica URI da conferência)

Do Relatório de Detalhe da Conferência, é possível acessar o [Relatório de diagnósticos no Lync Server 2013](lync-server-2013-diagnostic-report.md) clicando na métrica Relatório de Diagnóstico (Detalhe).

## Filtros

Nenhum. Você não pode filtrar o Relatório de Detalhe da Conferência.

## Métricas

A tabela a seguir lista as informações fornecidas na seção Informação da Conferência do Relatório de Detalhe da Conferência.

### Métricas de Informação da Conferência

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>É possível classificar este item?</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>URI de Conferência</strong></p></td>
<td><p></p></td>
<td><p>URI atribuído à conferência. Por exemplo:</p>
<p>sip:kmyer@litwareinc.com;gruu;opaque=app:conf:focus:id:drg2y8v4</p></td>
</tr>
<tr class="even">
<td><p><strong>FQDN do Pool</strong></p></td>
<td><p></p></td>
<td><p>Nome de domínio totalmente qualificado do pool do Registrador ou Servidor de Borda envolvido em uma sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora inicial</strong></p></td>
<td><p></p></td>
<td><p>Data e hora que a conferência iniciou.</p></td>
</tr>
<tr class="even">
<td><p><strong>Organizador</strong></p></td>
<td><p></p></td>
<td><p>Endereço SIP do usuário que organizou a conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p></p></td>
<td><p>Data e hora que a conferência terminou.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir lista a informação oferecida na Seção de Participação da Conferência do Relatório de Detalhe da Conferência.

### Métricas de Participação da Conferência

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>É possível classificar este item?</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Usuário</strong></p></td>
<td><p></p></td>
<td><p>Endereço SIP do usuário que participou da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Função</strong></p></td>
<td><p></p></td>
<td><p>Função (por exemplo, Apresentador) do participante da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Conectividade</strong></p></td>
<td><p></p></td>
<td><p>Conectividade de rede (geralmente Externa ou Interna) do participante.</p></td>
</tr>
<tr class="even">
<td><p>Hora de participação</p></td>
<td><p></p></td>
<td><p>Data e hora que o participante entrou na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora de saída</strong></p></td>
<td><p></p></td>
<td><p>Data e hora que o participante saiu da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Agente do usuário</strong></p></td>
<td><p></p></td>
<td><p>Identificador do software usado pelo ponto de extremidade do participante.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Relatórios de diagnóstico</strong></p></td>
<td><p></p></td>
<td><p>Oferece informação de resolução de problemas e diagnósticos. Incluindo códigos de resposta SIP, cabeçalhos de diagnóstico, hora de participação da conferência e IDs de diagnóstico para sessões em falha.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir lista a informação oferecida na seção Modalidades de Conferência do Relatório de Detalhe da Conferência.

### Métricas das Modalidades da Conferência

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>É possível classificar este item?</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Usuário</strong></p></td>
<td><p></p></td>
<td><p>Endereço SIP do usuário que participou da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora de participação</strong></p></td>
<td><p></p></td>
<td><p>Data e hora que o participante entrou na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora de saída</strong></p></td>
<td><p></p></td>
<td><p>Data e hora que um participante deixou a conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>URI do servidor de conferência</strong></p></td>
<td><p></p></td>
<td><p>URI para o servidor de Conferência usado na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Relatórios de diagnóstico</strong></p></td>
<td><p></p></td>
<td><p>Oferece informação de resolução de problemas e diagnóstico. Incluindo códigos de resposta SIP, cabeçalhos de diagnóstico, hora de participação da conferência e IDs de diagnósticos para sessões em falha.</p></td>
</tr>
</tbody>
</table>

