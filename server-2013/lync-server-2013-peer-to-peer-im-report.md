---
title: 'Lync Server 2013: Relatório de IM Ponto a Ponto'
TOCTitle: Relatório de IM Ponto a Ponto
ms:assetid: 19ec0145-2398-437b-8989-f780c179b798
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558620(v=OCS.15)
ms:contentKeyID: 49306037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de IM Ponto a Ponto no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Mensagens Instantâneas Ponto a Ponto fornece informações de tendência sobre sessões de IM (mensagens instantâneas) ponto a ponto, detalhadas por pool e tipo de autenticação. O relatório pode mostrar o número total de sessões que aconeceram durante o período de tempo especificado (por exemplo, dia por dia ou hora por hora), ou pode mostrar o número total de mensagens instantâneas enviadas durante esse período de tempo.

## Acessando o Relatório de Mensagens Instantâneas Ponto a Ponto

Você pode acessar o Relatório de Mensagens Instantâneas Ponto a Ponto apenas abrindo o [Relatório do Resumo de Atividades Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-activity-summary-report.md) e então clicando em qualquer uma das métricas a seguir:

  - Total de sessões de mensagens instantâneas ponto a ponto

  - Total de mensagens instantâneas ponto a ponto

## Usando o Relatório de Mensagens Instantâneas Ponto a Ponto da melhor maneira possível

Por padrão, o Relatório de Mensagens Instantâneas Ponto a Ponto mostra a você a conagem de mensagens por hora (ou dia, dependendo de suas configurações). No entanto, você também pode escolher visualizar o dia por sessões por hora. Para fazer isso, clique em **Ocultar/Exibir Parâmetros** no canto superior direito da janela Relatórios, e então clique em **Contagem de Sessão** a partir da lista **Relatar por** .

## Filtros

Os filtros fornecem uma maneira de obter um resultado mais refinado de conjunto de dados ou visualizar os dados resultantes de maneiras diferentes. A tabela a seguir lista os filtros que você pode utilizar com o Relatório do Sistema de Mensagens Instantâneas Ponto a Ponto.

### Filtros do Relatório do Sistema de Mensagens Instantâneas Ponto a Ponto

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
<p>Para visualizar por semana ou por mês, digite uma data qualquer da semana ou mês (não é necessário digitar o primeiro dia da semana ou mês)</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data e hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
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
<p>Caso as datas de início e término excedam o número máximo de valores permitidos para o intervalo selecionado, será exibido somente o número máximo de valores (começando a partir da data de inicio). Por exemplo, se você selecionar o intervalo Diariamente com uma data de início em 7/7/2012 e a data de término em 2/28/2012, os dados serão exibidos para dos dias 8/7/2012 12:00 AM ao 9/7/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Relatório de</strong></p></td>
<td><p>Indica os valores a serem usados no relatório. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Contagem de sessão</p></li>
<li><p>Contagem de mensagem</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Medição da sessão do Sistema de Mensagens Instantâneas Ponto a Ponto por Pool

A tabela a seguir lista as informações fornecidas pelo Relatório do Sistema de Mensagens Instantâneas Ponto a Ponto.

### Medição da sessão do Sistema de Mensagens Instantâneas Ponto a Ponto por Pool

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
<td><p>Nome do Pool de registradores ou do Servidor de Borda.</p></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora em que a sessões ocorreram.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>


## Medição da sessão do Sistema de Mensagens Instantâneas Ponto a Ponto por tipo de autenticação

A tabela a seguir lista as informações fornecidas pelo Relatório do Sistema de Mensagens Instantâneas Ponto a Ponto para cada tipo de autenticação usada pelos participantes em uma sessão ponto a ponto.

### Medição da sessão do Sistema de Mensagens Instantâneas Ponto a Ponto por tipo de autenticação

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
<td><p><strong>Tipo de Autenticação</strong> :</p></td>
<td><p>Não</p></td>
<td><p>Tipo de autenticação usada pelos participantes da sessão. Normalmente, os valores são um dos seguintes:</p>
<ul>
<li><p>Empresa</p></li>
<li><p>Federado</p></li>
<li><p>PIC</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Data/Hora</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora em que a sessões ocorreram.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ou contagem total de mensagens.</p></td>
</tr>
</tbody>
</table>

