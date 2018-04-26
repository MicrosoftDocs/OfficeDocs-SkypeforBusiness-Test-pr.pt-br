---
title: Set-CsConferenceServer
TOCTitle: Set-CsConferenceServer
ms:assetid: 90f9f1f1-0029-4f97-a8f4-719523cfad56
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398738(v=OCS.15)
ms:contentKeyID: 49307446
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConferenceServer

 

_**Tópico modificado em:** 2015-03-09_

Modifica as propriedades de um Servidor de Conferência A/V (também conhecido como Servidor de conferências). O Servidor de conferências oferece recursos de áudio e vídeo (A/V) para as conferências. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsConferenceServer [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AppSharingSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-AudioVideoSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomPort <UInt16>] [-EdgeServer <String>] [-Force <SwitchParameter>] [-ImSipPort <UInt16>] [-MeetingPsomPort <UInt16>] [-PhoneSipPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 modifica a porta SIP de mensagens instantâneas do servidor de conferências ConferencingServer:atl-cs-001.litwareinc.com. Nesse exemplo, a porta é alterada para 5075.

    Set-CsConferenceServer -Identity "ConferencingServer:atl-cs-001.litwareinc.com" -ImSipPort 5075

## EXEMPLO 2

O Exemplo 2 é uma variação do comando mostrado no Exemplo 1. Neste caso, no entanto, a porta SIP de mensagens instantâneas é alterada em todos os servidores de conferências da organização. Para isso, o comando primeiramente usa o cmdlet **Get-CsService** e o parâmetro ConferencingServer, para retornar uma coleção de todos os servidores de conferências em uso. A coleção será canalizada para o cmdlet **ForEach-Object**, que executará o cmdlet **Set-CsConferenceServer** em cada servidor na coleção, configurando ImSipPort como 5075.

    Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -ImSipPort 5075}

## Descrição detalhada

Os servidores de conferências (também conhecidos como servidores de conferências de A/V) são utilizados para prover recursos de áudio e vídeo para as conferências. Por sua vez, o cmdlet **Set-CsConferenceServer** pode ser usado para modificar as propriedades destes servidores; em particular, você pode especificar quais portas serão usadas para atividades como tráfego de áudio, de vídeo e compartilhamento de aplicativos. O cmdlet **Set-CsConferenceServer** também pode ser usado para associar um determinado servidor a um Servidor de Borda ou Servidor de Arquivamento.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsConferenceServer** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferenceServer"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Número total de portas alocadas para o compartilhamento de aplicativos. As portas a serem abertas serão iniciadas com o valor configurado em AppSharingPortStart e continuarão até o número de portas especificado em AppSharingPortCount. Por exemplo: se AppSharingPortStart for definido como 60.000 e AppSharingPortCount for definido como 100, serão utilizadas as portas 60.000 a 60.099 para o compartilhamento de aplicativos.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Primeira porta da série de portas de mídia alocadas para o compartilhamento de aplicativos. Por exemplo: –AppSharingPortStart 60000.</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingSipPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta SIP usada para escutar solicitações de compartilhamento de aplicativos. As portas atualmente usadas para o compartilhamento de aplicativos são configuradas usando-se AppSharingPortStart e AppSharingPortCount.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortCount</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Número total de portas alocadas para o envio e recebimento do tráfego de áudio. As portas a serem abertas serão iniciadas com o valor configurado em AudioPortStart e continuarão até o número de portas especificado em AudioPortCount. Por exemplo: se AudioPortStart for definido como 60.000 e AudioPortCount for definido como 100, serão utilizadas as portas 60.000 a 60.099 para o tráfego de áudio.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortStart</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Primeira porta da série de portas de mídia alocadas para o envio e recebimento do tráfego de áudio. Por exemplo: –AudioPortStart 60000.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioVideoSipPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta SIP usada para escutar solicitações de entrada para os serviços de áudio e vídeo. As portas atualmente usadas para o tráfego de áudio e vídeo são configuradas usando-se AudioPortCount, AudioPortStart, VideoPortCount e VideoPortStart.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>DataPsomPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta de dados utilizada pelo protocolo Modelo de objeto compartilhado persistente (PSOM).</p></td>
</tr>
<tr class="odd">
<td><p><em>EdgeServer</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>O local do serviço do Servidor de Borda a ser associado ao servidor de conferências. Por exemplo: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Local do serviço do servidor de conferências a ser modificado. Por exemplo: -Identity &quot;ConferencingServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Observe que o prefixo &quot;ConferencingServer:&quot; poderá ser ignorado. ao se especificar um servidor de conferências. Por exemplo: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>ImSipPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta utilizada para o tráfego de mensagens instantâneas.</p></td>
</tr>
<tr class="odd">
<td><p><em>MeetingPsomPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta utilizada pelo protocolo do Modelo de objetos compartilhados persistentes (PSOM), um protocolo da Microsoft utilizado em conferências.</p></td>
</tr>
<tr class="even">
<td><p><em>PhoneSipPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta utilizada para a telefonia.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortCount</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Número total de portas alocadas para o envio e recebimento do tráfego de vídeo. As portas a serem abertas serão iniciadas com o valor configurado em VideoPortStart e continuarão até o número de portas especificado em VideoPortCount. Por exemplo: se VideoPortStart for definido como 60.000 e VideoPortCount for definido como 100, serão utilizadas as portas 60.000 a 60.099 para o tráfego de vídeo.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortStart</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Primeira porta da série de portas alocadas para o envio e recebimento do tráfego de vídeo. Por exemplo: –VideoPortStart 60000.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet**Set-CsConferenceServer** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Set-CsConferenceServer** não retorna qualquer objeto ou valor. Em vez disso, o cmdlet modifica instâncias existentes do objeto Microsoft.Rtc.Management.Xds.DisplayConferenceServer.

## Consulte Também

#### Outros Recursos

[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[Get-CsService](get-csservice.md)

