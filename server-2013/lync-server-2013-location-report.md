---
title: 'Lync Server 2013: Relatório de Localização'
TOCTitle: Relatório de Localização
ms:assetid: cb2f1551-1e21-4f13-a39d-91f5f9010ccf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615035(v=OCS.15)
ms:contentKeyID: 49308121
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Localização no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Localização oferece informações sobre as métricas de qualidade de chamada agrupadas pelo local de rede (isto é, pela subrede). Se seus usuários enfrentarem problemas com suas chamadas, este relatório pode ajudar você a determinar se estes problemas são amplos ou estão confinados a um determinado segmento da rede.

## Acessando o Relatório de Localização

O Relatório de Localização é acessado na página inicial de Relatórios de Monitoramento. É possível detalhar o Relatório de Lista de Chamadas clicando em uma das seguintes métricas:

  - Volume da chamada

  - Porcentagem de chamada inválida

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou de exibir os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Locais permite que você filtre coisas como o local onde a chamada foi originada ou se a chamada ocorreu em uma conexão com ou sem fio. Também é possível escolher como os dados devem ser agrupados. Nesse caso, as chamadas são agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Locais.

### Filtros do Relatório de Locais

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
<td><p><strong>Local do chamador</strong></p></td>
<td><p>Sub-rede IP do usuário que fez a chamada. É possível selecionar somente <strong>[Tudo]</strong> para indicar todas as sub-redes.</p></td>
</tr>
<tr class="even">
<td><p><strong>Local do receptor da chamada</strong></p></td>
<td><p>Sub-rede IP do usuário que recebeu a chamada. É possível selecionar somente <strong>[Tudo]</strong> para indicar todas as sub-redes.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de rede</strong></p></td>
<td><p>Indica o tipo de rede que o cliente estava conectado quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indica se um cliente externo estava usando uma conexão de rede privada virtual (VPN) quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>VPN</p></li>
<li><p>Não-VPN</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Locais.

### Métricas do Relatório de Locais

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
<td><p><strong>Sub-rede do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Sub-rede IP do usuário que fez a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Sub-rede do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Sub-rede IP do usuário que recebeu a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Volume da chamada</strong></p></td>
<td><p>Sim</p></td>
<td><p>Número total de chamadas realizadas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Porcentagem de chamada inválida</strong></p></td>
<td><p>Sim</p></td>
<td><p>Porcentual de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada da qual pelo menos uma das métricas medidas excedeu o valor permitido (por exemplo, uma chamada que experimentou tremulação excessiva).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Viagem de ida e volta (ms)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média de (em milissegundos) exigida para que um pacote RTP (protocolo de transporte em tempo real) viaje até outra extremidade e retorne. Tempos de viagem de ida e volta de 100 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Os valores altos de ida e volta pode ser causados por roteamento de chamada internacional, um erro de configuração de roteamento ou um servidor de mídia sobrecarregado. Tempos de ida e volta altos resultam em dificuldades com conversas de áudio em tempo real e bidirecionais.</p></td>
</tr>
<tr class="even">
<td><p><strong>Degradação (MOS)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média da degradação MOS enfrentada durante uma chamada. Os valores de degradação variam de um baixo de 0,0 a um alto de 5,0. Um valor de 0,5 ou menos representa degradação aceitável. Historicamente, pontuações de opções médias foram calculadas com usuários classificando a qualidade de uma chamada em uma escala de 1 a 5. No Lync Server, o Lync Server usa um conjunto de algoritmos para prever como os usuários classificaram uma chamada.</p>
<p>Os valores de degradação altos podem ser causados por congestão, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia ou ponto de extremidade sobrecarregado. A alta degradação resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Perda de pacote</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de perda de pacote RTP. (A perda de pacote ocorre quando os pacotes RTP, um protocolo usado para transmissão de áudio e vídeo pela Internet, não conseguem chegar aos seus destinos.) Taxas de perda altas normalmente são causadas por congestionamento, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia sobrecarregado. A perda de pacote normalmente resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tremulação</strong></p></td>
<td><p>Sim</p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores altos de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção oculta</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio ocultas para o número total de amostras. (Uma amostra de áudio oculta é uma técnica usada para suavizar a transição abrupta que normalmente seria causada por pacotes de rede descartados.) Valores altos indicam níveis consideráveis de perda de ocultação aplicada causada por perda de pacote ou tremulação e resulta na perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de correção estendida</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio estendidas para o número total de amostras. (Áudio estendido é o áudio que foi expandido a fim de ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos indicam níveis significativos de extensão de amostra causada por tremulação e resultam em um som robótico ou distorcido.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção compactada</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio compactadas para o número total de amostras. (Áudio compactado é o áudio que foi compactado para ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos podem indicar níveis consideráveis de compactação de amostra causada por tremulação e resultam em um som acelerado ou distorcido.</p></td>
</tr>
</tbody>
</table>

