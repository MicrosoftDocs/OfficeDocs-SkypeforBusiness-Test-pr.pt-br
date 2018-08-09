---
title: "Requisitos de largura de banda de rede p/ tráfego de mídia no Lync Server 2013"
TOCTitle: "Requisitos de largura de banda de rede p/ tráfego de mídia no Lync Server 2013"
ms:assetid: 83e83b16-0f0e-4d87-901a-0faa4618cdc2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688118(v=OCS.15)
ms:contentKeyID: 49886290
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de largura de banda de rede para tráfego de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2015-09-24_

Uma parte importante do planejamento da rede está garantindo que a rede pode gerenciar o tráfego de mídia gerado pelo Lync Server. Esta seção ajuda a planejar-se para esse tráfego.

## Uso da rede de tráfego de mídia

O cálculo do uso da largura de banda do tráfego de mídia pode ser desafiador devido às diferentes variáveis, como o uso de codec, resolução e níveis de atividade. O uso da largura de banda é uma função do codec usado e da atividade do fluxo, que podem variar nos cenários. A tabela a seguir lista os codecs de áudio geralmente usados nos cenários do Lync Server 2013.

### Largura de banda de codec de áudio

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Codec de áudio</th>
<th>Cenários</th>
<th>Taxa de bits da carga de áudio (KBPS)</th>
<th>Apenas carga de áudio da largura de banda e cabeçalho IP (Kbps)</th>
<th>Carga de áudio da largura de banda, cabeçalho IP, UDP, RTP e SRTP (Kbps)</th>
<th>Carga de áudio da largura de banda, cabeçalho IP, UDP, RTP, SRTP e correção de erro de encaminhamento (Kbps)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Banda ampla RTAudio</p></td>
<td><p>Ponto a ponto</p></td>
<td><p>29,0</p></td>
<td><p>45,0</p></td>
<td><p>57,0</p></td>
<td><p>86,0</p></td>
</tr>
<tr class="even">
<td><p>Banda estreita RTAudio</p></td>
<td><p>Ponto a ponto, PSTN</p></td>
<td><p>11,8</p></td>
<td><p>27,8</p></td>
<td><p>39,8</p></td>
<td><p>51,6</p></td>
</tr>
<tr class="odd">
<td><p>G.722</p></td>
<td><p>Conferências</p></td>
<td><p>64,0</p></td>
<td><p>80,0</p></td>
<td><p>95,6</p></td>
<td><p>159,6</p></td>
</tr>
<tr class="even">
<td><p>Estéreo G.722</p></td>
<td><p>Ponto a ponto, conferências</p></td>
<td><p>128,0</p></td>
<td><p>144,0</p></td>
<td><p>159,6</p></td>
<td><p>223,6</p></td>
</tr>
<tr class="odd">
<td><p>G.711</p></td>
<td><p>PSTN</p></td>
<td><p>64,0</p></td>
<td><p>80,0</p></td>
<td><p>92,0</p></td>
<td><p>156,0</p></td>
</tr>
<tr class="even">
<td><p>Siren</p></td>
<td><p>Conferências</p></td>
<td><p>16,0</p></td>
<td><p>32,0</p></td>
<td><p>47,6</p></td>
<td><p>63,6</p></td>
</tr>
</tbody>
</table>


Os números da largura de banda na tabela anterior são baseados na geração de pacotes de 20ms (50 pacotes por segundo) e para Siren e G.722 incluem a sobrecarga do protocolo de transporte em tempo real seguro (SRTP) adicional dos cenários de conferência e supõe que o fluxo está 100% ativo. A Correção de erro de encaminhamento (FEC) é dinamicamente usada quando há uma perda de pacotes no link para ajudar a manter a qualidade dos fluxos de áudio.

A versão estéreo do codec G.722 é usada pelos sistemas baseados no Lync Room System, que permite a captura do microfone estéreo, a fim de que os ouvintes possam distinguir melhor várias pessoas falando na sala de reunião.

Para vídeos, o codec padrão é o padrão de codificação de vídeo avançada H.264/MPEG-4 Parte 10 com suas extensões de codificação de vídeo escalonável para escalabilidade temporal. Para manter a interoperabilidade com clientes Lync 2010 ou Office Communicator 2007 R2, o codec RTVideo ainda é usado em ligações de ponto a ponto entre Lync 2013 e clientes herdados. Em conferências com Lync 2013 e clientes herdados, o ponto de extremidade Lync 2013 pode codificar o vídeo por meio dos dois codecs de vídeo e enviar o bitstream H.264 para Lync 2013 e o bitstream RTVideo para Lync 2010 ou para clientes Office Communicator 2007 R2.

A largura de banda necessária depende da resolução, da qualidade e da taxa de quadros. Para cada resolução, há duas taxas de bits úteis:

  - **Taxa de bits de carga máxima**   Esta é a taxa de bits que o ponto de extremidade do Lync 2013 usará para resolução na taxa de quadros máxima suportada para esta resolução. Este valor é útil porque resulta em mais qualidade e taxa de quadros do vídeo melhor.

  - **Taxa de bits de carga mínima**   Esta é a taxa de bits abaixo da qual oponto de extremidade Lync 2013 passará a usar a menor resolução seguinte. Para garantir um nível mínimo de resolução, a taxa de bits da carga do vídeo disponível não deve ser inferior a esta taxa de bits mínima para a resolução em questão. Este valor é útil para que você possa compreender o menor valor possível em casos em que a taxa de bits máxima não está disponível ou não é praticável. Para alguns usuários, vídeoscom taxas de bits tão baixaspodem ser inaceitáveis. Por isso, tenha cuidado ao estabelecera taxa de bits de carga mínima do vídeo. Para cenas do vídeo em que há pouco ou nenhum movimento, a taxa de bits real pode ficar temporariamente abaixo do limite mínimo.

Lync 2013 oferece suporte a muitas resoluções. Isso permite ajustar-se melhor à largura de banda da rede e receber recursos de clientes. Além da alteração da taxa de proporção padrão de Lync 2013 para 16:9, a taxa de proporção 4:3 ainda é suportada em webcams quenão registram na taxa de proporção 16:9.

### Largura de banda da resolução do vídeo

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Codec de vídeo</th>
<th>Resolução e taxa de proporção</th>
<th>Taxa de bits de vídeo de carga máxima (Kbps)</th>
<th>Taxa de bits de vídeo de carga mínima (Kbps)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>H.264</p></td>
<td><p>320 x 180 (16:9)</p>
<p>212 x 160 (4:3)</p></td>
<td><p>250</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>H.264/RTVideo</p></td>
<td><p>424 x 240 (16:9)</p>
<p>320 x 240 (4:3)</p></td>
<td><p>350</p></td>
<td><p>100</p></td>
</tr>
<tr class="odd">
<td><p>H.264</p></td>
<td><p>480 x 270 (16:9)</p>
<p>424 x 320 (4:3)</p></td>
<td><p>450</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>H.264/RTVideo</p></td>
<td><p>640 x 360 (16:9)</p>
<p>640 x 480 (4:3)</p></td>
<td><p>800</p></td>
<td><p>300</p></td>
</tr>
<tr class="odd">
<td><p>H.264</p></td>
<td><p>848 x 480 (16:9)</p></td>
<td><p>1500</p></td>
<td><p>400</p></td>
</tr>
<tr class="even">
<td><p>H.264</p></td>
<td><p>960 x 540 (16:9)</p></td>
<td><p>2000</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>H.264/RTVideo</p></td>
<td><p>1280 x 720 (16:9)</p></td>
<td><p>2500</p></td>
<td><p>700</p></td>
</tr>
<tr class="even">
<td><p>H.264</p></td>
<td><p>1920 x1080 (16:9)</p></td>
<td><p>4000</p></td>
<td><p>1500</p></td>
</tr>
<tr class="odd">
<td><p>H.264/RTVideo</p></td>
<td><p>960 x 144 (20:3)</p></td>
<td><p>500</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>H.264</p></td>
<td><p>1280 x 192 (20:3)</p></td>
<td><p>1000</p></td>
<td><p>250</p></td>
</tr>
<tr class="odd">
<td><p>H.264</p></td>
<td><p>1920 x 288 (20:3)</p></td>
<td><p>2000</p></td>
<td><p>500</p></td>
</tr>
</tbody>
</table>


O FEC de vídeo é incluído na taxa de bits de carga de vídeo quando é usado para que não haja valores separados com o FEC de vídeo e sem o FEC de vídeo.

Os pontos de extremidade não transmitem pacotes de áudio ou vídeo continuamente. De acordo com o cenário, existem níveis diferentes de atividade de fluxo que indicam a frequência com que os pacotes são enviados para um fluxo. A atividade de um fluxo depende da mídia e do cenário e não depende do codec que está sendo usado. Em um cenário ponto a ponto:

  - Os pontos de extremidade enviam fluxos de áudio apenas quando os usuários falam.

  - Ambos os participantes recebem fluxos de áudio.

  - Se o vídeo é usado, ambos pontos de extremidade enviam e recebem fluxos de vídeo durante toda a chamada.

  - Para cenas dos vídeos em que há pouco ou nenhum movimento, a taxa de bits real pode ficar temporariamente bastante baixa, pois o codec de vídeo irá ignorar as regiões de codigicação do vídeo sem alterações.

Em um cenário de conferência:

  - Os pontos de extremidade enviam fluxos de áudio apenas quando os usuários falam.

  - Todos os participantes recebem fluxos de áudio.

  - Se o vídeo é usado, todos os participantespodem receber até cinco fluxos de vídeo e um fluxo de vídeo panorâmico (por exemplo, taxa de proporção 20:3). Por padrão, os cinco fluxosde vídeo têm vase no histório do orador ativo, mas os usuários também podem selecionar manualmente os participantesdos quais desejam receber fluxo de vídeo.

  - Cada participante que usar o fluxo de vídeo de envio do usuário enviará um ou mais fluxos de vídeo. O Lync 2013 agrega o recurso de envio de até cinco fluxos de vídeo para otimizar a qualidade do vídeo para todos os clientes receptores. A quantidade real de fluxos de vídeo enviados é determinada pelo remetente com base na capacidade da CPU, na largura de banda uplink disponível e na quantidade de clientes receptores que tenham selecionado um determinado fluxo de vídeo. O mais comum são os fluxos de vídeo H.264 e RTVideo enviados em caso de presença de clientes herdados na conferência. Outro cenário comum é o envio de diversos fluxos de vídeo H.264 (por exemplo, com a mesma resolução de vídeo) para acomodação de diferentes solicitações do receptor.

Além da largura de banda necessária para o tráfego do protocolo de transporte em tempo real (RTP) para mídia em áudio e vídeo, a largura de banda é necessária também paraoprotocolo de controle de transporte em tempo real (RTCP). O RTCP é usado para obter estatísticas e controle fora da banda para o fluxo RTP. Para fins de planejamento, use os números de largura de banda da tabela a seguir para verificar o tráfego RTCP. Esses valores representam a largura de banda máxima usada para RTCP e são diferentes nos fluxos de áudio e vídeo devido às diferenças nos dados de controle

### Largura de banda de RTCP

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Mídia</th>
<th>Largura de banda máxima de RTCP (Kbps)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Áudio</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>Vídeo (somente H.264 ou RTVideo enviado/recebido)</p></td>
<td><p>10</p></td>
</tr>
<tr class="odd">
<td><p>Vídeo (somente H.264 ou RTVideo enviado/recebido)</p></td>
<td><p>15</p></td>
</tr>
</tbody>
</table>


Para fins de planejamento da capacidade, as duas larguras de banda mencionadas a seguir são útei:

  - **Largura de banda máxima sem FEC**   A largura de banda máxima consumida por um fluxo, incluindo a atividade típica do fluxo e o codec típico usado em cenário sem FEC. Trata-se da largura de banda quando o fluxo está 100% em atividade e não há perda de pacote que gere uso de FEC.  É útil para a computação saber quanta largura de banda deve ser alocada para que o codec possa ser usado em um determinado cenário. 

  - **Largura de banda máxima com FEC**   A largura de banda máxima consumida por um fluxo, incluindo a atividade típica do fluxo e o codec típico usado em cenário com FEC. Trata-se da largura de banda quando o fluxo está 100% em atividade e há perda de pacote que gere uso de FEC para aprimorar a qualidade.  É útil para a computação saber quanta largura de banda deve ser alocada para que o codec possa ser usado em um determinado cenário e permitir ouso de FEC para preservar as condições de qualidade em caso de perda de pacotes. 

A tabela a seguir também lista outro valor da largura de banda, a **Largura de banda típica**. Trata-se da largura de banda consumida pelo fluxo,oque inclui a atividade típpica do fluxo e o codec típido usadono cenário. Essa largura de banda pode ser usada para aproximar a largura de banda consumida pelo tráfego de mídia, mas não deve ser usada no planejamento da capacidade porque as chamadas ultrapassarão seu valor quando o nível da atividadefor superior à media. A largura debanda típica para o fluxo de vídeo indicada nas tabelas abaixo baseia-se em diferentes resoluções de vídeo, conforme observados nos dados medidos de clientes. Por exemplo, em sessões ponto a ponto, a maioriados usuários usa a janela de renderização de vídeo padrão e parte dos usuários aumenta ou maximiza o aplicativo Lync para possibilitar resoluções mais altas.

As tabelas abaixo fornecem esses três valores de largura de banda para diversos cenários.

### Planejamento da capacidade de áudio/vídeo em sessões ponto a ponto

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Mídia</th>
<th>Codec</th>
<th>Largura de banda típica do fluxo (Kbps)</th>
<th>Largura de banda máxima sem FEC</th>
<th>Largura de banda máxima com FEC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Áudio</p></td>
<td><p>Banda ampla RTAudio</p></td>
<td><p>39,8</p></td>
<td><p>62</p></td>
<td><p>91</p></td>
</tr>
<tr class="even">
<td><p>Áudio</p></td>
<td><p>Banda estreita RTAudio</p></td>
<td><p>29,3</p></td>
<td><p>44,8</p></td>
<td><p>56,6</p></td>
</tr>
<tr class="odd">
<td><p>Vídeo principal ao chamar os pontos de extremidade Lync 2013</p></td>
<td><p>H.264</p></td>
<td><p>460</p></td>
<td><p>4010 (para resolução máxima de 1920 x 1080)</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="even">
<td><p>Vídeo principal ao chamar os pontos de extremidade Lync 2010 ou Office Communicator 2007 R2</p></td>
<td><p>RTVideo</p></td>
<td><p>460</p></td>
<td><p>2510 (para resolução máxima de 1280 x 720)</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="odd">
<td><p>Vídeo panorâmico ao chamar os pontos de extremidade Lync 2013</p></td>
<td><p>H.264</p></td>
<td><p>190</p></td>
<td><p>2010 (para resolução máxima de 1920 x 288)</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="even">
<td><p>Vídeo panorâmico ao chamar os pontos de extremidade Lync 2010 ou Office Communicator 2007 R2</p></td>
<td><p>RTVideo</p></td>
<td><p>190</p></td>
<td><p>510 (para resolução máxima de 960 x 144)</p></td>
<td><p>Não aplicável</p></td>
</tr>
</tbody>
</table>


### Planejamento de capacidade de áudio/vídeo para conferências

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Mídia</th>
<th>Codec típico</th>
<th>Largura de banda de fluxo típico (Kbps)</th>
<th>Largura de banda de fluxo máximo sem FEC</th>
<th>Largura de banda de fluxo máximo com FEC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Áudio</p></td>
<td><p>G0,722</p></td>
<td><p>46,1</p></td>
<td><p>100,6</p></td>
<td><p>164,6</p></td>
</tr>
<tr class="even">
<td><p>Áudio</p></td>
<td><p>Siren</p></td>
<td><p>25,5</p></td>
<td><p>52,6</p></td>
<td><p>68,6</p></td>
</tr>
<tr class="odd">
<td><p>Recepção de vídeo principal</p></td>
<td><p>H.264 e/ou RTVideo</p></td>
<td><p>260</p></td>
<td><p>8015</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="even">
<td><p>Envio de vídeo principal</p></td>
<td><p>H.264 e/ou RTVideo</p></td>
<td><p>270</p></td>
<td><p>8015</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="odd">
<td><p>Recepção de vídeo panorâmico</p></td>
<td><p>H.264 e/ou RTVideo</p></td>
<td><p>190</p></td>
<td><p>2010 (para resolução máxima de 1920 x 288)</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="even">
<td><p>Envio de vídeo panorâmico</p></td>
<td><p>H.264 e/ou RTVideo</p></td>
<td><p>190</p></td>
<td><p>2515 (para envio de taxas de bits com o uso de diversas resoluções/diversos codecs)</p></td>
<td><p>Não aplicável</p></td>
</tr>
</tbody>
</table>


Para o vídeoprincipal, a largurade banda típica e mínima do fluxo é a largura de banda agregada sobre todos os fluxos de vídeo recebidos e enviados, respectivamente. Mesmo com diversos fluxos de vídeo, a largura de banda típica de vídeo é inferior do que em cenários ponto a ponto porque muitas conferências de vídeo estão usando o compartilhamento de conteúdo, que usa janelas muito menores e, consequentemente, resoluções de vídeos menores. A largura de banda de carga de vídeo agregada máxiam suportada é de 8000 Kbps para fluxos de envio e recebimento que seria usados, por exemplo, se houvessea recepção de dois fluxos com resolução de 1920 x 1080p.

A largura de banda de típica de fluxo para vídeo panorâmico é baseada nos dispositivos disponíveis cuja resolução máxiam do fluxo de vídeo panorâmico é de 960 x 144. Quando o dispositivo com vídeo panorâmico na resolução 1920 x 288 ficr disponível, a largura de banda típida do fluxo deve aumentar.

### Planejamento de capacidade de áudio para PSTN

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Mídia</th>
<th>Codec típico</th>
<th>Largura de banda de fluxo típico (Kbps)</th>
<th>Largura de banda de fluxo máximo sem FEC</th>
<th>Largura de banda de fluxo máximo com FEC</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Áudio</p></td>
<td><p>G.711</p></td>
<td><p>64,8</p></td>
<td><p>97</p></td>
<td><p>161</p></td>
</tr>
<tr class="even">
<td><p>Áudio</p></td>
<td><p>Banda estreita RTAudio</p></td>
<td><p>30,9</p></td>
<td><p>44,8</p></td>
<td><p>56,6</p></td>
</tr>
</tbody>
</table>


Os números de largura de banda da rede dessas tabelas representam apenas o tráfego de uma via e incluem 5 Kbps de sobrecarga de tráfego RTCP para cada fluxo. Para vídeo, a taxa de bits de vídeo máxima é usada para computar o fluxo máximo.

