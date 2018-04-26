---
title: Relatório de tendência de localização
TOCTitle: Relatório de tendência de localização
ms:assetid: 61e2db3c-9f10-4411-8e7e-c6950faf8533
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204941(v=OCS.15)
ms:contentKeyID: 49306890
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de tendência de localização

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Tendências de Local fornece informações sobre as tendências de qualidade de chamada para locais de rede.

## Filtros

Filtros fornecem uma forma de retornar um conjunto de dados mais focado ou exibir os dados retornados de diferentes formas. Por exemplo, o Relatório de Tendências de Local permite filtrar os dados retornados por informações como tipo de acesso (ou seja, acesso interno x acesso externo) ou por conexão de rede com fio/sem fio. Você também pode escolher como os dados serão agrupados. Neste caso, as chamadas são agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Tendências de Local.

### Filtros do Relatório de Tendências de Local

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
<td><p>Data/hora de início para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora de início da seguinte maneira:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir uma hora de início, o relatório começará automaticamente às 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou do mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Para</strong></p></td>
<td><p>Data/hora de término do período. Para exibir os dados por hora, insira a data e hora de término da seguinte maneira:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir uma hora de término, o relatório terminará automaticamente às 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou do mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diário (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanal (é possível exibir no máximo 12 semanas)</p></li>
</ul>
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diário com a data de início 7/8/2012 e a data de término 28/9/2011, os dados serão exibidos para os dias de 7/8/2012 12:00 AM a 7/9/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de acesso</strong></p></td>
<td><p>Indica se o cliente estava conectado à rede interna ou à rede externa quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Interna</p></li>
<li><p>Externa</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de rede</strong></p></td>
<td><p>Indica o tipo de rede à qual o cliente estava conectado quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indica se um cliente externo estava usando uma conexão VPN (rede privada virtual) quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>VPN</p></li>
<li><p>Não VPN</p></li>
</ul></td>
</tr>
</tbody>
</table>

