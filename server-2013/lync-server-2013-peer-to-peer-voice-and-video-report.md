---
title: 'Lync Server 2013: Relatório de Voz e de Vídeo Ponto a Ponto'
TOCTitle: Relatório de Voz e de Vídeo Ponto a Ponto
ms:assetid: e17c36b5-5a2f-4673-9696-3b2d31c2bb2f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615040(v=OCS.15)
ms:contentKeyID: 49308378
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Voz e de Vídeo Ponto a Ponto no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Vídeo e Voz Ponto a Ponto oferece uma visão detalhada na distribuição de chamadas de voz e vídeo por um período de tempo específico (por exemplo, chamadas por hora ou chamadas por dia). O relatório também oferece a opção de exibir todas as chamadas de voz e vídeo realizadas ou exibição apenas das chamadas com êxito ou falha. Os relatórios mostram a informação de chamadas detalhada nos seguintes agrupamentos:

  - Chamadas por pools

  - Chamadas por tipo de chamada (por exemplo, uma chamada Lync para Lync verso uma chamada Lync para uma pessoa em uma rede PSTN)

  - Chamadas por tipo de acesso (os usuários conectados na rede interna verso usuários conectados na rede externa)

  - Chamadas por Servidor de Mediação

## Par acessar o relatório de vídeo e voz ponto a ponto

É possível acessar o Relatório de Vídeo e Voz Ponto a Ponto apenas abrindo o Relatório de Resumo de Atividade Ponto a Ponto e clicando em qualquer uma das seguintes métricas:

  - Total de sessões de áudio ponto a ponto

  - Total de minutos de áudio ponto a ponto

  - Total de sessões de vídeo ponto a ponto

  - Total de minutos de vídeo ponto a ponto

## Para aproveitar melhor o relatório de vídeo e voz ponto a ponto

Existem várias formas que você pode filtrar o Relatório de Vídeo e Voz Ponto a Ponto. No entanto, estas opções de filtragem são ocultas da exibição por padrão. Para exibir as opções de filtragem disponíveis para você, clique no botão **Exibir/ocultar parâmetros** no canto superior direito da janela Relatórios.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou exibir dados de maneiras diferentes. A tabela a seguir lista os filtros que podem ser usados com o Relatório de Vídeo e Voz Ponto a Ponto.

### Filtros do relatório de vídeo e voz ponto a ponto

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
<td><p><strong>Tipo de mídia</strong></p></td>
<td><p>Indica o tipo de mídia usado na sessão. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Ambos</p></li>
<li><p>Áudio</p></li>
<li><p>Vídeo</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Disposição da chamada</strong></p></td>
<td><p>Indica o sucesso ou fracasso da sessão. Selecione uma das seguintes opções:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Chamadas de sucesso</p></li>
<li><p>Chamadas com falha</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Relatório de</strong></p></td>
<td><p>Indica os valores a serem usados no relatório. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Contagem de sessão</p></li>
<li><p>Minutos de chamada</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Métricas para atividade de vídeo e voz ponto a ponto por Pool

A tabela a seguir lista as informações fornecidas no Relatório de Vídeo e Voz Ponto a Ponto para cada pool.

### Métricas para atividade de vídeo e voz ponto a ponto por Pool

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
<td><p>Nome do Pool de registradores ou Servidor de Borda usado para a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Período de data e hora durante o qual a chamada foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>


## Métricas da atividade de vídeo e voz ponto a ponto por tipo de chamada

A tabela a seguir lista as informações fornecidas no Relatório de Vídeo e Voz Ponto a Ponto para cada tipo de chamada realizada.

### Métricas da atividade de vídeo e voz ponto a ponto por tipo de chamada

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
<td><p><strong>Tipo de chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Indica o tipo de chamada que foi realizada. Os valores são um dos seguintes:</p>
<ul>
<li><p>UC-para-UC</p></li>
<li><p>UC-para-PSTN</p></li>
<li><p>PSTN-para-UC</p></li>
<li><p>PSTN-para-PSTN</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Período de data e hora durante o qual a chamada foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>


## Métricas da atividade de vídeo e voz ponto a ponto por tipo de acesso

A tabela a seguir lista as informações fornecidas no Relatório de Vídeo e Voz Ponto a Ponto para cada tipo de acesso à rede.

### Métricas da atividade de vídeo e voz ponto a ponto por tipo de acesso

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
<td><p><strong>Tipo de atividade</strong></p></td>
<td><p>Não</p></td>
<td><p>Indica se os clientes estavam conectados na rede interna ou rede externa quando a chamada foi realizada. Os valores são normalmente um dos seguintes:</p>
<ul>
<li><p>Interna</p></li>
<li><p>Externa</p></li>
<li><p>Misto</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Período de data e hora durante o qual a chamada foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>


## Métricas para atividade de vídeo e voz ponto a ponto por servidor de mediação

A tabela a seguir lista a informação oferecida no Relatório de Vídeo e Voz Ponto a Ponto para cada Servidor de Mediação.

### Métricas para atividade de vídeo e voz ponto a ponto por servidor de mediação

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
<td><p><strong>Servidor de Mediação</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do Servidor de Mediação.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Período de data e hora durante o qual a chamada foi realizada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>

