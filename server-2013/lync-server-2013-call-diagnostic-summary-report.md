---
title: 'Lync Server 2013: Relatório de Resumo de Diagnóstico de Chamadas'
TOCTitle: Relatório de Resumo de Diagnóstico de Chamadas
ms:assetid: 9091de56-13e6-440e-9353-f57c10c906fe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615016(v=OCS.15)
ms:contentKeyID: 49307466
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Resumo de Diagnóstico de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Resumo de Diagnóstico de Chamadas fornece uma visão geral de sessões peer-to-peer e de conferências que falharam. O relatório mostra a taxa de falha geral para os dois tipos de sessão, e detalha as informações de falha por tipo de modalidade de sessão:

  - Mensagens instantâneas

  - Compartilhamento de aplicativos

  - Transferência de arquivos

  - Áudio

  - Vídeo

## Como acessar o Relatório de resumo de diagnóstico de chamadas

O Relatório de resumo de diagnóstico de chamadas é acessado a partir da página inicial dos Relatórios de Monitoramento. A partir do Relatório de resumo de diagnóstico de chamadas, você pode acessar o [Relatório de Diagnóstico de Atividade Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md) clicando na métrica de taxa de falha sob a seção Resumo da Sessão Peer-to-Peer. Você pode também ascessar [Relatório de Diagnósticos da Conferência no Lync Server 2013](lync-server-2013-conference-diagnostic-report.md), clicando em qualquer das seguintes métricas da conferência:

  - Taxa de falha de sessão geral

  - Taxa de falha de foco

  - Taxa de falha de MCU

## Como usar melhor o Relatório de resumo de diagnóstico de chamadas

O Relatório de resumo de diagnóstico de chamadas contém gráficos que comparam taxas de falha de várias modalidades usadas no Microsoft Lync Server 2013. As colunas nesses gráficos são na verdade hotlinks; por exemplo, se você clicar na coluna Mensagens Instantâneas para sessões peer-to-peer, você obterá os detalhes de uma instância do [Relatório de Diagnóstico de Atividade Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md), um relatório que fornece mais detalhes sobre todas as sessões de mensagens instantâneas inclusas no Relatório de resumo de diagnóstico de chamadas.

## Filtros

Filtros fornecem uma forma de retornar um conjunto de dados mais focado ou exibir os dados retornados de diferentes formas. Por exemplo, o Relatório de Resumo de Diagnóstico de Chamadas permite filtrar por informações como pool do Registrador Avançado ou Servidor de Borda usado na sessão. Você também pode escolher como os dados serão agrupados. Neste caso, as chamadas são agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Resumo de Diagnóstico de Chamadas.

### Filtros do Relatório de Resumo de Diagnóstico de Chamadas

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
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com data de início em 7/7/2012 e data de término de 2/28/2012, os dados serão exibidos do dia 8/7/2012, às 12:00 AM, até o dia 9/7/2012, às 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN (Nome de domínio totalmente qualificado) do pool de Registradores ou Servidor de Borda. Você pode selecionar um pool individual ou clicar em <strong>[Tudo]</strong> para ver os dados de todos os pools. Essa lista suspensa é automaticamente preenchida para você com base nos registros no banco de dados.</p></td>
</tr>
</tbody>
</table>


## Métricas para sessões ponto a ponto

A tabela a seguir lista as informações fornecidas no Relatório de Resumo de Diagnóstico de Chamadas para sessões ponto a ponto (ou seja, sessões envolvendo somente dois participantes).

### Métricas para sessões ponto a ponto

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
<td><p><strong>Total de sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ponto a ponto conduzidas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de falha</strong></p></td>
<td><p>Não</p></td>
<td><p>Percentual de sessões ponto a ponto que falharam. Ao clicar neste item, o relatório exibe o relatório de Diagnóstico de Atividades Ponto a Ponto, que mostra informações mais detalhadas sobre as sessões ponto a ponto com falha.</p></td>
</tr>
</tbody>
</table>


## Métricas para sessões de conferência

A tabela a seguir lista as informações fornecidas pelo Relatório de Diagnóstico de Chamadas para sessões de conferência (ou seja, sessões envolvendo três ou mais participantes).

### Métricas para sessões de conferência

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
<td><p><strong>Conferências totais</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de conferências conduzidas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões de conferência totais</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de conferência conduzidas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha de sessão geral</strong></p></td>
<td><p>Não</p></td>
<td><p>Percentual de sessões de conferência totais que falharam.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões de Foco</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de conferência baseadas em Foco que falharam.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha de Foco</strong></p></td>
<td><p>Não</p></td>
<td><p>Percentual de sessões de conferência baseadas em Foco que falharam.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões MCU</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de conferências baseadas em servidor (anteriormente conhecidas como Unidade de Controle de Multipontos ou MCU) que falharam.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha de MCU</strong></p></td>
<td><p>Não</p></td>
<td><p>Percentual de conferências baseadas em servidor (anteriormente conhecidas como Unidade de Controle de Multipontos ou MCU) que falharam.</p></td>
</tr>
</tbody>
</table>

