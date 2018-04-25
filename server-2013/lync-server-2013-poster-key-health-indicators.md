---
title: Key Health Indicators no Lync Server 2013
TOCTitle: 'Pôster: Key Health Indicators'
ms:assetid: 8367dccf-adaa-4a0b-a4ed-bc9570cc5e24
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn593599(v=OCS.15)
ms:contentKeyID: 61084812
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Key Health Indicators no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este artigo acompanha o pôster [Key Health Indicators: A base para a manutenção de Lync Servers íntegros](http://go.microsoft.com/fwlink/?linkid=391838), que você pode baixar do Centro de Download.

![Pôster que descreve a solução de problemas usando dados KHI](images/Dn594589.b6fe82bd-d70f-4c1f-a812-b615ac5fa7d7(OCS.15).jpg "Pôster que descreve a solução de problemas usando dados KHI")

Use esse pôster para aprender sobre KHIs (Key Health Indicators), que são contadores de desempenho com limites que têm o objetivo de revelar problemas de experiência do usuário. A coleta de dados de KHI geralmente é a primeira etapa para implementação da CQM (Metodologia da Qualidade da Chamada), que visa assegurar uma experiência de áudio de qualidade para usuários do Lync.

Se você tiver dúvidas sobre como usar a CQM, envie suas perguntas para cqmfeedback@microsoft.com.

O pôster explica as seguintes áreas:

  - O que são Key Health Indicators?

  - Coletar dados de KHI

  - Fluxo de correção para todas as funções de servidor

  - Glossário

  - Servidores front-end

  - SQL Servers de back-end

  - Servidores de mediação

  - Servidores de borda

## O que são Key Health Indicators?

Key Health Indicators são contadores de desempenho com limites que têm o objetivo de revelar problemas de experiência do usuário. A coleta de dados de KHI geralmente é a primeira etapa para a implementação da CQM (Metodologia da Qualidade da Chamada), que visa assegurar uma experiência de áudio de qualidade para usuários do Lync.

Os KHIs são usados além das Soluções de Monitoramento do Lync padrão (por exemplo, System Center Operations Manager, Transações Sintéticas, Monitoring Server) e não em vez dessas soluções.

Colete os contadores de desempenho KHI e popule a planilha de KHI que acompanha o Guia de Rede para produzir um scorecard que ajudará a determinar a integridade do servidor de uma implantação do Lync. Depois de populada, essa planilha o orienta na reparação do ambiente e fornece mais profundidade a outros participantes. Avalie os KHIs mensalmente e incorpore-os em todos os processos operacionais em andamento da implantação.

Baixe o [Guia de Rede do Lync Server](http://go.microsoft.com/fwlink/p/?linkid=390677) para visualizar a lista completa de KHIs e obter as planilhas relacionadas.

## Coletar dados de KHI

1.  Execute o script de KHI fornecido com o Guia de Rede do Lync Server em cada Lync Server. Isso criará um Coletor de Dados dentro do Monitor de Desempenho e o nomeará como KHI. Por padrão, os dados serão sondados a cada 15 segundos.

2.  Antes do início do dia útil da sua empresa, acesse cada Lync Server e inicie o Coletor de Dados de KHI.

3.  No final desse dia, interrompa o Coletor de Dados de KHI e copie os dados em um local central.

4.  Depois de usar o Monitor de Desempenho para preencher a planilha de KHI fornecida com o download do Guia de Rede do Lync Server, compare os resultados aos destinos recomendados.

## Fluxo de correção para todas as funções de servidor

Para cada servidor na sua implementação do Lync, comece verificando se a integridade e o desempenho de sistema do componente do servidor estão no nível desejado ou acima dele. Somente depois disso você deverá examinar os indicadores em relação à função do servidor na implementação do Lync geral.

Comece coletando Dados de Desempenho de KHI de todos os servidores. Para cada uma das funções do sistema (os detalhes serão discutidos posteriormente neste documento) determine se os componentes básicos do sistema atendem aos destinos recomendados. Se não atenderem, corrija o desempenho do sistema, colete novamente os dados de KHI e verifique a integridade do sistema antes de examinar as métricas específicas da função de servidor na implementação do Lync. A integridade do componente para todas as funções é definida como:

  - Utilização de CPU \< 80%

  - Média de gravação em disco \< 10 ms

  - Média de leitura em disco \< 10 ms

  - Memória disponível \>20% do total do sistema em MB

  - Tamanho da fila de rede \< 2

  - Pacotes descartados (entrada / saída) = 0

## Glossário

Os seguintes termos e acrônimos são usados neste pôster:

AS MCU = Unidade de controle multiponto de compartilhamento de aplicativos

AV MCU = MCU de áudio/vídeo

IM MCU = MCU de mensagem instantânea

UCWA = API da Web de comunicações unificadas

AV Edge = Percurso de áudio/vídeo via borda

AV Auth = Autenticação de áudio/vídeo

Pilha SIP = Contém a implementação de SIP principal do Lync

Proxy de dados = Usado para conferência de borda

LySS = Serviço de Armazenamento do Lync

## Servidores front-end

Os seguintes destinos de KHI recomendados são específicos para servidores front-end além da integridade de componente básico:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Área funcional</th>
<th>Métricas de destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AS/AV/IM MCU</p></td>
<td><p>Estado de integridade de MCU &lt;2</p></td>
</tr>
<tr class="even">
<td><p>Componentes da Web</p></td>
<td><p>Tempos limite de AD de expansão da lista de distribuição &lt;0</p>
<p>Falhas de ABWQ = 0</p>
<p>Falhas de LIS = 0</p>
<p>Erros de autenticação &lt; 1/s</p>
<p>Solicitações de ASP.NET v4 recusadas = 0</p></td>
</tr>
<tr class="odd">
<td><p>Pilha de SIP</p></td>
<td><p>Média de processamento de mensagens de entrada &lt; 1 s</p>
<p>Respostas de entrada removidas &lt; 1/s Solicitações de entrada removidas &lt; 1/s</p>
<p>Latência da fila &lt; 100 ms</p>
<p>Latência de sproc &lt; 100 ms</p>
<p>Solicitações limitadas = 0</p>
<p>Erros de autenticação &lt; 1/s</p>
<p>Tempo limite das mensagens de entrada &lt; 2</p>
<p>Média de retenção de mensagens de entrada &lt; 1 s</p>
<p>Conexões controladas pelo fluxo &lt; 2</p>
<p>Atraso médio da fila de saída &lt; 2 s</p></td>
</tr>
<tr class="even">
<td><p>LySS</p></td>
<td><p>% de espaço usado pelo BD do Serviço de Armazenamento &lt; 80</p>
<p># de falhas de replicação de réplica = 0</p>
<p># de eventos de perda de dados = 0</p></td>
</tr>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>Expectativa de vida da página &gt; 300 s</p>
<p>Solicitações em lotes / s &lt; 2500</p></td>
</tr>
</tbody>
</table>


## SQL Servers de back-end

Os seguintes destinos de KHI recomendados são específicos para SQL Servers além da integridade do componente básico:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Área funcional</th>
<th>Métricas de destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SQL</p></td>
<td><p>Expectativa de vida da página &gt; 300 s</p>
<p>Solicitações em lotes / s &lt; 2500</p></td>
</tr>
</tbody>
</table>


## Servidores de mediação

Os seguintes destinos de KHI recomendados são específicos para servidores de mediação além da integridade do componente básico:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Área funcional</th>
<th>Métricas de destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Serviço do servidor de mediação</p></td>
<td><p>Índice de falha da chamada de carga = 0</p>
<p>Chamadas com falha devido ao proxy &lt;10</p>
<p>Chamadas com falha devido ao gateway &lt;10</p>
<p>Chamadas (entrada ou saída) recusadas = 0</p>
<p>Candidatos de mídia ausentes = 0</p>
<p>Falhas de verificação de conectividade de mídia = 0</p></td>
</tr>
</tbody>
</table>


## Servidores de borda

Os seguintes destinos de KHI recomendados são específicos para os servidores de borda além da integridade do componente básico:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Área funcional</th>
<th>Métricas de destino</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Aut AV</p></td>
<td><p>Solicitações inválidas &lt; 20/s</p></td>
</tr>
<tr class="even">
<td><p>Borda AV</p></td>
<td><p>Falhas de aut. &lt;20/s</p>
<p>Falhas de alocação &lt;20/s</p>
<p>Pacotes removidos &lt;300/s</p></td>
</tr>
<tr class="odd">
<td><p>Proxy de dados</p></td>
<td><p>Conexões de servidor limitadas &lt; 3</p>
<p>O sistema está limitando &lt;1</p></td>
</tr>
<tr class="even">
<td><p>Pilha SIP</p></td>
<td><p>Conexões acima do limite removidas &lt; 1</p>
<p>Envios com tempo limite &lt;10</p>
<p>Conexões controladas por fluxo &lt;100</p>
<p>Solicitações de entrada removidas &lt; 1/s</p>
<p>Média do processamento de mensagens &lt; 3 s</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Outros Recursos

[Guia de Rede do Lync Server](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[Key Health Indicators: A base para a manutenção de Lync Servers íntegros](http://go.microsoft.com/fwlink/?linkid=391838)  
[Metodologia de qualidade da chamada do Lync](http://go.microsoft.com/fwlink/?linkid=391841)

