---
title: Set-CsPstnGateway
TOCTitle: Set-CsPstnGateway
ms:assetid: 5d61e7e5-dacb-4dd3-bdd5-b757d98181d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398408(v=OCS.15)
ms:contentKeyID: 49306846
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsPstnGateway

 

_**Tópico modificado em:** 2015-03-09_

Modifica as propriedades de um gateway de PSTN (rede telefônica pública comutada). Gateways PSTN ajudam a dirigir as chamadas entre dispositivos na rede PSTN externa e dispositivos na sua rede Enterprise Voice interna. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsPstnGateway [-Identity <XdsGlobalRelativeIdentity>] [-AlternateByPassId <String>] [-Confirm [<SwitchParameter>]] [-Default <$true | $false>] [-Force <SwitchParameter>] [-GatewaySipClientTcpPort <UInt16>] [-GatewaySipClientTlsPort <UInt16>] [-MediationServer <String>] [-RepresentativeMediaIP <String>] [-Routable <$true | $false>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 configura o gateway PstnGateway:192.168.0.240 para ser o gateway padrão. Isso significa que PstnGateway:192.168.0.240 pode ser usado para tratar de chamadas originadas do Office Communications Server 2007 R2.

    Set-CsPstnGateway -Identity "PstnGateway:192.168.0.240" -Default $True

## EXEMPLO 2

O Exemplo 2 configura todos os gateways PSTN na organização, garantindo que cada um desses gateways possa ser usado em roteamento de saída. Para fazer isso, o comando primeiro usa o cmdlet **Get-CsService** e o parâmetro PstnGateway para retornar uma coleção de todos os gateways PSTN em uso no momento. Esta coleção é então canalizada para o cmdlet **ForEach-Object**. O cmdlet **ForEach-Object** executa o cmdlet **Set-CsPstnGateway** contra todos os gateways da coleção, definindo a propriedade Routable de cada gateway como True.

    Get-CsService -PstnGateway | ForEach-Object {Set-CsPstnGateway -Identity $_.Identity -Routable $True}

## Descrição detalhada

Gateways PSTN habilitam seus usuários Enterprise Voice a fazer e receber chamadas telefônicas de e para pessoas na rede PSTN. Esses gateways atuam como ponte entre o Servidor de Mediação e a rede PSTN.

Os gateways de PSTN geralmente são necessários quando se está usando um sistema telefônico PBX; nesse caso, você geralmente precisa empregar tanto um gateway PSTN quanto um Servidor de Mediação para rotear chamadas do Enterprise Voice para a rede PSTN. Por outro lado, se você estiver usando um sistema IP-PBX, poderá criar uma conexão SIP direta entre o PBX e o Servidor de Mediação, eliminando a necessidade de um gateway PSTN.

Depois que os seus gateways PSTN forem instalados e configurados, eles podem ser gerenciados com o cmdlet **Set-CsPstnGateway**.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsPstnGateway** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPstnGateway"}

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
<td><p><em>AlternateByPassId</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>GUID (identificador global exclusivo) representando o ID de passagem livre (bypass ID) alternativo. Esse ID é gerado automaticamente pelo Lync Server e é usado para ajudar a eliminar chamadas &quot;hairpin&quot;. Dependendo da forma como seu sistema foi configurado, isso irá permitir que chamadas &quot;hairpin&quot; passem livremente pelo Servidor de Mediação sem que seja necessário definir e associar sub-redes individuais em todos os seus sites e regiões.</p>
<p>Para fazer isso, geralmente é necessário habilitar globalmente a passagem livre para uso de sites e regiões de configurações de rede, e em seguida habilitar a passagem livre na configuração de tronco para seu gateway PSTN.</p>
<p>Uma chamada &quot;hairpin&quot; ocorre quando uma chamada de entrada da rede PSTN é direcionada de volta para essa rede via encaminhamento de chamadas ou toque simultâneo.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Default</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se definido como True, o gateway vai tratar de chamadas enviadas do Office Communications Server 2007 R2. Só pode haver um gateway padrão na coleção de gateways gerenciados por um único Servidor de Mediação.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime os prompts de confirmação ou mensagens de erro não fatal que podem ocorrer quando você executa o cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>GatewaySipClientTcpPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta de escuta usada para comunicação com os Servidores de Mediação usando protocolo TCP. O valor padrão é 5066.</p></td>
</tr>
<tr class="even">
<td><p><em>GatewaySipClientTlsPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Porta de escuta usada para comunicação com Servidores de Mediação usando o protocolo TLS. O valor padrão é 5067.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Identidade de serviço do gateway PSTN a ser modificado. Por exemplo: -Identity &quot;PstnGateway:192.168.0.240&quot;.</p>
<p>Observe que o prefixo &quot;PstnGatewayServer:&quot; pode ser deixado de fora ao especificar um gateway PSTN. Por exemplo: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>MediationServer</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Identidade de serviço do Servidor de Mediação a ser associada ao gateway PSTN. Por exemplo: -MediationServer &quot;MediationServer:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>RepresentativeMediaIP</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Endereço IP do processador de mídia associado ao gateway, desde que a localização do processador seja diferente do endereço de sinalização. Tanto a passagem livre de mídia quanto o CAC (controle de admissão de chamadas) são baseados na localização do processador de mídia do gateway; por padrão, a localização é a mesma do endereço de sinalização. Se duas localizações diferirem (por exemplo, com o processador de mídia em um site remoto e o par de sinalização no site central), RepresentativeMediaIP deve ser configurado com o endereço IP do processador de mídia.</p>
<p>Se vários processadores de mídia forem implantados no mesmo site, cada um com seu próprio endereço IP, será possível usar qualquer um desses endereços IP ao configurar a propriedade RepresentativeMediaIP.</p></td>
</tr>
<tr class="even">
<td><p><em>Routable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Se definido como True, o gateway pode ser usado em rotas de roteamento de saída.</p></td>
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

Nenhum. O cmdlet **Get-CsPstnGateway** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Set-CsPstnGateway** não retorna nenhum objeto ou valor. Em vez disso, o cmdlet modifica instâncias existentes do objeto Microsoft.Rtc.Management.Xds.DisplayPstnGateway.

## Consulte Também

#### Outros Recursos

[Get-CsService](get-csservice.md)

