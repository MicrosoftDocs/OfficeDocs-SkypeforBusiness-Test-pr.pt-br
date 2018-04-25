---
title: Relatório de tendência de qualidade de mídia do servidor
TOCTitle: Relatório de tendência de qualidade de mídia do servidor
ms:assetid: 8a51fd13-1487-4632-b5ec-f7ae2abe8ed4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205071(v=OCS.15)
ms:contentKeyID: 49307372
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de tendência de qualidade de mídia do servidor

 

_**Tópico modificado em:** 2015-03-09_

O relatório de tendências de qualidade de mídia do servidor é uma forma gráfica de comparar até cinco servidores em relação a métricas de qualidade de experiência, como volume da chamada, percentagem de chamadas ruins, perda de pacotes e tremulação. Ele facilita determinadas tarefas como identificar servidores com desempenho ruim, subutilizados e superutilizados.

## Acessando o relatório de tendências de qualidade de mídia do servidor

O relatório de tendências de qualidade de mídia do servidor pode ser acessado por um destes relatórios:

  - [Relatório de Desempenho do Servidor no Lync Server 2013](lync-server-2013-server-performance-report.md) (ao clicar na métrica "Tendência)

  - [Relatório Detalhado de Chamadas no Lync Server 2013](lync-server-2013-call-detail-report.md) (ao clicar na métrica do servidor de borda A/V; se quem fizer ou receber a chamada for um servidor, também será possível acessar o relatório de tendências de qualidade de mídia do servidor ao clicar no nome do ponto de extremidade)

## Aproveitando ao máximo o relatório de tendências de qualidade de mídia do servidor

Quando você clicar na métrica "Tendência" no [Relatório de Desempenho do Servidor no Lync Server 2013](lync-server-2013-server-performance-report.md) para um servidor específico, o relatório de tendências de qualidade de mídia do servidor será exibido. No entanto, você verá uma instância em branco do relatório; o servidor selecionado no Relatório de desempenho do servidor não será exibido na tela. Será necessário selecionar o servidor em questão no menu suspenso "Servidores". O menu suspenso "Servidores" apresenta também a opção "Seleciontar tudo". Essa opção não funcionará caso haja mais de cinco servidores; o relatório de tendências de qualidade de mídia do servidor só pode exibir dados para, no máximo, cinco servidores por vez.

Nos gráficos exibidos pelo relatório de tendências de qualidade de mídia do servidor, os pontos "Volume da chamada" e "Percentagem de chamadas ruins" são hotlinks. Quando você clicar em um ponto do gráfico, o sistema abrirá uma instância do [Relatório de Lista de chamadas no Lync Server 2013](lync-server-2013-call-list-report.md) exibindo o total de chamadas (ou chamadas ruins) para o período especificado.

## Filtros

Os filtros são uma forma de obter dados mais direcionados ou visualizar os dados obtidos de diferentes maneiras. A tabela a seguir relaciona os filtros que podem ser usados no relatório de tendências de qualidade de mídia do servidor.

### Filtros do relatório de tendências de qualidade de mídia do servidor

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
<td><p>Data/hora de início do intervalo de tempo. Para visualizar os dados por horas, insira as datas de início e término da seguinte forma:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir uma hora de início, o relatório começará automaticamente às 12:00 AM do dia especificado. Para visualizar os dados por dia, insera somente a data:</p>
<p>7/7/2012</p>
<p>Para visualizar por semana ou por mês, insira uma data da semana ou do mês que deseja visualizar (não é necessário inserir o primeiro dia da semana ou do mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora de término do intervalo de tempo. Para visualizar os dados por horas, insira a data e a horá de término da seguinte forma:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir uma hora de término, o relatório terminará automaticamente às 12:00 AM do dia especificado. Para visualizar os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para visualizar por semana ou por mês, insira uma data da semana ou do mês que deseja visualizar (não é necessário inserir o primeiro dia da semana ou do mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Horário (podem ser exibidas, no máximo, 25 horas)</p></li>
<li><p>Diário (podem ser exibidos, no máximo, 31 dias )</p></li>
<li><p>Semanal (podem ser exibidas, no máximo, 12 semanas)</p></li>
</ul>
<p>Se as datas de início e término ultrapassarem a quantidade máxima permitida para o intervalo selecionado, apenas o máximo de valores (a contar da data de início) será exibido. Por exemplo, se você selecionar o intervalo &quot;Diário&quot; com data de início em 7/7/2012 e data de término em 28/9/2012, os dados são exibidos das 12:00 AM do dia 7/8/2012 a 12:00 AM do dia 7/9/2012 (ou seja, um tota de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de servidor</strong></p></td>
<td><p>Tipo de servidor envolvido na chamada. Os valores permitidos são</p>
<ul>
<li><p>Servidor de mediação</p></li>
<li><p>Servidor de conferência A/V</p></li>
<li><p>Servidor de borda A/V</p></li>
<li><p>Gateway (servidor de mediação)</p></li>
<li><p>Gateway (Bypass do servidor de mediação)</p></li>
<li><p>Servidor de conferência AS</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Servidores</strong></p></td>
<td><p>Nome do servidor envolvidona sessão; essa lista suspensa é preenchida automaticamente com base no valor do filtro de tipo de arquivo. É possível selecionar até cinco servidores diferentes ao compilar o relatório.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de acesso</strong></p></td>
<td><p>Indica se o participante fez logon a partir da rede interna ou de uma rede externa. Os valores permitidos são:</p>
<ul>
<li><p>[Tudo]</p></li>
<li><p>Interna</p></li>
<li><p>Externa</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de rede</strong></p></td>
<td><p>Indicao tipo de rede ao qual o participante estava conectado. Osvalores permitidos são:</p>
<ul>
<li><p>[Tudo]</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>VPN</strong></p></td>
<td><p>Indica se o participante externos estava usando conexão VPN durante a sessão. Os valores permitidos são:</p>
<ul>
<li><p>[Tudo]</p></li>
<li><p>VPN</p></li>
<li><p>Não-VPN</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Metrics

A tabela a seguir lista as informações fornecidas no relatório de tendências de qualidade de mídia do servidor.

### Métricas do relatório de tendências de qualidade de mídia do servidor

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
<td><p>No</p></td>
<td><p>Quantidade média de degradação MOS (pontuação média de opinião) experimentada durante uma chamada. Os valores de degradação podem variar de 0,0 até 5,0. Valores até 0,5 representam degradação aceitável. Anteriormente, as pontuações médias de opinião eram calculadas por meio da avaliação dos usuários com relação à qualidade de uma chamada em uma escala de 1 a 5. O Lync Server usa um conjunto de algoritmos para prever como os usuários avaliaram uma chamada.</p>
<p>Valores de degradação altos podem ser causados por congestionamento, falta de largura de banda, congestionamento ou interferência sem fio, por servidor de mídia ou por ponto de extremidade sobrecarregado. A ala degração resulta na perda ou na distorção do áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Percentual de chamadas ruins</strong></p></td>
<td><p>Não</p></td>
<td><p>O total de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada em que pelo menos uma métrica excede o valor permitido (por exemplo, uma chamada com tremulação excessiva).</p></td>
</tr>
<tr class="even">
<td><p><strong>Viagem de ida e volta (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Quantidade média de tempo (em milésimos de seguntos) exigida para que um pacote (protocolo de transporte em tempo real) viaje até outra extremidade e retorne. Tempos de viagem de ida e volta de 200 milésimos de segundo ou menos são considerados de qualidade aceitável.</p>
<p>Viagens de ida e volta com altos valores podem ser resultado do roteamento de chamadas internacionais, configurações incorretas de roteamento ou servidor de mídia sobrecarregado. Viagens de ida e volta com altos valores resultam em dificuldades para conversas de áudio bidirecionais e em tempo real.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Perda de pacote</strong></p></td>
<td><p>No</p></td>
<td><p>Taxa média de perda de pacotes de protocolo de transporte em tempo real (RTP). A perda de pacotes ocorre quando pacotes RTP, um protocolo usado para transmitir áudio e vídeo pela Internet, falha ao tentar alcançar seu destino. Valores de perda altos podem ser causados por congestionamento, falta de largura de banda, congestionamento ou interferência sem fio ou por servidor de mídia congestionado. A perda de pacotes geralmente resulta na distorção ou na perda do áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tremulação (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. A tremulação é uma medida de quanto uma chamada treme. Valores de tremulação saltos podem ser causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção oculta</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio ocultas para o número total de amostras. Uma amostra de áudio oculta é uma técnica usada para suavizar a transição abrupta que normalmente seria causada por pacotes de rede descartados. Valores altos indicam níveis consideráveis de perda de ocultação aplicada causada por perda de pacote ou tremulação e resulta na perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de correção estendida</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio estendidas para a quantidade total de amostras. Áudio estendido é o áudio expandido a fim de ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado. Valores altos indicam níveis significativos de extensão de amostra causada por tremulação e resultam em som robótico ou distorcido.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de correção compactada</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa média de amostras de áudio compactadas para a quantidade total de amostras. Áudio compactado é o áudio que foi compactado para ajudar a manter a qualidade da chamada quando um pacote de rede descartado é detectado. Valores altos podem indicar níveis consideráveis de compactação de amostra causada por tremulação e resultam em um som acelerado ou distorcido.</p></td>
</tr>
</tbody>
</table>

