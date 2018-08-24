---
title: "Config. interv. de portas p/ seus servidores de medicação, apps e sua confer."
TOCTitle: "Config. interv. de portas p/ seus servidores de medicação, apps e sua confer."
ms:assetid: 4d6eaa5d-0127-453f-be6a-e55384772d83
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204872(v=OCS.15)
ms:contentKeyID: 49306662
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando intervalos de portas para seus servidores de medicação, aplicativos e sua conferência

 

_**Tópico modificado em:** 2015-04-30_

A fim de implementar a Qualidade do serviço, você deve configurar intervalos de porta idênticos para áudio, vídeo e compartilhamento de aplicativo no seu servidor de Conferência, de Aplicativo e de Mediação; além disso, esses intervalos de porta não devem se sobrepor de nenhuma maneira. Para usar um exemplo simples, imagine que você utilize as portas de 10000 a 10999 para vídeo nos seus servidores de Conferência. Isso significa que você deve reservar as portas de 10000 a 10999 para vídeo nos seus servidores de Aplicativo e de Mediação. Caso não o faça, a Qualidade do serviço não funcionará como esperado.

De forma semelhante, imagine que você reserva as portas de 10000 a 10999 para vídeo e, em seguida, reserva as portas de 10500 a 11999 para áudio. Isso pode gerar problemas na Qualidade do serviço porque os intervalos de porta se sobrepõem. Com a QoS, cada modalidade deve possuir um conjunto de portas único: se usar as portas de 10000 a 10999 para vídeo, então você deverá usar um intervalo diferente (por exemplo, de 11000 a 11999 para áudio).

Por padrão, os intervalos de porta de áudio e vídeo não se sobrepõem em Microsoft Lync Server 2013; no entanto, os intervalos atribuídos aos compartilhamentos de aplicativos se sobrepõem tanto aos intervalos de porta de áudio quanto aos de vídeo. (O que, por sua vez, significa que nenhum dessas intervalos são únicos.) Você pode verificar a existência de intervalos de porta para os servidores de Conferência, de Aplicativo e de Mediação executando os três comandos seguintes a partir do Shell de Gerenciamento do Lync Server 2013:

    Get-CsService -ConferencingServer | Select-Object Identity, AudioPortStart, AudioPortCount, VideoPortStart, VideoPortCount, AppSharingPortStart, AppSharingPortCount
    
    Get-CsService -ApplicationServer | Select-Object Identity, AudioPortStart, AudioPortCount
    
    Get-CsService -MediationServer | Select-Object Identity, AudioPortStart, AudioPortCount


> [!WARNING]  
> Como você pode observar nos comandos precedentes, é atribuído a cada tipo de porta – áudio, vídeo e compartilhamento de aplicativo – dois valores separados de propriedade: a porta inicial e a contagem de porta. A porta inicial indica a primeira porta usada por essa modalidade; por exemplo, se a porta inicial de áudio é igual a 50000, significa que a primeira porta usada para o tráfego de áudio é a porta 50000. Se a porta de contagem de áudio é 2 (valor inválido, mas é usado aqui pelo seu valor ilustrativo), significa que apenas duas portas estão alocadas para o áudio. Se a primeira porta é a porta 50000 e há um total de duas portas, significa que a segunda porta será a porta 50001 (os intervalos de porta devem ser contíguos). Dessa forma, o intervalo de porta para áudio seria da porta 50000 até a 50001, ambas incluídas.<BR>Observe que o servidor de Aplicativo e o servidor de Mediação suportam QoS somente para áudio; você não precisa modificar as portas de vídeo ou as de compartilhamento de aplicativo nos seus servidores de Aplicativo ou de Mediação.



Se você executou os três comandos anteriores, verá que os valores de portas padrão do Lync Server 2013 são configurados dessa forma:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Propriedade</th>
<th>Servidor de Conferência</th>
<th>Servidor de Aplicativo</th>
<th>Servidor de Mediação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioPortStart</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
</tr>
<tr class="even">
<td><p>AudioPortCount</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
</tr>
<tr class="odd">
<td><p>VideoPortStart</p></td>
<td><p>57501</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>VideoPortCount</p></td>
<td><p>8034</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationSharingPortStart</p></td>
<td><p>49152</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>ApplicationSharingPortCount</p></td>
<td><p>16383</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
</tbody>
</table>


Como observado anteriormente, ao configurar as portas Lync Server para a QoS, você deve assegurar que: 1) as configurações de porta de áudio sejam idênticas nos servidores de Conferência, de Aplicativo e de Mediação; 2) os intervalos de porta não se sobreponham. Se você observar com atenção a tabela anterior, verá que os intervalos de porta são idênticos nos três tipos de servidores. Por exemplo, a porta inicial de áudio está configurada para a porta 49152 em cada tipo de servidor e o número total de portas reservadas para áudio em cada servidor também é igual: 8348. No entanto, os intervalos de porta se sobrepõem: as portas de áudio iniciam na porta 49152, mas o mesmo acontece com as portas configuradas para o compartilhamento de aplicativo. Para usar a Qualidade do serviço de forma ótima, o compartilhamento de aplicativo deve ser reconfigurado para que use um único intervalo de porta. Por exemplo, você poderia configurar o compartilhamento de aplicativo para iniciar na porta 40803 e para usar as portas 8348. (Por que as portas 8348? Se você adicionar esses valores conjuntamente -- 40803 + 8348 -- significa que o compartilhamento de aplicativo usará as portas de 40803 até a 49151. Já que as portas de áudio não começam até a porta 49152, você não terá mais nenhum intervalo de porta em sobreposição.)

Após selecionar os novos intervalos de porta do compartilhamento de aplicativo, você será capaz de realizar suas modificações por meio do cmdlet Set-CsConferencingServer. Essa alteração não precisa ser feita no seus servidores de Aplicativo ou de Mediação, já que esses servidores não manipulam o tráfego do compartilhamento de aplicativos. Você precisa alterar somente os valores de porta nesses servidores caso decida reatribuir as portas usadas no tráfego de áudio.

Para modificar os valores de porta do compartilhamento de aplicativo em um único servidor de Conferência, execute um comando similar a esse a partir do Shell de Gerenciamento do Lync Server:

    Set-CsConferenceServer -Identity ConferencingServer:atl-cs-001.litwareinc.com -AppSharingPortStart 40803 -AppSharingPortCount 8348

Se deseja realizar essas alterações em todos os seus servidores de Conferência, você pode executar esse comando:

    Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -AppSharingPortStart 40803 -AppSharingPortCount 8348}

Após alterar as configurações de porta, você deverá parar e, em seguida, reiniciar cada serviço afetado pelas alterações.

Não é obrigatório que seus servidores de Conferência, de Aplicativo e de Mediação compartilhem os mesmos intervalos de porta; o único requisito é que você configure intervalos de porta únicos em todos os servidores. No entanto, a administração será normalmente mais fácil se você usar os mesmo conjuntos de portas em todos os servidores.

