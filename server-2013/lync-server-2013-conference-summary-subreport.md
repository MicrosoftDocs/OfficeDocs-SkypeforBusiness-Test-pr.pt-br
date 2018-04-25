---
title: Subrelatório de resumo da conferência
TOCTitle: Subrelatório de resumo da conferência
ms:assetid: 2fc1d2bf-34f5-4093-a6e2-250ec1f1b004
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204779(v=OCS.15)
ms:contentKeyID: 49306277
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Subrelatório de resumo da conferência

 

_**Tópico modificado em:** 2015-03-09_

O Subrelatório de Resumo da Conferência oferece uma visão geral das sessões de conferência em falha. Estas sessões em falha são detalhadas pelo tipo de sessão: Sessão de foco e sessões MCU.

## Filtros

Os filtros oferecem uma forma de retornar um conjunto de dados mais detalhado ou para exibir os dados retornados de formas diferentes. A tabela a seguir lista os filtros que você pode usar com o Subrelatório de Resumo da Conferência.

### Filtros do Subrelatório de Resumo da Conferência

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
<td><p>Data/hora inicial para o intervalo de tempo. Para exibir a data por horas, insira a data e a hora inicial como a seguir:</p>
<p>7/7/2012 13:00 horas</p>
<p>Se você não inserir uma hora inicial, o relatório começa imediatamente às 00:00 horas no dia especificado. Para exibir os dados por dia, insira apenas a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está em qualquer local da semana ou mês que você deseja exibir (você não precisa inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas sempre são de Domingo a Sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Para</strong></p></td>
<td><p>A data/hora final do intervalo de hora. Para exibir os dados por horas, insira a data e hora final como a seguir:</p>
<p>7/7/2012 13:00 horas</p>
<p>Se você não inserir uma hora final, o relatório termina automaticamente à 00:00 horas do dia especificado. Para exibir os dados por dia, apenas insira a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data que está dentro de qualquer dia da semana ou mês que deseja exibir (você não precisa inserir o primeiro dia da semana ou mês):</p>
<p>3/7/2012</p>
<p>As semanas sempre são de Domingo a Sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN do pool do Registrador ou Servidor de Borda. É possível selecionar um pool individual ou clicar em <strong>[Todos]</strong> para exibir os dados de todos os pools. Esta lista suspensa é preenchida automaticamente para você com base nos registros do banco de dados.</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Subrelatório de Resumo de Conferência.

### Métricas do Subrelatório de Resumo da Conferência

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
<td><p><strong>Total de conferências</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de conferências realizadas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de sessões de conferência</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de conferência. Uma única conferência pode ter várias sessões; por exemplo, uma conferência pode incluir uma sessão Foco e uma sessão MCU.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha de sessão geral</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de todas as conferências que falharam.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões de foco</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de Foco.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha do foco</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem das sessões de Foco que falharam.</p></td>
</tr>
<tr class="even">
<td><p>Sessões MCU</p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões MCU.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha MCU</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de sessões MCU que falharam.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sessões MCU por modalidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões MCU, agrupado por modalidade (por exemplo, conferência IM).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de falha por modalidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de sessões MCU que falharam, agrupadas por modalidade (por exemplo, conferência de IM).</p></td>
</tr>
</tbody>
</table>

