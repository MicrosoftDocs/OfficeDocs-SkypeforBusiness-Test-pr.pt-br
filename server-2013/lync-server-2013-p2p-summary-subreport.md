---
title: Subrelatório de Resumo P2P
TOCTitle: Subrelatório de Resumo P2P
ms:assetid: fc36185a-3cc5-4167-8c93-8a755fa75ac7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205416(v=OCS.15)
ms:contentKeyID: 49308703
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Subrelatório de Resumo P2P

 

_**Tópico modificado em:** 2015-03-09_

O Subrelatório de Resumo P2P oferece uma visão geral das sessões de comunicação ponto a ponto que falharam.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionadas ou para exibir os dados retornados de diferentes maneiras. A tabela a seguir lista os filtros que você pode usar com o Subrelatório de Resumo P2P.

### Filtros de Subrelatório de Resumo P2P

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
<p>Se você não inserir uma hora inicial, o relatório começa automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Para</strong></p></td>
<td><p>Data e hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir uma hora final, o relatório termina automaticamente as 12:00 AM no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas são sempre de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN (Nome de domínio totalmente qualificado) do Pool de registradores ou Servidor de Borda. Você pode selecionar um pool individual ou clicar em <strong>[Todos]</strong> para ver os dados de todos os pools. Essa lista suspensa é automaticamente preenchida para você com base nos registros no banco de dados.</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista a informação oferecida no Subrelatório de Resumo P2P.

### Métricas de Subrelatório de Resumo P2P

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
<td><p><strong>Total de sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões, incluindo sessões bem-sucedidas, com falha (tanto falhas esperadas quanto inesperadas) e sessões não categorizadas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de falha</strong></p></td>
<td><p>Não</p></td>
<td><p>Percentual de sessões ponto a ponto que falharam.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões por Modalidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões agrupadas por modalidade (por exemplo, mensagens instantâneas).</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de falha por modalidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões que falharam agrupadas por modalidade (por exemplo, mensagens instantâneas).</p></td>
</tr>
</tbody>
</table>

