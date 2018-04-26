---
title: 'Lync Server 2013: Relatório de Resumo da Conferência'
TOCTitle: Relatório de Resumo da Conferência
ms:assetid: 62f54812-5700-45a3-8526-8f58b0f77fbc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558656(v=OCS.15)
ms:contentKeyID: 49306909
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Resumo da Conferência no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Resumo de Conferências traz uma visão geral de suas sessões de conferência online. Uma conferência geralmente envolve mais do que dois usuários e exige o uso dos serviços de conferência do Microsoft Lync Server 2013. Por outro lado, uma sessão ponto a ponto geralmente envolve apenas dois usuários e não exige o uso dos serviços de conferência do Lync Server. As atividades ponto a ponto são relatadas no [Relatório do Resumo de Atividades Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-activity-summary-report.md).

O Relatório de Resumo de Conferências além de informar quantas conferências foram realizadas durante determinado período (por hora, diária, semanal ou mensalmente), também mostra o número total de pessoas que participaram dessas conferências e o número total de organizadores de conferência exclusivos.

Um organizador "exclusivo" é qualquer pessoa que agenda pelo menos uma conferência. Por exemplo, se Pilar Ackerman agendar uma conferência, ela será contabilizada como um organizador exclusivo. Se Ken Myer agendar 148 conferências, ele também será contabilizado como um único organizador exclusivo. Por exemplo, a tabela a seguir mostra oito conferências agendadas, mas apenas três organizadores exclusivos (Ken Myer, Pilar Ackerman e David Ahs).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Organizador da conferência</th>
<th>Data da conferência</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>David Ahs</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 1:00 PM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 2:00 PM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
</tbody>
</table>


O Relatório de Resumo de Conferências também indica quantas conferências incluíram áudio e/ou vídeo.

## Acessando o Relatório de Resumo de Conferências

O Relatório de Resumo de Conferências pode ser acessado na home page Relatórios de Monitoramento. Você pode filtrar pelo Relatório de Atividade de Conferência clicando em uma das métricas a seguir:

  - Conferências totais

  - Total de participantes

## Usando o Relatório de Resumo de Conferências da melhor maneira possível

Os valores totais da maioria das métricas usadas no Relatório de Resumo de Conferências constam na parte inferior do relatório. Desça para ver valores como o número total de conferências realizadas durante o período de tempo especificado e o número total de pessoas que participaram dessas conferências. Uma métrica que não é um total na parte inferior do relatório é Total de organizadores de conferências exclusivas. Por que não? Um dos motivos é o seguinte: suponha que você esteja analisando os dados referentes a um mês inteiro. No dia 1º, há 34 organizadores de conferência exclusivos. No dia 2, há 27 organizadores de conferência exclusivos. Isso significa que há 61 organizadores de conferência exclusivos nesses dois dias? Não necessariamente. Afinal, as 27 pessoas que organizaram conferências no dia 2 podem estar entre as 34 pessoas que organizaram conferências no dia 1º. Por exemplo, neste relatório simples, veja que Ken Myer e Pilar Ackerman agendaram conferências tanto no dia 7/7/2012 como no dia 7/2/2012:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Organizador da conferência</th>
<th>Data da conferência</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>David Ahs</p></td>
<td><p>7/7/2012 10:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 11:00 AM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/7/2012 1:00 PM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/7/2012 2:00 PM</p></td>
</tr>
<tr class="odd">
<td><p>Ken Myer</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
<tr class="even">
<td><p>Pilar Ackerman</p></td>
<td><p>7/2/2012 10:00 AM</p></td>
</tr>
</tbody>
</table>


Para ter uma ideia melhor do número total de usuários exclusivos que organizaram conferências, altere o intervalo de tempo. Por exemplo, exiba os dados por mês e não por dia.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou de exibir os dados retornados de diferentes maneiras. Por exemplo, o Relatório de Resumo de Conferências permite que você escolha como os dados devem ser agrupados. Nesse caso, conferências agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que você pode usar com o Relatório de Resumo de Conferências.

### Filtros do Relatório de Resumo de Conferências

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
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
<li><p>Mensalmente (é possível exibir no máximo 12 meses)</p></li>
</ul>
<p>Se as datas de início e término excedem o número máximo de valores permitidos para o intervalo selecionado, apenas o número máximo de valores (começando pela data de início) será exibido. Por exemplo, se você selecionar o intervalo Diário com a data de início 7/7/2012 e a data de término 2/28/2012, os dados serão exibidos para o intervalo de 8/7/2012 12:00 AM a 9/7/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir as informações fornecidas pelo Relatório de Resumo de Conferências.

### Métricas do Relatório de Resumo de Conferências

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
<td><p><strong>Por hora</strong></p>
<p><strong>Diário</strong></p>
<p><strong>Semanal</strong></p>
<p><strong>Mensal</strong></p></td>
<td><p>Não</p></td>
<td><p>Indica o intervalo de tempo selecionado na barra de ferramentas de filtro. Quando aplicável, é possível clicar em determinado intervalo de tempo para exibir informações detalhadas sobre ele. Por exemplo, se você estiver usando o intervalo Diário e clicar em 7/7/2012, verá um detalhamento por hora da atividade de registro do usuário para a data em questão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Conferências totais</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de conferências (independentemente do tipo de conferência) que foram mantidas. Quando você clica nesse item, o relatório mostra o Relatório de Resumo de Conferências para o período de tempo selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de participantes</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de pessoas que participaram nas conferências. Quando você clica nesse item, o relatório mostra o Relatório de Resumo de Conferências para o período de tempo selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Média de participantes por conferência</strong></p></td>
<td><p>Não</p></td>
<td><p>Número médio de pessoas que participaram de uma determinada conferência. É determinado dividindo o total de conferências pelo total de participantes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de conferências A/V</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de conferências com áudio ou vídeo.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de minutos de conferências de A/V</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de minutos para a conferência de áudio/vídeo.</p>
<p>A métrica do total de minutos de conferências de A/V resume todos os tipos de conferências de áudio/vídeo, incluindo: conferências de A/V; conferências de IM; conferências de compartilhamento de aplicativos; conferências de dados; e conferências de PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de minutos de participantes de conferências de A/V</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de minutos do participante na conferência de áudio/vídeo. Por exemplo, suponha que um usuário gaste cinco minutos em uma conferência de áudio/vídeo e um segundo usuário gaste três minutos nessa mesma conferência. O que soma um total de oito minutos de participantes: cinco minutos mais três minutos.</p></td>
</tr>
<tr class="even">
<td><p><strong>Média de minutos da conferência A/V</strong></p></td>
<td><p>Não</p></td>
<td><p>Número médio de minutos por conferência de áudio/vídeo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Número total de organizadores exclusivos de conferências</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de usuários que organizaram pelo menos uma conferência. Os usuários que organizaram mais de uma conferência são contados como um organizador exclusivo, assim como os usuários que só organizaram uma única conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de mensagens de conferência</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de mensagens instantâneas enviadas durante as conferências.</p></td>
</tr>
</tbody>
</table>

