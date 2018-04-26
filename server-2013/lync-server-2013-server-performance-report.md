---
title: 'Lync Server 2013: Relatório de Desempenho do Servidor'
TOCTitle: Relatório de Desempenho do Servidor
ms:assetid: 942bb39a-1790-498e-9d99-8f6ce2d155c3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615018(v=OCS.15)
ms:contentKeyID: 49307485
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Desempenho do Servidor no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de desempenho do servidor fornece uma lista de servidores do Microsoft Lync Server 2013 que têm a porcentagem mais alta de chamadas ruins. O relatório divide os servidores por tipo, relatando estatísticas separadas para os seguintes tipos:

  - Servidor de Mediação

  - Servidor de Conferência A/V

  - Servidor de Borda A/V

  - Gateway (Servidor de Mediação)

  - Gateway (desvio de Servidor de Mediação)

  - Vídeo (incluindo métricas de vídeo para Servidores de Conferência A/V e Servidores de Borda A/V)

  - Compartilhamento de aplicativos (incluindo métricas de compartilhamento de aplicativos para Servidores de Conferência A/V e Servidores de Borda A/V)

É importante observar a classificação mostrada neste relatório como classificação relativa. Por exemplo, suponha que seu servidor com pior desempenho tenha uma chamada ruim entre suas 1.000 chamadas efetuadas. Isso é uma porcentagem de 0,1% que é mais que aceitável. No entanto, se esse for seu servidor com pior desempenho (isto é, se todos os seus outros servidores tiverem uma porcentagem de chamada ruim mais baixa que 0,1%), então esse servidor aparecerá mesmo assim no Relatório de desempenho do servidor.

## Como avaliar o Relatório de desempenho do servidor

O Relatório de desempenho do servidor é acessado a partir da página inicial dos Relatórios de Monitoramento. Você pode se aprofundar nos detalhes do [Relatório de Lista de chamadas no Lync Server 2013](lync-server-2013-call-list-report.md) clicando em uma das seguintes métricas:

  - Volume da chamada

  - Porcentagem de chamada inválida

Além disso, você ver os detalhes do Relatório de Tendência de Qualidade de Mídia do Servidor clicando na seguinte métrica:

  - Tendência

## Como usar melhor o Relatório de desempenho do servidor

O Relatório de desempenho do servidor fornece várias maneiras de filtrar dados; por exemplo, você pode filtrar por tipo de rede (chamadas feitas de uma chamada cabeada x chamadas de uma conexão sem fio) e tipo de acesso (chamadas feitas de dentro do firewall x chamadas feitas de fora do firewall). Ao exibir o relatório de desempenho do servidor, é uma boa ideia usar esses filtros. Por exemplo, suponha que você tem um Servidor de Mediação que tenha uma porcentagem de chamadas ruins igual a 3,24%. Se você observar apenas as chamadas sem fio, o mesmo servidor teria uma porcentagem de chamadas ruins próxima de 20%. Isso significa que o servidor tem dificuldades com chamadas sem fio, um problema que é obscurecido parcialmente porque o servidor não tem problemas em lidar com chamadas com fio.

## Filtros

Filtros fornecem uma forma de retornar um conjunto de dados mais focado ou exibir os dados retornados de diferentes formas. Por exemplo o Relatório de Desempenho do Servidor permite fazer coisas como filtrar os dados retornados por tipo de servidor ou por tipo de rede (ou seja, com ou sem fio). Você também pode escolher como os dados serão agrupados. Neste caso, os dados são agrupados por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Desempenho do Servidor.

### Filtros do Relatório de Desempenho do Servidor

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
<td><p><strong>Tipo de Servidor</strong></p></td>
<td><p>Indica o tipo de servidor cujo desempenho deve ser reportado. Selecione um dos seguintes:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>Servidor de Mediação</p></li>
<li><p>Servidor de Conferência A/V</p></li>
<li><p>Servidor de Borda A/V</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>N Primeiros</strong></p></td>
<td><p>Indica o número de servidores (com base no percentual de chamadas ruins) a serem exibidos em cada categoria. Por exemplo, se você selecionar <strong>5</strong> , os cinco servidores com pior desempenho são exibidos. Selecione uma das seguintes opções:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>5</p></li>
<li><p>10</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de acesso</strong></p></td>
<td><p>Indica se um cliente estava conectado na rede interna ou na rede externa quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>Interna</p></li>
<li><p>Externa</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de rede</strong></p></td>
<td><p>Indica o tipo de rede que o cliente estava conectado quando a chamada foi realizada. Selecione um dos seguintes:</p>
<ol>
<li><p>[Todos]</p></li>
<li><p>Com fio</p></li>
<li><p>Sem fio</p></li>
</ol></td>
</tr>
<tr class="odd">
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

A tabela a seguir lista as informações fornecidas no Relatório de Desempenho do Servidor.

### Métricas do Relatório de Desempenho do Servidor: Resumo da chamada de áudio

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>É possível classificar por</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Servidor</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome/endereço IP do servidor.</p></td>
</tr>
<tr class="even">
<td><p><strong>Volume da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas realizadas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Porcentagem de chamada inválida</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada em que no mínimo uma das métricas medidas excedeu o valor permitido (por exemplo, uma chamada com tremulação excessiva).</p></td>
</tr>
<tr class="even">
<td><p><strong>Viagem de ida e volta (ms)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média de (em milissegundos) exigida para que um pacote RTP (protocolo de transporte em tempo real) viaje até outra extremidade e retorne. Tempos de viagem de ida e volta de 100 milissegundos ou menos são considerados de qualidade aceitável.</p>
<p>Altos valores de tempo de resposta podem ser causados por roteamento de chamadas internacionais, configuração incorreta de um roteamento ou um servidor de mídia sobrecarregado. Tempos de resposta altos resultam em dificuldades para conversas de áudio bidirecionais e em tempo real.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Degradação (MOS)</strong></p></td>
<td><p>Sim</p></td>
<td><p>Quantidade média de degradação de pontuação média de opinião (MOS) experimentada durante uma chamada. Valores de degradação podem variar de 0,0 a um máximo de 5,0. Um valor 0,5 ou inferior representa degradação aceitável. Historicamente, pontuações médias de opinião eram calculadas solicitando aos usuários para classificar a qualidade de uma chamada em uma escala de 1 a 5. No Lync Server, o Monitoring Server usa um conjunto de algoritmos para prever como os usuários teriam classificado uma chamada.</p>
<p>Os valores de degradação altos podem ser causados por congestão, falta de largura de banda, congestionamento ou interferência sem fio ou um servidor de mídia ou ponto de extremidade sobrecarregado. A alta degradação resulta em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Perda de pacote</strong></p></td>
<td><p>Sim</p></td>
<td><p>Taxa média de perda de pacotes de protocolo de transporte em tempo real (RTP) (a perda de pacotes ocorre quando pacotes RTP, um protocolo usado para transmitir áudio e vídeo pela internet, falha ao tentar alcançar seu destino). Altas taxas de perda geralmente são causadas por congestionamento, insuficiência da largura de banda, congestionamento ou interferência na rede sem fio ou um servidor de mídia sobrecarregado. A perda de pacotes normalmente resulta em distorção ou perda de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tremulação (ms)</strong></p></td>
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
</tbody>
</table>


### Métricas do Relatório de Desempenho do Servidor: Resumo da chamada de vídeo

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
<td><p><strong>Tipo de Chamada/Tipo de Ponto de Extremidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Ao clicar neste item, o relatório mostra informações detalhadas sobre chamadas baseadas no tipo escolhido. Tipos de chamada incluem:</p>
<ul>
<li><p>Chamadas Ponto a Ponto de UC</p></li>
<li><p>Sessões de Conferência de UC</p></li>
<li><p>Sessões de Conferência PSTN</p></li>
<li><p>Chamadas PSTN: Desvio de Mídia</p></li>
<li><p>Chamadas PSTN (Não Ignorar): Trecho de UC</p></li>
<li><p>Chamadas PSTN (Não Ignorar): Trecho de Gateway</p></li>
<li><p>Outros Tipos de Chamada</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Volume da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas por tipo de chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Porcentagem de chamada inválida</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada em que no mínimo uma das métricas medidas excedeu o valor permitido (por exemplo, uma chamada com tremulação excessiva).</p></td>
</tr>
<tr class="even">
<td><p><strong>Volume de chamadas (chamadas sem fio)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas que usaram uma conexão sem fio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Volume de chamadas (chamadas VPN)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas que usaram uma conexão VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>Volume de chamadas (chamadas externas)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de chamadas que usaram uma conexão externa (ou seja, uma conexão fora da rede interna).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de bits média (Kbits/s)</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa de bits média (em quilobytes por segundo).</p></td>
</tr>
<tr class="even">
<td><p><strong>% de taxa de bits baixa</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem da chamada onde a taxa de bits foi baixa.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Perda de pacote de saída</strong></p></td>
<td><p>Não</p></td>
<td><p>Perda de pacotes do Protocolo de transporte em tempo real (RTP) para pacotes enviados. (A perda de pacotes ocorre quando pacotes RTP, um protocolo usado para transmitir áudio e vídeo pela internet, falha ao tentar alcançar seu destino). Altas taxas de perda geralmente são causadas por congestionamento, insuficiência da largura de banda, congestionamento ou interferência na rede sem fio ou um servidor de mídia sobrecarregado. A perda de pacotes normalmente resulta em distorção ou perda de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>% de quadros congelados</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem de quadros &quot;congelados&quot;. Em um quadro congelado, o vídeo não avança enquanto a parte de áudio da chamada prossegue.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Taxa de quadros média de saída</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa de quadros média para transmissões de saída durante a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Taxa de quadros média de entrada</strong></p></td>
<td><p>Não</p></td>
<td><p>Taxa de quadros média para transmissões de entrada durante a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>% de taxa de quadros baixa de entrada</strong></p></td>
<td><p>Não</p></td>
<td><p>Porcentagem da chamada onde a taxa de bits foi baixa para vídeo de entrada.</p></td>
</tr>
<tr class="even">
<td><p><strong>% de integridade do cliente</strong></p></td>
<td><p></p></td>
<td><p>Indica o estado relativo do dispositivo do cliente durante a chamada.</p></td>
</tr>
</tbody>
</table>


### Métricas do Relatório de Desempenho do Servidor: Resumo da chamada de compartilhamento de aplicativo

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
<td><p><strong>Tipo de Chamada/Tipo de Ponto de Extremidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Ao clicar neste item, o relatório mostra informações detalhadas sobre chamadas baseadas no tipo escolhido. Tipos de chamada incluem:</p>
<ul>
<li><p>Chamadas Ponto a Ponto de UC</p></li>
<li><p>Sessões de Conferência de UC</p></li>
<li><p>Sessões de Conferência PSTN</p></li>
<li><p>Chamadas PSTN: Desvio de Mídia</p></li>
<li><p>Chamadas PSTN (Não Ignorar): Trecho de UC</p></li>
<li><p>Chamadas PSTN (Não Ignorar): Trecho de Gateway</p></li>
<li><p>Outros Tipos de Chamada</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Volume da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas por tipo de chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Porcentagem de chamada inválida</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas classificadas como ruins. Uma chamada ruim é qualquer chamada em que no mínimo uma das métricas medidas excedeu o valor permitido (por exemplo, uma chamada com tremulação excessiva).</p></td>
</tr>
<tr class="even">
<td><p><strong>Volume de chamadas (chamadas sem fio)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas que usaram uma conexão sem fio.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Volume de chamadas (chamadas VPN)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas que usaram uma conexão VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>Volume de chamadas (chamadas externas)</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de chamadas que usaram uma conexão externa (ou seja, uma conexão fora da rede interna).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tremulação (ms)</strong></p></td>
<td><p>Não</p></td>
<td><p>Tremulação média detectada entre chegadas de pacote RTP. (Tremulação é uma medição de quanto uma chamada treme.) Valores altos de tremulação são normalmente causados por congestionamento ou por um servidor de mídia sobrecarregado e resultam em perda ou distorção de áudio.</p></td>
</tr>
<tr class="even">
<td><p><strong>Unidirecional relativo médio</strong></p></td>
<td><p>Não</p></td>
<td><p>Atraso unidirecional relativo médio entre dois pontos de extremidade de mídia. Esta é uma medida de latência de salto único.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Latência média de processamento lado a lado RDP</strong></p></td>
<td><p>Não</p></td>
<td><p>A latência média de processamento lado a lado RDP no Servidor de Conferência AS durante a sessão de visualização. Essa métrica não cobre a latência de rede. Uma média alta reflete um atraso maior na experiência de visualização. Um servidor de conferência sobrecarregado pode enfrentar atrasos médios maiores.</p></td>
</tr>
<tr class="even">
<td><p><strong>% total de lado a lado estragado</strong></p></td>
<td><p>Não</p></td>
<td><p>A porcentagem total de lado a lado estragados.</p></td>
</tr>
</tbody>
</table>

