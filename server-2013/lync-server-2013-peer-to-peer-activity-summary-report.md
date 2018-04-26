---
title: 'Lync Server 2013: Relatório do Resumo de Atividades Ponto a Ponto'
TOCTitle: Relatório do Resumo de Atividades Ponto a Ponto
ms:assetid: e829a21e-9dfa-46ba-9b5b-077c175d6586
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615041(v=OCS.15)
ms:contentKeyID: 49308453
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório do Resumo de Atividades Ponto a Ponto no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Resumo de Atividades Ponto a Ponto fornece uma visão geral de suas sessões de comunicação ponto a ponto. Uma sessão ponto a ponto tipicamente envolve apenas dois usuários, e não requer o uso dos serviços de conferência do Lync Server. Em comparação, uma conferência tipicamente envolve mais de dois usuários e requer o uso dos serviços de conferência do Microsoft Lync Server 2013. Atividades de conferência são relatadas no Relatório de Resumo de Conferência.

O Relatório de Resumo de Atividade Ponto a Ponto ajuda você a responder perguntas como as seguintes:

  - Quantas mensagens instantâneas ponto a ponto meus usuários enviam em um dia normal?

  - Algum dentre os meus usuários estão de fato aprovietando os recursos de transferência de arquivo e de compartilhamento de aplicativo do Lync Server?

  - Usuários tem reclamado que a rede parece devagar em certos horários do dia. Quantos minutos são devotados para sessões de áudio e video durante estes períodos de tempo?

## Acessando o Relatório de Resumo de Atividade Ponto a Ponto

O Relatório de Resumo de Atividade Ponto a Ponto é acessado a partir da página inicial de Relatórios de Monitoramento. O [Relatório de IM Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-im-report.md) é aberto ao clicar em qualquer uma das métricas a seguir:

  - Total de sessões de mensagens instantâneas ponto a ponto

  - Total de mensagens instantâneas ponto a ponto

De modo parecido, você pode abrir o Relatório de Vídeo e Voz Ponto a Ponto clicando em qualquer uma destas métricas:

  - Total de sessões de áudio ponto a ponto

  - Total de minutos de sessão de áudio ponto a ponto

  - Total de sessões de áudio ponto a ponto

  - Total de minutos de sessão de áudio ponto a ponto

## Fazendo o Melhor Uso do Relatório de Resumo de Atividade Ponto a Ponto

Ao final do Relatório de Resumo de Atividade Ponto a Ponto, você encontrará os totais para métricas tais como Total de sessões de mensagens instantâneas ponto a ponto e Total de mensagens instantâneas ponto a ponto. Isso oferece um resumo rápido das informações detalhadas encontradas no corpo do relatório.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou de exibir os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Resumos de Atividades Ponto a Ponto permite que você escolha como os dados devem ser agrupados. Nesse caso, atividades agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Resumos de Atividades Ponta a Ponta.

### Filtros do Relatório de Resumos de Atividades Ponto a Ponto

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
<td><p>Data e hora inicial para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora inicial como a seguir:</p>
<p>7/17/2012 1:00 PM</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/17/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/13/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data e hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
<p>7/17/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/17/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/13/2012</p>
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
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com a data de início 7/17/2012 e uma data de término de 2/28/2012, os dados serão exibidos para os dias 8/7/2012 12:00 AM até 9/7/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Resumos de Atividades Ponto a Ponto.

### Métricas do Relatório de Resumos de Atividades Ponto a Ponto

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
<td><p>Indica o intervalo de tempo selecionado na barra de ferramentas do filtro. Quando aplicável, é possível clicar em um determinado intervalo de tempo para exibir informações detalhadas desse intervalo. Por exemplo, se você estiver usando o intervalo Diário e clicar em 7/17/2012, você verá uma divisão por hora da atividade de registro do usuário para essa data.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de sessões ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ponto a ponto conduzidas, independentemente do tipo de sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de sessões de mensagens instantâneas ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de mensagens instantâneas (IM) ponto a ponto. Quando você clica nesse item, o relatório mostra o Relatório de Mensagens Instantâneas Ponto a Ponto para o período selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de mensagens instantâneas ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de mensagens instantâneas enviadas em sessões ponto a ponto. Quando você clica nesse item, o relatório mostra o Relatório de Mensagens Instantâneas Ponto a Ponto para o período selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de sessões de áudio ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas de áudio ponto a ponto. Quando você clica nesse campo, o relatório mostra o Relatório de de Voz e Vídeo Ponto a Ponto para o período selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de minutos de sessão de áudio ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Tempo total gasto em sessões de áudio ponto a ponto. Quando você clica nesse item, o relatório mostra o relatório de vídeo e voz ponto a ponto para o período de tempo selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Média de minutos de sessão de áudio ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Tempo médio gasto em sessões de áudio ponto a ponto. Calculado dividindo o tempo de sessão de áudio total pelo número total de sessões de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de sessões de vídeo ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas de vídeo ponto a ponto. Observe que as sessões de vídeo também são contadas como sessões de áudio: cada sessão de vídeo é contada como uma sessão de vídeo e uma sessão de áudio. Quando você clica nesse item, o relatório mostra o relatório de vídeo e voz ponto a ponto para o período de tempo selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de minutos de sessão de vídeo ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Tempo total gasto em sessões de vídeo ponto a ponto. Quando você clica nesse item, o relatório mostra o relatório de vídeo e voz ponto a ponto para o período de tempo selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Média de minutos de sessão de vídeo ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Tempo médio gasto em sessões de vídeo ponto a ponto. Calculado dividindo o tempo de sessão de vídeo total pelo número total de sessões de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de sessões de transferência de arquivo ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ponto a ponto que incluem transferências de arquivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de sessões de compartilhamento de arquivo ponto a ponto</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ponto a ponto que incluem compartilhamento de aplicativo.</p></td>
</tr>
</tbody>
</table>

