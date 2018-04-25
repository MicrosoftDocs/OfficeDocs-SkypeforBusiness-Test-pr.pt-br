---
title: O Relatório de Distribuição da Métrica de Qualidade de Mídia
TOCTitle: Relatório de Distribuição da Métrica de Qualidade de Mídia
ms:assetid: d07996e6-b0a5-4ff8-9512-ab707762b4e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205262(v=OCS.15)
ms:contentKeyID: 49308172
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# O Relatório de Distribuição da Métrica de Qualidade de Mídia

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Distribuição da Métrica de Qualidade de Mídia permite ver um gráfico que mostra os valores de distribuição para a métrica Qualidade da Experiência como jitter ou perda do pacote. Por exemplo, suponha que seus usuários fazem um total de 10 ligações telefônicas; estas 10 chamadas relatam os seguintes tempos de ida e volta:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Número da chamada</th>
<th>Tempo de ida e volta (milissegundos)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>50</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>4550</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>50</p></td>
</tr>
</tbody>
</table>


A média para estes tempos de ida e volta é de 500 milissegundos (5000 dividido por 10). Cinco mil milissegundos é um tempo de ida e volta extremamente grande; como resultado, você pode acreditar ter um sério problema com a congestão de rede. (Tempo de ida e volta longo é geralmente resultado de redes sobrecarregadas.)

Na realidade, claro,, 90% das suas chamadas possuem excelentes tempos de ida e volta; você mal tinha uma chamada em seus resultados gerais. Se procurar pelo tempo de ida e volta médio, pode terminar em uma conclusão errada.

O Relatório de Distribuição da Métrica de Qualidade de Mídia ajuda a evitar conclusões incorretas mostrando uma distribuição gráfica de uma métrica especificada (como o tempo de ida e volta). Estes gráficos ajudam a tornar claro que você possui nova chamadas muito boas e uma muito ruim. Você ainda pode desejar investigar mais que uma chamada. No entanto, o fato que 9 de 10 chamadas foram muito boas sugere que não há motivo para fazer qualquer mudança radical em sua rede, pelo menos não neste momento.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionadas ou para exibir os dados retornados de diferentes maneiras. A tabela a seguir lista os filtros que você pode usar com o Relatório de Distribuição da Métrica de Qualidade de Mídia.

### Filtros do Relatório de Distribuição da Métrica de Qualidade de Mídia

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
<p>7/7/2012 13:00 horas</p>
<p>Se você não inserir uma hora inicial, o relatório começa automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Para</strong></p></td>
<td><p>Data/hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
<p>7/7/2012 13:00 horas</p>
<p>Se você não inserir uma hora final, o relatório termina automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Mínimo no eixo x</strong></p></td>
<td><p>Menor valor para ser exibido no eixo X do gráfico.</p></td>
</tr>
<tr class="even">
<td><p><strong>Máximo no eixo x</strong></p></td>
<td><p>Maior valor para ser exibido no eixo X do gráfico.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de acesso</strong></p></td>
<td><p>Indica se um cliente estava conectado na rede interna ou na rede externa quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Interna</p></li>
<li><p>Externa</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indica se um cliente externo estava usando uma conexão de rede privada virtual (VPN) quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>VPN</p></li>
<li><p>Não-VPN</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de rede</strong></p></td>
<td><p>Indica o tipo de rede que o cliente estava conectado quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
</ul></td>
</tr>
</tbody>
</table>

