---
title: Relatório de comparação de qualidade de mídia
TOCTitle: Relatório de comparação de qualidade de mídia
ms:assetid: c1d0b5a8-98ff-455a-b78b-a05a21cf066d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205236(v=OCS.15)
ms:contentKeyID: 49308000
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de comparação de qualidade de mídia

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Comparação de Qualidade da Mídia permite você comparar os valores de qualidade da chamada para diferentes tipos de chamadas de áudio (por exemplo, chamadas realizadas através de uma rede sem fio contra chamadas realizadas em uma conexão com fio).

## Acessando o Relatório de Comparação de Qualidade da Mídia

O Relatório de Comparação de Qualidade da Mídia é acessado na página inicial de Relatórios de Monitoramento.

## Filtros

Os filtros oferecem uma forma de retornar um conjunto de dados mais detalhado ou exibir os dados retornados em formas diferentes. A tabela a seguir lista os filtros que você pode usar com o Relatório de Comparação de Qualidade da Mídia.

### Filtros do Relatório de Comparação de Qualidade da Mídia

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
<td><p><strong>Chamadas</strong></p></td>
<td><p>Tipo de chamada a ser usada como o item de comparação principal. Os valores permitidos são:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Externa</p></li>
<li><p>Interna</p></li>
<li><p>VPN</p></li>
<li><p>Não-VPN</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
<li><p>Externa e com fio</p></li>
<li><p>Externa e sem fio</p></li>
<li><p>Externa e VPN</p></li>
<li><p>Externa e não-VPN</p></li>
<li><p>Interna e com fio</p></li>
<li><p>Interna e sem fio</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Comparar com chamadas</strong></p></td>
<td><p>Tipo de chamada a ser usada como o item de comparação secundária. Os valores permitidos são:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Externa</p></li>
<li><p>Interna</p></li>
<li><p>VPN</p></li>
<li><p>Não-VPN</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
<li><p>Externa e com fio</p></li>
<li><p>Externa e sem fio</p></li>
<li><p>Externa e VPN</p></li>
<li><p>Externa e não-VPN</p></li>
<li><p>Interna e com fio</p></li>
<li><p>Interna e sem fio</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
</ul>
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com a data de início 7/7/12 e uma data de término de 28/2/12, os dados serão exibidos para os dias 7/8/2 00:00 horas até 7/9/12 00:00 horas (ou seja, um total de 31 dias de dados).</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Comparação de Qualidade da Mídia.

### Métricas do Relatório de Comparação de Qualidade da Mídia

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
<td><p><strong>Volume da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Degradação (MOS)</strong></p></td>
<td><p>Não</p></td>
<td><p>Quantidade média de MOS (pontuação média de opinião) experimentada durante uma chamada. Os valores de degradação podem variar de 0,0 até 5,0. Um valor de 0,5 ou menos representa uma degradação aceitável. Historicamente, as pontuações média de opinião eram calculadas por meio da avaliação dos usuários com relação à qualidade de uma chamada em uma escala de 1-para-5. O Lync Server usa um conjunto de algoritmos para prever como os usuários avaliariam uma chamada.</p>
<p>Os valores de degradação altos podem ser causados por congestão, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia ou ponto de extremidade sobrecarregado. A alta degradação resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Porcentagem de chamada inválida</strong></p></td>
<td><p>Não</p></td>
<td><p>O número total de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada em que no mínimo uma das métricas medidas excedeu o valor permitido (por exemplo, uma chamada com tremulação excessiva).</p></td>
</tr>
<tr class="even">
<td><p><strong>Viagem de ida e volta (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Quantidade média de (em milissegundos) exigida para que um pacote de Protocolo de Transporte em Tempo Real viaje até outra extremidade e retorne. Tempos de viagem de ida e volta de 200 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Altos valores de tempo de resposta podem ser causados por roteamento de chamadas internacionais, configuração incorreta de um roteamento ou um servidor de mídia sobrecarregado. Tempos de resposta altos resultam em dificuldades para conversas de áudio bidirecionais e em tempo real.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Perda de pacote</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de perda de pacotes de Protocolo de Transporte em Tempo Real (RTP). (A perda de pacotes ocorre quando pacotes RTP, um protocolo usado para transmitir áudio e vídeo pela internet, falha ao tentar alcançar seu destino). Altas taxas de perda geralmente são causadas por congestionamento, insuficiência da largura de banda, congestionamento ou interferência na rede sem fio ou um servidor de mídia sobrecarregado. A perda de pacotes normalmente resulta em distorção ou perda de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tremulação (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção oculta</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio ocultas para o número total de amostras. (Uma amostra de áudio oculta é uma técnica usada para suavizar a transição abrupta que normalmente seria causada por pacotes de rede descartados.) Valores altos indicam níveis consideráveis de perda de ocultação aplicada causada por perda de pacote ou tremulação e resulta na perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de correção estendida</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio estendidas para o número total de amostras. (Áudio estendido é o áudio que foi expandido a fim de ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos indicam níveis significativos de extensão de amostra causada por tremulação e resultam em um som robótico ou distorcido.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção compactada</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio compactadas para o número total de amostras. (Áudio compactado é o áudio que foi compactado para ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos podem indicar níveis consideráveis de compactação de amostra causada por tremulação e resultam em um som acelerado ou distorcido.</p></td>
</tr>
</tbody>
</table>

