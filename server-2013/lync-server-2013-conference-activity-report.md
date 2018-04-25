---
title: 'Lync Server 2013: Relatório de Atividades de Conferência'
TOCTitle: Relatório de Atividades de Conferência
ms:assetid: 22ddb509-af16-4fc8-9b98-6f58caa6f37e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558627(v=OCS.15)
ms:contentKeyID: 49306131
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Atividades de Conferência no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Atividade de Conferência torna fácil responder perguntas como estas: quantas conferências estão sendo realizadas diariamente e quando estas conferências são realizadas? Informações como estas são úteis não apenas em seu próprio direito, mas também como uma ferramenta de resolução de problemas. Por exemplo, vamos supor que os usuários estão reclamando que a rede parece particularmente lenta no meio do dia. Uma rápida visualização dos relatórios de Atividade de Conferência pode sugerir uma razão possível: muitas conferências estão sendo programadas entre as 10:00 horas e as 14:00 horas do que em qualquer outro horário.

Se a rede lenta está causando problemas, é possível incentivar os usuários a reprogramar algumas de suas conferências durante horários com menos tráfego durante o dia.

## Acessando o Relatório de Atividade da Conferência

O Relatório de Atividade da Conferência é acessado em [Relatório de Resumo da Conferência no Lync Server 2013](lync-server-2013-conference-summary-report.md) clicando em uma das seguintes métricas:

  - Conferências totais

  - Total de participantes

## Tendo o melhor uso do Relatório de Atividade de Conferência

Por padrão, o Relatório de Atividade de Conferência mostra o número total de conferências para um determinado período de tempo (por exemplo, o número total de conferências por dia ou o número total de conferências por hora do dia). No entanto, é possível escolher exibir o número total de participantes neste período de tempo ou o número total de participantes em minutos. Para fazer isso, clique no botão Exibir/Ocultar parâmetros para exibir as opções de filtragem e selecione um dos seguintes na lista suspensa Relatar por:

  - Contagem de participantes

  - Minutos dos participantes

  - Contagem de conferência

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionadas ou para exibir os dados retornados de diferentes maneiras. A tabela a seguir lista os filtros que você pode usar com o Relatório de Atividades de Conferência.

### Filtros de relatório de atividade de conferência

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
<td><p>Data/hora de início para o intervalo de tempo. Para ver os dados por horas, insira a data e hora de início conforme segue:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora final de intervalo de tempo. Para ver os dados por horas, insira a data e hora final conforme segue:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione qualquer um dos seguintes:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
<li><p>Mensalmente (é possível exibir no máximo 12 meses)</p></li>
</ul>
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com data de início em 7/7/2012 e data de término de 2/28/2012, os dados serão exibidos do dia 8/7/2012, às 12:00 AM, até o dia 9/7/2012, às 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Relatório de</strong></p></td>
<td><p>Indica os valores a serem usados no relatório. Você pode selecionar um dos seguintes:</p>
<ul>
<li><p>Contagem de participantes</p></li>
<li><p>Minutos dos participantes</p></li>
<li><p>Contagem de conferência</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Métricas para conferências por pool

A tabela a seguir lista as informações no Relatório de Atividade de Conferência para cada pool.

### Métricas para conferências por pool

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
<td><p><strong>Pool</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do pool do Registrador ou Servidor de Borda usado na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora de quando a conferência foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Contagem total de participantes, minutos totais de participantes ou contagem total da conferência.</p></td>
</tr>
</tbody>
</table>


## Métricas para conferência por tipo de servidor

A tabela a seguir lista as informações no relatório de atividade de conferência para cada tipo de servidor.

### Métricas para conferência por tipo de servidor

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
<td><p><strong>Tipo de servidor de conferência</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de servidor usado na conferência, geralmente um dos seguintes:</p>
<ul>
<li><p>Servidor de conferência da Web</p></li>
<li><p>Servidor de conferência de IM</p></li>
<li><p>Servidor de conferência com telefonia</p></li>
<li><p>Servidor de conferência de AV.</p></li>
<li><p>Compartilhamento de Aplicativos</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora de quando a conferência foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Contagem total de participantes, minutos totais de participantes ou contagem total da conferência.</p></td>
</tr>
</tbody>
</table>

