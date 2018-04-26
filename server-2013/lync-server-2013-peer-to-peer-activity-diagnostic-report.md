---
title: 'Lync Server 2013: Relatório de Diagnóstico de Atividade Ponto a Ponto'
TOCTitle: Relatório de Diagnóstico de Atividade Ponto a Ponto
ms:assetid: 025e8ab4-2e64-4a6b-8f52-caf756a5cac3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558602(v=OCS.15)
ms:contentKeyID: 49305682
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Diagnóstico de Atividade Ponto a Ponto no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Diagnóstico de Atividades Ponto a Ponto fornece informações sobre o sucesso e falha de suas sessões de comunicação ponto a ponto. Observe que o Microsoft Lync Server 2013 diferencia entre os tipos de falha:

  - **Falha esperada** . Uma falha esperada é normalmente uma falha somente no sentido mais técnico. Por exemplo, vamos supor que você ligue para alguém, mas ele ou ela esteja fora do escritório e não possa atender ao telefone. Como a chamada não foi atendida, ela é considerada tecnicamente uma falha. Por outro lado, essa é uma falha esperada: o Microsoft Lync Server 2013 não espera que você atenda ao telefone se não estiver disponível. Da mesma maneira, uma falha esperada ocorrerá se você tentar enviar uma mensagem instantânea a um usuário que esteja offline, ou conectado apenas a um telefone que não suporta mensagem instantânea.

  - **Falha inesperada** . Um erro inesperado é exatamente o que o nome sugere: um erro que, baseado nas circunstâncias, você não espera. Por exemplo, vamos supor que você ligue para alguém e que a pessoa esteja disponível para atender à chamada; no entanto, quando o Lync Server 2013 tenta encaminhar sua chamada para a caixa postal, a chamada falha devido à perda de conectividade com a Unificação de Mensagens do Exchange. Esse é um erro inesperado: você espera que as chamada sempre sejam encaminhadas para a caixa postal. Como regra geral, falhas inesperadas são verdadeiras falhas: elas são problemas que provavelmente não podem ser corrigidos por meio da educação do usuário ou por medidas parecidas.

Observe que talvez as métricas Sucesso, Falha esperada e Falha inesperada não acrescentem à métrica Total de sessões. Por exemplo, na ilustração anterior, temos os seguintes valores:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Êxitos</th>
<th>Falhas esperadas</th>
<th>Falhas inesperadas</th>
<th>Total de sessões</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2024</p></td>
<td><p>469</p></td>
<td><p>16</p></td>
<td><p>2521</p></td>
</tr>
</tbody>
</table>


Se você adicionar 2024 + 469 + 16 terá um total de 2.509 sessões, ainda assim a coluna Total de sessões mostrará um total de 2.521 sessões. As 12 sessões que "faltam" são sessões que o sistema não pode categorizar como bem-sucedida ou sem sucesso. Esse será o caso, às vezes, quando um produto de terceiro apresentar um novo código de diagnóstico não conhecido pelo Lync Server. Quando isso acontece, as chamadas feitas usando esse produto, e o relatório desse código de diagnóstico, não podem sempre ser categorizados como Sucesso, Falha esperada ou Falha inesperada.

## Acessando o Relatório de Diagnóstico de Atividades Ponto a Ponto

O Relatório de Diagnóstico de Atividades Ponto a Ponto é acessado a partir da home page dos Relatórios de monitoramento. É possível acessar o [Relatório de Distribuição de Falha no Lync Server 2013](lync-server-2013-failure-distribution-report.md) clicando nas seguintes métricas:

  - Volume de falhas inesperadas

  - Volume de falhas esperadas

## Fazendo o melhor uso do Relatório de Diagnóstico de Atividades Ponto a Ponto

Há diversas maneiras de usar filtrar o Relatório de Diagnóstico de Atividades Ponto a Ponto, mas, por padrão, essas opções de filtragem ficam ocultas. Para exibir as opções de filtragem disponíveis, clique no botão Mostrar/Ocultar Parâmetros no canto superior direito da janela de relatório. Depois de fazer isso, as opções de filtragem ficarão disponíveis para uso.

## Filtros

Filtros oferecem uma maneira de você retornar um conjunto de dados mais preciso ou visualizar os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Diagnóstico de Atividade Ponto-a-Ponto permite que você filtre tais coisas como a modalidade de sessão (por exemplo, mensagens instantâneas, transferência de arquivos ou compartilhamento de arquivos). Você pode escolher também como os dados devem ser agrupados. Neste caso, as chamadas são agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que você pode utilizar com o Relatório de Diagnóstico de Atividade Ponto-a-Ponto.

### Filtros de Relatório de Diagnóstico de Atividade Ponto-a-Ponto

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
<tr class="odd">
<td><p><strong>Modalidade</strong></p></td>
<td><p>Indica o tipo de atividade de comunicação que ocorreu. Selecione um dos seguintes:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Mensagens instantâneas</p></li>
<li><p>Transferência de arquivos</p></li>
<li><p>Compartilhamento de aplicativos</p></li>
<li><p>Áudio</p></li>
<li><p>Vídeo</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Medidas (por modalidade)

A tabela a seguir lista as informações oferecidas no Relatório de Diagnóstico de Atividades Ponto-a-Ponto para cada modalidade.

### Medidas (por modalidade)

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
<td><p><strong>Volume de sucesso</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões ponto-a-ponto com êxito.</p></td>
</tr>
<tr class="even">
<td><p><strong>Porcentagem de sucesso</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de sessões ponto-a-ponto completas com problemas significativos. Calculado dividindo o Volume de sucesso pelo Total de sessões.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Volume de falha esperado</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões nas quais ocorreu uma &quot;falha esperada&quot;.</p>
<p>Uma falha esperada é quando se sabe que a falha ocorrerá. Por exemplo, se um usuário tiver definido seu status como Não perturbe, é esperado que qualquer chamada para esse usuário falhe.</p></td>
</tr>
<tr class="even">
<td><p><strong>Percentual de falha esperada</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de sessões ponto-a-ponto que tiveram um erro esperado. Calculado dividindo o Volume de falhas esperada pelo Total de sessões.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Volume de falha esperado</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões nas quais ocorreu uma &quot;falha inesperada&quot;.</p>
<p>Uma falha inesperada é uma falha que ocorre no que aparenta ser um sistema íntegro. Por exemplo, uma chamada não deve ser encerrada se o chamador for colocado em espera. Se isso ocorrer, isso seria sinalizado como uma falha inesperada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Percentual de falha inesperada</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de sessões ponto-a-ponto nas quais um erro inesperado ocorreu. Calculado dividindo o Volume de falhas inesperadas pelo Total de sessões.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Total de sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões, incluindo sessões bem-sucedidas, com falha (tanto falhas esperadas quanto inesperadas) e sessões não categorizadas.</p></td>
</tr>
</tbody>
</table>

