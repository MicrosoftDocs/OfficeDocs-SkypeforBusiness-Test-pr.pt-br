---
title: 'Lync Server 2013: Relatório de Lista de chamadas'
TOCTitle: Relatório de Lista de chamadas
ms:assetid: 9739f9f0-7a37-4844-91d5-f089d2011013
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615020(v=OCS.15)
ms:contentKeyID: 49307537
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Lista de chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Lista de Chamadas fornece métricas de Qualidade de Experiência (QoE) para chamadas individuais feitas e recebidas em sua organização. Observe que as métricas reais relatadas dependem de como você acessa o relatório de Lista de Chamadas. Por exemplo, ao abrir o relatório do [Relatório de Dispositivos no Lync Server 2013](lync-server-2013-device-report.md), você verá métricas como as seguintes, métricas que são também relatadas no Relatório de Dispositivos:

  - Microfone do chamador

  - Alto-falante do chamador

  - Microfone do receptor

  - Alto-falante do receptor

  - Tempo de troca da taxa de voz

No entanto, se você abrir o Relatório de Lista de Chamadas do [Relatório de Localização no Lync Server 2013](lync-server-2013-location-report.md), você não verá nenhuma dessas métricas; em vez disso, você verá:

  - Viagem de ida e volta (ms)

  - Degradação (MOS)

  - Perda de pacote

  - Tremulação (ms)

Há métricas relatadas no Relatório de Local. Entretanto, a partir do Relatório de Lista de Chamadas, é sempre possível clicar na métrica Detalhe para fornecer informações completas de QoE de qualquer chamada.

## Como acessar o Relatório de Lista de Chamadas

O Relatório de Lista de Chamadas pode ser acessado de qualquer um dos seguintes relatórios:

  - [Relatório de Localização no Lync Server 2013](lync-server-2013-location-report.md) (clicando na métrica de Volume de chamada ou Percentual de chamadas ruins)

  - [Relatório de Dispositivos no Lync Server 2013](lync-server-2013-device-report.md) (clicando na métrica de Volume de chamada ou Percentual de chamadas ruins)

  - [Relatório de Resumo de Qualidade de Mídia no Lync Server 2013](lync-server-2013-media-quality-summary-report.md) (clicando na métrica de Volume de chamada ou Percentual de chamadas ruins)

  - [Relatório de Desempenho do Servidor no Lync Server 2013](lync-server-2013-server-performance-report.md) (clicando na métrica de Volume de chamada ou Percentual de chamadas ruins)

No relatório de Lista de Chamada, você pode acessar o [Relatório Detalhado de Chamadas no Lync Server 2013](lync-server-2013-call-detail-report.md) clicando na métrica Detalhe.

## Como usar melhor o Relatório de Lista de Chamada

Se não conseguir se lembrar o que algumas das métricas do Relatório de Lista de Chamada (como o Tempo de troca da taxa de voz) realmente medem, coloque o mouse sobre o rótulo da métrica; um tool tip aparecerá fornecendo uma breve descrição da métrica.

## Filtros

Nenhum. Não é possível filtrar o Relatório de Lista de Chamadas.

## Métricas

A tabela a seguir lista as informações detalhadas fornecidas no Relatório de Lista de Chamadas para cada chamada.

### Métricas do Relatório de Lista de Chamadas

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
<td><p><strong>Detalhes</strong></p></td>
<td><p>Não</p></td>
<td><p>Ao clicar neste item, o relatório exibe informações adicionais sobre a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamador</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP da pessoa que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Receptor</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP da pessoa que recebeu a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora inicial</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e horário em que a chamada teve início.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e horário em que a chamada terminou.</p></td>
</tr>
<tr class="even">
<td><p><strong>Agente do usuário do chamador</strong></p></td>
<td><p>Sim</p></td>
<td><p>Software usado pelo ponto de extremidade da pessoa que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Agente do usuário do receptor da chamada</strong></p></td>
<td><p>Sim</p></td>
<td><p>Software usado pelo ponto de extremidade da pessoa que recebeu a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Viagem de ida e volta (ms)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média de (em milissegundos) exigida para que um pacote RTP (protocolo de transporte em tempo real) viaje até outra extremidade e retorne. Tempos de viagem de ida e volta de 100 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Os valores altos de ida e volta pode ser causados por roteamento de chamada internacional, um erro de configuração de roteamento ou um servidor de mídia sobrecarregado. Tempos de ida e volta altos resultam em dificuldades com conversas de áudio em tempo real e bidirecionais.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Degradação (MOS)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média da degradação MOS enfrentada durante uma chamada. Os valores de degradação variam de um baixo de 0,0 a um alto de 5,0. Um valor de 0,5 ou menos representa degradação aceitável. Historicamente, pontuações de opções médias foram calculadas com usuários classificando a qualidade de uma chamada em uma escala de 1 a 5. No Lync Server, o Lync Server usa um conjunto de algoritmos para prever como os usuários classificaram uma chamada.</p>
<p>Os valores de degradação altos podem ser causados por congestão, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia ou ponto de extremidade sobrecarregado. A alta degradação resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Perda de pacote</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de perda de pacote RTP. (A perda de pacote ocorre quando os pacotes RTP, um protocolo usado para transmissão de áudio e vídeo pela Internet, não conseguem chegar aos seus destinos.) Taxas de perda altas normalmente são causadas por congestionamento, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia sobrecarregado. A perda de pacote normalmente resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tremulação</strong></p></td>
<td><p>Sim</p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores altos de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de correção oculta</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio ocultas para o número total de amostras. (Uma amostra de áudio oculta é uma técnica usada para suavizar a transição abrupta que normalmente seria causada por pacotes de rede descartados.) Valores altos indicam níveis consideráveis de perda de ocultação aplicada causada por perda de pacote ou tremulação e resulta na perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção estendida</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio estendidas para o número total de amostras. (Áudio estendido é o áudio que foi expandido a fim de ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos indicam níveis significativos de extensão de amostra causada por tremulação e resultam em um som robótico ou distorcido.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de correção compactada</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de amostras de áudio compactadas para o número total de amostras. (Áudio compactado é o áudio que foi compactado para ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado.) Valores altos podem indicar níveis consideráveis de compactação de amostra causada por tremulação e resultam em um som acelerado ou distorcido.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Conectividade</strong></p></td>
<td><p>Sim</p></td>
<td><p>Tipo de link de comunicação sem fio. Normalmente é um dos seguintes:</p>
<ul>
<li><p>Retransmissão</p></li>
<li><p>Direto</p></li>
</ul></td>
</tr>
</tbody>
</table>

