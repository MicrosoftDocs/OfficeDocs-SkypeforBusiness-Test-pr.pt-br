---
title: Detalhes de exibição de QoE no Lync Server 2013
TOCTitle: Detalhes de exibição de QoE no Lync Server 2013
ms:assetid: 6a658318-a317-4546-a44c-a9c473d8e86a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688081(v=OCS.15)
ms:contentKeyID: 49886252
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Detalhes de exibição de QoE no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os modos de exibição englobam a maioria dos cenários comuns para retornar dados do banco de dados SQL de QoE (qualidade da experiência). É recomendável usar os modos de exibição para criar relatórios personalizados em vez de acessar diretamente as tabelas de banco de dados, pois é maior a probabilidade de haver compatibilidade entre os modos de exibição de versões antigas e de versões futuras.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome do modo de exibição</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-audiostreamdetail-view.md">Exibir AudioStreamDetail</a></p></td>
<td><p>Armazena informações sobre cada transmissão de áudio no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-medialine-view.md">Exibir MediaLine</a></p></td>
<td><p>Armazena informações sobre cada linha de mídia no banco de dados. Uma sessão de áudio geralmente contém uma linha de mídia de áudio. Uma sessão A/V (áudio e vídeo) geralmente contém uma linha de mídia de áudio e uma linha de mídia de vídeo. Porém, a sessão pode conter duas linhas de mídia de vídeo se um dispositivo de conferência ou se o Modo de Exibição de Galeria for usado.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-networkconfigurationsettings-view.md">Exibir NetworkConfigurationSettings</a></p></td>
<td><p>Armazena informações sobre a configuração de rede.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-session-view.md">Ver Session</a></p></td>
<td><p>Armazena informações sobre as sessões que têm registros no banco de dados.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-useragent-view.md">Exibir UserAgent</a></p></td>
<td><p>Armazena informações sobre os agentes de usuário que participaram de sessões que têm registros no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-videostreamdetail-view.md">Exibir VideoStreamDetail</a></p></td>
<td><p>Armazena informações sobre cada transmissão de vídeo no banco de dados.</p></td>
</tr>
</tbody>
</table>

