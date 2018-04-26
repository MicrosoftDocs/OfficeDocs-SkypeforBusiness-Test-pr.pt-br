---
title: Relatório de hora de ingresso na conferência
TOCTitle: Relatório de hora de ingresso na conferência
ms:assetid: e64dc89a-25e4-4cb8-bcb1-51712e69ba5a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205344(v=OCS.15)
ms:contentKeyID: 49308431
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de hora de ingresso na conferência

 

_**Tópico modificado em:** 2015-03-09_

O Sumário de Tempo de Ingresso em Conferência permite que você determine quanto tempo demora para que seus usuários ingressem em uma conferência. Um relatório mostra o tempo médio de ingresso (em milissegundos), e também oferece um detalhamento que permite que você saiba quantos usuários foram capazes de se juntar a uma conferência em 2 segundos ou menos, quantos usuários necessitaram de 2 a 5 segundos para ingressar em uma conferência, etc.

## Acessando o Relatório de Tempo de Ingresso em Conferência

O Relatório de Tempo de Ingresso em Conferência é acessado através da página inicial dos Relatórios de Monitoramento.

## Filtros

Os filtros oferecem uma forma de retornar um conjunto de dados mais direcionado ou exibir os dados devolvidos em formas diferentes. A tabela a seguir lista os filtros que você pode usar com o Relatórios de Tempo de Ingresso em Conferência.

### Filtros de Relatório de Tempo de Ingresso em Conferência

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>De</strong></p></td>
<td><p>Data/hora inicial para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora inicial como a seguir:</p>
<p>07/07/2012 13:00</p>
<p>Se você não inserir uma hora inicial, o relatório começa automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>07/07/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>03/07/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong></p></td>
<td><p>Data/hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
<p>07/07/2012 13:00</p>
<p>Se você não inserir uma hora final, o relatório termina automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>07/07/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>03/07/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Interval</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
<li><p>Mensalmente (é possível exibir no máximo 12 meses)</p></li>
</ul>
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com a data de início 07.07.12 e uma data de término de 28.02.12, os dados serão exibidos para os dias 07.08.12 12:00 AM até 07.09.12 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN (Nome de domínio totalmente qualificado) do pool de Registradores ou Servidor de Borda. Você pode selecionar um pool individual ou clicar em <strong>[Tudo]</strong> para ver os dados de todos os pools. Essa lista suspensa é automaticamente preenchida para você com base nos registros no banco de dados.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões de conferência</strong></p></td>
<td><p>Tipo de sessão. Os valores permitidos são:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Sessões de foco</p></li>
<li><p>Compartilhamento de aplicativos</p></li>
<li><p>Conferências A/V</p></li>
</ul>
<p>Caso selecione [Todos], o tempo total de ingresso em conferência será exibido no topo do relatório. Observe que estes totais são apenas para conferências que foram agendadas usando o Microsoft Exchange ou o Microsoft Outlook.</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Tempo de Ingresso em Conferência.

### Métricas do Relatório de Tempo de Ingresso em Conferência

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
<td><p><strong>Data</strong></p>
<p>O título para essa métrica irá variar dependendo do Intervalo selecionado.</p></td>
<td><p>Não</p></td>
<td><p>Data e horário em que aconteceu a conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões, incluindo sessões bem-sucedidas, com falha (tanto falhas esperadas quanto inesperadas) e sessões não categorizadas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Média (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Média de tempo (em milissegundos) que demorou para que os participantes ingressassem na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões &lt; 2 segundos, Volume</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de participantes que conseguiram ingressar na conferência em menos de 2 segundos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões &lt; 2 segundos, Porcentagem</strong></p></td>
<td><p>Não</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões de 2 a 5 segundos, Volume</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de participantes que demoraram de 2 a 5 segundos para ingressar na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões de 2 a 5 segundos, Porcentagem</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem do total de participantes da chamada demoraram entre 2 a 5 segundos para ingressar na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões de 5 a 10 segundos, Volume</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de participantes que demoraram entre 5 a 10 segundos para ingressar na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões de 5 a 10 segundos, Porcentagem</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem do total de participantes de chamadas que demoraram entre 5 a 10 segundos para ingressar na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões &gt; 10 segundos, Volume</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de participantes que precisaram de mais de 10 segundos para ingressar na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões &gt; 10 segundos, Porcentagem</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem do total de participantes de chamadas que precisaram de mais de 10 segundos para ingressar na conferência.</p></td>
</tr>
</tbody>
</table>

