---
title: Configurando intervalos de portas para seus servidores de borda
TOCTitle: Configurando intervalos de portas para seus servidores de borda
ms:assetid: 6f0ae442-6624-4e3f-849a-5b9e387fb8cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204996(v=OCS.15)
ms:contentKeyID: 49307054
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando intervalos de portas para seus servidores de borda

 

_**Tópico modificado em:** 2015-07-24_

Com servidores de borda, não é necessário configurar intervalos de portas separados para áudio, vídeo e compartilhamento de aplicativos. De modo semelhante, os intervalos de portas usados para servidores de borda não precisam corresponder aos usados nos servidores de conferências, aplicativos e mediação. Porém, para facilitar a administração, convém alterar os intervalos de portas do servidor de borda para que correspondam aos intervalos dos outros servidores. Por exemplo, suponha que você tenha configurado os servidores de conferências, aplicativos e mediação para usar os seguintes intervalos de portas:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de pacote</th>
<th>Porta inicial</th>
<th>Número de portas reservadas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Compartilhamento de aplicativos</p></td>
<td><p>40803</p></td>
<td><p>8348</p></td>
</tr>
<tr class="even">
<td><p>Áudio</p></td>
<td><p>49152</p></td>
<td><p>8348</p></td>
</tr>
<tr class="odd">
<td><p>Vídeo</p></td>
<td><p>57500</p></td>
<td><p>8034</p></td>
</tr>
<tr class="even">
<td><p><strong>Totais</strong></p></td>
<td><p>--</p></td>
<td><p>24730</p></td>
</tr>
</tbody>
</table>


Como você pode observar, os intervalos de portas para áudio, vídeo e compartilhamento de aplicativos começam na porta 40803 e abrangem um total de 24732 portas. Se preferir, você poderá configurar um servidor de borda específico para que use esses valores de portas gerais executando um comando semelhante a este no Shell de Gerenciamento do Lync Server:

    Set-CsEdgeServer -Identity EdgeServer:atl-edge-001.litwareinc.com -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730

Ou use o comando a seguir para configurar simultaneamente todos os servidores de borda na organização:

    Get-CsService -EdgeServer | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730}

Você pode verificar as configurações de portas atuais dos servidores de borda usando este comando do Shell de Gerenciamento do Lync Server:

    Get-CsService -EdgeServer | Select-Object Identity, MediaCommunicationPortStart, MediaCommunicationPortCount

