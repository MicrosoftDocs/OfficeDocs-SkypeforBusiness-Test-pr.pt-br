---
title: 'Lync Server 2013: Relatório Detalhado de Chamadas'
TOCTitle: Relatório Detalhado de Chamadas
ms:assetid: 38862e35-3fec-41b9-a035-0b301942d446
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558637(v=OCS.15)
ms:contentKeyID: 49306414
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório Detalhado de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório Detalhado de Chamadas apresenta uma visão detalhada de uma chamada individual; o relatório contém praticamente todas as medidas e estatísticas de qualidade da experiência coletados pelo Lync Server, divididas em sessões do relatório, tais como:

  - Informações da chamada

  - Medição do dispositivo e do sinal do chamador

  - Medição do dispositivo e do sinal de quem é chamado

  - Evento do cliente do chamador

  - Evento do cliente de quem é chamado

  - Fluxo de áudio (do chamador para que é chamado)

  - Fluxo de vídeo (do chamador para que é chamado)

  - Fluxo de áudio (de quem é chamado para o chamador)

  - Fluxo de vídeo (de quem é chamado para o chamador)

Lembre-se de que as categorias e medidas de um determinado relatório dependem de duas coisas: o tipo de sessão e o tipo de ponto de extremidade usados na sessão. Por exemplo, uma chamada com apenas áudio não reportará medidas de fluxo de vídeo; isso se deve ao fato de a chamada não ter um fluxo de vídeo. Da mesma forma, é possível ter um relatório que liste estatísticas do chamador, mas não de quem é chamado. Normalmente, isso ocorre quando quem foi chamado não usa um dispositivo compatível com SIP. Os pontos de extremidade são responsáveis por reportar estatísticas no final de uma chamada; no entanto, um telefone celular (que desconhece SIP ou as estatísticas de SIP) não pode reportar esse tipo de informação. Se você ligar para alguém e essa pessoa atender em um telefone celular, você não obterá um relatório desse telefone celular quando a chamada terminar.

O Relatório Detalhado de Chamadas é especialmente útil quando você está tentando determinar exatamente porque determinada chamada enfrentou problemas de qualidade de mídia.

## Acessando o Relatório Detalhado de Chamadas

O Relatório Detalhado de Chamadas pode ser acessado a partir de qualquer um dos seguintes relatórios:

  - O [Relatório de Localização no Lync Server 2013](lync-server-2013-location-report.md) (clicando no volume da chamada ou na medida Percentual de chamadas ruins)

  - O [Relatório de Resumo de Qualidade de Mídia no Lync Server 2013](lync-server-2013-media-quality-summary-report.md) (clicando no volume da chamada ou na medida Percentual de chamadas ruins)

  - O [Relatório de comparação de qualidade de mídia](lync-server-2013-media-quality-comparison-report.md) (clicando no [Relatório de Lista de chamadas no Lync Server 2013](lync-server-2013-call-list-report.md) e, depois, na medida Detalhes).

  - O [Relatório de Desempenho do Servidor no Lync Server 2013](lync-server-2013-server-performance-report.md) (clicando no volume da chamada ou na medida Percentual de chamadas ruins)

  - O [Relatório de Lista de chamadas no Lync Server 2013](lync-server-2013-call-list-report.md) (clicando na medida Detalhes)

No Relatório Detalhado de Chamadas, é possível acessar o [Relatório de Dispositivos no Lync Server 2013](lync-server-2013-device-report.md) clicando em uma das seguintes medidas:

  - Dispositivo de captura

  - Dispositivo de renderização

Também é possível acessar o Relatório de Tendências de Qualidade de Mídia clicando na medida Servidor de borda de áudio/vídeo.

## Fazendo o melhor uso do Relatório Detalhado de Chamadas

O Relatório Detalhado de Chamadas normalmente contém 250 medidas diferentes, inclusive itens como Descompasso do carimbo de data/hora do microfone, Tempo de SNR baixo e Extremidade próxima ao tempo de eco. Se não conseguir se lembrar o que exatamente todas essas medidas avaliam, tente pousar o mouse sobre o nome da medida; na maioria das vezes, uma dica de ferramenta será exibida descrevendo a medida.

Se tiver problemas para localizar uma medida, digite parte do nome da medida na caixa de pesquisa e clique em Localizar. Por exemplo, se não puder localizar a medida Tempo de SNR baixo, digite SNR na caixa de pesquisa e clique em Localizar.

Observe que o relatório rastreia apenas as informações sobre uma chamada. A chamada em si não é gravada.

## Filtros

Nenhum. Você não pode filtrar o Relatório Detalhado de Chamadas.

## Métricas

A tabela a seguir lista as informações fornecidas no Relatório Detalhado de Chamadas para cada chamada.

### Métricas do Relatório Detalhado de Chamadas

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
<td><p><strong>PAI do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>O P-Asserted-Identity do usuário que iniciou a chamada. Essa identidade é usada para transportar a identidade comprovada de um usuário dentro de uma rede confiável.</p></td>
</tr>
<tr class="even">
<td><p><strong>URI do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Ponto de extremidade do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Dispositivo usado para efetuar a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Agente do usuário do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Software usado no dispositivo que fez a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Início da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora em que a chamada foi iniciada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamada de desvio do Servidor de Mediação</strong></p></td>
<td><p>Não</p></td>
<td><p>Indica se a chamada conectou a um gateway de voz PSTN ou IP-PBX qualificado sem passar pelo Servidor de Mediação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OS do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Sistema operacional do computador do chamador.</p></td>
</tr>
<tr class="even">
<td><p><strong>CPU do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>CPU instalado no computador do usuário que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Número de core do CPU do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Número do processador no computador usado pela pessoa que iniciou a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Velocidade de CPU do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Velocidade de relógio do CPU do computador usado pela pessoa que iniciou a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Virtualização de CPU do chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Virtualização (se houver) no computador usado pela pessoa que iniciou a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>PAI do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>O P-Asserted-Identity do usuário convidado a entrar na chamada. Essa identidade é usada para transportar a identidade comprovada de um usuário dentro de uma rede confiável.</p></td>
</tr>
<tr class="odd">
<td><p><strong>URI do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que foi chamado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Ponto de extremidade do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Dispositivo usado para receber a chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Agente do usuário do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Software usado no dispositivo que recebeu a chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Duração</strong></p></td>
<td><p>Não</p></td>
<td><p>Tempo da chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sinalizador de aviso do desvio de mídia</strong></p></td>
<td><p>Não</p></td>
<td><p>Aviso emitido quando o Servidor de Mediação foi desviado.</p></td>
</tr>
<tr class="even">
<td><p><strong>OS do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Sistema operacional do computador do usuário que foi chamado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CPU do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>CPU instalado no computador do usuário que foi chamado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Número de core do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Número do processador no computador usado pela pessoa que foi chamada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Velocidade de CPU do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Velocidade de relógio do CPU do computador usado pela pessoa que foi chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Virtualização de CPU do receptor da chamada</strong></p></td>
<td><p>Não</p></td>
<td><p>Virtualização (se houver) no computador usado pela pessoa que foi chamada.</p></td>
</tr>
</tbody>
</table>

